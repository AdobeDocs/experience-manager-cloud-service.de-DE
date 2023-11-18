---
title: Erstellen eines Programms
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr erstes Programm erstellen.
role: Admin, User, Developer
exl-id: ade4bb43-5f48-4938-ac75-118009f0a73b
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 67%

---

# Erstellen eines Programms {#create-program}

In diesem Teil des [Onboarding-Journey,](overview.md) Hier erfahren Sie, wie Sie mit Cloud Manager Ihr erstes Programm erstellen.

## Ziel {#objective}

Nachdem Sie in dieser Onboarding-Tour das vorherige Dokument [Zugriff auf Cloud Manager](cloud-manager.md) durchgelesen haben, haben Sie sichergestellt, dass Sie angemessenen Zugriff auf Cloud Manager haben. Jetzt können Sie Ihr erstes Programm erstellen.

Nach dem Lesen dieses Dokuments haben Sie folgende Möglichkeiten:

* Verstehen und erklären Sie, was ein Programm ist.
* Den Unterschied zwischen Produktions- und Sandbox-Programmen erkennen.
* Erstellen Sie Ihr eigenes Programm.

## Was ist ein Programm? {#programs}

Programme sind die höchste Organisationsebene in Cloud Manager. Abhängig von Ihrer Lizenz mit Adobe können Sie mithilfe von Programmen Ihre Lösung organisieren und bestimmten Team-Mitgliedern Zugriff auf diese Programme gewähren.

Cloud Manager-Programme stellen eine Reihe von Cloud Manager-Umgebungen dar. Diese Programme unterstützen logische Gruppen von Geschäftsinitiativen, die normalerweise einem lizenzierten Service Level Agreement (SLA) entsprechen. Beispielsweise kann ein Programm die Adobe Experience Manager-Ressourcen (AEM) repräsentieren, um eine globale öffentliche Website für eine Organisation zu unterstützen, während ein anderes Programm ein internes, zentrales DAM darstellt.

Vielleicht erinnern Sie sich an das Beispiel von WKND Travel and Adventure Enterprises, welches als Mandant im Bereich Reisemedien agiert. In diesem Kontext könnte es beispielsweise zwei Programme geben. Ein AEM Sites-Programm für den Bereich WKND Magazine und ein AEM Assets-Programm für den Bereich WKND Media. Verschiedene Team-Mitglieder hätten dann aufgrund ihrer eigenen Arbeitsteilung Zugang zu den verschiedenen Programmen.

Es gibt zwei verschiedene Arten von Programmen:

* Ein **Produktionsprogramm** wird erstellt, um Live-Traffic für Ihre Site zu ermöglichen. Dies ist Ihre „echte“ Umgebung.
* Ein **Sandbox-Programm** wird normalerweise für Schulungen, Ausführungen von Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt.

Da sie für unterschiedliche Zwecke eingesetzt werden, haben die verschiedenen Umgebungen unterschiedliche Optionen. Die Erstellung erfolgt jedoch ähnlich. Für diese Onboarding-Journey erstellen Sie eine Sandbox-Umgebung.

>[!TIP]
>
>Wenn Sie ein Produktionsprogramm erstellen müssen, lesen Sie den Abschnitt [Zusätzliche Ressourcen](#additional-resources) einen Link zur Dokumentation mit detaillierten Beschreibungen der Programme.

## Erstellen eines Sandbox-Programms {#create-sandbox}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf der Landingpage von Cloud Manager auf **Programm hinzufügen** in der oberen rechten Ecke des Bildschirms.

   ![Cloud Manager-Landingpage](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/cloud-manager-my-programs.png)

1. Wählen Sie im Assistenten Programm erstellen die Option **Sandbox einrichten**, geben Sie dann einen Programmnamen ein und wählen Sie **Weiter**.

   ![Erstellen von Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/create-sandbox.png)

1. Im **Sandbox einrichten** auswählen, können Sie festlegen, welche Lösungen Sie in Ihrem Sandbox-Programm aktivieren möchten. Die Lösungen **Sites** und **Assets** sind immer in Sandbox-Programmen enthalten und werden automatisch ausgewählt. Dies reicht für Ihr Onboarding-Beispiel aus. Klicken Sie auf **Erstellen**.

   ![Lösungsauswahl](assets/set-up-sandbox-onboarding.png)

Auf der Landingpage wird eine neue Sandbox-Programmkarte mit einer Statusanzeige angezeigt, während der Einrichtungsprozess fortgesetzt wird.

![Erstellen von Sandboxes von der Übersichtsseite](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/program-create-setupdemo2.png)

Sobald das Programm abgeschlossen ist, weisen die Mitglieder Ihrer Organisation der **Entwickler** Produktprofil kann sich bei Cloud Manager anmelden und Cloud Manager-Git-Repositorys verwalten.

## Wie geht es weiter {#whats-next}

Nachdem Ihr erstes Programm erstellt wurde, können Sie Umgebungen dafür erstellen. Fahren Sie mit dem Onboarding-Journey fort, indem Sie das Dokument zum nächsten Mal lesen. [Erstellen von Umgebungen.](create-environments.md)

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt der Onboarding-Tour hinausgehen möchten.

* [Programme und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) – Erfahren Sie mehr über die Hierarchie von Cloud Manager und darüber, wie die verschiedenen Arten von Programmen in die Struktur passen und wie sie sich unterscheiden
* [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) – Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Sandbox-Programm für Schulungs-, Demo-, POC- oder andere produktionsfremde Zwecke erstellen
* [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) – Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Produktionsprogramm für das Hosten von Live-Traffic erstellen.
* [Verwenden von Adobe Cloud Manager – Programme](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de) – Cloud Manager-Programme stellen eine Reihe von AEM-Umgebungen dar, die logische Gruppen von Geschäftsinitiativen unterstützen, die in der Regel einem erworbenen Service Level Agreement (SLA) entsprechen.
* [AEM as a Cloud Service-Team und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md) – Erfahren Sie, wie Sie mit dem AEM as a Cloud Service-Team und Produktprofilen den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren und einschränken kann.
