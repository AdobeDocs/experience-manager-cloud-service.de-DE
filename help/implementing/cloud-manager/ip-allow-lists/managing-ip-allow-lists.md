---
title: Verwalten von IP-Zulassungslisten
description: Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 100%

---

# Verwalten von IP-Zulassungslisten {#manage-ip-allow-lists}

Erfahren Sie, wie Sie den Status von IP-Zulassungslisten in Cloud Manager anzeigen, bearbeiten, löschen und überprüfen können.

## Anzeigen und Aktualisieren von IP-Zulassungslisten {#update-ip-allow-lists}

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können die folgenden Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

**So zeigen Sie IP-Zulassungslisten an und aktualisieren diese:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Klicken Sie auf der Seite **Übersicht** im Menü auf der linken Seite unter **Services** auf ![Aufgabenlistensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile für die IP-Zulassungslisten, die angezeigt oder aktualisiert werden sollen.
1. Klicken Sie ganz rechts in der Zeile auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Klicken Sie im Dropdown-Menü auf **Anzeigen/aktualisieren**.
Im Assistenten **IP-Zulassungsliste anzeigen und aktualisieren** werden der Name und die IP-Adressen (oder IP-Bereiche) angezeigt, die die Regel definieren, sowie die Umgebungen und Services, auf die die Regel angewendet wird.
1. Ändern Sie den Namen oder die IP-Adresse nach Bedarf.

   Wenn Sie einen neuen IP-Bereich zu einer IP-Zulassungsliste hinzufügen oder daraus entfernen, wird dieser automatisch auf alle entsprechenden Umgebungen/Dienste angewendet bzw. wird die Anwendung auf die entsprechenden Umgebungen/Dienste aufgehoben, auf die er zuvor angewendet wurde.

   Eine IP-Zulassungsliste kann nicht aktualisiert werden, wenn eine vorherige Aktualisierung läuft und noch nicht abgeschlossen ist.

1. Klicken Sie auf **Aktualisieren**.

## Überprüfen des Status von IP-Zulassungslisten {#check-allow-list-status}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Übersicht** im Menü auf der linken Seite unter **Services** auf ![Aufgabenlistensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP-Zulassungslisten**.

1. Bewegen Sie in der Spalte **Status** der Tabelle „IP-Zulassungslisten“ den Mauszeiger über eine (in Verwendung befindliche) grüne IP-Zulassungsliste, um zu sehen, wie ein oder mehrere Services darauf angewendet werden.

   Die in der Tabelle angezeigten Statuswerte haben folgende Bedeutungen:

   | Status einer IP-Zulassungsliste | Beschreibung |
   | --- | --- |
   | Angewendet | Die IP-Zulassungsliste wurde erfolgreich auf eine oder mehrere Umgebungen angewendet. |
   | Wird aktualisiert | Es wird eine Aktualisierung der IP-Zulassungsliste durchgeführt, die eine oder mehrere Anwendungen oder eine Aufhebung der Anwendung der Liste beinhalten kann. Jede Anwendung bzw. Aufhebung der Anwendung wird zusammen mit ihrem eigenen Status **Nicht gestartet**, **In Bearbeitung**, **Fertig** oder **Fehlgeschlagen** aufgeführt. |
   | Fehlgeschlagen | Ein oder mehrere Anwendungs- oder Aufhebungsvorgänge sind bei einer Aktualisierung fehlgeschlagen.<br>• Jede Anwendung bzw. Aufhebung der Anwendung wird zusammen mit dem Status aufgelistet.<br>• Der Status lautet **Fehlgeschlagen**, wenn eine Anwendung/Aufhebung der Anwendung bei der Aktualisierung fehlschlägt. Der Status bleibt **Fehlgeschlagen**, bis alle Fehler behoben sind.<br>• Klicken Sie auf das Symbol **Wiederholen** neben dem Status, um den Fehler zu löschen.<br>• Eine IP-Zulassungsliste mit dem Status **Fehlgeschlagen** kann nicht aktualisiert oder gelöscht werden. |
   | Wird gelöscht | Eine IP-Zulassungsliste wird gerade gelöscht.<br>• Das Löschen umfasst das Aufheben der Anwendung der Liste bei allen Services.<br>• Jede Aufhebung wird zusammen mit ihrem eigenen Status aufgeführt: **Nicht gestartet**, **In Bearbeitung**, **Abgeschlossen** oder **Fehlgeschlagen**.<br>• Wenn der Löschvorgang abgeschlossen ist, wird die IP-Zulassungsliste nicht in der Tabelle der IP-Zulassungslisten angezeigt. Die IP-Zulassungsliste wird zudem auf keinen Service im Programm in Cloud Manager angewendet. |
   | Löschen fehlgeschlagen | Eine oder mehrere Aufhebungen sind während eines Löschvorgangs fehlgeschlagen.<br>• Jede Aufhebung wird mit dem Status **Abgeschlossen** oder **Fehlgeschlagen** aufgeführt.<br>• Der Status ändert sich zu **Löschen fehlgeschlagen**, wenn eine Aufhebung fehlschlägt. Der Status bleibt **Löschen fehlgeschlagen**, bis alle Fehlschläge gelöscht sind. Klicken Sie ganz rechts in der Tabellenzeile auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und klicken Sie dann im Dropdown-Menü auf **Löschen**, um Fehler zu löschen.<br>• Eine IP-Zulassungsliste kann nicht aktualisiert werden, während der Status **Fehlgeschlagen** lautet. |

## Löschen einer IP-Zulassungsliste {#delete-allow-list}

Wenn Sie eine IP-Zulassungsliste löschen, wird die Anwendung der Liste automatisch bei allen Services aufgehoben und die Liste aus der Tabelle der IP-Zulassungsliste gelöscht.

Benutzende mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können die folgenden Schritte ausführen, um eine IP-Zulassungsliste anzuzeigen und zu aktualisieren.

**So löschen Sie eine IP-Zulassungsliste:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Klicken Sie auf der Seite **Überblick** im linken Seitenmenü unter **Services** auf ![Aufgabenlistensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP-Zulassungslisten**.
1. Identifizieren Sie die Zeile für die zu löschende IP-Zulassungsliste, klicken Sie ganz rechts in der Zeile auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und dann auf **Löschen**.
1. Klicken Sie im Dialogfeld **IP-Zulassungsliste löschen** auf **Löschen**.

## Bereits vorhandene CDN-Konfigurationen {#pre-existing-cdn}

Wenn Sie bereits eine bestehende CDN-Konfiguration (Content Delivery Network) für Ihre IP-Zulassungslisten haben, finden Sie eine informative Meldung auf der Seite **IP-Zulassungsliste**. In der Nachricht wird empfohlen, diese Konfigurationen über die Benutzeroberfläche hinzuzufügen, damit sie in Cloud Manager sichtbar und konfigurierbar sind.

Die Nachricht verschwindet, sobald alle bereits vorhandenen Umgebungskonfigurationen über die Benutzeroberfläche migriert wurden. Es kann 1–2 Werktage dauern, bis die Nachricht nicht mehr angezeigt wird.

Weitere Details finden Sie unter [Hinzufügen einer IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md).

Eine ähnliche Nachricht wird auch auf den Seiten **SSL-Zertifikate** und **Umgebungen** für Umgebungen mit bereits vorhandenen CDN-Konfigurationen für SSL-Zertifikate oder benutzerdefinierte Domain-Namen angezeigt.
