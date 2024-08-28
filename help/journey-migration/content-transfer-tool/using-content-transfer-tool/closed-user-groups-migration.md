---
title: Migrieren geschlossener Benutzergruppen
description: Erfahren Sie mehr über die erforderlichen besonderen Überlegungen, um geschlossene Benutzergruppen nach der Migration von Inhalten zu Adobe Experience Manager as a Cloud Service zu aktivieren.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
feature: Migration
role: Admin
source-git-commit: 5b0dfb847a1769665899d6dd693a7946832fe7d1
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 32%

---


# Migrieren geschlossener Benutzergruppen {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migration geschlossener Benutzergruppen"
>abstract="Für die Migration geschlossener Benutzergruppen (CUG) sind derzeit einige Prüfungen und Schritte erforderlich, damit es nach einer Migration betriebsbereit ist."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=de" text="Geschlossene Benutzergruppen in AEM"

Derzeit benötigen geschlossene Benutzergruppen (CUG) einige zusätzliche Schritte, um in der Zielumgebung einer Migration verwendet werden zu können. In diesem Dokument werden das Szenario und die Schritte erläutert, die erforderlich sind, damit Knoten auf die beabsichtigte Weise geschützt werden.

## Migration geschlossener Benutzergruppen (CUGs)

Gruppen werden automatisch in eine CTT-/CAM-Migration nach Adobe Experience Manager as a Cloud Service eingeschlossen, wenn sie über den ACL-Knoten oder den CUG-Richtlinienknoten mit den migrierten Inhalten verknüpft sind. Vor der Live-Schaltung sollte überprüft werden, ob die Gruppe und ihre Mitglieder vorhanden sind. Gruppen, auf die eine CUG-Richtlinie verweist, werden hier als &quot;CUGs-Gruppen&quot;bezeichnet.

Um CUGs in AEM as a Cloud Service zu verwenden, müssen Benutzer in der Autoreninstanz vorhanden sein und Mitglieder der entsprechenden CUGs-Gruppen sein.  Dies kann mithilfe von Paketen erreicht werden, oder wenn die CUGs-Benutzer IMS-Benutzer sind, sind sie möglicherweise bereits vorhanden.  CUGs-Benutzer müssen dann Mitglieder der AEM CUGs-Gruppen sein.

Um das CUGs-Verhalten auf der Publish-Instanz zu aktivieren,
1. Die CUGs-Gruppen müssen aktiviert sein (wodurch sie und ihre Mitglieder in der Publish-Instanz repliziert werden) und
1. Die mit CUGs-Richtlinien geschützten Seiten müssen veröffentlicht werden (dies ermöglicht die Publish-Instanz und das Tracking der Richtlinien).
1. Nachdem alle Seiten veröffentlicht wurden, überprüfen Sie die Funktionalität für jede CUG-geschützte Seite.

Weitere Informationen finden Sie unter [Geschlossene Benutzergruppen](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=de).
