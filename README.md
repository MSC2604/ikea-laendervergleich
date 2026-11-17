# IKEA Ländervergleich

Private, unabhängige Vergleichsseite für IKEA Deutschland, Tschechien und Polen.

## Funktionen

- Gemeinsame Suche nach Produktname oder achtstelliger IKEA-Artikelnummer in allen drei Ländern.
- Bei Artikelnummern wird die Nummer normalisiert, bis zu 100 Suchtreffer werden angefordert und die Artikelnummer wird exakt abgeglichen.
- Produktname, Artikelnummer, Bild (wenn von IKEA geliefert), lokaler Preis und IKEA-Produktlink (wenn geliefert).
- Preisvergleich in Euro anhand der aktuellen Frankfurter-API v2 (kostenlos, ohne API-Schlüssel).
- Der letzte erfolgreich geladene Wechselkurs wird lokal zwischengespeichert und bei vorübergehendem API-Ausfall weiterverwendet; die Anzeige kennzeichnet ihn dann als zuletzt gespeicherten Kurs.
- Getrennte Einkaufslisten für Deutschland (EUR), Tschechien (CZK) und Polen (PLN).
- Lokale Speicherung, JSON-Sicherung und CSV-Export.
- Keine Filial-Bestandsabfrage.

## Grenzen

Die Suche verwendet die von den IKEA-Webseiten genutzte Suchschnittstelle. Sie ist keine offiziell dokumentierte öffentliche Entwickler-API und kann von IKEA jederzeit geändert oder eingeschränkt werden. Es gibt daher keine Garantie für jede Artikelnummer: Der Artikel muss im jeweiligen Landes-Sortiment vorhanden und in den IKEA-Suchdaten auffindbar sein. Ein fehlender Treffer in einem Land bedeutet nicht automatisch, dass der Artikel weltweit nicht existiert.

Die Produktpreise werden aus den Suchdaten des jeweiligen Landes übernommen. Die Euro-Umrechnung ist ein Referenzvergleich und kein verbindliches Zahlungsangebot. Maßgeblich ist immer der Preis auf der verlinkten IKEA-Länderseite.

Die Live-Erreichbarkeit der IKEA-Schnittstellen muss im Browser geprüft werden. Eine Codeanpassung allein kann keinen erfolgreichen Live-Aufruf für alle drei Länder und alle Artikelnummern garantieren.

## Veröffentlichung

GitHub Pages verwendet Branch `main` und den Ordner `/(root)`. Der Service Worker erhält bei App-Änderungen eine neue Cache-Version, damit installierte Geräte die aktualisierte Oberfläche laden.

## Datenschutz

Einkaufslisten und Filialauswahl werden lokal im Browser mit `localStorage` gespeichert. Es gibt keinen eigenen Server und keine Übertragung der Einkaufsliste.

## Automatische technische Prüfung

GitHub Actions prüft täglich um 05:00 UTC die Erreichbarkeit der IKEA-Suchendpunkte für Deutschland, Tschechien und Polen anhand des Testartikels 70556067. Dabei werden die exakte Artikelnummer, ein gültiger Landespreis, der Produktlink und die CORS-Freigabe geprüft. Zusätzlich werden die CZK- und PLN-Referenzkurse der Frankfurter-API v2 validiert. Die Prüfung läuft außerdem bei Änderungen an der App und kann manuell in GitHub Actions gestartet werden. Sie ist ein technischer Funktionstest mit einem Beispielartikel, keine Garantie für das gesamte IKEA-Sortiment.
