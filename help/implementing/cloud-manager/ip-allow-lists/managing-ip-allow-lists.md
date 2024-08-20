---
title: Verwalten von IP-Zulassungslisten
description: Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f4c6331491bb08e81964476ad58065c1ee022967
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 49%

---

# Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.

## Anzeigen und Aktualisieren von IP-Zulassungslisten {#update-ip-allow-lists}

Ein Benutzer mit der Rolle **Business Owner** oder **Deployment Manager** kann diese Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile für die IP-Zulassungslisten, die Sie anzeigen oder aktualisieren möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten am rechten Ende der Zeile.
1. Wählen Sie die Option **Anzeigen und aktualisieren** aus.
1. Der Assistent **Anzeigen und aktualisieren** zeigt den Namen und die IP-Adressen (oder Bereiche) an, die die Regel definieren, sowie die Umgebungen und Services, auf die die Regel angewendet wird.
1. Ändern Sie den Namen oder die IP-Adresse nach Bedarf und bestätigen Sie Ihre Übermittlung.

Durch Hinzufügen oder Entfernen eines neuen IP-Bereichs zu einer IP-Zulassungsliste wird dieser automatisch auf alle entsprechenden Umgebungen/Dienste angewendet bzw. aufgehoben, auf die er zuvor angewendet wurde.

An einer IP-Zulassungsliste können keine Aktualisierungen vorgenommen werden, solange eine vorherige Aktualisierung läuft und noch nicht abgeschlossen ist.

## Überprüfen des Status von IP-Zulassungslisten {#check-allow-list-status}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie auf das Symbol **Status** für die IP-Zulassungsliste in der Tabelle auf dem Bildschirm **Umgebungen** und wählen Sie die Seite **IP-Zulassungslisten** aus.

1. Cloud Manager zeigt den Status der Zulassungsliste wie im folgenden Abschnitt ](#status) [beschrieben an.

### Status einer IP-Zulassungsliste {#status}

[Beim Überprüfen des Status von IP-Zulassungslisten](#check-allow-list-status) können sie einen der folgenden Werte aufweisen.

* **Angewandt** - Die IP-Zulassungsliste wurde erfolgreich auf eine oder mehrere Umgebungen angewendet.

* **Aktualisieren** - Es wird eine Aktualisierung der IP-Zulassungsliste durchgeführt, die eine oder mehrere Anwendungen oder Aufheben der Anwendung der Liste enthalten kann.

   * Jede Anwendung bzw. Aufhebung der Anwendung wird zusammen mit dem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen** aufgeführt.

* **Fehlgeschlagen**: Ein oder mehrere Anwendungs- oder Aufhebungsvorgänge sind bei einem Update fehlgeschlagen.
   * Jede Anwendung bzw. Aufhebung der Anwendung wird zusammen mit dem Status aufgelistet.
      * Der Status lautet **Fehlgeschlagen**, wenn eine Anwendung bzw. Aufhebung bei der Aktualisierung fehlschlägt.
      * Der Status bleibt **Fehlgeschlagen**, bis alle Fehler behoben sind.
         * Wählen Sie das Symbol **Wiederholen** neben dem Status, um den Fehler zu löschen.
      * Sie können eine IP-Zulassungsliste mit dem Status **Fehlgeschlagen** nicht aktualisieren oder löschen.

* **Löschen** - Ein Löschen einer IP-Zulassungsliste wird ausgeführt.
   * Das Löschen umfasst das Aufheben der Anwendung der Liste bei allen Diensten.
   * Jede Aufhebung wird zusammen mit ihrem eigenen Status aufgeführt: **Nicht gestartet**, **In Bearbeitung**, **Fertig**, oder **Fehlgeschlagen**.
   * Bei Abschluss des Löschvorgangs:
      * Die IP-Zulassungsliste wird nicht in der Tabelle der IP-Zulassungsliste angezeigt.
      * Die IP-Zulassungsliste wird auf keinen Dienst im Programm in Cloud Manager angewendet.

* **Löschen fehlgeschlagen**: Eine oder mehrere Aufhebungen sind während eines Löschvorgangs fehlgeschlagen.

   * Jede Aufhebung wird mit dem Status **Fertig** oder **Fehlgeschlagen** aufgeführt.
   * Der Status wird zu **Löschen fehlgeschlagen**, wenn eine Aufhebung fehlschlägt.
   * Der Status bleibt als **Fehler löschen** erhalten, bis alle Fehler gelöscht wurden. Klicken Sie ganz rechts in der Tabellenzeile auf das Suchmenü und dann auf **Löschen** , damit Sie alle Fehler löschen können.
   * Sie können eine IP-Zulassungsliste nicht aktualisieren, solange der Status **Fehlgeschlagen** lautet.

## IP-Zulassungsliste löschen {#delete-allow-list}

Ein Benutzer mit der Rolle **Business Owner** oder **Deployment Manager** kann diese Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zur Seite **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile der IP-Zulassungsliste, die Sie löschen möchten.
1. Wählen Sie das Menü mit den Auslassungspunkten ganz rechts in der Zeile aus.
1. Klicken Sie auf **Löschen**.
1. Bestätigen Sie Ihre Übermittlung.

Durch das Löschen einer IP-Zulassungsliste wird die Anwendung automatisch von allen Diensten aufgehoben und aus der Tabelle gelöscht.

## Vorbestehende CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie über eine bereits vorhandene CDN-Konfiguration (Content Delivery Network) für Ihre IP-Zulassungslisten verfügen, finden Sie auf der Seite **IP-Zulassungsliste** eine informative Meldung. In der Nachricht wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Informationen finden Sie unter [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) .

Eine ähnliche Nachricht wird auch auf den Seiten **SSL-Zertifikate** und **Umgebungen** für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für SSL-Zertifikate oder benutzerdefinierte Domain-Namen angezeigt.
