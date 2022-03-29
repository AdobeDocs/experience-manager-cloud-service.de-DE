---
title: Integration von Adobe Sign in AEM Forms
description: Erfahren Sie, wie Sie Adobe Sign für [!DNL AEM Forms] as a Cloud Service konfigurieren.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 609c3072-1c3d-43fa-898a-b4e62db8483b
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 100%

---

# Integrieren von [!DNL Adobe Sign] mit [!DNL AEM Forms] as a Cloud Service  {#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign] aktiviert Arbeitsabläufe für E-Signaturen für adaptive Formulare. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit [!DNL Adobe Sign] und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um eine Dienstleistung zu beantragen. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstleister gesendet. Der Dienstleister prüft den Antrag und markiert ihn mit [!DNL Adobe Sign] als genehmigt. Sie können ähnliche Workflows für elektronische Signaturen ermöglichen, indem Sie [!DNL Adobe Sign] mit [!DNL AEM Forms] integrieren.

Um [!DNL Adobe Sign] mit [!DNL AEM Forms] zu verwenden, konfigurieren Sie [!DNL Adobe Sign] in AEM Cloud Services:

## Voraussetzungen {#prerequisites}

Um [!DNL Adobe Sign] mit [!DNL AEM Forms] zu integrieren, benötigen Sie Folgendes:

