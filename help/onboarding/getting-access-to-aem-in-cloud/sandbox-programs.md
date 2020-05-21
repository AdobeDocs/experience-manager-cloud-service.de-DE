---
title: Sandbox-Programm - Cloud-Dienst
description: Sandbox-Programm - Cloud-Dienst
translation-type: tm+mt
source-git-commit: e25e22c5d61defb3402e51b97c1d5364465e1027
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 1%

---


# Sandbox-Programme {#sandbox-programs}

## Einführung {#introduction}

Ein Sandbox-Programm ist einer der beiden Typen von Programmen, die im AEM Cloud-Dienst verfügbar sind, wobei der andere ein reguläres Programm ist.

Eine Sandbox wird normalerweise für Schulungen, laufende Demos, die Aktivierung oder den Testversand von Concept (POC) erstellt. Sie sind nicht dazu gedacht, Live-Verkehr zu transportieren.

Sandbox-Programm umfassen Sites und Assets und werden automatisch mit einer Git-Verzweigung gefüllt, die Beispielcode, eine Development-Umgebung und eine Nicht-Produktions-Pipeline enthält.

Weitere Informationen zu den Programm-Typen finden Sie unter [Einführung zu Programmen und Programmen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html) .

### Attribute von Sandbox-Programmen {#attributes-sandbox}

Sandbox-Programm haben die folgenden Attribute:

1. **Programm-Erstellung:** Die Erstellung des Sandbox-Programms erfolgt automatisch:
   * Einrichtung des Projekts mit Beispielcode und Inhalt
   * Schaffung einer Umgebung für die Entwicklung
   * Erstellung von Nicht-Produktionslinien-Pipeline, die zur Entwicklungs-Umgebung bereitgestellt werden (Bereitstellung der Hauptverzweigung zur Umgebung der Entwicklung)

1. **Lösungen:** Sandbox-Programm umfassen AEM-Sites und -Assets.

1. **AEM-Aktualisierungen:** AEM-Updates können manuell auf Umgebung in einem Sandbox-Programm angewendet werden und werden nicht automatisch gesendet.

1. **Hibernation:** Umgebung in einem Sandbox-Programm werden automatisch ausgeblendet, wenn für einen bestimmten Zeitraum keine Aktivität erkannt wird. Hibernated-Umgebung können manuell entfernt werden.

### Erstellen eines Sandbox-Programms {#creating-sandbox-program}

Mit einem Assistenten zum Erstellen von Programmen können Sie ein Sandbox-Programm erstellen.

Informationen zum Erstellen eines Sandbox-Programms finden Sie unter

### Erstellen von Sandbox-Umgebung {#creating-sandbox-environments}

Sandbox-Programm werden zum Zeitpunkt der Erstellung des Programms automatisch in einer Umgebung bereitgestellt. Die Development-Umgebung umfasst standardmäßig einen Autor und eine Veröffentlichungsstufe.

Der Produktions-Stage-Umgebung-Satz kann manuell dem Sandbox-Programm hinzugefügt werden, wenn der Anwender bereit ist, eine Produktionspipeline einzurichten.

Weitere Informationen zum manuellen Erstellen einer Umgebung finden Sie unter [Hinzufügen von Umgebung](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments) .

### Löschen von Sandbox-Umgebung {#deleting-sandbox-environments}

Benutzer mit den erforderlichen Berechtigungen können eine Entwicklungs- oder Produktions-/Stage-Umgebung oder -Sets löschen.

