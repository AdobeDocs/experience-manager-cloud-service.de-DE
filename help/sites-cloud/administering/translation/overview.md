---
title: Übersetzen von Inhalten für mehrsprachige Sites
description: Verschaffen Sie sich einen Überblick darüber, wie Inhalte für mehrsprachige Sites übersetzt werden.
feature: Language Copy
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 61%

---


# Übersetzen von Inhalten für mehrsprachige Sites {#translating-content-for-multilingual-sites}

Automatisieren Sie die Übersetzung von Seiteninhalten und Assets, um mehrsprachige Websites zu erstellen und zu verwalten. Zur Automatisierung von Übersetzungs-Workflows integrieren Sie die Übersetzungsdienstleister in AEM und erstellen Sie Projekte zur Übersetzung von Inhalten in mehrere Sprachen. AEM unterstützt menschliche und maschinelle Übersetzungs-Workflows.

* **Menschliche Übersetzung:** Inhalte werden an Ihren Übersetzungsanbieter gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.
* **Maschinelle Übersetzung:** Der Dienst für maschinelle Übersetzung übersetzt Ihre Inhalte sofort.

Die Übersetzung der Inhalte umfasst die folgenden Schritte:

1. [Stellen Sie eine Verbindung zwischen AEM und Ihrem Übersetzungsdienstleister her](integration-framework.md#connecting-to-a-translation-service-provider) und [erstellen Sie Konfigurationen für die Integration des Übersetzungs-Frameworks](integration-framework.md).
1. [Verknüpfen Sie die Seiten Ihres Sprach-Masters](integration-framework.md#configuring-pages-for-translation) mit dem Übersetzungsdienstleister und den Framework-Konfigurationen.
1. [Identifizieren Sie den Typ des zu übersetzenden ](rules.md) Inhalts.
1. [Bereiten Sie die Inhalte für die Übersetzung vor](preparation.md), indem Sie die Sprach-Master und die Stammseiten der Sprachkopien erstellen.
1. [Erstellen Sie Übersetzungsprojekte, ](managing-projects.md) um die zu übersetzenden Inhalte zu sammeln und den Übersetzungsprozess vorzubereiten.
1. Verwenden Sie die Übersetzungsprojekte, um [den Prozess zur Übersetzung der Inhalte zu verwalten](managing-projects.md).

Wenn Ihr Übersetzungsdienstleister keinen Connector für die Integration in AEM bereitstellt, unterstützt AEM auch die manuelle Extrahierung und das erneute Einfügen von Übersetzungsinhalten im XML-Format.

>[!NOTE]
>
>Ihr Benutzer muss Mitglied der Gruppe `project-administrators` sein, um die Funktionen der Sprachkopie verwenden zu können.

## Best Practices {#best-practices}

Die Seite [Best Practices für Übersetzung](best-practices.md) enthält wichtige Informationen zu Ihrer Implementierung.
