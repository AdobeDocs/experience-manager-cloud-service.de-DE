---
title: Hinzufügen eines benutzerdefinierten Domain-Namens
description: Erfahren Sie, wie Sie mit Cloud Manager einen benutzerdefinierten Domain-Namen hinzufügen.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 06e961febd7cb2ea1d8fca00cb3dee7f7ca893c9
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 49%

---


# Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn}

Erfahren Sie, wie Sie mit Cloud Manager einen benutzerdefinierten Domain-Namen hinzufügen.

## Voraussetzungen {#requirements}

Sie müssen diese Anforderungen erfüllen, bevor Sie einen benutzerdefinierten Domänennamen in Cloud Manager hinzufügen.

* Sie müssen ein SSL-Domänenzertifikat für die Domäne hinzugefügt haben, die Sie hinzufügen möchten, bevor Sie einen benutzerdefinierten Domänennamen hinzufügen, wie im Dokument [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) beschrieben.
* Sie müssen über die Rolle **Business Owner** oder **Deployment Manager** verfügen, um in Cloud Manager einen benutzerdefinierten Domänennamen hinzuzufügen.
* Sie müssen das Fastly CDN verwenden.

## Hinzufügen benutzerdefinierter Domänennamen {#where}

In Cloud Manager können Sie einen benutzerdefinierten Domain-Namen aus zwei Positionen hinzufügen:

* [Auf der Seite „Domain-Einstellungen“](#adding-cdn-settings)
* [Auf der Seite „Umgebungen“](#adding-cdn-environments)

Beim Hinzufügen eines benutzerdefinierten Domain-Namens wird die Domain mit dem spezifischsten gültigen Zertifikat bereitgestellt. Wenn mehrere Zertifikate dieselbe Domain haben, wird die zuletzt aktualisierte ausgewählt. Adobe empfiehlt, Zertifikate so zu verwalten, dass es keine überlappenden Domains gibt.

Die Schritte, die in diesem Dokument beschrieben werden, basieren auf Fastly. Wenn Sie ein anderes CDN verwenden, müssen Sie die Domain mit dem CDN konfigurieren, das Sie für die Verwendung ausgewählt haben.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Domain-Einstellungen {#adding-cdn-settings}

Gehen Sie folgendermaßen vor, um auf der Seite **Domain-Einstellungen** einen benutzerdefinierten Domain-Namen hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie zum linken Navigationsbereich, um die Registerkarte **Domain-Einstellungen** auszuwählen.

   ![Fenster „Domain-Einstellungen“](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie oben rechts auf die Schaltfläche **Domain hinzufügen**, um das Dialogfeld **Domain-Namen hinzufügen** zu öffnen.

   ![Dialog „Domain hinzufügen“](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Geben Sie auf der Registerkarte **Domänenname** den benutzerdefinierten Domänennamen in das Feld **Domänenname** ein.

   >[!NOTE]
   >
   >Verwenden Sie bei der Eingabe Ihrer Domain weder `http://`, noch `https://` oder Leerzeichen.

1. Wählen Sie die **Umgebung** aus, deren Service mit dem Domain-Namen verknüpft werden soll.

1. Wählen Sie entweder den Service **Veröffentlichen** oder **Vorschau**.

1. Wählen Sie aus der Dropdown-Liste das **Domain-SSL-Zertifikat** aus, das mit dem Domain-Namen verknüpft ist, und klicken Sie auf **Weiter**.

1. Die Registerkarte **Überprüfung** wird angezeigt.

   ![Verifizierung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   * Auf der Registerkarte **Verifizierung** werden die nächsten Schritte zum Konfigurieren Ihres benutzerdefinierten Domain-Namens beschrieben, mit denen ein erforderlicher TXT-Eintrag erstellt wird.
   * Sie können dies sofort tun (bevor Sie im Dialogfeld auf **Erstellen** tippen oder klicken) oder nachdem Sie im Dialogfeld auf **Erstellen** tippen oder klicken.
   * Die Optionen und nächsten Schritte werden nachfolgend beschrieben.

1. Tippen oder klicken Sie auf **Erstellen** , um den benutzerdefinierten Domänennamen in Cloud Manager zu speichern.

Cloud Manager wird automatisch eine TXT-Überprüfung Trigger, wenn Sie im Überprüfungsschritt des Assistenten **Benutzerdefinierte Domäne hinzufügen** die Option **Erstellen** auswählen. Daher wird empfohlen, den TXT-Eintrag bei der Erstellung des benutzerdefinierten Domänennamens in Cloud Manager zu erstellen. Dies ist jedoch nicht erforderlich. Für spätere Überprüfungen müssen Sie das Symbol Erneut überprüfen neben dem Status aktiv auswählen.

Der Name ist erst aktiv, wenn der TXT-Eintrag hinzugefügt und von Cloud Manager überprüft wurde. Eine erfolgreiche TXT-Überprüfung wird durch den Status **Verifiziert und bereitgestellt** gekennzeichnet.

* Weitere Informationen zu TXT-Einträgen finden Sie unter [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md).
* Weitere Informationen dazu, wie Cloud Manager den benutzerdefinierten Domänennamen und seinen TXT-Eintrag überprüft, finden Sie unter [Überprüfen des Domänennamenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) .

## Nächste Schritte {#next-steps}

Nachdem Sie Ihren benutzerdefinierten Domänennamen in Cloud Manager erstellt haben, müssen Sie einen TXT-Eintrag hinzufügen, um das Eigentum an der Domäne zu überprüfen. Fahren Sie mit dem Dokument [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) fort, um mit der Einrichtung Ihres benutzerdefinierten Domänennamens fortzufahren.

## Hinzufügen eines benutzerdefinierten Domain-Namens auf der Umgebungsseite {#adding-cdn-environments}

Die Schritte zum Hinzufügen eines benutzerdefinierten Domänennamens von der Seite **Umgebungen** sind dieselben wie beim Hinzufügen eines benutzerdefinierten Domänennamens von der Seite &quot;Domäneneinstellungen&quot;(3) durch [, der Einstiegspunkt unterscheidet sich jedoch. ](#adding-cdn-settings) Führen Sie die folgenden Schritte von der Seite **Umgebungen** aus, um einen benutzerdefinierten Domain-Namen hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie zur Seite mit den **Umgebungsdetails** für die gewünschte Umgebung.

   ![Eingabe des Domain-Namens auf der Seite „Umgebungsdetails“](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Verwenden Sie die Tabelle **Domain-Namen**, um den benutzerdefinierten Domain-Namen zu übermitteln.

   1. Geben Sie den benutzerdefinierten Domain-Namen ein.
   1. Wählen Sie in der Dropdown-Liste das mit diesem Namen verknüpfte SSL-Zertifikat aus.
   1. Klicken Sie auf **+Hinzufügen**.

   ![Löschen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Das Dialogfeld **Domänennamen hinzufügen** wird auf der Registerkarte **Domänenname** geöffnet. Fahren Sie so fort wie bei [Hinzufügen eines benutzerdefinierten Domänennamens von der Seite &quot;Domäneneinstellungen&quot;.](#adding-cdn-settings)
