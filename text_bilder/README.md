# text_bilder

Lege hier die Demo-Daten fuer das Notebook ab.

Erwartete Struktur:

```text
text_bilder/
  bilder/
  bilder_mit_boxen/
  bounding_boxen/
```

Regeln:

- Bilddateien in `bilder/`
- Optional vorberechnete Vergleichsbilder in `bilder_mit_boxen/`
- Bounding-Box-Dateien in `bounding_boxen/`
- Dateinamen muessen zusammenpassen, z. B.:
  - `bilder/schrauben_01.jpg`
  - `bounding_boxen/schrauben_01.txt`

Bounding-Box-Format pro Zeile:

```text
<class_id> <x_center_norm> <y_center_norm> <width_norm> <height_norm>
```
