---
title: Konfigurieren der OSGi-Einstellungen für die Vorschauebene
description: Erfahren Sie, wie Sie den AEM-Vorschaudienst konfigurieren, um vor der Live-Schaltung eine Vorschau des Inhalts anzuzeigen.
exl-id: 1200bb17-8a3c-4e41-85f4-ed2334b61f69
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 53%

---

# Konfigurieren der OSGi-Einstellungen für die Vorschauebene {#configure-osgi-preview-tier}

AEM bietet einen Sites-Vorschaudienst, mit dem Entwickler und Inhaltsautoren eine Vorschau des endgültigen Erlebnisses einer Website anzeigen können, bevor diese in die Veröffentlichungsumgebung gelangt und öffentlich verfügbar ist.

Dies erleichtert die Vorschau einer Reihe von Erlebnissen, die sonst nicht in der Autorenumgebung sichtbar wären. Beispielsweise Seitenübergänge, Experience Fragments und andere Inhalte, die ausschließlich auf der Veröffentlichungsseite enthalten sind.

Die OSGi-Eigenschaftswerte der Vorschauebene werden von der Veröffentlichungsebene übernommen. Die Werte der Vorschauebene können sich jedoch von der Veröffentlichungsebene unterscheiden, wenn Sie den Parameter `service` auf den Wert `preview` setzen. 

>[!NOTE]
>
>Weitere Informationen zu den Vorschauumgebungen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

## Konfigurieren der OSGi-Einstellungen für die Vorschauebene {#configuring-osgi-settings-for-the-preview-tier}

Das folgende Beispiel für eine OSGi-Eigenschaft bestimmt die URL eines Integrationsendpunkts.

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

Führen Sie die folgenden Schritte aus, um die Vorschauebene mithilfe der Developer Console zu debuggen:

* Wählen Sie in [Entwicklungs-Konsole](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools) entweder **-- Vorschau für alle --** oder eine Produktionsumgebung aus, die **prev** im Namen enthält.
* Erzeugen von relevanten Informationen für die Vorschauinstanz
Weitere Informationen zum Abrufen der URLs für Ihre Umgebungen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md).
