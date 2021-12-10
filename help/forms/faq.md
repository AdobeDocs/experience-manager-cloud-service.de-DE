---
title: 'Häufig gestellte Fragen zu Forms as a Cloud Service '
description: Häufig gestellte Fragen zu Forms as a Cloud Service
contentOwner: khsingh
exl-id: 0b14b680-7da5-4e0b-bd6a-c379d148f9d7
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 100%

---

# Häufig gestellte Fragen {#frequently-asked-questions}

* **Kann ich den Code-Editor zum Erstellen von Regeln verwenden?**
Sie können die Regeln mit dem Visual-Editor erstellen. Der Code-Editor ist in [!DNL Forms] as a Cloud Service nicht verfügbar. Wenn Ihr adaptives Formular Regelskripte verwendet, die mit dem Code-Editor entwickelt wurden, konvertieren Sie Ihre Code-Skripte mithilfe des [Migrations-Dienstprogramms](migrate-to-forms-as-a-cloud-service.md) in benutzerdefinierte Funktionen. Sie können benutzerdefinierte Funktionen mit dem Visual-Editor auf die gleiche Weise bearbeiten, wie Sie es vom Code-Editor gewohnt sind.

* **Kann ich ein XFA-basiertes adaptives Formular auf Cloud Service-Instanzen erstellen?**
Ja, Sie können ein XFA-basiertes adaptives Formular in der Cloud Service-Instanz erstellen. Die Unterstützung für XFA-basierte adaptive Formulare ist jedoch nicht für das AEM Forms as a Cloud Service SDK (lokale Entwicklungsumgebung) verfügbar. Wenn Sie XFA-basierte adaptive Formulare mit dem AEM Forms as a Cloud Service SDK verwenden möchten, kontaktieren Sie den Adobe Support mit Informationen zu Ihrem Nutzungsszenario und spezifischen Anforderungen.

<!-- * **Can I use an XDP as a Document of Record (DoR) template? Is Forms Designer included in AEM Forms as a Cloud Service license?** 

  Yes, you can use an XDP as a Document of Record template on Cloud Service instances. However, support to use XDP as a Document of Record template is not available for AEM Forms as a Cloud Service SDK (Local development environment). -->

* **Kann ich Inhalte von On-Premise- oder [!DNL Adobe-Managed Services]-Umgebungen zu einer [!DNL Forms] as a Cloud Service-Umgebung migrieren?**
Ja, Sie können benutzerdefinierten Code, Inhalte und Assets von On-Premise- oder [!DNL Adobe-Managed Services]-Umgebungen in eine [!DNL Forms] as a Cloud Service-Umgebung migrieren. Detaillierte Anweisungen finden Sie unter [Migrieren zu Forms as a Cloud Service](migrate-to-forms-as-a-cloud-service.md).

