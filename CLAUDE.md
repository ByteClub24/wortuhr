# Projekt-Kontext für Claude (Wortuhr)

Diese Datei gibt dir den vollständigen Stand des Projekts. Lies sie zuerst, bevor du arbeitest.

## Wer arbeitet hier

**Thomas**, CEO von easySAAS GmbH, Mitglied im Verein **ByteClub** (byteclub.at). Programmiert nicht aktiv, aber technisch versiert. Lernt gerade Fusion 360 an diesem Projekt.

**Kommunikation:**
- Sprache: **Deutsch**, du-Form
- Stil: **direkt, prägnant, keine Floskeln**. Kein "Großartige Frage!", kein "Gerne helfe ich dir dabei!", kein einleitendes Lob.
- Fusion 360 ist auf **Deutsch** installiert — verwende deutsche Menübezeichnungen (Ändern, Skizze, Konstruieren, Volumenkörper, etc.)
- Auf Vorschläge mit klarer Empfehlung antworten, nicht 5 Optionen auflisten und ihn entscheiden lassen

## Projekt

**Open-Source-Wortuhr** für den ByteClub. 10×10 LED-Raster mit Adafruit NeoPixel Strips, ESP32-basiert, parametrisch in Fusion 360 konstruiert.

**Repo:** github.com/ByteClub24/wortuhr
**Lizenzen:** CC-BY-SA 4.0 (Hardware/CAD/Docs), MIT (Firmware)

## Hardware-Eckdaten

- **LEDs:** Adafruit NeoPixel Strip, 60 LEDs/m, Pitch **16,7 mm** (gemessen)
- **Raster:** 10×10 = 100 LEDs. Oberste Reihe für **Icons** (Müllerinnerung, Stammtisch-Logos), untere 9 Reihen für die Zeit-Buchstaben
- **Buchstaben-Layout:** österreichischer Dialekt ("HOIBE", "OCHT", "ZWO"), liegt als Bild im Projekt
- **Außenmaße:** 195 × 195 × ca. 52 mm
- **Drucker:** Bambu Lab X2D, **0,4 mm Düse, 0,2 mm Layer Height** — alle Maße sind Vielfache von 0,2 mm
- **Controller:** Adafruit ESP32 Feather V2 oder ESP32-S3 Feather (USB-C, WLAN für NTP)
- **Sensor:** LDR GL5528 hinter einer 0,2-mm-Aussparung in der Frontplatte (automatische Nachtdimmung)
- **Strom:** primär USB-C 5V/3A, optional Slimline-Powerbank 20000 mAh im Gehäuse (Always-On-Modus nötig)
- **Verschluss Rückwand:** Heat-Set Inserts M3 (Ruthex) + Schrauben M3×8

## Schichtaufbau (von vorne nach hinten)

1. **Frontplatte** — 2 mm, **Galaxy-violett PLA**. Buchstaben als **0,2 mm Restwand (1 Layer)** für Backlight-Technik. Test vorab: bei abgeschalteter LED dürfen die Buchstaben nicht sichtbar sein. Falls Galaxy-Filament zu transluzent → 0,4 mm Restwand (2 Layer) oder Multi-Material.
2. **Diffusor** — weißes Pauspapier, eingelegt. Spalt im Gehäuse: 0,4 mm.
3. **Lichtgitter** — 15 mm hoch, **weißes PLA** (matt oder glänzend, Hauptsache weiß — entscheidend ist die Reflexion), Stegdicke 1,2 mm (6 Layer, blickdicht). Trennt jede der 100 Zellen lichtdicht. Querstege müssen am unteren Rand eine 0,6-mm-Aussparung (Höhe) × 11,2 mm (Breite) für den darunter durchlaufenden Strip haben.
4. **LED-Trägerplatte** — 2 mm, **schwarz PLA**. Hat 10 horizontale Rillen 0,4 mm tief × 11 mm breit für die NeoPixel-Strips. Links und rechts je 10 mm **Lötkanal** (offen nach oben, im Verkabelungsrand, kein Gitter darüber).
5. **Elektronikraum** — 30 mm tief. Platz für ESP32 + optional Slimline-Powerbank (16 mm dick).
6. **Rückwand** — 2 mm, schwarz. USB-C-Cutout. Wird mit M3-Schrauben in Heat-Set Inserts am Rahmen befestigt.
7. **Rahmen** — umlaufend 4 mm Wandstärke, Außenmaß 195×195 mm. **Falz innen vorne** (1,5 mm tief × 2,5 mm breit) zum Einschieben der Frontplatte von hinten.

