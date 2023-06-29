---
title: Architektur des universellen Editors
description: Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
exl-id: e6f40743-0f21-4fb6-bf23-76426ee174be
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 79%

---

# Architektur des universellen Editors {#architecture}

Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.

## Bausteine für Architekturen {#building-blocks}

Der universelle Editor besteht aus vier wesentlichen Bausteinen, die interagieren und es Inhaltsautoren ermöglichen, beliebige Aspekte von Inhalten in jeder Implementierung zu bearbeiten, sodass Sie außergewöhnliche Erlebnisse bereitstellen, die Geschwindigkeit von Inhalten erhöhen und ein modernes Entwicklererlebnis bieten können.

1. [Editoren](#editors)
1. [Remote-App](#remote-app)
1. [API-Ebene](#api-layer)
1. [Persistenzschicht](#persistence-layer)

In diesem Dokument werden die einzelnen Bausteine und ihr Austausch von Daten beschrieben.

![Architektur des universellen Editors](assets/architecture.png)

>[!TIP]
>
>Informationen zum Anzeigen des universellen Editors und seiner Architektur finden Sie unter [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) , um zu erfahren, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM App beginnen, diese zu verwenden.

### Editoren {#editors}

* **Universeller Editor** – Der universelle Editor verwendet ein instrumentiertes DOM, um die Bearbeitung von Inhalten im Kontext zu ermöglichen. Siehe [Attribute und Typen](attributes-types.md) für Details zu den erforderlichen Metadaten. Im Dokument [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) finden Sie ein Beispiel für die Instrumentierung in AEM.
* **Eigenschaftenleiste** – Einige Eigenschaften von Komponenten können nicht kontextbezogen bearbeitet werden, z. B. die Drehzeit eines Karussells oder welche Registerkarte für das Akkordeon immer geöffnet bzw. geschlossen werden soll. Um die Bearbeitung solcher Komponenteninformationen zu ermöglichen, wird in der Seitenleiste des Editors ein formularbasierter Editor bereitgestellt.

### Remote-App {#remote-app}

Damit eine App im universellen Editor kontextbezogen bearbeitet werden kann, muss das DOM instrumentiert werden. Die Remote-App muss bestimmte Attribute im DOM rendern. Siehe [Attribute und Typen](attributes-types.md) für Details zu den erforderlichen Metadaten. Im Dokument [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) finden Sie ein Beispiel für die Instrumentierung in AEM.

Der universelle Editor strebt ein minimales SDK an, daher liegt die Instrumentierung in der Verantwortung der Remote-App-Implementierung.

### API-Ebene {#api-layer}

* **Inhaltsdaten** – Für den universellen Editor sind weder die Quellsysteme der Inhaltsdaten noch die Art und Weise ihrer Nutzung wichtig. Es ist nur wichtig, die erforderlichen Attribute mithilfe von bearbeitbaren Kontextdaten zu definieren und bereitzustellen.
* **Persistieren von Daten** – Für alle bearbeitbaren Daten gibt es eine URN-Kennung. Diese URN wird verwendet, um die Persistenz zum richtigen System und zur richtigen Ressource zu leiten.

### Persistenzschicht {#persistence-layer}

* **Inhaltsfragmentmodell** – Um die Leiste zum Bearbeiten von Inhaltsfragment-Eigenschaften, den Inhaltsfragment-Editor und formularbasierte Editoren zu unterstützen, sind Modelle pro Komponente und Inhaltsfragment erforderlich.
* **Inhalt** – Der Inhalt kann an einer beliebigen Stelle gespeichert werden, z. B. in AEM, Magento usw.

![Persistenzschicht](assets/persistence-layer.png)

## Universeller Editor-Dienst und Backend-System-Dispatch {#service}

Der universelle Editor sendet alle Inhaltsänderungen an einen zentralen Dienst, den sogenannten universellen Editor-Dienst. Dieser Dienst, der auf Adobe I/O Runtime ausgeführt wird, lädt in der Erweiterungsregistrierung verfügbare Plug-ins basierend auf der bereitgestellten URN. Das Plug-in ist für die Kommunikation mit dem Backend und die Rückgabe einer einheitlichen Antwort verantwortlich.

![Universeller Editor-Dienst](assets/universal-editor-service.png)

## Rendern von Pipelines {#rendering-pipelines}

### Server-seitiges Rendering {#server-side}

![Server-seitiges Rendern](assets/server-side.png)

### Statische Site-Erstellung {#static-generation}

![Statische Site-Erstellung](assets/static-generation.png)

### Client-seitiges Rendern {#client-side}

![Client-seitiges Rendern](assets/client-side.png)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) - Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, sodass Sie außergewöhnliche Erlebnisse bereitstellen, die Inhaltsgeschwindigkeit erhöhen und ein modernes Entwicklererlebnis bieten können.
* [Inhaltserstellung mit dem universellen Editor](authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) – Erfahren Sie, wie der universelle visuelle Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Attribute und Typen](attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
