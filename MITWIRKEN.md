# Mitwirken (Setup + Workflow)

Diese Datei erklaert, wie du dieses Projekt lokal einrichtest und sauber per Pull Request beitragst.

## 1. Konten und Tools

### GitHub-Konto
- Erstelle ein Konto auf GitHub (falls noch nicht vorhanden).
- Richte SSH oder HTTPS fuer Git ein.

### Git installieren
- macOS: `xcode-select --install` (enthaelt Git).
- Windows: Git for Windows installieren.

### GitHub CLI (`gh`) installieren
- macOS (Homebrew): `brew install gh`
- Windows (winget): `winget install --id GitHub.cli`
- Danach anmelden:
  - `gh auth login`

## 2. LaTeX/TeXstudio einrichten

### TeXstudio installieren
- macOS und Windows: TeXstudio von der offiziellen Seite installieren.

### LaTeX-Distribution installieren
- macOS: MacTeX (empfohlen fuer volle Kompatibilitaet).
- Windows: MiKTeX oder TeX Live.

Hinweis:
- Bei MiKTeX am besten "install missing packages on-the-fly" aktivieren.
- Bei TeX Live koennen fehlende Pakete mit `tlmgr` nachinstalliert werden.

## 3. Repository lokal holen

Wenn du direkt im Haupt-Repo mit Schreibrechten arbeitest:
```bash
git clone https://github.com/gemurica/Regelungstechnik-Bibel-Ultra.git
cd Regelungstechnik-Bibel-Ultra
```

Wenn du ohne Schreibrechte arbeitest:
1. Repo auf GitHub forken.
2. Deinen Fork klonen.
3. Spaeter Pull Request gegen `gemurica/Regelungstechnik-Bibel-Ultra` stellen.

## 4. Kompilieren und Pakete pruefen

Hauptdatei ist `main.tex`.

Schnelltest im Terminal:
```bash
latexmk -pdf main.tex
```

Bei Paketfehlern:
- MiKTeX: fehlendes Paket installieren lassen.
- TeX Live: Paket mit `tlmgr` installieren.

In TeXstudio:
- `main.tex` oeffnen.
- Quick Build auf `PdfLaTeX` oder `latexmk` setzen.
- Kompilieren und PDF pruefen.

## 5. Beitrags-Workflow (Pflicht)

`main` ist geschuetzt. Direkte Pushes auf `main` sind blockiert.

Arbeite immer so:
```bash
git checkout -b feature/mein-thema
git add .
git commit -m "Kurze, klare Beschreibung"
git push -u origin feature/mein-thema
```

Dann Pull Request erstellen:
```bash
gh pr create --base main --head feature/mein-thema
```

## 6. Review durch Maintainer

- Der Maintainer prueft den PR (inkl. Render-Check in TeXstudio).
- Erst nach Freigabe wird gemergt.
- Nach Merge Branch loeschen:
  - Remote: `git push origin --delete feature/mein-thema`
  - Lokal: `git branch -d feature/mein-thema`

## 7. Attribution / Fairness

- Lies bitte `LICENSE`, `NOTICE` und `CONTRIBUTING.md`.
- Substantielle Beitraege koennen im `NOTICE` unter "Contributors" ergaenzt werden.

## 8. Hinweis zu Codex

Fuer dieses Projekt ist die Bearbeitung mit Codex oft am einfachsten:
- schnelle Dateiaenderungen,
- direkte Git-Unterstuetzung,
- saubere PR-Vorbereitung.

TeXstudio bleibt weiterhin der beste Schritt fuer den finalen visuellen PDF-Check.
