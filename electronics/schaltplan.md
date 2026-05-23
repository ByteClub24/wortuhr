# Schaltplan

Detaillierte Beschreibung folgt.

## Übersicht

- **ESP32 Feather** als Controller, USB-C als Strom + Programmierung
- **NeoPixel Strip Data-In** an einem GPIO mit 470Ω-Schutzwiderstand
- **5V-Versorgung der LEDs** direkt vom USB-C (nicht über den ESP32)
- **GND gemeinsam** zwischen Controller und LEDs
- **LDR** mit 10kΩ-Pulldown an einem ADC-Pin, sitzt hinter einer 0,2mm-Aussparung in der Frontplatte
