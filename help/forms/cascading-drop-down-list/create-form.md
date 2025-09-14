---
title: Erstellen eines Formulars mit dem universellen Editor
description: Verwenden Sie adaptive Formularausdrücke, um automatische Überprüfung und Berechnung hinzuzufügen sowie die Sichtbarkeit eines Abschnitts zu aktivieren oder zu deaktivieren.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 8%

---

# Erstellen eines Formulars mit dem universellen Editor

Erstellen Sie das folgende Formular mit dem universellen Editor. Das Formular enthält drei Dropdown-Listen, deren Werte mithilfe der API-Integration ausgefüllt werden
![adaptive-form](assets/address-form.png)

## Wohnsitzland

Bei der Initialisierung wird die Dropdown-Liste „Land des Wohnsitzes“ mit den Ergebnissen des API-Aufrufs ausgefüllt.
![initialize-event](assets/initialize-event.png)

## Erfolgs-Handler

Der Erfolgs-Handler wurde definiert, um die Aufzählungs- und Aufzählungsnamen der Dropdownliste „Land“ mit den entsprechenden Werten aus dem Array „GeoNames“ festzulegen. Das Array „geonames“ ist unter der Option „Ereignis-Payload“ verfügbar
![event-payload](assets/event-payload.png)
![success-handler](assets/success-handler.png)

## Untergeordnete Werte abrufen

Die Dropdown-Liste Bundesland oder Provinz wird gefüllt, wenn der Benutzer eine Auswahl in der Dropdown-Liste Wohnland trifft. Die dem ausgewählten Land zugeordnete GeonameId wird als Eingabeparameter an die GetChildren-API-Integration übergeben

![get-children](assets/invoke-service-get-children.png)

Der Erfolgs-Handler wurde definiert, um die Aufzählungs-/Aufzählungsnamen des Dropdown-Felds Bundesland/Provinz festzulegen
![get-children-success-handler](assets/child-success-handler.png)

Wenn das Bundesland oder die Provinz ausgewählt ist, können Sie die Dropdown-Liste Stadt nach dem oben genannten Muster ausfüllen, das zum Ausfüllen der Dropdownliste Bundesland oder Provinz verwendet wird.