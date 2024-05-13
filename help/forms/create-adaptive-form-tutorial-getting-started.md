---
title: Erste Schritte mit Adaptive Forms.
description: Erfahren Sie mit unserem schrittweisen Tutorial, wie Sie Mobile-responsive adaptive Formulare erstellen. Diese Formulare passen sich geräteübergreifend nahtlos an und sorgen so für ein reibungsloses Erlebnis.
keywords: Adaptive Formulare, responsive Formulare, HTML5-Formulare
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 3eb2a7ce311f9e738a95ea5fcf6876f4df1fa648
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 6%

---


# Erstellen eines adaptiven Formulars (Kernkomponenten) - Tutorial

An diesem Tag und in diesem Alter erwarten die Benutzer ein mobilfreundliches Erlebnis für alle Interaktionen, und Formulare bilden keine Ausnahme. Adaptive Formulare können Ihnen dabei helfen, Formulare zu erstellen, die nicht nur für Mobilgeräte geeignet sind, sondern auch die Benutzerinteraktion verbessern und die Zeit für ihre Bearbeitung verkürzen.

Dieses Tutorial enthält eine schrittweise Anleitung zum Erstellen eines adaptiven Formulars. Er ist in einen Anwendungsfall und mehrere Handbücher unterteilt, die Ihnen jeweils zeigen, wie Sie Ihrem adaptiven Formular eine neue Funktion hinzufügen können.

Am Ende des Tutorials können Sie:

* Erstellen eines adaptiven Formulars und seines Datenmodells
* Gestalten eines adaptiven Formulars
* Erstellen von Geschäftsregeln mit dem Regeleditor für adaptive Formulare
* Vorausfüllen adaptiver Formularfelder
* Hinzufügen von e-Signaturen zu Ihrem Formular
* Protect Ihres Formulars von Bots mithilfe von Google reCAPTCHA
* Lokalisieren des adaptiven Formulars für verschiedene Sprachen
* Formular konfigurieren, um strukturierte Daten zu erstellen
* Einrichten des Formulars zum Senden von Daten an einen REST-Endpunkt
* Veröffentlichen des adaptiven Formulars


## Warum erstellen Sie auf Kernkomponenten basierende Formulare?

AEM Forms bietet Foundation-Komponenten und Kernkomponenten zum Erstellen von Formularen. Kernkomponenten sind der moderne und empfohlene Ansatz zum Erstellen neuer Formulare. Warum Kernkomponenten verwenden? Diese Komponenten sind einfach, Open-Source-Komponenten (verfügbar auf GitHub), bieten eine hervorragende Google Lighthouse- und Web-Vitals-Bewertung, sind barrierefrei und bieten alle bekannten Funktionen von AEM Sites (wie Versionierung und Lokalisierung). Darüber hinaus sind diese Komponenten einfacher zu gestalten. Sie können ihr Erscheinungsbild einfach gemäß den Branding-Richtlinien Ihres Unternehmens anpassen. Diese weisen keine Drittanbieterabhängigkeiten auf. Jeder Entwickler mit Kenntnissen in JavaScript und CSS kann diese Komponenten einfach anpassen.

![Warum erstellen Sie Kernkomponenten-basierte adaptive Forms? Diese Komponenten sind einfach, einfacher zu gestalten, bieten hohe Lightthouse-Punktzahl, unterstützen Barrierefreiheitsstandards, leicht anpassbare Open-Source-Elemente, auf GitHub verfügbar, keine Abhängigkeit von Drittanbieter-Bibliotheken und verfügen über fast keine Lernkurve für AEM Entwickler und AEM Autoren. Darüber hinaus verfügen die AEM Forms-Kernkomponenten über alle Funktionen AEM WCM-Kernkomponenten.](/help/forms/assets/cc-core-components-benefits.png)

## Anwendungsfall: Optimierte Eigenheimkreditvorqualifikation mit adaptiver Forms

In diesem Tutorial erstellen Sie ein adaptives Formular für eine große Bank. Der Anwendungsfall lautet:

