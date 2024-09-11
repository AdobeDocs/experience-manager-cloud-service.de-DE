---
title: Überprüfen des Status von DNS-Einträgen
description: Erfahren Sie, wie Sie mithilfe von Cloud Manager feststellen können, ob Ihre DNS-Einstellungen ordnungsgemäß aufgelöst wurden.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8a10634e413ea5c66845dfffa7396a4554a5b3ca
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 39%

---


# Überprüfen des Status von DNS-Einträgen {#check-dns-record-status}

Erfahren Sie, wie Sie mithilfe von Cloud Manager feststellen können, ob Ihre DNS-Einstellungen ordnungsgemäß aufgelöst wurden.

## DNS-Eintragsstatus {#status}

Ein benutzerdefinierter Domänenname kann Live-Traffic erst bereitstellen, wenn das DNS korrekt aufgelöst wurde. In Cloud Manager können Sie feststellen, ob Ihr Domänenname ordnungsgemäß auf Ihre AEM as a Cloud Service-Website aufgelöst wird.

## Voraussetzungen {#requirements}

Erfüllen Sie diese Anforderungen, bevor Sie einen DNS-Datensatzstatus mit Cloud Manager überprüfen.

Sie müssen die DNS-Einstellungen für Ihren benutzerdefinierten Domänennamen bereits konfiguriert haben, wie unter [Benutzerdefinierten Domänennamen hinzufügen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) beschrieben.

## Überprüfen des Status von DNS-Einträgen {#how-to}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich auf **Domain-Einstellungen**.

1. Klicken Sie auf das Symbol **Status**, um den Domain-Namen zu sehen.

Cloud Manager führt eine DNS-Suche für Ihren Domänennamen durch und zeigt ihn [aktuellen Status](#statuses) an.

Cloud Manager Trigger automatisch eine DNS-Suche, wenn Ihr benutzerdefinierter Domänenname zum ersten Mal erfolgreich verifiziert und bereitgestellt wurde. Bei nachfolgenden Versuchen müssen Sie das Symbol zum **erneuten Auflösen** neben dem Status aktiv anklicken.

## DNS-Status in Cloud Manager {#statuses}

Eine benutzerdefinierte Domain kann einen der folgenden Status in Cloud Manager haben.

| Status | Beschreibung |
| --- | --- |
| DNS-Status nicht erkannt | Der DNS-Status wird erst erkannt, wenn Ihr benutzerdefinierter Domänenname erfolgreich verifiziert und bereitgestellt wurde. Dieser Status wird auch angezeigt, wenn der Name Ihrer benutzerdefinierten Domain gerade gelöscht wird. |
| DNS wird falsch aufgelöst | Dieser Status zeigt an, dass die Konfiguration der DNS-Einträge nicht aufgelöst wurde oder fehlerhaft ist. Weitere Informationen finden Sie unter [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) .<br>Wenn Sie bereit sind, müssen Sie neben dem Status das Symbol **Erneut auflösen** auswählen. |
| DNS-Auflösung läuft | Die Entschließung ist in Arbeit. Dieser Status wird normalerweise angezeigt, nachdem Sie neben dem Status auf das Symbol zum **erneuten Auflösen** geklickt haben. |
| DNS wird richtig aufgelöst | Ihre DNS-Einstellungen sind ordnungsgemäß konfiguriert. Ihre Website bedient Besucher. |

## Nächste Schritte {#next-steps}

Sie haben Ihre benutzerdefinierte Domain für die Nutzung mit Cloud Manager erfolgreich konfiguriert. Weitere Informationen zur Verwaltung Ihrer benutzerdefinierten Domänennamen mit Cloud Manager finden Sie im Dokument [Verwalten benutzerdefinierter Domänennamen](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) .
