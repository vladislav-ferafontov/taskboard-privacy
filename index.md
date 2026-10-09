# Datenschutzerklärung — Taskboard

**Stand:** 9. Oktober 2026  
**Status:** Entwurf auf Basis der tatsächlichen App-Implementierung. Abschnitte mit dem Hinweis **[ANGABE ERFORDERLICH]** oder **[RECHTLICHE PRÜFUNG ERFORDERLICH]** sind unvollständig oder müssen rechtlich bestätigt werden, bevor diese Erklärung veröffentlicht wird.

---

## 1. Verantwortlicher

Verantwortlich für die Verarbeitung personenbezogener Daten im Sinne der Datenschutz-Grundverordnung (DSGVO) ist:

**[ANGABE ERFORDERLICH — vollständiger gesetzlicher Name des Unternehmens]**  
**[ANGABE ERFORDERLICH — Anschrift]**  
**[ANGABE ERFORDERLICH — E-Mail-Adresse für Datenschutzanfragen]**  
**[ANGABE ERFORDERLICH — ggf. Telefon]**

**Datenschutzbeauftragter (falls bestellt):**  
**[ANGABE ERFORDERLICH — Name und Kontaktdaten, oder „nicht bestellt“]**

---

## 2. Gegenstand dieser Erklärung

Diese Datenschutzerklärung beschreibt die Verarbeitung personenbezogener Daten bei Nutzung der nativen App **Taskboard** (iOS / iPadOS / macOS, Bundle-ID `de.taaskboard.app`).

Taskboard ist eine **interne Betriebsanwendung** für Mitarbeiter und Administratoren eines Unternehmens. Sie dient der Verwaltung von Aufgaben, Schichten, Mitarbeiterdaten, Kiosk-Anmeldungen sowie der Steuerung von Restaurantmusik über Soundtrack Your Brand.

Die App richtet sich nicht an die allgemeine Öffentlichkeit als Verbraucherprodukt.

---

## 3. Überblick: Welche Daten werden verarbeitet?

Die App verarbeitet personenbezogene Daten nur, soweit dies für den Betrieb der genannten Funktionen erforderlich ist. Es wurden **keine Analytics-, Werbe- oder Tracking-SDKs** im Quellcode festgestellt.

### 3.1 Konten und Authentifizierung

| Daten | Zweck | Rechtsgrundlage (**[RECHTLICHE PRÜFUNG ERFORDERLICH]**) |
|-------|--------|----------------------------------------------------------|
| E-Mail-Adresse | Anmeldung, Passwort-Zurücksetzen, Kontoverwaltung | Art. 6 Abs. 1 lit. b / f DSGVO (Vertrag / berechtigtes Interesse an sicherem Zugang) |
| Passwort | Authentifizierung (wird über Supabase Auth verarbeitet; nicht im Klartext in der App persistiert) | wie oben |
| Anzeigename / vollständiger Name | Profil, Registrierung von Unternehmen, Sign in with Apple | wie oben |
| Benutzer-ID (Supabase Auth UUID) | Zuordnung zu Unternehmen, Rollen, Mitarbeiterdatensatz | wie oben |
| Sitzungs-Token (Access-/Refresh-Token) | Aufrechterhaltung der Anmeldung | wie oben |
| Apple-Identity-Token / Nonce (bei „Mit Apple anmelden“) | Anmeldung über Sign in with Apple | wie oben; zusätzlich Verarbeitung durch Apple gemäß deren Bedingungen |

Rollen in der App: Administrator, Mitarbeiter, Kiosk.

### 3.2 Unternehmens- und Mitgliedschaftsdaten

| Daten | Zweck |
|-------|--------|
| Unternehmensname | Zuordnung des Kontos zu einem Betrieb |
| Mitgliedschaftsrolle | Zugriffskontrolle (Admin / User / Kiosk) |

### 3.3 Mitarbeiterstammdaten (Administratorfunktion)

Soweit von Administratoren erfasst, können u. a. verarbeitet werden:

- Vorname, Nachname  
- Geburtsdatum  
- Foto (Mitarbeiterprofil)  
- PIN (für Kiosk-Anmeldung; in der Datenbank gespeichert)  
- Gruppenzugehörigkeit, Rolle, Aktivitätsstatus, Kalenderfarbe  
- Mobiltelefon, Adresse, persönliche E-Mail  
- Bankverbindung  
- Geburtsort, Geschlecht, Staatsangehörigkeit  
- Ausweis-/Arbeitserlaubnis-/Identifikationsnummern  
- Notfallkontakt (Name, Telefon)  
- Familienstand, Anzahl Kinder  
- Mitarbeiterdokumente (z. B. Ausweis, Arbeitserlaubnis) als Datei-Uploads  

