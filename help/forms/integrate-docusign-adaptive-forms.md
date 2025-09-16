---
title: Wie lässt sich DocuSign in ein adaptives Formular integrieren?
description: Erfahren Sie, wie Sie DocuSign mit einem adaptiven Formular verwenden können, um E-Signaturen einzuholen.
exl-id: fb2e75d6-e454-4999-a079-f663af79051f
feature: Adaptive Forms, Acrobat Sign
role: User, Developer
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 99%

---

# Verwenden von DocuSign mit einem adaptiven Formular {#integrate-aem-forms-with-DocuSign}

DocuSign ist eine herausragende Lösung für elektronische Signaturen. Damit lassen sich Vereinbarungen elektronisch unterzeichnen. Sie können DocuSign mit einem adaptiven Formular integrieren. Es hilft Ihnen dabei, ein adaptives Formular zur elektronischen Signatur an mehrere Empfänger zu senden. Die Verwendung von elektronischen Signaturen hilft Ihnen bei Folgendem:

- Geschäftsabschlüsse von jedem Gerät aus mit vollautomatischen Prozessen für Vorschlag, Angebot und Vertrag.
- Schnelleres Abschließen von Prozessen im Personalwesen und Zugang zu digitalen Abläufen für Ihre Mitarbeitenden.
- Kürzere Vertragszyklen und schnelleres Onboarding Ihrer Lieferanten.

