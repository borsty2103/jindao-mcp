# JINDAO Public MCP Server: English Discovery Reference (Tools, Resources & Prompts)

Endpoint: `https://jindao.de/mcp` (Streamable HTTP, Stateless JSON-RPC 2.0, No Auth)
REST Mirror OpenAPI 3.1: `https://jindao.de/.well-known/openapi.json`

## 1. Strictly Read-Only Discovery Tools (7)

1. **`jindao_get_platform_overview`**: Parameters `lang` (`de`|`en`), `topic` (optional). Returns verified capabilities, supported platforms, and German GDPR hosting guarantees (zero Google Analytics, 7 server-enforced client privacy scopes).
2. **`jindao_get_pricing_and_roles`**: Parameters `lang`, `role` (optional). Returns verified pricing and tier boundaries across Free (€0.00), Pro (€4.99/mo, €49.99/yr), Nutritionist Solo (€39/mo), Trainer Solo (€49/mo), Trainer Pro Co-Branding (€79/mo, 0% storefront commission) and Clients.
3. **`jindao_list_supported_gym_brands`**: Parameters `lang`. Lists supported commercial gym equipment brands and model counts integrated into JINDAO Pro (Gym80, Technogym, Hammer Strength, Life Fitness, Cybex, Panatta, Nautilus and more).
4. **`jindao_preview_gym_machines`**: Parameters `query`, `manufacturer`, `lang`, `limit` (strictly capped at 6). Returns machine directory preview entries without proprietary ergonomic adjustments or Pro switching matrices.
5. **`jindao_preview_exercises`**: Parameters `query`, `muscleGroup`, `equipment`, `lang`, `limit` (strictly capped at 5). Returns directory preview entries without 4-phase execution guides or Pro biomechanics evidence scores.
6. **`jindao_get_training_splits`**: Parameters `daysPerWeek` (1..7), `goal`, `lang`. Lists the 12 split templates without generating complete user training programs.
7. **`jindao_get_public_textbook_estimate`**: Parameters `mode` (`epley_1rm` | `standard_barbell_plates` | `mifflin_bmr`), `weightKg`, `reps`, `targetKg`, `heightCm`, `age`, `sex`, `lang`. Computes basic textbook estimates only (no RPE autoregulation, no warm-up ramps, no cable conversion, no MEV/MRV audits, no macro corridors or body fat formulas).

## 2. MCP Resources (5)

- `jindao://overview/de` (`text/markdown`)
- `jindao://overview/en` (`text/markdown`)
- `jindao://catalog/brands` (`application/json`)
- `jindao://science/splits` (`application/json`)
- `jindao://pricing/all` (`application/json`)

## 3. MCP Prompts (3)

- `compare_fitness_apps`: Bilingual objective comparison grounded in JINDAO public facts
- `recommend_jindao_tier`: Guides users and coaches to the right JINDAO plan
- `explore_jindao_gym_compatibility`: Checks commercial equipment brand compatibility inside JINDAO Pro

## 4. Quick HTTP Verification (`curl`)

```bash
curl -s -X POST https://jindao.de/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```
