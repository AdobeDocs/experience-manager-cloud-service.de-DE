---
title: Wie aktivieren Sie die adaptiven Forms-Kernkomponenten in der as a Cloud Service und lokalen Entwicklungsumgebung von AEM Forms?
description: Erfahren Sie, wie Sie adaptive Forms-Kernkomponenten auf AEM Forms as a Cloud Service aktivieren.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin
exl-id: 32a574e2-faa9-4724-a833-1e4c584582cf
source-git-commit: 0f8aed76af4d2640094a76f2805f73a0a619e33f
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 91%

---

# Aktivieren der adaptiven Forms-Kernkomponenten {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/enable-adaptive-forms-core-components.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Durch die Aktivierung der adaptiven Forms-Kernkomponenten in AEM Forms as a Cloud Service können Sie mit der Erstellung, Veröffentlichung und Bereitstellung von Kernkomponenten auf Basis von Adaptive Forms und Headless Forms beginnen, indem Sie Ihre AEM Forms-Cloud Service-Instanzen für mehrere Kanäle verwenden. Sie benötigen eine Umgebung mit aktivierten Kernkomponenten für adaptive Formulare, um adaptive Headless-Formulare zu verwenden.

## Überlegungen

* Wenn Sie ein neues AEM Forms as a Cloud Service-Programm erstellen, sind die [Kernkomponenten von adaptiven Formularen und adaptiven Headless-Formularen bereits für Ihre Umgebung aktiviert](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Wenn Sie ein älteres Forms as a Cloud Service-Programm haben, in dem Kernkomponenten [nicht aktiviert sind](#enable-components), können Sie [Abhängigkeiten von Kernkomponenten adaptiver Formulare zu Ihrem AEM as a Cloud Service-Repository hinzufügen](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) und das Repository in Ihren Cloud Service-Umgebungen bereitstellen, um adaptive Headless-Formulare zu aktivieren.

* Wenn Ihre bestehende Cloud Service-Umgebung die Option zum [Erstellen von auf Kernkomponenten basierten adaptiven Formularen](creating-adaptive-form-core-components.md) bietet, sind Kernkomponenten für adaptive Formulare und adaptive Headless-Formulare bereits für Ihre Umgebung aktiviert und Sie können auf Kernkomponenten basierte adaptive Formulare als Headless-Formulare für Kanäle wie Mobile, Web, native Apps und Dienste bereitstellen, die eine Headless-Darstellung von adaptiven Formularen erfordern.


## Aktivieren der Kernkomponenten für adaptive Formulare und adaptive Headless-Formulare {#enable-headless-forms}

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um die Kernkomponenten für adaptive Formulare und adaptive Headless-Formulare für eine AEM Forms as a Cloud Service-Umgebung zu aktivieren


![Kernkomponenten und Headless-adaptive Formulare aktivieren](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Klonen Sie Ihr AEM Forms as a Cloud Service-Git-Repository {#clone-git-repository}

1. Melden Sie sich bei [Cloud Manager](https://my.cloudmanager.adobe.com/) an und wählen Sie Ihre Organisation und Ihr Programm aus.

1. Navigieren Sie von Ihrer **Programmübersichtsseite** zur Karte **Pipelines** und klicken Sie auf die Schaltfläche **Zugriff auf Repo Info**, um auf Ihr Git-Repository zuzugreifen und es zu verwalten. Die Seite enthält die folgenden Informationen:

   * Die URL zum Git-Repository von Cloud Manager.
   * Anmeldeinformationen des Git-Repositorys (Benutzername und Password), Git-Benutzername.

   Klicken Sie auf **Kennwort generieren**, um das Kennwort anzuzeigen oder zu generieren.

1. Öffnen Sie das Terminal oder eine Eingabeaufforderung auf Ihrem lokalen Computer und führen Sie den folgenden Befehl aus:

   ```Shell
   git clone [Git Repository URL]
   ```

   Geben Sie bei Aufforderung die Anmeldeinformationen ein. Das Repository wird auf Ihrem lokalen Computer geklont.


## 2. Hinzufügen von Abhängigkeiten von Kernkomponenten für adaptive Formulare zu Ihrem Git-Repository {#add-adaptive-forms-core-components-dependencies}

1. Öffnen Sie Ihren Git-Repository-Ordner in einem einfachen Texteditor. Beispiel: VS Code.
1. Öffnen Sie die Datei `[AEM Repository Folder]\pom.xml`, um sie zu bearbeiten.
1. Ersetzen Sie die Versionen der Komponenten `core.forms.components.version`, `core.forms.components.af.version` und `core.wcm.components.version` durch die in der [Dokumentation zu Kernkomponenten](https://github.com/adobe/aem-core-forms-components) angegebenen Versionen. Wenn die Komponente nicht vorhanden ist, fügen Sie diese Komponenten hinzu.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.wcm.components.version>2.22.10</core.wcm.components.version>
       <core.forms.components.version>2.0.18</core.forms.components.version>
       <core.forms.components.af.version>2.0.18</core.forms.components.af.version>
   </properties>
   ```

   ![Erwähnung der neuesten Version der Kernkomponenten für adaptive Formulare](/help/forms/assets/latest-forms-component-version.png)

1. Fügen Sie im Abschnitt „Abhängigkeiten“ der Datei `[AEM Repository Folder]\pom.xml` die folgenden Abhängigkeiten hinzu und speichern Sie die Datei.

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

1. Öffnen Sie die Datei `[AEM Repository Folder]/all/pom.xml`, um sie zu bearbeiten. Fügen Sie die folgenden Abhängigkeiten in den Abschnitt `<embeddeds>` ein und speichern Sie die Datei.

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
   >  Um Ihre `${appId}` zu finden, suchen Sie in der Datei `[AEM Repository Folder]/all/pom.xml` den Begriff `-packages/application/install`. Der Text vor dem Begriff `-packages/application/install` ist Ihre `${appId}`. Der folgende Code `myheadlessform` ist zum Beispiel `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Fügen Sie im Abschnitt `<dependencies>` der Datei `[AEM Repository Folder]/all/pom.xml` die folgenden Abhängigkeiten hinzu und speichern Sie die Datei:

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

* [Erstellen und Bereitstellen von aktualisiertem Code in einer AEM Forms as a Cloud Service-Umgebung](#core-components-on-aem-forms-cs)

### Erstellen und Bereitstellen von aktualisiertem Code in einer lokalen Entwicklungsumgebung {#core-components-on-aem-forms-local-sdk}

1. Öffnen Sie die Eingabeaufforderung oder das Terminal.

1. Navigieren Sie zum Stammverzeichnis Ihres Git-Repository-Projekts.

1. Führen Sie den folgenden Befehl aus, um das Paket für Ihre Umgebung zu erstellen:

   ```Shell
       mvn clean install
   ```



   Nachdem das Paket erfolgreich erstellt wurde, finden Sie es unter [Git-Repository-Ordner]\all\target\[appid].all-[version].zip

1. Verwenden Sie den [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de), um das Paket [AEM Archetyp-Projektordner]\all\target\[appid].all-[version].zip in der lokalen Entwicklungsumgebung bereitzustellen.


### Erstellen und Bereitstellen von aktualisiertem Code in einer AEM Forms as a Cloud Service-Umgebung {#core-components-on-aem-forms-cs}

1. Öffnen Sie das Terminal oder die Eingabeaufforderung.
1. Navigieren Sie zu Ihrem `[AEM Repository Folder]` und führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. Nachdem die Dateien in das Git-Repository übertragen wurden, [führen Sie die Pipeline aus](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=de).

   Nach erfolgreicher Ausführung der Pipeline sind die Kernkomponenten für adaptive Formulare für die entsprechende Umgebung aktiviert. Außerdem werden Ihrer Forms as a Cloud Service-Umgebung eine Vorlage für adaptive Formulare (Kernkomponenten) sowie ein Design für Canvas 3.0 hinzugefügt, was Ihnen Optionen zum Anpassen und Erstellen von Kernkomponenten auf Basis von adaptiven Formularen bietet.


## Häufig gestellte Fragen {#faq}

### Was sind Kernkomponenten? {#core-components}

Die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind eine Reihe von standardisierten Web Content Management(WCM)-Komponenten für AEM, die die Entwicklungszeit beschleunigen und die Wartungskosten Ihrer Websites reduzieren.

### Welche Funktionen werden hinzugefügt, wenn Kernkomponenten aktiviert sind? {#core-components-capabilities}

Wenn die Kernkomponenten für adaptive Formulare für Ihre Umgebung aktiviert sind, werden Ihrer Umgebung eine leere, auf Kernkomponenten basierende Vorlage für adaptive Formulare und ein Canvas 3.0-Design hinzugefügt. Nachdem Sie die Kernkomponenten für adaptive Formulare für Ihre Umgebung aktiviert haben, können Sie Folgendes tun:

* [Kernkomponenten-basierte adaptive Formulare erstellen](/help/forms/creating-adaptive-form-core-components.md).
* [Vorlagen für Kernkomponenten-basierte adaptive Formulare erstellen](/help/forms/template-editor.md).
* [Benutzerdefinierte Designs für Kernkomponenten-basierte adaptive Formulare erstellen](/help/forms/using-themes-in-core-components.md).
* [JSON-Darstellungen für Kernkomponenten-basierte adaptive Formulare in Kanälen wie Mobilgeräten, Web- und nativen Apps und Diensten bereitstellen, für die die Headless-Darstellung eines Formulars erforderlich ist](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de).

### Sind für meine Umgebung Kernkomponenten für adaptive Formulare aktiviert? {#enable-components}

So prüfen Sie, ob die Kernkomponenten für adaptive Formulare für Ihre Umgebung aktiviert sind:

1. [Klonen Sie Ihr AEM Forms as a Cloud Service-Repository](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Öffnen Sie die Datei `[AEM Repository Folder]/all/pom.xml` Ihres AEM Forms as a Cloud Service-Git-Repositorys.

1. Suchen Sie nach den folgenden Abhängigkeiten:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content

   ![Suchen Sie das Artefakt „core-forms-components-af-core“ in „all/pom.xml“.](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Wenn die Abhängigkeiten vorhanden sind, sind die Kernkomponenten für adaptive Formulare für Ihre Umgebung aktiviert.

>[!MORELIKETHIS]
>
>* [Erstellen eines adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)