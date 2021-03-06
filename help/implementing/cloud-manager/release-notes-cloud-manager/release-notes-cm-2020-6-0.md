---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.6.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.6.0
feature: Release Information
exl-id: 879a5025-f94f-4549-bf6e-e1cc6b6a7b58
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.6.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.6.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.6.0 von Cloud Manager in AEM as a Cloud Service wurde am 4. Juni 2020 veröffentlicht.

## Neue Funktionen {#whats-new-cloud-manager}

* Ein Benutzer mit der Rolle *Business Owner* in Cloud Manager kann jetzt ein Sandbox-Programm von der Landingpage (über die Schaltfläche für den Schnellzugriff auf der Programmkarte) oder aus dem Programm heraus löschen.

   Weitere Informationen finden Sie unter [Löschen eines Sandbox-Programms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html?lang=de).

* Ein Sandbox-Programmbenutzer mit der Rolle *Business Owner* oder *Bereitstellungs-Manager* in Cloud Manager kann jetzt seinen Satz von Produktions- und Staging-Umgebungen löschen, der über die Cloud Manager-Benutzeroberfläche festgelegt wurde. Die Löschoption ist jetzt sowohl auf der Umgebungskarte auf der Seite **Programmübersicht** als auch auf der Seite **Umgebungen** verfügbar. Durch Auswahl der Löschoption für die Produktions- oder Staging-Umgebung wird die jeweils andere Umgebung im Satz auch gelöscht.

   Weitere Informationen finden Sie unter [Löschen eines Sandbox-Programms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html).

* Coachmarks auf der Landingpage, die dem Benutzer grundlegende Informationen zur Navigation liefern.

* Coachmarks auf der Seite **Programm-Übersicht** informieren den Benutzer über die grundlegende Navigation in Cloud Manager, um ihm den Einstieg zu erleichtern.

* In Cloud Manager ist jetzt eine Seite mit **LERNMATERIALIEN** verfügbar, auf die Sie über die obere Navigationsleiste zugreifen können. Die Seite enthält Ressourcen, die Benutzer über die häufigsten Workflows für ihre entsprechende Rolle in Cloud Manager informieren.

* Sandbox-Programme werden jetzt anhand eines **Sandbox**-Symbol identifiziert, das auf der Programmkarte auf der Landingpage sowie neben dem Programmnamen auf der Seite **Programmübersicht angezeigt** wird.

* Ein Benutzer mit der SysAdmin-Rolle hat jetzt 1-Klick-Zugriff auf den Speicherort in Admin Console, von der aus Benutzerrollen oder Berechtigungen für Cloud Manager verwaltet werden können. Eine Schaltfläche **Zugriff verwalten** ist jetzt auf der Landingpage neben der Schaltfläche **Programm hinzufügen** verfügbar.

   Weitere Informationen finden Sie unter [SysAdmin-Aufgaben](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=de#sysadmin-tasks).

* Ein Benutzer mit der SysAdmin-Rolle hat kann jetzt direkt aus Cloud Manager per 1-Klick-Zugriff auf die Autoreninstanz zugreifen.

   Weitere Informationen finden Sie unter [Verwalten des Zugriffs auf die Autoreninstanz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=de#manage-access-aem).

* Das Erstellungsprotokoll enthält jetzt eine Liste der gefundenen Artefakte einschließlich übersprungener Inhaltspakete.

* Der Schritt „Erstellen“ überprüft jetzt, ob alle erstellten Inhaltspakete alle obligatorischen Eigenschaften enthalten: Name, Gruppe und Version.

* Der Schritt „Erstellen“ überprüft jetzt, ob der Build mindestens ein Inhaltspaket erstellt hat.

### Fehlerbehebungen {#bug-fixes-cm}

* Unter bestimmten Umständen wurden die Symbole im Dialogfeld **Programm erstellen** falsch ausgerichtet.

* Die AEM-Versionskennung wurde auf der Seite **Programmübersicht** nicht konsistent angezeigt.

* Bei der Konfiguration der Produktions-Pipeline war die Option **Geplante Bereitstellung** für einige Kunden nicht sichtbar.

### Bekannte Probleme {#known-issues-cm}

* Umgebungen innerhalb eines Sandbox-Programms werden ausgeblendet, wenn für eine bestimmte Dauer keine Aktivität erkannt wurde. Dieser Status wird in Cloud Manager nicht verfolgt. Der Status kann jedoch über die Developer Console verfolgt werden. Dies wird in einer kommenden Version adressiert.

* Der Link zur Developer Console direkt aus Cloud Manager zeigt die Option zum Versetzen der Umgebung eines Sandbox-Programms in den Ruhezustand und zum Aufheben des Ruhezustands nicht an. Um dies zu beheben, fügen Sie in der Developer Console das Muster `#release-cm-p1234-e5678` am Ende der URL hinzu, wobei *1234* die Programm-ID und *5678* die Umgebungs-ID ist. Dies wird in einer kommenden Version adressiert.
