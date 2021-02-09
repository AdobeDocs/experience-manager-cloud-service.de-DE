---
title: Hinzufügen eines benutzerdefinierten Domain-Namens
description: Hinzufügen eines benutzerdefinierten Domain-Namens
translation-type: tm+mt
source-git-commit: 148a1f478aeabea970e46e7e565fccca7db6a7e9
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 55%

---


# Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn}

Ein Benutzer muss über die Rolle „Business Owner“ oder „Deployment Manager“ verfügen, um einen benutzerdefinierten Domain-Namen in Cloud Manager hinzuzufügen.

## Wichtige Überlegungen {#important-considerations}

* Vor dem Hinzufügen eines benutzerdefinierten Domain-Namens muss ein gültiges SSL-Zertifikat, das den benutzerdefinierten Domain-Namen enthält, in Ihrem Programm installiert werden. Weitere Informationen finden Sie unter [SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) hinzufügen.

* Domänennamen können nicht zu Umgebung hinzugefügt werden, solange eine laufende Pipeline an diese Umgebung angeschlossen ist.

* Es kann jeweils nur ein Domain-Name hinzugefügt werden. Domänen können jedoch keine Platzhalter enthalten. Benutzerdefinierte Domänen auf der Autorenseite werden nicht unterstützt.

* Jede Cloud Manager-Umgebung kann bis zu 100 benutzerdefinierte Domains pro Umgebung hosten.

* Derselbe Domain-Name kann nicht in mehr als einer Umgebung verwendet werden.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Domain-Einstellungen {#adding-cdn-settings}

Gehen Sie wie folgt vor, um über die Seite mit den Domain-Einstellungen einen benutzerdefinierten Domain-Namen hinzuzufügen:

1. Navigieren Sie zum Bildschirm **Umgebung** von **Übersicht**.

1. Klicken Sie im linken Navigationsmenü auf **Domäneneinstellungen**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie auf die Schaltfläche **Hinzufügen Domäne**, um das Dialogfeld **Hinzufügen Domänenname** zu öffnen.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create2.png)

1. Geben Sie unter **Domänenname** den benutzerdefinierten Domänennamen ein.

   >[!NOTE]
   >Bei der Eingabe Ihrer Domain sollten Sie keine `http://`, `https://` oder Leerzeichen verwenden.

1. Wählen Sie die Umgebung **aus, deren Veröffentlichungsdienst mit dem Domänennamen verknüpft wird.**

1. Wählen Sie in der Dropdownliste **SSL-Domänenzertifikat** aus und wählen Sie **Weiter**.

1. **hinzufügen Feld** Domänenname wird angezeigt. Dadurch gelangen Sie zum Bildschirm mit der Domain-Namensüberprüfung für Ihre Umgebung. Weitere Informationen finden Sie unter [Hinzufügen eines TXT-Datensatzes](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md).

   Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen:

1. Klicken Sie auf **Erstellen**.
1. Für die CDN-Implementierung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.
Navigieren Sie zu [Überprüfen Sie den Status der benutzerdefinierten Domäne](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md), um weitere Informationen zu verschiedenen Status und Adressen zu erhalten.

   >[!NOTE]
   >Der DNS-Testversand kann aufgrund von Verzögerungen bei der DNS-Verbreitung bis zu einigen Stunden dauern. Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Weitere Informationen finden Sie unter „Überprüfen des Status eines Domain-Namens“.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Umgebungen {#adding-cdn-environments}

1. Navigieren Sie zur Detailseite &quot;Umgebung&quot;für die Umgebung von Interesse.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Verwenden Sie die Eingabefelder oben in der Tabelle &quot;Domänennamen&quot;, um den benutzerdefinierten Domänennamen zu senden, und wählen Sie das SSL-Zertifikat in der Dropdown-Liste aus. Klicken Sie auf **+ Hinzufügen**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Markieren Sie die Felder im Dialogfeld **Hinzufügen Domänenname** und klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >Bei der Eingabe in Ihre Domäne dürfen Sie `http://`, `https://` oder Leerzeichen nicht einschließen.

1. Die Überprüfung des Domänennamens für Ihre Umgebung wird angezeigt.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   Weitere Informationen finden Sie unter [Domänenüberprüfung](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md). Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen.

1. Klicken Sie auf **Erstellen**.

1. Für die Bereitstellung benutzerdefinierter Domänennamen sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.

Zu diesem Zeitpunkt ist Ihr benutzerdefinierter Domain-Name bereit zum Testen und ein `CNAME`, der auf ihn verweist. Weitere Informationen zu verschiedenen Status und zur Adressierung finden Sie unter [Domänennamenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

>[!NOTE]
>Der DNS-Testversand kann aufgrund von Verzögerungen bei der DNS-Verbreitung bis zu einigen Stunden dauern. Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Weitere Informationen finden Sie unter „Überprüfen des Status eines Domain-Namens“.
