---
title: Integration von [!DNL Experience Manager Assets] mit  [!DNL Adobe Workfront]
description: Einführung in die Integration zwischen [!DNL Assets] und [!DNL Workfront]
role: Admin, Leader, Architect
feature: Workfront Integrations and Apps
exl-id: 365de3dc-51db-4dcf-94e2-104b5a5d33a8
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '390'
ht-degree: 100%

---

# Integration von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] mit [!DNL Adobe Workfront] {#assets-integration-overview}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

[!DNL Adobe Workfront] ist ein Programm für das Arbeits-Management, mit dem Sie den gesamten Arbeitszyklus an einem Ort verwalten können. Die Integration von [!DNL Workfront] und [!DNL Adobe Experience Manager Assets] ermöglicht es Unternehmen, die Geschwindigkeit von Inhalten und die Zeit bis zur Markteinführung zu verbessern, indem sie Workfront und Digital Asset Management miteinander verbinden. Im Rahmen der Verwaltung ihrer Arbeit in Workfront haben Benutzer Zugriff auf die erforderlichen Dokumente und Bilder.

Adobe bietet die [native Integration von [!DNL Workfront] und [!DNL Adobe Experience Manager Assets] an (durch Unterstützung von Assets Essentials und Assets as a Cloud Service)](https://experienceleague.adobe.com/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations.html?lang=de).

Mit der nativen Experience Manager-Integration können Sie:

* Schnelle Einrichtung der Integration in Workfront.

* Automatische Erstellung von Ordnern, die mit Workfront und Experience Manager verknüpft sind

* Einfaches Synchronisieren von Metadaten für vorhandene verknüpfte Assets

* Automatisches Aktualisieren von Projektmetadaten, wenn sie in Workfront geändert werden

* Einfaches Verbinden mehrerer Experience Manager Assets-Repositorys mit einer Workfront-Umgebung oder von mehreren Workfront-Umgebungen mit einem Experience Manager Assets-Repository über Organisations-IDs hinweg.


## Erweiterter Connector von Adobe Workfront für Experience Manager {#enhanced-connector-information}


Seit Juni 2022 bietet Adobe eine neue native Integration für die Verbindung von Workfront mit Adobe Experience Manager Assets as a Cloud Service. Diese Integration ist zu einer erforderlichen Methode geworden, um diese beiden Lösungen miteinander zu verbinden. Jede künftige neue Implementierung des erweiterten Connectors (1.9.8 und höher) zur Verbindung von Workfront mit AEM Assets as a Cloud Service wird blockiert. Weitere Informationen zum Einrichten dieser Integration finden Sie unter [Konfigurieren der Integration von Experience Manager Assets as a Cloud Service](workfront-connector-configure.md).

>[!NOTE]
>
>Adobe unterstützt nicht die gleichzeitige Verwendung des erweiterten Connectors für Workfront für Experience Manager und der Experience Manager-Integration.

Für Installationen, die vor Juni 2022 installiert wurden, finden Sie im Folgenden einige Hinweise für die Bereitstellung und Konfiguration von [!DNL Adobe Workfront for Experience Manager enhanced connector]:

* Adobe erfordert die Bereitstellung und Konfiguration des [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services]. Wird diese ohne zertifizierten Partner oder [!DNL Adobe Professional Services] bereitgestellt oder konfiguriert, wird sie von Adobe nicht unterstützt.
* Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager], die diesen Connector redundant machen. In diesem Fall kann es erforderlich sein, dass Kunden diesen Connector nicht mehr verwenden.
* Adobe unterstützt die Versionen 1.7.4 und höher des erweiterten Connectors. Frühere Vorabversionen und benutzerdefinierte Versionen werden nicht unterstützt. Informationen zum Überprüfen der erweiterten Connector-Version finden Sie in Schritt 5(a) der [Installationsanweisungen für den erweiterten Connector](workfront-connector-install.md).
* Siehe [Partnerzertifizierungsprüfung für den erweiterten Connector von Workfront for Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Informationen zur Prüfung finden Sie im [Prüfungshandbuch](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).