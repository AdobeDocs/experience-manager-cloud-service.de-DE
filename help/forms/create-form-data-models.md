---
title: Erstellen eines Formulardatenmodells
description: Die Experience Manager Forms-Datenintegration bietet eine intuitive Benutzeroberfläche zum Erstellen von und Arbeiten mit Formulardatenmodellen. Erfahren Sie, wie Sie Formulardatenmodelle mit oder ohne konfigurierte Datenquellen erstellen.
feature: Form Data Model
role: User, Developer
level: Beginner, Intermediate
exl-id: b17b7441-912c-44c7-a835-809f014a8c86
source-git-commit: 1f3104d4a986018675f751afa04fe0ed3b7f5c26
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 61%

---

# Erstellen von Formulardatenmodellen {#create-form-data-model}

![Datenintegration](do-not-localize/data-integeration.png)

Die [!DNL Experience Manager Forms]-Datenintegration bietet eine intuitive Benutzeroberfläche zum Erstellen von und Arbeiten mit Formulardatenmodellen. Ein Formulardatenmodell stützt sich auf Datenquellen für den Austausch von Daten. Sie können jedoch ein Formulardatenmodell mit oder ohne Datenquelle erstellen. Je nachdem, ob Sie Datenquellen konfiguriert haben, gibt es zwei Möglichkeiten, ein Formulardatenmodell zu erstellen:

* **Vorkonfigurierte Datenquellen verwenden**: Wenn Sie Datenquellen wie in [Konfigurieren von Datenquellen](configure-data-sources.md) konfiguriert haben, können Sie diese beim Erstellen eines Formulardatenmodells auswählen. Es stellt alle Datenmodellobjekte, Eigenschaften und Services aus den ausgewählten Datenquellen zur Verwendung im Formulardatenmodell zur Verfügung.

* **Ohne Datenquellen**: Wenn Sie für Ihr Formulardatenmodell keine Datenquellen konfiguriert haben, können Sie es auch ohne Datenquellen erstellen. Sie können das Formulardatenmodell verwenden, um adaptive Formulare <!--and interactive communication--> zu verfassen und sie anhand von Beispieldaten zu testen. Wenn Datenquellen verfügbar sind, können Sie das Formulardatenmodell an Datenquellen binden, die automatisch in den zugehörigen adaptiven Formularen reflektiert werden<!--and interactive communications-->.

>[!NOTE]
>
>Sie müssen Mitglied der beiden Gruppen **fdm-author** und **forms-user** sein, um Formulardatenmodelle erstellen und verwenden zu können. Wenden Sie sich an Ihren [!DNL Experience Manager]-Administrator, um Mitglied der Gruppen zu werden.

## Erstellen von Formulardatenmodellen {#data-sources}

Stellen Sie sicher, dass Sie die Datenquellen konfiguriert haben, die Sie im Formulardatenmodell verwenden möchten, und zwar wie in [Konfigurieren von Datenquellen](configure-data-sources.md) beschrieben. Gehen Sie folgendermaßen vor, um ein Formulardatenmodell basierend auf konfigurierten Datenquellen zu erstellen:

1. Gehen Sie in der [!DNL Experience Manager]-Autorinstanz zu **[!UICONTROL Forms > Datenintegration]**.
1. Tippen Sie auf **[!UICONTROL Erstellen > Formulardatenmodell]**.
1. Im Dialogfeld „Formulardatenmodell erstellen“:

   * Geben Sie einen Namen für das Formulardatenmodul ein.
   * (**Optional**) Geben Sie Titel, Beschreibung und Tags für das Formulardatenmodell an.
   * (**Optional und nur anwendbar, wenn Datenquellen konfiguriert sind**) Tippen Sie auf das Häkchensymbol neben dem Feld **[!UICONTROL Datenquellenkonfiguration]** und wählen Sie den Konfigurationsknoten, in dem sich die Cloud Services für die Datenquellen befinden, die Sie verwenden möchten. Das beschränkt die Liste der Datenquellen, die auf der nächsten Seite zur Auswahl stehen, auf diejenigen, die im ausgewählten Konfigurationsknoten verfügbar sind. Allerdings [!DNL Experience Manager] Benutzerprofil-Datenquellen werden standardmäßig aufgelistet. Wenn Sie keinen Konfigurationsknoten auswählen, werden Datenquellen von allen Konfigurationsknoten aufgelistet.

