---
title: Übersetzen von Inhalten für mehrsprachige Sites
description: Verschaffen Sie sich einen Überblick darüber, wie Inhalte für mehrsprachige Sites übersetzt werden.
feature: Language Copy
role: Admin
exl-id: c3e89719-4d08-401b-b9dd-19d1db03d72c
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 71%

---

# Übersetzen von Inhalten für mehrsprachige Sites {#translating-content-for-multilingual-sites}

Automatisieren Sie die Übersetzung von Seiteninhalten und Assets, um mehrsprachige Websites zu erstellen und zu pflegen. Um Übersetzungs-Workflows zu automatisieren, integrieren Sie Übersetzungsanbieter in AEM und erstellen Sie Projekte für die Übersetzung von Inhalten in mehrere Sprachen. AEM unterstützt Workflows für menschliche und maschinelle Übersetzungen.

* **Menschliche Übersetzung:** Inhalte werden an Ihren Übersetzungsdienstleister gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.
* **Maschinelle Übersetzung:** Der maschinelle Übersetzungs-Service übersetzt sofort Ihre Inhalte.

>[!TIP]
>
>Wenn Sie mit der Übersetzung von Inhalten noch nicht vertraut sind, lesen Sie [Sites Translation Journey,](/help/journey-sites/translation/overview.md) , der durch die Übersetzung Ihrer AEM Sites-Inhalte mithilfe der leistungsstarken Übersetzungs-Tools von AEM führt, ideal für Benutzer ohne AEM- oder Übersetzungserfahrung.

Die Übersetzung der Inhalte umfasst die folgenden Schritte:

1. [Stellen Sie eine Verbindung zwischen AEM und Ihrem Übersetzungsdienstleister her](integration-framework.md#connecting-to-a-translation-service-provider) und [erstellen Sie Konfigurationen für die Integration des Übersetzungs-Frameworks](integration-framework.md).
1. [Verknüpfen Sie die Seiten Ihres Sprachstamms](integration-framework.md#configuring-pages-for-translation) mit dem Übersetzungsdienstleister und den Framework-Konfigurationen.
1. [Identifizieren Sie die Art der zu übersetzenden Inhalte](rules.md).
1. [Bereiten Sie die Inhalte für die Übersetzung vor](preparation.md), indem Sie den Sprachstamm und die Stammseiten der Sprachkopien erstellen.
1. [Erstellen Sie Übersetzungsprojekte](managing-projects.md), um die zu übersetzenden Inhalte zusammenzustellen und den Übersetzungsprozess vorzubereiten.
1. Verwenden Sie die Übersetzungsprojekte, um [den Prozess zur Übersetzung der Inhalte zu verwalten](managing-projects.md).

Wenn Ihr Übersetzungsanbieter keinen Connector zur Integration mit AEM bereitstellt, unterstützt AEM die manuelle Extraktion und das erneute Einfügen von Übersetzungsinhalten im XML-Format.

>[!NOTE]
>
>Ihr Benutzer muss Mitglied der Gruppe `project-administrators` sein, um die Sprachkopie-Funktionen zu verwenden.

## Best Practices {#best-practices}

Die Seite [Best Practices für die Übersetzung](best-practices.md) enthält wichtige Informationen zur Implementierung.
