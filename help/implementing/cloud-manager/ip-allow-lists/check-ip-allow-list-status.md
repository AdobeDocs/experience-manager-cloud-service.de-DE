---
title: Überprüfen des IP-Zulassungslistenstatus
description: Überprüfen des IP-Zulassungslistenstatus
translation-type: tm+mt
source-git-commit: ddee11fdfa8cadfcd63472fd3c94cd8af555c856
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 85%

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

Kunden mit Umgebung, die bereits vorhandene CDN-Konfigurationen für IP-Zulassungslisten, SSL-Zertifikate oder benutzerdefinierte Domänennamen enthalten, sehen die folgende Meldung auf der Detailseite **IP-Zulassungsliste** und **Umgebung**.

![](/help/implementing/cloud-manager/assets/ip-allow-list-1.png)

>[!NOTE]
>Um die bereits vorhandenen Konfigurationen anzuzeigen und zu verwalten, müssen sie über die Benutzeroberfläche hinzugefügt werden, wie in der folgenden Abbildung dargestellt.

![](/help/implementing/cloud-manager/assets/ip-allow-list-2.png)

