---
title: Aktivieren des Funktionsumschalters, um Early-Adopter- und Vorabversionsfunktionen zu integrieren
description: Der Funktionsumschalter ist eine Funktion in AEM, mit der Admins neue Funktionen in einer Laufzeitumgebung aktivieren können.
feature: Adaptive Forms, Foundation Components, Core Components
role: User, Developer
exl-id: 3ad1370a-a399-4fbe-8168-c3a1cee06336
source-git-commit: c1d62f0dd5a25da7fbeef537e1c28fa8421f42cd
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 45%

---

# Aktivieren des Funktionsumschalters im Adobe Experience Software Development Kit (AEM SDK)

Mit dem Feature Toggle in AEM können Admins Funktionen zur Laufzeit aktivieren oder deaktivieren, die sich ideal für die Verwaltung von Early-Adopter- und Vorabversionsfunktionen ohne Code-Änderungen eignen. Es unterstützt schrittweise Rollouts, A/B-Tests und die schnelle Deaktivierung instabiler Funktionen.

In diesem Artikel wird beschrieben, wie Sie die Funktions-Umschalter im lokalen AEM-SDK-Setup aktivieren, das AEM as a Cloud Service mithilfe von SDK und Dispatcher simuliert. Mit dieser Einrichtung können Teams Tests in einer produktionsähnlichen Umgebung durchführen, bevor sie in der Cloud bereitgestellt werden.

## Warum sollten in einem AEM SDK-Setup Funktions-Umschalter verwendet werden?

Beim Arbeiten mit einem AEM SDK-Setup können Sie mit den Funktionen die Hilfe zu folgenden Themen umschalten:

* Sicheres Testen von Experimentalfunktionen.

* Rollout neuer Komponenten in Phasen.

* Pflege einer einzelnen Code-Basis über mehrere Umgebungen hinweg.

* Reduzierung des Risikos bei Bereitstellungen und Upgrades.

## Voraussetzungen

Stellen Sie vor dem Aktivieren der Funktionsumschalter in Ihrem AEM SDK-Setup Folgendes sicher:

* Die Benutzerin bzw. der Benutzer ist Mitglied der Gruppe `forms-users`.

* Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/bundles` und überprüfen Sie, ob das Bundle **(com.adobe.granite.toggle.impl.dev-1.1.2.jar)** vorhanden ist. Falls nicht vorhanden [laden Sie das Bundle über den Link herunter](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]s/cq650/hotfix/com.adobe.granite.toggle.impl.dev-1.1.8.jar).

  ![Funktionsumschalter](/help/forms/assets/aem-web-console-bundle.png)

### Funktionsumschalter aktivieren

Führen Sie die folgenden Schritte aus, um Funktions-Umschalter in Ihrer AEM SDK-Instanz zu aktivieren:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.

1. Navigieren Sie zu `http://author-instance-url:portnumber/system/console/configMgr`.

1. Suchen Sie im Konfigurations-Manager nach Adobe Granite Dynamic Toggle Provider .

   ![Funktionsumschalter](/help/forms/assets/aem-web-console-confi.png)

1. Klicken Sie auf das Symbol ✏️ .
1. Klicken Sie im Abschnitt Aktivierte Umschalter auf ➕ .
1. Fügen Sie die Funktionsumschalter-ID für die Funktion hinzu, wie in der Abbildung unten dargestellt.
   ![Funktionsumschalter](/help/forms/assets/feature-toggle.png)

1. Klicken Sie auf „Speichern“.

>[!NOTE]
>
> Die Funktionsumschalter-ID finden Sie im dedizierten Dokument für die Early-Adopter-Funktionen.


### Deaktivieren des Funktionsumschalters

Gehen Sie wie folgt vor, um die Funktionsumschalter für Funktionen zu deaktivieren, deren Umschalter aktiviert sind:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
1. Navigieren Sie zu `http://author-instance-url:portnumber/system/console/configMgr`.
1. Suchen Sie im Konfigurations-Manager nach Adobe Granite Dynamic Toggle Provider .
1. Klicken Sie auf das Symbol ✏️.
1. Klicken Sie im Abschnitt Deaktivierte Umschalter auf ➕.
1. Fügen Sie die Umschalternummer für die zu deaktivierende Funktion hinzu.

   ![Funktionsumschalter](/help/forms/assets/disable-toggle-feature.png)

### Technische Überlegung

Funktionsumschalter werden zur Laufzeit verwaltet und eignen sich am besten für Entwicklungs- oder Testsetups. Stellen Sie bei einem AEM SDK-Setup sicher, dass die Umschalter versionsgesteuert sind und mit CI/CD synchronisiert werden. Seitenaktualisierung oder Cache-Leerung können erforderlich sein, damit die Änderungen berücksichtigt werden.

>[!NOTE]
>
> Wenden Sie sich an das Adobe-Supportteam, um den Funktionsumschalter für die Produktionsumgebung zu aktivieren.