<!-- You can use package manager or Experience Manager UI to [export and import Forms and related assets](import-export-forms-templates.md), use the migration utility to make your existing assets compatible with [!DNL Forms] as a Cloud Service, use the [Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#best-practices-analyzer) tool to find the features and APIs that require changes and updated before migration, and use the [Content Transfer Tools](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/home.html) to move your custom code without refactoring it. -->

* **Wo erhalte ich die [!DNL Java™]-API-Referenzdokumentation zu AEM [!DNL Forms] as a Cloud Service?**
Sie können die Referenzdokumentation zur Java™-API von [!DNL Maven Central Repository] herunterladen. Zum Herunterladen:
   1. Öffnen Sie das [[!DNL Maven Central Repository]](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api).
   1. Suchen und öffnen Sie die Seite mit der neuesten SDK-Version für [!DNL Experience Manager Forms].
   1. Klicken Sie auf die Option „Alle anzeigen“, um alle Dateien anzuzeigen.
   1. Laden Sie die Datei `aem-forms-sdk-api-<version>-javadocs`.jar herunter und extrahieren Sie sie.
   1. Öffnen Sie die Datei „index.html“, um die API-Referenzdokumentation aufzurufen.

* **Wo erhalte ich die [!DNL JavaScript™]-API-Referenzdokumentation für adaptive Formulare?**
Sie können die [!DNL JavaScript™]-API-Referenzdokumentation vom [!DNL  Maven Central Repository] herunterladen. Zum Herunterladen:
   1. Öffnen Sie [[!DNL Maven Central Repository]](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api).
   1. Suchen und öffnen Sie die Seite mit der neuesten SDK-Version für [!DNL Experience Manager Forms].
   1. Klicken Sie auf die Option „Alle anzeigen“, um alle Dateien anzuzeigen.
   1. Laden Sie die `aem-forms-sdk-api-<version>-jsdoc.jar` herunter und extrahieren Sie sie.
   1. Öffnen Sie die Datei „index.html“, um die API-Referenzdokumentation aufzurufen.

* **Kann ich vorhandene Designs und Vorlagen weiterverwenden?**
Ja, Sie können mit AEM 6.4 Forms und AEM 6.5 Forms erstellte Designs weiterhin verwenden, nachdem Sie diese Designs mithilfe des [Migrationsdienstprogramms](migrate-to-forms-as-a-cloud-service.md) in [!DNL AEM Forms] as a Cloud Service übertragen haben.

   Außerdem können Sie ein Projekt auf der Grundlage des [!DNL AEM Forms] as a Cloud Service [-Archteyps](setup-local-development-environment.md#forms-cloud-service-local-development-environment) erstellen und die darin enthaltenen Beispielvorlagen und Designs verwenden.

* **Kann ich schemakonforme Daten generieren?**
Ja, Sie können adaptive Formulare erstellen, um schemakonforme Daten zu generieren.

<!-- * **Can I pass custom parameters to the prefill service?**
Custom parameters are planned for an upcoming release. -->

* **Kann ich Caching für geschützten Content aktivieren?**
Das Caching geschützter Inhaltsfunktionen ist standardmäßig deaktiviert. Um die Funktion zu aktivieren, folgen Sie den Anweisungen unter [Caching von geschütztem Content](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=de).

* **Ich habe ein lokalisiertes adaptives Formular, aber die lokalisierte Version wird nicht gerendert. Was könnte die Ursache sein, und wie kann man sie beheben?**

   Die URL-Konvention von lokalisierten adaptiven Formularen unterstützt nun die Angabe eines Gebietsschemas in der URL. Die neue URL-Konvention ermöglicht das Caching lokalisierter Formulare in einem Dispatcher oder CDN. Verwenden Sie in der Cloud Service-Umgebung, um die lokalisierte Version eines adaptiven Formulars anzufordern, das URL-Format `http://host:port/content/forms/af/<afName>.<locale>.html` statt `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe empfiehlt die Verwendung von Dispatcher- oder CDN-Caching. Auf diese Weise wird das Rendern vorausgefüllter Formulare beschleunigt.

* **Ich habe ein adaptives Formular aktualisiert. Warum ist die aktualisierte Version für Kunden nicht verfügbar?**
Standardmäßig aktualisiert CDN den Cache alle 5 Minuten. Warten Sie 5 Minuten und überprüfen Sie dann erneut die Verfügbarkeit der aktualisierten Version.

* **Kann ich den Unterschriftsschritt in einem adaptiven Formular verwenden, um Browser-basiertes Unterschreiben bereitzustellen?**
Nein, der Unterschriftsschritt ist in [!DNL Forms] as a Cloud Service nicht verfügbar. Entfernen Sie daher den Unterschriftsschritt aus Ihren adaptiven Formularen. Anstelle des Unterschriftsschritts lassen Sie zu, dass Benutzer ein adaptives Formular nach dem Senden signieren. So können Sie weiterhin Browser-basiertes Unterschreiben bereitstellen.

* **Kann ich den Überprüfungsschritt in einem adaptiven Formular verwenden?**
Nein, der Überprüfungsschritt ist in [!DNL Forms] as a Cloud Service nicht verfügbar. Entfernen Sie den Überprüfungsschritt aus Ihren vorhandenen adaptiven Formularen, bevor Sie sie in eine Cloud Service-Umgebung verschieben.

* **Kann ich zu einem adaptiven Formular Diagramme hinzufügen?**
Ja, Sie können zu adaptiven Formularen Diagramme hinzufügen. Adaptive Formulare beinhalten eine Diagrammkomponente. Darüber können Sie Diagramme in adaptive Formulare einfügen.

* **Kann ich ein Formulardatenmodell mit einem relationalen Datenbankmodell verbinden?**
Sie können ein Formulardatenmodell mit [!DNL RESTful web services], [!DNL SOAP-based web services], [!DNL OData services] und Experience Manager-Benutzerprofilen als Datenquelle verbinden. Die Verbindung eines Formulardatenmodells mit einer relationalen Datenbank wird nicht unterstützt.

* **Kann ich benutzerdefinierte Zertifikate zur Authentifikation mit dem Formulardatenmodell verwenden?**
Das Formulardatenmodell stellt keine Methode zur Verwendung benutzerdefinierter Zertifikate für die Authentifizierung bereit. Die benutzerdefinierten Zertifikate wie x509 und 2-Wege-SSL werden daher nicht unterstützt.

* **Kann ich Übermittlungsaktionen des Formularportals für adaptive Formulare verwenden?**

   Sie können Ihr vorhandenes adaptives Formular dahingehend ändern, dass die Übermittlungsaktionen [An REST-Endpunkt übermitteln](configuring-submit-actions.md#submit-to-rest-endpoint), [E-Mail senden](configuring-submit-actions.md#send-email), [Senden mit Formulardatenmodell](configuring-submit-actions.md#submit-using-form-data-model) und [AEM-Workflow aufrufen](configuring-submit-actions.md#invoke-an-aem-workflow) verwendet werden. Formularportal und Formularportal-Übermittlungsaktionen sind noch nicht verfügbar. Behalten Sie die monatlichen Versionshinweise hinsichtlich einer Verfügbarkeit dieser Funktionen im Auge.

* **Kann ich die [!DNL AEM Forms]-Mobile-App mit [!DNL AEM Forms] as a Cloud Service verwenden?**

   Adaptive Formulare bieten ein responsives Design. Diese Formulare ändern Erscheinungsbild, Design und Interaktivität je nach zugrunde liegendem Gerät. Sie können adaptive Formulare weiter auf Mobilgeräten verwenden, während Sie die monatlichen Versionshinweise hinsichtlich einer Verfügbarkeit der Funktionen mitverfolgen.

* **Welche Funktionen sind in der ersten GA-Version nicht enthalten?**
Das Formularportal, die [!DNL AEM Forms]-Mobile-App, die Integration mit Adobe Analytics und die Integration mit Adobe Target sind nicht Teil der ersten GA-Version. Informationen zu neuen Funktionen finden Sie in den monatlichen Versionshinweisen.
