---
title: Verwalten von SSL-Zertifikaten
description: Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer SSL-Zertifikate überprüfen und diese bearbeiten, ersetzen, aktualisieren und löschen können.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
source-git-commit: 878381f9c5780864f218a00a272b1600d578dcca
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 30%

---

# Verwalten von SSL-Zertifikaten {#managing-ssl-certificates}

Erfahren Sie, wie Sie mit Cloud Manager den Status Ihrer SSL-Zertifikate überprüfen und diese bearbeiten, ersetzen, aktualisieren und löschen können.

## Überprüfen des Status von SSL-Zertifikaten {#checking-status-an-ssl-certificate}

Der Status Ihrer SSL-Zertifikate ist auf der SSL-Zertifikatsseite auf einen Blick ersichtlich.

* **Grün** - Dieser Status zeigt an, dass Ihr Zertifikat mindestens 60 Tage ab dem aktuellen Datum gültig ist.

* **Orange** - Dieser Status gibt an, dass Ihr Zertifikat in weniger als 60 Tagen ablaufen soll.
   * Sie sollten sicherzustellen und planen, Ihr Zertifikat zu erneuern und über die Cloud Manager-Benutzeroberfläche zu ersetzen, um mögliche Website-Zugriffe oder Ausfälle zu vermeiden.
   * Cloud Manager sendet in der Benutzeroberfläche regelmäßige Benachrichtigungen, um Sie über einen bevorstehenden Zertifikatablauf zu informieren.

* **Rot** - Dieser Status gibt an, dass das SSL-Zertifikat abgelaufen ist.

## Aktualisieren eines SSL-Zertifikats {#update-ssl-certificate}

Wenn ein Zertifikat abläuft, funktionieren die Domains, die mit dem abgelaufenen Zertifikat verwendet werden, nicht mehr. Durch die Aktualisierung Ihrer Zertifikate mit den folgenden Schritten wird sichergestellt, dass Ihre Domäne weiterhin wie gewünscht funktioniert.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Navigieren Sie zu **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.
1. Navigieren Sie zum **SSL-Zertifikate** -Bildschirm aus dem **Umgebungen** angezeigt.
1. Es wird eine Tabelle mit einer Zeile für jedes SSL-Zertifikat angezeigt, das erfolgreich in Ihrem Programm installiert wurde. Klicken Sie auf die Suchschaltfläche ganz rechts in der Zeile des Zertifikats, das Sie aktualisieren möchten, und wählen Sie **Anzeigen und Aktualisieren**.
1. Die Zertifikatdetails werden angezeigt und können aktualisiert werden.

>[!NOTE]
>
>Ein Benutzer muss Mitglied der **Business Owner** oder **Bereitstellungsmanager** Rolle, um ein SSL-Zertifikat in Cloud Manager zu aktualisieren.

## Ersetzen eines SSL-Zertifikats {#replace-ssl-certificate}

Ein SSL-Zertifikat kann durch die gleichen Schritte ersetzt werden, die im Abschnitt beschrieben werden. [Aktualisieren eines SSL-Zertifikats.](#update-ssl-certificate)

## Löschen eines SSL-Zertifikats {#deleting-an-ssl-certificate}

Das Entfernen von Zertifikaten aus Cloud Manager ist eine dauerhafte Aktion, die nicht rückgängig gemacht werden kann. Als Best Practice empfiehlt Adobe, SSL-Dateien lokal zu speichern, bevor sie in Cloud Manager gelöscht werden.

Cloud Manager ermöglicht es nicht, ein SSL-Zertifikat zu löschen, dem eine oder mehrere Domains zugeordnet sind. Alle verknüpften Domains müssen vor dem Löschen des SSL-Zertifikats gelöscht werden. Weitere Informationen finden Sie im Dokument . [Verwalten benutzerdefinierter Domänennamen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) , um mehr zu erfahren.

Führen Sie die folgenden Schritte aus, um ein SSL-Zertifikat zu löschen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Navigieren Sie zu **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.
1. Navigieren Sie zum **SSL-Zertifikate** -Bildschirm aus dem **Umgebungen** angezeigt.
1. Es wird eine Tabelle mit einer Zeile für jedes SSL-Zertifikat angezeigt, das erfolgreich in Ihrem Programm installiert wurde. Klicken Sie auf die Suchschaltfläche rechts in der Zeile des Zertifikats, das Sie löschen möchten, und wählen Sie **Löschen**.
1. Bestätigen Sie den Löschvorgang im **SSL-Zertifikat löschen** angezeigt.

>[!NOTE]
>
>Ein Benutzer muss Mitglied der **Business Owner** oder **Bereitstellungsmanager** Rolle, um ein SSL-Zertifikat in Cloud Manager zu löschen.

## Vorbestehende CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration für Ihr SSL-Zertifikat verfügen, enthält die **SSL-Zertifikate** -Seite, die Sie dazu ermutigt, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1-2 Werktage dauern, bis die Nachricht ausgeblendet wird.

Weitere Informationen finden Sie im Dokument . [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) für weitere Details.

Eine ähnliche Nachricht wird auch auf der **IP-Zulassungsliste** und **Umgebungen** Seiten für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für IP-Zulassungslisten oder benutzerdefinierte Domänennamen.
