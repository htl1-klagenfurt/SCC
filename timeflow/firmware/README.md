# TimeFlow – Firmware

> TimeFlow – ein Projekt des Science Club der HTL1 Lastenstraße Klagenfurt. Siehe [ATTRIBUTION.md](../../ATTRIBUTION.md).

## Entwicklungsumgebung

1. **Arduino IDE** installieren.
2. Unter *Einstellungen → Zusätzliche Boardverwalter-URLs* die ESP8266-Boardunterstützung eintragen und im Boardverwalter **esp8266** installieren.
3. Board **LOLIN(WEMOS) D1 R2 & mini** auswählen.
4. Bibliotheken über die Bibliotheksverwaltung installieren:
   - **MD_MAX72XX** (LED-Matrizen mit MAX7219)
   - eine Bibliothek für den **MPU-6050**, z. B. *Adafruit MPU6050*, oder direkt über `Wire.h` auslesen

## Programmablauf

```
setup()
  Matrizen starten, Helligkeit niedrig einstellen
  Lagesensor starten
  obere Matrix mit Sand füllen

loop()  (etwa alle 20–40 ms)
  1. Beschleunigung lesen  → Richtung „unten“ bestimmen
  2. Richtung um 45° drehen, weil die Matrizen schräg eingebaut sind
  3. jedes Korn einen Schritt bewegen:
       Feld darunter frei?         → nach unten
       sonst schräg links/rechts?  → dorthin
       sonst                       → liegen bleiben
  4. Hals-Timer abgelaufen?        → ein Korn von oben nach unten übergeben
  5. Matrizen neu zeichnen
  6. Touch-Taster abfragen         → Zeit wählen / neu starten
```

## Die wichtigsten Stellschrauben

| Wert | Wirkung |
|---|---|
| Anzahl Körner | wie „voll“ die Uhr ist |
| Hals-Intervall in ms | Laufzeit = Körner × Intervall |
| Bewegungs-Takt in ms | wie flüssig der Sand rieselt |
| Helligkeit 0–15 | Sichtbarkeit und Akkulaufzeit |
| Schwelle Lagesensor | ab welcher Neigung der Sand zu rieseln beginnt |

## Code

Der Programmcode der Workshop-Version wird hier ergänzt. Wer eine eigene Version schreibt, nennt den Science Club der HTL1 Lastenstraße Klagenfurt im Kopfkommentar:

```cpp
/*
 * Basierend auf TimeFlow – ein Projekt des Science Club
 * der HTL1 Lastenstraße Klagenfurt
 * https://github.com/htl1-klagenfurt/SCC  ·  CC BY-NC-SA 4.0
 */
```
