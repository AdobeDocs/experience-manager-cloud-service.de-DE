---
title: Überblick über Edge Delivery Services
description: Erfahren Sie, wie AEM as a Cloud Service von der Leistung und den perfekten Lighthouse-Werten profitieren kann, die von Edge Delivery Services geboten werden.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
role: Admin, Architect, Developer
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 89%

---


# Überblick über Edge Delivery Services {#edge-delivery-services}

Mit Edge Delivery Services bietet AEM außergewöhnliche Erlebnisse, die Interaktionen und Konversionen fördern. Zu diesem Zweck liefert AEM wirkungsvolle Erlebnisse, die schnell erstellt und weiterentwickelt werden können. Edge Delivery Services ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autorinnen und Autoren schnell aktualisieren und veröffentlichen können und neue Sites schnell live geschaltet werden können. Sie können mit Edge Delivery Services die Konversion verbessern, Kosten reduzieren und extreme Inhaltsgeschwindigkeiten erzielen.

Mithilfe von Edge Delivery Services können Sie:

* schnell Sites mit einem perfekten Lighthouse-Score erstellen und Ihre Site-Leistung kontinuierlich durch Real Use Monitoring (RUM) überwachen.
* die Autoreneffizienz durch Entkopplung von Inhaltsquellen erhöhen. Standardmäßig können Sie sowohl WYSIWYG als auch Document-basiertes Authoring verwenden. Sie können also mit mehreren Inhaltsquellen an derselben Website arbeiten.
* ein integriertes Experimentierungs-Framework verwenden, das die schnelle Testerstellung, Ausführung ohne Leistungseinbußen und schnelle Freigabe für die Ermittlung eines Testgewinners ermöglicht.

## Übersicht {#overview}

