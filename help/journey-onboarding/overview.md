---
title: Einführung in die Onboarding-Tour durch AEM as a Cloud Service
description: Beginnen Sie hier für einen Überblick über die geführte Tour durch den Onboarding-Prozess bei AEM as a Cloud Service.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
recommendations: noDisplay
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 4a369104ea8394989149541ee1a7b956383c8f12
workflow-type: tm+mt
source-wordcount: '1295'
ht-degree: 100%

---


# Onboarding-Tour {#onboarding-journey}

Herzlichen Glückwunsch zur Wahl von AEM as a Cloud Service! Dieses Dokument ist Ihr Ausgangspunkt für eine geführte Tour durch den Onboarding-Prozess. Unabhängig davon, ob Sie eine neue Anwendung bereitstellen oder eine bestehende migrieren, werden im Rahmen dieser Onboarding-Tour Ihre Teams eingerichtet. Dadurch wird sichergestellt, dass diese auf AEM as a Cloud Service zugreifen können.

## Einführung {#introduction}

Adobe Experience Manager ist eine leistungsstarke Suite zusammenstellbarer Inhaltsdienste, die schnell wirkungsvolle, personalisierte Erlebnisse für alle Kanäle bereitstellen und so Inhalte für alle freigeben. **Edge Delivery Services** ist die neueste Innovation in Adobe Experience Manager, die extrem schnelle Inhalte ermöglicht und außergewöhnliche Erlebnisse bietet. Mehr über die ersten Schritte mit Edge Delivery Services erfahren Sie unter [Überblick über Edge Delivery Services](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/overview). Informationen zur Verwendung von Edge Delivery Services finden Sie auf der Seite [Entwicklertutorial](https://www.aem.live/developer/tutorial).

Onboarding ist der Vorgang, bei dem benannte Systemadmins AEM as a Cloud Service für Ihre Organisation einrichten. Dieser Prozess umfasst die anfängliche Bereitstellung von Cloud-Ressourcen und die Zuweisung von Benutzenden zu Rollen auf der Grundlage ihrer Aufgabenstellung. Dadurch kann sich jedes Mitglied anmelden und auf seine Ressourcen in AEM as a Cloud Service zugreifen.

![Die Onboarding-Tour](/help/journey-onboarding/assets/onboarding-journey.png)

Dieses Handbuch führt Sie durch die wichtigsten Onboarding-Themen, sodass Sie nach Abschluss Folgendes erreicht haben:

* Ein umfassendes Verständnis der verschiedenen Begriffe, Services und Benutzer, die am Onboarding-Prozess beteiligt sind.
* Ihrem Team wurde ermöglicht, loszulegen und die ersten Schritte zu unternehmen, um Inhalte für Ihr Programm mit AEM as a Cloud Service zu erstellen und zu entwickeln.

Das Ergebnis ist:

* Ihr Team ist eingerichtet und hat Zugriff auf Cloud-Ressourcen.
* AEM-Autoren und -Autorinnen haben Zugriff auf AEM as a Cloud Service und können mit der Erstellung von Inhalten beginnen.
* AEM-Entwickelnde und Implementierungs-Manager haben Zugriff auf AEM as a Cloud Service und können mit der Erstellung und Bereitstellung von benutzerdefinierten Programmen beginnen.

## Konzepte und Ziel {#concepts}

Auch wenn es zu Beginn der Arbeit mit AEM as a Cloud Service viel zu lernen gibt, sind es konzeptionell nur wenige, logische Teile.

* **Der Vertrag**: Sie müssen mit Ihrem Adobe-Vertrag vertraut sein, da er Aspekte des Onboarding-Prozesses definiert.
* **Admin Console**: Hier werden Benutzende verwaltet und Rollen zugewiesen.
* **Cloud Manager**: Das Tool zum Einrichten von Ressourcen wie Programmen und Umgebungen. Zudem können Sie hierüber auf Git zugreifen und Pipelines zur Verwaltung und Bereitstellung Ihres benutzerdefinierten Codes erstellen.

Diese Konzepte werden in dieser Onboarding-Tour detailliert beschrieben. Das Ziel besteht darin, dass Sie am Ende der Tour:

* den Benutzenden den benötigten Zugriff auf AEM as a Cloud Service gewähren können
* die ersten Cloud-Ressourcen für Ihr Projekt einrichten können
* Wissen, wie Sie Ihren ersten Code bereitstellen und Ihre ersten Inhalte erstellen können.

Im Grunde genommen können Sie mit Ihrem neuen AEM as a Cloud Service-Projekt sofort durchstarten!

## Zielgruppe {#audience}

Die Onboarding-Tour wurde speziell für **System-Admins** von Kundinnen und Kunden entwickelt, für die AEM as a Cloud Service und AEM im Allgemeinen neu ist. Die oder der System-Admin ist die Person, die nach Unterzeichnung Ihres AEM as a Cloud Service-Vertrags von Adobe zuerst kontaktiert wird. Sie ist in der Regel die erste Person, die auf Ihre Ressourcen zugreift und diese auf AEM as a Cloud Service eingerichtet hat. Wenn Sie dieses Thema lesen, sind Sie wahrscheinlich Systemadministrator bzw. -administratorin.

Die Systemadmins verwalten alle Aspekte der AEMaaCS-Benutzenden ihrer Organisation, vom Zugriff bis zu den Berechtigungen. Die oder der System-Admin muss dabei jedoch mit anderen Personen interagieren.

| Persona | Beschreibung | Rolle in der Tour |
|---|---|---|
| Systemadministrator | Zielperson dieser Tour; kümmert sich um die anfängliche Bereitstellung von Cloud-Ressourcen und die Zuweisung von Benutzenden zu den entsprechenden Rollen auf Grundlage ihrer beruflichen Zuständigkeiten | Verwaltet alle Aspekte ihrer Benutzer, vom Zugriff bis zu den Berechtigungen |
| Inhaltsautor | Erstellt und überprüft die Inhalte in AEM | Sobald die Systemadministratorin oder der Systemadministrator die Berechtigungen erteilt hat, können Autorinnen und Autoren ihre eigene Tour starten, um Inhalte zu erstellen |
| Entwicklerin oder Entwickler | Entwickelt AEM-Anwendungen, die Inhalte aus verschiedenen Quellen nutzen. | Sobald die Systemadministratorin oder der Systemadministrator die Berechtigungen erteilt hat, können Entwickelnde ihre eigene Tour starten, um Lösungen zu entwickeln. |
| Bereitstellungs-Manager | Fügt eine Umgebung hinzu oder aktualisiert sie, führt Pipelines aus und stellt Code für die AEM-Umgebung oder die Code-Qualitätsprüfung bereit. | Sobald der Systemadministrator die Berechtigungen erteilt hat, können Bereitstellungs-Manager ihre eigene Journey starten, um Bereitstellungen zu verwalten |

Dieses Onboarding-Handbuch zeigt den vollständigen Prozess des Onboarding als Systemadministrator. Die Rollen von AEM-Benutzern, Entwicklern und Bereitstellungs-Managern werden kurz als zusätzliche, optionale Teile der Tour erläutert.

>[!TIP]
>
>Wenn Sie neu bei AEM as a Cloud Service, aber bereits mit AEM vertraut sind und von On-Premise- oder Adobe Managed Services migrieren, sehen Sie sich die [Migrations-Tour zu AEM as a Cloud Service](/help/journey-migration/getting-started.md) an.

## Übersicht der Onboarding-Tour {#overview}

In den folgenden Artikeln werden die wichtigsten Onboarding-Konzepte detailliert beschrieben und Sie erhalten ein grundlegendes Wissen über AEM as a Cloud Service. Sie können direkt zu einem bestimmten Teil der Tour gehen. Beachten Sie jedoch, dass viele Konzepte auf denen der vorherigen Artikel aufbauen. Daher empfiehlt Adobe, wenn Sie neu im Onboarding sind, am Anfang zu beginnen und schrittweise vorzugehen.

| | Artikel | Beschreibung | Zielgruppe |
|---|---|---|---|
| 0 | Onboarding-Tour | Dieses Dokument | Systemadministrator |
| 1 | [Onboarding-Vorbereitung](preparation.md) | Bevor der Onboarding-Prozess beginnt, gibt es eine Reihe von vorbereitenden Schritten, die der Systemadmin verstehen muss, bevor er sich beim System anmeldet. | Systemadministrator |
| 2 | [Terminologie von AEM as a Cloud Service](terminology.md) | Bevor Sie sich zum ersten Mal bei AEMaaCS anmelden, ist es hilfreich, einige Begriffe des Systems und seiner grundlegenden Struktur zu verstehen. | Systemadministrator |
| 3 | [Die Admin Console](admin-console.md) | Erfahren Sie, was die Admin Console ist, wie Sie sich anmelden und wie Sie Ihr Profil als Systemadministrator überprüfen können. | Systemadministrator |
| 4 | [Zuweisen von Cloud Manager-Produktprofilen](assign-profiles-cloud-manager.md) | Überprüfen Sie die Cloud Manager-Produktprofile und erfahren Sie, wie Sie Team-Mitglieder Cloud Manager-Produktprofilen zuweisen. | Systemadministrator |
| 5 | [Zugreifen auf Cloud Manager](cloud-manager.md) | Hier erfahren Sie, wie Sie auf Cloud Manager zugreifen können, damit Sie Ihre Projektressourcen einrichten können. | Systemadministrator |
| 6 | [Erstellen eines Programms](create-program.md) | Erfahren Sie, wie Sie ein Programm mit Cloud Manager erstellen. | Systemadministrator |
| 7 | [Erstellen von Umgebungen](create-environments.md) | Erfahren Sie, wie Sie mit Cloud Manager eine Umgebung erstellen. | Systemadministrator |
| 8 | [Zuweisen von AEM-Produktprofilen](assign-profiles-aem.md) | Erfahren Sie, wie der Systemadministrierende Ihre Team-Mitglieder in AEM as a Cloud Service Produktprofilen zuordnet. | Systemadministrator |
| 9 | [Aufgaben für Entwickler und Bereitstellungs-Manager](developers.md) | Optional - Erfahren Sie, wie Sie als entwickelnde Person auf Cloud Manager Git zugreifen und es verwalten können und wie Sie als Bereitstellungs-Manager Pipelines einrichten und Code in Cloud Manager bereitstellen. | Entwickelnde und Bereitstellungs-Manager |
| 10 | [AEM-Benutzeraufgaben](aem-users.md) | Optional: Als AEM-Autor oder -Autorin erfahren Sie, wie Sie auf eine Instanz von AEM as a Cloud Service zugreifen und sich mit der Inhaltserstellung für AEM as a Cloud Service vertraut machen können. | AEM-Benutzende |

## Wie geht es weiter {#what-is-next}

Jetzt können Sie Ihre Onboarding-Tour durch AEM as a Cloud Service starten. Wir empfehlen Ihnen, mit dem nächsten Teil der Tour fortzufahren und den Artikel [Onboarding-Vorbereitung](preparation.md) zu lesen

## AEM-Dokumentations-Touren {#documentation-journeys}

[Eine Dokumentations-Tour](/help/journey-documentation/documentation-journeys.md) kombiniert viele verschiedene, komplizierte Themen und Merkmale. Sie bietet eine Erzählung, die es Lesenrinnen und Lesern, die neu bei AEM sind, ermöglicht, ein Geschäftsproblem von Anfang bis Ende zu verstehen und zu lösen, wobei nur minimale Vorkenntnisse zum Thema oder AEM vorausgesetzt werden.

Dokumentations-Touren werden auf der Grundlage von Best-Practice-Prinzipien entwickelt. Sie beruhen auf Informationen aus den neuesten Forschungsergebnissen von Adobe, bewährten Implementierungserfahrungen der Adobe-Beraterinnen und -Berater und dem Feedback aus Kundenprojekten.

Wenn Sie wissen möchten, was Adobe empfiehlt, damit Sie Ihr Team beim Onboarding in Ihrer neuen Applikation mit AEM as a Cloud Service unterstützen können, sind Sie hier genau richtig!

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt der Onboarding-Tour hinausgehen möchten.

* [Onboarding in AEM as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/onboarding) – In diesem kurzen Video erhalten Sie einen Überblick über den Cloud Service-Onboarding-Prozess für AEM.
