# 🤖 ARIA — AI for Curious Minds

> **An interactive AI interview experience for children aged 10–12**
> Built for school events and workshops across Europe 🇮🇹 🇪🇸 🇬🇷 🇫🇷 🇱🇺 🇬🇧

---

## What is ARIA?

ARIA (**A**rtificial **R**easoning and **I**ntelligence **A**ssistant) is a web app that lets children interview an AI in their own language. Instead of being told *about* artificial intelligence, kids get to ask their own questions and discover how AI works through a natural, playful conversation.

Children take on the role of journalists interviewing ARIA — a friendly AI with a personality — and earn badges as they explore different topics.

---

## Features

- 🌍 **6 languages** — Italian, Spanish, Greek, French (France & Luxembourg), English
- 🎤 **Interview format** — children ask questions, ARIA answers in character
- 💡 **12 suggested questions** per language to get the conversation started
- 🏅 **5 badge topics** to unlock: What is AI · How it learns · What it can do · Feelings · The future
- ⚡ **Animated thinking indicator** with rotating phrases while ARIA processes the question
- 🟢 **Live status banner** — shows whether ARIA is online or offline before children even pick a language
- 📱 **Fully responsive** — works on desktop, tablet and mobile

---

## How it works

```
Child's browser → Netlify Function (serverless) → Anthropic API → ARIA's response
```

The app is a single HTML file. A small Netlify serverless function acts as a secure proxy, so the API key never touches the browser.

---

## Project Structure

```
/
├── index.html                  # The entire front-end app
├── netlify/
│   └── functions/
│       └── chat.js             # Serverless proxy to Anthropic API
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

**3. Add your API key**

In Netlify: **Site configuration → Environment variables → Add variable**

| Key | Value |
|-----|-------|
| `ANTHROPIC_API_KEY` | `sk-ant-...` |

**4. Trigger a new deploy**

Go to **Deploys → Trigger deploy**. Your site will be live in about a minute.

---

## Activating and deactivating ARIA

ARIA is designed to be turned on only during live sessions. The status banner on the language selection screen automatically tells children whether ARIA is available or not.

**To activate** — make sure `ANTHROPIC_API_KEY` is set in Netlify environment variables and trigger a deploy.

**To deactivate** — remove or clear the `ANTHROPIC_API_KEY` variable in Netlify and trigger a deploy. The banner will show:

> *😴 ARIA is not available right now. To book a session write to info@innov2e.it*

...and all language buttons will be disabled automatically.

---

## Local development

Because the app calls `/api/chat` (a Netlify Function), you need the Netlify CLI to run it locally:

```bash
npm install -g netlify-cli
netlify dev
```

Then open `http://localhost:8888`.

---

## Technology

| Layer | Technology |
|-------|-----------|
| Front-end | Vanilla HTML, CSS, JavaScript (single file) |
| Serverless function | Netlify Functions (Node.js) |
| AI model | Claude Sonnet (`claude-sonnet-4-5`) via Anthropic API |
| Fonts | Google Fonts — Nunito + Fredoka One |
| Hosting | Netlify (free tier) |

---

## Pedagogical approach

ARIA is built around **discovery learning**. Rather than presenting facts about AI, the app:

- puts children in an active role (the interviewer, not the audience)
- uses language and analogies calibrated for ages 10–12
- encourages curiosity through suggested questions while leaving space for spontaneous ones
- gamifies exploration with badges that reward covering different topics
- is honest about AI's limitations (no real emotions, no physical body, can make mistakes)

---

## Languages supported

| Flag | Language | Region |
|------|----------|--------|
| 🇮🇹 | Italiano | Italia |
| 🇪🇸 | Español | España |
| 🇬🇷 | Ελληνικά | Ελλάδα |
| 🇫🇷 | Français | France |
| 🇱🇺 | Français | Luxembourg |
| 🇬🇧 | English | United Kingdom |

---

## Credits

Built by [innov2e](https://innov2e.it) for educational workshops on Artificial Intelligence.

Powered by [Claude](https://anthropic.com) — Anthropic's AI assistant.

---

## License

This project is intended for educational use. Feel free to adapt it for your own workshops — a mention is always appreciated! 🙏
