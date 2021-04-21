---
title: Arbeiten mit selektiver Veröffentlichung in Dynamic Media
description: Erfahren Sie, wie Sie mit Selektiver Veröffentlichung in Dynamic Media arbeiten.
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: Business Practitioner
exl-id: a5a2df68-be13-45a6-ad80-09fbd2fea8f2
translation-type: tm+mt
source-git-commit: e94289bccc09ceed89a2f8b926817507eaa19968
workflow-type: tm+mt
source-wordcount: '2935'
ht-degree: 52%

---

# Konfigurieren von selektiver Veröffentlichung auf der Ordnerebene in Dynamic Media {#selective-publish-configure-folder}

Sie können Assets auf Ordnerebene auf oder von Adobe Experience Manager oder Dynamic Media veröffentlichen oder die Veröffentlichung rückgängig machen. Verwenden Sie dazu entweder **[!UICONTROL Veröffentlichung verwalten]** oder **[!UICONTROL Schnellveröffentlichung]**. Diese Veröffentlichungsmethode ist nützlich, da sie nicht ausschließlich auf der **[!UICONTROL Dynamic Media Configuration]** basiert, deren Einstellungen für alle Ordner in Ihrer Dynamic Media-Instanz gültig sind.

Beispielsweise können Sie mit selektiver Veröffentlichung Assets für Produkte bearbeiten, die noch nicht live sind. In diesem Fall kann ein Marketingteam auf Bilder mit intelligenten Zuschnitten und dynamische Darstellungen zugreifen, die mit Dynamic Media synchronisiert werden. Sie können Werbematerialien erstellen, ohne diese Assets für den weltweiten Versand in Dynamic Media veröffentlichen zu müssen.

<!-- 
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>Beim *Kopieren* von Assets in und aus Ordnern wird der Veröffentlichungsstatus der Assets gelöscht. Wenn Sie Assets in oder aus Ordnern *verschieben*, deren Ordnereigenschaft auf **[!UICONTROL Selektive Veröffentlichung]** festgelegt ist, wird der Veröffentlichungsstatus dieser Assets jedoch beibehalten.

Falls Sie sich später entscheiden, die Einstellungen für **[!UICONTROL Selektive Veröffentlichung]** in einem Ordner zu ändern, wirken sich diese Änderungen nur auf neue Assets aus, die Sie ab diesem Zeitpunkt in den Ordner hochladen. Der Veröffentlichungsstatus vorhandener Assets im Ordner bleibt unverändert, bis Sie ihn im Dialogfeld **[!UICONTROL Quick Publish]** oder **[!UICONTROL Veröffentlichung verwalten]** manuell ändern.

Die Option **[!UICONTROL Dynamic Media Publish mode]** auf Ordnerebene ist immer standardmäßig auf den Wert eingestellt, der in der Einstellung **[!UICONTROL Assets veröffentlichen]** in **[!UICONTROL Dynamic Media Configuration]** enthalten ist. enthalten ist. Folgende Schritte in diesem Thema zeigen Ihnen jedoch, wie Sie diesen Standardwert auf der Ordnerebene manuell ändern können (wie in den folgenden Schritten beschrieben), um den Wert für die **[!UICONTROL Dynamic Media-Konfiguration]** zu überschreiben.

Unabhängig davon, ob Sie darauf vertrauen:

* Der Wert **[!UICONTROL Assets veröffentlichen]**, der in **[!UICONTROL Dynamic Media-Konfiguration]** festgelegt ist
* Oder der Wert **[!UICONTROL Dynamic Media Publish mode]**, der in den Eigenschaften auf Ordnerebene festgelegt ist

Sie können weiterhin **[!UICONTROL Sofort]**, **[!UICONTROL Bei Aktivierung]** oder **[!UICONTROL Selektive Veröffentlichung]** auswählen. Sie können beispielsweise den Wert **[!UICONTROL Assets veröffentlichen]** in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** auf **[!UICONTROL Bei Aktivierung]** setzen. Und Sie können den Modus-Wert **[!UICONTROL Dynamic Media Publish]** auf Ordnerebene auf **[!UICONTROL Selektive Veröffentlichung]** einstellen, umgekehrt usw.

Nachdem Sie selektive Veröffentlichung in einem Ordner konfiguriert haben, haben Sie folgende Möglichkeiten:

