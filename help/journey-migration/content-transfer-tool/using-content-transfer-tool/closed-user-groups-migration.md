---
title: Migration geschlossener Benutzergruppen
description: Erfahren Sie mehr über die erforderlichen besonderen Aspekte, um geschlossene Benutzergruppen nach der Migration von Inhalten zu Adobe Experience Manager as a Cloud Service zu aktivieren.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 9%

---

# Migration geschlossener Benutzergruppen {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migrieren von geschlossenen Benutzergruppen"
>abstract="Für die Migration geschlossener Benutzergruppen (CUG) sind derzeit einige Prüfungen und Schritte erforderlich, damit es nach einer Migration betriebsbereit ist."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=de" text="Geschlossene Benutzergruppen in AEM"

Derzeit benötigen geschlossene Benutzergruppen (CUG) einige zusätzliche Schritte, um in der Zielumgebung einer Migration verwendet zu werden. In diesem Dokument werden das Szenario und die Schritte erläutert, die erforderlich sind, damit Knoten auf die beabsichtigte Weise geschützt werden.

## Migration von Gruppen

Prinzipale (einschließlich Gruppen) werden automatisch in eine Migration nach Adobe Experience Manager as a Cloud Service einbezogen, wenn sie über die ACL dieses Inhalts mit den migrierten Inhalten verknüpft sind.

## Geschlossene Benutzergruppen in der Migration

Derzeit sind Gruppen zugeordnet *only* mit einer CUG-Richtlinie (Closed User Group) *not* automatisch in die Erfassung einbezogen werden. Wie oben erwähnt, werden sie migriert, wenn sie mit Inhalten über eine ACL verknüpft sind. Vor der Live-Schaltung sollte überprüft werden, ob die Gruppe und ihre Mitglieder vorhanden sind. Der Hauptbericht, der über die Ansicht &quot;Ingestions Job&quot;heruntergeladen wurde, kann verwendet werden, um zu sehen, ob die betreffende Gruppe enthalten war oder nicht, weil sie nicht in einer ACL enthalten war. Wenn die Gruppe nicht vorhanden ist, sollte sie in der Autoreninstanz erstellt werden, einschließlich des Hinzufügens entsprechender Mitglieder, und aktiviert werden, damit sie in der Veröffentlichungsinstanz vorhanden ist. Dies kann mithilfe von auf der Quelle erstellten Paketen erfolgen.

Schließlich müssen Prozesse ausgelöst und Eigenschaften festgelegt werden, um CUGs zu aktivieren. Veröffentlichen Sie dazu alle Seiten erneut, die mit einer CUG-Richtlinie verknüpft sind. Dadurch wird die Veröffentlichungsinstanz kalibriert, um die Richtlinien zu verfolgen.

Dies ermöglicht CUG-Richtlinien für die Veröffentlichung. Der Inhalt ist nur für authentifizierte Benutzer zugänglich, die Mitglieder der Gruppe sind, die den Richtlinien zugeordnet ist.

## Aktive Entwicklung

Das Migrationsteam arbeitet daran, CUG-Richtlinien automatisch zu migrieren und zu funktionieren, ohne dass nach der Aufnahme des Inhalts weitere Schritte erforderlich sind.
Schließen Sie CUG-Funktionen in alle Testprozesse ein, bevor Sie versuchen, live zu gehen.

## Zusammenfassung

Zusammenfassend sind dies die Schritte, um CUG nach einer Migration zu aktivieren:

1. Stellen Sie sicher, dass jede in CUG-Richtlinien verwendete Gruppe nach der Migration in der Veröffentlichungsinstanz vorhanden ist.
   - Eine Gruppe kann vorhanden sein, wenn sie in der ACL migrierter Inhalte enthalten ist.
   - Ist dies nicht der Fall, installieren Sie Pakete in der Zielinstanz (oder erstellen Sie sie dort manuell) und aktivieren Sie sie und ihre Mitglieder. Überprüfen Sie dann, ob es in der Veröffentlichungsinstanz vorhanden ist.
1. Veröffentlichen Sie alle mit einer CUG-Richtlinie verknüpften Seiten erneut, und stellen Sie sicher, dass sie veröffentlicht werden, indem Sie beispielsweise die Seite zuerst bearbeiten. Es ist wichtig, sie alle erneut zu veröffentlichen.
   - Nachdem alle Seiten erneut veröffentlicht wurden, überprüfen Sie die Funktionalität für jede CUG-geschützte Seite.
