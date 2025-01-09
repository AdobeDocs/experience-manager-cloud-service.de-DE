---
title: Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen
description: Erfahren Sie mehr über die Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen in AEM as a Cloud Service
feature: Security
role: Admin
hide: true
hidefromtoc: true
source-git-commit: c3e3905d3896d79149a386241d798f78631184b3
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen {#changes-in-user-group-and-product-profile-synchronization}

Wenn sich ein Benutzer bei AEM as a Cloud Service anmeldet oder ein Zugriffstoken verwendet wird, werden Adobe Admin Console-Benutzergruppen, Produktprofile und Produktprofildienste als Gruppen im AEM-Repository synchronisiert.

Am 28. Januar werden einige Änderungen am Synchronisierungsverhalten vorgenommen, sodass weniger Gruppen in AEM angezeigt werden, um die Benutzeroberfläche übersichtlicher zu gestalten und die Leistung zu optimieren. Zwei Kategorien von AEM-Gruppen werden entfernt:

1. AEM-Gruppen mit dem Suffix `GROUP_NAME_SUFFIX`. Diese Gruppen werden nicht in der Adobe Developer Console, sondern wie unten dargestellt im AEM-Gruppenverwaltungs-Bildschirm angezeigt. Falls Ihre AEM-Anwendung nicht auf diese Gruppen verweist, sollten Sie stattdessen Adobe Admin Console-Benutzergruppen verwenden.

   ![Entfernte Gruppen 1](/help/security/assets/removed-groups-1.png)

1. AEM-Gruppen, die mit Adobe Admin Console-Produktprofilen verknüpft sind, die nicht mit der spezifischen AEM-Ebene oder Umgebungskombination zusammenhängen (z. B. `author` oder `e4535`). Dazu können Produktprofile gehören, die:

   * Verwandt mit anderen Adobe-Produkten
   * mit Bezug zu anderen AEM-Programmen
   * mit anderen AEM-Umgebungen im selben AEM-Programm verknüpft sind
   * bezieht sich auf eine andere Ebene (z. B. `author` vs. `publish`) in derselben AEM-Umgebung
   * mit Cloud Manager verbunden (z. B. `Business Owner - Cloud Service`)

   Im folgenden Bild gibt es beispielsweise viele Zeilen mit dem Muster `AEM Administrators-<suffix>` oder `AEM Users-<suffix>`, wobei das Suffix nicht mit der aktuellen Umgebung zusammenhängt.

   ![Entfernte Gruppen 2](/help/security/assets/removed-groups-2.png)

Sie können überprüfen, welches Suffix mit der aktuellen Umgebung verbunden ist, indem Sie **Zugriff verwalten - Autorenprofile** (oder **Publish-Profile**) im Aktionsmenü der Umgebung in Cloud Manager auswählen.

![Suffixe überprüfen](/help/security/assets/suffix-check.png)

Dadurch wird zur Adobe Admin Console navigiert, wie im folgenden Screenshot dargestellt. Beachten Sie, dass der `<suffix>` entweder ein zufälliger Zeichensatz oder vielmehr die Ebene und Programm- und Umgebungs-IDs (z. B. `author - Program 12345 - Environment 45678`) sein kann.

![Suffixe in der Admin Console ](/help/security/assets/admin-console-profile-suffixes.png)

Falls Ihre AEM-Anwendung nicht auf diese Gruppen verweist, sollten Sie stattdessen Adobe Admin Console-Benutzergruppen verwenden.

>[!NOTE]
>
>Achten Sie insbesondere auf die folgenden potenziellen Fallstricke:
>
>1. Ihre AEM-Anwendung basiert auf einer AEM-Gruppe, die aus einem Cloud Manager-Produktprofil synchronisiert wurde
>1. Die Veröffentlichungsebene Ihrer AEM-Anwendung beruht auf einer AEM-Gruppe, die mit einem Produktprofil der Autorenebene synchronisiert wurde. Dies gilt auch für das umgekehrte Szenario (Autorenebene, die auf der Veröffentlichungsebene basiert).