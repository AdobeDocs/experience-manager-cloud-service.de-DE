---
title: Einführung in die Onboarding-Tour durch AEM as a Cloud Service
description: Beginnen Sie hier für einen Überblick über die geführte Tour durch den Onboarding-Prozess bei AEM as a Cloud Service.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
source-git-commit: 75c0e8cbaa409fa48750e794c27ace98eda107d0
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 100%

---


# Onboarding-Tour {#onboarding-journey}

Herzlichen Glückwunsch zur Wahl von AEM as a Cloud Service! Dieses Dokument ist Ihr Ausgangspunkt für eine geführte Tour durch den Onboarding-Prozess. Unabhängig davon, ob Sie ein neues Programm bereitstellen oder ein bestehendes migrieren, stellt diese Onboarding-Tour sicher, dass Ihre Teams eingerichtet sind und Zugriff auf AEM as a Cloud Service haben.

## Einführung    {#introduction}

Onboarding ist der Vorgang, bei dem ein benannter Systemadministrator AEM as a Cloud Service für Ihre Organisation einrichtet. Dazu gehört die anfängliche Bereitstellung von Cloud-Ressourcen und die Zuweisung von Benutzern zu Rollen, basierend auf ihrer Aufgabenstellung. Dadurch kann sich jedes Mitglied anmelden und auf seine AEM as a Cloud Service-Ressourcen zugreifen.

![Die Onboarding-Tour](/help/journey-onboarding/assets/onboarding-journey.png)

Dieses Handbuch führt Sie durch die wichtigsten Onboarding-Themen, sodass Sie nach Abschluss Folgendes erreicht haben:

* Ein umfassendes Verständnis der verschiedenen Begriffe, Services und Benutzer, die am Onboarding-Prozess beteiligt sind.
* Ihrem Team wurde ermöglicht, loszulegen und die ersten Schritte zu unternehmen, um Inhalte für Ihr Programm mit AEM as a Cloud Service zu erstellen und zu entwickeln.

Das Ergebnis ist:

* Ihr Team ist eingerichtet und hat Zugriff auf Cloud-Ressourcen.
* AEM-Autoren haben Zugriff auf AEM as a Cloud Service und können mit der Erstellung von Inhalten beginnen.
* AEM-Entwickler und Implementierungs-Manager haben Zugriff auf AEM as a Cloud Service und können mit der Erstellung und Bereitstellung von benutzerdefinierten Programmen beginnen.

## Konzepte und Ziel {#concepts}

Auch wenn es zu Beginn der Arbeit mit AEM as a Cloud Service viel zu lernen gibt, sind es konzeptionell nur wenige, logische Teile.

* **Der Vertrag** – Sie müssen mit Ihrem Adobe-Vertrag vertraut sein, da er Aspekte des Onboarding-Prozesses definiert.
* **Admin Console** – Hier werden Benutzer verwaltet und Rollen zugewiesen.
* **Cloud Manager** – Dieses Werkzeug dient zum Einrichten von Ressourcen wie Programmen und Umgebungen. Zudem können Sie hierüber auf Git zugreifen und Pipelines zur Verwaltung und Bereitstellung Ihres benutzerdefinierten Codes erstellen.

Diese Konzepte werden in dieser Onboarding-Journey detailliert beschrieben. Das Ziel besteht darin, dass Sie am Ende der Tour:

* Den erforderlichen Benutzern Zugriff auf AEMaaCS gewährt haben
* Die ersten Cloud-Ressourcen für Ihr Projekt eingerichtet haben
* Wissen, wie Sie Ihren ersten Code bereitstellen und Ihre ersten Inhalte erstellen können.

Im Grunde werden Sie mit Ihrem neuen Projekt in AEM as a Cloud Service sofort durchstarten!

## Zielgruppe {#audience}

Die Onboarding-Tour wurde speziell für **System-Admins** von Kundinnen und Kunden geschrieben, für die AEM as a Cloud Service und AEM im Allgemeinen neu ist. Der Systemadministrator ist die Person, die nach der Unterzeichnung des Vertrags für AEM as a Cloud Service zum ersten Mal von Adobe kontaktiert wird, und in der Regel auch die erste Person, die auf Ihre Ressourcen für AEM as a Cloud Service zugreift und diese einrichtet. Wenn Sie dies lesen, sind Sie wahrscheinlich der Systemadministrator.

Der Systemadministrator verwaltet alle Aspekte der AEMaaCS-Benutzer seiner Organisation, vom Zugriff bis zu den Berechtigungen. Der Systemadministrator muss dabei jedoch mit anderen Personen interagieren.

| Persona | Beschreibung | Rolle in der Tour |
|---|---|---|
| Systemadministrator | Zielperson dieser Tour, bietet die anfängliche Bereitstellung von Cloud-Ressourcen und die Zuweisung von Benutzern zu den entsprechenden Rollen auf der Grundlage ihrer beruflichen Zuständigkeiten | Verwaltet alle Aspekte ihrer Benutzer, vom Zugriff bis zu den Berechtigungen |
| Inhaltsautor | Erstellt und überprüft die Inhalte in AEM | Sobald der Systemadministrator die Berechtigungen erteilt hat, können Autoren ihre eigene Journey starten, um Inhalte zu erstellen |
| Entwickler | Entwickelt AEM-Anwendungen, die Inhalte aus verschiedenen Quellen nutzen | Sobald der Systemadministrator die Berechtigungen erteilt hat, können Entwickler ihre eigene Journey starten, um Lösungen zu entwickeln |
| Implementierungs-Manager | Fügt eine Umgebung hinzu oder aktualisiert sie, führt Pipelines aus und stellt Code für die AEM-Umgebung oder die Code-Qualitätsprüfung bereit. | Sobald der Systemadministrator die Berechtigungen erteilt hat, können Implementierungs-Manager ihre eigene Journey starten, um Implementierungen zu verwalten |

