---
title: Hinzufügen eines benutzerdefinierten Domain-Namens
description: Hinzufügen eines benutzerdefinierten Domain-Namens
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 1eb9423b0128c952bc16cf0b8dff95b0e86964a0
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 92%

---

# Hinzufügen eines benutzerdefinierten Domain-Namens {#adding-cdn}

Ein Benutzer muss über die Rolle „Business Owner“ oder „Deployment Manager“ verfügen, um einen benutzerdefinierten Domain-Namen in Cloud Manager hinzuzufügen.

## Wichtige Überlegungen {#important-considerations}

* Vor dem Hinzufügen eines benutzerdefinierten Domain-Namens muss ein gültiges SSL-Zertifikat, das den benutzerdefinierten Domain-Namen enthält, in Ihrem Programm installiert werden. Weitere Informationen finden Sie unter [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).

* Domain-Namen können nicht zur Umgebung hinzugefügt werden, solange eine laufende Pipeline an diese Umgebung angeschlossen ist.

* Es kann jeweils nur ein Domain-Name hinzugefügt werden. Domains können jedoch keine Platzhalter enthalten. Benutzerdefinierte Domains werden auf der Autorenseite nicht unterstützt.

* AEM as a Cloud Service unterstützt keine Platzhalterdomänen.

* Jede Cloud Manager-Umgebung kann bis zu 250 benutzerdefinierte Domains pro Umgebung hosten.

* Derselbe Domain-Name kann nicht in mehr als einer Umgebung verwendet werden.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Domain-Einstellungen {#adding-cdn-settings}

Gehen Sie wie folgt vor, um über die Seite mit den Domain-Einstellungen einen benutzerdefinierten Domain-Namen hinzuzufügen:

1. Navigieren Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.

1. Klicken Sie im linken Navigationsmenü auf **Domain-Einstellungen**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie auf die Schaltfläche **Domain hinzufügen**, um das Dialogfeld **Domain-Name hinzufügen** zu öffnen.

   ![](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Geben Sie unter **Domain-Name** den benutzerdefinierten Domain-Namen ein.

   >[!NOTE]
   >Bei der Eingabe Ihrer Domain sollten Sie weder `http://`, noch `https://` oder Leerzeichen verwenden.

1. Wählen Sie die **Umgebung** aus, deren Veröffentlichungs-Service mit dem Domain-Namen verknüpft werden soll.

1. Wählen Sie den Dienst entweder als **Publish** oder **Vorschau** aus.

   >[!NOTE]
   >Benutzerdefinierte Domänennamen werden jetzt in Cloud Manager für Sites-Programme sowohl für Veröffentlichungs- als auch für Vorschaudienste unterstützt. Jede Cloud Manager-Umgebung kann bis zu 250 benutzerdefinierte Domains pro Umgebung hosten. Weitere Informationen zum Vorschaudienst finden Sie unter [Vorschaudienst](/help/implementing/cloud-manager/manage-environments.md#preview-service).

1. Wählen Sie aus der Dropdown-Liste das **SSL-Zertifikat der Domain** und anschließend **Weiter** aus.

1. Das Dialogfeld **Domain-Name hinzufügen** wird angezeigt. Dadurch gelangen Sie zum Bildschirm mit der Domain-Namensüberprüfung für Ihre Umgebung. Weitere Informationen finden Sie unter [Hinzufügen eines TXT-Eintrags](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md).

   Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen:

1. Klicken Sie auf **Erstellen**.
1. Für die CDN-Implementierung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.
Unter [Überprüfen des benutzerdefinierten Domain-Namenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) erhalten Sie weitere Informationen zu den verschiedenen Status und dem Umgang damit.

   >[!NOTE]
   >Der DNS-Testversand kann aufgrund von Verzögerungen bei der DNS-Verbreitung bis zu einigen Stunden dauern. Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Weitere Informationen finden Sie unter „Überprüfen des Status eines Domain-Namens“.

## Hinzufügen eines benutzerdefinierten Domain-Namens über die Seite mit den Umgebungen {#adding-cdn-environments}

1. Navigieren Sie zur Seite mit den Umgebungsdetails für die gewünschte Umgebung.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Verwenden Sie die Eingabefelder oben in der Domain-Namenstabelle, um den benutzerdefinierten Domain-Namen zu senden, und wählen Sie das SSL-Zertifikat in der Dropdown-Liste aus. Klicken Sie auf **+ Hinzufügen**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Markieren Sie die Felder im Dialogfeld **Domain-Namen hinzufügen** und klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >Verwenden Sie bei der Eingabe Ihrer Domain weder `http://`, noch `https://` oder Leerzeichen.

1. Der Bildschirm mit der Domain-Namensüberprüfung für Ihre Umgebung wird angezeigt.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   Weitere Informationen finden Sie unter [Domain-Überprüfung](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md). Befolgen Sie die Anweisungen, um die Domain-Eigentümerschaft für Ihre Umgebung nachzuweisen.

1. Klicken Sie auf **Erstellen**.

1. Für die Implementierung eines benutzerdefinierten Domain-Namens sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** angezeigt.

Zu diesem Zeitpunkt ist Ihr benutzerdefinierter Domain-Name bereit zum Testen und ein `CNAME`, der auf ihn verweist. Unter [Domain-Namenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) erhalten Sie weitere Informationen zu den verschiedenen Status und dem Umgang damit.

>[!NOTE]
>Der DNS-Testversand kann aufgrund von Verzögerungen bei der DNS-Verbreitung bis zu einigen Stunden dauern. Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Weitere Informationen finden Sie unter „Überprüfen des Status eines Domain-Namens“.
