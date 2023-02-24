---
title: Wie erfolgt die Migration aus AEM 6.5 Forms und AEM 6.4 Forms in eine [!DNL AEM Forms] as a Cloud Service-Umgebung?
description: Migrieren von einer [!DNL AEM Forms] On-Premise-Umgebung zu einer [!DNL AEM Forms] as a Cloud Service-Umgebung
contentOwner: khsingh
feature: Adaptive Forms
role: User, Developer
level: Intermediate
topic: Migration
exl-id: 090e77ff-62ec-40cb-8263-58720f3b7558
source-git-commit: b11979acc23efe5f1af690443180a6b456d589ed
workflow-type: tm+mt
source-wordcount: '1816'
ht-degree: 74%

---

# Migrieren zu [!DNL AEM Forms] as a Cloud Service  {#Harden-your-AEM-Forms-as-a-Cloud-Service-environment}

Sie können Ihre adaptiven Formulare, Designs, Vorlagen und Cloud-Konfigurationen aus <!-- AEM 6.3 Forms--> AEM 6.4 Forms unter OSGi und AEM 6.5 Forms unter OSGi zu [!DNL AEM] as a Cloud Service migrieren. Bevor Sie diese Assets migrieren, verwenden Sie das Migrationsdienstprogramm, um das in früheren Versionen verwendete Format in das Format zu konvertieren, das in [!DNL AEM] as a Cloud Service verwendet wird. Wenn Sie das Migrationsdienstprogramm ausführen, werden die folgenden Assets aktualisiert:

* Benutzerdefinierte Komponenten für adaptive Formulare
* Adaptive Formularvorlagen und -Designs
* Cloud-Konfigurationen
* Code-Editor-Skripte werden in wiederverwendbare Funktionen konvertiert und auf visuelle Regeln angewendet.

## Aspekte {#consideration}

* Der Service hilft nur beim Migrieren von Inhalten aus [!DNL AEM Forms] in OSGi-Umgebungen. Das Migrieren von Inhalten aus [!DNL AEM Forms] auf JEE in eine Cloud Service-Umgebung wird nicht unterstützt.

* (Nur für AEM 6.3 Forms oder Umgebungen mit einer älteren Version, die auf AEM 6.4 Forms oder AEM 6.5 Forms aktualisiert wurde) Adaptive Formulare, die auf in AEM 6.3 Forms oder einer früheren Version verfügbaren mitgelieferten Vorlagen und Designs basieren, werden in [!DNL AEM Forms] as a Cloud Service nicht unterstützt.

* Der Verifizierungsschritt ist nicht verfügbar. Entfernen Sie den Überprüfungsschritt aus Ihren vorhandenen adaptiven Formularen, bevor Sie sie in eine Cloud Service-Umgebung verschieben.

* Der Signaturschritt für Adaptive Forms ist nicht verfügbar. Entfernen Sie den Unterschriftsschritt aus einem vorhandenen adaptiven Formular. Konfigurieren Sie Ihr adaptives Formular für die Verwendung des In-Browser-Signatur-Erlebnisses. Nach der Übermittlung eines adaptiven Formulars wird die Adobe Sign-Vereinbarung im Browser zur Unterzeichnung angezeigt. Die In-Browser-Signatur ermöglicht ein schnelleres Unterzeichnen und spart dem Unterzeichner Zeit.

## Unterschied zu AEM 6.5 Forms