1. Tippen Sie auf **[!UICONTROL Weiter]**.

1. (**Trifft nur zu, wenn Datenquellen konfiguriert sind**) Der Bildschirm **[!UICONTROL Datenquelle auswählen]** listet verfügbare Datenquellen auf, falls vorhanden. Wählen Sie Datenquellen aus, die Sie im Formulardatenmodell verwenden möchten.
1. Tippen Sie im Bestätigungsdialog auf **[!UICONTROL Erstellen]** und tippen Sie auf **[!UICONTROL Öffnen]**, um den Formulardatenmodelleditor zu starten.

   Im Folgenden werden die verschiedenen Komponenten der Benutzeroberfläche im Formulardatenmodelleditor beschrieben.

   ![Ein Formulardatenmodell mit drei Datenquellen: einem RESTful-Service, einem [!DNL Experience Manager]-Benutzerprofil und einem RDBMS](assets/fdm-ui.png)

   A. **[!UICONTROL Datenquellen]**: Listet Datenquellen in einem Formulardatenmodell auf. Erweitern Sie eine Datenquelle, um ihre Datenmodellobjekte und Services anzuzeigen.

   B. **[!UICONTROL Datenquellendefinitionen aktualisieren]**: Ruft alle Änderungen in den Datenquellendefinitionen aus den konfigurierten Datenquellen ab und aktualisiert sie in der Registerkarte „Data Sources“ des Formulardatenmodelleditors.

   C. **[!UICONTROL Modell]**: Inhaltsbereich, in dem hinzugefügte Datenmodellobjekte erscheinen.

   D. **[!UICONTROL Dienste]**: Inhaltsbereich, in dem hinzugefügte Datenquellenvorgänge oder -Services angezeigt werden.

   E. **[!UICONTROL Symbolleiste]**: Tools zum Arbeiten mit einem Formulardatenmodell. Die Symbolleiste zeigt mehr Optionen, abhängig vom ausgewählten Objekt im Formulardatenmodell.

   F. **[!UICONTROL Ausgewählte hinzufügen]**: Fügt dem Formulardatenmodell ausgewählte Datenmodellobjekte und Services hinzu.

Weitere Informationen zum Formulardatenmodelleditor und dazu, wie Sie mit ihm das Formulardatenmodell bearbeiten und konfigurieren können, finden Sie unter [Arbeiten mit einem Formulardatenmodell](work-with-form-data-model.md).

## Aktualisieren von Datenquellen {#update}

Führen Sie folgende Schritte aus, um Datenquellen zu einem vorhandenen Formulardatenmodell hinzuzufügen oder sie zu aktualisieren.

1. Wechseln Sie zu **[!UICONTROL Forms > Datenintegrationen]**, wählen Sie das Formulardatenmodell aus, dem Sie Datenquellen hinzufügen oder in dem Sie sie aktualisieren möchten, und tippen Sie auf **[!UICONTROL Eigenschaften]**.
1. Wechseln Sie in den Eigenschaften des Formulardatenmodells zur Registerkarte **[!UICONTROL Quelle aktualisieren]**.

   Auf der Registerkarte **[!UICONTROL Quelle aktualisieren]**:

   * Tippen Sie auf das Symbol „Durchsuchen“ im Feld **[!UICONTROL Kontextabhängige Konfiguration]** und wählen Sie einen Konfigurationsknoten aus, in dem sich die Cloud-Konfiguration für die hinzuzufügende Datenquelle befindet. Wenn Sie keinen Knoten auswählen, werden Cloud-Konfigurationen, die sich nur im Knoten `global` befinden, aufgelistet, wenn Sie auf **[!UICONTROL Quellen hinzufügen]** tippen.

   * Um eine neue Datenquelle hinzuzufügen, tippen Sie auf **[!UICONTROL Quellen hinzufügen]** und wählen Sie die Datenquellen aus, die dem Formulardatenmodell hinzugefügt werden sollen. Alle in `global` konfigurierten Datenquellen und ggf. der ausgewählte Konfigurationsknoten werden angezeigt.

   * Um eine vorhandene Datenquelle durch eine andere Datenquelle desselben Typs zu ersetzen, tippen Sie auf das Symbol **[!UICONTROL Bearbeiten]** für die Datenquelle und wählen Sie diese aus der Liste der verfügbaren Datenquellen aus.
   * Um eine vorhandene Datenquelle zu löschen, tippen Sie auf das Symbol **[!UICONTROL Löschen]** für die Datenquelle. Das Symbol „Löschen“ ist deaktiviert, wenn ein Datenmodellobjekt in der Datenquelle im Formulardatenmodell hinzugefügt wird.

      ![fdm-properties](assets/fdm-properties.png)

