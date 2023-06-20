---
title: Verwalten von IP-Zulassungslisten
description: Erfahren Sie, wie Sie den Status Ihrer IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 92%

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
1. Der Assistent **Anzeigen und aktualisieren** zeigt den Namen, die IP-Adressen (oder Bereiche), die die Regel definieren, zusammen mit den Umgebungen und Services an, auf die die Regel angewendet wird.
1. Nehmen Sie Änderungen am Namen oder an den IP-Adressen vor und bestätigen Sie Ihre Übermittlung.

Wenn Sie einen neuen IP-Bereich zu einer IP-Zulassungsliste hinzufügen oder daraus entfernen, wird dieser automatisch auf alle entsprechenden Umgebungen/Services angewendet bzw. wird die Anwendung auf die entsprechenden Umgebungen/Services aufgehoben, auf die er zuvor angewendet war.

Eine IP-Zulassungsliste kann nicht aktualisiert werden, während eine vorherige Aktualisierung läuft und noch nicht abgeschlossen ist.

## Überprüfen des Status von IP-Zulassungslisten {#check-allow-list-status}

Führen Sie diese Schritte aus, um den Status von IP-Zulassungslisten zu überprüfen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.

1. Klicken Sie in der Tabelle im Bildschirm **Umgebungen** auf das **Statussymbol** für die IP-Zulassungsliste und wählen Sie die Seite **IP-Zulassungslisten** aus.

1. Cloud Manager zeigt den Status der Zulassungsliste wie [im folgenden Abschnitt](#status) beschrieben an 

### Status einer IP-Zulassungsliste {#status}

[Bei der Überprüfung des Status von IP-Zulassungslisten](#check-allow-list-status) können sie einen der folgenden Werte aufweisen.

* **Angewendet** – Die IP-Zulassungsliste wurde erfolgreich auf eine oder mehrere Umgebungen angewendet.

* **Wird aktualisiert** – Es wird eine Aktualisierung der IP-Zulassungsliste durchgeführt, bei der die Liste einmal oder mehrmals angewendet bzw. die Anwendung aufgehoben werden kann.

   * Jede Anwendung/Aufhebung wird zusammen mit dem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen** aufgeführt.

* **Fehlgeschlagen** – Ein oder mehrere Anwendungs- oder Aufhebungsvorgänge sind bei einer Aktualisierung fehlgeschlagen.
   * Jede Anwendung und Aufhebung wird zusammen mit dem Status aufgelistet.
      * Der Status lautet **Fehlgeschlagen**, wenn eine Anwendung/Aufhebung bei der Aktualisierung fehlschlägt.
      * Der Status bleibt **Fehlgeschlagen**, bis alle Fehler behoben sind.
         * Sie müssen das Symbol **Erneut versuchen** neben dem Status auswählen, um den Fehler zu beheben.
      * Eine IP-Zulassungsliste kann mit dem Status **Fehlgeschlagen** nicht aktualisiert oder gelöscht werden.

* **Wird gelöscht** – Eine IP-Zulassungsliste wird derzeit gelöscht.
   * Das Löschen umfasst das Aufheben der Anwendung der Liste bei allen Services.
   * Jede Aufhebung wird zusammen mit dem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen** aufgeführt.
   * Sobald der Löschvorgang abgeschlossen ist, wird die IP-Zulassungsliste:
      * nicht mehr in der Tabelle „IP-Zulassungsliste“ angezeigt,
      * auf keinen Service im Programm in Cloud Manager mehr angewendet.

* **Löschen fehlgeschlagen** – Eine oder mehrere Aufhebungen sind während eines Löschvorgangs fehlgeschlagen.

   * Jede Aufhebung wird zusammen mit dem Status **Fertig** oder **Fehlgeschlagen** aufgeführt.
   * Der Status wird **Fehler löschen** wenn eine Aufhebung der Anwendung fehlschlägt.
   * Der Status bleibt unverändert als **Fehler löschen** bis alle Fehler behoben sind.
      * Sie müssen **Löschen** aus dem Menü mit den Auslassungspunkten ganz rechts in der Zeile in der Tabelle auswählen, um Fehler zu beheben.
   * Eine IP-Zulassungsliste kann nicht aktualisiert werden, während der Status **Fehlgeschlagen** ist.

## Löschen einer IP-Zulassungsliste {#delete-allow-list}

Benutzerinnen und Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile der IP-Zulassungsliste, die Sie löschen möchten.
1. Wählen Sie das Menü mit den Auslassungspunkten ganz rechts in der Zeile aus.
1. Klicken Sie auf **Löschen**.
1. Bestätigen Sie Ihre Übermittlung.

Durch das Löschen einer IP-Zulassungsliste wird deren Anwendung automatisch von allen Services aufgehoben und sie wird aus der Tabelle gelöscht.

## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration für Ihre IP-Zulassungslisten verfügen, enthält die **IP-Zulassungsliste** -Seite, die Sie dazu ermutigt, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie im Dokument [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md).

Eine ähnliche Nachricht wird auch auf den Seiten **SSL-Zertifikate** und **Umgebungen** für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für SSL-Zertifikate oder benutzerdefinierte Domain-Namen angezeigt.
