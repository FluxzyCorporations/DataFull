# Security Policy

## 🔒 Supported Versions

| Version | Supported |
|---------|-----------|
| 2.0.x   | ✅ Yes |
| < 2.0   | ❌ No  |

## 🐛 Reporting a Vulnerability

**Please do NOT open a public GitHub issue for security vulnerabilities.**

Send a private report to: **security@fluxzycorp.dev**

Include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (optional)

We will respond within **72 hours** and release a patch as soon as possible.

## ⚠️ Current Known Limitations

- DataFull has **no authentication layer** in v2.0. Do not expose port `8080` to the public internet.
- API keys (`anon_key`, `service_role_key`) are stored in plaintext in `datafull_config.json`. Keep this file private.
- Intended for **local development and LAN use only** unless you add a reverse proxy with authentication.

