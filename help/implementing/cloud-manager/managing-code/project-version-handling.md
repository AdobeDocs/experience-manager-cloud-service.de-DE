---
title: Umgang mit Maven-Projektversionen
description: 'Für Staging- und Produktionsimplementierungen von AEM as a Cloud Service generiert Cloud Manager eine eindeutige, inkrementierende Version. '
exl-id: 658bcbed-0733-45da-a3e3-9a5f817099c5
source-git-commit: 21607fadf33dac038c7f794b933b92f60b8e20a9
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 44%

---


# Umgang mit Maven-Projektversionen {#maven-project-version-handling}

Für Staging- und Produktionsimplementierungen von AEM as a Cloud Service generiert Cloud Manager eine eindeutige, inkrementelle Version

Diese Version wird auf der Seite [Seite mit Details zur Pipelineausführung](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) sowie der Aktivitätsseite. Wenn ein Build ausgeführt wird, wird das Maven-Projekt aktualisiert, um diese Version zu verwenden. Außerdem wird im Git-Repository ein Tag mit dieser Version als Name erstellt.

Wenn die Originalversion des Projekts bestimmte Kriterien erfüllt, führt die aktualisierte Maven-Projektversion sowohl die Originalversion des Projekts als auch die von Cloud Manager generierte Version zusammen. Das Tag verwendet jedoch immer die generierte Version. Damit diese Zusammenführung erfolgt, muss die ursprüngliche Projektversion mit genau drei Versionssegmenten erstellt werden, z. B. `1.0.0` oder `1.2.3`, aber nicht `1.0` oder `1`und die Originalversion darf nicht in `-SNAPSHOT`.

>[!IMPORTANT]
>
>Dieser ursprüngliche Projektversionswert muss statisch im `<version>`-Element der `pom.xml`-Datei der obersten Ebene in der Git-Repository-Verzweigung gesetzt werden.

Wenn die Originalversion diese Kriterien erfüllt, wird die generierte Version als neues Versionssegment an die Originalversion angehängt. Die generierte Version wird außerdem geringfügig geändert, um eine ordnungsgemäße Sortierung und Versionsverwaltung einzuschließen. Angenommen, eine generierte Version von `2019.926.121356.0000020490` würde die folgenden Ergebnisse haben.

| Version | Version in `pom.xml` | Kommentar |
|---|---|---|
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Richtig geformte Originalversion |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Snapshot-Version, überschrieben |
| `1` | `2019.926.121356.0000020490` | Unvollständige Version, überschrieben |

>[!NOTE]
>
>Unabhängig davon, ob die Originalversion in die mit Cloud Manager initialisierte Version integriert wurde oder nicht, ist die Originalversion als Maven-Eigenschaft mit dem Namen verfügbar `cloudManagerOriginalVersion`.
