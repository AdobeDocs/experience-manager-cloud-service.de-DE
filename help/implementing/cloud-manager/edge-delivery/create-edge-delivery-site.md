---
title: Erstellen Ihrer ersten Edge Delivery-Site mit einem Klick
description: Erfahren Sie, wie Sie mit einem Klick auf eine Schaltfläche schnell eine Edge Delivery-Site in Cloud Manager erstellen können.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 292bf0b4-990b-4980-b971-91b8aedde3de
source-git-commit: aa8aba7f798e251c8a25ee247402e23517707e88
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 62%

---

# Erstellen Ihrer ersten Edge Delivery-Site mit einem Klick{#about-one-click-edge-delivery-site}

Das Erstellen Ihrer ersten Edge Delivery-Site mit einem Klick wurde entwickelt, um das Onboarding und die Bereitstellung von Edge Delivery-Sites in Cloud Manager zu automatisieren. Dies vereinfacht den Prozess erheblich, da Sie nur auf eine einzige Schaltfläche klicken müssen. Mit diesem einen Klick erreichen Sie, dass die erforderliche Infrastruktur bereitgestellt, eine Integration mit GitHub zur Versionskontrolle durchgeführt und Ihr Dokument- und Asset-Speicher in Google Drive konfiguriert wird.

Diese Automatisierung trägt dazu bei, den manuellen Aufwand bei der Einrichtung Ihrer ersten Site zu reduzieren. Auf diese Weise werden nicht nur nahtlose Workflows sowie Skalierbarkeit sichergestellt, sondern auch die Leistung Ihrer Teams bei der Verwaltung von Inhalten am Edge verbessert.

<!--
 Check out this quick 2-minute video for a step-by-step walkthrough on creating your first Edge Delivery site—no hassle, just one click.

