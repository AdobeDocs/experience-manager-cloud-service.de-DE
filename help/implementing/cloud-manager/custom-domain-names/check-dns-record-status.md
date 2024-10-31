---
title: Überprüfen des Status von DNS-Einträgen
description: Erfahren Sie, wie Sie mithilfe von Cloud Manager feststellen können, ob Ihre DNS-Einstellungen ordnungsgemäß aufgelöst werden.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: ht
source-wordcount: '366'
ht-degree: 100%

---


# Überprüfen des Status von DNS-Einträgen {#check-dns-record-status}

Erfahren Sie, wie Sie mithilfe von Cloud Manager feststellen können, ob Ihre DNS-Einstellungen ordnungsgemäß aufgelöst werden.

## Status der DNS-Einträge {#status}

Ein benutzerdefinierter Domain-Name kann Livetraffic erst bereitstellen, wenn das DNS korrekt aufgelöst wird. In Cloud Manager können Sie feststellen, ob Ihr Domain-Name ordnungsgemäß zu Ihrer AEM as a Cloud Service-Website aufgelöst wird.

## Voraussetzungen {#requirements}

Sie müssen diese Voraussetzungen erfüllen, bevor Sie den Status eines DNS-Eintrags mit Cloud Manager überprüfen.

Sie müssen die DNS-Einstellungen für Ihren benutzerdefinierten Domain-Namen bereits konfiguriert haben, wie unter [Hinzufügen eines benutzerdefinierten DNS-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) beschrieben.

## Überprüfen des Status von DNS-Einträgen {#how-to}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Seitenmenü auf **Domain-Einstellungen**.

1. Klicken Sie auf das Symbol **Status**, um den Domain-Namen zu sehen.

Cloud Manager führt eine DNS-Suche nach Ihrem Domain-Namen durch und zeigt dessen [aktuellen Status](#statuses) an:

Cloud Manager löst automatisch eine DNS-Suche aus, wenn Ihr benutzerdefinierter Domain-Name zum ersten Mal überprüft und bereitgestellt wird. Bei nachfolgenden Versuchen müssen Sie das Symbol zum **erneuten Auflösen** neben dem Status aktiv anklicken.

## DNS-Status in Cloud Manager {#statuses}

Eine benutzerdefinierte Domain kann einen der folgenden Status in Cloud Manager haben.

| Status | Beschreibung |
| --- | --- |
| DNS-Status nicht erkannt | Der DNS-Status wird erst dann erkannt, wenn Ihr benutzerdefinierter Domain-Name erfolgreich überprüft und bereitgestellt wurde. Dieser Status wird auch angezeigt, wenn der Name Ihrer benutzerdefinierten Domain gerade gelöscht wird. |
| DNS wird falsch aufgelöst | Dieser Status gibt an, dass entweder die Konfiguration der DNS-Einträge nicht aufgelöst wurde oder fehlerhaft ist. Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).<br>Wenn Sie bereit sind, müssen Sie auf das Symbol **Erneut auflösen** neben dem Status klicken. |
| DNS-Auflösung in Bearbeitung | Die Auflösung läuft. Dieser Status wird normalerweise angezeigt, nachdem Sie auf das Symbol zum **erneuten Auflösen** neben dem Status geklickt haben. |
| DNS wird richtig aufgelöst | Ihre DNS-Einstellungen sind ordnungsgemäß konfiguriert. Ihre Website bedient Besucherinnen und Besucher. |

## Nächste Schritte {#next-steps}

Sie haben Ihre benutzerdefinierte Domain für die Nutzung mit Cloud Manager erfolgreich konfiguriert. Weitere Informationen zur Verwaltung Ihrer benutzerdefinierten Domain-Namen mit Cloud Manager finden Sie unter [Verwalten benutzerdefinierter Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md).
