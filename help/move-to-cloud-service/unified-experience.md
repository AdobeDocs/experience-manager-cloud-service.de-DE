---
title: Einheitliches Erlebnis für Tools zur Codeumgestaltung
description: Einheitliches Erlebnis für Tools zur Codeumgestaltung
translation-type: tm+mt
source-git-commit: 5d2b14c827603297a59cba7180fc1a68de0c841a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---


# Unified Experience for Code Refactoring Tools {#unified-experience}

Wir haben Tools entwickelt, um einige der Aufgaben zur Codeumgestaltung zu automatisieren, die erforderlich sind, um mit AEM als Cloud Service kompatibel zu sein. Um die Komplexität zu reduzieren, die mit der Installation und Einrichtung verschiedener Code-Refactoring-Tools verbunden ist, haben wir ein Plugin entwickelt, um Tools zu vereinheitlichen, die auf Code und Repositorys arbeiten.

## Vorteile {#benefits}

Das Plug-in Unified Experience bietet die folgenden Vorteile:

* Vereinheitlicht Tools, die am Quellcode arbeiten, in eine `node.js`-Anwendung, die als `aio-cli `-Plug-In verfügbar gemacht wird, um dem Benutzer eine einheitliche Benutzererfahrung zu bieten.

* Bietet die Möglichkeit, alle Werkzeuge über einen einzigen Befehl auszuführen, und bietet gleichzeitig die Flexibilität, spezifische Tools nach Bedarf auszuführen.

* Bietet Erweiterungen, um das Hinzufügen neuer Tools zu vereinfachen und gleichzeitig das Erlebnis konsistent zu gestalten.

## Das Plugin {#understanding-plugin}

Das `aio-cli-plugin-aem-cloud-service-migration`-Plugin besteht aus zwei Hauptteilen:

* **Benutzeroberfläche**

   * `aio-cli` Befehle zum Ausführen eines oder mehrerer Code Refactoring Tools (durch Verketten der Tools, die sequenziell ausgeführt werden sollen).
   * `config.yaml` , der die erforderlichen Eingabeparameter übernimmt.

* **zugrunde liegende Code Refactoring Tool Suite**

   Die Code Refactoring Tools führen ihre Funktionen wie folgt aus:

   * Scannen des jeweiligen Abschnitts des Kundencodes und Bearbeiten des Codes (basierend auf der Codeimplementierung für Best Practices), um die Ausgabe zu erstellen, die validiert und bereitgestellt werden kann.

   * Erstellung eines Zusammenfassungsberichts zur Aufzeichnung der während der Ausführung ausgeführten Vorgänge.

## Verfügbarkeit {#availability}

Siehe [Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration), um mehr über die Verwendung und den Beitrag zu diesem Plugin-Code zu erfahren, der in GitHub offen ist.

>[!NOTE]
>Derzeit ist das Plugin in AEM Dispatcher Converter und Repository Modernizer integriert.