>[!VIDEO](https://video.tv.adobe.com/v/3458975?quality=12&learn=on)
-->



<!--
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

1. Melden Sie sich bei Cloud Manager unter [experience.adobe.com](https://experience.adobe.com) an.
   1. Klicken Sie **Abschnitt „Schnellzugriff** auf **Experience Manager**.
   1. Klicken Sie im linken Panel auf **Cloud Manager**.
   1. Wählen Sie die gewünschte Organisation aus.
1. Klicken Sie in **Konsole** Meine Programme“ auf ein Programm.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.
1. Klicken Sie im linken Seitenmenü unter der Überschrift **Programm** auf **Überblick**.
1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**.
1. Klicken Sie auf der Seite &quot;Edge Delivery&quot; im Dialogfeld &quot;Edge Delivery-**&quot; in der Gruppe** Edge Delivery-Site hinzufügen **auf** Site jetzt erstellen **.**
1. Geben Sie **Dialogfeld &quot;Edge Delivery** Site erstellen“ im Textfeld **Projektname** den Namen Ihrer Site ein.
1. Wählen **unter &quot;**&quot; eine der folgenden Optionen aus:
   * **Dokumenterstellung** - Erstellen von Inhalten in Google Drive oder SharePoint. Diese Option ist die Standardeinstellung und erfordert keine AEM-Umgebung.
   * **AEM-Authoring (Beta)** - Verfassen Sie Inhalte in AEM mit dem universellen Editor. Wenn Sie diese Option wählen, wählen **unter „Vorlage**&quot; eine Anfangsvorlage für Ihre Edge Delivery-Site aus.

   ![Dialogfeld &quot;Edge Delivery-Site erstellen“ mit ausgewähltem AEM-Authoring.](/help/implementing/cloud-manager/edge-delivery/assets/eds-create-aem-authoring.png)

1. Wählen **in der Dropdown** Liste Authoring-Umgebungen eine AEM-Umgebung für das Authoring aus. Diese Umgebung muss bereits in Ihrem Programm vorhanden sein. Es ist nur die Autorenebene erforderlich. Eine Veröffentlichungsebene ist nicht erforderlich, wenn Edge Delivery die Bereitstellung handhabt. Siehe [Flexible Veröffentlichungsebene (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).

1. Klicken Sie **Site jetzt erstellen**.

   Oben in der Mitte des Bildschirms wird eine Popup-Meldung angezeigt, die Sie darüber informiert, dass die Bereitstellung der Edge Delivery-Site begonnen hat.

Wenn die Bereitstellung und Validierung der Site durch Cloud Manager abgeschlossen sind, wird der **Site-Name** (der zuvor eingegebene Projektname) im Listenfeld **Edge Delivery Sites** auf der Edge Delivery-Seite angezeigt. Außerdem wird links neben der Spalte Verifizierter Status ein grüner Punkt angezeigt.

Siehe auch [Veröffentlichen von Inhalten von AEM Author in Edge Delivery](#publish-from-aem-author).

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
   | Gewähren von Benutzerzugriff auf das Content-Repository auf Google Drive | <ul><li> Klicken Sie im Listenfeld **Edge Delivery-Sites** ganz rechts neben dem Namen Ihrer Site auf ![More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), um das Dropdown-Menü zu öffnen.</li><li>Klicken Sie im Dropdown-Menü auf ![Users Add icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_UsersAdd_18_N.svg) **Zugriff auf das Content-Repository erhalten**.</li><li>Geben Sie im Dialogfeld **`Add collaborators to your site`** die E-Mail-Adresse eines Mitwirkenden ein und klicken Sie auf ![Häkchensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Fahren Sie nach Bedarf mit dem Hinzufügen der E-Mail-Adressen von Mitwirkenden fort.</li><li>Klicken Sie abschließend auf **Mitarbeitende hinzufügen**. </li><li>Um den Link für Ihre Mitwirkenden an der Inhaltserstellung freizugeben, klicken Sie im Dialogfeld **Zusammenarbeit erfolgreich hinzugefügt** auf **OK**.</li><li>Klicken Sie im Dialogfeld „Zusammenarbeit erfolgreich hinzugefügt“ auf ![Copy icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg), um den Link zu kopieren und für Ihre Mitwirkenden freizugeben.<br>Vergewissern Sie sich vor der Freigabe des Links, dass die Mitwirkenden mit der E-Mail-Adresse angemeldet sind, die mit ihrem IMS-Konto verknüpft ist. Wenn ihr IMS-E-Mail-Konto nicht verfügbar ist, müssen sie die als Mitwirkende bzw. Mitwirkender hinzugefügte E-Mail-Adresse verwenden. Dadurch wird sichergestellt, dass Mitwirkende auf den Link zugreifen und die zu bearbeitenden oder zu aktualisierenden Inhalte auf Google Drive sehen können.</li><li>Klicken Sie nach Abschluss der Bearbeitung in Cloud Manager wie oben beschrieben auf **Site veröffentlichen**.<br>Oder sehen Sie sich die vorgenommenen Änderungen wie oben beschrieben in der Vorschau an.</li></ul> |
   | Gewähren von Benutzerzugriff auf das Basis-Rrepository auf GitHub | <ul><li> Klicken Sie im Listenfeld **Edge Delivery-Sites** ganz rechts neben dem Namen Ihrer Site auf ![More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), um das Dropdown-Menü zu öffnen.</li><li>Klicken Sie im Dropdown-Menü auf ![Code icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) **Zugriff auf das Basis-Repository erhalten**.</li><li>Geben Sie im Dialogfeld **Auf das Basis-Repository der Site zugreifen** den GitHub-Benutzernamen eines oder einer Mitwirkenden ein, und klicken Sie dann auf ![Checkmark icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Fahren Sie nach Bedarf mit dem Hinzufügen von GitHub-Benutzernamen fort.</li><li>Klicken Sie abschließend auf **Mitarbeitende hinzufügen**. </li>Benutzende müssen Zugriff auf ihren eigenen GitHub-Benutzernamen gewähren, um das Repository anzeigen zu können. |

## Veröffentlichen von Inhalten von AEM Author in Edge Delivery (Beta) {#publish-from-aem-author}

>[!NOTE]
>
>Die hier beschriebene Veröffentlichungsfunktion befindet sich in Beta. Um sich der Beta anzuschließen, senden Sie eine E-Mail an [&#128279;](mailto:grp-beta_xwalk-publish_config@adobe.com)grp-beta_xwalk-publish_config@adobe.com) mit Ihrer Adobe Organisations-ID und Programm-ID.

Diese Funktion ist nur für Edge Delivery-Sites verfügbar, die mit der Authoring-Option von AEM erstellt wurden.

Nachdem Ihre Edge Delivery-Site in Cloud Manager erstellt und **verifiziert** können Sie Inhalte mit dem universellen Editor von AEM erstellen und veröffentlichen.

**So greifen Sie über Cloud Manager auf den universellen Editor zu:**

1. Suchen Sie auf der Registerkarte Edge Delivery in der Liste Edge Delivery Sites Ihre Site.

   ![Veröffentlichen von Inhalten von AEM Author in Edge Delivery](/help/implementing/cloud-manager/edge-delivery/assets/eds-content-source-link.png)

1. Klicken Sie auf **Link** Content Source&quot; in der Zeile der Site. Durch Klicken auf diesen Link wird die Seite des universellen Editors von AEM geöffnet, in der Sie Inhalte für Ihre Site erstellen und bearbeiten können.

**So veröffentlichen Sie Inhalte:**

* **Von Cloud Manager** -

   1. Klicken Sie auf **&#x200B;**&#x200B;Registerkarte **Bereitstellung veröffentlichen** der Seite auf der Karte **Umgebungen** auf das hervorgehobene Symbol ![Info oder Informationen](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg).

   1. Wählen Sie im Informations-Popup die Option **Zum Aktivieren klicken** aus, um die Bereitstellung der Veröffentlichungsebene in der Benutzeroberfläche von Cloud Manager zu aktivieren.

      ![Klicken Sie, um die Bereitstellung der Veröffentlichungsebene zu aktivieren](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/click-to-activate-publish-tier-capabilities.png)

   1. Klicken Sie im Dialogfeld Veröffentlichungsebene aktivieren auf **Aktivieren**.

      ![Dialogfeld „Veröffentlichungsebene aktivieren“](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/activate-publish-tier.png)

      Nach der Aktivierung wird die Veröffentlichungsebene automatisch bereitgestellt. Alternativ kann die Veröffentlichungsebene automatisch bereitgestellt werden, wenn der Autor versucht, Inhalte direkt über die AEM-Benutzeroberfläche zu veröffentlichen.

      Nachdem die Veröffentlichungsebene aktiviert und erfolgreich bereitgestellt wurde, wird der Link **Zum Aktivieren klicken** abgeblendet/nicht verfügbar.

* **Von AEM-**: Klicken Sie in der Authoring-Oberfläche von AEM auf **Quick Publish**, um Inhalte direkt auf Ihrer Edge Delivery-Site zu veröffentlichen. Die Veröffentlichungsebene ist für diesen Vorgang nicht erforderlich, wenn die Bereitstellung von Edge Delivery verarbeitet wird.

Nach der Veröffentlichung können Sie eine Vorschau Ihres Inhalts unter der `.page` URL Ihrer Site anzeigen oder ihn live unter der `.live` URL anzeigen.—>

