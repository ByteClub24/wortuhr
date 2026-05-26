# Wortuhr

Open-Source-Wortuhr mit 10×10 LED-Raster — ein offenes Vereinsprojekt des [ByteClub](https://byteclub.at).

> Status: 🚧 in Entwicklung. CAD-Konstruktion läuft, Firmware folgt.

## Was ist das?

Eine Wortuhr zeigt die Uhrzeit in geschriebenen Worten an — bei dieser Variante mit österreichischen Dialekt-Begriffen wie *"HOIBE"*, *"OCHT"*, *"ZWO"*. Hinter einer Frontplatte sitzt ein 10×10-Raster aus einzeln ansteuerbaren NeoPixel-LEDs. Die richtigen Buchstaben werden zur passenden Uhrzeit beleuchtet, der Rest bleibt dunkel.

Die oberste Reihe ist für Icons reserviert (z.B. Müllerinnerung, Stammtisch-Hinweis), die unteren 9 Reihen zeigen die Zeit.

## Technische Eckdaten

- **LEDs:** Adafruit NeoPixel Strip, 60 LEDs/m, Pitch 16,7mm
- **Raster:** 10×10 = 100 LEDs
- **Controller:** ESP32 (Adafruit Feather V2 oder ESP32-S3), WLAN-Zeitabgleich via NTP
- **Helligkeitssensor:** LDR für automatische Nachtdimmung
- **Stromversorgung:** USB-C (5V/3A), optional Slimline-Powerbank
- **Außenmaße:** 195 × 195 × ca. 52 mm
- **Druck:** Bambu Lab X2D, 0,4mm Düse, 0,2mm Layer Height

## Aufbau (von vorne nach hinten)

1. **Frontplatte** (2mm, Galaxy-violett PLA) — Buchstaben als 0,2mm-Dünnstellen (Backlight-Technik)
2. **Diffusor** — weißes Pauspapier (0,4mm Spalt)
3. **Lichtgitter** (15mm, weißes PLA — matt oder glänzend, Hauptsache weiß für die Reflexion) — trennt jede LED-Zelle
4. **LED-Trägerplatte** (2mm, schwarz PLA) — mit Strip-Rillen und Lötkanälen
5. **Elektronikraum** (30mm) — ESP32 + optional Powerbank
6. **Rückwand** (2mm) — mit USB-C-Cutout, verschraubt mit Heat-Set M3 Inserts

Details siehe [`docs/aufbau.md`](docs/aufbau.md).

## Druckdaten

| Teil | Filament | Druckzeit |
|------|----------|-----------|
| Lichtgitter | 140 g | 3:30 h |

## Stückliste

Komplette BOM unter [`docs/stueckliste.md`](docs/stueckliste.md).

## Nachbauen

Anleitung folgt, sobald CAD und Firmware fertig sind. Die Konstruktion ist vollständig parametrisch — wer einen anderen LED-Pitch oder eine andere Größe möchte, kann das in Fusion 360 über die User Parameters anpassen.

Variante mit Holzrahmen statt gedrucktem Rahmen ist explizit vorgesehen — siehe `docs/aufbau.md`.

## Verein

Ein offenes Projekt des [ByteClub](https://byteclub.at). Beiträge sind willkommen — Issues und Pull Requests gerne.

## Lizenz

- **Hardware, CAD-Dateien, Dokumentation:** [CC-BY-SA 4.0](LICENSE)
- **Firmware** (sobald da): [MIT](LICENSE-FIRMWARE)
