---
title: Überprüfen des Domain-Namenstatus
description: Erfahren Sie, wie Sie feststellen können, ob Ihr benutzerdefinierter Domain-Name von Cloud Manager erfolgreich verifiziert wurde.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 85%

---


# Überprüfen des Domain-Namenstatus {#check-status}

Sie können den Status Ihres benutzerdefinierten Domain-Namens in Cloud Manager ermitteln.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicks **Domäneneinstellungen** im linken Navigationsbereich.

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

   * In solchen Fällen kontaktieren Sie bitte den Adobe-Support-Mitarbeiter.

* **Domain überprüft und bereitgestellt** –
Dieser Status gibt an, dass Ihr benutzerdefinierter Domain-Name verwendet werden kann.

   * An dieser Stelle steht Ihr benutzerdefinierter Domain-Name zum Testen bereit und verweist auf den Domain-Namen von Cloud Manager.
   * Weitere Informationen finden Sie unter [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md).

* **Wird gelöscht** – Das Löschen eines benutzerdefinierten Domain-Namens ist in Bearbeitung.

* **Löschvorgang fehlgeschlagen** – Das Löschen des benutzerdefinierten Domänen-Namens ist fehlgeschlagen und muss erneut versucht werden.

   * Weitere Information finden Sie unter [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md).

Cloud Manager löst automatisch eine TXT-Überprüfung aus, wenn Sie im Überprüfungsschritt des Assistenten zum **Hinzufügen benutzerdefinierter Domains** auf **Speichern** klicken. Für spätere Überprüfungen müssen Sie das Symbol Erneut überprüfen neben dem Status aktiv auswählen.

## Fehler bei Domain-Namen {#domain-error}

Im Folgenden finden Sie einige häufige Fehler bei Domain-Namen und dafür typische Lösungen.

### Fehler „Domain nicht installiert“ {#domain-not-installed}

Dieser Fehler kann bei der Domain-Validierung des TXT-Eintrags auftreten, selbst wenn Sie überprüft haben, dass der Datensatz ordnungsgemäß aktualisiert worden ist.

#### Fehlerursache {#cause}

Fastly beschränkt eine Domain auf das ursprünglich registrierte Konto, und kein anderes Konto kann eine Subdomain registrieren, ohne die Erlaubnis dafür einzuholen. Darüber hinaus können Sie mit Fastly nur einem Fastly-Dienst und -Konto eine Apex-Domäne und zugehörige Subdomains zuweisen. Wenn Sie über ein vorhandenes Fastly-Konto verfügen, das denselben Namen und dieselbe Subdomäne verknüpft, die für Ihre AEM Cloud Service-Domänen verwendet werden, wird dieser Fehler angezeigt.

#### Fehlerbehebung {#resolution}

Der Fehler wird wie folgt behoben:

* Entfernen Sie die Apex- und Subdomains aus dem vorhandenen Konto, bevor Sie die Domain in Cloud Manager installieren.

* Verwenden Sie diese Option, um die Apex-Domain und alle Subdomains mit dem AEM as a Cloud Service Fastly-Konto zu verknüpfen. Weitere Informationen finden Sie in der [Fastly-Dokumentation unter Arbeiten mit Domains](https://docs.fastly.com/en/guides/working-with-domains).

* Wenn Ihre Apex-Domain über mehrere Subdomains für AEM as a Cloud Service und davon verschiedene Sites verfügt, die Sie mit verschiedenen Fastly-Konten verknüpfen möchten, versuchen Sie, die Domain in Cloud Manager zu installieren. Falls die Domain-Installation fehlschlägt, erstellen Sie mit Fastly ein Kunden-Support-Ticket, damit Adobe in Ihrem Namen bei Fastly nachhaken kann.

>[!TIP]
>
>Die Lösung von Problemen bei der Domain-Delegation mit Fastly dauert normalerweise 1 bis 2 Werktage. Daher wird dringend empfohlen, die Domains rechtzeitig vor ihrem Aufschaltdatum zu installieren.

>[!NOTE]
>
>Leiten Sie das DNS Ihrer Site nicht an die IPs von AEM as a Cloud Service weiter, wenn die Domain nicht erfolgreich installiert wurde.

## Bereits vorhandene CDN-Konfigurationen für benutzerdefinierte Domain-Namen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration für Ihre benutzerdefinierten Domänennamen verfügen, finden Sie eine informative Meldung im **Benutzerdefinierte Domänennamen** und **Umgebung** Seiten, die Sie dazu ermutigen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
