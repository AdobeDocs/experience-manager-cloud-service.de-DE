---
title: Erstellen eines Programms
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr erstes Programm erstellen.
role: Admin, User, Developer
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 25%

---


# Erstellen eines Programms {#create-program}

In diesem Teil des [Onboarding-Journey,](overview.md) Hier erfahren Sie, wie Sie mit Cloud Manager Ihr erstes Programm erstellen.

## Ziel {#objective}

Nach der Überprüfung des vorherigen Dokuments in dieser Onboarding-Journey, [Zugriff auf Cloud Manager,](cloud-manager.md) Sie haben sichergestellt, dass Sie angemessenen Zugriff auf Cloud Manager haben. Jetzt können Sie Ihr erstes Programm erstellen.

Nach Lesen dieses Dokuments werden Sie:

* Verstehen Sie, was ein Programm ist.
* Erkennen Sie den Unterschied zwischen Produktions- und Sandbox-Programmen.
* Sie können Ihr eigenes Programm erstellen.

## Was ist ein Programm? {#programs}

Programme sind die höchste Organisationsebene in Cloud Manager. Abhängig von Ihrer Lizenz mit Adobe können Sie mithilfe von Programmen Ihre Lösung organisieren und bestimmten Teammitgliedern Zugriff auf diese Programme gewähren.

Cloud Manager-Programme stellen eine Reihe von Cloud Manager-Umgebungen dar. Diese Programme unterstützen logische Gruppen von Geschäftsinitiativen, die normalerweise einer lizenzierten Service Level Agreement (SLA) entsprechen. Beispielsweise kann ein Programm die AEM Ressourcen darstellen, um eine globale öffentliche Website für eine Organisation zu unterstützen, während ein anderes Programm ein internes, zentrales DAM darstellt.

Wenn Sie sich an das Beispiel der theoretischen WKND Travel and Adventure Enterprises erinnern, die ein Mandant ist, der sich auf reisebezogene Medien konzentriert, haben sie möglicherweise zwei Programme: ein Sites-Programm für die WKND Magazine-Division und ein Assets-Programm für den WKND Media-Bereich. Verschiedene Teammitglieder hätten dann aufgrund ihrer eigenen Arbeitsteilung Zugang zu den verschiedenen Programmen.

Es gibt zwei verschiedene Arten von Programmen:

* Ein **Produktionsprogramm** wird erstellt, um Live-Traffic für Ihre Site zu ermöglichen. Dies ist Ihre &quot;echte&quot;Umgebung.
* Ein **Sandbox-Programm** wird normalerweise für Schulungen, Ausführungen von Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt.

Da sie für unterschiedliche Zwecke eingesetzt werden, haben die verschiedenen Umgebungen unterschiedliche Optionen. Die Erstellung erfolgt jedoch ähnlich. Für diese Onboarding-Journey erstellen wir eine Sandbox-Umgebung.

## Erstellen eines Sandbox-Programms {#create-sandbox}

Gehen Sie wie folgt vor, um ein Sandbox-Programm zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf der Landingpage von Cloud Manager in der oberen rechten Ecke des Bildschirms auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

1. Wählen Sie im Assistenten „Programm erstellen“ die Option **Sandbox einrichten**, geben Sie einen Programmnamen ein und klicken Sie auf **Erstellen**.

   ![Erstellen von Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/create-sandbox.png)

Auf der Landingpage wird eine neue Sandbox-Programmkarte mit einer Statusanzeige angezeigt, während der Einrichtungsprozess fortgesetzt wird.

![Erstellen von Sandboxes von der Übersichtsseite](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/program-create-setupdemo2.png)

Sobald das Programm abgeschlossen ist, weisen die Mitglieder Ihrer Organisation der **Entwickler** Produktprofil kann sich bei Cloud Manager anmelden und Cloud Manager-Git-Repositorys verwalten.

## Wie geht es weiter? {#whats-next}

Nachdem Ihr erstes Programm erstellt wurde, können Sie Umgebungen dafür erstellen. Sie sollten Ihre Onboarding-Journey fortsetzen, indem Sie das Dokument zum nächsten Mal lesen. [Erstellen von Umgebungen.](create-environments.md)

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Programme und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) - Erfahren Sie mehr über die Hierarchie von Cloud Manager und darüber, wie die verschiedenen Arten von Programmen in die Struktur passen und wie sie voneinander abweichen.
* [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) - Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Sandbox-Programm für Trainings-, Demo-, POC- oder andere Nicht-Produktions-Zwecke erstellen.
* [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) - Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Produktionsprogramm für die Hosting von Live-Traffic erstellen.
* [Verwenden von Adobe Cloud Manager - Programme](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de) - Cloud Manager-Programme stellen eine Reihe von AEM Umgebungen dar, die logische Gruppen von Geschäftsinitiativen unterstützen, die in der Regel einem erworbenen Service Level Agreement (SLA) entsprechen.
