# Life Calendar Wallpaper

Dynamic wallpaper generator that tracks your year progress, life progress, or goal countdown.

## Features

- **Year Progress**: Visual grid showing days/weeks completed in the current year
- **Life Calendar**: Weeks of your life visualized as a dot grid
- **Goal Countdown**: Circular progress countdown to your target date
- **Timezone-aware**: Automatically handles DST and timezone differences
- **Customizable**: Choose colors, device sizes, and calendar types

## Project Structure

```
apple-wallpaper/
├── index.html          # Frontend website
├── styles.css          # Premium dark theme styling
├── app.js              # Frontend logic
├── data/
│   ├── countries.js    # Country-timezone mappings
│   └── devices.js      # Device resolution presets
└── worker/
    ├── wrangler.toml   # Cloudflare Worker config
    ├── package.json    # Dependencies
    └── src/
        ├── index.js    # Main entry point
        ├── timezone.js # Timezone utilities
        ├── svg.js      # SVG generation helpers
        └── generators/
            ├── year.js # Year calendar generator
            ├── life.js # Life calendar generator
            └── goal.js # Goal countdown generator
```

## Setup

### Frontend (Development)

Open `index.html` in a browser:

```bash
open index.html
# or use Live Server in VS Code
```

### Backend (Cloudflare Worker)

1. Install dependencies:
```bash
cd worker
npm install
```

2. Run locally:
```bash
npx wrangler dev
```

3. Deploy:
```bash
npx wrangler deploy
```

4. Update `WORKER_URL` in `app.js` with your deployed worker URL.

## URL Parameters

| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `country` | Yes | - | ISO 2-letter code (e.g., `us`, `in`) |
| `type` | Yes | - | `year`, `life`, or `goal` |
| `bg` | No | `111114` | Background color (hex) |
| `accent` | No | `FFD700` | Accent color (hex) |
| `width` | No | `1179` | Image width in pixels |
| `height` | No | `2556` | Image height in pixels |
| `dob` | For life | - | Date of birth (YYYY-MM-DD) |
| `lifespan` | No | `80` | Expected lifespan in years |
| `goal` | For goal | - | Target date (YYYY-MM-DD) |
| `goalName` | No | `Goal` | Name of your goal |
| `format` | No | `png` | Output format (`png` or `svg`) |

## Example URLs

**Year Progress (India, Gold accent)**
```
/generate?country=in&type=year&bg=111114&accent=FFD700&width=1179&height=2556
```

**Life Calendar (USA, Born 1990)**
```
/generate?country=us&type=life&dob=1990-05-15&lifespan=85&bg=0f0f23&accent=00D9FF
```

**Goal Countdown (UK, Wedding)**
```
/generate?country=gb&type=goal&goal=2026-06-15&goalName=Wedding%20Day&accent=FF6B6B
```

## iOS Shortcut Setup

1. Open **Shortcuts** app
2. Create new shortcut:
   - Add "Get Contents of URL" → paste your wallpaper URL
   - Add "Set Wallpaper" → choose Lock Screen
3. Set up Automation to run daily at 6:00 AM

## License

MIT