**Holzrahmen-Variante (für einen Vereinskollegen):** Statt gedrucktem Rahmen ein Holzrahmen möglich. Konstruktion ist so aufgebaut, dass die inneren Komponenten unverändert bleiben. Holzrahmen muss innen 187×187 mm haben, innen schwarz beizen wegen Lichtaustritt, Anschlag für Frontplatte als 5×5 mm Vierkantleiste statt Falz.

## Verkabelung

- Strips in **Boustrophedon-Layout** (Schlangenverlauf): Reihe 1 → U-Turn rechts → Reihe 2 → U-Turn links → Reihe 3 → ...
- Pro Reihenwechsel 3 Lötbrücken: 5V, GND, DOUT→DIN
- Lötkanal im Verkabelungsrand erlaubt Löten **nach dem Einkleben** der Strips (Zugang von oben, vor Gitter-Montage)
- ESP32 sitzt im Elektronikraum, USB-C-Buchse durch Rückwand

## User Parameters in Fusion (alle drin, importiert aus CSV)

### Atomare Parameter

| Name | Wert | Bedeutung |
|------|------|-----------|
| `ledPitch` | 16,7 mm | LED-Abstand |
| `gridCols`, `gridRows` | 10 | Raster |
| `stripWidth` | 11 mm | Strip-Breite + Toleranz |
| `stripHeightCut` | 0,4 mm | Strip-Höhe an Schneidstelle |
| `ledHeight` | 1,6 mm | LED-Höhe über Strip |
| `ledSize` | 5,5 mm | LED-Kantenlänge |
| `frontThk` | 2,0 mm | Frontplatten-Dicke |
| `letterThk` | 0,2 mm | Buchstaben-Restwand (1 Layer) |
| `diffuserSlot` | 0,4 mm | Spalt für Pauspapier |
| `gridHeight` | 15 mm | Lichtgitter-Höhe |
| `gridWall` | 1,2 mm | Steg-Dicke Gitter |
| `carrierThk` | 2,0 mm | Trägerplatten-Dicke |
| `carrierGroove` | 0,4 mm | Strip-Rille-Tiefe |
| `elecDepth` | 30 mm | Elektronikraum |
| `backThk` | 2,0 mm | Rückwand-Dicke |
| `frameWall` | 4 mm | Rahmenwand |
| `wireMargin` | 10 mm | Verkabelungsrand umlaufend |
| `falzDepth` | 1,5 mm | Falz-Tiefe Frontplatte |
| `falzWidth` | 2,5 mm | Falz-Breite Frontplatte |
| `fitTol` | 0,2 mm | Allgemeine Passungs-Toleranz |
| `insertDia` | 4,2 mm | Heat-Set Lochdurchmesser |
| `insertDepth` | 5 mm | Heat-Set Lochtiefe |

### Abgeleitete (Formeln)

| Name | Ausdruck | Wert |
|------|----------|------|
| `innerSize` | `ledPitch * gridCols` | 167 mm |
| `outerSize` | `innerSize + 2 * wireMargin + 2 * frameWall` | 195 mm |
| `totalDepth` | `frontThk + diffuserSlot + gridHeight + carrierThk + elecDepth + backThk` | 51,4 mm |
| `stripPassage` | `stripHeightCut + fitTol` | 0,6 mm |
| `gridCellSize` | `ledPitch - gridWall` | 15,5 mm |

CSV-Datei im Repo: `cad/wortuhr_parameters.csv`

## Konstruktions-Plan

### Schritt 1 (erledigt)
User Parameters in Fusion angelegt via CSV-Import.

### Schritt 2 (aktuell)
**Master-Layout-Skizze** in der XY-Ebene:
- Außenrechteck `outerSize × outerSize` zentriert um Origin (Rechteck um Mittelpunkt)
- Innenrechteck `innerSize × innerSize` zentriert um Origin (markiert LED-Raster-Bereich)
- Skizze umbenennen in `MASTER_Layout`

