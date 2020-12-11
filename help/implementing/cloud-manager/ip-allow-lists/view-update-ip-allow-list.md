---
title: Anzeigen und Aktualisieren - IP-Zulassungslisten im Konnektivitäts-Manager
description: Anzeigen und Aktualisieren - IP-Zulassungslisten im Konnektivitäts-Manager
translation-type: tm+mt
source-git-commit: e6a8d69ea87ac56a51cde2f131c4accff1bea527
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Anzeigen und Aktualisieren einer IP-Zulassungsliste {#view-update}

Sie können IP-Zulassungslisten in den folgenden Szenarien Ansicht und Aktualisierung durchführen:

* Zum Ansicht- und Aktualisierungsmenü, um die Details einer oder mehrerer IP-Zulassungslisten einfach Ansicht.
* So bearbeiten Sie einen oder mehrere der folgenden Schritte:
   * IP-Bereiche in der Definition des Regelnamens
   * Freundlicher Name der IP-Zulassungsliste

## IP-Zulassungsliste {#update-ip-allow-lists} aktualisieren


Ein Benutzer, der sich in der Rolle &quot;Geschäftsinhaber&quot;oder &quot;Deployment Manager&quot;befindet, muss angemeldet sein, um eine IP-Zulassungsliste aktualisieren zu können.

>[!NOTE]
>Der Assistent für Ansicht und Aktualisierung zeigt den Namen, die IP- oder IP-Bereiche an, die die Regel definieren. Darüber hinaus werden die Umgebung und der Dienst angezeigt, auf die die Regel angewendet wird.

Gehen Sie wie folgt vor, um eine IP-Zulassungsliste zu aktualisieren:

1. Navigieren Sie zur Seite **IP-Zulassungslisten** im Bildschirm **Umgebung**.
1. Identifizieren Sie die Zeile, in der die IP-Zulassungsliste, die Sie Ansicht/Aktualisierung vornehmen möchten, aufgeführt ist.
1. Wählen Sie **...**-Menü am äußersten rechten Ende der Zeile.
1. Wählen Sie die Option **Ansicht und Aktualisieren**.
1. Nehmen Sie Änderungen am Namen oder an den IPs vor und bestätigen Sie Ihre Übermittlung.

## Wichtige Überlegungen beim Hinzufügen, Aktualisieren oder Entfernen von IP-Zulassungslisten {#considerations}

* Wenn Sie der IP-Zulassungsliste einen neuen IP-Bereich hinzufügen, wird dieser automatisch auf alle entsprechenden Umgebung angewendet.
* Wenn Sie einen IP-Bereich aus der IP-Zulassungsliste entfernen, wird die Anwendung automatisch von allen entsprechenden Umgebung-Diensten aufgehoben.
* Aktualisierungen an einer IP-Zulassungsliste können nicht vorgenommen werden, solange eine vorherige Aktualisierung noch nicht abgeschlossen ist.
* Eine IP-Zulassungsliste kann nicht aktualisiert werden, wenn Fehler aus einer vorherigen Aktualisierung vorliegen. Fehler müssen durch Wiederholung des Updates gelöscht werden.
Weitere Informationen finden Sie unter [IP-Zulassungsliste-Status](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md) überprüfen.