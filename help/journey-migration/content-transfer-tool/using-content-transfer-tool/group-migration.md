---
title: Gruppenmigration
description: Überblick über die Gruppenmigration in AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 50c8dd725e20cbd372a7d7858fc67b0f53a8d6d4
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 97%

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

* Wenn sich eine Gruppe in einer ACL- oder CUG-Richtlinie mit migrierten Inhalten befindet, wird diese Gruppe migriert. Dabei gelten die unten aufgeführten Ausnahmen.
* Es gibt eine Reihe von Gruppen, die integriert und bereits im Cloud-Zielsystem vorhanden sind. Diese werden nie migriert.
   * Einige integrierte Gruppen können Mitgliedergruppen enthalten, die _nicht_ integriert sind. Solche Mitgliedergruppen (direkte Mitglieder oder Mitglieder von Mitgliedern usw.), auf die in einer ACL- oder CUG-Richtlinie für migrierte Inhalte verwiesen wird, werden migriert, um sicherzustellen, dass Benutzende, die Mitglieder dieser Gruppen sind (entweder direkt oder indirekt), ihren Zugriff auf die migrierten Inhalte beibehalten.
* Andere Gruppen, z. B. Gruppen, die sich nicht in einer ACL- oder CUG-Richtlinie befinden, Gruppen, die bereits im Zielsystem vorhanden sind, und Gruppen mit bereits im Zielsystem gespeicherten, eindeutigkeitsbeschränkten Daten werden nicht migriert.

Beachten Sie, dass der für eine Gruppe protokollierte/gemeldete Pfad nur der erste Pfad ist, der die Migration der Gruppe ausgelöst hat, und dass sich diese Gruppe auch in anderen Inhaltspfaden befinden könnte.

Die meisten migrierten Gruppen sind so konfiguriert, dass sie von IMS verwaltet werden.  Das bedeutet, dass eine Gruppe in IMS mit demselben Namen mit der Gruppe in AEM verknüpft wird und alle IMS-Benutzenden in der IMS-Gruppe AEM Benutzende und Mitglieder der Gruppe in AEM werden.  Dadurch können diese Benutzenden entsprechend den Richtlinien der ACLs oder CUGs für die Gruppe Zugriff auf den Inhalt haben.

