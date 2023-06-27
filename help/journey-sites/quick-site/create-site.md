---
title: Erstellen einer Site aus einer Vorlage
description: Erfahren Sie, wie Sie mithilfe einer Site-Vorlage schnell eine neue AEM-Site erstellen können.
exl-id: 31bb04c2-b3cc-44ca-b517-5b0d66d9b1fa
source-git-commit: 171aca87ff725a2f142f0336dca3491e213f55ab
workflow-type: tm+mt
source-wordcount: '1513'
ht-degree: 97%

---

# Erstellen einer Site aus einer Vorlage {#create-site-from-template}

Erfahren Sie, wie Sie mithilfe einer Site-Vorlage schnell eine neue AEM-Site erstellen können.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM-Journey zur schnellen Site-Erstellung, [Grundlegendes zu Cloud Manager und zum Workflow für die schnelle Site-Erstellung](cloud-manager.md), haben Sie sich mit Cloud Manager vertraut gemacht und erfahren, wie sich der Prozess zur schnellen Site-Erstellung zusammensetzt. Sie sollten jetzt:

* Wissen, wie AEM Sites und Cloud Manager zusammenarbeiten, um die Front-End-Entwicklung zu erleichtern.
* Erfahren haben, dass der Front-End-Anpassungsschritt vollständig von AEM entkoppelt ist und keine AEM-Kenntnisse erfordert.

Dieser Artikel baut auf diesen Grundlagen auf. Sie können also den ersten Konfigurationsschritt durchführen und eine neue Site aus einer Vorlage erstellen, die Sie später mithilfe von Front-End-Tools anpassen können.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie mithilfe einer Site-Vorlage schnell eine neue AEM-Site erstellen. Nach dem Lesen sollten Sie:

* Wissen, wie Sie AEM-Site-Vorlagen abrufen.
* Wissen, wie Sie mit einer Vorlage eine neue Site erstellen.
* Erfahren haben, wie Sie die Vorlage von Ihrer neuen Site herunterladen, um sie für den Front-End-Entwickler bereitzustellen.

## Verantwortliche Rolle {#responsible-role}

Dieser Teil der Journey gilt für den AEM-Administrator.

## Site-Vorlagen {#site-templates}

Site-Vorlagen bieten die Möglichkeit, grundlegende Site-Inhalte in einem handlichen und wiederverwendbaren Paket zu kombinieren. Site-Vorlagen enthalten in der Regel grundlegende Site-Inhalte und -Struktur sowie Site-Styling-Informationen, um neue Sites schnell live zu schalten. Die eigentliche Struktur sieht wie folgt aus:

* `files`: Ordner mit dem Benutzeroberflächen-Kit, der XD-Datei und möglicherweise anderen Dateien
* `previews`: Ordner mit Screenshots der Site-Vorlage
* `site`: Inhaltspaket des Inhalts, der für jede aus dieser Vorlage erstellte Site kopiert wird, z. B. Seitenvorlagen und Seiten.
* `theme`: Quellen des Vorlagen-Designs, um das Aussehen der Site zu ändern, einschließlich CSS, JavaScript usw.

Vorlagen sind leistungsstark, da sie wiederverwendbar sind, sodass Ihre Inhaltsautoren schnell eine Site erstellen können. Und da Sie in Ihrer AEM-Installation mehrere Vorlagen zur Verfügung haben können, können Sie flexibel verschiedene geschäftliche Anforderungen erfüllen.

>[!NOTE]
>
>Die Site-Vorlage darf nicht mit Seitenvorlagen verwechselt werden. Die hier beschriebenen Site-Vorlagen definieren die Gesamtstruktur einer Site. Eine Seitenvorlage definiert die Struktur und den anfänglichen Inhalt einer einzelnen Seite.

## Abrufen einer Site-Vorlage {#obtaining-template}

