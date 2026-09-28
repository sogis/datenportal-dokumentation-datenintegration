# Übernahme der Lieferantenanleitung

Quelle: `Anleitung_Datenlieferanten_V0_1.docx`, Patrick Balles, AFIN, Mai 2026;
Kommentare von Stefan Ziegler vom 14. August 2026. Abgleich: 28. September 2026.
Die organisatorischen Aussagen gelten gemäss Bestätigung des Auftraggebers als
verbindlich. Technische Vorgaben und Implementierung haben bei Abweichungen
Vorrang. Diese Matrix ist ein redaktioneller Nachweis, kein Teil der Website.

## Word-Abschnitte

| Abschnitt | Ziel in `docs/biblios` | Behandlung |
| --- | --- | --- |
| Vorspann: Zielgruppe, Unterstützung | `master.adoc`, `fragen_und_unterstuetzung.adoc` | Übernommen; Kontakte zentral statt mehrfach aufgeführt. |
| 1: Was ist das Datenportal? | `einstieg.adoc` | Zweck, ergänzende Portale und Rollen übernommen. |
| 2: Voraussetzungen | `einstieg.adoc` | Als Checkliste übernommen; CSV als einziges Datenanlieferungsformat präzisiert; A-Feldnummern durch sichtbare Feldnamen ersetzt. |
| 3: Publikationsprozess | `publikationsprozess.adoc` | Sieben Schritte und Zuständigkeiten übernommen; formelle AFIN-Freigabe, technische Publikation und Sichtbarkeit im Portal getrennt. Einrichtung durch AGI statt pauschal ein neuer GRETL-Job je Datensatz. |
| 4: Datenformat | `datenaufbereitung.adoc`, `datenformat_datenstruktur.adoc` | Bestehende technische Referenz führt. Keine zusätzliche XLSX-/Parquet-Lieferung; keine verpflichtende Versionierung im Dateinamen. Bereinigte Dateinamen empfohlen; Attributnamen separat verbindlich. Beobachtungsbezogene Hinweisspalten gemäss Repo bleiben erlaubt. |
| 5: Metadatenformular | `metadaten.adoc` | Fachliche Angaben übernommen, mit aktuellem Editor abgeglichen. Keine Zusage «21 Felder / 8 Pflichtfelder» oder ungeprüfte Automatikliste. Attributbeschreibungen hervorgehoben. Ergänzende Angaben aufgenommen; keine automatische I14Y-Publikation zugesagt. |
| 6: Aktualisierung | `datenanlieferung.adoc` | Intervalle, AFIN-Erinnerungen, Meldung von Inhalts-/Methodenänderungen und erneute Abstimmung bei Strukturänderungen übernommen. CSV-, Metadaten- und gemeinsame Lieferung unterschieden. |
| 7: FAQ | `fragen_und_unterstuetzung.adoc` | Fragen und Antworten übernommen und gebündelt; Rückmelde- und Erfahrungszeiten aus Word erhalten. Frage zur verzögerten Portalsichtbarkeit ergänzt. |
| 8: Kontakt | `fragen_und_unterstuetzung.adoc` | Beide Ansprechpersonen mit E-Mail und Telefonnummer sowie Portaladresse übernommen. |

## Sämtliche Word-Kommentare

Die IDs sind die originalen Word-IDs; Lücken in der Nummerierung sind keine
fehlenden Kommentare. Alle neun Kommentare waren im Dokument offen.

