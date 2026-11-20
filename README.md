# JINDAO Public MCP Server (Bilingual DE & EN)

Official discovery repository for the public, strictly read-only **JINDAO** Model Context Protocol (MCP) server hosted in Germany at `https://jindao.de/mcp`.

> **JINDAO (TRAIN · TRACK · EVOLVE)** covers strength training across **426 modeled commercial gym machines** (24+ brands), **5,443 exercises**, **17 individual muscles (MEV/MAV/MRV)**, doctor-letter medical rehab, adaptive nutrition, and unified workspaces for **Athletes (Free & Pro)**, **Personal Trainers (Solo & Pro)**, **Nutritionists (Solo)** and **Clients**.

---

## English Overview

### Endpoint & Authentication

- **Streamable HTTP Endpoint:** `https://jindao.de/mcp`
- **Transport:** Stateless Streamable HTTP (JSON-RPC 2.0, HTTP/HTTPS)
- **Authentication:** None required (100% public, zero private user data, read-only annotations on every tool)
- **Languages:** Bilingual German (`de`) and English (`en`) across all tools, resources and prompts
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

### Included Read-Only Tools (10)

| Tool | Purpose |
| :--- | :--- |
| `jindao_get_platform_overview` | Verified capabilities, roles (Free, Pro, Trainer, Nutritionist, Client), pricing and GDPR hosting facts |
| `jindao_search_exercises` | Search 5,443 exercises by query, muscle group or equipment with DE/EN cues and MET |
| `jindao_search_gym_machines` | Search 426 commercial machines (Gym80, Technogym, Hammer Strength, Life Fitness, Cybex, Panatta, Nautilus) |
| `jindao_find_machine_substitutes` | Find biomechanical gym-switch substitutes for any machine |
| `jindao_get_muscle_volume_landmarks` | Query 17 individual muscles (MEV/MAV/MRV) and audit weekly working sets |
| `jindao_calculate_1rm_and_load_table` | Estimate Epley/Brzycki 1RM, percentage table and RPE progression weight |
| `jindao_calculate_barbell_plates` | Exact per-side barbell plate decomposition plus 4-stage warm-up ramp |
| `jindao_convert_cable_pulley_weight` | Convert cable pulley stations (1:1, 2:1, 4:1) preserving true handle tension |
| `jindao_get_training_splits` | Filter all 12 training splits by weekly frequency or goal |
| `jindao_calculate_nutrition_and_body_composition` | Compute BMR, TDEE, macro targets, US Navy/RFM body fat percentage and FFMI |

---

## Deutscher Ueberblick

Der oeffentliche **JINDAO MCP Server** stellt KI-Assistenten, IDEs und Sprachmodellen verifizierte Fakten und Sportwissenschafts-Rechner unter `https://jindao.de/mcp` schreibgeschuetzt und ohne Anmeldung bereit:

- **426 reale Studiogeraete** von 24+ Marken inklusive Studio-Zwilling und Kabelzug-Umrechnung (`1:1`, `2:1`, `4:1`)
- **5.443 Uebungen**, **17 Einzelmuskeln** (MEV/MAV/MRV), **12 Trainings-Splits** und **6 Rechner**
- **Alle Rollen abgebildet:** Athleten (Free & Pro), Trainer (Solo & Pro mit Co-Branding), Ernaehrungsberater (Solo) und Klienten (7 serverseitig erzwungene Datenschutz-Freigaben)
- **Ausfuehrliche deutsche Werkzeug-Referenz:** [docs/TOOLS_DE.md](./docs/TOOLS_DE.md)

---

## Privacy & Security Guarantee

- This repository is strictly a **public discovery and schema package**. It contains zero proprietary application source code or user data.
- `https://jindao.de/mcp` has zero database access to user workouts, health metrics, client messages or billing records.
- Hosted in Germany (`jindao.de` and Frankfurt `europe-west3`) with zero Google Analytics.
