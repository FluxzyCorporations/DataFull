# DataFull — Contributing Guide

Thank you for your interest in contributing to **DataFull Studio**! 🎉

## 🛠️ Development Setup

```bash
git clone https://github.com/FluxzyCorporations/DataFull.git
cd DataFull
pip install -r requirements.txt
python app_gui.py
```

## 📁 Key Files

| File | Description |
|------|-------------|
| `server.py` | FastAPI backend — all HTTP routes |
| `app_gui.py` | Desktop launcher (tkinter + system tray) |
| `db_engine.py` | SQLite engine & query runner |
| `org_manager.py` | Organizations & Projects logic |
| `dashboard/templates/index.html` | Studio frontend (HTML/JS) |
| `dashboard/static/style.css` | Dark theme CSS |

## 🌿 Branch Naming

| Type | Example |
|------|---------|
| Feature | `feature/sql-history` |
| Bug fix | `fix/heartbeat-false-positive` |
| Docs | `docs/api-reference` |

## 📏 Code Style

- Python: follow **PEP 8** (4-space indent, type hints where possible)
- HTML/JS/CSS: 4-space indent, camelCase for JS functions
- Commit messages: start with an emoji + verb (`✨ Add bucket deletion`, `🐛 Fix port check`)

## 🚀 Submitting a PR

1. Fork → branch → code → test locally
2. Open a Pull Request against `main`
3. Fill in the PR template
4. Wait for review — usually within 48 h

## 💬 Questions?

Open a [Discussion](https://github.com/FluxzyCorporations/DataFull/discussions) or ping us in Issues.

