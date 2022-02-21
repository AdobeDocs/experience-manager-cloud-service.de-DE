---
title: Vorschau von Inhalten
description: Erfahren Sie, wie Sie mit dem AEM Vorschaudienst Inhalte vor der Live-Schaltung in der Vorschau anzeigen können.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: e70e6ee055c2542752e66e53aa70a9378b1bc5c0
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 30%

---


# Vorschau von Inhalten {#previewing-content}

AEM bietet einen Sites-Vorschaudienst, mit dem Entwickler und Inhaltsautoren eine Vorschau des finalen Erlebnisses einer Website anzeigen können, bevor diese in die Veröffentlichungsumgebung gelangt. Dieser Dienst ist öffentlich verfügbar.

Dies erleichtert die Vorschau von Seitenerlebnissen, die sonst nicht in der Autorenumgebung sichtbar wären, wie Seitenübergänge und andere Inhalte, die nur auf der Veröffentlichungsseite verfügbar sind.

Weitere Informationen zu den Vorschauumgebungen finden Sie im Dokument [Verwalten von Umgebungen.](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

## Veröffentlichen von Inhalten in der Vorschau {#publishing-content-to-preview}

Sie können Inhalte mithilfe der **Verwaltete Veröffentlichung** Benutzeroberfläche.

1. Wählen Sie in der Sites-Konsole die zu sendenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten** button
1. Wählen Sie im folgenden Assistenten **Vorschau** als Ziel aus.

   ![verwaltete Veröffentlichung](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Klicken Sie auf **Weiter** und dann auf **Veröffentlichen** zur Bestätigung.

1. In einem Dialogfeld werden die URLs für den Zugriff auf den Inhalt in der Vorschauumgebung angezeigt.


Alternativ dazu können Sie auch die im Assistenten angezeigten URLs verwenden, um den Vorschauinhalt anzuzeigen, und `preview-` in die Veröffentlichungs-URL Ihrer Produktionsinstanz ein.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Siehe Dokument . [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md) für weitere Informationen zum Abrufen der URLs für Ihre Umgebungen.

Inhalte können auch mithilfe einer [Arbeitsablauf für Veröffentlichungsinhalte](/help/operations/replication.md#publish-content-tree-workflow) mit dem `agentId` Parameter festgelegt auf `preview` oder mithilfe der [Replikations-API](/help/operations/replication.md#replication-api) mit einer `AgentFilter` für die Vorschau konfiguriert.

## Konfigurieren der OSGi-Einstellungen für die Vorschauebene {#configuring-osgi-settings-for-the-preview-tier}

Die OSGi-Eigenschaftswerte der Vorschaustufe werden von der Veröffentlichungsstufe übernommen. Die Werte der Vorschaustufe können sich jedoch von der Veröffentlichungsstufe unterscheiden, indem Sie die `service` Parameter auf den Wert `preview`. Das folgende Beispiel einer OSGi-Eigenschaft bestimmt die URL eines Integrationsendpunkts.

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
