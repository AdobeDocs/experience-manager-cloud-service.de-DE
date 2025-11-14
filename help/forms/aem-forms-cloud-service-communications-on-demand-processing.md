---
title: Wie richte ich synchrone APIs für interaktive Kommunikation ein?
description: Einrichten einer Entwicklungsumgebung für synchrone APIs für interaktive Kommunikation für Adobe Experience Manager Forms as a Cloud Service
role: Admin, Developer, User
feature: Adaptive Forms,APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: cb69041ff59ba1ff586e8c1c71090cc2eb9ad453
workflow-type: tm+mt
source-wordcount: '2573'
ht-degree: 2%

---


# Synchrone APIs für die Kommunikationsverarbeitung in AEM Forms as a Cloud Service

Dieses Handbuch enthält umfassende Anweisungen zum Einrichten und Verwenden synchroner AEM Forms Communications-APIs.

Erfahren Sie, wie Sie Ihre AEM as a Cloud Service-Umgebung konfigurieren, den API-Zugriff aktivieren und Kommunikations-APIs mithilfe der OAuth-Server-zu-Server-Authentifizierung aufrufen.

## Voraussetzungen

Um eine Umgebung zum Ausführen und Testen von AEM Forms Communications-APIs einzurichten, stellen Sie Folgendes sicher:

### Zugriff und Berechtigungen

Vergewissern Sie sich, dass Sie über die erforderlichen Zugriffsrechte und Berechtigungen verfügen, bevor Sie mit der Konfiguration der Kommunikations-APIs beginnen.

**Benutzer- und Rollenberechtigungen**

