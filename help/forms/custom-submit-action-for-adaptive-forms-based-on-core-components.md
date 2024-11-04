---
title: Wie erstelle ich eine benutzerdefinierte Übermittlungsaktion für ein adaptives Formular basierend auf Kernkomponenten?
description: Erfahren Sie, wie Sie eine benutzerdefinierte Übermittlungsaktion für eine adaptive Forms erstellen, um Daten zu verarbeiten, bevor Sie sie mit der benutzerdefinierten Übermittlungsaktion senden.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Intermediate
source-git-commit: b1d5e210d84ad1443b30e4b166f52da51a182b09
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 24%

---


# Erstellen einer benutzerdefinierten Sendeaktion für adaptive Forms (Kernkomponenten)

Mit einer Übermittlungsaktion können Benutzer das Ziel für die Daten auswählen, die aus einem Formular erfasst werden, und zusätzliche Funktionen definieren, die bei der Formularübermittlung ausgeführt werden. AEM Formular unterstützt mehrere vordefinierte [Übermittlungsaktionen (OOTB)](/help/forms/configure-submit-actions-core-components.md), z. B. das Senden einer E-Mail oder das Speichern von Daten an SharePoint oder OneDrive.

Sie können auch eine benutzerdefinierte Sendeaktion erstellen, um Funktionen hinzuzufügen, die nicht in den vordefinierten [Optionen](/help/forms/configure-submit-actions-core-components.md#select-and-configure-a-submit-action-for-an-adaptive-form-select-and-configure-submit-action) enthalten sind. Integrieren Sie beispielsweise die Formulardaten in eine Drittanbieteranwendung oder eine personalisierte SMS-Benachrichtigung, die auf der Benutzereingabe basiert.

<!-- ![Custom Submit Image](/help/forms/assets/custom-submit-action-hero-image.png)
-->

## Voraussetzungen

Bevor Sie mit der Erstellung Ihrer ersten benutzerdefinierten Übermittlungsaktion für Adaptive Forms beginnen, stellen Sie Folgendes sicher:

* **Nur-Text-Editor (IDE)**: Obwohl jeder Nur-Text-Editor funktionieren kann, bietet eine integrierte Entwicklungsumgebung (IDE) wie Microsoft Visual Studio Code erweiterte Funktionen zur einfacheren Bearbeitung.

* **Git**: Dieses Versionskontrollsystem ist für die Verwaltung von Codeänderungen erforderlich. Wenn Sie es nicht installiert haben, laden Sie es von https://git-scm.com herunter.

## Erstellen der ersten benutzerdefinierten Sendeaktion für das Formular

Das folgende Diagramm zeigt die Schritte zum Erstellen einer benutzerdefinierten Übermittlungsaktion für ein adaptives Formular:

![Workflow für benutzerdefinierte Übermittlungsaktionen](/help/forms/assets/custom-submit-action-workflow.png){width=50%, height-50%}

### AEM as a Cloud Service Git-Repository klonen.

1. Öffnen Sie die Befehlszeile und wählen Sie einen Ordner zum Speichern des AEM as a Cloud Service-Repositorys aus, z. B. `/cloud-service-repository/`.

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```
   **Wo finden Sie diese Informationen?**

   Eine schrittweise Anleitung zum Auffinden dieser Details finden Sie im Adobe Experience League-Artikel [Zugriff auf Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).

   **Ihr Projekt ist bereit.**

   Wenn der Befehl erfolgreich abgeschlossen wurde, wird in Ihrem lokalen Verzeichnis ein neuer Ordner erstellt. Dieser Ordner wird nach Ihrer Anwendung benannt (z. B. app-id). Dieser Ordner enthält alle Dateien und den Code, die aus Ihrem AEM as a Cloud Service-Git-Repository heruntergeladen wurden. Sie finden `<appid>` für Ihr AEM-Projekt in der Datei `archetype.properties`.

   ![Archetyp-Eigenschaften](/help/forms/assets/custom-submit-action-archetype-app-id.png)

   In diesem Handbuch wird dieser Ordner als `[AEMaaCS project directory]` bezeichnet.

## Neue Sendeaktion hinzufügen

1. Öffnen Sie den Repository-Ordner in einem Editor.

   ![Klontes Repository](/help/forms/assets/custom-submit-action-clone-repo.png)

1. Navigieren Sie zum folgenden Verzeichnis in Ihrem `[AEMaaCS project directory]`:

   ```
   /ui.apps/src/main/content/jcr_root/apps/<app-id>/
   ```
   **Wichtig**: Ersetzen Sie `<app-id>` durch Ihre tatsächliche Anwendungs-ID.

1. Erstellen Sie einen neuen Ordner für Ihre benutzerdefinierte Sendeaktion und geben Sie ihm einen Namen Ihrer Wahl. Benennen Sie den Ordner beispielsweise mit &quot;`customsubmitaction`&quot;.

   ![Erstellen Sie einen benutzerdefinierten Ordner für die Übermittlungsaktion](/help/forms/assets/custom-submit-action-create-folder.png)

1. Navigieren Sie zum Ordner mit der hinzugefügten benutzerdefinierten Übermittlungsaktion .

   Navigieren Sie innerhalb Ihres `[AEMaaCS project directory]` zu folgendem Pfad:

   `/ui.apps/src/main/content/jcr_root/apps/<app-id>/customsubmitaction/`

   `Important`: Replace <app-id> mit Ihrer eigentlichen Anwendungs-ID.

1. Erstellen Sie eine neue Konfigurationsdatei.
Erstellen Sie im Ordner `customsubmitaction` eine neue Datei mit dem Namen `.content.xml`.

   ![Konfigurationsdatei erstellen](/help/forms/assets/custom-submit-action-create-config-folder.png)

1. Öffnen Sie diese Datei und fügen Sie den folgenden Inhalt ein. Ersetzen Sie dabei `[customsubmitaction]` durch den Namen Ihrer Sendeaktion.

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
   jcr:description="[customsubmitaction]"
   jcr:primaryType="sling:Folder"
   
   guideComponentType="fd/af/components/guidesubmittype"
   guideDataModel="basic,xfa,xsd"
   submitService="[customsubmitaction]"/>
   ```

   Ersetzen Sie beispielsweise &quot;`[customsubmitaction]`&quot;durch den Namen Ihrer angepassten Sendeaktion &quot;1&quot;.`Custom Submit Action`

   ![Erstellen Sie eine benutzerdefinierte Konfigurationsdatei für die Sendeaktion](/help/forms/assets/custom-submit-action-config-file.png)

   >[!NOTE]
   >
   > Merken Sie sich den Namen der [customsubmitaction], da derselbe Name in der Dropdownliste `Submit action` beim Erstellen eines Formulars angezeigt wird.


**Den neuen Ordner in`filter.xml`** einschließen

1. Navigieren Sie zur Datei `/ui.apps/src/main/content/META-INF/vault/filter.xml` in Ihrem [AEMaaCS-Projektverzeichnis].

1. Öffnen Sie die Datei und fügen Sie die folgende Zeile am Ende ein:

   ```
   <filter root="/apps/<app-id>/[customsubmitaction-folder]"/>
   ```
   Fügen Sie beispielsweise die folgende Codezeile hinzu, um den Ordner &quot;`customsubmitaction`&quot;zur Datei &quot;`filter.xml`&quot;hinzuzufügen:

   ```
   <filter root="/apps/wknd/customsubmitaction"/>
   ```

   ![Fügen Sie die erstellten Ordner in die Datei filter.xml hinzu](/help/forms/assets/custom-submit-action-filter-xml.png)

1. Speichern Sie die Änderungen.

### Implementieren Sie den Dienst für die hinzugefügte Übermittlungsaktion.

1. Navigieren Sie zum folgenden Verzeichnis in Ihrem `[AEMaaCS project directory]`:
   `/core/src/main/java/com/<app-id>/core/service/`
   `Important`: Replace <app-id> mit Ihrer eigentlichen Anwendungs-ID.
1. Erstellen Sie eine neue Java-Datei, um den Dienst für die hinzugefügte Übermittlungsaktion zu implementieren. Fügen Sie beispielsweise die neue Java-Datei als `CustomSubmitService.java` hinzu.

   ![Benutzerdefinierter Ordner für Übermittlungsaktionen](/help/forms/assets/custom-submit-action-custom-submit-folder.png)

1. Öffnen Sie diese Datei und fügen Sie den Code für Ihre Implementierung der benutzerdefinierten Übermittlungsaktion hinzu.

   Der folgende Java-Code ist beispielsweise ein OSGi-Dienst, der die Formularübermittlung durch Protokollierung der gesendeten Daten verarbeitet und den Status `OK` zurückgibt. Fügen Sie den folgenden Code in die Datei `CustomSubmitService.java` ein:

   ```
   package com.wknd.core.service;
   
   import com.adobe.aemds.guide.model.FormSubmitInfo;
   import com.adobe.aemds.guide.service.FormSubmitActionService;
   import java.util.HashMap;
   import java.util.Map;
   import org.osgi.service.component.annotations.Component;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   
       @Component(
       service = FormSubmitActionService.class,
       immediate = true
           )
       public class CustomSubmitService implements FormSubmitActionService {
   
       private static final String serviceName = "Custom Submit Action";
   
       private static Logger log = LoggerFactory.getLogger(CustomSubmitService.class);
   
       @Override
       public String getServiceName() {
       return serviceName;
       }
   
       @Override
       public Map<String, Object> submit(FormSubmitInfo formSubmitInfo) {
       String data = formSubmitInfo.getData();
       log.info("Using custom submit action service, [data] --> " + data);
       Map<String, Object> result = new HashMap<>();
       result.put("status", "OK");
       return result;
        }
       }
   ```

   ![Custom Submit Action Service](/help/forms/assets/custom-submit-action-service.png)

1. Speichern Sie die Änderungen.

### Stellen Sie den Code bereit.

**Bereitstellen von Code für die lokale Entwicklungsumgebung**

* Stellen Sie die AEM as a Cloud Service `[AEMaaCS project directory]` in Ihrer lokalen Entwicklungsumgebung bereit, um die neue Sendeaktion auf Ihrem lokalen Computer auszuführen. Für die Bereitstellung in Ihrer lokalen Entwicklungsumgebung:

   1. Stellen Sie sicher, dass Ihre lokale Entwicklungsumgebung betriebsbereit ist. Wenn Sie noch keine lokale Entwicklungsumgebung eingerichtet haben, lesen Sie das Handbuch unter [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md).

   1. Öffnen Sie das Terminal-Fenster oder eine Eingabeaufforderung.

   1. Navigieren Sie zu &quot;`[AEMaaCS project directory]`&quot;.

   1. Führen Sie den folgenden Befehl aus:

      ```
      mvn -PautoInstallPackage clean install
      ```
      ![Lokale Bereitstellung](/help/forms/assets/custom-submit-action-local-deployment.png)

**Bereitstellen des Codes für die Cloud Service-Umgebung**

* Stellen Sie die AEM as a Cloud Service `[AEMaaCS project directory]` in Ihrer Cloud Service-Umgebung bereit. So stellen Sie es in Ihrer Cloud Service-Umgebung bereit:

   1. Übernehmen Sie Ihre Änderungen:

      Nachdem Sie die neue benutzerdefinierte Konfiguration für die Übermittlungsaktion hinzugefügt haben, übertragen Sie Ihre Änderungen mit einer klaren Git-Meldung. (Beispiel: &quot;Neue benutzerdefinierte Sendeaktion hinzugefügt&quot;).

   1. Stellen Sie den aktualisierten Code bereit:

      Lösen Sie eine Bereitstellung Ihres Codes durch die [vorhandene Full-Stack-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline) aus. Der aktualisierte Code wird automatisch erstellt und mit der neuen Unterstützung für die Übermittlungsaktion bereitgestellt.

      Wenn Sie noch keine Pipeline eingerichtet haben, lesen Sie das Handbuch zur [Einrichtung einer Pipeline für AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline).

      ![Cloud-Implementierung](/help/forms/assets/custom-submit-action-cloud-deployment.png)

      **Wie kann ich die Installation bestätigen?**

      Sobald das Projekt erfolgreich erstellt wurde, wird die benutzerdefinierte Übermittlungsaktion beim Erstellen eines Formulars in der Dropdown-Liste `Submit action` angezeigt.

      ![Dropdown-Liste Benutzerdefinierte Übermittlungsaktion](/help/forms/assets/custom-submit-action-drop-down-list.png)

  Ihre Umgebung kann jetzt die hinzugefügte benutzerdefinierte Übermittlungsaktion beim Erstellen eines Formulars verwenden.

### Vorschau eines adaptiven Formulars mit einer neu hinzugefügten Übermittlungsaktion

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Instanz an.
1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.

   ![Forms und Dokumente](/help/forms/assets/custom-submit-action-fnd.png)

1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Bearbeiten**. Das Formular wird im Bearbeitungsmodus geöffnet.

   ![Formular bearbeiten](/help/forms/assets/custom-submit-action-edit-af.png)

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie aus der Dropdownliste **[!UICONTROL Aktion übermitteln]** die Sendeaktion aus. Wählen Sie beispielsweise für die Sendeaktion &quot;`Custom Submit Action`&quot;aus.

   ![Benutzerdefiniertes Übermittlungsformular](/help/forms/assets/custom-submit-action-select-submit-action.png)

1. Füllen Sie das Formular aus und senden Sie es.

   ![Formular senden](/help/forms/assets/custom-submit-action-submit-form.png)

   ![Thankyou message](/help/forms/assets/custom-submit-action-thankyou-msg.png)

   Nachdem das Formular erfolgreich gesendet wurde, können Sie die **Adobe Experience Manager Web Console Configuration** überprüfen, um die Aktion der benutzerdefinierten Sendeaktion in der lokalen Entwicklungsumgebung zu überprüfen.
1. Rufen Sie `http://<host>:<port>/system/console/configMgr` auf.

1. Navigieren Sie zur **Adobe Experience Manager Web Console Log Support** unter `http://<host>:<port>/system/console/slinglog`.

   ![ConfigMgr](/help/forms/assets/custom-submit-action-sling-log.png)

1. Klicken Sie auf die Option `logs/error.log` .
   ![Öffnen Sie die Datei &quot;error.log&quot;](/help/forms/assets/custom-submit-action-error-log.png)

1. Öffnen Sie die Datei &quot;`error.log`&quot;, um zu sehen, dass die Daten angehängt wurden.

   ![error.log file](/help/forms/assets/custom-submit-action-form-data-display.png)

   >[!NOTE]
   >
   > Um Fehlerprotokolle in der AEM as a Cloud Service-Umgebung anzuzeigen, können Sie Splunk verwenden.

<!--
## Best practices

 * It is recommended to use the OSGi service approach for creating a custom submit action, as it is faster than the AEM servlet approach. 

## Next steps
-->

## Verwandte Artikel

{{af-submit-action}}


<!-- The [Adaptive Forms Core Components](https://github.com/adobe/aem-core-forms-components) repository includes a sample folder, `customsubmission/logsubmit`, to simplify the process of adding new custom submit actions. It also provides the Java service implementation for the `logsubmit` custom submit action, named `CustomAFSubmitService`.java. These resources are available on GitHub. -->