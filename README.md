# starssystem – Sterne-Belohnungssystem

Kleine Webseite („Sophias Sterne“), mit der ein Kind seine täglichen Aufgaben
abhakt und dafür Sterne sammelt. Die Sterne landen in einem Sparschwein und
lassen sich gegen Belohnungen eintauschen.

Live: <https://starsystem.aininger.com> (Achtung: Domain mit einem „s“, das Repo heißt `starssystem` mit zwei)

## Auf einen Blick

| | |
|---|---|
| Frontend | statisch, eine Datei (`index.html`, ca. 27 KB), GitHub Pages, Domain per `CNAME` |
| Backend | keines |
| Externe Quellen | keine |
| Secrets | keine |
| Speicher | nur im Browser (`localStorage`, Schlüssel `sophia_sterne_data_v1`) |

## Funktionen

- **Aufgaben** in drei Abschnitten (morgens, nachmittags, abends). Jede erledigte Aufgabe gibt einen Stern.
- **Feier-Animationen** pro fertigem Abschnitt und wenn alle Sterne des Tages voll sind.
- **Sparschwein:** Gesamtsumme aller Sterne.
- **Belohnungs-Shop:** Sterne gegen Belohnungen (z. B. Eis, Kino, Bildschirmzeit), mit Bestätigungsdialog und Verlauf der eingelösten Belohnungen.
- **Wochenübersicht** der letzten Tage.

## Daten

Alles liegt im `localStorage` des Browsers, in einem JSON-Objekt:

```json
{ "days": { "JJJJ-MM-TT": { "done": {}, "rewarded": false, "sectionDone": {} } },
  "piggyTotal": 0,
  "redeemed": [] }
```

Folgen davon:

- Die Daten gelten **pro Browser und Gerät**. Anderes Handy oder anderer Browser = anderer Stand.
- Browserdaten löschen oder privater Modus löscht auch die Sterne. Es gibt kein Backup und keinen Export.
- Es werden keine Daten an einen Server gesendet.

## Ändern

Aufgaben und Belohnungen stehen am Anfang des `<script>`-Blocks in `index.html`:

- `TASKS` – Aufgaben je Abschnitt (`id`, `emoji`, `label`)
- `REWARDS` – Belohnungen mit Preis in Sternen (`cost`)
- `STORAGE_KEY` – nicht ändern, sonst sind die gespeicherten Sterne weg

Aufgaben-IDs bleiben stabil, sonst passen alte Einträge nicht mehr zu den Aufgaben.

## Deployment

Kein Build. Änderung in `main` pushen, GitHub Pages (Branch `main`, Ordner `/`) liefert die Seite aus.

## Fallstricke

- Der Tageswechsel nutzt `toISOString()` (UTC). Kurz nach Mitternacht Wiener Zeit kann deshalb noch der Vortag gelten.
- Änderungen an der Datenstruktur brauchen Rücksicht auf bestehende `localStorage`-Daten (daher der Suffix `_v1` im Schlüssel).
