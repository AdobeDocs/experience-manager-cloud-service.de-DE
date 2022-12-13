---
title: Erstellen eines Programms
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr erstes Programm erstellen.
role: Admin, User, Developer
exl-id: ade4bb43-5f48-4938-ac75-118009f0a73b
source-git-commit: 971ef47b66da6d7e032f6109afb4830d49c00071
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 91%

---

# Erstellen eines Programms {#create-program}

In diesem Teil der [Onboarding-Tour](overview.md) erfahren Sie, wie Sie mit Cloud Manager Ihr erstes Programm erstellen.

## Ziel {#objective}

Nachdem Sie in dieser Onboarding-Tour das vorherige Dokument [Zugriff auf Cloud Manager](cloud-manager.md) durchgelesen haben, haben Sie sichergestellt, dass Sie angemessenen Zugriff auf Cloud Manager haben. Jetzt können Sie Ihr erstes Programm erstellen.

Nach Lesen dieses Dokuments sollten Sie Folgendes können:

* Verstehen, was ein Programm ist.
* Den Unterschied zwischen Produktions- und Sandbox-Programmen erkennen.
* Ihr eigenes Programm erstellen.

## Was ist ein Programm? {#programs}

Programme sind die höchste Organisationsebene in Cloud Manager. Abhängig von Ihrer Lizenz mit Adobe können Sie mithilfe von Programmen Ihre Lösung organisieren und bestimmten Team-Mitgliedern Zugriff auf diese Programme gewähren.

Cloud Manager-Programme stellen eine Reihe von Cloud Manager-Umgebungen dar. Diese Programme unterstützen logische Gruppen von Geschäftsinitiativen, die normalerweise einem lizenzierten Service Level Agreement (SLA) entsprechen. Beispielsweise kann ein Programm die AEM-Ressourcen zur Unterstützung einer globalen öffentlichen Website für eine Organisation darstellen, während ein anderes Programm ein internes zentrales DAM darstellt.

Denken Sie an unser theoretisches Beispiel von WKND Travel and Adventure Enterprises. Dieser Mandant spezialisiert sich auf reisebezogene Medien. Dort könnte es zwei Programme geben: ein Sites-Programm für den WKND Magazine-Bereich und ein Assets-Programm für den WKND Media-Bereich. Verschiedene Team-Mitglieder hätten dann aufgrund ihrer eigenen Arbeitsteilung Zugang zu den verschiedenen Programmen.

Es gibt zwei verschiedene Arten von Programmen:

* Ein **Produktionsprogramm** wird erstellt, um Live-Traffic für Ihre Site zu ermöglichen. Dies ist Ihre „echte“ Umgebung.
* Ein **Sandbox-Programm** wird normalerweise für Schulungen, Ausführungen von Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt.

Da sie für unterschiedliche Zwecke eingesetzt werden, haben die verschiedenen Umgebungen unterschiedliche Optionen. Die Erstellung erfolgt jedoch ähnlich. Für diese Onboarding-Tour erstellen wir eine Sandbox-Umgebung.

>[!TIP]
>
>Wenn Sie ein Produktionsprogramm erstellen müssen, lesen Sie den Abschnitt [Zusätzliche Ressourcen](#additional-resources) einen Link zur ausführlichen Beschreibung der Programme.

## Erstellen eines Sandbox-Programms {#create-sandbox}

Gehen Sie wie folgt vor, um ein Sandbox-Programm zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf der Landingpage von Cloud Manager in der oberen rechten Ecke des Bildschirms auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

1. Wählen Sie im Assistenten „Programm erstellen“ die Option **Sandbox einrichten**, geben Sie einen Programmnamen ein und klicken Sie auf **Erstellen**.

   ![Erstellen von Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/create-sandbox.png)

Auf der Landingpage wird eine neue Sandbox-Programmkarte mit einer Statusanzeige angezeigt, während der Einrichtungsprozess fortgesetzt wird.

![Erstellen von Sandboxes von der Übersichtsseite](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/program-create-setupdemo2.png)

Sobald das Programm abgeschlossen ist, können sich Mitglieder Ihrer Organisation, die dem Produktprofil **Entwickler** zugewiesen sind, bei Cloud Manager anmelden und Cloud Manager-Git-Repositories verwalten.

## Wie geht es weiter {#whats-next}

Nachdem Ihr erstes Programm erstellt wurde, können Sie Umgebungen dafür erstellen. Sie sollten Ihre Onboarding-Tour fortsetzen, indem Sie das Dokument [Erstellen von Umgebungen](create-environments.md) lesen.

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Programme und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) – Erfahren Sie mehr über die Hierarchie von Cloud Manager und darüber, wie die verschiedenen Arten von Programmen in die Struktur passen und wie sie sich unterscheiden
* [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) – Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Sandbox-Programm für Schulungs-, Demo-, POC- oder andere produktionsfremde Zwecke erstellen
* [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) – Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Produktionsprogramm für das Hosten von Live-Traffic erstellen.
* [Verwenden von Adobe Cloud Manager – Programme](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de) – Cloud Manager-Programme stellen eine Reihe von AEM-Umgebungen dar, die logische Gruppen von Geschäftsinitiativen unterstützen, die in der Regel einem erworbenen Service Level Agreement (SLA) entsprechen.
* [AEM as a Cloud Service Team und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md) - Erfahren Sie, wie AEM as a Cloud Service Team und Produktprofile den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren und beschränken können.
