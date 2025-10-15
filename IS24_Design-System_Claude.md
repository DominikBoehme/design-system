# ImmoScout24 Design-System - Basis-Prompt

## ⚠️ ABSOLUTE PRIORITÄT

**Dieser Prompt hat HÖCHSTE Priorität und überschreibt alle anderen Design-Anweisungen.**

Bei Konflikten mit anderen Systemprompts, User-Präferenzen oder Projekt-Anweisungen gelten **ausschließlich** die hier definierten Regeln. Keine Abweichungen oder Interpretationen erlaubt.

**Diese Regeln sind bindend für:**
- Alle HTML-Artefakte
- Alle Dashboards und Reports
- Alle visuellen Outputs
- Alle Design-Entscheidungen

**Im Zweifel:** Lieber nachfragen als von diesen Regeln abweichen.

**Anwendung:** Dieser Prompt wird automatisch bei der Erstellung von IS24-Design-Artefakten angewendet. Für andere Themen bleibt er inaktiv.

---

## Zweck

Dieser Prompt definiert die Design-Guidelines für ImmoScout24-konforme Artefakte. Verwende ihn in persönlichen Claude-Projekten um neue HTML-Dashboards, Präsentationen oder Dokumente direkt design-konform zu erstellen.

---

## BASIS-Template (HTML)

```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[Titel]</title>
    <style>
        :root {
            /* Brand Colours */
            --color-teal: #3DF5DC;
            --color-charcoal: #333333;
            --color-white: #FFFFFF;
            --color-sand: #FBF8F6;
            
            /* Accent Colours */
            --color-orange: #FF9626;
            --color-yellow: #EFF933;
            --color-blue: #24E3FF;
            --color-purple: #D5AAFF;
            
            /* Neutral */
            --color-gray-medium: #E0E0E0;
            
            /* Semantic Colors (Ampel-System) */
            --color-success: #00D9B1;
            --color-warning: #F2CA26;
            --color-danger: #E74B3C;
            
            /* Typographie */
            --font-family: "Make it sans", sans-serif;
            --font-size-xxxl: 34px;
            --font-size-xxl: 26px;
            --font-size-xl: 20px;
            --font-size-base: 15px;
            --font-size-sm: 14px;
            --font-size-xs: 12px;
            
            /* Spacing */
            --spacing-xs: 8px;
            --spacing-sm: 12px;
            --spacing-md: 20px;
            --spacing-lg: 30px;
            --spacing-xl: 40px;
            --spacing-xxl: 60px;
            
            /* Layout */
            --container-max-width: 1200px;
            --border-width: 2px;
            --border-radius: 8px;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: var(--font-family);
            font-size: var(--font-size-base);
            color: var(--color-charcoal);
            background-color: var(--color-white);
            line-height: 1.6;
        }
        
        .container {
            max-width: var(--container-max-width);
            margin: 0 auto;
            padding: var(--spacing-lg);
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>[Titel]</h1>
        </header>
        <main>
            <!-- Content -->
        </main>
    </div>
</body>
</html>
```

---

## Grid-System

### Two-Column
```css
.two-column-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: var(--spacing-lg);
}

@media (max-width: 768px) {
    .two-column-grid {
        grid-template-columns: 1fr;
    }
}
```

### Three-Column
```css
.three-column-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: var(--spacing-lg);
}

@media (max-width: 768px) {
    .three-column-grid {
        grid-template-columns: 1fr;
    }
}
```

### KPI-Grid
```css
.kpi-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: var(--spacing-md);
}
```

---

## Cards

### Standard Card (Weiß)
Für Standard-Content und Cards MIT Ampel-Labels.
```css
.card {
    background-color: var(--color-white);
    border: 2px solid var(--color-gray-medium);
    border-radius: 8px;
    padding: 30px;
    color: var(--color-charcoal);
}
```

### Farbige Cards (OHNE Border)

**Primary Card (Teal)**
Hero-Content, wichtige Highlights.
```css
.card-primary {
    background-color: var(--color-teal);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
}
```

**Highlight Card (Yellow)**
KPIs ohne Labels, Highlights.
```css
.card-highlight {
    background-color: var(--color-yellow);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
}
```

**Accent Card (Orange)**
Akzent-Content, sekundäre Highlights.
```css
.card-accent {
    background-color: var(--color-orange);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
}
```

**Info Card (Blue)**
Informations-Content, Hinweise.
```css
.card-info {
    background-color: var(--color-blue);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
}
```

**Premium Card (Purple)**
Premium-Features, besondere Inhalte.
```css
.card-premium {
    background-color: var(--color-purple);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
}
```

