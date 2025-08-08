---
title: Wie lässt sich Adobe Acrobat Sign in AEM Forms integrieren?
description: Erfahren Sie, wie Sie Adobe Acrobat Sign für [!DNL AEM Forms] as a Cloud Service konfigurieren.
feature: Adaptive Forms, Acrobat Sign
role: Admin, User
level: Intermediate
exl-id: 609c3072-1c3d-43fa-898a-b4e62db8483b
source-git-commit: bc422429d4a57bbbf89b7af2283b537a1f516ab5
workflow-type: tm+mt
source-wordcount: '2197'
ht-degree: 98%

---

# Verbinden von [!DNL AEM Forms] as a Cloud Service mit [!DNL Adobe Acrobat Sign] {#integrate-adobe-sign-with-aem-forms}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adobe-sign-integration-adaptive-forms.html?lang=de#adobe-acrobat-sign-for-government) |
| AEM as a Cloud Service | Dieser Artikel |

[!DNL Adobe Acrobat Sign] ermöglicht E-Signatur-Workflows für adaptive Formulare und AEM-Workflows. E-Signaturen verbessern die Workflows bei der Verarbeitung von Dokumenten in den Bereichen Recht, Vertrieb, Gehaltsabrechnung, Personalverwaltung u. v. a..

In einem typischen Szenario mit [!DNL Adobe Acrobat Sign] und adaptiven Formularen füllt der Benutzer ein adaptives Formular aus, um eine Dienstleistung zu beantragen. Dies könnte beispielsweise ein Antrag für eine Kreditkarte oder ein Formular für Dienstleistungen für Bürger sein. Wenn ein Benutzer das Antragsformular ausfüllt und signiert, wird dieses zur Bearbeitung an den Dienstleister gesendet. Der Dienstleister prüft den Antrag und markiert ihn mit [!DNL Adobe Acrobat Sign] als genehmigt. AEM Forms unterstützt sowohl Adobe Acrobat Sign als auch Adobe Acrobat Sign Solutions für Behörden. Je nach Ihrer Lizenz und Ihren Anforderungen können Sie AEM Forms mit einer der folgenden Lösungen integrieren oder verbinden:

