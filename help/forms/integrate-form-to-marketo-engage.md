---
Title: How to Integrate Marketo Engage with AEM Forms?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 74cd25f9-1ee1-4f3f-8e02-8714071e7c86
source-git-commit: e46c5afac945620cc44e9064956848acecc786bf
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 7%

---

# Integrieren von Marketo Engage mit AEM Forms

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

Durch die Integration von AEM Forms mit [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home) können Anwender die Funktionen von Marketo Engage nutzen, um Geschäftslogiken aus erfassten Daten zu erstellen und Workflows zu automatisieren, einschließlich intelligenter Kampagnen und E-Mail-Automatisierung. Das konfigurierte Formular kann erfasste Daten zur Verarbeitung an Marketo Engage senden.

## Vorteile der Integration von Marketo Engage in Formulare

Im Folgenden finden Sie einige Vorteile beim Verbinden eines AEM-Formulars mit Adobe Marketo Engage:

* **Vereinfachte Integration**: Durch die Verbindung von Formularen mit Marketo Engage entfällt die Notwendigkeit, ein separates Formulardatenmodell zu erstellen. Der Integrationsprozess ist unkompliziert und benutzerfreundlich.
* **Automatisierte Datenerfassung**: Dies hilft bei der automatischen Erfassung von Formularübermittlungen und ihrer Speicherung in Marketo, wodurch die manuelle Dateneingabe entfällt und Fehler reduziert werden.

* **Lead-Management**: Es optimiert die Lead-Management-Prozesse, indem Formularübermittlungen direkt in Ihre Marketing-Datenbank integriert werden, was eine bessere Nachverfolgung und Pflege von Leads ermöglicht.

* **Verbesserte Kampagnenleistung**: Sie verwendet Formulardaten zur Analyse und Optimierung von Marketing-Kampagnen, wodurch die Gesamtleistung und der ROI (Return on Investment) verbessert werden.

* **Analytics und Reporting**: Dies erleichtert den Zugriff auf zuverlässige Analyse- und Reporting-Tools wie Munchkin in Marketo, um die Effektivität von Formularen und Kampagnen zu messen.

* **Automatisierung von Folgemaßnahmen**: Dies hilft bei der Automatisierung von Folgenachrichten und Workflows, die durch Formularübermittlungen ausgelöst werden, und sorgt für eine zeitnahe Kommunikation mit Leads.

## Die wichtigsten Vorteile der Verwendung von AEM Forms gegenüber alternativen Formularlösungen

In der folgenden Tabelle sind die Gründe aufgeführt, warum Sie AEM Forms gegenüber anderen alternativen Formularlösungen bevorzugen:

| **Funktion** | **AEM Forms** | **Andere Formularlösungen** |
|-------------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------|
| **Anpassungen** | Ermöglicht das Hinzufügen spezifischer benutzerdefinierter Funktionen, das Anpassen von Formularaktionen und das Ändern des Feldverhaltens, um Formularinteraktionen und komplexe Workflows zu verbessern | Keine Anpassungsunterstützung |
| **Regeleditor** | Unterstützt einen integrierten Regeleditor zum Hinzufügen von Logiken und Bedingungen. | Kein Regeleditor |
| **Layout-Optionen** | Unterstützt mehrere Layout-Optionen | Eingeschränkte Layout-Optionen |
| **Vorbefüllungs-Service** | Bietet einen Vorbefüllungs-Service zum automatischen Ausfüllen von Formulardaten. | Kein Vorbefüllungs-Service verfügbar |
| **Einbetten in Sites** | Kann mit iFrame in Sites eingebettet werden | Kann nicht mit iFrame in Sites eingebettet werden |
| **Einfache Integration mit Sites** | Keine zusätzlichen Kenntnisse erforderlich. AEM Forms verwendet dieselben Kenntnisse wie Sites | Zusätzliches Lernen kann erforderlich sein |
| **Datenübermittlung** | Kann Daten an verschiedene Plattformen senden und bietet mehrere Connectoren, z. B. „Mit SharePoint verbinden“, „Mit OneDrive verbinden“, „Mit Salesforce verbinden“ und mehr. | Kann Daten an eingeschränkte Connectoren senden, z. B. an Salesforce |

