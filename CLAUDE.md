# Hinweise für Claude

Kleine Webseite „Sophias Sterne“ (Sterne-Belohnungssystem): eine einzige `index.html` auf GitHub Pages, kein Backend. Live unter `starsystem.aininger.com` (Domain mit einem „s“, das Repo heißt `starssystem` mit zwei).

## README und Wiki aktuell halten (wichtig)

Die `README.md` ist die einzige Quelle für das interne Wiki (`marioaininger-bot/wiki`). Das Wiki zieht sie jede Nacht vom Branch `main`, schreibt sie aber nie selbst um. Veraltet die README, veraltet das Wiki.

**Passe die README im selben Commit an, wenn du Folgendes änderst:**

- **Funktionen** der Seite (Abschnitte, Feiern, Sparschwein, Shop, Wochenübersicht)
- **Datenstruktur im `localStorage`** (`sophia_sterne_data_v1`) oder dessen Schlüssel
- **Domain** oder Deployment
- Kommt jemals ein **Backend oder eine externe Quelle** dazu, die Tabelle „Auf einen Blick“ und den Datenfluss ergänzen und im Wiki-Repo `docs/architektur.md` und `docs/betrieb/accounts.md` nachtragen.

## Regeln

- **`STORAGE_KEY` nicht ändern** und die Datenstruktur nur abwärtskompatibel erweitern, sonst sind die gespeicherten Sterne im Browser weg. Bei einem Bruch den Schlüssel bewusst hochzählen (`_v2`) und eine Migration einbauen.
- **Aufgaben-IDs** (`TASKS`) bleiben stabil, sonst passen alte Einträge nicht mehr.
- Die Seite hat kein Backend. Nichts an Server schicken, keine externen Skripte laden, keine Tracker.
- Die Seite gehört einem Kind: sparsam mit Namen und persönlichen Angaben in der Doku.
- Sprache der Doku und der Oberfläche: Deutsch (Österreich).
