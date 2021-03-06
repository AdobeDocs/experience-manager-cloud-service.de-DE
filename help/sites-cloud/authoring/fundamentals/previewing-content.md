---
title: Vorschau von Inhalten
description: Erfahren Sie, wie Sie mit dem AEM Preview Service vor der Live-Schaltung eine Vorschau von Inhalten anzeigen können.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 66bc262b35f69b7877e4a01df9ab26395afd604d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 93%

---


# Vorschau von Inhalten {#previewing-content}

AEM bietet den Sites Preview Service, der Entwicklern und Inhaltsautoren die Vorschau des endgültigen Erlebnisses einer Website ermöglicht, bevor diese in die Veröffentlichungsumgebung gelangt und öffentlich verfügbar ist.

Dies erleichtert die Vorschau von Seitenerlebnissen, die sonst nicht in der Autorenumgebung sichtbar wären, wie Seitenübergänge und andere Inhalte, die nur auf der Veröffentlichungsseite verfügbar sind.

Weitere Informationen zu den Vorschauumgebungen finden Sie im Dokument [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

>[!NOTE]
>
>Beim Veröffentlichen eines Experience Fragments in der Vorschau wird im Wesentlichen das gleiche Verfahren wie für eine Seite angewendet, allerdings in der Konsole oder im Editor für Experience Fragments.

## Veröffentlichen von Inhalten in der Vorschau {#publishing-content-to-preview}

Sie können Inhalte mithilfe der Benutzeroberfläche **Verwaltete Veröffentlichung** wie folgt im Preview Service veröffentlichen.

1. Wählen Sie in der Sites-Konsole die zu sendenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.
1. Wählen Sie im folgenden Assistenten **Vorschau** als Ziel aus.

   ![verwaltete Veröffentlichung](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klicken Sie auf **Weiter** und dann auf **Veröffentlichen** zur Bestätigung.

1. In einem Dialogfeld werden die URLs für den Zugriff auf die Inhalte in der Vorschau-Umgebung angezeigt.


Alternativ dazu können Sie auch die im Assistenten angezeigten URLs verwenden, um den Vorschauinhalt anzuzeigen. Sie können der Veröffentlichungs-URL Ihrer Produktionsinstanz auch ein `preview-` voranstellen.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Weitere Informationen zum Abrufen der URLs für Ihre Umgebungen finden Sie im Dokument [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md).

Inhalte können auch zur Vorschau veröffentlicht werden, indem ein [Workflow zur Veröffentlichung der Inhaltsstruktur](/help/operations/replication.md#publish-content-tree-workflow) verwendet wird, wobei der Parameter `agentId` für die Vorschau auf `preview` festgelegt ist, oder indem die [Replikations-API](/help/operations/replication.md#replication-api) mit einem für die Vorschau konfigurierten `AgentFilter` verwendet wird.

## Konfigurieren der OSGi-Einstellungen für die Vorschauebene {#configuring-osgi-settings-for-the-preview-tier}

Die OSGi-Eigenschaftswerte der Vorschauebene werden von der Veröffentlichungsebene übernommen. Die Werte der Vorschauebene können sich jedoch von der Veröffentlichungsebene unterscheiden, wenn Sie den Parameter `service` auf den Wert `preview` setzen. Das folgende Beispiel für eine OSGi-Eigenschaft bestimmt die URL eines Integrationsendpunkts.

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

In [diesem Abschnitt](/help/implementing/deploying/configuring-osgi.md#author-vs-publish-configuration) finden Sie weitere Informationen zur OSGi-Konfigurationsdokumentation.

## Debugging der Vorschau mithilfe der Entwicklungs-Konsole {#debugging-preview-using-the-developer-console}

Führen Sie die folgenden Schritte aus, um die Vorschauebene mithilfe der Entwicklungs-Konsole zu debuggen:

* Wählen Sie in [Entwicklungs-Konsole](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools) entweder **-- Vorschau für alle --** oder eine Produktionsumgebung aus, die **prev** im Namen enthält.
* Erzeugen von relevanten Informationen für die Vorschauinstanz
Weitere Informationen zum Abrufen der URLs für Ihre Umgebungen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md).