* Ein gültiges [Adobe Sign-Entwicklerkonto](https://acrobat.adobe.com/de/de/sign/developer-form.html).
* Eine [Adobe Sign API-Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Anmeldeinformationen (Client-ID und Client Secret) der [!DNL Adobe Sign]-API-Anwendung.
* Verwenden Sie [identische Schlüssel](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=de#make-sure-you-properly-replicate-encryption-keys-when-needed) für Autoren- und Veröffentlichungsinstanzen.
* (Nur für Authentifizierung mit amtlichem Lichtbildausweis) [Aktivieren Sie die Authentifizierungsmethode](https://helpx.adobe.com/de/sign/using/adobesign-authentication-government-id.html#AuditReport) mit amtlichem Lichtbildausweis.

## Konfigurieren von [!DNL Adobe Sign] mit [!DNL AEM Forms] {#configure-adobe-sign-with-aem-forms}

Wenn alle Voraussetzungen erfüllt sind, führen Sie die folgenden Schritte aus, um [!DNL Adobe Sign] in der Autoreninstanz mit [!DNL AEM Forms] zu konfigurieren.

1. Navigieren Sie auf der AEM Forms-Autoreninstanz zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.
1. Tippen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container für Cloud Services erstellt. Stellen Sie sicher, dass der Ordnername keine Leerzeichen enthält.
1. Navigieren Sie zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** und wählen Sie den Konfigurations-Container aus, den Sie im obigen Schritt erstellt haben.

   >[!NOTE]
   >
   >Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.

1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Sign]-Konfiguration in AEM Forms zu erstellen.
1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** auf der Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** einen **[!UICONTROL Namen]** für die Konfiguration an und tippen Sie auf **[!UICONTROL Weiter]**. Sie können optional einen **[!UICONTROL Titel]** angeben und durchsuchen, um ein **[!UICONTROL Miniaturbild]** für die Konfiguration auszuwählen.

1. Kopieren Sie die URL im aktuellen Browser-Fenster in einen Texteditor. Diese URL benötigen Sie, um [!DNL Adobe Sign] in einem späteren Schritt mit [!DNL AEM Forms] zu konfigurieren.

1. Konfigurieren Sie OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm:

   1. Öffnen Sie ein Browser-Fenster und melden Sie sich beim [!DNL Adobe Sign]-Entwicklerkonto an.
   1. Wählen Sie die für [!DNL AEM Forms] konfigurierte Anwendung aus und tippen Sie auf **[!UICONTROL OAuth für Anwendung konfigurieren]**.
   1. Fügen Sie im Feld **[!UICONTROL Umleitungs-URL]** die im vorherigen Schritt kopierte URL ein und klicken Sie dann auf **[!UICONTROL Speichern]**.
   1. Aktivieren Sie die folgenden OAuth-Einstellungen für das [!DNL Adobe Sign]-Programm und klicken Sie auf **[!UICONTROL Speichern]**.
   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   Schritt-für-Schritt-Anleitungen zum Konfigurieren der OAuth-Einstellungen für ein [!DNL Adobe Sign]-Programm und zum Abrufen der Schlüssel finden Sie in der Entwicklerdokumentation unter [Konfigurieren von OAuth-Einstellungen für die Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md).

   ![OAuth Config](assets/oauthconfig_new.png)

1. Kehren Sie zur Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** zurück. Auf der Registerkarte **[!UICONTROL Einstellungen]** wird im Feld **[!UICONTROL OAuth URL]** die folgende Standard-URL angegeben. Das Format der URL ist:

   `https://<shard>/public/oAuth/v2`

   Beispiel:
   `https://secure.na1.echosign.com/public/oauth/v2`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard. Sie können den Wert für die Datenbank-Shard ändern. Stellen Sie sicher, dass die [!DNL Adobe Sign]-Cloud-Konfigurationen auf die [korrekte Shard](https://helpx.adobe.com/de/sign/using/identify-account-shard.html) verweisen.

   Wenn Sie eine weitere [!DNL Adobe Sign]-Konfiguration für eine Funktion oder Komponente von Adobe Experience Manager erstellen, vergewissern Sie sich, dass alle [!DNL Adobe Sign]-Cloud-Konfigurationen auf dieselbe Shard verweisen.

1. Geben Sie die **[!UICONTROL Client-ID]** (auch als Anwendungs-ID bezeichnet) und das **[!UICONTROL Client-Geheimnis]** an. Verwenden Sie die Client-ID und das Client-Geheimnis des Adobe Sign-Programms, die Sie im vorherigen Schritt erstellt haben.

1. Wählen Sie die Option **[!UICONTROL Adobe Sign auch für Anhänge aktivieren]** aus, um Dateien, die an einem adaptiven Formular angehängt sind, an ein entsprechendes [!DNL Adobe Sign]-Dokument, das zum Signieren versandt wurde, anzuhängen.

1. Tippen Sie auf **[!UICONTROL Verbindung zu Adobe Sign herstellen]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen Benutzername und Kennwort des Kontos an, die bei der Erstellung des [!DNL Adobe Sign]-Programms verwendet wurden. Sobald Sie aufgefordert werden, den Zugriff für `your developer account` zu bestätigen, klicken Sie auf **[!UICONTROL Zugriff erlauben]**. Wenn die Anmeldeinformationen korrekt sind und Sie [!DNL AEM Forms] erlauben, auf Ihr [!DNL Adobe Sign]-Entwicklerkonto zuzugreifen, wird eine Erfolgsmeldung wie folgende angezeigt.

   ![Adobe Sign Cloud Configuration Success](assets/adobe-sign-cloud-configuration-success.png)

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Sign]-Konfiguration zu erstellen.

1. Wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**, wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**. Dadurch wird die Konfiguration in die entsprechende Umgebung im Veröffentlichungsmodus repliziert.

1. Wiederholen Sie alle oben genannten Schritte für Ihre Entwicklungs-, Staging- und Produktionsinstanzen (je nachdem, welche noch übrig sind), um die Konfiguration von [!DNL Adobe Sign] mit [!DNL AEM Forms] für Ihre Umgebung abzuschließen.

Jetzt können Sie [Adobe Sign-Felder zu einem adaptiven Formular hinzufügen](working-with-adobe-sign.md). Stellen Sie sicher, dass Sie den für den Cloud Service verwendeten Konfigurations-Container zu allen adaptiven Formularen hinzufügen, die für [!DNL Adobe Sign] aktiviert sind. Sie können einen Konfigurations-Container in den Eigenschaften eines adaptiven Formulars angeben.

## (Nur für AEM-Workflows) Konfigurieren der [!DNL Adobe Sign]-Planung, um den Unterzeichnungsstatus zu synchronisieren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Wenn Sie zum Unterzeichnen eines adaptiven Formulars den [!DNL Adobe Sign]-Workflow-Schritt verwenden, kann das Formular je nach Konfiguration des Workflow-Schritts nacheinander an jeweils einen Unterzeichner oder gleichzeitig an alle Unterzeichner gesendet werden. Adaptive Formulare für [!DNL Adobe Sign] werden erst dann an den Experience Manager-Formular-Server weitergeleitet, nachdem alle Unterzeichner den Unterzeichnungsvorgang abgeschlossen haben.

Standardmäßig überprüfen die [!DNL Adobe Sign]-Planungs-Services die Unterzeichnerreaktionen alle 24 Stunden. Sie können das Standardintervall für Ihre Umgebung ändern.

Um das Standardintervall zu ändern, geben Sie einen [Cron-Ausdruck](https://en.wikipedia.org/wiki/Cron#CRON_expression) für die Eigenschaft **sign.status.exp** der Konfiguration des **Adobe Sign-Konfigurations-Service** an.

Um beispielsweise den Konfigurations-Service täglich um 0:00 Uhr auszuführen, weisen Sie `0 0 0 1/1 * ? *` der Eigenschaft **sign.status.exp** des **Adobe Sign-Konfigurations-Service** zu. Folgende JSON-Datei zeigt das Beispiel einer täglichen Ausführung des Konfigurations-Service um 0:00 Uhr:

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

Um Konfigurationswerte festzulegen, [generieren Sie OSGi-Konfigurationen mit dem AEM-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und [stellen Sie die Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) in Ihrer Cloud Service-Instanz bereit.

<!-- , perform the following steps:

1. Log in to [!DNL AEM Forms] Server with admin credentials and navigate to **[!UICONTROL Tools]** &gt;**[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.

   You can also open the following URL in a browser window:
   `https://server/system/console/configMgr`

1. Locate and open the **[!UICONTROL Adobe Sign Configuration Service]** option. Specify a [cron expression](https://en.wikipedia.org/wiki/Cron#CRON_expression) in the **Status Update Scheduler Expression** field and click **Save**. For example, to run the configuration service daily at 00:00 am, specify `0 0 0 1/1 * ? *` in the **Status Update Scheduler Expression** field.

Default interval to sync status of [!DNL Adobe Sign] is now changed. -->

## Ähnliche Artikel {#related-articles}

* [Verwenden von Adobe Sign in einem adaptiven Formular](working-with-adobe-sign.md)

* [Best Practices für die Verwendung von Adobe Sign mit adaptiven Formularen](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
