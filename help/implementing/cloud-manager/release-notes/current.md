---
title: Versionshinweise für Cloud Manager 2025.1.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Version Cloud Manager 2025.1.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 17f6c359a0396c3ee68b43d0140d637856f7f502
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 93%

---

# Versionshinweise für Cloud Manager 2025.1.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

Erfahren Sie mehr über die Version Cloud Manager 2025.1.0 in AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.1.0 von Cloud Manager in AEM as a Cloud Service wurde am Mittwoch, dem 22. Januar 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den 13. Februar 2025 geplant.


## Neue Funktionen {#what-is-new}

* **Regeln zur Code-Qualität – SonarQube-Server-Upgrade:** Der Schritt „Cloud Manager-Code-Qualität“ wird planmäßig ab Donnerstag, den 13. Februar 2025, den SonarQube-Server 9.9 mit Version 2025.2.0 von Cloud Manager verwenden.

  Zur Vorbereitung sind die aktualisierten SonarQube-Regeln jetzt unter [Code-Qualitätsregeln](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules) verfügbar.

  Sie können die neuen Regeln frühzeitig überprüfen, indem Sie die folgende Pipeline-Textvariable festlegen:

  `CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

  Legen Sie außerdem die folgende Variable fest, um sicherzustellen, dass der Schritt „Code-Qualität“ für denselben Commit ausgeführt wird (wird normalerweise für dieselbe `commitId` übersprungen):

  `CM_DISABLE_BUILD_REUSE` = `true`

![Seite mit der Variablenkonfiguration](/help/implementing/cloud-manager/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe empfiehlt die Erstellung einer neuen CI/CD-Pipeline für die Code-Qualität, die auf derselben Verzweigung wie die Hauptproduktions-Pipeline konfiguriert ist. Legen Sie die entsprechenden Variablen *vor* der Version vom 13. Februar 2025 fest, um zu überprüfen, ob die neuen erzwungenen Regeln keine Blocker einführen.

* **Build-Unterstützung für Java 17 und Java 21:** Kundinnen und Kunden können jetzt mit Java 17 oder Java 21 erstellen und erhalten Zugriff auf Leistungsverbesserungen und neue Sprachfunktionen. Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projekt- und Bibliotheksversionen, finden Sie unter [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Wenn die Build-Version auf Java 17 oder Java 21 festgelegt ist, wird Java 21 als Laufzeit bereitgestellt.

   * **Aktivierung von Funktionen**
      * Diese Funktion wird am Donnerstag, dem 13. Februar 2025, zeitgleich mit dem standardmäßigen Rollout der neuen SonarQube-Version für alle Kundinnen und Kunden aktiviert.
      * Kundinnen und Kunden können sie *sofort* aktivieren, indem sie die beiden oben beschriebenen Variablenkonfigurationen für die Aktualisierung der SonarQube-Version 9.9 festlegen.

   * **Java 21-Laufzeitbereitstellung**
      * Die Java 21-Laufzeit wird beim Erstellen mit Java 17 oder Java 21 bereitgestellt.
      * Der schrittweise Rollout für alle Cloud Manager-Umgebungen beginnt im Februar für Sandboxes und Entwicklungsumgebungen und wird im April auf Produktionsumgebungen ausgeweitet.
      * Kundinnen und Kunden, die mit Java 11 erstellen und die Java 21-Laufzeitumgebung *früher* übernehmen möchten, können sich unter [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com) an Adobe wenden.

* **„CDN-Konfigurationen“ in „Domain-Zuordnungen“ umbenannt**: Im Rahmen der Verbesserungen der Benutzeroberfläche in AEM Cloud Manager wird die Bezeichnung „CDN-Konfigurationen“ jetzt in „Domain-Zuordnungen“ umbenannt. Durch diese Änderung wird die terminologische Angleichung an die Funktionalität verbessert. <!-- CMGR-64738 -->

  ![„CDN-Konfigurationen“ wurden in der Benutzeroberfläche in „Domain-Zuordnungen“ umbenannt](/help/implementing/cloud-manager/release-notes/assets/domain-mappings.png)

* **Bereitstellung einer Edge Delivery-Site mit einem Klick**: Cloud Manager ermöglicht es Benutzenden mit den entsprechenden Berechtigungen und Lizenzen nun, mit nur einem Klick eine beispielhafte Edge Delivery Services-Site zu erstellen. Dieser optimierte Prozess bietet die folgenden automatisierten Funktionen:

   * **GitHub-Integration**: Es wird automatisch ein GitHub-Repository innerhalb einer bestehenden Organisation erstellt, vorkonfiguriert mit einer Bausteinvorlage für Edge Delivery Services.
   * **Installation der AEM-Code-Synchronisierungsanwendung**: Die Installation der AEM-Code-Synchronisierungsanwendung im Repository sorgt für eine nahtlose Synchronisierung und Bereitstellung.
   * **Einrichten einer Umgebung für Zusammenarbeit an Content**: Es wird ein bestimmter Google Drive-Ordner für die Inhaltsspeicherung verknüpft und so eine gemeine Arbeitsumgebung zum Content-Management bereitgestellt.
   * **Inhaltsveröffentlichung**: Benutzende können nun Inhalte für bereitgestellte Sites direkt in der Cloud Manager-Benutzeroberfläche veröffentlichen. Das Ergebnis: einfachere Workflows und höhere Effizienz.
   * **Verbesserte Zusammenarbeit**: Die Plattform ermöglicht es Benutzenden, mehrere Mitarbeitende zum Google Drive-Ordner für die Inhaltsspeicherung hinzuzufügen, was Team-Arbeit und Inhaltsbeiträge vereinfacht.

  Diese Verbesserungen zielen darauf ab, die Automatisierung zu optimieren, Einrichtungsprozesse zu vereinfachen und die Zusammenarbeit für Edge Delivery Services-Benutzende zu verbessern. <!-- CMGR-59362 -->

  ![Bereitstellen einer Edge Delivery-Site](/help/implementing/cloud-manager/release-notes/assets/eds-one-click-60.png)

  ![Dialogfeld zum Bereitstellen einer Edge Delivery-Site](/help/implementing/cloud-manager/release-notes/assets/eds-provision-60.png)

* **Erweiterte Unterstützung für Edge Delivery Services-Sites**: Cloud Manager unterstützt nun das Onboarding für die neuesten Edge Delivery Services-Sites. Dieses Update beinhaltet eine umfassende Überarbeitung des CDN und Bereitstellungs-Stacks und führt so zu mehr Robustheit und besserer Wartbarkeit.

* **Erweiterte Filteroptionen für Pipelines**: Cloud Manager bietet nun auf der Pipelines-Seite erweiterte Filteroptionen, mit denen Sie schnell auf relevante Daten zugreifen und die Bereitstellungseffizienz verbessern können. Zu den wichtigsten Funktionen gehören u. a.:

   * **Filterung mit mehreren Kriterien**: Verfeinern Sie Suchergebnisse mit Filtern wie Pipeline-Name, Umgebung und Bereitstellungs-Code.
   * **Optimierte Pipeline-Suche**: Finden Sie bestimmte Pipelines nun einfacher und profitieren Sie von einer schnelleren Navigation und verbessertem Workflow-Management.

  Alles in allem wird sowohl die Verwaltung von Pipelines als auch deren Bereitstellung durch diese Verbesserungen effizienter und benutzerfreundlicher.

  ![Pipeline-Filterfunktion](/help/implementing/cloud-manager/release-notes/assets/pipeline-filters.png)

* **Selfservice-CDN-Konfiguration für Edge Delivery Service**: Neue Anwendende von Edge Delivery Service können ihr CDN nun unabhängig über Cloud Manager konfigurieren. Dieses Update erweitert die Unterstützung von `.hlx.page/live` auf die neue `.aem.page/live` und bietet so mehr Flexibilität und eine optimierte Einrichtung.

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adopter-Programm von Cloud Manager teil und nutzen Sie die Möglichkeit, zukünftige Funktionen zu testen.

* **Early-Adopter-Programm-Update – PR-Validierungsunterstützung für Bitbucket und GitLab**: Cloud Manager unterstützt jetzt die Pull Request(PR)-Validierung sowohl für Cloud- als auch für selbst gehostete Versionen von Bitbucket und GitLab. Mit dieser Funktion können Kundinnen und Kunden ihre Code-Änderungen vor dem Zusammenführen einer PR anhand der Adobe-Qualitätsschwellen für Code testen. Durch eine höhere Code-Qualität vor dem Zusammenführen verbessert diese Erweiterung die Erfolgsrate von Code-Änderungen in Produktions-Pipelines erheblich, sie reduziert die Time-to-Market und optimiert Entwicklungs-Workflows.

Weitere Informationen zum Einbringen eines eigenen Gits („Bring Your Own Git“) – nun mit Unterstützung für GitLab und Bitbucket – und zum Registrieren als Early Adopter finden Sie in den [Versionshinweisen zur Cloud Manager-Version von Oktober 2024](/help/implementing/cloud-manager/release-notes/2024/2024-10-0.md##gitlab-bitbucket).

* **Erweiterte Testumgebung** Eine speziell entwickelte Lösung, die die Lücke zwischen Entwicklung und Produktion schließt. Diese Umgebung ist auf die Unternehmensanforderungen zugeschnitten und repliziert Spezifikationen auf Produktionsebene, um genaue Benutzerakzeptanztests (UAT) und gründliche Leistungsbewertungen zu unterstützen.

Wenn Sie am Early-Adopter-Programm teilnehmen möchten, füllen Sie [dieses Formular aus](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Furldefense.com%2Fv3%2F__https%3A%2Fwww.feedbackprogram.adobe.com%2Fh%2Fs%2F6N425LYG1jQ1Nc0F20Zllt__%3B!!OgNkHJCYlf_CHg!fIp-QrZ9si3kcUIjRCniEzqAA8FcU1iN34SGQFtlcQ36eUQXOZWbDHP7oZajqddgpuOMAVL5CQpkZ6ths76Qks8%24&amp;data=05%7C02%7Cpanchapa%40adobe com%7Cf81bcaa4b20544f1818b08dccd07c78c%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638610680502164019%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMz IILCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=aGo6zz2ldPrta4lpvo3CLNENR5ghHDCPbG1adUaNZQ%3D&amp;reserved=0) und senden Sie eine E-Mail an [earlyadopter_cs_advtestenvironment@adobe.com](mailto:earlyadopter_cs_advtestenvironment@adobe.com) mit Ihrem `OrgID`.



<!-- ## Bug fixes -->




<!-- ## Known issues {#known-issues} -->
