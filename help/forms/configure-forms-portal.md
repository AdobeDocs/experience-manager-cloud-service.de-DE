---
title: Erstellen eines Forms-Portals auf einer Experience Manager Sites-Seite
description: Erfahren Sie, wie Sie ein Forms-Portal erstellen und vordefinierte Kernkomponenten auf einer AEM Sites-Seite verwenden.
exl-id: 13cfe3ba-2e85-46bf-a029-2673de69c626
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1784'
ht-degree: 26%

---

# Auflisten des adaptiven Forms in einem Portal {#publish-forms-on-portal}

In einer typischen formularzentrierten Bereitstellung sind die Entwicklung von Formularen und die Entwicklung von Portalen zwei getrennte Aktivitäten. Während Formularentwickler Formulare in einem Repository erstellen und speichern, erstellen Webentwickler eine Webanwendung, um Formulare aufzulisten und gesendete Formulare zu verarbeiten. Formulare werden in die Webstufe kopiert, da keine Kommunikation zwischen dem Formular-Repository und der Webanwendung besteht.

Solche Fälle führen oft zu Verwaltungsproblemen und Produktionsverzögerungen. Wenn beispielsweise eine neuere Version eines Formulars im Repository verfügbar ist, müssen Sie das Formular auf der Webstufe ersetzen, die Webanwendung ändern und das Formular erneut auf der öffentlichen Site bereitstellen. Die erneute Bereitstellung der Webanwendung verursacht möglicherweise einen Serverausfall. Normalerweise ist der Serverausfall eine geplante Aktivität. Daher können die Änderungen nicht sofort an die öffentliche Site gesendet werden.

AEM Forms bietet Portalkomponenten, die den Verwaltungsaufwand und Produktionsverzögerungen reduzieren. Die Komponenten ermöglichen es Webentwicklern, ein Forms-Portal auf mit Adobe Experience Manager (AEM) erstellten Websites zu erstellen und anzupassen.

Mit den Formularportalkomponenten können Sie die folgenden Funktionen hinzufügen:

* Auflisten von Formularen in benutzerdefinierten Layouts. Standardmäßig werden die Layouts für die Listenansicht und die Kartenansicht bereitgestellt. Sie können auch eigene benutzerdefinierte Layouts erstellen.
* Ermöglicht die Anzeige benutzerdefinierter Metadaten und benutzerdefinierter Aktionen bei deren Auflistung.
* Auflisten von Formularen, die von der AEM Forms-Benutzeroberfläche auf der Veröffentlichungsinstanz veröffentlicht wurden, in der Forms Portal-Komponenten verwendet werden.
* Endbenutzern die Wiedergabe von Formularen im HTML- und PDF-Format zu ermöglichen.
* Aktivieren Sie die Suche nach Formularen anhand von Titel und Beschreibung.
* Verwenden von benutzerdefiniertem CSS, um das Erscheinungsbild des Portals anzupassen.
* Erstellen von Links zu Formularen.
* Listet Entwürfe und Übermittlungen im Zusammenhang mit dem vom Endbenutzer erstellten adaptiven Forms auf.

## Komponenten einer Forms Portal-Seite {#forms-portal-components}

AEM Forms bietet standardmäßig die folgenden Portalkomponenten:

* Search &amp; Lister: Mit dieser Komponente können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten und Konfigurationsoptionen bereitstellen, um Formulare basierend auf angegebenen Kriterien aufzulisten.

* Entwürfe und Übermittlungen: Während die Komponente &quot;Search &amp; Lister&quot;Formulare anzeigt, die vom Forms-Autor veröffentlicht wurden, zeigt die Komponente &quot;Drafts &amp; Submissions&quot;Formulare an, die als Entwurf zum Abschließen späterer Formulare und gesendeter Formulare gespeichert wurden. Diese Komponente bietet jedem angemeldeten Benutzer eine personalisierte Nutzung.

* Link: Mit dieser Komponente können Sie einen Link zu einem Formular an einer beliebigen Stelle auf der Seite erstellen.

