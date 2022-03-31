---
title: Verwalten von IP-Zulassungslisten
description: Erfahren Sie, wie Sie den Status Ihrer IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.
source-git-commit: 878381f9c5780864f218a00a272b1600d578dcca
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 14%

---


# Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

Erfahren Sie, wie Sie den Status Ihrer IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.

## Anzeigen und Aktualisieren von IP-Zulassungslisten {#update-ip-allow-lists}

Ein Benutzer im **Business Owner** oder **Bereitstellungsmanager** Rolle kann diese Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Navigieren Sie zu **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile für die IP-Zulassungslisten, die Sie anzeigen oder aktualisieren möchten.
1. Klicken Sie auf die Suchschaltfläche am rechten Ende der Zeile.
1. Wählen Sie die Option **Anzeigen und Aktualisieren** aus.
1. Die **Anzeigen und Aktualisieren** -Assistent zeigt den Namen, die IP-Adressen (oder Bereiche), die die Regel definieren, zusammen mit den Umgebungen und dem Dienst an, auf die die Regel angewendet wird.
1. Nehmen Sie Änderungen am Namen oder an der IP-Adresse vor und bestätigen Sie Ihre Übermittlung.

Durch Hinzufügen oder Entfernen eines neuen IP-Bereichs zu einer IP-Zulassungsliste wird dieser automatisch auf alle entsprechenden Umgebungen/Dienste angewendet bzw. aufgehoben, auf die er zuvor angewendet wurde.

An einer IP-Zulassungsliste können keine Aktualisierungen vorgenommen werden, solange eine vorherige Aktualisierung noch nicht abgeschlossen ist.

## Überprüfen des Status von IP-Zulassungslisten {#check-allow-list-status}

Führen Sie diese Schritte aus, um den Status von IP-Zulassungslisten zu überprüfen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zu **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.

1. Klicken Sie auf **Status** für die IP-Zulassungsliste aus der Tabelle auf der **Umgebungen** und wählen Sie **IP-Zulassungslisten** Seite.

1. Cloud Manager zeigt den Status der Zulassungsliste wie beschrieben an [im folgenden Abschnitt.](#status)

### Status einer IP-Zulassungsliste {#status}

[Bei der Überprüfung des Status von IP-Zulassungslisten](#check-allow-list-status) sie können einen der folgenden Werte aufweisen.

* **Angewandt** - Die IP-Zulassungsliste wurde erfolgreich auf eine oder mehrere Umgebungen angewendet.

* **Aktualisieren** - Es wird eine Aktualisierung der IP-Zulassungsliste durchgeführt, die eine oder mehrere Anwendungen oder die Aufhebung der Anwendung der Liste umfassen kann.

   * Jede Anwendung/Nicht-Anwendung wird zusammen mit ihrem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen**.

* **Fehlgeschlagen** - Ein oder mehrere Anwendungs- bzw. Aufheben der Anwendung eines Updates sind fehlgeschlagen.
   * Jede Anwendung und jede Aufhebung der Anwendung wird zusammen mit ihrem Status aufgelistet.
      * Der Status lautet **Fehlgeschlagen** wenn eine Anwendung/Nicht-Anwendung in der Aktualisierung fehlschlägt.
      * Der Status bleibt wie folgt **Fehlgeschlagen** bis alle Fehler behoben sind.
         * Sie müssen die **Wiederholen** neben dem Status, um den Fehler zu löschen.
      * Eine IP-Zulassungsliste kann nicht mit einer **Fehlgeschlagen** Status.

* **Löschen** - Eine IP-Zulassungsliste wird derzeit gelöscht.
   * Das Löschen umfasst das Rückgängigmachen der Anwendung der Liste bei allen Diensten.
   * Jede Nicht-Anwendung wird zusammen mit ihrem eigenen Status von **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen**.
   * Nach Abschluss des Löschvorgangs wird die IP-Zulassungsliste:
      * Wird nicht mehr in der Tabelle der IP-Zulassungsliste angezeigt.
      * auf keinen Service im Programm in Cloud Manager mehr angewendet.

* **Fehler löschen** - Eine oder mehrere Rückgängigmachungen schlugen während eines Löschvorgangs fehl.

   * Jede Nicht-Anwendung wird zusammen mit dem Status aufgeführt **Fertig** oder **Fehlgeschlagen**.
   * Der Status lautet **Fehler löschen** wenn eine Aufhebung der Anwendung fehlschlägt.
   * Der Status bleibt wie folgt **Fehler löschen** bis alle Fehler behoben sind.
      * Sie müssen **Löschen** aus dem Menü mit den Auslassungspunkten ganz rechts neben der Zeile in der Tabelle, um einen Fehler zu beheben.
   * Eine IP-Zulassungsliste kann nicht aktualisiert werden, während der Status **Fehlgeschlagen**.

## Löschen einer IP-Zulassungsliste {#delete-allow-list}

Ein Benutzer im **Business Owner** oder **Bereitstellungsmanager** Rolle kann diese Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Navigieren Sie zu **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile der IP-Zulassungsliste, die Sie löschen möchten.
1. Wählen Sie das Suchmenü am rechten unteren Rand der Zeile aus.
1. Klicken Sie auf **Löschen**.
1. Bestätigen Sie Ihre Übermittlung.

Durch das Löschen einer IP-Zulassungsliste wird die Anwendung automatisch von allen Diensten aufgehoben und aus der Tabelle gelöscht.

## Vorbestehende CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration für Ihre IP-Zulassungslisten verfügen, enthält die **IP-Zulassungsliste** -Seite, die Sie dazu ermutigt, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1-2 Werktage dauern, bis die Nachricht ausgeblendet wird.

Weitere Informationen finden Sie im Dokument . [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) für weitere Details.

Eine ähnliche Nachricht wird auch auf der **SSL-Zertifikate** und **Umgebungen** Seiten für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für SSL-Zertifikate oder benutzerdefinierte Domänennamen.
