---
title: Verwenden der GraphiQL-IDE in AEM
description: Erfahren Sie, wie Sie die GraphiQL IDE in Adobe Experience Manager verwenden.
feature: Content Fragments,GraphQL API
exl-id: be2ebd1b-e492-4d77-b6ef-ffdea9a9c775
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 24%

---

# Verwenden der GraphiQL-IDE {#graphiql-ide}

Implementierung des Standards [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE ist für die Verwendung mit AEM GraphQL verfügbar. Sie kann [mit AEM installiert werden](#installing-graphiql-ide).

>[!NOTE]
>
>GraphiQL ist an den globalen Endpunkt gebunden (und funktioniert bei bestimmten Sites-Konfigurationen nicht mit anderen Endpunkten).

Mit dem GraphQL-Tool können Sie Abfragen direkt eingeben, testen und debuggen. GraphiQL bietet außerdem einfachen Zugriff auf die Dokumentation, sodass Sie leicht wissen können, welche Methoden verfügbar sind.

Beispiel:

* `http://localhost:4502/content/graphiql.html`

Dies bietet Funktionen wie Syntaxhervorhebung, automatische Vervollständigung, automatische Vorschläge sowie einen Verlauf und eine Online-Dokumentation:

![GraphiQL-Schnittstelle](assets/cfm-graphiql-interface.png "GraphiQL-Schnittstelle")

## Installieren der AEM GraphiQL IDE {#installing-graphiql-ide}

Die GraphiQL-IDE ist ein Entwicklungstool und wird nur in Umgebungen auf niedrigerer Ebene wie einer Entwicklungs- oder lokalen Instanz benötigt. Daher ist es nicht im AEM Projekt enthalten, sondern wird als separates Paket bereitgestellt, das auf Ad-hoc-Basis installiert werden kann.

1. Navigieren Sie zum **[Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)** > **AEM as a Cloud Service**.
1. Suchen Sie nach &quot;GraphiQL&quot;(stellen Sie sicher, dass Sie die **i** in **GraphiQL**.
1. Neueste Version herunterladen **GraphiQL Content Package v.x.x.x**
1. Aus dem **AEM Start** Menünavigation zu **Instrumente** > **Implementierung** > **Pakete**.
1. Klicken **Paket hochladen** und wählen Sie das im vorherigen Schritt heruntergeladene Paket aus. Klicken **Installieren** um das Paket zu installieren.
