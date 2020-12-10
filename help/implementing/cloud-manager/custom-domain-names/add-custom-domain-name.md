---
title: Hinzufügen eines benutzerdefinierten Domänennamens
description: Hinzufügen eines benutzerdefinierten Domänennamens
translation-type: tm+mt
source-git-commit: 68a62be11f711e30b87dfc60a85627dceaf06caa
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Hinzufügen eines benutzerdefinierten Domänennamens {#adding-cdn}

Ein Benutzer muss Geschäftsinhaber oder Deployment Manager sein, um einen benutzerdefinierten Domänennamen in Cloud Manager hinzufügen zu können.

## Wichtige Überlegungen {#important-considerations}

* Bevor Sie einen benutzerdefinierten Domänennamen hinzufügen, muss ein gültiges SSL-Zertifikat mit dem benutzerdefinierten Domänennamen in Ihrem Programm installiert werden. Weitere Informationen finden Sie unter [SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) hinzufügen.

* Es kann jeweils nur ein Domänenname hinzugefügt werden. Benutzer können jedoch Platzhalter wie `*.wknd.com` als Domänennamen hinzufügen, sodass mehrere Subdomänen mit einem einzigen TXT-Datensatz gehostet werden können.

* Jede Cloud Manager-Umgebung kann bis zu 100 benutzerdefinierte Domänen pro Umgebung hosten.

* Derselbe Domänenname kann nicht auf mehr als einer Umgebung verwendet werden.

## Hinzufügen eines benutzerdefinierten Domänennamens über die Seite &quot;Domäneneinstellungen&quot; {#adding-cdn-settings}

Gehen Sie wie folgt vor, um auf der Seite &quot;Domäneneinstellungen&quot;einen benutzerdefinierten Domänennamen hinzuzufügen:

1. Navigieren Sie zum Bildschirm **Umgebung** von **Übersicht**.

1. Klicken Sie im linken Navigationsmenü auf **Domäneneinstellungen**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klicken Sie auf die Schaltfläche **Hinzufügen Domäne**, um das Dialogfeld **Hinzufügen Domänenname** zu öffnen.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create2.png)

1. Geben Sie unter **Domänenname** den benutzerdefinierten Domänennamen ein.

   >[!NOTE]
   >Bei der Eingabe in Ihre Domäne sollten Sie weder `http://` noch `https://` noch Leerzeichen einschließen.

1. Wählen Sie die Umgebung **aus, deren Veröffentlichungsdienst mit dem Domänennamen verknüpft wird.**

1. Wählen Sie in der Dropdownliste **SSL-Domänenzertifikat** aus und wählen Sie **Weiter**.

1. **hinzufügen Feld** Domänenname wird angezeigt. Dadurch gelangen Sie zur Domänennamenüberprüfung für Ihre Umgebung. Weitere Informationen finden Sie unter [Hinzufügen eines TXT-Datensatzes](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md).
Befolgen Sie die Anweisungen zum Nachweis des Domänenbesitzes für Ihre Umgebung.

1. Klicken Sie auf **Erstellen**.
1. Für die CDN-Bereitstellung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** gekennzeichnet.
1. Navigieren Sie zum Überprüfen des Status des benutzerdefinierten Domänennamens, um weitere Informationen zu verschiedenen Status und Adressen zu erhalten.

   >[!NOTE]
   >DNS-Testversand kann aufgrund von Verzögerungen bei der DNS-Verbreitung bis zu einigen Stunden erkennen. Cloud Manager überprüft die Eigentumsrechte und aktualisiert den Status, der in der Tabelle &quot;Domäneneinstellungen&quot;angezeigt werden kann. Weitere Informationen finden Sie unter Überprüfen des Domänennamenstatus.

## Hinzufügen eines benutzerdefinierten Domänennamens auf der Seite &quot;Umgebung&quot;{#adding-cdn-environments}

1. Navigieren Sie zur Seite &quot;Umgebung-Detail&quot;für die Umgebung von Interesse.
1. Verwenden Sie die Eingabefelder oben in der Tabelle &quot;Domänennamen&quot;, um den benutzerdefinierten Domänennamen (SSL-Zertifikat) zu senden. Wählen Sie Hinzufügen.
1. Hiermit wird der Assistent für den Namen Hinzufügen benutzerdefinierten Domäne mit dem Namen der Umgebung gestartet, der bereits ausgefüllt wurde.
1. Geben Sie den benutzerdefinierten Domänennamen ein. Hinweis: Bei der Eingabe in Ihre Domäne dürfen Sie `http://`, `https://` oder Leerzeichen nicht einschließen. Wählen Sie Weiter.
1. Dadurch gelangen Sie zur Domänennamenüberprüfung für Ihre Umgebung. Weitere Informationen finden Sie unter [Domänenüberprüfung](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md). Befolgen Sie die Anweisungen zum Nachweis des Domänenbesitzes für Ihre Umgebung.
1. Wählen Sie **Weiter**.
1. Für die CDN-Bereitstellung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** gekennzeichnet.

An dieser Stelle steht Ihr benutzerdefinierter Domänenname zum Testen bereit und ein `CNAME` zeigt darauf. Weitere Informationen zu verschiedenen Status und Adressen finden Sie unter Domänennamenstatus.

>[!NOTE]
>DNS-Testversand kann aufgrund von Verzögerungen bei der DNS-Verbreitung bis zu einigen Stunden erkennen. Cloud Manager überprüft die Eigentumsrechte und aktualisiert den Status, der in der Tabelle &quot;Domäneneinstellungen&quot;angezeigt werden kann. Weitere Informationen finden Sie unter Überprüfen des Domänennamenstatus.
