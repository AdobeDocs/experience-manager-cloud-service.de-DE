---
title: Vorschau von Inhalten
description: Erfahren Sie, wie Sie mit dem AEM Preview Service vor der Live-Schaltung eine Vorschau von Inhalten anzeigen können.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: b93bcb5d26a63babf0b81c92a4fd85d358bfbea7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 82%

---


# Vorschau von Inhalten {#previewing-content}

AEM bietet den Sites Preview Service, der Entwicklern und Inhaltsautoren die Vorschau des endgültigen Erlebnisses einer Website ermöglicht, bevor diese in die Veröffentlichungsumgebung gelangt und öffentlich verfügbar ist.

Dies erleichtert die Vorschau von Seitenerlebnissen, die sonst nicht in der Autorenumgebung sichtbar wären, wie Seitenübergänge und andere Inhalte, die nur auf der Veröffentlichungsseite verfügbar sind.

>[!IMPORTANT]
>
>Für den Zugriff auf die Vorschau-Umgebung ist die Konfiguration einer IP-Zulassungsliste erforderlich. Weitere Informationen finden Sie [Zugriff auf den Vorschau-Service](/help/implementing/cloud-manager/manage-environments.md#access-preview-service#access-preview-service).
>
>Weitere Informationen zu allen Umgebungen finden Sie unter [Umgebungen verwalten](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

>[!NOTE]
>
>Da der Inhalt in *Vorschauumgebung veröffentlicht*, ist er über eine URL zugänglich.

## Veröffentlichen von Inhalten in der Vorschau {#publishing-content-to-preview}

Sie können Inhalte mithilfe der Benutzeroberfläche **Verwaltete Veröffentlichung** wie folgt im Preview Service veröffentlichen.

1. Wählen Sie in der Sites-Konsole die zu sendenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.
1. Wählen Sie im folgenden Assistenten **Vorschau** als Ziel aus.

   ![verwaltete Veröffentlichung](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klicken Sie auf **Weiter** und dann auf **Veröffentlichen** zur Bestätigung.

1. In einem Dialogfeld werden die URLs für den Zugriff auf die Inhalte in der Vorschau-Umgebung angezeigt.

   >[!NOTE]
   >
   >Sobald der Inhalt in der Vorschauumgebung *veröffentlicht* wird, ist er über die URL zugänglich (er erfordert also keinen Zugriff auf AEM).

Alternativ dazu können Sie auch die im Assistenten angezeigten URLs verwenden, um den Vorschauinhalt anzuzeigen. Sie können der Veröffentlichungs-URL Ihrer Produktionsinstanz auch ein `preview-` voranstellen.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Weitere Informationen [ Abrufen der URLs für Ihre ](/help/implementing/cloud-manager/manage-environments.md) finden Sie unter „Verwalten von Umgebungen“.

Inhalte können auch zur Vorschau veröffentlicht werden, indem ein [Workflow zur Veröffentlichung der Inhaltsstruktur](/help/operations/replication.md#publish-content-tree-workflow) verwendet wird, wobei der Parameter `agentId` für die Vorschau auf `preview` festgelegt ist, oder indem die [Replikations-API](/help/operations/replication.md#replication-api) mit einem für die Vorschau konfigurierten `AgentFilter` verwendet wird.

## Rückgängigmachen der Veröffentlichung von Inhalten in der Vorschau {#unpublishing-content-from-preview}

Das Rückgängigmachen der Veröffentlichung von Inhalten in der **Vorschau**-Umgebung entspricht im Wesentlichen dem Prozess des [Rückgängigmachens der Veröffentlichung von Seiten](/help/sites-cloud/authoring/sites-console/publishing-pages.md#unpublishing-pages) in der **Veröffentlichungs**-Umgebung.

Der einzige Unterschied besteht darin, dass Sie als **Ziel** **Vorschau** auswählen.
