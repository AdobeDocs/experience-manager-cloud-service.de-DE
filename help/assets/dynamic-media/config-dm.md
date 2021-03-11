---
title: Konfigurieren von Dynamic Media Cloud Service
description: Informationen zum Konfigurieren von Dynamic Media in Adobe Experience Manager as a Cloud Service.
translation-type: tm+mt
source-git-commit: a8eb6a88b889facca8518c05a80051fc17dd0617
workflow-type: tm+mt
source-wordcount: '3883'
ht-degree: 64%

---


# Wissenswertes über Dynamic Media Cloud Service {#configuring-dynamic-media}

Wenn Sie Adobe Experience Manager für verschiedene Umgebung wie Entwicklung, Staging und Live-Produktion verwenden, konfigurieren Sie Dynamic Media-Cloud Services für jede dieser Umgebung.

## Architekturgrafik von Dynamic Media {#architecture-diagram-of-dynamic-media}

Die folgende Architekturgrafik beschreibt die Funktionsweise von Dynamic Media.

Mit der neuen Architektur ist Experience Manager für primäre Quellelemente und für die Synchronisierung mit Dynamic Media für die Verarbeitung und Veröffentlichung von Assets verantwortlich:

1. Wenn das Asset aus einer Primärquelle in AEM hochgeladen wurde, wird es in Dynamic Media repliziert. Ab diesem Punkt übernimmt Dynamic Media die gesamte Asset-Verarbeitung und Ausgabenerstellung, z. B. Videokodierung und dynamische Varianten eines Bilds.
1. Nachdem die Ausgaben erstellt wurden, kann AEM sicher auf die Dynamic Media-Remote-Ausgabedarstellungen zugreifen und eine Vorschau dafür anzeigen (es werden keine Binärdateien an die AEM-Instanz zurückgesendet).
1. Nachdem die Inhalte veröffentlicht und genehmigt werden können, wird der Dynamic Media-Dienst Trigger, Inhalte an die Versand-Server zu übertragen und Inhalte im CDN zu zwischenspeichern.

![chlimage_1-550](assets/chlimage_1-550.png)

>[!NOTE]
>
>Für die folgende Liste von Funktionen müssen Sie das im Lieferumfang von Adobe Experience Manager - Dynamic Media enthaltene Out-of-the-Box-CDN verwenden. Andere benutzerdefinierte CDN werden von diesen Funktionen nicht unterstützt.
>
>* [Intelligente Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md)
>* [Cache-Ungültigmachung](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
>* [Hotlink-Schutz](/help/assets/dynamic-media/hotlink-protection.md)
>* [Bereitstellung von Inhalten per HTTP/2](/help/assets/dynamic-media/http2faq.md)
>* URL-Umleitung auf CDN-Ebene
>* Akamai ChinaCDN (für optimalen Versand in China)


<!-- OBSOLETE CONTENT

## (Optional) Migrating Dynamic Media presets and configurations from 6.3 to 6.5 Zero Downtime {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

If you are upgrading AEM Dynamic Media from 6.3 to 6.4 or 6.5 (which now includes the ability for zero downtime deployments), you are required to run the following curl command to migrate all your presets and configurations from `/etc` to `/conf` in CRXDE Lite.

>[!NOTE]
>
>If you run your AEM instance in compatibility mode--that is, you have the compatibility packaged installed--you do not need to run these commands.

For all upgrades, either with or without the compatibility package, you can copy the default, out-of-the-box viewer presets that originally came with Dynamic Media by running the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets/viewer.pushviewerpresets.json`

To migrate any custom viewer presets and configurations that you have created from `/etc` to `/conf`, run the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets.migratedmcontent.json`

-->

## Erstellen einer Dynamic Media-Konfiguration in Cloud Services {#configuring-dynamic-media-cloud-services}

<!-- **Before you creating a Dynamic Media Configuration in Cloud Services**: After you receive your provisioning email with Dynamic Media credentials, you must open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account to change your password. The password provided in the provisioning email is system-generated and intended to be a temporary password only. It is important that you update the password so that Dynamic Media Cloud Service is set up with the correct credentials. -->

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen.
1. Tippen Sie auf der linken Seite der Konsole auf das Symbol Tools und dann auf **[!UICONTROL Cloud Services > Dynamic Media Configuration]**.
1. Tippen Sie auf der Seite &quot;Dynamic Media Configuration Browser&quot;im linken Bereich auf **[!UICONTROL global]** (tippen Sie nicht auf das Ordnersymbol links neben **[!UICONTROL global]**). Tippen Sie dann auf **[!UICONTROL Erstellen]**.
1. Geben Sie auf der Seite **[!UICONTROL Dynamic Media-Konfiguration erstellen]** einen Titel, die E-Mail-Adresse des Dynamic Media-Kontos und ein Kennwort ein und wählen Sie Ihre Region aus. Diese Informationen werden Ihnen per Adobe in der Bereitstellungs-E-Mail bereitgestellt. Wenden Sie sich an den Kundendienst der Adobe, wenn Sie diese E-Mail nicht erhalten haben.
1. Klicken Sie auf **[!UICONTROL Mit Dynamic Media verbinden]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Kennwort ändern]** im Feld **[!UICONTROL Neues Kennwort]** ein neues Kennwort ein, das aus 8-25 Zeichen besteht. Das Kennwort muss je mindestens eines der folgenden Elemente enthalten:

   * Großbuchstabe
   * Kleinbuchstabe
   * Zahl
   * Sonderzeichen: `# $ & . - _ : { }`

   Das Feld **[!UICONTROL Aktuelles Kennwort]** ist absichtlich vorausgefüllt und wird von Interaktionen ausgeblendet.

   Bei Bedarf können Sie die Schreibweise eines von Ihnen eingegebenen oder erneut eingegebenen Kennworts überprüfen, indem Sie auf das Augensymbol tippen, um das Kennwort anzuzeigen. Tippen Sie erneut auf das Symbol, um das Kennwort auszublenden.

