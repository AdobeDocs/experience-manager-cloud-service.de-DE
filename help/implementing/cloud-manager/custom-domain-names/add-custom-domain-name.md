---
title: Hinzufügen eines benutzerdefinierten Domain-Namens
description: Erfahren Sie, wie Sie mit Cloud Manager einen benutzerdefinierten Domain-Namen hinzufügen.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 0febf4b4a59617e6cc4f8414963c4a91fcf8765e
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 100%

---

# Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn}

In Cloud Manager können Sie einen benutzerdefinierten Domain-Namen aus zwei Positionen hinzufügen:

* [Auf der Seite „Domain-Einstellungen“](#adding-cdn-settings)
* [Auf der Seite „Umgebungen“](#adding-cdn-environments)

>[!NOTE]
>
>Benutzerinnen oder Benutzer müssen über die Rolle **Geschäftsinhaber** oder **Implementierungs-Manager** verfügen, um einen benutzerdefinierten Domain-Namen in Cloud Manager hinzuzufügen.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Domain-Einstellungen {#adding-cdn-settings}

Gehen Sie folgendermaßen vor, um auf der Seite **Domain-Einstellungen** einen benutzerdefinierten Domain-Namen hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsbereich auf **Domain-Einstellungen**.

   ![Fenster „Domain-Einstellungen“](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie auf die Schaltfläche **Domain hinzufügen** oben rechts, um den Dalog **Domain-Namen hinzufügen** anzuzeigen.

   ![Dialog „Domain hinzufügen“](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Geben Sie im Feld **Domain-Name** den Domain-Namen ein.

   >[!NOTE]
   >
   >Verwenden Sie bei der Eingabe Ihrer Domain weder `http://`, noch `https://` oder Leerzeichen.

1. Wählen Sie die **Umgebung** aus, deren Service mit dem Domain-Namen verknüpft werden soll.

1. Wählen Sie entweder den Service **Veröffentlichen** oder **Vorschau**.

1. Wählen Sie aus der Dropdown-Liste das **Domain-SSL-Zertifikat** aus, das mit dem Domain-Namen verknüpft ist, und klicken Sie auf **Weiter**.

1. Das Dialogfeld **Domain-Name hinzufügen** wird angezeigt und Sie gelangen zum Verifizierungsprozess für Domain-Namen. Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen. Klicken Sie auf **Erstellen**.

   ![Verifizierung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Für die CDN-Implementierung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.

Im Dokument [Überprüfen des Status des benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) erhalten Sie weitere Informationen zu den verschiedenen Status und dem Umgang mit potenziellen Problemen.

>[!NOTE]
>
>Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Verbreitung einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Weitere Einzelheiten finden Sie im Dokument [Überprüfung des Status von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

>[!TIP]
>
>Weitere Informationen zu TXT-Einträgen finden Sie unter [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md).

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Umgebungen {#adding-cdn-environments}

Führen Sie die folgenden Schritte von der Seite **Umgebungen** aus, um einen benutzerdefinierten Domain-Namen hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie zur Seite mit den **Umgebungsdetails** für die gewünschte Umgebung.

   ![Eingabe des Domain-Namens auf der Seite „Umgebungsdetails“](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Verwenden Sie die Tabelle **Domain-Namen**, um den benutzerdefinierten Domain-Namen zu übermitteln.

   1. Geben Sie den benutzerdefinierten Domain-Namen ein.
   1. Wählen Sie in der Dropdown-Liste das mit diesem Namen verknüpfte SSL-Zertifikat aus.
   1. Klicken Sie auf **+ Hinzufügen**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Markieren Sie ausgewählten Werte im Dialogfeld **Domain-Namen hinzufügen** und klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >
   >Geben Sie bei der Eingabe des Domain-Namens kein `http://`, `https://` oder Leerzeichen ein.

1. Das Dialogfeld **Domain-Name hinzufügen** wird angezeigt und Sie gelangen zum Verifizierungsprozess für Domain-Namen. Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen. Klicken Sie auf **Erstellen**.

   ![Verifizierung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Für die CDN-Implementierung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.

Im Dokument [Überprüfen des Status des benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) erhalten Sie weitere Informationen zu den verschiedenen Status und dem Umgang mit potenziellen Problemen.

>[!NOTE]
>
>Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Verbreitung einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Weitere Einzelheiten finden Sie im Dokument [Überprüfung des Status von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

>[!TIP]
>
>Weitere Informationen zu TXT-Einträgen finden Sie unter [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md).
