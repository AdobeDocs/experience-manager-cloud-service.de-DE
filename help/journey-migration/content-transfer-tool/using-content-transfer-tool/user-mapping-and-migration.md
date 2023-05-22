---
title: Benutzerzuordnung und Prinzipalmigration
description: Übersicht über Benutzerzuordnung und Prinzipalmigration
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 100%

---

# Benutzerzuordnung und Prinzipalmigration {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Benutzerzuordnung"
>abstract="Mit dem Content Transfer Tool können Sie Benutzende und Gruppen aus Ihrem vorhandenen AEM-System in AEM as a Cloud Service verschieben. Vorhandene Benutzende müssen ihren IMS-IDs zugeordnet sein, damit sie nicht in der Autoreninstanz des Cloud Service dupliziert werden."

>[!NOTE]
>Frühere Versionen des Tools für die Benutzerzuordnung finden Sie in der [Legacy-Dokumentation](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Einführung {#introduction}

Im Rahmen der Umstellung auf Adobe Experience Manager (AEM) as a Cloud Service müssen Sie Benutzer und Gruppen aus Ihrem bestehenden AEM-System in AEM as a Cloud Service überführen. Verwenden Sie hierzu das Content Transfer Tool.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Autorenebene. Dies erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzern und Benutzergruppen. Die Benutzerprofilinformationen werden im Adobe Identity Management System (IMS) zentralisiert, das eine einmalige Anmeldung für alle Adobe Cloud-Programme ermöglicht. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=de#identity-management). Aufgrund dieser Änderung müssen bestehende Benutzende ihren IMS-IDs zugeordnet werden, um doppelte Benutzende auf der Cloud Service-Autoreninstanz zu vermeiden. Da sich Gruppen im traditionellen AEM grundlegend von Gruppen in IMS unterscheiden, werden Gruppen nicht zugeordnet, aber die beiden Gruppen müssen nach Abschluss der Migration aufeinander abgestimmt werden.

## Benutzerzuordnung und Migrationsdetails {#user-mapping-detail}

Das Content Transfer Tool und der Cloud Acceleration Manager migrieren alle Benutzerinnen und Benutzer, die mit dem migrierten Inhalt verknüpft sind. Diese Zuordnung erfolgt automatisch und ob sie durchgeführt wird, kann durch einen Umschalter gesteuert werden, bevor die Extraktion gestartet wird. Die Standardeinstellung des Umschalters kann von Benutzenden beim Starten der Extraktion überschrieben werden.

* Wenn das Quellsystem eine Autoreninstanz ist, ist die Wahl, die Zuordnung durchzuführen, standardmäßig _eingeschaltet_, da dies der empfohlene Prozess ist.
* Wenn das Quellsystem eine Veröffentlichungsinstanz ist, ist die Wahl, die Zuordnung durchzuführen, standardmäßig _ausgeschaltet_, da Benutzende auf Veröffentlichungsinstanzen normalerweise nicht migriert oder verwendet werden.

## Wichtige Aspekte bei der Zuordnung und Migration von Benutzenden {#important-considerations}


### Ausnahmefälle {#exceptional-cases}

Die folgenden spezifischen Fälle sind protokolliert:

1. Wenn Benutzende keine E-Mail-Adresse im `profile/email`-Feld ihres *jcr*-Knotens haben, werden die betreffenden Benutzenden bzw. Gruppen migriert, jedoch nicht zugeordnet. Dies ist auch dann der Fall, wenn die E-Mail-Adresse als Benutzername für die Anmeldung verwendet wird.

1. Falls die Benutzenden deaktiviert sind, werden sie ebenso behandelt, als wären sie nicht deaktiviert. Sie werden wie üblich zugeordnet und migriert, bleiben jedoch auf der Cloud-Instanz deaktiviert.

1. Falls auf der AEM Cloud Service-Zielinstanz Benutzende mit demselben Benutzernamen (rep:principalName) wie Benutzende auf der AEM-Quellinstanz existieren, werden die betroffenen Benutzenden oder Gruppen nicht migriert.

1. Wenn Benutzende migriert werden, ohne zuerst über die Benutzerzuordnung zugeordnet zu werden, oder wenn ihre E-Mail-Adresse nicht mit der für die Anmeldung bei IMS verwendeten E-Mail-Adresse übereinstimmt, können sie sich im Ziel-Cloud-System nicht mit ihrer IMS-ID anmelden. Sie können sich möglicherweise mit der herkömmlichen AEM-Methode anmelden. Beachten Sie jedoch, dass dies normalerweise nicht gewünscht oder erwartet wird.


## Zusätzliche Überlegungen {#additional-considerations}

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** festgelegt ist, werden bereits übertragene Benutzer in der Cloud Service-Instanz gelöscht und das gesamte vorhandene Repository wird neu erstellt, um Inhalte zu erfassen. Dadurch werden auch alle Einstellungen einschließlich der Berechtigungen für die Ziel-Cloud Service-Instanz zurückgesetzt. Dies gilt für einen Administrator, der der Gruppe **Administratoren** hinzugefügt wurde. Die Admin-Benutzerin bzw. der Admin-Benutzer muss der Gruppe **Administratoren** erneut hinzugefügt werden, um das Zugriffstoken für CTT abzurufen.
* Bei der Durchführung von Inhaltsauffüllungen werden (falls keine Inhalte übertragen werden, da sie seit der vorherigen Übertragung gleich geblieben sind) mit dem Inhalt verknüpfte Benutzende und Gruppen ebenfalls nicht übertragen, auch wenn sich die Benutzenden und Gruppen in der Zwischenzeit verändert haben. Dies liegt daran, dass Benutzende und Gruppen zusammen mit den Inhalten, mit denen sie verknüpft sind, migriert werden.
* Wenn auf der AEM Cloud Service-Zielinstanz Benutzende mit einem anderen Benutzernamen, aber derselben E-Mail-Adresse wie Benutzende auf der AEM-Quellinstanz bestehen und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung protokolliert und die Benutzerinnen und Benutzer der AEM-Quelle werden nicht übertragen, weil pro gegebener E-Mail-Adresse nur eine Person auf dem Zielsystem erlaubt ist.
