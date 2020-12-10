---
title: 'Anzeigen des Aktualisieren und Ersetzen eines SSL-Zertifikats - Verwalten von SSL '
description: Anzeigen des Aktualisieren und Ersetzen eines SSL-Zertifikats - Verwalten von SSL-Zertifikaten
translation-type: tm+mt
source-git-commit: d5a119921a06ea06cbf2b95353083aa987869629
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# Anzeigen und Aktualisieren und Ersetzen eines SSL-Zertifikats {#view-update-replace-ssl-certificate}

## Anzeigen und Aktualisieren eines SSL-Zertifikats {#view-update}

Wann werden diese Optionen in der Benutzeroberfläche von Cloud Manager verwendet?

* Ein vorhandenes Zertifikat läuft bald ab. Der Benutzer hat das Zertifikat mit dem Zertifikatanbieter erneuert und möchte das vorhandene Zertifikat, das demnächst abläuft, ersetzen. Hinweis: Nur Benutzer mit den entsprechenden Berechtigungen können Updates vornehmen.
* Verwenden Sie das Menü **Ansicht &amp; Aktualisierung**, um die SSL-Zertifikatdetails einfach Ansicht.
* Alternativ dazu können Sie den Namen ändern, der für den Verweis auf ein Zertifikat verwendet wurde.
* Nur Benutzer mit den entsprechenden Berechtigungen können Updates vornehmen.


## Aktualisierung eines SSL-Zertifikats zum Ablaufzeitpunkt {#update-ssl-certificate}

Wenn ein Zertifikat abläuft, funktionieren Domänen, die mit dem abgelaufenen Zertifikat verwendet werden, nicht mehr. Um ein abgelaufenes Zertifikat zu aktualisieren, müssen Sie die folgenden Schritte ausführen. Dadurch wird sichergestellt, dass Ihre Domäne weiterhin wie gewünscht funktioniert. Das Hinzufügen eines neuen Zertifikats erfordert die Aktualisierung des benutzerdefinierten Domänennamens mit dem neuen Zertifikat, bevor die Domänen wie gewünscht funktionieren. Weitere Informationen finden Sie unter [Anzeigen und Aktualisieren und Ersetzen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.md)

Gehen Sie wie folgt vor, um ein SSL-Zertifikat zu aktualisieren:

>[!NOTE]
>Ein Benutzer muss sich in der Rolle &quot;Geschäftsinhaber&quot;oder &quot;Deployment Manager&quot;befinden, um ein SSL-Zertifikat in Cloud Manager aktualisieren zu können.

1. Navigieren Sie auf der Seite **Umgebung** zum Bildschirm &quot;SSL-Zertifikate&quot;.
1. Es wird eine Tabelle mit einer Zeile für jedes SSL-Zertifikat angezeigt, das erfolgreich in Ihrem Programm installiert wurde.
1. Die Menüoptionen für jede Zeile können Sie durch Auswahl der drei Schaltflächen ganz rechts in der gewünschten Zeile aufrufen.
1. Wählen Sie **Ansicht und Aktualisierung**. Die Zertifikatdetails können von hier aus angezeigt werden.

## Ersetzen eines SSL-Zertifikats {#replace-ssl-certificate}

Gehen Sie wie folgt vor, um ein SSL-Zertifikat zu ersetzen:

1. Navigieren Sie auf der Seite **Umgebung** zum Bildschirm &quot;SSL-Zertifikate&quot;.
1. Es wird eine Tabelle mit einer Zeile für jedes SSL-Zertifikat angezeigt, das erfolgreich in Ihrem Programm installiert wurde.
1. Die Menüoptionen für jede Zeile können Sie durch Auswahl der drei Schaltflächen ganz rechts in der gewünschten Zeile aufrufen.
1. Wählen Sie **Ansicht und Aktualisierung**.
1. Um das Zertifikat zu ersetzen, fügen Sie den neuen Inhalt in die entsprechenden Eingabefelder ein und klicken Sie auf **Speichern**. Eventuelle Fehler müssen behoben werden.

   Lesen Sie [Zertifikatfehler](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-error), um häufig auftretende Probleme zu beheben.