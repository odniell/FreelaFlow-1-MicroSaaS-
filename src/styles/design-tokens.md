# 🎨 Design Tokens — FreelaFlow

## Cores

```css
:root {
  /* Azul principal */
  --blue: #2563EB;
  --blue-dark: #1E3A8A;
  --blue-mid: #3B82F6;
  --blue-light: #DBEAFE;
  --blue-pale: #EFF6FF;

  /* Neutros */
  --white: #FFFFFF;
  --gray-light: #F8FAFC;
  --gray-border: #E2E8F0;
  --gray-text: #64748B;
  --gray-mid: #334155;
  --gray-dark: #1E293B;

  /* Semânticos */
  --success: #10B981;
  --success-light: #D1FAE5;
  --warning: #F59E0B;
  --warning-light: #FEF3C7;
  --danger: #EF4444;
  --danger-light: #FEE2E2;
}
```

## Tipografia

| Fonte | Uso | Pesos |
|-------|-----|-------|
| Sora | Títulos, labels, sidebar, badges | 300, 400, 500, 600, 700, 800 |
| DM Sans | Corpo do texto, inputs, tabelas | 300, 400, 500, 600 |

```css
--font-display: 'Sora', sans-serif;
--font-body: 'DM Sans', sans-serif;
```

## Espaçamentos (Border Radius)

```css
--radius-sm: 8px;
--radius-md: 12px;
--radius-lg: 16px;
--radius-xl: 20px;
--radius-full: 9999px;
```

## Sombras

```css
--shadow-sm: 0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.04);
--shadow-md: 0 4px 16px rgba(37,99,235,0.10), 0 2px 6px rgba(0,0,0,0.06);
--shadow-lg: 0 12px 40px rgba(37,99,235,0.15), 0 4px 12px rgba(0,0,0,0.08);
```

## Componentes

### Botões

```html
<!-- Primário -->
<button class="btn btn-primary">Ação principal</button>

<!-- Secundário -->
<button class="btn btn-secondary">Ação secundária</button>

<!-- Ghost -->
<button class="btn btn-ghost">Ver todos →</button>

<!-- Danger -->
<button class="btn btn-danger">Excluir</button>

<!-- Success -->
<button class="btn btn-success">✅ Confirmar</button>

<!-- WhatsApp -->
<button class="btn btn-whatsapp">💬 Cobrar</button>

<!-- Tamanhos -->
<button class="btn btn-primary btn-sm">Pequeno</button>
<button class="btn btn-primary btn-lg">Grande</button>
<button class="btn btn-primary btn-xl">Extra grande</button>
```

### Badges de Status

```html
<span class="badge badge-success">
  <span class="status-dot"></span>Pago
</span>

<span class="badge badge-warning">
  <span class="status-dot"></span>Pendente
</span>

<span class="badge badge-danger">
  <span class="status-dot"></span>Atrasado
</span>
```

### Cards

```html
<!-- Card padrão do dashboard -->
<div class="dash-card">
  <div class="dash-card-header">
    <div class="dash-card-title">Título do card</div>
  </div>
  <!-- conteúdo -->
</div>

<!-- Card de estatística -->
<div class="dash-stat-card">
  <div class="dash-stat-icon" style="background:#EFF6FF;">📊</div>
  <div class="dash-stat-label">Label</div>
  <div class="dash-stat-value">R$0</div>
  <div class="dash-stat-change up">↑ +18%</div>
</div>
```

## Layout

- **Sidebar:** 240px de largura, fixa
- **Topbar:** 60px de altura
- **Content padding:** 28px
- **Breakpoint mobile:** 768px
