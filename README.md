# Cortex Console

**Web Administration Console for Cortex Linux**

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![React](https://img.shields.io/badge/react-18+-61DAFB.svg)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/typescript-5+-3178C6.svg)](https://typescriptlang.org)

## Overview

`cortex-console` provides a browser-based administration interface for Cortex Linux servers. It offers the same AI-assisted workflows as the CLI with a visual interface.

## Key Features

| Feature | Description |
|---------|-------------|
| **Dashboard** | System health, services, resources at a glance |
| **AI Assistant** | Same prompt-to-plan as CLI, in the browser |
| **Package Manager** | Visual apt interface with search |
| **Service Control** | Start/stop/restart systemd units |
| **Log Viewer** | Real-time journald streaming |
| **Config Editor** | Safe configuration changes |

## Architecture

```
cortex-console/
├── frontend/                   # React SPA
│   ├── src/
│   │   ├── components/         # UI components
│   │   ├── pages/              # Route pages
│   │   ├── hooks/              # React hooks
│   │   └── api/                # API client
│   └── public/
├── backend/                    # API server
│   ├── src/
│   │   ├── routes/             # REST endpoints
│   │   ├── auth/               # PAM integration
│   │   ├── broker/             # Privilege broker
│   │   └── ws/                 # WebSocket handlers
├── systemd/                    # Service units
└── tests/
```

## Topics (from Planning)

This repository covers 8+ major topics with ~80 decisions and ~70 tasks:

- [ ] Authentication and session management (PAM-backed)
- [ ] Authorization/RBAC and admin roles
- [ ] Backend privileged-operation broker (polkit/sudo mediation)
- [ ] Embedded AI assistant in the web console
- [ ] Extension framework for additional admin modules
- [ ] Public/remote API definition (OpenAPI + JSON Schema)
- [ ] Remote terminal access and command execution UX
- [ ] Task/job system with streaming logs and progress
- [ ] Web console architecture and deployment model

## Quick Start

```bash
# Install from Cortex repository
sudo apt install cortex-console

# Enable and start
sudo systemctl enable --now cortex-console

# Access at
https://localhost:9090
```

## Security Model

- PAM-backed authentication (same users as SSH)
- Polkit for privilege elevation
- No silent sudo - explicit confirmation required
- Session tokens with rotation
- CSRF protection on all forms

## Related Repositories

- [cortex-cli](https://github.com/cortexlinux/cortex-cli) - CLI equivalent
- [cortex-security](https://github.com/cortexlinux/cortex-security) - Auth policies

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

Apache 2.0 - See [LICENSE](LICENSE)