* [Veröffentlichen Sie Assets mithilfe von &quot;Veröffentlichung](#selective-publish-manage-publication) verwalten&quot;selektiv auf Dynamic Media oder Experience Manager.
* [Rückgängigmachen der Veröffentlichung von Assets aus Dynamic Media oder Experience Manager mithilfe von &quot;Veröffentlichung](#selective-unpublish-manage-publication) verwalten&quot;.
* [Veröffentlichen von Assets auf Dynamic Media oder Experience Manager mithilfe der Schnellveröffentlichung](#quick-publish-aem-dm).
* [Veröffentlichen Sie Assets mithilfe von Suchergebnissen selektiv bzw. machen Sie die Veröffentlichung rückgängig](#selective-publish-unpublish-search-results).

**So konfigurieren Sie eine selektive Veröffentlichung auf der Ordnerebene in Dynamic Media**

1. Tippen Sie in Experience Manager auf das Logo des Experience Managers, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Führen Sie einen der folgenden Schritte aus:
   * Eigenschaften eines vorhandenen Ordners bearbeiten – Navigieren Sie in der **[!UICONTROL Kartenansicht]**, der **[!UICONTROL Spaltenansicht]** oder der **[!UICONTROL Listenansicht]** zu einem Ordner, dessen Eigenschaften Sie bearbeiten möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
   * Bearbeiten Sie die Eigenschaften eines neuen Ordners: Klicken Sie in **[!UICONTROL Ansicht]**, **[!UICONTROL Ansicht]** oder **[!UICONTROL Liste-Ansicht]** oben rechts auf der Seite auf **[!UICONTROL Erstellen > Ordner]**. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** einen Titel (erforderlich) für den Ordner ein und tippen Sie dann auf **[!UICONTROL Erstellen]**. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Synchronisationsmodus]** eine der folgenden Optionen aus:

   | Synchronisationsmodus | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Übernommen]** | Kein expliziter Synchronisierungswert im Ordner; Stattdessen übernimmt der Ordner den Synchronisierungswert von einem seiner Vorgängerordner oder den Standardmodus, der in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** festgelegt ist. Der detaillierte Status von **[!UICONTROL Inherited]** wird als QuickInfo angezeigt. |
   | **[!UICONTROL Synchronisieren Sie alles in diesem Ordner-Unterbaum mit Dynamic Media]** | Damit das Veröffentlichen in Dynamic Media erfolgreich ist, müssen Assets mit Dynamic Media synchronisiert werden. Wenn Sie diese Option auswählen, werden alle Assets in dieser Unterstruktur zum Synchronisieren mit Dynamic Media ausgewählt. Die ordnerspezifischen Einstellungen setzen die Standardeinstellung in **[!UICONTROL Dynamic Media Configuration]** außer Kraft. |
   | **[!UICONTROL Alle Elemente in diesem Ordner-Unterbaum von der Dynamic Media-Synchronisierung ausschließen]** | Schließen Sie alle Assets in dieser Unterstruktur von der Synchronisierung mit Dynamic Media aus. |

   ![Selektive Veröffentlichung auf Ordnerebene](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** eine Option aus. Die Option **[!UICONTROL Dynamic Media Publish mode]** verwendet immer den Wert, der in **[!UICONTROL Dynamic Media Configuration]** festgelegt ist. festgelegte Wert verwendet wird. Sie können diesen Standardwert für die **[!UICONTROL Dynamic Media-Konfiguration]** jedoch manuell überschreiben, indem Sie eine der folgenden Optionen nutzen.

   >[!IMPORTANT]
   >
   >Unabhängig von der ausgewählten Option im Dynamic Media-Veröffentlichungsmodus werden alle Aktualisierungen, die Sie später an einem Asset vornehmen, das bereits *veröffentlicht ist, sofort ohne weitere Benutzeraktionen veröffentlicht.*

   | Option für Veröffentlichungsmodus für Dynamic Media | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Sofort]** | Wenn Assets in diesen Ordner hochgeladen werden, lädt das System die Assets in Experience Manager ein und stellt die URL/Einbettung sofort bereit. Diese Option ist nur an die Veröffentlichung von Experience Managern gebunden und es ist kein Benutzereingriff erforderlich, um Assets zu veröffentlichen.<br>Diese Option ist  ** nicht verfügbar, wenn Sie im vorherigen Schritt die Option Alles in diesem Ordner-Unterbaum  **[!UICONTROL ausschließen aus dem Dynamic Media]** Synchronisierungs- **[!UICONTROL Modus]** ausgewählt haben. |
   | **[!UICONTROL Bei Aktivierung]** | Wenn Assets in diesen Ordner hochgeladen werden, müssen Sie das Asset zuerst explizit veröffentlichen, bevor ein URL-/Einbettungslink bereitgestellt wird. Diese Option ist nur an die Veröffentlichung von Experience Managern gebunden.<br>Diese Option ist  ** nicht verfügbar, wenn Sie im vorherigen Schritt die Option Alles in diesem Ordner-Unterbaum  **[!UICONTROL ausschließen aus dem Dynamic Media]** Synchronisierungs- **[!UICONTROL Modus]** ausgewählt haben. |
   | **[!UICONTROL Selektive Veröffentlichung]** | Assets werden nach Wahl des Experience Managers oder nach Dynamic Media zum Versand im öffentlichen Bereich veröffentlicht. Beide Veröffentlichungsmethoden schließen sich gegenseitig aus. Das heißt, Sie können Assets in DMS7 veröffentlichen, damit Sie Funktionen wie smartes Zuschneiden oder dynamische Ausgabedarstellungen verwenden können. Oder Sie können Assets ausschließlich für eine sichere Vorschau auf Experience Manager veröffentlichen. dieselben Assets sind *nicht*, die in DMS7 veröffentlicht werden, um sie in der öffentlichen Domäne Versand. Diese Option steht nicht zur Verfügung, wenn Sie im vorherigen Schritt **[!UICONTROL Alles in diesem Ordner-Unterbaum aus Dynamic Media sync]** im **[!UICONTROL Synchronisierungsmodus]** ausschließen ausgewählt haben. |

1. Tippen Sie oben rechts auf der Seite auf **[!UICONTROL Speichern &amp; Schließen]** und dann auf **[!UICONTROL OK]**, um zu Experience Manager Assets zurückzukehren.

## Selektives Veröffentlichen von Assets auf Dynamic Media oder Experience Manager als Cloud Service mithilfe von &quot;Veröffentlichung verwalten{#selective-publish-manage-publication}&quot;

Bevor Sie mit **[!UICONTROL Veröffentlichung verwalten]** selektiv Assets auf Dynamic Media oder Experience Manager veröffentlichen können, müssen Sie Folgendes ausgeführt haben:

* Legen Sie die Option **[!UICONTROL Assets veröffentlichen]** in **[!UICONTROL Dynamic Media-Konfiguration]** auf **[!UICONTROL Selektive Veröffentlichung]** fest.
* Oder konfigurierte selektive Veröffentlichung auf Ordnerebene.

Siehe [Erstellen einer Dynamic Media-Konfiguration](#configuring-dynamic-media-cloud-services) oder [Konfigurieren von selektiver Veröffentlichung auf der Ordnerebene in Dynamic Media](#selective-publish-configure-folder).

<!--
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>Beim *Kopieren* von Assets in und aus Ordnern wird der Veröffentlichungsstatus der Assets gelöscht. Wenn Sie Assets in oder aus Ordnern *verschieben*, deren Ordnereigenschaft auf **[!UICONTROL Selektive Veröffentlichung]** festgelegt ist, wird der Veröffentlichungsstatus dieser Assets jedoch beibehalten.

**So veröffentlichen Sie Assets selektiv unter Verwendung von &quot;Veröffentlichung verwalten&quot;auf Dynamic Media oder Experience Manager**

1. Tippen Sie in Experience Manager auf das Logo des Experience Managers, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Führen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Verwenden Sie die Ansicht **[!UICONTROL Liste]**, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners einfacher überprüfen können.
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Verwenden Sie die Ansicht **[!UICONTROL Liste]**, damit Sie den Veröffentlichungsstatus eines bestimmten Assets einfacher überprüfen können.

      >[!NOTE]
      >
      >Wenn **[!UICONTROL Veröffentlichung verwalten]** nicht in der Symbolleiste angezeigt wird, tippen Sie auf die Schaltfläche mit den Auslassungszeichen und wählen Sie im Listenmenü die Option **[!UICONTROL Veröffentlichung verwalten]**.

1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** unter **[!UICONTROL Aktion]** den gewünschten Aktivierungstyp aus.

   | Aktion | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Veröffentlichen]**  (auf Experience Manager) | Um Assets für eine sichere Vorschau in Experience Manager zu veröffentlichen, wählen Sie diese Option. |
   | **[!UICONTROL In Dynamic Media veröffentlichen]** | Wenn Sie Assets für den Versand im öffentlichen Bereich auf Dynamic Media veröffentlichen möchten oder Sie Funktionen wie Smart-Zuschneiden oder dynamische Darstellungen verwenden möchten, wählen Sie diese Option.<br>Diese Option ist nur verfügbar, wenn in den Eigenschaften des Ordners der **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** auf **[!UICONTROL Selektive Veröffentlichung]** gesetzt ist. |

1. Legen Sie unter **[!UICONTROL Zeitplan]** den Zeitpunkt der Veröffentlichung fest.

   | Zeitplan | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Jetzt]** | Wählen Sie diese Option, um die Assets sofort zu veröffentlichen. |
   | **[!UICONTROL Später]** | Wählen Sie diese Option, um die Assets an einem bestimmten Datum zu einer bestimmten Uhrzeit zu veröffentlichen. |

1. Tippen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten]** auf **[!UICONTROL Weiter]**.
1. Führen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** einen der folgenden Schritte aus:
   * Wählen Sie bei Bedarf ein oder mehrere Assets aus, die Sie aus der Veröffentlichung entfernen möchten.
   * Tippen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL In Dynamic Media veröffentlichen]**.
