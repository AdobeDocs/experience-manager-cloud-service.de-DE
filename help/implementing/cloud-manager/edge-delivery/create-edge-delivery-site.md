---
title: Erstellen einer Edge Delivery-Site in Cloud Manager
description: Erfahren Sie, wie Sie mit einem Klick in Cloud Manager schnell eine Edge Delivery-Site erstellen können.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0e30cf827e764a356dde304df3124d0be3d2e58b
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 24%

---


# Über das Erstellen einer Edge Delivery-Site in Cloud Manager {#about-one-click-edge-delivery-site}

Die Funktion zum Erstellen einer Edge Delivery-Site unterstützt Sie bei der Automatisierung des Onboarding und der Bereitstellung von Edge Delivery-Sites in Cloud Manager. Dies vereinfacht den Prozess erheblich, da Sie nur auf eine einzige Schaltfläche klicken müssen. Mit diesem einen Klick erreichen Sie, dass die erforderliche Infrastruktur bereitgestellt, eine Integration mit GitHub zur Versionskontrolle durchgeführt und Ihr Dokument- und Asset-Speicher in Google Drive konfiguriert wird.

Diese Automatisierung trägt dazu bei, den manuellen Aufwand bei der Einrichtung Ihrer ersten Site zu reduzieren. Auf diese Weise werden nicht nur nahtlose Workflows sowie Skalierbarkeit sichergestellt, sondern auch die Leistung Ihrer Teams bei der Verwaltung von Inhalten am Edge verbessert.

## Wichtige Konzepte {#key-concepts}

Die wichtigsten Konzepte bei der Erstellung einer Edge Delivery-Site in Cloud Manager mit einem Klick.

| Schlüsselkonzept | Beschreibung |
| --- | --- |
| Automatisierte Edge-Bereitstellung | <ul><li>Benutzer können Edge Delivery-Sites sofort erstellen und konfigurieren.</li><li>Durch die Integration von Cloud Manager mit CI/CD-Workflows werden manuelle Onboarding-Prozesse reduziert oder überflüssig.</li><li>Integration mit Cloud Manager für nahtlose CI/CD-Workflows.</li></ul> |
| Integration mit Cloud Manager | <ul><li>Verwendet die Cloud Manager-Benutzeroberfläche, um den Edge Delivery-Prozess mit einem Klick auszulösen.</li><li>Ermöglichen des Zugriffs auf die automatisierte Repository-Erstellung und -Bereitstellung.</li></ul> |
| GitHub-basierte Versionskontrolle | <ul><li>Erstellt ein GitHub-Repository innerhalb einer Organisation mithilfe vordefinierter Bausteinvorlagen, um Bereitstellungen zu standardisieren.</li><li>Verbindet sich mit dem AEM-Bot für Inhaltsaktualisierungen.</li></ul> |
| Integration von Dokument- und Asset-Speicher | <ul><li>Erzeugt einen Google Drive-Ordner zum Speichern.<li>Installiert die AEM-Code-Synchronisierungsanwendung im Repository und sorgt so für eine nahtlose Synchronisierung und Bereitstellung.</li></li><li>Mitwirkende können Dokumente einfach verwalten.</li></ul> |
| Sicherheit und Skalierbarkeit | <ul><li>Stellt die Einhaltung der Sicherheitsstandards eines Unternehmens sicher.</li><li>Unterstützt mehrere Edge Delivery-Sites unter verschiedenen Cloud Manager-Mandanten.</li></ul> |

<!-- >
## Practical use cases {#use-cases}

| Use case | Description |
| --- | --- |
| Website and application deployment | <ul><li>Automate the hosting and delivery of static or dynamic sites.</li><li>Ensure fast performance through edge caching. </li></ul> |
| API gateway and content delivery | <ul><li>Optimize API responses by caching data at the edge.</li><li>Reduce backend load and improved response times. </li></ul> |
| Real-time content updates | <ul><li>Instant deployment of new content across edge locations.</li><li>Support integration with automated content pipelines. </li></ul> |
| Edge computing workloads | <ul><li>Support serverless computing to process workloads closer to users.</li><li>Reduce latency and enhance performance. </li></ul> |
| Security and governance | <ul><li>Security is provided with integrated DDoS (Distributed Denial of Service) protection and WAF (Web Application Firewall) integration.</li><li>Ensure that content is delivered securely through TLS (Transport Security Layer) encryption. </li></ul> |
-->

