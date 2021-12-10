---
title: Verwenden des AEM-Übersetzungs-Workflows zum Lokalisieren von adaptiven Formularen und Datensatzdokumenten
seo-title: Using AEM translation workflow to localize Adaptive Forms and Document of Record
description: Hier erfahren Sie, wie Sie AEM-Übersetzungs-Workflows zum Lokalisieren von adaptiven Formularen und Datensatzdokumenten verwenden.
seo-description: Learn to use AEM translation workflows to localize Adaptive Forms and Document of Record.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 100%

---


# Verwenden des AEM-Übersetzungs-Workflows zum Lokalisieren von adaptiven Formularen und Datensatzdokumenten {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Mit lokalisierten Formularen können Sie eine größere Zielgruppe über Ländergrenzen hinweg ansprechen. Mit den Adobe Experience Manager-Übersetzungs-Workflows können Sie adaptive Formulare und die entsprechenden Datensatzdokumente lokalisieren. Sie können zum Lokalisieren adaptiver Formulare **maschinelle Übersetzung** nutzen oder **Übersetzer** beauftragen.

In diesem Artikel wird die Vorgehensweise zum Einsetzen des AEM-Übersetzungs-Workflows in Verbindung mit adaptiven Formularen und Datensatzdokumenten erläutert.

## Lokalisieren eines adaptiven Formulars und Datensatzdokuments mithilfe maschineller Übersetzung {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

Der Service für maschinelle Übersetzung übersetzt sofort Inhalte Ihrer adaptiven Formulare und Datensatzdokumente. [!DNL AEM Forms] ist für die Verwendung einer Testversion von [!DNL Microsoft Translator] für maschinelle Übersetzung vorkonfiguriert. Führen Sie zum Aktivieren des Service für Ihre adaptiven Formulare und Datensatzdokumente folgende Schritte durch:

1. Wählen Sie auf der Benutzeroberfläche von [!DNL AEM Forms] ein Formular aus und tippen Sie auf die Option **Wörterbuch hinzufügen**.
1. Wählen Sie auf dem Bildschirm **Wörterbuch zum Übersetzungsprojekt hinzufügen** die Option **Neues Übersetzungsprojekt erstellen** oder **Zu vorhandenem Übersetzungsprojekt hinzufügen**.
1. Geben Sie im Feld **Projekttitel** den Titel an. Beispiel: `Government Reference Site - German locale.`
1. Geben Sie im Feld **Zielsprachen** ein Gebietsschema an (beispielsweise `German(de)`) und klicken Sie auf **Fertig**. Sie können mehrere Gebietsschemas angeben. Das Formular wird in alle im Feld **Zielsprachen** angegebenen Gebietsschemas übersetzt.
1. Klicken Sie im Dialogfeld „Wörterbuch hinzugefügt“ auf **Projekte öffnen**. Öffnen Sie auf dem Bildschirm „Projekte“ das neu erstellte Projekt.
1. Klicken Sie unten auf der Kachel **Übersetzungszusammenfassung** auf die **Auslassungspunkte**. Der Bildschirm „Übersetzungszusammenfassung“ wird geöffnet.
1. Klicken Sie am oberen Rand des Bildschirms **Übersetzungszusammenfassung** auf das Symbol **Bearbeiten**. Öffnen Sie die Registerkarte **Übersetzung** und wählen Sie auf dem Bildschirm **Übersetzungsmethode** die Option „Maschinelle Übersetzung“. Wählen Sie den entsprechenden **Übersetzungsanbieter** und die entsprechende **Cloudkonfiguration**. Klicken Sie am oberen Rand des Bildschirms auf das Symbol **Fertig**.
1. Klicken Sie auf der Kachel **Übersetzungsauftrag** auf das Symbol ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und dann auf **Start**. Der Status der Kachel ändert sich in „Entwurf“. Bei Fertigstellung der Übersetzung ändert sich der Status in **Bereit für Überprüfung**. Aktualisieren Sie die Seite nach einigen Minuten und überprüfen Sie den Status.
1. Nachdem sich der Status auf der Kachel **Übersetzungsauftrag** in **Bereit für Überprüfung** geändert hat, öffnen Sie das Formular in einem Browserfenster. Eine lokalisierte Version des Formulars wird angezeigt.

   >[!NOTE]
   >
   >* Stellen Sie vor dem Öffnen der lokalisierten Version des Formulars im Browserfenster sicher, dass das Gebietsschema des Browsers so eingestellt ist, dass es mit dem Gebietsschema des Formulars übereinstimmt. Wenn beispielsweise das Formular in die Sprache Deutsch(de) übersetzt wird, stellen Sie für das Gebietsschema des Browsers „Deutsch(de)“ ein.
   >* Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left – von rechts nach links). Zum Beispiel Hebräisch.


   Zusammen mit dem adaptiven Formular wird ebenfalls das automatisch generierte Datensatzdokument lokalisiert.

   Weitere Informationen zu Einstellungen und Konfigurationen für Datensatzdokumente finden Sie unter:

[Konfiguration von Vorlagen für Datensatzdokumente](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

[Einstellungen für Datensatzdokumente](generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Passen Sie die Branding-Informationen des Datensatzdokuments an](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) und stellen Sie sicher, dass für das Browsergebietsschema die Sprache eingestellt ist, für die Sie das adaptive Formular mithilfe maschineller Übersetzung lokalisiert haben. Das Browsergebietsschema hilft beim Lokalisieren der Branding-Informationen im Datensatzdokument.
1. Um das lokalisierte Datensatzdokument anzuzeigen, tippen Sie auf „Vorschau generieren“. Die PDF-Datensatzdokumentdatei wird erstellt und in einem neuen Browser-Tab geöffnet.

<!-- ## Localizing an Adaptive Form and its Document of Record using Human Translation {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

In Human translation the content is sent to a translation provider and translated by professional translators. When complete, the translated content is returned and imported into AEM. When your translation provider is integrated with AEM, content is automatically sent between AEM and the translation provider.

For translation, a dictionary containing files in XLIFF format is shared with the professional translators. The dictionary includes a separate XLIFF file for each locale. Each XLIFF file contains text that will be displayed to the end users and placeholders for the corresponding localized text.

Perform the following steps to localize a form and its Document of Record using Human Translators:

1. [Connect AEM with your translation service provider](/help/sites-administering/tc-tic.md) and [create translation integration framework configurations](/help/sites-administering/tc-tic.md).

1. [Associate the pages of your language master](/help/sites-administering/tc-tic.md) with the translation service and framework configurations.

1. [Identify the type of content](/help/sites-administering/tc-rules.md) to translate.

1. [Prepare the content for translation](/help/sites-administering/tc-prep.md) by authoring the language master and creating the root pages of language copies.

1. [Create translation projects](/help/sites-administering/tc-manage.md) to gather the content to translate and to prepare the translation process.

1. Use the translation projects to [manage the content translation process](/help/sites-administering/tc-manage.md).

>[!NOTE]
>
>* Adaptive Form components do not support right to left (RTL) languages. For example, Hebrew.
> -->

