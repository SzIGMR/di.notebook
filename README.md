# di.notebook

Testumgebung fuer oeffentliche Demo-Notebooks rund um `di.monta`, ausgelegt fuer [Notebook.link](https://notebook.link/).

## Ziel

Dieses Repository soll Notebooks enthalten, die direkt aus GitHub im Browser gestartet werden koennen, damit sich Demo-Flows ohne lokale Installation zeigen lassen.

Der aktuelle Demo-Fall ist bewusst einfach und robust:

- Bilder aus dem Repository laden
- YOLO-formatierte Bounding-Box-Dateien einlesen
- Boxen im Notebook direkt auf dem Originalbild visualisieren

## Notebook.link Setup

Dieses Repo ist Notebook.link-ready ueber:

- `.nblink/environment.yml`
- `.nblink/jupyter-lite.json`
- Notebooks unter `notebooks/`

Nach dem Push kann das Repo direkt ueber eine URL nach diesem Muster geoeffnet werden:

```text
https://notebook.link/github.com/<owner>/<repo>/
```

Ein konkretes Notebook kann dann im Dateibrowser geoeffnet oder ueber einen Link mit Default-Dokument referenziert werden.

## Aktuelle Demo-Struktur

Das Notebook sucht standardmaessig zuerst nach `text_bilder/` und faellt, falls nicht vorhanden, auf `test_bilder/` zurueck.

Erwartete Struktur:

```text
text_bilder/
  bilder/
    bild_1.jpg
    bild_2.png
  bilder_mit_boxen/
    bild_1.jpg
    bild_2.png
  bounding_boxen/
    bild_1.txt
    bild_2.txt
```

Die `.txt`-Dateien werden im YOLO-Format erwartet:

```text
<class_id> <x_center_norm> <y_center_norm> <width_norm> <height_norm>
```

Beispiel:

```text
0 0.803172 0.699833 0.026750 0.033167
0 0.831781 0.457708 0.019281 0.024875
```

Das Notebook zeichnet daraus die Boxen selbst auf das Originalbild. Falls unter `bilder_mit_boxen/` bereits vorberechnete Vergleichsbilder liegen, werden diese zusaetzlich angezeigt.

## Sichtbarkeit

- Oeffentliche GitHub-Repositories lassen sich direkt ueber Notebook.link oeffnen.
- Private Repositories koennen ueber die Notebook.link GitHub App freigegeben werden.
- Aber: Jeder mit dem erzeugten Notebook.link kann den freigegebenen Inhalt sehen und herunterladen.

Fuer private Repositories gilt zusaetzlich:

- Links werden ueber Commit-Hashes erstellt
- die Freigabe ist nicht "nur fuer eingeloggte Berechtigte" im klassischen Sinn

## Struktur

```text
.nblink/
  environment.yml
  jupyter-lite.json
notebooks/
  00_screw_detection_demo.ipynb
text_bilder/
  README.md
test_bilder/
  ...
```

## Notebook.link starten

Nach dem Push auf GitHub kannst du das Repo direkt ueber folgende Form oeffnen:

```text
https://notebook.link/github.com/<owner>/<repo>/
```

Dann im Dateibrowser:

1. `notebooks/00_screw_detection_demo.ipynb` oeffnen
2. Zellen ausfuehren
3. Bild aus der Tabelle oder Vorschau waehlen

## Naechster sinnvoller Schritt

Wenn du die Demo befuellen willst, brauchst du nur:

1. einen Ordner `text_bilder/` im Repo anlegen oder den bestehenden Datensatz von `test_bilder/` dorthin uebernehmen
2. Originalbilder in `text_bilder/bilder/` ablegen
3. zu jedem Bild eine gleichnamige `.txt`-Datei in `text_bilder/bounding_boxen/` ablegen
4. optional Vergleichsbilder mit bereits eingezeichneten Boxen in `text_bilder/bilder_mit_boxen/` hinterlegen
