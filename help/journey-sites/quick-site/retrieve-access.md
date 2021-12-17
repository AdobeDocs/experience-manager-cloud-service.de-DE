---
title: Git-Repository-Zugriffsinformationen abrufen
description: Learn how the front-end developer uses Cloud Manager to access git repository information.
source-git-commit: 5e1a89743c5ac36635a139ada690849507813c30
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 5%

---


# Retrieve Git Repository Access Information {#retrieve-access}

Erfahren Sie, wie der Frontend-Entwickler Cloud Manager verwendet, um auf Git-Repository-Informationen zuzugreifen.

## Die bisherige Entwicklung {#story-so-far}

Wenn Sie ein Frontend-Entwickler sind, der nur für die Anpassung des Site-Designs verantwortlich ist, benötigen Sie keine Kenntnisse darüber, wie AEM eingerichtet wurde, und können zum [Ziel](#objective) Abschnitt dieses Dokuments.

If you also serve the role of Cloud Manager or AEM administrator as well as front-end developer, you learned in the previous document of the AEM Quick Site Creation journey, [Grant Access to the Front-End Developer,](grant-access.md) how to onboard the front-end developer so they have access to the git repository, and you should now know:

* So fügen Sie einen Frontend-Entwickler als Benutzer hinzu.
* So gewähren Sie dem Frontend-Entwickler die erforderlichen Rollen.

In diesem Artikel wird im nächsten Schritt gezeigt, wie der Frontend-Entwickler den Cloud Manager-Zugriff nutzt, um Anmeldeinformationen für den Zugriff auf das AEM Git-Repository abzurufen.

Da nun eine Site basierend auf einer Vorlage erstellt wird, eine Pipeline eingerichtet ist, der Frontend-Entwickler integriert ist und alle benötigten Informationen enthält, verschiebt dieser Artikel die Perspektive weg von den Administratoren und ausschließlich hin zur Frontend-Entwicklerrolle.

## Ziel {#objective}

In diesem Dokument wird erläutert, wie Sie als Frontend-Entwickler auf Cloud Manager zugreifen und Zugriffsberechtigungen für das AEM Git-Repository abrufen können. Nach dem Lesen werden Sie:

* Erfahren Sie auf hoher Ebene, was Cloud Manager ist.
* Have retrieved your credentials to access the AEM git so you can commit your customizations.

## Verantwortliche Rolle {#responsible-role}

This part of the journey applies to the front-end developer.

## Voraussetzungen {#requirements}

The Quick Site Creation tool allows front-end developers to work independently without and knowledge of AEM or how it is set up. Der Cloud Manager-Administrator muss jedoch den Frontend-Entwickler in das Projektteam integrieren und der AEM Administrator muss Ihnen einige erforderliche Informationen zur Verfügung stellen. Make sure that you have the following information before continuing.

* Vom AEM Administrator:
   * Quelldateien für Designs zum Anpassen
   * Pfad zu einer Beispielseite, die als Referenz verwendet werden soll
   * Proxy-Benutzeranmeldeinformationen zum Testen Ihrer Anpassungen für Live-AEM
   * Anforderungen an die Frontend-Konstruktion
* Vom Cloud Manager-Administrator:
   * A welcome email from Cloud Manager informing you of access
   * Der Name des Programms oder die URL zu diesem innerhalb von Cloud Manager

If you are missing any of these items, please contact the AEM administrator or Cloud Manager administrator.

Es wird davon ausgegangen, dass der Frontend-Entwickler über umfassende Erfahrung mit Front-End-Entwicklungs-Workflows sowie allgemeinen installierten Tools verfügt, darunter:

* Git
* npm
* Webpack
* Bevorzugter Editor

## Grundlegendes zu Cloud Manager {#understanding-cloud-manager}

Cloud Manager enables organizations to self-manage AEM in the cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen.

Für den Frontend-Entwickler ist dies das Gateway zu:

* Greifen Sie auf AEM Git-Repository-Informationen zu, damit Sie Ihre Frontend-Anpassungen übernehmen können.
* Starten Sie die Bereitstellungs-Pipeline, um Ihre Anpassungen bereitzustellen.

Der Cloud Manager-Administrator hat Sie als Cloud Manager-Benutzer integriert. You should have received a welcome email similar to the following.

![Welcome email](assets/welcome-email.png)

Wenn Sie diese E-Mail nicht erhalten haben, wenden Sie sich an den Cloud Manager-Administrator.

## Access Cloud Manager {#access-cloud-manager}

1. Log into Adobe Experience Cloud at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) or click on the link provided in the welcome email.

1. Cloud Manager listet die verschiedenen verfügbaren Programme auf. Tippen oder klicken Sie auf das Element, auf das Sie zugreifen müssen, wie vom Cloud Manager-Administrator bereitgestellt. Wenn dies Ihr erstes Frontend-Projekt für AEMaaCS ist, ist wahrscheinlich nur ein Programm verfügbar.

   ![Auswählen eines Programms in Cloud Manager](assets/cloud-manager-select-program.png)

Jetzt sehen Sie einen Überblick über Ihr Programm. Ihre Seite sieht anders aus, ähnelt aber diesem Beispiel.

![Übersicht über Cloud Manager](assets/cloud-manager-overview.png)

## Abrufen von Repository-Zugriffsinformationen {#repo-access}

1. In the **Pipelines** section of the Cloud Manager page, tap or click the **Access Repo Info** button.

   ![Pipelines](assets/pipelines-repo-info.png)

1. Die **Repository-Informationen** wird geöffnet.

   ![Repo Info](assets/repo-info.png)

1. Tap or click the **Generate password** button to create a password for yourself.

1. Speichern Sie das generierte Kennwort in einem sicheren Kennwortmanager. Das Kennwort wird nie wieder angezeigt.

1. Also copy the **username** and **Git command line** fields. You will use this information later to access the repo.

1. Tippen oder klicken Sie auf **Schließen**.

## Wie geht es weiter {#what-is-next}

Now that you have completed this part of the AEM Quick Site Creation journey you should:

* Erfahren Sie auf hoher Ebene, was Cloud Manager ist.
* Sie haben Ihre Anmeldeinformationen abgerufen, um auf das AEM Git zuzugreifen, damit Sie Ihre Anpassungen übernehmen können.

Build on this knowledge and continue your AEM Quick Site Creation journey by next reviewing the document [Customize the Site Theme,](customize-theme.md) where you will learn how the site theme is built, how to customize, and how to test using live AEM content.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Journey zur Schnellseitenerstellung zu wechseln, indem Sie das Dokument lesen [Anpassen des Site-Designs,](customize-theme.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf dem Journey weiterarbeiten müssen.

* [Adobe Experience Manager Cloud Manager Documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=de) - Explore the Cloud Manager documentation for full details of its features.
