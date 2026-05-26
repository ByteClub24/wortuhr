# CAD

Fusion-360-Konstruktion der Wortuhr.

## Dateien

- `wortuhr.f3d` — Hauptdatei (kommt sobald exportiert)
- `wortuhr_parameters.csv` — alle User Parameters als CSV, importierbar in Fusion über Parameter ändern → Importieren

## Konstruktionsprinzip

Vollständig parametrisch über User Parameters. Die wichtigsten Eingangsparameter:

| Parameter | Wert | Bedeutung |
|-----------|------|-----------|
| `ledPitch` | 16,6 mm | LED-Abstand |
| `gridCols`, `gridRows` | 10 | Raster |
| `frameWall` | 1,5 mm | Rahmenwand-Dicke |
| `wireMargin` | 10 mm | Verkabelungsrand |
| `gridHeight` | 15 mm | Lichtgitter-Höhe |
| `elecDepth` | 30 mm | Elektronikraum-Tiefe |

Außenmaß und Gesamttiefe ergeben sich automatisch aus diesen Parametern.

## Exports

Druckfertige STLs liegen in `exports/`.
