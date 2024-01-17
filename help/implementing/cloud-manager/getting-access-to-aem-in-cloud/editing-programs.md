---
title: Verwalten und Bearbeiten von Programmen
description: Erfahren Sie, wie Sie Ihre Produktions- und Sandbox-Programme bearbeiten, um ihre Optionen nach der Erstellung anzupassen.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: 0d60c19638707262dab7f290f84fa873b694bc22
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 49%

---


# Verwalten und Bearbeiten von Programmen {#editing-programs}

Die **Eigene Programme** bietet eine Übersicht über alle Programme, auf die Sie Zugriff haben. Wenn Sie ein einzelnes Programm auswählen, wird die **Programmübersicht** auf einen Blick Details zum Programm.

Aus dem **Programmübersicht**, können Benutzer mit den erforderlichen Berechtigungen [in Ihrer Organisation erstellte Produktionsprogramme](creating-production-programs.md) und [Sandbox-Programme, die in Ihrer Organisation erstellt wurden.](creating-sandbox-programs.md) Durch die Bearbeitung eines Programms haben Sie folgende Möglichkeiten:

* Hinzufügen der Sites-Lösung zu einem vorhandenen Programm mit Assets oder umgekehrt.
* Entfernen von Sites oder Assets aus einem vorhandenen Programm, das sowohl Sites als auch Assets umfasst.
* Hinzufügen einer zweiten, nicht verwendeten Lösungsberechtigung entweder für ein vorhandenes Programm oder als neues Programm.
* Löschen von Sandbox-Programmen.

## Berechtigungen {#permissions}

Sie müssen Mitglied der **Business Owner** Rolle zum Bearbeiten von Programmen oder Löschen von Sandbox-Programmen sowie zum Zugriff auf das Lizenz-Dashboard.

## Meine Programme {#my-programs}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Die **Eigene Programme** zeigt eine Liste aller Programme an, auf die Sie als Kacheln zugreifen können.

![Seite &quot;Meine Programme&quot;](/help/implementing/cloud-manager/assets/my-programs.png)

### Aktionsaufruf {#cta}

Oben auf der Seite befindet sich ein Aktionsaufruf, der für den Status Ihres Unternehmens relevant ist. Wenn Sie beispielsweise Ihre Programme erfolgreich eingerichtet haben, können Statistiken über Ihre Aktivitäten in den letzten 90 Tagen angezeigt werden, darunter:

* Anzahl der [Bereitstellungen](/help/implementing/cloud-manager/deploy-code.md)
* Anzahl der [Codequalitätsprobleme](/help/implementing/cloud-manager/code-quality-testing.md) identifiziert
* Anzahl der Builds

Oder wenn Sie gerade mit der Einrichtung Ihrer Organisation beginnen, gibt es Tipps zu den nächsten Schritten oder Dokumentationsressourcen.

### Registerkarte &quot;Programme&quot; {#programs-tab}

Die **Programme** enthält Karten, die für jedes Programm stehen, auf das Sie Zugriff haben. Tippen oder klicken Sie auf eine Karte, um auf die **Programmübersicht** auf der Seite des Programms für Details zum Programm.

Verwenden Sie die Sortieroptionen, um das benötigte Programm besser zu finden.

