---
title: Häufig gestellte Fragen (FAQs) zu Content Hub
description: Hier erhalten Sie Antworten auf einige der am häufigsten gestellten Fragen (FAQs) zum Content-Hub.
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: 74b5c308-c1d3-4787-9f1f-f64cf09d298a
source-git-commit: 59f97fc6ded4274c27400f56b50b4a3329cc471a
workflow-type: tm+mt
source-wordcount: '1635'
ht-degree: 67%

---

# Häufig gestellte Fragen zu Content Hub {#content-hub-frequently-asked-questions}

![Häufig gestellte Fragen zu Content Hub](assets/content-hub-faqs.png)

## Was ist AEM Assets Content Hub? {#what-is-content-hub}

AEM Assets Content Hub ist eine Funktion von Adobe Experience Manager Assets as a Cloud Service.

Mit Content Hub können größere Teams relevante, genehmigte Assets ganz einfach über ein intuitives Portal entdecken und schnell an ihre Anforderungen anpassen.  Darüber hinaus bietet Content Hub einen Aufnahmemechanismus, der es diesen Benutzenden ermöglicht, beim Hochladen von Assets in das DAM einfach den Self-Service zu nutzen. Auf diese Weise können Unternehmen Inhalte schneller erstellen und gleichzeitig die Markenkonsistenz und die Einhaltung entsprechender Schutzmaßnahmen wahren.

<!--

## Why cannot I enable Content Hub on my Cloud Manager program/environment? {#cannot-enable-content-hub}

Content Hub is at this point is only available on AEM Cloud Manager Production programs, which include an Assets license (Assets Cloud Service, Assets Ultimate, Assets Prime). When you click [Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) to enable it, it is deployed and associated with the author production environment of AEM in that program. See [Deploy Content Hub](/help/assets/deploy-content-hub.md) for details and prerequisites.

-->

## Ich habe AEM Assets Content Hub in meinem Produktionsprogramm/meiner Produktionsumgebung aktiviert. Kann ich es deaktivieren? {#can-i-disable-content-hub}

Durch die Aktivierung von AEM Assets Content Hub in einem Produktionsprogramm wird es als Teil der Produktionsinfrastruktur bereitgestellt. AEM Cloud Manager lässt nicht zu, dass Produktionsinfrastrukturen entfernt oder deaktiviert werden, um das Risiko menschlicher Fehler bei der Produktionsnutzung zu minimieren.

Wenn Sie Ihren Benutzenden Content Hub nach der Bereitstellung nicht zur Verfügung stellen möchten, weisen Sie dem Content Hub-Produktprofil in der Admin Console keine Benutzenden zu. Weitere Informationen finden Sie unter [Bereitstellen von Content Hub](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile).

## Wie kann ich AEM Assets Content Hub in meiner Organisation auswerten? {#how-can-i-evaluate-content-hub}

AEM Assets Content Hub ist eine Funktion, die von Adobe bereitgestellt und gepflegt wird. Sie verfügt über keinen benutzerdefinierten Code, der eine typische Validierung über Entwicklung/Staging/Produktion erfordern würde. Darüber hinaus wird der Zugriff auf die Funktion für Benutzende vollständig von den Admins gesteuert, sodass Sie sie auswerten können, ohne dies allen Benutzenden zugänglich zu machen.

Sie können Content Hub auswerten, ohne dass sich dies auf Ihre in AEM as a Cloud Service Assets verwalteten Benutzenden/Produktionsinhalte auswirkt. Ein Auswertungsverfahren könnte wie folgt aussehen:

