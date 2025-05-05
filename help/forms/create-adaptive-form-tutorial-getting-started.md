---
title: Erste Schritte mit Adaptive Forms.
description: Erfahren Sie mit unserem schrittweisen Tutorial, wie Sie Mobile-responsive adaptive Formulare erstellen. Diese Formulare passen sich geräteübergreifend nahtlos an und sorgen so für ein reibungsloses Erlebnis.
keywords: Adaptive Formulare, responsive Formulare, HTML5-Formulare
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
hide: true
hidefromtoc: true
exl-id: b59cb56c-9629-48e4-b5c9-a861013a1360
source-git-commit: af58a784f24f212962ad73f11015fb788493d8b5
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 6%

---

# Erstellen eines adaptiven Formulars (Kernkomponenten) - Tutorial

Heutzutage erwarten die Benutzer ein mobilfreundliches Erlebnis für alle ihre Interaktionen, und Formulare sind keine Ausnahme. Adaptive Formulare können Ihnen dabei helfen, nicht nur mobilfreundliche Formulare zu erstellen, sondern auch die Benutzerinteraktion zu verbessern und die Zeit bis zum Ausfüllen zu verkürzen.

In diesem Tutorial erfahren Sie Schritt für Schritt, wie Sie ein adaptives Formular erstellen. Es ist in einen Anwendungsfall und mehrere Handbücher unterteilt, die Ihnen jeweils zeigen, wie Sie Ihrem adaptiven Formular eine neue Funktion hinzufügen.

Am Ende der Schulung sind Sie in der Lage:

* Erstellen eines adaptiven Formulars und seines Datenmodells
* Gestalten eines adaptiven Formulars
* Erstellen von Geschäftsregeln mit dem Regeleditor für adaptive Formulare
* Vorausfüllen von Feldern in adaptiven Formularen
* Hinzufügen von E-Signaturen zu einem Formular
* Protect des Formulars von Bots mit Google reCAPTCHA
* Lokalisieren Sie Ihr adaptives Formular in verschiedene Sprachen
* Konfigurieren des Formulars zur Erstellung strukturierter Daten
* Einrichten des Formulars zum Senden von Daten an einen REST-Endpunkt
* Publish des adaptiven Formulars


## Warum sollten auf Kernkomponenten basierende Formulare erstellt werden?

AEM Forms stellt Foundation-Komponenten und Kernkomponenten zum Erstellen von Forms-Erlebnissen bereit. Kernkomponenten sind der moderne und empfohlene Ansatz zum Erstellen jedes neuen Forms-Erlebnisses. Warum sollten Sie Kernkomponenten verwenden? Diese Komponenten sind einfach, Open-Source-Komponenten (auf GitHub verfügbar), bieten einen hervorragenden Wert für Google Lighthouse und Web Vitals, sind mit der Barrierefreiheit kompatibel und bieten alle bekannten Funktionen von AEM Sites (wie Versionierung und Lokalisierung). Darüber hinaus sind diese Komponenten einfacher zu gestalten. Sie können ihr Erscheinungsbild einfach gemäß den Branding-Richtlinien Ihres Unternehmens anpassen. Diese weisen keine Abhängigkeiten von Drittanbietern auf. Jeder Entwickler mit Kenntnissen in JavaScript und CSS kann diese Komponenten einfach anpassen.

![Warum sollten Sie auf Kernkomponenten basierende adaptive Forms erstellen? Diese Komponenten sind leicht, einfacher zu gestalten, bieten eine hohe Lighthouse-Punktzahl, unterstützen Standards für die Barrierefreiheit, leicht anpassbar, Open-Source-Komponenten, auf GitHub verfügbar, keine Abhängigkeit von Drittanbieterbibliotheken und haben fast keine Lernkurve für AEM-Entwickler und AEM-Autoren Darüber hinaus verfügen AEM Forms-Kernkomponenten über alle Funktionen von AEM WCM-Kernkomponenten.](/help/forms/assets/cc-core-components-benefits.png){width="50%"}

## Anwendungsfall: Optimierte Vorqualifizierung für Heimdarlehen mit Adaptive Forms

In diesem Tutorial erstellen Sie ein adaptives Formular für eine große Bank. Der Anwendungsfall ist:

Potenzielle Eigenheimkäufer besuchen die Website oder Filiale der Bank, um die Möglichkeiten für Eigenheimkredite zu erkunden. Der herkömmliche Bewerbungsprozess ist langwierig und überwältigend und erfordert häufig eine Vorabdokumentation. Dies hält einige Käufer davon ab, den Prozess in Gang zu setzen, was sowohl die Lead-Generierung der Bank als auch die Fähigkeit des Käufers behindert, selbstbewusst nach ihrem Traumhaus zu suchen.

Sie haben die Aufgabe, ein interaktives Formular zur Vorauswahl für Wohnungsbaudarlehen zu entwickeln. Dieses Formular würde grundlegende Informationen sammeln, den Kreditnehmer auf der Grundlage seiner Eingabe vorqualifizieren, geschätzte Darlehensbeträge, potenziellen Anzahlungsbedarf und Zinssätze basierend auf verschiedenen Darlehensarten anbieten. Für vorqualifizierte Nutzer soll ein vollständiger Kreditantrag direkt über das Formular für die Vorqualifizierung gestellt werden.

