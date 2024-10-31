---
title: Häufig gestellte Fragen zu Content Hub (FAQs)
description: Hier erhalten Sie Antworten auf einige der am häufigsten gestellten Fragen (FAQs) zu Content Hub.
source-git-commit: 3b8a80e346fe63450f9b57733c67de2e4b52b2b8
workflow-type: tm+mt
source-wordcount: '1100'
ht-degree: 1%

---

# Häufig gestellte Fragen zu Content Hub {#content-hub-frequently-asked-questions}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Häufig gestellte Frage zu Content Hub](assets/content-hub-faqs.png)

## Was ist Content Hub? {#what-is-content-hub}

Content Hub ist eine Funktion von Adobe Experience Manager Assets as a Cloud Service.

Content Hub ermöglicht es breiteren Teams, relevante, genehmigte Assets über ein intuitives Portal leicht zu entdecken und schnell an ihre Anforderungen anzupassen.  Darüber hinaus bietet Content Hub einen Erfassungsmechanismus, der es diesen Benutzern ermöglicht, sich beim Hochladen von Assets in das DAM einfach selbst zu bedienen. Dies ermöglicht es Unternehmen, Inhalte schneller zu erstellen und gleichzeitig die Markenkonsistenz und die Einhaltung entsprechender Schutzmaßnahmen zu wahren.

## Warum kann ich Content Hub nicht in meinem Cloud Manager-Programm/meiner -Umgebung aktivieren? {#cannot-enable-content-hub}

Content Hub ist derzeit nur für AEM Cloud Manager-Produktionsprogramme verfügbar, die eine Assets-Lizenz enthalten. Wenn Sie auf [Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) klicken, um es zu aktivieren, wird es bereitgestellt und der Autorenproduktionsumgebung von AEM in diesem Programm zugeordnet. Weitere Informationen und Voraussetzungen finden Sie unter [Content Hub bereitstellen](/help/assets/deploy-content-hub.md) .

