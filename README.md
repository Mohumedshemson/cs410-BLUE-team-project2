# Faíct

**The Fact AI Checking Tool** — an evidence-based fact-checking web app built for
ODU CS 411W. Submit a claim, and Faíct gathers evidence from fact-check databases
and trusted web sources, has an LLM analyze it, and returns a verdict, confidence
score, explanation, and source links. Every result is saved to a history page.

Verdicts must be grounded in retrieved evidence, not the model's opinion. When
evidence is thin, the answer is **Uncertain**.

## How it works

```
Claim → Flask route → Google Fact Check API ──┐
                      (Brave Search fallback) ─┴→ normalize + filter evidence
      → OpenAI analysis → verdict / confidence / explanation
      → save to SQLite → results page + history
```

Verdict labels: `True`, `False`, `Misleading`, `Uncertain`.

## Project structure

```
.
├── app.py                  # Flask app factory and entry point
├── config.py               # Settings loaded from .env
├── requirements.txt        # Python dependencies
├── .env.example            # Required environment variables
├── models/                 # SQLAlchemy models (Submission)
├── routes/                 # Flask blueprints (home, analyze, history)
├── services/
│   ├── evidence_service.py # Fact Check + Brave retrieval, normalization, filtering
│   └── ai_service.py       # OpenAI analysis and result validation
├── templates/              # Jinja2 templates (base, index, results, history)
├── static/                 # Images and JavaScript
├── tests/                  # PyTest suite (external APIs mocked)
├── docs/                   # Project docs, frameworks, course-site pages
├── platform-adapters/      # Agent, issue-tracker, and CI/CD context
└── AGENTS.md               # Entry point for AI coding agents
```

Contributor docs at the root: [CONTRIBUTING.md](CONTRIBUTING.md),
[STYLE.md](STYLE.md), [SECURITY.md](SECURITY.md), [MANIFESTO.md](MANIFESTO.md).

## Tech stack

Python · Flask · Flask-SQLAlchemy · SQLite (PostgreSQL planned) · Jinja2 ·
Tailwind CSS · OpenAI API · Google Fact Check Tools API · Brave Search API · PyTest

## Getting started

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
cp .env.example .env             # then fill in your API keys
python app.py
```

Open http://127.0.0.1:5000. If port 5000 is busy (macOS AirPlay uses it), run
`flask --app app run --port 5001`.

### Environment variables

| Variable | Purpose |
|----------|---------|
| `SECRET_KEY` | Flask session key |
| `DATABASE_URL` | Database URI (defaults to local SQLite `faict.db`) |
| `OPENAI_API_KEY` | Claim analysis |
| `OPENAI_MODEL` | Model name (optional; has a default) |
| `GOOGLE_FACT_CHECK_API_KEY` | Primary evidence source |
| `BRAVE_SEARCH_API_KEY` | Fallback web search |

Never commit `.env`. Without keys the app still runs but returns **Uncertain**
because no evidence is found.

## Testing

```bash
python -m pytest
```

Tests mock all external APIs, so they run offline and cost nothing.

## Current sprint (Oct 8 – Nov 8, 2026)

- Improve evidence relevance
- Persist source records linked to each submission
- Saved-result detail page
- Save user feedback
- Frontend polish
- Choose and build the next input type

## Team

Group Green: Johnovon Richards, Colby Scroggins, Shaavon Farrow, Patrick Cunanan,
Mohumed Shemson, Anthony Oliphant.
