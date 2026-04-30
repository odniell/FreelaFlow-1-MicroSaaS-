# 👥 Componente: Tabela de Clientes

## Descrição
Tabela completa com CRUD de clientes, busca em tempo real, filtro por status e ações por linha.

## Colunas
| Coluna | Campo | Notas |
|--------|-------|-------|
| Cliente | `name` + `email` | Com avatar de iniciais |
| Serviço | `service` | Texto livre |
| Valor | `value` | Formatado em R$ |
| Vencimento | `due` | Formato dd/mm/aaaa |
| Status | `status` | Badge colorido |
| Ações | — | Botões de ação |

## Ações por Linha
- 💬 **Cobrar via WhatsApp** — gera link `wa.me` com mensagem personalizada
- ✅ **Marcar como pago** — só aparece quando status ≠ 'pago'
- ✏️ **Editar** — abre modal com dados preenchidos
- 🗑️ **Excluir** — abre modal de confirmação

## Busca e Filtros
- Busca por nome, serviço ou e-mail (case-insensitive)
- Filtro por status: Todos / Pago / Pendente / Atrasado
- Filtragem em tempo real (sem submit)

## Limite Plano Free
- Máx. 3 clientes
- Banner de upgrade exibido quando limite atingido
- Botão "Novo Cliente" redireciona para upgrade

## Geração do Link WhatsApp
```javascript
const msg = encodeURIComponent(
  `Olá, ${name}! Passando para lembrar sobre o pagamento ` +
  `referente ao projeto "${service}", ` +
  `no valor de R$ ${value}. Qualquer dúvida, fico à disposição. 😊`
)
const url = `https://wa.me/55${phone}?text=${msg}`
window.open(url, '_blank')
```
