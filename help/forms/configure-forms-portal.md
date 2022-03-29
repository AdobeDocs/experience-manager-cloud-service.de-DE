---
title: Erstellen eines Formularportals auf einer Experience Manager Sites-Seite
description: Erfahren Sie, wie Sie ein Formularportal erstellen und vordefinierte Kernkomponenten auf einer Seite von AEM Sites verwenden können.
exl-id: 13cfe3ba-2e85-46bf-a029-2673de69c626
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1784'
ht-degree: 100%

---

# Auflisten der adaptiven Formulare in einem Portal {#publish-forms-on-portal}

In einer typischen formularzentrierten Bereitstellung sind die Entwicklung von Formularen und die Entwicklung von Portalen zwei getrennte Aktivitäten. Während Formularentwickler Formulare in einem Repository erstellen und speichern, erstellen Webentwickler eine Webanwendung, um Formulare aufzulisten und gesendete Formulare zu verarbeiten. Formulare werden in die Webstufe kopiert, da keine Kommunikation zwischen dem Formular-Repository und der Webanwendung besteht.

Solche Fälle führen oft zu Verwaltungsproblemen und Produktionsverzögerungen. Wenn beispielsweise eine neuere Version eines Formulars im Repository verfügbar ist, müssen Sie das Formular auf der Webstufe ersetzen, die Webanwendung ändern und das Formular erneut auf der öffentlichen Site bereitstellen. Die erneute Bereitstellung der Webanwendung verursacht möglicherweise einen Serverausfall. Normalerweise ist der Serverausfall eine geplante Aktivität. Daher können die Änderungen nicht sofort an die öffentliche Site gesendet werden.

AEM Forms bietet Portalkomponenten, die den Verwaltungsaufwand und Produktionsverzögerungen reduzieren. Mit den Komponenten können Web-Entwickler Formularportale auf mit Adobe Experience Manager (AEM) erstellten Websites erstellen und anpassen. 

Die Formularportalkomponenten ermöglichen es Ihnen, die folgende Funktion hinzuzufügen:

* Auflisten von Formularen in benutzerdefinierten Layouts. Standardmäßig werden Layouts für Listenansicht und Kartenansicht bereitgestellt. Sie können auch eigene benutzerdefinierte Layouts erstellen.
* Sie können benutzerdefinierte Metadaten sowie benutzerdefinierte Aktionen beim Auflisten anzeigen.
* Auflisten von Formularen, die von der AEM Forms-Benutzeroberfläche auf der Veröffentlichungsinstanz veröffentlicht wurden, in der Formularportal-Komponenten verwendet werden.
* Endbenutzern ermöglichen, Formulare im HTML- und PDF-Format anzuzeigen.
* Aktivieren der Suche nach Formularen anhand von Titel und Beschreibung.
* Verwenden von benutzerdefiniertem CSS, um das Erscheinungsbild des Portals anzupassen.
* Erstellen von Links zu Formularen.
* Auflisten von Entwürfen und Übermittlungen in Bezug auf adaptive Formulare auf, die vom Endbenutzer erstellt wurden.

## Komponenten einer Formularportal-Seite {#forms-portal-components}

AEM Forms bietet standardmäßig die folgenden Portalkomponenten:

* Search &amp; Lister: Mit der Komponente „Search &amp; Lister“ können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten. Außerdem enthält sie Konfigurationsoptionen, um Formulare basierend auf angegebenen Kriterien aufzulisten.

* Drafts &amp; Submissions: Während die Komponente „Search &amp; Lister“ Formulare anzeigt, die vom Formularautor veröffentlicht wurden, zeigt die Komponente „Drafts &amp; Submissions“ Formulare, die für den späteren Abschluss als Entwurf gespeichert wurden, sowie gesendete Formulare an. Diese Komponente bietet jedem angemeldeten Benutzer eine personalisierte Nutzung.

* Link: Mithilfe dieser Komponente können Sie einen Link zu einem Formular an jeder beliebigen Stelle auf der Seite erstellen.

