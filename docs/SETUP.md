# 🛠️ Guia de Configuração

## Pré-requisitos

Nenhum! O FreelaFlow v1.0 é um arquivo HTML estático puro. Basta um navegador moderno.

Para desenvolvimento com servidor local:
- Node.js 18+ (opcional)
- Python 3 (opcional)

---

## Instalação

### Método 1 — Direto no navegador
```bash
# Clone o repositório
git clone https://github.com/SEU-USUARIO/freelaflow.git

# Abra o arquivo principal
open freelaflow/public/index.html
```

### Método 2 — Servidor local com Node
```bash
git clone https://github.com/SEU-USUARIO/freelaflow.git
cd freelaflow

# Instale o serve globalmente (apenas uma vez)
npm install -g serve

# Rode o projeto
serve public -p 3000
```

Acesse: `http://localhost:3000`

### Método 3 — Servidor local com Python
```bash
cd freelaflow/public
python3 -m http.server 3000
```

Acesse: `http://localhost:3000`

---

## Configuração de Variáveis (futuras versões)

Quando integrar com Supabase, crie um arquivo `.env` na raiz:

```env
# Supabase
SUPABASE_URL=https://xxxxxxxxxxx.supabase.co
SUPABASE_ANON_KEY=sua-chave-anonima

# Abacate Pay
ABACATEPAY_API_KEY=sua-chave-api
ABACATEPAY_WEBHOOK_SECRET=seu-webhook-secret

# App
APP_URL=https://freelaflow.com.br
APP_NAME=FreelaFlow
```

> ⚠️ **Nunca commite o arquivo `.env` no Git!** Ele já está no `.gitignore`.

---

## Estrutura dos Dados (Estado Local)

O estado atual é gerenciado em memória (JavaScript). Estrutura dos clientes:

```javascript
{
  id: Number,
  name: String,        // Nome completo
  whatsapp: String,    // Número sem formatação: "11999999999"
  email: String,
  service: String,     // Serviço contratado
  value: Number,       // Valor em reais
  due: String,         // Data ISO: "2025-01-31"
  status: 'pago' | 'pendente' | 'atrasado'
}
```

---

## Personalização

### Alterar cores
Edite as variáveis CSS no topo do `public/index.html`:

```css
:root {
  --blue: #2563EB;        /* Cor principal */
  --blue-dark: #1E3A8A;   /* Cor escura */
  --blue-light: #DBEAFE;  /* Cor clara */
  /* ... */
}
```

### Alterar nome da plataforma
Busque por `FreelaFlow` no arquivo e substitua pelo seu nome.

### Alterar taxa horária base da calculadora
No JavaScript, altere a variável:
```javascript
const baseRate = 80; // R$ por hora base
```

---

## Próximos Passos

Veja o [ROADMAP.md](ROADMAP.md) para as próximas funcionalidades planejadas.