1. Tippen Sie auf **[!UICONTROL OK]**.

### Rückgängigmachen der Veröffentlichung von Assets aus Dynamic Media oder Experience Manager mithilfe von &quot;Veröffentlichung verwalten&quot;{#selective-unpublish-manage-publication}

1. Tippen Sie in Experience Manager auf das Logo des Experience Managers, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der linken Seite auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Führen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, für dessen Assets Sie die Veröffentlichung rückgängig machen möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Verwenden Sie die Ansicht **[!UICONTROL Liste]**, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners einfacher überprüfen können.
   * Navigieren Sie zu einem Ordner, für dessen Assets Sie die Veröffentlichung rückgängig machen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Verwenden Sie die Ansicht **[!UICONTROL Liste]**, damit Sie den Veröffentlichungsstatus eines bestimmten Assets einfacher überprüfen können.

      >[!NOTE]
      >
      >Wenn **[!UICONTROL Veröffentlichung verwalten]** nicht in der Symbolleiste angezeigt wird, tippen Sie auf die Schaltfläche mit den Auslassungszeichen und wählen Sie im Listenmenü die Option **[!UICONTROL Veröffentlichung verwalten]**.

1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** unter **[!UICONTROL Aktion]** die gewünschte Art der Deaktivierung aus.

   | Aktion | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Veröffentlichung rückgängig machen]**  (von Experience Manager) | Um die Veröffentlichung von Assets aus Experience Manager rückgängig zu machen, wählen Sie diese Option aus. |
   | **[!UICONTROL Veröffentlichung in Dynamic Media rückgängig machen]** | Um die Veröffentlichung von Assets aus Dynamic Media rückgängig zu machen, wählen Sie diese Option.<br>Diese Option ist nur verfügbar, wenn in den Eigenschaften des Ordners der **[!UICONTROL Veröffentlichungsmodus für Dynamic Media]** auf **[!UICONTROL Selektive Veröffentlichung]** gesetzt ist. |