## Überlegungen zur Integration von Marketo Engage in Formulare

Überlegungen zur Integration von Marketo Engage mit AEM Forms:

* AEM unterstützt nur die Personen(Leads)-Datenbank unter den verschiedenen Marketo-Datenbanken.
* Marketo ermöglicht die [Erstellung von 10 benutzerdefinierten Objekten](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-custom-objects/add-marketo-custom-object-fields) als benutzerdefinierte Objekte, um spezielle Daten über die Standardfelder hinaus in Leads zu speichern und so individuelle Geschäftsanforderungen zu unterstützen.
* AEM kann nur auf benutzerdefinierte Objekte zugreifen, wenn sie mit der Lead-Datenbank verknüpft sind

## Voraussetzungen für die Integration von Marketo Engage in Formulare

Im Folgenden finden Sie die Voraussetzungen für die Verbindung von Marketo Engage mit AEM Forms:

* Gültige Adobe Marketo Engage-Lizenz
* Eine funktionierende Instanz von Marketo Engage zum [Abrufen der Client-ID und des Client-](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/additional-integrations/create-a-custom-service-for-use-with-rest-api)), um eine Cloud-Konfiguration zu erstellen.

## Erstellen einer Cloud-Service-Konfiguration zum Verbinden von AEM Forms (Adaptive Forms) mit Marketo Engage

![Arbeitsablauf](/help/forms/assets/workflow-marketo-1.png)

>[!VIDEO](https://video.tv.adobe.com/v/3442865/engage-marketo-aem-forms-aem)

Die Cloud-Konfiguration verbindet Ihre Experience Manager-Instanz mit der Adobe Marketo Engage-Instanz. Führen Sie die folgenden Schritte aus, um eine Marketo Engage-Cloud-Konfiguration zu erstellen:

1. Navigieren Sie **Tools** > **Cloud Service** > **Marketo Engage**.

   ![Marketo Engage](/help/forms/assets/marketo-engage.png)

2. Öffnen Sie einen Ordner zum Hosten der Konfiguration und klicken Sie auf **Erstellen**. Das Fenster **Marketo Engage-Konfiguration erstellen** wird angezeigt.

   >[!NOTE]
   >
   > Sie können auch [Ordner für Cloud Service-Konfigurationen konfigurieren](/help/forms/configure-data-sources.md#configure-folder-for-cloud-service-configurations).

3. Geben Sie den **Titel** der Konfiguration und die Anmeldeinformationen für die Verbindung mit dem Service an. Sie können die Authentifizierungsdaten über das Adobe Marketo Engage-Dashboard abrufen:
   * **Client-ID** und **Client-Geheimnis** sind unter **Admin** > **Integration** > **LaunchPoint** verfügbar, indem Sie den benutzerdefinierten Service auswählen und auf **Details anzeigen** klicken.
   * **Identitäts-URL** ist unter **Admin** > **Integration** > **Web-Services** **Identity** im Abschnitt **REST-API** verfügbar.

4. Klicken Sie auf **Verbinden**.  Bei erfolgreicher Verbindung erscheint die Meldung `Authentication Successful`.
5. Klicken Sie **[!UICONTROL Erstellen]**, um die Cloud-Konfigurationseinstellungen zu speichern.

![Marketo Engage-Cloud-Konfiguration](/help/forms/assets/marketo-engage-cloud-configuration.png)

Jetzt können Sie die erstellte Cloud Service-Konfiguration verwenden, um die Marketo Engage-Datenquelle mit einem adaptiven Formular zu verbinden.

## Nächster Schritt

Sie haben die Cloud-Service-Konfiguration erstellt, um Adobe Marketo Engage mit AEM Forms zu integrieren. Jetzt können Sie Folgendes integrieren:
* [Neues adaptives Formular mit Marketo Engage](/help/forms/integrate-adaptive-form-with-marketo-engage.md)
* [Vorhandenes adaptives Formular mit Marketo Engage](/help/forms/use-marketo-engage-data-source-in-form.md)

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}
