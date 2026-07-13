# OnePort 365 CRM MVP - Design System Rules

**Project**: OnePort 365 Backoffice 2.0 MVP
**Architecture**: Standalone Single-Page HTML Application
**Last Updated**: 2026-07-09

---

## 1. Design System Structure

### 1.1 Token Definitions

All design tokens are defined as CSS custom properties in the `:root` selector at the top of `index.html` (lines 13-26).

**Location**: `/index.html` lines 13-26

```css
:root{
  /* Primary Colors */
  --green:#023819;      /* Primary brand dark */
  --green-2:#2f6b1e;    /* Forest green */
  --green-3:#7fae2e;    /* Mid green */
  --lime:#BFFB4F;       /* Accent lime */
  --lime-soft:#EDF4E1;  /* Soft lime background */

  /* Accent Colors */
  --gold:#FFCC1A;       /* Primary gold */
  --gold-deep:#B8860B;  /* Deep gold */
  --success:#008751;    /* Success state */
  --error:#FF1A1A;      /* Error/alert state */

  /* Surface Colors */
  --cream:#FDFBF1;      /* Cream background */
  --panel:#FFFFFF;      /* Panel/card background */
  --page:#faf9f5;       /* Page background */
  --sage:#D1DBBD;       /* Light sage */

  /* Border & Lines */
  --line:rgba(2,56,25,.09);   /* Light border */
  --line-2:rgba(2,56,25,.16); /* Medium border */

  /* Text Colors */
  --ink:#383838;        /* Primary text */
  --muted:#808080;      /* Muted text */
  --muted-2:#5F5E5A;    /* Secondary muted */

  /* Shadows */
  --sh-card:0 1px 2px rgba(2,56,25,.05);
  --sh-raise:0 2px 4px rgba(2,56,25,.05),0 10px 24px -10px rgba(2,56,25,.16);
  --sh-modal:0 4px 8px rgba(2,56,25,.06),0 18px 40px -16px rgba(2,56,25,.22);

  /* Customer Tier Colors */
  --tier-spot-bg:#EDEFE8; --tier-spot-tx:#5F5E5A;
  --tier-mid-bg:#FFF3CC; --tier-mid-tx:#B8860B;
  --tier-ent-bg:#023819; --tier-ent-tx:#BFFB4F;

  /* Typography */
  --f-head:'Nohemi','Poppins',sans-serif;
  --f-body:'Poppins',system-ui,sans-serif;
}
```

### 1.2 Typography System

**Fonts**:
- **Headings**: Nohemi (primary), Poppins (fallback)
- **Body/UI**: Poppins with system font fallback
- **Weights**: 400, 500, 600, 700

**Font Loading**:
```html
<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">

<!-- Custom Font (Nohemi) -->
@font-face{
  font-family:'Nohemi';
  font-weight:400 500;
  src:url('https://db.onlinewebfonts.com/t/29ddb4605533a38e086b48fa105e0d12.woff2') format('woff2');
}
@font-face{
  font-family:'Nohemi';
  font-weight:600 800;
  src:url('https://db.onlinewebfonts.com/t/2acd1ac6664b7b1a1545cc36d0680783.woff2') format('woff2');
}
```

**Typography Usage**:
- `h1, h2, h3, .head` → `font-family: var(--f-head)`
- All other elements → `font-family: var(--f-body)`
- Base font size: `14px`

---

## 2. Component Library

### 2.1 Component Architecture

**Structure**: Vanilla JavaScript with inline styles - No framework used
**Pattern**: Component functions that return HTML strings
**State Management**: Plain JavaScript variables

### 2.2 Core Components

#### Buttons