* [Verbinden von AEM Forms mit Adobe Acrobat Sign](#adobe-sign)
* [Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden](#adobe-acrobat-sign-for-government)

## Verbinden von AEM Forms mit Adobe Acrobat Sign {#adobe-sign}

Um **[!DNL AEM Forms]** mit **[!DNL Adobe Acrobat Sign]** zu verbinden, richten Sie die im Abschnitt „Voraussetzungen“ aufgelistete Software und Konten ein und konfigurieren Sie den Adobe Sign Cloud Service in Ihren Authoring- und Publishing-Instanzen von Forms as a Cloud Service:

### Voraussetzungen für das Verbinden von AEM Forms mit Adobe Acrobat Sign {#prerequisites-for-adobe-sign}

Um [!DNL Adobe Acrobat Sign] mit [!DNL AEM Forms] zu integrieren, benötigen Sie das folgende Setup:

1. Ein gültiges [Adobe Acrobat Sign-Entwicklerkonto](https://www.adobe.com/acrobat/business/developer-form.html).
1. Eine [Adobe Acrobat Sign API-Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
1. Anmeldeinformationen (Client-ID und Client Secret) der [!DNL Adobe Acrobat Sign]-API-Anwendung.
1. (Nur für Authentifizierung mit amtlichem Lichtbildausweis) [Aktivieren Sie die Authentifizierungsmethode](https://helpx.adobe.com/de/sign/using/adobesign-authentication-government-id.html#AuditReport) für die Authentifizierung mit amtlichem Lichtbildausweis.

### Verbinden von Authoring- und Publishing-Instanzen von AEM Forms mit Adobe Acrobat Sign {#configure-adobe-sign-with-aem-forms}

Wenn alle Voraussetzungen erfüllt sind, führen Sie die folgenden Schritte aus, um [!DNL Adobe Acrobat Sign] in der Autoreninstanz mit [!DNL AEM Forms] zu konfigurieren.

1. Navigieren Sie auf der AEM Forms-Autoreninstanz zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.
1. Wählen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** die Option **[!UICONTROL Erstellen]** aus.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Wählen Sie dann die Option **[!UICONTROL Erstellen]** aus. Es wird ein Konfigurations-Container für Cloud Services erstellt. Stellen Sie sicher, dass der Ordnername keine Leerzeichen enthält.
1. Gehen Sie zu **[!UICONTROL Werkzeuge]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** und öffnen Sie den Konfigurations-Container, den Sie im vorherigen Schritt erstellt haben.

   >[!NOTE]
   >
   >Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.

1. Wählen Sie auf der Konfigurationsseite **[!UICONTROL Erstellen]**, um die [!DNL Adobe Acrobat Sign]-Konfiguration in AEM Forms zu erstellen.
1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** auf der Seite **[!UICONTROL Erstellen der Konfiguration für Adobe Acrobat Sign]** einen **[!UICONTROL Namen]** für die Konfiguration an und wählen Sie **[!UICONTROL Weiter]**. Sie können optional einen **[!UICONTROL Titel]** angeben und durchsuchen, um eine **[!UICONTROL Miniaturansicht]** für die Konfiguration auszuwählen.

1. Jetzt haben Sie die Option **[!UICONTROL Lösung auswählen]** und können [!DNL Adobe Acrobat Sign] auswählen.

   <!--![Adobe Acrobat Sign Solutions](assets/adobe-sign-solution.png)-->
   ![Adobe Acrobat Sign Solutions-Konfiguration](assets/adobe-sign-solution-config.png)

<!--

[create URL](#create-a-redirect-url-for-your-aem-instance)
 -->

1. Kopieren Sie die im aktuellen Browser-Fenster vorhandene URL in einen Text-Editor und entfernen Sie den Teil `/ui#/aem` aus der URL. Die geänderte URL wird benötigt, um in einem späteren Schritt die [!DNL Adobe Acrobat Sign]-Anwendung mit [!DNL AEM Forms] zu konfigurieren. Wählen Sie **[!UICONTROL Weiter]** aus.

1. Führen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** folgende Schritte aus:
   * Das Feld **[!UICONTROL OAuth-URL]** enthält die Standard-URL, die das Adobe Sign-Datenbank-Shard enthält. Das Format der URL ist:

     `https://<shard>/public/oauth/v2`

     Zum Beispiel:
     `https://secure.na1.echosign.com/public/oauth/v2`

   * Das Feld **[!UICONTROL Zugriffs-Token-URL]** enthält die Standard-URL, die das Adobe Sign-Datenbank-Shard enthält. Das Format der URL ist:

     `https://<shard>/oauth/v2/token`

     Zum Beispiel:
     `https://api.na1.echosign.com/oauth/v2/token`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard. Sie können den Wert für die Datenbank-Shard ändern. Stellen Sie sicher, dass die [!DNL &#x200B; Adobe Acrobat Sign]-Cloud-Konfigurationen auf die [korrekte Shard](https://helpx.adobe.com/de/sign/using/identify-account-shard.html) verweisen.

   >[!NOTE]
   >
   >* Lassen Sie die Seite **Erstellen einer Konfiguration für Adobe Acrobat Sign** geöffnet. Schließen Sie sie nicht. Nachdem Sie die OAuth-Einstellungen für die Anwendung [!DNL Adobe Acrobat Sign] wie in den nächsten Schritten beschrieben konfiguriert haben, können Sie die **Client-ID** und den **geheimen Client-Schlüssel** abrufen.
   > * Navigieren Sie nach der Anmeldung bei Ihrem Adobe Sign-Konto zu **[!UICONTROL Acrobat Sign-API]** >**[!UICONTROL API-Informationen]** > **[!UICONTROL Dokumentation zu REST-API-Methoden]** > **[!UICONTROL OAuth-Zugriffs-Token]**, um auf Informationen im Zusammenhang mit der Adobe Sign OAuth-URL und der Zugriffs-Token-URL zuzugreifen.

1. Konfigurieren Sie OAuth-Einstellungen für das [!DNL Adobe Acrobat Sign]-Programm:

   1. Öffnen Sie ein Browser-Fenster und melden Sie sich beim [!DNL Adobe Acrobat Sign]-Entwicklerkonto an.
   1. Wählen Sie die für [!DNL AEM Forms] konfigurierte Anwendung aus und wählen Sie **[!UICONTROL OAuth für Anwendung konfigurieren]**.
   1. Fügen Sie im Feld **[!UICONTROL Umleitungs-URL]** die im vorherigen Schritt (Schritt 8) kopierte URL ein und klicken Sie dann auf **[!UICONTROL Speichern]**.
   1. Aktivieren Sie den folgenden Umfang für die Anwendung [!DNL Adobe Acrobat Sign] und klicken Sie auf **[!UICONTROL Speichern]**.

   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   >[!NOTE]
   > Sie können den Bereichsmodifikator direkt über die AEM-Benutzeroberfläche von `self` auf `account` ändern, wie in Schritt 12 beschrieben.

   Schritt-für-Schritt-Anleitungen zum Konfigurieren der OAuth-Einstellungen für ein [!DNL Adobe Acrobat Sign]-Programm und zum Abrufen der Schlüssel finden Sie in der Entwicklerdokumentation unter [Konfigurieren von OAuth-Einstellungen für die Anwendung](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md).

   ![OAuth Config](/help/forms/assets/oauthconfig-new.png)

1. Gehen Sie zurück zur Seite **[!UICONTROL Erstellen einer Konfiguration für Adobe Acrobat Sign]**. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** die [**[!UICONTROL Client-ID]** (auch als Anwendungs-ID bezeichnet) und das **[!UICONTROL Client-Geheimnis]**] an. Verwenden Sie die [Client-ID und das Client-Geheimnis der Adobe Acrobat Sign-Anwendung](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret), die Sie im vorherigen Schritt erstellt haben.

1. Im Abschnitt [!UICONTROL Autorisierungsbereich] können Sie die Bereiche entweder in „Konto“ oder „Selbst“ ändern, indem Sie den Bereichen je nach Bedarf das Präfix „account“ oder „self“ hinzufügen.
   ![Autorisierungsumfang](/help/forms/assets/authorization-scope.png)

1. Wählen Sie die Option **[!UICONTROL Adobe Acrobat Sign für Anhänge aktivieren]**, um Dateien, die an einem adaptiven Formular angehängt sind, an ein entsprechendes [!DNL Adobe Acrobat Sign]-Dokument anzuhängen, das zum Signieren versandt wird.

1. Wählen Sie **[!UICONTROL Verbindung zu Adobe Acrobat Sign herstellen]**. Wenn Sie zur Eingabe der Anmeldedaten aufgefordert werden, geben Sie **Benutzername** und **Passwort** des Kontos an, das Sie bei der Erstellung der [!DNL Adobe Acrobat Sign]-Anwendung verwendet haben. Wenn Sie aufgefordert werden, den Zugriff für `your developer account` zu bestätigen, klicken Sie auf **[!UICONTROL Zugriff erlauben]**. Wenn die Anmeldeinformationen korrekt sind und Sie [!DNL AEM Forms] erlauben, auf Ihr [!DNL Adobe Acrobat Sign]-Entwicklerkonto zuzugreifen, wird eine Erfolgsmeldung wie folgende angezeigt.

   ![Cloud-Konfiguration für Adobe Acrobat Sign erfolgreich](assets/adobe-sign-cloud-configuration-success.png)

1. Wählen Sie **[!UICONTROL Erstellen]**, um die [!DNL Adobe Acrobat Sign]-Konfiguration zu erstellen.

1. Wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**, wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**. Dadurch wird die Konfiguration in die entsprechende Umgebung im Veröffentlichungsmodus repliziert.

1. Wiederholen Sie alle oben genannten Schritte für Ihre Entwicklungs-, Staging- und Produktionsinstanzen (je nachdem, welche noch übrig sind), um die Konfiguration von [!DNL Adobe Acrobat Sign] mit [!DNL AEM Forms] für Ihre Umgebung abzuschließen.

Jetzt können Sie [Adobe Acrobat Sign-Felder zu einem adaptiven Formular hinzufügen](working-with-adobe-sign.md). Stellen Sie sicher, dass Sie den für den Cloud Service verwendeten Konfigurations-Container zu allen adaptiven Formularen hinzufügen, die für [!DNL Adobe Acrobat Sign] aktiviert sind. Sie können einen Konfigurations-Container in den Eigenschaften eines adaptiven Formulars angeben.

>[!NOTE]
>
> Um die Adobe Sign-Sandbox zu konfigurieren, können Sie die gleichen Konfigurationsschritte wie unter [Adobe Sign](#adobe-sign) beschrieben durchführen.

#### Fehlerbehebung {#resolve-config-error}

Wenn Sie [!DNL Adobe Acrobat Sign] mit [!DNL AEM Forms] verbinden, könnten Sie einen Fehler `Unable to authorize access because the client configuration is invalid: invalid_request` finden, wie in der Abbildung unten dargestellt. Sie können dieses Problem lösen, indem Sie die nachstehenden Schritte befolgen:

![Konfigurationsfehler](/help/forms/assets/config_error_sign.png)

1. Kopieren Sie die im aktuellen Browser-Fenster vorhandene URL in einen Texteditor und entfernen Sie den Teil `/ui#/aem` aus der URL.
1. Öffnen Sie ein Browser-Fenster und melden Sie sich beim [!DNL Adobe Acrobat Sign]-Entwicklerkonto an.
1. Wählen Sie die für [!DNL AEM Forms] konfigurierte Anwendung aus und wählen Sie **[!UICONTROL OAuth für Anwendung konfigurieren]**.
1. Fügen Sie im Feld **[!UICONTROL Umleitungs-URL]** die im vorherigen Schritt kopierte URL ein und klicken Sie dann auf **[!UICONTROL Speichern]**.

## Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden {#adobe-acrobat-sign-for-government}

Das Verbinden von AEM Forms mit Adobe Acrobat Sign Solutions für Behörden ist ein mehrstufiger Prozess. Er umfasst:

* Erstellen einer Umleitungs-URL für Ihre AEM-Instanzen
* Weitergeben der Umleitungs-URL und des Umfangs an das Team von Adobe Sign Solutions für Behörden
* Erhalten von Anmeldedaten vom Adobe Sign-Team
* Verwenden der erhaltenen Anmeldeinformationen, um AEM Forms mit Adobe Acrobat Sign Solutions für Behörden zu verbinden

![Adobe Sign-Workflow für Behörden](/help/forms/assets/adobe-acrobat-sign-govt-workflow.png)


AEM Forms as a Cloud Service bietet Entwicklungs-, Staging- und Produktionsumgebungen. Sie können damit beginnen, Ihre Entwicklungsumgebung mit Adobe Acrobat Sign Solutions für Behörden zu verbinden, und die Staging- und Produktionsumgebungen später verbinden.

### Bevor Sie beginnen {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Bevor Sie damit beginnen, AEM Forms mit Adobe Acrobat Sign zu verbinden, stellen Sie sicher, dass Ihr [Adobe Acrobat Sign Solutions für Behörden](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning)-Konto bereitgestellt wurde.


### Verbinden von AEM Forms as a Cloud Service mit Adobe Acrobat Sign Solutions für Behörden {#connect-adobe-acrobat-sign-for-government}

#### Erstellen einer Umleitungs-URL für Ihre AEM-Instanz

1. Gehen Sie in der Authoring-Instanz von Forms as a Cloud Service zu **[!UICONTROL Werkzeuge]** ![Hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.
1. Wählen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** die Option **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Wählen Sie anschließend **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container für Cloud Services erstellt. Stellen Sie sicher, dass der Ordnername keine Leerzeichen enthält.
1. Navigieren Sie zu **[!UICONTROL Tools]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Adobe Acrobat Sign]** und wählen Sie den Konfigurations-Container aus, den Sie im vorherigen Schritt erstellt haben. Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.
1. Wählen Sie auf der Konfigurationsseite die Option **[!UICONTROL Erstellen]**, um die [!DNL Adobe Acrobat Sign]-Konfiguration in AEM Forms zu erstellen.
1. Kopieren Sie die URL Ihres aktuellen Browser-Fensters in einen Texteditor und entfernen Sie `/ui#/aem` aus der URL. Diese URL wird als `re-direct URL` bezeichnet.
Im nächsten Abschnitt geben Sie die `re-direct URL` und die `Scopes` an das Adobe Sign-Team weiter und fordern Anmeldeinformationen (Client-ID und Client-Geheimnis) an.

#### Weitergeben der Umleitungs-URL und der Bereiche an das Adobe Sign-Team und Empfangen von Anmeldeinformationen

Das Team von Adobe Acrobat Sign für Behörden benötigt die `re-direct URL` und die bestimmten Bereiche, die für Ihre Adobe Acrobat Sign-Anwendung aktiviert werden sollen (siehe unten), um Anmeldeinformationen (Client-ID und Client-Geheimnis) zu generieren, mit denen Sie AEM Forms mit Adobe Acrobat Sign Solutions für Behörden verbinden können.

Geben Sie die `scopes` (unten aufgelistet) und die `re-direct URL`, die Sie im letzten Schritt des vorherigen Abschnitts erstellt und notiert haben, an die Kontaktperson für Adobe Acrobat Sign for Government Solutions ([Mitglied des Adobe Professional Services-Teams](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password)) weiter.

**_Bereiche_**

* [!DNL aggrement_read]
* [!DNL aggrement_write]
* [!DNL aggrement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

Die Kontaktperson generiert Anmeldeinformationen und teilt Ihnen diese mit. Im nächsten Abschnitt verwenden Sie die Anmeldeinformationen (Client-ID und Client-Geheimnis), um AEM Forms mit Adobe Acrobat Sign Solutions für Behörden zu verbinden.

#### Verwenden Sie die erhaltenen Anmeldeinformationen, um AEM Forms mit Adobe Acrobat Sign Solutions für Behörden zu verbinden.

1. Öffnen Sie die `re-direct URL` in Ihrem Browser. Sie haben die `re-direct URL` im letzten Schritt des Abschnitts [Erstellen einer Umleitungs-URL in Ihrer AEM-Instanz](#create-a-redirect-url-for-your-aem-instance) erstellt und notiert.

1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** der Seite **[!UICONTROL Erstellen einer Adobe Sign-Konfiguration]** einen **[!UICONTROL Namen]** für die Konfiguration an und wählen Sie **[!UICONTROL Weiter]** aus. Sie können optional einen **[!UICONTROL Titel]** angeben und eine **[!UICONTROL Miniaturansicht]** für die Konfiguration suchen. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** der Seite **[!UICONTROL Adobe Sign-Konfiguration erstellen]** für **[!UICONTROL Lösung auswählen]** die Option [!DNL Adobe Acrobat Sign Solutions for Government] aus.


   ![Adobe Acrobat Sign Solutions für Behörden](assets/adobe-sign-for-govt.png)

1. Geben Sie im Feld **[!UICONTROL E-Mail]** die E-Mail-Adresse an, die mit Ihrem Konto von Adobe Acrobat Sign Solutions für Behörden verknüpft ist.

1. Führen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** folgende Schritte aus:
   * Das Feld **[!UICONTROL OAuth-URL]** enthält die Standard-URL, die das Adobe Sign-Datenbank-Shard enthält. Das Format der URL ist:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/authorize`

     Zum Beispiel:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/authorize`

   * Das Feld **[!UICONTROL Zugriffs-Token-URL]** enthält die Standard-URL, die das Adobe Sign-Datenbank-Shard enthält. Das Format der URL ist:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/token`

     Zum Beispiel:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/token`

   Hierbei gilt:

   **na1** bezieht sich auf die Standarddatenbank-Shard. Sie können den Wert für die Datenbank-Shard ändern. Stellen Sie sicher, dass die [!DNL &#x200B; Adobe Acrobat Sign]-Cloud-Konfigurationen auf die [korrekte Shard](https://helpx.adobe.com/de/sign/using/identify-account-shard.html) verweisen.

   >[!NOTE]
   >
   > * Navigieren Sie nach der Anmeldung bei Ihrem Adobe Sign-Konto zu **[!UICONTROL Acrobat Sign-API]** > **[!UICONTROL API-Informationen]** > **[!UICONTROL Dokumentation zu REST-API-Methoden]** > **[!UICONTROL OAuth-Zugriffs-Token]**, um auf Informationen im Zusammenhang mit der OAuth-URL und der Zugriffs-Token-URL für Adobe Sign zuzugreifen.

1. Verwenden Sie die Anmeldeinformationen, die die Kontaktperson für Adobe Acrobat Sign for Government Solutions ([Mitglied des Adobe Professional Services-Teams]) im vorherigen Abschnitt als [**[!UICONTROL Client-ID]** und **[!UICONTROL Client-Geheimnis]**] geteilt hat.

1. Wählen Sie die Option **[!UICONTROL Adobe Acrobat Sign für Anhänge aktivieren]**, um Dateien, die an einem adaptiven Formular angehängt sind, an ein entsprechendes [!DNL Adobe Acrobat Sign]-Dokument anzuhängen, das zum Signieren versandt wird.

1. Wählen Sie **[!UICONTROL Mit Adobe Sign verbinden]** aus. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen den Benutzernamen und das Kennwort des Kontos an, die bei der Erstellung der [!DNL Adobe Acrobat Sign]-Anwendung verwendet wurden. Sobald Sie aufgefordert werden, den Zugriff für `your developer account` zu bestätigen, klicken Sie auf **[!UICONTROL Zugriff erlauben]**. Wenn die Anmeldeinformationen korrekt sind und Sie [!DNL AEM Forms] erlauben, auf Ihr [!DNL Adobe Acrobat Sign]-Entwicklerkonto zuzugreifen, wird eine Erfolgsmeldung wie folgende angezeigt.

   ![Cloud-Konfiguration für Adobe Acrobat Sign erfolgreich](assets/adobe-sign-cloud-configuration-success.png)

   <!-- 
      > When prompted for credentials, provide username and password of the account used while creating [!DNL Adobe Acrobat Sign] application. When asked to confirm access for `your developer account`, Click **[!UICONTROL Allow Access]**. 
      -->

1. Wählen Sie **[!UICONTROL Erstellen]**, um die Konfiguration zu erstellen.

1. Wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**, wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**. Dadurch wird die Konfiguration in den entsprechenden Publishing-Umgebungen repliziert.

1. Wiederholen Sie alle oben genannten Schritte für Ihre Entwicklungs-, Staging- und Produktionsinstanzen (je nachdem, welche noch übrig sind), um die Konfiguration von [!DNL Adobe Acrobat Sign Solutions for Government] mit [!DNL AEM Forms] für Ihre Umgebung abzuschließen.

Sie können jetzt Adobe Acrobat Sign-Felder [in einem adaptiven Formular](working-with-adobe-sign.md) oder einem [AEM-Workflow](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step) hinzufügen. Stellen Sie sicher, dass Sie den für die Cloud-Service-Konfiguration verwendeten Konfigurations-Container zu allen adaptiven Formularen hinzufügen, die für [!DNL Adobe Acrobat Sign] aktiviert sind. Sie können einen Konfigurations-Container in den Eigenschaften eines adaptiven Formulars angeben.

## Konfigurieren der [!DNL Adobe Acrobat Sign]-Planung, um den Signaturstatus zu synchronisieren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

AEM Forms as a Cloud Service bietet einen Planungs-Service, der den Status von Unterzeichnenden in definierten Intervallen überprüft. Die Szenarien, in denen Sie den Planungs-Service konfigurieren:

* Wenn Sie [Formular abschicken (nachdem jeder Empfänger die Unterzeichnungszeremonie abgeschlossen hat)](/help/forms/working-with-adobe-sign.md#select-adobe-sign-cloud-service-and-signing-order) verwenden, um ein Dokument zu signieren, wird das Formular erst abgeschickt, nachdem alle Unterzeichnenden das Formular unterzeichnet haben.
* Wenn Sie den [Signier-Schritt in einem AEM-Workflow](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step) verwenden, um ein Dokument zu signieren, wartet der Signier-Schritt darauf, dass alle Unterzeichnenden das Dokument signieren, bevor mit dem nächsten Schritt des Workflows fortgefahren wird.

Standardmäßig überprüfen die [!DNL Adobe Acrobat Sign]-Planungs-Services die Unterzeichnerreaktionen alle 24 Stunden. Sie können das Standardintervall für Ihre Umgebung ändern.

Um das Standardintervall zu ändern, geben Sie einen [Cron-Ausdruck](https://en.wikipedia.org/wiki/Cron#CRON_expression) für die Eigenschaft **sign.status.exp** der Konfiguration des **Adobe Acrobat Sign-Konfigurationsdienstes** an.

Um beispielsweise den Konfigurations-Service täglich um 0:00 :00 auszuführen, legen Sie die Eigenschaft **sign.status.exp** der Konfiguration **Adobe Acrobat Sign Configuration Service** fest, um `0 0 0 1/1 * ? *` anzugeben. Die folgende JSON-Datei zeigt das Beispiel für die tägliche Ausführung des Konfigurations-Service um :00 Uhr:

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

Um Konfigurationswerte festzulegen, [generieren Sie OSGi-Konfigurationen mit dem AEM-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und [stellen Sie die Konfiguration in Ihrer Cloud Service-Instanz bereit](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process).

## Häufig gestellte Fragen

* **F: Kann ich die Adobe Sign GovCloud-Signaturseite in einem iFrame rendern?**
* **A:** Ja, Sie können die Adobe Sign GovCloud-Signaturseite in einem iFrame rendern.

>[!MORELIKETHIS]
>
>* [E-Signieren eines Formulars mithilfe von Freihandsignaturen](/help/forms/signing-forms-using-scribble.md)
>* [Best Practices für das Verwenden von Adobe Sign mit adaptiven Formularen](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
