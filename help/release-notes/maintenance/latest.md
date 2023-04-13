---
title: Aktuelle Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: fb9b735c44dddda9572d3a1f90d49452c6ddc094
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 13%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Im folgenden Abschnitt finden Sie die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 11382 {#release-11382}

Nachfolgend sind die kontinuierlichen Verbesserungen für die Wartungsversion 11382 zusammengefasst, die am 28. März 2023 veröffentlicht wurde. Dieses Maintenance Release ist eine Aktualisierung von dem vorherigen Maintenance Release 11289.

Mit der Aktivierung der Funktionen für diese Wartungsversion steht Ihnen der volle Funktionsumfang zur Verfügung. Detaillierte Informationen finden Sie in den [aktuellen Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

>[!IMPORTANT]
>
> Auf der Benutzeroberfläche von Cloud Manager kann eine Diskrepanz festgestellt werden, die &quot;2023.3.11382&quot;anzeigt, während die offizielle Version &quot;2023.02&quot;lautet. Dies ist auf die verzögerte Aktivierung der Funktionen von 2023.02 zurückzuführen.
> Wir arbeiten daran, dies für bevorstehende Versionen zu beheben.

### Bekannte Probleme {#known-issues-11382}

- SITES-12573 - GraphQL-Abfragen, die Variablen innerhalb eines Filters verwenden, schlagen fehl, wenn keine Variable angegeben ist. Bitte aktualisieren Sie nicht auf diese Version, sollten Sie GraphQL mit AEM as a Cloud Service verwenden.
- SKYOPS-51970 - Identifizierte Regression der im Schritt &quot;buildImage&quot;verwendeten FACT-Version, die zu einer nicht übereinstimmenden Benutzerzuordnung führte.
- GRANITE-44542 - Es wurden Probleme für Kunden gemeldet, die keinen Paketnotentyp (durch Bereitstellung einer .content.xml mit jcr:primaryType) für Ordner im Paketfilter angegeben haben. Dies führte dazu, dass diese Ordner als nt:folder behandelt wurden, was in verschiedenen Fällen zu Problemen führte.

### Behobene Probleme {#fixed-issues-11382}

- ASSETS-21023 - Ausgabedarstellung für smartes Zuschneiden wurde behoben, bei der Kunden in der Publisher-Instanz aller AEM Umgebungen eine Nullzeiger-Ausnahme bemerken konnten, wenn versucht wurde, über die API auf diese Ausgabedarstellungen zuzugreifen.
- SKYOPS-49280 - Bei der Installation einer Konfiguration oder eines Bundle-Updates mit RDE in Publish kann das Ergebnis möglicherweise nicht beobachtet werden, da der Cache des Publish-Dispatchers nicht ungültig gemacht wird

#### Sites {#sites-issues-11382}

- SITES-7796 - Möglichkeit für Inhaltsautoren, das Übergeordnete Inhaltsfragment und die entsprechenden Varianten beim Export in Target zu veröffentlichen
- SITES-97 - GraphQL: Paginierung und Sortierung, Hybridfilterung

>[!NOTE]
>
> In SITES-97 wurden einige Verbesserungen an der GraphQL-Implementierung vorgenommen, die zu unerwartetem Verhalten führen können. Siehe [AEM Änderungen in GraphQL bezüglich der Verarbeitung von Nullwerten](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-21792.html?lang=de) für weitere Informationen.

#### Assets {#assets-issues-11382}

- ASSETS-20076 - Unterstützung für Video-Wasserzeichen hinzugefügt, die mit der aktuellen Unterstützung für Bild-Wasserzeichen übereinstimmen
- ASSETS-21428 - Hinzufügung von Ausschlüssen für CSS-Änderungen

#### Formulare {#forms-issues-11382}

- CQ-4351502 - Aktualisieren der Service-Benutzerzuordnung, um Lesezugriff in Sites zu ermöglichen

#### Platform {#platform-issues-11382}

- SITES-11040 - Bedingte Aktivierung der beibehaltenen Abfrage-Zwischenspeicherung in GraphQL im Dispatcher

### Eingebettete Technologien {#embedded-tech-11382}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [Oak API 1.44.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING-API | Version: 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Sprachspezifikation für HTML-Vorlagen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.21.2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
