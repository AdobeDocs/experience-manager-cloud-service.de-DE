---
title: Funktionsumschalter aktivieren, um Funktionen für frühzeitige Anpassungen und Vorabversionen zu integrieren
description: Der Feature Toggle ist eine Funktion in AEM, mit der Admins neue Funktionen in einer Laufzeitumgebung aktivieren können.
feature: Adaptive Forms, Foundation Components, Core Components
role: User, Developer
source-git-commit: cc4fccc51f487170bf6c14e4b302a8d5912c33a0
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 6%

---

# Funktionsumschalter in Adobe Experience Software Development Kit (AEM SDK) aktivieren

Mit dem Feature Toggle in AEM können Admins Funktionen zur Laufzeit aktivieren oder deaktivieren, die sich ideal für die Verwaltung von Early-Adopter- und Vorabversionsfunktionen ohne Code-Änderungen eignen. Es unterstützt schrittweise Rollouts, A/B-Tests und die schnelle Deaktivierung instabiler Funktionen.

In diesem Artikel wird beschrieben, wie Sie die Funktions-Umschalter im lokalen AEM-SDK-Setup aktivieren, das AEM as a Cloud Service mithilfe von SDK und Dispatcher simuliert. Mit dieser Einrichtung können Teams Tests in einer produktionsähnlichen Umgebung durchführen, bevor sie in der Cloud bereitgestellt werden.

## Warum sollten in einem AEM SDK-Setup Funktions-Umschalter verwendet werden?

Beim Arbeiten mit einem AEM SDK-Setup können Sie mit den Funktionen die Hilfe zu folgenden Themen umschalten:

* Testen von Experimentalfunktionen sicher.

* Das Rollout neuer Komponenten in Phasen.

* Pflege einer einzelnen Code-Basis über mehrere Umgebungen hinweg.

* Reduzierung des Risikos bei Bereitstellungen und Upgrades.

## Voraussetzungen

Stellen Sie vor dem Aktivieren der Funktionsumschalter in Ihrem AEM SDK-Setup Folgendes sicher:

* Benutzer ist Mitglied `forms-users` Gruppe.

* Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/bundles` und überprüfen Sie, ob das Bundle **(com.adobe.granite.toggle.impl.dev-1.1.2.jar)** vorhanden ist. Falls nicht vorhanden (laden [ das Bundle über den Link herunter](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/com.adobe.granite.toggle.impl.dev-1.1.2%20.jar).

  ![Feature-Umschalter](/help/forms/assets/aem-web-console-bundle.png)

### Umschalter für Funktionen aktivieren

Führen Sie die folgenden Schritte aus, um Funktions-Umschalter in Ihrer AEM SDK-Instanz zu aktivieren:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.

1. Navigieren Sie zu `http://author-instance-url:portnumber/system/console/configMgr`.

1. Suchen Sie im Konfigurations-Manager nach Adobe Granite Dynamic Toggle Provider .

   ![Feature-Umschalter](/help/forms/assets/aem-web-console-confi.png)

1. Klicken Sie auf das Symbol ✏️ .
1. Klicken Sie im Abschnitt Aktivierte Umschalter auf ➕ .
1. Fügen Sie die Funktions-Umschalter-ID für die Funktion hinzu, wie in der Abbildung unten dargestellt.
   ![Feature-Umschalter](/help/forms/assets/feature-toggle.png)

1. Klicken Sie auf „Speichern“.

>[!NOTE]
>
> Die Umschalter-ID für Funktionen finden Sie im Dokument für die Early-Adopter-Funktionen.


### Umschalten zwischen Funktionen deaktivieren

Gehen Sie wie folgt vor, um die Umschalter für Funktionen zu deaktivieren, deren Umschalter aktiviert sind:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
1. Navigieren Sie zu `http://author-instance-url:portnumber/system/console/configMgr`.
1. Suchen Sie im Konfigurations-Manager nach Adobe Granite Dynamic Toggle Provider .
1. Klicken Sie auf das Symbol ✏️.
1. Klicken Sie im Abschnitt Deaktivierte Umschalter auf ➕.
1. Fügen Sie die Umschaltnummer hinzu, damit die Funktion deaktiviert wird.

   ![Feature-Umschalter](/help/forms/assets/disable-toggle-feature.png)

### Technische Überlegung

Funktionsumschalter werden zur Laufzeit verwaltet und eignen sich am besten für Entwicklungs- oder Testsetups. Stellen Sie bei einem AEM SDK-Setup sicher, dass die Umschalter versionsgesteuert sind und mit CI/CD synchronisiert werden. Seitenaktualisierung oder Cache-Leerung können erforderlich sein, damit die Änderungen berücksichtigt werden.

>[!NOTE]
>
> Wenden Sie sich an das Adobe-Supportteam, um den Funktionsumschalter für die Produktionsumgebung zu aktivieren.