Am einfachsten beginnen Sie, indem [Sie die neueste Version der AEM-Standard-Site-Vorlage aus dem GitHub-Repository herunterladen](https://github.com/adobe/aem-site-template-standard/releases).

Nach dem Herunterladen können Sie sie wie jedes andere Paket in Ihre AEM-Umgebung hochladen. Im Abschnitt [Zusätzliche Ressourcen](#additional-resources) finden Sie Details zur Arbeit mit Paketen, wenn Sie weitere Informationen zu diesem Thema benötigen.

>[!TIP]
>
>Die AEM-Standard-Site-Vorlage kann an die Anforderungen Ihres Projekts angepasst werden und die Notwendigkeit weiterer Anpassungen vermeiden. Dies sprengt jedoch den Rahmen dieser Journey. Weitere Informationen finden Sie in der GitHub-Dokumentation zur Standard-Site-Vorlage.

>[!TIP]
>
>Sie können die Vorlage auch als Teil Ihres Projekt-Workflows aus der Quelle erstellen. Dies sprengt jedoch den Rahmen dieser Journey. Weitere Informationen finden Sie in der GitHub-Dokumentation zur Standard-Site-Vorlage.

## Installieren einer Site-Vorlage {#installing-template}

Die Verwendung einer Vorlage zur Erstellung einer neuen Site ist sehr einfach.

1. Melden Sie sich bei Ihrer AEM-Authoring-Umgebung an und navigieren Sie zur Sites-Konsole

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Tippen oder klicken Sie oben rechts im Bildschirm auf **Erstellen** und wählen Sie aus dem Dropdown-Menü **Site aus Vorlage**.

   ![Erstellen einer neuen Site aus einer Vorlage](assets/create-site-from-template.png)

1. Tippen oder klicken Sie im Assistenten zum Erstellen einer Site oben in der linken Spalte auf **Importieren**.

   ![Assistent zur Site-Erstellung](assets/site-creation-wizard.png)

1. Suchen Sie im Datei-Browser nach der Vorlage, die [Sie heruntergeladen haben](#obtaining-template), und tippen oder klicken Sie auf **Hochladen**.

1. Nach dem Hochladen wird sie in der Liste der verfügbaren Vorlagen angezeigt. Tippen oder klicken Sie auf die Vorlage, um sie auszuwählen (dadurch werden auch Informationen über die Vorlage in der rechten Spalte angezeigt), und tippen oder klicken Sie dann auf **Weiter**.

   ![Auswählen einer Vorlage](assets/select-site-template.png)

1. Geben Sie einen Titel für die Site ein. Ein Site-Name kann aus dem Titel bereitgestellt oder generiert werden, wenn er weggelassen wird.

   * Der Titel der Site wird in der Titelleiste des Browsers angezeigt.
   * Der Site-Name wird Teil der URL.

1. Tippen oder klicken Sie auf **Erstellen**. Die neue Site wird aus der Site-Vorlage erstellt.

   ![Details der neuen Site](assets/create-site-details.png)

1. Tippen oder klicken Sie im angezeigten Bestätigungsdialogfeld auf **Fertig**.

   ![Dialogfeld „Erfolg“](assets/success.png)

1. In der Sites-Konsole sind die neuen Sites sichtbar und in ihnen kann navigiert werden, um die von der Vorlage definierte grundlegende Struktur zu untersuchen.

   ![Neue Site-Struktur](assets/new-site.png)

Inhaltsautoren können jetzt mit der Bearbeitung beginnen.

## Ist eine weitere Anpassung erforderlich? {#customization-required}

Site-Vorlagen sind sehr leistungsstark und flexibel und können in beliebiger Anzahl für ein Projekt erstellt werden, was eine einfache Erstellung von Site-Varianten ermöglicht. Je nachdem, welcher Grad von Anpassungen bereits an der von Ihnen verwendeten Site-Vorlage vorgenommen wurde, müssen Sie möglicherweise nicht einmal zusätzliche Front-End-Anpassungen vornehmen.

* Wenn Ihre Site keine zusätzliche Anpassung erfordert, haben Sie es geschafft. Ihre Journey endet hier!
* Wenn Sie weiterhin zusätzliche Front-End-Anpassungen benötigen oder einfach den gesamten Prozess verstehen möchten, falls Sie später Anpassungen benötigen, lesen Sie bitte weiter.

## Beispielseite {#example-page}

Wenn Sie eine zusätzliche Front-End-Anpassung benötigen, sollten Sie beachten, dass der Front-End-Entwickler möglicherweise nicht mit den Details Ihres Inhalts vertraut ist. Daher ist es empfehlenswert, dem Entwickler einen Pfad zu typischen Inhalten zur Verfügung zu stellen, die als Referenz verwendet werden können, wenn das Design angepasst wird. Ein typisches Beispiel ist die Startseite für die primäre Sprache der Site.

1. Navigieren Sie im Sitebrowser zur Startseite der primären Sprache der Site, tippen oder klicken Sie dann auf die Seite, um sie auszuwählen, und tippen oder klicken Sie dann in der Menüleiste auf **Bearbeiten**.

   ![Typische Startseite](assets/home-page-in-console.png)

1. Wählen Sie im Editor in der Symbolleiste die Schaltfläche **Seiteninformationen** und dann **Als veröffentlicht anzeigen**.

   ![Bearbeiten der Startseite](assets/home-page-edit.png)

1. Kopieren Sie in der sich öffnenden Registerkarte den Pfad des Inhalts aus der Adressleiste.  Er sieht in etwa so aus: `/content/<your-site>/en/home.html?wcmmode=disabled`. 

   ![Startseite](assets/home-page.png)

1. Speichern Sie den Pfad, um ihn später dem Front-End-Entwickler bereitzustellen.

## Herunterladen des Designs {#download-theme}

Nachdem die Site erstellt wurde, kann das von der Vorlage generierte Design der Site heruntergeladen und dem Front-End-Entwickler zur Anpassung bereitgestellt werden.

1. Zeigen Sie in der Sites-Konsole auf die **Site**-Leiste.

   ![Anzeigen der Site-Leiste](assets/show-site-rail.png)

1. Tippen oder klicken Sie auf das Stammverzeichnis der neuen Site und tippen oder klicken Sie in der Site-Leiste auf **Design-Quellen herunterladen**.

   ![Herunterladen von Design-Quellen](assets/download-theme-sources.png)

Sie haben jetzt eine Kopie der Quelldateien des Designs in Ihren Download-Dateien.

## Einrichten des Proxy-Benutzers {#proxy-user}

Damit der Front-End-Entwickler die Anpassungen anhand des tatsächlichen AEM-Inhalts von Ihrer Site in der Vorschau anzeigen kann, müssen Sie einen Proxy-Benutzer einrichten.

1. Navigieren Sie in AEM in der Hauptnavigation zu **Tools** -> **Sicherheit** -> **Benutzer**.
1. Tippen oder klicken Sie in der Benutzerverwaltungskonsole auf **Erstellen**.

   ![Benutzerverwaltungskonsole](assets/user-management-console.png)
1. Im Fenster **Neuen Benutzer erstellen** müssen Sie mindestens Folgendes angeben:
   * **ID** – Notieren Sie sich diesen Wert, da Sie ihn dem Front-End-Entwickler bereitstellen müssen.
   * **Passwort** – Speichern Sie diesen Wert sicher in einem Passwort-Vault, da Sie ihn dem Front-End-Entwickler bereitstellen müssen.

   ![Neue Benutzerdetails](assets/new-user-details.png)

1. Fügen Sie auf der Registerkarte **Gruppen** den Proxy-Benutzer zur Gruppe `contributors` hinzu.
   * Durch die Eingabe des Begriffs `contributors` wird in AEM die Funktion zur automatischen Vervollständigung ausgelöst, damit die Gruppe leicht ausgewählt werden kann.

   ![Hinzufügen zur Gruppe](assets/add-to-group.png)

1. Tippen oder klicken Sie auf **Speichern und schließen**.

Sie haben die Konfiguration abgeschlossen. Inhaltsautoren können jetzt mit der Erstellung von Inhalten auf der Site beginnen. Die Vorbereitung für die Front-End-Anpassung beginnt im nächsten Schritt der Journey.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der AEM-Journey zur schnellen Site-Erstellung abgeschlossen haben, sollten Sie:

* Wissen, wie Sie AEM-Site-Vorlagen abrufen.
* Wissen, wie Sie mit einer Vorlage eine neue Site erstellen.
* Erfahren haben, wie Sie die Vorlage von Ihrer neuen Site herunterladen, um sie für den Front-End-Entwickler bereitzustellen.

Fahren Sie aufbauend auf diesen Kenntnissen mit der AEM-Journey zur schnellen Site-Erstellung fort, indem Sie als Nächstes das Dokument [Einrichten der Pipeline](pipeline-setup.md) lesen. Darin erstellen Sie eine Front-End-Pipeline, um die Anpassung des Designs Ihrer Site zu verwalten.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, mit dem nächsten Teil der Journey zur schnellen Site-Erstellung fortzufahren, indem Sie das Dokument [Einrichten der Pipeline](pipeline-setup.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Aber sie sind nicht erforderlich, um die Journey fortzusetzen.

* [AEM-Standard-Site-Vorlage](https://github.com/adobe/aem-site-template-standard) – Dies ist das GitHub-Repository der AEM-Standard-Site-Vorlage.
* [Erstellen und Organisieren von Seiten](/help/sites-cloud/authoring/fundamentals/organizing-pages.md) – In diesem Handbuch wird beschrieben, wie Sie Seiten Ihrer AEM-Site verwalten, wenn Sie sie nach der Erstellung aus der Vorlage weiter anpassen möchten.
* [Arbeiten mit Paketen](/help/implementing/developing/tools/package-manager.md) – Pakete ermöglichen den Import und Export von Repository-Inhalten. In diesem Dokument wird erläutert, wie Sie mit Paketen in AEM 6.5 arbeiten. Dies gilt auch für AEMaaCS.
* [Dokumentation zur Site-Administration](/help/sites-cloud/administering/site-creation/create-site.md) – Weitere Informationen zu den Funktionen des Tools für die schnelle Site-Erstellung finden Sie in den technischen Dokumenten zur Site-Erstellung.
* [Erstellen oder Hinzufügen von Formularen zu einer AEM Sites-Seite](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) - Lernen Sie Schritt für Schritt Techniken und Best Practices für die Integration von Formularen in Ihre Website kennen und optimieren Sie Ihre digitalen Erlebnisse für eine maximale Wirkung.
