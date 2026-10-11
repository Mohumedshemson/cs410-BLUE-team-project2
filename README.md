# Faíct

An AI-assisted fact-checking application being developed for ODU CS 411W.

## What Is This Project?

Faíct is a prototype application that combines Flask backend services with AI-powered analysis to help verify claims and provide evidence-based verdicts. The project is structured for human-agent collaboration using the Agentic-Agile development framework.

**For AI agents:** Start with [`AGENTS.md`](AGENTS.md) — it contains the universal entry point and all context you need.

**For humans:** Continue reading this file for project overview, setup, and architecture.

---

## Current Prototype

The current skeleton supports:

- Text claim submission
- Flask backend processing
- Placeholder AI analysis
- Placeholder evidence retrieval
- Verdict, confidence, explanation, and source display
- SQLite database storage
- Flask-SQLAlchemy ORM

---

## Technology Stack

- **Runtime:** Python 3
- **Framework:** Flask
- **Frontend:** HTML, Jinja templates
- **Styling:** Tailwind CSS, custom CSS
- **Client-side:** JavaScript
- **ORM:** Flask-SQLAlchemy
- **Database:** SQLite (development), PostgreSQL (planned)
- **AI Services:** OpenAI API, Google Fact Check API
- **Testing:** PyTest
- **Version Control:** Git/GitHub

---

## Project Structure

```
cs410-BLUE-team-project/
├── app.py                      # Flask app factory and entry point
├── config.py                   # Configuration management
├── requirements.txt            # Python dependencies
├── .env.example                # Environment variables template
├── .gitignore                  # Git ignore rules
├── AGENTS.md                   # AI agent entry point
├── MANIFESTO.md                # Agentic-Agile principles
├── STYLE.md                    # Code conventions
├── CONTRIBUTING.md             # Contribution workflow
├── platform-adapters/          # Agent & issue tracker configs
│   ├── agent-tools/            # Agent-specific adapters
│   └── issue-trackers/         # Issue tracker templates
├── docs/                       # Documentation
│   └── sample-issues/          # Example stories
├── routes/                     # Flask route handlers
├── services/                   # Business logic services
├── models/                     # SQLAlchemy models
├── templates/                  # Jinja templates
├── static/                     # CSS, JS, images
└── tests/                      # Test suite
```

---

## Getting Started

### Prerequisites

- Python 3.8+
- pip and virtualenv

### Installation

1. **Clone the repository:**

```bash
git clone https://github.com/Mohumedshemson/cs410-BLUE-team-project.git
cd cs410-BLUE-team-project
```

2. **Create a virtual environment:**

```bash
python -m venv .venv
```

3. **Activate the virtual environment:**

**On Windows (PowerShell):**
```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```

**On macOS/Linux:**
```bash
source .venv/bin/activate
```

4. **Install dependencies:**

```bash
pip install -r requirements.txt
```

5. **Create a `.env` file** (copy from `.env.example` and fill in values):

```bash
cp .env.example .env
```

6. **Run the application:**

```bash
python app.py
```

7. **Open in browser:**

Navigate to `http://127.0.0.1:5000`

---

## Application Architecture

The application follows a layered architecture:

```
User Input (HTML Form)
  ↓
Flask Route Handler (/routes/main.py)
  ↓
Evidence Retrieval Service (/services/evidence.py)
  ↓
AI Analysis Service (/services/ai.py)
  ↓
Database (SQLAlchemy Models → SQLite)
  ↓
Results Page (Jinja Template)
```

### Key Layers

- **Routes:** HTTP endpoints for claim submission and verdict retrieval
- **Services:** Business logic for evidence retrieval and AI analysis (currently placeholders)
- **Models:** SQLAlchemy ORM models for database entities
- **Templates:** Jinja2 templates for HTML rendering
- **Config:** Environment-based configuration management

---

## Development Status

### Phase 1: Prototype (Current)

- [x] Flask application skeleton
- [x] SQLAlchemy ORM setup
- [x] Placeholder AI analysis
- [x] Placeholder evidence retrieval
- [x] Basic UI with form submission
- [x] Database schema and models

### Phase 2: Integration (Planned)

- [ ] OpenAI API integration for real AI analysis
- [ ] Google Fact Check API integration
- [ ] Real evidence retrieval from web sources
- [ ] Enhanced UI/UX
- [ ] Comprehensive test suite

### Phase 3: Production (Planned)

- [ ] PostgreSQL deployment
- [ ] Performance optimization
- [ ] Security hardening
- [ ] Documentation and API spec
- [ ] Deployment pipeline

---

## Development Workflow

This project uses **Agentic-Agile** practices for human-agent collaboration:

1. **Specifications first:** Work is defined in GitHub Issues using the structured story template (see `.github/ISSUE_TEMPLATE/agentic-story.md`).
2. **Clear scope:** Each issue specifies file ownership and acceptance criteria.
3. **Parallel execution:** Multiple agents can work simultaneously on non-overlapping files.
4. **Wave-based delivery:** Work executes in small parallel batches with review gates.

### Code Conventions

- **Style:** Follow `STYLE.md` for code formatting, naming, and documentation.
- **Commits:** Use Conventional Commits format (e.g., `feat(api): add endpoint`)
- **PRs:** Link to issues, describe changes clearly, self-review before submission.
- **Tests:** Write tests alongside features; aim for high coverage on business logic.

### Running Tests

```bash
pytest
```

---

## Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
OPENAI_API_KEY=<your-openai-api-key>
GOOGLE_FACT_CHECK_API_KEY=<your-google-fact-check-api-key>
SECRET_KEY=<your-secret-key-for-flask>
DATABASE_URL=sqlite:///faict.db  # or postgresql://user:pass@host/db
```

---

## Resources

- [AGENTS.md](AGENTS.md) — AI agent entry point
- [MANIFESTO.md](MANIFESTO.md) — Agentic-Agile principles
- [STYLE.md](STYLE.md) — Code conventions
- [CONTRIBUTING.md](CONTRIBUTING.md) — Human contribution workflow
- [GitHub Issues](../../issues) — Backlog and stories
- [GitHub Discussions](../../discussions) — Team discussions

---

## Team

This project is developed by the BLUE Team for ODU CS 411W.

---

## License

MIT License — See LICENSE file for details.
