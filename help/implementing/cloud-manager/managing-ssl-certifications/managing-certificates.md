---
title: Verwalten von SSL-Zertifikaten
description: Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer SSL-Zertifikate überprüfen und diese bearbeiten, ersetzen, aktualisieren und löschen können.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8e2fc0d4ee82e79d1a822a528b1a46acce3c192a
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 68%

---


# Verwalten von SSL-Zertifikaten {#managing-ssl-certificates}

Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer von Adobe verwalteten und der kundenseitig verwalteten SSL-Zertifikate überprüfen und diese löschen können. Kundenseitig verwaltete Zertifikate können Sie ebenfalls bearbeiten und aktualisieren (ersetzen).

## Überprüfen des Status von SSL-Zertifikaten {#checking-status-an-ssl-certificate}

Der Status Ihrer SSL-Zertifikate ist auf der Seite **SSL-Zertifikate** auf einen Blick ersichtlich.

| Status des SSL-Zertifikats | Beschreibung |
| --- | --- |
| Grün | Das Zertifikat ist ab dem aktuellen Datum mindestens 14 Tage gültig. |
| Orangefarben | Das Zertifikat läuft in weniger als 14 Tagen ab.<br>• Sie sollten sicherstellen, dass es einen Plan gibt, wann Sie Ihr Zertifikat erneuern und über die Cloud Manager-Benutzeroberfläche ersetzen, um mögliche Website-Zugriffe oder Ausfälle zu vermeiden.<br>• Cloud Manager sendet in der Benutzeroberfläche regelmäßige Benachrichtigungen, um Sie über einen bevorstehenden Zertifikatablauf zu informieren. |
| Rot | Das SSL-Zertifikat ist abgelaufen.<br>Siehe [Aktualisieren eines abgelaufenen kundenverwalteten SSL-Zertifikats](#update-ssl-certificate) oder [Löschen eines SSL-Zertifikats](#deleting-an-ssl-certificate). |

## Aktualisieren eines abgelaufenen kundenverwalteten SSL-Zertifikats {#update-ssl-certificate}

Wenn ein kundenseitig verwaltetes Zertifikat abläuft, funktionieren die Domains, die mit dem abgelaufenen Zertifikat verwendet werden, nicht mehr. Durch das Aktualisieren Ihrer Zertifikate wird sichergestellt, dass Ihre Domain weiterhin wie gewünscht funktioniert.

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**Aktualisieren eines abgelaufenen kundenverwalteten SSL-Zertifikats:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.
1. Navigieren Sie auf dem Bildschirm **Umgebungen** zum Bildschirm **SSL-Zertifikate**.
1. Klicken Sie in der Zeile des abgelaufenen, kundenseitig verwalteten Zertifikats, das Sie aktualisieren möchten, auf die Schaltfläche mit den Auslassungspunkten ganz rechts und wählen Sie dann **Anzeigen und aktualisieren** aus.

   ![Aktualisieren einer abgelaufenen kundenverwalteten SSL-Zertifizierung](/help/implementing/cloud-manager/assets/ssl/ssl-cert-update.png)

1. Gehen Sie im Dialogfeld **SSL-Zertifikat anzeigen und aktualisieren** wie folgt vor:

   * (Optional) Geben Sie im Feld **Zertifikatname** einen neuen Namen ein.
   * Fügen Sie im Feld **Zertifikat** den neuen Schlüssel des Zertifikatinhalts ein.
   * Aktualisieren Sie dieses Feld im Feld **Privater Schlüssel** nur, wenn Sie Änderungen am Zertifikat vorgenommen haben.
   * Fügen Sie im Feld **Zertifikatskette** (oder Vertrauenskette) die Zertifikatskette ein.

1. Klicken Sie auf **Aktualisieren** , um Ihre Änderungen zu speichern und sie automatisch anzuwenden. —>

## Ersetzen eines abgelaufenen kundenverwalteten SSL-Zertifikats {#replace-ssl-certificate}

Führen Sie dieselben Schritte aus, die unter [Aktualisieren eines abgelaufenen SSL-Zertifikats](#update-ssl-certificate) beschrieben werden, um ein abgelaufenes, vom Kunden verwaltetes SSL-Zertifikat zu ersetzen.

## Umbenennen eines von Adobe verwalteten SSL-Zertifikats (#rename-an-ssl-certificate)

Im Folgenden finden Sie einige Gründe, warum Sie möglicherweise ein SSL-Zertifikat umbenennen möchten:

* **Verbesserte Organisation**: Das Umbenennen des Zertifikats kann dazu beitragen, seinen Zweck zu verdeutlichen, z. B. die Identifizierung der Umgebung (z. B. Staging, Produktion) oder Domäne, für die es bestimmt ist.
* **Vermeiden von Verwirrung**: Wenn Sie mehrere Zertifikate verwalten, kann ein klarer, beschreibender Name dazu beitragen, Fehler zu verhindern, wie etwa das Anwenden des falschen Zertifikats auf die falsche Domäne.
* **Konformität und Prüfung**: Ordnungsgemäß benannte Zertifikate können aus Sicherheits- und Prüfgründen leichter verfolgt werden.

**So benennen Sie ein von Adobe verwaltetes SSL-Zertifikat um:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Klicken Sie oben links auf der Seite auf das Hamburger-Symbol, um das linke Navigationsmenü anzuzeigen.
1. Klicken Sie unter der Überschrift **Dienste** auf **SSL-Zertifikate**.
1. Klicken Sie auf der Seite **SSL-Zertifikate** am Ende einer Zeile, deren Zertifikat Sie umbenennen möchten, auf das Auslassungszeichen.
1. Klicken Sie auf **Umbenennen**.
1. Geben Sie im Dialogfeld **DV-Zertifikat umbenennen** im Textfeld **Zertifikatname** den neuen Namen des Zertifikats ein.
1. Klicken Sie auf **Umbenennen**.

## Löschen eines SSL-Zertifikats {#deleting-an-ssl-certificate}

Das Löschen von SSL-Zertifikaten, die von Adobe oder kundenseitig verwaltet werden, aus Cloud Manager ist eine dauerhafte Aktion, die nicht rückgängig gemacht werden kann. Als Best Practice empfiehlt Adobe, SSL-Dateien lokal zu speichern, bevor sie in Cloud Manager gelöscht werden.

>[!NOTE]
>
>Sie können ein von Adobe verwaltetes SSL-Zertifikat, dem mindestens eine aktive Domain zugeordnet ist, nicht löschen. Alle verknüpften aktiven Domains müssen vor dem Löschen des SSL-Zertifikats gelöscht werden. Weitere Information finden Sie unter [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md).

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**Löschen eines SSL-Zertifikats**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.
1. Navigieren Sie auf dem Bildschirm **Umgebungen** zum Bildschirm **SSL-Zertifikate**.
1. Klicken Sie in der Zeile des Zertifikats, das Sie löschen möchten, auf die Schaltfläche mit den Auslassungspunkten ganz rechts und wählen Sie dann **Löschen** aus.
Wenn die Schaltfläche „Löschen“ ein Informationssymbol aufweist, wie im folgenden Bild dargestellt, finden Sie weitere Informationen unter Hinweis oben.

   ![Schaltfläche „Löschen“ mit Informationssymbol](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete-infoicon.png)

1. Klicken Sie im Dialogfeld **SSL-Zertifikat löschen** auf **Löschen**, um den Löschvorgang zu bestätigen.
1. Führen Sie die Pipeline aus, um die Bereitstellung des gelöschten Zertifikats aufzuheben.

## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie bereits über eine CDN-Konfiguration für Ihr SSL-Zertifikat verfügen, zeigt die Seite **SSL-Zertifikate** eine informative Meldung an. In dieser wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und verwaltbar sind.

Die Nachricht verschwindet, nachdem alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert worden sind. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie unter [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) .

Eine ähnliche Meldung wird auch auf den Seiten **IP-Zulassungsliste** und **Umgebungen** für Umgebungen bereitgestellt, die bereits über CDN-Konfigurationen für IP-Zulassungslisten oder benutzerdefinierte Domänennamen verfügen.
