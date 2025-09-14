---
title: API-Integration erstellen
description: Verwenden Sie adaptive Formularausdrücke, um automatische Überprüfung und Berechnung hinzuzufügen sowie die Sichtbarkeit eines Abschnitts zu aktivieren oder zu deaktivieren.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 7%

---


# API-Integration erstellen

In diesem Tutorial werden zwei API-Integrationen erstellt

- GetAllCountries gibt eine Liste von Ländern zurück
- GetChildren - Gibt unmittelbar untergeordnete Elemente des Landes oder Staates zurück, der durch die geonameId repräsentiert wird.

## GetAllCountries - API-Integrationskonfiguration

- Konfiguration der API-Integration

   - Anzeigename: GetAllCountries → eine Bezeichnung für diese API in Ihrem System.

   - API-URL: `https://secure.geonames.org/countryInfoJSON` - der aufrufende Endpunkt.

   - HTTP-Methode: GET - Sie stellen eine einfache GET-Anfrage.

   - Content-Typ: JSON - Antwort wird im JSON-Format erwartet.

- Optionen:

   - Verschlüsselung erforderlich deaktiviert - keine Verschlüsselungsschicht über HTTPS hinaus.

   - Ausführen beim Client aktiviert - der Aufruf wird vom Client/Browser ausgeführt, nicht Server-seitig.
- Authentifizierungstyp
   - Keine- da die GeoNames-API keine OAuth- oder API-Schlüssel in Kopfzeilen erfordert
- Eingabe:
   - Im Eingabeabschnitt wird definiert, was an die API gesendet wird
   - **username** →: Zeichenfolge, in der Abfrage gesendet, Standard: gbedekar.
   - Jede Anfrage hängt ?username=gbedekar an die URL an
- Ausgabe
   - Die Ausgabe definiert, welche Felder aus der JSON-Antwort extrahiert und verwendet werden sollen.
Die GeoNames-Antwort sieht wie folgt aus:

  ![json-response](assets/geonames-data.png)
   - Zwei Felder aus dem GeoNames-Array zugeordnet:

     geonames[*].geonameId → als Zahl

     geonames[*].countryName als Zeichenfolge →

     Das [*] bedeutet, dass es sich für jedes Land im Array wiederholt.



![Alle Länder](assets/api-integration.png)


## GetChildren

GeoNames werden nach den unmittelbar untergeordneten Elementen des Ortes gefragt, dessen geonameId als Abfrageparameter übergeben wird

- Konfiguration der API-Integration

   - Anzeigename: GetAllCountries → eine Bezeichnung für diese API in Ihrem System.

   - API-URL: `https://secure.geonames.org/children` → den aufgerufenen Endpunkt.

   - HTTP-Methode: GET → Sie eine einfache GET-Anfrage stellen.

   - Inhaltstyp: JSON-→-Antwort wird im JSON-Format erwartet.

- Optionen:

   - Verschlüsselung erforderlich deaktiviert → keine Verschlüsselungsschicht über HTTPS hinaus.

   - Ausführen beim Client, → überprüft wurde, ob der Aufruf vom Client/Browser ausgeführt wird, nicht serverseitig.
- Authentifizierungstyp
   - Keine- da die GeoNames-API keine OAuth- oder API-Schlüssel in Kopfzeilen erfordert
- Eingabe:
   - Definiert, was an die API gesendet wird
   - **username** →: Zeichenfolge, in der Abfrage gesendet, Standard: gbedekar.
   - Jede Anfrage hängt ?username=gbedekar an die URL an
   - **geonameId** -> Typ: Zeichenfolge. Gibt die untergeordneten Elemente des Landes bzw. Bundeslandes zurück, das durch die geonameId repräsentiert wird
   - **type** =>String. Wenn auf JSON gesetzt wird, wird die Antwort im JSON-Format zurückgegeben.
- Ausgabe
   - Definiert, welche Felder aus der JSON-Antwort extrahiert und verwendet werden sollen.
Die GeoNames-Antwort sieht wie folgt aus:

  ![json-response](assets/child-elements-data.png)
   - Zwei Felder aus dem GeoNames-Array zugeordnet:

     geonames[*].geonameId → als Zahl

     geoNames[*].name → als Zeichenfolge

     Das [*] bedeutet, dass es sich für jedes Land im Array wiederholt.


![get-children](assets/get-children-api-integration.png)
