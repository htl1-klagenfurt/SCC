# TimeFlow – Firmware

> TimeFlow – ein Projekt des Science Club der HTL1 Lastenstraße Klagenfurt. Siehe [ATTRIBUTION.md](../../ATTRIBUTION.md).

Der Code liegt in [`SCC_Sanduhr_Main_Code_02/`](SCC_Sanduhr_Main_Code_02/). Er enthält alle vier Modi (Sanduhr, Uhr & Wecker, Info, Easter Egg mit Animationen und Labyrinth).

## Installation

1. **Arduino IDE** installieren.
2. Unter *Einstellungen → Zusätzliche Boardverwalter-URLs* die ESP8266-Boardunterstützung eintragen und im Boardverwalter **esp8266** installieren.
3. Board **LOLIN(WEMOS) D1 R2 & mini** wählen.
4. Bibliotheken über die Bibliotheksverwaltung installieren:
   - **LedControl** (LED-Matrizen mit MAX7219)
   - **MPU6050** (Lagesensor, `MPU6050.h`)
   - **RTClib** von Adafruit (Echtzeituhr DS1307)
   - **DHT sensor library** von Adafruit (DHT22)
5. Den Ordner `SCC_Sanduhr_Main_Code_02` öffnen und hochladen.

## Pins

| Funktion | Pin |
|---|---|
| Matrix DIN / CS / CLK | D8 / D3 / D0 |
| Touch-Taste 1 / 2 | D5 / D6 |
| DHT22 | D4 |
| Buzzer | D7 |
| I²C SCL / SDA (MPU-6050 auf 0x69, DS1307) | D1 / D2 |

## Stellschrauben im Code

| Konstante | Wirkung |
|---|---|
| `N_SAND` | Anzahl der Sandkörner (Standard 32) |
| `SAND_INTERVAL` | Millisekunden zwischen zwei Sand-Schritten |
| `SHAKE_THRESHOLD` | wie stark geschüttelt werden muss |
| `DISPLAY_0_ROTATION`, `DISPLAY_1_ROTATION` | Ausrichtung der beiden Matrizen |
| `hourglass_hours/minutes/seconds` | Standard-Laufzeit beim Einschalten (5 s) |

Eigene Versionen bitte mit dem Kopfkommentar zur Namensnennung weitergeben (siehe erste Zeilen der `.ino`-Datei).
