---
title: Überprüfen des Domain-Namenstatus
description: Erfahren Sie, wie Sie feststellen können, ob Ihr benutzerdefinierter Domänenname von Cloud Manager erfolgreich verifiziert wurde.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: ba0226b5ad3852dd5f72dd7e0ace650035f5ac6a
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 13%

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

## Fehler bei Domain-Namen {#domain-error}

In diesem Abschnitt werden mögliche Fehler und deren Behebung erläutert.

**Domäne nicht installiert** - Sie erhalten diesen Fehler während der Domänenvalidierung des TXT-Eintrags, selbst wenn Sie überprüft haben, ob der Datensatz ordnungsgemäß aktualisiert wurde.

**Fehlerbehebung** - Sperrt eine Domain schnell auf das ursprüngliche Konto, das sie registriert hat, und kein anderes Konto kann eine Subdomain registrieren, ohne um Erlaubnis zu fragen. Darüber hinaus ermöglicht Fastly es Ihnen nur, eine Apex-Domäne und zugehörige Subdomains einem Fastly-Dienst und -Konto zuzuweisen. Wenn Sie über ein vorhandenes Fastly-Konto verfügen, das denselben Namen und dieselbe Subdomain verknüpft, die für Ihre AEM Cloud Service-Domänen verwendet werden, wird dieser Fehler angezeigt.

**Fehlerbehebung** - Der Fehler wird wie folgt behoben:

* Entfernen Sie die Apex- und Subdomänen aus dem vorhandenen Konto, bevor Sie die Domäne in Cloud Manager installieren. Verwenden Sie diese Option, um die Apex-Domäne und alle Subdomänen mit dem AEM as a Cloud Service Fastly-Konto zu verknüpfen. Siehe [Arbeiten mit Domänen in der Schnelldokumentation](https://docs.fastly.com/en/guides/working-with-domains) für weitere Details.

* Wenn Ihre Apex-Domäne über mehrere Subdomains für AEM as a Cloud Service und nicht AEM as a Cloud Service Sites verfügt, die Sie mit verschiedenen Fastly-Konten verknüpfen möchten, versuchen Sie, die Domäne in Cloud Manager zu installieren. Wenn die Domäneninstallation fehlschlägt, erstellen Sie ein Support-Ticket mit Schnell , damit wir in Ihrem Namen mit Fastly fortfahren können.

>[!NOTE]
>
>HINWEIS: Führen Sie das DNS Ihrer Site nicht an as a Cloud Service IPs AEM, wenn die Domäne nicht erfolgreich installiert wurde.

## Vorbestehende CDN-Konfigurationen für benutzerdefinierte Domain-Namen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration für Ihre benutzerdefinierten Domänennamen verfügen, enthält die **Benutzerdefinierte Domänennamen** und **Umgebung** Seiten, die Sie dazu ermutigen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1-2 Werktage dauern, bis die Nachricht ausgeblendet wird.

Weitere Informationen finden Sie im Dokument . [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) für weitere Details.
