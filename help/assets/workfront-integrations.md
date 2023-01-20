---
title: „Integration von [!DNL Experience Manager Assets] mit  [!DNL Adobe Workfront]“
description: Einführung in die Integration zwischen [!DNL Assets] und [!DNL Workfront]
role: Admin,Leader,Architect
feature: Integrations
exl-id: 365de3dc-51db-4dcf-94e2-104b5a5d33a8
source-git-commit: 269dff32b41dba86fb048418da3f3b3ef8a6781e
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 94%

---

# Integration von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] mit [!DNL Adobe Workfront] {#assets-integration-overview}

[!DNL Adobe Workfront] ist ein Programm für das Arbeits-Management, mit dem Sie den gesamten Arbeitszyklus an einem Ort verwalten können. Die Integration von [!DNL Workfront] und [!DNL Adobe Experience Manager Assets] ermöglicht es Unternehmen, die Geschwindigkeit von Inhalten und die Zeit bis zur Markteinführung zu verbessern, indem sie Workfront und Digital Asset Management miteinander verbinden. Im Rahmen der Verwaltung ihrer Arbeit in Workfront haben Benutzer Zugriff auf die erforderlichen Dokumente und Bilder.

Adobe von Angeboten an [integrieren [!DNL Workfront] und [!DNL Adobe Experience Manager Assets] nativ (Unterstützung von Assets Essentials und Assets as a Cloud Service) oder Verwendung des Workfront for Experience Manager Enhanced Connector](https://experienceleague.adobe.com/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations.html?lang=de). Bei einer nativen Integration benötigen Sie keinen Connector, um die beiden Lösungen zu integrieren.

>[!NOTE]
>
>Adobe unterstützt nicht die parallele Verwendung von Workfront für Experience Manager-erweiterte Connectoren und Experience Manager-Integrationen.

Mit der nativen Experience Manager-Integration und [!DNL Workfront for Experience Manager enhanced connector] können Sie:

| Native [!DNL Adobe Experience Manager Assets]-Funktionen | [!DNL Workfront for Experience Manager enhanced connector]-Funktionen |
|---|---|
| <ul><li>Schnelle Einrichtung der Integration in Workfront.</li><li>Automatische Erstellung von Ordnern, die mit Workfront und Experience Manager verknüpft sind</li><li>Einfaches Synchronisieren von Metadaten für vorhandene verknüpfte Assets</li><li>Automatisches Aktualisieren von Projektmetadaten, wenn sie in Workfront geändert werden</li><li>Einfaches Verbinden mehrerer Experience Manager Assets-Repositorys mit einer Workfront-Umgebung oder von mehreren Workfront-Umgebungen mit einem Experience Manager Assets-Repository über Organisations-IDs hinweg.</li> | <ul><li>Erstellen von automatisch verknüpften Experience Manager-Ordnern in Workfront und organisieren dieser Ordner anhand von Workfront-Portfolios, -Programmen und -Projekten.</li><li>Synchronisieren der Workfront-Projektmetadaten mit den verknüpften Experience Manager-Ordnern.</li><li>Aktualisierung der Experience Manager-Metadaten mit neuen Versionen.</li><li>Setzen des Status von Workfront-Objekten auf der Grundlage konfigurierbarer Bedingungen mit Experience Manager-Workflows.</li><li>Veröffentlichen von Assets in der Veröffentlichungsumgebung von Experience Manager oder in Brand Portal.</li> |

Unten finden Sie die [unterstützten Funktionen für einen Vergleich](#feature-parity-matrix) zwischen der nativer Integration mit einer Integration, bei der Connectoren zwischen den beiden Lösungen verwendet werden.



Siehe Plattformunterstützung und [Voraussetzungen für den erweiterten Connector](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe erfordert die Implementierung und Konfiguration des [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services]. Wird diese ohne zertifizierten Partner oder [!DNL Adobe Professional Services] bereitgestellt oder konfiguriert, wird sie von Adobe nicht unterstützt.
>
>* Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager], die diesen Connector redundant machen. In diesem Fall kann es erforderlich sein, dass Kunden diesen Connector nicht mehr verwenden.
>
>* Adobe unterstützt die Versionen 1.7.4 und höher des erweiterten Connectors. Frühere Vorabversionen und benutzerdefinierte Versionen werden nicht unterstützt. Informationen zum Überprüfen der erweiterten Connector-Version finden Sie in Schritt 5(a) der [Installationsanweisungen für den erweiterten Connector](workfront-connector-install.md).
>
>* Siehe [Partnerzertifizierungsprüfung für den erweiterten Connector von Workfront for Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Informationen zur Prüfung finden Sie im [Prüfungshandbuch](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).


## Vergleichen verschiedener Integrationen zwischen [!DNL Assets] und [!DNL Workfront] {#feature-parity-matrix}

Im Folgenden finden Sie Details zu den Funktionen, die durch verschiedene Integrationstypen zwischen [!DNL Assets] und [!DNL Workfront] verfügbar sind.

| Funktion | Beschreibung | [!DNL Workfront] und [!DNL Assets Essentials] *Kein Connector (OOTB)* | [!DNL Workfront for Experience Manager enhanced connector] *Erfordert Connector* | Workfront und [!DNL Experience Manager as a Cloud Service] *Kein Connector (OOTB)* |
|----|----|----|-----|-----|
| Implementierungsmethoden | Passend für welches [!DNL Assets]-Angebot. | Assets Essentials | Cloud Service, Adobe Managed Services, On-Premise | Cloud Service |
| **Allgemein** |
| Senden digitaler Dateien von [!DNL Workfront] zu [!DNL Assets] | Die neueste Version eines WF-Dokuments kann in AEM Assets hochgeladen werden, wo sie als neue Version des Dokuments verknüpft wird. | ✓ | ✓ | ✓ |
| Manuelles Verknüpfen von AEM-Ordnern mit Workfront-Objekten | Vorhandene AEM-Ordner können als Workfront-Ordner verknüpft werden, wobei die untergeordneten Assets als neue Workfront-Dokumente verknüpft werden. | ✓ | ✓ | ✓ |
| Verknüpfen von [!DNL Assets] mit Workfront-Objekten | Vorhandene Assets in AEM können mit einem neuen Workfront-Dokument oder einer neuen Version eines vorhandenen Dokuments verknüpft werden. | ✓ | ✓ | ✓ |
| Assets, die verknüpften Ordnern hinzugefügt wurden, werden automatisch an AEM gesendet | Wenn ein Dokument zu einem verknüpften Ordner hinzugefügt wird, wird das verknüpfte Asset automatisch als neues Asset in AEM Assets hochgeladen. | ✓ | ✓ | ✓ |
| Herunterladen von verknüpften AEM Assets aus Workfront | Wenn ein Asset in Workfront verknüpft ist, kann der Benutzer die Bytes des Assets herunterladen. | ✓ | ✓ | ✓ |
| Suchen nach AEM Assets in Workfront | Der AEM Assets-Selektor in Workfront ermöglicht die Volltextsuche nach Assets. | ✓ | ✓ | ✓ |
| Suche nach AEM-Ordnern in Workfront | Die AEM Assets-Auswahl in Workfront ermöglicht die Volltextsuche nach Ordnern. | ✓ | ✓ | ✓ |
| Anzeigen von und Navigieren in der AEM-Ordnerhierarchie in Workfront | Die AEM Assets-Auswahl in Workfront ermöglicht das Durchsuchen der AEM Assets-Hierarchie im Rahmen der in AEM festgelegten Zugriffssteuerungen und -berechtigungen der Benutzenden. | ✓ | ✓ | ✓ |
| Nachverfolgen von Asset-Versionen in AEM-Zeitplänen | Behalten Sie den Überblick über den Verlauf der Dokumentversionen zwischen Workfront und AEM. | ✓ | ✓ | ✓ |
| Aufheben der Verknüpfung von Assets mit AEM Assets in Workfront | Ein vorhandenes verknüpftes Asset aus AEM kann vom zugehörigen Workfront-Dokument getrennt werden. Dadurch wird das ursprüngliche Asset in AEM nicht gelöscht. | ✓ | ✓ | ✓ |
| Hinzufügen von neu versionierten Assets zu AEM Assets aus Workfront | Wenn eine neu hinzugefügte Version zu einem Dokument in Workfront hinzugefügt wird, kann ein Benutzer die neue Version an AEM senden, um die vorhandene Version zu ersetzen. | ✓ | ✓ | ✓ |
| In Workfront verknüpfte Assets, wenn auf „Benutzer zu AEM leiten“ geklickt wurde | Benutzer werden zu AEM weitergeleitet, um eine Vorschau eines verknüpften Assets aus Workfront anzuzeigen. | ✓ | ✓ | In Kürze |
| Automatisches Erstellen von verknüpften AEM-Ordnern in Workfront | Erstellen Sie unter Verwendung des Projektstatus automatisch verknüpfte AEM-Ordner in Workfront. Konfigurieren Sie AEM-Ordner automatisch auf der Basis von Workfront-Portfolios, -Programmen und -Projekten. | Nein | ✓ | Nein |
| Direktes Navigieren zu AEM-Repositorys in Workfront | Ermöglichen Sie Benutzenden, zu verfügbaren AEM-Repositorys zu navigieren, die in Workfront konfiguriert sind. | ✓ | Nein | ✓ |
| Verknüpfte AEM in Workfront erstellen | Erstellen Sie manuell verknüpfte AEM Ordner in Workfront mithilfe der Option auf der Registerkarte &quot;Dokumente&quot;. | ✓ | Nein | ✓ |
| Synchronisierung von Kommentaren | Automatische Synchronisierung von Kommentaren für Assets aus [!DNL Workfront] nach [!DNL Assets] | Nein | ✓ | Nein |
| Unterstützung der Verbindung mehrerer Workfront-Umgebungen mit einer einzelnen AEM-Umgebung | Benutzende aus mehreren Workfront-Umgebungen können eine Verbindung mit einer einzigen AEM-Umgebung herstellen. | ✓ | Nein | ✓ |
| Unterstützung der Verbindung mehrerer AEM-Umgebungen mit einer einzelnen Workfront-Umgebung | Benutzende einer einzelnen Workfront-Umgebung können Assets an mehrere AEM-Umgebungen senden oder damit verknüpfen. | ✓ | ✓ | ✓ |
| **Metadaten** |
| Zuordnen von Workfront Asset-Metadaten zu AEM Assets | Eigenschaften von Workfront-Objekten und benutzerdefinierten Formularen können mit Metadateneigenschaften von AEM-Assets verknüpft werden. Die Werte werden beim ersten Hochladen/Verknüpfen übertragen. | ✓ | ✓ | ✓ |
| Automatisches Erstellen von benutzerdefinierten Dokumentenformularen in Workfront | Hängen Sie mithilfe von AEM-Workflows benutzerdefinierte Formulare an Workfront-Dokumente, Aufgaben und Probleme an. | Nein | ✓ | Nein |
| Bidirektionale automatische Aktualisierung von Metadaten zwischen AEM Assets und Workfront | Automatische Aktualisierung von Metadaten zwischen AEM Assets und Workfront. Ein Asset muss zunächst von Workfront an AEM gesendet werden und die Workfront-Asset-Metadaten müssen AEM-Assets zugeordnet werden, damit bidirektionale Aktualisierungen von Metadaten ordnungsgemäß funktionieren. | Nein | ✓ | Nein |
| Echtzeit-Ansicht in Workfront für zugeordnete Metadaten in AEM | Zeigen Sie die aktualisierten AEM zugeordneten Metadaten in den Workfront-Bedienfeldern „Document Details“ und „Document Summary“ an. | ✓ | Nein | ✓ |
| Echtzeit-Push von aktualisierten Workfront-Metadaten an AEM | Aktualisieren Sie die zugeordneten Workfront-Metadaten automatisch in AEM, ohne ein Asset oder eine neue Version eines Assets erneut zu pushen. | ✓ | Nein | ✓ |
| Zuordnen von Workfront-Metadaten zu AEM Assets-Ordnern | Synchronisieren Sie Metadaten von Workfront-Projekten mit verknüpften AEM-Ordnern. | Nein | ✓ | ✓ |
| Aktualisierungen der AEM-Metadaten mit neuen Versionen | Es kann eine Konfiguration in AEM vorgenommen werden, um zu bestimmen, ob ein neu versioniertes Asset in Workfront auch mit allen an den Metadaten vorgenommenen Änderungen gepusht wird. | Nein | ✓ | Nein |
| Automatische Aktualisierung von AEM-Metadaten bei Änderungen an benutzerdefinierten Formularen in Workfront | Sie können in AEM Aktualisierungen an Dokumentformularen in Workfront abonnieren. Infolgedessen werden bei jeder Aktualisierung der benutzerdefinierten Formularmetadaten des Workfront-Dokuments die Werte für die zugeordneten AEM-Metadatenfelder geändert. | Nein | ✓ | Nein |
| **Workflows (vorkonfiguriert)** |
| Erstellen einer neuen Testversion für verknüpfte Assets | Beim Verknüpfen eines Assets in Workfront kann automatisch ein Testversand generiert werden. | Nein | Benutzerdefiniert | Nein |
| Festlegen des Status von Workfront-Objekten | Festlegen des Status von Workfront-Objekten anhand konfigurierbarer Bedingungen mithilfe von AEM-Workflows | Nein | ✓ | In Kürze |
| Veröffentlichen von Assets in der AEM-Veröffentlichungsumgebung oder in Brand Portal | Sie können Workfront-Benutzern die Möglichkeit geben, verknüpfte Assets automatisch in einer AEM-Veröffentlichungsumgebung oder in Brand Portal zu veröffentlichen. | Nein | ✓ | In Kürze |
