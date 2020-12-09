---
title: IP-Zulassungslisten-Status überprüfen
description: IP-Zulassungslisten-Status überprüfen
translation-type: tm+mt
source-git-commit: b9b2591ce25040b108484984851308bc80eee958
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# IP-Zulassungsliste-Status {#check-allow-list-status} überprüfen

Gehen Sie wie folgt vor, um den Status der Aktualisierungen Ihrer IP-Zulassungsliste zu ermitteln:

1. Klicken Sie auf das Statussymbol für die IP-Zulassungsliste in der Tabelle auf Umgebung > IP-Zulassungsliste.

1. Cloud Manager zeigt einen der folgenden Status an, wie im folgenden Abschnitt beschrieben.

## Status einer IP-Zulassungsliste {#status}

Die folgenden Statusdefinitionen werden in einer IP-Zulassungsliste angezeigt:

* **Angewandt**: IP-Zulassungsliste wurde erfolgreich auf Umgebung angewendet.  Die Umgebung und der Dienst sind wie im folgenden Bild dargestellt zu sehen.

* **Aktualisieren**: Eine Aktualisierung der IP-Zulassungsliste, die eine oder mehrere Änderungen beinhalten kann, wird derzeit durchgeführt. Alle &quot;Anwenden&quot;und &quot;Rückgängig&quot;werden zusammen mit &quot;Nicht gestartet/In Bearbeitung/Abgeschlossen&quot;oder &quot;Fehlgeschlagen&quot;aufgelistet.

* **Fehlgeschlagen**: Ein oder mehrere Vorgänge zum Anwenden oder Aufheben der Anwendung bei einer Aktualisierung sind fehlgeschlagen. Alle &quot;Anwenden&quot;und &quot;Rückgängig&quot;werden zusammen mit &quot;Abgeschlossen&quot;oder &quot;Fehlgeschlagen&quot;aufgelistet.

   >[!NOTE]
   > * Der Status ist &quot;Fehlgeschlagen&quot;, auch wenn eine Anwendung/Aufhebung in der Aktualisierung fehlschlägt.
   >* Der Status &quot;Fehlgeschlagen&quot;bleibt bestehen, bis alle Fehler gelöscht wurden. Der Benutzer muss das Symbol &quot;Wiederholen&quot;neben dem Status auswählen, um den Fehler zu löschen.
   >* Der Benutzer kann die IP-Zulassungsliste nicht aktualisieren oder löschen, während der Status Fehlgeschlagen ist.


* **Löschen**: Die Löschanforderung wird ausgeführt. Dies bedeutet, dass alle Dienste nicht angewendet werden. Jede Aufhebung wird zusammen mit &quot;Nicht gestartet/Wird ausgeführt/Abgeschlossen&quot;oder &quot;Fehlgeschlagen&quot;aufgeführt.

   >[!NOTE]
   >Nach Abschluss des Löschvorgangs wird die IP-Zulassungsliste wie folgt ausgeführt:
   >* Wird nicht mehr in der Tabelle &quot;IP-Zulassungsliste&quot;angezeigt >* Auf keinen Dienst im Programm in Cloud Manager mehr angewendet


* **Löschen fehlgeschlagen**: Ein oder mehrere Vorgänge zum Rückgängigmachen der Anwendung bei einem Löschvorgang sind fehlgeschlagen. Jede Aufhebung wird zusammen mit &quot;Abgeschlossen&quot;oder &quot;Fehlgeschlagen&quot;angezeigt.

   >[!NOTE]
   >* Der Status &quot;Löschen fehlgeschlagen&quot;lautet auch dann, wenn ein Fehler beim Aufheben der Anwendung auftritt.
   >* Der Status &quot;Löschen fehlgeschlagen&quot;bleibt erhalten, bis alle Fehler gelöscht wurden. Der Benutzer muss in **die Option Löschen auswählen...**-Menü ganz rechts in der Zeile in der Tabelle, um Fehler zu löschen.
   >* Benutzer darf die IP-Zulassungsliste nicht aktualisieren, während der Status &quot;Fehlgeschlagen&quot;ist.


