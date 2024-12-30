---
title: Migrieren geschlossener Benutzergruppen
description: Erfahren Sie mehr über die erforderlichen besonderen Überlegungen, um geschlossene Benutzergruppen nach der Migration von Inhalten zu Adobe Experience Manager as a Cloud Service zu aktivieren.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
feature: Migration
role: Admin
source-git-commit: c721a8db801602389822222b08ca4ea1fd2293e4
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 100%

---


# Migrieren geschlossener Benutzergruppen {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migration geschlossener Benutzergruppen"
>abstract="Für die Migration geschlossener Benutzergruppen (CUG) sind derzeit einige Prüfungen und Schritte erforderlich, damit es nach einer Migration betriebsbereit ist."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-65/content/security/closed-user-groups" text="Geschlossene Benutzergruppen in AEM"

Derzeit benötigen geschlossene Benutzergruppen (CUG) einige zusätzliche Schritte, um in der Zielumgebung einer Migration verwendet werden zu können. In diesem Dokument werden das Szenario und die Schritte erläutert, die erforderlich sind, damit Knoten auf die beabsichtigte Weise geschützt werden.

## Migration geschlossener Benutzergruppen (CUGs)

Gruppen werden automatisch in eine CTT/CAM-Migration zu Adobe Experience Manager as a Cloud Service einbezogen, wenn sie über die ACL dieses Inhalts oder durch seinen CUG-Richtlinienknoten mit den migrierten Inhalten verknüpft sind. Vor der Live-Schaltung sollte überprüft werden, ob die Gruppe und ihre Mitglieder vorhanden sind. Gruppen, auf die eine CUG-Richtlinie verweist, werden hier als „CUGs-Gruppen“ bezeichnet.

Um CUGs in AEM as a Cloud Service zu verwenden, müssen Benutzende in der Autoreninstanz vorhanden und Mitglieder der entsprechenden CUGs-Gruppen sein.  Dies kann mithilfe von Paketen erreicht werden. Wenn die CUGs-Benutzenden IMS-Benutzende sind, sind sie möglicherweise bereits vorhanden.  CUGs-Benutzende müssen dann Mitglieder der AEM CUGs-Gruppen werden.

Um das CUGs-Verhalten auf der Veröffentlichungsinstanz zu aktivieren,
1. müssen die CUGs-Gruppen aktiviert werden (wodurch sie und ihre Mitglieder in der Veröffentlichungsinstanz repliziert werden),
1. Die Veröffentlichung *aller* mit CUGs-Richtlinien geschützten Seiten muss rückgängig gemacht werden (um die globale CUGs-Anzahl zu löschen) und
1. die mit CUGs-Richtlinien geschützten Seiten müssen anschließend veröffentlicht werden (dies ermöglicht die Veröffentlichungsinstanz und das Tracking der Richtlinien).
1. Nachdem alle Seiten veröffentlicht wurden, überprüfen Sie die Funktionalität für jede CUG-geschützte Seite.

Weitere Informationen finden Sie unter [Geschlossene Benutzergruppen](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/security/closed-user-groups).