Potenzielle Eigenheimkäufer besuchen die Website oder Zweigstelle der Bank, um die Möglichkeiten für Eigenheimdarlehen zu erkunden. Der herkömmliche Anwendungsprozess ist langwierig und überwältigend und erfordert häufig eine vorzeitige Dokumentation. Dies hindert einige Käufer daran, den Prozess einzuleiten, was sowohl die Lead-Generierung der Bank als auch die Fähigkeit des Käufers behindert, selbstbewusst nach ihrem Traumhaus zu suchen.

Sie werden gebeten, ein interaktives Formular für die Vorqualifizierung von Hypothekendarlehen zu entwickeln. Dieses Formular würde grundlegende Informationen sammeln, den Kreditnehmer auf der Grundlage seines Inputs vorqualifizieren, geschätzte Darlehensbeträge, potenzielle Ausfallauszahlungserfordernisse und Zinssätze auf der Grundlage verschiedener Darlehensarten anbieten. Vorqualifizierte Benutzer können einen vollständigen Kreditantrag direkt über das Vorqualifizierungsformular einreichen.

Das Formular würde mit adaptiven Formularen erstellt. Dies ermöglicht ein personalisiertes Erlebnis bei gleichzeitiger Erfassung der erforderlichen Finanzdaten für eine genaue Vorqualifizierung von Eigenheimdarlehen.

Nach Abschluss des Tutorials würde Ihr Formular wie folgt aussehen und funktionieren:

![Arbeitsformular hier hinzufügen](/help/forms/assets/cc-tutorial-final-form.png)

## Einrichten einer Entwicklungsumgebung

Sie können das adaptive Formular direkt auf Ihrem lokalen Computer erstellen und testen, bevor Sie es in einer Cloud Service-Umgebung bereitstellen. Adobe bietet ein AEM SDK für die lokale Entwicklung, mit dem Sie

* Lokales Erstellen, Anpassen und Testen von Formularen
* Designs für Formulare und Build-Konfigurationen lokal erstellen
* Stellen Sie Ihre fertigen Assets einfach in der Cloud bereit.

Die lokale Entwicklung mit AEM SDK spart Ihnen Zeit und vereinfacht den Entwicklungsprozess


**Bereit zum Beginnen?**