Sie können [Importieren der nativen Forms Portal-Komponenten](#import-forms-portal-components-aem-archetype) aus dem AEM Projektarchetyp. Führen Sie nach dem Import die folgenden Konfigurationen durch:
* [Externen Speicher konfigurieren](#configure-azure-storage-adaptive-forms)
* [Aktivieren der Forms Portal-Komponenten](#enable-forms-portal-components)
* [Konfigurieren der Forms Portal-Komponenten](#configure-forms-portal-components)

## Importieren von Forms Portal-Komponenten {#import-forms-portal-components-aem-archetype}

So importieren Sie vordefinierte Forms Portal-Komponenten in AEM Forms as a Cloud Service:

1. **Klonen Sie das Cloud Manager-Git-Repository in Ihrer lokalen Entwicklungsinstanz:** Ihr Cloud Manager-Git-Repository enthält ein AEM-Standardprojekt. Es basiert auf [AEM Archetype](https://github.com/adobe/aem-project-archetype/). Klonen Sie Ihr Cloud Manager-Git-Repository mithilfe der Self-Service-Git-Kontoverwaltung der Cloud Manager-Benutzeroberfläche, um das Projekt in Ihre lokale Entwicklungsumgebung zu bringen. Weitere Informationen zum Zugriff auf das Repository finden Sie unter [Zugreifen auf Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html?lang=de).

1. **Erstellen [!DNL Experience Manager Forms] as a [Cloud Service] Projekt:** Erstellen [!DNL Experience Manager Forms] as a [Cloud Service] Projekt basierend auf [AEM Archetyp 27](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) oder höher. Der Archetyp unterstützt Entwickler beim einfachen Einstieg in die Entwicklung für [!DNL AEM Forms] as a Cloud Service. Er enthält auch einige Beispiel-Designs und Vorlagen, die Ihnen bei den ersten Schritten helfen.

   Erstellen [!DNL Experience Manager Forms] as a Cloud Service Projekt, öffnen Sie die Eingabeaufforderung und führen Sie den folgenden Befehl aus. Um [!DNL Forms]-spezifische Konfigurationen, Designs und Vorlagen einzuschließen, stellen Sie `includeForms=y` ein.

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=30 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   Ändern Sie im obigen Befehl außerdem `appTitle`, `appId` und `groupId`, sodass die Werte Ihrer Umgebung entsprechen.

1. **Führen Sie in der Vorabversion die folgenden Schritte aus, um die Forms Portal-Komponenten zu verwenden:**
   * [Vorabversionskanal aktivieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en).
   * Ersetzen `core-forms-components-*` Version mit der gewünschten Vorabversion (z. B. 1.0.4-PRERELEASE-2021223) in Ihrer `Cloud Manager/AEM Archetype` Projekt durch Aktualisierung `<core.forms.components.version>x.y.z</core.forms.components.version>` -Eigenschaft in der obersten Ebene `pom.xml` des Archetypprojekts.

1. **Stellen Sie das Projekt in Ihrer lokalen Entwicklungsumgebung bereit:** Sie können den folgenden Befehl verwenden, um eine Bereitstellung in Ihrer lokalen Entwicklungsumgebung durchzuführen

   `mvn -PautoInstallPackage clean install`

   Die vollständige Liste der Befehle finden Sie unter [Erstellen und Installieren](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=de#building-and-installing)

1. [Stellen Sie den Code in Ihrer  [!DNL AEM Forms]  as a Cloud Service-Umgebung bereit](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#embeddeds).


## Konfigurieren von Azure Storage für adaptive Forms {#configure-azure-storage-adaptive-forms}

[[!DNL Experience Manager Forms] Datenintegration](data-integration.md) stellt [!DNL Azure] Speicherkonfiguration für die Integration von Formularen mit [!DNL Azure] Speicherdienste. Das Formulardatenmodell kann verwendet werden, um adaptive Formulare zu erstellen, die mit [!DNL Azure]Server interagieren, um Unternehmens-Workflows zu ermöglichen.

### AzureStorage-Konfiguration erstellen {#create-azure-storage-configuration}

Bevor Sie diese Schritte ausführen, stellen Sie sicher, dass Sie über ein Azure-Speicherkonto und einen Zugriffsschlüssel verfügen, um den Zugriff auf die [!DNL Azure] Speicherkonto.

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure-Speicher]**.
1. Wählen Sie einen Ordner aus, um die Konfiguration zu erstellen, und tippen Sie auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Feld **[!UICONTROL Titel]** einen Titel für die Konfiguration an.
1. Geben Sie den Namen des [!DNL Azure]-Speicherkontos im Feld **[!UICONTROL Azure-Speicherkonto]** an.

### Unified Storage Connector für Forms Portal konfigurieren {#configure-usc-forms-portal}

Führen Sie die folgenden Schritte aus, um Unified Storage Connector für AEM-Workflows zu konfigurieren:

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]**.
1. Im **[!UICONTROL Forms Portal]** Bereich, wählen Sie **[!UICONTROL Azure]** von **[!UICONTROL Speicherung]** Dropdown-Liste.
1. Geben Sie den [Konfigurationspfad für die Azure-Speicherkonfiguration](#create-azure-storage-configuration) im Feld **[!UICONTROL Pfad für Speicherkonfiguration]** an.
1. Tippen Sie auf **[!UICONTROL Veröffentlichen]** und dann auf **[!UICONTROL Speichern]** , um die Konfiguration zu speichern.

## Aktivieren von Forms Portal-Komponenten {#enable-forms-portal-components}

Um eine beliebige Kernkomponente (einschließlich der vordefinierten Portalkomponenten) auf einer Adobe Experience Manager-Site (AEM) zu verwenden, müssen Sie eine Proxy-Komponente erstellen und für Ihre Site aktivieren. Informationen zum Erstellen einer Proxy-Komponente und Aktivieren von Portal-Komponenten finden Sie unter [Verwenden von Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=en#create-proxy-components).

Sobald eine Portalkomponente aktiviert ist, können Sie sie in der Autoreninstanz Ihrer Sites-Seite verwenden.

## Hinzufügen und Konfigurieren von Forms Portal-Komponenten {#configure-forms-portal-components}

Sie können Forms Portal auf mit AEM erstellten Websites erstellen und anpassen, indem Sie die Portalkomponenten hinzufügen und konfigurieren. Stellen Sie sicher, dass [Komponenten sind aktiviert](#enable-forms-portal-components) bevor Sie sie im Forms-Portal verwenden.

Um eine Komponente hinzuzufügen, ziehen Sie die Komponente entweder aus dem Bereich &quot;Komponenten&quot;in den Layout-Container auf der Seite oder tippen Sie auf das Symbol zum Hinzufügen im Layout-Container und fügen Sie die Komponente aus dem [!UICONTROL Neue Komponente einfügen] angezeigt.

### Komponente &quot;Drafts and Submissions&quot;konfigurieren {#configure-drafts-submissions-component}

Die Komponente &quot;Drafts &amp; Submissions&quot;zeigt Formulare an, die als Entwurf zum Ausfüllen späterer und gesendeter Formulare gespeichert wurden. Tippen Sie zum Konfigurieren auf die Komponente und tippen Sie dann auf ![Symbol &quot;Konfigurieren&quot;](assets/configure_icon.png). Im [!UICONTROL Entwürfe und Übermittlungen] Geben Sie den Titel an, um die Formularliste als Entwurf oder übermittelte Formulare anzugeben. Wählen Sie außerdem aus, ob die Komponente Entwürfe von Formularen oder übermittelte Formulare im Karten- oder Listenformat auflisten soll.

![Symbol &quot;Entwürfe&quot;](assets/drafts-component.png)

![Symbol &quot;Sendungen&quot;](assets/submission-listing.png)

### Konfigurieren der Komponente &quot;Search &amp; Lister&quot; {#configure-search-lister-component}

Die Komponente &quot;Search &amp; Lister&quot;wird verwendet, um adaptive Formulare auf einer Seite aufzulisten und die Suche in den aufgeführten Formularen zu implementieren.

![Symbol &quot;Search &amp; Lister&quot;](assets/search-and-lister-component.png)

Tippen Sie zum Konfigurieren auf die Komponente und tippen Sie dann auf ![Symbol &quot;Konfigurieren&quot;](assets/configure_icon.png). Die [!UICONTROL Search &amp; Lister] wird geöffnet.

1. Im [!UICONTROL Anzeige] konfigurieren Sie Folgendes:
   * In **[!UICONTROL Titel]**, geben Sie den Titel für die Komponente &quot;Search &amp; Lister&quot;an. Ein ungefährer Titel ermöglicht es den Benutzern, die Liste der Formulare schnell zu durchsuchen.
   * Aus dem **[!UICONTROL Layout]** wählen Sie das Layout für die Formulare im Karten- oder Listenformat aus.
   * Auswählen **[!UICONTROL Suche ausblenden]** und **[!UICONTROL Sortierung ausblenden]** um die Suche auszublenden und nach Funktionen zu sortieren.
   * In **[!UICONTROL QuickInfo]** Geben Sie die QuickInfo ein, die angezeigt wird, wenn Sie den Mauszeiger über die Komponente bewegen.
1. Im [!UICONTROL Asset-Ordner] auf, geben Sie den Speicherort an, von dem aus die Formulare abgerufen und auf der Seite aufgeführt werden. Sie können mehrere Ordnerspeicherorte konfigurieren.
1. Im [!UICONTROL Ergebnisse] festlegen, konfigurieren Sie die maximale Anzahl von Formularen, die pro Seite angezeigt werden sollen. Der Standardwert beträgt acht Formulare pro Seite.

### Link-Komponente konfigurieren {#configure-link-component}

Mit der Komponente &quot;Link&quot;können Sie Links zu einem adaptiven Formular auf der Seite bereitstellen. Tippen Sie zum Konfigurieren auf die Komponente und tippen Sie dann auf ![Symbol &quot;Konfigurieren&quot;](assets/configure_icon.png). Die [!UICONTROL Komponente &quot;Link bearbeiten&quot;] wird geöffnet.

1. Im [!UICONTROL Anzeige] Geben Sie die Beschriftung der Relation und die QuickInfo ein, um die Identifizierung der durch die Relation dargestellten Formulare zu erleichtern.
1. Im [!UICONTROL Asset-Informationen] -Registerkarte den Repository-Pfad angeben, in dem das Asset gespeichert ist.
1. Im [!UICONTROL Abfrageparameter] -Tab die zusätzlichen Parameter im Schlüssel-Wert-Paarformat angeben. Wenn der Link angeklickt wird, werden diese zusätzlichen Parameter zusammen mit dem Formular übergeben.

## Konfigurieren der asynchronen Formularübermittlung mit Adobe Sign {#configure-asynchronous-form-submission-using-adobe-sign}

Sie können konfigurieren, dass ein adaptives Formular nur gesendet wird, wenn alle Empfänger die Unterzeichnungszeremonie abgeschlossen haben. Gehen Sie wie folgt vor, um die Einstellung mit Adobe Sign zu konfigurieren.

1. Öffnen Sie in der Autoreninstanz ein adaptives Formular im Bearbeitungsmodus.
1. Tippen Sie im linken Bereich auf das Symbol Eigenschaften und erweitern Sie die **[!UICONTROL ELEKTRONISCHE UNTERSCHRIFT]** -Option.
1. Auswählen **[!UICONTROL Adobe Sign aktivieren]**. Es werden verschiedene Konfigurationsoptionen angezeigt.
1. Im [!UICONTROL Senden des Formulars] auswählen, wählen Sie die **[!UICONTROL nach Abschluss der Unterzeichnungszeremonie durch jeden Empfänger]** -Option, um die Aktion &quot;Formular senden&quot;zu konfigurieren, bei der das Formular zuerst zur Unterzeichnung an alle Empfänger gesendet wird. Nachdem alle Empfänger das Formular signiert haben, wird das Formular nur noch gesendet.

## Adaptive Forms als Entwürfe speichern {#save-adaptive-forms-as-drafts}

Sie können Formulare als Entwürfe speichern, um sie später abzuschließen. Es gibt zwei Möglichkeiten, ein Formular als Entwurf zu speichern:
* Erstellen Sie eine Regel &quot;Formular speichern&quot;für eine Formularkomponente, z. B. eine Schaltfläche. Beim Klicken auf die Schaltfläche werden die Trigger der Regel und das Formular als Entwurf gespeichert.
* Aktivieren Sie die Funktion Automatisches Speichern , mit der das Formular gemäß dem angegebenen Ereignis oder nach einem konfigurierten Zeitintervall gespeichert wird.

### Erstellen von Regeln zum Speichern eines adaptiven Formulars als Entwurf {#rule-to-save-adaptive-form-as-draft}

Gehen Sie wie folgt vor, um eine Regel &quot;Formular speichern&quot;für eine Formularkomponente zu erstellen, z. B. eine Schaltfläche:

1. Öffnen Sie in der Autoreninstanz ein adaptives Formular im Bearbeitungsmodus.
1. Tippen Sie im linken Bereich auf ![Symbol &quot;Komponenten&quot;](assets/components_icon.png) und ziehen Sie die [!UICONTROL Schaltfläche] -Komponente in das Formular ein.
1. Tippen Sie auf [!UICONTROL Schaltfläche] und tippen Sie dann auf ![Symbol &quot;Konfigurieren&quot;](assets/configure_icon.png).
1. Tippen Sie auf [!UICONTROL Regeln bearbeiten] -Symbol, um den Regeleditor zu öffnen.
1. Tippen **[!UICONTROL Erstellen]** , um die Regel zu konfigurieren und zu erstellen.
1. Im [!UICONTROL Wann] Wählen Sie &quot;wird angeklickt&quot;und im [!UICONTROL Dann] Wählen Sie die Optionen &quot;Formular speichern&quot;.
1. Tippen Sie auf **[!UICONTROL Fertig]**, um die Regel zu speichern.

### Automatisches Speichern aktivieren {#enable-auto-save}

Sie können die Funktion zum automatischen Speichern für ein adaptives Formular wie folgt konfigurieren:

1. Öffnen Sie in der Autoreninstanz ein adaptives Formular im Bearbeitungsmodus.
1. Tippen Sie im linken Bereich auf das ![Symbol Eigenschaften](assets/configure_icon.png) und erweitern Sie die [!UICONTROL AUTOMATISCHES SPEICHERN] -Option.
1. Wählen Sie die **[!UICONTROL Aktivieren]** aktivieren, um das automatische Speichern des Formulars zu aktivieren. Sie können Folgendes konfigurieren:
* Standardmäßig wird die [!UICONTROL Adaptives Formularereignis] auf &quot;true&quot;gesetzt ist, was bedeutet, dass das Formular nach jedem Ereignis automatisch gespeichert wird.
* In [!UICONTROL Trigger], konfigurieren Sie , um die automatische Speicherung auf der Grundlage des Vorkommens eines Triggers oder nach einem bestimmten Zeitintervall durchzuführen.
