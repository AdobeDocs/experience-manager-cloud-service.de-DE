---
title: Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen
description: Erfahren Sie mehr über die Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen in AEM as a Cloud Service
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 0b097ab3-bf1d-4d43-9e19-d544594844ef
source-git-commit: cddfcddc0ca3652270bdb735e580386ac9ff1fc7
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen {#changes-in-user-group-and-product-profile-synchronization}

Wenn sich ein Benutzer bei AEM as a Cloud Service anmeldet oder ein Zugriffstoken verwendet wird, werden Adobe Admin Console-Benutzergruppen, Produktprofile und Produktprofildienste als Gruppen im AEM-Repository synchronisiert.

Bei AEM-Versionen über 18751 (ein Wartungsversion wird ab dem 27. Januar in Produktionsumgebungen eingeführt), werden einige Änderungen am Synchronisierungsverhalten vorgenommen, sodass weniger Gruppen in AEM angezeigt werden, um die Benutzeroberfläche übersichtlicher zu gestalten und die Leistung zu optimieren. Zwei Kategorien von AEM-Gruppen werden entfernt:

1. AEM-Gruppen mit dem Suffix `GROUP_NAME_SUFFIX`. Diese Gruppen werden nicht in der Adobe Developer Console, sondern wie unten dargestellt im AEM-Gruppenverwaltungs-Bildschirm angezeigt. Falls Ihre AEM-Anwendung nicht auf diese Gruppen verweist, verweisen Sie stattdessen auf Adobe Admin Console-Benutzergruppen ohne dieses Suffix.

   ![Entfernte Gruppen 1](/help/security/assets/removed-groups-1.png)

1. AEM-Gruppen, die mit Adobe Admin Console-Produktprofilen verknüpft sind, die nicht mit der bestimmten Umgebung zusammenhängen. Dazu können Produktprofile gehören, die:

   * Verwandt mit anderen Adobe-Produkten
   * mit Bezug zu anderen AEM-Programmen
   * mit anderen AEM-Umgebungen im selben AEM-Programm verknüpft sind
   * mit Cloud Manager verbunden (z. B. `Business Owner - Cloud Service`)

   Im folgenden Bild gibt es beispielsweise viele Zeilen mit dem Muster `AEM Administrators-<suffix>` oder `AEM Users-<suffix>`, wobei das Suffix nicht mit der aktuellen Umgebung zusammenhängt.

   ![Entfernte Gruppen 2](/help/security/assets/removed-groups-2.png)

Sie können überprüfen, welches Suffix mit der aktuellen Umgebung verbunden ist, indem Sie **Zugriff verwalten - Autorenprofile** (oder **Publish-Profile**) im Aktionsmenü der Umgebung in Cloud Manager auswählen.

![Suffixe überprüfen](/help/security/assets/suffix-check.png)

Dadurch wird zur Adobe Admin Console navigiert, wie im folgenden Screenshot dargestellt. Beachten Sie, dass der `<suffix>` entweder ein zufälliger Zeichensatz oder vielmehr die Ebene und Programm- und Umgebungs-IDs (z. B. `author - Program 12345 - Environment 45678`) sein kann.

![Suffixe in der Admin Console ](/help/security/assets/admin-console-profile-suffixes.png)

Sollte Ihre AEM-Anwendung auf eine Gruppe verweisen, die nicht mehr in der AEM angezeigt wird, stellen Sie sicher, dass Sie entweder i) ein Produktprofil aus der richtigen AEM-Instanz oder ii) eine Adobe Admin Console-Benutzergruppe verwenden.

