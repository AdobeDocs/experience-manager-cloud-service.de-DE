---
title: Erste Schritte mit dem Experience Modernization Agent für AEM-Authoring-Projekte
description: Erfahren Sie mehr über die spezifischen Einrichtungsschritte, die für AEM-Authoring-Projekte erforderlich sind, wenn Sie mit dem Experience Modernization Agent unter Verwendung der Experience Modernization Console beginnen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: a1b2c3d4-e5f6-4789-a012-3456789abcde
source-git-commit: df23c3a4c497943135f8719425225526ae14aa92
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 1%

---


# Erste Schritte mit dem Experience Modernization Agent für AEM-Authoring-Projekte {#getting-started-aem-authoring}

Bei AEM-Authoring-Projekten mit dem universellen Editor unterscheidet sich die Vorbereitung des Experience Modernization Agent vom standardmäßigen Edge Delivery-Ablauf. In diesem Dokument werden diese Einrichtungsunterschiede behandelt. Sobald die folgenden Schritte abgeschlossen sind, folgen Sie dem [ „Erste Schritte mit dem Experience ](getting-started.md)&quot;.

## Erstellen des Edge Delivery Services-Projekt-Repositorys {#create-repo}

1. Verwenden Sie das [`aem-block-collection-xwalk`](https://github.com/adobe-rnd/aem-block-collection-xwalk)-Repository als Vorlage (nicht das standardmäßige Edge Delivery Services-Textbaustein).
1. Befolgen Sie das [Tutorial zum universellen Editor](https://www.aem.live/developer/ue-tutorial), um Ihr Repository einzurichten.
   * Beenden, wenn Sie aufgefordert werden, eine Site in AEM zu erstellen.
1. Löschen Sie `paths.json` und übertragen Sie diese Änderung auf `main`.
1. Fügen Sie die [AEM Code Connector](https://github.com/apps/aem-code-connector/installations/select_target)-App zu Ihrem Repository hinzu.
   * Dadurch kann die Konsole Ihren Code überprüfen.

## Erstellen einer neuen Site in AEM {#create-site}

1. Wählen Sie in der AEM Sites-Konsole **Erstellen** > **Site aus Vorlage**.
1. Wählen Sie die **AEM-Site mit Edge Delivery Services-Vorlage**.
   * Sehen Sie es nicht aufgelistet? [Installieren der Vorlage.](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)
1. Behalten Sie **Namen** der Website (nicht den Titel) bei.
   * Der Site-Name wird als eindeutige Kennung verwendet.
   * Der Titel kann zur Anzeige geändert werden.
1. Klicken Sie auf **Erstellen**.
   * Sie werden zur Sites-Seite weitergeleitet.
   * Aktualisieren Sie die Seite, wenn die neue Site nicht sofort angezeigt wird.
1. Wenn Sie dies noch nicht beim [Einrichten des Repositorys“ getan haben, aktualisieren ](#create-repo) `fstab.yaml` so, dass es auf Ihren AEM-Host, Ihren Git-Eigentümer und Ihr Git-Repository verweist, und übertragen Sie diese Änderungen in `main`.
   * Anweisungen finden [ unter „Konfigurieren ](/help/implementing/cloud-manager/edge-delivery/configure-content-source.md) Inhaltsquelle“.

## Fahren Sie mit den standardmäßigen Schritten für erste Schritte fort {#continue}

Sobald die oben genannten Schritte abgeschlossen sind, können Sie mit dem standardmäßigen Erste-Schritte-Handbuch fortfahren, um mit der Migration Ihrer Inhalte zu beginnen.

![Content-Import](assets/content-import.png)

Führen Sie die folgenden Schritte im Standardhandbuch aus.

1. [Vorbereiten eines Edge Delivery GitHub-Repositorys](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#prepare-repo)
1. [Öffnen der Experience Modernization Console](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#open-console)
1. [Verbinden Ihres GitHub-Repositorys](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#connect-repo)
1. [Eingabeaufforderung starten](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#start-prompting)

![Inhalt importiert](assets/content-imported-aem-authoring.png)

Nachdem Sie diese Schritte zum Migrieren des Inhalts abgeschlossen haben, fahren Sie mit den folgenden Schritten fort.

## Inhalt überprüfen {#validate-content}

Validieren des Inhalts der ausgewählten Seite im Vorschaubereich. Alle Fehler werden durch Klicken auf die Schaltfläche **Fehler** angezeigt.
Setzen Sie Ihr Chat-Gespräch mit dem Agenten fort, um die Fehler zu beheben. Verwenden Sie die Funktion **Zum Chat hinzufügen**, um Fehlerbehebungen für bestimmte Elemente der Seite, Parser-Dateien oder Transformatordateien auszuwählen.

![Kontextueller Chat](assets/contextual-chat.png)

## Inhalt hochladen {#upload-content}

So laden Sie Ihre Inhalte in AEM hoch:

1. Stellen Sie sicher, dass Sie sich in der Ansicht **Inhalt** befinden, und klicken Sie auf die Schaltfläche **Inhalt hochladen** oben rechts.
1. Wählen **Dialogfeld „Inhaltspaket erstellen** die Seiten aus, die in das Paket aufgenommen werden sollen.
   * Geben Sie optional einen **Paketnamen** ein (standardmäßig den Website-Namen, wenn Sie das Feld leer lassen).
   * Verwenden Sie **Alle auswählen**, **Auswahl aufheben**, **Alle erweitern** oder **Alle reduzieren**, um die Liste zu verwalten.
1. Klicken Sie **Paket erstellen**.

   ![Inhaltspaket erstellen - Seiten auswählen und erstellen](assets/content-package.png)

1. Nachdem das Paket erstellt wurde, wird im Dialogfeld **Inhaltspaket hochladen** angezeigt, dass das Paket bereit ist.
   1. Sie können **Paket herunterladen**, um es lokal zu speichern, oder mit dem Hochladen fortfahren.
   1. Bestätigen **unter „In AEM hochladen** die **AEM-** und den **AEM-Host** (in den Projekteinstellungen vorausgefüllt).
      * Lassen Sie optional **Bilder hochladen** aktiviert, um Bilder einzuschließen.
   1. Klicken Sie **In AEM hochladen**.

   ![Paket kann in AEM hochgeladen oder heruntergeladen werden](assets/upload-package-start.png)

1. Das Dialogfeld zeigt den Upload-Fortschritt an, während Seiten und Assets an AEM gesendet werden. Nach Abschluss des Uploads werden eine Erfolgsmeldung und das Upload-Protokoll angezeigt. Klicken Sie **Schließen**, um das Dialogfeld zu schließen.

   ![Upload-Fortschritt und -Abschluss in AEM](assets/upload-package-complete.png)

Ihr importierter Inhalt befindet sich jetzt in AEM. Fahren Sie mit [Push-Code-](getting-started.md#push-code-changes)) in den ersten Schritten fort.

## Zusätzliche Ressourcen {#additional-resources}

* [Erste Schritte mit dem Experience Modernization Agent](getting-started.md) - Vollständiger Workflow, einschließlich Konsole, Eingabeaufforderung, Upload und Vorschau
* [Experience Modernization Console](console.md) - Konsolenreferenz
* [Tutorial zum universellen Editor](https://www.aem.live/developer/ue-tutorial) - Einrichten eines AEM-Authoring- und universellen Editor-Projekts
* [`aem-block-collection-xwalk`](https://github.com/adobe-rnd/aem-block-collection-xwalk) - Vorlagen-Repository für AEM-Authoring- und universelle Editor-Projekte