AEM Forms as a Cloud Service bietet eine [benutzerdefinierte Übermittlungsaktion für DocuSign](#deploy-custom-submit-action). Die Übermittlungsaktion hilft Ihnen dabei, die adaptiven Formulare für elektronische Signaturen mithilfe von DocuSign-APIs zu senden.

| Sie können auch die E-Signaturlösung von Adobe, Adobe Sign, verwenden, um ein adaptives Formular elektronisch unterzeichnen zu lassen. AEM Forms verfügt über eine wesentlich tiefere Integration mit Adobe Sign und bietet wesentlich feinere Steuerelemente wie sequenzielles und paralleles Signieren, mehrere Authentifizierungsmethoden, formularinternes Signieren und mehr. Weitere Informationen finden Sie unter [Verwenden von Adobe Sign in einem adaptiven Formular](working-with-adobe-sign.md). |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## Voraussetzungen {#prerequisites}

Zur Integration von DocuSign mit AEM Forms sind folgende Elemente erforderlich:

- Ein DocuSign-[Entwicklerkonto](https://developers.docusign.com/platform/account/)
- Ein DocuSign-Programm
- Anmeldeinformationen (Client-ID und Client-Geheimnis) des DocuSign-API-Programms.
- [Benutzerdefinierte Übermittlungsaktion und Cloud-Service für DocuSign](https://github.com/adobe/aem-forms-docusign-sample)
- (Nur für lokale Entwicklungsumgebungen) [Einrichtung des aufzuzeichnenden Dokuments](setup-local-development-environment.md#docker-microservices).

## Konfiguration der benutzerdefinierten Übermittlungsaktion und des Cloud-Service für DocuSign {#deploy-custom-submit-action}

AEM Forms as a Cloud Service bietet eine benutzerdefinierte Übermittlungsaktion für DocuSign. Die Übermittlungsaktion hilft Ihnen dabei, die adaptiven Formulare für elektronische Signaturen mithilfe von DocuSign-APIs zu senden. Der Code für eine benutzerdefinierte Übermittlungsaktion ist unter [AEM Forms-Beispiele für öffentliches Git-Repository](https://github.com/adobe/aem-forms-docusign-sample) verfügbar. Sie können den Code so bereitstellen, wie er sich in Ihrer AEM Forms-Umgebung befindet, oder ihn gemäß den Anforderungen Ihres Unternehmens anpassen.

Führen Sie die folgenden Schritte aus, um die vorkonfigurierte benutzerdefinierte Übermittlungsaktion und den DocuSign-Cloud-Service zu konfigurieren:

1. [Klonen Sie Ihr AEM Forms as a Cloud Service-Projekt](setup-local-development-environment.md#forms-cloud-service-local-development-environment) oder erstellen Sie ein [!DNL Experience Manager Forms] as a [!DNL Cloud Service]-Projekt basierend auf [AEM Archetyp 27](https://github.com/adobe/aem-project-archetype) oder höher. So erstellen Sie ein [!DNL Experience Manager Forms] as a [!DNL Cloud Service]-Projekt basierend auf AEM Archetyp:
   </br> Öffnen Sie die Eingabeaufforderung und führen Sie den folgenden Befehl aus, um ein [!DNL Experience Manager Forms] as a Cloud Service-Projekt zu erstellen:

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=27 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   Ändern Sie im obigen Befehl außerdem `appTitle`, `appId` und `groupId`, sodass die Werte Ihrer Umgebung entsprechen.

1. Klonen Sie das Repository [aem-forms-samples](https://github.com/adobe/aem-forms-docusign-sample). Dieses Repository enthält eine benutzerdefinierte Übermittlungsaktion für DocuSign und Konfigurationsdetails zur Verbindung mit dem DocuSign-Server.

1. Öffnen Sie das in Schritt 1 erstellte AEM Forms as a Cloud Service-Projekt zur Bearbeitung in der IDE Ihrer Wahl.

1. Öffnen Sie die Datei `[AEM Forms as a Cloud Service project]\pom.xml` zur Bearbeitung und nehmen Sie die folgenden Änderungen vor:

   1. Fügen Sie Folgendes am Ende des `<properties>`-Tags hinzu:

      ```shell
      <repository.location>maven_repository</repository.location>
      ```

   1. Fügen Sie Folgendes am Ende des `<repositories>`-Tags hinzu:

      ```shell
       <repository>
          <id>project-repository</id>
          <url>file://${project.basedir}/${repository.location}</url>
       </repository>
      ```

      Wenn es kein `<repositories>`-Tag gibt, erstellen Sie das Tag unter dem `<properties>`-Tag.

   1. Fügen Sie Folgendes am Ende des `<dependencyManagement>`-Tags hinzu:

      ```shell
       <dependency>
         <groupId>com.adobe.aemforms.samples</groupId>
         <artifactId>forms.integration.docusign.all</artifactId>
         <type>zip</type>
         <version>1.0.0</version>
       </dependency>
      ```

1. Führen Sie die folgenden Schritte in der Datei `all/pom.xml` aus, die im Projektordner von Cloud Service verfügbar ist:

   1. Fügen Sie Folgendes am Ende des `<embeddeds>`-Tags hinzu:

      ```shell
       <embedded>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
          <target>/apps/moonlightprodprogram-vendor-packages/application/install</target>
       </embedded>
      ```

   1. Fügen Sie Folgendes am Ende des `<dependencies>`-Tags hinzu:

      ```shell
       <dependency>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
       </dependency>
      ```

1. Öffnen Sie die Eingabeaufforderung und gehen Sie zu `aem-forms-samples\forms-integration-docusign` (in Schritt 3 geklont) und führen Sie den folgenden Befehl aus:

   ```shell
   mvn clean install -Dinstall.dir="<AEM Forms as a Cloud Service project path>/maven_repository"
   ```

   `<AEM Forms as a Cloud Service project path>` bezieht sich auf den Namen des Ordners, der in Schritt 1 dieses Verfahrens erstellt wurde.

1. Stellen Sie das Projekt in Ihrer lokalen Entwicklungsumgebung bereit. Sie können folgenden Befehl verwenden, um die Bereitstellung für Ihre lokale Entwicklungsumgebung durchzuführen.

   `mvn -PautoInstallPackage clean install`

   Nachdem Sie diese Schritte ausgeführt haben, können Sie eine neue benutzerdefinierte Übermittlungsaktion [Übermitteln mit elektronischen DocuSign-Signaturen](#enabledocusign), die in der Liste der Übermittlungsoptionen für ein adaptives Formular verfügbar ist, und eine [DocuSign-Cloud-Service-Konfiguration](#configure-docusign-with-aem-forms) in Ihrer lokalen Entwicklungsumgebung sehen.

1. Kompilieren Sie den Code und [stellen Sie ihn in Ihrer [!DNL AEM Forms] as a Cloud Service-Umgebung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de#customer-releases) bereit.

## Integration von [!DNL DocuSign] mit [!DNL AEM Forms] {#configure-docusign-with-aem-forms}

Wenn alle Voraussetzungen erfüllt sind, führen Sie die folgenden Schritte aus, um [!DNL DocuSign] in der Autoreninstanz mit [!DNL AEM Forms] zu konfigurieren.

1. Gehen Sie zu **[!UICONTROL Tools]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL DocuSign]** und wählen Sie einen Ordner aus, in dem die Konfiguration gehostet werden soll.

1. Wählen Sie auf der Konfigurationsseite **[!UICONTROL Erstellen]**, um die [!DNL DocuSign]-Konfiguration in AEM Forms zu erstellen.
1. Geben Sie auf der Registerkarte **[!UICONTROL Allgemein]** auf der Seite **[!UICONTROL DocuSign-Konfiguration erstellen]** einen **[!UICONTROL Namen]** für die Konfiguration an und wählen Sie **[!UICONTROL Weiter]**. Sie können optional einen **[!UICONTROL Titel]** angeben.

1. Kopieren Sie die URL im aktuellen Browser-Fenster in einen Texteditor. Diese URL benötigen Sie, um [!DNL DocuSign] in einem späteren Schritt mit [!DNL AEM Forms] zu konfigurieren.

1. Konfigurieren Sie OAuth-Einstellungen für das [!DNL DocuSign]-Programm:

   1. Öffnen Sie ein Browser-Fenster und melden Sie sich beim [!DNL DocuSign] [-Entwicklerkonto](https://admindemo.docusign.com/apps-and-keys) an.
   1. Öffnen Sie die Anwendung, die für [!DNL AEM Forms] konfiguriert ist.
   1. Fügen Sie im Feld **[!UICONTROL Umleitungs-URL]** die im vorherigen Schritt kopierte URL ein und klicken Sie dann auf **[!UICONTROL Speichern]**.
   1. Notieren Sie sich die Integrations- und Geheimschlüssel.

   Schritt-für-Schritt-Anleitungen zum Konfigurieren der OAuth-Einstellungen für ein [!DNL DocuSign]-Programm und zum Abrufen der Schlüssel finden Sie in der Entwicklerdokumentation unter [Konfigurieren von OAuth-Einstellungen für die Anwendung](https://support.docusign.com/guides/ndse-admin-guide-api-and-keys).

1. Kehren Sie zur Seite **[!UICONTROL DocuSign-Konfiguration erstellen]** zurück. Auf der Registerkarte **[!UICONTROL Einstellungen]** wird im Feld **[!UICONTROL OAuth-URL]** die folgende Standard-URL angegeben:

   `https://account-d.docusign.com/oauth/auth`

1. Geben Sie die **[!UICONTROL Client-ID]** (DocuSign-Integrationsschlüssel) und das **[!UICONTROL Client-Geheimnis]** (geheimer DocuSign-Schlüssel) ein.

1. Wählen Sie **[!UICONTROL Verbindung zu DocuSign herstellen]**. Geben Sie bei Aufforderung zur Eingabe der Anmeldeinformationen den Benutzernamen und das Kennwort des Kontos an, die bei der Erstellung des [!DNL DocuSign]-Programms verwendet wurden. Sobald Sie aufgefordert werden, den Zugriff für `your developer account` zu bestätigen, klicken Sie auf **[!UICONTROL Zugriff erlauben]**. Wenn die Anmeldeinformationen korrekt sind, wird eine Erfolgsmeldung angezeigt.

1. Wählen Sie **[!UICONTROL Erstellen]**, um die [!DNL DocuSign]-Konfiguration zu erstellen.

1. Wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**, wählen Sie die Konfiguration aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**. Dadurch wird die Konfiguration in die entsprechende Umgebung im Veröffentlichungsmodus repliziert.

1. Wiederholen Sie alle oben genannten Schritte für Ihre Entwicklungs-, Staging- und Produktionsinstanzen (je nachdem, welche noch übrig sind), um die Konfiguration von [!DNL DocuSign] mit [!DNL AEM Forms] für Ihre Umgebung abzuschließen.

Jetzt ist Ihre AEM Forms-Umgebung für die Verwendung von DocuSign konfiguriert. Stellen Sie sicher, dass Sie den für den Cloud Service verwendeten Konfigurations-Container zu allen adaptiven Formularen hinzufügen, die für [!DNL DocuSign] aktiviert sind. Sie können einen Konfigurations-Container in den Eigenschaften eines adaptiven Formulars angeben.

### Verwenden von [!DNL DocuSign] in einem adaptiven Formular {#enabledocusign}

Sie können [!DNL DocuSign] für ein vorhandenes adaptives Formular aktivieren oder ein [!DNL DocuSign]-fähiges adaptives Formular erstellen. Wählen Sie eine der folgenden Möglichkeiten:

- [Ein  [!DNL DocuSign] -fähiges adaptives Formular erstellen](#create-an-adaptive-form-for-docusign)
- [ [!DNL DocuSign]  für ein vorhandenes adaptives Formular aktivieren](#editafsign).

#### Adaptives Formular für DocuSign erstellen {#create-an-adaptive-form-for-docusign}

Erstellen eines signaturfähigen adaptiven Formulars:

1. Gehen Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie **[!UICONTROL Erstellen]** und dann **[!UICONTROL Adaptives Formular]** aus. Eine Liste von Vorlagen wird angezeigt. Wählen Sie eine Vorlage aus und dann **[!UICONTROL Weiter]**.
1. Auf der Registerkarte **[!UICONTROL Standard]**:

   1. Geben Sie **[!UICONTROL Name]** und **[!UICONTROL Titel]** für das adaptive Formular an.

   1. Wählen Sie den [Konfigurations-Container](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) aus, der bei der [Integration von [!DNL DocuSign] in [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md) erstellt wurde.

   Der Konfigurations-Container enthält die für Ihre Umgebung konfigurierten [!DNL DocuSign]-Cloud Services. Diese Services können im Builder für adaptive Formulare ausgewählt werden.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Formularmodell]** eine der folgenden Optionen:

   - Wenn Sie über eine benutzerdefinierte Formularvorlage verfügen und ein Datensatzdokument auf Grundlage der Formularvorlage benötigen, wählen Sie die Option **[!UICONTROL Formularvorlage als Vorlage für das Datensatzdokument zuordnen]** und wählen Sie eine Datensatzdokumentvorlage aus. Wenn Sie diese Option verwenden, zeigen die zum Signieren gesendeten Dokumente nur die Felder an, die auf der zugehörigen Formularvorlage basieren. Es werden nicht alle Felder des adaptiven Formulars angezeigt.

   - Wenn Sie keine benutzerdefinierte Formularvorlage haben, wählen Sie die Option **[!UICONTROL Datensatzdokument erzeugen]**. Wenn Sie diese Option verwenden, zeigt das zum Signieren gesendete Dokument alle Felder des adaptiven Formulars an.

1. Wählen Sie **[!UICONTROL Erstellen]**. Es wird ein signaturfähiges adaptives Formular erstellt. Sie können Ihre [!DNL DocuSign]-Felder zum Formular hinzufügen und dieses zum Signieren senden.
1. Öffnen Sie Ihr adaptives Formular im Bearbeitungsmodus. Wählen Sie auf der Registerkarte **[!UICONTROL Inhalt]** die Option **[!UICONTROL Formular-Container]** und dann ![Konfigurieren](assets/configure-icon.svg).

1. Wählen Sie im Abschnitt **[!UICONTROL Übermittlung]** die Option **[!UICONTROL Senden mit DocuSign-E-Signaturen]** aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** aus.

1. Wählen Sie im Abschnitt **[!UICONTROL Aktionskonfiguration]** die Option **[!UICONTROL Hinzufügen]**, um eine Empfängerin bzw. einen Empfänger hinzuzufügen, und geben Sie die E-Mail-Adresse der Person an. Wählen Sie erneut **[!UICONTROL Hinzufügen]**, um weitere Empfängerinnen oder Empfänger hinzuzufügen.

1. Geben Sie im Feld **[!UICONTROL E-Mail-Betreffzeile]** den Betreff für die E-Mail-Nachricht an. Wählen Sie **Anhänge einschließen**, um Anhänge in die E-Mail-Nachricht aufzunehmen.

1. Wählen Sie ![Speichern](assets/save_icon.svg) aus, um die Eigenschaften zu speichern.

#### Aktivieren von [!DNL DocuSign] für ein adaptives Formular {#editafsign}

Verwenden von [!DNL DocuSign] in einem vorhandenen adaptiven Formular:

1. Gehen Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie das adaptive Formular aus und wählen Sie dann **[!UICONTROL Eigenschaften]**.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Standard]** den [Konfigurations-Container](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) aus, der bei der Integration von [!DNL DocuSign] in [!DNL AEM Forms] erstellt wurde.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Formularmodell]** eine der folgenden Optionen:

   - Wenn Sie über eine benutzerdefinierte Formularvorlage verfügen und ein Datensatzdokument auf Grundlage der Formularvorlage benötigen, wählen Sie die Option **[!UICONTROL Formularvorlage als Vorlage für das Datensatzdokument zuordnen]** und wählen Sie eine Datensatzdokumentvorlage aus. Wenn Sie diese Option verwenden, zeigen die zum Signieren gesendeten Dokumente nur die Felder an, die auf der zugehörigen Formularvorlage basieren. Es werden nicht alle Felder des adaptiven Formulars angezeigt.

   - Wenn Sie keine benutzerdefinierte Formularvorlage haben, wählen Sie die Option **[!UICONTROL Datensatzdokument erzeugen]**. Wenn Sie diese Option verwenden, zeigt das zum Signieren gesendete Dokument alle Felder des adaptiven Formulars an.

1. Wählen Sie **[!UICONTROL Speichern und schließen]**. Das adaptive Formular ist für [!DNL DocuSign] aktiviert. Jetzt können Sie Ihre [!DNL DocuSign]-Felder zum Formular hinzufügen und dieses zum Signieren senden.

1. Öffnen Sie Ihr adaptives Formular im Bearbeitungsmodus. Wählen Sie auf der Registerkarte **[!UICONTROL Inhalt]** die Option **[!UICONTROL Formular-Container]** und dann ![Konfigurieren](assets/configure-icon.svg).

1. Wählen Sie im Abschnitt **[!UICONTROL Übermittlung]** die Option **[!UICONTROL Senden mit DocuSign-E-Signaturen]** aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** aus.

1. Wählen Sie im Abschnitt **[!UICONTROL Aktionskonfiguration]** die Option **[!UICONTROL Hinzufügen]**, um eine Empfängerin bzw. einen Empfänger hinzuzufügen, und geben Sie die E-Mail-Adresse der Person an. Wählen Sie erneut **[!UICONTROL Hinzufügen]**, um weitere Empfängerinnen oder Empfänger hinzuzufügen.

1. Geben Sie im Feld **[!UICONTROL E-Mail-Betreffzeile]** den Betreff für die E-Mail-Nachricht an. Wählen Sie **Anhänge einschließen**, um Anhänge in die E-Mail-Nachricht aufzunehmen.

1. Wählen Sie ![Speichern](assets/save_icon.svg) aus, um die Eigenschaften zu speichern.