Edge Delivery Services ist ein zusammenstellbarer Satz von Diensten, der eine hohe Flexibilität bei der Erstellung von Inhalten auf Ihrer Website ermöglicht. Sie können beide [AEM Content Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/getting-started/concepts.html?lang=de) und WYSIWYG-Authoring mit der [Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) sowie [Dokumentenbasiertes Authoring.](https://www.aem.live/docs/authoring)

Das folgende Diagramm zeigt, wie Sie Inhalte in Microsoft Word (dokumentenbasiertes Authoring) bearbeiten und mit Edge Delivery Services veröffentlichen können. Außerdem wird die WYSIWYG-Bearbeitung mit dem universellen Editor angezeigt.

![Architektur von Edge Delivery](assets/AEM-with-EDS-publishing-simple2.png)

Sie können Inhalte direkt aus Microsoft Word- oder Google-Dokumenten verwenden. Diese Quellen werden dann zu Seiten auf Ihrer Website. Darüber hinaus können Überschriften, Listen, Bilder und Schriftelemente von der ursprünglichen Quelle auf die Website übertragen werden. Der neue Inhalt wird sofort und ohne Neuerstellungsprozess hinzugefügt.

Edge Delivery Services nutzt GitHub, damit Sie Code direkt über ihr GitHub-Repository verwalten und bereitstellen können. Sie können beispielsweise Inhalte entweder in Google Docs oder Microsoft Word schreiben, und die Funktionalität Ihrer Site kann mithilfe von CSS und JavaScript in GitHub entwickelt werden. Wenn Sie dann bereit sind, verwenden Sie die Sidekick-Browser-Erweiterung, um Inhaltsaktualisierungen in der Vorschau anzuzeigen und zu veröffentlichen.

Weitere Informationen finden Sie in der Edge Delivery Services-Dokumentation:

* Weitere Informationen zu den ersten Schritten mit Edge Delivery finden Sie im Abschnitt [Build](https://www.aem.live/docs/#build).
* Informationen zum Erstellen und Veröffentlichen von Inhalten mithilfe von Edge Delivery finden Sie im Abschnitt [Veröffentlichen](https://www.aem.live/docs/authoring).
* Informationen dazu, wie Sie Ihr Website-Projekt ordnungsgemäß starten, finden Sie im Abschnitt [Launch](https://www.aem.live/docs/#launch).

## Edge Delivery Services und andere Adobe Experience Cloud-Produkte {#edge-other-products}

Edge Delivery Services sind Teil von Adobe Experience Manager, und insofern können sowohl Edge Delivery Services- als auch AEM-Sites auf derselben Domain vorhanden sein, was bei größeren Websites häufig der Fall ist. Darüber hinaus können Inhalte aus Edge Delivery Services einfach in Ihre AEM Sites-Seiten aufgenommen werden und umgekehrt.

Lesen Sie hierzu die [Erste Schritte für Entwickler mit WYSIWYG mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) , um zu erfahren, wie Sie Ihr eigenes Projekt mit AEM und Edge Delivery Services erstellen können.

Sie können Edge Delivery Services auch mit [Adobe Target](https://www.aem.live/developer/target-integration), [Real Use Monitoring (RUM)](https://www.aem.live/developer/rum) zur Diagnose der Nutzung und Performance Ihrer Websites sowie mit [Adobe Experience Platform Launch](https://experienceleague.adobe.com/de/docs/experience-platform/tags/home) nutzen.

## Erste Schritte mit Edge Delivery Services {#getting-started}

Die ersten Schritte mit Edge Delivery Services sind einfach, wenn Sie das [Entwicklertutorial „Erste Schritte“](https://www.aem.live/developer/tutorial) befolgen.

## So erhalten Sie Hilfe von Adobe {#getting-help}

Adobe bietet drei Kanäle, um Ihnen mit Edge Delivery Services zu helfen:

* Interaktion mit [Community-Ressourcen](#community-resources) für allgemeine Anfragen,
* Zugriff auf Ihren [Kanal für die Produktzusammenarbeit](#collaboration-channel) für spezifische Fragen,
* [Einreichen eines Support-Tickets](#support-ticket) zur Lösung wichtiger und kritischer Probleme.

### Zugreifen auf Community-Ressourcen {#community-resources}

Adobe setzt sich dafür ein, Sie mit bestmöglicher Community-Interaktion und -Unterstützung für Edge Delivery Services, WYSIWYG und dokumentbasiertes Authoring zu unterstützen.

* Beteiligen Sie sich an der [Experience League-Community](https://adobe.ly/3Q6kTKl), um Fragen zu stellen, Feedback zu teilen, Diskussionen einzuleiten, Unterstützung von Adobe- und AEM-Fachleuten und -Champions zu erhalten und in Echtzeit mit Gleichgesinnten in Kontakt zu treten. 
* Schließen Sie sich unserem [Discord-Kanal](https://discord.gg/aem-live) an, einer lockereren Plattform für Echtzeitinteraktionen und schnellen Ideenaustausch.

### Zugriff auf Ihren Kanal für die Produktzusammenarbeit {#collaboration-channel}

Angesichts des Nutzens des Kanals zur direkten Kommunikation mit Benutzenden wird für alle AEM-Projekte beim Start ein Slack-Kanal eingerichtet, um für eine bessere Geschwindigkeit zu sorgen sowie wichtige Aktualisierungen und skalierte Berichte zur Erlebnisqualität zu ermöglichen. Sie erhalten eine Einladung von Adobe, einem speziell für Ihre Organisation eingerichteten Slack-Kanal beizutreten.

Weitere Informationen finden Sie im Dokument [Verwenden des Slack-Bots](https://www.aem.live/docs/slack).

Sie können über Ihren bereitgestellten Kanal zur Produktzusammenarbeit mit Adobe-Produkt-Teams interagieren, um Antworten bezüglich der Produktnutzung oder Best Practices zu erhalten. Für Konversationen über den Kanal für die Produktzusammenarbeit gelten keine Vorgaben für Service-Levels (SLTs).

### Einreichen eines Support-Tickets {#support-ticket}

Wenn ein Produktproblem zusätzliche Untersuchungen und Fehlerbehebungen erfordert und Antwort-SLTs erfüllen muss, können Sie ein Support-Ticket nach dem folgenden Verfahren über die Admin Console einreichen:

1. [Folgen Sie dem standardmäßigen Support-Prozess](https://experienceleague.adobe.com/?support-tab=home?lang=de#support) und erstellen Sie ein Ticket.
1. Fügen Sie **Edge Delivery** zum Titel des Tickets hinzu.
1. Geben Sie in der Beschreibung zusätzlich zur Problembeschreibung die folgenden Details an:

   * URL der Live-Website. Beispiel: `www.mydomain.com`.
   * URL der Ursprungs-Website (`.hlx`-URL).

## Wie geht es weiter {#whats-next}

Lesen Sie zunächst den Artikel: [Verwenden von Edge Delivery Services](/help/edge/using.md).
