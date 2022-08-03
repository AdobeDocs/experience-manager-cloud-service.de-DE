---
title: AEM as a Cloud Service Einführung in Onboarding-Journey
description: Beginnen Sie hier für einen Überblick über die geführte Journey durch den Onboarding-Prozess zu AEM as a Cloud Service.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
source-git-commit: 75c0e8cbaa409fa48750e794c27ace98eda107d0
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 25%

---


# Onboarding-Tour {#onboarding-journey}

Herzlichen Glückwunsch zur Auswahl AEM as a Cloud Service! Dieses Dokument ist der Ausgangspunkt für ein geführtes Journey durch den Onboarding-Prozess. Unabhängig davon, ob Sie eine neue Anwendung bereitstellen oder eine bestehende migrieren, stellt diese Onboarding-Journey sicher, dass Ihre Teams eingerichtet sind und Zugriff auf AEM as a Cloud Service haben.

## Einführung {#introduction}

Beim Onboarding wird ein bestimmter Systemadministrator AEM as a Cloud Service für Ihr Unternehmen eingerichtet. Dazu gehört die anfängliche Bereitstellung von Cloud-Ressourcen und die Zuweisung von Benutzern zu Rollen, basierend auf ihrer Aufgabenstellung. Dadurch kann sich jedes Mitglied anmelden und auf seine AEM as a Cloud Service-Ressourcen zugreifen.

![Onboarding-Journey](/help/journey-onboarding/assets/onboarding-journey.png)

Dieser Leitfaden führt Sie durch die wichtigsten Onboarding-Themen, sodass Sie nach Abschluss Folgendes haben:

* Umfassendes Verständnis der verschiedenen Begriffe, Dienste und Benutzer, die am Onboarding-Prozess beteiligt sind.
* Ihrem Team wurde ermöglicht, die ersten Schritte zu unternehmen, um Inhalte für Ihr AEM as a Cloud Service-Programm zu erstellen und zu entwickeln.

Das führt zu folgenden Problemen:

* Ihr Team wird eingerichtet und hat Zugriff auf Cloud-Ressourcen.
* AEM Autoren haben Zugriff auf AEM as a Cloud Service und können mit der Erstellung von Inhalten beginnen.
* AEM Entwickler und Bereitstellungsmanager haben Zugriff auf AEM as a Cloud Service und können mit der Erstellung und Bereitstellung benutzerdefinierter Programme beginnen.

## Konzepte und Ziele {#concepts}

Auch wenn bei den ersten Schritten mit AEM as a Cloud Service viel zu lernen scheint, gibt es konzeptionell nur einige logische Teile.

* **Der Vertrag** - Sie müssen mit Ihrem Adobe-Vertrag vertraut sein, da er Aspekte des Onboarding-Prozesses definiert.
* **Admin Console** - Hier werden Benutzer verwaltet und Rollen zugewiesen.
* **Cloud Manager** - Dies ist das Tool zum Einrichten von Ressourcen wie Programmen und Umgebungen. Dort können Sie auch auf Git zugreifen und Pipelines erstellen, um Ihren benutzerdefinierten Code zu verwalten und bereitzustellen.

Diese Konzepte werden in dieser Onboarding-Journey detailliert beschrieben. Das Ziel besteht darin, dass Sie am Ende der Journey:

* Haben den erforderlichen Benutzern Zugriff auf AEMaaCS gewährt
* Sie haben die ersten Cloud-Ressourcen für Ihr Projekt eingerichtet
* Erfahren Sie, wie Sie Ihren ersten Code bereitstellen und Ihren ersten Inhalt erstellen.

Im Grunde werden Sie mit Ihrem neuen AEM as a Cloud Service Projekt auf den Boden stoßen!

## Zielgruppe {#audience}

Die Onboarding-Journey ist speziell für die **Systemadministrator** der neuen AEM as a Cloud Service und AEM des Kunden im Allgemeinen. Der Systemadministrator ist die Person, die nach der Unterzeichnung Ihres AEM as a Cloud Service Vertrags von Adobe zuerst kontaktiert wird, und ist in der Regel die erste Person, die auf Ihre AEM as a Cloud Service Ressourcen zugreift und diese eingerichtet hat. Wenn Sie dies lesen, sind Sie wahrscheinlich der Systemadministrator.

Der Systemadministrator verwaltet alle Aspekte der AEMaaCS-Benutzer seines Unternehmens, vom Zugriff auf Berechtigungen. Der Systemadministrator muss jedoch unterwegs mit anderen Personen interagieren.

| Rolle | Beschreibung | Rolle in der Tour |
|---|---|---|
| Systemadministrator | Ziel dieser Journey, bietet die anfängliche Bereitstellung von Cloud-Ressourcen und die Zuweisung von Benutzerrollen zu entsprechenden Rollen, die auf ihren Aufgaben basieren | Verwaltet alle Aspekte von Benutzern vom Zugriff auf Berechtigungen |
| Inhaltsautor | Erstellt und überprüft den Inhalt in AEM | Nachdem der Systemadministrator Berechtigungen erteilt hat, können Autoren ihre eigene Journey starten und Inhalte erstellen |
| Entwickler | Entwickelt AEM-Anwendungen, die Inhalte aus verschiedenen Quellen nutzen | Sobald Entwickler Berechtigungen vom Systemadministrator erhalten haben, können sie ihre eigenen Journey-Entwicklungslösungen starten |
| Deployment Manager | Fügt eine Umgebung hinzu oder aktualisiert sie, führt Pipelines aus und stellt Code für AEM Umgebung oder Codequalität bereit. | Sobald Bereitstellungsmanager Berechtigungen vom Systemadministrator erhalten haben, können sie mit der Verwaltung von Bereitstellungen durch ihre eigenen Journey beginnen |

