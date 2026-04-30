# 🚀 Guia de Deploy

## GitHub Pages (Gratuito — Recomendado para MVP)

### Passo a passo:

1. **Faça o push do projeto para o GitHub**
```bash
git init
git add .
git commit -m "feat: initial commit - FreelaFlow v1.0"
git remote add origin https://github.com/SEU-USUARIO/freelaflow.git
git push -u origin main
```

2. **Ative o GitHub Pages**
   - Vá em `Settings` > `Pages`
   - Source: **Deploy from a branch**
   - Branch: `main` | Folder: `/public`
   - Clique em **Save**

3. **Acesse em ~2 minutos**
```
https://SEU-USUARIO.github.io/freelaflow
```

---

## Vercel (Melhor performance — Recomendado para produção)

### Via CLI:
```bash
npm i -g vercel
cd freelaflow
vercel

# Quando perguntar:
# ? Set up and deploy "freelaflow"? → Y
# ? Which scope? → seu usuário
# ? Link to existing project? → N
# ? What's your project's name? → freelaflow
# ? In which directory is your code located? → ./
# ? Want to modify these settings? → Y
# ? Which settings would you like to overwrite? → Output Directory
# ? Output Directory: → public
```

### Via GitHub (automático):
1. Acesse [vercel.com](https://vercel.com) e conecte seu GitHub
2. Importe o repositório `freelaflow`
3. Em **Build & Output Settings**:
   - Framework Preset: **Other**
   - Output Directory: `public`
4. Clique em **Deploy**

✅ Deploy automático a cada `git push`!

---

## Netlify

### Via drag & drop (mais rápido):
1. Acesse [netlify.com/drop](https://app.netlify.com/drop)
2. Arraste a pasta `/public` para a área indicada
3. Pronto! URL gerada automaticamente.

### Via GitHub:
1. Acesse [app.netlify.com](https://app.netlify.com) > **Add new site**
2. Conecte o repositório GitHub
3. Configure:
   - Build command: *(deixe vazio)*
   - Publish directory: `public`
4. Clique em **Deploy site**

---

## Domínio Personalizado

### Configurar domínio próprio (ex: `freelaflow.com.br`):

**No Vercel:**
1. Settings > Domains > Add Domain
2. Digite seu domínio
3. Configure os DNS conforme instruções

**No Netlify:**
1. Site Settings > Domain Management > Add custom domain
2. Configure os DNS conforme instruções

**Registro de domínio .com.br:**
- [Registro.br](https://registro.br) — R$40/ano
- [GoDaddy](https://godaddy.com)
- [Namecheap](https://namecheap.com)

---

## SSL/HTTPS

✅ Automático em todas as plataformas acima (Let's Encrypt gratuito).

---

## Checklist pré-deploy

- [ ] Substituir nome de exemplo nos depoimentos
- [ ] Atualizar link de pagamento (Abacate Pay)
- [ ] Configurar domínio personalizado
- [ ] Testar em mobile
- [ ] Testar botão de cobrança WhatsApp
- [ ] Verificar todos os links da landing page
- [ ] Adicionar Google Analytics (opcional)
- [ ] Configurar meta tags de SEO
