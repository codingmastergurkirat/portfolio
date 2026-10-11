# Portfolio — Setup & Architecture Guide

Welcome to your redesigned, **200% impressive** personal portfolio website!

## ✨ New Aesthetic Highlights

1. **Typography**: Google Font **Anta** (`font-family: 'Anta', sans-serif`) with **Noto Sans Gurmukhi** for Punjabi script.
2. **Color Palette**: Electric Yellow (`#ffe600`), Crisp White (`#ffffff`), and Deep Matte Black (`#050505`, `#0e0e11`).
3. **Curved Architecture**: Curved cards (`rounded-3xl` / `32px`), pill badges (`9999px`), and organic glassmorphism containers.
4. **Welcome / Loading Screen**:
   - Sacred **Ik Onkar (ੴ)** glowing medallion with orbital ring.
   - Traditional greeting in Gurmukhi script: **ਸਤਿ ਸ੍ਰੀ ਅਕਾਲ** (Sat Shri Akal).
   - Smooth morphing transition to **WELCOME** in Anta font.
   - Graceful cubic-bezier upward curtain unveil + Skip Intro button.
5. **Project Popup Modals**:
   - Clicking any project thumbnail triggers an instant on-screen popup modal.
   - Includes cross (`✕`) close icon on top right, clean visual banner, concise summary, key highlights, tech pills, Live Demo link, and GitHub Code link.
   - Fits on screen comfortably without scrolling; closes via `✕`, backdrop click, or `Escape` key.
6. **Aesthetic Floating Island Dock**:
   - Replaces the old fixed left sidebar.
   - Floats at the bottom center with curved glassmorphism pill shape, magnetic hover animations, and tooltip labels (GitHub, LinkedIn, X, LeetCode, Email, Back-to-Top).
7. **Direct Actions**:
   - **Contact Button**: Direct `mailto:gurkiratjap@gmail.com` trigger.
   - **Copy Email**: One-click copy with toast pill notification.
   - **Show My Resume**: Opens a dedicated curved Resume Modal with option to Print / Save as PDF.
8. **Lag-Free Corner Scroll Animations**:
   - Lightweight `IntersectionObserver` animating elements from corner angles (`.reveal-corner-left`, `.reveal-corner-right`, `.reveal-up`).

---

## 🎨 Customizing Design Tokens

All colors, radiuses, and fonts can be tuned in `:root` inside `index.html`:

```css
:root {
  --bg-deep: #050505;
  --bg-surface: #0e0e11;
  --yellow: #ffe600;
  --yellow-glow: rgba(255, 230, 0, 0.35);
  --white: #ffffff;
  --font-anta: 'Anta', sans-serif;
  --radius-lg: 32px;
  --radius-pill: 9999px;
}
```

---

## 🚀 Deployment

The site is a standalone static web application (`index.html` + `profile.jpeg`). It is 100% ready to deploy to Vercel, Netlify, or GitHub Pages without build steps.
