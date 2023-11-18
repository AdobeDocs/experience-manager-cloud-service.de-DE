---
title: Benutzerzuordnung und Prinzipalmigration
description: Überblick über Benutzerzuordnung und Hauptmigration in AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 45%

---

# Benutzerzuordnung und Prinzipalmigration {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Benutzerzuordnung"
>abstract="Mit dem Content Transfer Tool können Benutzende und Gruppen von einem bestehenden AEM-System zu AEM as a Cloud Service verschoben werden. Vorhandene Benutzende müssen ihren IMS-IDs zugeordnet sein, damit sie nicht in der Authoring-Instanz des Cloud Service dupliziert werden."

>[!NOTE]
>Frühere Versionen des Tools für die Benutzerzuordnung finden Sie in der [Legacy-Dokumentation](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Einführung {#introduction}

Im Rahmen der Umstellung auf Adobe Experience Manager (AEM) as a Cloud Service müssen Benutzer und Gruppen (oder &quot;Prinzipale&quot;) von bestehenden AEM auf AEM as a Cloud Service migriert werden. Diese Aufgabe wird vom Content Transfer Tool durchgeführt.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Authoring-Ebene. Dieser Prozess setzt voraus, dass die [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzenden und Benutzergruppen verwendet wird. Die Benutzerprofilinformationen sind im Adobe Identity Management System (IMS) zentralisiert, das Single Sign-on über alle Adobe-Cloud-Anwendungen hinweg bereitstellt. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=de#identity-management). Aufgrund dieser Änderung müssen bestehende Benutzer ihren IMS-IDs zugeordnet werden, um zu verhindern, dass in der Autoreninstanz des Cloud Service doppelte Benutzer erstellt werden. Da sich Gruppen im traditionellen AEM grundlegend von Gruppen in IMS unterscheiden, werden Gruppen nicht zugeordnet, aber die beiden Gruppen müssen nach Abschluss der Migration aufeinander abgestimmt werden.

## Details zur Hauptmigration {#principal-migration-detail}

Das Content Transfer Tool und Cloud Acceleration Manager migrieren alle Prinzipale, die mit dem migrierten Inhalt verknüpft sind, in das Cloud-System.  Das Content Transfer Tool kopiert dazu während des Extraktionsvorgangs alle Prinzipale aus dem AEM.  CAM Ingestion wählt dann nur die Prinzipale aus, die mit dem aufgenommenen Inhalt verbunden sind, und migriert sie. Wenn ein Prinzipal eine ACL- oder CUG-Richtlinie mit migrierten Inhalten verwendet, werden dieser Prinzipal und alle Gruppen, in denen er sich befindet, sowie ihre übergeordneten (übergeordneten) Gruppen migriert. Wenn ein Prinzipal im Inhalt eine Gruppe ist, werden auch alle untergeordneten Gruppen und Benutzer migriert.

## Details zur Benutzerzuordnung {#user-mapping-detail}

AEM-Benutzende können entsprechenden Adobe IMS-Benutzenden mit derselben E-Mail-Adresse zugeordnet werden.  Diese Zuordnung kann automatisch in der CTT erfolgen (während des Extraktionsschritts) und ob sie abgeschlossen ist oder nicht, kann durch einen Umschalter gesteuert werden, bevor die Extraktion gestartet wird. Die Standardeinstellung des Umschalters kann von Benutzenden beim Starten der Extraktion überschrieben werden.

* Wenn es sich bei dem Quellsystem um eine Authoring-Instanz handelt, ist die Zuordnungsoption standardmäßig _eingeschaltet_, da dies der empfohlene Prozess ist.
* Wenn das Quellsystem eine Veröffentlichungsinstanz ist, können Sie die Zuordnung standardmäßig vornehmen. _off_, da Benutzer normalerweise nicht migriert oder in Veröffentlichungsinstanzen verwendet werden; oder wenn sie verwendet werden, wird normalerweise ein anderes Authentifizierungssystem (d. h. nicht IMS) für sie verwendet.

Unabhängig davon, ob Benutzer während der Extraktion zugeordnet werden, werden sie zusammen mit den Gruppen bei der Erfassung in das Cloud-System migriert, wenn sie mit Inhalten verknüpft sind, die migriert werden.

## Wichtige Aspekte bei der Zuordnung und Migration von Benutzenden {#important-considerations}

### Ausnahmefälle {#exceptional-cases}

Die folgenden spezifischen Fälle sind protokolliert:

1. Wenn Benutzende keine E-Mail-Adresse im `profile/email`-Feld ihres *jcr*-Knotens haben, werden die betreffenden Benutzenden bzw. Gruppen migriert, jedoch nicht zugeordnet. Dies ist auch dann der Fall, wenn die E-Mail-Adresse als Benutzername für die Anmeldung verwendet wird.
2. Wenn der Benutzer deaktiviert ist, wird er wie andere Benutzer behandelt. Er wird normal zugeordnet und migriert und bleibt in der Cloud-Instanz deaktiviert.
3. Wenn ein Prinzipal mit demselben Namen (rep:principalName) sowohl in der Quell-AEM-Instanz als auch in der AEM Cloud Service-Zielinstanz vorhanden ist, wird der betreffende Prinzipal nicht migriert und der zuvor vorhandene Prinzipal im Cloud-System bleibt unverändert.
4. Wenn ein Benutzer migriert wird, ohne über die Benutzerzuordnung zugeordnet zu werden, kann sich der Benutzer auf dem Ziel-Cloud-System nicht mit seiner IMS-ID anmelden. Oder wenn die E-Mail-Adresse nicht mit der für die Anmeldung bei IMS verwendeten E-Mail-Adresse übereinstimmt, kann sich das Cloud-Zielsystem nicht mit seiner IMS-ID anmelden. Sie können sich möglicherweise mit der herkömmlichen AEM-Methode (lokale Anmeldung) anmelden, aber diese Methode ist normalerweise nicht das, was gewünscht oder erwartet wird.

## Zusätzliche Überlegungen {#additional-considerations}

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** festgelegt ist, werden bereits übertragene Benutzer in der Cloud Service-Instanz zusammen mit dem gesamten vorhandenen Repository gelöscht. Es wird ein neues Repository erstellt, in das Inhalte aufgenommen werden. Dadurch werden auch alle Einstellungen zurückgesetzt, einschließlich der Berechtigungen für die Cloud Service-Zielinstanz. Dies gilt für Admin-Benutzende, die der Gruppe der **Admins** hinzugefügt wurden. Der Admin-Benutzer muss der **Administratoren** -Gruppe, um das Zugriffstoken für die CTT/CAM-Aufnahme abzurufen.
* Wenn bei der Durchführung von Inhaltsauffüllungen Inhalte nicht übertragen werden, weil sie sich seit der letzten Übertragung nicht geändert haben, werden auch die mit diesen Inhalten verbundenen Benutzenden und Gruppen nicht übertragen. Diese Regel gilt auch dann, wenn sich die Benutzer und Gruppen im Quellsystem geändert haben. Der Grund dafür ist, dass Benutzer und Gruppen nur zusammen mit dem Inhalt migriert werden, mit dem sie verknüpft sind.
* Wenn die AEM Cloud Service-Zielinstanz über eine Benutzerin oder einen Benutzer mit einem anderen Benutzernamen, aber derselben E-Mail-Adresse wie eine oder einer der Benutzenden in der AEM-Quellinstanz verfügt und die Benutzerzuordnung aktiviert ist, wird in den Protokollen eine Fehlermeldung aufgezeichnet. Außerdem wird die AEM-Quellbenutzerin oder der AEM-Quellbenutzer nicht übertragen, da nur eine Benutzerin oder ein Benutzer mit einer bestimmten E-Mail-Adresse auf dem Zielsystem zulässig ist.
* Siehe [Migrieren geschlossener Benutzergruppen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) für zusätzliche Überlegungen zu Prinzipalen, die in einer CUG-Richtlinie (Closed User Group, geschlossene Benutzergruppe) verwendet werden.

## Endgültige Zusammenfassung und Bericht {#final-report}

Nach erfolgreicher Extraktion und Aufnahme wird ein Bericht mit den Details zur Prinzipalmigration generiert. Weitere Informationen finden Sie unter [Validieren der Prinzipalmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration).
