---
title: Unified Experience für Code-Refaktorierungs-Tools
description: Erfahren Sie mehr über Unified Experience für Code-Refaktorierungs-Tools.
exl-id: daee0e2d-1e2b-41a3-acab-fc59142d0e05
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 87%

---

# Unified Experience für Code-Refaktorierungs-Tools {#unified-experience}

Wir haben Tools entwickelt, um einige der Code-Refaktorierungsaufgaben zu automatisieren, die für die Kompatibilität mit AEM as a Cloud Service erforderlich sind. Um die Komplexität bei der Installation und Einrichtung verschiedener Code-Refaktorierungs-Tools zu reduzieren, haben wir ein Plug-in zur Vereinheitlichung von Tools entwickelt, die mit Code und Repositorys arbeiten.

## Vorteile {#benefits}

Das Plug-in Unified Experience bietet die folgenden Vorteile:

* Vereinheitlicht Tools, die mit Quell-Code arbeiten, in einer `node.js`-Anwendung, die als `aio-cli `-Plug-in verfügbar gemacht wird, um dem Benutzer ein einheitliches Benutzererlebnis zu bieten.

* Bietet die Möglichkeit, alle Tools über einen einzigen Befehl auszuführen, und bietet gleichzeitig die Flexibilität, bestimmte Tools nach Bedarf auszuführen.

* Bietet Erweiterbarkeit, um das Hinzufügen neuer Tools zu vereinfachen und gleichzeitig die Erlebnis konsistent zu halten.

## Grundlegendes zum Plug-in {#understanding-plugin}

Das `aio-cli-plugin-aem-cloud-service-migration`-Plug-in besteht aus zwei Hauptteilen:

* **Benutzeroberfläche**

   * `aio-cli`-Befehle zum Ausführen eines oder mehrerer Code-Refaktorierungs-Tools (durch Verketten der nacheinander auszuführenden Tools).
   * `config.yaml` zur Aufnahme der erforderlichen Eingabeparameter.

* **Zugrunde liegende Code-Refaktorierungs-Tool-Suite**

  Die Code-Refaktorierungs-Tools führen ihre Funktionen wie folgt aus:

   * Scannen des jeweiligen Abschnitts des Kunden-Codes und Bearbeiten des Codes (basierend auf der Code-Implementierung für Best Practices), um die Ausgabe zu erstellen, die dann validiert und bereitgestellt werden kann.

   * Erstellen eines zusammenfassenden Berichts zum Aufzeichnen der während der Ausführung durchgeführten Vorgänge.

## Verfügbarkeit {#availability}

Siehe [Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) , um mehr über die Verwendung zu erfahren und wie Sie zu diesem Plug-in-Code beitragen können, der in GitHub offen zugänglich ist.

>[!NOTE]
>Derzeit ist das Plug-in in AEM Dispatcher Converter und Repository Modernizer integriert.