**[RECHTLICHE PRÜFUNG ERFORDERLICH]:** Speicherung von Ausweisdaten, Bankdaten und besonderen Kategorien personenbezogener Daten kann besondere rechtliche Anforderungen (z. B. Art. 9 DSGVO, nationale Arbeits-/Sozialvorschriften) auslösen. Die hier genannten Felder existieren in der Implementierung; ob und in welchem Umfang sie in Ihrem Betrieb tatsächlich genutzt werden, muss in der Praxis und rechtlich bestätigt werden.

### 3.4 Aufgaben und Anhänge

| Daten | Zweck |
|-------|--------|
| Aufgabentitel, Beschreibungen, Status, Zuweisungen | Betriebsorganisation |
| Fotos und Videos als Aufgabenanhänge | Dokumentation der Aufgabenerfüllung |
| Übertragungen / Voraussetzungen von Aufgaben | Arbeitsabläufe |

Kamerazugriff, Mikrofon (für Video) und Fotobibliothek werden nur für Anhänge und Mitarbeiterprofile angefordert, soweit der Nutzer diese Funktionen nutzt.

### 3.5 Schichten und Statistik

Verarbeitet werden Schichtpläne, Vorlieben, Tauschwünsche, Beschäftigungsarten, Betriebszeiten sowie daraus abgeleitete statistische Auswertungen innerhalb des Unternehmenskontexts.

### 3.6 Soundtrack Your Brand (Musiksteuerung)

Wenn Nutzer die Geräte-/Musikfunktion nutzen:

| Daten | Zweck |
|-------|--------|
| Soundtrack-Zugangsdaten (E-Mail/Passwort zur Soundtrack-Anmeldung) | Anmeldung beim Soundtrack-Dienst (Passwort wird nicht dauerhaft in der App gespeichert) |
| Soundtrack Access- und Refresh-Token | Sitzung; Speicherung im **iOS-/macOS-Keychain** auf dem Gerät |
| Sound-Zone-IDs und Gerätenamen | Auswahl und Steuerung von Lautsprecherzonen |
| Gerätezuordnung (lokal in UserDefaults) | Merken konfigurierter Geräte auf dem Gerät |

Kommunikation erfolgt mit den Servern von Soundtrack Your Brand (`api.soundtrackyourbrand.com`, inkl. WebSocket).

### 3.7 Lokale Gerätespeicherung

| Speicher | Inhalt |
|----------|--------|
| Keychain | Kiosk-Mitarbeiter-Session-ID; Soundtrack-Sitzungstoken |
| UserDefaults | Kennzeichnung einer laufenden Passwort-Wiederherstellung; lokal gespeicherte Soundtrack-Gerätekonfiguration |
| System-Keychain / Auth-Speicher der Supabase-SDK | Auth-Sitzung (gemäß supabase-swift) |

---

## 4. Speicherung und Empfänger

### 4.1 Supabase (Backend)

Primärer Backend-Dienst ist **Supabase** (Projekt-URL in der App-Konfiguration: Host `*.supabase.co`).

Dort werden u. a. gespeichert:

- Auth-Benutzer und Sitzungen  
- Unternehmens-, Mitgliedschafts- und Profildaten  
- Mitarbeiterdaten und Dokumente  
- Aufgaben und Anhänge  
- Schichtdaten  

**Storage-Buckets (laut Implementierung):**

- `employee-photos`  
- `employee-documents`  
- `task-attachments`  

**[ANGABE ERFORDERLICH]:** Region / Standort des Supabase-Projekts (z. B. EU / Frankfurt).  
**[RECHTLICHE PRÜFUNG ERFORDERLICH]:** Auftragsverarbeitungsvertrag (Art. 28 DSGVO) mit Supabase und ggf. Standardvertragsklauseln bei Drittlandtransfer.

Supabase verarbeitet Daten als Auftragsverarbeiter im Auftrag des Verantwortlichen, soweit ein entsprechender Vertrag besteht.

### 4.2 Edge Functions

Serverseitige Funktionen (u. a. `admin-create-user`, `delete-own-account`) laufen in der Supabase-Infrastruktur und nutzen den Service-Role-Schlüssel **nur serverseitig**, nicht in der App.

### 4.3 Apple

Bei Nutzung von „Mit Apple anmelden“ werden Authentifizierungsdaten an Apple übermittelt. Es gelten zusätzlich die Datenschutzbestimmungen von Apple.

### 4.4 Soundtrack Your Brand

Bei Nutzung der Musiksteuerung werden Anmeldedaten und Steuerungsbefehle an Soundtrack Your Brand übermittelt. Es gelten zusätzlich deren Datenschutzbestimmungen.

**[ANGABE ERFORDERLICH]:** Link zur Datenschutzerklärung von Soundtrack Your Brand, sofern veröffentlicht.

### 4.5 Keine Werbung / kein Tracking

In der geprüften Codebasis wurden keine Drittanbieter-SDKs für Werbung, Analytics oder Tracking festgestellt. Einzige spezifizierte Swift-Package-Abhängigkeit der App ist **supabase-swift** (inkl. zugehöriger Open-Source-Hilfsbibliotheken).

---

## 5. Speicherdauer

Die App selbst enthält **keine fest kodierten Löschfristen** für Serverdaten.

