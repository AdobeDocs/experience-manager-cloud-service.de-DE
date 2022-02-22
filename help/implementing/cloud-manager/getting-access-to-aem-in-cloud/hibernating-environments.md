---
title: 'Ruhezustand und Reaktivieren von Sandbox-Umgebungen '
description: Erfahren Sie, wie Umgebungen eines Sandbox-Programms automatisch in den Ruhezustand wechseln und wie Sie den Ruhezustand deaktivieren können.
exl-id: c0771078-ea68-4d0d-8d41-2d9be86408a4
source-git-commit: 5cb58b082323293409aad08d4e5dd9289283e0a6
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 20%

---


# Ruhezustand und Ruhezustand von Sandbox-Umgebungen {#hibernating-introduction}

Umgebungen eines Sandbox-Programms werden in den Ruhezustand versetzt, wenn acht Stunden lang keine Aktivität erkannt wurde. Der Ruhezustand ist in Sandbox-Programmumgebungen eindeutig. Bei Produktions-Programmumgebungen gibt es keinen Ruhezustand.

## Ruhezustand {#hibernation-introduction}

Der Ruhezustand kann entweder automatisch oder manuell aktiviert werden.

* **Automatisch** - Sandbox-Programmumgebungen werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt. Inaktivität ist definiert, da weder der Autoren- noch der Vorschau- oder der Veröffentlichungsdienst Anforderungen empfangen.
* **Manuell** - Als Benutzer können Sie eine Sandbox-Programmumgebung manuell in den Ruhezustand versetzen. Dies ist nicht erforderlich, da der Ruhezustand automatisch wie zuvor beschrieben erfolgt.

Es kann einige Minuten dauern, bis Sandbox-Programmumgebungen in den Ruhezustand wechseln. Daten werden im Ruhezustand beibehalten.

### Verwenden des manuellen Ruhezustands {#using-manual-hibernation}

Sie können Ihr Sandbox-Programm manuell über die Developer Console in den Ruhezustand versetzen. Der Zugriff auf die Developer Console für ein Sandbox-Programm ist für alle Benutzer von Cloud Manager verfügbar.

Führen Sie diese Schritte aus, um Ihre Sandbox-Programmumgebungen manuell in den Ruhezustand zu versetzen.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, das Sie in den Ruhezustand versetzen möchten, um seine Details anzuzeigen.

1. Im **Umgebungen** Karte, klicken Sie auf die Suchschaltfläche und wählen Sie **Entwicklerkonsole**.

   * Siehe Dokument . [Aufrufen der Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) Weitere Informationen zur Entwicklerkonsole.

   ![Menüoption &quot;Developer Console&quot;](assets/developer-console-menu-option.png)

1. Klicken Sie in der Entwicklerkonsole auf **Ruhezustand**.

   ![Schaltfläche &quot;Ruhezustand&quot;](assets/hibernate-1.png)

1. Klicken Sie auf **Ruhezustand**, um den Schritt zu bestätigen.

   ![Ruhezustand bestätigen](assets/hibernate-2.png)

Nach erfolgreicher Aktivierung des Ruhezustands wird im Bildschirm **Developer Console** eine Benachrichtigung zur Fertigstellung des Ruhezustands für Ihre Umgebung angezeigt.

![Ruhezustand - Bestätigung](assets/hibernate-4.png)

In der Entwicklerkonsole können Sie auch auf das **Umgebungen** -Link in den Breadcrumbs über dem **Pod** Dropdown für eine Liste der Umgebungen, die in den Ruhezustand versetzt werden sollen.

![Liste der Umgebungen für den Ruhezustand](assets/hibernate-1b.png)

## Deaktivieren des Ruhezustands {#de-hibernation-introduction}

Sie können Ihr Sandbox-Programm manuell über die Developer Console in den Ruhezustand versetzen.

>[!IMPORTANT]
>
>Ein Benutzer mit **Entwickler** Rolle kann den Ruhezustand einer Sandbox-Programmumgebung deaktivieren.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, das Sie in den Ruhezustand versetzen möchten, um seine Details anzuzeigen.

1. Im **Umgebungen** Karte, klicken Sie auf die Suchschaltfläche und wählen Sie **Entwicklerkonsole**.

   * Siehe Dokument . [Aufrufen der Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) Weitere Informationen zur Entwicklerkonsole.

1. Klicken Sie auf **Ruhezustand deaktivieren**.

   ![Ruhezustand deaktivieren, Schaltfläche](assets/de-hibernation-img1.png)

1. Klicken **Ruhezustand deaktivieren** , um den Schritt zu bestätigen.

   ![Deaktivieren des Ruhezustands](assets/de-hibernation-img2.png)

1. Sie erhalten eine Benachrichtigung, dass die Deaktivierung des Ruhezustands begonnen und mit dem Fortschritt aktualisiert wurde.

   ![Benachrichtigung zum Ruhezustand](assets/de-hibernation-img3.png)

1. Nach Abschluss des Prozesses ist die Sandbox-Programmumgebung wieder aktiv.

   ![Abschluss der Aufhebung des Ruhezustands](assets/de-hibernation-img4.png)


In der Entwicklerkonsole können Sie auch auf das **Umgebungen** -Link in den Breadcrumbs über dem **Pod** Dropdown-Liste für eine Liste der Umgebungen, die den Ruhezustand deaktivieren sollen.

![Liste der im Ruhezustand befindlichen Pods](assets/de-hibernate-1b.png)

### Berechtigungen zum Deaktivieren des Ruhezustands {#permissions-de-hibernate}

Jeder Anwender mit einem Produktprofil, das Zugriff auf AEM as a Cloud Service gewährt, sollte auf die **Developer Console** zugreifen und somit die Umgebung reaktivieren können.

## Zugreifen auf eine im Ruhezustand befindliche Umgebung {#accessing-hibernated-environment}

Bei Browser-Anforderungen an den Autoren-, Vorschau- oder Veröffentlichungsdienst einer im Ruhezustand befindlichen Umgebung wird dem Benutzer eine Landingpage angezeigt, auf der der im Ruhezustand befindliche Status der Umgebung beschrieben wird, sowie ein Link zur Developer Console, auf der der Dienst deaktiviert werden kann.

![Landingpage des Ruhezustands-Dienstes](assets/de-hibernation-img5.png)

## Bereitstellungen und AEM {#deployments-updates}

In im Ruhezustand befindlichen Umgebungen können weiterhin Bereitstellungen und manuelle AEM vorgenommen werden.

* Ein Anwender kann eine Pipeline verwenden, um benutzerdefinierten Code für im Ruhezustand befindliche Umgebungen bereitzustellen. Die Umgebung verbleibt im Ruhezustand; der neue Code wird in der Umgebung angezeigt, sobald der Ruhezustand deaktiviert wird.

* AEM Aktualisierungen können auf im Ruhezustand befindliche Umgebungen angewendet werden und manuell über Cloud Manager ausgelöst werden. Die Umgebung verbleibt im Ruhezustand; die neue Version erscheint in der Umgebung, sobald der Ruhezustand deaktiviert wurde.

## Ruhezustand und Löschung {#hibernation-deletion}

* Umgebungen in einem Sandbox-Programm werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt.
   * Inaktivität ist definiert, da weder der Autoren- noch der Vorschau- oder der Veröffentlichungsdienst Anforderungen empfangen.
   * Nach dem Ruhezustand können sie manuell deaktiviert werden.
* Sandbox-Programme werden gelöscht, nachdem sie sich sechs Monate im kontinuierlichen Ruhezustand befinden. Danach können sie neu erstellt werden.
