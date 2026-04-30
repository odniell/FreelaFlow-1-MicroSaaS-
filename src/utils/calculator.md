# 🧮 Calculadora de Preços — Lógica

## Fórmula

```
preço = baseRate × horas × multiplicadorServico × multiplicadorExp × multiplicadorComplexidade × multiplicadorPrazo

preçoMínimo  = preço × 0.8
preçoIdeal   = preço × 1.0
preçoPremium = preço × 1.4
```

## Parâmetros

### Taxa horária base
```javascript
const baseRate = 80 // R$ 80/hora como base do mercado BR
```

### Multiplicadores de Serviço
| Serviço | Multiplicador |
|---------|--------------|
| Desenvolvimento Web | 1.0 |
| Design Gráfico | 0.9 |
| Desenvolvimento Mobile | 1.1 |
| Social Media / Conteúdo | 0.8 |
| Consultoria / Estratégia | 1.2 |
| Edição de Vídeo | 0.85 |
| Copywriting / Redação | 0.95 |

### Multiplicadores de Experiência
| Nível | Multiplicador |
|-------|--------------|
| Iniciante | 0.7 |
| Intermediário | 1.0 |
| Avançado | 1.5 |
| Expert | 2.0 |

### Multiplicadores de Complexidade
| Nível | Multiplicador |
|-------|--------------|
| Baixa | 0.8 |
| Média | 1.0 |
| Alta | 1.3 |

### Multiplicadores de Prazo
| Tipo | Multiplicador |
|------|--------------|
| Normal | 1.0 |
| Urgente | 1.4 |

## Exemplo de Cálculo

```
Serviço:       Desenvolvimento Web   → 1.0
Horas:         40h
Experiência:   Avançado              → 1.5
Complexidade:  Média                 → 1.0
Prazo:         Normal                → 1.0

base     = 80 × 40 × 1.0 = 3.200
base_adj = 3.200 × 1.5 × 1.0 × 1.0 = 4.800

Preço Mínimo:  4.800 × 0.8 = R$ 3.840
Preço Ideal:   4.800 × 1.0 = R$ 4.800
Preço Premium: 4.800 × 1.4 = R$ 6.720
```

## Implementação JavaScript

```javascript
function calcPrice({ service, hours, exp, complexity, deadline }) {
  const baseRate = 80
  const base = baseRate * hours * service
  const adjusted = base * exp * complexity * deadline

  return {
    min:     Math.round(adjusted * 0.8 / 10) * 10,
    ideal:   Math.round(adjusted * 1.0 / 10) * 10,
    premium: Math.round(adjusted * 1.4 / 10) * 10
  }
}
```

> Os valores são arredondados para a dezena mais próxima para apresentação profissional.