| ID | Aussage | Ziel und Umsetzung |
| --- | --- | --- |
| 0 | CSV ist momentan das einzig unterstützte Format. | Einstieg, technische Referenz und FAQ: CSV für Daten, XTF/XML separat für Metadaten. |
| 1 | Einfache Webseite zur Metadatenerfassung vorgesehen. | Metadaten: vorhandenen Datenblatt-Editor mit Import, lokalem Entwurf und Export beschrieben. |
| 2 | Technische Prüfung noch definieren. | Datenanlieferung: Liefercheckliste und separate Beschreibung der belegten automatisierten Prüfungen. Keine pauschale Garantie, dass alle redaktionellen Vorgaben maschinell geprüft werden. |
| 5 | XLSX und Parquet werden aus CSV erzeugt. | Einstieg, Anlieferung und FAQ korrigiert; keine zusätzlichen Lieferformate. |
| 6 | Bestehende Datenportal-Dokumentation heranziehen. | Technische Referenz beibehalten und intern verlinkt. Alter externer Link aus dem Kommentar durch die integrierte Referenz ersetzt. |
| 7 | Dateiname wird ohnehin umbenannt. | Keine Pflicht zur Jahres-/Datumsangabe. Datenstand im Datenblatt und Ausgabe im Serien-Lieferformular erklären. |
| 8 | Keine Leerzeichen, Umlaute oder Sonderzeichen. | Datenaufbereitung: bereinigte Dateinamen mit Beispielen empfohlen; Regeln für Attribute separat verlinkt. |
| 9 | Beispiel mit Webseite. | Metadaten: Erfassungsschritte und fiktives ausgefülltes Beispiel anhand der aktuellen Feldnamen, kein Word-Formular. |
| 10 | Attributbeschreibungen sind besonders wichtig für KI. | Eigener Abschnitt mit Name, Typ, Beschreibung, Einheit, CodeList und Pflicht sowie konkreter Bedeutung von Codes, fehlenden Werten und Nachweisgrenzen. |

## Technischer Abgleich und bewusste Abweichungen

Die folgenden Pfade beziehen sich auf die neben diesem Repository liegenden
Quellrepos. Sie dienen der Pflege, nicht als zusätzliche Anweisungen an Lieferanten.

| Thema | Beleg | Entscheidung |
| --- | --- | --- |
| Editorfelder und Pflichtangaben | `datenportal-datenblatt-editor/src/components/DatasetForm.vue`, `SharedMetadataSections.vue`, `src/domain/validation.ts` | Sichtbare Feldnamen verwenden; Identifier, Zugänglichkeit, Publikationsstatus, Themen und Modified nicht als automatisch gesetzt darstellen. Keywords sind komma-, nicht semikolongetrennt. |
| Lizenz | Editor ohne Lizenzfeld; `datenportal-themenrepo/shared/sql/publication/assemble.sql`, `shared/xsl/opendata/catalog.xsl` | Word-Empfehlung `terms_by` nicht als auswählbare Lizenz übernehmen. Katalogwerte bleiben erhalten, RDF verwendet fest `terms_open`. Abweichende Nutzungsbedingungen vor Publikation mit AFIN/AGI klären und technisch umsetzen. |
| Editorbedienung | `datenportal-datenblatt-editor/src/components/StartPage.vue`, `src/app/App.vue`, `README.md` | Lokale Dateien importieren und als XTF exportieren; Browserentwurf ist keine Einreichung. Keine Anleitung zum derzeit deaktivierten Quellenimport. Vom Auftraggeber bestätigter Einstieg: https://daten.so.ch/datenblatt-editor. |
| Einstieg zur Anlieferung | Vom Auftraggeber bestätigte Zieladresse und Anmeldung | https://daten.so.ch/anlieferung führt zur Anlieferungsoberfläche in Jenkins. Übergang von der vorbereiteten CSV und dem exportierten Datenblatt zur Anlieferung ergänzt. Die Anmeldung erfolgt mit dem kantonalen Benutzerkonto via AD/LDAP; AGI vergibt die Berechtigungen für die Datenanlieferung. Die Zieladressen wurden übernommen, ihre künftige Erreichbarkeit ist keine Voraussetzung der Dokumentationsprüfung. |
| Attribute | `datenportal-datenblatt-editor/src/components/AttributeTable.vue`, `src/domain/validation.ts`; `datenportal-themenrepo/shared/sql/publication/delivery.sql` | Attributnamen und Reihenfolge abgleichen. Fehlende Beschreibungen und doppelte Namen sind Editorwarnungen; doppelte CSV-Kopfzeilen sind Verarbeitungsfehler. `URI` wird zwar im Editor angeboten, in der CSV-Verarbeitung aber nicht unterstützt; URL-Spalten als `TEXT` deklarieren. |
| Lieferprüfung und Konvertierung | `datenportal-themenrepo/shared/sql/publication/delivery.sql`, `shared/gradle/datenportal-publication.gradle` | Nichtleere/eindeutige Kopfzeilen; bei Attributliste Namen/Reihenfolge, Typkonvertierung und Pflichtwerte; zusätzliche CsvValidator-Prüfung nur bei hinterlegtem Modell. XLSX und Parquet entstehen aus der typisierten Tabelle. |
| CSV-Textbegrenzung | `gretl-modular/gretl-core/src/main/java/ch/so/agi/gretl/internal/duckdb/DuckDbSessionBuilder.java`; bestehendes Semikolon-Textbeispiel | Der Reader verwendet `read_csv` ohne abgeschaltete Quote-Erkennung. Widersprüchliches «kein Textbegrenzungszeichen» entfernt; doppelte Anführungszeichen und deren Verdoppelung erläutert. |
| Kleine Referenzkorrekturen | `datenformat_datenstruktur.adoc` | Excel-Standardbehauptung und XXXX-Platzhalter ersetzt; falsches Komma in Total-Beispiel korrigiert; Nachweisgrenzenbeispiel an `0.01` angeglichen; Tippfehler behoben. Die bestehende Zeitvorgabe UTC+1 wurde nicht neu definiert. |
| Lieferung und Serien | `datenportal-themenrepo/docs/biblios/startformular.adoc`, `lieferverarbeitung.adoc` | CSV, Datenblatt oder beides; Ausgabe nur bei Serien-CSV. Reine Metadaten betreffen das ganze Datenblatt. Keine automatische Freigabe unbekannter Ausgaben behaupten. |
| Veröffentlichung | `datenportal-dokumentation-architektur/docs/biblios/zusammenspiel.adoc` | Fachliche Freigabe, technische Publikationsfreigabe und Portal-Reload unterscheiden. Standardmässig ausgeschaltete Reload-Option erklären. |