* [Aktivieren Sie Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) in der Produktionsumgebung (Cloud Manager-Programm)
* [Fügen Sie eine Person als AEM-Admin](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator) vom Produktionsautor- zum Content Hub-Produktprofil hinzu.
* Die bzw. der AEM-Admin [konfiguriert Content Hub](/help/assets/configure-content-hub-ui-options.md)
* Die bzw. der AEM-Admin oder eine AEM-Benutzerin bzw. ein AEM-Benutzer in der AEM-Produktionsautoreninstanz [genehmigt eine Reihe von Assets für Content Hub](/help/assets/approve-assets-content-hub.md). Wenn Sie keine Produktionsinhalte im DAM ändern möchten, sollten Sie einen separaten Auswertungsordner in der AEM-Autoreninstanz erstellen und einige Assets vom DAM in diesen Ordner hochladen/taggen oder kopieren.
* Die bzw. der Admin Console-Admin fügt [einige ausgewählte Benutzende](/help/assets/deploy-content-hub.md#onboard-content-hub-users) zum Content Hub-Produktprofil hinzu, damit sie mit der Auswertung beginnen können.
* Nachdem die Auswertung abgeschlossen ist, können AEM-Benutzende in der Autoreninstanz die Genehmigung für die Test-Assets entfernen und Produktions-Assets für Content Hub genehmigen. Anschließend kann die bzw. der Admin Console-Admin alle Benutzenden hinzufügen, die Zugriff auf Content Hub und genehmigte Inhalte benötigen. Herzlichen Glückwunsch! Ihr Content Hub ist jetzt live.

Es gibt ein Early-Access-Programm für Content Hub in Sandbox-Programmen und ihren Autorenproduktionsumgebungen. Weitere Informationen finden Sie unter [Einführung in Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Wenden Sie sich an Ihr Adobe-Accountteam, um mehr über das Early-Access-Programm zu erfahren.

## Warum sehe ich nach der Anmeldung bei AEM Assets Content Hub keine Assets? {#no-assets-in-content-hub}

Die Assets, die in Assets as a Cloud Service als genehmigt markiert sind, sind automatisch in Content Hub verfügbar. Wenn Sie nach dem Anmelden bei Content Hub keine Assets sehen können, genehmigen Sie Assets mithilfe der AEM as a Cloud Service-Autorenumgebung, um sie in Content Hub verfügbar zu machen. Weitere Informationen finden Sie unter [Genehmigen von Assets für Content Hub](/help/assets/approve-assets-content-hub.md).

## Warum sehe ich meine Assets nicht, die ich entweder direkt mit AEM Assets Content Hub hochlade oder sie mit Content Hub aus Dropbox- oder OneDrive-Konten importiere? {#no-assets-uploaded-from-content-hub}

Welche Assets mit AEM Assets Content Hub hochgeladen werden, hängt davon ab, ob Sie den Umschalter [Automatische Genehmigung](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) in der Benutzeroberfläche „Konfiguration“ aktiviert haben:

* Wenn der Umschalter **Automatische Genehmigung** aktiviert ist, sind die Assets, die Sie mit Content Hub hochladen, automatisch verfügbar.

* Wenn der Umschalter **Automatische Genehmigung** deaktiviert ist, werden die Assets, die Sie mit Content Hub hochladen, nicht automatisch angezeigt. Die Assets sind im Ordner `hydrated-assets` Ihrer Assets as a Cloud Service-Umgebung verfügbar. Navigieren Sie zu dem Ordner und ändern Sie die Status dieser Assets [gemeinsam](/help/assets/approve-assets-content-hub.md) in `Approved`, damit diese Assets in Content Hub angezeigt werden.

## Wie kann ich mit AEM Assets Content Hub in der AEM as a Cloud Service-Umgebung hochgeladene Assets schnell finden? {#find-uploaded-assets-on-aem-cloud}

Sie können mit AEM Assets Content Hub in der AEM as a Cloud Service-Umgebung hochgeladene Assets schnell finden, indem Sie:

1. Navigieren Sie zum Ordner `hydrated-assets`.

1. Klicken Sie auf **[!UICONTROL Filter]** und legen Sie im Feld **[!UICONTROL Asset-Status]** den Wert **[!UICONTROL Kein Status]** fest.

1. Sortieren Sie Assets mit dem Feld **[!UICONTROL Änderungsdatum]**.

## Warum sehe ich die Option Mit Adobe Express bearbeiten auf meiner Asset-Karte nicht, um Assets neu mischen zu können, um mit AEM Assets Content Hub neue Varianten zu erstellen? {#edit-using-express-not-available}

Um die Option **Bearbeiten mit Adobe Express** auf der Asset-Karte in AEM Assets Content Hub anzuzeigen, muss der Benutzer über eine Berechtigung für Adobe Express Enterprise oder Teams verfügen (siehe [Pläne](https://www.adobe.com/de/express/pricing)) sowie über Berechtigungen für [Content Hub-Benutzer mit Berechtigungen zum Remixen von Assets in neue Varianten](#onboard-content-hub-users-add-assets).

Es gibt einige Konfigurationen dazu, wie Benutzende [!DNL Content Hub] und [!DNL Adobe Express] zugewiesen werden:

1. Die Organisation verfügt über eine [Assets Ultimate](/help/assets/assets-ultimate-overview.md)- oder [Assets Prime](/help/assets/assets-prime.md)-Lizenz, und Benutzende werden einem der Experience Manager-Profile in Admin Console zugewiesen, die die Adobe Express-Berechtigung enthalten (mitwirkende Person oder Power-User). Die Integration funktioniert ohne zusätzliche Konfiguration.

1. [!DNL Adobe Express] wird in derselben [!DNL Adobe Admin Console] bereitgestellt wie [!DNL Experience Manager Assets] mit [!DNL Content Hub]. Die Integration funktioniert ohne zusätzliche Konfiguration.

1. [!DNL Adobe Express] wird in einer anderen [!DNL Adobe Admin Console] bereitgestellt als [!DNL Experience Manager Assets] mit [!DNL Content Hub]. In diesem Fall kann die bzw. der [!DNL Assets]-Admin die Integration so konfigurieren (siehe [Dokumentation](/help/assets/connect-assets-with-creative-cloud.md)), dass die Integration funktioniert.

   >[!NOTE]
   >
   >Die Person, die Express- und Assets-Produktprofilen in zwei Admin Consoles zugewiesen ist, muss über dieselbe E-Mail-Adresse verfügen und ein Unternehmenskonto vom Typ **Unternehmen oder Schule** statt des **persönlichen** Kontos verwenden. In der idealen Konfiguration sind beide Admin Consoles als **Federated ID** mit einer vertrauenswürdigen Beziehung zwischen ihnen eingerichtet, damit Benutzende von einem nahtlosen Single Sign-on-Erlebnis profitieren. Einige der Express-Abos (z. B. Express Teams) unterstützen Federated ID/Single Sign-on nicht.

Zusätzlich zu den richtigen Produktberechtigungen erfordert die Adobe Express-Integration in Content Hub, dass zugewiesene Benutzende mindestens über Berechtigungen vom Typ [!UICONTROL Bearbeiten] für die Assets-Autorenumgebung verfügen, die Content Hub unterstützt, und zwar mindestens für die Ordnerhierarchie **[#UICONTROL /content/dam/hydrated-assets/]**, in der Content Hub-Benutzende mit Express erstellte Inhalte speichern können. Siehe [Berechtigungsverwaltung](/help/security/touch-ui-principal-view.md) in der Admin-Ansicht (Touch-Benutzeroberfläche) oder eine vereinfachte [Berechtigungsverwaltung in der Assets-Ansicht](https://experienceleague.adobe.com/de/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

## Kann ich AEM Assets Content Hub so einrichten, dass die Markenrichtlinien meines Unternehmens als Link auf der Startseite angezeigt werden? {#content-hub-setup-brand-guidelines}

Zusätzlich zu den standardmäßigen Registerkarten „Alle Assets&quot;, „Sammlungen“ und „Einblicke“ auf der AEM Assets Content Hub-Startseite können Sie benutzerdefinierte Links als separate Registerkarten hinzufügen. Informationen zum Einrichten finden Sie unter [Benutzerspezifische Links](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub).

## Gibt es Pläne für die Migration von Bestandskunden von Brand Portal zu AEM Assets Content Hub? {#migration-brand-portal}

Adobe bietet Migrationsunterstützung von Brand Portal zu AEM Assets Content Hub, die Sie durch die Erstellung eines Adobe-Support-Tickets verwenden können.

## Warum wird die Option Produkteinstellungen/-konfiguration in AEM Assets Content Hub nicht angezeigt? {#ui-configuration-option-missing}

Um auf die [Konfigurations-Benutzeroberfläche](/help/assets/configure-content-hub-ui-options.md) in AEM Assets Content Hub zugreifen zu können, müssen Sie [Content Hub-Administrator sein](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator). Wenn Sie dem Produktprofil für AEM-Admins in der Produktions-Autoreninstanz in der Adobe Admin Console zugewiesen sind und die Konfigurationsoption trotzdem nicht angezeigt wird, stellen Sie sicher, dass das Produktprofil für AEM-Admins nicht umbenannt wurde. Weitere Informationen finden Sie unter [AEM as a Cloud Service – Team- und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md).

## Wie geht AEM Assets Content Hub mit den Einschränkungen von Brand Portal um? {#content-hub-brand-portal-comparison}


In der folgenden Tabelle sind die wichtigsten Unterschiede zwischen AEM Assets Content Hub und Brand Portal aufgeführt:

| Bereich | Funktion | Content Hub | Brand Portal |
|---|---|----|----|
| Konfigurieren des Verteilungserlebnisses | Konfigurieren von Metadaten für Filter, Asset-Details und die Seite zum Hinzufügen von Assets | ✓ | − |
|  | Konfigurieren externer Links über das Portal | ✓ | − |
|  | Konfigurieren von Bannernachrichten | ✓ | ✓ |
|  | Konfigurieren des Bannerbilds für Branding | ✓ | ✓ |
|  | Konfigurieren von primären und sekundären Farben für die Benutzeroberfläche gemäß den Branding-Anforderungen | ✓ | − |
| Freigeben von Assets aus dem DAM | Freigeben von ursprünglich genehmigten Assets aus dem DAM | ✓ | ✓ |
|  | Genehmigte Asset-Änderungen automatisch synchronisiert | ✓ | − |
| Suche und Filter | Dynamische Filter (Optionen werden basierend auf angezeigten Assets dynamisch angezeigt) | ✓ | − |
|  | Suchverlauf | ✓ | − |
| Asset-Upload | Lokales Laufwerk | ✓ | ✓ |
|  | Hinzufügen konfigurierbarer Metadaten beim Hochladen von Assets | ✓ | − |
| Download und Ausgabedarstellungen | Herunterladen des Original-Assets | ✓ | ✓ |
|  | Freigeben und Herunterladen statischer Ausgabedarstellungen aus dem DAM | ✓ | ✓ |
|  | Herunterladen dynamischer Ausgabedarstellungen (Voreinstellung und intelligenter Zuschnitt) | ✓ | ✓ |
|  | Möglichkeit, die Anzeige und das Herunterladen abgelaufener Assets einzuschränken | ✓ | − |
| Link-Freigabe und Sammlungen | Link-Freigabe für angemeldete Personen | ✓ | ✓ |
|  | Öffentliche Sammlungen | ✓ | ✓ |
|  | Suchen in Sammlungen | ✓ | − |
|  | Anonyme Link-Freigabe | ✓ | ✓ |
|  | Private Sammlungen | ✓ | ✓ |
| Berechtigungen | ACL-basierte Berechtigungen | − | ✓ |
|  | Attributbasierte Zugriffssteuerung – Übersicht | ✓ | − |
| Express-Integration | Bearbeiten von Content Hub-Assets in Adobe Express und Speichern im DAM | ✓ | − |
| Dashboards und Berichte | Erkenntnis-Dashboard | ✓ | − |
| Erweiterbarkeit der Benutzeroberfläche | Benutzerdefinierte Erweiterungspunkte auf der Seite „Asset-Details“ | Eingeschränkte Verfügbarkeit | − |
| Demnächst verfügbare Innovationen | Lieblingssammlungen nach Personen | ✓ | − |
|  | Angeheftete Sammlungen nach Admin | ✓ | − |
|  | Semantische Suche | ✓ | − |
|  | Lokalisierte Suche und Anzeige von Metadaten | ✓ | − |

## Wie kann ich ein Repository auswählen, um Assets nur für die ausgewählte Umgebung in AEM Assets Content Hub anzuzeigen? {#select-repository-multiple-environments}

Wenn Sie AEM Assets Content Hub für Produktionsumgebungen und andere untere Umgebungen für dasselbe Programm konfiguriert haben, können Sie das Repository auswählen und die Assets für die ausgewählte Umgebung anzeigen. Führen Sie die folgenden Schritte aus:

1. Klicken Sie auf das Benutzersymbol im rechten Bereich.

1. Wählen Sie im Abschnitt **[!UICONTROL Produkteinstellungen]** die Option **[!UICONTROL Repository auswählen]** aus.

1. Wählen Sie aus dem Dropdown-Menü **[!UICONTROL Repository]** das Repository aus und klicken Sie zur Bestätigung auf **[!UICONTROL OK]**.

   Content Hub zeigt jetzt Assets für die ausgewählte Umgebung an.

## Wie kann AEM Assets Content Hub die Miniaturvorschau für den Dateityp .ZIP anzeigen? {#thumbnail-preview-zip-file}

Um eine Miniaturansicht für Dateitypen wie ZIP-Dateien in AEM Assets Content Hub bereitzustellen, können Sie eine Ausgabedarstellung mit dem Namen `cq5dam.preview.jpg` oder `cq5dam.preview.png` zum Stamm des Pfads hinzufügen, unter dem die ZIP-Datei in der Authoring-Umgebung von AEM as a Cloud Service verfügbar ist.

Das Bild, das Sie als Ausgabedarstellung hinzufügen:

* Kann im JPG-, JPEG- oder PNG-Format vorliegen.

* Darf maximal 50 MB groß sein

Sofern verfügbar, zeigt Content Hub das Bild als Vorschauminiatur für die ZIP-Datei in Content Hub an.