1. Legen Sie unter **[!UICONTROL Zeitplan]** den Zeitpunkt der Deaktivierung fest.

   | Zeitplan | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Jetzt]** | Wählen Sie diese Option, um die Veröffentlichung der Assets sofort rückgängig zu machen. |
   | **[!UICONTROL Später]** | Wählen Sie diese Option, um die Veröffentlichung der Assets an einem bestimmten Datum zu einer bestimmten Uhrzeit rückgängig zu machen. |

1. Tippen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten]** auf **[!UICONTROL Weiter]**.
1. Führen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, deren Veröffentlichung Sie rückgängig machen möchten.
   * Tippen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** auf **[!UICONTROL Veröffentlichung rückgängig machen]** oder **[!UICONTROL Veröffentlichung in Dynamic Media rückgängig machen]**.
1. Tippen Sie auf **[!UICONTROL OK]**.

## Veröffentlichen von Assets auf Dynamic Media oder Experience Manager mithilfe der Schnellveröffentlichung {#quick-publish-aem-dm}

Für einfache Asset-Aktivierungen können Sie **[!UICONTROL Quick Publish]** verwenden. Mit der Funktion **[!UICONTROL Quick Publish]** werden die ausgewählten Assets ohne weitere Benutzerinteraktion sofort veröffentlicht. Alle nicht veröffentlichten Verweise werden ebenfalls automatisch veröffentlicht.

