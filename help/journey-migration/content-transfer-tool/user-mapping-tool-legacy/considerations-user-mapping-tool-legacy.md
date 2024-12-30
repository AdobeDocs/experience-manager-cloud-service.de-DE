---
title: Wichtige Überlegungen zur Verwendung des Tools für die Benutzerzuordnung (veraltete Version)
description: Wichtige Überlegungen zur Verwendung des Tools für die Benutzerzuordnung (veraltete Version)
exl-id: 0d39a5be-93e1-4b00-ac92-c2593c02b740
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: 13a2386c099624a46e84126a939a9470e9b3a5f2
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 100%

---

# Wichtige Überlegungen zur Verwendung des Tools für die Benutzerzuordnung (veraltete Version) {#important-considerations}

>[!INFO]
>
>Diese Dokumentation bezieht sich auf eine veraltete Version des Tools. Weitere Informationen zur neuesten Version finden Sie unter [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

## Ausnahmefälle {#exceptional-cases}

Die folgenden spezifischen Fälle sind protokolliert:

1. Wenn eine Benutzerin oder ein Benutzer keine E-Mail-Adresse im Feld `profile/email` des *jcr*-Knotens hat, wird die betreffende Person oder Gruppe migriert, jedoch nicht zugeordnet. Diese Regel gilt auch dann, wenn die E-Mail-Adresse als Benutzername für die Anmeldung verwendet wird.

1. Wenn eine E-Mail im Adobe Identity Management System (IMS) für die verwendete Organisations-ID nicht gefunden wird (oder wenn die IMS-ID nicht abgerufen werden kann), wird die betreffende Person oder Gruppe migriert, aber nicht zugeordnet.

1. Falls die Benutzenden deaktiviert sind, werden sie ebenso behandelt, als wären sie nicht deaktiviert. Sie werden wie üblich zugeordnet und migriert, bleiben jedoch in der Cloud-Instanz deaktiviert.

1. Falls in der AEM Cloud Service-Zielinstanz eine Person mit demselben Benutzernamen (rep:principalName) wie eine oder einer der Benutzenden in der AEM-Quellinstanz existiert, wird die Person oder Gruppe nicht migriert.

1. Wenn Benutzende migriert werden, ohne zunächst über die Benutzerzuordnung zugeordnet zu werden, können sie sich auf dem Cloud-Zielsystem nicht mit ihrer IMS-ID anmelden. Sie können sich gegebenenfalls mit der herkömmlichen AEM-Methode anmelden, jedoch wird dies normalerweise nicht gewünscht oder erwartet.

## Zusätzliche Überlegungen {#additional-considerations}

* Wenn die Einstellung **Vorhandene Inhalte in der Cloud-Instanz vor der Aufnahme löschen** festgelegt ist, werden bereits übertragene Benutzende in der Cloud Service-Instanz gelöscht. Das gesamte vorhandene Repository wird ebenfalls gelöscht und ein neues Repository erstellt, in das Inhalte aufgenommen werden. Dadurch werden auch alle Einstellungen zurückgesetzt, einschließlich der Berechtigungen für die Cloud Service-Zielinstanz. Dies gilt für Admin-Benutzende, die der Gruppe der **Admins** hinzugefügt wurden. Die Admin-Benutzenden müssen der Gruppe der **Admins** erneut hinzugefügt werden, um das Zugriffs-Token für CTT abzurufen.

* Adobe empfiehlt, alle vorhandenen Benutzenden aus der AEM Cloud Service-Zielinstanz zu entfernen, bevor CTT mit Benutzerzuordnung ausgeführt wird. Dies ist erforderlich, um beim Migrieren der Benutzenden Konflikte zwischen der AEM-Quellinstanz und AEM-Zielinstanz zu vermeiden. Diese Konflikte treten während der Aufnahme auf, wenn dieselbe Benutzerin oder derselbe Benutzer in der AEM-Quellinstanz und in der AEM-Zielinstanz vorhanden ist.

* Wenn bei der Durchführung von Inhaltsauffüllungen Inhalte nicht übertragen werden, weil sie sich seit der letzten Übertragung nicht geändert haben, werden auch die mit diesen Inhalten verbundenen Benutzenden und Gruppen nicht übertragen. Diese Regel gilt auch dann, wenn sich die Benutzenden und Gruppen zwischenzeitlich geändert haben. Dies liegt daran, dass Benutzende und Gruppen zusammen mit den Inhalten, mit denen sie verknüpft sind, migriert werden.

* Wenn AEM Cloud Service eine Person mit einem anderen Benutzernamen, aber derselben E-Mail-Adresse wie eine Benutzerin oder ein Benutzer in der AEM-Quellinstanz aufweist und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung protokolliert. Außerdem wird die AEM-Quellbenutzerin oder der AEM-Quellbenutzer nicht übertragen, da nur eine Benutzerin oder ein Benutzer mit einer bestimmten E-Mail-Adresse auf dem Zielsystem zulässig ist.

* Wenn zwei Benutzende in der AEM-Quellinstanz dieselbe E-Mail-Adresse haben und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung protokolliert. Außerdem wird eine oder einer der AEM-Quellbenutzenden übertragen, da nur eine Person mit einer bestimmten E-Mail-Adresse auf dem Zielsystem zulässig ist.

### Wie geht es weiter {#whats-next}

Nun, da Sie die wichtigen Überlegungen und Ausnahmefälle kennen, können Sie das Tool verwenden. Weitere Informationen finden Sie unter [Verwendung des Tools für die Benutzerzuordnung](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/using-user-mapping-tool-legacy.md).
