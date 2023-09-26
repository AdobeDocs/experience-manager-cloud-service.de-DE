---
title: Verwalten von IP-Zulassungslisten
description: Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
source-git-commit: d67c5c9baafb9b7478f1d1c2ad924f5a8250a1ee
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 29%

---

# Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.

## Anzeigen und Aktualisieren von IP-Zulassungslisten {#update-ip-allow-lists}

Ein Benutzer im **Business Owner** oder **Bereitstellungsmanager** Rolle kann diesen Schritten folgen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile für die IP-Zulassungslisten, die Sie anzeigen oder aktualisieren möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten am rechten Ende der Zeile.
1. Wählen Sie die Option **Anzeigen und aktualisieren** aus.
1. Die **Anzeigen und Aktualisieren** -Assistent zeigt den Namen, die IP-Adressen (oder Bereiche), die die Regel definieren, zusammen mit den Umgebungen und Diensten an, auf die die Regel angewendet wird.
1. Ändern Sie den Namen oder die IP-Adresse nach Bedarf und bestätigen Sie Ihre Übermittlung.

Durch Hinzufügen oder Entfernen eines neuen IP-Bereichs zu einer IP-Zulassungsliste wird diese automatisch auf alle entsprechenden Umgebungen/Dienste angewendet bzw. deren Anwendung aufgehoben.

An einer IP-Zulassungsliste können keine Aktualisierungen vorgenommen werden, solange eine vorherige Aktualisierung läuft und noch nicht abgeschlossen ist.

## Überprüfen des Status von IP-Zulassungslisten {#check-allow-list-status}

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie auf **Status** Symbol für die IP-Zulassungsliste aus der Tabelle auf der **Umgebungen** und wählen Sie die **IP-Zulassungslisten** Seite.

1. Cloud Manager zeigt den Status der Zulassungsliste wie beschrieben an [im folgenden Abschnitt.](#status)

### Status einer IP-Zulassungsliste {#status}

[Bei der Überprüfung des Status von IP-auf die Zulassungsliste gesetzt werden,](#check-allow-list-status) sie können einen der folgenden Werte aufweisen.

* **Angewandt** - Die IP-Zulassungsliste wurde erfolgreich auf eine oder mehrere Umgebungen angewendet.

* **Aktualisieren** - Es wird eine Aktualisierung der IP-Zulassungsliste durchgeführt, die eine oder mehrere Anwendungen oder Aufheben der Anwendung der Liste enthalten kann.

   * Jede Anwendung/Aufhebung wird zusammen mit dem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen** aufgeführt.

* **Fehlgeschlagen** - Ein oder mehrere Anwendungs- oder Aufheben der Anwendung eines Updates sind fehlgeschlagen.
   * Jede Anwendung und jede Aufhebung der Anwendung wird zusammen mit ihrem Status aufgelistet.
      * Der Status lautet **Fehlgeschlagen**, wenn eine Anwendung/Aufhebung bei der Aktualisierung fehlschlägt.
      * Der Status bleibt unverändert als **Fehlgeschlagen** bis alle Fehler behoben sind.
         * Wählen Sie die **Wiederholen** neben dem Status angezeigt, damit Sie den Fehler löschen können.
      * Sie können eine IP-Zulassungsliste nicht mit einer **Fehlgeschlagen** -Status.

* **Löschen** - Das Löschen einer IP-Zulassungsliste wird ausgeführt.
   * Das Löschen umfasst das Aufheben der Anwendung der Liste bei allen Diensten.
   * Jede Nicht-Anwendung wird zusammen mit ihrem eigenen Status von **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen**.
   * Wenn der Löschvorgang abgeschlossen ist:
      * Die IP-Zulassungsliste wird nicht in der Tabelle der IP-Zulassungsliste angezeigt.
      * Die IP-Zulassungsliste wird auf keinen Dienst im Programm in Cloud Manager angewendet.

* **Fehler löschen** - Eine oder mehrere Nicht-Anwendungen sind während eines Löschvorgangs fehlgeschlagen.

   * Jede Aufhebung der Anwendung wird zusammen mit dem Status aufgeführt **Fertig** oder **Fehlgeschlagen**.
   * Der Status wird **Fehler löschen** , wenn eine Nicht-Anwendung fehlschlägt.
   * Der Status bleibt unverändert als **Fehler löschen** bis alle Fehler behoben sind.
      * Auswählen **Löschen** aus dem Menü mit den Auslassungspunkten ganz rechts neben der Zeile in der Tabelle, damit Sie Fehler löschen können.
   * Sie können eine IP-Zulassungsliste nicht aktualisieren, solange der Status **Fehlgeschlagen**.

## Löschen einer IP-Zulassungsliste {#delete-allow-list}

Ein Benutzer im **Business Owner** oder **Bereitstellungsmanager** Rolle kann diesen Schritten folgen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile der IP-Zulassungsliste, die Sie löschen möchten.
1. Wählen Sie das Menü mit den Auslassungspunkten ganz rechts in der Zeile aus.
1. Klicken Sie auf **Löschen**.
1. Bestätigen Sie Ihre Übermittlung.

Beim Löschen einer IP-Zulassungsliste wird die Anwendung automatisch von allen Diensten aufgehoben und aus der Tabelle gelöscht.

## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration für Ihre IP-Zulassungslisten verfügen, finden Sie eine informative Meldung zum **IP-Zulassungsliste** Seite. In der Nachricht wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Siehe [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) für weitere Details.

Eine ähnliche Nachricht wird auch auf den Seiten **SSL-Zertifikate** und **Umgebungen** für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für SSL-Zertifikate oder benutzerdefinierte Domain-Namen angezeigt.
