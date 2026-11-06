<div align="center">

<img src="../datafull.png" alt="DataFull Logo" width="96" />

# DataFull Studio

### Modern Database Suite for Local & LAN Development

[![License: MIT](https://img.shields.io/badge/License-MIT-3ecf8e?style=flat-square)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776ab?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Platform](https://img.shields.io/badge/Platform-Windows-0078d4?style=flat-square&logo=windows&logoColor=white)](https://github.com/FluxzyCorporations/.XIP/releases)
[![Version](https://img.shields.io/badge/Version-2.0.0-3ecf8e?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)](#)

<br/>

> **DataFull** is a complete, self-hosted database platform that combines the simplicity of XAMPP with the elegance of Supabase Studio — running 100% locally on your machine, with optional LAN/network exposure.

<br/>

[📥 Download Portable](https://github.com/FluxzyCorporations/.XIP/releases/download/ZIP/DataFull-v2.0-portable.zip) · [🌐 Official Website](https://datafull.vercel.app) · [🐛 Report a Bug](https://github.com/FluxzyCorporations/DataFull/issues) · [💬 Discussions](https://github.com/FluxzyCorporations/DataFull/discussions)

</div>

---

## 📸 Screenshots

<div align="center">

| Dashboard Studio | SQL Console | Table Editor |
|---|---|---|
| ![Dashboard](https://i.imgur.com/placeholder1.png) | ![SQL](https://i.imgur.com/placeholder2.png) | ![Tables](https://i.imgur.com/placeholder3.png) |

</div>

---

## ✨ Features

<table>
<tr>
<td width="50%">

**🏢 Multi-Tenant Architecture**
- Organizations & Projects system (Supabase-style)
- Each project has its own isolated SQLite database
- Independent API keys per project (`anon_key` + `service_role_key`)
- Project-scoped file storage (Buckets)

**📋 Table Editor**
- Spreadsheet-style data viewer & editor
- Visual table creator with typed columns
- Supported types: `TEXT`, `INTEGER`, `REAL`, `BOOLEAN`, `TIMESTAMP`
- One-click row insert, update and delete

</td>
<td width="50%">

**⚡ Live SQL Console**
- Full SQL execution with `F5` / `Ctrl+Enter`
- Execution time meter (ms)
- Pre-built templates: `SELECT`, `CREATE TABLE`, `INSERT`, `JOIN`
- MySQL/MariaDB `.sql` dump exporter

**🔌 Auto REST API v1**
- Every table gets instant HTTP endpoints
- `GET`, `POST` with filter & limit support
- Code snippets ready to copy: `fetch`, `requests`, `cURL`

</td>
</tr>
<tr>
<td width="50%">

**📁 Object Storage & Buckets**
- Create public/private buckets per project
- Upload files via UI or drag-and-drop
- Public CDN-style URLs for assets
- Served at `localhost:8080/DataFull/storage/...`

**🔁 Heartbeat Monitor**
- Real-time server status polling every 2.5 s
- Instant paused/active banner in the web UI
- Resume button directly from the browser

</td>
<td width="50%">

**🚀 Integrated Services Panel**
| # | Service | Port |
|---|---------|------|
| 1 | DataFull DB Engine | `8080` |
| 2 | HTTP Web Server | `8080` |
| 3 | Apache VHost Gateway | `8081` |
| 4 | MySQL/MariaDB Bridge | `3306` |
| 5 | Storage Engine | internal |

</td>
</tr>
</table>

---

## 🖥️ Desktop Control Panel

The **DataFull Launcher** (`app_gui.py`) is a system-tray application with a modern dark UI:

- 🟢 / 🔴 per-service toggle controls
- **Start All** · **Pause DB** · **Open Studio** · **Open WWW folder** global buttons
- Real-time event log with timestamps
- Runs silently in the system tray — zero browser needed to stay online

---

## 🚀 Quick Start

### Requirements

- **Python 3.10+** — [Download](https://python.org/downloads)
- **Windows 7 / 8 / 10 / 11** (64-bit)
- No other runtime or database installation needed

### Option A — Portable ZIP (Recommended)

```bash
# 1. Download and unzip DataFull-v2.0-portable.zip
# 2. Double-click:
start.bat
```

> This launches the system tray launcher and opens the Studio automatically.

### Option B — From Source

```bash
# 1. Clone
git clone https://github.com/FluxzyCorporations/DataFull.git
cd DataFull

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch
python app_gui.py
```

### Access the Dashboard

| URL | Description |
|-----|-------------|
| `http://localhost:8080/DataFull` | 🏠 DataFull Studio Dashboard |
| `http://localhost:8080/DataFull/<project>` | 📂 Your project's web root |
| `http://localhost:8080/DataFull/api/v1/<org>/<project>/<table>` | 🔌 Auto REST API |
| `http://localhost:8081` | 🚀 Apache VHost Gateway |

---

## 📁 Project Structure

```
DataFull/
├── app_gui.py              # Desktop launcher & system tray (tkinter)
├── server.py               # FastAPI server — Studio dashboard + REST API
├── config.py               # Config loader/saver (JSON)
├── db_engine.py            # SQLite database engine + query runner
├── org_manager.py          # Organizations & Projects CRUD
├── project_manager.py      # Per-project initialization
├── services_manager.py     # Service lifecycle (start/stop/status)
├── storage_manager.py      # Bucket & file storage management
├── datafull_icon.py        # Programmatic ICO generator (PIL)
├── requirements.txt        # Python dependencies
├── start.bat               # One-click launcher for Windows
│
├── dashboard/
│   ├── templates/index.html    # Studio UI (HTML — Supabase-inspired)
│   └── static/
│       ├── style.css           # Dark theme CSS (~22 KB)
│       └── app.js              # Frontend logic (~35 KB)
│
├── data/
│   ├── main_database.db        # Master DB (orgs, projects, keys)
│   └── organizations/
│       └── <org-id>/
│           └── projects/
│               └── <project-id>/database.db
│
├── storage/                # File storage (Buckets)
│   └── <org-id>/<project-id>/<bucket>/
│
└── www/                    # Web projects root (HTTP served)
    └── <project-name>/index.html
```

---

## 🌐 LAN / Network Mode

To expose DataFull on your local network (e.g. `192.168.1.x:8080`), change the port binding in `config.py`:

```json
{
  "port": 8080,
  "host": "0.0.0.0"
}
```

Then access from any device on your network:
```
http://<your-local-ip>:8080/DataFull
```

> ⚠️ Only expose on trusted networks. DataFull has no built-in authentication layer yet.

---

## 🔌 REST API Reference

Every table in any project is automatically available via REST:

```
GET  /DataFull/api/v1/{org}/{project}/{table}?limit=50
POST /DataFull/api/v1/{org}/{project}/{table}
```

**JavaScript Example:**
```js
const res = await fetch('http://localhost:8080/DataFull/api/v1/my-org/my-project/users?limit=10', {
  headers: { 'Authorization': 'Bearer YOUR_ANON_KEY' }
});
const data = await res.json();
```

**Python Example:**
```python
import requests

r = requests.get(
    'http://localhost:8080/DataFull/api/v1/my-org/my-project/users',
    headers={'Authorization': 'Bearer YOUR_ANON_KEY'}
)
print(r.json())
```

**cURL:**
```bash
curl http://localhost:8080/DataFull/api/v1/my-org/my-project/users \
  -H "Authorization: Bearer YOUR_ANON_KEY"
```

---

## 📦 Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| `fastapi` | ≥ 0.100.0 | Web framework & REST API |
| `uvicorn` | ≥ 0.22.0 | ASGI server |
| `python-multipart` | ≥ 0.0.9 | File upload support |
| `pystray` | ≥ 0.19.4 | System tray icon |
| `Pillow` | ≥ 10.0.0 | Image/icon generation |
| `psutil` | ≥ 5.9.0 | Process & port monitoring |

All installed via:
```bash
pip install -r requirements.txt
```

---

## 🗺️ Roadmap

- [ ] 🔐 Built-in authentication (JWT / session tokens)
- [ ] 🐬 Native MySQL / MariaDB connection (not just bridge)
- [ ] 🐘 PostgreSQL backend support
- [ ] 🌍 Real-time subscriptions (WebSocket)
- [ ] 🐳 Docker container support
- [ ] 🖥️ macOS & Linux launcher
- [ ] 📊 Query analytics & slow query log
- [ ] 🔔 Webhooks per table event

---

## 🤝 Contributing

Contributions, issues and feature requests are welcome!

1. Fork the repository
2. Create your branch: `git checkout -b feature/AmazingFeature`
3. Commit your changes: `git commit -m 'Add AmazingFeature'`
4. Push: `git push origin feature/AmazingFeature`
5. Open a Pull Request

---

## 📄 License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for more information.

---

## 👨‍💻 Author

<div align="center">

Made with ❤️ by **[FluxzyCorporations](https://github.com/FluxzyCorporations)**

[![GitHub](https://img.shields.io/badge/GitHub-FluxzyCorporations-181717?style=flat-square&logo=github)](https://github.com/FluxzyCorporations)

</div>

