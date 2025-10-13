---
title: Erstellen einer API-Integration
description: Erstellen Sie zwei API-Integrationen für zwei Geonames-APIs.
feature: Edge Delivery Services
role: User
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: ht
source-wordcount: '393'
ht-degree: 100%

---


# Erstellen einer API-Integration

In diesem Tutorial werden zwei API-Integrationen erstellt.

- GetAllCountries gibt eine Liste von Ländern zurück.
- GetChildren gibt unmittelbar untergeordnete Elemente des Landes oder der Region zurück, die von der geonameId repräsentiert werden.

## GetAllCountries – Konfiguration der API-Integration

- Konfiguration der API-Integration

   - Anzeigename: GetAllCountries → ein Label für diese API in Ihrem System.

   - API-URL: `https://secure.geonames.org/countryInfoJSON` → der aufgerufene Endpunkt.

   - HTTP-Methode: GET → Sie stellen eine einfache GET-Anfrage.

   - Content-Typ: JSON → Antwort wird im JSON-Format erwartet.

- Optionen:

   - „Verschlüsselung erforderlich“ deaktiviert → keine Verschlüsselungsschicht über HTTPS hinaus.

   - „Ausführen vom Client“ aktiviert → der Aufruf wird vom Client/Browser ausgeführt, nicht Server-seitig.
- Authentifizierungstyp
   - Keiner: Da die GeoNames-API keine OAuth- oder API-Schlüssel in Headern erfordert.
- Eingabe:
   - Im Abschnitt „Eingabe“ wird definiert, was an die API gesendet wird.
   - **username** → Typ: Zeichenfolge, in der Abfrage gesendet, Standard: gbedekar.
   - Jede Anfrage hängt „?username=gbedekar“ an die URL an.
- Ausgabe
   - Die Ausgabe definiert, welche Felder aus der JSON-Antwort extrahiert und verwendet werden sollen.
Die GeoNames-Antwort sieht wie folgt aus:

  ![json-response](assets/geonames-data.png)
   - Zwei Felder aus dem Array „geonames“ werden zugeordnet:

     geonames[*].geonameId → als Zahl

     geonames[*].countryName → als Zeichenfolge

     [*] bedeutet, dass es für jedes Land im Array wiederholt wird.



![get-all-countries](assets/api-integration.png)


## GetChildren

GeoNames wird nach den unmittelbar untergeordneten Elementen des Ortes gefragt, dessen geonameId als Abfrageparameter übergeben wird.

- Konfiguration der API-Integration

   - Anzeigename: GetAllCountries → ein Label für diese API in Ihrem System.

   - API-URL: `https://secure.geonames.org/children` → der aufgerufene Endpunkt.

   - HTTP-Methode: GET → Sie stellen eine einfache GET-Anfrage.

   - Content-Typ: JSON → Antwort wird im JSON-Format erwartet.

- Optionen:

   - „Verschlüsselung erforderlich“ deaktiviert → keine Verschlüsselungsschicht über HTTPS hinaus.

   - „Ausführen vom Client“ aktiviert → der Aufruf wird vom Client/Browser ausgeführt, nicht Server-seitig.
- Authentifizierungstyp
   - Keiner: Da die GeoNames-API keine OAuth- oder API-Schlüssel in Headern erfordert.
- Eingabe:
   - Definiert, was an die API gesendet wird.
   - **username** → Typ: Zeichenfolge, in der Abfrage gesendet, Standard: gbedekar.
   - Jede Anfrage hängt „?username=gbedekar“ an die URL an.
   - **geonameId** → Typ: Zeichenfolge. Gibt unmittelbar untergeordnete Elemente des Landes/der Region zurück, die von der geonameId repräsentiert werden.
   - **type** → Zeichenfolge. Wenn dies auf JSON festgelegt wird, wird die Antwort im JSON-Format zurückgegeben.
- Ausgabe
   - Definiert, welche Felder aus der JSON-Antwort extrahiert und verwendet werden sollen.
Die GeoNames-Antwort sieht wie folgt aus:

  ![json-response](assets/child-elements-data.png)
   - Zwei Felder aus dem Array „geonames“ werden zugeordnet:

     geonames[*].geonameId → als Zahl

     geonames[*].countryName → als Zeichenfolge

     [*] bedeutet, dass es für jedes Land im Array wiederholt wird.


![get-children](assets/get-children-api-integration.png)
