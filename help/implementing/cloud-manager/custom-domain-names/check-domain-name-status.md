---
title: Überprüfen des Domain-Namenstatus
description: Erfahren Sie, wie Sie feststellen können, ob Ihr benutzerdefinierter Domain-Name von Cloud Manager erfolgreich verifiziert wurde.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: ba0226b5ad3852dd5f72dd7e0ace650035f5ac6a
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 100%

---


# Überprüfen des Domain-Namenstatus {#check-status}

Sie können den Status Ihres benutzerdefinierten Domain-Namens in Cloud Manager ermitteln.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich auf **Domain-Einstellungen**.

1. Klicken Sie auf das Symbol **Status**, um den Domain-Namen zu sehen.

Cloud Manager überprüft den Domain-Besitz über den TXT-Wert und zeigt eine der folgenden Statusmeldungen an.

* **Domain-Überprüfung fehlgeschlagen**
– TXT-Wert fehlt entweder oder wird mit Fehlern erkannt.

   * Befolgen Sie die Anweisungen zur Behebung des Problems.
   * Wenn Sie bereit sind, müssen Sie das Symbol zum **erneuten Überprüfen** neben dem Status auswählen.

* **Die Domain-Überprüfung wird durchgeführt** –
Die Überprüfung ist in Bearbeitung.

   * Dieser Status wird in der Regel angezeigt, nachdem Sie das Symbol **Erneut überprüfen** neben dem Status angeklickt haben.

* **Verifiziert, Bereitstellung fehlgeschlagen** – Die TXT-Überprüfung war erfolgreich, aber die CDN-Bereitstellung schlug fehl.

   * In solchen Fällen kontaktieren Sie bitte Ihren Adobe-Support-Mitarbeiter.

* **Domain überprüft und bereitgestellt** –
Dieser Status gibt an, dass Ihr benutzerdefinierter Domain-Name verwendet werden kann.

   * An dieser Stelle steht Ihr benutzerdefinierter Domain-Name zum Testen bereit und verweist auf den Domain-Namen von Cloud Manager.
   * Weitere Informationen finden Sie im Dokument [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md).

* **Wird gelöscht** – Das Löschen eines benutzerdefinierten Domain-Namens ist in Bearbeitung.

* **Löschvorgang fehlgeschlagen** – Das Löschen des benutzerdefinierten Domänen-Namens ist fehlgeschlagen und muss erneut versucht werden.

   * Weitere Informationen finden Sie im Dokument [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md).

Cloud Manager löst automatisch eine TXT-Überprüfung aus, wenn Sie im Überprüfungsschritt des Assistenten zum **Hinzufügen benutzerdefinierter Domains** auf **Speichern** klicken. Für spätere Überprüfungen müssen Sie das Symbol Erneut überprüfen neben dem Status aktiv auswählen.

## Fehler bei Domain-Namen {#domain-error}

In diesem Abschnitt werden mögliche Fehler und deren Behebung erläutert.

**Domain nicht installiert** – Sie erhalten diese Fehlermeldung während der Domain-Validierung des TXT-Eintrags, selbst nachdem Sie überprüft haben, ob der Datensatz ordnungsgemäß aktualisiert wurde.

**Fehlererklärung** – Sperrt eine Domain schnell auf das ursprüngliche Konto, das sie registriert hat, und kein anderes Konto kann eine Subdomain registrieren, ohne um Erlaubnis zu fragen. Darüber hinaus ermöglicht Fastly es Ihnen nur, eine Apex-Domain und zugehörige Subdomains einem Fastly-Service und -Konto zuzuweisen. Wenn Sie über ein vorhandenes Fastly-Konto verfügen, das denselben Namen und dieselbe Subdomain verknüpft, die für Ihre AEM as a Cloud Service-Domains verwendet werden, wird dieser Fehler angezeigt.

**Fehlerbehebung** – Der Fehler wird wie folgt behoben:

* Entfernen Sie die Apex- und Subdomains aus dem vorhandenen Konto, bevor Sie die Domain in Cloud Manager installieren. Verwenden Sie diese Option, um die Apex-Domain und alle Subdomains mit dem AEM as a Cloud Service Fastly-Konto zu verknüpfen. Weitere Informationen finden Sie in der [Fastly-Dokumentation unter Arbeiten mit Domains](https://docs.fastly.com/en/guides/working-with-domains).

* Wenn Ihre Apex-Domain mehrere Subdomains für AEM as a Cloud Service- und Nicht-AEM as a Cloud Service-Sites hat, die Sie mit verschiedenen Fastly-Konten verknüpfen möchten, versuchen Sie, die Domain im Cloud Manager zu installieren. Wenn die Domain-Installation fehlschlägt, erstellen Sie ein Kundensupport-Ticket bei Fastly, damit wir in Ihrem Namen mit Fastly Kontakt aufnehmen können.

>[!NOTE]
>
>HINWEIS: Leiten Sie den DNS Ihrer Website nicht an die IPs von AEM as a Cloud Service weiter, wenn die Domain nicht erfolgreich installiert wurde.

## Vorbestehende CDN-Konfigurationen für benutzerdefinierte Domain-Namen {#pre-existing-cdn}

Wenn Sie eine bereits bestehende CDN-Konfiguration für Ihre benutzerdefinierten Domain-Namen haben, wird auf den Seiten **Benutzerdefinierte Domain-Namen** und **Umgebung** eine informative Meldung angezeigt, die Sie auffordert, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie im Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie im Dokument [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
