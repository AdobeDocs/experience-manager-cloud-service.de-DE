---
title: Ruhezustand und Ruhezustand von Sandbox-Umgebungen
description: Erfahren Sie, wie die Umgebungen eines Sandbox-Programms automatisch in den Ruhezustand wechseln und den Ruhezustand deaktivieren können.
exl-id: c0771078-ea68-4d0d-8d41-2d9be86408a4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 88b4864da30fbf201dbd5bde1ac17d3be977648f
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 47%

---


# Ruhezustand und Ruhezustand von Sandbox-Umgebungen {#hibernating-introduction}

Umgebungen eines Sandbox-Programms werden in den Ruhezustand versetzt, wenn acht Stunden lang keine Aktivität erkannt wurde. Der Ruhezustand ist nur in Sandbox-Programmumgebungen verfügbar. Produktionsprogrammumgebungen können nicht in den Ruhezustand versetzt werden.

## Ruhezustand {#hibernation-introduction}

Der Ruhezustand kann entweder automatisch oder manuell aktiviert werden.

* **Automatisch**: Sandbox-Programmumgebungen werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt. Inaktivität ist definiert als das Fehlen von Anforderungen an Autoren-, Vorschau- und Veröffentlichungsdienste.
* **Manuell**: Als Benutzer können Sie eine Sandbox-Programmumgebung manuell in den Ruhezustand versetzen. Dies ist nicht erforderlich, da der Ruhezustand automatisch wie zuvor beschrieben erfolgt.

Es kann einige Minuten dauern, bis Sandbox-Programmumgebungen in den Ruhezustand wechseln. Daten werden im Ruhezustand beibehalten.

### Manuelles Ruhezustand einer Sandbox-Programmumgebung {#using-manual-hibernation}

Über die Entwicklerkonsole können Sie Ihr Sandbox-Programm manuell in den Ruhezustand versetzen. Der Zugriff auf die Developer Console für ein Sandbox-Programm steht allen Benutzern von Cloud Manager zur Verfügung.

**So löschen Sie eine Sandbox-Programmumgebung manuell in den Ruhezustand:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** auf ein *Sandbox-Programm*, das Sie in den Ruhezustand versetzen möchten, um die Details anzuzeigen.