>[!NOTE]
>
>Um Assets mit **[!UICONTROL Schnellveröffentlichung]** auf Dynamic Media oder Experience Manager zu veröffentlichen, stellen Sie sicher, dass **[!UICONTROL Selektive Veröffentlichung]** entweder in Ihrer **[!UICONTROL Dynamic Media-Konfiguration]** oder in den Ordnereigenschaften des ausgewählten Ordners aktiviert ist.

**So veröffentlichen Sie Assets mit der Schnellveröffentlichung auf Dynamic Media oder Experience Manager:**

1. Tippen Sie in Experience Manager auf das Logo des Experience Managers, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie links auf der Seite auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann rechts auf der Seite auf **[!UICONTROL Assets > Dateien]**.
1. Führen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** einen der folgenden Schritte aus:
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Wählen Sie den Ordner aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Schnellveröffentlichung]**. Verwenden Sie die Ansicht **[!UICONTROL Liste]**, damit Sie den Veröffentlichungsstatus eines bestimmten Ordners einfacher überprüfen können.
   * Navigieren Sie zu einem Ordner, dessen Assets Sie veröffentlichen möchten. Öffnen Sie den Ordner und wählen Sie dann ein oder mehrere Assets aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Quick Publish]**. Verwenden Sie die Ansicht **[!UICONTROL Liste]**, damit Sie den Veröffentlichungsstatus eines bestimmten Assets einfacher überprüfen können.

      >[!NOTE]
      >
      >Wenn **[!UICONTROL Quick Publish]** nicht in der Symbolleiste angezeigt wird, tippen Sie auf die Schaltfläche mit den Auslassungszeichen und wählen Sie im Listenmenü die Option **[!UICONTROL Quick Publish]**.

      ![„Quick Publish“ auf der Ordnerebene in Dynamic Media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Wählen Sie aus dem Listenmenü **[!UICONTROL Quick Publish]** eine der folgenden Optionen aus.

   | Option „Quick Publish“ | Funktion |
   | --- | --- | 
   | Auf Experience Manager veröffentlichen | Veröffentlicht die ausgewählten Assets sofort in Experience Manager. |
   | In Brand Portal veröffentlichen | Veröffentlicht die ausgewählten Assets sofort in **[!UICONTROL Brand Portal]**.<br>Diese Option ist nur verfügbar, wenn Ihre Experience Manager Assets-Instanz  **[!UICONTROL Brand]** Portal bereits konfiguriert hat. |
   | In Dynamic Media veröffentlichen | Veröffentlicht die ausgewählten Assets sofort in Dynamic Media.<br>Ein Asset muss bereits mit Dynamic Media synchronisiert werden. Stellen Sie bei Bedarf sicher, dass **[!UICONTROL Synchronisierungsmodus]** in den Eigenschaften eines Ordners bereits auf **[!UICONTROL Synchronisieren Sie alles in diesem Ordner-Unterbaum mit Dynamic Media]** eingestellt ist. |

1. Tippen Sie auf **[!UICONTROL OK,]** und dann auf **[!UICONTROL Schließen]**.

## Selektive Veröffentlichung oder Rückgängigmachen der Veröffentlichung von Assets mithilfe von Suchergebnissen {#selective-publish-unpublish-search-results}

In den Suchergebnissen können Assets aus allen Asset-Ordnern angezeigt werden, die unterschiedliche Veröffentlichungseinstellungen für Dynamic Media haben. Wenn Sie ein oder mehrere Assets aus den Suchergebnissen ausgewählt haben und die Assets unterschiedliche Einstellungen für den Dynamic Media-Veröffentlichungsmodus haben, können Sie die Option &quot;Veröffentlichung verwalten ]**&quot;in der Symbolleiste zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung Trigger haben.**[!UICONTROL 

Siehe auch [Suchen von Assets in Experience Manager](/help/assets/search-assets.md).

**So veröffentlichen Sie Assets selektiv mithilfe von Suchergebnissen oder machen die Veröffentlichung rückgängig**

1. Tippen Sie in Experience Manager links oben auf der Seite auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der Seite links auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Tippen Sie in der Symbolleiste rechts oben auf der Seite auf das Suchsymbol (Lupe).
1. Geben Sie im Textfeld **[!UICONTROL Zu suchender Typ]** ein Keyword ein und drücken Sie dann die **[!UICONTROL Eingabetaste]**.
1. Tippen Sie oben rechts auf der Seite auf das Symbol **[!UICONTROL Listenansicht]**.
1. Tippen Sie oben links auf das Symbol **[!UICONTROL Filter]**.

   ![Listenansicht und Filter in Suchergebnissen](/help/assets/assets-dm/select-publish-search-result.png)

1. Erweitern Sie im linken Bereich den **[!UICONTROL Status]** und dann das Suchprädikat für **[!UICONTROL Dynamic Media]**.
1. Verwenden Sie die Kontrollkästchen **[!UICONTROL Veröffentlicht]** und **[!UICONTROL Veröffentlichung rückgängig gemacht]**, um die Suchergebnisse je nach Veröffentlichungsstatus der Dynamic Media-Assets weiter zu verfeinern.
Optional können Sie diese Kontrollkästchen mit der Suchvorhersage **[!UICONTROL Veröffentlichen]** verwenden, um die Suchergebnisse der Elemente **[!UICONTROL Veröffentlicht]** und **[!UICONTROL Nicht veröffentlicht]** zu verfeinern.
1. Führen Sie einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, die Sie veröffentlichen oder deren Veröffentlichung Sie rückgängig machen möchten.
   * Tippen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Suchergebnisse]** auf **[!UICONTROL Alle auswählen]**.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Falls erforderlich, tippen Sie auf das Auslassungszeichen in der Symbolleiste, um **[!UICONTROL Veröffentlichung verwalten]** anzuzeigen.
