---
title: Überprüfen des Status von DNS-Einträgen
description: Erfahren Sie, wie Sie mithilfe von Cloud Manager feststellen können, ob Ihre DNS-Einstellungen ordnungsgemäß aufgelöst werden.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
source-git-commit: 2278abcf0c34fd34a7730242ee27814d37b7d4d0
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 100%

---

# Überprüfen des Status von DNS-Einträgen {#check-dns-record-status}

In Cloud Manager können Sie feststellen, ob Ihr Domain-Name ordnungsgemäß auf Ihre AEM as a Cloud Service-Website aufgelöst wird.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich auf **Domain-Einstellungen**.

1. Klicken Sie auf das Symbol **Status** für den Domain-Namen.

Cloud Manager führt eine DNS-Suche nach Ihrem Domain-Namen durch und zeigt eine der folgenden Statusmeldungen an.

* **DNS-Status nicht erkannt**: Der DNS-Status wird erst dann erkannt, wenn Ihr benutzerdefinierter Domain-Name erfolgreich überprüft und bereitgestellt wurde.

   * Dieser Status wird auch angezeigt, wenn der Name Ihrer benutzerdefinierten Domain gerade gelöscht wird.

* **DNS wird falsch aufgelöst**: Dies zeigt an, dass entweder die Konfiguration der DNS-Einträge noch nicht aufgelöstübertragen wurde oder fehlerhaft ist.

   * Weitere Informationen finden Sie im Dokument [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md).
   * Wenn Sie bereit sind, müssen Sie auf das Symbol zum **erneuten Auflösen** neben dem Status klicken.

* **DNS-Auflösung in Bearbeitung**: Die Auflösung ist in Bearbeitung.

   * Dieser Status wird normalerweise angezeigt, nachdem Sie neben dem Status auf das Symbol zum **erneuten Auflösen** geklickt haben.

* **DNS wird korrekt aufgelöst**: Ihre DNS-Einstellungen sind ordnungsgemäß konfiguriert.

   * Ihre Website bedient Besucher.

Cloud Manager löst automatisch eine DNS-Suche aus, wenn Ihr benutzerdefinierter Domain-Name zum ersten Mal überprüft und bereitgestellt wird. Bei nachfolgenden Versuchen müssen Sie das Symbol zum **erneuten Auflösen** neben dem Status aktiv anklicken.
