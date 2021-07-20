---
title: Einrichten von Cloud-Ressourcen über Cloud Manager
description: Auf dieser Seite erfahren Sie, wie Sie Cloud-Ressourcen über Cloud Manager einrichten
hide: true
hidefromtoc: true
index: false
source-git-commit: 021146e4e1d65c7fe81ed3dba70b32daf34b9704
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 0%

---

# Einrichten von Cloud-Ressourcen über Cloud Manager {#setup-cloud-resources}

Der Systemadministrator, der der Rolle &quot;Business Owner&quot;zugewiesen ist, sollte auf Cloud Manager zugreifen und sich dort anmelden. Danach muss sich ein Team-Mitglied, das dem Produktprofil &quot;Business Owner&quot;zugewiesen ist, bei Cloud Manager anmelden und Ihr Cloud-Programm und Ihre Umgebungen erstellen, damit Ihr Expertenteam beginnen kann.

## Zielsetzung {#objective}

In diesem Dokument erfahren Sie, wie Ihre Cloud-Ressourcen erstellt werden und wer sie verwenden kann.

Nach Lesen dieses Abschnitts sollten Sie Folgendes tun:

* Beachten Sie, dass ein Systemadministrator, der der Rolle &quot;Business Owner&quot;zugewiesen ist, als erster auf Cloud Manager zugreifen und sich dort anmelden muss.
* Erfahren Sie, wie Ihr Cloud-Programm und Ihre Umgebungen erstellt werden.

## Einführung {#introduction}

Das Hinzufügen Ihrer Cloud-Ressourcen erfolgt über Cloud Manager durch Ihr Team-Mitglied, das dem Cloud Manager Business Owner-Produktprofil zugewiesen ist. Diese Person ist in der Regel eine Person, die die Geschäftsanforderungen versteht und die Ersteinrichtung von Cloud Manager abschließt.

