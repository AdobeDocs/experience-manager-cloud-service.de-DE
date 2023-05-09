---
title: Architektur des universellen Editors
description: Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
exl-id: e6f40743-0f21-4fb6-bf23-76426ee174be
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 1%

---

# Architektur des universellen Editors {#architecture}

Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.

## Bausteine für Architekturen {#building-blocks}

Der universelle Editor besteht aus vier wesentlichen Bausteinen, die interagieren und es Inhaltsautoren ermöglichen, beliebige Aspekte von Inhalten in jeder Implementierung zu bearbeiten, um außergewöhnliche Erlebnisse bereitzustellen, die Geschwindigkeit von Inhalten zu erhöhen und ein modernes Entwicklererlebnis zu bieten.

1. [Editoren](#editors)
1. [Remote App](#remote-app)
1. [API-Ebene](#api-layer)
1. [Persistenzschicht](#persistence-layer)

In diesem Dokument werden die einzelnen Bausteine und ihr Austausch von Daten beschrieben.

![Architektur des universellen Editors](assets/architecture.png)

>[!TIP]
>
>Wenn Sie den universellen Editor und dessen Architektur in Aktion sehen möchten, lesen Sie das Dokument . [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) , um zu erfahren, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM App beginnen, diese zu verwenden.

### Editoren {#editors}

* **Universal Editor** - Der Universal Editor verwendet ein instrumentiertes DOM, um die Bearbeitung von Inhalten im Kontext zu ermöglichen. Lesen Sie das Dokument [Attribute und Typen](attributes-types.md) für Details zu den erforderlichen Metadaten. Siehe Dokument . [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) für ein Beispiel der Instrumentierung in AEM.
* **Eigenschaftenleiste** - Einige Eigenschaften von Komponenten können nicht kontextbezogen bearbeitet werden, z. B. die Drehzeit eines Karussells oder die Registerkarte für das Akkordeon, die immer geöffnet oder geschlossen werden soll. Um die Bearbeitung solcher Komponenteninformationen zu ermöglichen, wird in der Seitenleiste des Editors ein formularbasierter Editor bereitgestellt.

### Remote App {#remote-app}

Damit eine App im Kontext im universellen Editor bearbeitbar ist, muss das DOM instrumentiert werden. Die Remote-App muss bestimmte Attribute im DOM rendern. Lesen Sie das Dokument [Attribute und Typen](attributes-types.md) für Details zu den erforderlichen Metadaten. Siehe Dokument . [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) für ein Beispiel der Instrumentierung in AEM.

Der universelle Editor strebt ein minimales SDK an, daher fällt die Instrumentierung in die Verantwortung der Remote-App-Implementierung.

### API-Ebene {#api-layer}

* **Inhaltsdaten** - Für den universellen Editor sind weder die Quellsysteme der Inhaltsdaten noch die Art und Weise ihrer Nutzung wichtig. Es ist nur wichtig, die erforderlichen Attribute mithilfe von bearbeitbaren Kontextdaten zu definieren und bereitzustellen.
* **Beständige Daten** - Für jede bearbeitbare Daten gibt es eine URN-Kennung. Diese URN wird verwendet, um die Persistenz zum richtigen System und zur richtigen Ressource zu leiten.

### Persistenzschicht {#persistence-layer}

* **Inhaltsfragmentmodell** - Um die Leiste zum Bearbeiten von Inhaltsfragmenteigenschaften, den Inhaltsfragment-Editor und formularbasierte Editoren zu unterstützen, sind Modelle pro Komponente und Inhaltsfragment erforderlich.
* **Inhalt** - Der Inhalt kann an einer beliebigen Stelle gespeichert werden, z. B. in AEM, Magento usw.

![Persistenzschicht](assets/persistence-layer.png)

## Universal Editor Service und Backend System Dispatcher {#service}

Der universelle Editor sendet alle Inhaltsänderungen an einen zentralen Dienst, den so genannten universellen Editor-Dienst. Dieser Dienst, der auf Adobe I/O Runtime ausgeführt wird, lädt in der Erweiterungsregistrierung verfügbare Plugins basierend auf der bereitgestellten URN. Das Plug-in ist für die Kommunikation mit dem Backend und die Rückgabe einer einheitlichen Antwort verantwortlich.

![Universal Editor Service](assets/universal-editor-service.png)

## Rendering-Pipelines {#rendering-pipelines}

### Server-seitiges Rendering {#server-side}

![Server-seitiges Rendering](assets/server-side.png)

### Statische Site-Erstellung {#static-generation}

![Statische Site-Generierung](assets/static-generation.png)

### Client-seitiges Rendering {#client-side}

![Client-seitiges Rendering](assets/client-side.png)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) - Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Inhaltserstellung mit dem universellen Editor](authoring.md) - Erfahren Sie, wie einfach und intuitiv es für Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) - Erfahren Sie, wie der universelle Visual Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) - Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM App beginnen, um ihn zu verwenden.
* [Attribute und Typen](attributes-types.md) - Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Universelle Editor-Authentifizierung](authentication.md) - Erfahren Sie, wie der universelle Editor authentifiziert wird.
