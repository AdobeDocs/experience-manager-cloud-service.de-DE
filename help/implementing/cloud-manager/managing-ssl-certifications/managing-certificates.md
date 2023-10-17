---
title: Verwalten von SSL-Zertifikaten
description: Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer SSL-Zertifikate überprüfen und diese bearbeiten, ersetzen, aktualisieren und löschen können.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 95%

---


# Verwalten von SSL-Zertifikaten {#managing-ssl-certificates}

Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer SSL-Zertifikate überprüfen und diese bearbeiten, ersetzen, aktualisieren und löschen können.

## Überprüfen des Status von SSL-Zertifikaten {#checking-status-an-ssl-certificate}

Der Status Ihrer SSL-Zertifikate ist auf der SSL-Zertifikatsseite auf einen Blick ersichtlich.

* **Grün**: Dieser Status zeigt an, dass Ihr Zertifikat ab dem aktuellen Datum mindestens 60 Tage gültig ist.

* **Orange**: Dieser Status gibt an, dass Ihr Zertifikat in weniger als 60 Tagen ablaufen wird.
   * Sie sollten sicherstellen und planen, Ihr Zertifikat zu erneuern und über die Cloud Manager-Benutzeroberfläche zu ersetzen, um mögliche Website-Zugriffe oder Ausfälle zu vermeiden.
   * Cloud Manager sendet in der Benutzeroberfläche regelmäßige Benachrichtigungen, um Sie über einen bevorstehenden Zertifikatablauf zu informieren.

* **Rot**: Dieser Status gibt an, dass das SSL-Zertifikat abgelaufen ist.

## Aktualisieren eines SSL-Zertifikats {#update-ssl-certificate}

Wenn ein Zertifikat abläuft, funktionieren die Domains, die mit dem abgelaufenen Zertifikat verwendet werden, nicht mehr. Durch die Aktualisierung Ihrer Zertifikate mit den folgenden Schritten wird sichergestellt, dass Ihre Domain weiterhin wie gewünscht funktioniert.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.
1. Gehen Sie auf der Seite **Umgebungen** zum Bildschirm **SSL-Zertifikate**.
1. Es wird eine Tabelle mit einer Zeile für jedes SSL-Zertifikat angezeigt, das erfolgreich in Ihrem Programm installiert wurde. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile des Zertifikats, das Sie aktualisieren möchten, und wählen Sie **Anzeigen und aktualisieren**.
1. Die Zertifikatdetails werden angezeigt und können geändert werden.
1. Führen Sie die Pipeline aus, um das aktualisierte Zertifikat bereitzustellen.

>[!NOTE]
>
>Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um ein SSL-Zertifikat in Cloud Manager zu aktualisieren.

## Ersetzen eines SSL-Zertifikats {#replace-ssl-certificate}

Ein SSL-Zertifikat kann durch Befolgen der gleichen Schritte, die im Abschnitt [Aktualisieren eines SSL-Zertifikats](#update-ssl-certificate) beschrieben werden, ersetzt werden.

## Löschen eines SSL-Zertifikats {#deleting-an-ssl-certificate}

Das Entfernen von Zertifikaten aus Cloud Manager ist eine dauerhafte Aktion, die nicht rückgängig gemacht werden kann. Als Best Practice empfiehlt Adobe, SSL-Dateien lokal zu speichern, bevor sie in Cloud Manager gelöscht werden.

Cloud Manager ermöglicht es nicht, ein SSL-Zertifikat zu löschen, dem eine oder mehrere Domains zugeordnet sind. Alle verknüpften Domains müssen vor dem Löschen des SSL-Zertifikats gelöscht werden. Weitere Informationen finden Sie unter [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md).

Gehen Sie wie folgt vor, um ein SSL-Zertifikat zu löschen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.
1. Gehen Sie auf der Seite **Umgebungen** zum Bildschirm **SSL-Zertifikate**.
1. Es wird eine Tabelle mit einer Zeile für jedes SSL-Zertifikat angezeigt, das erfolgreich in Ihrem Programm installiert wurde. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile des Zertifikats, das Sie löschen möchten, und klicken Sie auf **Löschen**.
1. Bestätigen Sie den Löschvorgang im Dialogfeld **SSL-Zertifikat löschen**.
1. Führen Sie die Pipeline aus, um die Bereitstellung des gelöschten Zertifikats aufzuheben.

>[!NOTE]
>
>Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um ein SSL-Zertifikat in Cloud Manager zu löschen.

## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration für Ihr SSL-Zertifikat verfügen, finden Sie auf der Seite **SSL-Zertifikate** eine informative Nachricht, die Sie dazu ermutigt, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Details finden Sie unter [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).

Eine ähnliche Nachricht wird auch auf den Seiten **IP-Zulassungsliste** und **Umgebungen** für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für IP-Zulassungslisten oder benutzerdefinierte Domain-Namen gezeigt.
