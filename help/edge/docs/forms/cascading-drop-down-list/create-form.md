---
title: Erstellen des Formulars mit dem universellen Editor
description: Erstellen eines adaptiven Formulars zum Testen der kaskadierenden Dropdown-Liste mithilfe der API-Integrationen
feature: Edge Delivery Services
role: User
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: ht
source-wordcount: '202'
ht-degree: 100%

---

# Erstellen des Formulars mit dem universellen Editor

Erstellen Sie das folgende Formular mit dem universellen Editor. Das Formular enthält drei Dropdown-Listen, deren Werte mithilfe der API-Integration ausgefüllt werden.
![adaptive-form](assets/address-form.png)

## Wohnsitzland

Bei der Initialisierung wird die Dropdown-Liste für das Wohnsitzland mit den Ergebnissen des API-Aufrufs ausgefüllt.
![initialize-event](assets/initialize-event.png)

## Erfolgs-Handler

Der Erfolgs-Handler wurde so definiert, dass „enum“ und „enumNames“ der Dropdown-Liste für das Land auf die entsprechenden Werten aus dem Array „geonames“ festgelegt werden. Das Array „geonames“ ist unter der Option „Ereignis-Payload“ verfügbar.
![event-payload](assets/event-payload.png)
![success-handler](assets/success-handler.png)

## Abrufen untergeordneter Werte

Die Dropdown-Liste für die Region oder Provinz wird ausgefüllt, wenn Benutzende eine Auswahl in der Dropdown-Liste für das Wohnsitzland treffen. Die dem ausgewählten Land zugeordnete geonameId wird als Eingabeparameter an die GetChildren-API-Integration übergeben.

![get-children](assets/invoke-service-get-children.png)

Der Erfolgs-Handler wurde so definiert, dass „enum“ und „enumNames“ des Dropdown-Felds „StateOrProvince“ festgelegt werden.
![get-children-success-handler](assets/child-success-handler.png)

Wenn die Region oder Provinz ausgewählt ist, können Sie die Dropdown-Liste für die Stadt nach dem oben genannten Muster ausfüllen, das zum Ausfüllen der Dropdown-Liste für die Region oder Provinz verwendet wird.