```css
/* Primary Button */
.btn {
  border: 1px solid transparent;
  border-radius: 10px;
  padding: 11px 18px;
  font-family: var(--f-body);
  font-weight: 600;
  font-size: 14px;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 7px;
  transition: box-shadow .15s, filter .15s;
}

/* Gold/Lime variant (primary CTA) */
.btn-gold, .btn-lime {
  background: var(--lime);
  color: var(--green);
  box-shadow: var(--sh-card);
}
.btn-gold:hover, .btn-lime:hover {
  filter: brightness(.97);
  box-shadow: var(--sh-raise);
}

/* Ghost variant (secondary) */
.btn-ghost {
  background: #fff;
  border: 1px solid var(--line-2);
  color: var(--ink);
}
.btn-ghost:hover {
  background: var(--page);
}

/* Outline variant */
.btn-outline {
  /* Defined inline in specific contexts */
}
```

#### Cards

```css
.card {
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 14px;
  padding: 13px 14px;
  box-shadow: var(--sh-card);
}
```

#### KPI Cards

```css
.kpi {
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 16px;
  padding: 18px 20px;
  box-shadow: var(--sh-card);
}

.kpis .kpi:first-child {
  background: var(--lime-soft);
  border-color: transparent;
}

.kpi .val {
  font-family: var(--f-head);
  font-size: 32px;
  font-weight: 700;
  color: var(--green);
  line-height: 1;
}
```

#### Badges

```css
/* Rate Type Badge */
.rate-badge {
  /* Inline styles, varies by rate type */
  font-size: 11px;
  padding: 4px 10px;
  border-radius: 6px;
  font-weight: 600;
  text-transform: capitalize;
}

/* Equipment Badge */
.equip-badge {
  /* Inline styles */
}

/* Stage Pill */
.stage-pill {
  background: var(--tier-spot-bg);
  color: var(--muted-2);
  font-size: 11px;
  padding: 3px 9px;
  border-radius: 6px;
}
```

#### Tables

```css
table {
  width: 100%;
  border-collapse: collapse;
}

.tbl-wrap {
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 16px;
  overflow: hidden;
  box-shadow: var(--sh-card);
}

th {
  text-align: left;
  font-size: 11px;
  letter-spacing: .5px;
  color: var(--muted-2);
  font-weight: 600;
  text-transform: uppercase;
  padding: 13px 16px;
  background: #F3F7EA;
}

td {
  padding: 10px 14px;
  border-top: .5px solid var(--line);
  font-size: 13px;
  vertical-align: middle;
}
```

#### Modals

```css
.overlay {
  position: fixed;
  inset: 0;
  background: rgba(10,26,12,.42);
  display: none;
  align-items: center;
  justify-content: center;
  padding: 20px;
  z-index: 50;
}

.modal {
  background: #fff;
  border-radius: 16px;
  max-width: 520px;
  width: 100%;
  box-shadow: var(--sh-modal);
  max-height: 90vh;
  display: flex;
  flex-direction: column;
}

.modal.wide {
  max-width: 800px;
}
```

---

## 3. Frameworks & Libraries

### 3.1 Architecture

**Type**: Standalone Single-Page Application
**Framework**: None (Vanilla JavaScript)
**Build System**: None required
**Bundler**: None required

### 3.2 Technology Stack

- **HTML5**: Single file structure
- **CSS3**: Inline `<style>` block with CSS custom properties
- **JavaScript (ES6+)**: Inline `<script>` block
- **No Dependencies**: Pure web standards

### 3.3 Development Server

```json
{
  "scripts": {
    "start": "npx http-server -p 8080 -o",
    "dev": "npx http-server -p 8080 -o"
  }
}
```

**Server Options**:
1. `npm start` (recommended)
2. `npx http-server -p 8080 -o`
3. `python3 -m http.server 8080`

---

## 4. Asset Management

### 4.1 Asset Structure

```
/assets/
├── oneport365-logo.png     # Company logo (134KB)
└── carriers/               # Carrier logos for freight rates
    ├── msc.svg
    ├── maersk.svg
    ├── cma.svg
    ├── hapag.svg
    ├── cosco.svg
    ├── evergreen.svg
    ├── one.svg
    ├── pil.svg
    └── zim.svg
```

