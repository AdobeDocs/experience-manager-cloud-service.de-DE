---
title: Aktivieren der adaptiven Forms-Kernkomponenten in der as a Cloud Service und lokalen Entwicklungsumgebung von AEM Forms
seo-title: Step-by-Step Guide for enabling Adaptive Forms Core Components on AEM Forms as a Cloud Service and local development environment
description: In unserer schrittweisen Anleitung erfahren Sie, wie Sie die adaptiven Forms-Kernkomponenten in AEM Forms as a Cloud Service aktivieren können. Unser Tutorial führt Sie durch den Prozess, wodurch es einfach wird, diese leistungsstarke Funktion für Ihre AEM Forms-Umgebung zu aktivieren.
seo-description: Learn how to enable Adaptive Forms Core Components on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin
source-git-commit: 8c125d834ebfff5601f56646d59ce00a80fcc0ba
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 11%

---


# Aktivieren der adaptiven Forms-Kernkomponenten in der as a Cloud Service und lokalen Entwicklungsumgebung von AEM Forms {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

Durch die Aktivierung der Kernkomponenten für adaptive Formulare in AEM Forms as a Cloud Service können Sie mit der Erstellung, Veröffentlichung und Bereitstellung von auf Kernkomponenten basierenden adaptiven Formularen und Headless-Formularen beginnen, und zwar für mehrere Kanäle mithilfe der Instanzen von AEM Forms as a Cloud Service. Sie benötigen eine Umgebung mit aktivierten adaptiven Forms-Kernkomponenten, um Headless Adaptive Forms zu verwenden.

## Überlegungen

