---
title: Erstellen einer Site aus Vorlage
description: Erfahren Sie, wie Sie mithilfe einer Site-Vorlage schnell eine neue AEM erstellen können.
source-git-commit: 73e9d1debe70aff7f53d658bbac074fc53d8f1ae
workflow-type: tm+mt
source-wordcount: '1518'
ht-degree: 1%

---


# Erstellen einer Site aus Vorlage {#create-site-from-template}

Erfahren Sie, wie Sie mithilfe einer Site-Vorlage schnell eine neue AEM erstellen können.

>[!CAUTION]
>
>Das Tool für die schnelle Site-Erstellung ist derzeit eine technische Vorschau. Sie wird zu Test- und Evaluierungszwecken bereitgestellt und ist nicht zur Verwendung in der Produktion bestimmt, es sei denn, sie wurde mit der Adobe Support vereinbart.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Schnellsite-Journey [Machen Sie sich mit Cloud Manager und dem Arbeitsablauf für die schnelle Site-Erstellung vertraut,](cloud-manager.md) Sie haben sich mit Cloud Manager vertraut gemacht und erfahren, wie der neue Schnellsite-Erstellungsprozess verbunden wird. Sie sollten jetzt:

* Erfahren Sie, wie AEM Sites und Cloud Manager zusammenarbeiten, um die Front-End-Entwicklung zu erleichtern.
* Erfahren Sie, wie der Front-End-Anpassungsschritt vollständig von AEM entkoppelt ist und kein AEM Wissen erfordert.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie den ersten Konfigurationsschritt durchführen und eine neue Site aus einer Vorlage erstellen können, die Sie später mithilfe von Frontend-Tools anpassen können.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie mithilfe einer Site-Vorlage schnell eine neue AEM erstellen. Nach dem Lesen sollten Sie:

* Erfahren Sie, wie Sie AEM Site-Vorlagen abrufen.
* Erfahren Sie, wie Sie mit einer Vorlage eine neue Site erstellen.
* Erfahren Sie, wie Sie die Vorlage von Ihrer neuen Website herunterladen können, um sie für den Frontend-Entwickler bereitzustellen.

## Verantwortliche Rolle {#responsible-role}

Dieser Teil der Journey gilt für den AEM Administrator.

## Site-Vorlagen {#site-templates}

Site-Vorlagen bieten die Möglichkeit, grundlegende Site-Inhalte in einem bequemen und wiederverwendbaren Paket zu kombinieren. Site-Vorlagen enthalten in der Regel grundlegende Site-Inhalte und -Struktur sowie Site-Styling-Informationen, um neue Sites schnell zu starten. Die eigentliche Struktur sieht wie folgt aus:

* `files`: Ordner mit dem Benutzeroberflächen-Kit, XD und möglicherweise anderen Dateien
* `previews`: Ordner mit Screenshots der Site-Vorlage
* `site`: Inhaltspaket des Inhalts, der für jede aus dieser Vorlage erstellte Site kopiert wird, z. B. Seitenvorlagen, Seiten usw.
* `theme`: Quellen des Vorlagendesigns, um das Aussehen der Site zu ändern, einschließlich CSS, JavaScript usw.

Vorlagen sind leistungsstark, da sie wiederverwendbar sind, sodass Ihre Inhaltsautoren schnell eine Site erstellen können. Und da Sie in Ihrer AEM mehrere Vorlagen zur Verfügung haben, können Sie flexibel verschiedene geschäftliche Anforderungen erfüllen.

>[!NOTE]
>
>Die Site-Vorlage darf nicht mit Seitenvorlagen verwechselt werden. Die hier beschriebenen Site-Vorlagen definieren die Gesamtstruktur einer Site. Eine Seitenvorlage definiert die Struktur und den anfänglichen Inhalt einer einzelnen Seite.

## Beziehen einer Site-Vorlage {#obtaining-template}