![Sortieroptionen](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* Sortieren nach
   * Erstellungsdatum (Standard)
   * Programmname
   * Status
* Aufsteigend (Standard)/Absteigend
* Rasteransicht (Standard)
* Listenansicht

### Lizenzregisterkarte {#license-tab}

Die **Lizenz** bietet Ihnen einen schnellen Zugriff auf die [Lizenz-Dashboard.](/help/implementing/cloud-manager/license-dashboard.md)

## Programmübersicht {#program-overview}

Nachdem Sie ein Programm aus dem **[Eigene Programme](#my-programs)** Seite, öffnet Cloud Manager die **Programmübersicht** Seite für das ausgewählte Programm.

![Seite &quot;Programmübersicht&quot;](/help/implementing/cloud-manager/assets/program-overview.png)

Tippen oder klicken Sie oben links auf der Seite auf den Programmnamen, um schnell zu einem anderen Programm oder zurück zum **[Eigene Programme](#my-programs)** Seite. Sie können auch [Bearbeiten des ausgewählten Programms](#editing) oder [ein Programm hinzufügen.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

![Programmumschalter](/help/implementing/cloud-manager/assets/program-switcher.png)

Der Aktionsaufruf am oberen Rand gibt Ihnen je nach Status Ihres Programms hilfreiche Informationen. Für ein neues Programm werden die nächsten Schritte sowie eine Erinnerung an ein &quot;Go-Live&quot;-Datum angezeigt. [wird während der Programmerstellung festgelegt.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md)

![Aktionsaufruf für ein neues Programm](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

Bei einem Live-Programm den Status Ihrer letzten Bereitstellung mit Links für Details und dem Beginn einer neuen Implementierung.

![Aktionsaufruf](/help/implementing/cloud-manager/assets/info-banner.png)

**Umgebungen** und **Pipelines** -Karten geben einen schnellen Überblick über beide innerhalb des ausgewählten Programms.

![Karten](/help/implementing/cloud-manager/assets/environments-pipelines.png)

Die **Leistung** -Karte einen Überblick über die **[CDN-Dashboard.](/help/implementing/cloud-manager/cdn-performance.md)**

![Leistungskarte](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

## Bearbeiten von Programmen {#editing}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Im **[Eigene Programme](#my-programs)** klicken Sie auf das Programm, das Sie bearbeiten möchten, um dessen Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Programms und anschließend auf **Programm bearbeiten**.

   ![Option „Programm bearbeiten“](assets/edit-program-overview.png)

1. Die Seite **Programm bearbeiten** wird geöffnet. Wählen Sie die Registerkarte **Allgemein** aus, um den Programmnamen und die Beschreibung zu bearbeiten.

   * Für ein Programm muss mindestens eine Lösung ausgewählt sein.

   ![Registerkarte „Allgemein“](assets/edit-program-prod1.png)

1. Wählen Sie die Registerkarte **Lösungen und Add-ons** aus, um die Lösungen für das Programm zu ändern.

   ![Lösungen auswählen](assets/edit-prg.png)

1. Klicken Sie auf den Pfeil vor dem Lösungsnamen, um optionale Add-ons anzuzeigen, z. B. die Add-on-Option **Commerce** unter **Sites**.

   ![Add-ons bearbeiten](assets/edit-program-add-on.png)

1. Auf der Registerkarte **Einstellungen für die Live-Schaltung** können Sie den geplanten Tag der Veröffentlichung für das Programm ändern.

   ![Live-Schaltungs-Einstellungen bearbeiten](assets/edit-program-go-live.png)

   * Dieses Datum dient nur zu Informationszwecken.  Dadurch wird das Go Live-Widget auf der Programmübersichtsseite ausgelöst. Im Gegenzug bietet es produktinterne Links zur Dokumentation der Best Practices in Adobe Experience Manager (AEM) as a Cloud Service, um sich an Ihrer Tour auszurichten und zu einem erfolgreichen Go Live-Erlebnis beizutragen.
   * Diese Registerkarte ist nicht für Sandbox-Programme verfügbar.

1. Wenn die erforderlichen Berechtigungen für das Programm verfügbar sind, zeigt die Registerkarte **Sicherheit** an, wo Sie die Sicherheitsoptionen für das Programm ändern können.

   ![Sicherheitseinstellungen bearbeiten](assets/edit-program-security.png)

   * HIPAA kann nach der [Programmerstellung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) weder aktiviert noch deaktiviert werden.
      * Hier finden Sie [weitere Informationen](https://www.adobe.com/go/hipaa-ready) zur Implementierung einer HIPAA-fähigen Lösung von Adobe.
   * Nach der Aktivierung kann der WAF-DDOS-Schutz durch Einrichten einer [produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) konfiguriert werden.

1. Klicken Sie auf **Aktualisieren**, um Ihre Änderungen am Programm zu speichern.

Jedes Mal, wenn ein Programm bearbeitet wird, einschließlich des Hinzufügens oder Entfernens einer Lösung oder eines Add-ons, werden diese Änderungen erst nach der nächsten Bereitstellung wirksam.

## Löschen von Sandbox-Programmen {#delete-sandbox-program}

Durch das Löschen eines Sandbox-Programms werden alle damit verbundenen Umgebungen und Pipelines entfernt.

>[!TIP]
>
>Benutzende mit den Rollen **Geschäftsinhaber** oder **Bereitstellungs-Manager** können alternativ ihre Produktions- und Staging-Umgebungen anstelle des gesamten Sandbox-Programms löschen.

Gehen Sie wie folgt vor, um ein Sandbox-Programm zu löschen:

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Im **[Eigene Programme](#my-programs)** klicken Sie auf das Programm, das Sie bearbeiten möchten, um dessen Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Programms und wählen Sie **Programm löschen**.

   ![Option „Programm löschen“](assets/delete-sandbox1.png)

Alternativ können Sie auf der Übersichtsseite von Cloud Manager auf der Karte Ihres Programms auf den Butten mit Auslassungspunkten klicken und anschließend auf **Programm löschen**.

![Sandbox aus Programmkarte löschen](assets/delete-sandbox2.png)

>[!NOTE]
>
>Es können nur Sandbox-Programme gelöscht werden. Produktionsprogramme können nicht gelöscht werden.
