---
title: Verwalten von SSL-Zertifikaten
description: Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer SSL-Zertifikate überprüfen und diese bearbeiten, ersetzen, aktualisieren und löschen können.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: d2f05915c0bf0af073db7f070b83f13aeae55252
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 14%

---


# SSL-Zertifikate verwalten {#managing-ssl-certificates}

Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer von Adobe verwalteten und kundenverwalteten SSL-Zertifikate überprüfen und wie Sie diese löschen können. Für kundenverwaltete Zertifikate können Sie sie auch bearbeiten und aktualisieren (ersetzen).

## Überprüfen des Status von SSL-Zertifikaten {#checking-status-an-ssl-certificate}

Der Status Ihrer SSL-Zertifikate kann auf einen Blick von der Seite **SSL-Zertifikate** aus verstanden werden.

| Status des SSL-Zertifikats | Beschreibung |
| --- | --- |
| Grün | Das Zertifikat ist mindestens 14 Tage ab dem aktuellen Datum gültig. |
| Orangefarben | Das Zertifikat läuft in weniger als 14 Tagen ab.<br> ・ Stellen Sie sicher, dass Sie planen, Ihr Zertifikat zu erneuern und es über die Cloud Manager-Benutzeroberfläche zu ersetzen, um möglichen Site-Zugriff oder -Ausfällen vorzubeugen.<br> ・ Cloud Manager sendet regelmäßige Benachrichtigungen in der Benutzeroberfläche, um Sie vor einem bevorstehenden Zertifikatablauf zu warnen. |
| Rot | Das SSL-Zertifikat ist abgelaufen.<br>Siehe [Aktualisieren eines abgelaufenen kundenverwalteten SSL-Zertifikats](#update-ssl-certificate) oder [Löschen eines SSL-Zertifikats](#deleting-an-ssl-certificate). |

## Aktualisieren eines abgelaufenen kundenverwalteten SSL-Zertifikats {#update-ssl-certificate}

Wenn ein vom Kunden verwaltetes Zertifikat abläuft, funktionieren alle Domänen, die mit dem abgelaufenen Zertifikat verwendet werden, nicht mehr. Durch die Aktualisierung Ihrer Zertifikate wird sichergestellt, dass Ihre Domäne weiterhin wie gewünscht funktioniert.

Ein Benutzer muss Mitglied der Rolle **Business Owner** oder **Deployment Manager** sein, um diese Aufgabe abzuschließen.

**Aktualisieren eines abgelaufenen kundenverwalteten SSL-Zertifikats:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.
1. Navigieren Sie im Bildschirm **Umgebungen** zum Bildschirm **SSL-Zertifikate** .
1. Klicken Sie in der Zeile des abgelaufenen kundenverwalteten Zertifikats, das Sie aktualisieren möchten, auf die Suchschaltfläche ganz rechts und wählen Sie dann **Ansicht und Aktualisieren** aus.

   ![Aktualisieren einer abgelaufenen kundenverwalteten SSL-Zertifizierung](/help/implementing/cloud-manager/assets/ssl/ssl-cert-update.png)

1. Gehen Sie im Dialogfeld **SSL-Zertifikat anzeigen und aktualisieren** wie folgt vor:

   * (Optional) Geben Sie im Feld **Zertifikatname** einen neuen Namen ein.
   * Fügen Sie im Feld **Zertifikat** den neuen Zertifikatinhaltsschlüssel ein.
   * Aktualisieren Sie dieses Feld im Feld **Privater Schlüssel** nur, wenn Sie Änderungen am Zertifikat vorgenommen haben.
   * Fügen Sie im Feld **Zertifikatskette** (oder Vertrauenskette) die Zertifikatskette ein.

1. Klicken Sie auf **Aktualisieren** , um Ihre Änderungen zu speichern und sie automatisch anzuwenden.

## Ersetzen eines abgelaufenen kundenverwalteten SSL-Zertifikats {#replace-ssl-certificate}

Führen Sie dieselben Schritte aus, die unter [Aktualisieren eines abgelaufenen SSL-Zertifikats](#update-ssl-certificate) beschrieben werden, um ein abgelaufenes, vom Kunden verwaltetes SSL-Zertifikat zu ersetzen.

## Löschen eines SSL-Zertifikats {#deleting-an-ssl-certificate}

Das Löschen von von Adobe verwalteten oder kundenverwalteten SSL-Zertifikaten aus Cloud Manager ist eine dauerhafte Aktion, die nicht rückgängig gemacht werden kann. Als Best Practice empfiehlt Adobe, SSL-Dateien lokal zu speichern, bevor sie in Cloud Manager gelöscht werden.

>[!NOTE]
>
>Sie können ein von Adobe verwaltetes SSL-Zertifikat, dem mindestens eine aktive Domäne zugeordnet ist, nicht löschen. Alle zugehörigen aktiven Domänen müssen vor dem Löschen des SSL-Zertifikats gelöscht werden. Weitere Informationen finden Sie unter [Verwalten benutzerdefinierter Domänennamen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) .

Ein Benutzer muss Mitglied der Rolle **Business Owner** oder **Deployment Manager** sein, um diese Aufgabe abzuschließen.

**So löschen Sie ein SSL-Zertifikat:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.
1. Navigieren Sie im Bildschirm **Umgebungen** zum Bildschirm **SSL-Zertifikate** .
1. Klicken Sie in der Zeile des Zertifikats, das Sie löschen möchten, auf die Suchschaltfläche ganz rechts und wählen Sie dann **Löschen** aus.
Wenn die Schaltfläche Löschen ein Informationssymbol aufweist, das im folgenden Bild dargestellt wird, finden Sie weitere Informationen unter Hinweis oben.

   ![Schaltfläche &quot;Löschen&quot;mit Informationssymbol](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete-infoicon.png)

1. Klicken Sie im Dialogfeld **SSL-Zertifikat löschen** auf **Löschen** , um den Löschvorgang zu bestätigen.
1. Führen Sie die Pipeline aus, um die Bereitstellung des gelöschten Zertifikats aufzuheben.

## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie bereits über eine CDN-Konfiguration für Ihr SSL-Zertifikat verfügen, zeigt die Seite **SSL-Zertifikate** eine informative Meldung an. Es wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und verwaltbar sind.

Die Nachricht verschwindet, nachdem alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie unter [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) .

Eine ähnliche Meldung wird auch auf den Seiten **IP-Zulassungsliste** und **Umgebungen** für Umgebungen bereitgestellt, die bereits über CDN-Konfigurationen für IP-Zulassungslisten oder benutzerdefinierte Domänennamen verfügen.
