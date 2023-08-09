---
title: Migrieren geschlossener Benutzergruppen
description: Auf dieser Seite finden Sie die erforderlichen, besonderen Überlegungen, um geschlossene Benutzergruppen nach der Migration von Inhalten zu Adobe Experience Manager as a Cloud Service zu aktivieren.
hide: true
hidefromtoc: true
source-git-commit: ca3c4bae2e652d75190d68c76b1dd4e09239f16c
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---

# Migrieren geschlossener Benutzergruppen {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migration geschlossener Benutzergruppen"
>abstract="Für die Migration geschlossener Benutzergruppen (CUG) sind derzeit einige Prüfungen und Schritte erforderlich, damit sie nach einer Migration wirksam werden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html" text="Geschlossene Benutzergruppen in AEM"

Derzeit benötigen geschlossene Benutzergruppen (CUG) einige zusätzliche Schritte, um in der Zielumgebung einer Migration verwendet zu werden.  In diesem Dokument werden das Szenario und die Schritte erläutert, die erforderlich sind, damit Knoten auf die beabsichtigte Weise geschützt werden.

## Migration von Gruppen

Prinzipale (einschließlich Gruppen) werden automatisch in eine Migration nach Adobe Experience Manager as a Cloud Service einbezogen, wenn sie über die ACL dieses Inhalts mit den migrierten Inhalten verknüpft sind.

## Geschlossene Benutzergruppen in der Migration

Derzeit sind Gruppen zugeordnet *only* mit einer CUG-Richtlinie (Closed User Group) *not* automatisch in die Erfassung einbezogen werden. Wenn sie wie oben beschrieben über eine ACL mit Inhalten verknüpft sind, werden sie migriert. Überprüfen Sie, ob die Gruppe vorhanden ist, bevor Sie live gehen. Der Hauptbericht, der über die Ansicht &quot;Ingestions Job&quot;heruntergeladen wurde, kann verwendet werden, um zu sehen, ob die betreffende Gruppe enthalten war oder nicht, weil sie nicht in einer ACL enthalten war. Wenn die Gruppe nicht vorhanden ist, sollte sie in der -Autoreninstanz erstellt und entsprechende Mitglieder hinzugefügt und aktiviert werden, damit sie in der -Veröffentlichungsinstanz vorhanden ist.

Schließlich müssen Prozesse ausgelöst werden, um CUG zu aktivieren. Veröffentlichen Sie dazu jeden Inhalt, der die CUG-Richtlinie enthält, erneut. Wenn also in Ihren normalen Testprozessen festgestellt wird, dass die CUG nicht funktioniert, veröffentlichen Sie den Inhalt erneut (stellen Sie sicher, dass er veröffentlicht wird, auch wenn er nicht geändert wurde).

Dies sollte CUG-Richtlinien für die Veröffentlichung aktivieren. Der Inhalt ist nur für authentifizierte Benutzer zugänglich, die Mitglieder der Gruppe sind, die mit den Richtlinien verknüpft ist.

## Aktive Entwicklung

Das Migrationsteam arbeitet daran, CUG-Richtlinien automatisch zu migrieren und zu funktionieren, ohne dass nach der Aufnahme des Inhalts weitere Schritte erforderlich sind.
Es ist ratsam, CUG-Funktionen in alle Testprozesse aufzunehmen, bevor Sie versuchen, live zu gehen.

## Zusammenfassung

Zusammenfassend sind dies die Schritte, um CUG nach einer Migration zu aktivieren:

1. Stellen Sie sicher, dass jede in CUG-Richtlinien verwendete Gruppe nach der Migration in der Veröffentlichungsinstanz vorhanden ist.
   - Eine Gruppe kann bereits vorhanden sein, wenn sie in der ACL eines migrierten Inhalts enthalten ist.
   - Ist dies nicht der Fall, installieren Sie Pakete in der Zielinstanz (oder erstellen Sie sie manuell dort) und aktivieren Sie sie und ihre Mitglieder. Überprüfen Sie dann, ob es in der Veröffentlichungsinstanz vorhanden ist.
1. Wenn die CUG-Richtlinie den Knoten noch nicht schützt, veröffentlichen Sie die Seite erneut (stellen Sie sicher, dass sie veröffentlicht wird, selbst wenn keine Änderungen an dieser Seite vorgenommen wurden).
   - Überprüfen Sie für jeden CUG-geschützten Knoten.
