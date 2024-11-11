---
title: Navigieren zur Cloud Manager-Benutzeroberfläche
description: Erfahren Sie, wie die Benutzeroberfläche von Cloud Manager aufgebaut ist und wie Sie Ihre Programme und Umgebungen verwalten.
exl-id: 3f3d7631-2bc9-440b-9888-50f6529bcd42
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 767f6609b3f585630d45aee0d61483dbe66f66cf
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 40%

---


# Navigieren zur Cloud Manager-Benutzeroberfläche {#navigation}

Erfahren Sie, wie die Benutzeroberfläche von Cloud Manager aufgebaut ist und wie Sie Ihre Programme und Umgebungen verwalten.

Die Benutzeroberfläche für die Cloud-Verwaltung besteht in erster Linie aus zwei grafischen Schnittstellen:

* der [Konsole „Meine Programme“](#my-programs-console), in der Sie alle Ihre Programme anzeigen und verwalten können.
* dem [Fenster „Programmübersicht“](#program-overview), in dem Sie die Details eines einzelnen Programms sehen und verwalten können.

>[!TIP]
>
>Sehen Sie sich auch die [Onboarding-Dokumentation Journey](/help/journey-onboarding/overview.md) an, um einen vollständigen Überblick darüber zu erhalten, wie Sie mit AEM as a Cloud Service mit Cloud Manager arbeiten können.

## Konsole „Meine Programme“ {#my-programs-console}

Wenn Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) anmelden und die entsprechende Organisation auswählen, gelangen Sie in die Konsole **Meine Programme**.

![Konsole „Meine Programme“](assets/my-programs-console.png)

Die Konsole „Meine Programme“ bietet einen Überblick über alle Programme, auf die Sie in der ausgewählten Organisation Zugriff haben. Sie besteht aus mehreren Teilen.

1. [Symbolleisten](#toolbars-my-programs-toolbars) für die Auswahl von Organisationen, Warnmeldungen und Kontoeinstellungen
1. Registerkarten, um die aktuelle Ansicht der Programme zu wechseln:
   * Ansicht **Startseite** (Standard) mit Auswahl der Ansicht **Meine Programme**, die einen Überblick über alle Programme enthält
   * **Lizenz**, die auf das [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md) zugreift.
   * Beachten Sie, dass die Registerkarten standardmäßig geschlossen sind und über das Symbol &quot;Menü anzeigen&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) in der Kopfzeile [Cloud Manager](#cloud-manager-header) angezeigt werden können.![
1. [Statistiken und Aktionsaufrufe](#statistics) für einen Überblick über Ihre aktuellen Aktivitäten
1. [**Meine Programme**](#my-programs-section) mit einem Überblick über Ihre gesamten Programme
1. [Schnelllinks](#quick-links-section) , um einfach auf zugehörige Ressourcen zuzugreifen.

>[!TIP]
>
>Weitere Informationen zu Programmen finden Sie unter [Programme und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

### Symbolleisten {#my-programs-toolbars}

Es gibt zwei Symbolleisten übereinander.

#### Cloud Manager-Kopfzeile {#cloud-manager-header}

Die erste ist der Header von Cloud Manager, der bestehen bleibt, wenn Sie in Cloud Manager navigieren. Er ist ein Anker, der Ihnen Zugriff auf Einstellungen und Informationen bietet, die für alle Cloud Manager-Programme gelten.

![Die Kopfzeile von Experience Cloud](assets/experience-cloud-header.png)

1. Klicken Sie auf ![Menüsymbol einblenden](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) (Seitenmenü ein- oder ausblenden), um Ihnen Zugriff auf verschiedene Registerkarten zu gewähren, über die Sie zu bestimmten Teilen eines Programms gelangen können. Alternativ können Sie je nach Kontext zwischen dem [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md) und der Konsole **[Meine Programme](#my-programs-console)** wechseln.
1. Wenn Sie auf die Schaltfläche Adobe Cloud Manager klicken, gelangen Sie zurück zur Konsole My Programs von Cloud Manager, unabhängig davon, wo Sie sich in Cloud Manager befinden.
1. Klicken Sie auf **Feedback** , um Adobe Feedback zu Cloud Manager zu geben.
1. Klicken Sie auf die Organisationsauswahl, um die Organisation anzuzeigen, bei der Sie sich derzeit angemeldet haben (in diesem Beispiel &quot;Foundation Intern&quot;). Klicken Sie auf diese Option, um zu einer anderen Organisation zu wechseln, wenn Ihre Adobe ID mit mehreren Organisationen verknüpft ist.
1. Klicken Sie auf das Symbol ![Apps](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) (Lösungsschalter), um schnell zu anderen Experience Cloud-Lösungen zu wechseln.
1. Klicken Sie auf das Hilfesymbol ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Help_18_N.svg), um Ihnen schnellen Zugriff auf Lern- und Support-Ressourcen zu gewähren.![
1. Klicken Sie auf das Bell-Symbol ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) ([Benachrichtigungen](/help/implementing/cloud-manager/notifications.md)), um unter anderem Benachrichtigungen und Mitteilungen anzuzeigen.![
1. Klicken Sie auf das Symbol, das den Benutzerzugriff auf Ihre Benutzereinstellungen darstellt. Wenn Sie kein Benutzerbild konfiguriert haben, wird ein zufälliges Symbol zugewiesen.

#### Programmsymbolleiste {#program-toolbar}

Die Programmsymbolleiste enthält Links zum Wechseln zwischen Cloud Manager-Programmen und -Aktionen, die dem Kontext entsprechen.

![Programmsymbolleiste](assets/program-toolbar.png)

1. Der Selektor **Meine Programme** öffnet eine Dropdown-Liste, in der Sie andere Programme schnell auswählen oder kontextbezogene Aktionen ausführen können, z. B. ein neues Programm erstellen
1. Über den Link **Erste Schritte** haben Sie Zugriff auf die Journey[Onboarding-Dokumentation](/help/journey-onboarding/overview.md), um Cloud Manager einzurichten und auszuführen.
1. Die Aktionsschaltfläche bietet kontextbezogene Aktionen, z. B. das Hinzufügen eines Programms.

### Statistiken und Aktionsaufrufe {#statistics}

Der Abschnitt Statistiken und Aktionsaufrufe enthält aggregierte Daten für Ihre Organisation. Wenn Sie beispielsweise Ihre Programme erfolgreich eingerichtet haben, können Statistiken über Ihre Aktivitäten aus den letzten 90 Tagen angezeigt werden, darunter:

* Anzahl der [Bereitstellungen](/help/implementing/cloud-manager/deploy-code.md)
* Anzahl der identifizierten [Code-Qualitätsprobleme](/help/implementing/cloud-manager/code-quality-testing.md)
* Anzahl der Builds

Oder wenn Sie gerade mit der Einrichtung Ihrer Organisation beginnen, gibt es Tipps zu den nächsten Schritten oder Dokumentationsressourcen.

### Bereich &quot;Meine Programme&quot; {#my-programs-section}

Der Hauptinhalt der Konsole **Meine Programme** ist die Liste der Programme im Abschnitt **Meine Programme** .

Im Abschnitt **Meine Programme** werden die Karten der einzelnen Programme aufgelistet. Klicken Sie auf eine Karte, um die Seite **Programmübersicht** des Programms aufzurufen, auf der Sie Details zum Programm finden.

>[!NOTE]
>
>Abhängig von Ihren Berechtigungen können Sie bestimmte Programme möglicherweise nicht auswählen.


Verwenden Sie die Sortieroptionen, um das Programm, das Sie benötigen, leichter zu finden.

![Sortieroptionen](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* Sortieren nach:
   * **Erstellungsdatum** (Standard)
   * **Programmname**
   * **Status**
* ![Symbol &quot;Sortierreihenfolge nach unten&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) Aufsteigend (Standard) / ![Symbol &quot;Sortierreihenfolge nach oben&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg) Absteigend
* ![Symbol für die klassische Rasteransicht](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) Rasteransicht (Standard)
* ![Listensymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ViewList_18_N.svg) Listenansicht

#### Programmkarten {#program-cards}

Eine Karte (oder Zeile in einer Tabelle) stellt jedes Programm dar, bietet einen Überblick über das Programm und schnelle Links, um Maßnahmen zu ergreifen.

![Programmkarte](assets/program-card.png)

* Mit dem Programm verknüpftes Bild, sofern konfiguriert. Das obige Bild ist &quot;WKND&quot;.
* Dem Programm zugewiesener Name. Das obige Bild zeigt &quot;SecurBank Sample&quot;als Programmnamen.
* Diensttyp:
   * **Experience Manager Cloud** - für AEM as a Cloud Service-Programme
   * **Experience Manager** - für [AMS (Adobe Managed Services)-Programme](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/introduction)
* [Programmtyp](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md):
   * Sandbox
   * Produktion
* Status. Im Bild oben ist der Status Bereit mit einem Häkchen.
* Konfigurierte Lösungen. In der obigen Abbildung sind Sites und Assets die konfigurierten Lösungen.
* Erstellungsdatum.

Ein Produktionsprogramm kann so gekennzeichnet sein, dass es zusätzliche Funktionen anzeigt, die Sie zum Zeitpunkt des Hinzufügens ausgewählt haben, z. B.:

* ![HIPAA-Badge](assets/hipaa.png) [HIPAA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* ![WAF-DDOS Badge](assets/waf-ddos-protection.png) [WAF-DDOS Protection](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* [99,99 % SLA (Service Level Agreement)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)

Über das Informationssymbol erhalten Sie auch Schnellzugriff auf zusätzliche Informationen zum Programm (nützlich in der Listenansicht).

![Informationen](assets/information-list-view.png)

Über das Symbol ![Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_22/Smock_More_22_N.svg) haben Sie Zugriff auf weitere Aktionen, die Sie im Programm ausführen können.

![Schaltfläche mit Auslassungspunkten für Programme](assets/program-ellipsis.png)

* Navigieren Sie zu einem bestimmten ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_22/Smock_Data_22_N.svg) [Umgebung](/help/implementing/cloud-manager/manage-environments.md) des Programms
* Öffnen Sie das Symbol ![Programmübersicht](/help/implementing/cloud-manager/assets/program-overview.svg) [Programmübersicht](#program-overview)
* ![Symbol &quot;Bearbeiten&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) [Bearbeiten des Programms](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#editing)
* ![Symbol &quot;Löschen&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)[Löschen eines Sandbox-Programms](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#delete-sandbox-program)

>[!TIP]
>
>Weitere Informationen zu Programmen sowie zum Hinzufügen und Verwalten von Programmen finden Sie unter folgenden Themen:
>
>* [Programme und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
>* [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
>* [Sandbox-Programme erstellen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)


### Abschnitt &quot;Schnelllinks&quot; {#quick-links-section}

Über den Schnelllink-Abschnitt erhalten Sie Zugriff auf häufig verwendete Ressourcen, die miteinander verknüpft sind.

## Seite &quot;Programmübersicht&quot; {#program-overview}

Wenn ein Programm in der Konsole **[Meine Programme](#my-programs-console)** ausgewählt ist, gelangen Sie zur Seite **Programmübersicht**.

![Programmübersicht](assets/program-overview.png)

Die Programmübersicht bietet Zugriff auf alle Details eines Cloud Manager-Programms. Wie die Konsole **Meine Programme** besteht sie aus mehreren Teilen.

1. [Symbolleisten](#program-overview-toolbar) , um schnell zur Konsole &quot;Meine Programme&quot;zurückzuspringen und im Programm zu navigieren
1. [Registerkarten](#program-tabs), um zwischen den verschiedenen Aspekten des Programms zu wechseln
1. Ein [Aktionsaufruf](#cta) basierend auf den letzten Aktionen des Programms
1. Eine [Übersicht über die Umgebungen](#environments) des Programms
1. Eine [Übersicht über die Pipelines](#pipelines) des Programms
1. Überblick über die Leistung des Programms ](#performance)[
1. Links zu [nützlichen Ressourcen](#useful-resources)

### Symbolleisten {#program-overview-toolbar}

Die Symbolleisten für die Programmübersicht ähneln den Symbolleisten der Konsole [Meine Programme](#my-programs-toolbars). Hier werden nur die Unterschiede veranschaulicht.

#### Cloud Manager-Kopfzeile {#cloud-manager-header-2}

In der linken oberen Ecke der Seite befindet sich die Kopfzeile von Adobe Cloud Manager. Sie können auf das Symbol für das seitliche Menü ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) klicken, um das Seitenmenü von Registerkarten zu anderen Bereichen der Software ein- oder auszublenden.![

![Cloud Manager-Seitenmenü](assets/cloud-manager-hamburger.png)

Klicken Sie auf Adobe Cloud Manager , um zur Startseite zurückzukehren.

#### Programmsymbolleiste {#program-toolbar-2}

Die Programmsymbolleiste ermöglicht weiterhin einen schnellen Wechsel zu anderen Programmen, bietet aber auch Zugriff auf kontextbezogene Aktionen wie das Hinzufügen und Bearbeiten des Programms.

![Programmsymbolleiste](assets/cloud-manager-program-toolbar.png)

Die Symbolleiste zeigt immer die Registerkarte an, auf der Sie sich derzeit befinden, auch wenn Sie die Registerkarten mit dem Symbol ![Menü anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) ausgeblendet haben.

### Programmregisterkarten {#program-tabs}

Jedem Programm sind zahlreiche Optionen und Daten zugeordnet. Diese Optionen und Daten werden in Tabs zusammengefasst, um die Navigation im Programm zu vereinfachen. Die Registerkarten bieten Zugriff auf:

**Programm**

* ![Symbol für moderne Rasteransicht](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ModernGridView_18_N.svg) Übersicht - Die Programmübersicht, wie im aktuellen Dokument beschrieben
* ![Glockensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) [Aktivität](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity) - Der Verlauf der Pipeline-Ausführungen des Programms
* ![Workflow-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) [Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines) - Alle für das Programm konfigurierten Pipelines
* ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) [Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md) - Alle für das Programm konfigurierten Repositorys
* ![Diagrammpie-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_GraphPie_18_N.svg) [Berichte](/help/implementing/cloud-manager/sla-reporting.md) - Metriken wie SLA-Daten

**Dienste**

* ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) [Umgebungen](/help/implementing/cloud-manager/manage-environments.md) - Alle für das Programm konfigurierten Umgebungen
* ![Webseiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) [Edge Delivery Sites](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md) - Verwalten von Edge Delivery-Sites
* ![Einstellungssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) [Domäneneinstellungen](/help/implementing/cloud-manager/custom-domain-names/introduction.md) - Verwalten Sie benutzerdefinierte Domänennamen für das Programm
* ![Symbol &quot;Schließen&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) [SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) - Verwalten von SSL-Zertifikaten für das Programm
* ![Symbol für ein soziales Netzwerk](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) [CDN-Konfigurationen](/help/implementing/cloud-manager/custom-domain-names/introduction.md) - Verwalten von CDN-Konfigurationen
* ![Symbol &quot;Aufgabenliste&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) - Zulassungslisten für bestimmte IP-Adressen definieren
* ![Box icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) [Content Sets](/help/implementing/developing/tools/content-copy.md) - Sets von Inhalten, die für Kopierzwecke erstellt wurden
* ![Verlaufssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) [Aktivität &quot;Inhalt kopieren&quot;](/help/implementing/developing/tools/content-copy.md) - Aktivitäten zum Kopieren von Inhalten
* ![Kanalsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Channel_18_N.svg) [Netzwerkinfrastrukturen](/help/security/configuring-advanced-networking.md) - Verwalten erweiterter Netzwerkoptionen für das Programm

**Ressourcen**

* ![Buchsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Book_18_N.svg) Lernpfade - Zusätzliche Lernressourcen über Cloud Manager

Wenn Sie ein Programm öffnen, gelangen Sie standardmäßig zur Registerkarte **Übersicht**. Die aktuelle Registerkarte ist hervorgehoben. Wählen Sie eine andere Registerkarte aus, um deren Details anzuzeigen.

Klicken Sie oben links in der Kopfzeile [Cloud Manager](#cloud-manager-header-2) auf das Symbol ![Menü einblenden](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) , um das Seitenmenü von Registerkarten ein- oder auszublenden.

### Aktionsaufruf {#cta}

Der Abschnitt mit dem Aktionsaufruf stellt Ihnen je nach Status Ihres Programms hilfreiche Informationen zur Verfügung. Bei einem neuen Programm werden möglicherweise die nächsten Schritte und eine Erinnerung an ein &quot;Go-Live&quot;-Datum, [festgelegt während der Programmerstellung, angezeigt.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md)

![Aktionsaufruf für ein neues Programm](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

Bei einem Live-Programm den Status Ihrer letzten Bereitstellung mit Links zu Details und zum Beginn einer neuen Bereitstellung.

![Aktionsaufruf](/help/implementing/cloud-manager/assets/info-banner.png)

### Karte „Umgebungen“ {#environments}

Die Karte **Umgebungen** gibt Ihnen einen Überblick über Ihre Umgebungen und stellt Links für Schnellaktionen bereit.

Die Karte **Umgebungen** listet nur drei Umgebungen auf. Klicken Sie auf **Alle anzeigen**, um alle Umgebungen des Programms zu sehen.

Siehe auch [Umgebungen verwalten](/help/implementing/cloud-manager/manage-environments.md).

### Karte „Pipelines“ {#pipelines}

Die Karte **Pipelines** gibt Ihnen einen Überblick über Ihre Pipelines sowie Links für Schnellaktionen.

Auf der Karte **Pipelines** sind nur drei Pipelines aufgeführt. Klicken Sie auf **Alle anzeigen**, um alle Pipelines des Programms zu sehen.

Weitere Informationen zur Verwaltung Ihrer Pipelines finden Sie unter [Verwalten von Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) .

### Leistungskarte {#performance}

Die Karte **Leistung** bietet einen Überblick über das **[CDN-Dashboard](/help/implementing/cloud-manager/cdn-performance.md)**.

![Leistungskarte](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

### Nützliche Ressourcen {#useful-resources}

Der Abschnitt **Nützliche Ressourcen** enthält Links zu weiteren Lernressourcen für Cloud Manager.
