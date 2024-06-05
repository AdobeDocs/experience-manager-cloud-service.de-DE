---
title: Unified Experience für Code-Refaktorierungs-Tools
description: Erfahren Sie mehr über Unified Experience für Code-Refaktorierungs-Tools.
exl-id: daee0e2d-1e2b-41a3-acab-fc59142d0e05
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 37%

---

# Unified Experience für Code-Refaktorierungs-Tools {#unified-experience}

Adobe hat Tools entwickelt, um einige der Code-Refaktorierungsaufgaben zu automatisieren, die für die Kompatibilität mit Adobe Experience Manager (AEM) as a Cloud Service erforderlich sind. Um die Komplexität bei der Installation und Einrichtung verschiedener Code-Refaktorierungs-Tools zu reduzieren, hat Adobe ein Plug-in entwickelt, um Tools zu vereinheitlichen, die mit Code und Repositorys arbeiten.

## Vorteile {#benefits}

Das Plug-in Unified Experience bietet die folgenden Vorteile:

* Vereinheitlicht Tools, die mit Quell-Code arbeiten, in einer `node.js`-Anwendung, die als `aio-cli `-Plug-in verfügbar gemacht wird, um dem Benutzer ein einheitliches Benutzererlebnis zu bieten.

* Führt alle Tools über einen einzigen Befehl aus und bietet gleichzeitig die Flexibilität, spezifische Tools nach Bedarf auszuführen.

* Vereinfachen Sie das Hinzufügen neuer Tools und halten Sie das Erlebnis konsistent.

## Grundlegendes zum Plug-in {#understanding-plugin}

Das `aio-cli-plugin-aem-cloud-service-migration`-Plug-in besteht aus zwei Hauptteilen:

* **Benutzeroberfläche**

   * `aio-cli` -Befehle zum Ausführen eines oder mehrerer Code-Refaktorierungs-Tools (durch Verketten der nacheinander auszuführenden Tools).
   * `config.yaml` zur Aufnahme der erforderlichen Eingabeparameter.

* **Zugrunde liegende Code-Refaktorierungs-Tool-Suite**

  Die Code-Refaktorierungs-Tools führen ihre Funktionen wie folgt aus:

   * Scannen des entsprechenden Abschnitts des Kundencodes und Bearbeiten des Codes (basierend auf der Code-Implementierung auf Best Practices), um die Ausgabe zu erhalten, die dann validiert und bereitgestellt werden kann.

   * Erstellen eines zusammenfassenden Berichts zum Aufzeichnen der während der Ausführung durchgeführten Vorgänge.

## Verfügbarkeit {#availability}

Siehe [Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) wo Sie mehr über die Verwendung erfahren und erfahren, wie Sie zu diesem Plug-in-Code beitragen können, der in GitHub offen zugänglich ist.

>[!NOTE]
>Derzeit ist das Plug-in in AEM Dispatcher Converter und Repository Modernizer integriert.
