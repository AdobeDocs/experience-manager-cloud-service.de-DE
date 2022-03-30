---
title: Überprüfen des Status von DNS-Einträgen
description: Erfahren Sie, wie Sie mithilfe von Cloud Manager feststellen können, ob Ihre DNS-Einstellungen ordnungsgemäß aufgelöst werden.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
source-git-commit: 2278abcf0c34fd34a7730242ee27814d37b7d4d0
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 24%

---

# Überprüfen des Status von DNS-Einträgen {#check-dns-record-status}

In Cloud Manager können Sie feststellen, ob Ihr Domänenname ordnungsgemäß auf Ihre AEM as a Cloud Service Website aufgelöst wird.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.

1. Klicken Sie auf **Domäneneinstellungen** im linken Navigationsbereich.

1. Klicken Sie auf **Status** für den Domänennamen.

Cloud Manager führt eine DNS-Suche nach Ihrem Domain-Namen durch und zeigt eine der folgenden Statusmeldungen an.

* **DNS-Status nicht erkannt** - Der DNS-Status wird erst erkannt, wenn Ihr benutzerdefinierter Domänenname erfolgreich verifiziert und bereitgestellt wurde.

   * Dieser Status wird auch angezeigt, wenn der Name Ihrer benutzerdefinierten Domain gerade gelöscht wird.

* **DNS löst falsch auf** - Dies weist darauf hin, dass die Konfiguration der DNS-Einträge nicht aufgelöst wurde oder fehlerhaft ist.

   * Siehe Dokument . [DNS-Einstellungen konfigurieren](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) , um mehr zu erfahren.
   * Wenn Sie bereit sind, müssen Sie die **Erneut auflösen** neben dem Status.

* **DNS-Auflösung läuft** - Die Entschließung ist in Arbeit.

   * Dieser Status wird normalerweise angezeigt, nachdem Sie die **Erneut auflösen** neben dem Status.

* **DNS löst ordnungsgemäß auf** - Ihre DNS-Einstellungen sind ordnungsgemäß konfiguriert.

   * Ihre Website bedient Besucher.

Cloud Manager Trigger automatisch eine DNS-Suche, wenn Ihr benutzerdefinierter Domänenname zum ersten Mal erfolgreich verifiziert und bereitgestellt wurde. Für nachfolgende Versuche müssen Sie die **Erneut auflösen** neben dem Status.
