---
title: Überprüfen des Domain-Namenstatus
description: Erfahren Sie, wie Sie überprüfen können, ob Cloud Manager Ihren benutzerdefinierten Domänennamen erfolgreich bestätigt hat.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 3ff7b76f7892269f6ca001ff2c079bc693c06d93
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 40%

---


# Überprüfen des Domänennamenstatus {#check-status}

Erfahren Sie, wie Sie überprüfen können, ob Cloud Manager Ihren benutzerdefinierten Domänennamen erfolgreich bestätigt hat.

## Voraussetzungen {#requirements}

Erfüllen Sie diese Anforderungen, bevor Sie den Status Ihres Domain-Namens in Cloud Manager überprüfen.

* Fügen Sie zunächst einen TXT-Eintrag für Ihre benutzerdefinierte Domäne hinzu, wie im Dokument [Benutzerdefinierten Domänennamen hinzufügen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) beschrieben.

## Prüfen Sie den Status Ihres benutzerdefinierten Domain-Namens. {#how-to}

Sie können den Status Ihres benutzerdefinierten Domänennamen in Cloud Manager ermitteln.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich auf **Domain-Einstellungen**.

1. Klicken Sie auf das Symbol **Status**, um den Domain-Namen zu sehen.

Das Statusdetail wird angezeigt. Ihre benutzerdefinierte Domain kann verwendet werden, wenn der Status **Domain überprüft und bereitgestellt** angezeigt wird. Weitere Informationen zu den verschiedenen Status und ihren Bedeutungen finden Sie im [nächsten Abschnitt](#statuses).

>[!NOTE]
>
>Cloud Manager überprüft die Trigger automatisch, wenn Sie im Überprüfungsschritt des Assistenten **Benutzerdefinierte Domäne hinzufügen** die Option **Erstellen** auswählen, wenn Sie [ einen neuen benutzerdefinierten Domänennamen zu Cloud Manager hinzufügen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Für spätere Überprüfungen müssen Sie das Symbol „Erneut überprüfen“ neben dem Status aktiv auswählen.

## Überprüfungsstatus {#statuses}

Cloud Manager überprüft den Domänenbesitz über den TXT-Wert [ und zeigt eine der folgenden Statusmeldungen an.](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

| Status | Beschreibung |
| --- | --- |
| Domain-Überprüfung fehlgeschlagen | Der TXT-Wert fehlt oder wird mit Fehlern erkannt.<br> Befolgen Sie die Anweisungen in der Statusmeldung, um das Problem zu beheben. Wenn Sie bereit sind, müssen Sie das Symbol zum **erneuten Überprüfen** neben dem Status auswählen. |
| Domänenüberprüfung läuft | Die Überprüfung wird durchgeführt.<br>Dieser Status wird normalerweise angezeigt, nachdem Sie das Symbol **Erneut überprüfen** neben dem Status ausgewählt haben. Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern. |
| Verifiziert - Bereitstellung fehlgeschlagen | Die TXT-Überprüfung war erfolgreich, aber die CDN-Bereitstellung schlug fehl.<br>Wenden Sie sich in solchen Fällen an Ihren Adobe-Support-Mitarbeiter. |
| Domain verifiziert und bereitgestellt | Dieser Status zeigt an, dass Ihr benutzerdefinierter Domänenname zur Verwendung bereit ist.<br>An dieser Stelle kann Ihr benutzerdefinierter Domänenname getestet werden und auf den Cloud Manager-Domänennamen verweisen. Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) . |
| Wird gelöscht | Das Löschen eines benutzerdefinierten Domain-Namens wird ausgeführt. |
| Löschen fehlgeschlagen | Das Löschen eines benutzerdefinierten Domänennamens ist fehlgeschlagen und muss erneut versucht werden.<br>Weitere Informationen finden Sie unter [Verwalten benutzerdefinierter Domänennamen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) . |


## Domain name errors {#domain-error}

Im Folgenden finden Sie einige häufige Fehler bei der Überprüfung des Domain-Namens und dafür gängige Lösungen.

### Fehler &quot;Domain not installed&quot; {#domain-not-installed}

Dieser Fehler kann bei der Domain-Validierung des TXT-Eintrags auftreten, selbst wenn Sie überprüft haben, dass der Datensatz ordnungsgemäß aktualisiert worden ist.

#### Fehlerursache {#cause}

Sperrt eine Domäne schnell für das Konto, das sie zuerst registriert, und andere Konten müssen die Berechtigung zur Registrierung einer Subdomain anfordern. Darüber hinaus ermöglicht Fastly es Ihnen nur, eine Apex-Domain und zugehörige Subdomains einem Fastly-Service und -Konto zuzuweisen. Wenn Sie über ein vorhandenes Fastly-Konto verfügen, das denselben Namen und dieselbe Subdomain verknüpft, die für Ihre AEM as a Cloud Service-Domains verwendet werden, wird dieser Fehler angezeigt.

#### Fehlerbehebung {#resolution}

Der Fehler wird wie folgt behoben:

* Entfernen Sie die Apex- und Subdomains aus dem vorhandenen Konto, bevor Sie die Domain in Cloud Manager installieren.

* Verwenden Sie diese Option, um die Apex-Domain und alle Subdomains mit dem AEM as a Cloud Service Fastly-Konto zu verknüpfen. Weitere Informationen finden Sie in der [Fastly-Dokumentation unter Arbeiten mit Domains](https://docs.fastly.com/en/guides/working-with-domains).

* Wenn Ihre Apex-Domäne über mehrere Subdomänen für AEM as a Cloud Service und Nicht-AEM-Sites verfügt, die eine Verknüpfung mit verschiedenen Schnellkonten herstellen müssen, versuchen Sie, die Domäne in Cloud Manager zu installieren. Dieser Prozess hilft bei der Verwaltung von Subdomain-Verbindungen über verschiedene Fastly-Konten hinweg. Wenn die Domain-Installation fehlschlägt, erstellen Sie ein Support-Ticket mit Fastly, damit Adobe schnell in Ihrem Namen folgen kann.

>[!TIP]
>
>Die Lösung von Problemen bei der Domain-Delegation mit Fastly dauert normalerweise 1 bis 2 Werktage. Daher wird dringend empfohlen, die Domains rechtzeitig vor ihrem Aufschaltdatum zu installieren.

>[!NOTE]
>
>Leiten Sie das DNS Ihrer Site nicht an die IPs von AEM as a Cloud Service weiter, wenn die Domain nicht erfolgreich installiert wurde.

## Vorhandene CDN-Konfigurationen für benutzerdefinierte Domänennamen {#pre-existing-cdn}

Wenn Sie bereits über eine CDN-Konfiguration für Ihre benutzerdefinierten Domänennamen verfügen, wird auf den Seiten **Benutzerdefinierte Domänennamen** und **Umgebung** eine informative Meldung angezeigt. Es wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager verwaltet und angezeigt werden können.

Die Nachricht verschwindet, nachdem alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) .

## Nächste Schritte {#next-steps}

Nachdem Sie Ihren Domänenstatus in Cloud Manager überprüft haben, konfigurieren Sie die DNS-Einstellungen, indem Sie DNS-, CNAME- oder APEX-Einträge hinzufügen, die auf AEM as a Cloud Service verweisen. Fahren Sie mit dem Dokument [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) fort, um mit der Einrichtung Ihres benutzerdefinierten Domänennamens fortzufahren.
