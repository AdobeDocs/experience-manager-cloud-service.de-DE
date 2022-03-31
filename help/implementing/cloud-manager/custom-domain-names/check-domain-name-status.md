---
title: Überprüfen des Domain-Namenstatus
description: Erfahren Sie, wie Sie feststellen können, ob Ihr benutzerdefinierter Domänenname von Cloud Manager erfolgreich verifiziert wurde.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: 878381f9c5780864f218a00a272b1600d578dcca
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 21%

---


# Überprüfen des Domain-Namenstatus {#check-status}

Sie können den Status Ihres benutzerdefinierten Domänennamen in Cloud Manager ermitteln.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.

1. Klicken Sie auf **Domäneneinstellungen** im linken Navigationsbereich.

1. Klicken Sie auf **Status** für den Domänennamen.

Cloud Manager überprüft den Domain-Besitz über den TXT-Wert und zeigt eine der folgenden Statusmeldungen an.

* **Domänenüberprüfung fehlgeschlagen** - Der TXT-Wert fehlt oder wird mit Fehlern erkannt.

   * Befolgen Sie die Anweisungen zur Behebung des Problems.
   * Wenn Sie bereit sind, müssen Sie die **Erneut überprüfen** neben dem Status.

* **Domänenüberprüfung läuft** - Die Überprüfung wird durchgeführt.

   * Dieser Status wird normalerweise angezeigt, nachdem Sie die **Erneut überprüfen** neben dem Status.

* **Verifiziert, Bereitstellung fehlgeschlagen** - Die TXT-Überprüfung war erfolgreich, aber die CDN-Bereitstellung schlug fehl.

   * In solchen Fällen kontaktieren Sie bitte Ihren Kundenbetreuer bei der Adobe.

* **Domäne überprüft und bereitgestellt** - Dieser Status zeigt an, dass Ihr benutzerdefinierter Domänenname verwendet werden kann.

   * An dieser Stelle steht Ihr benutzerdefinierter Domain-Name zum Testen bereit und verweist auf den Domain-Namen von Cloud Manager.
   * Weitere Informationen finden Sie im Dokument . [DNS-Einstellungen konfigurieren](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) , um mehr zu erfahren.

* **Löschen** - Das Löschen eines benutzerdefinierten Domain-Namens wird ausgeführt.

* **Löschvorgang fehlgeschlagen** - Das Löschen des benutzerdefinierten Domänennamens ist fehlgeschlagen und muss erneut versucht werden.

   * Weitere Informationen finden Sie im Dokument . [Verwalten benutzerdefinierter Domänennamen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) , um mehr zu erfahren.

Cloud Manager Trigger bei Auswahl von automatisch eine TXT-Überprüfung **Speichern** über den Überprüfungsschritt der **Benutzerdefinierte Domäne hinzufügen** Assistent. Für spätere Überprüfungen müssen Sie das Symbol Erneut überprüfen neben dem Status aktiv auswählen.

## Vorbestehende CDN-Konfigurationen für benutzerdefinierte Domain-Namen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration für Ihre benutzerdefinierten Domänennamen verfügen, enthält die **Benutzerdefinierte Domänennamen** und **Umgebung** Seiten, die Sie dazu ermutigen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1-2 Werktage dauern, bis die Nachricht ausgeblendet wird.

Weitere Informationen finden Sie im Dokument . [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) für weitere Details.
