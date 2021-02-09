---
title: 'Anzeigen, Aktualisieren und Ersetzen eines SSL-Zertifikats – Verwalten von SSL '
description: Anzeigen, Aktualisieren und Ersetzen eines SSL-Zertifikats – Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: b76a22469f248dde316dcaa514a906fe4361afd1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 76%

---


# Anzeigen und Aktualisieren und Ersetzen eines SSL-Zertifikats {#view-update-replace-ssl-certificate}

## Anzeigen und Aktualisieren eines SSL-Zertifikats {#view-update}

Wann werden diese Optionen in der Benutzeroberfläche von Cloud Manager verwendet?

* Ein vorhandenes Zertifikat läuft bald ab. Der Benutzer hat das Zertifikat beim Zertifikatanbieter erneuert und möchte das vorhandene Zertifikat, das demnächst abläuft, ersetzen. Hinweis: Nur Benutzer mit den entsprechenden Berechtigungen können Aktualisierungen vornehmen.
* Verwenden Sie das Menü **Ansicht &amp; Aktualisierung**, um die SSL-Zertifikatdetails einfach Ansicht.
* Alternativ können Sie von diesem Bildschirm aus den Namen ändern, der zur Referenzierung eines Zertifikats verwendet wurde.
* Nur Benutzer mit den entsprechenden Berechtigungen können Aktualisierungen vornehmen.


## Aktualisieren eines SSL-Zertifikats, das demnächst abläuft {#update-ssl-certificate}

Wenn ein Zertifikat abläuft, funktionieren die Domains, die mit dem abgelaufenen Zertifikat verwendet werden, nicht mehr. Um ein abgelaufenes Zertifikat zu aktualisieren, müssen Sie die folgenden Schritte ausführen. Dadurch wird sichergestellt, dass Ihre Domain weiterhin wie gewünscht funktioniert. Wenn Sie ein neues Zertifikat hinzufügen, müssen Sie den benutzerdefinierten Domain-Namen mit dem neuen Zertifikat aktualisieren, bevor die Domains wie gewünscht funktionieren. Weitere Informationen finden Sie unter [Anzeigen und Aktualisieren und Ersetzen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.md).

Gehen Sie wie folgt vor, um ein SSL-Zertifikat zu aktualisieren:

>[!NOTE]
>Ein Benutzer muss über die Rolle „Business Owner“ oder „Deployment Manager“ verfügen, um ein SSL-Zertifikat in Cloud Manager zu aktualisieren.

1. Navigieren Sie auf der Seite **Umgebungen** zum Bildschirm „SSL-Zertifikate“.
1. Es wird eine Tabelle mit einer Zeile für jedes SSL-Zertifikat angezeigt, das erfolgreich in Ihrem Programm installiert wurde.
1. Sie können auf die Menüoptionen für jede Zeile zugreifen, indem Sie die drei Schaltflächen ganz rechts in der gewünschten Zeile auswählen.
1. Wählen Sie **Ansicht und Aktualisierung**. Die Zertifikatdetails können von hier aus angezeigt werden.

## Ersetzen eines SSL-Zertifikats {#replace-ssl-certificate}

Gehen Sie wie folgt vor, um ein SSL-Zertifikat zu ersetzen:

1. Navigieren Sie auf der Seite **Umgebungen** zum Bildschirm „SSL-Zertifikate“.
1. Es wird eine Tabelle mit einer Zeile für jedes SSL-Zertifikat angezeigt, das erfolgreich in Ihrem Programm installiert wurde.
1. Sie können auf die Menüoptionen für jede Zeile zugreifen, indem Sie die drei Schaltflächen ganz rechts in der gewünschten Zeile auswählen.
1. Wählen Sie **Ansicht und Aktualisierung**.
1. Um das Zertifikat zu ersetzen, fügen Sie den neuen Inhalt in die entsprechenden Eingabefelder ein und klicken Sie auf **Speichern**. Dabei müssen Sie eventuell auftretende Fehler beheben.

   Lesen Sie [Zertifikatfehler](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-error), um häufig auftretende Probleme zu beheben.