1. [Einrichten von Entwicklungstools für AEM Projekte](/help/forms/setup-local-development-environment.md#set-up-development-tools-for-aem-projects): Laden Sie die neueste Version von herunter und installieren Sie sie. [Java 11™](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#local-development-environment-set-up), [Git](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#install-git), [Node.js (npm)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#node-js), und [Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#install-maven). Installieren Sie außerdem einen Nur-Text-Editor. Die Beispiele in diesem Tutorial basieren auf Visual Studio Code.

1. [Installieren des AEM SDK](/help/forms/setup-local-development-environment.md#set-up-local-experience-manager-environment-for-development): Laden Sie die neueste Version des AEM SDK herunter und installieren Sie sie. Dies stellt die wichtigsten Instrumente für AEM Entwicklung dar. Beachten Sie die Version des AEM SDK.

   ![Softwareverteilung](/help/forms/assets/software-distribution.png)

   ![AEM SDK installieren](/help/forms/assets/start-aem-sdk.png)

1. [Hinzufügen des AEM Forms-Add-ons](/help/forms/setup-local-development-environment.md#add-forms-archive-to-local-author-and-publish-instances-and-configure-forms-specific-users): Laden Sie das AEM Forms-Add-on herunter und installieren Sie es, das mit der Version Ihres AEM SDK übereinstimmt, aus dem [Softwareverteilung](https://experience.adobe.com/#/downloads) Portal.
   ![install-aem-forms-add-on](/help/forms/assets/install-aem-forms-add-on.png)

   +++AEM Forms-Add-on installieren

       Um das AEM Forms-Add-on zu installieren, beenden Sie AEM SDK, fügen Sie die AEM Forms-Add-on-Datei (.far) zum Ordner &quot;AEM SDK/crx-quickstart/install&quot;hinzu und starten Sie AEM SDK neu.
   
+++

1. [Benutzerberechtigungen konfigurieren](/help/forms/setup-local-development-environment.md#configure-users-and-permissions): Erstellen Sie Benutzer mit Entwicklungs-, Authoring- und anderen Berechtigungen und fügen Sie diese Benutzer zu vordefinierten Formulargruppen hinzu.


1. [Adaptive Forms-Vorlagen hinzufügen](/help/forms/setup-local-development-environment.md#set-up-a-development-project-for-forms-based-on-experience-manager-archetype): Verwenden Sie AEM Archetypen 48 oder höher, um ein neues AEM-Projekt zu erstellen und es in Ihrem AEM SDK bereitzustellen. Das Projekt fügt Ihrem AEM SDK adaptive Forms-Vorlagen hinzu.

   +++Adaptive Forms-Vorlagen hinzufügen

   1. Führen Sie den folgenden Befehl aus, um ein AEM Projekt zu erstellen.

      ```
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion="48" -D appTitle=securbank -D appId=securbank -D groupId=com.securbank -D includeFormsenrollment="y" -D aemVersion="cloud"
      ```

      ![AEM-archetyoe-project](/help/forms/assets/aem-archetype-project.png)

   1. Stellen Sie das Projekt in Ihrer lokalen Entwicklungsumgebung bereit. Sie können folgenden Befehl verwenden, um die Bereitstellung für Ihre lokale Entwicklungsumgebung durchzuführen.

      ```
      cd securbank
      
      mvn -PautoInstallPackage clean install
      ```

+++

   Nach der Bereitstellung des AEM können Sie adaptive Forms-Vorlagen in Ihrer Umgebung sehen.

   ![Adaptive Formularvorlagen](/help/forms/assets/adaptive-forms-templates.png)

Eine schrittweise Anleitung zum Einrichten Ihrer lokalen AEM Forms-Entwicklungsumgebung finden Sie unter [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md)



## Nächster Schritt

Nach dem Konfigurieren der Entwicklungsumgebung können Sie ein adaptives Formular erstellen. Im nächsten Artikel lernen Sie

* Erstellen eines adaptiven Formulars aus der leeren Vorlage
* Layout-Felder zur Anzeige und einfachen Annahme von Informationen.
* Vorschau des Formulars

<!-- 

### Step 2: Create Form Data Model

A form data model lets you connect an adaptive form to disparate data sources. For example, AEM user profile, RESTful web services, SOAP-based web services, OData services, and relational databases. You can use the form data model with an adaptive form to retrieve, update, delete, and add data to connected data sources.

Goals of article:

* Create the form data model using Rest endpoint.
* Add data model objects so you can form the data model.
* Configure read and write services for the form data model.
* Test form data model and configured services with test data.

### Step 4: Apply rules to adaptive form fields

AEM Forms provide an editor to write rules on adaptive form objects. These rules define actions to trigger on form objects based on preset conditions, user inputs, and user actions on the form. It helps ensure accuracy and speeds up the form-filling experience.

Goals:

* Create and apply rules to adaptive form fields.
* Use rules to trigger form data model services to update the data to database.

### Step 5: Style your adaptive form

Adaptive forms provide OOTB themes and allows you to customize an existing theme to make a brand specific theme. 


A theme contains styling details for components and panels, and you can reuse a theme in different forms. Styles include properties such as background colors, state colors, transparency, alignment, and size. When you apply the theme to your form, the specified style reflects on corresponding components of your form.

Goals:

* Apply an out of the box theme to an adaptive form.
* Create your brand specific theme.


### Step 6: Publish your adaptive form

You can publish adaptive forms as a stand-alone form (single page application), include in AEM Sites page, or include in a non-AEM Sites page.

Goals:

* Publish the adaptive form as an AEM Page.
* Embed the adaptive form in an AEM Sites Page.
* Embed the adaptive form in an external webpage (a non-AEM webpage hosted outside AEM).

-->