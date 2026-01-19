# Address Sketch Tool - PWA Setup Guide

## Quick Start

```bash
# 1. Generate icons
open ~/address-sketch/generate-icons.html
# Click the button and move downloaded icons to the icons/ folder

# 2. Test locally (requires a local server for PWA features)
cd ~/address-sketch
python3 -m http.server 8000
# Open http://localhost:8000
```

## Files Structure

```
address-sketch/
├── index.html           # Main PWA app
├── manifest.json        # PWA manifest
├── sw.js               # Service worker (offline support)
├── generate-icons.html  # Icon generator tool
├── SETUP.md            # This guide
└── icons/
    ├── icon.svg        # Vector icon
    ├── icon-72.png     # Generated icons
    ├── icon-96.png
    ├── icon-128.png
    ├── icon-144.png
    ├── icon-152.png
    ├── icon-180.png    # iOS
    ├── icon-192.png
    ├── icon-384.png
    └── icon-512.png
```

## Step 1: Generate Icons

1. Open `generate-icons.html` in your browser
2. Click "Generate & Download Icons"
3. Move all downloaded PNG files to the `icons/` folder

## Step 2: Deploy to GitHub Pages

```bash
cd ~/address-sketch
git init
git add .
git commit -m "Initial commit - Address Sketch PWA"
git branch -M main

# Create repo at github.com/new, then:
git remote add origin https://github.com/YOUR_USERNAME/address-sketch.git
git push -u origin main
```

**Enable GitHub Pages:**
1. Go to repo Settings → Pages
2. Source: Deploy from branch
3. Branch: main / root
4. Save

Your PWA will be live at: `https://YOUR_USERNAME.github.io/address-sketch/`

## Step 3: Setup Google AdSense

### Apply for AdSense
1. Go to https://adsense.google.com
2. Sign up with your Google account
3. Add your GitHub Pages URL
4. Wait for approval (1-2 weeks)

### After Approval
1. Get your Publisher ID from AdSense dashboard (format: `ca-pub-XXXXXXXXXXXXXXXX`)
2. Create ad units in AdSense:
   - Display ads (responsive)
   - Sidebar ads (160x600)

### Update Code
In `index.html`, replace:
- `ca-pub-XXXXXXXXXXXXXXXX` → Your Publisher ID
- `data-ad-slot="XXXXXXXXXX"` → Your ad slot IDs

```bash
git add .
git commit -m "Add AdSense codes"
git push
```

## PWA Features

| Feature | Description |
|---------|-------------|
| Installable | Users can install on home screen |
| Offline | Works without internet |
| Responsive | Optimized for mobile, iPad, desktop |
| Touch optimized | Smooth drawing on touch devices |
| Auto-save | Sketch saved to localStorage |
| High DPI | Crisp on retina displays |

## Mobile/iPad Optimization

The app includes:
- `touch-action: none` - Prevents scrolling while drawing
- High DPI canvas - Sharp on retina displays
- `passive: false` touch events - Smooth drawing
- Responsive toolbar - Adapts to screen size
- iOS safe area support - Works with notch

## Testing PWA Locally

PWA features (install, offline) require HTTPS or localhost:

```bash
# Python
python3 -m http.server 8000

# Node.js
npx serve .

# Then open http://localhost:8000
```

## Troubleshooting

### Icons not showing
- Make sure all PNGs are in `icons/` folder
- Check browser console for 404 errors

### PWA not installable
- Must be served over HTTPS (GitHub Pages provides this)
- Check manifest.json is loading (DevTools → Application → Manifest)

### Drawing lag on iPad
- Clear browser cache
- Close other tabs
- The app uses `desynchronized: true` for best performance

## Revenue Tips

### Increase Traffic
- Share on social media
- Post in relevant forums
- Create YouTube tutorials
- Submit to web app directories

### AdSense Best Practices
- Don't click your own ads
- Keep ad density reasonable
- Don't place ads that interfere with drawing

### Expected Revenue
| Monthly Views | Estimated Revenue |
|---------------|-------------------|
| 1,000 | $1-5 |
| 10,000 | $10-50 |
| 100,000 | $100-500 |

*Varies by geography and user engagement*
