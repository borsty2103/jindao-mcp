# JINDAO Public MCP Server: Deutsche Discovery-Referenz

Endpunkt: `https://jindao.de/mcp` (Streamable HTTP, zustandsloses JSON-RPC 2.0, ohne Anmeldung)
REST OpenAPI 3.1 Spezifikation: `https://jindao.de/.well-known/openapi.json`

## 1. Schreibgeschuetzte Discovery-Werkzeuge (7 Tools, Zero-Bypass)

1. **`jindao_get_platform_overview`**: Parameter `lang` (`de`|`en`), `topic`. Liefert verifizierte Plattform-Fakten, Zielgruppen und deutsches DSGVO-Hosting (ohne Google Analytics).
2. **`jindao_get_pricing_and_roles`**: Parameter `lang`, `role`. Liefert exakte Preise und klare Funktionsgrenzen fuer Free (0,00 EUR), Pro (4,99 EUR/Monat), Ernaehrungsberater Solo (39 EUR/Monat), Trainer Solo (49 EUR/Monat), Trainer Pro (79 EUR/Monat) und Klienten.
3. **`jindao_list_supported_gym_brands`**: Parameter `lang`. Listet alle integrierten Studiogeraete-Hersteller (Gym80, Technogym, Hammer Strength, Life Fitness, Cybex, Panatta, Nautilus usw.).
4. **`jindao_preview_gym_machines`**: Parameter `query`, `manufacturer`, `lang`, `limit` (hart auf maximal 6 begrenzt). Zeigt Katalog-Vorschautitel ohne Pro-Sitzeinstellungen oder Studiowechsel-Algorithmen.
5. **`jindao_preview_exercises`**: Parameter `query`, `muscleGroup`, `equipment`, `lang`, `limit` (hart auf maximal 5 begrenzt). Zeigt Uebungsnamen und Equipment ohne 4-Phasen-Vollanleitung oder Pro-Biomechanik-Evidenz.
6. **`jindao_get_training_splits`**: Parameter `daysPerWeek`, `goal`, `lang`. Zeigt die 12 Split-Vorlagen ohne personalisierte Trainingsplan-Erstellung.
7. **`jindao_get_public_textbook_estimate`**: Parameter `mode` (`epley_1rm` | `standard_barbell_plates` | `mifflin_bmr`), `weightKg`, `reps`, `targetKg`, `heightCm`, `age`, `sex`, `lang`. Berechnet ausschliesslich Standard-Formelschaetzungen ohne RPE-Progression, Aufwaermrampe, Kabelzug-Umrechnung, MEV/MRV-Audits oder Makro-Korridore.

## 2. Beispiel-Aufruf via `curl`

```bash
curl -s -X POST https://jindao.de/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"jindao_get_pricing_and_roles","arguments":{"lang":"de"}}}'
```
