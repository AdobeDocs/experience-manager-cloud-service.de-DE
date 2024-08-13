---
title: Lizenz-Dashboard
description: Cloud Manager bietet ein Dashboard, über das Sie die AEMaaCS-Produktberechtigungen, die für Ihre Organisation oder Ihren Mandanten verfügbar sind, einfach einsehen können.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: eae5c75e1bf4f7201fe2c01d08737d36489ca3e4
workflow-type: ht
source-wordcount: '1101'
ht-degree: 100%

---


# Lizenz-Dashboard {#license-dashboard}

Cloud Manager bietet ein Dashboard, über das Sie die AEMaaCS-Produktberechtigungen, die für Ihre Organisation oder Ihren Mandanten verfügbar sind, einfach einsehen können.

>[!IMPORTANT]
>
>Das Lizenz-Dashboard gilt nur für AEM as a Cloud Service-Programme. [AMS-Programme](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/introduction) sind nicht im Lizenz-Dashboard enthalten.
>
>Informationen zum Ermitteln des Diensttyps Ihres Programms (AMS oder AEMaaCS) finden Sie im Dokument [Navigieren auf der Benutzeroberfläche von Cloud Manager](/help/implementing/cloud-manager/navigation.md#program-cards).

## Übersicht {#overview}

Das Lizenz-Dashboard von Cloud Manager bietet einfachen Zugriff auf folgende Informationen:

1. Berechtigungen für Lösungen stehen Ihnen für alle Ihre Programme zur Verfügung, einschließlich verwendeter und verfügbarer Lösungen
1. Verbrauchsmetriken für Inhaltsanfragen mit einer Darstellung der Entwicklung nach Monaten für die Sites-Lösung

## Verwenden des Lizenz-Dashboards {#using-dashboard}

Gehen Sie wie folgt vor, um auf Ihr Lizenz-Dashboard zuzugreifen.

>[!NOTE]
>
>Benutzende mit der Rolle **Geschäftsinhaber** müssen angemeldet sein, damit ihnen das Lizenz-Dashboard angezeigt wird.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Tippen oder klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** auf die Schaltfläche mit dem Hamburger-Menü im [Cloud Manager-Header.](/help/implementing/cloud-manager/navigation.md#cloud-manager-header) Dadurch werden die Registerkarten angezeigt.
1. Tippen oder klicken Sie auf der Registerkarte auf die Option **Lizenz** .

![Lizenz-Dashboard](assets/license-dashboard.png)

Das Dashboard ist in drei Abschnitte unterteilt, die Ihnen Folgendes zeigen:

* **Lösungen**: In diesem Abschnitt werden die von Ihnen lizenzierten Lösungen wie Sites oder Assets zusammengefasst.
* **Add-ons**: In diesem Abschnitt werden die Add-ons zu Ihren lizenzierten Lösungen zusammengefasst, die für Sie verfügbar sind.
* **Andere Berechtigungen**: In diesem Abschnitt wird zusammengefasst, welche Sandbox- und Entwicklungsumgebung sowie andere Berechtigungen in Ihrem Mandanten genutzt werden können.

In jedem Abschnitt wird zusammengefasst, welche Produkte bzw. Umgebungen verfügbar sind und wie sie verwendet werden. Derzeit werden nur Sites- und Asset-Lösungen angezeigt, selbst wenn im Mandanten andere Lösungen vorhanden sind.

* In der Spalte **Status** wird die Anzahl der nicht verwendeten Berechtigungen im Vergleich zur Gesamtanzahl angezeigt, die für den Mandanten verfügbar sind.
* Die Spalte **Konfiguriert in** gibt die Programme an, auf die die Lösungsberechtigungen angewendet wurden.
   * Eine Berechtigung gilt nur dann als verwendet, wenn eine Produktionsumgebung erstellt wurde oder, falls eine existiert, wenn eine Update-Pipeline dafür ausgeführt wurde.
   * Es wird nur eine begrenzte Anzahl von Programmen einzeln in der Spalte aufgeführt, der Rest wird durch einen Eintrag `+x` repräsentiert.
   * Bewegen Sie den Mauszeiger über den Eintrag `+x`, damit ein Popup mit den Details zu allen Programmen angezeigt wird.
* In der Spalte **Nutzung** wird die Schaltfläche **[Nutzungsdetails anzeigen](#view-usage-details)** angezeigt, um Nutzungsstatistiken für die Lösung anzuzeigen.

>[!TIP]
>
>Informationen zum Verwalten Ihrer Adobe-Berechtigungen in Ihrem gesamten Unternehmen über die Admin Console finden Sie im [Überblick über die Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html).

## Anzeigen von Nutzungsdetails {#view-usage-details}

Die Schaltfläche **Nutzungsdetails anzeigen** bietet Zugriff auf das Fenster **Nutzungsdetails** der ausgewählten Lösung. In diesem Fenster finden Sie eine detaillierte Aufschlüsselung mit Diagrammen zur Verwendung Ihrer Lösung. Wie diese Nutzung gemessen wird, hängt von der gewählten Lösung ab.

### Details zur Site-Nutzung {#sites-usage-details}

Das Fenster **Details zur Site-Nutzung** enthält Diagramme, die einen Überblick über die Verwendung Ihrer Sites-Lizenzen auf der Grundlage von [Inhaltsanforderungen](#what-is-a-content-request) geben.

![Fenster „Details zur Site-Nutzung“](assets/sites-usage-details.png)

Die linke Seite des Fensters zeigt ein Tortendiagramm mit der Aufschlüsselung des Vertrags für das im Dropdown-Menü **Vertragsjahr anzeigen** ausgewählte Vertragsjahr.

Auf der rechten Seite des Fensters befindet sich ein Flächendiagramm, in dem die Nutzung für das ausgewählte Vertragsjahr nach Programm aufgeschlüsselt dargestellt wird. Wenn Sie den Mauszeiger darüber bewegen, wird ein Popup mit Details pro Programm für den ausgewählten Zeitpunkt angezeigt.

### Details zur Asset-Nutzung {#assets-usage-details}

Das Fenster **Details zur Asset-Nutzung** enthält Diagramme, die einen Überblick über die Verwendung Ihrer Asset-Lizenzen auf der Grundlage von [Speicher](#storage) und [Standardbenutzenden](#standard-users) geben. Wählen Sie die entsprechende Registerkarte aus, um zwischen den Ansichten umzuschalten.

Für die Ansichten von Speicher und Standardbenutzenden können Sie das Dropdown-Menü **Umgebungstyp** verwenden, um die Ansicht zwischen Produktions-, Staging- und Entwicklungsumgebungen umzuschalten.

#### Speicher {#storage}

![Fenster „Details zur Asset-Nutzung“ für den Speicher](assets/assets-usage-details-storage.png)

Die linke Seite des Fensters zeigt ein Tortendiagramm mit der Aufschlüsselung des Vertrags für das im Dropdown-Menü **Vertragsjahr anzeigen** ausgewählte Vertragsjahr.

Auf der rechten Seite des Fensters befindet sich ein Flächendiagramm, in dem die Nutzung für das ausgewählte Vertragsjahr nach Programm aufgeschlüsselt dargestellt wird. Wenn Sie den Mauszeiger darüber bewegen, wird ein Popup mit Details pro Programm für den ausgewählten Zeitpunkt angezeigt.

#### Standardbenutzende {#standard-users}

![Fenster „Details zur Asset-Nutzung“ für Standardbenutzende](assets/assets-usage-details-standard-users.png)

Die linke Seite des Fensters zeigt ein Tortendiagramm mit der Aufschlüsselung des Vertrags für das im Dropdown-Menü **Vertragsjahr anzeigen** ausgewählte Vertragsjahr.

Auf der rechten Seite des Fensters befindet sich ein Flächendiagramm, in dem die Nutzung für das ausgewählte Vertragsjahr nach Programm aufgeschlüsselt dargestellt wird. Wenn Sie den Mauszeiger darüber bewegen, wird ein Popup mit Details pro Programm für den ausgewählten Zeitpunkt angezeigt.

## Häufig gestellte Fragen {#faq}

### Was ist eine Inhaltsanfrage? {#what-is-a-content-request}

Bei einer Inhaltsanfrage handelt es sich um eine Anfrage, die an AEM Sites oder ein kundenseitig bereitgestelltes Caching-System wie ein Content Delivery Network (CDN) gesendet wird, um Inhalte oder Daten entweder im HTML-Format als Seitenansicht oder im JSON-Format als API-Aufruf bereitzustellen.

Für jeden Seitenaufruf oder für jeweils fünf API-Aufrufe wird 1 Inhaltsanfrage gezählt, gemessen am Eingang des ersten Caching-Systems, das eine Inhaltsanfrage erhält. Inhaltsanfragen werden nur für Produktionsumgebungen gezählt.

Inhaltsanfragen schließen Anfragen oder Aktivitäten aus, die von oder für Adobe allein zum Zweck der Bereitstellung von Produkten und Dienstleistungen initiiert wurden. Auch der von Adobe identifizierte Benutzeragenten-Traffic von Bots, Crawlern und Spidern im Zusammenhang mit gängigen Suchmaschinen und Social-Media-Services ist ausgeschlossen.

Siehe auch [Grundlegendes zu Cloud Service-Inhaltsanfragen](/help/implementing/cloud-manager/content-requests.md).

### Wie misst Adobe Experience Manager Inhaltsanfragen? {#how-are-content-requests-measured}

Inhaltsanfragen werden auf den Edge-Servern von AEM as a Cloud Service erfasst. Der Ursprungs-Traffic zählt nicht für Inhaltsanfragen. Das in AEM as a Cloud Service integrierte CDN verfolgt gültige HTML- und JSON-Anfragen.

AEM verfügt auch über Regeln, um bekannte Bots auszuschließen, einschließlich bekannter Services, die die Site regelmäßig besuchen, um ihren Suchindex oder -Service zu aktualisieren.

Siehe auch [Grundlegendes zu Cloud Service-Inhaltsanfragen](/help/implementing/cloud-manager/content-requests.md).

### Warum zeigt mein Analytics-Bericht andere Ergebnisse als die AEM-Inhaltsanfragen an? {#why-are-reports-different}

Inhaltsanfragen weisen Abweichungen von den Analytics-Reporting-Tools eines Unternehmens auf. Weitere Informationen finden Sie unter [Grundlegendes zu Cloud Service-Inhaltsanfragen](/help/implementing/cloud-manager/content-requests.md).

### Wie erfahre ich mehr über mein Inhaltsanfragevolumen? {#current-request-volumes}

Wenn Sie zusätzliche Einblicke in das Inhaltsanfragevolumen erhalten möchten, das im Lizenz-Dashboard angezeigt wird, kann Ihnen Ihr Adobe-Team einen Bericht bereitstellen, der die wichtigsten Treiber von Inhaltsanfragen aufzeigt. Wenden Sie sich an Ihr Adobe-Team oder an den Adobe-Kunden-Support, um einen Bericht über die hauptsächliche Nutzung anzufordern.

### Was passiert, wenn ich mein eigenes CDN verwende? {#using-own-cdn}

Das Lizenz-Dashboard zeigt nur Daten an, die vom Cloud Service-CDN verfolgt werden.  Wenn Sie sich für ein eigenes CDN (BYOCDN) entscheiden, melden Sie das in Ihrem Vertrag festgelegte Inhaltsanfragevolumen einmal jährlich an Adobe.
