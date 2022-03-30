---
title: Hinzufügen eines benutzerdefinierten Domain-Namens
description: Erfahren Sie, wie Sie mit Cloud Manager einen benutzerdefinierten Domänennamen hinzufügen.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 0febf4b4a59617e6cc4f8414963c4a91fcf8765e
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 29%

---

# Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn}

Sie können einen benutzerdefinierten Domänennamen aus zwei Positionen in Cloud Manager hinzufügen:

* [Auf der Seite &quot;Domäneneinstellungen&quot;](#adding-cdn-settings)
* [Auf der Seite &quot;Umgebungen&quot;](#adding-cdn-environments)

>[!NOTE]
>
>Ein Benutzer muss über die **Business Owner** oder **Bereitstellungsmanager** Rolle, um einen benutzerdefinierten Domänennamen in Cloud Manager hinzuzufügen

## Hinzufügen eines benutzerdefinierten Domänennamens über die Seite &quot;Domäneneinstellungen&quot; {#adding-cdn-settings}

Führen Sie die folgenden Schritte aus, um einen benutzerdefinierten Domänennamen aus dem **Domäneneinstellungen** Seite.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.

1. Klicken Sie auf **Domäneneinstellungen** im linken Navigationsbereich.

   ![Fenster &quot;Domain Settings&quot;](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie auf **Domäne hinzufügen** Schaltfläche oben rechts, um die **Domänennamen hinzufügen** angezeigt.

   ![Dialogfeld &quot;Domäne hinzufügen&quot;](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Geben Sie den benutzerdefinierten Domänennamen in das **Domänenname** -Feld.

   >[!NOTE]
   >
   >Verwenden Sie bei der Eingabe Ihrer Domain weder `http://`, noch `https://` oder Leerzeichen.

1. Wählen Sie die **Umgebung** deren Dienst mit dem Domänennamen verknüpft wird.

1. Wählen Sie entweder **Veröffentlichen** oder **Vorschau** Dienst.

1. Wählen Sie die **SSL-Domänenzertifikat** mit dem Domänennamen aus der Dropdown-Liste verknüpft sind, und wählen Sie **Weiter**.

1. Die **Domänennamen hinzufügen** wird angezeigt und Sie gelangen zum Verifizierungsprozess für Domänennamen. Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen. Klicken Sie auf **Erstellen**.

   ![Überprüfung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Für die CDN-Implementierung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.

Siehe Dokument . [Überprüfen des Status des benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) , um mehr über verschiedene Status zu erfahren und mögliche Probleme zu beheben.

>[!NOTE]
>
>Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Verbreitung einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Siehe Dokument . [Überprüfen des Status des benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) für weitere Details.

>[!TIP]
>
>Siehe [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) , um mehr über TXT-Einträge zu erfahren.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Umgebungen {#adding-cdn-environments}

Führen Sie die folgenden Schritte aus, um einen benutzerdefinierten Domänennamen aus dem **Umgebungen** Seite.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zu **Umgebungsdetails** für die Umgebung von Interesse.

   ![Eingabe des Domänennamens auf der Seite &quot;Umgebungsdetails&quot;](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Verwenden Sie die **Domänennamen** -Tabelle, um den benutzerdefinierten Domänennamen zu senden.

   1. Geben Sie den benutzerdefinierten Domain-Namen ein.
   1. Wählen Sie in der Dropdown-Liste das mit diesem Namen verknüpfte SSL-Zertifikat aus.
   1. Klicken Sie auf **+ Hinzufügen**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Überprüfen Sie die in der Variablen **Domänennamen hinzufügen** und klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >
   >Nicht einschließen `http://`, `https://`, oder Leerzeichen bei der Eingabe im Domänennamen.

1. Die **Domänennamen hinzufügen** wird angezeigt und Sie gelangen zum Verifizierungsprozess für Domänennamen. Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen. Klicken Sie auf **Erstellen**.

   ![Überprüfung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Für die CDN-Implementierung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.

Siehe Dokument . [Überprüfen des Status des benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) , um mehr über verschiedene Status zu erfahren und mögliche Probleme zu beheben.

>[!NOTE]
>
>Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Verbreitung einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Siehe Dokument . [Überprüfen des Status des benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) für weitere Details.

>[!TIP]
>
>Siehe [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) , um mehr über TXT-Einträge zu erfahren.
