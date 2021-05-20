---
title: Überprüfen des IP-Zulassungslistenstatus
description: Überprüfen des IP-Zulassungslistenstatus
exl-id: 5ddea04f-3720-4663-90a8-9399019bfcbe
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 78%

---

# Überprüfen des IP-Zulassungslistenstatus {#check-allow-list-status}

Führen Sie die folgenden Schritte aus, um den Status von Aktualisierungen Ihrer IP-Zulassungsliste zu ermitteln:

1. Klicken Sie in der Tabelle auf der Seite **Umgebungen** auf das Statussymbol für die IP-Zulassungsliste und wählen Sie die Seite **IP-Zulassungslisten** aus.

1. Cloud Manager zeigt einen der folgenden Status an, wie im Abschnitt unten beschrieben.

## Status einer IP-Zulassungsliste {#status}

Die folgenden Statusdefinitionen werden in einer IP-Zulassungsliste angezeigt:

* **Angewandt**: Die IP-Zulassungsliste wurde erfolgreich auf Umgebungen angewendet.  Die Umgebungen und der Service sind wie in der folgenden Abbildung zu sehen.

* **Aktualisierung läuft**: Eine Aktualisierung der IP-Zulassungsliste, die einen oder mehrere Anwendungs- oder Aufhebungsvorgänge beinhalten kann, wird derzeit durchgeführt. Jedes „Anwenden“ und „Anwendung aufheben“ wird zusammen mit „Nicht gestartet“/„In Bearbeitung“/„Abgeschlossen“ oder „Fehlgeschlagen“ aufgelistet.

* **Fehlgeschlagen**: Ein oder mehrere Anwendungs- oder Aufhebungsvorgänge sind bei einer Aktualisierung fehlgeschlagen. Jedes „Anwenden“ und „Anwendung aufheben“ wird zusammen mit „Abgeschlossen“ oder „Fehlgeschlagen“ aufgelistet.
   * Der Status ist auch dann „Fehlgeschlagen“, wenn nur ein „Anwenden“/„Anwendung aufheben“ in der Aktualisierung fehlschlägt.
   * Der Status bleibt „Fehlgeschlagen“, bis alle Fehler behoben sind. Der Benutzer muss das Symbol „Erneut versuchen“ neben dem Status auswählen, um den Fehler zu beheben.
   * Der Benutzer kann die IP-Zulassungsliste nicht aktualisieren oder löschen, während der Status „Fehlgeschlagen“ ist.

* **Wird gelöscht**: Eine Löschanfrage wird gerade ausgeführt. Dies beinhaltet das Aufheben der Anwendung auf alle Services. Jedes „Anwendung aufheben“ wird zusammen mit „Nicht gestartet“/„In Bearbeitung“/„Abgeschlossen“ oder „Fehlgeschlagen“ aufgelistet.
Sobald der Löschvorgang abgeschlossen ist, wird die IP-Zulassungsliste:
   * nicht mehr in der Tabelle „IP-Zulassungsliste“ angezeigt,
   * auf keinen Service im Programm in Cloud Manager mehr angewendet.

* **Löschen fehlgeschlagen**: Ein oder mehrere Aufhebungsvorgänge sind bei einer Löschung fehlgeschlagen. Jedes „Anwendung aufheben“ wird zusammen mit „Abgeschlossen“ oder „Fehlgeschlagen“ aufgelistet.

   * Der Status ist auch dann „Löschen fehlgeschlagen“, wenn nur ein „Anwendung aufheben“ fehlschlägt.
   * Der Status bleibt „Löschen fehlgeschlagen“, bis alle Fehler behoben sind. Der Benutzer muss „Löschen“ aus dem Menü **...** ganz rechts in der Zeile in der Tabelle auswählen, um Fehler zu beheben.
   * Der Benutzer darf die IP-Zulassungsliste nicht aktualisieren, während der Status „Fehlgeschlagen“ ist.

## Vorbestehende CDN-Konfigurationen für IP-Zulassungslisten {#pre-existing-cdn}

Kunden mit Umgebungen, die bereits vorhandene CDN-Konfigurationen für IP-Zulassungslisten, SSL-Zertifikate oder benutzerdefinierte Domänennamen enthalten, sehen die folgende Meldung auf der Detailseite **IP-Zulassungsliste** und **Umgebung** . Die auf der Benutzeroberfläche angezeigte Nachricht verschwindet, sobald der Kunde alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche vollständig migriert hat. Es kann 1-2 Werktage dauern, bis die Nachricht ausgeblendet wird.

>[!NOTE]
>Um die bereits vorhandenen Konfigurationen anzuzeigen und zu verwalten, müssen sie über die Benutzeroberfläche hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) .

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
