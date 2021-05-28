---
title: Integration mit Adobe Analytics
description: 'Integration mit Adobe Analytics '
feature: Verwalten
role: Administrator
exl-id: e353a1fa-3e99-4d79-a0d1-40851bc55506
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 94%

---

# Integration mit Adobe Analytics{#integrating-with-adobe-analytics}

Die Integration von Adobe Analytics und AEM as a Cloud Service ermöglicht es Ihnen, Web-Seitenaktivität zu erfassen. Die Integration setzt Folgendes voraus:

* Verwenden der Touch-Benutzeroberfläche, um eine Analytics-Konfiguration in AEM as a Cloud Service zu erstellen.
* Hinzufügen und Konfigurieren von Adobe Analytics als Erweiterung in [Adobe Experience Platform Launch](#analytics-launch). Weitere Informationen zu Adobe Experience Platform Launch finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/launch/using/intro/get-started/quick-start.html).

Im Vergleich zu früheren Versionen von AEM ist in der Analytics-Konfiguration von AEM as a Cloud Service keine Framework-Unterstützung gegeben. Stattdessen erfolgt diese nun über Adobe Experience Platform Launch, das De-facto-Tool für die Instrumentierung einer AEM-Site mit Analytics-Funktionen (JS-Bibliotheken). In Adobe Experience Platform Launch wird eine Eigenschaft eingerichtet, bei der die Adobe Analytics-Erweiterung konfiguriert werden kann und Regeln zum Senden von Daten an Adobe Analytics erstellt werden. Adobe Experience Platform Launch hat die Aufgabe der von SiteCatalyst bereitgestellten Analysefunktionen übernommen.

>[!NOTE]
>
>Kunden mit Adobe Experience Manager as a Cloud Service, die kein Analytics-Konto haben, können Zugriff auf das Analytics Foundation Pack für Experience Cloud anfordern. Dieses Foundation Pack ermöglicht eine eingeschränkte Verwendung von Analytics.

## Erstellen der Adobe Analytics-Konfiguration {#analytics-configuration}

1. Navigieren Sie zu **Tools** > **Cloud-Services**.
2. Wählen Sie **Adobe Analytics**.
   ![Adobe Analytics-Fenster](assets/analytics_screen2.png "Adobe Analytics-Fenster")
3. Klicken Sie auf die Schaltfläche **Erstellen**.
4. Füllen Sie die Details aus (siehe unten) und klicken Sie auf **Verbinden**.

### Konfigurationsparameter {#configuration-parameters}

Die Konfigurationsfelder im Fenster für die Adobe Analytics-Konfiguration sind:

![Konfigurationsparameter](assets/properties_field1.png "Konfigurationsparameter")

| Eigenschaft | Beschreibung |
|---|---|
| Unternehmen | Adobe Analytics-Anmeldung – Unternehmen |
| Benutzername | Adobe Analytics-API-Benutzer |
| Passwort | Adobe Analytics-Passwort für die Authentifizierung |
| Rechenzentrum | Das Adobe Analytics-Rechenzentrum, mit dem Ihr Konto verbunden ist (Server, z. B. San José oder London) |
| Segment | Option zur Verwendung eines in der aktuellen Report Suite definierten Analytics-Segments. Die Analytics-Berichte werden basierend auf dem Segment gefiltert. Weitere Informationen finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/analytics/components/segmentation/seg-overview.html). |
| Report Suites | Ein Repository, in dem Sie Daten senden und Berichte abrufen können. Eine Report Suite definiert die vollständigen, unabhängigen Berichte für eine bestimmte Website, eine Reihe von Websites oder eine Untergruppe von Website-Seiten. Sie können die Berichte, die aus einer bestimmten Report Suite abgerufen werden, jederzeit entsprechend Ihren Anforderungen anzeigen. |

### Hinzufügen einer Konfiguration zu einer Site {#add-configuration}

Um eine Touch-UI-Konfiguration auf eine Site anzuwenden, navigieren Sie zu: **Sites** > **Beliebige Site-Seite auswählen** > **Eigenschaften** > **Erweitert** > **Konfiguration** > Konfigurationsmandanten auswählen.

## Integrieren von Adobe Analytics in AEM-Sites mithilfe von Adobe Experience Platform Launch {#analytics-launch}

Adobe Analytics kann in der Launch-Präsenz als Erweiterung hinzugefügt werden. Es können Regeln definiert werden, die das Zuordnen und Ausführen eines post-Aufrufs an Adobe Analytics erledigen:

* In [diesem Video](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/via-adobe-launch/basic-configuration-of-the-analytics-launch-extension.html) erfahren Sie, wie Sie die Analytics-Erweiterung in Launch für eine einfache Site konfigurieren.

* Weitere Informationen zum Erstellen von Regeln und Senden von Daten an Adobe Analytics finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html).

>[!NOTE]
>
>Vorhandene (ältere) Frameworks funktionieren weiterhin, können jedoch nicht in der Touch-optimierten Benutzeroberfläche konfiguriert werden. Es wird empfohlen, die Variablenzuordnungskonfigurationen in Adobe Experience Platform Launch neu zu erstellen.

>[!NOTE]
>
>Die IMS-Konfiguration (technische Konten) für Adobe Experience Platform Launch ist in AEM as a Cloud Service vorkonfiguriert. Benutzer müssen diese Konfiguration nicht erstellen.
