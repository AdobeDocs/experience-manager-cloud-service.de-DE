---
title: Übersetzen von Inhalten für mehrsprachige Sites
description: Verschaffen Sie sich einen Überblick darüber, wie Inhalte für mehrsprachige Sites übersetzt werden.
feature: Language Copy
role: Admin
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: c3e89719-4d08-401b-b9dd-19d1db03d72c
solution: Experience Manager Sites
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 98%

---

# Übersetzen von Inhalten für mehrsprachige Sites {#translating-content-for-multilingual-sites}

Automatisieren Sie die Übersetzung von Seiteninhalten und Assets, um mehrsprachige Websites zu erstellen und zu pflegen. Um Übersetzungs-Workflows zu automatisieren, integrieren Sie Übersetzungsdienstleister in AEM und erstellen Sie Projekte für die Übersetzung von Inhalten in mehrere Sprachen. AEM unterstützt Workflows für menschliche und maschinelle Übersetzungen.

* **Menschliche Übersetzung:** Inhalte werden an Ihren Übersetzungsdienstleister gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.
* **Maschinelle Übersetzung:** Der maschinelle Übersetzungs-Service übersetzt sofort Ihre Inhalte.

>[!TIP]
>
>Wenn Sie mit der Übersetzung von Inhalten noch nicht vertraut sind, durchlaufen Sie unsere [Sites-Übersetzungs-Tour](/help/journey-sites/translation/overview.md), die Sie durch die Übersetzung Ihrer AEM Sites-Inhalte mithilfe der leistungsstarken Übersetzungs-Tools von AEM führt und ideal für alle ist, die noch keine Erfahrung mit AEM oder Übersetzungen haben.

Die Übersetzung der Inhalte umfasst die folgenden Schritte:

1. [Stellen Sie eine Verbindung zwischen AEM und Ihrem Übersetzungsdienstleister her](integration-framework.md#connecting-to-a-translation-service-provider) und [erstellen Sie Konfigurationen für die Integration des Übersetzungs-Frameworks](integration-framework.md).
1. [Verknüpfen Sie die Seiten Ihres Sprachstamms](integration-framework.md#configuring-pages-for-translation) mit dem Übersetzungsdienstleister und den Framework-Konfigurationen.
1. [Identifizieren Sie die Art der zu übersetzenden Inhalte](rules.md).
1. [Bereiten Sie die Inhalte für die Übersetzung vor](preparation.md), indem Sie den Sprachstamm und die Stammseiten der Sprachkopien erstellen.
1. [Erstellen Sie Übersetzungsprojekte](managing-projects.md), um die zu übersetzenden Inhalte zusammenzustellen und den Übersetzungsprozess vorzubereiten.
1. Verwenden Sie die Übersetzungsprojekte, um [den Prozess zur Übersetzung der Inhalte zu verwalten](managing-projects.md).

Wenn Ihr Übersetzungsanbieter keinen Connector zur Integration mit AEM bereitstellt, unterstützt AEM auch die manuelle Extraktion und das erneute Einfügen von Übersetzungsinhalten im XML-Format.

>[!NOTE]
>
>Ihre Benutzerin bzw. Ihr Benutzer muss Mitglied der Gruppe `project-administrators` sein, um die Sprachkopie-Funktionen verwenden zu können.

## Best Practices {#best-practices}

Die Seite [Best Practices für die Übersetzung](best-practices.md) enthält wichtige Informationen zur Implementierung.
