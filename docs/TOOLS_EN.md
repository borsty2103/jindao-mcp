# JINDAO Public MCP Server: Englische Referenz (Tools, Resources & Prompts)

Endpoint: `https://jindao.de/mcp` (Streamable HTTP, Stateless JSON-RPC 2.0, No Auth)
REST Mirror OpenAPI 3.1: `https://jindao.de/.well-known/openapi.json`

## 1. Tools (Read-Only)

1. **`jindao_get_platform_overview`**: Parameters `lang` (`de`|`en`), `topic` (optional). Returns verified pricing for Free (€0.00), Pro (€4.99/mo, €49.99/yr), Nutritionist Solo (€39/mo), Trainer Solo (€49/mo), Trainer Pro (€79/mo, 0% storefront commission) and Client privacy scopes.
2. **`jindao_search_exercises`**: Parameters `query`, `muscleGroup`, `equipment`, `lang`, `limit` (1..50). Queries all 5,443 exercises.
3. **`jindao_search_gym_machines`**: Parameters `query`, `manufacturer`, `loadingType`, `lang`, `limit` (1..50). Queries 426 commercial machines across 24+ manufacturers.
4. **`jindao_find_machine_substitutes`**: Parameters `machineName` (required), `targetManufacturer`, `lang`. Returns biomechanically compatible substitutes across gym brands.
5. **`jindao_get_muscle_volume_landmarks`**: Parameters `muscle`, `weeklySetsByMuscle` (map of muscle to weekly sets), `lang`. Audits weekly volume across 17 individual muscles (MEV/MAV/MRV).
6. **`jindao_calculate_1rm_and_load_table`**: Parameters `weightKg` (required), `reps` (required), `rpe` (5..10), `lang`. Returns Epley/Brzycki 1RM, percentage table and RPE next weight recommendation.
7. **`jindao_calculate_barbell_plates`**: Parameters `targetKg` (required), `barKg` (default 20), `availablePlatesKg`, `lang`. Returns per-side plates plus 4-stage warm-up ramp.
8. **`jindao_convert_cable_pulley_weight`**: Parameters `weightKg` (required), `fromRatio`, `toRatio`, `lang`. Converts 1:1 / 2:1 / 4:1 cable stack weights.
9. **`jindao_get_training_splits`**: Parameters `daysPerWeek` (1..7), `goal`, `lang`. Filters all 12 training splits.
10. **`jindao_calculate_nutrition_and_body_composition`**: Parameters `weightKg`, `heightCm`, `age` (required), `sex`, `activityFactor`, `goal`, `waistCm`, `neckCm`, `hipCm`, `lang`. Computes BMR, TDEE, macros, US Navy/RFM body fat and FFMI.

## 2. MCP Resources (6)

- `jindao://overview/de` (`text/markdown`)
- `jindao://overview/en` (`text/markdown`)
- `jindao://catalog/brands` (`application/json`)
- `jindao://science/muscle-landmarks` (`application/json`)
- `jindao://science/splits` (`application/json`)
- `jindao://pricing/all` (`application/json`)

## 3. MCP Prompts (4)

- `jindao_coach_client_plan`: Structured coaching assessment and workout planning prompt
- `jindao_gym_switch_transition`: Equipment mapping workflow when switching gyms
- `jindao_rehab_safety_check`: Safe three-phase progression check after medical injury
- `jindao_weekly_volume_audit`: 17-muscle MEV/MAV/MRV weekly set audit

## 4. Quick HTTP Verification (`curl`)

```bash
curl -s -X POST https://jindao.de/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```
