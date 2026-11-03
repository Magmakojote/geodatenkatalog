# Geodaten Katalog

Eine kleine Webseite, die eine CSV-Liste von Geodatendiensten (WMS, WFS, WMTS, Feature Services, Downloads …) als durchsuchbare Kachelübersicht darstellt. Entstanden als internes Nachschlagewerk für Kollegen, damit niemand eine lange Excel-Tabelle durchscrollen muss.

## Benutzung

1. `index.html` im Browser öffnen (lokal per Doppelklick)
2. Beim ersten Aufruf die CSV-Datei auswählen.
3. Fertig: Suche und Filter (Region, Typ, Thema) stehen oben bereit.

Die Daten werden nur im eigenen Browser gespeichert (localStorage) und nirgendwohin übertragen. Beim nächsten Öffnen sind sie also noch da. Ein erneuter Import überschreibt die vorhandene Liste.

Die Seite lädt React, Babel, Tailwind und PapaParse von öffentlichen CDNs. Sie braucht deshalb eine Internetverbindung.

## Aufbau der CSV

Als Trennzeichen wird Semikolon oder Komma automatisch erkannt. Wichtig ist die Kodierung: In Excel unter **„Speichern unter“ → „CSV UTF-8 (durch Trennzeichen getrennt)“** speichern, sonst werden Umlaute falsch dargestellt.

Erkannte Spalten (bei mehreren Namen wird der erste vorhandene genommen):

| Anzeige       | Spaltenname in der CSV                           |
|---------------|--------------------------------------------------|
| Titel         | `Name im GIS`, `Name` oder `Dienstbezeichnung`   |
| Region        | `Geltungsbereich` oder `Gebiet`                  |
| Typ           | `Form` (z. B. WMS, WFS, CSV)                     |
| Beschreibung  | `Beschreibung` oder `Kurzbeschreibung`           |
| Link          | `URL`                                            |
| Quelle        | `Plattform/Quelle`                               |
| Status        | `Status` (`okay` = grün, `/` = kein Punkt, alles andere = rot) |
| Thema         | `Thema`                                          |

Weitere Spalten werden ignoriert. Zeilen ohne Namen werden übersprungen. Eine Vorlage liegt in `beispiel.csv`.

Hinweis zum Status: Er zeigt nur an, was in der CSV steht. Die Seite prüft nicht selbst, ob ein Dienst erreichbar ist.
