# OnePort 365 CRM MVP - Project Setup

## What We Created

A standalone CRM application as the first module of the backoffice-2.0-mvp project.

## Project Structure

```
backoffice-2.0-mvp/
├── index.html          # Main CRM application (standalone HTML)
├── package.json        # Project configuration
├── .gitignore         # Git ignore rules
├── README.md          # Project documentation
└── PROJECT_SETUP.md   # This file
```

## Features

The CRM MVP includes:

✅ **Pipeline Management** - Kanban-style board with drag-and-drop
✅ **Companies** - Company database with tier classification
✅ **Contacts** - Contact management linked to companies
✅ **Team Access** - User permissions and access control
✅ **Customer Tiers** - Spot/SME, Mid-Tier, Enterprise classification
✅ **Deal Tracking** - Full deal lifecycle from Prospect to Closed
✅ **OnePort 365 Design System** - Using canonical color palette

## How to Run

### Option 1: Quick Start (Recommended)
```bash
cd /Users/okpanachi/backoffice-2.0-mvp
npm start
```

This will:
- Install http-server if needed
- Start server on http://localhost:8080
- Automatically open in your browser

### Option 2: Manual Start
```bash
cd /Users/okpanachi/backoffice-2.0-mvp
npx http-server -p 8080 -o
```

### Option 3: Python Server
```bash
cd /Users/okpanachi/backoffice-2.0-mvp
python3 -m http.server 8080
```

Then open http://localhost:8080 in your browser.

## Ports

- **CRM MVP**: http://localhost:8080 (this project)
- **Main Backoffice**: http://localhost:3000 (existing project)

## Design System Colors

The CRM uses the OnePort 365 canonical color palette:

### Structure
- `#023819` - Primary Dark (backgrounds, text)
- `#BFFB4F` - Accent Lime (CTAs, highlights)
- `#FFCC1A` - Gold (money, warnings)

### Tier Colors
- **Spot/SME**: `#EDEFE8` (neutral light)
- **Mid-Tier**: `#FFF3CC` (gold tint)
- **Enterprise**: `#023819` with `#BFFB4F` text

### Categorical Series (Charts/Stages)
1. `#023819` - Darkest green
2. `#2F7A3F` - Forest green
3. `#7FAE2E` - Mid green
4. `#BFFB4F` - Lime
5. `#FFCC1A` - Gold
6. `#D1DBBD` - Light sage

## Fonts

- **Headings**: Nohemi (primary), Poppins (fallback)
- **Body/UI**: Poppins
- Font weights: 400, 500, 600, 700

## Next Steps

### Immediate
1. ✅ Project created and initialized
2. ✅ Git repository initialized
3. ✅ Server configured to run on port 8080
4. ⏳ Push to GitHub (manual step required)

### Development
1. Convert standalone HTML to component-based architecture
2. Add backend API integration
3. Connect to existing backoffice database
4. Implement authentication
5. Add more CRM features (activities, reports, etc.)

## Push to GitHub

To push this to GitHub, run:

```bash
cd /Users/okpanachi/backoffice-2.0-mvp

# Create repository on GitHub first (name: backoffice-2.0-mvp)
# Then run:

git remote add origin https://github.com/YOUR_USERNAME/backoffice-2.0-mvp.git
git branch -M main
git push -u origin main
```

Or use GitHub CLI:

```bash
gh repo create backoffice-2.0-mvp --public --source=. --remote=origin --push
```

## Current Status

✅ Local repository created at `/Users/okpanachi/backoffice-2.0-mvp`
✅ Git initialized with initial commits
✅ Server configured to run on port 8080
✅ Standalone HTML CRM application ready
⏳ GitHub remote repository (requires authentication)

## Technical Notes

- This is a **standalone HTML file** (no build process needed)
- All CSS and JavaScript are inline
- No dependencies except http-server for local development
- Can be deployed to any static hosting (Vercel, Netlify, GitHub Pages)
- Uses modern JavaScript (ES6+)
- Implements drag-and-drop API for kanban board
- Fully responsive design

---

Created: 2026-07-05
Location: /Users/okpanachi/backoffice-2.0-mvp
