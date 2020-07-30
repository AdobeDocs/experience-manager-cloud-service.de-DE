---
title: Integrieren mit Adobe Analytics
description: 'Integrieren mit Adobe Analytics '
translation-type: tm+mt
source-git-commit: f2ed74afd2df43e31ff1002cd42a60f372d0b769
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 18%

---


# Integrieren mit Adobe Analytics{#integrating-with-adobe-analytics}

Die Integration von Adobe Analytics und AEM as a Cloud Service ermöglicht es Ihnen, Web-Seitenaktivität zu erfassen. Die Integration erfordert:

* Verwenden der Touch-Benutzeroberfläche, um eine Analytics-Konfiguration in AEM als Cloud Service zu erstellen.
* Hinzufügen und Konfigurieren von Adobe Analytics als Erweiterung in [Adobe Launch].(https://docs.adobe.com/content/help/en/launch/using/intro/get-started/quick-start.html).

Im Vergleich zu früheren Versionen von AEM wird in der Analytics-Konfiguration in AEM als Cloud Service keine Frameworkunterstützung bereitgestellt. Stattdessen erfolgt sie jetzt über Adobe Launch, das defacto-Tool zur Instrumentierung einer AEM Site mit Analytics-Funktionen (JS-Bibliotheken). Beim Start der Adobe wird eine Eigenschaft erstellt, bei der die Adobe Analytics-Erweiterung konfiguriert werden kann und Regeln zum Senden von Daten an Adobe Analytics erstellt werden. Adobe Launch hat die Aufgabe der von SiteCatalyst bereitgestellten Analytics ersetzt.

>[!NOTE]
>
>Kunden mit Adobe Experience Manager as a Cloud Service, die kein Analytics-Konto haben, können Zugriff auf Analytics Foundation Pack für Experience Cloud anfordern. Dieses Foundation Pack bietet eine eingeschränkte Verwendung von Analytics.

## Erstellen der Analytics-Konfiguration {#analytics-configuration}

1. Navigate to **Tools** → **Cloud Services**.
2. Select **Adobe Analytics Configurations**.
   ![Analytics](assets/analytics_screen1.png "WindowAnalytics-Fenster")
3. Select the **Create** button.
4. Füllen Sie die Details aus (siehe unten) und klicken Sie auf **Verbinden**.

### Configuration Parameters {#configuration-parameters}

Die Konfigurationsfelder im Fenster &quot;Adobe Analytics-Konfiguration&quot;sind:

![Konfigurationsparameter](assets/properties_field1.png "Konfigurationsparameter")

| Eigenschaft | Beschreibung |
|---|---|
| Unternehmen | Adobe Analytics Login-Firma |
| Benutzername | Adobe Analytics API-Benutzer |
| Kennwort | Adobe Analytics-Kennwort für die Authentifizierung |
| Datenzentrum | Das Adobe Analytics-Rechenzentrum, mit dem Ihr Konto verbunden ist (Server, z. B. San Jose, London) |
| Segment | Option zur Verwendung eines in der aktuellen Berichte-Suite definierten Analytics-Segments. Die Analytics-Berichte werden auf Grundlage des Segments gefiltert. Weitere Informationen finden Sie auf [dieser Seite](https://docs.adobe.com/content/help/en/analytics/components/segmentation/seg-overview.html) . |
| Report Suites | Ein Repository, in dem Sie Daten senden und Berichte abrufen. Eine Report Suite definiert den vollständigen, unabhängigen Berichte auf einer bestimmten Website, eine Reihe von Websites oder eine Untergruppe von Webseiten. Sie können die Berichte, die aus einer einzigen Report Suite abgerufen wurden, in einer Ansicht bearbeiten, und zwar jederzeit entsprechend Ihren Anforderungen. |

### Hinzufügen einer Konfiguration zu einer Site {#add-configuration}

Um eine Touch-UI-Konfiguration auf eine Site anzuwenden, gehen Sie zu: **Sites** → **Wählen Sie eine beliebige Site-Seite** → **Eigenschaften** → **Erweitert** → **Konfiguration** → Konfiguration.

## Integrieren von Adobe Analytics auf AEM Sites mithilfe von Adobe Launch

Adobe Analytics kann als Erweiterung in der Eigenschaft &quot;Start&quot;hinzugefügt werden. Es können Regeln definiert werden, die die Zuordnung und den anschließenden Aufruf an Adobe Analytics durchführen:

* In [diesem Video](https://docs.adobe.com/content/help/en/analytics-learn/tutorials/implementation/via-adobe-launch/basic-configuration-of-the-analytics-launch-extension.html) erfahren Sie, wie Sie die Analytics-Erweiterung in Launch für eine einfache Site konfigurieren.

* Weitere Informationen zum Erstellen von Regeln und zum Senden von Daten an Adobe Analytics finden Sie auf [dieser Seite](https://docs.adobe.com/content/help/en/core-services-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html) .

>[!NOTE]
>
>Vorhandene (ältere) Frameworks funktionieren weiterhin, können jedoch nicht in der Touch-Benutzeroberfläche konfiguriert werden. Es wird empfohlen, die Variablenzuordnungskonfigurationen in Launch neu zu erstellen.

>[!NOTE]
>
>Die IMS-Konfiguration (technische Konten) für Launch ist in AEM as a Cloud Service vorkonfiguriert. Benutzer müssen diese Konfiguration nicht erstellen.
