---
title: Überprüfen des IP-Zulassungslistenstatus
description: Überprüfen des IP-Zulassungslistenstatus
translation-type: tm+mt
source-git-commit: e6a8d69ea87ac56a51cde2f131c4accff1bea527
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 81%

---


# Überprüfen des IP-Zulassungslistenstatus {#check-allow-list-status}

Führen Sie die folgenden Schritte aus, um den Status von Aktualisierungen Ihrer IP-Zulassungsliste zu ermitteln:

1. Klicken Sie auf das Statussymbol für die IP-Zulassungsliste in der Tabelle im Bildschirm **Umgebung** und wählen Sie **IP-Zulassungslisten**.

1. Cloud Manager zeigt einen der folgenden Status an, wie im Abschnitt unten beschrieben.

## Status einer IP-Zulassungsliste {#status}

Die folgenden Statusdefinitionen werden in einer IP-Zulassungsliste angezeigt:

* **Angewandt**: Die IP-Zulassungsliste wurde erfolgreich auf Umgebungen angewendet.  Die Umgebungen und der Dienst sind wie in der folgenden Abbildung zu sehen.

* **Aktualisierung läuft**: Eine Aktualisierung der IP-Zulassungsliste, die einen oder mehrere Anwendungs- oder Aufhebungsvorgänge beinhalten kann, wird derzeit durchgeführt. Jedes „Anwenden“ und „Anwendung aufheben“ wird zusammen mit „Nicht gestartet“/„In Bearbeitung“/„Abgeschlossen“ oder „Fehlgeschlagen“ aufgelistet.

* **Fehlgeschlagen**: Ein oder mehrere Anwendungs- oder Aufhebungsvorgänge sind bei einer Aktualisierung fehlgeschlagen. Jedes „Anwenden“ und „Anwendung aufheben“ wird zusammen mit „Abgeschlossen“ oder „Fehlgeschlagen“ aufgelistet.
   * Der Status ist auch dann „Fehlgeschlagen“, wenn nur ein „Anwenden“/„Anwendung aufheben“ in der Aktualisierung fehlschlägt.
   * Der Status &quot;Fehlgeschlagen&quot;bleibt bestehen, bis alle Fehler gelöscht wurden. Der Benutzer muss das Symbol zum Wiederholen neben dem Status auswählen, um den Fehler zu löschen.
   * Der Benutzer kann die IP-Zulassungsliste nicht aktualisieren oder löschen, während der Status „Fehlgeschlagen“ ist.

* **Wird gelöscht**: Eine Löschanfrage wird gerade ausgeführt. Dies beinhaltet das Aufheben der Anwendung auf alle Dienste. Jedes „Anwendung aufheben“ wird zusammen mit „Nicht gestartet“/„In Bearbeitung“/„Abgeschlossen“ oder „Fehlgeschlagen“ aufgelistet.
Sobald der Löschvorgang abgeschlossen ist, wird die IP-Zulassungsliste:
   * Wird nicht mehr in der Tabelle &quot;IP-Zulassungsliste&quot;angezeigt.
   * Auf keinen Dienst im Programm in Cloud Manager mehr angewendet werden.

* **Löschen fehlgeschlagen**: Ein oder mehrere Aufhebungsvorgänge sind bei einer Löschung fehlgeschlagen. Jedes „Anwendung aufheben“ wird zusammen mit „Abgeschlossen“ oder „Fehlgeschlagen“ aufgelistet.

   * Der Status ist auch dann „Löschen fehlgeschlagen“, wenn nur ein „Anwendung aufheben“ fehlschlägt.
   * Der Status bleibt „Löschen fehlgeschlagen“, bis alle Fehler behoben sind. Der Benutzer muss „Löschen“ aus dem Menü **...** ganz rechts in der Zeile in der Tabelle auswählen, um Fehler zu beheben.
   * Der Benutzer darf die IP-Zulassungsliste nicht aktualisieren, während der Status „Fehlgeschlagen“ ist.

