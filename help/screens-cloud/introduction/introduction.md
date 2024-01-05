---
title: Einführung in AEM Screens as a Cloud Service
description: Diese Seite dient als Einführung in Adobe Experience Manager Screens as a Cloud Service.
exl-id: b1cc0a63-ecd3-4d89-ac49-f384cc610cdc
source-git-commit: a77e5dc4273736b969e9a4a62fcac75664495ee6
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 56%

---

# Einführung in AEM Screens as a Cloud Service {#introduction-screens-cloud}

Mit Adobe Experience Manager (AEM) Screens as a Cloud Service können Sie ansprechende und dynamische Digital Signage-Erlebnisse erstellen, die in öffentlichen Räumen verwendet werden sollen. Dies ist die nächste Weiterentwicklung des AEM Screens-Produkts und stellt einen großen Sprung nach vorne in Bezug auf Benutzerfreundlichkeit und Skalierbarkeit dar.

AEM Screens as a Cloud Service ist eine Lösung für die digitale Beschilderung, mit der Marketer digitale Erlebnisse skaliert erstellen und verwalten können. Im Rahmen einer umfassenden Digital Marketing-Strategie sind zudem verschiedene Arten von physischen Bildschirmen enthalten. Das Omni-Channel-Angebot von Adobe wird über die üblichen Internet- und Mobilkanäle hinaus erweitert und umfasst auch allgegenwärtige Kanäle der digitalen Beschilderung. AEM Screens as a Cloud Service ermöglicht relevantere, kontextbezogene, produktivere und vorausschauende Benutzererlebnisse durch ein tiefes Verständnis der Inhaltserstellung, der Inhaltszusammenstellung, des Managements von ausgelösten Ereignissen und der Medienwiedergabe für alle Verbraucher und Besucher in allen öffentlichen Bereichen.

## Grundlegendes zu Komponenten in Screens as a Cloud Service {#understanding-components}

Screens as a Cloud Service besteht aus zwei Hauptkomponenten:

* **[Content Provider](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html)**: das Screens-Add-on, das auf AEM Cloud Service oder auf Adobe Managed Services (AMS) ausgeführt wird. Mit dem Screens Content Provider kann der Inhaltsautor Kanäle erstellen und verwalten. Die Inhaltsautoren können neue Inhalte hinzufügen und den Inhalt bearbeiten, ohne sich Gedanken über die Details der Erstellung von Displays oder der Registrierung von Playern machen zu müssen. Der Content Provider bietet eine Abstraktion aus den zugrunde liegenden Details der Entwicklung von Inhalten, Displays oder der Registrierung von Playern.

* **[Dienstleister](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html)**: der Digital Signage Management-Dienst, der auf Adobe I/O Runtime ausgeführt wird. Mit dem Screens Services Provider können Inhaltsautoren, Entwickler und Administratoren Anzeigen und Player für die Inhaltswiedergabe verwalten, sobald die Inhalte zu den Kanälen hinzugefügt wurden. Außerdem informiert der Screens-Dienstleister den Orchestrator darüber, wo und wann Inhalte auf hoher Ebene abgespielt werden.


## Architektonischer Übersicht {#architectural-overview}

Als as a Cloud Service AEM Screens-Benutzer können Sie Inhalte in Kanälen hinzufügen und verwalten. Sie können Anzeigen und Player über die speziell für Screens as a Cloud Service konzipierten Schnittstellen registrieren und verwalten, d. h. **Screens-Dienstleister** und **Screens Content Provider**.

![Bild](/help/screens-cloud/assets/architecture-screenscloud.png)
