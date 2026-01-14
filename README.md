# LifeGrid

> Time, visualized.

Dynamic wallpapers that track your year, life, and goals. Updated daily, automatically.

![LifeGrid](https://via.placeholder.com/800x400/000000/FFFFFF?text=LifeGrid)

## ✨ Features

- **Year Progress** – See every day of the year as a grid
- **Life Calendar** – Every week of your life as a dot
- **Goal Countdown** – Count down to what matters
- **Timezone-aware** – Handles DST automatically
- **Customizable** – Black/white theme with accent colors

## 📁 Project Structure

```
lifegrid/
├── index.html          # Frontend (Apple-inspired dark theme)
├── styles.css          # Black & white aesthetic with ruler borders
├── app.js              # Card selection, preview, URL generation
├── data/
│   ├── countries.js    # 65+ countries with timezones
│   └── devices.js      # Device resolution presets
└── worker/
    ├── wrangler.toml   # Cloudflare Worker config
    ├── package.json    # Dependencies (resvg-wasm)
    └── src/
        ├── index.js    # Main entry point
        ├── timezone.js # Timezone utilities
        ├── svg.js      # SVG generation helpers
        └── generators/
            ├── year.js # Year progress calendar
            ├── life.js # Life calendar (dots)
            └── goal.js # Goal countdown (circle)
```

## 🚀 Quick Start

### Frontend
```bash
# Just open in browser
open index.html
```

### Backend
```bash
cd worker
npm install
npx wrangler dev      # Local development
npx wrangler deploy   # Deploy to Cloudflare
```

After deploying, update `WORKER_URL` in `app.js`.

## 🔗 API Reference

```
GET /generate?country=us&type=year&bg=000000&accent=FFFFFF&width=1179&height=2556
```

| Param | Description |
|-------|-------------|
| `country` | ISO 2-letter code (`us`, `in`, `gb`) |
| `type` | `year`, `life`, or `goal` |
| `bg` | Background color (hex without #) |
| `accent` | Accent color (hex without #) |
| `width` | Image width in pixels |
| `height` | Image height in pixels |
| `dob` | Date of birth for life calendar |
| `lifespan` | Expected years (default: 80) |
| `goal` | Target date for countdown |
| `goalName` | Name of your goal |

## 📱 iOS Shortcut

1. Copy your generated URL
2. Open **Shortcuts** app
3. New Shortcut:
   - `Get Contents of URL` → paste URL
   - `Set Wallpaper` → Lock Screen
4. Automate to run daily at 6 AM

---

Made with ❤️ for mindful living