- Adobe ID erstellt unter [https://account.adobe.com/](https://account.adobe.com/de)
- Mit der E-Mail Ihres Unternehmens verknüpfte Adobe ID
- Adobe Managed Services-Produktkontext zugewiesen
- In der Adobe Admin Console zugewiesene Entwicklerrolle
- Berechtigung zum Erstellen von Projekten in der Adobe Developer Console

>[!NOTE]
>
> Weitere Informationen zum Zuweisen von Rollen und Gewähren des Zugriffs für Benutzer finden Sie im Artikel [Hinzufügen von Benutzern und Rollen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/users-and-roles).

**Cloud Manager-Zugriff**

- Anmeldedaten für [Cloud Manager](https://my.cloudmanager.adobe.com)
- Zugriff zum Anzeigen und Verwalten der Programmumgebungen
- Berechtigung zum Erstellen und Ausführen von CI/CD-Pipelines
- Zugriff auf Umgebungsdetails und Konfiguration

**Git-Repository-Zugriff**

- Zugriff auf das Cloud Manager-Git-Repository
- Git-Anmeldeinformationen für das Klonen und Pushen von Änderungen

### Entwicklungs-Tools

- **Node.js** zum Ausführen von Beispielanwendungen
- Neueste Version von **Git**
- Zugriff auf **Terminal/Befehlszeile**
- **Texteditor oder IDE** zum Bearbeiten von Konfigurationsdateien (VS Code, IntelliJ usw.)
- **Postman** oder ein ähnliches Tool für API-Tests

>[!NOTE]
>
> Dies ist ein einmaliger Prozess pro Umgebung, der abgeschlossen sein muss, bevor Sie mit der Einrichtung der AEM Forms Communications APIs fortfahren.

Nun werden wir jeden Schritt im Detail verstehen.

### Schritt 1: AEM-Instanz aktualisieren

So aktualisieren Sie die AEM-Instanz:

1. **Bei Adobe Cloud Manager anmelden**
   1. Navigieren Sie zu [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
   2. Mit Adobe ID anmelden

2. **Navigieren Sie zur Programmübersicht**
   1. Wählen Sie Ihr Programm aus der Liste aus. Sie werden zur Seite Programmübersicht weitergeleitet

3. **Umgebungsdetails suchen**
   1. Wählen Sie das Symbol `ellipsis`(…) neben dem Umgebungsnamen aus und klicken Sie auf **Aktualisieren**
   2. Klicken Sie auf **Senden** und führen Sie die vorgeschlagene Full-Stack-Pipeline aus.

      ![Umgebung aktualisieren](/help/forms/assets/update-env.png)

### Schritt 2: Git-Repository klonen

Klonen Sie das Cloud Manager-Git-Repository, um Ihre API-Konfigurationsdateien zu verwalten.

1. **Suchen Sie den Abschnitt Repository**
   1. Klicken Sie auf der **Programmübersicht** auf die Registerkarte **Repositorys**
   2. Suchen Sie den Repository-Namen und klicken Sie auf das Menü mit den Auslassungspunkten (…)
   3. Repository-URL kopieren

      >[!NOTE]
      >
      > Das URL-Format ist normalerweise `https://git.cloudmanager.adobe.com/<org>/<program>/`

2. **Klonen mit dem Git-Befehl**

   1. Öffnen Sie die Eingabeaufforderung oder das Terminal
   2. Führen Sie den `git clone` Befehl aus, um das Git-Repository zu klonen.

      ```bash
      git clone [repository-url]
      ```

      >[!NOTE]
      >
      > Verwenden Sie zum Klonen des Git-Repositorys die von Adobe Cloud Manager bereitgestellten Anmeldeinformationen.

      Um beispielsweise Ihr Git-Repository zu klonen, führen Sie den folgenden Befehl aus:

      ```bash
      https://git.cloudmanager.adobe.com/formsinternal01/AEMFormsInternal-ReleaseSanity-p43162-uk59167/
      ```

      ![Klonen des Git-Repositorys](/help/forms/assets/repo-clone.png)


**Optionen für die Git-Repository-Integration**

Adobe Cloud Manager unterstützt beide Repository-Optionen:

- **Direkte Verwendung des Git-Repositorys von Cloud Manager**
   - Verwenden des nativen Git-Repositorys von Cloud Manager
   - Integrierte Integration mit Pipelines

- **Integration mit dem kundenverwalteten Git-Repository**
   - Verbinden Ihres eigenen Git-Repositorys (GitHub, GitLab, Bitbucket usw.)
   - Konfigurieren der Synchronisierung mit Adobe Cloud Manager

Weitere Informationen zur Integration von Adobe Cloud Manager und Adobe Cloud Manager finden Sie unter [Dokumentation zur Git-Integration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/git-integration.html).

### Schritt 3: Zugriff auf die AEM Cloud Service-Umgebung und den AEM Forms-Endpunkt

Greifen Sie auf Ihre AEM Cloud Service-Umgebungsdetails zu, um die für die API-Konfiguration erforderlichen URLs und Kennungen abzurufen.

1. **Bei Adobe Cloud Manager anmelden**
   1. Navigieren Sie zu [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
   2. Mit Adobe ID anmelden

2. **Navigieren Sie zur Programmübersicht**
Wählen Sie Ihr Programm aus der Liste aus. Sie werden zur Seite Programmübersicht weitergeleitet

3. **Zugriff auf und Ansicht der AEM Cloud Service-Umgebung**

   Sie können die Umgebungsdetails von AEM Cloud Service mit einer der beiden Optionen anzeigen oder darauf zugreifen:

   - **Option 1: Von der Übersichtsseite**

      1. Auf der Seite **Programmübersicht**
      2. Klicken Sie **Menü links**„Umgebungen“.  Es wird eine Liste aller Umgebungen angezeigt

         ![Alle Umgebungen anzeigen](/help/forms/assets/all-env.png)

      3. Klicken Sie auf den spezifischen Umgebungsnamen, um die Details anzuzeigen

         ![option1-environment details](/help/forms/assets/option1-env.png)

   - **Option 2: aus dem Abschnitt Umgebungen**

      1. Auf der Seite Programmübersicht :
      2. Suchen Sie den Abschnitt **Umgebungen**.
      3. Klicken Sie auf **„Alle anzeigen**, um alle Umgebungen anzuzeigen
      4. Klicken Sie auf **Menü mit den Auslassungspunkten (…)** neben der Umgebung
         ![option1-environment details](/help/forms/assets/option2-env-details.png)
      5. Wählen Sie **Details anzeigen“**

         ![option1-environment details](/help/forms/assets/option1-env.png)

4. **Finden Sie Ihren AEM Forms-Endpunkt**

   Beachten Sie auf **Detailseite** Umgebung“ die folgenden Details:

   **Autoren-Service-URL**

   - URL: `https://author-pXXXXX-eYYYYY.adobeaemcloud.com`
   - Bucket: author-pXXXXX-eYYYY
Beispiel: `https://author-p43162-e177398.adobeaemcloud.com`

   **Veröffentlichungs-Service-URL**

   - URL: `https://publish-pXXXXX-eYYYYY.adobeaemcloud.com`
   - Bucket: publish-pXXXXX-eYYYY
Beispiel: `https://publish-p43162-e177398.adobeaemcloud.com`

>[!NOTE]
>
> Informationen zum Zugriff auf die AEM Cloud Service-Umgebung und den AEM Forms-Endpunkt finden Sie unter [Dokumentation zum Verwalten von Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=de).

### Schritt 4: API-Zugriffskonfiguration

Führen Sie die folgenden Schritte aus, um AEM Forms Communications-APIs zu konfigurieren:

#### 4.1 Adobe Developer Console-Projekteinrichtung

1. **Zugriff auf Adobe Developer Console**
   1. Navigieren Sie zu [Adobe Developer Console](https://developer.adobe.com/console)
   2. Mit Adobe ID anmelden

2. **Neues Projekt erstellen**
   1. Klicken Sie **Abschnitt „Schnellstart** auf **Neues Projekt erstellen**
   2. Ein neues Projekt wird mit einem Standardnamen erstellt

      ![ADC-Projekt erstellen](/help/forms/assets/adc-home.png)

   3. Klicken **oben** auf „Projekt bearbeiten“

      ![Projekt bearbeiten](/help/forms/assets/adc-edit-project.png)

   4. Geben Sie einen aussagekräftigen Namen an (z. B. „FormsProject„)
   5. Klicken Sie auf **Speichern**.

      ![Projektname bearbeiten](/help/forms/assets/adc-edit-projectname.png)

#### 4.2 Hinzufügen von Forms-Kommunikations-APIs

Sie können je nach Ihren Anforderungen verschiedene AEM Forms Communications-APIs hinzufügen.

**a. Für Document Services-APIs**

1. Klicken Sie auf **API hinzufügen**

   ![API hinzufügen](/help/forms/assets/adc-add-api.png)

2. **Forms-Kommunikations-APIs**
   1. Filtern _im Dialogfeld „API_&quot; nach **Experience Cloud**
   2. Wählen Sie **Forms-Kommunikations-APIs“**

   ![Forms-Kommunikations-API hinzufügen](/help/forms/assets/adc-add-forms-api.png)


3. Wählen Sie **OAuth Server-zu-Server** Authentifizierungsmethode aus

   ![Authentifizierungsmethode auswählen](/help/forms/assets/adc-add-authentication-method.png)

**b. Für Forms Runtime-APIs**

1. **Klicken Sie auf API hinzufügen**
   - Klicken Sie in Ihrem Projekt auf die Schaltfläche **API hinzufügen**

   ![API hinzufügen](/help/forms/assets/adc-add-api.png)

2. **AEM Forms-Bereitstellungs- und Laufzeit-API auswählen**
   - Filtern _im Dialogfeld „API_&quot; nach **Experience Cloud**
   - Wählen Sie **AEM Forms-Bereitstellungs- und Laufzeit-API“**
   - Klicken Sie auf **Weiter**.

   ![Laufzeit-API hinzufügen](/help/forms/assets/add-runtime-api.png)


3. **Authentifizierungsmethode**
   - Wählen Sie die Authentifizierungsmethode **OAuth-Server-zu-Server** aus.


   ![Authentifizierungsmethode auswählen](/help/forms/assets/add-authentication-for-runtime-apis.png)

#### 4.3 Produktprofil hinzufügen

Gehen Sie wie folgt vor, um das Produktprofil hinzuzufügen:

1. Wählen Sie das entsprechende **Produktprofil** basierend auf der erforderlichen Zugriffsebene aus:

   | Zugriffstyp | Produktprofil |
   |------------------|----------------------|
   | Nur-Lese-Zugriff | `AEM Users - author - Program XXX - Environment XXX` |
   | Lese-/Schreibzugriff | `AEM Assets Collaborator Users - author - Program XXX - Environment XXX` |
   | Vollständiger administrativer Zugriff | `AEM Administrators - author - Program XXX - Environment XXX` |

2. Wählen Sie das **Produktprofil** aus, das Ihrer Autoren-Service-URL (`https://author-pXXXXX-eYYYYY.adobeaemcloud.com`) entspricht. Beispiel: `https://author-pXXXXX-eYYYYY.adobeaemcloud.com` auswählen.

3. Klicken Sie auf **Konfigurierte API speichern**. Die API und das Produktprofil werden zu Ihrem Projekt hinzugefügt

   ![Projektkonfiguration auswählen](/help/forms/assets/adc-add-product-profile.png)

#### 4.4 Erstellen und Speichern von Anmeldeinformationen

1. **Zugriff auf Ihre Anmeldedaten**

   1. Navigieren Sie zu Ihrem Projekt in Adobe Developer Console
   2. Klicken Sie auf **OAuth Server-zu-Server** Anmeldedaten
   3. Sehen Sie sich den Abschnitt **Anmeldedaten** an

   ![Anzeigen der Anmeldeinformationen](/help/forms/assets/adc-view-credential.png)

2. **API-Anmeldeinformationen aufzeichnen**

   ```text
   API Credentials:
   ================
   Client ID: <your_client_id>
   Client Secret: <your_client_secret>
   Technical Account ID: <tech_account_id>
   Organization ID: <org_id>
   Scopes: AdobeID,openid,read_organizations
   ```

#### 4.5 Generieren von Zugriffstoken

**a. Zum Testen**

Manuelles Generieren von Zugriffs-Token in Adobe Developer Console:

1. **Navigieren Sie zu Ihrem Projekt**
   1. Öffnen Sie in Adobe Developer Console Ihr Projekt
   2. Klicken Sie auf **OAuth Server-zu-Server**

2. **Zugriffs-Token generieren**
   1. Klicken Sie im API-Abschnitt Ihres Projekts auf **Schaltfläche** Zugriffs-Token generieren“.
   2. Kopieren des generierten Zugriffstokens

   ![Zugriffs-Token generieren](/help/forms/assets/adc-access-token.png)

   >[!NOTE]
   >
   > Das Zugriffs-Token ist **24 Stunden lang gültig**

**b. Für die Produktion**

Programmgesteuerte Generierung von Token mithilfe des cURL-Befehls:

**Erforderliche Anmeldedaten:**

- Client-ID
- Client-Geheimnis
- Bereiche (typischerweise: `AdobeID,openid,read_organizations`)

**Token-Endpunkt:**

```
https://ims-na1.adobelogin.com/ims/token/v3
```

**Beispielanfrage (curl):**

```bash
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'grant_type=client_credentials' \
  -d 'client_id=<YOUR_CLIENT_ID>' \
  -d 'client_secret=<YOUR_CLIENT_SECRET>' \
  -d 'scope=AdobeID,openid,read_organizations'
```

**Antwort:**

```json
{
  "access_token": "eyJhbGciOiJSUz...",
  "token_type": "bearer",
  "expires_in": 86399
}
```

#### 4.6 Registrieren der Client-ID in der AEM-Umgebung

Damit die Client-ID Ihres ADC-Projekts mit der AEM-Instanz kommunizieren kann, müssen Sie sie mithilfe einer YAML-Konfigurationsdatei registrieren und über eine Konfigurations-Pipeline bereitstellen.

1. **Konfigurationsordner suchen oder erstellen**

   1. Navigieren Sie zum geklonten AEM Project-Repository und dann zum Ordner `config` .
   2. Wenn es nicht vorhanden ist, erstellen Sie es auf der Stammprojektebene:

   ```bash
   mkdir config
   ```

2. Erstellen Sie eine neue Datei mit dem Namen `api.yaml` im `config`:

   ```bash
   touch config/api.yaml
   ```

3. Fügen Sie den folgenden Code in die `api.yaml`-Datei ein:

   ```yaml
   kind: "API"
   version: "1"
   metadata:
   envTypes: ["dev"]  # or ["prod", "stage"] for production environments
   data:
   allowedClientIDs:
       author:
       - "<your_client_id>"
       publish:
       - "<your_client_id>"
       preview:
       - "<your_client_id>"
   ```

   Im Folgenden werden die Konfigurationsparameter erläutert:

   - **kind**: Immer auf `"API"` gesetzt (gibt dies als API-Konfiguration an)
   - **version**: API-Version, normalerweise `"1"` oder `"1.0"`
   - **envTypes**: Array von Umgebungstypen, für die diese Konfiguration gilt
      - `["dev"]` - Nur Entwicklungsumgebungen
      - `["stage"]` - Nur Staging-Umgebungen
      - `["prod"]` - Nur Produktionsumgebungen
   - **allowedClientIDs**: Client-IDs dürfen auf Ihre AEM-Instanz zugreifen
      - **author**: Client-IDs für die Autorenebene
      - **publish**: Client-IDs für die Veröffentlichungsebene
      - **preview**: Client-IDs für die Vorschauebene

   Fügen Sie beispielsweise die `allowedClientIDs` als `6bc4589785e246eda29a545d3ca55980` und envTypes als `dev` hinzu:

   ![Konfigurationsdatei wird hinzugefügt](/help/forms/assets/create-api-yaml-file.png)

4. **Änderungen übernehmen und per Push übertragen**

   1. Navigieren Sie zum Stammordner des geklonten Repositorys und führen Sie die folgenden Befehle aus:


   ```bash
       git add config/api.yaml
       git commit -m "Whitelist client id for api invocation"
       git push origin <your-branch>
   ```

   ![Git-Änderungen per Push übertragen](/help/forms/assets/push-yaml-changes-in-git.png)


5. **Konfigurations-Pipeline einrichten**

   1. **Bei Cloud Manager anmelden**
      1. Navigieren Sie zu [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
      2. Mit Adobe ID anmelden

   2. **Navigieren Sie zu Ihrem Programm**
Wählen Sie das gewünschte Programm aus der Liste aus, und Sie werden auf die Seite Programmübersicht weitergeleitet

   3. **Suchen Sie die Karte Pipelines**
      1. Suchen Sie die Karte **Pipelines** auf der Seite Programmübersicht .
      1. Klicken Sie auf **Schaltfläche „Hinzufügen**

   4. **Pipeline-Typ auswählen**

      - **Für Entwicklungsumgebungen**: Wählen Sie **Produktionsfremde Pipeline hinzufügen“**. Produktionsfremde Pipelines sind für Entwicklungs- und Staging-Umgebungen vorgesehen

      - **Für Produktionsumgebungen**: Wählen Sie **Produktions-Pipeline hinzufügen“**. Produktions-Pipelines erfordern zusätzliche Genehmigungen

        >[!NOTE]
        >
        > Erstellen Sie in diesem Fall eine produktionsfremde Pipeline, da eine Entwicklungsumgebung verfügbar ist.

   5. **Pipeline konfigurieren - Registerkarte „Konfiguration“**

      Auf der Registerkarte **Konfiguration**:

      a. **Pipeline-**
      - Wählen Sie **Bereitstellungs-Pipeline“**

      b. **Name der Pipeline**
      - Geben Sie einen beschreibenden Namen an, z. B. benennen Sie die Pipeline wie `api-config-pipieline`

      c. **Bereitstellungs-Trigger**
      - **Manuell**: Bereitstellung nur bei manueller Auslösung (für die Ersteinrichtung empfohlen)
      - **Bei Git-**: Automatische Bereitstellung, wenn Änderungen an die Verzweigung gepusht werden

      d. **Verhalten bei bedeutenden Metrikfehlern**
      - **Jedes Mal fragen**: Bei Fehlern Aktion anfordern (Standard)
      - **Sofort fehlschlagen**: Pipeline bei Metrikfehlern automatisch fehlschlagen
      - **Sofort fortfahren**: Trotz Fehlern fortfahren

      e. Klicken Sie auf **„Weiter“**, um zur Registerkarte **Source-Code** zu gelangen

      ![Pipeline konfigurieren](/help/forms/assets/add-config-pipeline.png)

   6. **Pipeline konfigurieren - Registerkarte &quot;Source-Code“**

      Auf der Registerkarte **Source** Code:

      a. **Bereitstellungstyp**
      - Wählen Sie **Zielgerichtete Bereitstellung“**

      b. **Bereitstellungsoptionen**
      - Wählen Sie **„Konfiguration“** (nur Konfigurationsdateien bereitstellen). Dadurch wird Cloud Manager mitgeteilt, dass es sich um eine Konfigurationsbereitstellung handelt.

      c. **Geeignete Bereitstellungsumgebung auswählen**
      - Wählen Sie die Umgebung aus, in der Sie die Konfiguration bereitstellen möchten. In diesem Fall handelt es sich um eine `dev` Umgebung.

      d. **Definieren von Source-Code-Details**

      - **Repository**: Wählen Sie das Repository aus, das Ihre `api.yaml` enthält. Wählen Sie beispielsweise das `AEMFormsInternal-ReleaseSanity-p43162-uk59167` Repository aus.
      - **Git-Verzweigung**: Wählen Sie Ihre Verzweigung aus. In diesem Fall wird unser Code beispielsweise in der `main` bereitgestellt.
      - **Code-Speicherort**: Geben Sie den Pfad zu `config` Verzeichnis ein. Da sich `api.yaml` im Stammordner `config` befindet, geben Sie `/config` ein

      e. Klicken Sie auf **„Speichern**, um die Pipeline zu erstellen

      ![Pipeline konfigurieren](/help/forms/assets/confirm-pipeline-1.png)

6. **Konfiguration bereitstellen**

   Nachdem die Pipeline erstellt wurde, stellen Sie Ihre `api.yaml`-Konfiguration bereit:

   1. **Aus der Pipeline-Übersicht**
      1. Suchen Sie auf der Seite Programmübersicht die Karte **Pipelines**
      2. Navigieren Sie zur neu erstellten Konfigurations-Pipeline in der Liste. Suchen Sie beispielsweise nach dem von Ihnen erstellten Pipeline-Namen (z. B. „api-config-pipeline„). Sie können Pipeline-Details einschließlich Status und letzter Ausführung sehen.

   2. **Bereitstellung starten**
      1. Klicken Sie auf die **„Erstellen**-Schaltfläche (oder das Wiedergabesymbol ▶) neben Ihrer Pipeline
      2. Bestätigen Sie die Bereitstellung, wenn Sie dazu aufgefordert werden und die Pipeline-Ausführung beginnt

      ![Pipeline ausführen](/help/forms/assets/run-config-pipeline.png)

   3. **Überprüfen der erfolgreichen Bereitstellung**
      - Warten Sie, bis die Pipeline abgeschlossen ist.
         - Wenn dies erfolgreich ist, ändert sich der Status in „Erfolg“ (grünes Häkchen ✓).
         - Wenn dies fehlschlägt, ändert sich der Status in „Fehlgeschlagen“ (rotes Kreuz ✗). Klicken Sie **Protokolle herunterladen**, um die Fehlerdetails anzuzeigen.

           ![Pipeline-Erfolg](/help/forms/assets/pipeline-suceess.png)

      Jetzt können Sie mit dem Testen der Forms Communications-APIs beginnen. Zu Testzwecken können Sie die Postman, curl oder einen anderen REST-Client verwenden, um die APIs aufzurufen.

### Schritt 5: API-Spezifikationen und -Tests

Nachdem Sie Ihre Umgebung konfiguriert haben, können Sie mit dem Testen der AEM Forms-Kommunikations-APIs entweder mit der [Swagger-Benutzeroberfläche](#a-using-swagger-ui-for-api-testing) oder programmgesteuert beginnen, indem Sie das NodeJS-Programm entwickeln.

In diesem Beispiel generieren wir eine PDF mithilfe der Document Services-APIs unter Verwendung der Vorlage und der XDP-Datei.

#### A. Verwenden der Swagger-Benutzeroberfläche für API-Tests

PDF Die Swagger-Benutzeroberfläche bietet eine interaktive Oberfläche zum Testen von APIs, ohne Code zu schreiben. Verwenden Sie die Funktion &quot;**ausprobieren**, um die Document Service[API zum Generieren von ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) aufzurufen und zu testen.

1. Navigieren Sie zur API-Dokumentation
   - Forms-API: [Forms-API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)
   - Document Services: [Document Services-API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)
Öffnen Sie die [Document Services-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document) in Ihrem Browser.
2. Erweitern Sie den Abschnitt **Dokumenterstellung** und wählen Sie [Generiert ein ausfüllbares PDF-Formular aus einer XDP- oder PDF-Vorlage, optional mit Datenzusammenführung](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm).
3. Klicken Sie im rechten Bereich auf &quot;**ausprobieren**.

   ![Swagger-Tests für API](/help/forms/assets/api-doc-generation.png)
4. Geben Sie die folgenden Werte ein:

   | **Abschnitt** | **Parameter** | **Wert** |
   |--------------|---------------|------------|
   | bucket | AEM-Instanz | AEM-Instanzname ohne den Adobe-Domänennamen (`.adobeaemcloud.com`) Verwenden Sie beispielsweise `p43162-e177398` als Bucket. |
   | Sicherheit | Bearer Token | Verwenden Sie das Zugriffstoken aus den OAuth-Server-zu-Server-Anmeldeinformationen des Adobe Developer Console-Projekts. |
   | Hauptteil | template | Laden Sie eine XDP-Datei hoch, um das PDF-Formular zu generieren. Sie können beispielsweise &quot;[ XDP“ verwenden](/help/forms/assets/ClosingForm.xdp) um eine PDF zu generieren. |
   | Hauptteil | data | Eine optionale XML-Datei mit den Daten, die mit der Vorlage zusammengeführt werden sollen, um ein vorausgefülltes PDF-Formular zu generieren. Sie können beispielsweise &quot;[ XML“ verwenden](/help/forms/assets/ClosingForm.xml) um eine PDF zu generieren. |
   | Parameter | X-Adobe-Accept-Experimental | 1 |

5. Klicken Sie auf **Senden**, um die API aufzurufen

   ![API senden](/help/forms/assets/api-send.png)

6. Überprüfen Sie die Antwort auf der Registerkarte **Antwort**:
   - Wenn der Antwort-Code `200` ist, bedeutet dies, dass die PDF erfolgreich erstellt wurde.
   - Wenn der Antwort-Code `400` ist, bedeutet dies, dass die Anfrageparameter ungültig oder fehlerhaft sind.
   - Wenn der Antwort-Code `500` ist, bedeutet dies, dass ein interner Server-Fehler vorliegt.

   In diesem Fall lautet der Antwort-Code `200`. Das bedeutet, dass die PDF erfolgreich generiert wurde:

   ![Überprüfungsantwort](/help/forms/assets/api-success.png)

   Jetzt können Sie die [erstellte PDF](/help/forms/assets/create-pdf.pdf) über die Schaltfläche **Herunterladen** herunterladen und in PDF Viewer anzeigen:

   ![PDF anzeigen](/help/forms/assets/create-pdf.png)

>[!NOTE]
>
> Zu Testzwecken können Sie auch den [Postman](https://www.postman.com/), [curl](https://curl.se/) oder einen anderen REST-Client verwenden, um die AEM-APIs aufzurufen.

#### B. Programmgesteuert durch Entwickeln eines NodeJS-Programms

Entwickeln Sie eine Node.js-Anwendung, um ein ausfüllbares PDF-Formular aus einer **XDP**-Vorlage und einer **XML**-Datendatei mithilfe der **Document Services-API**

##### Voraussetzungen

- Auf Ihrem System installierte Node.js
- Aktive AEM as a Cloud Service Instanz
- Bearer-Token für die API-Authentifizierung von Adobe Developer Console
- XDP-Beispieldatei: [closingForm.xdp](/help/forms/assets/ClosingForm.xdp)
- XML-Beispieldatei: [closingForm.xml](/help/forms/assets/ClosingForm.xml)

Um die Node.js-Anwendung zu entwickeln, folgen Sie der schrittweisen Entwicklung:

##### Schritt 1: Erstellen Sie ein neues Node.js-Projekt

Öffnen Sie den Befehl/das Terminal und führen Sie die folgenden Befehle aus:

```bash
# Create a new directory
mkdir demo-nodejs-generate-pdf
cd demo-nodejs-generate-pdf

##### Initialize Node.js project
npm init -y
```

![Neues Node-JS-Projekt erstellen](/help/forms/assets/api-1.png)

##### Schritt 2: Installieren erforderlicher Abhängigkeiten

Installieren Sie die **node-fetch**, **dotenv** und **form-data**-Bibliotheken, um HTTP-Anfragen zu stellen, Umgebungsvariablen zu lesen und Formulardaten zu verarbeiten.

```bash
npm install node-fetch
npm install dotenv
npm install form-data
```

![npm-Abhängigkeiten installieren](/help/forms/assets/api-2.png)

##### Schritt 3: Aktualisieren Sie package.json

1. Öffnen Sie den Befehl cmd/Terminal und führen Sie den Befehl aus:

   ```bash
   code .
   ```

   ![Projekt im Editor öffnen](/help/forms/assets/api-3.png)

   Das Projekt wird im Code-Editor geöffnet.

2. Aktualisieren Sie die `package.json` Datei , um die `type` zu `module` hinzuzufügen.

   ```bash
   {
   "name": "demo-nodejs-generate-pdf",
   "version": "1.0.0",
   "type": "module",
   "main": "index.js",
   }
   ```

   ![Paketdatei aktualisieren](/help/forms/assets/api-4.png)

##### Schritt 4: Erstellen einer .env-Datei

1. Erstellen der .env-Datei auf der Stammebene eines Projekts
2. Fügen Sie die folgende Konfiguration hinzu und ersetzen Sie die Platzhalter durch die tatsächlichen Werte aus den OAuth Server-zu-Server-Anmeldeinformationen des ADC-Projekts.

   ```bash
   CLIENT_ID=<ADC Project OAuth Server-to-Server credential ClientID>
   CLIENT_SECRET=<ADC Project OAuth Server-to-Server credential Client Secret>
   SCOPES=<ADC Project OAuth Server-to-Server credential Scopes>
   ```

   ![Erstellen einer ENV-Datei](/help/forms/assets/api-5.png)

   >[!NOTE]
   >
   > Sie können die `CLIENT_ID`, `CLIENT_SECRET` und `SCOPES` aus dem Adobe Developer Console-Projekt kopieren.

##### Schritt 5: Erstellen Sie src/index.js

1. Erstellen `index.js` Datei auf der Stammebene des Projekts
2. Fügen Sie den folgenden Code hinzu und ersetzen Sie die Platzhalter durch die tatsächlichen Werte:

```javascript
// Import the dotenv configuration to load environment variables from the .env file
import "dotenv/config";

// Import fetch for making HTTP requests
import fetch from "node-fetch";
import fs from "fs";
import FormData from "form-data";

// REPLACE THE FOLLOWING VALUE WITH YOUR OWN
const bucket = <bucket-value>; // Your AEM Cloud Service Bucket name
const xdpFilePath = <xdp-file>;
const xmlFilePath = <xml-file>;

// Load environment variables
const clientId = process.env.CLIENT_ID;
const clientSecret = process.env.CLIENT_SECRET;
const scopes = process.env.SCOPES;

// Adobe IMS endpoint for obtaining an access token
const adobeIMSV3TokenEndpointURL = "https://ims-na1.adobelogin.com/ims/token/v3";

// Function to get an access token
const getAccessToken = async () => {
    console.log("Getting access token from IMS...");

    const options = {
        method: "POST",
        headers: {
            "Content-Type": "application/x-www-form-urlencoded",
        },
        body: `grant_type=client_credentials&client_id=${clientId}&client_secret=${clientSecret}&scope=${scopes}`,
    };

    const response = await fetch(adobeIMSV3TokenEndpointURL, options);
    const responseJSON = await response.json();

    console.log("Access token received.");
    return responseJSON.access_token;
};

// Function to generate PDF form from XDP and XML
const generatePDF = async () => {
    const accessToken = await getAccessToken();

    console.log("Generating PDF form from XDP and XML...");

    // Read XDP and XML files
    const xdpFile = fs.readFileSync(xdpFilePath);
    const xmlFile = fs.readFileSync(xmlFilePath);

    const url = `https://${bucket}.adobeaemcloud.com/adobe/document/generate/pdfform`;

    const formData = new FormData();
    formData.append("template", xdpFile, {
        filename: "form.xdp",
        contentType: "application/vnd.adobe.xdp+xml"
    });
    formData.append("data", xmlFile, {
        filename: "data.xml",
        contentType: "application/xml"
    });

    const response = await fetch(url, {
        method: "POST",
        headers: {
            Authorization: `Bearer ${accessToken}`,
            "X-Api-Key": clientId,
            "X-Adobe-Accept-Experimental": "1",
            ...formData.getHeaders()
        },
        body: formData,
    });

    if (response.ok) {
        const arrayBuffer = await response.arrayBuffer();
        fs.writeFileSync("generatedForm.pdf", Buffer.from(arrayBuffer));
        console.log("✅ PDF form generated successfully (saved as generatedForm.pdf)");
    } else {
        console.error("❌ Failed to generate PDF. Status:", response.status);
        console.error(await response.text());
    }
};

// Run the PDF generation function
generatePDF();
```

![index.js erstellen](/help/forms/assets/api-6.png)

##### Schritt 6: Anwendung ausführen

```bash
node src/index.js
```

![Anwendung ausführen](/help/forms/assets/api-7.png)

Die PDF wird im `demo-nodejs-generate-pdf` erstellt. Navigieren Sie zum Ordner , um die generierte Datei mit dem Namen `generatedForm.pdf` zu finden.

![Erstellte PDF anzeigen](/help/forms/assets/api-8.png)

Sie können die [generierte PDF](/help/forms/assets/create-pdf.png) öffnen, um sie anzuzeigen.

## Fehlerbehebung

### Häufige Probleme und mögliche Ursachen

#### Problem 1: 403 Verbotener Fehler

**Symptome:**

- API-Anfragen geben `403 Forbidden` zurück
- Fehlermeldung: *Zugriff verweigert* oder *Unzureichende Berechtigungen*
- Tritt auch bei einem gültigen Zugriffstoken auf

**Mögliche Ursachen:**

- Unzureichende Berechtigungen im Produktprofil, die mit den OAuth Server-zu-Server-Anmeldeinformationen verknüpft sind
- Der Dienstbenutzergruppe in der AEM-Autoreninstanz fehlen die erforderlichen Berechtigungen für die erforderlichen Inhaltspfade

#### Problem 2: 401 Nicht autorisierter Fehler

**Symptome:**

- API-Anfragen geben `401 Unauthorized` zurück
- Fehlermeldung: *Ungültiges oder abgelaufenes Token*

**Mögliche Ursachen:**

- Zugriffstoken abgelaufen (nur für 24 Stunden gültig)
- Falsche oder nicht übereinstimmende Client-ID und Client-Geheimnis
- Fehlende oder falsch formatierte Authentifizierungskopfzeilen in der API-Anfrage

#### Problem 3: Fehler „404 Nicht gefunden“

**Symptome:**

- API-Anfragen geben `404 Not Found` zurück
- Fehlermeldung: *Ressource nicht gefunden* oder *API-Endpunkt nicht gefunden*

**Mögliche Ursachen:**

- Client-ID nicht in der `api.yaml` der AEM-Instanz registriert
- Falscher Bucket-Parameter (stimmt nicht mit der AEM-Instanzkennung überein)
- Ungültige oder nicht vorhandene Ressourcen-ID (Formular oder Asset)

#### Problem 4: Die Option „Server-zu-Server-Authentifizierung“ ist nicht verfügbar

**Symptome:**

- OAuth-Server-zu-Server-Option fehlt oder ist in Adobe Developer Console deaktiviert

**Mögliche Ursache:**

- Der Benutzer, der die Integration erstellt, wird **zugehörigen Produktprofil** als Entwickler hinzugefügt

#### Problem 5: Pipeline-Bereitstellung schlägt fehl

**Symptome:**

- Pipeline-Ausführung konfigurieren schlägt fehl
- Bereitstellungsprotokolle enthalten Fehler im Zusammenhang mit `api.yaml`

**Mögliche Ursachen:**

- Ungültige YAML-Syntax (Einzug, Anführungszeichen oder Probleme mit dem Array-Format)
- `api.yaml` in falschem Verzeichnis platziert
- Fehlerhafte oder falsche Client-ID in der Konfiguration


## Verwandte Artikel

Informationen zum Einrichten einer Umgebung für Batch (asynchrone APIs) finden Sie unter [Batch-Verarbeitung in AEM Forms as a Cloud Service Communications](/help/forms/aem-forms-cloud-service-communications-batch-processing.md).