### Schritt 3 (geplant)
**Komponente "LED-Trägerplatte"**:
- Neue Komponente erstellen
- Skizze auf XY-Ebene: Außenrechteck = innerer Bereich des Rahmens = `outerSize - 2*frameWall` × dito
- Extrude `carrierThk` nach unten (in -Z)
- 10 Rillen für Strips ausschneiden (Rechteck-Muster über `gridRows`), je `carrierGroove` tief
- Lötkanal links und rechts ausschneiden (10 mm breit × volle Höhe, `carrierGroove` tief)

### Schritt 4 (geplant)
**Komponente "Lichtgitter"** auf der Trägerplatte aufbauen.

### Weitere Schritte
5. Frontplatte (mit Buchstaben-Aussparungen, später)
6. Rahmen (mit Falz und Heat-Set-Löchern)
7. Rückwand (mit USB-C-Cutout)

## Wichtige Detail-Entscheidungen (nicht überschreiben!)

- **Lötkanal nach OBEN offen** (im Verkabelungsrand): erlaubt Löten *nach* dem Einkleben der Strips. Kein Service-Cutout durch die Trägerplatte nach hinten.
- **Strips kleben ZUERST**, dann löten. NICHT umgekehrt.
- **Quersteg-Aussparung im Gitter:** `stripPassage` (0,6 mm) hoch × `stripWidth + fitTol` (11,2 mm) breit am unteren Steg-Rand. So läuft der Strip an Schneidstellen unter dem Steg durch, oben ist der Steg dicht.
- **Innen schwarz, Reflexion weiß:** Trägerplatte und Rückwand schwarz (kein Lichtleiten), Gitter weiß (matt oder glänzend egal — wichtig ist nur die weiße Reflexion).
- **Verschluss Rückwand:** Heat-Set Inserts (entschieden) — NICHT Magnete, nicht Schnappverschluss.
- **Powerbank:** optional, NICHT primär. Auto-Shutoff vieler Powerbanks bei Strömen <80 mA ist ein bekanntes Problem (LDR-Dimmung nachts).

## Was NICHT noch mal diskutieren

Folgende Themen sind durchdiskutiert und entschieden, kein Re-Debate:
- LED-Dichte → 60er gewählt
- Frontplatten-Material → Galaxy-violett, 0,2 mm Restwand (mit Multi-Material als Plan B)
- Lötkanal-Position → in Verkabelungsrand, oben offen
- Verschluss → Heat-Set Inserts
- Stromversorgung → USB-C primär, Powerbank optional

## Offene Punkte / nächste Entscheidungen

- LDR-Position: noch genau festlegen (versteckt in Rand oder als "leere Zelle" im Raster)
- Buchstabenbreite vs. Zellengröße: aktuelle Zellengröße `gridCellSize` = 15,5 mm. Buchstabenhöhe entsprechend ~10 mm (kommt bei der Frontplatten-Konstruktion)
- Konkrete Geometrie für Heat-Set-Aufnahme im Rahmen (Säulchen oder verstärkte Wandstelle)
- Befestigung des ESP32 im Elektronikraum (M2-Säulchen, Klebepads, ...)

## Hinweise für CAD-Anleitung

Wenn Thomas Schritt-für-Schritt-Anleitungen für Fusion bekommt:
- **Deutsche Menünamen** verwenden
- Konkrete Klick-Pfade ("Konstruieren → Skizze erstellen")
- Tastenkürzel angeben wenn praktisch (S, D für Bemaßung, E für Extrude)
- Beim Bemaßen: er soll **Parameternamen statt Zahlen** eingeben (`outerSize` statt `195 mm`)
- Komponenten klar trennen, jede ihre eigene Skizze
- Bottom-up: erst LED-Trägerplatte, dann darüber liegende Schichten

## Repo-Struktur

```
wortuhr/
├── README.md
├── LICENSE              (CC-BY-SA 4.0)
├── LICENSE-FIRMWARE     (MIT)
├── CLAUDE.md            (diese Datei)
├── cad/
│   ├── wortuhr.f3d
│   └── wortuhr_parameters.csv
│   └── exports/
├── docs/
│   ├── aufbau.md
│   ├── stueckliste.md
│   └── druckparameter.md
├── electronics/
└── firmware/
```