---
title: Überprüfen des Domain-Namensstatus
description: Erfahren Sie, wie Sie überprüfen können, ob Cloud Manager Ihren benutzerdefinierten Domain-Namen erfolgreich bestätigt hat.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: d9e067ec7aa9226721853a3e35a8863445a5002e
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 89%

---


# Überprüfen des Domain-Namensstatus {#check-status}

Erfahren Sie, wie Sie überprüfen können, ob Cloud Manager Ihren benutzerdefinierten Domain-Namen erfolgreich bestätigt hat.

## Überprüfen des Status eines benutzerdefinierten Domain-Namens {#how-to}

Bevor Sie den Status Ihres Domain-Namens in Cloud Manager überprüfen, stellen Sie sicher, dass Sie bereits ein kundenseitig verwaltetes SSL-Zertifikat (OV/EV) für Ihre benutzerdefinierte Domain hinzugefügt haben, wie unter [Hinzufügen eines kundenseitig verwalteten SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md##add-customer-managed-ssl-cert) beschrieben.

**So überprüfen Sie den Status eines benutzerdefinierten Domain-Namens:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Seitenmenü auf **Domain-Einstellungen**.

1. Klicken Sie auf das Symbol **Status**, um den Domain-Namen zu sehen.

Das Statusdetail wird angezeigt. Ihre benutzerdefinierte Domain kann verwendet werden, wenn der Status **Domain überprüft und bereitgestellt** angezeigt wird. Weitere Informationen zu den verschiedenen Status und ihren Bedeutungen finden Sie im [nächsten Abschnitt](#statuses).

>[!NOTE]
>
>Bei Verwendung eines *von Adobe verwalteten SSL-Zertifikats (DV)* mit der Domain löst Cloud Manager automatisch eine Überprüfung aus, wenn Sie beim [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) im Dialogfeld „Domain verifizieren“ auf **Überprüfen** klicken.
>
>Wenn Sie ein **kundenseitig verwaltetes SSL-Zertifikat (OV/EV)** verwenden möchten, wird Ihre Domain überprüft, *nachdem* Sie [das OV/EV-SSL-Zertifikat hinzugefügt haben](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).


## Überprüfungsstatus {#statuses}

Cloud Manager überprüft die Eigentümerschaft der Domain über das kundenseitig verwaltete SSL-Zertifikat (OV/EV). Wenn dies abgeschlossen ist, wird eine der folgenden Statusmeldungen angezeigt:

| Status | Beschreibung |
| --- | --- |
| Domain-Überprüfung fehlgeschlagen | Das kundenseitig verwaltete EV/OV-Zertifikat fehlt entweder oder wird mit Fehlern erkannt.<br> Befolgen Sie die Anweisungen in der Statusmeldung, um das Problem zu beheben. Wenn Sie bereit sind, müssen Sie das Symbol zum **erneuten Überprüfen** neben dem Status auswählen. |
| Überprüfung des Domain-Namens in Bearbeitung | Die Überprüfung läuft.<br>Dieser Status wird in der Regel angezeigt, nachdem Sie das Symbol **Erneut überprüfen** neben dem Status ausgewählt haben. Die DNS-Überprüfung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern. |
| Überprüft. Bereitstellung fehlgeschlagen | Die Überprüfung des EV/OV-Zertifikats war erfolgreich, aber die CDN-Bereitstellung ist fehlgeschlagen.<br>Wenden Sie sich in einem solchen Fall an den Adobe-Support. |
| Domain überprüft und bereitgestellt | Dieser Status gibt an, dass Ihr benutzerdefinierter Domain-Name verwendet werden kann.<br>An dieser Stelle steht Ihr benutzerdefinierter Domain-Name zum Testen und Verweisen auf den Domain-Namen von Cloud Manager bereit. Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |
| Wird gelöscht | Die Löschung eines benutzerdefinierten Domain-Namens wird durchgeführt. |
| Löschen fehlgeschlagen | Die Löschung eines benutzerdefinierten Domain-Namens ist fehlgeschlagen und muss wiederholt werden.<br>Weitere Information finden Sie unter [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md). |


## Fehler bei Domain-Namen {#domain-error}

Im Folgenden finden Sie einige häufige Fehler bei der Überprüfung des Domain-Namens und dafür gängige Lösungen.

### Fehler „Domain nicht installiert“ {#domain-not-installed}

<!-- This error may occur during domain validation of the EV/OV certificate even after you have checked that the certificate has been updated appropriately. -->

Wenn Sie eine Domain-Zuordnung in Cloud Manager hinzufügen, kann die folgende Fehlermeldung auftreten:

*Die Domain ist bereits in einem Fastly-Konto installiert. Entfernen Sie sie zuerst von dort, bevor Sie sie zu Cloud Service hinzufügen.*

Diese Meldung weist darauf hin, dass die Domain derzeit mit einem anderen Fastly-Konto verknüpft ist - in der Regel außerhalb der Kontrolle von Adobe. Um fortzufahren, muss die Domain vom anderen Konto getrennt werden, bevor sie zur von Adobe verwalteten Cloud Service hinzugefügt werden kann. Dieses Problem tritt normalerweise auf, wenn dieselbe Domain bereits einer anderen Herkunft in einer Nicht-Adobe Fastly-Konfiguration zugeordnet ist.

#### Fehlerursache {#cause}

Fastly beschränkt eine Domain auf das ursprünglich registrierte Konto; für andere Konten muss die Berechtigung zur Registrierung einer Subdomain angefordert werden. Darüber hinaus ermöglicht Fastly es Ihnen nur, eine Apex-Domain und zugehörige Subdomains einem Fastly-Service und -Konto zuzuweisen. Wenn Sie über ein vorhandenes Fastly-Konto verfügen, das denselben Namen und dieselbe Subdomain verknüpft, die für Ihre AEM as a Cloud Service-Domains verwendet werden, wird dieser Fehler angezeigt.

#### Fehlerbehebung {#resolution}

Der Fehler wird wie folgt behoben:

* Entfernen Sie die Apex- und Subdomains aus dem vorhandenen Konto, bevor Sie die Domain in Cloud Manager installieren.

* Verwenden Sie diese Option, um die Apex-Domain und alle Subdomains mit dem AEM as a Cloud Service Fastly-Konto zu verknüpfen. Weitere Informationen finden Sie in der [Fastly-Dokumentation unter Arbeiten mit Domains](https://docs.fastly.com/en/guides/working-with-domains).

* Wenn Ihre Apex-Domain über mehrere Subdomains für AEM as a Cloud Service und AEM-fremde Sites verfügt, die mit verschiedenen Fastly-Konten verknüpft sein müssen, versuchen Sie, die Domain in Cloud Manager zu installieren. Dieser Vorgang hilft bei der Verwaltung von Subdomain-Verbindungen über verschiedene Fastly-Konten hinweg. Falls die Domain-Installation fehlschlägt, erstellen Sie bei Fastly ein Kunden-Support-Ticket, damit Adobe in Ihrem Namen bei Fastly nachhaken kann.

>[!TIP]
>
>Die Lösung von Problemen bei der Domain-Delegation mit Fastly dauert normalerweise 1 bis 2 Werktage. Daher wird empfohlen, die Domains rechtzeitig vor dem Tag ihrer Live-Schaltung zu installieren.

>[!NOTE]
>
>Leiten Sie das DNS Ihrer Site nicht an die IPs von AEM as a Cloud Service weiter, wenn die Domain nicht erfolgreich installiert wurde.

## Bereits vorhandene CDN-Konfigurationen für benutzerdefinierte Domain-Namen {#pre-existing-cdn}

Wenn Sie bereits über eine CDN(Content Delivery Network)-Konfiguration für Ihre benutzerdefinierten Domain-Namen verfügen, wird auf den Seiten **Individuelle Domain-Namen** und **Umgebung** eine informative Meldung angezeigt. In dieser wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager verwaltet und angezeigt werden können.

Die Nachricht verschwindet, nachdem alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert worden sind. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

## Nächste Schritte {#next-steps}

Nachdem Sie den Domain-Status in Cloud Manager überprüft haben, konfigurieren Sie die DNS-Einstellungen, indem Sie DNS-CNAME- oder APEX-Einträge hinzufügen, die auf AEM as a Cloud Service verweisen. Fahren Sie mit dem Dokument [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) fort, um die Einrichtung Ihres benutzerdefinierten Domain-Namens fortzusetzen.
