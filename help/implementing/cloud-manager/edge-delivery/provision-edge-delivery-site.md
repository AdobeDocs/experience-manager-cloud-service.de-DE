---
title: Bereitstellen einer Edge Delivery-Site in Cloud Manager
description: Erfahren Sie, wie Sie mit einem Klick in Cloud Manager schnell eine Edge Delivery-Site erstellen können.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 11%

---


# Über die Bereitstellung einer Edge Delivery-Site in Cloud Manager {#about-provision-edge-delivery-site}

Der One Click Edge Delivery Service (EDS) wurde entwickelt, um das Onboarding und die Bereitstellung von Edge Delivery-Sites in Cloud Manager zu automatisieren. Dies vereinfacht den Prozess erheblich, da Sie auf eine einzelne Schaltfläche klicken müssen. Dieser einfache Klick stellt die erforderliche Infrastruktur bereit, integriert sich mit GitHub für die Versionskontrolle und konfiguriert Ihren Dokument- und Asset-Speicher in Google Drive.

Diese Automatisierung trägt dazu bei, den manuellen Aufwand für die Einrichtung Ihrer ersten Site zu reduzieren. Es sorgt für nahtlose Workflows, Skalierbarkeit und verbessert die Leistung Ihrer Teams bei der Verwaltung von Inhalten an der Edge.

## Wichtige Konzepte {#key-concepts}

Wichtige Konzepte bei der Verwendung der Edge Delivery-Site-Bereitstellung mit einem Klick.

| Schlüsselkonzept | Beschreibung |
| --- | --- |
| Automatisierte Edge-Bereitstellung | <ul><li>Benutzer können Edge Delivery-Sites sofort bereitstellen und konfigurieren.</li><li>Verringert oder eliminiert den Bedarf an manuellen Onboarding-Prozessen durch die Verwendung der Integration von Cloud Manager mit dem CI/CD-Workflow.</li><li>Integration mit Cloud Manager für nahtlose CI/CD-Workflows.</li></ul> |
| Integration mit Cloud Manager | <ul><li>Verwendet die Cloud Manager-Benutzeroberfläche zum Trigger des Edge Delivery-Prozesses mit einem Klick.</li><li>Ermöglicht den Zugriff auf die automatisierte Repository-Erstellung und -Bereitstellung.</li></ul> |
| GitHub-basierte Versionskontrolle | <ul><li>Erstellt ein GitHub-Repository innerhalb einer Organisation mithilfe vordefinierter Textvorlagen, um Bereitstellungen zu standardisieren.</li><li>Links zum AEM-Bot für Inhaltsaktualisierungen.</li></ul> |
| Integration von Dokumenten- und Asset-Speicher | <ul><li>Erzeugt einen Ordner auf dem Google-Laufwerk.<li>Installiert die AEM-Code-Synchronisierungsanwendung im Repository, um eine nahtlose Synchronisierung und Bereitstellung sicherzustellen.</li></li><li>Ermöglicht mehreren Mitarbeitern die einfache Verwaltung von Dokumenten.</li></ul> |
| Sicherheit und Skalierbarkeit | <ul><li>Stellt die Einhaltung von Unternehmenssicherheitsstandards sicher.</li><li>Unterstützt mehrere Edge Delivery Sites unter verschiedenen Cloud Manager-Mandanten.</li></ul> |



## Bereitstellen einer Edge Delivery-Site in Cloud Manager {#provision-edge-delivery-site}

Um eine Adobe Edge-Bereitstellungs-Site mit einem Klick bereitstellen zu können, muss Ihr Unternehmen über eine verfügbare Edge Delivery Services-Lizenz verfügen. Diese Lizenz ist Teil von Adobe Experience Manager (AEM) und für die Bereitstellung von Edge Delivery Services in Cloud Manager erforderlich.

In Bezug auf Berechtigungen müssen Sie Mitglied der Rolle Geschäftsinhaber sein oder Ihnen wurden die entsprechenden Berechtigungen zum Hinzufügen oder Bearbeiten von Programmen in Cloud Manager gewährt. Mit dieser Zugriffsebene können Sie die Integration von Edge Delivery Services in Ihre Programme verwalten.

Siehe auch [Einführung in Edge Delivery Services in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

MÜSSEN ZUERST DIE RICHTIGEN AEM-BOT-KONFIGURATIONEN FÜR AUTOMATISCHE INHALTSAKTUALISIERUNGEN VORHANDEN SEIN? WAHR? FALSCH?

**So stellen Sie eine Edge Delivery-Site in Cloud Manager bereit:**

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.
1. Klicken Sie im linken Menü unter der Überschrift **Services** auf ![Web-Seitensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
1. Klicken Sie auf der Edge Delivery-Seite im Dialogfeld **Edge Delivery** Aufgabenliste im Gruppenfeld **Voraussetzungen abschließen** auf **Bereitstellen**.
1. Geben **im Dialogfeld &quot;Edge Delivery-Site bereitstellen** im Textfeld **Projektname** den Namen Ihrer Site ein und klicken Sie dann auf **Bereitstellung**.
In der oberen Mitte des Bildschirms wird eine Meldung angezeigt, die Sie darüber informiert, dass die Bereitstellung der Edge Delivery-Site begonnen hat.
Wenn die Bereitstellung abgeschlossen ist und Ihre Site validiert wurde, wird der Site-Name im Bereich **Edge Delivery Sites** auf der Edge Delivery-Seite angezeigt.

### Erkunden einer neu bereitgestellten Edge Delivery-Site




1. Klicken Sie auf den Link Git-Repository rechts neben dem Namen der Site.

Publish. Klicken Sie auf Site-Name, nehmen Sie einige Änderungen vor und veröffentlichen Sie

Seite in der Vorschau anzeigen und dann URL ändern, um die Live-Version anzuzeigen.

Mitarbeiter hinzufügen.




## Publish und Edge Delivery Site



## Hinzufügen von Mitarbeitern zu einer Edge Delivery-Site


































Diese Verbesserungen zielen darauf ab, die Automatisierung zu optimieren, Einrichtungsprozesse zu vereinfachen und die Zusammenarbeit für Edge Delivery Services-Benutzende zu verbessern. <!-- CMGR-59362 -->

![Bereitstellen einer Edge Delivery-Site](/help/implementing/cloud-manager/release-notes/assets/eds-one-click-60.png)

![Dialogfeld zum Bereitstellen einer Edge Delivery-Site](/help/implementing/cloud-manager/release-notes/assets/eds-provision-60.png)