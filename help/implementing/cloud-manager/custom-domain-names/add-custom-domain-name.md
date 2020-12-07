---
title: Hinzufügen eines benutzerdefinierten Domänennamens
description: Hinzufügen eines benutzerdefinierten Domänennamens
translation-type: tm+mt
source-git-commit: 6571c11cedbc0d81fbdfd8072a39b1327bdba10b
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---


# Hinzufügen eines benutzerdefinierten Domänennamens {#adding-cdn}

Ein Benutzer muss Geschäftsinhaber oder Deployment Manager sein, um einen benutzerdefinierten Domänennamen in Cloud Manager hinzufügen zu können.

>[!NOTE]
>Bevor Sie einen benutzerdefinierten Domänennamen hinzufügen, muss ein gültiges SSL-Zertifikat mit dem benutzerdefinierten Domänennamen in Ihrem Programm installiert werden. Weitere Informationen finden Sie unter Installieren eines SSL-Zertifikats.

Es kann jeweils nur ein Domänenname hinzugefügt werden. Benutzer können jedoch Platzhalter wie `*.wknd.com` als Domänennamen hinzufügen, sodass mehrere Subdomänen mit einem einzigen TXT-Datensatz gehostet werden können.
Jede Cloud Manager-Umgebung kann bis zu 50 benutzerdefinierte Domänen pro Umgebung hosten.
Derselbe Domänenname kann nicht auf mehr als einer Umgebung verwendet werden.

## Hinzufügen eines benutzerdefinierten Domänennamens über die Seite &quot;Domäneneinstellungen&quot; {#adding-cdn-settings}

Gehen Sie wie folgt vor, um auf der Seite &quot;Domäneneinstellungen&quot;einen benutzerdefinierten Domänennamen hinzuzufügen:

1. Navigieren Sie auf der Seite **Umgebung** zur Seite &quot;Domäneneinstellungen&quot;.

1. Wählen Sie **Hinzufügen benutzerdefinierten Domänennamen** aus, um den Assistenten zum Hinzufügen benutzerdefinierter Domänennamen zu starten.

1. Geben Sie den benutzerdefinierten Domänennamen ein.

   >[!NOTE]
   >Bei der Eingabe in Ihre Domäne sollten Sie weder `http://` noch `https://` noch Leerzeichen einschließen.

1. Wählen Sie die Umgebung aus, deren Veröffentlichungsdienst mit dem Domänennamen verknüpft werden soll.

1. Wählen Sie das SSL-Zertifikat aus der Dropdown-Liste aus und wählen Sie Weiter.

1. Dadurch gelangen Sie zur Domänennamenüberprüfung für Ihre Umgebung. Weitere Informationen finden Sie unter Hinzufügen eines TXT-Datensatzes.

   >[!NOTE]
   >Befolgen Sie die Anweisungen zum Nachweis des Domänenbesitzes für Ihre Umgebung.

1. Wählen Sie Weiter.
1. Für die CDN-Bereitstellung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** gekennzeichnet.
1. Navigieren Sie zum Überprüfen des Status des benutzerdefinierten Domänennamens, um weitere Informationen zu verschiedenen Status und Adressen zu erhalten.

   >[!NOTE]
   >DNS-Testversand kann aufgrund von Verzögerungen bei der DNS-Verbreitung bis zu einigen Stunden erkennen. Cloud Manager überprüft die Eigentumsrechte und aktualisiert den Status, der in der Tabelle &quot;Domäneneinstellungen&quot;angezeigt werden kann. Weitere Informationen finden Sie unter Überprüfen des Domänennamenstatus.

## Hinzufügen eines benutzerdefinierten Domänennamens auf der Seite &quot;Umgebung&quot;{#adding-cdn-environments}

1. Navigieren Sie zur Seite &quot;Umgebung-Detail&quot;für die Umgebung von Interesse.
1. Verwenden Sie die Eingabefelder oben in der Tabelle &quot;Domänennamen&quot;, um den benutzerdefinierten Domänennamen (SSL-Zertifikat) zu senden. Wählen Sie Hinzufügen.
1. Hiermit wird der Assistent für den Namen Hinzufügen benutzerdefinierten Domäne mit dem Namen der Umgebung gestartet, der bereits ausgefüllt wurde.
1. Geben Sie den benutzerdefinierten Domänennamen ein. Hinweis: Bei der Eingabe in Ihre Domäne dürfen Sie `http://`, `https://` oder Leerzeichen nicht einschließen. Wählen Sie Weiter.
1. Dadurch gelangen Sie zur Domänennamenüberprüfung für Ihre Umgebung. Weitere Informationen finden Sie unter Domain Verification (Hinzufügen TXT Record).

   >[!NOTE]
   >Befolgen Sie die Anweisungen zum Nachweis des Domänenbesitzes für Ihre Umgebung.

1. Wählen Sie Weiter.
1. Für die CDN-Bereitstellung sind ein gültiges SSL-Zertifikat und eine erfolgreiche TXT-Überprüfung erforderlich. Dies wird durch den Status **Geprüft und bereitgestellt** gekennzeichnet.

An dieser Stelle steht Ihr benutzerdefinierter Domänenname zum Testen bereit und ein `CNAME` zeigt darauf. Weitere Informationen zu verschiedenen Status und Adressen finden Sie unter Domänennamenstatus.

>[!NOTE]
>DNS-Testversand kann aufgrund von Verzögerungen bei der DNS-Verbreitung bis zu einigen Stunden erkennen. Cloud Manager überprüft die Eigentumsrechte und aktualisiert den Status, der in der Tabelle &quot;Domäneneinstellungen&quot;angezeigt werden kann. Weitere Informationen finden Sie unter Überprüfen des Domänennamenstatus.