## Erstellen einer Edge Delivery-Site in Cloud Manager mit einem Klick {#one-click-edge-delivery-site}

Um eine Adobe Edge-Bereitstellungs-Site mit einem Klick zu erstellen, muss Ihr Unternehmen über eine verfügbare Edge Delivery Services-Lizenz verfügen. Diese Lizenz ist Teil von Adobe Experience Manager (AEM) und zum Erstellen von Edge Delivery Services in Cloud Manager erforderlich.

Was Berechtigungen angeht, müssen Sie Mitglied der Rolle „Geschäftsinhaber“ sein oder Ihnen müssen die entsprechenden Berechtigungen zum Hinzufügen oder Bearbeiten von Programmen in Cloud Manager gewährt worden sein. Mit dieser Zugriffsebene können Sie die Integration von Edge Delivery Services in Ihre Programme steuern.

Siehe auch [Einführung in Edge Delivery Services in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

<!-- PROPER AEM BOT CONFIGURATIONS MUST BE IN PLACE FIRST FOR AUTOMATIC CONTENT UPDATES? TRUE or FALSE? -->

**So erstellen Sie eine Edge Delivery-Site in Cloud Manager mit einem Klick:**

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.
1. Klicken Sie im Menü links unter der Überschrift **Programm** auf **Übersicht**.
1. Klicken Sie auf der **Programmübersicht** auf die Registerkarte **Edge Delivery**.
1. Klicken Sie auf der Seite &quot;Edge Delivery&quot; im Dialogfeld &quot;Edge Delivery-**&quot; in der Gruppe** Edge Delivery-Site hinzufügen **auf** Site jetzt erstellen **.**
1. Geben **im Dialogfeld &quot;Edge Delivery-Site**&quot; im Textfeld **Projektname** den Namen Ihrer Site ein und klicken Sie dann auf **Site jetzt erstellen**.

   In der oberen Mitte des Bildschirms wird eine Meldung angezeigt, die Sie darüber informiert, dass die Bereitstellung der Edge Delivery-Site begonnen hat.

Wenn die Site-Bereitstellung und -Validierung durch Cloud Manager abgeschlossen sind, wird **Site-Name** (der zuvor eingegebene Projektname) im Listenfeld **Edge Delivery Sites** auf der Edge Delivery-Seite angezeigt. Außerdem wird links neben der Repository-URL ein grünes Häkchen angezeigt.


### Erkunden einer mit einem Klick erstellten Edge Delivery-Site {#explore-one-click-ed-site}

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.
1. Klicken Sie im Menü links unter der Überschrift **Programm** auf **Übersicht**.
1. Klicken Sie auf der **Programmübersicht** auf die Registerkarte **Edge Delivery**.
1. Führen Sie auf der Seite &quot;Edge Delivery&quot; einen der folgenden Schritte aus:

   | Zu erkunden | Schritte |
   | --- | --- |
   | GitHub-Repository einer Site | <ul><li>Klicken Sie im Listenfeld **Edge Delivery Sites** unter der Spaltenüberschrift **Repository** auf die URL der soeben erstellten Site.<br>Möglicherweise müssen Sie sich mit Ihrem Benutzernamen oder Ihrer E-Mail-Adresse und Ihrem Passwort bei GitHub anmelden.</li> |
   | Veröffentlichen einer Site | <ul><li> Klicken Sie im Listenfeld **Edge Delivery Sites** ganz rechts neben dem Namen Ihrer Site auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), um das Dropdown-Menü zu öffnen.</li><li>Klicken Sie ![ Dropdown](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PublishCheck_18_N.svg)Menü auf **Überprüfen Sie** Veröffentlichungssymbol/-site).<br>Eine Popup-Meldung wird angezeigt, die Sie darüber informiert, dass die Veröffentlichung der Site erfolgreich gestartet wurde.</li></ul> |
   | Vorschau einer veröffentlichten Site | <ul><li>Klicken Sie im Listenfeld **Edge Delivery Sites** unter der Spaltenüberschrift **Site-Name** auf die URL der soeben erstellten und veröffentlichten Site.<br>Beachten Sie in der URL-Adressleiste Ihres Browsers, dass die URL der Site mit `.page` endet, was anzeigt, dass Sie eine Vorschau der Site sehen.</li><li>Um die Site live anzuzeigen, ändern Sie `.page` in der URL-Adressleiste manuell in `.live`.</li></ul> |
   | Gewähren von Benutzerzugriff auf das Inhalts-Repository auf dem Google-Laufwerk | <ul><li> Klicken Sie im Listenfeld **Edge Delivery Sites** ganz rechts neben dem Namen Ihrer Site auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), um das Dropdown-Menü zu öffnen.</li><li>Klicken Sie ![ Dropdown](https://spectrum.adobe.com/static/icons/workflow_18/Smock_UsersAdd_18_N.svg)Menü auf Benutzer hinzufügen **Zugriff auf** Inhalts-Repository erhalten).</li><li>Geben **im Dialogfeld Mitarbeiter zu Ihrer Site hinzufügen** die E-Mail-Adresse eines Mitwirkenden ein und klicken Sie dann auf ![Häkchensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Fahren Sie mit dem Hinzufügen von Beitragende-E-Mails fort, sofern erforderlich.</li><li>Wenn Sie fertig sind, klicken Sie auf **Mitarbeiter hinzufügen**.</li><li>Um den Link für Ihre Mitwirkenden an der Inhaltserstellung freizugeben, klicken Sie im Dialogfeld **0&rbrace;Collaboration erfolgreich hinzugefügt“ auf** OK **.**</li><li>Klicken Sie im Dialogfeld Erfolgreich hinzugefügte Collaboration auf ![Kopiersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg), um den Link zu kopieren und für Ihre Mitwirkenden freizugeben.<br>Bevor Sie den Link freigeben, vergewissern Sie sich, dass die Mitarbeiter mit der E-Mail-Adresse angemeldet sind, die mit ihrem IMS-Konto verknüpft ist. Wenn ihr IMS-E-Mail-Konto nicht verfügbar ist, muss sie die als Mitarbeiter hinzugefügte E-Mail-Adresse verwenden. Dadurch wird sichergestellt, dass Mitwirkende auf den Link zugreifen und die zu bearbeitenden oder zu aktualisierenden Inhalte auf Google Drive sehen können.</li><li>Wenn Sie die Bearbeitung abgeschlossen haben, klicken Sie **Website veröffentlichen** in Cloud Manager, wie oben beschrieben.<br>Oder sehen Sie sich die vorgenommenen Änderungen wie oben beschrieben in der Vorschau an.</li></ul> |
   | Gewähren Sie Benutzern Zugriff auf das Basis-Repository auf GitHub | <ul><li> Klicken Sie im Listenfeld **Edge Delivery Sites** ganz rechts neben dem Namen Ihrer Site auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), um das Dropdown-Menü zu öffnen.</li><li>Klicken Sie ![ Dropdown-Menü ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg)Code-Symbol **(Zugriff auf** Basis-Repository).</li><li>Geben **im Dialogfeld Zugriff auf das Basis-Repository für Ihre Site** den GitHub-Benutzernamen eines Mitarbeiters ein und klicken Sie dann auf ![Häkchensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Fügen Sie bei Bedarf weitere GitHub-Benutzernamen hinzu.</li><li>Wenn Sie fertig sind, klicken Sie auf **Mitarbeiter hinzufügen**.</li>Benutzer müssen Zugriff auf ihren eigenen GitHub-Benutzernamen gewähren, um das Repository anzeigen zu können. |




