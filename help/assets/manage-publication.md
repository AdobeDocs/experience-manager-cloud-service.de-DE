---
title: 'Veröffentlichung verwalten '
description: Veröffentlichen oder Rückgängigmachen der Veröffentlichung von Assets in Experience Manager Assets, Dynamic Media und Brand Portal
contentOwner: Vishabh Gupta
mini-toc-levels: 1
feature: Asset Management, Publishing, Collaboration, Asset Processing
role: User, Architect, Admin
source-git-commit: 6ffdd6801fffb743314759b6c303723c2599dfa5
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 14%

---


# Veröffentlichung in Experience Manager Assets verwalten {#manage-publication-in-aem}

Als [!DNL Adobe Experience Manager Assets] Administrator: Sie können Assets und Ordner mit Assets aus Ihrer Autoreninstanz in [!DNL Experience Manager Assets], [!DNL Dynamic Media]und [!DNL Brand Portal]. Außerdem können Sie den Veröffentlichungs-Workflow für ein Asset oder einen Ordner zu einem späteren Zeitpunkt einplanen. Nach der Veröffentlichung können Benutzer auf die Assets zugreifen und sie an andere Benutzer weiterleiten. Standardmäßig können Sie Assets und Ordner in [!DNL Experience Manager Assets]. Sie können jedoch [!DNL Experience Manager Assets] , um die Veröffentlichung in [[!DNL Dynamic Media]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html) und [[!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/configure-aem-assets-with-brand-portal.html).

Sie können Assets auf der Asset- oder Ordnerebene veröffentlichen oder die Veröffentlichung rückgängig machen, indem Sie entweder **[!UICONTROL Quick Publish]** oder **[!UICONTROL Veröffentlichung verwalten]** -Option verfügbar im [!DNL Experience Manager Assets] -Schnittstelle. Wenn Sie nachfolgende Änderungen am ursprünglichen Asset oder Ordner in [!DNL Experience Manager Assets], werden die Änderungen erst dann in der Veröffentlichungsinstanz übernommen, wenn Sie die Veröffentlichung von [!DNL Experience Manager Assets]. Dadurch wird sichergestellt, dass laufende Änderungen nicht in der Veröffentlichungsinstanz verfügbar sind. In der Veröffentlichungsinstanz sind nur genehmigte Änderungen verfügbar, die von einem Administrator veröffentlicht werden.

* [Veröffentlichen von Assets mit &quot;Quick Publish&quot;](#quick-publish)
* [Veröffentlichen von Assets mit &quot;Veröffentlichung verwalten&quot;](#manage-publication)
* [Assets später veröffentlichen](#publish-assets-later)
* [Veröffentlichen von Assets in Dynamic Media](#publish-assets-to-dynamic-media)
* [Veröffentlichen von Assets in Brand Portal](#publish-assets-to-brand-portal)
* [Einschränkungen und Tipps](#limitations-and-tips)

## Veröffentlichen von Assets mit &quot;Quick Publish&quot; {#quick-publish}

Mit der Funktion &quot;Quick Publish&quot;können Sie Inhalte sofort an dem ausgewählten Ziel veröffentlichen. Aus dem [!DNL Experience Manager Assets] Navigieren Sie zum übergeordneten Ordner und wählen Sie alle Assets oder Ordner aus, die Sie veröffentlichen möchten. Klicken **[!UICONTROL Quick Publish]** in der Symbolleiste und wählen Sie in der Dropdown-Liste das Ziel aus, an dem Sie die Assets veröffentlichen möchten.

![Quick Publish](assets/quick-publish-to-aem.png)

## Veröffentlichen von Assets mit &quot;Veröffentlichung verwalten&quot; {#manage-publication}

Mit der Option Veröffentlichung verwalten können Sie Inhalte in und vom ausgewählten Ziel veröffentlichen oder deren Veröffentlichung rückgängig machen. [Inhalt hinzufügen](#add-content) zur Veröffentlichungsliste aus dem gesamten DAM-Repository [Ordnereinstellungen einschließen](#include-folder-settings) zum Veröffentlichen des Inhalts der ausgewählten Ordner und zum Anwenden von Filtern und [Veröffentlichung planen](#publish-assets-later) zu einem späteren Zeitpunkt.

Aus dem [!DNL Experience Manager Assets] Navigieren Sie zum übergeordneten Ordner und wählen Sie alle Assets oder Ordner aus, die Sie veröffentlichen möchten. Klicken **[!UICONTROL Veröffentlichung verwalten]** in der Symbolleiste. Wenn Sie [!DNL Dynamic Media] und [!DNL Brand Portal] in der [!DNL Experience Manager Assets] Instanz: Sie können Assets und Ordner nur in veröffentlichen [!DNL Experience Manager Assets].

![Veröffentlichung verwalten](assets/manage-publication-aem.png)

Die folgenden Optionen sind im [!UICONTROL Veröffentlichung verwalten] -Schnittstelle:

* [!UICONTROL Aktionen]
   * `Publish`: Veröffentlichen von Assets und Ordnern in dem ausgewählten Ziel
   * `Unpublish`: Rückgängigmachen der Veröffentlichung von Assets und Ordnern über das Ziel

* [!UICONTROL Destination]
   * `Publish`: Veröffentlichen von Assets und Ordnern in [!DNL Experience Manager Assets] (`AEM`)
   * `Dynamic Media`: Veröffentlichen von Assets in [!DNL Dynamic Media]
   * `Brand Portal`: Veröffentlichen von Assets und Ordnern in [!DNL Brand Portal]

* [!UICONTROL Zeitplan]
   * `Now`: Sofortiges Veröffentlichen von Assets
   * `Later`: Veröffentlichen von Assets basierend auf dem `Activation` Datum oder Uhrzeit

Um fortzufahren, klicken Sie auf **[!UICONTROL Nächste]**. Basierend auf der Auswahl wird die **[!UICONTROL Anwendungsbereich]** -Tab spiegelt verschiedene Optionen wider. Die Optionen für **[!UICONTROL Inhalt hinzufügen]** und **[!UICONTROL Ordnereinstellungen einschließen]** sind nur zum Veröffentlichen von Assets und Ordnern in verfügbar [!DNL Experience Manager Assets] (`Destination: Publish`).

![Umfang der Veröffentlichung verwalten](assets/manage-publication-aem-scope.png)

### Inhalt hinzufügen {#add-content}

>[!NOTE]
>
>Diese Funktion ist im Vorversionskanal verfügbar. Siehe [Dokumentation zum Vorabversionskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease) für Informationen zur Aktivierung der Funktion für Ihre Umgebung.

Veröffentlichen in [!DNL Experience Manager Assets] können Sie der Veröffentlichungsliste weitere Inhalte (Assets und Ordner) hinzufügen. Sie können der Liste weitere Assets oder Ordner über die dam-Repositorys hinweg hinzufügen. Klicken Sie auf **[!UICONTROL Inhalt hinzufügen]** um weitere Inhalte hinzuzufügen.

Sie können mehrere Assets aus einem Ordner hinzufügen oder mehrere Ordner gleichzeitig hinzufügen. Es ist jedoch nicht möglich, Assets aus mehreren Ordnern gleichzeitig hinzuzufügen.

![Inhalt hinzufügen](assets/manage-publication-add-content.png)

### Ordnereinstellungen einschließen {#include-folder-settings}

>[!NOTE]
>
>Diese Funktion ist im Vorversionskanal verfügbar. Siehe [Dokumentation zum Vorabversionskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease) für Informationen zur Aktivierung der Funktion für Ihre Umgebung.

Standardmäßig wird ein Ordner in [!DNL Experience Manager Assets] veröffentlicht alle Assets, Unterordner und deren Referenzen.

Um den Ordnerinhalt zu filtern, den Sie veröffentlichen möchten, klicken Sie auf **[!UICONTROL Ordnereinstellungen einschließen]**:

* `Include folder contents`

   * Aktiviert: Alle Assets des ausgewählten Ordners, Unterordner (einschließlich aller Assets der Unterordner) und Verweise werden veröffentlicht.
   * Deaktiviert: Nur der ausgewählte Ordner (leer) und die Verweise werden veröffentlicht. Die Assets des ausgewählten Ordners werden nicht veröffentlicht.

* `Include folder contents` und `Include only immediate folder contents`

   Wenn beide Optionen ausgewählt sind, werden alle Assets des ausgewählten Ordners, der Unterordner (leer) und Verweise veröffentlicht. Die Assets der Unterordner werden nicht veröffentlicht.

<!--
* [!UICONTROL Include only immediate folder contents]: Only the subfolders content and references are published. 

Only the selected folder content and references are published.
-->

![Ordnereinstellungen einschließen](assets/manage-publication-include-folder-settings.png)

Klicken Sie nach dem Anwenden der Filter auf **[!UICONTROL OK]** und klicken Sie anschließend auf **[!UICONTROL Veröffentlichen]**. Beim Klicken auf die Veröffentlichungsschaltfläche wird eine Bestätigungsmeldung angezeigt `Resource(s) have been scheduled for publication` angezeigt. Die ausgewählten Assets und (oder) Ordner werden basierend auf dem Planer (`Now` oder `Later`). Melden Sie sich bei Ihrer Veröffentlichungsinstanz an, um zu überprüfen, ob die Assets und (oder) Ordner erfolgreich veröffentlicht wurden.

![In AEM veröffentlichen](assets/manage-publication-publish-aem.png)

In der obigen Abbildung können Sie verschiedene Werte für die **[!UICONTROL Target veröffentlichen]** -Attribut. Erinnern wir uns an die Tatsache, dass Sie sich für die Veröffentlichung in entschieden haben [!DNL Experience Manager Assets] (`Destination: Publish`). Warum wird dann angezeigt, dass nur ein Ordner und ein Asset in veröffentlicht werden? `AEM`und die beiden anderen Assets in beiden veröffentlicht werden `AEM` und `Dynamic Media`?

Hier müssen Sie die Rolle der Ordnereigenschaften verstehen. Die **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** -Eigenschaft spielt eine wichtige Rolle bei der Veröffentlichung. Um die Eigenschaften eines Ordners anzuzeigen, wählen Sie einen Ordner aus und klicken Sie auf **[!UICONTROL Eigenschaften]** aus der Symbolleiste. Informationen zu einem Asset finden Sie in den Eigenschaften des übergeordneten Ordners.

In der folgenden Tabelle wird erläutert, wie die Veröffentlichung je nach der definierten **[!UICONTROL Ziel]** und **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]**:

| [!UICONTROL Ziel] | [!UICONTROL Veröffentlichungsmodus für Dynamic Media] | [!UICONTROL Ziel veröffentlichen] | Zulässiger Inhalt |
| --- | --- | --- | --- |
| Veröffentlichen | Selektive Veröffentlichung | `AEM` | Assets und/oder Ordner |
| Veröffentlichen   | Unmittelbar | `AEM` und `Dynamic Media` | Assets und/oder Ordner |
| Veröffentlichen   | Bei Aktivierung | `AEM` und `Dynamic Media` | Assets und/oder Ordner |
| Dynamic Media | Selektive Veröffentlichung | `Dynamic Media` | Assets |
| Dynamic Media | Unmittelbar | `None` | Assets können nicht veröffentlicht werden |
| Dynamic Media | Bei Aktivierung | `None` | Assets können nicht veröffentlicht werden |

>[!NOTE]
>
>Nur Assets werden in veröffentlicht [!DNL Dynamic Media].
>
>Veröffentlichen eines Ordners in [!DNL Dynamic Media] wird nicht unterstützt.
>
>Wenn Sie einen Ordner auswählen (`Selective Publish`) und wählen Sie die [!DNL Dynamic Media] Ziel, [!UICONTROL Target veröffentlichen] Attribut `None`.


Lassen Sie uns jetzt die **[!UICONTROL Ziel]** im oben genannten Anwendungsfall **[!UICONTROL Dynamic Media]** und überprüfen Sie die Ergebnisse. Dadurch wird nur das Asset von `Selective Publish` Ordner veröffentlicht in [!DNL Dynamic Media]. Die Assets von `Immediate` und `Upon Activation` Ordner werden nicht veröffentlicht und spiegeln `None`.

![In Dynamic Media veröffentlichen](assets/manage-publication-dynamic-media.png)

>[!NOTE]
>
>Wenn [!DNL Dynamic Media] nicht konfiguriert ist auf [!DNL Experience Manager Assets] und **[!UICONTROL Ziel]** is **[!UICONTROL Veröffentlichen]**, werden die Assets und Ordner immer in veröffentlicht `AEM`.
>
>Veröffentlichen in [!DNL Brand Portal] ist unabhängig von den Ordnereigenschaften. Alle Assets, Ordner und Sammlungen können in Brand Portal veröffentlicht werden. Siehe [Veröffentlichen von Assets in Brand Portal](#publish-assets-to-brand-portal).

>[!NOTE]
>
>Wenn Sie die [!DNL Manage Publication] -Assistenten verwenden, funktioniert Ihre Anpassung weiterhin mit den vorhandenen Funktionen.
>
>Sie können die vorhandene Anpassung jedoch entfernen, um die neue [!DNL Manager Publication] Funktionen.


## Assets später veröffentlichen {#publish-assets-later}

So planen Sie den Veröffentlichungs-Workflow für Assets zu einem späteren Zeitpunkt:

1. Aus dem [!UICONTROL Experience Manager Assets] Navigieren Sie zum übergeordneten Ordner und wählen Sie alle Assets oder Ordner aus, die Sie für die Veröffentlichung planen möchten.
1. Klicken **[!UICONTROL Veröffentlichung verwalten]** in der Symbolleiste.
1. Klicken **[!UICONTROL Veröffentlichen]** von **[!UICONTROL Aktion]** und wählen Sie anschließend die **[!UICONTROL Ziel]** wo Sie den Inhalt veröffentlichen möchten.
1. Wählen Sie **[!UICONTROL Später]** unter **[!UICONTROL Planung]** aus.
1. Wählen Sie eine **[!UICONTROL Aktivierungsdatum]** und geben Sie Datum und Uhrzeit an. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![Workflow &quot;Veröffentlichung verwalten&quot;](assets/manage-publication-workflow.png)

1. Im **[!UICONTROL Anwendungsbereich]** Registerkarte, **[!UICONTROL Inhalt hinzufügen]** (falls erforderlich). Klicken Sie auf **[!UICONTROL Weiter]**.
1. Im **[!UICONTROL Workflows]** Registerkarte einen Workflow-Titel angeben. Klicken Sie auf **[!UICONTROL Später veröffentlichen]**.

   ![Workflow-Titel](assets/manage-publication-workflow-title.png)

   Melden Sie sich bei der Zielinstanz an, um die veröffentlichten Assets zu überprüfen (je nach geplantem Datum oder Uhrzeit).

## Veröffentlichen von Assets in Dynamic Media {#publish-assets-to-dynamic-media}

Nur Assets werden in veröffentlicht [!DNL Dynamic Media]. Das Veröffentlichungsverhalten unterscheidet sich jedoch je nach Ordnereigenschaften. Ein Ordner kann **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** für eine selektive Veröffentlichung konfiguriert werden, bei der es sich um Folgendes handeln kann:

* `Selective Publish`
* `Immediate`
* `Upon Activation`

Der Veröffentlichungsprozess für **[!UICONTROL Sofort]** und **[!UICONTROL Bei Aktivierung]** -Modus konsistent ist, unterscheidet sich jedoch für **[!UICONTROL Selektive Veröffentlichung]**. Siehe [Selektive Veröffentlichung auf Ordnerebene in Dynamic Media konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html). Nachdem Sie selektive Veröffentlichung in einem Ordner konfiguriert haben, haben Sie folgende Möglichkeiten:

* [Assets mithilfe von &quot;Veröffentlichung verwalten&quot;selektiv in Dynamic Media oder Experience Manager veröffentlichen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-publish-manage-publication)
* [Heben Sie die Veröffentlichung von Assets in Dynamic Media oder Experience Manager mithilfe von „Veröffentlichung verwalten“ auf](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-unpublish-manage-publication)
* [Veröffentlichen von Assets in Dynamic Media oder Experience Manager mithilfe von „Quick Publish“](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#quick-publish-aem-dm)
* [Veröffentlichen Sie Assets mithilfe von Suchergebnissen selektiv bzw. heben Sie die Veröffentlichung auf](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-publish-unpublish-search-results)

## Veröffentlichen von Assets in Brand Portal {#publish-assets-to-brand-portal}

Sie können Assets, Ordner und Sammlungen in der [!DNL Experience Manager Assets Brand Portal] -Instanz.

* [Veröffentlichen von Assets in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-assets-to-bp)
* [Veröffentlichen von Ordnern in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-folders-to-brand-portal)
* [Veröffentlichen von Sammlungen in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-collections-to-brand-portal)

## Einschränkungen und Tipps {#limitations-and-tips}

* Die Option [!UICONTROL Veröffentlichung verwalten] ist nur für Benutzerkonten mit Berechtigungen zur Replikation verfügbar.
* Leere Ordner werden nicht veröffentlicht.
* Wenn Sie ein Asset veröffentlichen, das gerade verarbeitet wird, wird nur der ursprüngliche Inhalt veröffentlicht. Die Ausgabedarstellungen fehlen. Warten Sie entweder auf den Abschluss der Verarbeitung und veröffentlichen oder veröffentlichen Sie das Asset erneut, nachdem die Verarbeitung abgeschlossen ist.
* Wenn Sie die Veröffentlichung eines komplexen Assets aufheben möchten, achten Sie darauf, nur die Veröffentlichung des Assets aufzuheben. Vermeiden Sie das Rückgängigmachen der Veröffentlichung der Verweise, da diese von anderen veröffentlichten Assets referenziert werden können.

