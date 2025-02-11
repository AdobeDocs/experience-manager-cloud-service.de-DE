---
title: Verwalten von SSL-Zertifikaten
description: Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer SSL-Zertifikate überprüfen und diese bearbeiten, ersetzen, aktualisieren und löschen können.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f0cf9fa7da7e89d42ab90dee0e8400b26f004574
workflow-type: ht
source-wordcount: '1023'
ht-degree: 100%

---


# Verwalten von SSL-Zertifikaten {#managing-ssl-certificates}

Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer SSL-Zertifikate überprüfen und diese bearbeiten, ersetzen, aktualisieren und löschen können.

## Überprüfen des Status von SSL-Zertifikaten {#checking-status-an-ssl-certificate}

Cloud Manager bietet einen Überblick über den Status aller Zertifikate für Ihr Programm.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das Seitenmenü anzuzeigen.
1. Klicken Sie unter der Überschrift **Services** auf ![Sperrsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL-Zertifikate**.

Die Seite **SSL-Zertifikate** zeigt den Status Ihrer SSL-Zertifikate.

| Status des SSL-Zertifikats | Beschreibung |
| --- | --- |
| Grün | Das Zertifikat ist ab dem aktuellen Datum mindestens 14 Tage gültig. |
| Orangefarben | Das Zertifikat läuft in weniger als 14 Tagen ab.<br>• Sie sollten sicherstellen, dass es einen Plan gibt, wann Sie Ihr Zertifikat erneuern und über die Cloud Manager-Benutzeroberfläche ersetzen, um mögliche Website-Zugriffe oder Ausfälle zu vermeiden.<br>• Cloud Manager sendet in der Benutzeroberfläche regelmäßige Benachrichtigungen, um Sie über einen bevorstehenden Zertifikatablauf zu informieren. |
| Rot | Das SSL-Zertifikat ist abgelaufen.<br>Siehe [Aktualisieren eines abgelaufenen, kundenseitig verwalteten SSL-Zertifikats](#update-ssl-certificate) oder [Löschen eines SSL-Zertifikats](#deleting-an-ssl-certificate). |

## Aktualisieren eines abgelaufenen, kundenseitig verwalteten SSL-Zertifikats {#update-ssl-certificate}

Wenn ein kundenseitig verwaltetes Zertifikat abläuft, funktionieren die Domains, die mit dem abgelaufenen Zertifikat verwendet werden, nicht mehr. Durch das Aktualisieren Ihrer Zertifikate wird sichergestellt, dass Ihre Domain weiterhin wie gewünscht funktioniert.

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**Aktualisieren eines abgelaufenen, kundenseitig verwalteten SSL-Zertifikats:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das Seitenmenü anzuzeigen.
1. Klicken Sie unter der Überschrift **Services** auf ![Sperrsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL-Zertifikate**.
1. Klicken Sie in der Zeile des abgelaufenen, kundenseitig verwalteten Zertifikats, das Sie aktualisieren möchten, ganz rechts auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg). Klicken Sie anschließend auf **Anzeigen und aktualisieren**.

   ![Aktualisieren einer abgelaufenen, kundenseitig verwalteten SSL-Zertifizierung](/help/implementing/cloud-manager/assets/ssl/ssl-cert-update.png)

1. Gehen Sie im Dialogfeld **SSL-Zertifikat anzeigen und aktualisieren** wie folgt vor:

   * (Optional) Geben Sie im Feld **Zertifikatname** einen neuen Namen ein.
   * Fügen Sie im Feld **Zertifikat** den neuen Schlüssel des Zertifikatinhalts ein.
   * Aktualisieren Sie dieses Feld im Feld **Privater Schlüssel** nur, wenn Sie Änderungen am Zertifikat vorgenommen haben.
   * Fügen Sie im Feld **Zertifikatskette** (oder Vertrauenskette) die Zertifikatskette ein.

1. Klicken Sie auf **Aktualisieren**, um Ihre Änderungen zu speichern und sie automatisch anzuwenden.


>[!NOTE]
>
>Wenn zwei oder mehr SAN-Zertifikate denselben SAN-Domain-Eintrag abdecken und eines der Zertifikate aktualisiert wird, installiert das System das aktualisierte Zertifikat für die Domain.
>
>Weitere Informationen finden Sie unter [Fehlerbehebung bei SSL-Zertifikatproblemen](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md#wrong-san-cert).

## Ersetzen eines abgelaufenen, kundenseitig verwalteten SSL-Zertifikats {#replace-ssl-certificate}

Führen Sie dieselben Schritte aus, die unter [Aktualisieren eines abgelaufenen SSL-Zertifikats](#update-ssl-certificate) beschrieben sind, um ein abgelaufenes, kundenseitig verwaltetes SSL-Zertifikat zu ersetzen.

## Umbenennen eines von Adobe verwalteten SSL-Zertifikats (#rename-an-ssl-certificate)

Im Folgenden finden Sie einige Gründe, aus denen Sie möglicherweise ein SSL-Zertifikat umbenennen möchten:

* **Verbesserte Organisation**: Das Umbenennen des Zertifikats kann dazu beitragen, seinen Zweck zu verdeutlichen, z. B. die Identifizierung der Umgebung (z. B. Staging, Produktion) oder der Domain, für die es bestimmt ist.
* **Vermeiden von Verwirrung**: Wenn Sie mehrere Zertifikate verwalten, kann ein klarer, beschreibender Name dazu beitragen, Fehler zu verhindern, wie etwa das Anwenden des falschen Zertifikats auf die falsche Domain.
* **Konformität und Auditing**: Das Verfolgen ordnungsgemäß benannter Zertifikate aus Sicherheits- und Audit-Gründen ist leichter.

**So benennen Sie ein von Adobe verwaltetes SSL-Zertifikat um:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das Seitenmenü anzuzeigen.

1. Klicken Sie unter der Überschrift **Services** auf ![Sperrsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL-Zertifikate**.

1. Klicken Sie auf der Seite **SSL-Zertifikate** auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren **von Adobe verwaltetes** Zertifikat umbenannt werden soll.

1. Klicken Sie im Dropdown-Menü auf **Umbenennen**.

1. Geben Sie im Dialogfeld **DV-Zertifikat umbenennen** den neuen Namen des Zertifikats in das Feld **Zertifikatname** ein. 

1. Klicken Sie auf **Umbenennen**.


## Löschen eines SSL-Zertifikats {#deleting-an-ssl-certificate}

Das Löschen von SSL-Zertifikaten, die von Adobe oder kundenseitig verwaltet werden, aus Cloud Manager ist eine dauerhafte Aktion, die nicht rückgängig gemacht werden kann. Als Best Practice empfiehlt Adobe, SSL-Dateien lokal zu speichern, bevor sie in Cloud Manager gelöscht werden.

>[!NOTE]
>
>Sie können ein von Adobe verwaltetes SSL-Zertifikat, dem mindestens eine aktive Domain zugeordnet ist, nicht löschen. Alle verknüpften aktiven Domains müssen vor dem Löschen des SSL-Zertifikats gelöscht werden. Weitere Information finden Sie unter [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md).

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**Löschen eines SSL-Zertifikats**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das Seitenmenü anzuzeigen.

1. Klicken Sie unter der Überschrift **Services** auf ![Sperrsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL-Zertifikate**.

1. Klicken Sie auf der Seite „SSL-Zertifikate“ ganz rechts in der Tabellenzeile des zu löschenden Zertifikats auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und dann auf **Löschen**.

   Wenn die Schaltfläche **Löschen** ein Informationssymbol aufweist, wie in der folgenden Abbildung dargestellt, finden Sie weitere Informationen im Hinweis oben.

   ![Schaltfläche „Löschen“ mit Informationssymbol](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete-infoicon.png)

1. Klicken Sie im Dialogfeld **SSL-Zertifikat löschen** auf **Löschen**, um den Löschvorgang zu bestätigen.

1. Führen Sie die Pipeline aus, um die Bereitstellung des gelöschten Zertifikats aufzuheben.


## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie bereits über eine CDN-Konfiguration für Ihr SSL-Zertifikat verfügen, zeigt die Seite **SSL-Zertifikate** eine informative Meldung an. In dieser wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und verwaltbar sind.

Die Nachricht verschwindet, nachdem alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert worden sind. Es kann einen bis zwei Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Details finden Sie unter [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).

Eine ähnliche Nachricht wird auch auf den Seiten **IP-Zulassungsliste** und **Umgebungen** für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für IP-Zulassungslisten oder benutzerdefinierte Domain-Namen gezeigt.
