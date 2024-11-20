---
title: Gruppenmigration
description: Überblick über die Gruppenmigration in AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 7e7b311d425ae6cdee9eb9311c0a12af84f81096
workflow-type: ht
source-wordcount: '1447'
ht-degree: 100%

---


# Gruppenmigration {#group-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_groupmigration"
>title="Gruppenmigration"
>abstract="Mit dem Content Transfer Tool können Gruppen von einem bestehenden Adobe Experience Manager(AEM)-System nach AEM as a Cloud Service kopiert werden."

>[!NOTE]
>Frühere Versionen des Tools für die Benutzerzuordnung finden Sie in der [Legacy-Dokumentation](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Einführung {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermigration"
>title="Benutzende werden nicht migriert"
>abstract="Das Content Transfer Tool führt keine Benutzermigration mehr durch. Benutzende sollten in Admin Console verwaltet werden."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="AEM Admin Console-Dokumentation"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

Im Rahmen der Umstellung auf Adobe Experience Manager (AEM) as a Cloud Service müssen Gruppen von bestehenden AEM-Systemen zu AEM as a Cloud Service migriert werden. Diese Aufgabe wird vom Content Transfer Tool durchgeführt.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Authoring-Ebene. Dieser Prozess setzt voraus, dass die [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzenden und Benutzergruppen verwendet wird. Die Benutzerprofilinformationen sind im Identity Management System (IMS) von Adobe zentralisiert, das Single Sign-on über alle Adobe-Cloud-Anwendungen hinweg bereitstellt. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=de#identity-management). Aufgrund dieser Änderung werden Benutzende automatisch in AEM erstellt, wenn sie sich zum ersten Mal über IMS anmelden.  Daher migriert CTT die Benutzenden nicht zum Cloud-System.  IMS-Benutzende müssen in IMS-Gruppen platziert werden. Hierbei kann es sich um migrierte Gruppen oder neue Gruppen in den AEM-Gruppen handeln, denen Zugriff auf die migrierten AEM-Inhalte gewährt wurde.  Dadurch haben Benutzende auf dem Cloud-System denselben Zugriff wie bei ihrem AEM-Quellsystem.

## Details zur Gruppenmigration {#group-migration-detail}

Das Content Transfer Tool und Cloud Acceleration Manager migrieren alle Gruppen, die mit den zum Cloud-System migrierten Inhalten verbunden sind. Das Content Transfer Tool kopiert dazu während des Extraktionsvorgangs alle Gruppen aus dem AEM-Quellsystem. CAM Ingestion wählt dann nur bestimmte Gruppen aus und migriert diese:

* Es gibt eine Reihe von Gruppen, die integriert und bereits im Cloud-Zielsystem vorhanden sind. Diese werden nie migriert.
* Direkte Mitgliedergruppen aller integrierten Gruppen, auf die in einer ACL- oder CUG-Richtlinie für migrierte Inhalte direkt oder indirekt verwiesen wird, werden migriert, um sicherzustellen, dass Benutzende, die direkte oder indirekte Mitglieder dieser Gruppen sind, ihren Zugriff auf die migrierten Inhalte behalten.
* Wenn sich eine Gruppe in einer ACL- oder CUG-Richtlinie mit migrierten Inhalten befindet, wird diese Gruppe migriert.
* Andere Gruppen, z. B. Gruppen, die sich nicht in einer ACL- oder CUG-Richtlinie befinden, Gruppen, die bereits im Zielsystem vorhanden sind, und Gruppen mit bereits im Zielsystem gespeicherten, eindeutigkeitsbeschränkten Daten werden nicht migriert.

Beachten Sie, dass der für eine Gruppe protokollierte/gemeldete Pfad nur der erste Pfad ist, der die Migration der Gruppe ausgelöst hat, und dass sich diese Gruppe auch in anderen Inhaltspfaden befinden könnte.

Die meisten migrierten Gruppen sind so konfiguriert, dass sie von IMS verwaltet werden.  Das bedeutet, dass eine Gruppe in IMS mit demselben Namen mit der Gruppe in AEM verknüpft wird und alle IMS-Benutzenden in der IMS-Gruppe AEM Benutzende und Mitglieder der Gruppe in AEM werden.  Dadurch können diese Benutzenden entsprechend den Richtlinien der ACLs oder CUGs für die Gruppe Zugriff auf den Inhalt haben.

Beachten Sie, dass migrierte Gruppen nicht mehr als „lokale Gruppen“ angesehen werden. Sie sind IMS-Gruppen und müssen in IMS neu erstellt werden, damit sie zwischen AEM und IMS synchronisiert werden können.  Gruppen können in IMS unter anderem über die Admin Console einzeln oder massenhaft erstellt werden.  Weitere Informationen zum Erstellen von Gruppen (einzeln oder in großer Anzahl) in der Admin Console finden Sie unter [Verwalten von Benutzergruppen](https://helpx.adobe.com/de/enterprise/using/user-groups.html).

Die Ausnahme für diese IMS-Konfiguration sind Gruppen, die von Assets-Sammlungen erstellt wurden. Wenn eine Sammlung in AEM erstellt wird, werden Gruppen für den Zugriff auf diese Sammlung erstellt. Diese Gruppen werden in das Cloud-System migriert, sind jedoch nicht für die Verwaltung durch IMS konfiguriert.  Um diesen Gruppen IMS-Benutzende hinzuzufügen, müssen sie auf der Seite „Gruppeneigenschaften“ in der Assets-Benutzeroberfläche entweder einzeln oder gemeinsam als Teil einer anderen IMS-Gruppe hinzugefügt werden.


## Deaktivieren der Gruppenmigration {#group-migration-option}

Die CTT-Version 3.0.20 und höher enthält eine Option zur Deaktivierung der Migration von Gruppen.  Dies wird in der OSGi-Konsole wie folgt konfiguriert:

* Öffnen Sie die OSGi-Konfiguration `(http://<server>/system/console/configMgr)`
* Klicken Sie auf die Konfiguration namens **Konfiguration des Extraktionsdienstes für das Content Transfer Tool**
* Deaktivieren Sie die Option **Gruppen in die Migration einbeziehen**, um Gruppenmigrationen zu deaktivieren
* Klicken Sie auf **Speichern**, um sicherzustellen, dass die Konfiguration auf dem Server gespeichert wird und aktiv ist

Wenn diese Einstellung deaktiviert ist, werden keine Gruppen migriert und es gibt weder einen Bericht zur Prinzipalmigration noch einen Benutzerbericht.

## Benutzerbericht {#user-report}

Während der Migration werden Benutzende zwar nicht migriert, aber die Benutzergruppenbeziehungen im Quellsystem gehen verloren, es sei denn, sie werden auf irgendeine Weise erfasst.  Der Benutzerbericht erfasst einige dieser Informationen im Textformat in einem Benutzerbericht. Jede Benutzerin und jeder Benutzer wird gemeldet (eine Person pro Zeile) sowie eine Liste der Gruppen, denen die Person angehört (nicht migrierte Gruppen werden jedoch nicht in diese Liste aufgenommen), es sei denn, die Liste der Gruppen ist leer. In diesem Fall wird die Person nicht angezeigt. Die mit jeder Benutzerin bzw. jedem Benutzer gemeldeten Gruppen sind diejenigen, denen die Person direkt oder indirekt im Quellsystem angehört. Da es sein kann, dass Gruppen im Quellsystem verschachtelt sind, aber im Zielsystem nicht, unterstützt diese Gruppenliste die neue reduzierte Gruppenstruktur in IMS.

Bei einer löschenden und einer anschließenden nicht löschenden Aufnahme enthalten die Gruppen in der Liste einer Benutzerin oder eines Benutzers die Gruppen, die in beiden Phasen migriert wurden.

Neben den Gruppen für jede Benutzerin und jeden Benutzer gibt es ein Feld im Bericht, in dem für die Person Notizen hinzugefügt werden können (eine detaillierte Beschreibung der Bedeutung der Notiz ist ebenfalls im Bericht enthalten).  Mögliche Notizen sind:

* Benutzende, auf die direkt in einer ACL verwiesen wird, haben in ihrem Hinweisabschnitt den Eintrag *Hinweis-A*, da dies kein empfohlener Anwendungsfall und keine empfohlene Best Practice ist.
* Benutzende, die direkte Mitglieder einer integrierten Gruppe sind, haben in ihrem Hinweisabschnitt den Eintrag *Hinweis-B*, da dies ebenfalls kein empfohlener Anwendungsfall und keine empfohlene Best Practice ist.

Diese Fälle können gleichzeitig auftreten, aber auch zur selben Zeit wie die früheren Fälle.

Der Benutzerbericht wird am Ende des Berichts zur Prinzipalmigration hinzugefügt und ist daher Teil dieses Berichts (siehe [Endgültige Zusammenfassung und Bericht](#final-summary-and-report) unten).  Mit den Informationen in diesem Bericht, einschließlich der für jede Benutzerin und jeden Benutzer gemeldeten Gruppen, kann eine Massen-Benutzer-Upload-Datei erstellt werden, die in der Admin Console verwendet werden kann, um in IMS eine große Anzahl von Benutzenden zu erstellen.  Vorhandene IMS-Benutzende können auch massenhaft bearbeitet werden.

Weitere Informationen zur Massenerstellung oder -bearbeitung von Benutzenden über die Admin Console finden Sie unter [Verwalten mehrerer Benutzender | CSV-Massen-Upload](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html).

## Zusätzliche Überlegungen {#additional-considerations}

* Wenn die Einstellung **Vorhandene Inhalte in der Cloud-Instanz vor der Aufnahme löschen** festgelegt ist, werden bereits übertragene Gruppen in der Cloud Service-Instanz gemeinsam mit dem gesamten existierenden Repository gelöscht, und es wird ein neues Repository erstellt, in das Inhalte aufgenommen werden. Dadurch werden auch alle Einstellungen zurückgesetzt, einschließlich der Berechtigungen für die Cloud Service-Zielinstanz. Dies gilt für alle Benutzenden, die zur Gruppe der **Admins** hinzugefügt wurden. Admin-Benutzende müssen der Gruppe **Admins** erneut hinzugefügt werden, um das Zugriffs-Token für die CTT- bzw. CAM-Aufnahme abrufen zu können.
* Wenn bei der Durchführung von nicht löschenden Aufnahmen (die Option **Vorhandene Inhalte löschen** ist nicht eingestellt) Inhalte nicht übertragen werden, weil sie sich seit der letzten Übertragung nicht geändert haben, werden auch die mit diesen Inhalten verbundenen Gruppen nicht übertragen. Diese Regel gilt auch dann, wenn sich die Gruppen auf dem Quellsystem zwischenzeitlich geändert haben. Dies liegt daran, dass Gruppen zusammen mit den Inhalten migriert werden, mit denen sie verknüpft sind. Aus diesem Grund werden in diesem Fall keine Gruppen migriert, die Mitglieder einer Gruppe im Quellsystem sind, es sei denn, sie sind Teil einer anderen Gruppe, die migriert wird, oder befinden sich in der ACL anderer Inhalte, die migriert werden. Um diese Gruppen anschließend zu migrieren, sollten Sie Pakete verwenden, Gruppen aus der Zielgruppe löschen und den relevanten Inhalt erneut migrieren oder erneute Migrationen mit einer löschenden Aufnahme durchführen.
* Wenn während einer nicht löschenden Aufnahme eine Gruppe mit denselben eindeutigkeitsbeschränkten Daten (rep:principalName, rep:authorizableId, jcr:uuid oder rep:externalId) sowohl in der AEM-Quellinstanz als auch in der AEM Cloud Service-Zielinstanz vorhanden ist, wird die betreffende Gruppe _nicht_ migriert und die zuvor vorhandene Gruppe im Cloud-System bleibt unverändert. Dies wird im Bericht zur Prinzipalmigration protokolliert.
* Siehe [Migrieren von geschlossenen Benutzergruppen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) für zusätzliche Überlegungen zu Gruppen, die in einer Richtlinie für geschlossene Benutzergruppen (CUG) verwendet werden.

## Endgültige Zusammenfassung und Bericht

Nach erfolgreicher Extraktion und Aufnahme wird ein Bericht mit den Details zur Migration der Gruppe generiert. Weitere Informationen finden Sie unter [Validieren der Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-group-migration).
