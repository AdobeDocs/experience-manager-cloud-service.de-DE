---
title: Navigieren in der Benutzeroberfläche von Cloud Manager
description: Erfahren Sie, wie die Benutzeroberfläche von Cloud Manager aufgebaut ist und wie Sie Ihre Programme und Umgebungen verwalten.
exl-id: 3f3d7631-2bc9-440b-9888-50f6529bcd42
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4c42888af1e846c011242af2c328e553bb811cfd
workflow-type: tm+mt
source-wordcount: '1693'
ht-degree: 98%

---


# Navigieren in der Benutzeroberfläche von Cloud Manager {#navigation}

Erfahren Sie, wie die Benutzeroberfläche von Cloud Manager aufgebaut ist und wie Sie Ihre Programme und Umgebungen verwalten.


Die Benutzeroberfläche für die Cloud-Verwaltung besteht in erster Linie aus zwei grafischen Schnittstellen:

* der [Konsole „Meine Programme“](#my-programs-console), in der Sie alle Ihre Programme anzeigen und verwalten können.
* dem [Fenster „Programmübersicht“](#program-overview), in dem Sie die Details eines einzelnen Programms sehen und verwalten können.

>[!TIP]
>
>Sehen Sie sich auch die [Tour zur Onboarding-Dokumentation](/help/journey-onboarding/overview.md) an, um einen vollständigen Überblick über den Einstieg in AEM as a Cloud Service mit Cloud Manager zu erhalten.


## KI-Assistent in AEM

Für Kunden, [ die erforderlichen Kriterien erfüllt haben](/help/implementing/cloud-manager/ai-assistant-in-aem.md#get-access) steht der KI-Assistent in AEM den Benutzenden ihres Unternehmens zur Verfügung. Siehe [KI-Assistent in AEM](/help/implementing/cloud-manager/ai-assistant-in-aem.md).


## Konsole „Meine Programme“ {#my-programs-console}

Wenn Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) anmelden und die entsprechende Organisation auswählen, gelangen Sie in die Konsole **Meine Programme**.

![Konsole „Meine Programme“](assets/my-programs-console.png)

Die Konsole „Meine Programme“ bietet einen Überblick über alle Programme, auf die Sie in der ausgewählten Organisation Zugriff haben. Sie besteht aus mehreren Teilen.

1. [Symbolleisten](#toolbars-my-programs-toolbars) für die Auswahl von Organisationen, Warnmeldungen und Kontoeinstellungen
1. Registerkarten, um die aktuelle Ansicht der Programme zu wechseln:
   * Ansicht der **Startseite** (Standard) mit Auswahl der Ansicht **Meine Programme**, die einen Überblick über alle Programme enthält
   * **Lizenz** für den Zugriff auf das [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).
   * Beachten Sie, dass die Registerkarten standardmäßig geschlossen sind und über das ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) im [Cloud Manager-Header](#cloud-manager-header) angezeigt werden können.
1. [Statistiken und Aktionsaufrufe](#statistics) für einen Überblick über Ihre aktuellen Aktivitäten
1. [**Meine Programme**](#my-programs-section) mit einem Überblick über Ihre gesamten Programme
1. [Direkt-Links](#quick-links-section) für den einfachen Zugriff auf zugehörige Ressourcen.

>[!TIP]
>
>Weitere Informationen zu Programmen finden Sie unter [Programme und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

### Symbolleisten {#my-programs-toolbars}

Es gibt zwei Symbolleisten übereinander.

#### Cloud Manager-Kopfzeile {#cloud-manager-header}

Die erste ist der Header von Cloud Manager, der bestehen bleibt, wenn Sie in Cloud Manager navigieren. Er ist ein Anker, der Ihnen Zugriff auf Einstellungen und Informationen bietet, die für alle Cloud Manager-Programme gelten.

![Die Kopfzeile von Experience Cloud](assets/experience-cloud-header.png)

1. Klicken Sie auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) (Seitenmenü ein- oder ausblenden), um Zugriff auf verschiedene Registerkarten zu erhalten, über die Sie zu bestimmten Teilen eines Programms gelangen können. Alternativ können Sie je nach Kontext zwischen dem [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md) und der Konsole **[Meine Programme](#my-programs-console)** wechseln.
1. Durch Klicken auf die Schaltfläche „Adobe Cloud Manager“ gelangen Sie zurück zur Konsole „Meine Programme“ von Cloud Manager, unabhängig davon, wo Sie sich in Cloud Manager befinden.
1. Klicken Sie auf **Feedback**, um Adobe Feedback zu Cloud Manager zu geben.
1. Durch Klicken auf die Organisationsauswahl wird die Organisation angezeigt, bei der Sie derzeit angemeldet sind (in diesem Beispiel „Foundation Internal“). Klicken Sie auf diese Option, um zu einer anderen Organisation zu wechseln, wenn Ihre Adobe ID mit mehreren Organisationen verknüpft ist.
1. Klicken Sie auf ![Apps-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) (Lösungsumschalter), um schnell zu anderen Experience Cloud-Lösungen zu wechseln.
1. Ein Klicken auf ![Hilfesymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Help_18_N.svg) bietet Schnellzugriff auf Lern- und Support-Ressourcen.
1. Klicken Sie auf ![Glockensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) ([Benachrichtigungen](/help/implementing/cloud-manager/notifications.md)), um unter anderem Benachrichtigungen und Mitteilungen anzuzeigen.
1. Klicken Sie auf das Symbol für die Benutzerin bzw. den Benutzer, um auf Ihre Benutzereinstellungen zuzugreifen. Wenn Sie kein Benutzerbild konfiguriert haben, wird ein zufälliges Symbol zugewiesen.

#### Programmsymbolleiste {#program-toolbar}

Die Programmsymbolleiste enthält Links zum Wechseln zwischen Cloud Manager-Programmen und -Aktionen, die dem Kontext entsprechen.

![Programmsymbolleiste](assets/program-toolbar.png)

1. Die Auswahl **Meine Programme** wird in einer Dropdown-Liste geöffnet, in der Sie andere Programme schnell auswählen oder kontextbezogene Aktionen ausführen können, z. B. die Erstellung eines neuen Programms
1. Über den Link **Erste Schritte** erhalten Sie Zugriff auf die [Tour zur Onboarding-Dokumentation](/help/journey-onboarding/overview.md), die Ihnen den Einstieg in Cloud Manager erleichtert.
1. Die Aktionsschaltfläche bietet kontextbezogene Aktionen, z. B. das Hinzufügen eines Programms.

### Statistiken und Aktionsaufrufe {#statistics}

Im Abschnitt für Statistiken und Aktionsaufrufe finden Sie zusammengefasste Daten zu Ihrer Organisation. Wenn Sie z. B. Ihre Programme erfolgreich eingerichtet haben, können Sie hier Statistiken über Ihre Aktivitäten der letzten 90 Tage einsehen, einschließlich:

* Anzahl der [Bereitstellungen](/help/implementing/cloud-manager/deploy-code.md)
* Anzahl der identifizierten [Code-Qualitätsprobleme](/help/implementing/cloud-manager/code-quality-testing.md)
* Anzahl der Builds

Oder wenn Sie gerade mit der Einrichtung Ihrer Organisation beginnen, gibt es Tipps zu den nächsten Schritten oder Dokumentationsressourcen.

### Abschnitt „Meine Programme“ {#my-programs-section}

Der Hauptinhalt der Konsole **Meine Programme** ist die Liste der Programme im Abschnitt **Meine Programme**.

Im Abschnitt **Meine Programme** sind die Karten der einzelnen Programme aufgelistet. Klicken Sie auf eine Karte, um die Seite **Programmübersicht** des Programms aufzurufen, auf der Sie Details zum Programm finden.

>[!NOTE]
>
>Abhängig von Ihren Berechtigungen können Sie bestimmte Programme möglicherweise nicht auswählen.


Verwenden Sie die Sortieroptionen, um das benötigte Programm leichter zu finden.

![Sortieroptionen](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* Sortieren nach:
   * **Erstellungsdatum** (Standard)
   * **Programmname**
   * **Status**
* ![Symbol für Sortierreihenfolge nach unten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) Aufsteigend (Standard) / ![Symbol für Sortierreihenfolge nach oben](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg) Absteigend
* ![Symbol für die klassische Rasteransicht](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) Rasteransicht (Standard)
* ![Symbol für das Anzeigen der Liste](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ViewList_18_N.svg) Listenansicht

#### Programmkarten {#program-cards}

Jedes Programm wird durch eine Karte (oder eine Zeile in einer Tabelle) dargestellt, die einen Überblick über das Programm und Direkt-Links bietet, um Maßnahmen zu ergreifen.

![Programmkarte](assets/program-card.png)

* Das mit dem Programm verknüpfte Bild, sofern konfiguriert. Das Bild oben zeigt „WKND“.
* Dem Programm zugewiesener Name. Das Bild oben zeigt „SecurBank Sample“ als Programmnamen.
* Diensttyp:
   * **Experience Manager Cloud** — für AEM as a Cloud Service-Programme
   * **Experience Manager** — für [AMS(Adobe Managed Services)-Programme](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/introduction)
* [Programmtyp](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
   * Sandbox
   * Produktion
* Status. Im Bild oben lautet der Status „Bereit“ mit einem Häkchen.
* Konfigurierte Lösungen. Auf dem Bild oben sind „Sites“ und „Assets“ die konfigurierten Lösungen.
* Erstellungsdatum.

Ein Produktionsprogramm kann so gekennzeichnet sein, dass es zusätzliche Funktionen anzeigt, die Sie zum Zeitpunkt des Hinzufügens ausgewählt haben, z. B.:

* ![HIPAA-Zeichen](assets/hipaa.png) [HIPAA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* ![WAF-DDOS-Zeichen](assets/waf-ddos-protection.png) [WAF-DDOS-Schutz](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* [SLA (Service Level Agreement) von 99,99 %](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)

Über das Informationssymbol erhalten Sie auch Schnellzugriff auf zusätzliche Informationen zum Programm (nützlich in der Listenansicht).

![Informationen](assets/information-list-view.png)

Über das Symbol ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_22/Smock_More_22_N.svg) gelangen Sie zu weiteren Aktionen, die Sie im Programm ausführen können.

![Schaltfläche mit Auslassungspunkten für Programme](assets/program-ellipsis.png)

* Navigieren zu einer bestimmten ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_22/Smock_Data_22_N.svg) [Umgebung](/help/implementing/cloud-manager/manage-environments.md) des Programms
* Öffnen der ![Programmübersicht-Symbol](/help/implementing/cloud-manager/assets/program-overview.svg) [Programmübersicht](#program-overview)
* ![Bearbeiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) [Bearbeiten des Programms](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#editing)
* ![Löschen-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)[Löschen eines Sandbox-Programms](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#delete-sandbox-program)

>[!TIP]
>
>Weitere Informationen zu Programmen sowie zum Hinzufügen und Verwalten von Programmen finden Sie unter folgenden Themen:
>
>* [Programme und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
>* [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
>* [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)


### Abschnitt „Direkt-Links“ {#quick-links-section}

Über den Abschnitt „Direkt-Links“ erhalten Sie Zugriff auf häufig verwendete, zugehörige Ressourcen.

## Seite „Programmübersicht“ {#program-overview}

Wenn ein Programm in der Konsole **[Meine Programme](#my-programs-console)** ausgewählt wird, werden Sie zur Seite **Programmübersicht** weitergeleitet.

![Programmübersicht](assets/program-overview.png)

Die Programmübersicht bietet Zugriff auf alle Details eines Cloud Manager-Programms. Wie die Konsole **Meine Programme** besteht sie aus mehreren Teilen.

1. [Symbolleisten](#program-overview-toolbar), um schnell zur Konsole „Meine Programme“ zurückzukehren und durch das Programm zu navigieren
1. [Registerkarten](#program-tabs), um zwischen den verschiedenen Aspekten des Programms zu wechseln
1. Ein [Aktionsaufruf](#cta) basierend auf den letzten Aktionen des Programms
1. Eine [Übersicht über die Umgebungen](#environments) des Programms
1. Eine [Übersicht über die Pipelines](#pipelines) des Programms
1. Eine [Übersicht über die Leistung](#performance) des Programms
1. Links zu [nützlichen Ressourcen](#useful-resources)

### Symbolleisten {#program-overview-toolbar}

Die Symbolleisten für die Programmübersicht ähneln denen der [Konsole „Meine Programme“](#my-programs-toolbars). Hier werden nur die Unterschiede veranschaulicht.

#### Cloud Manager-Kopfzeile {#cloud-manager-header-2}

In der linken oberen Ecke der Seite befindet sich der Adobe Cloud Manager-Header. Sie können auf ![Seitenmenü-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) klicken, um das Seitenmenü von Registerkarten zu anderen Bereichen der Software ein- oder auszublenden.

![Cloud Manager-Seitenmenü](assets/cloud-manager-hamburger.png)

Klicken Sie auf „Adobe Cloud Manager“, um zur Startseite zurückzukehren.

#### Programmsymbolleiste {#program-toolbar-2}

Die Programmsymbolleiste ermöglicht weiterhin einen schnellen Wechsel zu anderen Programmen, bietet aber auch Zugriff auf kontextbezogene Aktionen wie das Hinzufügen und Bearbeiten des Programms.

![Programmsymbolleiste](assets/cloud-manager-program-toolbar.png)

Die Symbolleiste zeigt immer die Registerkarte an, die gerade aktiv ist, selbst wenn Sie die Registerkarten mit ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) ausgeblendet haben.

### Programmregisterkarten {#program-tabs}

Jedem Programm sind zahlreiche Optionen und Daten zugeordnet. Diese Optionen und Daten werden auf Registerkarten zusammengefasst, um die Navigation im Programm zu vereinfachen. Die Registerkarten bieten Zugriff auf:

**Programm**

* ![Symbol für moderne Rasteransicht](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ModernGridView_18_N.svg) Übersicht: Die im aktuellen Dokument beschriebene Programmübersicht
* ![Glockensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) [Aktivität:](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity) Verlauf der Pipeline-Ausführungen des Programms
* ![Workflow-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) [Pipelines:](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines) Alle für das Programm konfigurierten Pipelines
* ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) [Repositorys:](/help/implementing/cloud-manager/managing-code/managing-repositories.md) Alle für das Programm konfigurierten Repositorys
* ![Kreisdiagramm-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_GraphPie_18_N.svg) [Berichte:](/help/implementing/cloud-manager/sla-reporting.md) Metriken wie SLA-Daten

**Dienste**

* ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) [Umgebungen:](/help/implementing/cloud-manager/manage-environments.md) Alle für das Programm konfigurierten Umgebungen
* ![Webseiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) [Edge Delivery Sites:](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md) Verwalten von Edge Delivery-Sites
* ![Einstellungssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) [Domain-Einstellungen:](/help/implementing/cloud-manager/custom-domain-names/introduction.md) Verwalten benutzerdefinierter Domain-Namen für das Programm
* ![Symbol für geschlossenes Schloss](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) [SSL-Zertifikate:](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) Verwalten von SSL-Zertifikaten für das Programm
* ![Symbol für soziale Netzwerke](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) [CDN-Konfigurationen](/help/implementing/cloud-manager/custom-domain-names/introduction.md): Verwalten von Domain-Zuordnungen
* ![Aufgabenlisten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) [IP-Zulassungslisten:](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) Definieren von Zulassungslisten für bestimmte IP-Adressen
* ![Kisten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) [Content-Sets:](/help/implementing/developing/tools/content-copy.md) Sets von Inhalten, die für Kopierzwecke erstellt wurden
* ![Verlaufs-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) [Aktivität zum Kopieren von Inhalten:](/help/implementing/developing/tools/content-copy.md) Aktivitäten zur Inhaltskopie
* ![Kanal-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Channel_18_N.svg) [Netzwerkinfrastrukturen:](/help/security/configuring-advanced-networking.md) Verwalten erweiterter Netzwerkoptionen für das Programm

**Ressourcen**

* ![Buch-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Book_18_N.svg) Lernpfade: Zusätzliche Lernressourcen zu Cloud Manager

Wenn Sie ein Programm öffnen, gelangen Sie standardmäßig zur Registerkarte **Übersicht**. Die aktuelle Registerkarte ist hervorgehoben. Wählen Sie eine andere Registerkarte aus, um deren Details anzuzeigen.

Klicken Sie oben links im [Cloud Manager-Header](#cloud-manager-header-2) auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das Seitenmenü von Registerkarten ein- oder auszublenden.

### Aktionsaufruf {#cta}

Der Abschnitt mit dem Aktionsaufruf stellt Ihnen je nach Status Ihres Programms hilfreiche Informationen zur Verfügung. Für ein neues Programm werden Ihnen möglicherweise die nächsten Schritte angezeigt sowie eine Erinnerung an den Tag der Live-Schaltung, [der bei der Programmerstellung festgelegt wurde](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).

![Aktionsaufruf für ein neues Programm](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

Bei einem Live-Programm den Status Ihrer letzten Bereitstellung mit Links zu Details und zum Beginn einer neuen Bereitstellung.

![Aktionsaufruf](/help/implementing/cloud-manager/assets/info-banner.png)

### Karte „Umgebungen“ {#environments}

Die Karte **Umgebungen** gibt Ihnen einen Überblick über Ihre Umgebungen und stellt Links für Schnellaktionen bereit.

Auf der Karte **Umgebungen** sind nur drei Umgebungen aufgeführt. Klicken Sie auf ![Workflow-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Alle anzeigen**, um alle Umgebungen des Programms anzuzeigen.

Weitere Informationen finden Sie auch unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md).

### Karte „Pipelines“ {#pipelines}

Die Karte **Pipelines** gibt Ihnen einen Überblick über Ihre Pipelines und stellt Links für Schnellaktionen bereit.

Auf der Karte **Pipelines** sind nur drei Pipelines aufgeführt. Klicken Sie auf ![Workflow-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Alle anzeigen**, um alle Pipelines des Programms anzuzeigen.

Weitere Informationen zur Verwaltung Ihrer Pipelines finden Sie unter [Verwalten von Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md).

### Leistungskarte {#performance}

Die Karte **Leistung** gibt einen Überblick über das **[CDN-Dashboard](/help/implementing/cloud-manager/cdn-performance.md)**.

![Leistungskarte](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

### Nützliche Ressourcen {#useful-resources}

Der Abschnitt **Nützliche Ressourcen** enthält Links zu weiteren Lernressourcen für Cloud Manager.
