---
title: Verwalten von IP-Zulassungslisten
description: Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b9fb178760b74cb0e101506b6a9ff5ae30c18490
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 44%

---

# Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.

## Anzeigen und Aktualisieren von IP-Zulassungslisten {#update-ip-allow-lists}

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können die folgenden Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

**Anzeigen und Aktualisieren von IP-Zulassungslisten:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Klicken Sie auf der Seite **Übersicht** im Seitenbereich unter **Dienste** auf das Symbol ![Aufgabenliste](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile für die IP-Zulassungslisten, die angezeigt oder aktualisiert werden sollen.
1. Klicken Sie rechts in der Zeile auf das Symbol &quot;![Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Klicken Sie im Dropdown-Menü auf **Anzeigen und Aktualisieren**.
Das Dialogfeld **IP-Zulassungsliste anzeigen und aktualisieren** enthält den Namen, die IP-Adressen (oder Bereiche), die die Regel definieren, sowie die Umgebungen und Dienste, auf die die Regel angewendet wird.
1. Ändern Sie den Namen oder die IP-Adresse nach Bedarf.

   Wenn Sie einen neuen IP-Bereich zu einer IP-Zulassungsliste hinzufügen oder daraus entfernen, wird dieser automatisch auf alle entsprechenden Umgebungen/Dienste angewendet bzw. wird die Anwendung auf die entsprechenden Umgebungen/Dienste aufgehoben, auf die er zuvor angewendet wurde.

   Eine IP-Zulassungsliste kann nicht aktualisiert werden, wenn eine vorherige Aktualisierung läuft und noch nicht abgeschlossen ist.

1. Klicken Sie auf **Aktualisieren**.

## Überprüfen des Status von IP-Zulassungslisten {#check-allow-list-status}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Übersicht** im Seitenbereich unter **Dienste** auf das Symbol ![Aufgabenliste](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP-Zulassungslisten**.

1. Bewegen Sie in der Spalte **Status** der Tabelle &quot;IP-Zulassungslisten&quot;den Mauszeiger über eine (in Verwendung befindliche) grüne IP-Zulassungsliste, um zu sehen, wie ein oder mehrere Dienste darauf angewendet werden.

   Die in der Tabelle angezeigten Statuswerte haben folgende Bedeutungen:

   | Status der IP-Zulassungsliste | Beschreibung |
   | --- | --- |
   | Applied | Die IP-Zulassungsliste wurde erfolgreich auf eine oder mehrere Umgebungen angewendet. |
   | Wird aktualisiert | Es wird eine Aktualisierung der IP-Zulassungsliste durchgeführt, die eine oder mehrere Anwendungen oder die Aufhebung der Anwendung der Liste umfassen kann. Jede Anwendung bzw. Aufhebung der Anwendung wird zusammen mit dem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen** aufgeführt. |
   | Fehlgeschlagen | Ein oder mehrere Anwendungs- oder Aufheben der Anwendung eines Updates sind fehlgeschlagen.<br> ・ Jede Anwendung und jede Aufhebung der Anwendung wird zusammen mit ihrem Status aufgelistet.<br> ・ Der Status lautet **Fehlgeschlagen** , wenn eine Anwendung/Nicht-Anwendung in der Aktualisierung fehlschlägt. Der Status bleibt **Fehlgeschlagen**, bis alle Fehler behoben sind.<br> ・ Klicken Sie auf das Symbol **Wiederholen** neben dem Status, damit Sie den Fehler löschen können.<br> ・ Sie können eine IP-Zulassungsliste mit dem Status **Fehlgeschlagen** nicht aktualisieren oder löschen. |
   | Wird gelöscht | Eine IP-Zulassungsliste wird derzeit gelöscht.<br> ・ Löschen bedeutet, dass die Anwendung der Liste für alle Dienste aufgehoben wird.<br> ・ Jede Nicht-Anwendung wird zusammen mit ihrem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Abgeschlossen** oder **Fehlgeschlagen** aufgelistet.<br> ・ Wenn der Löschvorgang abgeschlossen ist, wird die IP-Zulassungsliste nicht in der Tabelle der IP-Zulassungsliste angezeigt. Außerdem wird die IP-Zulassungsliste auf keinen Dienst im Programm in Cloud Manager angewendet. |
   | Fehler löschen | Eine oder mehrere Aufhebungen schlugen während eines Löschvorgangs fehl.<br> ・ Jede Nicht-Anwendung wird zusammen mit dem Status **Abgeschlossen** oder **Fehlgeschlagen** aufgelistet.<br> ・ Der Status wird zu **Fehler beim Löschen** , wenn eine Nicht-Anwendung fehlschlägt. Der Status bleibt **Löschen fehlgeschlagen**, bis alle Fehlschläge gelöscht sind. Klicken Sie ganz rechts in der Tabellenzeile auf das Symbol &quot;![Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und klicken Sie dann im Dropdown-Menü auf &quot;**Löschen**&quot;, um einen Fehler zu löschen.<br> ・ Sie können eine IP-Zulassungsliste nicht aktualisieren, solange der Status **Fehlgeschlagen** lautet. |

## Löschen einer IP-Zulassungsliste {#delete-allow-list}

Wenn Sie eine IP-Zulassungsliste löschen, wird die Anwendung automatisch von allen Diensten aufgehoben und aus der Tabelle der IP-Zulassungsliste gelöscht.

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können die folgenden Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

**Löschen einer IP-Zulassungsliste:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Klicken Sie auf der Seite **Übersicht** im Seitenbereich unter **Dienste** auf das Symbol ![Aufgabenliste](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile für die IP-Zulassungsliste, die Sie löschen möchten, und klicken Sie dann am rechten Ende der Zeile auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) .
1. Klicken Sie im Dropdown-Menü auf **Löschen**.
1. Klicken Sie im Dialogfeld IP-Zulassungsliste löschen auf **Löschen**.

## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie bereits eine bestehende CDN-Konfiguration (Content Delivery Network) für Ihre IP-Zulassungslisten haben, finden Sie eine informative Meldung auf der Seite **IP-Zulassungsliste**. In der Nachricht wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Details finden Sie unter [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md).

Eine ähnliche Nachricht wird auch auf den Seiten **SSL-Zertifikate** und **Umgebungen** für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für SSL-Zertifikate oder benutzerdefinierte Domain-Namen angezeigt.
