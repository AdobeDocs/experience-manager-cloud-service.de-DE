---
title: Überprüfen des Domain-Namenstatus
description: Überprüfen des Domain-Namenstatus
translation-type: tm+mt
source-git-commit: f11cb3b56f51046779300626d1deb037dd687309
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 72%

---


# Überprüfen des Domain-Namenstatus {#check-status}

Sie können feststellen, ob Ihr Domain-Name erfolgreich überprüft wurde, indem Sie auf der Seite mit den Domain-Einstellungen auf das Statussymbol für den Domain-Namen in der Tabelle für Umgebungen klicken.

>[!NOTE]
>Cloud Manager löst automatisch eine TXT-Überprüfung aus, wenn Sie im Überprüfungsschritt des Assistenten zum Hinzufügen benutzerdefinierter Domains auf „Speichern“ klicken oder tippen. Für spätere Überprüfungen müssen Sie das Symbol **Erneut überprüfen** neben dem Status aktiv auswählen.

Cloud Manager überprüft den Domain-Besitz über den TXT-Wert und zeigt eine der folgenden Statusmeldungen an:

* **Fehler bei der Domain-Überprüfung**
TXT-Wert fehlt entweder oder wird mit Fehlern erkannt. Befolgen Sie die Anweisungen und versuchen Sie es erneut. Wenn Sie bereit sind, müssen Sie die 
*überprüfen Sie* das Symbol neben dem Status.

* **Die Domain-Überprüfung wird durchgeführt**
Die Überprüfung erfolgt. Dieser Status wird normalerweise angezeigt, nachdem Sie die Variable 
*überprüfen Sie* das Symbol neben dem Status.

* **Überprüft, Fehler bei der Bereitstellung**
TXT-Überprüfung war erfolgreich. Die CDN-Bereitstellung ist jedoch fehlgeschlagen. Ein Adobe-Support-Mitarbeiter wird automatisch benachrichtigt.

* **Domain überprüft und bereitgestellt**
Dieser Status gibt an, dass Ihr benutzerdefinierter Domain-Name verwendet werden kann.
   >[!NOTE]
   >An dieser Stelle steht Ihr benutzerdefinierter Domänenname zum Testen bereit und wird auf den Domänennamen von Cloud Manager verwiesen. Weitere Informationen finden Sie unter [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md).

* **Wird gelöscht**
Die Löschung des benutzerdefinierten Domain-Namens wird durchgeführt.

* **Löschen fehlgeschlagen**
Die Löschung des benutzerdefinierten Domain-Namens ist fehlgeschlagen. Sie müssen es erneut versuchen. Weitere Informationen finden Sie unter [Löschen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md).

