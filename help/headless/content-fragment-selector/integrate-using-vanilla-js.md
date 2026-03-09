---
title: Integrieren des Inhaltsfragment-Selektors mit Vanilla JS
description: Integrieren Sie den Inhaltsfragment-Selektor in verschiedene Adobe-, Nicht-Adobe- und Drittanbieteranwendungen.
role: Admin, User, Developer
source-git-commit: 592e443928f2c9c18ac281027026132b1c877ce3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 10%

---

# Integrieren des Inhaltsfragment-Selektors mit Vanilla JS {#integrate-content-fragment-selector-using-vanilla-js}

Sie können jede Adobe- oder Nicht-Adobe-Anwendung mit dem Adobe Experience Manager (AEM) as a Cloud Repository integrieren und Inhaltsfragmente aus dieser Anwendung auswählen.

Die Integration erfolgt durch den Import des Inhaltsfragment-Selektor-Pakets und die Verbindung zur AEM as a Cloud Service mithilfe der Vanilla JavaScript-Bibliothek. Bearbeiten Sie eine Datei `index.html` oder eine andere geeignete Datei innerhalb Ihrer Anwendung, um:

* Authentifizierungsdetails zu definieren
* Zugriff auf das AEM as a Cloud Service-Repository
* Konfigurieren der Anzeigeeigenschaften des Inhaltsfragmentselektors

Sie können eine Authentifizierung durchführen, ohne einige der IMS-Eigenschaften zu definieren, wenn Sie:

* eine Adobe-Anwendung in ([&#x200B; Shell) &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell)
* Für die Authentifizierung bereits ein IMS-Token generiert haben
