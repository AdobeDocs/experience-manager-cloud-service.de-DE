---
title: Überprüfen des Domain-Namenstatus
description: Erfahren Sie, wie Sie feststellen können, ob Ihr benutzerdefinierter Domain-Name von Cloud Manager erfolgreich verifiziert wurde.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 93%

---


# Überprüfen des Domain-Namenstatus {#check-status}

Erfahren Sie, wie Sie feststellen können, ob Ihr benutzerdefinierter Domain-Name von Cloud Manager erfolgreich verifiziert wurde.

## Voraussetzungen {#requirements}

Sie müssen diese Anforderungen erfüllen, bevor Sie Ihren Domain-Namensstatus in Cloud Manager überprüfen.

* Sie müssen zunächst einen TXT-Eintrag für Ihre benutzerdefinierte Domäne hinzufügen, wie im Dokument [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) beschrieben.

## Überprüfen des Status Ihres benutzerdefinierten Domain-Namens {#how-to}

Sie können den Status Ihres benutzerdefinierten Domain-Namens in Cloud Manager ermitteln.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich auf **Domain-Einstellungen**.

1. Klicken Sie auf das Symbol **Status**, um den Domain-Namen zu sehen.

Das Statusdetail wird angezeigt. Ihre benutzerdefinierte Domain kann verwendet werden, wenn der Status **Domain überprüft und bereitgestellt** angezeigt wird. Weitere Informationen zu den verschiedenen Status und ihren Bedeutungen finden Sie im [nächsten Abschnitt](#statuses).

>[!NOTE]
>
>Cloud Manager überprüft den Trigger automatisch, wenn Sie im Überprüfungsschritt des Assistenten **Benutzerdefinierte Domäne hinzufügen** die Option **Erstellen** auswählen, wenn Sie [ einen neuen benutzerdefinierten Domänennamen zu Cloud Manager hinzufügen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Für spätere Überprüfungen müssen Sie das Symbol „Erneut überprüfen“ neben dem Status aktiv auswählen.

## Grundlagen zu Überprüfungsstatus {#statuses}

Cloud Manager überprüft den Domain-Besitzstatus über den [TXT-Wert](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) und zeigt eine der folgenden Statusmeldungen an.

* **Domain-Überprüfung fehlgeschlagen** – TXT-Wert fehlt entweder oder wird mit Fehlern erkannt.

   * Befolgen Sie die Anweisungen in der Statusmeldung, um das Problem zu beheben.
   * Wenn Sie bereit sind, müssen Sie das Symbol zum **erneuten Überprüfen** neben dem Status auswählen.

* **Die Domain-Überprüfung wird durchgeführt** –
Die Überprüfung ist in Bearbeitung.

   * Dieser Status wird in der Regel angezeigt, nachdem Sie das Symbol **Erneut überprüfen** neben dem Status angeklickt haben.
   * Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.

* **Verifiziert, Bereitstellung fehlgeschlagen** – Die TXT-Überprüfung war erfolgreich, aber die CDN-Bereitstellung schlug fehl.

   * In solchen Fällen kontaktieren Sie bitte den Adobe-Support-Mitarbeiter.

* **Domain überprüft und bereitgestellt** –
Dieser Status gibt an, dass Ihr benutzerdefinierter Domain-Name verwendet werden kann.

   * An dieser Stelle steht Ihr benutzerdefinierter Domain-Name zum Testen bereit und verweist auf den Domain-Namen von Cloud Manager.
   * Weitere Informationen finden Sie unter [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md).

* **Wird gelöscht** – Das Löschen eines benutzerdefinierten Domain-Namens ist in Bearbeitung.

* **Löschvorgang fehlgeschlagen** – Das Löschen des benutzerdefinierten Domänen-Namens ist fehlgeschlagen und muss erneut versucht werden.

   * Weitere Information finden Sie unter [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md).

## Fehler bei Domain-Namen {#domain-error}

Im Folgenden finden Sie einige häufige Fehler bei der Überprüfung des Domain-Namens und dafür gängige Lösungen.

### Fehler „Domain nicht installiert“ {#domain-not-installed}

Dieser Fehler kann bei der Domain-Validierung des TXT-Eintrags auftreten, selbst wenn Sie überprüft haben, dass der Datensatz ordnungsgemäß aktualisiert worden ist.

#### Fehlerursache {#cause}

Fastly beschränkt eine Domain auf das ursprünglich registrierte Konto, und kein anderes Konto kann eine Subdomain registrieren, ohne die Erlaubnis dafür einzuholen. Darüber hinaus ermöglicht Fastly es Ihnen nur, eine Apex-Domain und zugehörige Subdomains einem Fastly-Service und -Konto zuzuweisen. Wenn Sie über ein vorhandenes Fastly-Konto verfügen, das denselben Namen und dieselbe Subdomain verknüpft, die für Ihre AEM as a Cloud Service-Domains verwendet werden, wird dieser Fehler angezeigt.

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

Wenn Sie eine bereits bestehende CDN-Konfiguration für Ihre benutzerdefinierten Domain-Namen haben, wird auf den Seiten **Benutzerdefinierte Domain-Namen** und **Umgebung** eine informative Meldung angezeigt, die Sie auffordert, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

## Nächste Schritte {#next-steps}

Nachdem Sie den Domain-Status in Cloud Manager überprüft haben, müssen Sie die DNS-Einstellungen konfigurieren, indem Sie DNS-CNAME- oder APEX-Einträge hinzufügen, die auf AEM as a Cloud Service verweisen. Befolgen Sie das Dokument [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md), um mit der Einrichtung Ihres benutzerdefinierten Domain-Namens fortzufahren.
