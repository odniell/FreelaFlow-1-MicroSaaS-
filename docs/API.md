# 🔌 Documentação de API e Integrações

## Supabase (Banco de Dados + Auth)

### Instalação
```bash
npm install @supabase/supabase-js
```

### Schema SQL — Tabela de Clientes
```sql
-- Rodar no SQL Editor do Supabase
CREATE TABLE clients (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  user_id UUID REFERENCES auth.users(id) ON DELETE CASCADE,
  name TEXT NOT NULL,
  whatsapp TEXT,
  email TEXT,
  service TEXT NOT NULL,
  value DECIMAL(10,2) DEFAULT 0,
  due_date DATE,
  status TEXT CHECK (status IN ('pago', 'pendente', 'atrasado')) DEFAULT 'pendente',
  notes TEXT,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

-- Row Level Security (cada usuário vê apenas seus dados)
ALTER TABLE clients ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users can only access own clients"
  ON clients FOR ALL
  USING (auth.uid() = user_id);

-- Tabela de perfis/planos
CREATE TABLE profiles (
  id UUID REFERENCES auth.users(id) PRIMARY KEY,
  name TEXT,
  plan TEXT CHECK (plan IN ('free', 'plus')) DEFAULT 'free',
  calc_uses_today INTEGER DEFAULT 0,
  calc_uses_reset_at DATE DEFAULT CURRENT_DATE,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

ALTER TABLE profiles ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users can access own profile"
  ON profiles FOR ALL
  USING (auth.uid() = id);
```

### Inicialização no código
```javascript
import { createClient } from '@supabase/supabase-js'

const supabase = createClient(
  process.env.SUPABASE_URL,
  process.env.SUPABASE_ANON_KEY
)

// Buscar clientes
const { data: clients, error } = await supabase
  .from('clients')
  .select('*')
  .order('created_at', { ascending: false })

// Adicionar cliente
const { data, error } = await supabase
  .from('clients')
  .insert([{ name, whatsapp, email, service, value, due_date, status }])

// Atualizar status
const { error } = await supabase
  .from('clients')
  .update({ status: 'pago' })
  .eq('id', clientId)

// Deletar
const { error } = await supabase
  .from('clients')
  .delete()
  .eq('id', clientId)
```

---

## Abacate Pay (Pagamentos)

### Criar assinatura Plus
```javascript
// POST /api/subscribe
const response = await fetch('https://api.abacatepay.com/v1/subscriptions', {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${process.env.ABACATEPAY_API_KEY}`,
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    customer: {
      name: user.name,
      email: user.email,
      taxId: user.cpf  // CPF opcional
    },
    products: [{
      externalId: 'freelaflow-plus',
      name: 'FreelaFlow Plus',
      quantity: 1,
      price: 2900  // centavos = R$29,00
    }],
    returnUrl: 'https://freelaflow.com.br/sucesso',
    completionUrl: 'https://freelaflow.com.br/api/webhook/abacatepay'
  })
})

const { url } = await response.json()
window.location.href = url  // Redireciona para checkout
```

### Webhook de confirmação
```javascript
// POST /api/webhook/abacatepay
app.post('/api/webhook/abacatepay', async (req, res) => {
  const signature = req.headers['x-abacatepay-signature']
  // Verificar assinatura...

  const { event, data } = req.body

  if (event === 'billing.paid') {
    // Atualizar plano do usuário para 'plus' no Supabase
    await supabase
      .from('profiles')
      .update({ plan: 'plus' })
      .eq('email', data.customer.email)
  }

  res.json({ ok: true })
})
```

---

## WhatsApp (Atual — Link Direto)

A implementação atual usa links `wa.me` sem necessidade de API:

```javascript
function chargeWhatsApp(client) {
  const phone = client.whatsapp.replace(/\D/g, '')
  const msg = encodeURIComponent(
    `Olá, ${client.name}! Passando para lembrar sobre o pagamento ` +
    `referente ao projeto "${client.service}", ` +
    `no valor de R$ ${client.value.toLocaleString('pt-BR')}. ` +
    `Qualquer dúvida, fico à disposição. 😊`
  )
  window.open(`https://wa.me/55${phone}?text=${msg}`, '_blank')
}
```

---

## Variáveis de Ambiente

```env
# .env (não commitar!)
SUPABASE_URL=https://xxxxxxxxxxx.supabase.co
SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...

ABACATEPAY_API_KEY=sk_live_...
ABACATEPAY_WEBHOOK_SECRET=whsec_...

APP_URL=https://freelaflow.com.br
NODE_ENV=production
```