1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** die gewünschte Aktion aus.

   | Ausgewählte Aktion | Einstellung für die Veröffentlichung von Assets in der Dynamic Media-Konfiguration | Asset-Status |
   | --- | --- | --- |
   | Veröffentlichen | Sofort oder bei Aktivierung | Veröffentlicht an Experience Manager und Dynamic Media. |
   | Veröffentlichen | Selektive Veröffentlichung | Nur für Experience Manager veröffentlicht. |
   | Veröffentlichung rückgängig machen | Sofort oder bei Aktivierung | Veröffentlichung in Experience Manager und Dynamic Media rückgängig gemacht. |
   | Veröffentlichung rückgängig machen | Selektive Veröffentlichung | Nur Veröffentlichung von Experience Manager rückgängig gemacht. |
   | In Dynamic Media veröffentlichen | Sofort oder bei Aktivierung | Nicht in Experience Manager oder Dynamic Media oder beidem veröffentlicht. |
   | In Dynamic Media veröffentlichen | Selektive Veröffentlichung | Nur in Dynamic Media veröffentlicht. |
   | Veröffentlichung in Dynamic Media rückgängig machen | Sofort oder bei Aktivierung | Veröffentlichung von Experience Manager oder Dynamic Media oder beidem nicht rückgängig gemacht. |
   | Veröffentlichung in Dynamic Media rückgängig machen | Selektive Veröffentlichung | Veröffentlichung nur in Dynamic Media rückgängig gemacht. |

1. Legen Sie unter **[!UICONTROL Zeitplan]** den Zeitpunkt der Deaktivierung fest.

   | Ausgewählter Zeitplan | Ergebnis |
   | --- | --- |
   | Jetzt | Die ausgewählte Aktion wird sofort ausgeführt. |
   | Später | Die ausgewählte Aktion wird am ausgewählten Datum zur ausgewählten Uhrzeit ausgeführt. |