Sie können [die gebrauchsfertigen Formularportal-Komponenten aus dem AEM-Projektarchetyp importieren](#import-forms-portal-components-aem-archetype). Führen Sie nach dem Import die folgenden Konfigurationen durch:
* [Konfigurieren eines externen Speichers](#configure-azure-storage-adaptive-forms)
* [Aktivieren der Formularportal-Komponenten](#enable-forms-portal-components)
* [Konfigurieren der Formularportal-Komponenten](#configure-forms-portal-components)

## Importieren von Formularportal-Komponenten {#import-forms-portal-components-aem-archetype}

So importieren Sie vordefinierte Formularportal-Komponenten in AEM Forms as a Cloud Service:

1. **Klonen Sie das Cloud Manager-Git-Repository in Ihrer lokalen Entwicklungsinstanz:** Ihr Cloud Manager-Git-Repository enthält ein AEM-Standardprojekt. Es basiert auf [AEM Archetype](https://github.com/adobe/aem-project-archetype/). Klonen Sie Ihr Cloud Manager-Git-Repository mithilfe der Self-Service-Git-Kontoverwaltung der Cloud Manager-Benutzeroberfläche, um das Projekt in Ihre lokale Entwicklungsumgebung zu bringen. Weitere Informationen zum Zugriff auf das Repository finden Sie unter [Zugriff auf Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html?lang=de).

1. **Erstellen von [!DNL Experience Manager Forms] als [Cloud Service]-Projekt**: Erstellen Sie [!DNL Experience Manager Forms] als ein [Cloud Service]-Projekt basierend auf [AEM Archetyp 27](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) oder höher. Der Archetyp unterstützt Entwickler beim einfachen Einstieg in die Entwicklung für [!DNL AEM Forms] as a Cloud Service. Darin sind auch einige Beispiel-Designs und Vorlagen enthalten, die Ihnen bei den ersten Schritten helfen.

   Um ein Projekt für [!DNL Experience Manager Forms] as a Cloud Service zu erstellen, öffnen Sie die Eingabeaufforderung und führen Sie den folgenden Befehl aus. Um [!DNL Forms]-spezifische Konfigurationen, Designs und Vorlagen einzuschließen, stellen Sie `includeForms=y` ein.

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=30 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   Ändern Sie im obigen Befehl außerdem `appTitle`, `appId` und `groupId`, sodass die Werte Ihrer Umgebung entsprechen.

1. **Führen Sie in der Vorabversion die folgenden Schritte aus, um die Komponenten des Formularportals zu verwenden:**
   * [Aktivieren Sie den Kanal der Vorabversion](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de).
   * Ersetzen Sie die Version `core-forms-components-*` mit der gewünschten Vorabversion (z. B. 1.0.4-PRERELEASE-20211223) in Ihrem `Cloud Manager/AEM Archetype`-Projekt, indem Sie die `<core.forms.components.version>x.y.z</core.forms.components.version>`-Eigenschaft in der obersten Ebene von `pom.xml` des Archetypprojekts aktualisieren.

1. **Stellen Sie das Projekt in Ihrer lokalen Entwicklungsumgebung bereit:** Sie können den folgenden Befehl verwenden, um eine Bereitstellung in Ihrer lokalen Entwicklungsumgebung durchzuführen

   `mvn -PautoInstallPackage clean install`

   Die vollständige Liste der Befehle finden Sie unter [Erstellen und Installieren](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=de#building-and-installing)

1. [Stellen Sie den Code in Ihrer [!DNL AEM Forms] as a Cloud Service-Umgebung bereit](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de#embeddeds).


## Konfigurieren von Azure Storage für adaptive Formulare {#configure-azure-storage-adaptive-forms}

[[!DNL Experience Manager Forms] Datenintegration](data-integration.md) bietet eine [!DNL Azure]-Speicherkonfiguration, um Formulare in [!DNL Azure]-Speicher-Services zu integrieren. Das Formulardatenmodell kann verwendet werden, um adaptive Formulare zu erstellen, die mit [!DNL Azure]-Server interagieren, um Unternehmens-Workflows zu ermöglichen.

### Erstellen der Azure-Speicherkonfiguration {#create-azure-storage-configuration}

Stellen Sie vor dem Ausführen dieser Schritte sicher, dass Sie über ein Azure-Speicherkonto und einen Zugriffsschlüssel verfügen, um den Zugriff auf das [!DNL Azure]-Speicherkonto zu autorisieren.

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure-Speicher]**.
1. Wählen Sie einen Ordner aus, um die Konfiguration zu erstellen, und tippen Sie auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Feld **[!UICONTROL Titel]** einen Titel für die Konfiguration an.
1. Geben Sie den Namen des [!DNL Azure]-Speicherkontos im Feld **[!UICONTROL Azure-Speicherkonto]** an.

### Konfigurieren von Unified Storage Connector für das Formularportal {#configure-usc-forms-portal}

Führen Sie die folgenden Schritte aus, um Unified Storage Connector für AEM-Workflows zu konfigurieren:

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]**.
1. Wählen Sie im Abschnitt **[!UICONTROL Formularportal]** den Eintrag **[!UICONTROL Azure]** aus der Dropdown-Liste **[!UICONTROL Speicher]** aus.
1. Geben Sie den [Konfigurationspfad für die Azure-Speicherkonfiguration](#create-azure-storage-configuration) im Feld **[!UICONTROL Pfad für Speicherkonfiguration]** an.
1. Tippen Sie auf **[!UICONTROL Veröffentlichen]** und dann auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

## Aktivieren von Komponenten des Formularportals {#enable-forms-portal-components}

Um eine beliebige Kernkomponente (einschließlich der vordefinierten Portalkomponenten) auf einer Adobe Experience Manager-Site (AEM) zu verwenden, müssen Sie eine Proxy-Komponente erstellen und für Ihre Site aktivieren. Informationen zum Erstellen einer Proxy-Komponente und Aktivieren von Portalkomponenten finden Sie unter [Verwenden von Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=de#create-proxy-components).

Sobald eine Portalkomponente aktiviert ist, können Sie sie in der Autoreninstanz Ihrer Sites-Seite verwenden.

## Hinzufügen und Konfigurieren von Komponenten des Formularportals {#configure-forms-portal-components}

Sie können das Formularportal auf mit AEM erstellten Websites erstellen und anpassen, indem Sie die Portalkomponenten hinzufügen und konfigurieren. Stellen Sie sicher, dass [Komponenten aktiviert sind](#enable-forms-portal-components), bevor Sie sie im Formularportal verwenden.

Um eine Komponente hinzuzufügen, ziehen Sie die Komponente entweder aus dem Bereich „Komponenten“ in den Layout-Container auf der Seite oder tippen Sie auf das Symbol zum Hinzufügen im Layout-Container und fügen Sie die Komponente über das Dialogfeld [!UICONTROL Neue Komponente einfügen] hinzu.

### Konfigurieren der Komponente für Entwürfe und Einsendungen {#configure-drafts-submissions-component}

Die Komponente für Entwürfe und Einsendungen zeigt Formulare an, die als Entwurf zum späteren Ausfüllen und für gesendete Formulare gespeichert wurden. Tippen Sie zum Konfigurieren auf die Komponente und tippen Sie dann auf das ![Symbol „Konfigurieren“](assets/configure_icon.png). Geben Sie im Dialogfeld [!UICONTROL Entwürfe und Einsendungen] den Titel an, um die Formularliste als Entwurf oder übermittelte Formulare anzugeben. Wählen Sie außerdem aus, ob die Komponente Entwürfe von Formularen oder übermittelte Formulare im Karten- oder Listenformat auflisten soll.

![Symbol für Entwürfe](assets/drafts-component.png)

![Symbol für Einsendungen](assets/submission-listing.png)

### Konfigurieren der Komponente für Suche und Auflister {#configure-search-lister-component}

Die Komponente für Suche und Auflister wird verwendet, um adaptive Formulare auf einer Seite aufzulisten und die Suche in den aufgelisteten Formularen zu implementieren.

![Symbol für Suche und Auflister](assets/search-and-lister-component.png)

Tippen Sie zum Konfigurieren auf die Komponente und tippen Sie dann auf das ![Symbol „Konfigurieren“](assets/configure_icon.png). Das Dialogfeld [!UICONTROL Suche und Auflister] wird geöffnet.

1. Konfigurieren Sie auf der Registerkarte [!UICONTROL Anzeige] Folgendes:
   * In **[!UICONTROL Titel]** geben Sie den Titel für die Komponente für Suche und Auflister an. Ein aussagekräftiger Titel ermöglicht es den Benutzern, die Liste der Formulare schnell zu durchsuchen.
   * Unter **[!UICONTROL Layout]** wählen Sie das Layout, um die Formulare im Karten- oder Listenformat darzustellen.
   * Wählen Sie **[!UICONTROL Suche ausblenden]** und **[!UICONTROL Sortierung ausblenden]**, um die Suche und Sortierung nach Funktionen auszublenden.
   * Geben Sie unter **[!UICONTROL QuickInfo]** die QuickInfo ein, die angezeigt wird, wenn Sie den Mauszeiger über die Komponente bewegen.
1. Geben Sie auf der Registerkarte [!UICONTROL Asset-Ordner] den Speicherort an, von dem die Formulare abgerufen und auf der Seite aufgeführt werden. Sie können mehrere Speicherorte für Ordner konfigurieren.
1. Konfigurieren Sie auf der Registerkarte [!UICONTROL Ergebnisse] die maximale Anzahl von Formularen, die pro Seite angezeigt werden sollen. Der Standardwert ist acht Formulare pro Seite.

### Konfigurieren der Link-Komponente {#configure-link-component}

Mit der Link-Komponente können Sie Links zu einem adaptiven Formular auf der Seite bereitstellen. Tippen Sie zum Konfigurieren auf die Komponente und tippen Sie dann auf ![Symbol konfigurieren](assets/configure_icon.png). Der Dialog [!UICONTROL Link-Komponente bearbeiten] wird geöffnet.

1. Geben Sie auf der Registerkarte [!UICONTROL Anzeige] die Link-Beschriftung und die QuickInfo ein, um die Identifizierung der durch diesen Link dargestellten Formulare zu erleichtern.
1. Geben Sie auf der Registerkarte [!UICONTROL Asset-Informationen] den Repository-Pfad an, unter dem das Asset gespeichert ist.
1. Geben Sie auf der Registerkarte [!UICONTROL Abfrageparameter] die zusätzlichen Parameter im Schlüssel-Wert-Paarformat an. Wenn auf den Link geklickt wird, werden diese zusätzlichen Parameter zusammen mit dem Formular übergeben.

## Konfigurieren der asynchronen Formularübermittlung mit Adobe Sign {#configure-asynchronous-form-submission-using-adobe-sign}

Sie können konfigurieren, dass ein adaptives Formular nur gesendet wird, wenn alle Empfänger das Unterschriftsverfahren abgeschlossen haben. Gehen Sie wie folgt vor, um die Einstellung mit Adobe Sign zu konfigurieren.

1. Öffnen Sie in der Autoreninstanz ein adaptives Formular im Bearbeitungsmodus.
1. Tippen Sie im linken Bereich auf das Symbol „Eigenschaften“ und erweitern Sie die Option **[!UICONTROL ELEKTRONISCHE UNTERSCHRIFT]**.
1. Wählen Sie **[!UICONTROL Adobe Sign aktivieren]** aus. Es werden verschiedene Konfigurationsoptionen angezeigt.
1. Wählen Sie im Abschnitt [!UICONTROL Formular senden] die Option **[!UICONTROL nach Abschluss der Signaturzeremonie durch jeden Empfänger]** aus, um die Aktion „Formular senden“ zu konfigurieren, bei der das Formular erst zur Unterschrift an alle Empfänger gesendet wird. Erst nachdem alle Empfänger das Formular signiert haben, wird das Formular gesendet.

## Speichern von adaptiven Formularen als Entwürfe {#save-adaptive-forms-as-drafts}

Sie können Formulare als Entwürfe speichern, um sie später abzuschließen. Es gibt zwei Möglichkeiten, ein Formular als Entwurf zu speichern:
* Erstellen Sie eine Regel „Formular speichern“ für eine Formularkomponente, beispielsweise eine Schaltfläche. Beim Klicken auf die Schaltfläche wird die Regel ausgelöst und das Formular als Entwurf gespeichert.
* Aktivieren Sie die Funktion „Automatisches Speichern“, mit der das Formular beim angegebenen Ereignis oder nach einem konfigurierten Zeitintervall gespeichert wird.

### Erstellen von Regeln zum Speichern eines adaptiven Formulars als Entwurf {#rule-to-save-adaptive-form-as-draft}

Gehen Sie wie folgt vor, um eine Regel „Formular speichern“ für eine Formularkomponente wie beispielsweise eine Schaltfläche zu erstellen:

1. Öffnen Sie in der Autoreninstanz ein adaptives Formular im Bearbeitungsmodus.
1. Tippen Sie im linken Bereich auf das ![Symbol „Komponenten“](assets/components_icon.png) und ziehen Sie die Komponente [!UICONTROL Schaltfläche] auf das Formular.
1. Tippen Sie auf die Komponente [!UICONTROL Schaltfläche] und tippen Sie dann auf das ![Symbol „Konfigurieren“](assets/configure_icon.png).
1. Tippen Sie auf das Symbol [!UICONTROL Regeln bearbeiten], um den Regeleditor zu öffnen.
1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Regel zu konfigurieren und zu erstellen.
1. Wählen Sie im Abschnitt [!UICONTROL Wann] die Option „wird angeklickt“ und im Abschnitt [!UICONTROL Dann] die Option „Formular speichern“ aus.
1. Tippen Sie auf **[!UICONTROL Fertig]**, um die Regel zu speichern.

### Automatisches Speichern aktivieren {#enable-auto-save}

Sie können die Funktion zum automatischen Speichern für ein adaptives Formular wie folgt konfigurieren:

1. Öffnen Sie in der Autoreninstanz ein adaptives Formular im Bearbeitungsmodus.
1. Tippen Sie im linken Bereich auf das ![Symbol „Eigenschaften“](assets/configure_icon.png) und erweitern Sie die Option [!UICONTROL AUTOMATISCHES SPEICHERN].
1. Setzen Sie das Häkchen bei **[!UICONTROL Aktivieren]**, um das automatische Speichern des Formulars zu aktivieren. Sie können Folgendes konfigurieren:
* Standardmäßig wird [!UICONTROL Adaptives Formularereignis] auf „true“ gesetzt, was bedeutet, dass das Formular nach jedem Ereignis automatisch gespeichert wird.
* Wählen Sie unter [!UICONTROL Auslöser] die Einstellungen entsprechend, sodass die automatische Speicherung basierend auf dem Vorkommen eines Ereignisses oder nach einem bestimmten Zeitintervall ausgelöst wird.
