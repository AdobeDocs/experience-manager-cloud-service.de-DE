---
title: Ruhezustand und Aufheben des Ruhezustands von Sandbox-Umgebungen
description: Erfahren Sie, wie die Umgebungen eines Sandbox-Programms automatisch in den Ruhezustand übergehen und wie Sie den Ruhezustand wieder aufheben können.
exl-id: c0771078-ea68-4d0d-8d41-2d9be86408a4
source-git-commit: d1b2226a1deec2e71056c43c84672cb4a358bc8c
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 94%

---


# Ruhezustand und Aufheben des Ruhezustands von Sandbox-Umgebungen {#hibernating-introduction}

Umgebungen eines Sandbox-Programms werden in den Ruhezustand versetzt, wenn acht Stunden lang keine Aktivität erkannt wurde. Der Ruhezustand ist Sandbox-Programmumgebungen vorbehalten. Bei Produktions-Programmumgebungen gibt es keinen Ruhezustand.

## Ruhezustand {#hibernation-introduction}

Der Ruhezustand kann entweder automatisch oder manuell aktiviert werden.

* **Automatisch**: Sandbox-Programmumgebungen werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt. Inaktivität liegt vor, wenn weder der Autoren-Service noch die Vorschau- oder Veröffentlichungs-Service Anfragen erhalten.
* **Manuell**: Als Benutzer können Sie eine Sandbox-Programmumgebung manuell in den Ruhezustand versetzen. Dies ist nicht unbedingt erforderlich, da der Ruhezustand wie zuvor beschrieben automatisch eintritt.

Es kann einige Minuten dauern, bis Sandbox-Programmumgebungen in den Ruhezustand wechseln. Daten werden im Ruhezustand beibehalten.

### Verwenden des manuellen Ruhezustands {#using-manual-hibernation}

Über die Entwicklerkonsole können Sie Ihr Sandbox-Programm manuell in den Ruhezustand versetzen. Der Zugriff auf die Entwicklerkonsole für ein Sandbox-Programm steht allen Anwendern von Cloud Manager zur Verfügung.