Das Formular würde mit adaptiven Formularen erstellt. Dies ermöglicht ein personalisiertes Erlebnis bei gleichzeitiger Erfassung der erforderlichen Finanzdaten für eine genaue Präqualifikation für Wohnungsbaudarlehen.

Nach Abschluss des Tutorials würde Ihr Formular wie das folgende Formular aussehen und funktionieren:

![Hier ein Arbeitsformular hinzufügen](/help/forms/assets/cc-tutorial-final-form.png)

## Einrichten einer Entwicklungsumgebung

Sie können das adaptive Formular direkt auf Ihrem lokalen Computer erstellen und testen, bevor Sie es in einer Cloud Service-Umgebung bereitstellen. Adobe stellt eine AEM SDK für lokale Entwicklung bereit, mit der Sie

* Lokales Erstellen, Anpassen und Testen von Formularen.
* Designs für Formulare entwerfen und Konfigurationen lokal erstellen,
* Stellen Sie Ihre fertigen Assets einfach in der Cloud bereit.

Lokale Entwicklung mit AEM SDK spart Ihnen Zeit und vereinfacht den Entwicklungsprozess


**Bereit zum Starten?**

1. [Einrichten von Entwicklungstools für AEM-Projekte](/help/forms/setup-local-development-environment.md#set-up-development-tools-for-aem-projects): Laden Sie die neueste Version von [Java 11™](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#local-development-environment-set-up), [Git](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#install-git), [Node.js (npm)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#node-js) und [Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=de#install-maven) herunter und installieren Sie sie. Wenn Sie auch einen Nur-Text-Editor installieren, basieren die Beispiele in diesem Tutorial auf Visual Studio Code.

1. [AEM SDK installieren](/help/forms/setup-local-development-environment.md#set-up-local-experience-manager-environment-for-development): Laden Sie die neueste Version der AEM SDK herunter und installieren Sie sie. Damit stehen die wesentlichen Instrumente für die AEM-Entwicklung zur Verfügung. Notieren Sie sich die Version von AEM SDK.

   ![Software-Distribution](/help/forms/assets/software-distribution.png)

   ![Installieren von AEM SDK](/help/forms/assets/start-aem-sdk.png)

1. [AEM Forms-Add-on hinzufügen](/help/forms/setup-local-development-environment.md#add-forms-archive-to-local-author-and-publish-instances-and-configure-forms-specific-users): Laden Sie das AEM Forms-Add-on, das der Version Ihrer AEM-SDK entspricht, vom [Software Distribution](https://experience.adobe.com/#/downloads)Portal herunter und installieren Sie es.
   ![install-aem-forms-add-on](/help/forms/assets/install-aem-forms-add-on.png)

   +++Installieren des AEM Forms-Add-ons:

   So installieren Sie das AEM Forms-Add-on:

   1. AEM SDK stoppen.
   1. Fügen Sie die AEM Forms-Add-on-Datei (.far) zum `AEM SDK/crx-quickstart/install` hinzu.
   1. Starten Sie AEM SDK neu.

   +++

1. [Konfigurieren von Benutzerberechtigungen](/help/forms/setup-local-development-environment.md#configure-users-and-permissions): Erstellen Sie Benutzer mit Entwicklungs-, Authoring- und anderen Berechtigungen und fügen Sie diese Benutzer vordefinierten Formulargruppen hinzu.


1. [Adaptive Forms-Vorlagen hinzufügen](/help/forms/setup-local-development-environment.md#set-up-a-development-project-for-forms-based-on-experience-manager-archetype): Verwenden Sie AEM-Archetypen 48 oder höher, um ein neues AEM-Projekt zu erstellen und es in Ihrer AEM-SDK bereitzustellen. Das Projekt fügt Ihrer AEM-SDK Vorlagen für adaptive Forms hinzu.

   ![Adaptive Formularvorlagen](/help/forms/assets/adaptive-forms-templates.png)

   +++Hinzufügen von Vorlagen für adaptive Forms zu Ihrer AEM-SDK:

   1. Führen Sie den folgenden Befehl aus, um ein AEM-Projekt zu erstellen.

      ```
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion="48" -D appTitle=securbank -D appId=securbank -D groupId=com.securbank -D includeFormsenrollment="y" -D aemVersion="cloud"
      ```

      ![AEM-Archetype-Project](/help/forms/assets/aem-archetype-project.png)

   1. Stellen Sie das Projekt in Ihrer lokalen Entwicklungsumgebung bereit. Sie können folgenden Befehl verwenden, um die Bereitstellung für Ihre lokale Entwicklungsumgebung durchzuführen.

      ```
      cd securbank
      
      mvn -PautoInstallPackage clean install
      ```

   Nach der Bereitstellung des AEM-Projekts können Sie Vorlagen für adaptive Forms in Ihrer Umgebung sehen.

   +++


Detaillierte Anweisungen und eine schrittweise Anleitung zum Einrichten Ihrer lokalen AEM Forms-Entwicklungsumgebung finden Sie im Artikel [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md) .



## Nächster Schritt

Nach dem Konfigurieren der Entwicklungsumgebung können Sie ein adaptives Formular erstellen. Im nächsten Artikel lernen Sie Folgendes

* Erstellen eines adaptiven Formulars aus der leeren Vorlage
* Layout-Felder zum Anzeigen und einfachen Akzeptieren von Informationen.
* Vorschau des Formulars anzeigen.

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
