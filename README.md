# AeroQuest MCQ

**Aerospace Engineering MCQ Assessment Web App**
Sci-fi themed, one-time-use exam system with Google Sheets integration.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Full MCQ web app (single file) |
| `questions.json` | 30 aerospace MCQs with answers (edit to customize) |
| `vercel.json` | Vercel deployment config |
| `code.gs` | Code to add to your Google Apps Script |

## Deploy to Vercel (Free)

1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → Import Project → Select your repo
3. Deploy (no build config needed — it's pure HTML)
4. Your URL will be: `https://your-project.vercel.app`

## Google Apps Script Setup

Open your existing Apps Script project and follow instructions in `code.gs`:
- Paste the `loginMCQ` block into `doGet(e)`
- Paste the `submitMCQ` block into `doPost(e)`
- Deploy as new version

## Sheet Columns Written by MCQ

| Col | Field | Written when |
|-----|-------|-------------|
| I | `points` | Student submits |
| J | `attempt` | Student submits (set to 1) |

## Adding Questions

Edit `questions.json`. Fields:
- `"question"` — question text
- `"equation"` — LaTeX string (optional, shown as rendered math)
- `"image"` — full URL to image (optional)
- `"optionA/B/C/D"` — answer choices
- `"answer"` — correct answer (`"A"`, `"B"`, `"C"`, or `"D"`)

## Local Testing

```bash
python3 -m http.server 8080
# Open http://localhost:8080/index.html
```

## Anti-Cheat Features

- Fullscreen lock on login
- Tab-switch / window blur detection → 3 strikes → session lock
- Right-click, copy, paste disabled
- F12 / DevTools keyboard shortcuts blocked  
- DevTools setter trap (console-based detection)
- One-time attempt: blocked on re-login if already submitted
