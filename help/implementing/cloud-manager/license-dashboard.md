---
title: Lizenz-Dashboard
description: Cloud Manager bietet ein Dashboard, über das Sie die AEMaaCS-Produktberechtigungen, die für Ihre Organisation oder Ihren Mandanten verfügbar sind, einfach einsehen können.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b5987ce142a92fee8fff30fbe66d147cd68bdb21
workflow-type: ht
source-wordcount: '938'
ht-degree: 100%

---


# Lizenz-Dashboard {#license-dashboard}

Cloud Manager bietet ein Dashboard, über das Sie die Produktberechtigungen für Adobe Experience Manager as a Cloud Service (AEMaaCS), die für Ihre Organisation oder Ihren Mandanten verfügbar sind, einfach einsehen können.

>[!IMPORTANT]
>
>Das Lizenz-Dashboard gilt nur für AEM as a Cloud Service-Programme. [AMS-Programme](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/introduction) sind nicht im Lizenz-Dashboard enthalten.
>
>Zum Ermitteln des Diensttyps Ihres Programms (AMS oder AEMaaCS) lesen Sie [Navigation durch die Cloud Manager-Benutzeroberfläche](/help/implementing/cloud-manager/navigation.md#program-cards).

## Überblick {#overview}

Das Lizenz-Dashboard von Cloud Manager bietet einfachen Zugriff auf Berechtigungen für Lösungen, die Ihnen für alle Ihre Programme zur Verfügung stehen, einschließlich der verwendeten und der verfügbaren Lösungen. Dazu kommen Verbrauchsmetriken für Inhaltsanfragen mit einer Darstellung der Entwicklung nach Monaten für die Sites-Lösung.

## Zugriff auf das Lizenz-Dashboard {#using-dashboard}

>[!NOTE]
>
>Benutzende mit der Rolle **Geschäftsinhaber** müssen angemeldet sein, damit ihnen das Lizenz-Dashboard angezeigt wird.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** im [Cloud Manager-Header](/help/implementing/cloud-manager/navigation.md#cloud-manager-header) auf das Symbol ![Menü anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg). Durch diese Aktion werden die Registerkarten angezeigt.
1. Klicken Sie auf der Registerkarte auf die Option **Lizenz**.

![Lizenz-Dashboard](assets/license-dashboard.png)

Das Dashboard ist in drei Abschnitte unterteilt, die Ihnen Folgendes zeigen:

* **Lösungen**: Die von Ihnen lizenzierten Lösungen. Beispielsweise Sites, Edge Delivery Services, Assets u. a.

  ![Lösungsliste](assets/solutions.png)

* **Add-ons**: Die mit Ihren lizenzierten Lösungen verfügbaren Add-ons.
* **Sonstige Berechtigungen**: Die Sandbox- und Entwicklungsumgebung sowie sonstigen Berechtigungen, die mandantenseitig genutzt werden können.

In jedem Abschnitt wird zusammengefasst, welche Produkte bzw. Umgebungen verfügbar sind und wie sie verwendet werden. Derzeit werden nur Sites- und Asset-Lösungen angezeigt, selbst wenn im Mandanten andere Lösungen vorhanden sind.

* In der Spalte **Status** wird die Anzahl der nicht verwendeten Berechtigungen im Vergleich zur Gesamtanzahl angezeigt, die für den Mandanten verfügbar sind.
* Die Spalte **Konfiguriert in** gibt die Programme an, auf die die Lösungsberechtigungen angewendet wurden.
   * Eine Berechtigung gilt nur als verwendet, wenn eine Produktionsumgebung erstellt wird. Oder, falls schon eine existiert, wenn eine Update-Pipeline darauf ausgeführt wurde.
   * Es wird nur eine begrenzte Anzahl von Programmen einzeln in der Spalte aufgeführt, der Rest wird durch einen Eintrag `+x` repräsentiert.
   * Bewegen Sie den Mauszeiger über den Eintrag `+x`, damit ein Popup mit den Details zu allen Programmen angezeigt wird.
* In der Spalte **Nutzung** wird die Schaltfläche **[Nutzungsdetails anzeigen](#view-usage-details)** angezeigt, um Nutzungsstatistiken für die Lösung anzuzeigen.

>[!TIP]
>
>Informationen zum Verwalten Ihrer Adobe-Berechtigungen in Ihrem gesamten Unternehmen über die Admin Console finden Sie im [Überblick über die Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html).

## Nutzungsdetails anzeigen {#view-usage-details}

<!--
The **View usage details** button gives access to the chosen solution's **Usage Details** window. This window gives a detailed breakdown including charts to show your solution's usage. How that usage is measured depends on the chosen solution. -->

Die Schaltfläche **Nutzungsdetails anzeigen** im Lizenzbereich von Cloud Manager bietet eine detaillierte Aufschlüsselung Ihrer aktuellen Ressourcennutzung. Wenn Sie darauf klicken, wird ein Bericht oder Dashboard geöffnet, in dem wichtige Metriken zu Ihrer Lizenz angezeigt werden. <!-- ADD THIS SENTENCE IF ASSETS USAGE DETAILS GETS REINSTATED ", such as the number of users, storage consumption, or bandwidth usage, depending on the type of services you're using." --> Diese Funktion hilft Ihnen, die Einhaltung Ihrer vertraglichen Verpflichtungen zu überwachen und sicherzustellen, und bietet gleichzeitig Einblicke in eine bessere Ressourcenplanung und -optimierung.

### Details zur Site-Nutzung {#sites-usage-details}

Das Fenster **Details zur Site-Nutzung** enthält Diagramme, die einen Überblick über die Verwendung Ihrer Sites-Lizenzen auf der Grundlage von [Inhaltsanfragen](#what-is-a-content-request) geben.

![Fenster „Details zur Site-Nutzung“](assets/sites-usage-details.png)

Die linke Seite des Fensters zeigt ein Tortendiagramm mit der Aufschlüsselung des Vertrags für das im Dropdown-Menü **Vertragsjahr anzeigen** ausgewählte Vertragsjahr.

Auf der rechten Seite des Fensters befindet sich ein Flächendiagramm, in dem die Nutzung für das ausgewählte Vertragsjahr nach Programm aufgeschlüsselt dargestellt wird. Wenn Sie den Mauszeiger darüber bewegen, wird ein Popup mit Details pro Programm für den ausgewählten Zeitpunkt angezeigt.

In der rechten oberen Ecke der Dashboard-Seite können Sie auf **Bericht herunterladen** klicken, um die Daten als CSV-Datei zu exportieren. Dieser Download vereinfacht die Analyse und Freigabe von Nutzungs-Trends.

<!-- REMOVED AS PER CQDOC-21983
### Assets usage details {#assets-usage-details}

The **Assets usage details** window, presents graphs giving an overview of the usage of your Assets licenses based on [storage](#storage) and [standard users](#standard-users). Select the appropriate tab to toggle between the views.

For both storage and standard users views, you can use the **Environment Type** dropdown to toggle the view between production, stage, and development environments.

#### Storage {#storage}

![Assets usage details window for storage](assets/assets-usage-details-storage.png)

The left side of the window presents a pie chart showing the contract breakdown for the contract year selected in the **View contract year** dropdown.

The right side of the window presents an area chart showing the usage broken down by program over time for the selected contract year. A hover reveals a popup with details per program for the selected point in time.

#### Standard Users {#standard-users}

![Assets usage details window for standard-users](assets/assets-usage-details-standard-users.png)

The left side of the window presents a pie chart showing the contract breakdown for the contract year selected in the **View contract year** dropdown.

The right side of the window presents an area chart showing the usage broken down by program over time for the selected contract year. A hover reveals a popup with details per program for the selected point in time. -->

## Häufig gestellte Fragen {#faq}

### Was ist eine Inhaltsanfrage?{#what-is-a-content-request}

Bei einer Inhaltsanfrage handelt es sich um eine an AEM Sites oder ein von der Kundschaft bereitgestelltes Caching-System, wie z. B. ein Netzwerk zur Inhaltsbereitstellung. Sie ruft Inhalte oder Daten im HTML-Format für Seitenansichten ab. Oder im JSON-Format für API-Aufrufe.

Für jeden Seitenaufruf oder für jeweils fünf API-Aufrufe wird 1 Inhaltsanfrage gezählt, gemessen am Eingang des ersten Caching-Systems, das eine Inhaltsanfrage erhält. Inhaltsanfragen werden nur für Produktionsumgebungen gezählt.

Inhaltsanfragen schließen Anfragen oder Aktivitäten aus, die von oder für Adobe allein zum Zweck der Bereitstellung von Produkten und Dienstleistungen initiiert wurden. Auch der von Adobe identifizierte Benutzeragenten-Traffic von Bots, Crawlern und Spidern im Zusammenhang mit gängigen Suchmaschinen und Social-Media-Services ist ausgeschlossen.

Siehe auch [Grundlegendes zu Cloud Service-Inhaltsanfragen](/help/implementing/cloud-manager/content-requests.md).

### Wie misst Adobe Experience Manager Inhaltsanfragen?{#how-are-content-requests-measured}

Inhaltsanfragen werden auf den Edge-Servern von AEM as a Cloud Service erfasst. Der Ursprungs-Traffic zählt nicht für Inhaltsanfragen. Das in AEM as a Cloud Service integrierte CDN verfolgt gültige HTML- und JSON-Anfragen.

AEM verfügt auch über Regeln, um bekannte Bots auszuschließen, einschließlich bekannter Services, die die Site regelmäßig besuchen, um ihren Suchindex oder -Service zu aktualisieren.

Siehe auch [Grundlegendes zu Cloud Service-Inhaltsanfragen](/help/implementing/cloud-manager/content-requests.md).

### Warum zeigt mein Analytics-Bericht andere Ergebnisse als die AEM-Inhaltsanfragen an?{#why-are-reports-different}

Inhaltsanfragen weisen Abweichungen von den Analytics-Reporting-Tools eines Unternehmens auf. Weitere Informationen finden Sie unter [Grundlegendes zu Cloud Service-Inhaltsanfragen](/help/implementing/cloud-manager/content-requests.md).

### Wie erfahre ich mehr über mein Inhaltsanfragevolumen?{#current-request-volumes}

Wenn Sie zusätzliche Einblicke in das Inhaltsanfragevolumen erhalten möchten, das im Lizenz-Dashboard angezeigt wird, kann Ihnen Ihr Adobe-Team einen Bericht bereitstellen, der die wichtigsten Treiber von Inhaltsanfragen aufzeigt. Wenden Sie sich an Ihr Adobe-Team oder an den Adobe-Kunden-Support, um einen Bericht über die hauptsächliche Nutzung anzufordern.

### Was passiert, wenn ich mein eigenes CDN verwende?{#using-own-cdn}

Das Lizenz-Dashboard zeigt nur Daten an, die vom Cloud Service-CDN verfolgt werden. Wenn Sie sich für ein eigenes CDN (BYOCDN) entscheiden, melden Sie das in Ihrem Vertrag festgelegte Inhaltsanfragevolumen einmal jährlich an Adobe.


