---
title: Verwalten von IP-Zulassungslisten
description: Erfahren Sie, wie Sie den Status Ihrer IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
source-git-commit: 5311ba7f001201fc94c73fa52bc7033716c1ba78
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 57%

---

# Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

Erfahren Sie, wie Sie den Status Ihrer IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.

## Anzeigen und Aktualisieren von IP-Zulassungslisten {#update-ip-allow-lists}

Benutzerinnen und Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile für die IP-Zulassungslisten, die Sie anzeigen oder aktualisieren möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten am rechten Ende der Zeile.
1. Wählen Sie die Option **Anzeigen und aktualisieren** aus.
1. Die **Anzeigen und Aktualisieren** -Assistent zeigt den Namen, die IP-Adressen (oder Bereiche), die die Regel definieren, zusammen mit den Umgebungen und dem Dienst an, auf die die Regel angewendet wird.
1. Ändern Sie den Namen oder die IP-Adresse nach Bedarf und bestätigen Sie Ihre Übermittlung.

Wenn Sie einen neuen IP-Bereich zu einer IP-Zulassungsliste hinzufügen oder daraus entfernen, wird dieser automatisch auf alle entsprechenden Umgebungen/Services angewendet bzw. wird die Anwendung auf die entsprechenden Umgebungen/Services aufgehoben, auf die er zuvor angewendet war.

An einer IP-Zulassungsliste können keine Aktualisierungen vorgenommen werden, solange eine vorherige Aktualisierung läuft und noch nicht abgeschlossen ist.

## Überprüfen des Status von IP-Zulassungslisten {#check-allow-list-status}

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.

1. Klicken Sie in der Tabelle im Bildschirm **Umgebungen** auf das **Statussymbol** für die IP-Zulassungsliste und wählen Sie die Seite **IP-Zulassungslisten** aus.

1. Cloud Manager zeigt den Status der Zulassungsliste wie beschrieben an [im folgenden Abschnitt.](#status)

### Status einer IP-Zulassungsliste {#status}

[Bei der Überprüfung des Status von IP-Zulassungslisten](#check-allow-list-status) können sie einen der folgenden Werte aufweisen.

* **Angewendet** – Die IP-Zulassungsliste wurde erfolgreich auf eine oder mehrere Umgebungen angewendet.

* **Aktualisieren** - Es wird eine Aktualisierung der IP-Zulassungsliste durchgeführt, die eine oder mehrere Anwendungen oder die Aufhebung der Anwendung der Liste umfassen kann.

   * Jede Anwendung/Aufhebung wird zusammen mit dem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen** aufgeführt.

* **Fehlgeschlagen** - Ein oder mehrere Anwendungs- oder Aufheben der Anwendung eines Updates sind fehlgeschlagen.
   * Jede Anwendung und jede Aufhebung der Anwendung wird zusammen mit ihrem Status aufgelistet.
      * Der Status lautet **Fehlgeschlagen**, wenn eine Anwendung/Aufhebung bei der Aktualisierung fehlschlägt.
      * Der Status bleibt unverändert als **Fehlgeschlagen** bis alle Fehler behoben sind.
         * Wählen Sie die **Wiederholen** neben dem Status angezeigt, damit Sie den Fehler löschen können.
      * Eine IP-Zulassungsliste kann nicht mit einer **Fehlgeschlagen** Status.

* **Wird gelöscht** – Eine IP-Zulassungsliste wird derzeit gelöscht.
   * Das Löschen umfasst das Aufheben der Anwendung der Liste für alle Dienste.
   * Jede Nicht-Anwendung wird zusammen mit ihrem eigenen Status von **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen**.
   * Sobald der Löschvorgang abgeschlossen ist, wird die IP-Zulassungsliste:
      * nicht mehr in der Tabelle „IP-Zulassungsliste“ angezeigt,
      * auf keinen Service im Programm in Cloud Manager mehr angewendet.

* **Fehler löschen** - Eine oder mehrere Nicht-Anwendungen sind während eines Löschvorgangs fehlgeschlagen.

   * Jede Aufhebung der Anwendung wird zusammen mit dem Status aufgeführt **Fertig** oder **Fehlgeschlagen**.
   * Der Status wird **Fehler löschen** , wenn eine Nicht-Anwendung fehlschlägt.
   * Der Status bleibt unverändert als **Fehler löschen** bis alle Fehler behoben sind.
      * Auswählen **Löschen** aus dem Menü mit den Auslassungspunkten ganz rechts neben der Zeile in der Tabelle, damit Sie Fehler löschen können.
   * Eine IP-Zulassungsliste kann nicht aktualisiert werden, solange der Status **Fehlgeschlagen**.

## Löschen einer IP-Zulassungsliste {#delete-allow-list}

Benutzerinnen und Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile der IP-Zulassungsliste, die Sie löschen möchten.
1. Wählen Sie das Menü mit den Auslassungspunkten ganz rechts in der Zeile aus.
1. Klicken Sie auf **Löschen**.
1. Bestätigen Sie Ihre Übermittlung.

Durch das Löschen einer IP-Zulassungsliste wird die Anwendung automatisch von allen Diensten aufgehoben und aus der Tabelle gelöscht.

## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration für Ihre IP-Zulassungslisten verfügen, finden Sie eine informative Meldung auf der **IP-Zulassungsliste** Seite. In der Nachricht wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Siehe [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) für weitere Details.

Eine ähnliche Nachricht wird auch auf den Seiten **SSL-Zertifikate** und **Umgebungen** für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für SSL-Zertifikate oder benutzerdefinierte Domain-Namen angezeigt.
