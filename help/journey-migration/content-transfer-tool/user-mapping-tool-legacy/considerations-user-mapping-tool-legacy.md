---
title: Wichtige Überlegungen zur Verwendung des Tools für die Benutzerzuordnung (veraltete Version)
description: Wichtige Überlegungen zur Verwendung des Tools für die Benutzerzuordnung (veraltete Version)
exl-id: 0d39a5be-93e1-4b00-ac92-c2593c02b740
hide: true
hidefromtoc: true
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 12%

---

# Wichtige Überlegungen zur Verwendung des Tools für die Benutzerzuordnung (veraltete Version) {#important-considerations}

>[!INFO]
>
>Diese Dokumentation bezieht sich auf eine veraltete Version des Tools. Weitere Informationen zur neuesten Version finden Sie unter [Benutzerzuordnung und Hauptmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

## Ausnahmefälle {#exceptional-cases}

Die folgenden spezifischen Fälle sind protokolliert:

1. Wenn der Benutzer keine E-Mail-Adresse in der `profile/email` ihres *jcr* -Knoten, wird der betreffende Benutzer oder die fragliche Gruppe migriert, aber nicht zugeordnet. Diese Regel ist auch dann anwendbar, wenn die E-Mail-Adresse als Benutzername für die Anmeldung verwendet wird.

1. Wenn im Adobe Identity Management System (IMS) keine E-Mail für die verwendete Organisations-ID gefunden wird (oder wenn die IMS-ID nicht abgerufen werden kann), wird der Benutzer oder die Gruppe migriert, aber nicht zugeordnet.

1. Falls die Benutzenden deaktiviert sind, werden sie ebenso behandelt, als wären sie nicht deaktiviert. Er wird wie gewohnt zugeordnet und migriert und bleibt in der Cloud-Instanz deaktiviert.

1. Wenn ein Benutzer in der AEM Cloud Service-Zielinstanz mit demselben Benutzernamen (rep:principalName) wie einer der Benutzer in der Quell-AEM-Instanz vorhanden ist, wird der Benutzer oder die Gruppe nicht migriert.

1. Wenn ein Benutzer migriert wird, ohne zunächst über die Benutzerzuordnung zugeordnet zu werden, kann er sich auf dem Ziel-Cloud-System nicht mit seiner IMS-ID anmelden. Sie können sich möglicherweise mit der herkömmlichen AEM anmelden, aber dieser Workflow ist normalerweise nicht das, was gewünscht oder erwartet wird.

## Zusätzliche Überlegungen {#additional-considerations}

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** festgelegt ist, werden bereits übertragene Benutzer in der Cloud Service-Instanz gelöscht. Das gesamte vorhandene Repository wird ebenfalls gelöscht und ein neues Repository erstellt, in das Inhalte aufgenommen werden. Diese Aktion setzt auch alle Einstellungen zurück, einschließlich Berechtigungen für die Ziel-Cloud Service-Instanz, und gilt für einen Administrator, der der **Administratoren** hinzugefügt. Der Admin-Benutzer muss in die **Administratoren** -Gruppe, um das Zugriffstoken für CTT abzurufen.

* Adobe empfiehlt, dass Sie jeden vorhandenen Cloud Service aus der Ziel-AEM-Instanz entfernen, bevor Sie CTT mit User Mapping ausführen. Diese Aktion ist erforderlich, um Konflikte zwischen der Migration von Benutzern aus der AEM zur Ziel-AEM-Instanz zu vermeiden. Konflikte können während der Aufnahme auftreten, wenn derselbe Benutzer in der Quell-AEM-Instanz und der Ziel-AEM-Instanz vorhanden ist.

* Wenn bei der Auffüllung von Inhalten keine Inhalte übertragen werden, weil sie seit der vorherigen Übertragung nicht geändert wurden, werden die mit diesen Inhalten verknüpften Benutzer und Gruppen auch nicht übertragen. Diese Regel gilt auch dann, wenn sich die Benutzer und Gruppen zwischenzeitlich geändert haben. Der Grund dafür ist, dass Benutzer und Gruppen zusammen mit den Inhalten migriert werden, mit denen sie verknüpft sind.

* Wenn die AEM Cloud Service einen Benutzer mit einem anderen Benutzernamen, aber derselben E-Mail-Adresse wie ein Benutzer in der Quell-AEM-Instanz hat und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung protokolliert. Außerdem wird der Quell-AEM-Benutzer nicht übertragen, da nur ein Benutzer mit einer bestimmten E-Mail-Adresse auf dem Zielsystem zulässig ist.

* Wenn zwei Benutzer in der Quell-AEM-Instanz dieselbe E-Mail-Adresse haben und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung protokolliert. Außerdem wird einer der Quell-AEM-Benutzer übertragen, da nur ein Benutzer mit einer bestimmten E-Mail-Adresse auf dem Zielsystem zulässig ist.

### Wie geht es weiter {#whats-next}

Nun, da Sie die wichtigen Überlegungen und Ausnahmefälle kennen, können Sie das Tool verwenden. Weitere Informationen finden Sie unter [Verwendung des Tools für die Benutzerzuordnung](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/using-user-mapping-tool-legacy.md).
