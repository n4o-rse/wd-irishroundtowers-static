# PRIMER — wd-irishroundtowers-static

Arbeitsplan für `n4o-rse/wd-irishroundtowers-static`. Stand: 2026-11-18 (Gerüst erzeugt mit `tools/new_satellite.py` aus wikibase-static 0.28.1).

Sprache: dieses Dokument ist deutsch, alles andere im Repo (Code, Kommentare, README) ist britisches Englisch.

## Beschlusslage

- Items: every instance of Irish round tower (Q1335799) or of a subclass, as in the WikiProject IrishRoundTowers
- Technik wie `wd-ogham-static`: `import-wikidata --generic --provenance item` (der Wrapper `main.py` setzt beides), `entity_files: false`, `browser_graph: slim`, Präfix `irt`, Deploy über die Action (`deploy: true`).
- Eigene Ids `Q100` ff. und `P100` ff.; die Wikidata-Id steht als Zwilling `P4`.

## Schritte

| Id | Schritt | Stand |
|---|---|---|
| S0 | Gerüst, erster Lauf (`seeds-from-sparql`, `import-wikidata`, `--strict`), Push | offen |
| S2 | `data/crm.csv` (CIDOC-CRM-Anker für die Klassen), `--skip-property` für Rauschen | offen |
| S3 | Seeds prüfen: findet die Abfrage zu viel oder zu wenig? (`data/raw/wikidata-seeds/*.json`, `dist/wikidata-gaps.csv`) | offen |

## Offene Punkte

- `owl:sameAs` der `P4`-Zwillinge auf Wikidata (Paket, S14d).
- Fotos und Beispielabfragen (`queries.yaml`) für Vorträge.