1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Aktualisierungen zu speichern.

>[!NOTE]
>
>Nachdem Sie neue Datenquellen hinzugefügt oder vorhandene Datenquellen in einem Formulardatenmodell aktualisiert haben, müssen Sie die Bindungsreferenzen in adaptiven Formularen<!--and interactive communications--> aktualisieren, die das aktualisierte Formulardatenmodell verwenden.

## Kontextabhängige Konfigurationen für bestimmte Ausführungsmodi {#runmode-specific-context-aware-config}

[!UICONTROL Formulardatenmodell] nutzt [Kontextabhängige Konfigurationen von Sling](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/context-aware-configs.html?lang=de) Unterstützung verschiedener Datenquellenparameter für die Verbindung mit Datenquellen für verschiedene [!DNL Experience Manager] Ausführungsmodi.

Wann [!UICONTROL Formulardatenmodell] verwendet Cloud-Konfigurationen zum Speichern von Parametern, die beim Einchecken und Bereitstellen über die Quell-Code-Verwaltung (Cloud Manager GIT-Repository) eine Cloud-Konfiguration mit denselben Parametern für alle Ausführungsmodi (Entwicklung, Staging und Produktion) erstellen. Für Anwendungsfälle, in denen unterschiedliche Datensätze für Test- und Produktionsumgebungen benötigt werden, verwenden wir jedoch Datenquellenparameter (z. B. die Datenquellen-URL) für verschiedene [!DNL Experience Manager] Ausführungsmodi.

Dazu müssen Sie eine OSGi-Konfiguration erstellen, die Datenquellenparameter-Wert-Paare enthält. Dadurch wird dasselbe Paar aus [!UICONTROL Formulardatenmodell] Cloud-Konfiguration zur Laufzeit. Da die OSGi-Konfigurationen diese Ausführungsmodi standardmäßig unterstützen, können Sie einen Datenquellenparameter basierend auf dem Ausführungsmodus in andere Werte überschreiben.

So aktivieren Sie bereitstellungsspezifische Cloud-Konfigurationen in [!UICONTROL Formulardatenmodell]:

1. Erstellen Sie die Cloud-Konfiguration auf der lokalen Entwicklungsinstanz. Ausführliche Anweisungen finden Sie unter [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md).

1. Speichern Sie Ihre Cloud-Konfiguration im Dateisystem.
   1. Paket mit Filter erstellen `/conf/{foldername}/settings/cloudconfigs/fdm`. Verwenden Sie dasselbe `{foldername}` wie in Schritt 1. und ersetzen `fdm` mit `azurestorage` für die Azure-Speicherkonfiguration.
   1. Erstellen und laden Sie das Paket herunter. Weitere Informationen finden Sie unter [Paketaktionen](/help/implementing/developing/tools/package-manager.md).

1. Integrieren der Cloud-Konfiguration in [!DNL Experience Manager] Archetypprojekt.
   1. Entpacken Sie das heruntergeladene Paket.
   1. Kopieren `jcr_root` Ordner und legen Sie sie `ui.content` > `src` > `main` > `content`.
   1. Aktualisieren `ui.content` > `src` > `main` > `content` > `META-INF` > `vault` > `filter.xml` Filter enthalten `/conf/{foldername}/settings/cloudconfigs/fdm`. Weitere Informationen finden Sie unter [ui.content-Modul AEM Projektarchetyps](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uicontent.html). Wenn dieses Archetypprojekt über die CM-Pipeline bereitgestellt wird, wird dieselbe Cloud-Konfiguration in allen Umgebungen (oder Ausführungsmodi) installiert. Um den Wert von Feldern (wie URL) von Cloud-Konfigurationen basierend auf der Umgebung zu ändern, verwenden Sie die OSGi-Konfiguration, die im folgenden Schritt beschrieben wird.

