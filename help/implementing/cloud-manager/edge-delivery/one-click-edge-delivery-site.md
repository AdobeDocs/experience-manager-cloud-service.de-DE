---
title: Erstellen einer Edge Delivery-Site in Cloud Manager mit einem Klick
description: Erfahren Sie, wie Sie mit einem Klick in Cloud Manager schnell eine Edge Delivery-Site erstellen können.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8034fc8454fca41c2430fa1179f80d2d2ab80563
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 71%

---


# Über die Erstellung einer Edge Delivery-Site in Cloud Manager mit einem Klick {#about-one-click-edge-delivery-site}

Der mit einem Klick aufrufbare Edge Delivery Service (EDS) wurde entwickelt, um das Onboarding und die Bereitstellung von Edge Delivery-Sites in Cloud Manager zu automatisieren. Dies vereinfacht den Prozess erheblich, da Sie nur auf eine einzige Schaltfläche klicken müssen. Mit diesem einen Klick erreichen Sie, dass die erforderliche Infrastruktur bereitgestellt, eine Integration mit GitHub zur Versionskontrolle durchgeführt und Ihr Dokument- und Asset-Speicher in Google Drive konfiguriert wird.

Diese Automatisierung trägt dazu bei, den manuellen Aufwand bei der Einrichtung Ihrer ersten Site zu reduzieren. Auf diese Weise werden nicht nur nahtlose Workflows sowie Skalierbarkeit sichergestellt, sondern auch die Leistung Ihrer Teams bei der Verwaltung von Inhalten am Edge verbessert.

## Wichtige Konzepte {#key-concepts}

Wichtige Konzepte bei der Erstellung einer Edge Delivery-Site mit einem Klick.

| Schlüsselkonzept | Beschreibung |
| --- | --- |
| Automatisierte Edge-Bereitstellung | <ul><li>Benutzer können Edge Delivery-Sites sofort erstellen und konfigurieren.</li><li>Durch die Integration von Cloud Manager mit dem CI/CD-Workflow reduziert oder eliminiert sie den manuellen Onboarding-Prozess.</li><li>Integration mit Cloud Manager für nahtlose CI/CD-Workflows.</li></ul> |
| Integration mit Cloud Manager | <ul><li>Verwendet die Cloud Manager-Benutzeroberfläche, um den Edge Delivery-Prozess mit einem Klick auszulösen.</li><li>Ermöglicht den Zugriff auf eine automatisierte Repository-Erstellung und -Bereitstellung.</li></ul> |
| GitHub-basierte Versionskontrolle | <ul><li>Erstellt ein GitHub-Repository innerhalb einer Organisation mithilfe vordefinierter Bausteinvorlagen, um Bereitstellungen zu standardisieren.</li><li>Verbindet sich mit dem AEM-Bot für Inhaltsaktualisierungen.</li></ul> |
| Integration von Dokument- und Asset-Speicher | <ul><li>Erzeugt einen Google Drive-Ordner zum Speichern.<li>Installiert die AEM-Code-Synchronisierungsanwendung im Repository und sorgt so für eine nahtlose Synchronisierung und Bereitstellung.</li></li><li>Ermöglicht mehreren Mitarbeitenden die einfache Verwaltung von Dokumenten.</li></ul> |
| Sicherheit und Skalierbarkeit | <ul><li>Stellt die Einhaltung der Sicherheitsstandards eines Unternehmens sicher.</li><li>Unterstützt mehrere Edge Delivery-Sites unter verschiedenen Cloud Manager-Mandanten.</li></ul> |



## Erstellen einer Edge Delivery-Site in Cloud Manager mit einem Klick {#one-click-edge-delivery-site}

Um eine Adobe Edge-Bereitstellungs-Site mit einem Klick erstellen zu können, muss Ihr Unternehmen über eine verfügbare Edge Delivery Services-Lizenz verfügen. Diese Lizenz ist Teil von Adobe Experience Manager (AEM) und zum Erstellen von Edge Delivery Services in Cloud Manager erforderlich.

Was Berechtigungen angeht, müssen Sie Mitglied der Rolle „Geschäftsinhaber“ sein oder Ihnen müssen die entsprechenden Berechtigungen zum Hinzufügen oder Bearbeiten von Programmen in Cloud Manager gewährt worden sein. Mit dieser Zugriffsebene können Sie die Integration von Edge Delivery Services in Ihre Programme steuern.

Siehe auch [Einführung in Edge Delivery Services in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

MÜSSEN ZUERST DIE RICHTIGEN AEM-BOT-KONFIGURATIONEN FÜR AUTOMATISCHE INHALTSAKTUALISIERUNGEN VORHANDEN SEIN? RICHTIG? FALSCH?

**So erstellen Sie eine Edge Delivery-Site in Cloud Manager mit einem Klick:**

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.
1. Klicken Sie im linken Seitenmenü unter **Services** auf ![Web-Seiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery-Sites**.
1. Klicken Sie auf der Edge Delivery-Seite im Dialogfeld **Aufgabenliste für Edge Delivery** im Gruppenfeld **Voraussetzungen erfüllen** auf **Bereitstellung**.
1. Geben Sie im Dialogfeld zum **Bereitstellen der Edge Delivery-Site** in das Textfeld **Projektname** den Namen Ihrer Site ein und klicken Sie dann auf **Bereitstellung**.
Oben in der Mitte des Bildschirms wird eine Popup-Meldung angezeigt, die Sie darüber informiert, dass die Bereitstellung der Edge Delivery-Site begonnen hat.
Wenn die Bereitstellung abgeschlossen ist und Ihre Site validiert wurde, wird der Site-Name im Bereich **Edge Delivery-Sites** auf der Edge Delivery-Seite angezeigt.

### Erkunden einer neu erstellten Edge Delivery-Site


1. Klicken Sie auf den Git-Repository-Link rechts neben dem Namen der Site.

Veröffentlichen.

Klicken Sie auf Site-Name,

Nehmen Sie einige Änderungen vor und veröffentlichen Sie dann

Zeigen Sie die Seite in einer Vorschau an und ändern Sie dann die URL, um die Live-Version anzuzeigen.

Fügen Sie Mitarbeitende hinzu.


## Vorschau einer Edge Delivery-Site mit einem Klick

## Edge Delivery-Site mit einem Klick veröffentlichen





## Hinzufügen von Mitarbeitern zu einer Edge Delivery-Site mit einem Klick


































Diese Verbesserungen zielen darauf ab, die Automatisierung zu optimieren, Einrichtungsprozesse zu vereinfachen und die Zusammenarbeit für Edge Delivery Services-Benutzende zu verbessern. <!-- CMGR-59362 -->

![Erstellen einer Edge Delivery-Site mit einem Klick](/help/implementing/cloud-manager/release-notes/assets/eds-one-click-60.png)

![Dialogfeld zum Bereitstellen einer Edge Delivery-Site](/help/implementing/cloud-manager/release-notes/assets/eds-provision-60.png)