Es gibt ein frühzeitiges Zugriffsprogramm für Content Hub in Sandbox-Programmen/Autorenproduktionsumgebungen. Weitere Informationen finden Sie unter [Einführung in Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Wenden Sie sich an Ihr Adobe-Account-Team, um mehr über das Frühzugsprogramm zu erfahren.

Content Hub ist derzeit nicht für Nicht-Produktionsumgebungen (Staging, Entwicklung usw.) verfügbar.

## Ich habe Content Hub in meinem Produktionsprogramm/in meiner Produktionsumgebung aktiviert. Kann ich es deaktivieren? {#can-i-disable-content-hub}

Durch die Aktivierung von Content Hub in einem Produktionsprogramm wird als Teil der Produktionsinfrastruktur bereitgestellt. AEM Cloud Manager ermöglicht nicht das Entfernen oder Deaktivieren von Produktionsinfrastrukturen, um das Risiko der Produktionsnutzung durch menschliche Fehler zu minimieren.

Wenn Sie Ihren Benutzern nach der Bereitstellung keine Content Hub bereitstellen möchten, weisen Sie in Admin Console keine Benutzer dem Content Hub-Produktprofil zu. Weitere Informationen finden Sie unter [Content Hub bereitstellen](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile) .

## Wie kann ich Content Hub in meinem Unternehmen auswerten, da es nur für Produktionsprogramme/Produktionsumgebungen verfügbar ist? {#how-can-i-evaluate-content-hub}

Content Hub ist eine Funktion, die Adobe bereitstellt und verwaltet, und verfügt über keinen benutzerdefinierten Code, der eine typische Validierung über dev/stage/production erfordert. Darüber hinaus wird der Zugriff auf die Funktion für Benutzer vollständig vom Administrator gesteuert, sodass Sie sie auswerten können, ohne sie allen Benutzern zugänglich zu machen.

Sie können Content Hub auswerten, ohne dass sich dies auf Ihre in AEM as a Cloud Service Assets verwalteten Benutzer/Produktionsinhalte auswirkt. Ein Bewertungsverfahren könnte wie folgt aussehen:

* [Content Hub aktivieren](/help/assets/deploy-content-hub.md#enable-content-hub) in der Produktionsumgebung (Cloud Manager-Programm)
* [Fügen Sie einen AEM Administrator Benutzer](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator) vom Produktionsautor zum Content Hub-Produktprofil hinzu.
* AEM Administrator [konfiguriert Content Hub](/help/assets/configure-content-hub-ui-options.md)
* AEM Administrator oder ein AEM Benutzer in AEM Produktionsautor [genehmigt eine Reihe von Assets für Content Hub](/help/assets/approve-assets-content-hub.md). Wenn Sie keine Produktionsinhalte in DAM ändern möchten, sollten Sie möglicherweise einen separaten Bewertungsordner in der AEM Autoreninstanz erstellen und einige Assets von DAM hochladen/taggen oder darin kopieren.
* Der Admin Console-Administrator fügt [einige ausgewählte Benutzer](/help/assets/deploy-content-hub.md#onboard-content-hub-users) zum Content Hub-Produktprofil hinzu, damit sie mit der Auswertung beginnen können.
* Nachdem die Auswertung abgeschlossen ist, können AEM Benutzer in der Autoreninstanz die Genehmigung aus den Testassets entfernen, Produktions-Assets für Content Hub genehmigen und dann der Admin Console-Administrator alle Benutzer hinzufügen, die Zugriff auf Content Hub und genehmigte  benötigen. Herzlichen Glückwunsch! Ihr Content Hub ist jetzt live.

Adobe bietet auch ein frühzeitiges Zugriffsprogramm für Content Hub in Staging-Umgebungen. Weitere Informationen finden Sie unter der Frage [Warum kann ich Content Hub nicht in meinem Cloud Manager-Programm/meiner-Umgebung aktivieren?](#cannot-enable-content-hub) für Details.

## Warum werden nach dem Anmelden bei Content Hub keine Assets angezeigt? {#no-assets-in-content-hub}

Die Assets, die in Assets as a Cloud Service als genehmigt markiert wurden, sind automatisch in Content Hub verfügbar. Wenn Sie nach dem Anmelden bei Content Hub keine Assets sehen können, genehmigen Sie Assets mithilfe der AEM as a Cloud Service-Autorenumgebung, um sie in Content Hub verfügbar zu machen. Weitere Informationen finden Sie unter [Genehmigen von Assets für Content Hub](/help/assets/approve-assets-content-hub.md).

## Warum sehe ich meine Assets nicht, die ich entweder direkt mit Content Hub hochladen oder aus Dropbox- oder OneDrive-Konten mit Content Hub importiere? {#no-assets-uploaded-from-content-hub}

Die Anzeige von Assets, die mit Content Hub hochgeladen wurden, hängt davon ab, ob Sie den Umschalter [Automatische Genehmigung](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) auf der Konfigurationsoberfläche aktiviert haben:

* Wenn der Umschalter **Automatische Genehmigung** aktiviert ist, sind die Assets, die Sie mit Content Hub hochladen, automatisch verfügbar.

* Wenn der Umschalter **Automatische Genehmigung** deaktiviert ist, werden die Assets, die Sie mit Content Hub hochladen, nicht automatisch angezeigt. Die Assets sind im Ordner &quot;`hydrated-assets`&quot;Ihrer Assets as a Cloud Service-Umgebung verfügbar. Navigieren Sie zum Ordner und bearbeiten Sie [stapelweise](/help/assets/approve-assets-content-hub.md) den Status dieser Assets in `Approved` , damit diese Assets in Content Hub angezeigt werden.

## Wie schnell finden Sie Assets, die mit Content Hub in der AEM as a Cloud Service-Umgebung hochgeladen wurden? {#find-uploaded-assets-on-aem-cloud}

Sie können mithilfe von Content Hub in der AEM as a Cloud Service-Umgebung schnell nach Assets suchen, indem Sie:

1. Navigieren Sie zum Ordner &quot;`hydrated-assets`&quot;.

1. Klicken Sie auf **[!UICONTROL Filter]** und legen Sie im Feld **[!UICONTROL Asset-Status]** den Wert **[!UICONTROL Kein Status]** fest.

1. Sortieren von Assets mithilfe des Felds **[!UICONTROL Änderungsdatum]**

## Warum sehe ich die Option &quot;Bearbeiten mit Adobe Expreß&quot;auf meiner Asset-Karte nicht an, um Assets neu mischen zu können, um neue Varianten zu erstellen? {#edit-using-express-not-available}

Um die Option &quot;Bearbeiten mit Adobe Expreß&quot;auf der Asset-Karte anzuzeigen, müssen Sie zusätzlich zu den Berechtigungen für [Content Hub-Benutzer mit Berechtigungen zum Remix von Assets in neue Varianten](#onboard-content-hub-users-add-assets) über Adobe Expreß-Berechtigungen verfügen. Adobe Express muss in derselben Organisation in der Adobe-Admin Console bereitgestellt werden, in der Adobe Experience Manager bereitgestellt wird.

## Kann ich Content Hub so einrichten, dass die Markenrichtlinien meines Unternehmens als Link auf der Startseite angezeigt werden? {#content-hub-setup-brand-guidelines}

Sie können benutzerdefinierte Links als separate Registerkarten hinzufügen, die über die standardmäßigen Registerkarten &quot;Alle Assets&quot;, &quot;Sammlungen&quot;und &quot;Einblicke&quot;auf der Startseite von Content Hub hinausgehen. Informationen zum Einrichten finden Sie unter [Benutzerspezifische Links](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub).

## Gibt es Pläne für die Migration bestehender Brand Portal-Kunden nach Content Hub? {#migration-brand-portal}

Adobe bietet Migrationsunterstützung von Brand Portal nach Content Hub, die Sie durch Erstellen eines Adobe-Support-Tickets verwenden können.

## Warum kann ich die Option &quot;Produkteinstellungen/Konfiguration&quot;in Content Hub nicht sehen? {#ui-configuration-option-missing}

Um auf die [Konfigurations-Benutzeroberfläche](/help/assets/configure-content-hub-ui-options.md) zugreifen zu können, müssen Sie ein [Content Hub-Administrator](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator) sein. Wenn Sie dem Produktprofil AEM Administratoren in der Produktionsautorinstanz in Adobe Admin Console zugewiesen sind und die Konfigurationsoption weiterhin nicht angezeigt wird, stellen Sie sicher, dass das Produktprofil AEM Administratoren nicht umbenannt wird. Weitere Informationen finden Sie unter [AEM as a Cloud Service-Team und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md) .


