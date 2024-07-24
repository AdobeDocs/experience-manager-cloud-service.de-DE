---
title: Überprüfen des Status von DNS-Einträgen
description: Erfahren Sie, wie Sie mithilfe von Cloud Manager feststellen können, ob Ihre DNS-Einstellungen ordnungsgemäß aufgelöst werden.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 06e961febd7cb2ea1d8fca00cb3dee7f7ca893c9
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 62%

---


# Überprüfen des Status von DNS-Einträgen {#check-dns-record-status}

Erfahren Sie, wie Sie mithilfe von Cloud Manager feststellen können, ob Ihre DNS-Einstellungen ordnungsgemäß aufgelöst werden.

## DNS-Eintragsstatus {#status}

Ein benutzerdefinierter Domänenname kann Live-Traffic erst bereitstellen, wenn das DNS korrekt aufgelöst wurde. In Cloud Manager können Sie feststellen, ob Ihr Domain-Name ordnungsgemäß auf Ihre AEM as a Cloud Service-Website aufgelöst wird.

## Voraussetzungen {#requirements}

Sie müssen diese Anforderungen erfüllen, bevor Sie einen DNS-Datensatzstatus mit Cloud Manager überprüfen.

* Sie müssen die DNS-Einstellungen für Ihren benutzerdefinierten Domänennamen bereits konfiguriert haben, wie im Dokument [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) beschrieben.

## Überprüfen des DNS-Datensatzstatus {#how-to}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich auf **Domain-Einstellungen**.

1. Klicken Sie auf das Symbol **Status**, um den Domain-Namen zu sehen.

Cloud Manager führt eine DNS-Suche für Ihren Domänennamen durch und zeigt den aktuellen Status [an.](#statuses)

Cloud Manager löst automatisch eine DNS-Suche aus, wenn Ihr benutzerdefinierter Domain-Name zum ersten Mal überprüft und bereitgestellt wird. Bei nachfolgenden Versuchen müssen Sie das Symbol zum **erneuten Auflösen** neben dem Status aktiv anklicken.

## DNS-Status in Cloud Manager {#statuses}

Eine benutzerdefinierte Domäne kann einen der folgenden Status in Cloud Manager haben.

* **DNS-Status nicht erkannt**: Der DNS-Status wird erst dann erkannt, wenn Ihr benutzerdefinierter Domain-Name erfolgreich überprüft und bereitgestellt wurde.

   * Dieser Status wird auch beobachtet, wenn Ihr benutzerdefinierter Domänenname gerade gelöscht wird.

* **DNS wird falsch aufgelöst**: Dies zeigt an, dass entweder die Konfiguration der DNS-Einträge noch nicht aufgelöstübertragen wurde oder fehlerhaft ist.

   * Weitere Informationen finden Sie unter [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md).
   * Wenn Sie bereit sind, müssen Sie auf das Symbol zum **erneuten Auflösen** neben dem Status klicken.

* **DNS-Auflösung in Bearbeitung**: Die Auflösung ist in Bearbeitung.

   * Dieser Status wird normalerweise angezeigt, nachdem Sie neben dem Status auf das Symbol zum **erneuten Auflösen** geklickt haben.

* **DNS wird korrekt aufgelöst**: Ihre DNS-Einstellungen sind ordnungsgemäß konfiguriert.

   * Ihre Website bedient Besucher.

## Nächste Schritte {#next-steps}

Herzlichen Glückwunsch! Sie haben Ihre benutzerdefinierte Domäne für die Verwendung mit Cloud Manager erfolgreich konfiguriert. Weitere Informationen zur Verwaltung Ihrer benutzerdefinierten Domänennamen mit Cloud Manager finden Sie im Dokument [Verwalten benutzerdefinierter Domänennamen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) .
