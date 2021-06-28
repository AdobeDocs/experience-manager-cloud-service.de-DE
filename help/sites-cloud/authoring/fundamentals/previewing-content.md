---
title: Vorschau des Inhalts
description: Erfahren Sie, wie Sie mit dem AEM Preview Service vor der Live-Schaltung eine Vorschau des Inhalts anzeigen können.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: e31fd00b05832e84f87221287f79038acbdb8ec3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Vorschau des Inhalts {#previewing-content}

>[!NOTE]
>
>Die Vorschaufunktion ist Teil der Version 2021.5.0 und wird in den nächsten Wochen schrittweise eingeführt.

AEM bietet einen Sites Preview Service, der Entwicklern und Inhaltsautoren die Vorschau des endgültigen Erlebnisses einer Website ermöglicht, bevor diese in die Veröffentlichungsumgebung gelangt und öffentlich verfügbar ist.

Dies erleichtert die Vorschau von Seitenerlebnissen, die sonst nicht in der Autorenumgebung sichtbar wären, wie Seitenübergänge und andere Inhalte, die nur auf der Veröffentlichungsseite verfügbar sind.

## Veröffentlichen von Inhalten in der Vorschau {#publishing-content-to-preview}

Sie können Inhalte mithilfe der Benutzeroberfläche &quot;Veröffentlichung verwalten&quot;wie folgt im Vorschaudienst veröffentlichen:

1. Wählen Sie die zu sendenden Seiten aus, um eine Vorschau in der Sites-Konsole anzuzeigen, und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten** .
1. Wählen Sie im folgenden Assistenten **Vorschau** als Ziel aus

   ![verwaltete Veröffentlichung](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klicken Sie auf **Weiter** und dann zur Bestätigung **Veröffentlichen**.

Zeigen Sie den Vorschauinhalt an und hängen Sie **preview** an die Veröffentlichungs-URL Ihrer Produktionsinstanz an. Die URL sollte wie folgt erstellt werden:

```
https://preview-p[programID]-e[environmentID].adobeaemcloud.com/pathtopage.html
```

Weitere Informationen zum Abrufen der URLs für Ihre Umgebungen finden Sie unter [Verwalten Ihrer Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/manage-your-environment.html?lang=en) .

Inhalte können auch zur Vorschau veröffentlicht werden, indem ein [Workflow der Inhaltsstruktur veröffentlichen](/help/operations/replication.md#publish-content-tree-workflow) verwendet wird, wobei der Parameter agentId für die Vorschau festgelegt ist, oder indem die [Replikations-API](/help/operations/replication.md#replication-api) mit einem für die Vorschau konfigurierten AgentFilter verwendet wird.

## Konfigurieren der OSGi-Einstellungen für die Vorschauebene {#configuring-osgi-settings-for-the-preview-tier}

Die OSGi-Eigenschaftswerte der Vorschaustufe werden von der Veröffentlichungsstufe übernommen, aber die Vorschaustufenwerte können mithilfe umgebungsspezifischer Werte, die den Dienstparameter mit dem Wert &quot;preview&quot;festlegen, von der Veröffentlichungsstufe unterschieden werden. Nehmen Sie das folgende Beispiel einer OSGi-Eigenschaft, die die URL eines Integrationsendpunkts bestimmt:

```
[
{
"name":"INTEGRATION_URL",
"type":"string",
"value":"http://s2.integrationvendor.com",
"service": "preview"
}
]
```

Weitere Informationen finden Sie in [diesem Abschnitt](/help/implementing/deploying/configuring-osgi.md#author-vs-publish-configuration) der OSGi-Konfigurationsdokumentation.

## Debugging der Vorschau mithilfe der Developer Console {#debugging-preview-using-the-developer-console}

Führen Sie die folgenden Schritte aus, um die Vorschauebene mithilfe der Developer Console zu debuggen:

* Wählen Sie in [Developer Console](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools) entweder **— All Preview —** oder eine Produktionsumgebung aus, die **prev** im Namen enthält.
* Generieren Sie die relevanten Informationen für die Vorschauinstanz
Weitere Informationen zum Abrufen der URLs für Ihre Umgebungen finden Sie unter [Verwalten Ihrer Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/manage-your-environment.html?lang=en) .
