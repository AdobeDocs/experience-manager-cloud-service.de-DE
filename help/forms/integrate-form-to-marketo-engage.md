---
Title: How to Integrate Marketo Engage with AEM Forms?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 6%

---


# Integrieren von Marketo Engage mit AEM Forms

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

Durch die Integration von AEM Forms in [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home) können Benutzer die Funktionen von Marketo Engage nutzen, um Geschäftslogik aus erfassten Daten zu erstellen und Workflows zu automatisieren, einschließlich Smart-Kampagnen und E-Mail-Automatisierung. Das konfigurierte Formular kann erfasste Daten zur Verarbeitung an Marketo Engage senden.

## Vorteile der Integration von Marketo Engage in Formulare

Im Folgenden finden Sie einige Vorteile beim Verbinden eines AEM Formulars mit Adobe Marketo Engage:

* **Vereinfachte Integration**: Durch das Verbinden von Formularen mit Marketo Engage entfällt die Notwendigkeit, ein separates Formulardatenmodell zu erstellen. Der Integrationsprozess ist einfach und benutzerfreundlich.
* **Automatisierte Datenerfassung**: Dies hilft beim automatischen Erfassen und Speichern von Formularübermittlungen in Marketo, wodurch manuelle Dateneingabe vermieden und Fehler reduziert werden.

* **Lead-Management**: Dies optimiert Lead-Management-Prozesse, indem Formularübermittlungen direkt in Ihre Marketing-Datenbank integriert werden, was eine bessere Verfolgung und Pflege von Leads ermöglicht.

* **Verbesserte Kampagnenleistung**: Es werden Formulardaten verwendet, um Marketing-Kampagnen zu analysieren und zu optimieren, wodurch die Gesamtleistung und der ROI (Return on Investment) verbessert werden.

* **Analyse und Berichterstellung**: Dies hilft beim Zugriff auf robuste Analyse- und Reporting-Tools wie Munchkin innerhalb von Marketo, um die Effektivität von Formularen und Kampagnen zu messen.

* **Folgenautomatisierung**: Dies hilft bei der Automatisierung von Folgenachrichten und Workflows, die durch Formularübermittlungen ausgelöst werden, und gewährleistet eine zeitnahe Kommunikation mit Leads.

## Wesentliche Vorteile der Verwendung von AEM Forms gegenüber alternativen Formularlösungen

In der folgenden Tabelle werden die Gründe für die Wahl von AEM Forms anstelle anderer alternativer Formularlösungen erläutert:

| **Funktion** | **AEM Forms** | **Andere Formularlösungen** |
|-------------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------|
| **Anpassungen** | Ermöglicht das Hinzufügen bestimmter benutzerdefinierter Funktionen, das Anpassen von Formularaktionen und das Ändern von Feldverhalten, um Formularinteraktionen und komplexe Workflows zu verbessern | Keine Unterstützung bei der Anpassung |
| **Regeleditor** | Unterstützt einen integrierten Regeleditor zum Hinzufügen von Logik und Bedingungen. | Keine Unterstützung des Regeleditors |
| **Layout-Optionen** | Mehrere Layoutoptionen werden unterstützt | Eingeschränkte Layoutoptionen |
| **Vorbefüllungs-Dienst** | Bietet einen Vorbefüllungs-Dienst zum automatischen Ausfüllen von Formulardaten. | Kein Vorbefüllungs-Service verfügbar |
| **Einbetten in Sites** | Kann mit iFrame in Sites eingebettet werden | Kann nicht mit iFrame in Sites eingebettet werden |
| **Einfachere Integration mit Sites** | Kein zusätzliches Lernen erforderlich; AEM Forms verwendet dieselben Fähigkeiten wie Sites | Möglicherweise ist zusätzliches Lernen erforderlich |
| **Datenübermittlung** | Kann Daten an verschiedene Plattformen senden und bietet mehrere Connectoren, z. B. Verbindung zu SharePoint, Verbindung zu OneDrive, Verbindung zu Salesforce und mehr. | Kann Daten an begrenzte Connectoren senden, z. B. an Salesforce |