* Wenn Sie ein neues as a Cloud Service AEM Forms-Programm erstellen, [Adaptive Forms-Kernkomponenten und Headless-Adaptive Forms sind bereits für Ihre Umgebung aktiviert](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Wenn Sie über ein älteres as a Cloud Service Forms-Programm verfügen, in dem Kernkomponenten [nicht aktiviert](#enable-components)können Sie [Adaptive Forms-Kernkomponenten-Abhängigkeiten hinzufügen](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) in Ihr AEM as a Cloud Service Repository kopieren und das Repository in Ihren Cloud Service-Umgebungen bereitstellen, um Headless Adaptive Forms zu aktivieren.

* Wenn Ihre bestehende Cloud Service-Umgebung eine Option bietet, [Erstellen von auf Kernkomponenten basierenden adaptiven Forms](creating-adaptive-form-core-components.md), Adaptive Forms-Kernkomponenten und Headless-Adaptive Forms sind bereits für Ihre Umgebung aktiviert. Sie können auf Kernkomponenten basierende adaptive Forms als Headless-Formulare für Kanäle wie mobile, Web, native Apps und Dienste bereitstellen, für die eine Headless-Darstellung des adaptiven Forms erforderlich ist.


## Aktivieren der adaptiven Forms-Kernkomponenten und des Headless-Adaptiven Forms {#enable-headless-forms}

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um die adaptiven Forms-Kernkomponenten und die Headless-Adaptive Forms für eine as a Cloud Service AEM Forms-Umgebung zu aktivieren


![Kernkomponenten und Headless-adaptive Formulare aktivieren](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Klonen Sie Ihr as a Cloud Service AEM Forms-Git-Repository. {#clone-git-repository}

1. Anmelden bei [Cloud Manager](https://my.cloudmanager.adobe.com/) und wählen Sie Ihre Organisation und das Programm aus.

1. Navigieren Sie zum **Pipelines** Karte aus **Programmübersicht** klicken Sie auf die **Zugriff auf Repo Info** -Schaltfläche, um auf Ihr Git-Repository zuzugreifen und es zu verwalten. Die Seite enthält die folgenden Informationen:

   * URL zum Cloud Manager-Git-Repository.
   * Anmeldeinformationen des Git-Repositorys (Benutzername und Kennwort) Git-Benutzernamen.

   Klicken **Kennwort generieren** , um das Kennwort anzuzeigen oder zu generieren.

1. Öffnen Sie das Terminal oder die Eingabeaufforderung auf Ihrem lokalen Computer und führen Sie den folgenden Befehl aus:

   ```Shell
   git clone [Git Repository URL]
   ```

   Geben Sie bei Aufforderung die Anmeldeinformationen ein. Das Repository wird auf Ihrem lokalen Computer geklont.


## 2. Hinzufügen von Abhängigkeiten von adaptiven Forms-Kernkomponenten zu Ihrem Git-Repository {#add-adaptive-forms-core-components-dependencies}

1. Öffnen Sie den Ordner &quot;Git-Repository&quot;in einem Texteditor. Beispiel: VS Code.
1. Öffnen Sie die Datei `[AEM Repository Folder]\pom.xml`, um sie zu bearbeiten.
1. Ersetzen von Versionen der `core.forms.components.version`, `core.forms.components.af.version` und `core.wcm.components.version` Komponenten mit den in [Dokumentation zu Kernkomponenten](https://github.com/adobe/aem-core-forms-components). Wenn die Komponente nicht vorhanden ist, fügen Sie diese Komponenten hinzu.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.wcm.components.version>2.22.10</core.wcm.components.version>
       <core.forms.components.version>2.0.18</core.forms.components.version>
       <core.forms.components.af.version>2.0.18</core.forms.components.af.version>
   </properties>
   ```

   ![Erwähnen der neuesten Version der Forms-Kernkomponenten](/help/forms/assets/latest-forms-component-version.png)

1. Im Abschnitt Abhängigkeiten des `[AEM Repository Folder]\pom.xml` , fügen Sie die folgenden Abhängigkeiten hinzu und speichern Sie die Datei.

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

1. Öffnen Sie die Datei `[AEM Repository Folder]/all/pom.xml` zum Bearbeiten. Fügen Sie die folgenden Abhängigkeiten in die `<embeddeds>` und speichern Sie die Datei.

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
   >  Ersetzen `${appId}` mit Ihrer appId.
   >
   >  Suchen Sie nach `${appId}`in der `[AEM Repository Folder]/all/pom.xml` -Datei, suchen Sie die `-packages/application/install` Begriff. Der Text vor dem `-packages/application/install` ist `${appId}`. Der folgende Code beispielsweise `myheadlessform` is `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Im `<dependencies>` Abschnitt `[AEM Repository Folder]/all/pom.xml` , fügen Sie die folgenden Abhängigkeiten hinzu und speichern Sie die Datei:

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

1. Öffnen Sie `[AEM Repository Folder]/ui.apps/pom.xml` zur Bearbeitung. Fügen Sie die `af-core bundle` Abhängigkeiten erstellen und die Datei speichern.

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
1. Navigieren Sie zu Ihrer `[AEM Repository Folder]` und führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. Nachdem die Dateien in das Git-Repository übertragen wurden, [Pipeline ausführen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=de).

   Nach erfolgreicher Pipelineausführung sind die adaptiven Forms-Kernkomponenten für die entsprechende Umgebung aktiviert. Außerdem werden Ihrer as a Cloud Service Forms-Umgebung eine Vorlage für adaptive Forms (Kernkomponenten) und ein Design für Arbeitsfläche 3.0 hinzugefügt, die Ihnen Optionen zum Anpassen und Erstellen von Kernkomponenten auf Basis von Adaptives Forms bietet.


## Häufig gestellte Fragen {#faq}

### Was sind Kernkomponenten? {#core-components}

Die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind eine Reihe standardisierter Web Content Management (WCM)-Komponenten, mit denen AEM die Entwicklungszeit verkürzen und die Wartungskosten Ihrer Websites reduzieren können.

### Welche Funktionen wurden zur Aktivierung von Kernkomponenten hinzugefügt? {#core-components-capabilities}

Wenn die adaptiven Forms-Kernkomponenten für Ihre Umgebung aktiviert sind, werden Ihrer Umgebung eine leere, auf Kernkomponenten basierende Vorlage für adaptive Formulare und ein Canvas 3.0-Design hinzugefügt. Nachdem Sie die adaptiven Forms-Kernkomponenten für Ihre Umgebung aktiviert haben, können Sie Folgendes tun:

* [Erstellen von Kernkomponenten-basierten adaptiven Forms](/help/forms/creating-adaptive-form-core-components.md).
* [Erstellen von Kernkomponenten-basierten Vorlagen für adaptive Formulare](/help/forms/template-editor.md).
* [Benutzerdefinierte Designs für auf Kernkomponenten basierende adaptive Formularvorlagen erstellen](/help/forms/using-themes-in-core-components.md).
* [Bereitstellung von JSON-Darstellungen der Kernkomponente für adaptive Formulare in Kanälen wie Mobilgeräten, Web, nativen Apps und Diensten, für die die Headless-Darstellung eines Formulars erforderlich ist](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de).

### Sind adaptive Forms-Kernkomponenten für meine Umgebung aktiviert? {#enable-components}

So prüfen Sie, ob die Kernkomponenten der adaptiven Forms für Ihre Umgebung aktiviert sind:

1. [as a Cloud Service AEM Forms-Repository klonen](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Öffnen Sie die `[AEM Repository Folder]/all/pom.xml` -Datei Ihres AEM Forms Cloud Service-Git-Repositorys.

1. Suchen Sie nach den folgenden Abhängigkeiten:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-example-apps
   * core-forms-components-examples-content

   ![Suchen Sie das Artefakt core-forms-components-af-core in all/pom.xml .](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Wenn die Abhängigkeiten vorhanden sind, sind die adaptiven Forms-Kernkomponenten für Ihre Umgebung aktiviert.

