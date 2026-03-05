# Command X

A mobile-first X (Twitter) content OS — live trends, breaking headlines, AI draft generation, and post queue.

## Tech Stack

- **Frontend** — vanilla HTML/CSS/JS, no dependencies
- **Backend** — Vercel serverless function (`/api/claude.js`) proxies Anthropic API calls
- **AI** — Claude Sonnet 4.6 via Anthropic API (web search + generation)

## Deploy to Vercel

### 1. Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
gh repo create command-x --public --push
```

### 2. Import to Vercel

1. Go to [vercel.com](https://vercel.com) → **Add New Project**
2. Import your GitHub repo
3. Set **Root Directory** to `/` (default)
4. Under **Environment Variables**, add:
   ```
   ANTHROPIC_API_KEY = sk-ant-...
   ```
5. Click **Deploy**

### 3. Done

Your app will be live at `https://your-project.vercel.app`

## Local Development

```bash
npm i -g vercel
vercel dev
```

Then open `http://localhost:3000`

> Local dev also requires the `ANTHROPIC_API_KEY` env var. Create a `.env` file:
> ```
> ANTHROPIC_API_KEY=sk-ant-...
> ```

## Project Structure

```
commandx/
├── api/
│   └── claude.js      # Serverless proxy — keeps API key server-side
├── public/
│   └── index.html     # Full app — trends, headlines, drafts, queue
├── vercel.json        # Routing config
└── README.md
```

## Features

- **Trends** — live Reddit + Hacker News via Claude web search
- **Headlines** — breaking news from NYT, WSJ, Reuters, BBC, AP
- **AI Drafts** — 6 styles: Engaging, Controversial, Informative, Humorous, Thread, Hot Take
- **Post Queue** — save drafts, schedule, post directly to X
- **Mobile-first** — bottom tab bar on mobile, sidebar on desktop