1. Erstellen Sie eine kontextabhängige Apache Sling-Konfiguration. So erstellen Sie die OSGi-Konfiguration:
   1. **Einrichten von OSGi-Konfigurationsdateien in [!DNL Experience Manager] Archetyp-Projekt.**
Erstellen von OSGi Factory-Konfigurationsdateien mit PID 
`org.apache.sling.caconfig.impl.override.OsgiConfigurationOverrideProvider`. Erstellen Sie eine Datei mit demselben Namen unter jedem Ausführungsmodusordner, in dem die Werte pro Ausführungsmodus geändert werden müssen. Weitere Informationen finden Sie unter [Konfigurieren von OSGi für [!DNL Adobe Experience Manager]](/help/implementing/deploying/configuring-osgi.md#creating-sogi-configurations).

   1. **Legen Sie die OSGi-Konfigurations-JSON fest.** So verwenden Sie den Apache Sling Context-Aware Configuration Override Provider:
      1. In der lokalen Entwicklungsinstanz `/system/console/configMgr`, wählen Sie die werkseitige OSGi-Konfiguration mit dem Namen aus. **[!UICONTROL Apache Sling Context-Aware Configuration Override Provider: OSGi-Konfiguration]**.
      1. Geben Sie eine Beschreibung an.
      1. Auswählen **[!UICONTROL enabled]**.
      1. Geben Sie unter Überschreibungen Felder an, die basierend auf der Umgebung in der Sling-Überschreibungssyntax geändert werden müssen. Weitere Informationen finden Sie unter [Kontextabhängige Konfiguration von Apache Sling - Außerkraftsetzen](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration-override.html#override-syntax). Beispiel, `cloudconfigs/fdm/{configName}/url="newURL"`.
Durch Auswahl von **[!UICONTROL +]**.
      1. Wählen Sie **[!UICONTROL Speichern]** aus.
      1. Um die JSON-Datei für die OSGi-Konfiguration zu erhalten, führen Sie die Schritte unter [Generieren von OSGi-Konfigurationen mit dem AEM SDK QuickStart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart).
      1. Platzieren Sie JSON in den OSGi Factory Configuration Files , die im vorherigen Schritt erstellt wurden.
      1. Ändern Sie den Wert von `newURL` basierend auf der Umgebung (oder dem Ausführungsmodus).
      1. Um den geheimen Wert basierend auf dem Runmode zu ändern, kann die geheime Variable mithilfe von [Cloud Manager-API](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) und später kann im [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md#secret-configuration-values).
Wenn dieses Archetyp-Projekt über die CM-Pipeline bereitgestellt wird, stellt Override in verschiedenen Umgebungen (oder im Ausführungsmodus) unterschiedliche Werte bereit.

      >[!NOTE]
      >
      >[!DNL Adobe Managed Service] -Benutzer können die geheimen Werte mithilfe von &quot;crypto&quot;-Unterstützung verschlüsseln (weitere Informationen finden Sie unter [Verschlüsselungsunterstützung für Konfigurationseigenschaften](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/encryption-support-for-configuration-properties.html#enabling-encryption-support) und verschlüsselten Text im Wert nach platzieren [Kontextabhängige Konfigurationen sind in Service Pack 6.5.13.0 verfügbar.](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html#runmode-specific-context-aware-config).

1. Aktualisieren Sie die Datenquellendefinitionen mit der Option zum Aktualisieren der Datenquellendefinitionen im Abschnitt [Formulardatenmodell-Editor](#data-sources) , um den FDM-Cache über die FDM-Benutzeroberfläche zu aktualisieren und die neueste Konfiguration zu erhalten.

## Nächste Schritte {#next-steps}

Sie haben jetzt ein Formulardatenmodell, dem Datenquellen hinzugefügt wurden. Als Nächstes können Sie das Formulardatenmodell bearbeiten, um Datenmodellobjekte und -Services hinzuzufügen und zu konfigurieren, Verknüpfungen zwischen Datenmodellobjekten hinzuzufügen, Eigenschaften zu bearbeiten, benutzerdefinierte Datenmodellobjekte und -eigenschaften hinzuzufügen, Beispieldaten zu generieren und so weiter.

Weitere Informationen finden Sie unter [Arbeiten mit einem Formulardatenmodell](work-with-form-data-model.md).
