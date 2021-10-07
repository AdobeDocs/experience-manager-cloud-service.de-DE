---
title: Wichtige Überlegungen zum Benutzerzuordnungs-Tool
description: Wichtige Überlegungen zum Benutzerzuordnungs-Tool
source-git-commit: 9d131daf5b6a0b1530ebff48627f6130ef716f3e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 71%

---


# Wichtige Überlegungen zum Benutzerzuordnungs-Tool {#important-considerations}


## Ausnahmefälle {#exceptional-cases}

Die folgenden Sonderfälle werden protokolliert:

1. Wenn ein Benutzer keine E-Mail-Adresse im `profile/email`-Feld seines *jcr*-Knotens hat, wird der betreffende Benutzer oder die betreffende Gruppe migriert, jedoch nicht zugeordnet.

1. Wenn eine bestimmte E-Mail im Adobe Identity Management System (IMS) für die verwendete Organisations-ID nicht gefunden wird (oder wenn die IMS-ID aus einem anderen Grund nicht abgerufen werden kann), wird der betreffende Benutzer oder die betreffende Gruppe migriert, aber nicht zugeordnet.

1. Wenn der Benutzer derzeit deaktiviert ist, wird er genauso behandelt, als wäre er nicht deaktiviert. Er wird normal zugeordnet und migriert und bleibt in der Cloud-Instanz deaktiviert.

1. Wenn auf der Ziel-AEM Cloud Service-Instanz ein Benutzer mit demselben Benutzernamen (rep:principalName) wie einer der Benutzer in der Quell-AEM-Instanz vorhanden ist, wird der betreffende Benutzer oder die betreffende Gruppe nicht migriert.

## Weitere Aspekte {#additional-considerations}

* Wenn die Einstellung **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** festgelegt ist, werden bereits übertragene Benutzer in der Cloud Service-Instanz gelöscht und das gesamte vorhandene Repository wird neu erstellt, um Inhalte zu erfassen. Dadurch werden auch alle Einstellungen einschließlich der Berechtigungen für die Ziel-Cloud Service-Instanz zurückgesetzt. Dies gilt für einen Administrator, der der Gruppe **Administratoren** hinzugefügt wurde. Der Administrator muss der Gruppe **Administratoren** erneut hinzugefügt werden, um das Zugriffs-Token für CTT abzurufen.

* Es wird empfohlen, alle vorhandenen Benutzer aus der Ziel-AEM Cloud Service-Instanz zu entfernen, bevor CTT mit Benutzerzuordnung ausgeführt wird. Dies dient dazu, Konflikte zwischen migrierenden Benutzern der Quell-AEM-Instanz und der Ziel-AEM-Instanz zu vermeiden. Die Konflikte treten während der Aufnahme auf, wenn derselbe Benutzer in der Quell-AEM-Instanz und in der Zielgruppe-AEM-Instanz vorhanden ist.

* Wenn beim Auffüllen von Inhalten der Inhalt nicht übertragen wird, weil er sich seit der vorherigen Übertragung nicht geändert hat, werden auch die mit diesem Inhalt verknüpften Benutzer und Gruppen nicht übertragen, selbst wenn sich die Benutzer und Gruppen in der Zwischenzeit geändert haben. Dies liegt daran, dass Benutzer und Gruppen zusammen mit dem Inhalt, mit dem sie verknüpft sind, migriert werden.

* Wenn die AEM Cloud Service-Zielinstanz über einen Benutzer mit einem anderen Benutzernamen, aber derselben E-Mail-Adresse wie einer der Benutzer in der Quell-AEM-Instanz verfügt und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung in die Protokolle geschrieben und der Quell-AEM-Benutzer wird nicht übertragen, da nur ein Benutzer mit einer bestimmten E-Mail-Adresse im Zielsystem zulässig ist.

* Wenn zwei Benutzer in der Quell-AEM-Instanz dieselbe E-Mail-Adresse haben und die Benutzerzuordnung aktiviert ist, wird eine Fehlermeldung in die Protokolle geschrieben und eine der Quell-AEM-Benutzer wird nicht übertragen, da nur ein Benutzer mit einer bestimmten E-Mail-Adresse im Zielsystem zulässig ist.