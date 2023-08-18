---
title: Migrieren geschlossener Benutzergruppen
description: Auf dieser Seite finden Sie die erforderlichen, besonderen Überlegungen, um geschlossene Benutzergruppen nach der Migration von Inhalten zu Adobe Experience Manager as a Cloud Service zu aktivieren.
hide: true
hidefromtoc: true
source-git-commit: 9da813d39d154e81da5b9814aa86b8318dc0bb3a
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 3%

---

# Migrieren geschlossener Benutzergruppen {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migration geschlossener Benutzergruppen"
>abstract="Für die Migration geschlossener Benutzergruppen (CUG) sind derzeit einige Prüfungen und Schritte erforderlich, damit sie nach einer Migration betriebsbereit ist."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=de" text="Geschlossene Benutzergruppen in AEM"

Derzeit benötigen geschlossene Benutzergruppen (CUG) einige zusätzliche Schritte, um in der Zielumgebung einer Migration verwendet zu werden.  In diesem Dokument werden das Szenario und die Schritte erläutert, die erforderlich sind, damit Knoten auf die beabsichtigte Weise geschützt werden.

## Migration von Gruppen

Prinzipale (einschließlich Gruppen) werden automatisch in eine Migration nach Adobe Experience Manager as a Cloud Service einbezogen, wenn sie über die ACL dieses Inhalts mit den migrierten Inhalten verknüpft sind.

## Geschlossene Benutzergruppen in der Migration

Derzeit sind Gruppen zugeordnet *only* mit einer CUG-Richtlinie (Closed User Group) *not* automatisch in die Erfassung einbezogen werden. Wie oben erwähnt, werden sie migriert, wenn sie über eine ACL mit Inhalten verknüpft sind. Vor der Live-Schaltung sollte überprüft werden, ob die Gruppe und ihre Mitglieder vorhanden sind. Der Hauptbericht, der über die Ansicht &quot;Ingestions Job&quot;heruntergeladen wurde, kann verwendet werden, um zu sehen, ob die betreffende Gruppe enthalten war oder nicht, weil sie nicht in einer ACL enthalten war. Wenn die Gruppe nicht vorhanden ist, sollte sie in der -Autoreninstanz erstellt und entsprechende Mitglieder hinzugefügt und aktiviert werden, damit sie in der -Veröffentlichungsinstanz vorhanden ist. Dies kann mithilfe von auf der Quelle erstellten Paketen erfolgen.

Schließlich müssen Prozesse ausgelöst und Eigenschaften festgelegt werden, um CUGs zu aktivieren. Veröffentlichen Sie dazu alle Seiten, die mit einer CUG-Richtlinie verknüpft sind, erneut. Dadurch wird die Veröffentlichungsinstanz kalibriert, um die Richtlinien zu verfolgen.

Dadurch werden CUG-Richtlinien für die Veröffentlichung aktiviert und der Inhalt kann nur für authentifizierte Benutzer zugänglich sein, die Mitglieder der Gruppe sind, die mit den Richtlinien verknüpft ist.

## Aktive Entwicklung

Das Migrationsteam arbeitet daran, CUG-Richtlinien automatisch zu migrieren und zu funktionieren, ohne dass nach der Aufnahme des Inhalts weitere Schritte erforderlich sind.
Es ist ratsam, CUG-Funktionen in alle Testprozesse aufzunehmen, bevor Sie versuchen, live zu gehen.

## Zusammenfassung

Zusammenfassend sind dies die Schritte, um CUG nach einer Migration zu aktivieren:

1. Stellen Sie sicher, dass jede in CUG-Richtlinien verwendete Gruppe nach der Migration in der Veröffentlichungsinstanz vorhanden ist.
   - Eine Gruppe kann bereits vorhanden sein, wenn sie in der ACL eines migrierten Inhalts enthalten ist.
   - Ist dies nicht der Fall, installieren Sie Pakete in der Zielinstanz (oder erstellen Sie sie manuell dort) und aktivieren Sie sie und ihre Mitglieder. Überprüfen Sie dann, ob es in der Veröffentlichungsinstanz vorhanden ist.
1. Veröffentlichen Sie alle mit einer CUG-Richtlinie verknüpften Seiten erneut, und stellen Sie sicher, dass sie veröffentlicht werden, indem Sie beispielsweise die Seite zuerst bearbeiten. Es ist wichtig, alle erneut zu veröffentlichen.
   - Nachdem alle Seiten erneut veröffentlicht wurden, überprüfen Sie die Funktionalität für jede CUG-geschützte Seite.