### 4.2 Asset Usage Patterns

**Logo Usage**:
```html
<img src="assets/oneport365-logo.png" alt="OnePort 365" class="logo-img">
```

**Carrier Logos** (dynamic):
```javascript
function carrierLogo(name){
  const cls=carrierClass(name);
  if(cls) return `assets/carriers/${cls}.svg`;
  return null;
}

// Usage in HTML
const logoPath = carrierLogo(carrier.name);
if(logoPath) {
  html = `<img src="${logoPath}" alt="${carrier.name}">`;
}
```

### 4.3 Asset Optimization

- **SVG**: Used for all carrier logos (vector format)
- **PNG**: Used for company logo
- **No CDN**: All assets served locally from `/assets/`

---

## 5. Icon System

### 5.1 Icon Approach

**Type**: Inline SVG icons
**Style**: Stroke-based outlines (Feather-style)
**Format**: SVG markup directly in HTML strings

### 5.2 Icon Pattern

```javascript
// Icons are inline SVG with consistent attributes
const icon = `<svg viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" fill="none" stroke-width="1.8">
  <path d="M4 20V10M10 20V4M16 20v-7M22 20H2"/>
</svg>`;
```

### 5.3 Common Icons

**Freight Type Icons**:
```javascript
const RATE_TYPES = [
  {
    key: 'ocean',
    label: 'Ocean Freight',
    icon: '<svg viewBox="0 0 24 24"><path d="M3 18h18M4 12h16v6H4zM6 12V8l6-4 6 4v4"/></svg>'
  },
  {
    key: 'air',
    label: 'Air Freight',
    icon: '<svg viewBox="0 0 24 24"><path d="M21 16v-2l-8-5V3.5a1.5 1.5 0 10-3 0V9l-8 5v2l8-2.5V19l-2 1.5V22l3.5-1 3.5 1v-1.5L13 19v-5.5l8 2.5z"/></svg>'
  },
  // ...more
];
```

### 5.4 Icon Sizing

- **Small**: `16x16px` (toolbar icons)
- **Default**: `20x20px` (nav icons, buttons)
- **Medium**: `24x24px` (empty states)
- **Large**: `48x48px` (large empty states)

### 5.5 Icon Color

Icons inherit color from parent via `stroke="currentColor"`:
```css
.nav-ico svg {
  stroke: currentColor;  /* Inherits from .nav-ico color */
}
```

---

## 6. Styling Approach

### 6.1 CSS Methodology

**Approach**: Utility-first with semantic classes
**Architecture**: Inline `<style>` block in `index.html`
**No CSS Preprocessors**: Pure CSS with custom properties
**No CSS Modules**: Global scope

### 6.2 Naming Conventions

**Patterns**:
- BEM-like: `.rate-row`, `.rate-badge`, `.rate-expired-tag`
- Utility: `.on`, `.active`, `.expired`
- Semantic: `.topbar`, `.sidebar`, `.content`

**Examples**:
```css
/* Block-Element pattern */
.rate-row
.rate-modal-header
.rate-modal-carrier-logo

/* State modifiers */
.rate-row.expired
.tab.active
.viewtog button.on
```

### 6.3 Global Styles

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  outline: none;
}

body {
  font-family: var(--f-body);
  color: var(--ink);
  background: var(--page);
  font-size: 14px;
  -webkit-font-smoothing: antialiased;
}
```

### 6.4 Responsive Design

**Approach**: Flexbox-based with CSS Grid for layouts
**No Media Queries**: Single desktop view (not mobile-responsive yet)
**Fluid Layouts**: Using `flex: 1` and percentage-based widths

```css
.kpis {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}

