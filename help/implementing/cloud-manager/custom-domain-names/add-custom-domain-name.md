---
title: Hinzufügen eines benutzerdefinierten Domain-Namens
description: Erfahren Sie, wie Sie mit Cloud Manager einen benutzerdefinierten Domain-Namen hinzufügen.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 600288a87e024fbe58ff605a8bcdc61535cc0759
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 74%

---

# Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn}

In Cloud Manager können Sie einen benutzerdefinierten Domain-Namen aus zwei Positionen hinzufügen:

* [Auf der Seite „Domain-Einstellungen“](#adding-cdn-settings)
* [Auf der Seite „Umgebungen“](#adding-cdn-environments)

>[!NOTE]
>
>Ein Benutzer muss über die **Business Owner** oder **Bereitstellungsmanager** Rolle, um einen benutzerdefinierten Domänennamen in Cloud Manager hinzuzufügen, und Sie müssen das schnelle CDN verwenden.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Domain-Einstellungen {#adding-cdn-settings}

Gehen Sie folgendermaßen vor, um auf der Seite **Domain-Einstellungen** einen benutzerdefinierten Domain-Namen hinzuzufügen. Wenn Sie ein anderes CDN als das bereitgestellte verwenden, funktionieren diese Schritte nicht für Sie und Sie müssen Ihre Domäne mit dem von Ihnen eingerichteten CDN konfigurieren.

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

1. Wählen Sie die **Umgebung** deren Dienst mit dem Domänennamen verknüpft ist.

1. Wählen Sie entweder den Service **Veröffentlichen** oder **Vorschau**.

1. Wählen Sie aus der Dropdown-Liste das **Domain-SSL-Zertifikat** aus, das mit dem Domain-Namen verknüpft ist, und klicken Sie auf **Weiter**.

1. Das Dialogfeld **Domain-Name hinzufügen** wird angezeigt und Sie gelangen zum Verifizierungsprozess für Domain-Namen. Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen. Klicken Sie auf **Erstellen**.

   ![Verifizierung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Für die CDN-Bereitstellung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.

Siehe [Überprüfen des Status des benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) , um mehr über verschiedene Status zu erfahren und mögliche Probleme zu beheben.

>[!NOTE]
>
>Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Verbreitung einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Siehe [Überprüfen des Status des benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) für weitere Details.

>[!TIP]
>
>Siehe [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) , um mehr über TXT-Einträge zu erfahren.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Umgebungen {#adding-cdn-environments}

Führen Sie die folgenden Schritte von der Seite **Umgebungen** aus, um einen benutzerdefinierten Domain-Namen hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie zur Seite mit den **Umgebungsdetails** für die gewünschte Umgebung.

   ![Eingabe des Domain-Namens auf der Seite „Umgebungsdetails“](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Verwenden Sie die Tabelle **Domain-Namen**, um den benutzerdefinierten Domain-Namen zu übermitteln.

   1. Geben Sie den benutzerdefinierten Domain-Namen ein.
   1. Wählen Sie in der Dropdown-Liste das mit diesem Namen verknüpfte SSL-Zertifikat aus.
   1. Klicken Sie auf **+ Hinzufügen**.

   ![Benutzerspezifischen Domänennamen hinzufügen](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Markieren Sie ausgewählten Werte im Dialogfeld **Domain-Namen hinzufügen** und klicken Sie auf **Weiter**.

   ![Fenster &quot;Domänenname&quot;](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >
   >Geben Sie bei der Eingabe des Domain-Namens kein `http://`, `https://` oder Leerzeichen ein.

1. Das Dialogfeld **Domain-Name hinzufügen** wird angezeigt und Sie gelangen zum Verifizierungsprozess für Domain-Namen. Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen. Klicken Sie auf **Erstellen**.

   ![Verifizierung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Für die CDN-Bereitstellung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.

Siehe [Überprüfen des Status des benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) , um mehr über verschiedene Status zu erfahren und mögliche Probleme zu beheben.

>[!NOTE]
>
>Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Verbreitung einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Siehe [Überprüfen des Status des benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) für weitere Details.

>[!TIP]
>
>Siehe [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) , um mehr über TXT-Einträge zu erfahren.
