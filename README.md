# 🤖 ARIA — AI for Curious Minds

> **An interactive AI interview experience for children aged 10–12**
> Built for school events and workshops across Europe 🇮🇹 🇪🇸 🇬🇷 🇫🇷 🇱🇺 🇬🇧

---

## What is ARIA?

ARIA (**A**rtificial **R**easoning and **I**ntelligence **A**ssistant) is a web app that lets children interview an AI in their own language. Instead of being told *about* artificial intelligence, kids get to ask their own questions and discover how AI works through a natural, playful conversation.

Children take on the role of journalists interviewing ARIA — a friendly AI with a personality — and earn badges as they explore different topics. A depth meter tracks how articulate and curious their questions are.

---

## Features

- 🌍 **6 languages** — Italian, Spanish, Greek, French (France & Luxembourg), English
- 🎤 **Interview format** — children ask questions, ARIA answers in character
- 💡 **12 suggested questions** per language to spark the conversation
- 🏅 **5 badge topics** — What is AI · How it learns · What it can do · Feelings · The future
- ⭐ **Depth meter** — 5 stars that reflect how thoughtful the questions are (local scoring + AI evaluation every 3 questions)
- 💬 **Guided hint** — after 15 seconds of inactivity, ARIA suggests 3 contextual follow-up questions
- 🟢 **Live status banner** — shows whether ARIA is online or offline at startup
- 🧑‍🏫 **Teacher panel** — password-protected overlay with full stats and conversation transcript
- 📄 **PDF export** — one-click download of the full interview with stats, badges and conversation
- 📱 **Fully responsive** — works on desktop, tablet and mobile

---

## How it works

```
Child's browser → Netlify Function (serverless proxy) → Anthropic API → ARIA's response
```

The app is a single HTML file. A Netlify serverless function acts as a secure proxy so the API key and teacher password never touch the browser.

---

## Project Structure

```
/
├── index.html                  # The entire front-end app
├── netlify/
│   └── functions/
│       └── chat.js             # Serverless proxy — handles /api/chat and /api/teacher-auth
└── README.md
```

---

## Deployment

### Prerequisites

- A [Netlify](https://netlify.com) account (free tier is sufficient)
- An [Anthropic](https://console.anthropic.com) API key

### Steps

**1. Fork or clone this repository**

```bash
git clone https://github.com/innov2e/al-for-curious-minds.git
```

**2. Connect to Netlify**

Go to [netlify.com](https://netlify.com) → **Add new site** → **Import from Git** → select this repository. Leave all build settings as default and deploy.

**3. Set environment variables**

In Netlify: **Site configuration → Environment variables → Add variable**

| Variable | Value | Required |
|----------|-------|----------|
| `ANTHROPIC_API_KEY` | `sk-ant-...` | ✅ Yes |
| `TEACHER_PASSWORD` | Your chosen password | ✅ Yes |

> ⚠️ If `TEACHER_PASSWORD` is not set, the default password `aria2025` will be used. Always set your own.

**4. Trigger a new deploy**

Go to **Deploys → Trigger deploy**. Your site will be live in about a minute.

---

## Activating and deactivating ARIA

ARIA is designed to be turned on only during live sessions. The status banner on the language selection screen automatically shows children whether ARIA is available.

**To activate** — make sure `ANTHROPIC_API_KEY` is set and trigger a deploy.

**To deactivate between events** — remove or clear `ANTHROPIC_API_KEY` in Netlify environment variables and trigger a deploy. The banner will show:

> *😴 ARIA is not available right now. To book a session write to info@innov2e.it*

All language buttons will be disabled automatically.

---

## Teacher Panel

The teacher panel gives facilitators a real-time view of each child's session.

**How to access:** click the 🧑‍🏫 button (bottom-right, visible only after choosing a language), then enter the teacher password.

**What it shows:**
- Number of questions asked
- Badges unlocked (which topics were explored)
- Depth score (0–5 stars + percentage bar)
- Full conversation transcript (child questions + ARIA answers)

**Session reset:** the panel includes a reset button to clear the conversation and all stats for the next child, without reloading the page.

---

## PDF Export

Click the 💾 button (bottom-right) at any point during a session to download a formatted PDF containing:

- Session metadata (date, language)
- Stats summary (questions, badges, depth level)
- Badge checklist
- Full conversation transcript

The PDF is generated entirely in the browser using [jsPDF](https://github.com/parallax/jsPDF) — no server needed.

---

## Local Development

Because the app calls `/api/chat` and `/api/teacher-auth` (Netlify Functions), you need the Netlify CLI to run it locally:

```bash
npm install -g netlify-cli
netlify dev
```

Then open `http://localhost:8888`.

Make sure you have a `.env` file (or Netlify dev environment) with:

```
ANTHROPIC_API_KEY=sk-ant-...
TEACHER_PASSWORD=yourpassword
```

---

## Technology

| Layer | Technology |
|-------|-----------|
| Front-end | Vanilla HTML, CSS, JavaScript (single file) |
| Serverless function | Netlify Functions (Node.js ESM) |
| AI model | Claude Sonnet (`claude-sonnet-4-5`) via Anthropic API |
| PDF generation | jsPDF 2.5.1 (loaded dynamically, CDN) |
| Fonts | Google Fonts — Nunito + Fredoka One |
| Hosting | Netlify (free tier) |

---

## Languages Supported

| Flag | Language | Region |
|------|----------|--------|
| 🇮🇹 | Italiano | Italia |
| 🇪🇸 | Español | España |
| 🇬🇷 | Ελληνικά | Ελλάδα |
| 🇫🇷 | Français | France |
| 🇱🇺 | Français | Luxembourg |
| 🇬🇧 | English | United Kingdom |

---

## Pedagogical Approach

ARIA is built around **discovery learning**. Rather than presenting facts about AI, the app:

- puts children in an active role (the interviewer, not the audience)
- uses language and analogies calibrated for ages 10–12
- encourages curiosity through suggested questions while leaving space for spontaneous ones
- tracks depth of engagement through a 5-star scoring system
- offers contextual hints when children seem stuck (after 15 seconds of inactivity)
- is honest about AI's limitations (no real emotions, no physical body, can make mistakes)

---

## Credits

Built by [innov2e](https://innov2e.it) for educational workshops on Artificial Intelligence.

Powered by [Claude](https://anthropic.com) — Anthropic's AI assistant.

---

## License

This project is intended for educational use. Feel free to adapt it for your own workshops — a mention is always appreciated! 🙏