In den folgenden Abschnitten erfahren Sie, wie Sie Ihre [Cloud Service-Programme](#create-cloud-service-program) und [Umgebungen](#create-cloud-environments) erstellen.

### Voraussetzungen {#prerequisites}

* Der Systemadministrator, der der Rolle &quot;Business Owner&quot;zugewiesen ist, sollte auf Cloud Manager zugreifen und sich dort anmelden.

* Informationen zur Navigation und Anmeldung bei Cloud Manager

* Kennenlernen von Cloud Manager-Produktprofilen

* Machen Sie sich mit den Überlegungen zur Programmerstellung vertraut. Sehen Sie sich dieses Video an, um mehr zu erfahren.

* Grundlegendes zu den Konzepten von Cloud Manager-Programmen und -Umgebungen

## Navigieren zu Cloud Manager {#navigate-cloud-manager}

1. Der Benutzer &quot;Business Owner&quot;erhält eine Begrüßungs-E-Mail, von der aus er starten kann. Wenn er sie nicht finden kann, navigieren Sie direkt zu experience.adobe.com und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie auf der Startseite Experience Cloud Experience Manager aus:


1. Dadurch gelangen Sie zur AEM Homepage. Wählen Sie hier Cloud Manager aus:


1. Dadurch gelangen Sie zur Landingpage von Cloud Manager, wie unten dargestellt:


1. Überprüfen Sie jetzt, ob Ihnen das Produktprofil Business Owner zugewiesen wurde. Wählen Sie dazu Ihr Profil oben rechts wie unten gezeigt aus:


1. Wählen Sie nun Benutzerrollen aus und stellen Sie sicher, dass Sie Business Owner zugewiesen sind.


   Gute Arbeit! Sie haben sich erfolgreich als Business Owner bei Cloud Manager angemeldet!

## Erstellen des Cloud Service-Programms {#create-cloud-service-program}


1. Navigieren Sie zur Landingpage von Cloud Manager , wie unten dargestellt.

   >[!NOTE]
   >Sie müssen ein Team-Mitglied sein, das dem Cloud Manager Business Owner-Produktprofil zugewiesen ist, um diesen Schritt erfolgreich abzuschließen.

1. Wählen Sie hier Programm hinzufügen aus, um den Assistenten Programm hinzufügen zu starten. Sehen Sie sich das Video an, um zu erfahren, wie Sie Ihr AEMaaCS-Programm erstellen, und wichtige Überlegungen vor der Erstellung Ihres Programms an.

1. Eine schrittweise Anleitung zur Verwendung des Assistenten Programm hinzufügen finden Sie hier.

   >[!CAUTION]
   >Beachten Sie, dass der Programmname nach der Erstellung nicht mehr geändert werden kann. Wir empfehlen Ihnen, sich bezüglich des Namens, den Sie Ihrem Programm geben möchten, sicher zu sein.

   Falls Sie den Programmnamen ändern müssen, müssen Sie sich an den Support der Adobe wenden oder sich alternativ an Ihren Kundenbetreuer der Adobe wenden. Sie werden dazu beitragen, das Programm effektiv zu löschen. Sie müssen von Anfang an mit einem potenziellen Verlust an Arbeit beginnen, den Ihr Team geleistet hat.

1. Nach erfolgreicher Erstellung Ihres Cloud-Programms können Sie zu Ihrem Programm navigieren, um die Übersichtsseite Ihres Programms wie unten dargestellt anzuzeigen:

1. Wenn Sie dies noch nicht getan haben, ist es jetzt an der Zeit, Ihre Entwickler-Mitglieder Ihrem Cloud Manager-Team hinzuzufügen, navigieren Sie zu Benutzer zum Entwicklerproduktprofil hinzufügen und führen Sie die beschriebenen Schritte aus.

1. Mitglieder, die dem Produktprofil &quot;Entwickler&quot;zugewiesen sind, können sich bei Cloud Manager anmelden und Cloud Manager Git verwalten.


   Gute Arbeit! Nachdem Ihr Programm erfolgreich erstellt wurde, können Ihre Entwickler auf Ihr Cloud Manager-Git zugreifen!


## Erstellen von Cloud-Umgebungen {#create-cloud-environments}

1. Nachdem Sie Ihr Cloud-Programm erfolgreich erstellt haben, erstellen Sie Ihre Cloud-Umgebungen, indem Sie zur Cloud Manager-Übersichtsseite navigieren und auf der Umgebungskarte Hinzufügen auswählen.

   >[!NOTE]
   >Ein Cloud Manager-Benutzer mit der Rolle Business Owner oder Deployment Manager muss angemeldet sein, um diesen Schritt erfolgreich durchführen zu können.

   Sehen Sie sich außerdem das Schnellvideo-Tutorial an, um mehr über Cloud Manager-Umgebungen und darüber zu erfahren, wie Sie sie Ihrem Programm hinzufügen können.

1. Dadurch wird der Assistent zum Hinzufügen der Umgebung gestartet, der Sie beim Hinzufügen Ihrer Umgebung unterstützt. Fügen Sie zuerst Ihre Entwicklungsumgebung hinzu, um sich kennenzulernen.

1. Wenn Sie dies noch nicht getan haben, können Sie jetzt Ihre Entwickler-Mitglieder zu Ihrem Cloud Manager-Team hinzufügen, zu Benutzer zum Entwicklerproduktprofil hinzufügen navigieren und die beschriebenen Schritte ausführen. Auf diese Weise können Ihre Entwickler mit dem Navigieren zu Cloud Manager und Verwalten von Cloud Manager Git beginnen.


   Herzlichen Glückwunsch! Jetzt wurden Ihre Cloud-Programmumgebungen erstellt und Ihre Entwickler wurden zum Team hinzugefügt!

## Nächste Schritte {#whats-next}

Jetzt müssen Ihren Teammitgliedern Berechtigungen für die Instanz erteilt werden, da die Berechtigungen zum Verwalten von Cloud Manager nicht ausreichen. Nachdem Ihre Cloud-Ressourcen erstellt wurden und für den Zugriff durch Ihr Team bereit sind, muss der Systemadministrator Ihre Team-Mitglieder AEM als Cloud Service-Produktprofile aus Admin Console zuweisen.

>[!NOTE]
>Um Zugriff auf AEM als Cloud Service zu erhalten, müssen Benutzer einem von zwei Produktprofilen &quot;AEM Benutzer&quot;oder &quot;AEM Administratoren&quot;angehören. Weitere Informationen

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* Programmtypen und Hinzufügen eines Programms
* Umgebungstypen und Hinzufügen einer Umgebung
* Verwalten von Cloud Manager Git
* Zugriff auf AEM als Cloud Service von Admin Console konfigurieren