Die einfachste Art, zu beginnen, ist [Laden Sie die neueste Version der AEM Standard-Site-Vorlage aus dem GitHub-Repository herunter.](https://github.com/adobe/aem-site-template-standard/releases)

Nach dem Herunterladen können Sie es wie jedes andere Paket in Ihre AEM-Umgebung hochladen. Siehe [Abschnitt &quot;Zusätzliche Ressourcen&quot;](#additional-resources) für Details zur Arbeit mit Paketen, wenn Sie weitere Informationen zu diesem Thema benötigen.

>[!TIP]
>
>Die AEM Standard-Site-Vorlage kann an die Anforderungen Ihres Projekts angepasst werden und die Notwendigkeit weiterer Anpassungen vermeiden. Dieses Thema geht jedoch über den Rahmen dieser Journey hinaus. Weitere Informationen finden Sie in der GitHub-Dokumentation der Standard-Site-Vorlage .

>[!TIP]
>
>Sie können die Vorlage auch aus der Quelle als Teil Ihres Projekt-Workflows erstellen. Dieses Thema geht jedoch über den Rahmen dieser Journey hinaus. Weitere Informationen finden Sie in der GitHub-Dokumentation der Standard-Site-Vorlage .

## Installieren einer Site-Vorlage {#installing-template}

Die Verwendung einer Vorlage zur Erstellung einer neuen Site ist sehr einfach.

1. Melden Sie sich bei Ihrer AEM Authoring-Umgebung an und navigieren Sie zur Sites-Konsole

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Tippen oder klicken Sie auf **Erstellen** oben rechts im Bildschirm und aus dem Dropdown-Menü wählen Sie **Site aus Vorlage**.

   ![Erstellen einer neuen Site aus einer Vorlage](assets/create-site-from-template.png)

1. Tippen oder klicken Sie im Assistenten &quot;Site erstellen&quot;auf **Import** oben in der linken Spalte.

   ![Assistent zur Site-Erstellung](assets/site-creation-wizard.png)

1. Suchen Sie im Dateibrowser nach der Vorlage . [Sie haben zuvor](#obtaining-template) und tippen oder klicken Sie auf **Hochladen**.

1. Nach dem Hochladen wird er in der Liste der verfügbaren Vorlagen angezeigt. Tippen oder klicken Sie auf die Vorlage, um sie auszuwählen (dadurch werden auch Informationen über die Vorlage in der rechten Spalte angezeigt) und tippen oder klicken Sie dann auf **Nächste**.

   ![Wählen Sie eine Vorlage aus](assets/select-site-template.png)

1. Geben Sie einen Titel für Ihre Site an. Ein Site-Name kann angegeben werden oder wird aus dem Titel generiert, wenn er weggelassen wird.

   * Der Titel der Site wird in der Titelleiste des Browsers angezeigt.
   * Der Site-Name wird Teil der URL.

1. Tippen oder klicken Sie auf **Erstellen** und die neue Site aus der Site-Vorlage erstellt wird.

   ![Details der neuen Site](assets/create-site-details.png)

1. Tippen oder klicken Sie im angezeigten Bestätigungsdialogfeld auf **Fertig**.

   ![Dialogfeld &quot;Erfolg&quot;](assets/success.png)

1. In der Sites-Konsole sind die neuen Sites sichtbar und können navigiert werden, um die von der Vorlage definierte grundlegende Struktur zu untersuchen.

   ![Neue Site-Struktur](assets/new-site.png)

Inhaltsautoren können jetzt mit der Bearbeitung beginnen.

## Ist eine weitere Anpassung erforderlich? {#customization-required}

Site-Vorlagen sind sehr leistungsstark und flexibel und können für ein Projekt erstellt werden, was eine einfache Erstellung von Site-Varianten ermöglicht. Je nachdem, welcher Grad der Anpassung bereits an die von Ihnen verwendete Site-Vorlage vorgenommen wurde, müssen Sie möglicherweise nicht einmal zusätzliche Frontend-Anpassungen vornehmen.

* Wenn Ihre Site keine zusätzliche Anpassung erfordert, gratulieren Sie dazu! Deine Journey endet hier!
* Wenn Sie weiterhin zusätzliche Frontend-Anpassungen benötigen oder einfach den gesamten Prozess verstehen möchten, falls Sie zukünftige Anpassungen benötigen, lesen Sie bitte weiter.

## Beispielseite {#example-page}

Wenn Sie eine zusätzliche Frontend-Anpassung benötigen, sollten Sie beachten, dass der Frontend-Entwickler möglicherweise nicht mit den Details Ihres Inhalts vertraut ist. Daher ist es empfehlenswert, dem Entwickler einen Pfad zu typischen Inhalten zur Verfügung zu stellen, der als Referenz verwendet werden kann, wenn das Design angepasst wird. Ein typisches Beispiel ist die Startseite für die Übergeordnete Sprache der Site.

1. Navigieren Sie im Sites-Browser zur Startseite der Übergeordneten Sprache der Site, tippen oder klicken Sie dann auf die Seite, um sie auszuwählen, und tippen oder klicken Sie auf **Bearbeiten** in der Menüleiste.

   ![Typische Startseite](assets/home-page-in-console.png)

1. Wählen Sie im Editor die **Seiteninformationen** in der Symbolleiste und **Als veröffentlicht anzeigen**.

   ![Bearbeiten der Startseite](assets/home-page-edit.png)

1. Kopieren Sie in der sich öffnenden Registerkarte den Pfad des Inhalts aus der Adressleiste. Sie sieht ungefähr so aus: `/content/<your-site>/en/home.html?wcmmode=disabled`.

   ![Startseite](assets/home-page.png)

1. Speichern Sie den Pfad, der später für den Frontend-Entwickler bereitgestellt werden soll.

## Thema herunterladen {#download-theme}

Nachdem die Site erstellt wurde, kann das von der Vorlage generierte Design der Site heruntergeladen und dem Frontend-Entwickler zur Anpassung bereitgestellt werden.

1. Zeigen Sie in der Sites-Konsole die **Site** Leiste.

   ![Seitenleiste anzeigen](assets/show-site-rail.png)

1. Tippen oder klicken Sie auf das Stammverzeichnis der neuen Site und tippen oder klicken Sie auf **Themenquellen herunterladen** in der Site-Leiste.

   ![Herunterladen von Themenquellen](assets/download-theme-sources.png)

Sie haben jetzt eine Kopie der Quelldateien des Designs in Ihren Download-Dateien.

## Proxy-Benutzer einrichten {#proxy-user}

Damit der Frontend-Entwickler die Anpassungen anhand des tatsächlichen AEM von Ihrer Site in der Vorschau anzeigen kann, müssen Sie einen Proxy-Benutzer einrichten.

1. Navigieren Sie AEM von der Hauptnavigation zu **Instrumente** -> **Sicherheit** -> **Benutzer**.
1. Tippen oder klicken Sie in der Benutzerverwaltungskonsole auf **Erstellen**.

   ![Benutzerverwaltungskonsole](assets/user-management-console.png)
1. Im **Neuen Benutzer erstellen** -Fenster müssen Sie mindestens Folgendes angeben:
   * **ID** - Notieren Sie sich diesen Wert, da Sie ihn dem Frontend-Entwickler bereitstellen müssen.
   * **Passwort** - Speichern Sie diesen Wert sicher in einem Kennwortvault, da Sie ihn dem Frontend-Entwickler bereitstellen müssen.

   ![Neue Benutzerdetails](assets/new-user-details.png)

1. Im **Gruppen** Registerkarte den Proxy-Benutzer zum `contributors` hinzugefügt.
   * Eingabe im Begriff `contributors` Trigger AEM die Funktion der automatischen Vervollständigung für die einfache Auswahl der Gruppe.

   ![Zu Gruppe hinzufügen](assets/add-to-group.png)

1. Tippen oder klicken Sie auf **Speichern und schließen**.

Sie haben die Konfiguration abgeschlossen. Inhaltsautoren können jetzt mit der Erstellung von Inhalten auf der Site beginnen, die Vorbereitung für die Frontend-Anpassung im nächsten Schritt der Journey zu beginnen.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der Journey zur AEM Schnellseitenerstellung abgeschlossen haben, sollten Sie Folgendes tun:

* Erfahren Sie, wie Sie AEM Site-Vorlagen abrufen.
* Erfahren Sie, wie Sie mit einer Vorlage eine neue Site erstellen.
* Erfahren Sie, wie Sie die Vorlage von Ihrer neuen Website herunterladen können, um sie für den Frontend-Entwickler bereitzustellen.

Machen Sie sich mit diesem Wissen vertraut und fahren Sie mit der Journey zur AEM SchnellSite-Erstellung fort, indem Sie das Dokument erneut überprüfen. [Einrichten der Pipeline,](pipeline-setup.md) wo Sie eine Front-End-Pipeline erstellen, um die Anpassung des Designs Ihrer Site zu verwalten.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey zur Schnellseitenerstellung zu wechseln, indem Sie das Dokument lesen [Einrichten der Pipeline,](pipeline-setup.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf dem Journey weiterarbeiten müssen.

* [AEM Standard-Site-Vorlage](https://github.com/adobe/aem-site-template-standard) - Dies ist das GitHub-Repository der AEM Standard-Site-Vorlage.
* [Erstellen und Organisieren von Seiten](/help/sites-cloud/authoring/fundamentals/organizing-pages.md) - In diesem Handbuch wird beschrieben, wie Sie Seiten Ihrer AEM-Site verwalten, wenn Sie sie nach der Erstellung aus der Vorlage weiter anpassen möchten.
* [Arbeiten mit Paketen](/help/implementing/developing/tools/package-manager.md) - Pakete ermöglichen den Import und Export von Repository-Inhalten. In diesem Dokument wird erläutert, wie Sie mit Paketen in AEM 6.5 arbeiten, was auch für AEMaaCS gilt.
* [Dokumentation zur Site-Verwaltung](/help/sites-cloud/administering/site-creation/create-site.md) - Weitere Informationen zu den Funktionen des Tools für die schnelle Site-Erstellung finden Sie in den technischen Dokumenten zur Site-Erstellung .
