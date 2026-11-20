# JINDAO Public MCP Server (Bilingual DE & EN)

Official discovery repository for the public, strictly read-only **JINDAO** Model Context Protocol (MCP) server hosted in Germany at `https://jindao.de/mcp`.

> **JINDAO (TRAIN · TRACK · EVOLVE)** covers strength training across **426 modeled commercial gym machines** (24+ brands), **5,443 exercises**, **17 individual muscles (MEV/MAV/MRV)**, doctor-letter medical rehab, adaptive nutrition, and unified workspaces for **Athletes (Free & Pro)**, **Personal Trainers (Solo & Pro)**, **Nutritionists (Solo)** and **Clients**.

---

## English Overview

### Endpoint & Authentication

- **Streamable HTTP Endpoint:** `https://jindao.de/mcp`
- **Transport:** Stateless Streamable HTTP (JSON-RPC 2.0, HTTP/HTTPS)
- **Authentication:** None required (strictly public product/brand discovery, capped previews and textbook estimators; zero access to user accounts, Pro engines, Trainer workspaces or Nutritionist portals)
- **Languages:** Bilingual German (`de`) and English (`en`) across all 7 tools, 5 resources and 3 prompts
- **Discovery Manifests:**
  - MCP Server Card: `https://jindao.de/.well-known/mcp.json`
  - Google A2A Agent Card: `https://jindao.de/.well-known/agent.json`
  - OpenAPI 3.1 REST Spec: `https://jindao.de/.well-known/openapi.json`
  - `llms.txt`: `https://jindao.de/llms.txt` and `https://jindao.de/llms-full.txt`
- **Documentation:** [TOOLS_EN.md](./docs/TOOLS_EN.md) and [TOOLS_DE.md](./docs/TOOLS_DE.md)

### Client Quickstart Configuration

#### Cursor / VS Code / Antigravity / Windsurf (`mcp.json`)

```json
{
  "mcpServers": {
    "jindao": {
      "type": "streamable-http",
      "url": "https://jindao.de/mcp"
    }
  }
}
```

#### Claude Desktop (`claude_desktop_config.json`) via `mcp-remote`

```json
{
  "mcpServers": {
    "jindao": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://jindao.de/mcp"]
    }
  }
}
```

### Included Read-Only Discovery Tools (7)

| Tool | Purpose |
| :--- | :--- |
| `jindao_get_platform_overview` | Verified platform facts, supported roles and German GDPR hosting overview |
| `jindao_get_pricing_and_roles` | Live Free, Pro, Nutritionist Solo, Trainer Solo, Trainer Pro and Client consent scope comparison |
| `jindao_list_supported_gym_brands` | Supported commercial gym equipment brands and model counts (full Gym Twin in JINDAO Pro) |
| `jindao_preview_gym_machines` | Capped directory preview (max 6 items) without proprietary ergonomic setups or resistance curves |
| `jindao_preview_exercises` | Capped directory preview (max 5 items) without full 4-phase coaching guides or Pro evidence scores |
| `jindao_get_training_splits` | High-level catalog of all 12 training split templates without generating user workout plans |
| `jindao_get_public_textbook_estimate` | Basic textbook formulas only: Epley 1RM, standard 20 kg barbell plate split or Mifflin-St Jeor BMR |

---

## Deutscher Ueberblick

Der oeffentliche **JINDAO MCP Server** stellt KI-Assistenten, IDEs und Sprachmodellen verifizierte Produktfakten, Tarife, Herstellerlisten, begrenzte Katalogvorschauen und drei einfache Basisformeln unter `https://jindao.de/mcp` schreibgeschuetzt bereit. Geschuetzte Konto-, Pro-, Trainer- und Ernaehrungsberater-Funktionen bleiben vollstaendig hinter Login und Lizenz geschuetzt.

- **Ausfuehrliche deutsche Werkzeug-Referenz:** [docs/TOOLS_DE.md](./docs/TOOLS_DE.md)

---

## Privacy & Security Guarantee

- This repository is strictly a **public discovery and schema package**. It contains zero proprietary application source code or user data.
- `https://jindao.de/mcp` cannot access private user records and cannot bypass JINDAO account registration, Pro, Trainer or Nutritionist paywalls.
- Hosted in Germany (`jindao.de` and Frankfurt `europe-west3`) with zero Google Analytics.
