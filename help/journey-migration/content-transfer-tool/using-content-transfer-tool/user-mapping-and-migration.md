---
title: Benutzerzuordnung und Hauptmigration
description: Übersicht über Benutzerzuordnung und Hauptmigration
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 32%

---

# Benutzerzuordnung und Hauptmigration {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Benutzerzuordnung"
>abstract="Mit dem Content Transfer Tool können Sie Anwender und Gruppen aus Ihrem vorhandenen AEM-System in AEM as a Cloud Service verschieben. Vorhandene Benutzende müssen ihren IMS-IDs zugeordnet sein, damit sie nicht in der Autoreninstanz des Cloud Service dupliziert werden."

>[!NOTE]
>Frühere Versionen des Tools für die Benutzerzuordnung finden Sie in der [Legacy-Dokumentation](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Einführung {#introduction}

Im Rahmen der Umstellung auf Adobe Experience Manager (AEM) as a Cloud Service müssen Sie Benutzer und Gruppen aus Ihrem bestehenden AEM-System in AEM as a Cloud Service überführen. Verwenden Sie hierzu das Content Transfer Tool.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Autorenebene. Dies erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzern und Benutzergruppen. Die Benutzerprofilinformationen werden im Adobe Identity Management System (IMS) zentralisiert, das eine einmalige Anmeldung für alle Adobe Cloud-Programme ermöglicht. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html#identity-management). Aufgrund dieser Änderung müssen bestehende Benutzer ihren IMS-IDs zugeordnet werden, um zu verhindern, dass Benutzer in der Autoreninstanz des Cloud Service doppelt verwendet werden. Da sich Gruppen in traditionellen AEM grundlegend von Gruppen in IMS unterscheiden, werden Gruppen nicht zugeordnet, aber die beiden Gruppen müssen nach Abschluss der Migration abgestimmt werden.

## Benutzerzuordnung und Migrationsdetails {#user-mapping-detail}

Das Content Transfer Tool und Cloud Acceleration Manager migrieren alle Benutzer, die mit dem migrierten Inhalt verknüpft sind. Diese Zuordnung erfolgt automatisch und ob sie durchgeführt wird, kann durch einen Umschalter gesteuert werden, bevor die Extraktion gestartet wird. Die Standardeinstellung des Umschalters kann vom Benutzer beim Starten der Extraktion überschrieben werden.

* Wenn das Quellsystem eine Autoreninstanz ist, können Sie die Zuordnung standardmäßig vornehmen. _on_, da dies der empfohlene Prozess ist.
* Wenn das Quellsystem eine Veröffentlichungsinstanz ist, können Sie die Zuordnung standardmäßig vornehmen. _off_, da Benutzer normalerweise nicht migriert oder in Veröffentlichungsinstanzen verwendet werden.

## Wichtige Aspekte bei der Zuordnung und Migration von Benutzenden {#important-considerations}


### Ausnahmefälle {#exceptional-cases}

Die folgenden spezifischen Fälle werden protokolliert:

1. Wenn der Benutzer keine E-Mail-Adresse in der `profile/email` ihres *jcr* -Knoten, den der betreffende Benutzer oder die fragliche Gruppe migrieren kann, aber nicht zugeordnet wird. Dies ist auch dann der Fall, wenn die E-Mail-Adresse als Benutzername für die Anmeldung verwendet wird.

1. Wenn der Benutzer deaktiviert ist, wird er so behandelt, als wäre er nicht deaktiviert. Sie wird wie gewohnt zugeordnet und migriert und bleibt in der Cloud-Instanz deaktiviert.

1. Wenn ein Benutzer in der AEM Cloud Service-Zielinstanz mit demselben Benutzernamen (rep:principalName) wie einer der Benutzer in der Quell-AEM-Instanz vorhanden ist, wird der betreffende Benutzer oder die betreffende Gruppe nicht migriert.

1. Wenn ein Benutzer migriert wird, ohne zuerst über die Benutzerzuordnung zugeordnet zu werden, oder wenn seine E-Mail-Adresse nicht mit der für die Anmeldung bei IMS verwendeten E-Mail-Adresse übereinstimmt, kann er sich im Target-Cloud-System nicht mit seiner IMS-ID anmelden. Sie können sich möglicherweise mit der herkömmlichen AEM anmelden. Beachten Sie jedoch, dass dies normalerweise nicht gewünscht oder erwartet wird.


## Zusätzliche Überlegungen {#additional-considerations}

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** festgelegt ist, werden bereits übertragene Benutzer in der Cloud Service-Instanz gelöscht und das gesamte vorhandene Repository wird neu erstellt, um Inhalte zu erfassen. Dadurch werden auch alle Einstellungen einschließlich der Berechtigungen für die Ziel-Cloud Service-Instanz zurückgesetzt. Dies gilt für einen Administrator, der der Gruppe **Administratoren** hinzugefügt wurde. Der Admin-Benutzer muss der **Administratoren** -Gruppe, um das Zugriffstoken für CTT abzurufen.
* Wenn Content-Uploads durchgeführt werden und Inhalte nicht übertragen werden, weil sie sich seit der vorherigen Übertragung nicht geändert haben, werden Benutzer und Gruppen, die mit diesem Inhalt verknüpft sind, auch dann nicht übertragen, wenn sich die Benutzer und Gruppen zwischenzeitlich geändert haben. Dies liegt daran, dass Benutzer und Gruppen zusammen mit dem Inhalt, mit dem sie verknüpft sind, migriert werden.
* Wenn die AEM Cloud Service-Zielinstanz über einen Benutzer mit einem anderen Benutzernamen, aber derselben E-Mail-Adresse wie einer der Benutzer in der Quell-AEM-Instanz verfügt und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung in die Protokolle geschrieben und der Quell-AEM-Benutzer wird nicht übertragen, da nur ein Benutzer mit einer bestimmten E-Mail-Adresse auf dem Zielsystem zulässig ist.
