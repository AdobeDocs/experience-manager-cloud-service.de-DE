---
title: Gruppenmigration
description: Überblick über die Gruppenmigration in AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 1f9526f8e8aa6a070e95827fab16431b0ee7566b
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 10%

---


# Gruppenmigration {#group-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_groupmigration"
>title="Gruppenmigration"
>abstract="Mit dem Content Transfer Tool können Sie Gruppen aus Ihrem bestehenden Adobe Experience Manager (AEM)-System in AEM as a Cloud Service kopieren."

>[!NOTE]
>Frühere Versionen des Tools für die Benutzerzuordnung finden Sie in der [Legacy-Dokumentation](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Einführung {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermigration"
>title="Benutzer werden nicht migriert"
>abstract="Das Content Transfer Tool migriert Benutzer nicht mehr. Benutzer sollten in der Admin Console verwaltet werden."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="Dokumentation zur AEM Admin Console"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

Im Rahmen der Umstellung von Journey auf Adobe Experience Manager (AEM) as a Cloud Service müssen Gruppen von bestehenden AEM auf AEM as a Cloud Service migriert werden. Diese Aufgabe wird vom Content Transfer Tool durchgeführt.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Authoring-Ebene. Dieser Prozess setzt voraus, dass die [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzenden und Benutzergruppen verwendet wird. Die Benutzerprofilinformationen sind im Identity Management System (IMS) von Adobe zentralisiert, das Single Sign-on über alle Adobe-Cloud-Anwendungen hinweg bereitstellt. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=de#identity-management). Aufgrund dieser Änderung werden Benutzer automatisch am AEM erstellt, wenn sie sich zum ersten Mal über IMS anmelden.  Daher migriert CTT die Benutzer nicht in das Cloud-System.  IMS-Benutzer müssen in IMS-Gruppen platziert werden. Hierbei kann es sich um migrierte Gruppen oder neue Gruppen handeln, die in die AEM-Gruppen platziert werden, denen Zugriff auf die migrierten AEM gewährt wurde.  Auf diese Weise haben Benutzer im Cloud-System denselben Zugriff wie auf ihr AEM.

## Gruppenmigrationsdetails {#group-migration-detail}

Das Content Transfer Tool und Cloud Acceleration Manager migrieren alle Gruppen, die mit dem zu migrierenden Inhalt in das Cloud-System verbunden sind. Das Content Transfer Tool kopiert dazu während des Extraktionsvorgangs alle Gruppen aus dem AEM. CAM-Aufnahme wählt dann nur bestimmte Gruppen aus und migriert sie:

* Es gibt eine Reihe von Gruppen, die integriert sind und bereits im Zielcloud-System vorhanden sind. Diese werden nie migriert.
* Direkte Mitgliedergruppen aller integrierten Gruppen, die direkt oder indirekt in einer ACL- oder CUG-Richtlinie für migrierte Inhalte genannt werden, werden migriert, um sicherzustellen, dass Benutzer, die direkt oder indirekt Mitglieder dieser Gruppen sind, ihren Zugriff auf die migrierten Inhalte behalten.
* Wenn eine Gruppe eine ACL- oder CUG-Richtlinie mit migrierten Inhalten verwendet, wird diese Gruppe migriert.
* Andere Gruppen, wie z. B. die nicht in einer ACL- oder CUG-Richtlinie gefunden werden, die bereits im Zielsystem vorhanden sind, und solche mit bereits im Zielsystem gespeicherten eindeutigen Begrenzungen werden nicht migriert.

Beachten Sie, dass der für eine Gruppe protokollierte/gemeldete Pfad nur der erste Pfad ist, der die zu migrierende Gruppe ausgelöst hat, und dass sich diese Gruppe auch auf anderen Inhaltspfaden befinden kann.

Die meisten migrierten Gruppen sind so konfiguriert, dass sie von IMS verwaltet werden.  Das bedeutet, dass eine Gruppe in IMS mit demselben Namen mit der Gruppe in AEM verknüpft wird und alle IMS-Benutzer in der IMS-Gruppe AEM Benutzer und Mitglieder der Gruppe in AEM werden.  Dadurch können diese Benutzer entsprechend den ACLs- oder CUGs-Richtlinien für die Gruppe Zugriff auf den Inhalt haben.

Die Ausnahme für diese IMS-Konfiguration sind Gruppen, die von Assets-Sammlungen erstellt werden. Wenn eine Sammlung auf AEM erstellt wird, werden Gruppen für den Zugriff auf diese Sammlung erstellt. Diese Gruppen werden in das Cloud-System migriert, sind jedoch nicht für die Verwaltung durch IMS konfiguriert.  Um diesen Gruppen IMS-Benutzer hinzuzufügen, müssen sie auf der Seite Gruppeneigenschaften in der Assets-Benutzeroberfläche entweder einzeln oder gemeinsam als Teil einer anderen IMS-Gruppe hinzugefügt werden.


## Gruppenmigration deaktivieren {#group-migration-option}

Die CTT-Version 3.0.20 und höher enthält eine Option, um die Migration von Gruppen zu deaktivieren.  Dies wird in der OSGi-Konsole wie folgt konfiguriert:

* Öffnen Sie die OSGi-Konfiguration `(http://<server> /system/console/configMgr)`
* Klicken Sie auf die Konfiguration **Konfiguration des Extraktionsdienstes für das Content Transfer Tool**
* Deaktivieren Sie **Gruppen in die Migration einbeziehen** , um Gruppenmigrationen zu deaktivieren.
* Klicken Sie auf **Speichern** , um sicherzustellen, dass die Konfiguration auf dem Server gespeichert und aktiv ist.

Wenn diese Einstellung deaktiviert ist, werden keine Gruppen migriert und es gibt keinen Bericht zur Hauptmigration oder einen Benutzerbericht.

## Benutzerbericht {#user-report}

Während der Migration werden Benutzer nicht migriert, aber die Benutzergruppenbeziehungen im Quellsystem gehen verloren, es sei denn, sie werden auf irgendeine Weise erfasst.  Der Benutzerbericht erfasst einige dieser Informationen im Textformat in einem Benutzerbericht. Jeder Benutzer wird gemeldet (eine pro Zeile) sowie eine Liste der Gruppen, denen er angehört (aber nicht migrierte Gruppen werden nicht in diese Liste aufgenommen), es sei denn, die Liste der Gruppen ist leer; in diesem Fall wird der Benutzer nicht angezeigt. Die mit jedem Benutzer gemeldeten Gruppen sind diejenigen, denen der Benutzer direkt oder indirekt im Quellsystem angehört. Da Gruppen im Quellsystem verschachtelt sein können, während sie im Zielsystem nicht enthalten sind, unterstützt diese Gruppenliste die neue reduzierte Gruppenstruktur in IMS.

Bei einer Löschung und einer anschließenden Nicht-Löschaufnahme enthalten die Gruppen in der Liste eines Benutzers die Gruppen, die in beiden Phasen migriert wurden.

Neben den Gruppen für jeden Benutzer gibt es ein Feld im Bericht, in dem dem Benutzer Notizen hinzugefügt werden können (und eine detaillierte Beschreibung der Bedeutung der Notiz ist auch im Bericht enthalten).  Mögliche Hinweise sind:

* Benutzer, die direkt in einer ACL referenziert werden, haben im Abschnitt &quot;Hinweise&quot;den Eintrag *Hinweis-A* , da dies kein empfohlener Anwendungsfall oder keine empfohlene Best Practice ist.
* Benutzer, die direkt zu einer integrierten Gruppe gehören, haben im Abschnitt &quot;Hinweise&quot;den Eintrag *Hinweis-B* , da dies auch kein empfohlener Anwendungsfall oder keine empfohlene Best Practice ist.

Diese Fälle können gleichzeitig auftreten, aber auch zur selben Zeit wie die früheren Fälle.

Der Benutzerbericht wird am Ende des Berichts zur Hauptmigration hinzugefügt (und ist daher Teil dieses Berichts) (siehe [Endgültige Zusammenfassung und Bericht](#final-summary-and-report) unten).

## Zusätzliche Überlegungen {#additional-considerations}

* Wenn die Einstellung &quot;**Vorhandenen Inhalt in der Cloud-Instanz vor der Aufnahme löschen**&quot;festgelegt ist, werden zuvor auf die Cloud Service-Instanz übertragene Gruppen zusammen mit dem gesamten vorhandenen Repository gelöscht. Es wird ein neues Repository erstellt, in das Inhalte aufgenommen werden. Durch diesen Vorgang werden auch alle Einstellungen zurückgesetzt, einschließlich Berechtigungen für die Ziel-Cloud Service-Instanz. Er gilt auch für alle Benutzer, die der Gruppe **Administratoren** hinzugefügt wurden. Admin-Benutzende müssen der Gruppe **Admins** erneut hinzugefügt werden, um das Zugriffstoken für die CTT- bzw. CAM-Aufnahme abrufen zu können.
* Wenn keine Löschvorgänge ausgeführt werden (**Vorhandenen Inhalt löschen** ist nicht festgelegt), werden bei nicht übertragenen Inhalten, da sie seit der vorherigen Übertragung nicht geändert wurden, auch die mit diesem Inhalt verknüpften Gruppen nicht übertragen. Diese Regel gilt auch dann, wenn sich die Gruppen im Quellsystem geändert haben. Dies liegt daran, dass Gruppen nur zusammen mit dem Inhalt migriert werden, mit dem sie verknüpft sind. Aus diesem Grund werden in diesem Fall keine Gruppen migriert, die Mitglieder einer Gruppe im Quellsystem sind, es sei denn, sie sind Teil einer anderen Gruppe, die migriert wird, oder in der ACL verschiedener Inhalte, die migriert werden. Um diese Gruppen anschließend zu migrieren, sollten Sie Pakete verwenden, Gruppen aus der Zielgruppe löschen und den relevanten Inhalt neu migrieren oder eine Neumigration mithilfe einer Wischerfassung in Erwägung ziehen.
* Wenn während einer Erfassung ohne Löschung eine Gruppe mit denselben durch Eindeutigkeit beschränkten Daten (rep:principalName, rep:authorizableId, jcr:uuid oder rep:externalId) sowohl für die Quell-AEM-Instanz als auch für die AEM Cloud Service-Zielinstanz vorhanden ist, wird die fragliche Gruppe _nicht_ migriert und die zuvor bestehende Gruppe im Cloud-System bleibt unverändert. Dies wird im Bericht zur Prinzipalmigration protokolliert.
* Siehe [Migrieren von geschlossenen Benutzergruppen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) für zusätzliche Überlegungen zu Gruppen, die in einer Richtlinie für geschlossene Benutzergruppen (CUG) verwendet werden.

## Endgültige Zusammenfassung und Bericht

Nach erfolgreichem Abschluss der Extraktion und Aufnahme wird ein Bericht mit den Details zur Gruppenmigration erstellt. Weitere Informationen finden Sie unter [Überprüfen der Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-group-migration) .
