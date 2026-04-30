# ⚡ FreelaFlow

> Plataforma SaaS para freelancers organizarem clientes, projetos, cobranças e precificação de serviços.

![FreelaFlow](https://img.shields.io/badge/FreelaFlow-v1.0.0-2563EB?style=for-the-badge)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

---

## 📋 Sobre o Projeto

FreelaFlow é um micro-SaaS completo desenvolvido para freelancers brasileiros que precisam:

- 👥 **Gerenciar clientes** com dados completos e status de pagamento
- 📁 **Controlar projetos** ativos e histórico de entregas
- 💬 **Cobrar via WhatsApp** com mensagens geradas automaticamente
- 🧮 **Calcular preços** de serviços com base em horas, experiência, complexidade e urgência
- 📊 **Visualizar faturamento** com dashboard e gráficos

---

## 🚀 Demo

Abra o arquivo `public/index.html` diretamente no navegador — não precisa de servidor.

**Ou acesse via GitHub Pages** (após configurar):
```
https://SEU-USUARIO.github.io/freelaflow
```

---

## 📦 Estrutura do Projeto

```
freelaflow/
├── public/
│   └── index.html          # Aplicação completa (SPA)
├── src/
│   ├── components/         # Componentes documentados
│   │   ├── Sidebar.md
│   │   ├── ClientTable.md
│   │   ├── Calculator.md
│   │   └── Dashboard.md
│   ├── pages/              # Documentação das páginas
│   │   ├── Landing.md
│   │   ├── Auth.md
│   │   └── App.md
│   ├── hooks/              # Lógica de negócio documentada
│   │   └── useClients.md
│   ├── utils/              # Utilitários
│   │   └── calculator.md
│   └── styles/             # Guia de design
│       └── design-tokens.md
├── docs/
│   ├── SETUP.md            # Guia de configuração
│   ├── DEPLOY.md           # Guia de deploy
│   ├── ROADMAP.md          # Próximas features
│   └── API.md              # Integração com backend
├── .gitignore
├── LICENSE
└── README.md
```

---

## ✨ Funcionalidades

### Plano Free
- ✅ Até 3 clientes cadastrados
- ✅ 1 cálculo de preço por dia
- ✅ Gestão básica de projetos
- ✅ Cobrança via WhatsApp
- ✅ Dashboard com métricas

### Plano Plus (R$29/mês)
- ✅ Clientes ilimitados
- ✅ Calculadora de preços ilimitada
- ✅ Cobranças ilimitadas
- ✅ Relatórios de faturamento
- ✅ Dashboard premium com gráficos
- ✅ Alertas de pagamentos atrasados

---

## 🎨 Design System

| Token | Valor |
|-------|-------|
| Azul principal | `#2563EB` |
| Azul escuro | `#1E3A8A` |
| Azul claro | `#DBEAFE` |
| Cinza texto | `#64748B` |
| Cinza claro | `#F8FAFC` |
| Sucesso | `#10B981` |
| Alerta | `#F59E0B` |
| Perigo | `#EF4444` |

**Fontes:** Sora (display) + DM Sans (corpo)

---

## 🛠️ Como Usar

### 1. Clone o repositório
```bash
git clone https://github.com/SEU-USUARIO/freelaflow.git
cd freelaflow
```

### 2. Abra no navegador
```bash
# Opção simples — abra direto
open public/index.html

# Opção com servidor local (recomendado)
npx serve public
# ou
python3 -m http.server 3000 --directory public
```

### 3. Acesse
```
http://localhost:3000
```

---

## 🌐 Deploy

### GitHub Pages (Gratuito)
```bash
# 1. Vá em Settings > Pages no seu repositório
# 2. Source: Deploy from a branch
# 3. Branch: main / pasta: /public
# 4. Save — seu site estará em:
#    https://SEU-USUARIO.github.io/freelaflow
```

### Vercel (Recomendado)
```bash
npm i -g vercel
vercel --prod
# Configure: Output Directory = public
```

### Netlify
```bash
# Arraste a pasta /public para netlify.com/drop
# ou conecte o repositório GitHub
```

---

## 🔌 Integrações Planejadas

| Serviço | Finalidade | Status |
|---------|-----------|--------|
| Supabase | Banco de dados + Auth | 🔜 Roadmap |
| Abacate Pay | Pagamentos + Assinaturas | 🔜 Roadmap |
| WhatsApp API | Cobranças automáticas | ✅ Link direto implementado |
| SendGrid | E-mails transacionais | 🔜 Roadmap |

---

## 📈 Roadmap

Veja o [ROADMAP.md](docs/ROADMAP.md) completo.

**v1.1** — Persistência com localStorage  
**v1.2** — Backend com Supabase  
**v1.3** — Autenticação real  
**v1.4** — Integração Abacate Pay  
**v2.0** — App mobile (PWA)  

---

## 🤝 Contribuindo

1. Fork o projeto
2. Crie sua branch: `git checkout -b feature/minha-feature`
3. Commit: `git commit -m 'feat: adiciona minha feature'`
4. Push: `git push origin feature/minha-feature`
5. Abra um Pull Request

---

## 📄 Licença

MIT License — veja [LICENSE](LICENSE) para detalhes.

---

## 👤 Autor

Feito com ♥ para freelancers brasileiros.

**⭐ Se este projeto te ajudou, deixe uma estrela no GitHub!**
