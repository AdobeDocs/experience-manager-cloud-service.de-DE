---
title: Einheitliches Erlebnis für Tools zur Codeumgestaltung
description: Einheitliches Erlebnis für Tools zur Codeumgestaltung
translation-type: tm+mt
source-git-commit: c554506aea99518c94666f5d2e6151a3dce3b91e
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# Einheitliches Erlebnis für Tools zur Codeumgestaltung {#unified-experience}

Die Unified Experience for Code Refactoring-Tools vereinheitlichen das Erlebnis für die Ausführung von AEM als Cloud Service-Code-Refactoring-Tools, die auf Dispatcher-Dateien, Code und Repositorys arbeiten.

Dieses Tool reduziert die Komplexität der Verwendung von Code-Refactoring-Werkzeugen, wobei jede von ihnen unterschiedliche Ausführungsanforderungen hinsichtlich Installation, Einrichtung und Ausführung hat.

## Vorteile {#benefits}

Die Unified Experience for Code Refactoring Tools rufen alle Code-Refactoring-Tools auf und führen sie aus, die am Quellcode von derselben Stelle aus arbeiten.

Die Unique Experience for Code Refactoring Tools zusammen mit den zugehörigen Repositorys ermöglichen Folgendes:

* Vereinheitlichen Sie alle Werkzeuge, die bei der Migration von Quellcode in eine `node.js` `aio-cli plugin` Anwendung eingesetzt werden, um dem Benutzer eine einheitliche Benutzererfahrung zu bieten.

* Bereitstellung zur Durchführung der Gesamtmigration über einen einzelnen Befehl und gleichzeitig Flexibilität bei der Ausführung eines bestimmten Tools gemäß Anforderung.

* Vereinfachen Sie den zukünftigen Zusatz neuer Tools, wie z.B. das Hinzufügen neuer Tools zum Plugin, sollte einfach einen neuen Befehl für Entwickler und ein einfaches Plugin-Update für Benutzer erfordern, damit das Erlebnis mit einer höheren Wertschöpfung konsistent bleibt.

## Erläuterungen zum Plugin {#understanding-plugin}

Der Code, die Repository-Struktur oder Konfigurationen auf dem lokalen Computer des Kunden werden neu `aio-cli-plugin-aem-cloud-service-migration` berechnet. Diese Seite erfasst die detaillierten Anforderungen und Designentscheidungen für das einheitliche Erlebnis.
Es ist als Open Source für Community verfügbar, um es für benutzerdefinierte Anwendungsfälle zu erweitern.

Diese Tools vereinen alle Code-Refactoring-Tools in einer &quot;node.js&quot;-Anwendung, um dem Benutzer eine einheitliche Benutzererfahrung `aio-cli plugin` zu bieten. Das Plug-in überprüft die lokale Codebasis des Kunden und stellt AEM als Cloud Service kompatiblen Code, Konfigurationen und Pakete her, die dann auf Cloud Service-Umgebung bereitgestellt werden können.

Das Zusatzmodul besteht aus zwei Hauptteilen:

* **Benutzeroberfläche**

   `aio-cli` Befehle zum Ausführen eines oder mehrerer Migrationswerkzeuge (durch Verketten der sequenziell auszuführenden Tools)`config.yaml` , die die erforderlichen Eingabeparameter

* **zugrunde liegende Migration Tool Suite**

   Die Migrationstools führen ihre Funktionen wie folgt aus:

   * Überprüfen Sie den entsprechenden Abschnitt des Kundencodes und führen Sie die Migration (basierend auf der Codeimplementierung) durch, um die Ausgabe zu erstellen, die validiert und bereitgestellt werden kann.

   * Aufzeichnung der während der Migration ausgeführten Vorgänge in konsistenter Reihenfolge, um einen Zusammenfassungsbericht zu erstellen.

## Verfügbarkeit {#availability}

Sie können das `aio-cli-plugin-aem-cloud-service-migration` über `aio-cli`installieren und verwenden.

>[!NOTE]
>Dieses Tool ist derzeit nur mit dem Dispatcher Converter integriert.

Siehe [Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) , um mehr über die Verwendung und den Beitrag zu diesem Plugin-Code zu erfahren, der in GitHub offen ist.