Dieses Onboarding-Handbuch zeigt den vollständigen Prozess des Onboarding als Systemadministrator. Die Rollen von AEM-Benutzern, Entwicklern und Implementierungs-Managern werden kurz als zusätzliche, optionale Teile der Tour erläutert.

>[!TIP]
>
>Wenn Sie neu bei AEM as a Cloud Service sind, sich aber bereits mit AEM auskennen und von On-Premise- oder Adobe Managed Services migrieren, sollten Sie sich [Migrations-Tour zu AEM as a Cloud Service](/help/journey-migration/getting-started.md) ansehen.

## Übersicht über Onboarding-Tour {#overview}

In den folgenden Artikeln werden die wichtigsten Onboarding-Konzepte detailliert beschrieben und Sie erhalten ein grundlegendes Wissen über AEM as a Cloud Service. Obwohl Sie direkt zu einem bestimmten Teil der Tour gehen können, beachten Sie, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Für Einsteiger empfiehlt sich daher, von vorn zu beginnen und schrittweise vorzugehen.

| Nummer | Artikel | Beschreibung | Zielgruppe |
|---|---|---|---|
| 0 | Onboarding-Tour | Dieses Dokument | Systemadministrator |
| 1 | [Onboarding-Vorbereitung](preparation.md) | Bevor der Onboarding-Prozess beginnt, gibt es eine Reihe von vorbereitenden Schritten, die der Systemadmin verstehen muss, bevor er sich beim System anmeldet. | Systemadministrator |
| 2 | [Terminologie von AEM as a Cloud Service](terminology.md) | Bevor Sie sich zum ersten Mal bei AEMaaCS anmelden, ist es hilfreich, einige Begriffe des Systems und seiner grundlegenden Struktur zu verstehen. | Systemadministrator |
| 3 | [Die Admin Console](admin-console.md) | Erfahren Sie, was die Admin Console ist, wie Sie sich anmelden und wie Sie Ihr Profil als Systemadministrator überprüfen können. | Systemadministrator |
| 4 | [Zuweisen von Cloud Manager-Produktprofilen](assign-profiles-cloud-manager.md) | Überprüfen Sie die Cloud Manager-Produktprofile und erfahren Sie, wie Sie Team-Mitglieder Cloud Manager-Produktprofilen zuweisen. | Systemadministrator |
| 5 | [Zugreifen auf Cloud Manager](cloud-manager.md) | Hier erfahren Sie, wie Sie auf Cloud Manager zugreifen können, damit Sie Ihre Projektressourcen einrichten können. | Systemadministrator |
| 6 | [Erstellen eines Programms](create-program.md) | Erfahren Sie, wie Sie ein Programm mit Cloud Manager erstellen. | Systemadministrator |
| 7 | [Erstellen von Umgebungen](create-environments.md) | Erfahren Sie, wie Sie mit Cloud Manager eine Umgebung erstellen. | Systemadministrator |
| 8 | [Zuweisen von AEM-Produktprofilen](assign-profiles-aem.md) | Erfahren Sie, wie ein Systemadministrator Ihre Team-Mitglieder Produktprofilen in AEM as a Cloud Service zuweist. | Systemadministrator |
| 9 | [Aufgaben für Entwickler und Bereitstellungs-Manager](developers.md) | Optional – Erfahren Sie, wie Sie als Entwickler auf Cloud Manager Git zugreifen und es verwalten können und wie Sie als Implementierungs-Manager Pipelines einrichten und Code in Cloud Manager bereitstellen können. | Entwickelnde und Implementierungs-Manager |
| 10 | [AEM-Benutzeraufgaben](aem-users.md) | Optional – Erfahren Sie, wie Sie als AEM-Autor auf eine Instanz von AEM as a Cloud Service zugreifen und sich mit der Inhaltserstellung für AEM as a Cloud Service vertraut machen können. | AEM-Benutzer |

## Wie geht es weiter {#what-is-next}

Jetzt können Sie Ihre Onboarding-Tour durch AEM as a Cloud Service starten. Wir empfehlen Ihnen, mit dem nächsten Teil der Tour fortzufahren und den Artikel [Onboarding-Vorbereitung](preparation.md) lesen

## AEM-Dokumentations-Touren {#documentation-journeys}

[Eine Dokumentations-Tour](/help/journey-documentation/documentation-journeys.md) verbindet viele verschiedene und möglicherweise komplizierte Themen und Funktionen durch eine Erzählung, die dem nicht mit AEM vertrauten Leser hilft, ein geschäftliches Problem von Anfang bis Ende zu verstehen und zu lösen, wobei nur minimale Vorkenntnisse zum Thema oder zu AEM vorausgesetzt werden.

Dokumentations-Touren werden auf der Grundlage von Best-Practice-Prinzipien entwickelt, die auf Informationen aus den neuesten Forschungsergebnissen von Adobe, bewährten Implementierungserfahrungen der Adobe-Berater und dem Feedback aus Kundenprojekten basieren.

Wenn Sie wissen möchten, was Adobe empfiehlt, damit Sie Ihr Team beim Onboarding in Ihrem neuen Programm mit AEM as a Cloud Service unterstützen können, sind Sie hier genau richtig!
