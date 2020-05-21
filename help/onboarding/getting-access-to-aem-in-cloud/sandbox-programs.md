---
title: Sandbox-Programm - Cloud-Dienst
description: Sandbox-Programm - Cloud-Dienst
translation-type: tm+mt
source-git-commit: eb874176c71d7f3d03d953f7bae4cb3db2ffb3b9
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---


# Sandbox-Programme {#sandbox-programs}

## Einführung {#introduction}

Ein Sandbox-Programm ist einer der beiden Typen von Programmen, die im AEM Cloud-Dienst verfügbar sind, wobei der andere ein reguläres Programm ist.

Eine Sandbox wird normalerweise für Schulungen, laufende Demos, Aktivierungsmaßnahmen oder POCs erstellt. Sie sind nicht dazu gedacht, Live-Verkehr zu transportieren.

Sandbox-Programm umfassen Sites und Assets und werden automatisch mit einer Git-Verzweigung geliefert, die Beispielcode, eine Development-Umgebung und eine Nicht-Produktions-Pipeline enthält.

Weitere Informationen zu Programm-Typen finden Sie unter [Einführung zu Programmen und Programm-Typen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html).

### Attribute von Sandbox-Programmen {#attributes-sandbox}

Sandbox-Programm haben die folgenden Attribute:

1. **Erstellung von Programmen:** Die Erstellung des Sandbox-Programms erfolgt automatisch:
   * Einrichtung des Projekts mit Beispielcode und Inhalt
   * Schaffung einer Umgebung für die Entwicklung
   * Erstellung von Nicht-Produktionslinien-Pipeline, die zur Entwicklungs-Umgebung bereitgestellt werden (Master-Zweig, der in der Umgebung für Entwicklung bereitgestellt wird)

1. **Dazu gehören:** Sandbox-Programm umfassen Sites und Assets.

1. **AEM-Updates:** AEM-Updates können manuell auf Umgebung in einem Sandbox-Programm angewendet werden und werden nicht automatisch gesendet.

1. **Hibernation:** Umgebung in einem Sandbox-Programm werden automatisch ausgeblendet, wenn für einen bestimmten Zeitraum keine Aktivität erkannt wird. Hibernated-Umgebung können manuell entfernt werden.

### Erstellen eines Sandbox-Programms {#creating-sandbox-program}

Ein Assistent zum Erstellen von Programmen fordert den Benutzer auf, Details zu übermitteln.

