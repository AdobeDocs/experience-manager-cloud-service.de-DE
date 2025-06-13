---
title: Erweitern von [!DNL Adobe Experience Manager] as a Cloud Service mit dem Adobe Developer App Builder.
description: Erweitern von [!DNL Adobe Experience Manager] as a Cloud Service mit dem Adobe Developer App Builder.
exl-id: 50d82745-5deb-4bfa-961b-714842403601
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 00a05b3bdc1a689947c1507847da99b54c94dcac
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 78%

---

# Erweitern von [!DNL Adobe Experience Manager] as a Cloud Service mit dem Adobe Developer App Builder {#extend-using-app-builder}

## Was ist der App Builder für AEM as a Cloud Service? {#project-appbuilder}

Der neue Adobe Developer App Builder bietet ein Erweiterbarkeits-Framework, mit dem Entwicklerinnen und Entwickler Funktionen in AEM as a Cloud Service einfach erweitern können.

Der App Builder bietet ein einheitliches Erweiterungs-Framework für Drittanbieter zur Integration und Erstellung benutzerdefinierter Erlebnisse, die Adobe Experience Manager erweitern. Mit diesem vollständigen Erweiterbarkeits-Framework, das auf der Infrastruktur der Adobe basiert, können Entwickler benutzerdefinierte Microservices erstellen, Adobe Experience Manager über Adobe-Lösungen und den Rest des IT-Stacks erweitern und integrieren.

Der App Builder bietet Kunden eine Möglichkeit, Adobe Experience Manager in verschiedenen Anwendungsfällen einfach zu erweitern:

* Middleware-Erweiterbarkeit: Verbinden Sie externe Systeme mit Adobe-Anwendungen, indem Sie benutzerdefinierte Connectoren erstellen oder eine Suite vorgefertigter Integrationen nutzen.
* Erweiterbarkeit der Hauptdienste: Erweiterung der Kernanwendungsfunktionen durch Erweiterung des Standardverhaltens um benutzerdefinierte Funktionen und Geschäftslogik.
* Benutzererlebnis-Erweiterbarkeit: Erweitern Sie das Kernerlebnis, um Geschäftsanforderungen zu unterstützen oder kundenspezifische digitale Eigenschaften, Storefronts und Back-Office-Apps zu erstellen.

>[!NOTE]
>
> Kunden mit AEM 6.5, die App Builder nutzen möchten, lesen bitte den Abschnitt [Erweitern von Adobe Experience Manager 6.5 mit dem Adobe Developer App Builder](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/app-builder.html?lang=de).

## Architektur {#architecture}

Anstelle einer vordefinierten Lösung bietet der Adobe Developer App Builder eine gemeinsame, konsistente und standardisierte Entwicklungsplattform für die Erweiterung von Adobe Cloud-Lösungen wie AEM, einschließlich:

* Adobe Developer Console: Für die Entwicklung benutzerdefinierter Microservices und Erweiterungen können Entwickelnde Projekte erstellen und verwalten und dabei auf alle Tools und APIs zugreifen, die zum Erstellen von Plug-ins und Integrationen erforderlich sind.
* Entwickler-Tools : Open-Source-Tools, SDKs und Bibliotheken, mit denen Entwickler einfach benutzerdefinierte Erweiterungen und Integrationen erstellen können. Verwenden Sie React Spectrum (UI-Toolkit von Adobe), damit Sie über eine gemeinsame Benutzeroberfläche für alle Adobe-Apps verfügen.
* Services - I/O Runtime für das Hosting der Infrastruktur auf der Server-losen Adobe-Plattform und I/O Events für ereignisbasierte Integrationen. Adobe bietet auch native Unterstützung für das Speichern von Daten und Dateien.
* Adobe Experience Cloud - Entwickler können Erweiterungen und Integrationen übermitteln, die in ihrer Experience Cloud-Organisation veröffentlicht werden sollen. Systemadministratoren können diese Erweiterungen dann überprüfen, verwalten und genehmigen. Nach der Veröffentlichung finden Sie Ihre benutzerdefinierten App Builder-Erweiterungen und -Tools zusammen mit anderen Adobe Experience Cloud-Anwendungen.

Die folgende Abbildung zeigt, wie eine auf App Builder aufbauende Standardanwendung diese Funktionen nutzt:

![Architektur](/help/implementing/developing/extending/assets/appbuilder-architecture.jpg)

Weitere Informationen zur App Builder-Architektur finden Sie unter [Architekturübersicht.](https://developer.adobe.com/app-builder/docs/guides/app_builder_guides/architecture_overview/architecture-overview)

## Erste Schritte mit dem App Builder {#additional-resources}

Adobe hat die Dokumentation „Erste Schritte“ erstellt, damit Sie mit App Builder beginnen können:

* [App Builder – Erste Schritte](https://developer.adobe.com/app-builder/docs/getting_started/)

## Weiteres Lernen mit Dokumentation {#appbuilder-documentation}

Für den App Builder gibt es Videos und Dokumentation für Entwickler, einschließlich Handbüchern, und Referenzdokumentation, die Sie bei der Entwicklung Ihrer eigenen benutzerdefinierten Anwendungen unterstützen:

* [App Builder–Dokumentation](https://developer.adobe.com/app-builder/docs/overview/)
* [App Builder–Videos](https://www.youtube.com/playlist?list=PLcVEYUqU7VRfDij-Jbjyw8S8EzW073F_o)

## Testen einer der Beispielanwendungen {#appbuilder-codesamples}

Sind Sie bereit, mit der Entwicklung zu beginnen? Adobe bietet viele Beispielanwendungen, mit denen Sie schnell loslegen können:

* [App Builder-Code-Labs auf der Adobe Developer-Website](https://developer.adobe.com/app-builder/docs/resources/)