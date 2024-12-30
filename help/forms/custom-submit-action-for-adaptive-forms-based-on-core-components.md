---
title: Erstellen einer benutzerdefinierten Übermittlungsaktion für ein adaptives Formular basierend auf Kernkomponenten
description: Erfahren Sie, wie Sie eine benutzerdefinierte Übermittlungsaktion für eine adaptive Forms erstellen, um Daten zu verarbeiten, bevor Sie sie mit der benutzerdefinierten Übermittlungsaktion übermitteln.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Intermediate
exl-id: a369b585-d148-4b5a-8afe-d5673ea865d0
source-git-commit: 4eb0feecbc5d0f090789bd3023e366ef4eb620db
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 28%

---

# Erstellen einer benutzerdefinierten Übermittlungsaktion für adaptive Forms (Kernkomponenten)

Mit einer Übermittlungsaktion können Benutzer das Ziel für die in einem Formular erfassten Daten auswählen und zusätzliche Funktionen definieren, die bei der Formularübermittlung ausgeführt werden sollen. AEM-Formular unterstützt mehrere [ Übermittlungsaktionen (OOTB), ](/help/forms/configure-submit-actions-core-components.md). B. das Senden einer E-Mail oder das Speichern von Daten an SharePoint oder OneDrive.

Sie können auch eine benutzerdefinierte Übermittlungsaktion erstellen, um Funktionen hinzuzufügen, die nicht in den [vordefinierten Optionen“ enthalten ](/help/forms/configure-submit-actions-core-components.md#select-and-configure-a-submit-action-for-an-adaptive-form-select-and-configure-submit-action). Integrieren Sie beispielsweise die Formulardaten in eine Drittanbieteranwendung oder einen Trigger in einer personalisierten SMS-Benachrichtigung, die auf Benutzereingaben basiert.

<!-- ![Custom Submit Image](/help/forms/assets/custom-submit-action-hero-image.png)
-->

## Voraussetzungen

Bevor Sie mit der Erstellung Ihrer ersten benutzerdefinierten Übermittlungsaktion für adaptive Forms beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

* **Nur-Text-Editor (IDE)**: Zwar kann jeder einfache Nur-Text-Editor verwendet werden, aber eine integrierte Entwicklungsumgebung (IDE) wie Microsoft Visual Studio Code bietet erweiterte Funktionen für eine einfachere Bearbeitung.

* **Git**: Dieses Versionskontrollsystem ist für die Verwaltung von Code-Änderungen erforderlich. Wenn Sie nicht über das Programm verfügen, laden Sie es von https://git-scm.com herunter.

## Erstellen der ersten benutzerdefinierten Sende-Aktion für das Formular

Das folgende Diagramm zeigt die Schritte zum Erstellen einer benutzerdefinierten Übermittlungsaktion für ein adaptives Formular:

![Workflow für benutzerdefinierte Übermittlungsaktionen](/help/forms/assets/custom-submit-action-workflow.png){width=50%, height-50%}

### Klonen Sie das AEM as a Cloud Service-Git-Repository.

1. Öffnen Sie die Befehlszeile und wählen Sie einen Ordner zum Speichern des AEM as a Cloud Service-Repositorys aus, z. B. `/cloud-service-repository/`.

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```
   **Wo finden Sie diese Informationen?**

   Eine schrittweise Anleitung zum Auffinden dieser Details finden Sie im Adobe Experience League-Artikel [Zugriff auf Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).

   **Ihr Projekt ist bereit.**

   Wenn der Befehl erfolgreich abgeschlossen wurde, wird in Ihrem lokalen Verzeichnis ein neuer Ordner erstellt. Dieser Ordner wird nach Ihrem Programm benannt (z. B. app-id). Dieser Ordner enthält alle Dateien und den Code, die Sie aus Ihrem AEM as a Cloud Service-Git-Repository heruntergeladen haben. Sie finden `<appid>` für Ihr AEM-Projekt in der Datei `archetype.properties`.

   ![Archetyp-Eigenschaften](/help/forms/assets/custom-submit-action-archetype-app-id.png)

   In diesem Handbuch wird dieser Ordner als `[AEMaaCS project directory]` bezeichnet.

## Neue Übermittlungsaktion hinzufügen

1. Öffnen Sie den Repository-Ordner in einem Editor.

   ![geklontes Repository](/help/forms/assets/custom-submit-action-clone-repo.png)

1. Navigieren Sie in Ihrem `[AEMaaCS project directory]` zum folgenden Verzeichnis:

   ```
   /ui.apps/src/main/content/jcr_root/apps/<app-id>/
   ```
   **Wichtig**: Ersetzen Sie `<app-id>` durch Ihre tatsächliche Anwendungs-ID.

1. Erstellen Sie einen neuen Ordner für Ihre benutzerdefinierte Übermittlungsaktion und geben Sie ihr einen Namen Ihrer Wahl. Benennen Sie beispielsweise den Ordner als `customsubmitaction`.

   ![Erstellen eines benutzerdefinierten Ordners für Übermittlungsaktionen](/help/forms/assets/custom-submit-action-create-folder.png)

1. Navigieren Sie zum hinzugefügten Verzeichnis für benutzerdefinierte Übermittlungsaktionen .

   Navigieren Sie innerhalb Ihres `[AEMaaCS project directory]` zu folgendem Pfad:

   `/ui.apps/src/main/content/jcr_root/apps/<app-id>/customsubmitaction/`

   `Important`: ersetzen <app-id> mit Ihrer tatsächlichen Anwendungs-ID.

1. Erstellen Sie eine neue Konfigurationsdatei.
Erstellen Sie im Ordner `customsubmitaction` eine neue Datei mit dem Namen `.content.xml`.

   ![Konfigurationsdatei erstellen](/help/forms/assets/custom-submit-action-create-config-folder.png)

1. Öffnen Sie diese Datei und fügen Sie den folgenden Inhalt ein. Ersetzen Sie dabei `[customsubmitaction]` durch den Namen Ihrer Übermittlungsaktion

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
   jcr:description="[customsubmitaction]"
   jcr:primaryType="sling:Folder"
   
   guideComponentType="fd/af/components/guidesubmittype"
   guideDataModel="basic,xfa,xsd"
   submitService="[customsubmitaction]"/>
   ```

   Ersetzen Sie zum Beispiel den `[customsubmitaction]` mit dem benutzerdefinierten Namen der Übermittlungsaktion wie `Custom Submit Action`.

   ![Erstellen einer benutzerdefinierten Konfigurationsdatei für Übermittlungsaktionen](/help/forms/assets/custom-submit-action-config-file.png)

   >[!NOTE]
   >
   > Merken Sie sich den Namen der [customSubmitAction], da derselbe Name beim Erstellen eines Formulars in der `Submit action` Dropdown-Liste angezeigt wird.


**Fügen Sie den neuen Ordner in`filter.xml`** ein

1. Navigieren Sie zur Datei `/ui.apps/src/main/content/META-INF/vault/filter.xml` in Ihrem [AEMaaCS-Projektverzeichnis].

1. Öffnen Sie die Datei und fügen Sie die folgende Zeile am Ende ein:

   ```
   <filter root="/apps/<app-id>/[customsubmitaction-folder]"/>
   ```
   Fügen Sie beispielsweise die folgende Codezeile hinzu, um den `customsubmitaction` Ordner in der `filter.xml`-Datei hinzuzufügen:

   ```
   <filter root="/apps/wknd/customsubmitaction"/>
   ```

   ![Fügen Sie die erstellten Ordner in der Datei „filter.xml“ hinzu](/help/forms/assets/custom-submit-action-filter-xml.png)

1. Speichern Sie die Änderungen.

### Implementieren Sie den Service für die hinzugefügte Übermittlungsaktion.

1. Navigieren Sie in Ihrem `[AEMaaCS project directory]` zum folgenden Verzeichnis:
   `/core/src/main/java/com/<app-id>/core/service/`
   `Important`: ersetzen <app-id> mit Ihrer tatsächlichen Anwendungs-ID.
1. Erstellen Sie eine neue Java-Datei, um den Service für die hinzugefügte Übermittlungsaktion zu implementieren. Fügen Sie beispielsweise eine neue Java-Datei als `CustomSubmitService.java` hinzu.

   ![Ordner für benutzerdefinierte Sende-Aktionen](/help/forms/assets/custom-submit-action-custom-submit-folder.png)

1. Öffnen Sie diese Datei und fügen Sie den Code für Ihre benutzerdefinierte Übermittlungsaktionsimplementierung hinzu.

   Der folgende Java-Code ist beispielsweise ein OSGi-Dienst, der die Formularübermittlung verarbeitet, indem er die übermittelten Daten protokolliert und einen `OK` zurückgibt. Fügen Sie den folgenden Code in die `CustomSubmitService.java`-Datei ein:

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

   ![Service für benutzerdefinierte Sende-Aktionen](/help/forms/assets/custom-submit-action-service.png)

1. Speichern Sie die Änderungen.

### Stellen Sie den Code bereit.

**Bereitstellen von Code für eine lokale Entwicklungsumgebung**

* Stellen Sie die AEM as a Cloud Service `[AEMaaCS project directory]` in Ihrer lokalen Entwicklungsumgebung bereit, um die neue Übermittlungsaktion auf Ihrem lokalen Computer auszuprobieren. Für die Bereitstellung in Ihrer lokalen Entwicklungsumgebung:

   1. Stellen Sie sicher, dass Ihre lokale Entwicklungsumgebung betriebsbereit ist. Wenn Sie noch keine lokale Entwicklungsumgebung eingerichtet haben, lesen Sie das Handbuch unter [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md).

   1. Öffnen Sie das Terminal-Fenster oder eine Eingabeaufforderung.

   1. Navigieren Sie zum `[AEMaaCS project directory]`.

   1. Führen Sie den folgenden Befehl aus:

      ```
      mvn -PautoInstallPackage clean install
      ```
      ![Lokale Bereitstellung](/help/forms/assets/custom-submit-action-local-deployment.png)

**Stellen Sie den Code für die Cloud Service-Umgebung bereit**

* Stellen Sie die AEM as a Cloud Service `[AEMaaCS project directory]` in Ihrer Cloud Service-Umgebung bereit. So stellen Sie es in Ihrer Cloud Service-Umgebung bereit:

   1. Übergeben Sie Ihre Änderungen:

      Nachdem Sie die neue benutzerdefinierte Konfiguration der Übermittlungsaktion hinzugefügt haben, übertragen Sie Ihre Änderungen mit einer klaren Git-Nachricht. (Beispiel: „Neue benutzerdefinierte Übermittlungsaktion hinzugefügt„).

   1. Stellen Sie den aktualisierten Code bereit:

      Lösen Sie eine Bereitstellung Ihres Codes durch die [vorhandene Full-Stack-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline) aus. Der aktualisierte Code wird automatisch mit der neuen Unterstützung für benutzerdefinierte Übermittlungsaktionen erstellt und bereitgestellt.

      Wenn Sie noch keine Pipeline eingerichtet haben, lesen Sie das Handbuch zur [Einrichtung einer Pipeline für AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline).

      ![Cloud-Bereitstellung](/help/forms/assets/custom-submit-action-cloud-deployment.png)

      **Wie kann ich die Installation bestätigen?**

      Nachdem das Projekt erfolgreich erstellt wurde, wird die benutzerdefinierte Übermittlungsaktion beim Erstellen eines Formulars in der Dropdown-Liste `Submit action` angezeigt.

      ![Benutzerdefinierte Übermittlungsaktion - Dropdown-Liste](/help/forms/assets/custom-submit-action-drop-down-list.png)

  Ihre Umgebung kann jetzt beim Erstellen eines Formulars die hinzugefügte benutzerdefinierte Übermittlungsaktion verwenden.

### Vorschau eines adaptiven Formulars mit neu hinzugefügter Übermittlungsaktion

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Instanz an.
1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.

   ![Forms und Dokumente](/help/forms/assets/custom-submit-action-fnd.png)

1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Bearbeiten**. Das Formular wird im Bearbeitungsmodus geöffnet.

   ![Formular bearbeiten](/help/forms/assets/custom-submit-action-edit-af.png)

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie in **[!UICONTROL Dropdown-Liste]**&#x200B;Übermittlungsaktion“ die Übermittlungsaktion aus. Wählen Sie beispielsweise die Übermittlungsaktion wie `Custom Submit Action` aus.

   ![Benutzerdefiniertes Formular senden](/help/forms/assets/custom-submit-action-select-submit-action.png)

1. Füllen Sie das Formular aus und senden Sie es ab.

   ![Formular senden](/help/forms/assets/custom-submit-action-submit-form.png)

   ![Dankesnachricht](/help/forms/assets/custom-submit-action-thankyou-msg.png)

   Nachdem das Formular erfolgreich übermittelt wurde, können Sie die **Konfiguration der Adobe Experience Manager-Web-Konsole** überprüfen, um die Aktion der benutzerdefinierten Übermittlungsaktion in der lokalen Entwicklungsumgebung zu überprüfen.
1. Rufen Sie `http://<host>:<port>/system/console/configMgr` auf.

1. Navigieren Sie zur Protokollunterstützung für die **Adobe Experience Manager Web Console** unter `http://<host>:<port>/system/console/slinglog`.

   ![ConfigMgr](/help/forms/assets/custom-submit-action-sling-log.png)

1. Klicken Sie auf die Option `logs/error.log` .
   ![Öffnen Sie die Datei error.log](/help/forms/assets/custom-submit-action-error-log.png)

1. Öffnen Sie die `error.log` Datei , um zu sehen, dass die Daten angehängt wurden.

   ![error.log-Datei](/help/forms/assets/custom-submit-action-form-data-display.png)

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
