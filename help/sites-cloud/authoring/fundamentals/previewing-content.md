---
title: Vorschau des Inhalts
description: Erfahren Sie, wie Sie mit dem AEM Preview Service vor der Live-Schaltung eine Vorschau des Inhalts anzeigen können.
source-git-commit: 9b4ac173c55380cbc06de64677470818aa801df4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Vorschau von Inhalten {#previewing-content}

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