1. Tippen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Veröffentlichung verwalten – Optionen]** auf **[!UICONTROL Weiter]**.
1. (Optional) Überprüfen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten - Umfang]** in der Tabelle die Spalte **[!UICONTROL Ziel veröffentlichen]**, um die ausgewählten Assets anzuzeigen.

   | Einstellung für die Veröffentlichung von Assets in der Dynamic Media-Konfiguration | Ausgewählte Aktion | Veröffentlichungsziel |
   | --- | --- | --- |
   | Sofort oder <br>bei Aktivierung | Veröffentlichen | Experience Manager und Dynamic Media |
   | Sofort oder <br>bei Aktivierung | In Dynamic Media veröffentlichen | Kein |
   | Selektive Veröffentlichung | Veröffentlichen | Experience Manager |
   | Selektive Veröffentlichung | In Dynamic Media veröffentlichen | Dynamic Media |
   | Sofort oder <br>bei Aktivierung | Veröffentlichung rückgängig machen | Experience Manager und Dynamic Media |
   | Sofort oder <br>bei Aktivierung | Veröffentlichung in Dynamic Media rückgängig machen | Kein |
   | Selektive Veröffentlichung | Veröffentlichung rückgängig machen | Experience Manager |
   | Selektive Veröffentlichung | Veröffentlichung in Dynamic Media rückgängig machen | Dynamic Media |

1. Führen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** einen der folgenden Schritte aus:
   * Wählen Sie ein oder mehrere Assets aus, die Sie aus der Veröffentlichung oder dem Rückgängigmachen der Veröffentlichung entfernen möchten.
   * Tippen Sie oben rechts auf der Seite **[!UICONTROL Veröffentlichung verwalten – Umfang]** auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Veröffentlichung rückgängig machen]**, um die Aktion zu starten.
1. Tippen Sie auf **[!UICONTROL OK]**.

## Überprüfen des Veröffentlichungsstatus eines Assets {#check-publish-status-of-asset}

Sie können **[!UICONTROL Zeitschiene]** mit **[!UICONTROL Ansicht]**, **[!UICONTROL Ansicht]** oder **[!UICONTROL Liste-Ansicht]** in Experience Manager verwenden, um den Veröffentlichungsstatus eines Assets schnell zu überprüfen.

**So prüfen Sie den Veröffentlichungsstatus eines Assets**

1. Tippen Sie in Experience Manager links oben auf der Seite auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen. Tippen Sie auf der Seite links auf das Navigationssymbol (direkt über dem Werkzeugsymbol) und dann auf **[!UICONTROL Assets > Dateien]**.
1. Öffnen Sie in der **[!UICONTROL Kartenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Listenansicht]** (im Screenshot unten ist die **[!UICONTROL Listenansicht]** dargestellt) einen Ordner, der Assets enthält, die Sie veröffentlicht haben oder deren Veröffentlichung Sie rückgängig gemacht haben.
1. Wählen Sie ein Asset aus, damit es mit einem Häkchen angezeigt wird. Siehe als Beispiel den Screenshot unten.
1. Wählen Sie in der linken oberen Ecke der Seite aus dem Dropdown-Menü **[!UICONTROL Zeitschiene]**. . Der Bereich **[!UICONTROL Status]** links zeigt den Veröffentlichungsstatus des ausgewählten Assets an.
Wenn Sie die Ansicht **[!UICONTROL Liste]** verwenden, wird eine zusätzliche Spalte für den Veröffentlichungsstatus **[!UICONTROL Dynamic Media]** angezeigt.
   * In einem Ordner, der für die Synchronisierung mit Dynamic Media konfiguriert ist, wird standardmäßig die Spalte **[!UICONTROL Dynamic Media]** angezeigt.
   * In einem Ordner, der für die Synchronisierung mit Dynamic Media konfiguriert ist, wird die Spalte &quot;Dynamic Media&quot;nicht angezeigt.**
      ![Listenansicht und Zeitleistensegment](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Fehlerbehebung bei der selektiven Veröffentlichung {#selective-publish-troubleshoot}

Bei Assets, die nicht mit Dynamic Media synchronisiert werden, bei denen jedoch eine Veröffentlichungsaktion für Dynamic Media ausgelöst wird, kommt es zu folgender Fehlermeldung und Lösung:

![Fehler bei der selektiven Veröffentlichung](/help/assets/assets-dm/selective-publish-error.png)
