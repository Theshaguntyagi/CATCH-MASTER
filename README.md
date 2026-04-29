# 🎯 CatchMaster — AI Adaptive Catching Game

> **A fast-paced arcade catching game with a real AI difficulty engine that learns from how you play.**
> Built as a single HTML file — zero dependencies, zero installation, runs anywhere.

![Version](https://img.shields.io/badge/version-2.0.0-00e5ff?style=for-the-badge)
![HTML5](https://img.shields.io/badge/HTML5-Canvas-ff6b35?style=for-the-badge&logo=html5)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-ffd60a?style=for-the-badge&logo=javascript)
![Mobile](https://img.shields.io/badge/Mobile-Ready-00ff94?style=for-the-badge)
![Themes](https://img.shields.io/badge/Themes-Dark%20%26%20Light-c084fc?style=for-the-badge)

---

## 🕹️ Play It

**Just open `CatchMaster.html` in any browser. That's it. No install. No server. No dependencies.**

Works on:
- ✅ Chrome, Firefox, Safari, Edge
- ✅ iPhone & Android (touch controls)
- ✅ Desktop & Laptop (mouse controls)
- ✅ Fully offline

---

## 🎮 How to Play

| Control | Action |
|---------|--------|
| 🖱️ Move Mouse | Move catcher left / right |
| 👆 Slide Finger | Move catcher on mobile |
| 🌙 / ☀️ Button | Toggle dark / light theme |

### Catch good items. Dodge bombs. Survive as long as you can.

---

## 💎 Items & Scoring

| Item | Color | Points | Effect |
|------|-------|--------|--------|
| 💎 **Gem** | Cyan | +10 pts | Core item — catch these |
| ⭐ **Star** | Gold | +50 pts | Rare bonus — huge points |
| 🪙 **Coin** | Orange | +25 pts | Medium reward |
| 🛡️ **Shield** | Green | — | Absorbs one bomb hit |
| 🧊 **Freeze** | Purple | — | Slows all items for ~3s |
| 💣 **Bomb** | Red | -1 Life | Avoid at all costs |
| ⬛ **Dud** | Grey | -15 pts | Avoid — score penalty |

---

## ❤️ Miss Streak System

**Miss 3 gems in a row → Lose 1 Life**

This is the core survival mechanic:

```
Miss 1 gem  →  Yellow border flash  +  "MISS! ×1" warning
Miss 2 gems →  Red pulsing border   +  "MISS! ×2 ⚠" danger
Miss 3 gems →  LOSE A LIFE ❌       +  Full screen shake + explosion
```

- **Catching any good item** resets your miss streak back to zero
- A **3-gem miss meter** in the bottom bar shows your current danger level
- **Catching a shield** also resets the miss streak

---

## 🤖 AI Difficulty Engine

CatchMaster uses a two-layer adaptive difficulty system:

### Layer 1 — Score-Based Curve (primary)
Difficulty increases directly with your score in clear, noticeable jumps:

| Score | Speed | Spawn Rate | Bomb Chance |
|-------|-------|-----------|-------------|
| 0 | ×2.0 | Slow | 16% |
| 200 | ×2.5 | Normal | 22% |
| 350 | ×3.0 | Faster | 30% |
| 550 | ×3.6 | Fast | 40% |
| 800 | ×4.3 | Very Fast | 50% |
| 1,200 | ×5.8 | Rapid | 60% |
| 2,800 | ×6.8 | Insane | 68% |
| 4,000+ | ×9.0+ | Nightmare | 70%+ |

### Layer 2 — AI Rolling Window (fine-tuning)
The AI tracks your last 24 catches and adjusts spawn rate in real time:

```
Hit rate > 85%  →  AI spawns items faster (too easy for you)
Hit rate > 75%  →  AI nudges spawn slightly faster
Hit rate < 30%  →  AI backs off (you're struggling)
Hit rate < 45%  →  AI gives slight breathing room
```

### Difficulty Labels
```
CALIBRATING → NOVICE → EASY → MEDIUM → HARD → EXPERT → INSANE 🔥 → ☠️ NIGHTMARE
```

---

## 📉 Catcher Shrinks as You Progress

The catcher width gets narrower the higher your score — making precision increasingly critical:

| Score | Catcher Width |
|-------|--------------|
| 0 – 300 | 88px (forgiving) |
| 300 – 700 | 80px |
| 700 – 1,200 | 70px |
| 1,200 – 2,000 | 60px |
| 2,000 – 3,500 | 50px |
| 3,500+ | 42px (tiny!) |

---

## 🏆 Combo System

Chain catches without missing to multiply your score:

```
Every 5× combo  →  +0.5× score multiplier
Combo ×5        →  Popup flash
Combo ×10       →  🔥 Fire flash
Combo ×20       →  💥 Max explosion popup
```

Missing a gem or hitting a bomb resets your combo to zero.

---

## 🌙 Themes

Press the **🌙 / ☀️** button in the top-right corner to toggle themes:

| Dark Mode | Light Mode |
|-----------|------------|
| Deep navy background | Soft lavender background |
| Cyan neon accents | Blue accents |
| Scanline overlay | Subtle grid |
| Perfect for gaming at night | Perfect for daytime play |

---

## 📊 Level Milestones

| Level | Score Required |
|-------|---------------|
| Level 1 | Start |
| Level 2 | 100 pts |
| Level 3 | 350 pts |
| Level 4 | 800 pts |
| Level 5 | 1,500 pts |
| Level 6 | 3,000 pts |
| Level 7 | 5,000 pts |
| Level 8 | 8,000 pts |

---

## 🎨 Visual Effects

- ✨ **Particle bursts** on every catch — colour-matched to the item
- 💥 **Ring shockwave** on star and bomb events
- 🌊 **Item trails** — items leave a glowing wake as they fall
- 📳 **Canvas shake** on bomb hit or 3-miss life loss
- 🔴 **Danger zone** — canvas bottom glows red when lives ≤ 2
- 🟡 **Border flash** — full-canvas coloured border on miss warnings
- 🎯 **Aim laser** — soft glow line from catcher upward
- ⚡ **Level up flash** — full centre animation on each level milestone
- 🏆 **Score milestone badges** — pop up at 500, 1000, 2500, 5000, 10000 pts
- 🔢 **Floating score text** — every catch shows points at item position

---

## 🏗️ Architecture

```
CatchMaster.html
│
├── 🎨 CSS (embedded)
│   ├── Dark & Light theme CSS variables
│   ├── All UI components (HUD, overlays, miss meter)
│   ├── Animations (keyframes)
│   └── Responsive layout (mobile first)
│
└── 🧠 JavaScript (embedded)
    ├── Canvas Engine      — drawBg, drawItems, drawCatcher, drawParticles
    ├── Score→Difficulty   — direct bracket mapping (Layer 1)
    ├── AI Engine          — rolling hit-rate window (Layer 2)
    ├── Miss Streak System — 3-miss → lose life
    ├── Spawn System       — weighted random item pool
    ├── Combo System       — score multipliers
    ├── Particle System    — bursts, rings, trails, floats
    └── Input System       — mouse + touch unified
```

---

## 🔮 Upcoming Features

### 🎮 v2.1 — Game Modes
- [ ] 🏃 **Endless Mode** — current mode, no time limit
- [ ] ⏱️ **Time Attack** — score as much as possible in 60 seconds
- [ ] 💀 **One Life Mode** — single life, maximum tension
- [ ] 🎯 **Precision Mode** — misses count double, gems worth more
- [ ] 👥 **Two Player Mode** — split keyboard, same screen

### 🌐 v2.2 — Leaderboard
- [ ] 🏅 **Global Leaderboard** — MongoDB-backed high score table
- [ ] 📛 **Username entry** — set your name before playing
- [ ] 📅 **Daily Challenge** — same seed for everyone, compete daily
- [ ] 🗺️ **Country flags** — show player origin on leaderboard
- [ ] 👑 **Hall of Fame** — all-time top 10 permanently displayed

### ✨ v2.3 — Power-ups & Items
- [ ] 💣 **Magnet** — pulls nearby gems toward catcher for 5s
- [ ] ⬛ **Black Hole** — destroys all on-screen items
- [ ] 🌀 **Slow-Mo** — slows everything for 4 seconds
- [ ] 🎁 **Mystery Box** — random good or bad effect
- [ ] 🔥 **Fire Trail** — catcher burns, auto-destroys bombs for 5s
- [ ] ✖️ **Double Points** — 2× score multiplier for 8 seconds

### 🎨 v2.4 — Themes & Customisation
- [ ] 🌆 **Cyberpunk Theme** — neon on dark city
- [ ] 🌸 **Sakura Theme** — pink petals, soft pastels
- [ ] 🌊 **Ocean Theme** — deep blue with wave effects
- [ ] 🔥 **Lava Theme** — orange and volcanic
- [ ] 🎭 **Custom Catcher Skins** — unlock with score milestones
- [ ] 🎵 **Sound Effects** — toggle-able audio feedback

### 📱 v2.5 — Mobile Enhancement
- [ ] 📳 **Haptic Feedback** — vibration on bomb hit
- [ ] 📲 **PWA / Install** — add to home screen as native app
- [ ] 🔔 **Push Notifications** — daily challenge reminders
- [ ] 🖐️ **Gesture Controls** — tilt device to move catcher
- [ ] 📊 **Native Share** — share your score to Instagram/WhatsApp

### 🧠 v3.0 — True ML Difficulty
- [ ] 🤖 **TensorFlow.js model** — on-device neural network adapts to player style
- [ ] 📈 **Play style profiling** — detects if you're aggressive, defensive, or erratic
- [ ] 🎯 **Pattern injection** — AI creates item patterns designed to fool your style
- [ ] 📉 **Skill regression detection** — notices when you start tilting and eases off
- [ ] 🧬 **Session memory** — remembers your best strategies between sessions

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Rendering** | HTML5 Canvas 2D API |
| **Language** | Vanilla JavaScript (ES6+) |
| **Styling** | Pure CSS with custom properties |
| **Fonts** | Exo 2 + Share Tech Mono (Google Fonts) |
| **Storage** | localStorage (high score persistence) |
| **Build tool** | None — single file, zero dependencies |

---

## 📁 File Structure

```
CatchMaster.html       ← The entire game. One file.
README.md              ← This file
```

That's it. No `node_modules`. No build step. No config files.

---

## 🚀 Deployment

Since it's a single HTML file, you can host it literally anywhere:

**GitHub Pages:**
```bash
git add CatchMaster.html
git commit -m "deploy catchmaster"
git push
# Enable Pages in repo settings → deploy from main branch
```

**Netlify drag & drop:**
```
Drag CatchMaster.html to netlify.com/drop
Get a live URL in 10 seconds
```

**Vercel:**
```bash
npx vercel --prod
```

**Share directly:**
```
Just send the .html file to anyone — opens in browser immediately
```

---

## 📜 Scoring Tips

1. **Maintain combos** — a ×10 combo doubles every gem's points
2. **Prioritise stars** — 50 pts each, with combo multiplier = huge gains
3. **Use freeze wisely** — grab it before hard sections to slow the chaos
4. **Shield first** — always collect shields before going aggressive
5. **Watch the miss meter** — at ×2 warning, play defensive for 2–3 items
6. **Early speed matters** — score fast early before catcher shrinks

---

## ⚠️ Browser Compatibility

| Browser | Support |
|---------|---------|
| Chrome 80+ | ✅ Full |
| Firefox 75+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Edge 80+ | ✅ Full |
| Opera | ✅ Full |
| IE 11 | ❌ Not supported |

---

## 📄 License

MIT License — free to use, share, remix, and build upon.

---

## 👨‍💻 Author

<div align="center">

Crafted with ❤️ by **Shagun Tyagi**

[![GitHub](https://img.shields.io/badge/GitHub-theshaguntyagi-181717?style=for-the-badge&logo=github)](https://github.com/theshaguntyagi)

*"A game isn't hard — until the AI decides it should be."*

---

⭐ **Star this repo if you enjoyed playing!**

</div>