1. Geben Sie im Feld **[!UICONTROL Kennwort wiederholen]** das neue Kennwort erneut ein und tippen Sie dann auf **[!UICONTROL Fertig]**.

   Das neue Kennwort wird gespeichert, wenn Sie auf **[!UICONTROL Speichern]** oben rechts auf der Seite **[!UICONTROL Dynamic Media-Konfiguration erstellen]** tippen.

   Wenn Sie im Dialogfeld **[!UICONTROL Kennwort ändern]** auf **[!UICONTROL Abbrechen]** tippen, müssen Sie beim Speichern der neu erstellten Dynamic Media-Konfiguration trotzdem ein neues Kennwort eingeben.

   Weitere Informationen finden Sie unter [Ändern des Kennworts für Dynamic Media](#change-dm-password).

1. Nachdem die Verbindung erfolgreich hergestellt wurde, können Sie Folgendes einrichten:

   | Eigenschaft | Beschreibung |
   |---|---|
   | Unternehmen | Der Name des Dynamic Media-Kontos. Es ist möglich, dass Sie über mehrere Dynamic Media-Konten für verschiedene Untermarken, Geschäftsbereiche oder Staging-/Produktions-Umgebung verfügen. |
   | Pfad zum Stammordner des Unternehmens | Pfad zum Stammordner Ihres Unternehmens. |
   | Veröffentlichen von Assets | Sie können aus den folgenden drei Optionen auswählen:<br>**[!UICONTROL Sofort ]**: Wenn Assets hochgeladen werden, nimmt das System die Assets auf und stellt die URL/den Link zur Einbettung sofort bereit. Zum Veröffentlichen von Assets ist kein Benutzereingriff erforderlich.<br>**[!UICONTROL Bei Aktivierung]**: Sie müssen das Asset explizit zuerst veröffentlichen, bevor ein URL-/Einbettungslink bereitgestellt wird.<br>**[!UICONTROL Selektive Veröffentlichung ]**: Assets werden nur zur sicheren Vorschau automatisch veröffentlicht. Sie können auch explizit auf AEM veröffentlicht werden, ohne sie für den Versand in der öffentlichen Domäne in DMS7 zu veröffentlichen. Bei dieser Option wird in Zukunft beabsichtigt, Assets zu veröffentlichen, um sie in Dynamic Media zu AEM und zu veröffentlichen, wobei sich die Elemente gegenseitig ausschließen. Das heißt, Sie können Assets in DMS7 veröffentlichen, damit Sie Funktionen wie smartes Zuschneiden oder dynamische Ausgabedarstellungen verwenden können. Oder Sie können Assets ausschließlich in AEM zur Vorschau veröffentlichen. Diese Assets werden nicht in DMS7 veröffentlicht, um sie öffentlich zugänglich zu machen. |
   | Sicherer Vorschau-Server | Damit haben Sie die Möglichkeit, den URL-Pfad zu Ihrem Vorschau-Server für sichere Ausgabedarstellungen anzugeben. Das heißt, dass AEM sicher auf die Dynamic Media-Remote-Ausgabedarstellungen zugreifen und eine Vorschau dafür anzeigen kann, nachdem die Ausgabedarstellungen erstellt wurden (es werden keine Binärdateien an die AEM-Instanz zurückgesendet).<br>Wenn Sie keine spezielle Vereinbarung zur Verwendung des Servers Ihrer eigenen Firma oder eines Spezialservers haben, empfiehlt Adobe, diese Einstellung wie angegeben zu belassen. |
   | Alle Inhalte synchronisieren | Standardmäßig ausgewählt. Deaktivieren Sie diese Option, wenn Sie Assets aus der Synchronisierung mit Dynamic Media gezielt ein- oder ausschließen möchten. Wenn Sie diese Option deaktivieren, können Sie aus den beiden folgenden Synchronisierungsmodi für Dynamic Media wählen:<br>**[!UICONTROL Synchronisierungsmodus für Dynamic Media]**<br>**[!UICONTROL Standardmäßig aktiviert ]**: Die Konfiguration wird auf alle Ordner angewendet, es sei denn, Sie markieren einen Ordner speziell zum Ausschließen. <!-- you can then deselect the folders that you do not want the configuration applied to.--><br>**[!UICONTROL Standardmäßig deaktiviert]**: Die Konfiguration wird auf einen Ordner erst dann angewendet, wenn Sie einen ausgewählten Ordner explizit zur Synchronisierung mit Dynamic Media markieren.<br>Um einen ausgewählten Ordner zur Synchronisierung mit Dynamic Media zu markieren, wählen Sie einen Asset-Ordner aus und klicken Sie dann in der Symbolleiste auf  **[!UICONTROL Eigenschaften]**. Wählen Sie auf der Registerkarte **[!UICONTROL Details]** in der Dropdown-Liste **[!UICONTROL Synchronisierungsmodus für Dynamic Media]** eine der folgenden drei Optionen aus. Wenn Sie fertig sind, tippen Sie auf **[!UICONTROL Speichern]**. *Denken Sie daran: Diese drei Optionen stehen nicht zur Verfügung, wenn Sie zuvor **Alle Inhalte synchronisieren**ausgewählt haben.* Weitere Informationen finden Sie unter [Arbeiten mit selektiver Veröffentlichung auf Ordnerebene in Dynamic Media.](/help/assets/dynamic-media/selective-publishing.md)<br>**[!UICONTROL Vererbt ]**: Kein expliziter Synchronisierungswert im Ordner. Stattdessen übernimmt der Ordner den Synchronisierungswert von einem seiner Vorgängerordner oder den Standardmodus in der Cloud-Konfiguration. Der detaillierte Status für geerbte Inhalte wird als QuickInfo angezeigt.<br>**[!UICONTROL Für Unterordner]** aktivieren: Schließen Sie alle Elemente in dieser Unterstruktur für die Synchronisierung mit Dynamic Media ein. Die ordnerspezifischen Einstellungen setzen den Standardmodus in der Cloud-Konfiguration außer Kraft.<br>**[!UICONTROL Deaktiviert für Unterordner ]**: Schließen Sie alle Elemente in diesem Unterbaum von der Synchronisierung mit Dynamic Media aus. |

   >[!NOTE]
   >
   >Die Versionierung wird in Dynamic Media nicht unterstützt. Eine verzögerte Aktivierung gilt nur, wenn auf der Seite &quot;Dynamic Media-Konfiguration bearbeiten&quot;auf **[!UICONTROL Bei Aktivierung]** die Option &quot;Assets veröffentlichen ]**&quot;eingestellt ist. Und dann erst, wenn das Asset zum ersten Mal aktiviert wurde.**[!UICONTROL 
   >
   >
   >Wenn ein Asset aktiviert wurde, werden alle Aktualisierungen automatisch live in der S7-Bereitstellung übernommen.

   ![dynamicmediaconfiguration2updated](/help/assets/assets-dm/dynamicmediaconfigurationupdated.png)

1. Tippen Sie auf **[!UICONTROL Speichern]**. Das neue Kennwort und die Konfiguration für Dynamic Media werden gespeichert. Wenn Sie stattdessen auf **[!UICONTROL Abbrechen]** tippen, wird das Kennwort nicht aktualisiert.
1. Tippen Sie im Dialogfeld **[!UICONTROL Konfigurieren von Dynamic Media]** auf **[!UICONTROL OK]**, um die Konfiguration zu starten.

   >[!IMPORTANT]
   >
   >Wenn die neue Dynamic Media-Konfiguration abgeschlossen ist, erhalten Sie eine Statusbenachrichtigung in AEM Posteingang.
   >
   >Diese Benachrichtigung im Posteingang informiert Sie darüber, ob die Konfiguration erfolgreich war oder nicht.
   > Weitere Informationen finden Sie unter [Fehlerbehebung bei einer neuen Dynamic Media-Konfiguration](#troubleshoot-dm-config) und [Ihr Posteingang](/help/sites-cloud/authoring/getting-started/inbox.md).

1. Damit Dynamic Media-Inhalte vor der Veröffentlichung sicher Vorschau werden können, müssen Sie die AEM Autoreninstanz mit &quot;neu&quot;verknüpfen, um eine Verbindung mit Dynamic Media herzustellen. Gehen Sie wie folgt vor, um diese Aktion einzurichten:

   * Öffnen Sie die Desktopanwendung [Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich dann bei Ihrem Konto an. Ihre Anmeldeinformationen und Anmeldedaten wurden von der Adobe zum Zeitpunkt der Bereitstellung bereitgestellt. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.
   * Klicken Sie in der Navigationsleiste oben rechts auf der Seite auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinstellungen > Image-Server]**.

   * Wählen Sie auf der Seite „Veröffentlichung zum Image-Server“ in der Dropdown-Liste „Veröffentlichungskontext“ die Option **[!UICONTROL Image-Serving testen]**.
   * Tippen Sie für den Client-Adressfilter auf **[!UICONTROL Hinzufügen]**.
   * Um die Adresse zu aktivieren (einschalten), aktivieren Sie das Kontrollkästchen und geben Sie dann die IP-Adresse der AEM-Autoreninstanz (nicht Dispatcher-IP) ein.
   * Klicken Sie auf **[!UICONTROL Speichern]**.

Sie haben nun die Grundkonfiguration abgeschlossen und können Dynamic Media verwenden.

Wenn Sie Ihre Konfiguration weiter anpassen möchten, können Sie auch eine der Aufgaben unter [Konfigurieren der erweiterten Einstellungen in Dynamic Media](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode) durchführen.

### Fehlerbehebung bei einer neuen Dynamic Media-Konfiguration {#troubleshoot-dm-config}

Wenn eine neue Dynamic Media-Konfiguration abgeschlossen ist, erhalten Sie eine Statusbenachrichtigung in AEM Posteingang. Diese Benachrichtigung informiert Sie darüber, ob die Konfiguration erfolgreich war oder nicht, wie in den folgenden Bildern aus dem Posteingang dargestellt.

![Experience Manager-Posteingangserfolg](/help/assets/dynamic-media/assets/dmconfig-inbox-success.png)

![Experience Manager-Posteingang fehlgeschlagen](/help/assets/dynamic-media/assets/dmconfig-inbox-failure.png)

Weitere Informationen finden Sie unter [Ihr Posteingang](/help/sites-cloud/authoring/getting-started/inbox.md).

**Fehlerbehebung bei einer neuen Dynamic Media-Konfiguration**

1. Tippen Sie oben rechts auf der AEM-Seite auf das Glockensymbol und dann auf **[!UICONTROL Alle anzeigen]**.
1. Tippen Sie auf der Seite „Posteingang“ auf die Erfolgsbenachrichtigung, um einen Überblick über den Status und die Protokolle der Konfiguration zu erhalten.

   Wenn die Konfiguration fehlschlug, tippen Sie auf die Fehlerbenachrichtigung ähnlich dem folgenden Screenshot.

   ![Dynamic Media-Setup fehlgeschlagen](/help/assets/dynamic-media/assets/dmconfig-fail-notification.png)

1. Überprüfen Sie auf der Seite **[!UICONTROL DMSETUP]** die Konfigurationsdetails, die den Fehler beschreiben. Beachten Sie insbesondere alle Fehlermeldungen oder Fehler-Codes. Wenden Sie sich mit diesen Informationen an die Kundenunterstützung der Adobe.

   ![Seite &quot;Dynamic Media einrichten&quot;](/help/assets/dynamic-media/assets/dmconfig-fail-page.png)

### Ändern des Kennworts für Dynamic Media {#change-dm-password}

Das Ablaufdatum des Kennworts wird in Dynamic Media auf 100 Jahre ab dem aktuellen Systemdatum gesetzt.

Das Kennwort muss je mindestens eines der folgenden Elemente enthalten:

* Großbuchstabe
* Kleinbuchstabe
* Zahl
* Sonderzeichen: `# $ & . - _ : { }`

Bei Bedarf können Sie die Schreibweise eines von Ihnen eingegebenen oder erneut eingegebenen Kennworts überprüfen, indem Sie auf das Augensymbol tippen, um das Kennwort anzuzeigen. Tippen Sie erneut auf das Symbol, um das Kennwort auszublenden.

Das geänderte Kennwort wird gespeichert, wenn Sie auf **[!UICONTROL Speichern]** oben rechts auf der Seite **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** tippen.

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen.
1. Tippen Sie auf der linken Konsolenkonsole auf das Symbol Tools und dann auf **[!UICONTROL Cloud Services > Dynamic Media Configuration.]**
1. Tippen Sie auf der Seite &quot;Dynamic Media Configuration Browser&quot;im linken Bereich auf **[!UICONTROL global]**. Tippen oder wählen Sie nicht das Ordnersymbol links neben **[!UICONTROL global]**. Tippen Sie dann auf **[!UICONTROL Bearbeiten.]**
1. Tippen Sie auf der Seite **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** direkt unter dem Feld **[!UICONTROL Kennwort]** auf **[!UICONTROL Kennwort ändern]**.
1. Gehen Sie im Dialogfeld **[!UICONTROL Kennwort ändern]** wie folgt vor:

   * Geben Sie im Feld **[!UICONTROL Neues Kennwort]** ein neues Kennwort ein.

      Das Feld **[!UICONTROL Aktuelles Kennwort]** ist absichtlich vorausgefüllt und wird von Interaktionen ausgeblendet.

   * Geben Sie im Feld **[!UICONTROL Kennwort wiederholen]** das neue Kennwort erneut ein und tippen Sie dann auf **[!UICONTROL Fertig]**.

1. Tippen Sie oben rechts auf der Seite **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL OK]**.

## (Optional) Konfigurieren der erweiterten Einstellungen in Dynamic Media {#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Um die Konfiguration und Einrichtung von Dynamic Media weiter anzupassen oder die Leistung zu optimieren, können Sie eine oder mehrere der folgenden *optionalen*-Aufgaben ausführen:

* [Einrichtung und Konfiguration der Einstellungen von Dynamic Media](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(Optional) Steigern der Leistung von Dynamic Media](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

### (Optional) Einrichtung und Konfiguration der Einstellungen von Dynamic Media {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings}

Verwenden Sie die Benutzeroberfläche von Dynamic Media Classic, um Ihre Dynamic Media-Einstellungen zu ändern.

Bei einigen der oben genannten Aufgaben müssen Sie die Desktopanwendung [Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) öffnen und sich dann bei Ihrem Konto anmelden.

Die Einrichtungs- und Konfigurationsaufgaben umfassen Folgendes:

* [Veröffentlichungseinstellungen für Image-Server](#publishing-setup-for-image-server)
* [Konfigurieren der allgemeinen Programmeinstellungen](#configuring-application-general-settings)
* [Konfigurieren des Farb-Managements](#configuring-color-management)
* [Bearbeiten von MIME-Typen für unterstützte Formate](#editing-mime-types-for-supported-formats)
* [Hinzufügen von MIME-Typen für nicht unterstützte Formate](#adding-mime-types-for-unsupported-formats)

<!-- * [Creating batch set presets to auto-generate Image Sets and Spin Sets](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) -->

#### Veröffentlichungseinstellungen für Image-Server  {#publishing-setup-for-image-server}

Mit den Veröffentlichungseinstellungen wird festgelegt, wie Assets standardmäßig von Dynamic Media bereitgestellt werden. Wenn keine Einstellung festgelegt wird, stellt Dynamic Media ein Asset gemäß den Standardeinstellungen unter „Veröffentlichungseinstellungen“ bereit. Beispiel: Bei der Anfrage, ein Bild bereitzustellen, das kein Auflösungsattribut enthält, wird ein Bild mit der Einstellung „Standardobjektauflösung“ bereitgestellt.

So konfigurieren Sie Veröffentlichungseinstellungen: Klicken Sie in Dynamic Media Classic auf **[!UICONTROL Einrichtung > Anwendungseinstellungen > Veröffentlichungseinstellungen > Image-Server]**.

Auf dem Bildschirm „Image-Server“ werden Standardeinstellungen für das Bereitstellen von Bildern festgelegt. Auf dem Bildschirm der Benutzeroberfläche finden Sie die Beschreibungen der einzelnen Einstellungen.

**[!UICONTROL Anfrage-Attribute]**: Mit diesen Einstellungen werden Einschränkungen für die Bilder festgelegt, die über den Server bereitgestellt werden können.
**[!UICONTROL Standardattribute für Anfragen]**: Diese Einstellungen beziehen sich auf die standardmäßige Darstellung von Bildern.
**[!UICONTROL Allgemeine Attribute für Miniaturansichten]**: Diese Einstellungen beziehen sich auf die standardmäßige Darstellung von Miniaturbildern.
**[!UICONTROL Standardeinstellungen für Katalogfelder]**: Diese Einstellungen beziehen sich auf die Auflösung und den Standardtyp für Miniaturansichten von Bildern.
**[!UICONTROL Farbverwaltungsattribute]**: Mit diesen Einstellungen wird festgelegt, welche ICC-Farbprofile verwendet werden.
**[!UICONTROL Kompatibilitätsattribute]**: Diese Einstellung ermöglicht die Behandlung von Anfangs- und Endabsätzen in Textebenen wie in Version 3.6, um die Abwärtskompatibilität zu gewährleisten.
**[!UICONTROL Lokalisierungsunterstützung]**: Mit diesen Einstellungen können mehrere Gebietsschemaattribute verwaltet werden. Außerdem kann damit eine Zeichenfolge der Gebietsschemakarte angegeben werden, damit Sie festlegen können, welche Sprachen für die verschiedenen QuickInfos in Viewern unterstützt werden sollen. Weitere Informationen zur Einrichtung der **[!UICONTROL Lokalisierungsunterstützung]** finden Sie unter [Überlegungen beim Einrichten der Lokalisierung von Assets](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/publish-setup.html#considerations-when-setting-up-localization-of-assets).

#### Konfigurieren der allgemeinen Programmeinstellungen {#configuring-application-general-settings}

Zum Öffnen der Seite „Allgemeine Programmeinstellungen“ über die globale Navigationsleiste in Dynamic Media Classic klicken Sie auf **[!UICONTROL Einrichtung > Anwendungseinstellungen > Allgemeine Einstelllungen]**.

**[!UICONTROL Server]**: Bei der Kontobereitstellung stellt Dynamic Media automatisch die zugeordneten Server für Ihr Unternehmen bereit. Diese Server werden verwendet, um URL-Zeichenfolgen für Ihre Website und Anwendungen zu erstellen. Diese URL-Aufrufe gelten spezifisch für Ihr Konto. Ändern Sie keine Server-Namen, sofern Sie nicht vom AEM-Support ausdrücklich dazu angewiesen werden.
**[!UICONTROL Bilder überschreiben]**: Dynamic Media lässt zwei Dateien mit denselben Namen nicht zu. Die URL-ID (Dateiname ohne Erweiterung) eines Elements muss jeweils eindeutig sein. Diese Optionen legen fest, wie Ersatz-Assets hochgeladen werden, d. h. ob sie das Original ersetzen oder doppelt vorhanden sind. Duplizierte Assets werden durch Anhängen von „-1“ umbenannt („chair.tif“ wird beispielsweise zu „chair-1.tif“). Diese Optionen wirken sich auf Assets aus, die in einen anderen Ordner hochgeladen wurden als das Original oder auf Assets mit einer anderen Dateierweiterung als das Original.
**[!UICONTROL Im aktuellen Ordner Bilder mit demselben Namen und derselben Erweiterung überschreiben]**: Diese Option stellt die strengste Ersetzungsregel dar. Es ist erforderlich, dass Sie das Ersatzbild in denselben Ordner wie das Original hochladen und dieselbe Dateierweiterung wie das Original haben. Wenn diese Voraussetzungen nicht erfüllt sind, wird ein Duplikat erstellt. Wählen Sie immer **[!UICONTROL Im aktuellen Ordner Bilder mit demselben Namen und derselben Erweiterung überschreiben]** aus, um die Konsistenz mit AEM sicherzustellen.
**[!UICONTROL In einem beliebigen Ordner überschreiben, Name/Erweiterung]**  des Basisassets - Erfordert, dass das Ersatzbild dieselbe Dateierweiterung wie das Originalbild hat. Beispielsweise muss &quot;Sessel.jpg&quot;die Datei &quot;Sessel.jpg&quot;ersetzen, nicht &quot;Sessel.tif&quot;. Sie können das Ersatzbild jedoch in einen anderen Ordner hochladen als den, in dem sich das Original befindet. Das hochgeladene Bild bleibt dann im neuen Ordner; die Datei befindet sich also nicht mehr am ursprünglichen Speicherort..
**[!UICONTROL In belieb. Ordner Assets mit ident. Namen unabh. von Erweit. überschreiben]**: Diese Option stellt die am wenigsten einschränkende Ersetzungsregel dar. Sie können ein Ersatzbild in einen anderen Ordner als das Originalbild hochladen, eine Datei mit einer anderen Dateierweiterung hochladen und die Originaldatei ersetzen. Wenn sich die Originaldatei in einem anderen Ordner befindet, bleibt das Ersatzbild in dem neuen Ordner, in den es hochgeladen wurde.
**[!UICONTROL Standardfarbprofile]**: Zusätzliche Informationen finden Sie unter [Konfigurieren des Farb-Managements](#configuring-color-management). Standardmäßig zeigt das System 15 Ausgabedarstellungen an, wenn Sie **[!UICONTROL Ausgabedarstellungen]** auswählen, und 15 Viewer-Voreinstellungen, wenn Sie in der Detailansicht des Assets **[!UICONTROL Viewer]** auswählen. Sie können diese Grenze erhöhen. Siehe [Erhöhen oder Verringern der Anzahl angezeigter Bildvorgaben](/help/assets/dynamic-media/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) oder [Erhöhen oder Verringern der Anzahl angezeigter Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

#### Konfigurieren des Farb-Managements {#configuring-color-management}

Mit dem Dynamic Media-Farbmanagement können Sie Assets farblich markieren. Bei der Farbkorrektur behalten übernommene Assets ihren Farbraum (RGB, CMYK, Grau) und das eingebettete Farbprofil bei. Wenn Sie eine dynamische Ausgabedarstellung anfordern, wird die Bildfarbe gemäß dem Zielfarbraum korrigiert, indem eine CMYK-, RGB- oder Grau-Ausgabe verwendet wird. Siehe [Konfigurieren von Bildvorgaben](/help/assets/dynamic-media/managing-image-presets.md).

So konfigurieren Sie die Standardfarbeigenschaften für die Aktivierung der Farbkorrektur beim Anfordern von Bildern:

1. Öffnen Sie die Desktopanwendung [Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich dann mit den Anmeldeinformationen an, die während der Bereitstellung bereitgestellt werden.
1. Navigieren Sie zu **[!UICONTROL Einrichtung > Anwendungseinstellungen]**.
1. Erweitern Sie den Bereich **[!UICONTROL Veröffentlichungseinstellungen]** und wählen Sie **[!UICONTROL Image-Server]**. Legen Sie **[!UICONTROL Veröffentlichungskontext]** beim Festlegen von Standardwerten für Veröffentlichungsinstanzen auf **[!UICONTROL Image Serving]** fest.
1. Blättern Sie zu der Eigenschaft, die Sie ändern müssen, z. B. zu einer Eigenschaft im Bereich **[!UICONTROL Farbmanagementattribute]**.
Sie können die folgenden Farbkorrektureigenschaften festlegen:

   | Eigenschaft | Beschreibung |
   |---|---|
   | CMYK-Standardfarbraum | Name des standardmäßigen CMYK-Farbprofils. |
   | Graustufen-Standardfarbraum | Name des standardmäßigen grauen Farbprofils. |
   | RGB-Standardfarbraum | Name des standardmäßigen RGB-Profils. |
   | Rendering-Absicht der Farbkonvertierung | Gibt die Rendering-Absicht an. Zulässige Werte sind: **[!UICONTROL wahrnehmungsorientiert]**, **[!UICONTROL relativ farbmetrisch]**, **[!UICONTROL Sättigung]**, **[!UICONTROL absolut farbmetrisch.]** Adobe empfiehlt **[!UICONTROL relativ]** als Standard. |

1. Tippen Sie auf **[!UICONTROL Speichern]**.

So können Sie beispielsweise den **[!UICONTROL RGB-Standardfarbraum]** auf *sRGB* und den **[!UICONTROL CMYK-Standardfarbraum]** auf *WebCoated* festlegen.

Dies hat folgende Auswirkungen:

* Die Farbkorrektur für RGB- und CMYK-Bilder wird aktiviert.
* RGB-Profile, die kein Farbbild aufweisen, werden als im Farbraum *sRGB* angezeigt.
* CMYK-Profile ohne Farbraum werden als Farbraum *WebCoated* angenommen.
* Dynamische Darstellungen, die die RGB-Ausgabe zurückgeben, geben sie im Farbraum *sRGB* zurück.
* Dynamische Darstellungen, die CMYK-Ausgabe zurückgeben, geben sie im Farbraum *WebCoated* zurück.

#### Bearbeiten von MIME-Typen für unterstützte Formate {#editing-mime-types-for-supported-formats}

Sie können festlegen, welche Asset-Typen von Dynamic Media verarbeitet werden, und erweiterte Asset-Verarbeitungsparameter anpassen. Beispielsweise können Sie Asset-Verarbeitungsparameter für folgende Aktionen festlegen:

* Konvertieren eines Adobe PDF-Dokuments in ein E-Katalog-Asset
* Konvertieren eines Adobe Photoshop-Dokuments (.PSD) in ein Bannervorlagen-Asset für Personalisierung
* Rastern Sie eine Adobe Illustrator-Datei (.AI) oder eine Adobe Photoshop Encapsulated PostScript® file (.EPS).
* [Videoprofile](/help/assets/dynamic-media/video-profiles.md) und [Bilddarstellungsprofile](/help/assets/dynamic-media/image-profiles.md) können jeweils zum Definieren der Verarbeitung von Videos und Bildern verwendet werden.

Informationen hierzu finden Sie unter [Hochladen von Assets](/help/assets/add-assets.md).

**So bearbeiten Sie die MIME-Typen für unterstützte Formate**

1. Klicken Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Allgemein > CRXDE Lite]**.
1. Navigieren Sie in der linken Leiste zu:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![MIME-Typen](assets/mimetypes.png)

1. Wählen Sie unter dem Ordner mimeTypes einen MIME-Typ aus.
1. Im rechten unteren Bereich der Seite „CRXDE Lite“:

   * Doppelklicken Sie auf das Feld **[!UICONTROL Aktiviert]**. Standardmäßig sind alle Asset-MIME-Typen aktiviert (auf **[!UICONTROL true]** eingestellt). Das bedeutet, dass die Assets zur Verarbeitung mit Dynamic Media synchronisiert werden. Wenn Sie diesen Asset-MIME-Typ von der Verarbeitung ausschließen möchten, ändern Sie diese Einstellung in **[!UICONTROL false]**.

   * Doppelklicken Sie auf **[!UICONTROL jobParam]**, um das zugehörige Textfeld zu öffnen. Eine Liste der zulässigen Verarbeitungsparameter, die Sie für einen bestimmten MIME-Typ verwenden können, finden Sie unter [Unterstützte MIME-Typen](/help/assets/file-format-support.md).

1. Führen Sie einen der folgenden Schritte aus:
   * Wiederholen Sie die Schritte 3-4, um weitere MIME-Typen zu bearbeiten.
   * Klicken Sie auf der Menüleiste der Seite „CRXDE Lite“ auf **[!UICONTROL Alle speichern]**.

1. Tippen Sie links oben auf der Seite auf **[!UICONTROL CRXDE Lite]**, um zu AEM zurückzukehren.

#### Hinzufügen von MIME-Typen für nicht unterstützte Formate {#adding-mime-types-for-unsupported-formats}

Sie können benutzerdefinierte MIME-Typen für nicht unterstützte Formate in Experience Manager Assets hinzufügen. Um sicherzustellen, dass ein neuer Knoten, den Sie in CRXDE Lite hinzufügen, nicht von Experience Manager gelöscht wird, verschieben Sie den MIME-Typ vor `image_`. Stellen Sie außerdem sicher, dass der aktivierte Wert auf **[!UICONTROL false]** eingestellt ist.

**So fügen Sie MIME-Typen für nicht unterstützte Formate hinzu**

1. Tippen Sie in AEM auf **[!UICONTROL Tools > Vorgänge > Web-Konsole]**.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. Auf der Seite **[!UICONTROL Adobe Experience Manager-Web-Konsolen-Konfiguration]** wird eine neue Browser-Registerkarte geöffnet.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. Scrollen Sie auf der Seite nach unten zum Namen *Adobe CQ Scene7 Asset MIME type Service*, wie im folgenden Screenshot gezeigt. Tippen Sie rechts neben dem Namen auf die Option **[!UICONTROL Konfigurationswerte bearbeiten]** (Stiftsymbol).

   ![2019-08-02_16-44-56](assets/2019-08-02_16-44-56.png)

1. Klicken Sie auf der Seite **Adobe CQ Scene7 Asset MIME type Service** auf ein beliebiges Pluszeichen &lt;+>. Die Position in der Tabelle, an der Sie auf das Pluszeichen klicken, um den neuen MIME-Typ hinzuzufügen, ist trivial.

   ![2019-08-02_16-27-27](assets/2019-08-02_16-27-27.png)

1. Geben Sie `DWG=image/vnd.dwg` in das leere Textfeld ein, das Sie soeben hinzugefügt haben.

   Das Beispiel `DWG=image/vnd.dwg` dient nur zur Veranschaulichung. Der hier hinzugefügte MIME-Typ kann ein beliebiges anderes nicht unterstütztes Format sein.

   ![2019-08-02_16-36-36](assets/2019-08-02_16-36-36.png)

1. Tippen Sie unten rechts auf der Seite auf **[!UICONTROL Speichern]**.

   An dieser Stelle können Sie die Registerkarte des Browsers schließen, auf der die Seite „Adobe Experience Manager-Web-Konsolen-Konfiguration“ geöffnet ist.

1. Kehren Sie zur Browser-Registerkarte zurück, in der sich Ihre geöffnete AEM-Konsole befindet.
1. Tippen Sie in AEM auf **[!UICONTROL Tools > Allgemein > CRXDE Lite]**.

   ![2019-08-02_16-55-41](assets/2019-08-02_16-55-41.png)

1. Navigieren Sie in der linken Leiste zu:

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Ziehen Sie den MIME-Typ `image_vnd.dwg` und legen Sie ihn direkt über `image_` in die Struktur, wie im folgenden Screenshot gezeigt.

   ![crxdelite_cqdoc-14627](assets/crxdelite_cqdoc-14627.png)

1. Wenn der MIME-Typ `image_vnd.dwg` noch ausgewählt ist, klicken Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** in der Zeile **[!UICONTROL enabled]** unter der Spaltenüberschrift **[!UICONTROL value]** auf den Wert. Klicken Sie dann bei Dublette auf den Wert. Die Dropdown-Liste **[!UICONTROL Value]** wird geöffnet.
1. Geben Sie `false` in das Feld ein (oder wählen Sie **[!UICONTROL false]** aus der Dropdown-Liste).

   ![2019-08-02_16-60-30](assets/2019-08-02_16-60-30.png)

1. Klicken Sie in der oberen linken Ecke der Seite „CRXDE Lite“ auf **[!UICONTROL Alle speichern]**.



### (Optional) Steigern der Leistung von Dynamic Media {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Für die reibungslose Ausführung von Dynamic Media mit dem Ausführungsmodus <!--(with `dynamicmedia_scene7` run mode)--> empfiehlt Adobe die folgenden Maßnahmen zur Optimierung der Synchronisierungsleistung/-skalierbarkeit:

* Aktualisieren der vordefinierten Auftragsparameter zur Verarbeitung verschiedener Dateiformate.
* Aktualisieren der vordefinierten Warteschlangen-Workerthreads des Granite-Workflows (Video-Assets).
* Aktualisieren der vordefinierten Warteschlangen-Workerthreads des Granite-Verlaufs-Workflows (Bilder und Nicht-Video-Assets).
* Aktualisieren der maximalen Upload-Verbindungen mit dem Dynamic Media Classic-Server.

#### Aktualisieren der vordefinierten Auftragsparameter zur Verarbeitung verschiedener Dateiformate.

Beim Hochladen von Dateien können Sie die Auftragsparameter für eine schnellere Verarbeitung anpassen. Wenn Sie beispielsweise PSD-Dateien hochladen, diese jedoch nicht als Vorlagen verarbeiten möchten, können Sie die Ebenenextraktion auf „false“ (falsch/aus) setzen. In diesem Fall würden die angepassten Auftragsparameter als `process=None&createTemplate=false` angezeigt.

Adobe empfiehlt die Verwendung der folgenden &quot;angepassten&quot;Auftragsparameter für PDF-, PostScript®- und PSD-Dateien:

| Dateityp | Empfohlene Auftragsparameter |
| ---| ---|
| PDF | `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=Layername&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- To update any of these parameters, follow the steps in [Enabling MIME type-based Assets/Dynamic Media Classic upload job parameter support](#enabling-mime-type-based-assets-scene-upload-job-parameter-support). -->

#### Aktualisieren der Verlaufs-Workflow-Warteschlange von Granite {#updating-the-granite-transient-workflow-queue}

Die Transit-Workflow-Warteschlange von Granite wird für den Workflow **[!UICONTROL DAM-Update-Asset]** verwendet. In Dynamic Media wird sie für die Bildaufnahme und -verarbeitung genutzt.

**So aktualisieren Sie die Verlaufs-Workflow-Warteschlange von Granite**

1. Navigieren Sie zu [https://&lt;Server>/system/console/configMgr](https://localhost:4502/system/console/configMgr) und suchen Sie nach **Warteschlange: Warteschlange für die Granite-Übergangs-Workflows**.

   >[!NOTE]
   >
   >Anstelle einer direkten URL ist eine Textsuche erforderlich, da die OSGi-PID dynamisch generiert wird.

1. Ändern Sie im Feld **[!UICONTROL Maximale Anzahl an parallelen Aufträgen]** die Zahl in den gewünschten Wert.

   Sie können **[!UICONTROL Maximale Anzahl an parallelen Aufträgen]** erhöhen, um das Hochladen von Dateien zu Dynamic Media angemessen zu unterstützen. Der genaue Wert hängt von der Hardwarekapazität ab. In bestimmten Szenarien, z. B. einer ersten Migration oder einem einmaligen Massen-Upload, können Sie einen großen Wert verwenden. Beachten Sie jedoch, dass die Verwendung eines hohen Werts (z. B. die zweifache Anzahl der Kerne) negative Auswirkungen auf andere gleichzeitige Aktivitäten haben kann. Testen Sie daher den Wert und passen Sie ihn je nach Anwendungsfall an.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Tippen Sie auf **[!UICONTROL Speichern]**.

#### Aktualisieren der Granite-Workflow-Warteschlange {#updating-the-granite-workflow-queue}

Die Granite-Workflow-Warteschlange wird für Workflows ohne Verlauf verwendet. In Dynamic Media wurden Videos mit dem Arbeitsablauf **[!UICONTROL Dynamic Media Encode Video]** verarbeitet.

So aktualisieren Sie die Granite-Workflow-Warteschlange:

1. Navigieren Sie zu `https://<server>/system/console/configMgr` und suchen Sie nach **Warteschlange: Granite-Workflow-Warteschlange**.

   >[!NOTE]
   >
   >Anstelle einer direkten URL ist eine Textsuche erforderlich, da die OSGi-PID dynamisch generiert wird.

1. Ändern Sie im Feld **[!UICONTROL Maximale Anzahl an parallelen Aufträgen]** die Zahl in den gewünschten Wert.

   Die maximale Anzahl der parallelen Aufträge hängt standardmäßig von der Anzahl der verfügbaren CPU-Kerne ab. Auf einem 4-Core-Server werden beispielsweise zwei Arbeitsthreads zugewiesen. (Ein Wert zwischen 0,0 und 1,0 basiert auf einem Quotienten oder eine Zahl größer als 1 weist die Anzahl der Arbeitsthreads zu.)

   In den meisten Fällen ist die Standardeinstellung 0,5 ausreichend.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Tippen Sie auf **[!UICONTROL Speichern]**.

#### Aktualisieren der Scene7-Upload-Verbindung {#updating-the-scene-upload-connection}

Die Einstellung &quot;Scene7 Upload Connection&quot;synchronisiert Experience Manager-Assets mit Dynamic Media Classic-Servern.

So aktualisieren Sie die Scene7-Upload-Verbindung:

1. Navigieren Sie zu `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. Ändern Sie die Anzahl im Feld **[!UICONTROL Anzahl der Verbindungen]** oder im Feld **[!UICONTROL Aktives Auftragstimeout]** oder beide nach Bedarf.

   Die Einstellung **[!UICONTROL Anzahl der Verbindungen]** steuert die maximale Anzahl der HTTP-Verbindungen, die für den Experience Manager zum Dynamic Media-Upload zulässig sind. In der Regel ist der vordefinierte Wert von zehn Verbindungen ausreichend.

   Die Einstellung **[!UICONTROL Zeitüberschreitung bei aktiven Aufträgen]** legt die Wartezeit für hochgeladene Dynamic Media-Assets bis zur Veröffentlichung auf dem Übermittlungs-Server fest. Dieser Wert beträgt standardmäßig 2.100 Sekunden oder 35 Minuten.

   In den meisten Fällen ist die Einstellung „2100“ausreichend.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Tippen Sie auf **[!UICONTROL Speichern]**.

<!-- NOTE - OBSOLETE that customisations to replication agents to transform content are no longer used; the following content is obsolete now 

### (Optional) Filtering assets for replication {#optional-filtering-assets-for-replication}

In non-Dynamic Media deployments, you replicate *all* assets (both images and video) from your AEM author environment to the AEM publish node. This workflow is necessary because the AEM publish servers also deliver the assets.

However, in Dynamic Media deployments, because assets are delivered by way of the cloud service, there is no need to replicate those same assets to AEM publish nodes. Such a "hybrid publishing" workflow avoids extra storage costs and longer processing times to replicate assets. Other content, such as Site pages, continue to be served from the AEM publish nodes.

The filters provide a way for you to *exclude* assets from being replicated to the AEM publish node.

#### Using default asset filters for replication {#using-default-asset-filters-for-replication}

If you are using Dynamic Media for imaging and/or video, then you can use the default filters that we provide as-is. The following filters are active by default:

<table>
 <tbody>
  <tr>
   <td> </td>
   <td><strong>Filter</strong></td>
   <td><strong>Mimetype</strong></td>
   <td><strong>Renditions</strong></td>
  </tr>
  <tr>
   <td>Dynamic Media Image Delivery</td>
   <td><p>filter-images</p> <p>filter-sets</p> <p> </p> </td>
   <td><p>Starts with <strong>image/</strong></p> <p>Contains <strong>application/</strong> and ends with <strong>set</strong>.</p> </td>
   <td>The out-of-the-box "filter-images" (applies to single images assets, including interactive images) and "filter-sets" (applies to Spin Sets, Image Sets, Mixed Media Sets, and Carousel Sets) will:
    <ul>
     <li>Exclude from replication the original image and static image renditions.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Dynamic Media Video Delivery</td>
   <td>filter-video</td>
   <td>Starts with <strong>video/</strong></td>
   <td>The out-of-the-box "filter-video" will:
    <ul>
     <li>Exclude from replication the original video and static thumbnail renditions.<br /> <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Filters apply to mime types and cannot be path specific.

#### Customizing asset filters for replication {#customizing-asset-filters-for-replication}

1. In AEM, tap the AEM logo to access the global navigation console and tap the **[!UICONTROL Tools > General > CRXDE Lite]**.
1. In the left folder tree, navigate to `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` to review the filters.

   ![chlimage_1-17](assets/chlimage_1-2.png)

1. To define the Mime Type for the filter, you can locate the Mime Type as follows:

   In the left rail, expand `content > dam > <locate_your_asset> > jcr:content > metadata`, and then in the table, locate `dc:format`.

   The following graphic is an example of an asset's path to `dc:format`.

   ![chlimage_1-18](assets/chlimage_1-3.png)

   Notice that the `dc:format` for the asset `Fiji Red.jpg` is `image/jpeg`.

   To have this filter apply to all images, regardless of their format, set the value to `image/*` where `*` is a regular expression that is applied to all images of any format.

   To have the filter apply only to images of the type JPEG, enter a value of `image/jpeg`.

1. Define what renditions you want to include or exclude from replication.

   Characters that you can use to filter for replication include the following:

<table>
 <tbody>
  <tr>
   <td><strong>Character to use</strong></td>
   <td><strong>How it filters assets for replication</strong></td>
  </tr>
  <tr>
   <td>*</td>
   <td>Wildcard character<br /> </td>
  </tr>
  <tr>
   <td>+</td>
   <td>Includes assets for replication.</td>
  </tr>
  <tr>
   <td>-</td>
   <td>Excludes assets from replication.</td>
  </tr>
 </tbody>
</table>

   Navigate to `content/dam/<locate your asset>/jcr:content/renditions`.

   The following graphic is an example of an asset's renditions.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   If you only wanted to replicate the original, then you would enter `+original`.

   -->

