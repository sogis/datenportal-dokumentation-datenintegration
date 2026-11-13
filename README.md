# datenportal-dokumentation-datenintegration

«Anleitung für Datenlieferanten» für das Datenportal Kanton Solothurn.
Der Einstieg ist `docs/biblios/master.adoc`. Die neun Kapitel werden als
zusammenhängende Seite im zentralen Repository `datenportal-dokumentation`
unter der bestehenden Quellen-ID `datenpublikation` eingebunden.

Die fachlichen Kapitel führen von den Voraussetzungen über die Erstpublikation
bis zur Nachführung. Die letzten beiden Kapitel enthalten die Bedienungsanleitungen
für den Datenblatt-Editor und Jenkins. Zwölf benannte Screenshot-Platzhalter
werden später durch Aufnahmen der tatsächlichen Oberflächen ersetzt. HTML und
PDF verwenden dieselben AsciiDoc-Quellen; PDF-Ausgabe und Layout werden separat
mit Biblios geprüft und eingerichtet.

Die [Übernahmematrix](docs/redaktion/uebernahmematrix.md) hält die Integration
der Word-Anleitung einschliesslich aller Kommentare und die technischen
Abgleiche fest. Sie gehört zur redaktionellen Pflege und wird nicht in die
Lieferantenanleitung eingebunden.

Für eine lokale Vorschau im zentralen Repository:

```sh
PYTHON=.venv/bin/python ./scripts/generate-local-config.sh
java -jar ../thoth/thoth-biblios/build/libs/thoth-biblios-0.0.1-SNAPSHOT-all.jar serve \
  --config biblios.local.yml --port 8091 --use-local-working-tree
```

Java 25 und ein gebautes Biblios-JAR werden benötigt. Die Option
`--use-local-working-tree` berücksichtigt auch noch nicht committierte Inhalte.
