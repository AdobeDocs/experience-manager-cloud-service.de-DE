---
title: Erstellen Ihrer ersten Edge Delivery-Site mit einem Klick
description: Erfahren Sie, wie Sie mit einem Klick in Cloud Manager schnell eine Edge Delivery-Site erstellen können.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 292bf0b4-990b-4980-b971-91b8aedde3de
source-git-commit: 9bf64836c2f769c31017d7f9df6bc26b280606a0
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 95%

---

# Erstellen Ihrer ersten Edge Delivery-Site mit einem Klick{#about-one-click-edge-delivery-site}

Die Erstellung Ihrer ersten Edge Delivery-Site mit einem Klick hilft Ihnen bei der Automatisierung des Onboarding und der Bereitstellung von Edge Delivery-Sites in Cloud Manager. Dies vereinfacht den Prozess erheblich, da Sie nur auf eine einzige Schaltfläche klicken müssen. Mit diesem einen Klick erreichen Sie, dass die erforderliche Infrastruktur bereitgestellt, eine Integration mit GitHub zur Versionskontrolle durchgeführt und Ihr Dokument- und Asset-Speicher in Google Drive konfiguriert wird.

Diese Automatisierung trägt dazu bei, den manuellen Aufwand bei der Einrichtung Ihrer ersten Site zu reduzieren. Auf diese Weise werden nicht nur nahtlose Workflows sowie Skalierbarkeit sichergestellt, sondern auch die Leistung Ihrer Teams bei der Verwaltung von Inhalten am Edge verbessert.

<!-- ADD LINK TO DORU'S VIDEO DEMO -->

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

Um eine Adobe Edge Delivery-Site mit einem Klick zu erstellen, muss Ihre Organisation über eine verfügbare Edge Delivery Services-Lizenz verfügen. Diese Lizenz ist Teil von Adobe Experience Manager (AEM) und für die Erstellung von Edge Delivery Services in Cloud Manager erforderlich.

Was Berechtigungen angeht, müssen Sie Mitglied der Rolle „Geschäftsinhaber“ sein oder Ihnen müssen die entsprechenden Berechtigungen zum Hinzufügen oder Bearbeiten von Programmen in Cloud Manager gewährt worden sein. Mit dieser Zugriffsebene können Sie die Integration von Edge Delivery Services in Ihre Programme steuern.

