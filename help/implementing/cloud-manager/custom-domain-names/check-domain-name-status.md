---
title: Überprüfen des Domain-Namenstatus
description: Überprüfen des Domain-Namenstatus
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: 417939cb7a206d2b98b5e631a09307edc6724c17
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 80%

---

# Überprüfen des Domain-Namenstatus {#check-status}

Sie können feststellen, ob Ihr Domain-Name erfolgreich überprüft wurde, indem Sie auf der Seite mit den Domain-Einstellungen auf das Statussymbol für den Domain-Namen in der Tabelle für Umgebungen klicken.

>[!NOTE]
>Cloud Manager löst automatisch eine TXT-Überprüfung aus, wenn Sie im Überprüfungsschritt des Assistenten zum Hinzufügen benutzerdefinierter Domains auf „Speichern“ klicken oder tippen. Für spätere Überprüfungen müssen Sie das Symbol **Erneut überprüfen** neben dem Status aktiv auswählen.

Cloud Manager überprüft den Domain-Besitz über den TXT-Wert und zeigt eine der folgenden Statusmeldungen an:

* **Fehler bei der Domain-Überprüfung**
TXT-Wert fehlt entweder oder wird mit Fehlern erkannt. Befolgen Sie die Anweisungen und versuchen Sie es erneut. Wählen Sie das Symbol 
*Erneut überprüfen* neben dem Status aus.

* **Die Domain-Überprüfung wird durchgeführt**
Die Überprüfung erfolgt. Dieser Status wird normalerweise angezeigt, nachdem Sie das Symbol 
*Erneut überprüfen* neben dem Status aus.

* **Überprüft, Fehler bei der Bereitstellung**
TXT-Überprüfung war erfolgreich. Die CDN-Bereitstellung ist jedoch fehlgeschlagen. Ein Adobe-Support-Mitarbeiter wird automatisch benachrichtigt.

* **Domain überprüft und bereitgestellt**
Dieser Status gibt an, dass Ihr benutzerdefinierter Domain-Name verwendet werden kann.
   >[!NOTE]
   >An dieser Stelle steht Ihr benutzerdefinierter Domain-Name zum Testen bereit und verweist auf den Domain-Namen von Cloud Manager. Weitere Informationen finden Sie unter [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md).

* **Wird gelöscht**
Die Löschung des benutzerdefinierten Domain-Namens wird durchgeführt.

* **Löschen fehlgeschlagen**
Die Löschung des benutzerdefinierten Domain-Namens ist fehlgeschlagen. Sie müssen es erneut versuchen. Weitere Informationen finden Sie unter [Löschen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md).


## Vorbestehende CDN-Konfigurationen für benutzerdefinierte Domänennamen {#pre-existing-cdn}

Kunden mit Umgebungen, die bereits vorhandene CDN-Konfigurationen für IP-Zulassungslisten, SSL-Zertifikate oder benutzerdefinierte Domänennamen enthalten, sehen die folgende Meldung auf der Detailseite **IP-Zulassungsliste** und **Umgebung** . Die auf der Benutzeroberfläche angezeigte Meldung wird ausgeblendet, sobald der Kunde alle bereits vorhandenen Konfigurationen der Umgebung über die Benutzeroberfläche vollständig migriert hat. Es kann ein bis zwei Werktage dauern, bis die Meldung ausgeblendet wird.

>[!NOTE]
>Um die bereits vorhandenen Konfigurationen anzuzeigen und zu verwalten, müssen sie über die Benutzeroberfläche hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) .

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