## Abnahmeszenarien

1. **Erstpublikation:** Voraussetzungen → Anmeldung → Datenaufbereitung und
   Datenblatt → fachliche/technische Prüfung → AFIN-Freigabe → durch AGI
   eingerichtete Lieferung → Kontrolle des tatsächlich geladenen Portalstands.
2. **Regelmässige Lieferung:** Vereinbartes Intervall → CSV prüfen → vorhandenes
   Datenblatt weiterverwenden oder aktualisieren → bei Serie Ausgabe angeben →
   Lieferung und Sichtbarkeit kontrollieren. Kein Datumszwang im Dateinamen.
3. **Metadaten- oder Strukturänderung:** Aktuelles vollständiges Datenblatt
   importieren → Metadaten ohne CSV korrigieren; bei Struktur-/Methodenänderungen
   vorab AFIN/AGI einbeziehen und Prüf-/Freigabeschritte erneut durchlaufen.

Zur technischen Abnahme die zentrale Biblios-Vorschau mit lokalen Arbeitsständen
erzeugen und Navigation, interne Verweise, Tabellen und CSV-Beispiele prüfen.
Die Quellen-ID `datenpublikation`, Repository-Name und URL-Struktur bleiben erhalten.

## Prüfergebnis vom 28. September 2026

- Biblios hat alle fünf eingebundenen Quellen mit Java 25 und lokalen
  Arbeitsständen erfolgreich gebaut. Die Anleitung liegt weiterhin unter
  `datenpublikation/main/` und enthält die sieben vorgesehenen Hauptkapitel.
- Alle internen Sprungziele sind vorhanden, IDs sind eindeutig, und es bleiben
  keine Include-/Querverweis-Platzhalter im HTML zurück. Der Navigationssprung
  zum Metadatenkapitel wurde im Browser geprüft.
- Alle fünf Tabellen besitzen konsistente Spaltenzahlen. Die Desktopansicht
  wurde in Chrome bei 1440 Pixel Breite visuell geprüft.
- Alle sechs CSV-Beispiele haben konsistente Spaltenzahlen und wurden zusätzlich
  mit DuckDB JDBC 1.5.5.1 (`read_csv`, `header=true`, `all_varchar=true`) gelesen.
  Semikolon im Text und verdoppelte Anführungszeichen bleiben korrekt erhalten.
- Die drei oben beschriebenen Abläufe wurden redaktionell durchgegangen.
  Es wurden keine Lieferungen oder Veröffentlichungen in einem produktiven
  Portal ausgeführt.
- Darstellungsgrenze: Bei 390 Pixel Bildschirmbreite führen die Tabellen im
  aktuellen Biblios-Theme zu horizontalem Seitenüberlauf (654 Pixel
  Dokumentbreite). Eine responsive Tabellenbehandlung ist eine separate
  Verbesserung am zentralen Theme; dieses Dokumentationsupdate ändert es nicht.