Weitere Informationen zum Löschen einer Umgebung finden Sie unter [Löschen von Umgebung](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#deleting-environment) .


## Hibernating- und EntHibernating-Sandbox-Umgebung {#hibernating-introduction}

Sandbox-Programm-Umgebung werden in den *Ruhezustand* versetzt, wenn für einen bestimmten Zeitraum keine Aktivität erkannt wird.

>[!NOTE]
>Hibernation ist einzigartig in Sandbox-Programm-Umgebung. Regelmäßige Umgebung des Programms führen nicht zu Hibernationen.

### Hibernation {#hibernation-introduction}

Eine Ruhezeit kann entweder automatisch oder manuell erfolgen. Es kann einige Minuten dauern, bis Sandbox-Programm-Umgebung in den *Ruhezustand* wechseln. Daten werden während der Winterzeit beibehalten.

Die Hibernation wird wie folgt kategorisiert:

* **Automatische** Sandbox-Programm-Umgebung werden nach achtstündiger Inaktivität automatisch ausgeblendet, d. h., weder Autor- noch Veröffentlichungsdienste erhalten eine Anfrage.

* **Manuell**: Als Benutzer können Sie eine Sandbox-Programm-Umgebung manuell löschen, obwohl dies nicht erforderlich ist, da eine Ruhezeit nach einer bestimmten Inaktivität (acht Stunden) automatisch eintritt.

#### Manuelle Bereinigung {#using-manual-hibernation}

Sie können Ihr Sandbox-Programm in der Developer Console auf zwei verschiedene Arten manuell löschen:

* Detailbildschirm der Umgebung
* Bildschirm zur Umgebung

Gehen Sie wie folgt vor, um Ihre Sandbox-Programm-Umgebung manuell zu löschen:

1. Navigieren Sie zur **Developer Console**.
Informationen zum Zugriff auf die [Developer Console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#accessing-developer-console) über die Karte für **Umgebung** finden Sie unter Zugriff auf die Developer Console **** .

1. Click **Hibernate**, as shown in the figure below:

   ![](assets/hibernate-1.png)

   Oder

   Klicken Sie in der Liste Umgebung auf **Hibernate** , wie in der folgenden Abbildung dargestellt:

   ![](assets/hibernate-1b.png)

1. Klicken Sie auf **Hibernate** , um den Schritt zu bestätigen.

   ![](assets/hibernate-2.png)

1. Nach erfolgreichem Beenden des Ruhezustands wird im Bildschirm &quot; **Developer Console** &quot;die Benachrichtigung zum Abschluss des Ruhezustands für Ihre Umgebung angezeigt.

   ![](assets/hibernate-4.png)


### Enthibernation {#de-hibernation-introduction}

1. Navigieren Sie zur **Developer Console**.
Informationen zum Zugriff auf die [Developer Console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#accessing-developer-console) über die Karte für **Umgebung** finden Sie unter Zugriff auf die Developer Console **** .

   >[!IMPORTANT]
   >Der Zugriff auf die Developer Console wird von der **Cloud Manager - Entwicklerrolle** in der **Admin-Konsole** definiert. Ein Benutzer mit der Berechtigung für die Rolle &quot;Entwickler&quot;kann eine Sandbox-Programm-Umgebung deaktivieren.

1. Click on **De-hibernate**, as shown in the figure below:

   ![](assets/de-hibernation-img1.png)

   Oder

   Klicken Sie auf **Enthibernate** aus der Liste der **Umgebung** , wie in der folgenden Abbildung dargestellt:

   ![](assets/de-hibernate-1b.png)


1. Klicken Sie auf **De Hibernate** , um den Schritt zu bestätigen.

   ![](assets/de-hibernation-img2.png)

1. Sie erhalten die Benachrichtigung, dass der Bereinigungsprozess begonnen hat, und Sie werden über den Fortschritt informiert.

   ![](assets/de-hibernation-img3.png)

1. Nach Abschluss des Vorgangs ist die Sandbox-Programm-Umgebung erneut aktiv.

   ![](assets/de-hibernation-img4.png)

#### Zugriff auf eine ausgeblendete Umgebung {#accessing-hibernated-environment}

Bei Browseranfragen zum Autoren- oder Veröffentlichungsstatus einer überzähligen Umgebung wird dem Benutzer eine Landingpage angezeigt, die den Status der Umgebung beschreibt, wie in der folgenden Abbildung dargestellt:

![](assets/de-hibernation-img5.png)


Ein Benutzer mit **Cloud Manager - Entwicklerrolle** kann auf die **Developer Console** klicken, um auf die Entwicklerkonsole zuzugreifen und die Umgebung zu deaktivieren.

>[!NOTE]
> Für viele Funktionen in Cloud Manager sind spezielle Berechtigungen erforderlich. Weitere Informationen zu Rollen für Benutzer, die die Verfügbarkeit bestimmter Funktionen steuern, finden Sie unter Benutzer und Rollen[hinzufügen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/what-is-required/add-users-roles.html).

## AEM-Aktualisierungen für Sandbox-Umgebung {#aem-updates-sandbox}

Weitere Informationen finden Sie in den [AEM-Versionsupdates](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#version-updates) .

Ein Benutzer kann AEM-Updates manuell auf die Umgebung in einem Sandbox-Programm anwenden.

Informationen zum Aktualisieren einer Umgebung finden Sie unter [Aktualisieren der Umgebung](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#updating-dev-environment) .

>[!NOTE]
>Eine *Nicht-Produktionspipeline* , die in der für die Entwicklung relevanten Umgebung bereitgestellt wird, muss konfiguriert werden, damit eine manuelle Aktualisierungspipeline initiiert werden kann.

>[!NOTE]
>Eine *Produktionsleitung* muss konfiguriert werden, damit eine manuelle Update-Pipeline zu Production+Stage-Umgebung gestartet werden kann.

>[!NOTE]
>Die manuelle Aktualisierung auf *Produktions* - oder *Stage* -Umgebung wird automatisch aktualisiert. Der Produktions- und Stage-Umgebung-Satz muss sich in derselben AEM-Version befinden.





