# ImmoScout24 Design-System - Basis-Prompt

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
            --color-success: #00D9B1;  /* Grün */
            --color-warning: #F2CA26;  /* Gelb */
            --color-danger: #E74B3C;   /* Rot */
            
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

### Basis-Card (Weiß)
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
```css
.card-primary {
    background-color: var(--color-teal);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
}

.card-highlight {
    background-color: var(--color-yellow);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
}

.card-accent {
    background-color: var(--color-orange);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
}

.card-info {
    background-color: var(--color-blue);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
}

.card-premium {
    background-color: var(--color-purple);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 30px;
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
Farbige Cards (Teal, Yellow, Orange, Blue, Purple):
  → border: none

Weiße/Sand Cards:
  → border: 2px solid var(--color-gray-medium)

NIEMALS farbige Borders
```

### 3. border-radius IMMER
```
ALLE Cards, Buttons, Badges: border-radius: 8px (oder 4px bei Badges)
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
            borderColor: chartColors.green600,  // ✅ Chart-Farbe
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
Card enthält Ampel-Labels (↑/→/↓)?
  → Card MUSS weiß oder Sand sein
  → MIT Border (2px solid gray-medium)
  → MIT border-radius (8px)

Card ohne Labels:
  → Kann farbig sein
  → OHNE Border
  → MIT border-radius (8px)
```

---

## Buttons

```css
.btn-primary {
    background-color: var(--color-teal);
    color: var(--color-charcoal);
    border: none;
    border-radius: 8px;
    padding: 12px 24px;
    font-weight: 600;
}

.btn-secondary {
    background-color: var(--color-white);
    color: var(--color-teal);
    border: 2px solid var(--color-teal);
    border-radius: 8px;
    padding: 12px 24px;
}
```

---

## Häufige Fehler (Top 10)

1. ❌ Weiße Schrift auf Brand-Farben → ✅ Immer Charcoal (#333)
2. ❌ box-shadow verwenden → ✅ border (nur weiße Cards)
3. ❌ Eckige Ecken (border-radius: 0) → ✅ border-radius: 8px
4. ❌ Border auf farbigen Cards → ✅ border: none
5. ❌ Gradients (linear-gradient) → ✅ Solid Colors
6. ❌ Brand-Farben in Charts → ✅ chartColors verwenden
7. ❌ Ampel-Labels auf farbigen Cards → ✅ Labels nur auf Weiß/Sand
8. ❌ ↑ mit Rot, ↓ mit Grün → ✅ ↑=Grün, ↓=Rot, →=Gelb
9. ❌ Card-Padding <30px → ✅ Minimum 30px
10. ❌ Farbige Borders → ✅ Nur gray-medium bei weißen Cards

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
- [ ] KEINE box-shadow
- [ ] KEINE Gradients (linear/radial)
- [ ] Charts: chartColors (NICHT Brand-Farben)
- [ ] Ampel-Labels (↑/→/↓): nur auf Weiß/Sand
- [ ] Ampel-Logik: ↑=Grün, →=Gelb, ↓=Rot
- [ ] Cards mit Ampel-Labels: weiß + border
- [ ] Cards ohne Labels: farbig erlaubt
- [ ] Minimum 30px Card-Padding

---

## Support

Bei Fragen zur Implementierung kontaktiere das Creative Studio Team.
