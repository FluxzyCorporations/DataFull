# Changelog

All notable changes to **DataFull Studio** will be documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) · Versioning follows [SemVer](https://semver.org).

---

## [2.0.0] — 2026-11-06

### ✨ Added
- **Multi-tenant Architecture:** Organizations & Projects system (Supabase-style)
- **Table Editor:** Spreadsheet-style data viewer with visual table creator
- **Live SQL Console:** Full SQL execution with execution time meter (ms)
- **Auto REST API v1:** Every table gets instant `GET`/`POST` endpoints
- **Object Storage:** Buckets with public/private file storage
- **Heartbeat Monitor:** Real-time active/paused banner in the web UI (polls every 2.5 s)
- **5 Integrated Services:** DB Engine, HTTP Server, Apache VHost, MySQL Bridge, Storage Engine
- **Desktop Launcher:** System-tray app with dark UI inspired by Docker Desktop & Supabase
- **MySQL/MariaDB Export:** Generate `.sql` dumps compatible with phpMyAdmin, MySQL 5.7+, MariaDB
- **LAN Mode:** Configurable `host: 0.0.0.0` for local network access
- **API Key System:** Auto-generated `anon_key` and `service_role_key` per project

### 🔨 Changed
- Replaced flat XAMPP-style panel with full Supabase-inspired Studio dashboard
- Moved from single-database model to per-project isolated SQLite databases

### 🐛 Fixed
- System tray icon rendering on Windows 7/8/10/11
- FastAPI startup race condition between services
- Port conflict detection for Apache VHost Gateway (8081)

---

## [1.0.0] — 2026-10-01 *(Initial prototype)*

### ✨ Added
- Basic SQLite database with simple REST endpoint
- Minimal launcher UI
- HTTP file server for `www/` directory

