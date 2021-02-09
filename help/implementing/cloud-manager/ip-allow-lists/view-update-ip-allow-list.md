---
title: Anzeigen und Aktualisieren - IP-Zulassungslisten in Cloud Manager
description: Anzeigen und Aktualisieren - IP-Zulassungslisten in Cloud Manager
translation-type: tm+mt
source-git-commit: 7fdfa626147a72f3d7fb98b89a19a871fc7a13ca
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 83%

---


# Anzeigen und Aktualisieren einer IP-Zulassungsliste {#view-update}

Sie können IP-Zulassungslisten in den folgenden Szenarien anzeigen und aktualisieren:

* Über das Menü „Anzeigen und aktualisieren“, um die Details einer oder mehrerer IP-Zulassungslisten anzuzeigen.
* Zum Bearbeiten eines oder mehrerer der folgenden Punkte:
   * IP-Bereiche in der Definition des Regelnamens
   * Anzeigename der Regel für die IP-Zulassungsliste

## Aktualisieren einer IP-Zulassungsliste {#update-ip-allow-lists}


Ein Benutzer mit der Rolle „Business Owner“ oder „Deployment Manager“ muss angemeldet sein, um eine IP-Zulassungsliste zu aktualisieren.

>[!NOTE]
>Der Assistent zum Anzeigen und Aktualisieren zeigt den Namen, die IPs oder die IP-Bereiche an, die die Regel definieren. Darüber hinaus werden die Umgebungen und der Service angezeigt, auf die die Regel angewendet wird.

Gehen Sie wie folgt vor, um eine IP-Zulassungsliste zu aktualisieren:

1. Navigieren Sie zur Seite **IP-Zulassungslisten** im Bildschirm **Umgebung**.
1. Geben Sie die Zeile an, in der die Regel der IP-Zulassungsliste aufgeführt ist, die Sie anzeigen/aktualisieren möchten.
1. Wählen Sie das Menü **...** ganz rechts in der Zeile aus.
1. Wählen Sie die Option **Ansicht und Aktualisieren**.
1. Nehmen Sie Änderungen am Namen oder an den IPs vor und bestätigen Sie Ihre Übermittlung.

## Wichtige Überlegungen beim Hinzufügen, Aktualisieren oder Entfernen von IP-Zulassungslisten {#considerations}

* Wenn Sie der IP-Zulassungsliste einen neuen IP-Bereich hinzufügen, wird dieser automatisch auf alle entsprechenden Umgebungen angewendet.
* Wenn Sie einen IP-Bereich aus der IP-Zulassungsliste entfernen, wird dieser automatisch von allen entsprechenden Umgebungs-Services entfernt.
* Eine IP-Zulassungsliste kann nicht aktualisiert werden, während eine vorherige Aktualisierung läuft und noch nicht abgeschlossen ist.
* Eine IP-Zulassungsliste kann nicht aktualisiert werden, wenn bei einer vorherigen Aktualisierung Fehler aufgetreten sind. Alle Fehler müssen behoben werden, indem versucht wird, das Update erneut auszuführen.
Weitere Informationen finden Sie unter [IP-Zulassungsliste-Status](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md) überprüfen.