---
title: Vorschau von Inhalten
description: Erfahren Sie, wie Sie mit dem AEM Preview Service vor der Live-Schaltung eine Vorschau von Inhalten anzeigen können.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 78c5649c6b9c04cb459f5730161affeb452c916c
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# Vorschau von Inhalten {#previewing-content}

>[!NOTE]
>
>Um die Vorschaufunktion für Umgebungen zu aktivieren, die vor dem 3. August 2021 erstellt wurden, stellen Sie sicher, dass die Umgebung AEM Version 2021.05.5368.20210529T101701Z oder höher ist, und führen Sie dann eine kundeninitiierte Pipeline aus.

AEM bietet den Sites Preview Service, der Entwicklern und Inhaltsautoren die Vorschau des endgültigen Erlebnisses einer Website ermöglicht, bevor diese in die Veröffentlichungsumgebung gelangt und öffentlich verfügbar ist.

Dies erleichtert die Vorschau von Seitenerlebnissen, die sonst nicht in der Autorenumgebung sichtbar wären, wie Seitenübergänge und andere Inhalte, die nur auf der Veröffentlichungsseite verfügbar sind.

Weitere Informationen finden Sie unter [Zugriff auf den Vorschau-Service](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

## Veröffentlichen von Inhalten in der Vorschau {#publishing-content-to-preview}

Sie können Inhalte mithilfe der Benutzeroberfläche „Verwaltete Vöffentlichung“ wie folgt im Vorschau-Service veröffentlichen:

1. Wählen Sie die zu sendenden Seiten aus, um eine Vorschau in der Sites-Konsole anzuzeigen, und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.
1. Wählen Sie im folgenden Assistenten **Vorschau** als Ziel aus.

   ![verwaltete Veröffentlichung](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klicken Sie auf **Weiter** und dann auf **Veröffentlichen** zur Bestätigung.

1. In einem Dialogfeld werden die URLs für den Zugriff auf die Inhalte in der Vorschau-Umgebung angezeigt.

   Sie können auch **preview** an die Veröffentlichungs-URL Ihrer Produktionsinstanz anhängen, um den Vorschauinhalt anzuzeigen.

   Die URL sollte wie folgt aufgebaut sein:

   ```
   https://preview-p[programID]-e[environmentID].adobeaemcloud.com/pathtopage.html
   ```

Weitere Informationen zum Abrufen der URLs für Ihre Umgebungen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md).

Inhalte können auch zur Vorschau veröffentlicht werden, indem ein [Workflow zur Veröffentlichung der Inhaltsstruktur](/help/operations/replication.md#publish-content-tree-workflow) verwendet wird, wobei der Parameter „agentId“ für die Vorschau festgelegt ist, oder indem die [Replikations-API](/help/operations/replication.md#replication-api) mit einem für die Vorschau konfigurierten AgentFilter verwendet wird.

## Konfigurieren der OSGi-Einstellungen für die Vorschauebene {#configuring-osgi-settings-for-the-preview-tier}

Die OSGi-Eigenschaftswerte der Vorschauebene werden von der Veröffentlichungsebene übernommen, aber die Werte der Vorschauebene können mithilfe umgebungsspezifischer Werte, die den Service-Parameter mit dem Wert „preview“ festlegen, von der Veröffentlichungsebene unterschieden werden. Nehmen Sie das folgende Beispiel einer OSGi-Eigenschaft, die die URL eines Integrationsendpunkts bestimmt:

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
