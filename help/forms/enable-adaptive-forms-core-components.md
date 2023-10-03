---
title: Aktivieren der adaptiven Forms-Kernkomponenten in der as a Cloud Service und lokalen Entwicklungsumgebung von AEM Forms
description: Erfahren Sie, wie Sie adaptive Forms-Kernkomponenten auf AEM Forms as a Cloud Service aktivieren.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin
exl-id: 32a574e2-faa9-4724-a833-1e4c584582cf
source-git-commit: defeee2fee42c6274c71438d6f9fde6e49a05081
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 65%

---

# Aktivieren der adaptiven Forms-Kernkomponenten {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/enable-adaptive-forms-core-components.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Durch die Aktivierung der adaptiven Forms-Kernkomponenten in AEM Forms as a Cloud Service können Sie mit der Erstellung, Veröffentlichung und Bereitstellung von Kernkomponenten auf Basis von Adaptive Forms und Headless Forms beginnen, indem Sie Ihre AEM Forms-Cloud Service-Instanzen für mehrere Kanäle verwenden. Um adaptive Headless-Formulare verwenden zu können, müssen Sie die Kernkomponenten für adaptive Formulare in Ihrer Umgebung aktivieren.

## Überlegungen

* Wenn Sie ein neues as a Cloud Service AEM Forms-Programm erstellen, [Adaptive Forms-Kernkomponenten und Headless-Adaptive Forms sind bereits für Ihre Umgebung aktiviert](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Wenn Sie über ein älteres Forms as a Cloud Service-Programm verfügen, in dem die Kernkomponenten [nicht aktiviert sind](#enable-components), können Sie zu Ihrem AEM as a Cloud Service-Repository [Abhängigkeiten von Kernkomponenten für adaptive Formulare hinzufügen](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) und dieses in Ihren Cloud Service-Umgebungen nutzen, um adaptive Headless-Formulare zu aktivieren.

* Wenn Ihre bestehende Cloud Service-Umgebung eine Option bietet, [Erstellen von auf Kernkomponenten basierenden adaptiven Forms](creating-adaptive-form-core-components.md), Adaptive Forms-Kernkomponenten und Headless-Adaptive Forms sind bereits für Ihre Umgebung aktiviert. Sie können auf Kernkomponenten basierende adaptive Forms als Headless-Formulare für Kanäle wie mobile, Web, native Apps und Dienste bereitstellen, für die eine Headless-Darstellung des adaptiven Forms erforderlich ist.


## Aktivieren der adaptiven Forms-Kernkomponenten und des Headless-Adaptiven Forms {#enable-headless-forms}

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um die adaptiven Forms-Kernkomponenten und die Headless-Adaptive Forms für eine as a Cloud Service AEM Forms-Umgebung zu aktivieren


![Kernkomponenten und Headless-adaptive Formulare aktivieren](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Klonen Sie Ihr AEM Forms as a Cloud Service Git-Repository {#clone-git-repository}

1. Melden Sie sich bei [Cloud Manager](https://my.cloudmanager.adobe.com/) an und wählen Sie Ihr Unternehmen und das Programm aus.

1. Navigieren Sie zur Karte **Pipelines** auf der Seite **Programmübersicht** und klicken Sie auf **Auf Repo-Info zugreifen**, um Ihr Git-Repository zu öffnen und zu verwalten. Die Seite enthält folgende Informationen:

   * Die URL zum Cloud Manager-Git-Repository.
   * Anmeldeinformationen für das Git-Repository (Benutzername und Kennwort) Git-Benutzername.

   Klicken Sie auf **Kennwort generieren**, um das Kennwort anzuzeigen oder zu generieren.

1. Öffnen Sie das Terminal oder die Eingabeaufforderung auf Ihrem lokalen Computer und führen Sie folgenden Befehl aus:

   ```Shell
   git clone [Git Repository URL]
   ```

   Geben Sie die Anmeldeinformationen ein, wenn Sie dazu aufgefordert werden. Das Repository wird auf Ihrem lokalen Computer geklont.


## 2. Fügen Sie Abhängigkeiten von Kernkomponenten für adaptive Formulare zu Ihrem Git-Repository hinzu {#add-adaptive-forms-core-components-dependencies}

1. Öffnen Sie Ihren Git-Repository-Ordner in einem einfachen Texteditor. Beispiel: VS Code.
1. Öffnen Sie die Datei `[AEM Repository Folder]\pom.xml` zur Bearbeitung.
1. Ersetzen Sie die Versionen der Komponenten `core.forms.components.version`, `core.forms.components.af.version` und `core.wcm.components.version` durch die in der [Dokumentation zu Kernkomponenten](https://github.com/adobe/aem-core-forms-components) angegebenen Versionen. Wenn die Komponente nicht vorhanden ist, fügen Sie diese Komponenten hinzu.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.wcm.components.version>2.22.10</core.wcm.components.version>
       <core.forms.components.version>2.0.18</core.forms.components.version>
       <core.forms.components.af.version>2.0.18</core.forms.components.af.version>
   </properties>
   ```

   ![Erwähnung der neuesten Version der Forms-Kernkomponenten](/help/forms/assets/latest-forms-component-version.png)

1. Fügen Sie im Abschnitt Abhängigkeiten der Datei `[AEM Repository Folder]\pom.xml` folgende Abhängigkeiten hinzu und speichern Sie die Datei.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. Öffnen Sie die Datei `[AEM Repository Folder]/all/pom.xml`, um sie zu bearbeiten. Fügen Sie die folgenden Abhängigkeiten im Abschnitt `<embeddeds>` hinzu und speichern Sie die Datei.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  Ersetzen Sie `${appId}` durch Ihre appId.
   >
   >  Um Ihre `${appId}` zu finden, suchen Sie in der Datei `[AEM Repository Folder]/all/pom.xml` den Ausdruck `-packages/application/install`. Der Text vor dem Ausdruck `-packages/application/install` ist Ihre `${appId}`. Im folgenden Code ist zum Beispiel `myheadlessform` die `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Fügen Sie folgende Abhängigkeiten im Abschnitt `<dependencies>` der Datei `[AEM Repository Folder]/all/pom.xml` hinzu und speichern Sie die Datei:

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. Öffnen Sie `[AEM Repository Folder]/ui.apps/pom.xml` zur Bearbeitung. Fügen Sie die Abhängigkeit `af-core bundle` hinzu und speichern Sie die Datei.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >Achten Sie darauf, dass die folgenden Artefakte der Kernkomponenten von adaptiven Formularen nicht in Ihr Projekt eingeschlossen werden.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > und
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. Speichern und schließen Sie die Datei.

## 3. Erstellen und Bereitstellen des aktualisierten Codes

Stellen Sie den aktualisierten Code in Ihren lokalen Entwicklungs- und Cloud Service-Umgebungen bereit, um die Kernkomponenten in beiden Umgebungen zu aktivieren:

* [Erstellen und Bereitstellen von aktualisiertem Code in einer lokalen Entwicklungsumgebung (AEM as a Cloud Service SDK)](#core-components-on-aem-forms-local-sdk)

* [Erstellen und Bereitstellen von aktualisiertem Code in einer as a Cloud Service AEM Forms-Umgebung](#core-components-on-aem-forms-cs)

### Erstellen und Bereitstellen von aktualisiertem Code in einer lokalen Entwicklungsumgebung {#core-components-on-aem-forms-local-sdk}

1. Öffnen Sie die Eingabeaufforderung oder das Terminal.

1. Navigieren Sie zum Stammverzeichnis Ihres Git-Repository-Projekts.

1. Führen Sie den folgenden Befehl aus, um das Paket für Ihre Umgebung zu erstellen:

   ```Shell
       mvn clean install
   ```



   Nachdem das Paket erfolgreich erstellt wurde, finden Sie es unter [Git-Repository-Ordner]\all\target\[appid].all-[version].zip

1. Verwenden Sie die [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) zur Bereitstellung der [AEM Archetyp-Projektordner]\all\target\[appid].all-[version].zip-Paket in der lokalen Entwicklungsumgebung.


### Erstellen und Bereitstellen von aktualisiertem Code in einer as a Cloud Service AEM Forms-Umgebung {#core-components-on-aem-forms-cs}

1. Öffnen Sie das Terminal oder die Eingabeaufforderung.
1. Navigieren Sie zu Ihrem `[AEM Repository Folder]` und führen Sie folgende Befehle in der angegebenen Reihenfolge aus

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. Nach der Übertragung der Dateien in das Git-Repository können Sie die [Pipeline ausführen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=de).

   Nach erfolgreicher Pipeline-Ausführung sind die Kernkomponenten für adaptive Formulare für die entsprechende Umgebung aktiviert. Außerdem werden eine Vorlage für adaptive Formulare (Kernkomponenten) und ein Canvas 3.0-Design zu Ihrer Forms as a Cloud Service-Umgebung hinzugefügt, mit denen Sie adaptive Formulare auf Grundlage der Kernkomponenten anpassen und erstellen können.


## Häufig gestellte Fragen {#faq}

### Was sind Kernkomponenten? {#core-components}

Die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind eine Reihe standardisierter Web Content Management(WCM)-Komponenten für AEM, mit denen Sie die Entwicklungszeiten verkürzen und die Wartungskosten für Ihre Web-Seiten senken können.

### Welche Funktionen werden durch die Aktivierung der Kernkomponenten hinzugefügt? {#core-components-capabilities}

Nachdem Sie die Kernkomponenten der adaptiven Formulare für Ihre Umgebung aktiviert haben, werden eine leere Vorlage für adaptive Formulare und ein Canvas 3.0-Design zu Ihrer Umgebung hinzugefügt. Nachdem Sie die Kernkomponenten der adaptiven Formulare für Ihre Umgebung aktiviert haben, können Sie Folgendes tun:

* [Erstellen Sie adaptive Formulare auf Grundlage der Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md).
* [Erstellen Sie Vorlagen für adaptive Formulare auf Grundlage der Kernkomponenten](/help/forms/template-editor.md).
* [Erstellen Sie benutzerdefinierte Vorlagen-Designs für adaptive Formulare auf Grundlage der Kernkomponenten](/help/forms/using-themes-in-core-components.md).
* [Stellen Sie JSON-Darstellungen adaptiver Formulare auf Grundlage der Kernkomponenten für Kanäle wie Mobile, Web, native Apps und Dienste bereit, die eine Headless-Darstellung des Formulars erfordern](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de).

### Sind für meine Umgebung Kernkomponenten für adaptive Formulare aktiviert? {#enable-components}

So finden Sie heraus, ob die Kernkomponenten für adaptive Formulare für Ihre Umgebung aktiviert sind:

1. [Klonen Sie Ihr AEM Forms as a Cloud Service-Repository](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Öffnen Sie die Datei `[AEM Repository Folder]/all/pom.xml` Ihres AEM Forms Cloud Service-Git-Repositorys.

1. Suchen Sie nach folgenden Abhängigkeiten:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content

   ![Suchen Sie das Artefakt core-forms-components-af-core in all/pom.xml](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Wenn die Abhängigkeiten vorhanden sind, sind die Kernkomponenten für adaptive Formulare für Ihre Umgebung aktiviert.