| Kategorie | Bekannter Umgang |
|-----------|------------------|
| Auth-Sitzung | Bis Abmeldung, Token-Ablauf oder Löschung des Kontos |
| Soundtrack-Token (Keychain) | Bis Abmeldung von Soundtrack oder Löschung der App-Daten |
| Kiosk-Session (Keychain) | Bis Idle-Timeout / Abmeldung / App-Datenlöschung |
| Serverdaten (Mitarbeiter, Aufgaben, Schichten, Dateien) | **[ANGABE ERFORDERLICH — interne Aufbewahrungsfristen]** |
| Kontolöschung | Nutzer können in den Einstellungen „Konto löschen“ auslösen. Dabei werden Auth-Konto, Profil und Mitgliedschaften entfernt und Mitarbeiterverknüpfungen gelöst. **Unternehmensdaten anderer Mitarbeiter bleiben erhalten.** |

**[RECHTLICHE PRÜFUNG ERFORDERLICH]:** Konkrete Lösch- und Aufbewahrungskonzepte (gesetzliche Aufbewahrungspflichten im Arbeits-/Steuerrecht).

---

## 6. Rechte der betroffenen Personen

Betroffene Personen haben nach Maßgabe der DSGVO insbesondere folgende Rechte:

- Auskunft (Art. 15)  
- Berichtigung (Art. 16)  
- Löschung (Art. 17)  
- Einschränkung der Verarbeitung (Art. 18)  
- Datenübertragbarkeit (Art. 20)  
- Widerspruch (Art. 21)  
- Beschwerde bei einer Aufsichtsbehörde  

Zur Ausübung dieser Rechte wenden Sie sich an die unter Abschnitt 1 genannte Kontaktadresse. Innerhalb der App kann das eigene Anmeldekonto unter **Einstellungen → Konto löschen** gelöscht werden (soweit die zugehörige Serverfunktion verfügbar ist).

**[ANGABE ERFORDERLICH]:** Zuständige Datenschutz-Aufsichtsbehörde (falls bekannt / gewünscht).

---

## 7. Sicherheit

- Kommunikation mit Supabase und Soundtrack erfolgt über HTTPS bzw. WSS.  
- Sensible Sitzungsdaten (Kiosk-Session, Soundtrack-Token) werden im Keychain gespeichert.  
- Die App enthält den **öffentlichen** Supabase-Anon-Key (üblich für Client-Apps); der Schutz der Daten hängt von serverseitigen Regeln (Row Level Security) und Admin-Funktionen ab.  
- Der Service-Role-Schlüssel wird **nicht** in der App ausgeliefert.

**[RECHTLICHE PRÜFUNG ERFORDERLICH]:** Technische und organisatorische Maßnahmen (TOM) Ihres Betriebs ergänzen.

---

## 8. Pflichtangaben / Berechtigungen auf dem Gerät

Die App kann folgende Systemberechtigungen anfordern:

- Kamera — Fotos/Videos für Anhänge und Profile  
- Mikrofon — Videoaufnahmen bei Aufgabenanhängen  
- Fotobibliothek — Auswahl von Medien  

Ohne Nutzung der jeweiligen Funktion werden diese Zugriffe nicht benötigt.

---

## 9. Minderjährige

Die App ist für den betrieblichen Einsatz durch Mitarbeiter vorgesehen.  
**[ANGABE ERFORDERLICH]:** Ggf. Klarstellung, dass die App nicht für Personen unter 16 Jahren bestimmt ist (oder abweichende Altersgrenze).

---

## 10. Änderungen

Wir können diese Datenschutzerklärung anpassen, wenn sich die App, die Infrastruktur oder rechtliche Anforderungen ändern. Die jeweils aktuelle Fassung wird unter der öffentlichen URL dieser Erklärung bereitgestellt.

---

## 11. Quellen dieser Beschreibung (Transparenzhinweis)

Diese Erklärung wurde aus der Implementierung der Taskboard-App abgeleitet (Auth, Mitarbeiter-, Aufgaben-, Schicht- und Soundtrack-Module, Storage-Buckets, Edge Functions, Privacy Manifest). Sie ersetzt **keine** anwaltliche Beratung.

---

## Fehlende Angaben (Checkliste vor Veröffentlichung)

Bitte ergänzen Sie vor dem Publizieren:

1. Gesetzlicher Firmenname  
2. Anschrift  
3. Datenschutz-Kontakt-E-Mail  
4. Datenschutzbeauftragter (oder Vermerk „nicht bestellt“)  
5. Supabase-Region / Hosting-Standort  
6. Aufbewahrungsfristen für Mitarbeiter-, Aufgaben- und Schicht­daten  
7. Bestätigung der Rechtsgrundlagen durch eine juristische Prüfung  
8. Link zur Datenschutzerklärung von Soundtrack Your Brand (falls vorhanden)  
9. Zuständige Aufsichtsbehörde (optional, aber üblich)  
10. Altersangabe / Zielgruppe
