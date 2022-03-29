---
title: Abrufen von Zugriffsinformationen zum Git-Repository
description: Erfahren Sie, wie der Front-End-Entwickler Cloud Manager verwendet, um auf Git-Repository-Informationen zuzugreifen.
exl-id: 3ef1cf86-6da4-4c09-9cfc-acafc8f6dd5c
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 100%

---

# Abrufen von Zugriffsinformationen zum Git-Repository {#retrieve-access}

Erfahren Sie, wie der Front-End-Entwickler Cloud Manager verwendet, um auf Git-Repository-Informationen zuzugreifen.

## Die bisherige Entwicklung {#story-so-far}

Wenn Sie ein Front-End-Entwickler sind, der nur für die Anpassung des Sitedesigns verantwortlich ist, benötigen Sie keine Kenntnisse darüber, wie AEM eingerichtet wurde, und können zum Abschnitt [Ziel](#objective) dieses Dokuments wechseln.

Wenn Sie auch in der Rolle eines Cloud Manager- oder AEM-Administrators sowie eines Front-End-Entwicklers arbeiten, haben Sie im vorherigen Dokument der AEM-Journey zur schnellen Site-Erstellung, [Gewähren von Zugriff für Front-End-Entwickler](grant-access.md), gelernt, wie Sie den Front-End-Entwickler integrieren, damit er Zugriff auf das Git-Repository hat, und Sie sollten jetzt Folgendes wissen:

* Wie ein Front-End-Entwickler als Benutzer hinzugefügt wird.
* Wie dem Front-End-Entwickler die erforderlichen Rollen zugewiesen werden.

In diesem Artikel wird der nächste Schritt gemacht und gezeigt, wie der Front-End-Entwickler den Cloud Manager-Zugriff nutzt, um Anmeldeinformationen für den Zugriff auf das AEM-Git-Repository abzurufen.

Da nun eine Site basierend auf einer Vorlage erstellt wurde, eine Pipeline eingerichtet ist, der Front-End-Entwickler eingebunden wurde und alle benötigten Informationen hat, wird in diesem Artikel die Perspektive weg von den Administratoren und ausschließlich hin zur Front-End-Entwicklerrolle verschoben.

## Ziel {#objective}

In diesem Dokument wird erläutert, wie Sie als Front-End-Entwickler auf Cloud Manager zugreifen und Zugriffsberechtigungen für das AEM-Git-Repository abrufen können. Nach dem Lesen sollten Sie:

* Erfahren Sie ganz allgemein, was Cloud Manager ist.
* Rufen Sie Ihre Anmeldeinformationen ab, um auf AEM-Git zuzugreifen, damit Sie Ihre Anpassungen übernehmen können.

## Verantwortliche Rolle {#responsible-role}

Dieser Teil der Journey gilt für Front-End-Entwickler.

## Voraussetzungen {#requirements}

Das Tools zur schnellen Site-Erstellung ermöglicht es Front-End-Entwicklern, unabhängig zu arbeiten, ohne über Kenntnisse zu AEM oder dessen Einrichtung verfügen zu müssen. Der Cloud Manager-Administrator muss jedoch den Front-End-Entwickler in das Projekt-Team aufnehmen und der AEM-Administrator muss Ihnen einige erforderliche Informationen zur Verfügung stellen. Stellen Sie sicher, dass Sie über die folgenden Informationen verfügen, bevor Sie fortfahren.

* Vom AEM-Administrator:
   * Quelldateien für Designs zum Anpassen
   * Pfad zu einer Beispielseite, die als Referenz verwendet werden soll
   * Proxy-Benutzeranmeldeinformationen zum Testen Ihrer Anpassungen mit Live-AEM-Inhalt
   * Anforderungen an das Front-End-Design
* Vom Cloud Manager-Administrator:
   * Eine Begrüßungs-E-Mail von Cloud Manager, die Sie über den Zugriff informiert
   * Name des Programms oder dessen URL innerhalb von Cloud Manager

Wenn eines dieser Elemente fehlt, wenden Sie sich an den AEM-Administrator oder den Cloud Manager-Administrator.

Es wird davon ausgegangen, dass der Front-End-Entwickler über umfassende Erfahrung mit Front-End-Entwicklungs-Workflows sowie allgemeinen installierten Tools verfügt. Beispiele:

* Git
* npm
* Webpack
* Bevorzugter Editor

## Grundlegendes zu Cloud Manager {#understanding-cloud-manager}

Cloud Manager ermöglicht Unternehmen die Selbstverwaltung von AEM in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen.

Der Front-End-Entwickler hat dadurch folgende Möglichkeiten:

* Zugreifen auf AEM-Git-Repository-Informationen, damit Sie Ihre Front-End-Anpassungen übernehmen können.
* Starten der Bereitstellungs-Pipeline, um Ihre Anpassungen bereitzustellen.

Der Cloud Manager-Administrator hat Sie als Cloud Manager-Benutzer integriert. Sie sollten eine Begrüßungs-E-Mail wie die folgende erhalten haben.

![Begrüßungs-E-Mail](assets/welcome-email.png)

Wenn Sie diese E-Mail nicht erhalten haben, wenden Sie sich an den Cloud Manager-Administrator.

## Zugreifen auf Cloud Manager {#access-cloud-manager}

1. Melden Sie sich bei Adobe Experience Cloud unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an oder klicken Sie auf den in der Begrüßungs-E-Mail angegebenen Link.

1. Cloud Manager listet die verschiedenen verfügbaren Programme auf. Tippen oder klicken Sie auf das Programm, auf das Sie zugreifen müssen, wie vom Cloud Manager-Administrator angegeben. Wenn dies Ihr erstes Front-End-Projekt für AEMaaCS ist, ist wahrscheinlich nur ein Programm verfügbar.

   ![Auswählen eines Programms in Cloud Manager](assets/cloud-manager-select-program.png)

Jetzt sehen Sie einen Überblick über Ihr Programm. Ihre Seite sieht anders aus, ähnelt aber diesem Beispiel.

![Übersicht über Cloud Manager](assets/cloud-manager-overview.png)

## Abrufen von Repository-Zugriffsinformationen {#repo-access}

1. Tippen oder klicken Sie im Abschnitt **Pipelines** auf der Cloud Manager-Seite auf die Schaltfläche **Auf Repository-Informationen zugreifen**.

   ![Pipelines](assets/pipelines-repo-info.png)

1. Das Dialogfeld **Repository-Informationen** wird geöffnet.

   ![Repo-Info](assets/repo-info.png)

1. Tippen oder klicken Sie auf die Schaltfläche **Kennwort generieren**, um ein Passwort für sich selbst zu erstellen.

1. Speichern Sie das generierte Passwort in einem sicheren Passwort-Manager. Das Passwort wird nicht wieder angezeigt.

1. Kopieren Sie außerdem die Felder **Benutzername** und **Git-Befehlszeile**. Sie nutzen diese Informationen später, um auf das Repository zuzugreifen.

1. Tippen oder klicken Sie auf **Schließen**.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der AEM-Journey zur schnellen Site-Erstellung abgeschlossen haben, sollten Sie:

* Erfahren Sie ganz allgemein, was Cloud Manager ist.
* Rufen Sie Ihre Anmeldeinformationen ab, um auf AEM-Git zuzugreifen, damit Sie Ihre Anpassungen übernehmen können.

Nutzen Sie Ihre Kenntnisse und fahren Sie mit der AEM-Journey zur schnellen Site-Erstellung fort, indem Sie das Dokument [Anpassen des Sitedesigns](customize-theme.md) lesen. Hier erfahren Sie, wie das Sitedesign erstellt, angepasst und mit Live-AEM-Inhalt getestet wird.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, mit dem nächsten Teil der Journey zur schnellen Site-Erstellung fortzufahren, indem Sie das Dokument [Anpassen des Sitedesigns](customize-theme.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Sie sind jedoch nicht erforderlich, um die Journey fortzusetzen.

* [Dokumentation zu Adobe Experience Manager Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=de) – Vollständige Details zu den Funktionen finden Sie in der Dokumentation zu Cloud Manager.