| Funktion | Unterschied zu AEM 6.5 Forms |
|--------------|-----------|
| HTML5 Forms (Mobile Forms) | Der Dienst unterstützt keine HTML5 Forms (Mobile Forms). Wenn Sie Ihre XDP-basierten Formulare als HTML5 Forms wiedergeben, können Sie die Funktion weiterhin in AEM 6.5 Forms verwenden. |
| Adaptive Formulare | <li><b>XSD-basierte adaptive Forms:</b> Der Dienst unterstützt keine HTML5 Forms (Mobile Forms). Wenn Sie Ihre XDP-basierten Formulare als HTML5 Forms wiedergeben, können Sie die Funktion weiterhin in AEM 6.5 Forms verwenden. </li> <li><b> Adaptive Formularvorlagen:</b> Verwenden Sie die Build-Pipeline und das entsprechende Git-Repository Ihres Programms, um vorhandene adaptive Formularvorlagen zu importieren. </li><li><b>Regeleditor:</b> AEM Forms as a Cloud Service bietet eine härtere [Regeleditor](rule-editor.md#visual-rule-editor). Der Code-Editor ist nicht auf Forms as a Cloud Service verfügbar. Das Migrationsdienstprogramm hilft Ihnen bei der Migration Ihrer Formulare mit benutzerdefinierten Regeln (die im Code-Editor erstellt wurden). Das Dienstprogramm konvertiert solche Regeln in benutzerdefinierte Funktionen, die von Forms as a Cloud Service unterstützt werden. Sie können die wiederverwendbaren Funktionen mit dem Regeleditor verwenden, um weiterhin Ergebnisse zu erhalten, die mit Regelskripten erzielt wurden. `onSubmitError` oder `onSubmitSuccess` -Funktionen sind jetzt als Aktionen im Regeleditor verfügbar. </li> <li><b>Entwürfe und Übermittlungen:</b> Der Dienst speichert keine Metadaten für Entwürfe und übermittelte adaptive Forms. </li> <li><b> Vorbefüllungsdienst:</b> Standardmäßig führt der Vorbefüllungs-Dienst Daten mit einem adaptiven Formular auf dem Client zusammen, anstatt Daten auf dem Server in AEM 6.5 Forms zusammenzuführen. Die Funktion hilft, die zum Vorausfüllen eines adaptiven Formulars erforderliche Zeit zu verbessern. Sie können immer konfigurieren, dass die Zusammenführungsaktion auf dem Adobe Experience Manager Forms-Server ausgeführt wird. </li><li><b>Übermittlungsaktionen:</b> Die **E-Mail als PDF** -Aktion nicht verfügbar ist. Die Übermittlungsaktion **E-Mail** bietet Optionen zum Senden von Anhängen und zum Anhängen von Datensatzdokumenten (Document of Record, DoR) per E-Mail. </li> |
| Formulardatenmodell | <li>Das Forms-Datenmodell unterstützt nur HTTP- und HTTP-Endpunkte zum Senden von Daten. </li><li>Forms as a Cloud Service ermöglicht die Verwendung von Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive und Diensten, die allgemeine CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) als Datenspeicher unterstützen. Der Dienst unterstützt keinen JDBC-Connector, Mutual SSL for Rest Connector und x509 zertifikatbasierte Authentifizierung für SOAP-Datenquellen. </li> |
| Service zur automatischen Formularkonvertierung | Der Dienst stellt kein Metamodell für den Automated forms conversion-Dienst bereit. Sie können [Laden Sie es aus der Automated forms conversion-Service-Dokumentation herunter.](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model). |
| Konfigurationen | <li>E-Mail unterstützt standardmäßig nur HTTP- und HTTPS-Protokolle. [Kontaktieren Sie das Support-Team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#sending-email), um Ports für den Versand von E-Mails und das SMTP-Protokoll für Ihre Umgebung zu aktivieren. </li> <li>Wenn Sie benutzerdefinierte Bundles verwenden, kompilieren Sie Ihren Code mit der neuesten Version von adobe-aemfd-docmanager neu, bevor Sie diese Bundles mit Forms as a Cloud Service verwenden.</li> |
| Document Manipulation APIs (Assembler-Dienst) | Der Dienst unterstützt keine von anderen Diensten oder Anwendungen abhängigen Vorgänge: <li>Die Konvertierung von Dokumenten im Nicht-PDF-Format in das PDF-Format wird nicht unterstützt. Beispielsweise werden Microsoft Word zum PDF, Microsoft Excel zum PDF und HTML zum PDF nicht unterstützt</li><li>Adobe Distiller-basierte Konvertierungen werden nicht unterstützt. Zum Beispiel PostScript(PS) zu PDF</li><li>Forms Service-basierte Konvertierungen werden nicht unterstützt. Beispielsweise XDP auf PDF forms.</li><li>Der Dienst unterstützt nicht die Konvertierung einer signierten PDF oder Transparent-PDF in ein anderes PDF-Format.</li> |

## Voraussetzungen {#prerequisites}

* Aktivierten Sie die Option [Forms aktivieren – Digitale Registrierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html?lang=de#editing-program) für Ihr Forms-Cloud Service-Programm und [führen Sie die Pipeline aus](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=de).

   ![Probelaufergebnis](assets/enable-add-on.png)

* In einer Cloud Service-Umgebung arbeitet das Migrationsdienstprogramm mit dem User Mapping Tool und dem Content Transfer Tool zusammen. Das Migrationsdienstprogramm macht [!DNL AEM Forms]-Assets mit Cloud Service kompatibel und das Content Transfer Tool migriert den Inhalt aus Ihrer [!DNL AEM Forms]-Umgebung in eine [!DNL AEM] as a Cloud Service-Umgebung. Bevor Sie das Migrationsdienstprogramm verwenden, machen Sie sich damit vertraut, wie der [Umstieg auf AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/home.html?lang=de) funktioniert. In den Prozess sind zwei Tools involviert:
   * [User Mapping Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#cloud-migration): Mit dem User Mapping Tool können Sie Ihre Benutzer den entsprechenden Adobe IMS-Benutzerkonten zuordnen.
   * [Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de#cloud-migration): Mit dem Content Transfer Tool können Sie Inhalte aus Ihrer vorhandenen Umgebung vorbereiten und in eine Cloud Service-Umgebung übertragen.
* Konten mit Administratorrechten in [!DNL AEM Forms] as a Cloud Service und Ihrer lokalen [!DNL AEM Forms]-Umgebung.
* Laden Sie den Best Practice Analyzer, das Content Transfer Tool und das [!DNL AEM Forms] Migration Utility (Migrationsdienstprogramm) aus dem [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunter und installieren Sie die Tools.

* Führen Sie das Tool [Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de#cloud-migration) aus und beheben Sie die gemeldeten Probleme.

<!-- * Download the latest [compatibility package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#aem-65-forms-releases) for your [!DNL AEM Forms] version. -->

## Migrieren von [!DNL AEM Forms]-Assets  {#use-the-migration-utility}

Führen Sie die folgenden Schritte aus, um Ihre [!DNL AEM Forms]-Assets mit Cloud Service kompatibel zu machen und sie in eine [!DNL AEM] as a Cloud Service-Umgebung zu übertragen.

1. Erstellen Sie einen [Klon](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/correct-method-to-clone-the-aem-environment/td-p/363487?profile.language=de) Ihrer bestehenden [!DNL AEM Forms]-Umgebung.

   Verwenden Sie immer die geklonte Umgebung, um das Content Transfer Tool und das Migrationsdienstprogramm auszuführen. Das Content Transfer Tool und das Migrationsdienstprogramm nehmen einige Änderungen am Inhalt und an den Assets vor. Daher sollten Sie das Content Transfer Tool und das Migrationsdienstprogramm nicht in einer Produktions-Umgebung ausführen.

1. Melden Sie sich mit Administratorrechten bei Ihrer geklonten Umgebung an.

1. Führen Sie das [User Mapping Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#cloud-migration) aus, um Ihre Benutzer den entsprechenden Adobe IMS-Benutzerkonten zuzuordnen. Sie benötigen Adobe IMS-Benutzerkonten, um sich bei einer [!DNL AEM Forms] as a Cloud Service-Instanz anzumelden.

1. Laden Sie das [Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de#cloud-migration) und das [!DNL AEM Forms] as a Cloud Service-Migrationsdienstprogramm aus dem [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) in die geklonte Umgebung herunter und installieren Sie die Tools. Sie können AEM Package Manager verwenden, um das Tool und das Dienstprogramm zu installieren.

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Inhaltsmigration]**.

1. Öffnen Sie die Karte **[!UICONTROL Forms für Migration vorbereiten]**. Der Browser zeigt fünf Optionen an:
   * **[!UICONTROL AEM Forms-Assets-Migration]**
   * **[!UICONTROL Migration von benutzerdefinierten adaptiven Formularkomponenten]**
   * **[!UICONTROL Migration von adaptiven Formularvorlagen]**
   * **[!UICONTROL Migration von AEM Forms-Cloud-Konfigurationen]**
   * **[!UICONTROL Migration von Code-Editor-Skript]**

1. Verwenden Sie die Optionen nacheinander, um Ihre [!DNL AEM Forms]-Assets mit [!DNL AEM] as a Cloud Service kompatibel zu machen:

   1. Tippen Sie auf **[!UICONTROL Migration von AEM Forms-Assets]** und tippen Sie im nächsten Bildschirm auf **[!UICONTROL Migration beginnen]**. Dadurch werden adaptive Formulare und Designs in Ihrer [!DNL AEM Forms]-Umgebung mit [!DNL AEM] as a Cloud Service kompatibel gemacht.

   1. Tippen Sie auf **[!UICONTROL Migration von adaptiven Formularkomponenten]** und tippen Sie auf der Seite „Migration benutzerdefinierter Komponenten“ auf **[!UICONTROL Migration beginnen]**. Dadurch werden alle benutzerdefinierten Komponenten, die für adaptive Formulare und Komponentenüberlagerungen in Ihrer [!DNL AEM Forms]-Umgebung entwickelt wurden, mit [!DNL AEM] as a Cloud Service kompatibel gemacht.

   1. Tippen Sie auf **[!UICONTROL Migration von adaptiven Formularvorlagen]** und tippen Sie auf der Seite „Migration von Komponenten“ auf **[!UICONTROL Migration beginnen]**. Dadurch werden Vorlagen für adaptive Formulare unter /apps oder /conf, die mit dem AEM-Vorlageneditor erstellt wurden, mit [!DNL AEM] as a Cloud Service kompatibel gemacht.

   1. Tippen Sie auf **[!UICONTROL Migration von AEM Forms Cloud-Konfigurationen]** und tippen Sie dann auf der Seite „Migration von Konfigurationen“ auf **[!UICONTROL Migration beginnen]**. Dadurch werden die folgenden Cloud Services aktualisiert und an einen neuen Speicherort verschoben:

      * Form Data Model Cloud Service (Cloud Service für Formulardatenmodell)
      * Google reCAPTCHA Cloud Service
      * [!DNL Adobe Sign] Cloud Service
      * Adobe Fonts Cloud Service (Cloud Service für Adobe Fonts)
   1. Tippen Sie auf **[!UICONTROL Migration von Code-Editor-Skripten]**, geben Sie einen Speicherort für wiederverwendbare Funktionen an und tippen Sie auf [!UICONTROL Migration beginnen].

   Der Cloud Service unterstützt keine Regeleditorskripte. Das Tool für die **[!UICONTROL Migration von Code-Editor-Skripten]** konvertiert alle Regelskripte in Ihrer Umgebung in wiederverwendbare Funktionen und wendet die wiederverwendbaren Funktionen auf den entsprechenden Speicherort im Visual Editor an. Diese wiederverwendbaren Funktionen werden in Form von Client-Bibliotheken gespeichert und helfen Ihnen dabei, die vorhandenen Funktionen zu erhalten. Das Tool wendet die generierten wiederverwendbaren Funktionen automatisch auf entsprechende adaptive Formulare an.

   Verwenden Sie den [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de#contentmanagement), um die wiederverwendbaren Funktionen (Client-Bibliotheken) in ein Paket zu exportieren.

1. [Stellen Sie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de#deploying-content-packages-via-cloud-manager-and-package-manager) das Paket mit den wiederverwendbare Funktionen (Client-Bibliotheken), [benutzerspezifischen Code, Komponenten, Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html?lang=de#cloud-manager) und benutzerdefinierte gebietsschemaspezifische Bibliotheken in Ihrer [!DNL AEM] as a Cloud Service-Umgebung bereit.

   <!-- 1. Install the latest [Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration) to your cloned [!DNL AEM Forms] environment. -->

1. Führen Sie das [Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de#cloud-migration) aus. Geben Sie beim Festlegen von Parametern im Bildschirm **[!UICONTROL Migrationsset erstellen]** den Pfad von Adaptives Forms, Designs, Vorlagen, Formulardatenmodelle, Cloud Services, benutzerdefinierte Komponenten und andere AEM Forms-spezifische Elemente in der Option **[!UICONTROL Einzuschließende Pfade]** an. Dadurch werden die angegebenen [!DNL AEM Forms]-Assets zum Migrationssatz hinzugefügt.

## Pfade verschiedener AEM Forms-spezifischer Assets

* **Adaptive Formulare**: Adaptive Formulare finden Sie unter `/content/dam/formsanddocuments/`und /content/forms/af. Beispiel: Für ein adaptives Formular mit dem Titel „WKND-Registrierung“ fügen Sie die Pfade `/content/dam/formsanddocuments/wknd-registration` und `/content/forms/af/wknd-registration` hinzu.
* **Formulardatenmodelle**: Alle Formulardatenmodelle finden Sie unter `/content/dam/formsanddocuments-fdm`. Beispiel: `/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`.

* **Client-Bibliotheken**: Der Standardpfad von Client-Bibliotheken lautet `/etc/clientlibs/fd/theme`.

* **Adaptive Formularvorlagen**: Der Standardpfad von Vorlagen lautet `/conf/<template folder>`. Beispiel: Für eine Vorlage mit dem Titel „Basic“ fügen Sie den Pfad `/conf/ReferenceEditableTemplates/settings/wcm/templates/basic` hinzu.

* **Designs für adaptive Formulare und Client-Bibliotheken**: Der Standardpfad von Designs lautet ` /content/dam/formsanddocuments-themes/`, und der Standardpfad von Client-Bibliotheken ist `/etc/clientlibs/fd/theme`. Beispiel: Für eine Vorlage mit dem Titel „WKND-Design“ fügen Sie den Pfad ` /content/dam/formsanddocuments-themes/wkndtheme` und die Client-Bibliotheken für das Design unter `/etc/clientlibs/reference-themes/wkndtheme-3-0` hinzu. Sie können Designs und Client-Bibliotheken auch an anderen benutzerdefinierten Pfaden speichern.

* **Cloud-Konfigurationen**: Sie finden die Cloud-Konfigurationen unter `/conf/`. Die Cloud-Konfiguration für das Formulardatenmodell beispielsweise befindet sich unter `/conf/global/settings/cloudconfigs/fdm`.

* **Workflow-Modell**: AEM Workflow-Modelle finden Sie unter `/conf/global/settings/workflow/models/`. Beispiel: Für ein Workflow-Modell mit dem Titel „WKND-Registrierung“ fügen Sie den Pfad `/conf/global/settings/workflow/models/wknd-registration` hinzu.

Sie können die unten aufgeführten Ordnerpfade der obersten Ebene oder bestimmte Ordnerpfade wie unten beschrieben hinzufügen. Dadurch können Sie bestimmte Assets und alle Assets und Formulare gleichzeitig migrieren.

* /content/dam/formsanddocuments-fdm
* /content/dam/formsanddocuments/themes
* /content/forms/af
* /etc/clientlibs/fd/theme

Um AEM Workflow-Modelle zu migrieren, geben Sie die folgenden Pfade an:

* /conf/global/settings/workflow/models/
* /conf/global/settings/workflow/launcher
* /var/workflow/models
