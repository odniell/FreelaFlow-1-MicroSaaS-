# 📊 Componente: Dashboard

## Descrição
Painel principal com métricas, gráfico de faturamento, alertas de pagamentos atrasados e lista de clientes recentes.

## Métricas Exibidas

| Card | Cálculo | Ícone |
|------|---------|-------|
| Total de Clientes | `clients.length` | 👥 |
| Projetos Ativos | `clients.filter(c => c.status !== 'pago').length` | 📁 |
| Pagamentos Pendentes | `sum(clients where status==='pendente').value` | ⏳ |
| Pagamentos Recebidos | `sum(clients where status==='pago').value` | ✅ |
| Receita Total | `sum(all clients).value` | 💰 |

## Gráfico de Faturamento
- Barras mensais (12 meses)
- Destaque automático no mês atual
- Tooltip com valor ao hover

## Alertas
- Mostra clientes com `status === 'atrasado'`
- Botão de cobrança rápida via WhatsApp por alerta
- Empty state quando não há atrasos

## Função de Renderização
```javascript
function renderDashboard() {
  // 1. Calcula métricas
  // 2. Atualiza cards de stats
  // 3. Renderiza gráfico de barras
  // 4. Renderiza alertas
  // 5. Renderiza lista de clientes recentes
}
```
