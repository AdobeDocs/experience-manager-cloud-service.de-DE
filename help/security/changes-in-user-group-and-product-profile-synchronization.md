---
title: Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen
description: Erfahren Sie mehr über die Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen in AEM as a Cloud Service
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 0b097ab3-bf1d-4d43-9e19-d544594844ef
source-git-commit: 5c103fcce1ae47bc89f4f572d89967c62c1f7603
workflow-type: ht
source-wordcount: '385'
ht-degree: 100%

---

# Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen {#changes-in-user-group-and-product-profile-synchronization}

Wenn sich Benutzende bei AEM as a Cloud Service anmelden oder ein Zugriffs-Token verwendet wird, werden Benutzergruppen, Produktprofile und Produktprofildienste von Adobe Admin Console als Gruppen im AEM-Repository synchronisiert.

Ab der AEM-Wartungsversion 19149 ändert sich das Verhalten bei der Gruppensynchronisierung, um die Benutzeroberfläche übersichtlicher zu gestalten und die Leistung zu optimieren. Insbesondere wird die Benutzergruppenmitgliedschaft für die beiden folgenden AEM-Gruppenkategorien nicht mehr synchronisiert:

1. AEM-Gruppen mit dem Suffix `GROUP_NAME_SUFFIX`. Diese Gruppen werden nicht in der Adobe Developer Console, sondern wie unten dargestellt im AEM-Bildschirm „Gruppenverwaltung“ angezeigt. Falls Ihre AEM-Anwendung auf diese Gruppen verweist, sollten Sie stattdessen unbedingt auf Adobe Admin Console-Benutzergruppen ohne dieses Suffix verweisen.

   ![Entfernte Gruppen 1](/help/security/assets/removed-groups-1.png)

1. AEM-Gruppen, die mit Adobe Admin Console-Produktprofilen verknüpft sind, die nicht mit der spezifischen Umgebung zusammenhängen. Dazu können Produktprofile gehören, die verbunden sind mit:

   * anderen Adobe-Produkten
   * anderen AEM-Programmen
   * anderen AEM-Umgebungen im selben AEM-Programm
   * Cloud Manager (z. B. `Business Owner - Cloud Service`)

   Im folgenden Bild gibt es beispielsweise viele Zeilen mit dem Muster `AEM Administrators-<suffix>` oder `AEM Users-<suffix>`, wobei das Suffix nicht mit der aktuellen Umgebung zusammenhängt.

   ![Entfernte Gruppen 2](/help/security/assets/removed-groups-2.png)

Sie können überprüfen, welches Suffix mit der aktuellen Umgebung verbunden ist, indem Sie **Zugriff verwalten – Autorenprofile** (oder **Veröffentlichungsprofile**) im Aktionsmenü der Umgebung in Cloud Manager auswählen.

![Überprüfen von Suffixen](/help/security/assets/suffix-check.png)

Dadurch navigieren Sie zur Adobe Admin Console, wie im folgenden Screenshot dargestellt. Es ist zu beachten, dass `<suffix>` entweder ein zufälliger Zeichensatz oder vielmehr die Ebene und Programm- und Umgebungs-IDs (z. B. `author - Program 12345 - Environment 45678`) sein kann.

![Suffixe in der Admin Console ](/help/security/assets/admin-console-profile-suffixes.png)

Falls Ihre AEM-Anwendung auf eine Gruppe verweist, die nicht mehr in AEM angezeigt wird, stellen Sie sicher, dass Sie stattdessen entweder i) ein Produktprofil aus der richtigen AEM-Instanz oder ii) eine Adobe Admin Console-Benutzergruppe verwenden.

Die Gruppenmitgliedschaften der Benutzenden werden synchronisiert, wenn sie sich bei der Umgebung anmelden; sie werden aus Gruppen entfernt, die nicht mit der aktuellen Umgebung zusammenhängen. Die Gruppen selbst bleiben bestehen und umfassen Benutzende, die sich seit der Aktivierung der Funktion nicht mehr angemeldet haben.
