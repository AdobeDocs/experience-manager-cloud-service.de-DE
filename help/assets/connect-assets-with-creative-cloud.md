---
title: Verbinden von AEM Assets mit Creative Cloud
description: Erfahren Sie, wie Sie AEM Assets konfigurieren und mit Creative Cloud verbinden. Stellen Sie eine Verbindung zu einer Creative Cloud-Berechtigung her, die einer anderen IMS-Organisation zugewiesen wurde, um die neuesten Creative Cloud-Integrationen in AEM Assets, einschließlich Express- und Creative Cloud-Bibliotheken, einfach zu verwenden.
source-git-commit: 8c0c01be301ccaeac4e658c16d63227e55b67fcf
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Verbinden von AEM Assets mit Creative Cloud  {#cross-org-entitlements}

Experience Manager Assets hat die Möglichkeit, eine Verbindung zu einer Creative Cloud-Berechtigung herzustellen, die einer anderen IMS-Organisation zugewiesen wurde, um die neuesten Creative Cloud-Integrationen in AEM Assets, einschließlich Express- und Creative Cloud-Bibliotheken, einfach zu verwenden.

Wenn Ihre Creative Cloud-Produkte und AEM Assets für verschiedene IMS-Organisationen bereitgestellt werden, können Sie eine Verbindung zu einer anderen Creative Cloud-Organisation herstellen, um integrierte Workflows zwischen den beiden Lösungen ausführen zu können.

## Voraussetzungen {#prerequisites}

* Administratorrechte für Experience Manager Assets

* Aktive Berechtigung zum Creative Cloud für dieselbe Benutzer-ID, die über Creative Cloud und Experience Manager hinweg verwendet wird. Berechtigungen für persönliche und Federated IDs mit derselben E-Mail-Adresse werden als unterschiedliche Benutzer-IDs behandelt.

## Verbindung zu einer neuen Creative Cloud-Organisation herstellen {#connect-to-creative-cloud-org}

Führen Sie die folgenden Schritte aus, um eine Verbindung zu einer neuen Creative Cloud-Organisation herzustellen:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Creative Cloud]**.

1. Wählen Sie die neue Creative Cloud-Organisation mithilfe der **[!UICONTROL Neue Creative Cloud-Organisations-ID auswählen]** Dropdown-Liste. In der Liste werden alle Organisationen angezeigt, auf die Sie Zugriff haben. Wählen Sie die Organisation mit aktiven Creative Cloud-Berechtigungen aus.

1. Klicks **[!UICONTROL Switch-Organisationen]** , um zur neuen Organisation zu wechseln.

   ![Organisationsübergreifende Berechtigungen](assets/cross-org-entitlements.png)

## Einschränkungen {#limitations}

* Sie können AEM Assets jeweils mit einer Creative Cloud-Organisation verbinden. Die gleichzeitige Verbindung mit mehreren Creative Cloud-Organisationen wird nicht unterstützt.

* Die Creative Cloud-Organisation, mit der Sie innerhalb von AEM Assets eine Verbindung herstellen, gilt für alle Benutzer in Ihrem Unternehmen.