Informationen zum Erstellen eines Sandbox-Programms finden Sie unter [Erstellen eines Sandbox-Programms](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/creating-a-program.html#create-demo-program).

### Erstellen von Sandbox-Umgebung {#creating-sandbox-environments}

Sandbox-Programm werden zum Zeitpunkt der Erstellung des Programms automatisch in einer Umgebung bereitgestellt. Die Development-Umgebung wird standardmäßig mit einem Autor und einer Veröffentlichungsstufe geliefert.

Der Produktions-Stage-Umgebung-Satz kann manuell dem Sandbox-Programm hinzugefügt werden, wenn der Anwender bereit ist, eine Produktionspipeline einzurichten.

Informationen zum manuellen Erstellen einer Umgebung finden Sie unter [Hinzufügen von Umgebung](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments).

### Löschen von Sandbox-Umgebung  {#deleting-sandbox-environments}

Benutzer mit den erforderlichen Berechtigungen können eine Entwicklungs- oder Produktions-/Stage-Umgebung/Sätze löschen.

Informationen zum Löschen einer Umgebung finden Sie unter [Löschen von Umgebung](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#deleting-environment).


## Hibernating- und EntHibernating-Sandbox-Umgebung {#hibernating-introduction}

Sandbox-Programm-Umgebung werden nach einer Inaktivität in den *Ruhemodus* versetzt.

>[!NOTE]
>Hibernation ist einzigartig in Sandbox-Programm-Umgebung. Regelmäßige Umgebung des Programms werden nicht gehäutet.

### Hibernation {#hibernation-introduction}

Eine Ruhezeit kann entweder automatisch oder manuell erfolgen. Es kann bis zu ein paar Minuten dauern, bis eine Umgebung geheilt wird. Daten werden während der Winterzeit beibehalten.

Die Hibernation wird wie folgt kategorisiert:

* **Automatische** Sandbox-Programm-Umgebung werden nach achtstündiger Inaktivität automatisch ausgeblendet, d. h., weder der Autor- noch der Veröffentlichungsdienst erhalten eine Anforderung.

* **Manuell**: Die Kunden können eine Sandbox-Programm-Umgebung manuell löschen, dies ist jedoch nicht erforderlich, da die Bergung nach einer Inaktivität automatisch erfolgt.

#### Manuelle Bereinigung {#using-manual-hibernation}


Eine manuelle Bereinigung kann von einem der beiden Bildschirme in der Entwicklerkonsole aus erreicht werden.

Gehen Sie wie folgt vor, um Ihre Programm-Umgebung manuell zu berühren:

1. Navigieren Sie zur Developer Console.
1. Klicken Sie auf Hibernate
1. Klicken Sie zur Bestätigung auf Hibernate.
1. Nach erfolgreichem Beenden sehen Sie den folgenden Bildschirm.
1. Im Anzeigebereich &quot;Umgebung&quot;, der unten dargestellt wird und über den Sie auf den Link &quot;Umgebung&quot;im Bildschirm &quot;Umgebung&quot;klicken können, können Sie auf die Schaltfläche &quot;Hibernate&quot;in der Zeile der gewünschten Umgebung klicken. Daraufhin wird ein Bestätigungsbildschirm angezeigt.

### Enthibernation {#de-hibernation-introduction}

>[!IMPORTANT]
>Der Zugriff auf die Developer Console wird in der Admin-Konsole über die Rolle &quot;Cloud Manager - Entwickler&quot;definiert. Mit dieser Berechtigung kann ein Benutzer eine Umgebung löschen.

### Zugriff auf eine ausgeblendete Umgebung {#accessing-hibernated-environment}

Bei Browseranfragen zum Autoren- oder Veröffentlichungsstatus einer überzähligen Umgebung trifft der Benutzer auf eine Landingpage, die den Status der Umgebung beschreibt, wie nachfolgend dargestellt:

Ein Benutzer mit der Rolle &quot;Cloud Manager - Entwicklerrolle&quot;kann auf die Schaltfläche &quot;Developer Console&quot;klicken, um auf die Entwicklerkonsole zuzugreifen und die Umgebung zu deaktivieren. Informationen zum Festlegen von Rollen finden Sie in der Dokumentation zu Cloud Manager.

Wenn ein Benutzer in einem Unternehmen nicht auf die Schaltfläche &quot;Developer Console&quot;klicken kann, um in die Developer Console gelangen zu können, muss ihm wahrscheinlich die Schaltfläche &quot;Cloud Manager - Developer Role&quot;zugewiesen werden.




## AEM-Aktualisierungen für Sandbox-Umgebung {#aem-updates-sandbox}


Weitere Informationen finden Sie unter [AEM-Versionsupdates](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#version-updates).

Benutzer können AEM-Updates manuell auf die Umgebung in einem Sandbox-Programm anwenden (siehe Abbildung unten). Dies kann erfolgen, wenn der angezeigte Status AKTUALISIERBAR ist. Die Option &quot;Aktualisieren&quot;steht im Dropdown-Menü auf der Umgebung-Karte zur Verfügung. Sie kann auch im Menü &quot;Verwalten&quot;im Bildschirm &quot;UMGEBUNG&quot;ausgewählt werden.

>[!NOTE]
>Eine Nicht-Produktionsleitung, die in die Umgebung von Interesse für die Entwicklung einführt, muss konfiguriert werden, damit eine manuelle Aktualisierungspipeline initiiert werden kann.

>[!NOTE]
>Eine Produktionsleitung muss so konfiguriert sein, dass eine manuelle Update-Pipeline zur Produktions- und Stage-Umgebung gestartet werden kann.

>[!NOTE]
>Die manuelle Aktualisierung auf Produktions- oder Stage-Umgebung wird automatisch aktualisiert. Der Produktions- und Stage-Umgebung-Satz muss sich in derselben AEM-Version befinden.