Siehe auch [Einführung in Edge Delivery Services in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

<!-- PROPER AEM BOT CONFIGURATIONS MUST BE IN PLACE FIRST FOR AUTOMATIC CONTENT UPDATES? TRUE or FALSE? -->

**So erstellen Sie eine Edge Delivery-Site in Cloud Manager mit einem Klick:**

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.
1. Klicken Sie im linken Seitenmenü unter der Überschrift **Programm** auf **Überblick**.
1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**. 
1. Klicken Sie auf der Edge Delivery-Seite im Dialogfeld **Aufgabenliste für Edge Delivery** im Gruppenfeld **Edge Delivery-Site hinzufügen** auf **Site jetzt erstellen**.
1. Geben Sie im Dialogfeld **Edge Delivery-Site erstellen** in das Textfeld **Projektname** den Namen Ihrer Site ein und klicken Sie dann auf **Site jetzt erstellen**.

   Oben in der Mitte des Bildschirms wird eine Popup-Meldung angezeigt, die Sie darüber informiert, dass die Bereitstellung der Edge Delivery-Site begonnen hat.

Wenn die Bereitstellung und Validierung der Site durch Cloud Manager abgeschlossen sind, wird der **Site-Name** (der zuvor eingegebene Projektname) im Listenfeld **Edge Delivery Sites** auf der Edge Delivery-Seite angezeigt. Außerdem wird links neben der Repository-URL ein grünes Häkchen angezeigt.


### Erkunden einer mit einem Klick erstellten Edge Delivery-Site {#explore-one-click-ed-site}

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.
1. Klicken Sie im linken Seitenmenü unter der Überschrift **Programm** auf **Überblick**.
1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**.
1. Führen Sie auf der Edge Delivery-Seite eine der folgenden Aktionen aus:

   | Folgendes kann erkundet werden | Schritte |
   | --- | --- |
   | GitHub-Repository einer Site | <ul><li>Klicken Sie im Listenfeld **Edge Delivery-Sites** unter der Spaltenüberschrift **Repository** auf die URL der soeben erstellten Site.<br>Möglicherweise müssen Sie sich mit Ihrem Benutzernamen oder Ihrer E-Mail-Adresse und Ihrem Kennwort bei GitHub anmelden.</li> |
   | Veröffentlichen einer Site | <ul><li> Klicken Sie im Listenfeld **Edge Delivery-Sites** ganz rechts neben dem Namen Ihrer Site auf ![More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), um das Dropdown-Menü zu öffnen.</li><li>Klicken Sie im Dropdown-Menü auf ![Publish Check icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PublishCheck_18_N.svg) **Site veröffentlichen**.<br>Es wird eine Popup-Meldung mit dem Hinweis angezeigt, dass die Veröffentlichung der Site erfolgreich gestartet wurde.</li></ul> |
   | Vorschau einer veröffentlichten Site | <ul><li>Klicken Sie im Listenfeld **Edge Delivery-Sites** unter der Spaltenüberschrift **Site-Name** auf die URL der soeben erstellten und veröffentlichten Site.<br>Beachten Sie, dass die URL der Site in der URL-Adressleiste Ihres Browsers mit `.page` endet. Dies zeigt an, dass Sie eine Vorschau der Site sehen.</li><li>Um die Site live anzuzeigen, ändern Sie `.page` in der URL-Adressleiste manuell in `.live`.</li></ul> |
   | Gewähren von Benutzerzugriff auf das Content-Repository auf Google Drive | <ul><li> Klicken Sie im Listenfeld **Edge Delivery-Sites** ganz rechts neben dem Namen Ihrer Site auf ![More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), um das Dropdown-Menü zu öffnen.</li><li>Klicken Sie im Dropdown-Menü auf ![Users Add icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_UsersAdd_18_N.svg) **Zugriff auf das Content-Repository erhalten**.</li><li>Geben Sie im Dialogfeld **Mitarbeitende zur Site hinzufügen** die E-Mail-Adresse eines oder einer Mitwirkenden ein und klicken Sie dann auf ![Checkmark icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Fahren Sie nach Bedarf mit dem Hinzufügen der E-Mail-Adressen von Mitwirkenden fort.</li><li>Klicken Sie abschließend auf **Mitarbeitende hinzufügen**. </li><li>Um den Link für Ihre Mitwirkenden an der Inhaltserstellung freizugeben, klicken Sie im Dialogfeld **Zusammenarbeit erfolgreich hinzugefügt** auf **OK**.</li><li>Klicken Sie im Dialogfeld „Zusammenarbeit erfolgreich hinzugefügt“ auf ![Copy icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg), um den Link zu kopieren und für Ihre Mitwirkenden freizugeben.<br>Vergewissern Sie sich vor der Freigabe des Links, dass die Mitwirkenden mit der E-Mail-Adresse angemeldet sind, die mit ihrem IMS-Konto verknüpft ist. Wenn ihr IMS-E-Mail-Konto nicht verfügbar ist, müssen sie die als Mitwirkende bzw. Mitwirkender hinzugefügte E-Mail-Adresse verwenden. Dadurch wird sichergestellt, dass Mitwirkende auf den Link zugreifen und die zu bearbeitenden oder zu aktualisierenden Inhalte auf Google Drive sehen können.</li><li>Klicken Sie nach Abschluss der Bearbeitung in Cloud Manager wie oben beschrieben auf **Site veröffentlichen**.<br>Oder sehen Sie sich die vorgenommenen Änderungen wie oben beschrieben in der Vorschau an.</li></ul> |
   | Gewähren von Benutzerzugriff auf das Basis-Rrepository auf GitHub | <ul><li> Klicken Sie im Listenfeld **Edge Delivery-Sites** ganz rechts neben dem Namen Ihrer Site auf ![More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), um das Dropdown-Menü zu öffnen.</li><li>Klicken Sie im Dropdown-Menü auf ![Code icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) **Zugriff auf das Basis-Repository erhalten**.</li><li>Geben Sie im Dialogfeld **Auf das Basis-Repository der Site zugreifen** den GitHub-Benutzernamen eines oder einer Mitwirkenden ein, und klicken Sie dann auf ![Checkmark icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Fahren Sie nach Bedarf mit dem Hinzufügen von GitHub-Benutzernamen fort.</li><li>Klicken Sie abschließend auf **Mitarbeitende hinzufügen**. </li>Benutzende müssen Zugriff auf ihren eigenen GitHub-Benutzernamen gewähren, um das Repository anzeigen zu können. |
