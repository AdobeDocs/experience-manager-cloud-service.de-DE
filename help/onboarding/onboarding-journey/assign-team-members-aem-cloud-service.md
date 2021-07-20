---
title: 'Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service-Produktprofilen '
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder AEM as a Cloud Service-Produktprofilen zuweisen.
hide: true
hidefromtoc: true
index: false
source-git-commit: 8b30fc9494e152aa742cf17c02f982f5c9479473
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 2%

---


# Zuweisen zu AEM as a Cloud Service-Produktprofilen {#assign-team-members-cloud-service}

## Zielsetzung {#objective}

Dieses Dokument hilft Ihnen dabei, die Schritte zu verstehen, die Ihr Systemadministrator unternehmen muss, um Ihre Teammitglieder AEM als Cloud Service-Produktprofile zuzuweisen, und warum es wichtig ist, Ihren AEM-Autoren die Möglichkeit zu geben, mit AEM auf ihre Journey zuzugreifen.

Nach Lesen dieses Abschnitts sollten Sie Folgendes tun:

* Erfahren Sie, warum und wie Ihre Teammitglieder AEM as a Cloud Service-Produktprofilen zugewiesen werden
* Erfahren Sie, wie Sie Team-Mitglieder AEM Benutzerproduktprofil hinzufügen.
* Erfahren Sie, wie Sie Team-Mitglieder zum Produktprofil AEM Administratoren hinzufügen.


## Einführung {#introduction}

Um Zugriff auf AEM als Cloud Service zu erhalten, müssen Benutzer einem von zwei Produktprofilen angehören: &quot;AEM Benutzer&quot;oder &quot;AEM Administratoren&quot;. Ihren Teammitgliedern müssen Berechtigungen für die AEM-Instanz gewährt werden, da die Berechtigungen zum Verwalten von Cloud Manager nicht ausreichen. Weitere Informationen

>[!NOTE]
>Jeder Benutzer, der AEM Benutzerproduktprofil vom Systemadministrator zugewiesen wurde, hat (schreibgeschützt) Zugriff auf Cloud Manager.

## Voraussetzungen {#prerequisites}

* Produktprofile für AEM als Cloud Service
* Machen Sie sich mit Admin Console vertraut
* Ihren Team-Mitgliedern wurden entsprechend Cloud Manager-Produktprofile zugewiesen und Cloud-Ressourcen wurden eingerichtet.
* Details zu Ihrem Teammitglied: Der Systemadministrator muss über die Namen und E-Mail-Adressen sowie die Rollen und Zuständigkeiten der Teammitglieder verfügen, die Zugriff auf AEM als Cloud Service benötigen. Für das Onboarding empfehlen wir, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Rest des Onboarding fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie später eine größere Anzahl von Benutzern skalieren.


1. Bei Admin Console anmelden
(Wie zuvor)

1. Produktprofile AEM as a Cloud Service überprüfen
Von Admin Console aus können Sie die Liste der Cloud Manager-Profile sehen. Gehen Sie hierfür wie folgt vor:

1. Nachdem Sie sich bei Adobe Admin Console angemeldet haben, wählen Sie Adobe Experience Manager as a Cloud Service auf der Karte Produkte und Dienste aus:

1. Navigieren Sie zur Instanz (Autoreninstanz der Entwicklungsumgebung) und wählen Sie sie aus, wie im folgenden Bild dargestellt.



   Jetzt können Sie die Liste der AEM als Cloud Service-Produktprofile sehen, die einem Benutzer basierend auf seiner Rolle zugewiesen werden müssen. Weitere Informationen dazu finden Sie unter AEM as a Cloud Service - Produktprofile .




## Hinzufügen von Teammitgliedern zu AEM Benutzer- oder AEM Administrator-Produktprofil {#add-team-members}

Um Zugriff auf die AEMaaCS-Instanz zu erhalten, müssen Benutzer zu einem der beiden Produktprofile &quot;AEM Benutzer&quot;oder &quot;AEM Administratoren&quot;gehören.

>[!NOTE]
>Sie müssen über Berechtigungen für die Instanz verfügen. Berechtigungen zur Verwaltung von Cloud Manager reichen nicht aus. Weitere Informationen

Die folgenden Schritte müssen von einem Systemadministrator ausgeführt werden, der auch in der Rolle &quot;Business Owner&quot;tätig ist.

1. Navigieren Sie in Cloud Manager zu Cloud Manager und wählen Sie im Kontext der interessanten Umgebung die Schaltfläche Zugriff verwalten aus, wie unten dargestellt:

1. Nachdem Sie auf Zugriff verwalten geklickt haben, navigiert eine neue REGISTERKARTE zu der Admin Console, von der aus Sie Zugriff auf die Autoreninstanz der Umgebung haben. Wählen Sie &quot;AEM Administratoren&quot;oder &quot;AEM Benutzer&quot;basierend auf den Berechtigungen, die diese Person erteilen muss. Erfahren Sie mehr über AEM als Cloud Service-Produktprofile.

1. Wählen Sie Benutzer hinzufügen wie unten gezeigt aus und reichen Sie die erforderlichen Details ein, um das Hinzufügen des Teammitglieds abzuschließen:


1. Sie sollten diese Schritte für alle Umgebungen wiederholen, einschließlich Entwicklung, Staging und Produktion, wenn Sie über die Informationen der Teammitglieder verfügen, die Zugriff benötigen.

   Der Benutzer, den Sie hinzugefügt haben, hat jetzt Zugriff auf die AEM als Cloud Service-Autorendienste!


## Nächste Schritte {#whats-next}

Die Benutzer, die Sie AEMaaCS-Produktprofilen zugewiesen haben, können jetzt lernen, wie Sie auf die -Autoreninstanz zugreifen und sich mit Authoring-Seiten in AEM as a Cloud Service vertraut machen. Weitere Informationen

## Zusätzliche Ressourcen {#additional-resources}

Zugriff auf AEM konfigurieren (Videodurchlauf)
Schnellstartanleitung zum Verfassen von Seiten (Authoring)