## Überlegungen zur Integration von Marketo Engage in Formulare

Bei der Integration von Marketo Engage mit AEM Forms sind einige Aspekte zu beachten:

* AEM unterstützt nur die People(Leads)-Datenbank in den verschiedenen Marketo-Datenbanken.
* Marketo ermöglicht die [ Erstellung von 10 benutzerdefinierten Objekten](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-custom-objects/add-marketo-custom-object-fields) als benutzerdefinierten Objekten, um spezialisierte Daten über die Standardfelder in Leads hinaus zu speichern und so individuelle Geschäftsanforderungen zu erfüllen.
* AEM können nur auf benutzerdefinierte Objekte zugreifen, wenn sie mit der Lead-Datenbank verknüpft sind

## Voraussetzungen für die Integration von Marketo Engage in Formulare

Nachfolgend finden Sie die Voraussetzungen für die Verbindung von Marketo Engage mit AEM Forms:

* Eine gültige Adobe Marketo Engage-Lizenz
* Eine funktionierende Instanz der Marketo Engage zum [Abrufen der Client-ID und des Client-Geheimnisses](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/additional-integrations/create-a-custom-service-for-use-with-rest-api), um eine Cloud-Konfiguration zu erstellen.

## Erstellen Sie eine Cloud Service-Konfiguration, um AEM Forms (Adaptive Forms) mit Marketo Engage zu verbinden.

![Arbeitsablauf](/help/forms/assets/workflow-marketo-1.png)

Die Cloud-Konfiguration verbindet Ihre Experience Manager-Instanz mit der Adobe Marketo Engage-Instanz. Führen Sie die folgenden Schritte aus, um eine Marketo Engage-Cloud-Konfiguration zu erstellen:

1. Navigieren Sie zu **Tools** > **Cloud Service** > **Marketo Engage**.

   ![Marketo Engage](/help/forms/assets/marketo-engage.png)

1. Öffnen Sie einen Ordner zum Hosten der Konfiguration und klicken Sie auf **Erstellen**. Das Fenster **Marketo Engage-Konfiguration erstellen** wird angezeigt.

   >[!NOTE]
   >
   > Sie können auch den Ordner [für Cloud Service-Konfigurationen konfigurieren](/help/forms/configure-data-sources.md#configure-folder-for-cloud-service-configurations).

1. Geben Sie den **Titel** der Konfiguration und die Anmeldeinformationen für die Verbindung mit dem Dienst an. Sie können die Authentifizierungsberechtigungen vom Adobe Marketo Engage-Dashboard abrufen:
   * **Client-ID** und **Client-Geheimnis** sind in **Admin** > **Integration** > **LaunchPoint** verfügbar, indem Sie den benutzerdefinierten Dienst auswählen und auf **Details anzeigen** klicken.
   * **Identitäts-URL** ist in **Admin** > **Integration** > **Web Services** als **Identität** im Abschnitt **REST-API** verfügbar.

1. Klicken Sie auf **Verbinden**.  Bei erfolgreicher Verbindung erscheint die Meldung `Authentication Successful`.
1. Klicken Sie auf **[!UICONTROL Erstellen]** , um die Cloud-Konfigurationseinstellungen zu speichern.

![Marketo Engage Cloud-Konfiguration](/help/forms/assets/marketo-engage-cloud-configuration.png)

Jetzt können Sie die erstellte Cloud Service-Konfiguration verwenden, um die Marketo Engage-Datenquelle mit einem adaptiven Formular zu verbinden.

## Nächster Schritt

Sie haben die Cloud Service-Konfiguration erstellt, um Adobe Marketo Engage in AEM Forms zu integrieren. Jetzt können Sie Folgendes integrieren:
* [Neues adaptives Formular mit Marketo Engage](/help/forms/integrate-adaptive-form-with-marketo-engage.md)
* [Vorhandenes adaptives Formular mit Marketo Engage](/help/forms/use-marketo-engage-data-source-in-form.md)

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}



