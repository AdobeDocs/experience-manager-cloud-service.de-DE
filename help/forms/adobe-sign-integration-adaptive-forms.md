---
title: Wie integrieren Sie Adobe Acrobat Sign in AEM Forms?
description: Erfahren Sie, wie Sie Adobe Acrobat Sign für konfigurieren [!DNL AEM Forms] as a Cloud Service?
feature: Adaptive Forms
role: User
level: Intermediate
source-git-commit: d9c5934c03b9c5aa91bafa09569d441fc7868937
workflow-type: tm+mt
source-wordcount: '1931'
ht-degree: 47%

---

# Verbinden [!DNL AEM Forms] as a Cloud Service mit [!DNL Adobe Acrobat Sign] {#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Acrobat Sign] ermöglicht E-Signatur-Workflows für adaptive Forms- und AEM-Workflows. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit [!DNL Adobe Acrobat Sign] und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um eine Dienstleistung zu beantragen. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstleister gesendet. Der Dienstleister prüft den Antrag und markiert ihn mit [!DNL Adobe Acrobat Sign] als genehmigt. AEM Forms unterstützt sowohl Adobe Acrobat Sign als auch Adobe Acrobat Sign Solutions for Government. Abhängig von Ihrer Lizenz und Ihren Anforderungen können Sie AEM Forms mit einer der folgenden Lösungen integrieren oder verbinden:

* [Verbinden von AEM Forms mit Adobe Acrobat Sign](#adobe-sign)
* [Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden](#adobe-acrobat-sign-for-government)

## Verbinden von AEM Forms mit Adobe Acrobat Sign {#adobe-sign}

Verbindung herstellen **[!DNL AEM Forms]** mit **[!DNL Adobe Acrobat Sign]**, richten Sie die im Abschnitt &quot;Voraussetzungen&quot;aufgelistete Software und Konten ein und konfigurieren Sie die Adobe Sign Cloud Service in Ihren as a Cloud Service Autoren- und Veröffentlichungsinstanzen von Forms:

### Voraussetzungen für die Verbindung von AEM Forms mit Adobe Acrobat Sign {#prerequisites-for-adobe-sign}

Sie benötigen die folgende Einrichtung zur Integration [!DNL Adobe Acrobat Sign] mit [!DNL AEM Forms]:

1. Ein aktiver [Adobe Acrobat Sign-Entwicklerkonto](https://acrobat.adobe.com/de/de/sign/developer-form.html).
1. Ein [Adobe Acrobat Sign API-Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
1. Anmeldeinformationen (Client-ID und Client Secret) der [!DNL Adobe Acrobat Sign]-API-Anwendung.
1. (Nur für Authentifizierung mit Behörden-ID) [Authentifizierungsmethode aktivieren](https://helpx.adobe.com/de/sign/using/adobesign-authentication-government-id.html#AuditReport) für die Authentifizierung mit der Behördenkennung.



### AEM Forms-Autoren- und Veröffentlichungsinstanzen mit Adobe Acrobat Sign verbinden {#configure-adobe-sign-with-aem-forms}

Wenn alle Voraussetzungen erfüllt sind, führen Sie die folgenden Schritte aus, um [!DNL Adobe Acrobat Sign] in der Autoreninstanz mit [!DNL AEM Forms] zu konfigurieren.

1. Navigieren Sie auf der AEM Forms-Autoreninstanz zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.
1. Tippen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container für Cloud Services erstellt. Stellen Sie sicher, dass der Ordnername keine Leerzeichen enthält.
1. Navigieren Sie zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** und öffnen Sie den Konfigurationscontainer, den Sie im vorherigen Schritt erstellt haben.

   >[!NOTE]
   >
   >Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.

1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Acrobat Sign]-Konfiguration in AEM Forms zu erstellen.
1. Im **[!UICONTROL Allgemein]** des **[!UICONTROL Adobe Acrobat Sign-Konfiguration erstellen]** Seite, geben Sie eine **[!UICONTROL Name]** für die Konfiguration und tippen Sie auf **[!UICONTROL Nächste]**. Sie können optional einen **[!UICONTROL Titel]** angeben und durchsuchen, um ein **[!UICONTROL Miniaturbild]** für die Konfiguration auszuwählen.

1. Jetzt können Sie **[!UICONTROL Lösung auswählen]** auswählen [!DNL Adobe Acrobat Sign].

   ![Adobe Acrobat Sign Solutions für Regierungsbehörden](assets/adobe-sign-solution.png)

1. Kopieren Sie die im aktuellen Browser-Fenster vorhandene URL in ein Notebook und entfernen Sie den Teil `/ui#/aem` von der URL aus. Die geänderte URL muss dann konfiguriert werden [!DNL Adobe Acrobat Sign] Anwendung mit [!DNL AEM Forms]in einem späteren Schritt. Tippen Sie auf **[!UICONTROL Weiter]**.

1. Auf der Registerkarte **[!UICONTROL Einstellungen]** enthält das Feld **[!UICONTROL OAuth URL]** die Standard-URL. Das Format der URL ist:

   `https://<shard>/public/oAuth/v2`

   Beispiel:
   `https://secure.na1.echosign.com/public/oauth/v2`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard. Sie können den Wert für die Datenbank-Shard ändern. Stellen Sie sicher, dass die [!DNL  Adobe Acrobat Sign]-Cloud-Konfigurationen auf die [korrekte Shard](https://helpx.adobe.com/de/sign/using/identify-account-shard.html) verweisen.

   Wenn Sie eine weitere [!DNL Adobe Acrobat Sign]-Konfiguration für eine Funktion oder Komponente von Adobe Experience Manager erstellen, vergewissern Sie sich, dass alle [!DNL Adobe Acrobat Sign]-Cloud-Konfigurationen auf dieselbe Shard verweisen.

   >[!NOTE]
   >
   > Behalten Sie die **Adobe Acrobat Sign-Konfiguration erstellen** Seite öffnen. Schließen Sie sie nicht. Nachdem Sie die OAuth-Einstellungen für die Anwendung [!DNL Adobe Acrobat Sign] wie in den nächsten Schritten beschrieben konfiguriert haben, können Sie die **Client-ID** und den **geheimen Client-Schlüssel** abrufen.


1. Konfigurieren Sie OAuth-Einstellungen für das [!DNL Adobe Acrobat Sign]-Programm:

   1. Öffnen Sie ein Browser-Fenster und melden Sie sich beim [!DNL Adobe Acrobat Sign]-Entwicklerkonto an.
   1. Wählen Sie die für [!DNL AEM Forms] konfigurierte Anwendung aus und tippen Sie auf **[!UICONTROL OAuth für Anwendung konfigurieren]**.
   1. Fügen Sie im Feld **[!UICONTROL Umleitungs-URL]** die im vorherigen Schritt (Schritt 8) kopierte URL ein und klicken Sie dann auf **[!UICONTROL Speichern]**.
   1. Aktivieren Sie den folgenden Umfang für die Anwendung [!DNL Adobe Acrobat Sign] und klicken Sie auf **[!UICONTROL Speichern]**.

   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   Schritt-für-Schritt-Anleitungen zum Konfigurieren der OAuth-Einstellungen für ein [!DNL Adobe Acrobat Sign]-Programm und zum Abrufen der Schlüssel finden Sie in der Entwicklerdokumentation unter [Konfigurieren von OAuth-Einstellungen für die Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md).

   ![OAuth Config](assets/oauthconfig_new.png)

1. Gehen Sie zurück zu **[!UICONTROL Adobe Acrobat Sign-Konfiguration erstellen]** Seite. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** [die **[!UICONTROL Client-ID]** (auch als Anwendungs-ID bezeichnet) und den **[!UICONTROL geheimen Client-Schlüssel]**] an. Verwenden Sie die [Client-ID und Client-Geheimnis der Adobe Acrobat Sign-Anwendung](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) die Sie im vorherigen Schritt erstellt haben.

1. Wählen Sie die **[!UICONTROL Adobe Acrobat Sign für Anlagen aktivieren]** Option zum Anhängen von Dateien, die an ein adaptives Formular angehängt sind, an die entsprechende [!DNL Adobe Acrobat Sign] Dokument zum Signieren gesendet.

1. Tippen **[!UICONTROL Verbindung zu Adobe Acrobat Sign herstellen]**. Wenn Sie nach Anmeldeinformationen gefragt werden, geben Sie **Benutzername** und **password** des beim Erstellen verwendeten Kontos [!DNL Adobe Acrobat Sign] Anwendung. Wenn Sie zur Bestätigung aufgefordert werden, können Sie `your developer account`, klicken Sie auf **[!UICONTROL Zugriff erlauben]**. Wenn die Anmeldeinformationen korrekt sind und Sie [!DNL AEM Forms] erlauben, auf Ihr [!DNL Adobe Acrobat Sign]-Entwicklerkonto zuzugreifen, wird eine Erfolgsmeldung wie folgende angezeigt.

   ![Erfolg der Adobe Acrobat Sign Cloud-Konfiguration](assets/adobe-sign-cloud-configuration-success.png)

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Acrobat Sign]-Konfiguration zu erstellen.

1. Wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**, wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**. Dadurch wird die Konfiguration in die entsprechende Umgebung im Veröffentlichungsmodus repliziert.

1. Wiederholen Sie alle oben genannten Schritte für Ihre Entwicklungs-, Staging- und Produktionsinstanzen (je nachdem, welche noch übrig sind), um die Konfiguration von [!DNL Adobe Acrobat Sign] mit [!DNL AEM Forms] für Ihre Umgebung abzuschließen.

Jetzt können Sie [Adobe Acrobat Sign-Felder zu einem adaptiven Formular hinzufügen](working-with-adobe-sign.md). Stellen Sie sicher, dass Sie den für den Cloud Service verwendeten Konfigurations-Container zu allen adaptiven Formularen hinzufügen, die für [!DNL Adobe Acrobat Sign] aktiviert sind. Sie können einen Konfigurations-Container in den Eigenschaften eines adaptiven Formulars angeben.

## Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden {#adobe-acrobat-sign-for-government}

[!BADGE Dokumentation zur Vorabversion]{type=Caution tooltip="Gelber Status"}
<span class="preview"> Dieser Abschnitt enthält die Dokumentation zur Vorabversion und kann geändert werden.</span>

Die Verbindung von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden ist ein mehrstufiger Prozess. Er umfasst:

* Erstellen der Umleitungs-URL für Ihre AEM-Instanzen
* Freigeben der Umleitungs-URL und des Umleitungs-Umfangs für Adobe Sign Solutions for Government-Teams
* Anmeldeinformationen vom Adobe Sign-Team erhalten
* Verwenden der erhaltenen Anmeldeinformationen, um AEM Forms mit Adobe Acrobat Sign Solutions for Government zu verbinden

![](/help/forms/assets/adobe-acrobat-sign-govt-workflow.png)


AEM Forms as a Cloud Service bietet Entwicklungs-, Staging- und Produktionsumgebungen. Sie können damit beginnen, Ihre Entwicklungsumgebung für mit Adobe Acrobat Sign Solutions for Government zu verbinden und die Staging- und Produktionsumgebungen später miteinander zu verbinden.

### Bevor Sie beginnen {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Stellen Sie vor der Verbindung von AEM Forms mit Adobe Acrobat Sign sicher, dass Ihre [Adobe Acrobat Sign Solutions für Regierungsbehörden](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) -Konto bereitgestellt wurde.


### Verbinden von AEM Forms as a Cloud Service mit Adobe Acrobat Sign Solutions für Regierungseinrichtungen {#connect-adobe-acrobat-sign-for-government}

#### Erstellen einer Umleitungs-URL für Ihre AEM-Instanz

1. Navigieren Sie in der as a Cloud Service Autoreninstanz von Forms zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurationsbrowser]**.
1. Tippen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container für Cloud Services erstellt. Stellen Sie sicher, dass der Ordnername keine Leerzeichen enthält.
1. Navigieren Sie zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** und öffnen Sie den Konfigurationscontainer, den Sie im vorherigen Schritt erstellt haben. Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.
1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Adobe Acrobat Sign]-Konfiguration in AEM Forms zu erstellen.
1. Kopieren Sie die URL Ihres aktuellen Browser-Fensters auf ein Notebook und entfernen Sie `/ui#/aem` von der URL aus. Diese URL wird als `re-direct URL`. Im nächsten Abschnitt teilen Sie die `re-direct URL` und `Scopes` mit Adobe Sign-Team und Anforderungsberechtigungen (Client-ID und Client-Geheimnis).


#### Freigeben der Umleitungs-URL und der Bereiche für das Adobe Sign-Team und Empfangen von Anmeldeinformationen

Das Adobe Acrobat Sign for Government Solutions-Team benötigt `re-direct URL` und die bestimmten Bereiche, die für Ihre Adobe Acrobat Sign-Anwendung aktiviert werden sollen (siehe unten), um Anmeldeinformationen (Client-ID und Client-Geheimnis) zu generieren, mit denen Sie AEM Forms mit Adobe Acrobat Sign Solutions für Behörden verbinden können.

Freigeben von `scopes` (siehe unten) und die `re-direct URL` den letzten Schritt des vorherigen Abschnitts mit Ihrem Adobe Acrobat Sign for Government Solution-Support-Mitarbeiter ([Adobe Professional Services-Teammitglied](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password)).

**_Bereiche_**

* [!DNL aggrement_read]
* [!DNL aggrement_write]
* [!DNL aggrement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

Der Support-Mitarbeiter generiert Anmeldeinformationen und gibt diese für Sie frei. Im nächsten Abschnitt verwenden Sie die Anmeldeinformationen (Client-ID und Client-Geheimnis), um AEM Forms mit Adobe Acrobat Sign Solutions for Government zu verbinden.

#### Verwenden Sie die erhaltenen Anmeldeinformationen, um AEM Forms mit Adobe Acrobat Sign Solutions for Government zu verbinden.

1. Öffnen Sie die `re-direct URL` in Ihrem Browser. Sie haben die `re-direct URL` im letzten Schritt des [Erstellen einer Umleitungs-URL auf Ihrer AEM-Instanz](#create-redirect-url) Abschnitt.

1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** auf der Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** einen **[!UICONTROL Namen]** für die Konfiguration an und tippen Sie auf **[!UICONTROL Weiter]**. Sie können optional einen **[!UICONTROL Titel]** angeben und durchsuchen, um ein **[!UICONTROL Miniaturbild]** für die Konfiguration auszuwählen. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Im **[!UICONTROL Einstellungen]** des **[!UICONTROL Adobe Sign-Konfiguration erstellen]** für die **[!UICONTROL Lösung auswählen]** auswählen [!DNL Adobe Acrobat Sign Solutions for Government].

   ![Adobe Acrobat Sign Solutions für Regierungsbehörden](assets/adobe-sign-for-govt.png)

1. Im **[!UICONTROL Email]** eingeben, geben Sie die E-Mail-Adresse an, die mit Ihrem Adobe Acrobat Sign Solutions for Government-Konto verknüpft ist.

1. Die **[!UICONTROL OAuth-URL]** gibt die Adobe Sign-Datenbank-Shard an. Das Feld enthält die Standard-URL. Ändern Sie die URL nicht.

1. Verwenden Sie die Anmeldeinformationen, die von Adobe Acrobat Sign für den Support-Mitarbeiter der Regierungslösung ([Adobe Professional Services-Teammitglied]) im vorherigen Abschnitt als [**[!UICONTROL Client-ID]** und **[!UICONTROL Client Secret]**].

1. Wählen Sie die **[!UICONTROL Adobe Acrobat Sign für Anlagen aktivieren]** Option zum Anhängen von Dateien, die an ein adaptives Formular angehängt sind, an die entsprechende [!DNL Adobe Acrobat Sign] Dokument zum Signieren gesendet.

1. Tippen Sie auf **[!UICONTROL Verbindung zu Adobe Sign herstellen]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen Benutzername und Kennwort des Kontos an, die bei der Erstellung des [!DNL Adobe Acrobat Sign]-Programms verwendet wurden. Sobald Sie aufgefordert werden, den Zugriff für `your developer account` zu bestätigen, klicken Sie auf **[!UICONTROL Zugriff erlauben]**. Wenn die Anmeldeinformationen korrekt sind und Sie [!DNL AEM Forms] erlauben, auf Ihr [!DNL Adobe Acrobat Sign]-Entwicklerkonto zuzugreifen, wird eine Erfolgsmeldung wie folgende angezeigt.

   ![Erfolg der Adobe Acrobat Sign Cloud-Konfiguration](assets/adobe-sign-cloud-configuration-success.png)

   <!-- > When prompted for credentials, provide username and password of the account used while creating [!DNL Adobe Acrobat Sign] application. When asked to confirm access for `your developer account`, Click **[!UICONTROL Allow Access]**. -->

1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die -Konfiguration zu erstellen.

1. Wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**, wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**. Die Konfiguration wird in den entsprechenden Veröffentlichungsumgebungen repliziert.

1. Wiederholen Sie alle oben genannten Schritte für Ihre Entwicklungs-, Staging- und Produktionsinstanzen (je nachdem, welche noch übrig sind), um die Konfiguration von [!DNL Adobe Acrobat Sign Solutions for Government] mit [!DNL AEM Forms] für Ihre Umgebung abzuschließen.

Jetzt können Sie [Adobe Acrobat Sign-Felder in einem adaptiven Formular hinzufügen](working-with-adobe-sign.md) oder [AEM Workflow](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step). Stellen Sie sicher, dass Sie den für die Cloud Service-Konfiguration verwendeten Konfigurationscontainer zu allen adaptiven Forms hinzufügen, für die die Option aktiviert ist [!DNL Adobe Acrobat Sign]. Sie können einen Konfigurations-Container in den Eigenschaften eines adaptiven Formulars angeben.

## (Nur für AEM-Workflows) Konfigurieren der [!DNL Adobe Acrobat Sign]-Planung, um den Unterzeichnungsstatus zu synchronisieren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Wenn Sie zum Unterzeichnen eines adaptiven Formulars den [!DNL Adobe Acrobat Sign]-Workflow-Schritt verwenden, kann das Formular je nach Konfiguration des Workflow-Schritts nacheinander an jeweils einen Unterzeichner oder gleichzeitig an alle Unterzeichner gesendet werden. Adaptive Formulare für [!DNL Adobe Acrobat Sign] werden erst dann an den Experience Manager-Formular-Server weitergeleitet, nachdem alle Unterzeichner den Unterzeichnungsvorgang abgeschlossen haben.

Standardmäßig überprüfen die [!DNL Adobe Acrobat Sign]-Planungs-Services die Unterzeichnerreaktionen alle 24 Stunden. Sie können das Standardintervall für Ihre Umgebung ändern.

Um das Standardintervall zu ändern, geben Sie eine [Cron-Ausdruck](https://en.wikipedia.org/wiki/Cron#CRON_expression) für **sign.status.exp** -Eigenschaft der **Adobe Acrobat Sign Configuration Service** Konfiguration.

Um beispielsweise den Konfigurationsdienst täglich um 00:00 Uhr auszuführen, legen Sie die **sign.status.exp** -Eigenschaft der **Adobe Acrobat Sign Configuration Service** Konfiguration `0 0 0 1/1 * ? *`. Folgende JSON-Datei zeigt das Beispiel einer täglichen Ausführung des Konfigurations-Service um 0:00 Uhr:

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

Um Konfigurationswerte festzulegen, [generieren Sie OSGi-Konfigurationen mit dem AEM-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und [stellen Sie die Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) in Ihrer Cloud Service-Instanz bereit.


## Ähnliche Artikel {#related-articles}

* [Verwenden von Adobe Acrobat Sign in einem adaptiven Formular](working-with-adobe-sign.md)

* [Best Practices für die Verwendung von Adobe Acrobat Sign mit Adaptive Forms](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
