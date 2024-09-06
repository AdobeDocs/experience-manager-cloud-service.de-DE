---
title: Benutzerdefinierten Domänennamen hinzufügen
description: Erfahren Sie, wie Sie mit Cloud Manager einen benutzerdefinierten Domain-Namen hinzufügen.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4a369104ea8394989149541ee1a7b956383c8f12
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 48%

---


# Benutzerdefinierten Domänennamen hinzufügen {#adding-cdn}

Erfahren Sie, wie Sie mit Cloud Manager einen benutzerdefinierten Domain-Namen hinzufügen.

## Voraussetzungen {#requirements}

Erfüllen Sie diese Anforderungen, bevor Sie einen benutzerdefinierten Domänennamen in Cloud Manager hinzufügen.

* Sie müssen ein SSL-Domänenzertifikat für die Domäne hinzugefügt haben, die Sie hinzufügen möchten, bevor Sie einen benutzerdefinierten Domänennamen hinzufügen, wie im Dokument [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) beschrieben.
* Sie müssen über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um einen benutzerdefinierten Domain-Namen in Cloud Manager hinzufügen zu können.
* Verwenden Sie das Fastly-CDN.

## Hinzufügen benutzerdefinierter Domänennamen {#where}

In Cloud Manager können Sie einen benutzerdefinierten Domain-Namen aus zwei Positionen hinzufügen:

* [Auf der Seite „Domain-Einstellungen“](#adding-cdn-settings)
* [Auf der Seite „Umgebungen“](#adding-cdn-environments)

Beim Hinzufügen eines benutzerdefinierten Domänennamens wird die Domäne mit dem spezifischsten, gültigen Zertifikat bereitgestellt. Wenn mehrere Zertifikate dieselbe Domain haben, wird die zuletzt aktualisierte ausgewählt. Adobe empfiehlt, Zertifikate so zu verwalten, dass es keine überlappenden Domains gibt.

Die Schritte, die in diesem Dokument beschrieben werden, basieren auf Fastly. Wenn Sie ein anderes CDN verwendet haben, konfigurieren Sie Ihre Domäne mit dem CDN, das Sie für die Verwendung ausgewählt haben.

## Fügen Sie auf der Seite &quot;Domäneneinstellungen&quot;einen benutzerdefinierten Domänennamen hinzu. {#adding-cdn-settings}

Gehen Sie folgendermaßen vor, um auf der Seite **Domain-Einstellungen** einen benutzerdefinierten Domain-Namen hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie zum linken Navigationsbereich, um die Registerkarte **Domain-Einstellungen** auszuwählen.

   ![Fenster „Domain-Einstellungen“](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie oben rechts auf die Schaltfläche **Domain hinzufügen**, um das Dialogfeld **Domain-Namen hinzufügen** zu öffnen.

   ![Dialogfeld &quot;Domäne hinzufügen&quot;](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Geben Sie auf der Registerkarte **Domain-Name** den benutzerdefinierten Domain-Namen in das Feld **Domain-Name** ein.

   >[!NOTE]
   >
   >Verwenden Sie bei der Eingabe Ihrer Domain weder `http://`, noch `https://` oder Leerzeichen.

1. Wählen Sie die **Umgebung** aus, deren Service mit dem Domain-Namen verknüpft werden soll.

1. Wählen Sie entweder den Service **Veröffentlichen** oder **Vorschau**.

1. Wählen Sie aus der Dropdown-Liste das **Domain-SSL-Zertifikat** aus, das mit dem Domain-Namen verknüpft ist, und klicken Sie auf **Weiter**.

1. Die Registerkarte **Überprüfung** wird angezeigt.

   ![Verifizierung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   * Auf der Registerkarte **Überprüfung** werden die nächsten Schritte zum Konfigurieren Ihres benutzerdefinierten Domain-Namens beschrieben, wobei ein erforderlicher TXT-Eintrag erstellt wird.
   * Sie können diesen Schritt sofort ausführen (bevor Sie im Dialogfeld auf **Erstellen** klicken) oder nachdem Sie im Dialogfeld auf **Erstellen** geklickt haben.
   * Die Optionen und nächsten Schritte werden nachfolgend beschrieben.

1. Klicken Sie auf **Erstellen** , um den benutzerdefinierten Domänennamen in Cloud Manager zu speichern.

Wenn Sie im Assistenten zum Hinzufügen benutzerdefinierter Domänen **die Option** Erstellen **auswählen, führt Cloud Manager Trigger eine TXT-Überprüfung durch.** Erstellen Sie den TXT-Eintrag, wenn Sie den benutzerdefinierten Domänennamen in Cloud Manager einrichten. Dieser Schritt ist jedoch nicht erforderlich. Für nachfolgende Überprüfungen müssen Sie aktiv das Symbol **Erneut überprüfen** neben dem Status auswählen.

Der Name ist erst aktiv, nachdem Cloud Manager überprüft hat, ob der TXT-Eintrag hinzugefügt und verifiziert wurde. Der Status von **Verifiziert und bereitgestellt** zeigt eine erfolgreiche TXT-Überprüfung an.

* Weitere Informationen zu TXT-Einträgen finden Sie unter [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) .
* Weitere Informationen dazu, wie Cloud Manager den benutzerdefinierten Domänennamen und seinen TXT-Eintrag überprüft, finden Sie unter [Überprüfen des Domänennamenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) .

## Nächste Schritte {#next-steps}

Nachdem Sie Ihren benutzerdefinierten Domänennamen in Cloud Manager erstellt haben, fügen Sie einen TXT-Eintrag hinzu, um das Eigentum an der Domäne zu überprüfen. Befolgen Sie das Dokument [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md), um mit der Einrichtung Ihres benutzerdefinierten Domain-Namens fortzufahren.

## Fügen Sie auf der Seite &quot;Umgebungen&quot;einen benutzerdefinierten Domänennamen hinzu {#adding-cdn-environments}

Die Schritte zum Hinzufügen eines benutzerdefinierten Domänennamens von der Seite **Umgebungen** sind mit denen beim Hinzufügen eines benutzerdefinierten Domänennamens von der Seite &quot;Domäneneinstellungen&quot;](#adding-cdn-settings) identisch, der Einstiegspunkt unterscheidet sich jedoch. [ Führen Sie die folgenden Schritte von der Seite **Umgebungen** aus, um einen benutzerdefinierten Domain-Namen hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zur Seite &quot;**Umgebungsdetails**&quot;für die interessante Umgebung.

   ![Eingabe des Domain-Namens auf der Seite „Umgebungsdetails“](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Verwenden Sie die Tabelle **Domain-Namen**, um den benutzerdefinierten Domain-Namen zu übermitteln.

   1. Geben Sie den benutzerdefinierten Domain-Namen ein.
   1. Wählen Sie in der Dropdown-Liste das mit diesem Namen verknüpfte SSL-Zertifikat aus.
   1. Klicken Sie auf **+Hinzufügen**.

   ![Fügen Sie einen benutzerdefinierten Domänennamen hinzu](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Das Dialogfeld **Domänennamen hinzufügen** wird auf der Registerkarte **Domänenname** geöffnet. Fahren Sie so fort wie bei [Hinzufügen eines benutzerdefinierten Domänennamens von der Seite &quot;Domäneneinstellungen&quot;](#adding-cdn-settings).
