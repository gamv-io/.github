<div align="center">

<img src="https://gamv.io/icon.svg" alt="Gamvio" width="80" />

# Gamvio

### The Web3 Game Store

**Play 75+ browser games · Earn token rewards · Build and publish your own games**

[![Play Now](https://img.shields.io/badge/Play_Now-gamv.io-00E5FF?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0iYmxhY2siPjxwYXRoIGQ9Ik0xNS41IDE3YTIuNSAyLjUgMCAxMDAtNSAyLjUgMi41IDAgMDAwIDV6TTguNSAxNS41YTEgMSAwIDEwMC0yIDEgMSAwIDAwMCAyeiIvPjxwYXRoIGZpbGwtcnVsZT0iZXZlbm9kZCIgZD0iTTQuNSAyQTIuNSAyLjUgMCAwMDIgNC41djE1QTIuNSAyLjUgMCAwMDQuNSAyMmgxNWEyLjUgMi41IDAgMDAyLjUtMi41di0xNUEyLjUgMi41IDAgMDAxOS41IDJoLTE1ek04LjUgMTJhMS41IDEuNSAwIDExMCAzIDEuNSAxLjUgMCAwMTAtM3ptNCAyLjVhMyAzIDAgMTE2IDAgMyAzIDAgMDEtNiAwek04IDcuNWEuNS41IDAgMDEuNS0uNWgxVjZhLjUuNSAwIDAxMSAwdjFoMWEuNS41IDAgMDEwIDFoLTF2MWEuNS41IDAgMDEtMSAwVjhoLTFhLjUuNSAwIDAxLS41LS41eiIgY2xpcC1ydWxlPSJldmVub2RkIi8+PC9zdmc+&labelColor=0a0a12)](https://gamv.io)
[![SDK Docs](https://img.shields.io/badge/SDK_Docs-8B5CF6?style=for-the-badge&logo=book&logoColor=white&labelColor=0a0a12)](https://gamv.io/developers/docs)
[![npm](https://img.shields.io/npm/v/@gamvio/game-sdk?style=for-the-badge&logo=npm&label=game-sdk&color=CB3837&labelColor=0a0a12)](https://www.npmjs.com/package/@gamvio/game-sdk)

</div>

---

## What is Gamvio?

Gamvio is a **Web3 game store platform** where players discover and play browser-based games while earning blockchain token rewards. Developers can integrate their games through our SDK and tap into a built-in player base with leaderboards, quests, and a token economy.

### For Players

- **75+ instant-play games** — arcade, puzzle, strategy, board, card, brain teasers
- **Earn POINT tokens** — rewards for playing, daily quests, and check-in streaks
- **Global leaderboards** — compete for top rankings on every game
- **Free to play** — no downloads, no installs, play in your browser

### For Developers

- **One-command setup** — `npx create-gamvio-game my-game`
- **Anti-cheat scoring** — HMAC-SHA256 signed, server-verified score submissions
- **Built-in economy** — automatic POINT token rewards for players of your game
- **Leaderboards included** — global and weekly rankings per game, zero config
- **Test mode** — develop locally with instant test tokens, no platform login needed

---

## Quick Start for Developers

```bash
# 1. Scaffold a new game project
npx create-gamvio-game my-game
cd my-game

# 2. Add your SDK credentials (from dev.gamv.io)
cp .env.example .env.local

# 3. Start development — test mode activates automatically on localhost
npm install
npm run dev
```

### How It Works

```
┌─────────────────┐      ┌──────────────────┐      ┌─────────────────┐
│   Your Game      │      │   Your Server     │      │   Gamvio API     │
│   (Browser)      │ ───► │   (Next.js)       │ ───► │   (gamv.io)      │
│                  │      │                   │      │                  │
│  useGamvio()     │      │  HMAC signing     │      │  Score verify    │
│  submitScore()   │      │  Session mgmt     │      │  Leaderboard     │
│  getLeaderboard()│      │  Secrets safe     │      │  Token rewards   │
└─────────────────┘      └──────────────────┘      └─────────────────┘
```

> **Key security feature:** HMAC signing keys and API secrets stay on your server. The browser never sees them. Scores are cryptographically verified to prevent cheating.

---

## Open Source Repositories

### 🔧 Developer Tools

| Repository | Description | |
|:-----------|:------------|:--|
| [**game-sdk**](https://github.com/gamv-io/game-sdk) | TypeScript SDK — auth, sessions, scoring, leaderboards | [![npm](https://img.shields.io/npm/v/@gamvio/game-sdk?style=flat-square&color=00E5FF)](https://www.npmjs.com/package/@gamvio/game-sdk) |
| [**create-gamvio-game**](https://github.com/gamv-io/create-gamvio-game) | CLI scaffolding — `npx create-gamvio-game` | [![npm](https://img.shields.io/npm/v/create-gamvio-game?style=flat-square&color=00E5FF)](https://www.npmjs.com/package/create-gamvio-game) |

### 🎮 Sample Projects

| Repository | Games | Description |
|:-----------|:------|:------------|
| [**sample-arcade**](https://github.com/gamv-io/sample-arcade) | Gravity Flip · Neon Racer · Pixel Runner · Rhythm Tap · Asteroid Miner | Action & arcade games with SDK integration |
| [**sample-strategy**](https://github.com/gamv-io/sample-strategy) | Tower Defense · Shadow Chess · Infection · Merge Lab · Portal Maze | Strategy & puzzle games with SDK integration |

---

## Platform Architecture

```
                    ┌─────────────────────────────────────┐
                    │           gamv.io (Cloudflare)       │
                    └───────────┬─────────────────────────┘
                                │
                    ┌───────────┼───────────────┐
                    │           │               │
              ┌─────▼─────┐ ┌──▼──────┐ ┌──────▼──────┐
              │  Web App   │ │ Dev     │ │  Admin      │
              │  Next.js   │ │ Portal  │ │  Dashboard  │
              │  :4000     │ │ :4001   │ │  :4002      │
              └─────┬──────┘ └──┬──────┘ └──────┬──────┘
                    │           │               │
              ┌─────▼───────────▼───────────────▼──────┐
              │           Go API (Fiber) :8080          │
              │                                         │
              │  Auth · Games · Sessions · Leaderboard  │
              │  Tokens · Quests · SDK · Admin           │
              └──────────┬──────────────┬──────────────┘
                         │              │
                  ┌──────▼──────┐ ┌─────▼─────┐
                  │ PostgreSQL  │ │   Redis    │
                  │    :5433    │ │   :6379    │
                  └─────────────┘ └───────────┘
```

## Tech Stack

| Layer | Technology |
|:------|:-----------|
| **Frontend** | Next.js 15 · React 19 · Tailwind CSS 4 · TypeScript |
| **Backend** | Go 1.22 · Fiber v2 · PostgreSQL 16 · Redis 7 |
| **Auth** | NextAuth v5 · Google OAuth · Kakao OAuth |
| **Blockchain** | Xphere (EVM-compatible) · Thirdweb SDK |
| **Game SDK** | TypeScript · HMAC-SHA256 · Server Actions |
| **Infrastructure** | Ubuntu · Nginx · PM2 · Docker · Cloudflare |

## SDK Features

| Feature | Description |
|:--------|:------------|
| **Session Management** | Start/end game sessions with server-generated HMAC keys |
| **Score Submission** | Cryptographically signed scores — tamper-proof |
| **Leaderboards** | Global and weekly rankings, player rank lookup |
| **Player Auth** | Email/password or wallet login via SDK API keys |
| **Token Rewards** | Automatic POINT distribution based on score thresholds |
| **Test Mode** | `POST /sdk/auth/test-token` — instant dev tokens with API key only |
| **Multi-Game** | One project can host multiple games with dynamic `gameId` |

---

## Game Categories

| Category | Count | Examples |
|:---------|:------|:--------|
| 🕹️ **Arcade** | 15+ | Tetris, Snake, Flappy Jump, Space Invaders, Breakout |
| 🧩 **Puzzle** | 12+ | 2048, Sudoku, Minesweeper, Hex Puzzle, Pipe Connect |
| ♟️ **Strategy** | 8+ | Tower Defense, Shadow Chess, Infection, Reversi |
| 🎲 **Board** | 10+ | Go-Stop, Baduk, Omok, Chess, Janggi, Yut-Nori |
| 🃏 **Card** | 8+ | Texas Hold'em, Seotda, Badugi, One Card, Seven Poker |
| 🧠 **Brain** | 6+ | Math Sprint, Word Scramble, Crossword, Typing Race |
| 🎯 **Casual** | 10+ | Bubble Shooter, Merge Lab, Color Match, Tower Stack |
| 💰 **Crypto** | 1 | Crypto Predict (real-time OraXL oracle data) |

---

## Links

| | |
|:--|:--|
| 🌐 **Platform** | [gamv.io](https://gamv.io) |
| 🔧 **Developer Portal** | [dev.gamv.io](https://dev.gamv.io) |
| 📖 **SDK Documentation** | [gamv.io/developers/docs](https://gamv.io/developers/docs) |
| 📡 **API Reference** | [gamv.io/developers/api](https://gamv.io/developers/api) |
| 📦 **npm Package** | [@gamvio/game-sdk](https://www.npmjs.com/package/@gamvio/game-sdk) |
| 🛡️ **Admin Dashboard** | [admin.gamv.io](https://admin.gamv.io) |

---

<div align="center">

**Built in Seoul 🇰🇷**

[Play Games](https://gamv.io) · [Build Games](https://gamv.io/developers) · [Get SDK Keys](https://dev.gamv.io)

</div>