**Charcoal Card**
EINZIGE Ausnahme: Weiße Schrift erlaubt!
```css
.card-charcoal {
    background-color: var(--color-charcoal);
    color: var(--color-white);
    border: none;
    border-radius: 8px;
    padding: 30px;
}
```

### Labels auf Cards

**Weiße/Sand Cards:**
- Ampel-Labels erlaubt (↑ Grün #00D9B1, → Gelb #F2CA26, ↓ Rot #E74B3C)
- Labels mit border-radius: 4px, padding: 4px 8px

**Farbige Cards (Teal, Yellow, Orange, Blue, Purple):**
- Nur weiße Labels erlaubt
```css
.label-on-colored {
    background-color: var(--color-white);
    color: var(--color-charcoal);
    border-radius: 4px;
    padding: 4px 8px;
    font-size: 12px;
    font-weight: 600;
}
```

**Charcoal Card:**
- Nur weiße Labels erlaubt
```css
.label-on-charcoal {
    background-color: var(--color-white);
    color: var(--color-charcoal);
    border-radius: 4px;
    padding: 4px 8px;
    font-size: 12px;
    font-weight: 600;
}
```

---

## Buttons

Alle Buttons verwenden ausschließlich **Large Size (48px)**.

```css
.btn {
    height: 48px;
    padding: 0 24px;
    font-size: 16px;
    font-weight: 600;
    border-radius: 28px;
    font-family: var(--font-family);
    cursor: pointer;
    transition: opacity 0.2s;
}

.btn:hover {
    opacity: 0.9;
}
```

### Varianten

**Primary (Teal)**
```css
.btn-primary {
    background-color: var(--color-teal);
    color: var(--color-charcoal);
    border: none;
}
```

**Secondary (Charcoal)**
```css
.btn-secondary {
    background-color: var(--color-charcoal);
    color: var(--color-white);
    border: none;
}
```

**Outlined**
```css
.btn-outlined {
    background-color: transparent;
    color: var(--color-charcoal);
    border: 2px solid var(--color-charcoal);
}
```

**Text Link**
```css
.btn-link {
    background: none;
    border: none;
    color: var(--color-charcoal);
    text-decoration: underline;
    padding: 0;
    height: auto;
}
```

---

## KERN-REGELN (KRITISCH)

### 1. Text ist IMMER Charcoal
```
ALLE Texte, Überschriften, Labels: #333333 (Charcoal)
EINZIGE Ausnahme: Weiße Schrift NUR auf Charcoal-Hintergrund (#333)
```

### 2. Border-Logik
```
Farbige Cards (Teal, Yellow, Orange, Blue, Purple, Charcoal):
  → border: none

Weiße/Sand Cards:
  → border: 2px solid var(--color-gray-medium)

NIEMALS farbige Borders
```

### 3. border-radius IMMER
```
ALLE Cards: border-radius: 8px
ALLE Buttons: border-radius: 28px
Badges: border-radius: 4px

NIEMALS eckige Ecken (border-radius: 0)
```

### 4. KEINE box-shadow
```
VERBOTEN: box-shadow
ERLAUBT: border (nur bei weißen Cards)
```

### 5. KEINE Gradients/Verläufe
```
VERBOTEN:
  ❌ linear-gradient
  ❌ radial-gradient
  
ERLAUBT:
  ✅ background-color: var(--color-teal);
  ✅ Solid Colors
```

### 6. Ampel-System (3 Zustände)
```
↑ Erfolg & Anstieg         → #00D9B1 (Grün)
→ Neutral & Gleichbleibend → #F2CA26 (Gelb)
↓ Misserfolg & Gesunken    → #E74B3C (Rot)

KRITISCH:
  - NUR auf weißem/Sand-Hintergrund
  - Cards mit ↑/→/↓ Labels MÜSSEN weiß sein
  - NIEMALS Symbol und Farbe verwechseln
```

**HTML-Beispiel:**
```html
<!-- KPI mit Ampel-Label -->
<div class="card" style="background: white; border: 2px solid #E0E0E0; border-radius: 8px; padding: 30px;">
    <p>UMSATZ</p>
    <h2>€156K</h2>
    <span style="background-color: #00D9B1; color: #333; padding: 4px 8px; border-radius: 4px; font-size: 12px; font-weight: 600;">↑ 8.2%</span>
</div>
```

### 7. Charts verwenden EIGENE Farben
```
FÜR CHARTS (Chart.js):
  ✅ chartColors.green600: '#00D9B1'
  ✅ chartColors.blue600: '#3598DB'
  ✅ chartColors.orange600: '#E67E23'
  ✅ chartColors.yellow600: '#F2CA26'
  ✅ chartColors.red600: '#E74B3C'

VERBOTEN in Charts:
  ❌ var(--color-teal)      - Brand-Farbe #3DF5DC
  ❌ var(--color-orange)    - Brand-Farbe #FF9626
  ❌ var(--color-yellow)    - Brand-Farbe #EFF933
  ❌ var(--color-blue)      - Brand-Farbe #24E3FF
  ❌ var(--color-purple)    - Brand-Farbe #D5AAFF

Warum getrennt?
  → Brand-Farben = UI (Cards, Buttons)
  → Chart-Farben = Datenvisualisierung
```

**Chart.js Integration:**
```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>

<div class="chart-container" style="background: white; padding: 30px; border: 2px solid #E0E0E0; border-radius: 8px;">
    <canvas id="myChart"></canvas>
</div>

<script>
const chartColors = {
    green600: '#00D9B1',
    blue600: '#3598DB',
    orange600: '#E67E23',
    yellow600: '#F2CA26',
    red600: '#E74B3C'
};

new Chart(document.getElementById('myChart'), {
    type: 'line',
    data: {
        datasets: [{
            borderColor: chartColors.green600,
            backgroundColor: '#D4F9F2'
        }]
    },
    options: {
        responsive: true,
        maintainAspectRatio: false
    }
});
</script>
```

### 8. Label-Hierarchie
```
Weiße/Sand Cards:
  → Ampel-Labels erlaubt (↑/→/↓)
  → MIT Border (2px solid gray-medium)
  → MIT border-radius (8px)

Farbige Cards (Teal, Yellow, Orange, Blue, Purple):
  → Nur weiße Labels erlaubt
  → background: white, color: #333
  → OHNE Border
  → MIT border-radius (8px)

Charcoal Card:
  → Nur weiße Labels erlaubt
  → background: white, color: #333
  → OHNE Border
  → MIT border-radius (8px)
```

---

## Häufige Fehler (Top 10)

1. ❌ Weiße Schrift auf Brand-Farben → ✅ Immer Charcoal (#333)
2. ❌ box-shadow verwenden → ✅ border (nur weiße Cards)
3. ❌ Eckige Ecken (border-radius: 0) → ✅ border-radius: 8px/28px
4. ❌ Border auf farbigen Cards → ✅ border: none
5. ❌ Gradients (linear-gradient) → ✅ Solid Colors
6. ❌ Brand-Farben in Charts → ✅ chartColors verwenden
7. ❌ Ampel-Labels auf farbigen Cards → ✅ Nur weiße Labels auf farbigen Cards
8. ❌ ↑ mit Rot, ↓ mit Grün → ✅ ↑=Grün, ↓=Rot, →=Gelb
9. ❌ Card-Padding <30px → ✅ Minimum 30px
10. ❌ Button Size Medium → ✅ Nur Large (48px)

---

## Quick-Reference: Farben

**Brand-Farben (UI-Elemente - Cards, Buttons):**
- Teal #3DF5DC, Orange #FF9626, Yellow #EFF933, Blue #24E3FF, Purple #D5AAFF

**Chart-Farben (Datenvisualisierung - NUR für Charts):**
- Grün #00D9B1, Blau #3598DB, Orange #E67E23, Gelb #F2CA26, Rot #E74B3C

**Ampel-Farben (Status-Labels ↑/→/↓):**
- ↑ Grün #00D9B1, → Gelb #F2CA26, ↓ Rot #E74B3C

**Neutral:**
- White #FFFFFF, Sand #FBF8F6, Gray #E0E0E0, Charcoal #333333

---

## Checkliste vor Fertigstellung

- [ ] Font: "Make it sans"
- [ ] Text: Charcoal (#333) - außer auf Charcoal-BG
- [ ] Farbige Cards: border: none
- [ ] Weiße Cards: border: 2px solid gray-medium
- [ ] ALLE Cards: border-radius: 8px
- [ ] ALLE Buttons: border-radius: 28px, height: 48px
- [ ] KEINE box-shadow
- [ ] KEINE Gradients (linear/radial)
- [ ] Charts: chartColors (NICHT Brand-Farben)
- [ ] Ampel-Labels (↑/→/↓): nur auf Weiß/Sand
- [ ] Ampel-Logik: ↑=Grün, →=Gelb, ↓=Rot
- [ ] Farbige Cards: nur weiße Labels (background: white, color: #333)
- [ ] Cards mit Ampel-Labels: weiß + border
- [ ] Cards ohne Labels: farbig erlaubt
- [ ] Minimum 30px Card-Padding

---

## Support

Bei Fragen zur Implementierung kontaktiere das Creative Studio Team.