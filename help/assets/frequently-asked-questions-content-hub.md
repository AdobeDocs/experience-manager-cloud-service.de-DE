---
title: Häufig gestellte Fragen (FAQs) zu Content Hub
description: Hier erhalten Sie Antworten auf einige der am häufigsten gestellten Fragen (FAQs) zum Content-Hub.
exl-id: 74b5c308-c1d3-4787-9f1f-f64cf09d298a
source-git-commit: 95c643151e4828fa2eae0725dc1081aeeabc42fb
workflow-type: ht
source-wordcount: '1367'
ht-degree: 100%

---

# Häufig gestellte Fragen zu Content Hub {#content-hub-frequently-asked-questions}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

![Häufig gestellte Fragen zu Content Hub](assets/content-hub-faqs.png)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub-Handbuch als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

## Was ist Content Hub? {#what-is-content-hub}

Content Hub ist eine Funktion von Adobe Experience Manager Assets as a Cloud Service.

Mit Content Hub können größere Teams relevante, genehmigte Assets ganz einfach über ein intuitives Portal entdecken und schnell an ihre Anforderungen anpassen.  Darüber hinaus bietet Content Hub einen Aufnahmemechanismus, der es diesen Benutzenden ermöglicht, beim Hochladen von Assets in das DAM einfach den Self-Service zu nutzen. Auf diese Weise können Unternehmen Inhalte schneller erstellen und gleichzeitig die Markenkonsistenz und die Einhaltung entsprechender Schutzmaßnahmen wahren.

## Warum kann ich Content Hub nicht in meinem Cloud Manager-Programm bzw. meiner Cloud Manager-Umgebung aktivieren? {#cannot-enable-content-hub}

Content Hub ist derzeit nur für AEM Cloud Manager-Produktionsprogramme verfügbar, die eine Assets-Lizenz enthalten (Assets Cloud Service, Assets Ultimate, Assets Prime). Wenn Sie auf [Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) klicken, um es zu aktivieren, wird es bereitgestellt und der Autorenproduktionsumgebung von AEM in diesem Programm zugeordnet. Weitere Informationen und Voraussetzungen finden Sie unter [Bereitstellen von Content Hub](/help/assets/deploy-content-hub.md).

## Ich habe Content Hub in meinem Produktionsprogramm oder meiner Produktionsumgebung aktiviert. Kann ich es deaktivieren? {#can-i-disable-content-hub}

Durch das Aktivieren von Content Hub in einem Produktionsprogramm wird es als Teil der Produktionsinfrastruktur bereitgestellt. AEM Cloud Manager lässt nicht zu, dass Produktionsinfrastrukturen entfernt oder deaktiviert werden, um das Risiko menschlicher Fehler bei der Produktionsnutzung zu minimieren.

Wenn Sie Ihren Benutzenden Content Hub nach der Bereitstellung nicht zur Verfügung stellen möchten, weisen Sie dem Content Hub-Produktprofil in der Admin Console keine Benutzenden zu. Weitere Informationen finden Sie unter [Bereitstellen von Content Hub](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile).

## Wie kann ich Content Hub in meinem Unternehmen auswerten angesichts der Tatsache, dass es nur für Produktionsprogramme/Produktions-Authoring-Umgebungen verfügbar ist? {#how-can-i-evaluate-content-hub}

Content Hub ist eine von Adobe bereitgestellte und verwaltete Funktion und verfügt über keinen benutzerdefinierten Code, der eine typische Validierung über Entwicklung/Staging/Produktion erfordern würde. Darüber hinaus wird der Zugriff auf die Funktion für Benutzende vollständig von den Admins gesteuert, sodass Sie sie auswerten können, ohne dies allen Benutzenden zugänglich zu machen.

Sie können Content Hub auswerten, ohne dass sich dies auf Ihre in AEM as a Cloud Service Assets verwalteten Benutzenden/Produktionsinhalte auswirkt. Ein Auswertungsverfahren könnte wie folgt aussehen:

* [Aktivieren Sie Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) in der Produktionsumgebung (Cloud Manager-Programm)
* [Fügen Sie eine Person als AEM-Admin](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator) vom Produktionsautor- zum Content Hub-Produktprofil hinzu.
* Die bzw. der AEM-Admin [konfiguriert Content Hub](/help/assets/configure-content-hub-ui-options.md)
* Die bzw. der AEM-Admin oder eine AEM-Benutzerin bzw. ein AEM-Benutzer in der AEM-Produktionsautoreninstanz [genehmigt eine Reihe von Assets für Content Hub](/help/assets/approve-assets-content-hub.md). Wenn Sie keine Produktionsinhalte im DAM ändern möchten, sollten Sie einen separaten Auswertungsordner in der AEM-Autoreninstanz erstellen und einige Assets vom DAM in diesen Ordner hochladen/taggen oder kopieren.
* Die bzw. der Admin Console-Admin fügt [einige ausgewählte Benutzende](/help/assets/deploy-content-hub.md#onboard-content-hub-users) zum Content Hub-Produktprofil hinzu, damit sie mit der Auswertung beginnen können.
* Nachdem die Auswertung abgeschlossen ist, können AEM-Benutzende in der Autoreninstanz die Genehmigung für die Test-Assets entfernen und Produktions-Assets für Content Hub genehmigen. Anschließend kann die bzw. der Admin Console-Admin alle Benutzenden hinzufügen, die Zugriff auf Content Hub und genehmigte Inhalte benötigen. Herzlichen Glückwunsch! Ihr Content Hub ist jetzt live.

Es gibt ein Early-Access-Programm für Content Hub in Sandbox-Programmen und ihren Autorenproduktionsumgebungen. Weitere Informationen finden Sie unter [Einführung in Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Wenden Sie sich an Ihr Adobe-Accountteam, um mehr über das Early-Access-Programm zu erfahren.

Content Hub ist noch nicht für Nicht-Produktionsumgebungen (Staging und Entwicklung) verfügbar. Die erwartete Verfügbarkeit für Staging-/Entwicklungsumgebungen für Assets Ultimate ist März 2025.

## Warum werden nach dem Anmelden bei Content Hub keine Assets angezeigt? {#no-assets-in-content-hub}

Die Assets, die in Assets as a Cloud Service als genehmigt markiert sind, sind automatisch in Content Hub verfügbar. Wenn Sie nach dem Anmelden bei Content Hub keine Assets sehen können, genehmigen Sie Assets mithilfe der AEM as a Cloud Service-Autorenumgebung, um sie in Content Hub verfügbar zu machen. Weitere Informationen finden Sie unter [Genehmigen von Assets für Content Hub](/help/assets/approve-assets-content-hub.md).

## Warum werden mir keine Assets angezeigt, die ich entweder direkt mit Content Hub hochlade oder aus Dropbox- oder OneDrive-Konten mit Content Hub importiere? {#no-assets-uploaded-from-content-hub}

Das Anzeigen von Assets, die mit Content Hub hochgeladen wurden, hängt davon ab, ob Sie den Umschalter [Automatische Genehmigung](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) auf der Benutzeroberfläche „Konfiguration“ aktiviert haben:

* Wenn der Umschalter **Automatische Genehmigung** aktiviert ist, sind die Assets, die Sie mit Content Hub hochladen, automatisch verfügbar.

* Wenn der Umschalter **Automatische Genehmigung** deaktiviert ist, werden die Assets, die Sie mit Content Hub hochladen, nicht automatisch angezeigt. Die Assets sind im Ordner `hydrated-assets` Ihrer Assets as a Cloud Service-Umgebung verfügbar. Navigieren Sie zu dem Ordner und ändern Sie die Status dieser Assets [gemeinsam](/help/assets/approve-assets-content-hub.md) zu `Approved`, damit diese Assets in Content Hub angezeigt werden.

## Wie kann ich schnell nach Assets suchen, die mit Content Hub in der AEM as a Cloud Service-Umgebung hochgeladen wurden? {#find-uploaded-assets-on-aem-cloud}

So können Sie schnell nach Assets suchen, die mit Content Hub in der AEM as a Cloud Service-Umgebung hochgeladen wurden:

1. Navigieren Sie zum Ordner `hydrated-assets`.

1. Klicken Sie auf **[!UICONTROL Filter]** und legen Sie im Feld **[!UICONTROL Asset-Status]** den Wert **[!UICONTROL Kein Status]** fest.

1. Sortieren Sie Assets mit dem Feld **[!UICONTROL Änderungsdatum]**.

## Warum wird auf meiner Asset-Karte nicht die Option zum Bearbeiten mit Adobe Express angezeigt, damit ich Assets zum Erstellen neuer Varianten remixen kann? {#edit-using-express-not-available}

Um die Option zum **Bearbeiten mit Adobe Express** auf der Asset-Karte anzuzeigen, müssen Benutzende zusätzlich zu den Berechtigungen für [Content Hub-Benutzende mit Berechtigungen zum Remixen von Assets in neue Varianten](#onboard-content-hub-users-add-assets) über Adobe Express Enterprise- oder Teams-Berechtigungen verfügen (siehe [Abos](https://www.adobe.com/de/express/pricing)). 

Es gibt einige Konfigurationen dazu, wie Benutzende [!DNL Content Hub] und [!DNL Adobe Express] zugewiesen werden:

1. Die Organisation verfügt über eine [Assets Ultimate](/help/assets/assets-ultimate-overview.md)- oder [Assets Prime](/help/assets/assets-prime.md)-Lizenz, und Benutzende werden einem der Experience Manager-Profile in Admin Console zugewiesen, die die Adobe Express-Berechtigung enthalten (mitwirkende Person oder Power-User). Die Integration funktioniert ohne zusätzliche Konfiguration.

1. [!DNL Adobe Express] wird in derselben [!DNL Adobe Admin Console] bereitgestellt wie [!DNL Experience Manager Assets] mit [!DNL Content Hub]. Die Integration funktioniert ohne zusätzliche Konfiguration.

1. [!DNL Adobe Express] wird in einer anderen [!DNL Adobe Admin Console] bereitgestellt als [!DNL Experience Manager Assets] mit [!DNL Content Hub]. In diesem Fall kann die bzw. der [!DNL Assets]-Admin die Integration so konfigurieren (siehe [Dokumentation](/help/assets/connect-assets-with-creative-cloud.md)), dass die Integration funktioniert.

   >[!NOTE]
   >
   >Die Person, die Express- und Assets-Produktprofilen in zwei Admin Consoles zugewiesen ist, muss über dieselbe E-Mail-Adresse verfügen und ein Unternehmenskonto vom Typ **Unternehmen oder Schule** statt des **persönlichen** Kontos verwenden. In der idealen Konfiguration sind beide Admin Consoles als **Federated ID** mit einer vertrauenswürdigen Beziehung zwischen ihnen eingerichtet, damit Benutzende von einem nahtlosen Single Sign-on-Erlebnis profitieren. Einige der Express-Abos (z. B. Express Teams) unterstützen Federated ID/Single Sign-on nicht.

Zusätzlich zu den richtigen Produktberechtigungen erfordert die Adobe Express-Integration in Content Hub, dass zugewiesene Benutzende mindestens über Berechtigungen vom Typ [!UICONTROL Bearbeiten] für die Assets-Autorenumgebung verfügen, die Content Hub unterstützt, und zwar mindestens für die Ordnerhierarchie **[#UICONTROL /content/dam/hydrated-assets/]**, in der Content Hub-Benutzende mit Express erstellte Inhalte speichern können. Siehe [Berechtigungsverwaltung](/help/security/touch-ui-principal-view.md) in der Admin-Ansicht (Touch-Benutzeroberfläche) oder eine vereinfachte [Berechtigungsverwaltung in der Assets-Ansicht](https://experienceleague.adobe.com/de/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

## Kann ich Content Hub so einrichten, dass die Markenrichtlinien meiner Organisation als Link auf der Startseite angezeigt werden? {#content-hub-setup-brand-guidelines}

Sie können zusätzlich zu den Standardregisterkarten „Alle Assets“, „Sammlungen“ und „Erkenntnisse“ benutzerspezifische Links als separate Registerkarten auf der Startseite von Content Hub hinzufügen. Informationen zum Einrichten finden Sie unter [Benutzerspezifische Links](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub).

## Gibt es Pläne, bestehende Brand Portal-Kundschaft nach Content Hub zu migrieren? {#migration-brand-portal}

Adobe bietet Unterstützung bei der Migration von Brand Portal nach Content Hub. Öffnen Sie hierzu ein Adobe-Support-Ticket.

## Warum kann ich die Option „Produkteinstellungen/Konfiguration“ in Content Hub nicht sehen? {#ui-configuration-option-missing}

Um auf die [Konfigurationsoberfläche](/help/assets/configure-content-hub-ui-options.md) zugreifen zu können, müssen Sie [Content Hub-Admin](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator) sein. Wenn Sie dem Produktprofil für AEM-Admins in der Produktions-Autoreninstanz in der Adobe Admin Console zugewiesen sind und die Konfigurationsoption trotzdem nicht angezeigt wird, stellen Sie sicher, dass das Produktprofil für AEM-Admins nicht umbenannt wurde. Weitere Informationen finden Sie unter [AEM as a Cloud Service – Team- und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md).
