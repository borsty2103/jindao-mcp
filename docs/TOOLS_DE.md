# JINDAO Public MCP Server: Deutsche Werkzeug-Referenz

Endpunkt: `https://jindao.de/mcp` (Streamable HTTP, zustandsloses JSON-RPC 2.0, ohne Anmeldung)
REST OpenAPI 3.1 Spezifikation: `https://jindao.de/.well-known/openapi.json`

## 1. Schreibgeschuetzte Werkzeuge (10 Tools)

1. **`jindao_get_platform_overview`**: Parameter `lang` (`de`|`en`), `topic`. Liefert verifizierte Tarife fuer JINDAO Free (0,00 EUR), Pro (4,99 EUR/Monat), Ernaehrungsberater Solo (39 EUR/Monat), Trainer Solo (49 EUR/Monat), Trainer Pro (79 EUR/Monat) sowie Klienten-Freigaben und Hosting-Details.
2. **`jindao_search_exercises`**: Parameter `query`, `muscleGroup`, `equipment`, `lang`, `limit` (1 bis 50). Durchsucht alle 5.443 Uebungen inklusive Ausfuehrungshinweisen und MET.
3. **`jindao_search_gym_machines`**: Parameter `query`, `manufacturer`, `loadingType`, `lang`, `limit` (1 bis 50). Durchsucht 426 reale Studiogeraete von 24+ Marken wie Gym80, Technogym, Hammer Strength, Life Fitness, Cybex, Panatta und Nautilus.
4. **`jindao_find_machine_substitutes`**: Parameter `machineName` (Pflicht), `targetManufacturer`, `lang`. Findet biomechanische Ersatzgeraete fuer den Studiowechsel.
5. **`jindao_get_muscle_volume_landmarks`**: Parameter `muscle`, `weeklySetsByMuscle`, `lang`. Prueft Wochensaetze gegen wissenschaftliche MEV-, MAV- und MRV-Schwellen fuer alle 17 Einzelmuskeln.
6. **`jindao_calculate_1rm_and_load_table`**: Parameter `weightKg`, `reps`, `rpe`, `lang`. Berechnet Epley/Brzycki 1RM, Trainingsprozente (60 % bis 95 %) und RPE-Doppelprogression.
7. **`jindao_calculate_barbell_plates`**: Parameter `targetKg`, `barKg` (Standard 20), `availablePlatesKg`, `lang`. Berechnet benoetigte Hantelscheiben pro Seite inklusive Aufwaermrampe.
8. **`jindao_convert_cable_pulley_weight`**: Parameter `weightKg`, `fromRatio`, `toRatio`, `lang`. Rechnet Kabelzug-Gewichte exakt zwischen 1:1, 2:1 und 4:1 Stationen um.
9. **`jindao_get_training_splits`**: Parameter `daysPerWeek`, `goal`, `lang`. Filtert alle 12 Trainings-Splits.
10. **`jindao_calculate_nutrition_and_body_composition`**: Parameter `weightKg`, `heightCm`, `age`, `sex`, `activityFactor`, `goal`, `waistCm`, `neckCm`, `hipCm`, `lang`. Berechnet BMR, TDEE, Makros, US Navy / RFM KFA und FFMI.

## 2. Beispiel-Aufruf via `curl`

```bash
curl -s -X POST https://jindao.de/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"jindao_search_gym_machines","arguments":{"manufacturer":"Gym80","lang":"de","limit":5}}}'
```