.board {
  display: flex;
  gap: 14px;
  overflow-x: auto;  /* Horizontal scroll for kanban */
}
```

---

## 7. Project Structure

### 7.1 File Organization

```
backoffice-2.0-mvp/
├── index.html              # Main application (CRM + Rates)
├── login.html              # Login page
├── package.json            # NPM scripts
├── vercel.json            # Vercel deployment config
├── .gitignore             # Git ignore rules
├── PROJECT_SETUP.md       # Setup documentation
├── README.md              # Project readme
├── CLAUDE.md              # This design system doc
├── assets/
│   ├── oneport365-logo.png
│   └── carriers/
│       ├── msc.svg
│       ├── maersk.svg
│       ├── cma.svg
│       ├── hapag.svg
│       ├── cosco.svg
│       ├── evergreen.svg
│       ├── one.svg
│       ├── pil.svg
│       └── zim.svg
└── .vercel/
    └── project.json
```

### 7.2 Code Structure (index.html)

```html
<!DOCTYPE html>
<html>
<head>
  <!-- Fonts -->
  <!-- Styles (lines 10-290) -->
</head>
<body>
  <!-- App Structure (lines 291-337) -->
  <div class="app">
    <div class="sidebar"><!-- Nav --></div>
    <div class="main">
      <div class="topbar"><!-- Header --></div>
      <div class="tabs"><!-- Tab navigation --></div>
      <div class="content"><!-- Dynamic content --></div>
    </div>
  </div>

  <!-- Overlay for modals -->
  <div class="overlay"></div>

  <!-- JavaScript (lines 339-1240) -->
  <script>
    // Data models (lines 340-502)
    // State management (lines 502-504)
    // Helper functions (lines 505-563)
    // Modal functions (lines 565-687)
    // Render functions (lines 689-1044)
    // Event listeners (lines 1046-1240)
  </script>
</body>
</html>
```

### 7.3 Feature Organization

**Sections**:
1. **CRM** (default section)
   - Pipeline (Kanban board)
   - Companies
   - Contacts
   - Team

2. **Rates** (freight rates module)
   - Ocean Freight
   - Air Freight
   - Export Haulage
   - Import Haulage
   - Other Charges

**Section Switching**:
```javascript
function switchSection(section){
  activeSection = section;
  if(section === 'rates'){
    $('.topbar h2').textContent = 'Rates';
    $('#tabs').style.display = 'none';
    renderRates();
  } else {
    $('.topbar h2').textContent = 'CRM';
    $('#tabs').style.display = 'flex';
    render();
  }
}
```

---

## 8. Special Patterns

### 8.1 Customer Tier System

**Three Tiers**:
- **Spot/SME**: `--tier-spot-bg` / `--tier-spot-tx`
- **Mid-Tier**: `--tier-mid-bg` / `--tier-mid-tx`
- **Enterprise**: `--tier-ent-bg` / `--tier-ent-tx`

```javascript
// Tier badge helper
function clsKey(c) {
  return c === 'Enterprise' ? 'ent' : c === 'Mid-Tier' ? 'mid' : 'spot';
}

// Usage
const tierKey = clsKey(company.cls);
html += `<span class="tier-badge tier-${tierKey}">${company.cls}</span>`;
```

### 8.2 Carrier Branding

**Pattern**: Branded background colors for known carriers

```javascript
function carrierClass(name){
  const n = name.toLowerCase();
  if(n.includes('msc')) return 'msc';
  if(n.includes('maersk')) return 'maersk';
  if(n.includes('cma')) return 'cma';
  // ...etc
  return '';
}

