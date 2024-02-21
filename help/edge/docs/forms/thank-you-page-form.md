---
title: Dankeseite für EDS Forms konfigurieren
description: Dankeseite für EDS Forms konfigurieren
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0604838311bb9ab195789fad755b0910e09519fd
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 5%

---


# Umleitungen für Formularbausteine konfigurieren

Sie haben die Möglichkeit, den Formularblock so zu konfigurieren, dass er zu einer anderen Seite auf Ihrer Website umgeleitet wird, anstatt zur standardmäßigen &quot;Danke&quot;-Seite. So richten Sie eine andere Seite als Umleitungsziel ein

1. Öffnen Sie die Datei `[EDS Project]/blocks/form/form.js`, um sie zu bearbeiten.

   ![Code für Dankeschön-Knoten](/help/edge/assets/change-thankyou-node.png)

1. Ändern Sie die `thankyou` Knoten in der folgenden Zeile zum Knoten Ihrer Wahl:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   Beispiel:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'home';
   ```

   >[!NOTE]
   >
   > Stellen Sie sicher, dass eine Dokumentseite mit demselben Namen im Projektordner für den Edge Delivery Service in Microsoft SharePoint oder Google Tabellen erstellt wird, sofern sie noch nicht erstellt wurde.


1. Fahren Sie fort, um den aktualisierten Ordner &quot;form.js&quot;und die zugrunde liegenden Dateien in Ihr Edge Delivery Service-Projekt auf GitHub einzuchecken. Durch diese Aktualisierung wird sichergestellt, dass das Formular jetzt wie angegeben an den aktualisierten Knoten weitergeleitet wird.
