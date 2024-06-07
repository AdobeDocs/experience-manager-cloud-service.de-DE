---
title: Benutzerzuordnung und Prinzipalmigration
description: Überblick über Benutzerzuordnung und Prinzipalmigration in AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: ht
source-wordcount: '1060'
ht-degree: 100%

---

# Benutzerzuordnung und Prinzipalmigration {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Benutzermigration"
>abstract="Mit dem Content Transfer Tool können Benutzende und Gruppen von einem bestehenden AEM-System zu AEM as a Cloud Service verschoben werden. Vorhandene Benutzende müssen zugeordnet sein, damit sie sich über ihre IMS-IDs anmelden können."

>[!NOTE]
>Frühere Versionen des Tools für die Benutzerzuordnung finden Sie in der [Legacy-Dokumentation](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Einführung {#introduction}

Im Rahmen der Umstellung auf Adobe Experience Manager (AEM) as a Cloud Service müssen Benutzende und Gruppen (oder „Prinzipale“) von bestehenden AEM-Systemen zu AEM as a Cloud Service migriert werden. Diese Aufgabe wird vom Content Transfer Tool durchgeführt.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Authoring-Ebene. Dieser Prozess setzt voraus, dass die [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzenden und Benutzergruppen verwendet wird. Die Benutzerprofilinformationen sind im Identity Management System (IMS) von Adobe zentralisiert, das Single Sign-on über alle Adobe-Cloud-Anwendungen hinweg bereitstellt. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=de#identity-management). Aufgrund dieser Änderung müssen vorhandene Benutzende ihren IMS-IDs zugeordnet werden, damit sie über ihre IMS-Profile auf AEMaaCS zugreifen können. Da sich Gruppen im traditionellen AEM grundlegend von Gruppen in IMS unterscheiden, werden Gruppen nicht zugeordnet, aber die beiden Gruppensätze müssen nach Abschluss der Migration aufeinander abgestimmt werden.

## Details zur Prinzipalmigration {#principal-migration-detail}

Das Content Transfer Tool und der Cloud Acceleration Manager migrieren alle Prinzipale, die mit dem migrierten Inhalt verknüpft sind, zum Cloud-System. Das Content Transfer Tool kopiert dazu während des Extraktionsvorgangs alle Prinzipale aus dem AEM-Quellsystem. CAM Ingestion wählt dann nur die Prinzipale aus, die mit dem aufgenommenen Inhalt verbunden sind, und migriert sie. Wenn ein Prinzipal eine ACL- oder CUG-Richtlinie mit migrierten Inhalten verwendet, werden dieser Prinzipal und alle Gruppen, in denen er sich befindet, sowie ihre übergeordneten Gruppen migriert. Wenn ein Prinzipal eines Inhalts eine Gruppe ist, werden auch alle untergeordneten Gruppen und Benutzenden migriert.

## Details zur Benutzerzuordnung {#user-mapping-detail}

AEM-Benutzende können entsprechenden Adobe IMS-Benutzenden mit derselben E-Mail-Adresse zugeordnet werden. Diese Zuordnung erfolgt automatisch in CTT (während des Extraktionsschritts). Ob sie durchgeführt wird oder nicht, kann vor dem Extraktionsstart durch einen Umschalter gesteuert werden. Die Standardeinstellung des Umschalters kann von Benutzenden beim Starten der Extraktion überschrieben werden.

* Wenn es sich bei dem Quellsystem um eine Authoring-Instanz handelt, ist die Zuordnungsoption standardmäßig _eingeschaltet_, da dies der empfohlene Prozess ist.
* Wenn das Quellsystem eine Veröffentlichungsinstanz ist, dann ist die Wahl, die Zuordnung vorzunehmen, standardmäßig auf _aus_ festgelegt, da Benutzende normalerweise nicht migriert oder in Veröffentlichungsinstanzen verwendet werden. Falls sie doch verwendet werden, wird normalerweise ein anderes Authentifizierungssystem (d. h. nicht IMS) für sie verwendet.

Unabhängig davon, ob Benutzende während der Extraktion zugeordnet werden oder nicht, werden sie bei der Aufnahme in das Cloud-System zusammen mit den Gruppen migriert, wenn sie mit Inhalten verknüpft sind, die migriert werden.

## Wichtige Aspekte bei der Zuordnung und Migration von Benutzenden {#important-considerations}

### Ausnahmefälle {#exceptional-cases}

Die folgenden spezifischen Fälle sind protokolliert:

1. Wenn Benutzende keine E-Mail-Adresse im Feld `profile/email` ihres *jcr*-Knotens haben, werden die betreffenden Benutzenden bzw. Gruppen migriert, jedoch nicht zugeordnet. Dies ist selbst dann der Fall, wenn die E-Mail-Adresse als Benutzername für die Anmeldung verwendet wird.
2. Wenn die Person deaktiviert ist, wird sie wie andere Benutzende behandelt: Sie wird normal zugeordnet und migriert und bleibt in der Cloud-Instanz deaktiviert.
3. Wenn ein Prinzipal mit denselben eindeutigkeitsbeschränkten Daten (rep:principalName, jcr:uuid oder rep:externalId) sowohl in der AEM-Quellinstanz als auch in der AEM Cloud Service-Zielinstanz vorhanden ist, wird der betreffende Prinzipal nicht migriert und der zuvor vorhandene Prinzipal im Cloud-System bleibt unverändert. Dies wird im Bericht zur Prinzipalmigration protokolliert.
4. Wenn jemand IMS nicht über die Benutzerzuordnung zugeordnet wird, wird das Benutzerprofil im Cloud-AEM-System von IMS nicht erkannt. In diesem Fall wird bei der Anmeldung über IMS ein neues (dupliziertes) Profil auf AEM erstellt, es enthält jedoch keine der vorherigen Profilinformationen. Das ursprüngliche Benutzerprofil existiert im Cloud-AEM-System, die Person kann sich jedoch nicht über IMS anmelden, sondern nur über die herkömmliche AEM-Methode (lokale Anmeldung). Daher wird die Zuordnung aller Benutzenden für alle Autorenmigrationen dringend empfohlen.

## Zusätzliche Überlegungen {#additional-considerations}

* Wenn die Einstellung **Vorhandene Inhalte in der Cloud-Instanz vor der Aufnahme löschen** festgelegt ist, werden bereits übertragene Prinzipale in der Cloud Service-Instanz gemeinsam mit dem gesamten existierenden Repository gelöscht, und es wird ein neues Repository erstellt, in das Inhalte aufgenommen werden. Dadurch werden auch alle Einstellungen zurückgesetzt, einschließlich der Berechtigungen für die Cloud Service-Zielinstanz. Dies gilt für Admin-Benutzende, die der Gruppe der **Admins** hinzugefügt wurden. Admin-Benutzende müssen der Gruppe **Admins** erneut hinzugefügt werden, um das Zugriffstoken für die CTT- bzw. CAM-Aufnahme abrufen zu können.
* Wenn bei der Durchführung von nicht löschenden Aufnahmen (**Vorhandene Inhalte löschen** ist nicht eingestellt) Inhalte nicht übertragen werden, weil sie sich seit der letzten Übertragung nicht geändert haben, werden auch die mit diesen Inhalten verbundenen Benutzenden und Gruppen nicht übertragen. Diese Regel gilt auch dann, wenn sich die Benutzenden und Gruppen auf dem Quellsystem zwischenzeitlich geändert haben. Dies liegt daran, dass Benutzende und Gruppen zusammen mit den Inhalten migriert werden, mit denen sie verknüpft sind. Aus diesem Grund werden keine neue Prinzipale einer Gruppe im Quellsystem migriert, es sei denn, sie sind Teil einer anderen Gruppe, die migriert wird, oder befinden sich in der ACL anderer Inhalte, die migriert werden. Um diese Prinzipale anschließend zu migrieren, sollten Sie Pakete verwenden oder Prinzipale aus der Zielgruppe löschen und den relevanten Inhalt erneut migrieren („Extrahieren mit Überschreiben“ und „Mit Bereinigen aufnehmen“).
* Doppelte E-Mail-Adressen sind in IMS nicht zulässig, jedoch in AEM (sowohl lokal als auch in der Cloud). Benutzende können sich über IMS über ihre E-Mail-Adresse bei AEM anmelden und werden in dem von IMS referenzierten Benutzerprofil angemeldet.
* Siehe [Migrieren geschlossener Benutzergruppen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) für zusätzliche Überlegungen zu Prinzipalen, die in einer CUG-Richtlinie (Closed User Group, geschlossene Benutzergruppe) verwendet werden.

## Endgültige Zusammenfassung und Bericht {#final-report}

Nach erfolgreicher Extraktion und Aufnahme wird ein Bericht mit den Details zur Prinzipalmigration generiert. Weitere Informationen finden Sie unter [Validieren der Prinzipalmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration).
