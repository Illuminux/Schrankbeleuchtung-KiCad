
# Schrankbeleuchtung mit Raspberry Pi Pico W

## 🔧 Hardware-Komponenten
- **Raspberry Pi Pico W** – Steuerung via PWM und GPIO
- **4x IRLML6344TRPBF MOSFETs** – LED-Treiber, je mit 100 Ω Gate-Widerstand (RQ73C2A100RBTD)
- **4x LED-Streifen (12 V)** – angeschlossen über B2B-XH-AMLFSNP (Pin 1 = 12 V, Pin 2 = Drain)
- **4x Reedkontakte** – angeschlossen über B2B-XH-AMLFSNP (Pin 1 = GPIO, Pin 2 = GND), je mit 10 kΩ Pull-up gegen 3,3 V
- **LM2596SX-5.0NOPB** – 5 V-Festspannungsregler
  - CIN: 470 µF Elko (EEE-FKE101XAL)
  - COUT: 100 µF MLCC (GRM32ER61A107ME0L)
  - Spule: 33 µH (SPM7054VC-330M-D)
  - Schottky-Diode: SS34 (Sperrrichtung gegen GND)

## ⚙️ Funktion
- Reedkontakte erkennen Türöffnung/-schließung
- Pico steuert LED-Fading per PWM
- LED-Streifen werden über MOSFETs geschaltet
- Versorgung: 12 V Netzteil → 5 V über LM2596 für Pico

## 🧠 Zusätzliche Hinweise & Ideen

### Sicherheit & Schutz
- **Verpolungsschutz**: Eine Diode am Eingang des 12 V Netzteils könnte helfen, versehentliche Verpolung zu vermeiden.
- **Sicherung**: Eine kleine Sicherung (z. B. 1 A) in der 12 V-Zuleitung schützt bei Kurzschluss.

### Software-Logik (Pico W)
- Debouncing der Reedkontakte (z. B. per Software mit Zeitverzögerung)
- PWM-Fading mit sanftem Ein-/Ausblenden (z. B. logarithmisch für angenehmeres Licht)
- Optional: WLAN-Funktionalität für Statusüberwachung oder OTA-Updates

### Erweiterungen
- **Helligkeitssensor**: Nur bei Dunkelheit einschalten
- **Taster für manuelle Steuerung**
- **Webinterface**: Steuerung und Statusanzeige über Smartphone

### Dokumentation
- Schaltplan (z. B. mit KiCad oder Fritzing)
- PCB-Layout, falls du eine Platine planst
- Fotos vom Aufbau oder Gehäuse

## 📦 Zusammenfassung als Tabelle (für Doku-Zwecke)

| Komponente               | Funktion                                  |
|--------------------------|-------------------------------------------|
| Raspberry Pi Pico W      | Steuerung, PWM, Reedkontakt-Auswertung    |
| IRLML6344TRPBF (4x)      | MOSFETs zur LED-Ansteuerung               |
| LED-Streifen (4x, 12 V)  | Beleuchtung                               |
| Reedkontakte (4x)        | Türerkennung                              |
| LM2596SX-5.0             | 12 V → 5 V Spannungsregler                |
| Elko 470 µF              | Eingangspuffer für LM2596                 |
| MLCC 100 µF              | Ausgangspuffer für LM2596                 |
| Spule 33 µH              | Teil des Schaltreglers                    |
| Schottky-Diode SS34      | Freilaufdiode / Schutz                    |