Gehen Sie wie folgt vor, um Ihre Sandbox-Programmumgebungen manuell in den Ruhezustand zu versetzen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Im **[Eigene Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** -Konsole, tippen oder klicken Sie auf das Programm, dessen Details Sie im Ruhezustand anzeigen möchten.

1. Klicken Sie auf der Karte **Umgebungen** auf die Schaltfläche mit den Auslassungspunkten und wählen Sie **Entwicklerkonsole** aus.

   * Siehe [Aufrufen der Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console), um weitere Informationen zur Developer Console zu erhalten.

   ![Menüoption „Entwicklerkonsole“](assets/developer-console-menu-option.png)

1. Klicken Sie in der Entwicklerkonsole auf **Ruhezustand**.

   ![Schaltfläche „Ruhezustand“](assets/hibernate-1.png)

1. Klicken Sie auf **Ruhezustand**, um den Schritt zu bestätigen.

   ![Bestätigen des Ruhezustands](assets/hibernate-2.png)

Nach erfolgreicher Aktivierung des Ruhezustands wird im Bildschirm **Developer Console** eine Benachrichtigung zur Fertigstellung des Ruhezustands für Ihre Umgebung angezeigt.

![Ruhezustand – Bestätigung](assets/hibernate-4.png)

In der Developer Console können Sie auch auf den Link **Umgebungen** in den Breadcrumbs oberhalb der Dropdown-Liste **Pod** klicken, um eine Liste der Umgebungen zu erhalten, die in den Ruhezustand versetzt werden sollen.

![Liste der Umgebungen, die in den Ruhezustand versetzt werden sollen](assets/hibernate-1b.png)

## Aufheben des Ruhezustands {#de-hibernation-introduction}

Über die Entwicklerkonsole können Sie Ihr Sandbox-Programm manuell in den Ruhezustand versetzen.

>[!IMPORTANT]
>
>Ein Benutzer mit der Rolle **Entwickler** kann den Ruhezustand einer Sandbox-Programmumgebung aufheben.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Im **[Eigene Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** -Konsole, tippen oder klicken Sie auf das Programm, dessen Ruhezustand Sie deaktivieren möchten, um dessen Details anzuzeigen.

1. Klicken Sie auf der Karte **Umgebungen** auf die Schaltfläche mit den Auslassungspunkten und wählen Sie **Entwicklerkonsole** aus.

   * Siehe [Aufrufen der Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console), um weitere Informationen zur Developer Console zu erhalten.

1. Klicken Sie auf **Aus Ruhezustand holen**.

   ![Schaltfläche „Ruhezustand aufheben“](assets/de-hibernation-img1.png)

1. Klicken Sie auf **Ruhezustand aufheben**, um den Schritt zu bestätigen.

   ![Bestätigen der Aufhebung des Ruhezustands](assets/de-hibernation-img2.png)

1. Sie erhalten eine Benachrichtigung, dass die Aufhebung des Ruhezustands begonnen hat und werden über den Fortschritt informiert.

   ![Benachrichtigung zum Fortschritt beim Ruhezustand](assets/de-hibernation-img3.png)

1. Nach Abschluss des Vorgangs ist die Sandbox-Programmumgebung wieder aktiv.

   ![Abschluss der Aufhebung des Ruhezustands](assets/de-hibernation-img4.png)


In der Developer Console können Sie auch auf den Link **Umgebungen** in den Breadcrumbs oberhalb der Dropdown-Liste **Pod** klicken, um eine Liste der Umgebungen, die aus dem Ruhezustand geholt werden soll, zu erhalten.

![Liste der im Ruhezustand befindlichen Pods](assets/de-hibernate-1b.png)

### Berechtigungen zum Aufheben des Ruhezustands {#permissions-de-hibernate}

Jeder Anwender mit einem Produktprofil, das Zugriff auf AEM as a Cloud Service gewährt, sollte auf die **Developer Console** zugreifen und somit die Umgebung reaktivieren können.

## Zugreifen auf eine im Ruhezustand befindliche Umgebung {#accessing-hibernated-environment}

Bei Browser-Anfragen an den Autoren-, Vorschau- oder Veröffentlichungs-Service einer im Ruhezustand befindlichen Umgebung wird dem Benutzer eine Landingpage angezeigt, auf der der Status der Umgebung als im Ruhezustand befindlich beschrieben wird, sowie ein Link zur Entwicklerkonsole, auf der der Ruhezustand des Service aufgehoben werden kann.

![Landingpage für Services im Ruhezustand](assets/de-hibernation-img5.png)

## Bereitstellungen und AEM-Updates {#deployments-updates}

In im Ruhezustand befindlichen Umgebungen können weiterhin Bereitstellungen und manuelle AEM-Upgrades vorgenommen werden.

* Ein Anwender kann eine Pipeline verwenden, um benutzerdefinierten Code für im Ruhezustand befindliche Umgebungen bereitzustellen. Die Umgebung verbleibt im Ruhezustand; der neue Code wird in der Umgebung angezeigt, sobald der Ruhezustand deaktiviert wird.

* AEM-Upgrades können auf im Ruhezustand befindliche Umgebungen angewendet werden; sie können von Kunden in Cloud Manager manuell ausgelöst werden. Die Umgebung verbleibt im Ruhezustand; die neue Version erscheint in der Umgebung, sobald der Ruhezustand deaktiviert wurde.

## Ruhezustand und Löschung {#hibernation-deletion}

* Umgebungen in einem Sandbox-Programm werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt.
   * Inaktivität liegt vor, wenn weder der Autoren-Service noch die Vorschau- oder Veröffentlichungs-Service Anfragen erhalten.
   * Sobald sie sich im Ruhezustand befinden, kann der Ruhezustand [manuell aufgehoben werden.](#de-hibernation-introduction)
* Sandbox-Programme werden nach sechs Monaten, nachdem sie sich im kontinuierlichen Ruhezustand befinden, gelöscht. Danach können sie neu erstellt werden.

>[!NOTE]
>
>Nur Sandbox-Umgebungen werden nach sechsmonatigem kontinuierlichen Ruhezustand automatisch gelöscht. Das Sandbox-Programm mit seinem Repository und Code bleibt erhalten.