Dieses Onboarding-Handbuch zeigt den vollständigen Prozess des Onboarding als Systemadministrator. Die Rollen von AEM-Benutzern, Entwicklern und Bereitstellungsmanagern werden kurz als zusätzliche, optionale Teile der Journey untersucht.

>[!TIP]
>
>Wenn Sie neu bei AEM as a Cloud Service sind, sich aber bereits mit AEM auskennen und von On-Premise- oder Adobe Managed Services migrieren, sollten Sie die Informationen unter [AEM Journey zur as a Cloud Service Migration.](/help/journey-migration/getting-started.md)

## Übersicht über Onboarding-Journey {#overview}

In den folgenden Artikeln werden die wichtigsten Onboarding-Konzepte detailliert beschrieben und Ihnen grundlegende Kenntnisse über AEM as a Cloud Service. Obwohl Sie direkt zu einem bestimmten Teil der Tour gehen können, beachten Sie, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Für Einsteiger empfiehlt sich daher, von vorn zu beginnen und schrittweise vorzugehen.

| Nummer | Artikel | Beschreibung | Zielgruppe |
|---|---|---|---|
| 0 | Onboarding-Tour | Dieses Dokument | Systemadministrator |
| 1 | [Onboarding-Vorbereitung](preparation.md) | Bevor der Onboarding-Prozess beginnt, muss der Systemadministrator eine Reihe oder vorbereitende Schritte durchführen, bevor er sich beim System anmeldet. | Systemadministrator |
| 2 | [AEM as a Cloud Service Terminologie](terminology.md) | Bevor Sie sich zum ersten Mal bei AEMaaCS anmelden, ist es hilfreich, einige Begriffe des Systems und seiner grundlegenden Struktur zu verstehen. | Systemadministrator |
| 3 | [Die Admin Console](admin-console.md) | Erfahren Sie, was die Admin Console ist, wie Sie sich anmelden und wie Sie Ihr Profil als Systemadministrator überprüfen können. | Systemadministrator |
| 4 | [Zuweisen von Cloud Manager-Produktprofilen](assign-profiles-cloud-manager.md) | Überprüfen Sie die Cloud Manager-Produktprofile und erfahren Sie, wie Sie Team-Mitglieder Cloud Manager-Produktprofilen zuweisen. | Systemadministrator |
| 5 | [Zugreifen auf Cloud Manager](cloud-manager.md) | Hier erfahren Sie, wie Sie auf Cloud Manager zugreifen können, damit Sie Ihre Projektressourcen einrichten können. | Systemadministrator |
| 6 | [Erstellen eines Programms](create-program.md) | Erfahren Sie, wie Sie ein Programm mit Cloud Manager erstellen. | Systemadministrator |
| 7 | [Umgebungen erstellen](create-environments.md) | Erfahren Sie, wie Sie eine Umgebung mit Cloud Manager erstellen. | Systemadministrator |
| 8 | [Zuweisen AEM Produktprofilen](assign-profiles-aem.md) | Erfahren Sie, wie ein Systemadministrator Ihre Team-Mitglieder AEM as a Cloud Service-Produktprofilen zuweist. | Systemadministrator |
| 9 | [Aufgaben für Entwickler und Bereitstellungs-Manager](developers.md) | Optional - Erfahren Sie, wie Sie als Entwickler auf Cloud Manager Git zugreifen und es verwalten können und wie Sie als Bereitstellungsmanager Pipelines einrichten und Code in Cloud Manager bereitstellen können. | Entwickler und Bereitstellungsmanager |
| 10 | [AEM Benutzeraufgaben](aem-users.md) | Optional - Erfahren Sie, wie Sie als AEM Autor auf AEM as a Cloud Service Instanz zugreifen und sich mit der Inhaltserstellung für AEM as a Cloud Service vertraut machen können. | AEM |

## Wie geht es weiter {#what-is-next}

Jetzt können Sie Ihre AEM as a Cloud Service Onboarding-Journey starten. Wir empfehlen Ihnen, mit dem nächsten Teil der Journey fortzufahren und den Artikel zu lesen [Onboarding-Vorbereitung](preparation.md)

## AEM-Dokumentations-Touren {#documentation-journeys}

[Eine Dokumentations-Tour](/help/journey-documentation/documentation-journeys.md) verbindet viele verschiedene und möglicherweise komplizierte Themen und Funktionen durch eine Erzählung, die dem nicht mit AEM vertrauten Leser hilft, ein geschäftliches Problem von Anfang bis Ende zu verstehen und zu lösen, wobei nur minimale Vorkenntnisse zum Thema oder zu AEM vorausgesetzt werden.

Dokumentations-Touren werden auf der Grundlage von Best-Practice-Prinzipien entwickelt, die auf Informationen aus den neuesten Forschungsergebnissen von Adobe, bewährten Implementierungserfahrungen der Adobe-Berater und dem Feedback aus Kundenprojekten basieren.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Ihr Team in Ihre neue AEM as a Cloud Service Applikation zu integrieren, können Sie damit beginnen!