Beachten Sie, dass migrierte Gruppen nicht mehr als „lokale Gruppen“ von AEM angesehen werden. Sie sind IMS-kompatible Gruppen in AEM, obwohl sie möglicherweise noch nicht in IMS existieren.   Sie müssen in IMS separat neu erstellt werden, damit sie zwischen AEM und IMS synchronisiert werden können.  Gruppen können in IMS unter anderem über die Admin Console einzeln oder massenhaft erstellt werden.  Weitere Informationen zum Erstellen von Gruppen (einzeln oder in großer Anzahl) in der Admin Console finden Sie unter [Verwalten von Benutzergruppen](https://helpx.adobe.com/de/enterprise/using/user-groups.html).

Die Ausnahme von dieser IMS-Konfiguration betrifft Gruppen, die von Assets-Sammlungen und privaten Ordnern erstellt wurden. Wenn eine Sammlung oder ein privater Ordner in AEM erstellt wird, werden Gruppen für den Zugriff auf diese Inhalte erstellt. Diese Gruppen werden in das Cloud-System migriert, sind jedoch nicht für die Verwaltung durch IMS konfiguriert.  Um diesen Gruppen IMS-Benutzende hinzuzufügen, müssen sie auf der Seite „Gruppeneigenschaften“ in der Assets-Benutzeroberfläche entweder einzeln oder gemeinsam als Teil einer anderen IMS-Gruppe hinzugefügt werden.


## Deaktivieren der Gruppenmigration {#group-migration-option}

Die CTT-Version 3.0.20 und höher enthält eine Option zur Deaktivierung der Migration von Gruppen.  Dies wird in der OSGi-Konsole wie folgt konfiguriert:

* Öffnen Sie die OSGi-Konfiguration `(http://<server>/system/console/configMgr)`
* Klicken Sie auf die Konfiguration namens **Konfiguration des Extraktionsdienstes für das Content Transfer Tool**
* Deaktivieren Sie die Option **Gruppen in die Migration einbeziehen**, um Gruppenmigrationen zu deaktivieren
* Klicken Sie auf **Speichern**, um sicherzustellen, dass die Konfiguration auf dem Server gespeichert wird und aktiv ist

Wenn diese Einstellung deaktiviert ist, werden keine Gruppen migriert und es gibt weder einen Bericht zur Prinzipalmigration noch einen Benutzerbericht (siehe unten).

## Bericht zur Prinzipalmigration und Benutzerbericht {#principal-migration-report}

Wenn bei der Migration Gruppen eingeschlossen werden (Standard), wird ein Bericht zur Prinzipalmigration gespeichert, in dem beschrieben wird, was während der Migration mit den einzelnen Gruppen passiert.  So laden Sie diesen Bericht nach erfolgreicher Aufnahme herunter:
* Navigieren Sie in CAM zu „Content-Übertragung“ und wählen Sie „Aufnahmevorgänge“ aus.
* Klicken Sie auf die Auslassungspunkte (…) in der Zeile der betreffenden Aufnahme und wählen Sie „Prinzipalzusammenfassung anzeigen“ aus.
* Wählen Sie im angezeigten Dialogfeld in der Dropdown-Liste unter „Datei herunterladen…“ die Option „Bericht zur Prinzipalmigration“ und klicken Sie auf die Schaltfläche „Herunterladen“.
* Speichern Sie die resultierende CSV-Datei.

Einige der aufgezeichneten Informationen pro Gruppe sind:
* Bei einer Migration der Pfad zur ersten ACL oder CUG, die zur Migration der Gruppe geführt hat.
* Ob die Gruppe zuvor migriert wurde. Wenn die aktuelle Aufnahme eine nicht löschende Aufnahme war, wurden einige Gruppen möglicherweise während einer vorherigen Aufnahme migriert.
* Ob die Gruppe eine integrierte Gruppe ist. Diese Gruppen werden nicht migriert, da sie sich immer in der AEMaaCS-Zielumgebung befinden.
* Wenn die Gruppe nicht Teil einer ACL oder CUG für den migrierten Inhalt war, wurde sie nicht migriert.
* Wenn es sich bei der Gruppe um eine lokale Gruppe handelt, z. B. eine Gruppe, die durch eine Assets-Sammlung erstellt wurde, wurde sie möglicherweise migriert. In diesem Fall wird dem Bericht für diese Gruppe das Wort „lokal“ hinzugefügt.

Während der Migration werden Benutzende zwar nicht migriert, aber die Benutzergruppenbeziehungen im Quellsystem würden verloren gehen, es sei denn, sie wurden auf irgendeine Weise erfasst. Der Aufnahmeprozess erfasst einige dieser Informationen im Textformat in einem Benutzerbericht, der am Ende des Berichts zur Prinzipalmigration angezeigt wird.

### Benutzerbericht {#user-report}

Im Abschnitt „Benutzerbericht“ werden Benutzende (eine Person pro Zeile) zusammen mit ihrer E-Mail-Adresse und einer Liste der IMS-aktivierten Gruppen gemeldet, die während dieser Aufnahme migriert wurden.  Gruppen, die nicht migriert wurden, bei einer früheren Aufnahme migriert wurden oder lokale Gruppen sind, sind nicht in der Liste enthalten.   Wenn eine Benutzerin bzw. ein Benutzer keiner migrierten IMS-aktivierten Gruppe angehört und es keine zusätzlichen Anmerkungen gibt, dass es sich um einen Sonderfall handelt (siehe **Anmerkungen** unten), ist diese Person _nicht_ Teil des Berichts. Die mit jeder Benutzerin und jedem Benutzer gemeldeten Gruppen sind diejenigen, denen die Person direkt oder indirekt im Quellsystem angehört. Da es sein kann, dass Gruppen im Quellsystem verschachtelt sind, aber im Zielsystem nicht, unterstützt diese Gruppenliste die neue reduzierte Gruppenstruktur in IMS.

Bei einer löschenden und einer anschließenden nicht löschenden Aufnahme sind die Gruppen in der Liste einer Benutzerin bzw. eines Benutzers von der nicht löschenden Aufnahme diejenigen Gruppen, die in der Phase der nicht löschenden Aufnahme migriert wurden.

#### Anmerkungen {#user-report-notes}

Neben den Gruppen für jede Benutzerin und jeden Benutzer gibt es ein Feld im Benutzerbericht, in dem Anmerkungen über die Person für Informationszwecke hinzugefügt werden können (eine detaillierte Beschreibung der Bedeutung der Anmerkung ist ebenfalls im Bericht enthalten).  Mögliche Anmerkungen sind:

* **Anmerkung-A**: Benutzende, auf die direkt in einer ACL verwiesen wird, haben in ihrem Anmerkungsabschnitt den Eintrag *Anmerkung-A*, da dies kein empfohlener Anwendungsfall und keine empfohlene Best Practice ist.
* **Anmerkung-B**: Benutzende, die direkte Mitglieder einer integrierten Gruppe sind, haben in ihrem Anmerkungsabschnitt den Eintrag *Anmerkung-B*, da dies ebenfalls kein empfohlener Anwendungsfall und keine empfohlene Best Practice ist.
* **Anmerkung-C**: Benutzende, die direkte oder indirekte Mitglieder einer migrierten lokalen Gruppe sind (z. B. einer Gruppe, die durch eine Assets-Sammlung erstellt wurde), haben in ihrem Anmerkungsabschnitt den Eintrag *Anmerkung-C*, da lokale Gruppen nicht für die Verwaltung durch IMS konfiguriert sind.

Diese Fälle können gleichzeitig auftreten, aber auch zur selben Zeit wie die früheren Fälle.  _Weitere Informationen dazu, auf welche Gruppen sich die einzelnen Anmerkungen für die einzelnen Benutzenden beziehen, finden Sie im Aufnahmeprotokoll. Es enthält diese Informationen für jede einzelne Person._

Der Benutzerbericht wird am Ende des Berichts zur Prinzipalmigration hinzugefügt und ist daher Teil dieses Berichts (siehe [Endgültige Zusammenfassung und Bericht](#final-summary-and-report) unten), um Kundinnen und Kunden ein vollständigeres Verständnis der Gruppen und Benutzenden sowie ihrer Beziehungen zu vermitteln.

## Dateien für den Massen-Upload {#bulk-upload-files}

Da Gruppen nur zu AEM as a Cloud Service migriert werden, müssen sie auch zu IMS hinzugefügt werden, damit sie in der Cloud ordnungsgemäß mit AEM funktionieren. Darüber hinaus werden Benutzende nicht migriert, sodass sie auch zu IMS hinzugefügt werden müssen. Das CTT/CAM-Migrations-Tool führt diesen Schritt zwar nicht aus, aber der Aufnahmeprozess erstellt zwei Dateien für den Massen-Upload, eine für Gruppen und eine für Benutzende. Diese Dateien können bearbeitet und dann zusammen mit der Massen-Upload-Funktion der Admin Console verwendet werden, um IMS-Gruppen und -Benutzende basierend auf Ihren AEM-Gruppen und -Benutzenden zu erstellen.

Weitere Informationen zur Verwendung von Massen-Upload-Dateien zum Erstellen von Benutzenden und Gruppen mit der Admin Console finden Sie unter [Massen-Upload von Gruppen und Benutzenden in IMS](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/bulk-principal-uploading.md).

Weitere Informationen zur Verwaltung von AEM as a Cloud Service-Benutzenden finden Sie zudem unter [Verwalten von Benutzenden](https://helpx.adobe.com/de/enterprise/using/users.html).

## Zusätzliche Überlegungen {#additional-considerations}

* Wenn die Einstellung **Vorhandene Inhalte in der Cloud-Instanz vor der Aufnahme löschen** festgelegt ist, werden bereits übertragene Gruppen in der Cloud Service-Instanz gemeinsam mit dem gesamten existierenden Repository gelöscht, und es wird ein neues Repository erstellt, in das Inhalte aufgenommen werden. Dadurch werden auch alle Einstellungen zurückgesetzt, einschließlich der Berechtigungen für die Cloud Service-Zielinstanz. Dies gilt für alle Benutzenden, die zur Gruppe der **Admins** hinzugefügt wurden. Admin-Benutzende müssen der Gruppe **Admins** erneut hinzugefügt werden, um das Zugriffs-Token für die CTT- bzw. CAM-Aufnahme abrufen zu können.
* Wenn bei der Durchführung von nicht löschenden Aufnahmen (die Option **Vorhandene Inhalte löschen** ist nicht eingestellt) Inhalte nicht übertragen werden, weil sie sich seit der letzten Übertragung nicht geändert haben, werden auch die mit diesen Inhalten verbundenen Gruppen nicht übertragen. Diese Regel gilt auch dann, wenn sich die Gruppen auf dem Quellsystem zwischenzeitlich geändert haben. Dies liegt daran, dass Gruppen zusammen mit den Inhalten migriert werden, mit denen sie verknüpft sind. Aus diesem Grund werden in diesem Fall keine Gruppen migriert, die Mitglieder einer Gruppe im Quellsystem sind, es sei denn, sie sind Teil einer anderen Gruppe, die migriert wird, oder befinden sich in der ACL anderer Inhalte, die migriert werden. Um diese Gruppen anschließend zu migrieren, sollten Sie Pakete verwenden, Gruppen aus der Zielgruppe löschen und den relevanten Inhalt erneut migrieren oder erneute Migrationen mit einer löschenden Aufnahme durchführen.
* Wenn während einer nicht löschenden Aufnahme eine Gruppe mit denselben eindeutigkeitsbeschränkten Daten (rep:principalName, rep:authorizableId, jcr:uuid oder rep:externalId) sowohl in der AEM-Quellinstanz als auch in der AEM Cloud Service-Zielinstanz vorhanden ist, wird die betreffende Gruppe _nicht_ migriert und die zuvor vorhandene Gruppe im Cloud-System bleibt unverändert. Dies wird im Bericht zur Prinzipalmigration protokolliert.
* Siehe [Migrieren von geschlossenen Benutzergruppen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) für zusätzliche Überlegungen zu Gruppen, die in einer Richtlinie für geschlossene Benutzergruppen (CUG) verwendet werden.

## Endgültige Zusammenfassung und Bericht

Nach erfolgreicher Extraktion und Aufnahme wird ein Bericht mit den Details zur Migration der Gruppe generiert. Weitere Informationen finden Sie unter [Validieren der Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-group-migration).
