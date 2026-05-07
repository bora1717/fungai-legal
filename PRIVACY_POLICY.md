# Datenschutzerklärung — fungAI

**Stand:** 7. Mai 2026
**Verantwortlich:** Bora Tarlan (tarlanbora2@yahoo.com)
**App:** fungAI (Bundle-ID: `com.bora2012.fungai`)

Diese Datenschutzerklärung informiert dich darüber, welche Daten die App
fungAI ("App", "wir") erhebt, verarbeitet und speichert. Die Verarbeitung
erfolgt nach Artikeln 6, 13, 32 DSGVO sowie den Anforderungen der App
Store / Play Store Richtlinien.

---

## 1. Erhobene Daten

### 1.1 Bild-Daten (Pflicht für Pilzerkennung)
- **Quelle:** Kamera oder Foto-Galerie
- **Zweck:** Klassifikation des fotografierten Pilzes (lokal via TFLite-Modell
  und/oder via Anthropic Claude Vision API)
- **Speicherung:** Bilder werden **nicht dauerhaft gespeichert**. Sie werden
  ausschließlich zur Echtzeit-Inferenz übermittelt und nach der Antwort
  verworfen.
- **Hash-Speicherung:** Zur Betrugs­erkennung wird ein perceptual Hash (pHash,
  64 Bit) deines Bildes in der Datenbank gespeichert. Aus dem Hash kann das
  Originalbild **nicht rekonstruiert werden**.

### 1.2 EXIF-Metadaten
- **Erhoben:** Aufnahmezeit, GPS-Koordinaten (falls vorhanden), Kameramodell,
  Hersteller
- **Zweck:** Validierung gegen Manipulation (Schicht 2 des Anti-Fraud-Systems)
- **Speicherung:** Nur Hash-basierte Auswertung, keine Klartext-EXIF-Daten in
  Langzeit­speicher.

### 1.3 Standort­daten
- **Erhoben:** GPS-Koordinaten zum Zeitpunkt des Scans (Genauigkeit: einige
  Meter)
- **Zweck:** Validierung des Fundortes gegen die GBIF-Datenbank
  (Verbreitungsdaten der erkannten Art) und Anti-Fraud-Schicht 2
- **Speicherung:** Nach erfolgreicher Validierung gelöscht. Keine Bewegungs­profile.

### 1.4 Sensor-Daten (Beschleunigung / Gyroskop)
- **Erhoben:** Während des Live-Kamera-Modus zur Liveness-Prüfung
- **Zweck:** Anti-Fraud-Schicht 1 (verhindert Foto-vom-Bildschirm-Angriffe)
- **Speicherung:** Wird **nicht übertragen oder gespeichert**, ausschließlich
  lokal als Echtheits­merkmal ausgewertet.

### 1.5 Account-Daten
- **Erhoben:** E-Mail (für Login via Supabase Auth), User-ID, Punktestand,
  Achievement-Fortschritt
- **Zweck:** Authentifizierung, Gamification, Score-Speicherung
- **Speicherung:** Bei Supabase (EU-Region), Row-Level-Security aktiv.

### 1.6 Crash- und Fehler­berichte
- **Erhoben:** Nur wenn Sentry konfiguriert ist (`EXPO_PUBLIC_SENTRY_DSN`).
  Stack-Traces, Geräte­modell, OS-Version. **Keine PII** (E-Mail, Klar­name,
  Adresse) wird übermittelt.
- **Zweck:** Stabilitäts­überwachung, Bug-Fixing
- **Auftragsverarbeiter:** Sentry GmbH (DPA gemäß Art. 28 DSGVO)

---

## 2. Datenweitergabe an Dritte

| Empfänger          | Zweck                          | Standort         | Rechtsgrundlage |
|--------------------|--------------------------------|------------------|-----------------|
| Anthropic, PBC     | Claude Vision-Klassifikation   | USA (DPF-konform)| Art. 6(1)(b) DSGVO |
| Supabase Inc.      | Backend / Auth / Storage       | EU (Frankfurt)   | Art. 6(1)(b) DSGVO |
| Sentry GmbH        | Crash-Reporting (optional)     | EU (Deutschland) | Art. 6(1)(f) DSGVO |
| GBIF.org           | Verbreitungs-Lookup (Art-Name) | EU/Global        | Art. 6(1)(b) DSGVO |
| Apple / Google     | App-Distribution               | USA              | Art. 6(1)(b) DSGVO |

Es findet **kein Verkauf** deiner Daten statt. Es gibt **keine
Werbe-Tracking-SDKs** (Facebook, Google Ads, AppsFlyer etc.).

---

## 3. Deine Rechte (DSGVO)

Du hast das Recht auf:
- **Auskunft** (Art. 15) — welche Daten gespeichert sind
- **Berichtigung** (Art. 16) — falscher Daten
- **Löschung** (Art. 17) — komplette Account-Löschung
- **Einschränkung** (Art. 18)
- **Datenübertragbarkeit** (Art. 20) — Export im JSON-Format
- **Widerspruch** (Art. 21)
- **Beschwerde** bei der zuständigen Aufsichts­behörde

**Anfragen:** tarlanbora2@yahoo.com — wir antworten innerhalb von 30 Tagen.

**Account löschen:** Einstellungen → Account → "Account löschen". Alle
zugehörigen Daten (Scans, pHashes, Punkte, Achievements) werden innerhalb
von 30 Tagen unwiderruflich entfernt.

---

## 4. Speicherdauer

| Daten                        | Speicherdauer                                  |
|------------------------------|-----------------------------------------------|
| Bilder (Original)            | 0 Sekunden (nicht persistiert)                 |
| pHash zur Fraud-Detection    | 365 Tage, danach automatisch gelöscht          |
| EXIF (Klartext)              | Nicht gespeichert                              |
| Standort (Klartext)          | Nicht gespeichert                              |
| Standort-Hash für Fraud      | 365 Tage                                       |
| Account-Daten                | Bis zur Account-Löschung                       |
| Crash-Reports (Sentry)       | 90 Tage (Sentry-Default)                       |

---

## 5. Sicherheit

- **Transport:** TLS 1.2+ für alle API-Calls (Supabase, Anthropic, GBIF)
- **At-Rest:** Supabase-Datenbank mit AES-256-Verschlüsselung
- **API-Schlüssel:** Anthropic-Key ist server­seitig (Edge-Functions),
  niemals im Client
- **Authentifizierung:** Supabase Auth (JWT, RLS-Policies)

---

## 6. Kinder

Die App ist für Nutzer ab 13 Jahren bestimmt (Apple) bzw. ab 16 Jahren
(Google, DSGVO). Wir erheben wissentlich keine Daten von Kindern unter
diesem Alter.

---

## 7. Änderungen

Wir behalten uns vor, diese Datenschutz­erklärung zu aktualisieren.
Wesentliche Änderungen werden über die App-Update-Notes kommuniziert.

---

## 8. Kontakt

Bora Tarlan
E-Mail: tarlanbora2@yahoo.com

Aufsichts­behörde: zuständige Landes­datenschutz­behörde am Wohnort des Nutzers.
