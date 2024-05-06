---
title: Verwalten von IP-Zulassungslisten
description: Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
source-git-commit: d1b2226a1deec2e71056c43c84672cb4a358bc8c
workflow-type: ht
source-wordcount: '789'
ht-degree: 100%

---

# Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.

## Anzeigen und Aktualisieren von IP-Zulassungslisten {#update-ip-allow-lists}

Benutzende mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile für die IP-Zulassungslisten, die angezeigt oder aktualisiert werden sollen.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten am rechten Ende der Zeile.
1. Wählen Sie die Option **Anzeigen und aktualisieren** aus.
1. Der Assistent **Anzeigen und aktualisieren** zeigt den Namen und die IP-Adressen (oder Bereiche) an, die die Regel definieren, sowie die Umgebungen und Services, auf die die Regel angewendet wird.
1. Ändern Sie den Namen oder die IP-Adresse nach Bedarf und bestätigen Sie Ihre Übermittlung.

Wenn Sie einen neuen IP-Bereich zu einer IP-Zulassungsliste hinzufügen oder daraus entfernen, wird dieser automatisch auf alle entsprechenden Umgebungen/Services angewendet bzw. wird die Anwendung auf die entsprechenden Umgebungen/Services aufgehoben, auf die er zuvor angewendet wurde.

Eine IP-Zulassungsliste kann nicht aktualisiert werden, wenn eine vorherige Aktualisierung läuft und noch nicht abgeschlossen ist.

## Überprüfen des Status von IP-Zulassungslisten {#check-allow-list-status}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie in der Tabelle im Bildschirm **Umgebungen** auf das **Statussymbol** für die IP-Zulassungsliste und wählen Sie die Seite **IP-Zulassungslisten** aus.

1. Cloud Manager zeigt den Status der Zulassungsliste an, wie [im folgenden Abschnitt](#status) beschrieben.

### Status einer IP-Zulassungsliste {#status}

[Bei der Überprüfung des Status von IP-Zulassungslisten](#check-allow-list-status) können diese einen der folgenden Werte aufweisen.

* **Angewendet**: Die IP-Zulassungsliste wurde erfolgreich auf eine oder mehrere Umgebungen angewendet.

* **Wird aktualisiert**: Es wird eine Aktualisierung der IP-Zulassungsliste durchgeführt, die eine oder mehrere Anwendungen oder eine Aufhebung der Anwendung der Liste beinhalten kann.

   * Jede Anwendung bzw. Aufhebung der Anwendung wird zusammen mit dem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen** aufgeführt.

* **Fehlgeschlagen**: Ein oder mehrere Anwendungs- oder Aufhebungsvorgänge sind bei einem Update fehlgeschlagen.
   * Jede Anwendung bzw. Aufhebung der Anwendung wird zusammen mit dem Status aufgelistet.
      * Der Status lautet **Fehlgeschlagen**, wenn eine Anwendung bzw. Aufhebung bei der Aktualisierung fehlschlägt.
      * Der Status bleibt **Fehlgeschlagen**, bis alle Fehler behoben sind.
         * Wählen Sie das Symbol **Wiederholen** neben dem Status, um den Fehler zu löschen.
      * Eine IP-Zulassungsliste mit dem Status **Fehlgeschlagen** kann nicht aktualisiert oder gelöscht werden.

* **Wird gelöscht**: Eine IP-Zulassungsliste wird derzeit gelöscht.
   * Das Löschen umfasst das Aufheben der Anwendung der Liste bei allen Diensten.
   * Jede Aufhebung wird zusammen mit ihrem eigenen Status aufgeführt: **Nicht gestartet**, **In Bearbeitung**, **Fertig**, oder **Fehlgeschlagen**.
   * Bei Abschluss des Löschvorgangs:
      * Die IP-Zulassungsliste wird nicht in der Tabelle der IP-Zulassungsliste angezeigt.
      * Die IP-Zulassungsliste wird auf keinen Service im Programm in Cloud Manager angewendet.

* **Löschen fehlgeschlagen**: Eine oder mehrere Aufhebungen sind während eines Löschvorgangs fehlgeschlagen.

   * Jede Aufhebung wird mit dem Status **Fertig** oder **Fehlgeschlagen** aufgeführt.
   * Der Status wird zu **Löschen fehlgeschlagen**, wenn eine Aufhebung fehlschlägt.
   * Der Status bleibt **Löschen fehlgeschlagen**, bis alle Fehlschläge gelöscht sind.
      * Wählen Sie **Löschen** aus dem Menü mit den Auslassungspunkten ganz rechts in der Tabellenzeile, damit Sie alle Fehler löschen können.
   * Eine IP-Zulassungsliste kann nicht aktualisiert werden, solange sie den Status **Fehlgeschlagen** aufweist.

## Löschen einer IP-Zulassungsliste {#delete-allow-list}

Benutzende mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile der IP-Zulassungsliste, die gelöscht werden soll.
1. Wählen Sie das Menü mit den Auslassungspunkten ganz rechts in der Zeile aus.
1. Klicken Sie auf **Löschen**.
1. Bestätigen Sie Ihre Übermittlung.

Das Löschen einer IP-Zulassungsliste hebt automatisch ihre Anwendung von allen Diensten auf und löscht sie aus der Tabelle.

## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie eine bereits bestehende CDN-Konfiguration für Ihre IP-Zulassungslisten haben, ist eine entsprechende Informationsmeldung auf der Seite **IP-Zulassungsliste** vorhanden. In der Nachricht wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie unter [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md).

Eine ähnliche Nachricht wird auch auf den Seiten **SSL-Zertifikate** und **Umgebungen** für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für SSL-Zertifikate oder benutzerdefinierte Domain-Namen angezeigt.