// CSS for each carrier
.carrier-logo.msc { background: #003D6B; color: #fff; }
.carrier-logo.maersk { background: #42B0D5; color: #fff; }
// ...etc
```

### 8.3 Date Formatting

```javascript
// Expiry date display with color coding
function formatExpiry(dateStr){
  const exp = new Date(dateStr);
  const days = Math.ceil((exp - today) / (1000*60*60*24));

  if(isExpired) return `<span style="color:var(--error)">Expired</span>`;
  if(days <= 14) return `<span class="expiry-soon">${days} days</span>`;
  return `<span class="expiry-normal">${exp.toLocaleDateString()}</span>`;
}
```

### 8.4 Currency Formatting

```javascript
function formatAmount(amt, type){
  if(type === 'air') return `$${amt.toFixed(2)}/kg`;
  if(type === 'haulage-export' || type === 'haulage-import' || type === 'other') {
    return `₦${amt.toLocaleString()}`;
  }
  return `$${amt.toLocaleString()}`;
}
```

---

## 9. State Management

### 9.1 Application State

```javascript
// Global state variables (lines 502-503)
let activeTab = 'pipeline';      // CRM tab
let pipeView = 'board';          // board or list
let activeSection = 'rates';     // crm or rates
let rateType = 'ocean';          // ocean, air, haulage-export, etc.
let seq = 100;                   // Deal sequence number

// Rates filters
let rateSearch = '';
let rateCarrier = '';
let rateRateType = '';
```

### 9.2 Data Models

**Defined as arrays of objects**:
- `users` - User accounts
- `companies` - Company database
- `contacts` - Contact database
- `deals` - Pipeline deals
- `rates` - Freight rates

---

## 10. Integration Guidelines

### 10.1 Adding New Components

**Pattern**:
1. Define CSS in the `<style>` block
2. Create render function that returns HTML string
3. Add to appropriate section render function
4. Update state variables if needed

### 10.2 Adding New Sections

**Pattern**:
1. Add navigation icon to `.sidebar`
2. Create `render[SectionName]()` function
3. Update `switchSection()` function
4. Add data model if needed

### 10.3 Color Usage Rules

**Primary Actions**: Use `--lime` background with `--green` text
**Destructive Actions**: Use `--error` color
**Success States**: Use `--success` color
**Money/Financial**: Use `--gold` color
**Backgrounds**: Use `--page` for main, `--panel` for cards
**Borders**: Use `--line` (light) or `--line-2` (medium)
**Text**: Use `--ink` (primary), `--muted` (secondary), `--muted-2` (tertiary)

### 10.4 Typography Scale

```css
/* Headings */
h1 { font-size: 24-26px; font-weight: 600-700; }
h2 { font-size: 20px; font-weight: 600; }
h3 { font-size: 16-18px; font-weight: 600; }

/* Body */
body { font-size: 14px; }  /* Default */
small, .small { font-size: 12-13px; }
.tiny { font-size: 11px; }

/* Large values */
.kpi .val { font-size: 32px; font-weight: 700; }
```

---

## 11. Deployment

### 11.1 Static Hosting

**Platforms**:
- Vercel (configured via `vercel.json`)
- Netlify
- GitHub Pages
- Any static file host

### 11.2 Build Process

**None required** - Deploy `index.html` and `/assets/` directly

### 11.3 Vercel Configuration

```json
{
  "version": 2,
  "builds": [
    {
      "src": "*.html",
      "use": "@vercel/static"
    }
  ]
}
```

---

## 12. Browser Support

**Target**: Modern browsers (Chrome, Firefox, Safari, Edge)
**ES6+ Features**: Arrow functions, template literals, destructuring, spread operator
**CSS Features**: Custom properties, flexbox, grid, border-radius
**APIs**: Drag and Drop API (for kanban board)

---

## 13. Performance Notes

- **No bundling**: Single HTML file loads instantly
- **Inline styles**: No external CSS requests
- **Inline scripts**: No external JS requests
- **Local assets**: Logo and carrier icons served locally
- **Font loading**: Uses `font-display: swap` for performance

---

## 14. Future Considerations

### 14.1 Planned Improvements
- Convert to component-based architecture (React/Vue)
- Add backend API integration
- Implement authentication system
- Add mobile responsive design
- Separate CSS and JS into external files
- Add build process with bundler

### 14.2 Component Library Migration
When migrating to a framework:
- Extract CSS custom properties to design tokens file
- Convert inline styles to styled-components or CSS modules
- Create reusable component library
- Implement proper state management (Redux/Vuex)

---

**End of Design System Documentation**