1. Klicken Sie auf der Karte **Umgebungen** auf das Symbol ![Mehr ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und klicken Sie auf **Developer Console**.

   * Siehe [Aufrufen der Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console), um weitere Informationen zur Developer Console zu erhalten.

   ![Menüoption „Entwicklerkonsole“](/help/implementing/cloud-manager/assets/developer-console-menu-option.png)

1. Klicken Sie auf der Seite **Developer Console** auf **Ruhezustand**.

<!-- UPDATE THESE SCREENSHOTS WHEN NEW AEM DEVELOPER CONSOLE UI IS RELEASED. AS OF OCTOBER 14, 2024, NEW UI IS STILL IN BETA -->

![Schaltfläche „Ruhezustand“](assets/hibernate-1.png)

1. Klicken Sie auf **Ruhezustand**, um den Schritt zu bestätigen.

   ![Bestätigen des Ruhezustands](assets/hibernate-2.png)

Nach erfolgreicher Aktivierung des Ruhezustands wird im Bildschirm **Developer Console** eine Benachrichtigung zur Fertigstellung des Ruhezustands für Ihre Umgebung angezeigt.

![Ruhezustand – Bestätigung](assets/hibernate-4.png)

Klicken Sie in der Developer Console auf den Link **Umgebungen** in den Breadcrumbs über der Dropdownliste **Werbeunterbrechung** , um die für den Ruhezustand verfügbaren Umgebungen anzuzeigen.

![Liste der Umgebungen, die in den Ruhezustand versetzt werden sollen](assets/hibernate-1b.png)

## Manuelles Deaktivieren des Ruhezustands eines Sandbox-Programms über Developer Console {#de-hibernation-introduction}

Sie können Ihr Sandbox-Programm manuell aus der Developer Console in den Ruhezustand versetzen.

>[!IMPORTANT]
>
>Ein Benutzer mit der Rolle **Entwickler** kann den Ruhezustand einer Sandbox-Programmumgebung aufheben.

**So deaktivieren Sie den Ruhezustand eines Sandbox-Programms manuell aus der Developer Console:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** auf das Programm, dessen Ruhezustand Sie deaktivieren möchten, um dessen Details anzuzeigen.

1. Klicken Sie auf der Karte **Umgebungen** auf https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg und klicken Sie auf **Developer Console**.

   * Siehe [Aufrufen der Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console), um weitere Informationen zur Developer Console zu erhalten.

1. Klicken Sie auf **Aus Ruhezustand holen**.

   ![Schaltfläche „Ruhezustand aufheben“](assets/de-hibernation-img1.png)

1. Klicken Sie auf **Ruhezustand aufheben**, um den Schritt zu bestätigen.

   ![Bestätigen der Aufhebung des Ruhezustands](assets/de-hibernation-img2.png)

1. Sie erhalten eine Benachrichtigung, dass die Aufhebung des Ruhezustands begonnen hat und werden über den Fortschritt informiert.

   ![Benachrichtigung zum Fortschritt beim Ruhezustand](assets/de-hibernation-img3.png)

1. Nach Abschluss des Vorgangs ist die Sandbox-Programmumgebung wieder aktiv.

   ![Abschluss der Aufhebung des Ruhezustands](assets/de-hibernation-img4.png)

Klicken Sie in der Developer Console auf den Link **Umgebungen** in den Breadcrumbs über der Dropdownliste **Werbeunterbrechung**, um auf Umgebungen zuzugreifen, die für die Aufhebung des Ruhezustands verfügbar sind.

![Liste der im Ruhezustand befindlichen Pods](assets/de-hibernate-1b.png)

### Berechtigungen zum Deaktivieren des Ruhezustands {#permissions-de-hibernate}

Jeder Anwender mit einem Produktprofil, das Zugriff auf AEM as a Cloud Service gewährt, sollte auf die **Developer Console** zugreifen und somit die Umgebung reaktivieren können.

## Zugriff auf eine im Ruhezustand befindliche Umgebung {#accessing-hibernated-environment}

Wenn ein Benutzer eine Browseranforderung an den Autoren-, Vorschau- oder Veröffentlichungsdienst einer im Ruhezustand befindlichen Umgebung sendet, wird ihm eine Landingpage angezeigt. Auf dieser Seite wird der Ruhezustand der Umgebung erläutert und ein Link zur Developer Console zur Deaktivierung des Ruhezustands bereitgestellt.

![Landingpage für Services im Ruhezustand](assets/de-hibernation-img5.png)

## Bereitstellungen und AEM {#deployments-updates}

In im Ruhezustand befindlichen Umgebungen können weiterhin Bereitstellungen und manuelle AEM-Upgrades vorgenommen werden.

* Ein Anwender kann eine Pipeline verwenden, um benutzerdefinierten Code für im Ruhezustand befindliche Umgebungen bereitzustellen. Die Umgebung bleibt im Ruhezustand und der neue Code wird in der Umgebung angezeigt, sobald der Ruhezustand deaktiviert wurde.

* AEM-Upgrades können auf im Ruhezustand befindliche Umgebungen angewendet werden; sie können von Kunden in Cloud Manager manuell ausgelöst werden. Die Umgebung bleibt im Ruhezustand und die neue Version wird in der Umgebung angezeigt, sobald der Ruhezustand deaktiviert wurde.

## Ruhezustand und Löschung {#hibernation-deletion}

* Umgebungen in einem Sandbox-Programm werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt.
   * Inaktivität ist definiert als das Fehlen von Anforderungen an Autoren-, Vorschau- und Veröffentlichungsdienste.
   * Sobald sie sich im Ruhezustand befinden, kann der [Ruhezustand manuell aufgehoben werden](#de-hibernation-introduction).
* Sandbox-Programme werden gelöscht, nachdem sie sich sechs Monate im kontinuierlichen Ruhezustand befunden haben. Danach können sie neu erstellt werden.

>[!NOTE]
>
>Nur Sandbox-Umgebungen werden nach sechsmonatigem kontinuierlichen Ruhezustand automatisch gelöscht. Das Sandbox-Programm mit seinem Repository und Code bleibt erhalten.
