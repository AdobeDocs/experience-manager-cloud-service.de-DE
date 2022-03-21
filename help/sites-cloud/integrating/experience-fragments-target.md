---
title: Exportieren von Experience Fragments in Adobe Target
description: Exportieren von Experience Fragments in Adobe Target
exl-id: 752d91f9-13a6-40c2-9425-7d18dafe9205
source-git-commit: 8e13f671ada67e4e22b66094ad23bf5a0508ccba
workflow-type: tm+mt
source-wordcount: '2259'
ht-degree: 54%

---

# Exportieren von Experience Fragments in Adobe Target{#exporting-experience-fragments-to-adobe-target}

>[!CAUTION]
>
>* Die AEM Experience Fragments werden in den Standardarbeitsbereich von Adobe Target exportiert.
>* AEM müssen gemäß den Anweisungen unter mit Adobe Target integriert werden [Integration mit Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md).


Sie können exportieren [Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md), erstellt in Adobe Experience Manager as a Cloud Service (AEM), in Adobe Target (Target). Diese können dann als Angebote in Target-Aktivitäten verwendet werden, um Erlebnisse in großem Maßstab zu testen und zu personalisieren.

Für den Export eines Experience Fragment nach Adobe Target stehen drei Optionen zur Verfügung:

* HTML (Standard): Unterstützung der Bereitstellung von Web- und Hybridinhalten
* JSON: Unterstützung der Headless Content-Bereitstellung
* HTML und JSON

Um Ihre Instanz für den Export AEM Experience Fragments in Adobe Target vorzubereiten, müssen Sie Folgendes tun:

* [Integrieren Sie es mit Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Hinzufügen der Cloud-Konfiguration](#add-the-cloud-configuration)
* [Ältere Konfiguration hinzufügen](#add-the-legacy-configuration)

Danach können Sie:

* [Experience Fragment nach Adobe Target exportieren](#exporting-an-experience-fragment-to-adobe-target)
* [Verwenden Ihrer Experience Fragments in Adobe Target](#using-your-experience-fragments-in-adobe-target)
* Und auch [Löschen eines bereits nach Adobe Target exportierten Experience Fragments](#deleting-an-experience-fragment-already-exported-to-adobe-target)

Experience Fragments können in den Standardarbeitsbereich in Adobe Target oder in benutzerdefinierte Arbeitsbereiche für Adobe Target exportiert werden.

>[!NOTE]
>
>Die Adobe Target-Arbeitsbereiche sind nicht in Adobe Target selbst vorhanden. Sie werden in Adobe IMS (Identity Management System) definiert und verwaltet und dann zur lösungsübergreifenden Verwendung mithilfe der Adobe Developer Console ausgewählt.

>[!NOTE]
>
>Adobe Target-Arbeitsbereiche können verwendet werden, um es Mitgliedern einer Organisation (Gruppe) zu ermöglichen, Angebote und Aktivitäten nur für diese Organisation zu erstellen und zu verwalten. ohne Zugriff auf andere Benutzer. Zum Beispiel länderspezifische Organisationen innerhalb eines globalen Unternehmens.

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* [Adobe Target-Entwicklung](http://developers.adobetarget.com/)
>* [Kernkomponenten - Experience Fragments](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)
>* [Adobe Target - Wie verwende ich Adobe Experience Manager (AEM)-Experience Fragments?](https://experienceleague.adobe.com/docs/target/using/experiences/offers/aem-experience-fragments.html?lang=en)
>* [AEM 6.5 - Manuelles Konfigurieren der Integration mit Adobe Target - Erstellen einer Target Cloud-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-configuring.html#creating-a-target-cloud-configuration)


## Voraussetzungen {#prerequisites}

Verschiedene Aktionen sind erforderlich:

1. Sie müssen [AEM mit Adobe Target integrieren](/help/sites-cloud/integrating/integrating-adobe-target.md).

1. Experience Fragments werden aus der AEM-Autoreninstanz exportiert. Daher müssen Sie [Konfigurieren von AEM Link Externalizer](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer) auf der Autoreninstanz, um sicherzustellen, dass alle Verweise im Experience Fragment für die Webbereitstellung externalisiert werden.

   >[!NOTE]
   >
   >Für das Neuschreiben von Links, das nicht standardmäßig erfolgt, ist der [Experience Fragment Link Rewriter Provider](/help/implementing/developing/extending/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) verfügbar. Damit können benutzerspezifische Regeln für Ihre Instanz entwickelt werden.

## Hinzufügen der Cloud-Konfiguration {#add-the-cloud-configuration}

Bevor Sie ein Fragment exportieren, müssen Sie die **Cloud-Konfiguration** für **Adobe Target** zum Fragment oder Ordner hinzufügen. Dies ermöglicht Ihnen auch Folgendes:

* die für den Export zu verwendenden Formatoptionen angeben
* Target-Arbeitsbereich als Ziel auswählen
* eine Externalizer-Domäne zum Neuschreiben von Verweisen im Experience Fragment auswählen (optional)

Die erforderlichen Optionen können in den **Seiteneigenschaften** des erforderlichen Ordners bzw. Fragments ausgewählt werden. Die Spezifikation wird nach Bedarf vererbt.

1. Navigieren Sie zur **Experience Fragment**-Konsole.

1. Öffnen Sie die **Seiteneigenschaften** für den entsprechenden Ordner oder das Fragment.

   >[!NOTE]
   >
   >Wenn Sie die Cloud-Konfiguration zum übergeordneten Ordner „Experience Fragment“ hinzufügen, wird die Konfiguration von allen untergeordneten Elementen geerbt.
   >
   >Wenn Sie die Cloud-Konfiguration zum Experience Fragment selbst hinzufügen, wird die Konfiguration von allen Varianten geerbt.

1. Wählen Sie die Registerkarte **Cloud-Services** aus.

1. under **Cloud Service-Konfiguration** auswählen **Adobe Target** aus der Dropdown-Liste aus.

   >[!NOTE]
   >
   >Das JSON-Format eines Experience Fragment-Angebots kann angepasst werden. Definieren Sie dazu eine Customer Experience Fragment-Komponente und kommentieren Sie dann, wie die Eigenschaften im Komponenten-Sling-Modell exportiert werden.
   >
   >Siehe Kernkomponente: [Kernkomponenten - Experience Fragments](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/experience-fragment.html)

1. under **Adobe Target** select:

   * die entsprechende Konfiguration
   * die Option für das erforderliche Format
   * einen Adobe Target-Arbeitsbereich
   * falls erforderlich - die Externalizer-Domäne

   >[!CAUTION]
   >
   >Die Externalizer-Domäne ist optional.
   >
   > Ein AEM Externalizer wird konfiguriert, wenn der exportierte Inhalt auf einen bestimmten *publish* Domäne. Weitere Informationen finden Sie unter [Konfigurieren des AEM Link Externalizer](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer).
   >
   > Beachten Sie außerdem, dass Externalizer-Domänen nur für den Inhalt des Experience Fragment relevant sind, das an Target gesendet wird, und nicht für Metadaten wie Angebotsinhalt anzeigen.

   Beispiel für einen Ordner:

   ![Ordner - Cloud Services](assets/xf-target-integration-01.png "Ordner - Cloud Services")

1. Klicken Sie auf **Speichern und schließen**.

## Ältere Konfiguration hinzufügen {#add-the-legacy-configuration}

<!-- This is effectively the Manually Integrating with Adobe Target {#manually-integrating-with-adobe-target} section from 6.5 -->

>[!IMPORTANT]
>
>Das Hinzufügen einer neuen Legacy-Konfiguration ist ein Sonderszenario, das nur für den Export von Experience Fragments unterstützt wird.

Nachher [Hinzufügen der Cloud-Konfiguration](#add-the-cloud-configuration) Um Launch by Adobe zu verwenden, müssen Sie zur anfänglichen Integration von AEM in Adobe Target auch die manuelle Integration mit Adobe Target mithilfe einer veralteten Konfiguration durchführen.

### Erstellen einer Target-Cloud-Konfiguration {#creating-a-target-cloud-configuration}

Erstellen Sie eine Target-Cloud-Konfiguration, um für AEM die Interaktion mit Adobe Target zu ermöglichen. Zum Erstellen der Konfiguration geben Sie den Adobe Target-Client-Code und die Benutzeranmeldeinformationen an.

Sie erstellen die Target-Cloud-Konfiguration nur einmal, da Sie die Konfiguration mehreren AEM-Kampagnen zuordnen können. Erstellen Sie eine Konfiguration für jeden Client-Code, falls Sie über mehrere Adobe Target-Client-Codes verfügen.

Sie können die Cloud-Konfiguration so konfigurieren, dass Segmente aus Adobe Target synchronisiert werden. Wenn Sie die Synchronisierung aktivieren, werden die Segmente im Hintergrund aus Target importiert, sobald die Cloud-Konfiguration gespeichert wurde.

Verwenden Sie das folgende Verfahren, um eine Target-Cloud-Konfiguration in AEM zu erstellen:

1. Navigieren Sie zu **Ältere Cloud Services** über die **AEM** > **Instrumente** > **Cloud Services** > **Ältere Cloud Services**.
Beispiel: ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))

   Die **Adobe Experience Cloud** Die Übersichtsseite wird geöffnet.

1. Im **Adobe Target** Abschnitt, klicken Sie auf **Jetzt konfigurieren**.
1. Im **Konfiguration erstellen** dialog:

   1. Geben Sie der Konfiguration eine **Titel**.
   1. Wählen Sie die **Adobe Target-Konfiguration** Vorlage.
   1. Klicken Sie auf **Erstellen**.

Sie können jetzt die neue Konfiguration zur Bearbeitung auswählen.

1. Das Dialogfeld „Bearbeiten“ wird geöffnet.

   ![config-target-settings-dialog](assets/config-target-settings-dialog.png)

   <!-- Can this still occur?

   >[!NOTE]
   >
   >When configuring A4T with AEM, you may see a Configuration reference missing entry. To be able to select the analytics framework, do the following:
   >
   >1. Navigate to **Tools** &gt; **General** &gt; **CRXDE Lite**.
   >1. Navigate to **/libs/cq/analytics/components/testandtargetpage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**
   >1. Set the property **disable** to **false**.
   >1. Tap or click **Save All**.

   -->

1. Im **Adobe Target-Einstellungen** -Dialogfeld Werte für diese Eigenschaften angeben.

   * **Authentifizierung**: Diese Standardeinstellung ist IMS (Benutzeranmeldeinformationen werden nicht mehr unterstützt).

   * **Client-Code**: Der Client-Code des Target-Kontos.

   * **Mandanten-ID**: die Mandanten-ID

   * **IMS-Konfiguration**: Wählen Sie die gewünschte Konfiguration aus der Dropdown-Liste aus.

   * **API-Typ**: standardmäßig auf REST gesetzt (XML ist veraltet)

   * **A4T-Analyse-Cloud-Konfiguration**: Wählen Sie die Analyse-Cloud-Konfiguration aus, die für Target-Aktivitätsziele und -metriken verwendet wird. Sie benötigen sie, wenn Sie Adobe Analytics als Quelle für die Berichterstellung für bestimmte Inhalte verwenden.

      <!-- Is this needed?
     If you do not see your cloud configuration, see note in [Configuring A4T Analytics Cloud Configuration](#configuring-a-t-analytics-cloud-configuration).
     -->

   * **Verwenden Sie genaues Targeting:** Standardmäßig ist dieses Kontrollkästchen aktiviert. Bei Aktivierung dieser Option wird für die Cloud Service-Konfiguration gewartet, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Siehe Hinweis unten.

   * **Segmente aus Adobe Target synchronisieren:** Wählen Sie diese Option aus, um in Target definierte Segmente herunterzuladen und in AEM zu verwenden. Sie müssen diese Option auswählen, wenn die Eigenschaft „API-Typ“ auf „REST“ festgelegt ist, da Inline-Segmente nicht unterstützt werden und Sie immer Segmente aus Target verwenden müssen. (Beachten Sie, dass der AEM-Begriff „Segment“ hier dem Target-Begriff „Zielgruppe“ entspricht.)

   * **Client-Bibliothek:** Diese Standardeinstellung ist &quot;AT.js&quot;(mbox.js wird nicht mehr unterstützt).

      >[!NOTE]
      >
      >die Target-Bibliotheksdatei, [AT.JS](https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/implement-target-for-client-side-web.html)ist eine neue Implementierungsbibliothek für Adobe Target, die sowohl für typische Webimplementierungen als auch für Einzelseitenanwendungen entwickelt wurde.
      >
      >mbox.js ist veraltet und wird zu einem späteren Zeitpunkt entfernt.
      >
      >Adobe empfiehlt, anstelle von „mbox.js“ die Datei „AT.js“ als Client-Bibliothek zu verwenden.
      >
      >„AT.js“ bietet im Vergleich zur Bibliothek „mbox.js“ viele Verbesserungen, z. B.:
      >
      >* Verbesserte Seitenladezeiten für Web-Implementierungen
      >* Verbesserte Sicherheit
      >* Bessere Implementierungsoptionen für Einzelseitenanwendungen
      >* „AT.js“ enthält die Komponenten, die in „target.js“ enthalten waren, sodass „target.js“ nicht mehr aufgerufen wird.

      >
      >Sie können im Dropdown-Menü **Client-Bibliothek** die Datei „AT.js“ oder „mbox.js“ auswählen.

   * **Tag Management System zum Bereitstellen der Client-Bibliothek verwenden** - Wählen Sie diese Option, um die Client-Bibliothek aus Adobe Launch oder einem anderen Tag-Management-System (oder DTM, das nicht mehr unterstützt wird) zu verwenden.

   * **Benutzerdefinierte at.js**: Navigieren Sie zu , um Ihre benutzerdefinierte AT.js-Datei hochzuladen. Lassen Sie das Feld leer, um die Standardbibliothek zu verwenden.

      >[!NOTE]
      >
      >Wenn Sie den Opt-in für den Adobe Target-Konfigurationsassistenten durchführen, wird die „präzise Zielgruppenerfassung“ aktiviert.
      >
      >Präzise Zielgruppenerfassung bedeutet, dass für die Cloud Service-Konfiguration gewartet wird, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Daher kann es in Bezug auf die Leistung bei der präzisen Zielgruppenerfassung zu einer Verzögerung von einigen Millisekunden kommen, bevor das Laden des Inhalts erfolgt.
      >
      >Die präzise Zielgruppenerfassung ist auf der Autoreninstanz immer aktiviert. Auf der Veröffentlichungsinstanz können Sie die präzise Zielgruppenerfassung aber global deaktivieren, indem Sie in der Cloud Service-Konfiguration das Häkchen neben „Präzise Zielgruppenerfassung“ entfernen (**http://localhost:4502/etc/cloudservices.html**). Außerdem können Sie die präzise Zielgruppenerfassung unabhängig von Ihrer Einstellung in der Cloud Service-Konfiguration auch für einzelne Komponenten ein- oder ausschalten.
      >
      >Wenn Sie Komponenten als Ziel ***bereits*** angegeben haben und diese Einstellung dann ändern, wirken sich Ihre Änderungen nicht auf diese Komponenten aus. Sie müssen alle Änderungen an dieser Komponente direkt vornehmen.

1. Klicken Sie auf **Mit Adobe Target verbinden**, um die Verbindung mit Target zu initialisieren. Wenn die Verbindung erfolgreich hergestellt wurde, wird die Meldung **Verbindung erfolgreich** angezeigt. Klicken Sie auf **OK** und dann auf **OK.**

   Falls Sie keine Verbindung mit Target herstellen können, helfen Ihnen die Informationen im Abschnitt zur [Fehlerbehebung](#troubleshooting-target-connection-problems) weiter.

### Hinzufügen eines Target-Frameworks {#adding-a-target-framework}

<!-- Is this section needed? -->

Nachdem Sie die Target-Cloud-Konfiguration konfiguriert haben, können Sie ein Target-Framework hinzufügen. Das Framework identifiziert die Standardparameter, die von der verfügbaren [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md) Komponenten. Target nutzt die Parameter, um die Segmente zu ermitteln, die für den aktuellen Kontext gelten.

Sie können für eine Target-Konfiguration mehrere Frameworks erstellen. Mehrere Frameworks sind nützlich, wenn Sie für unterschiedliche Abschnitte Ihrer Website jeweils einen anderen Parametersatz an Target senden müssen. Erstellen Sie ein Framework für jeden Parametersatz, der gesendet werden muss. Ordnen Sie die einzelnen Abschnitte Ihrer Website jeweils dem passenden Framework zu. Beachten Sie, dass auf einer Webseite jeweils nur ein Framework verwendet werden kann.

1. Klicken Sie auf der Target-Konfigurationsseite auf die **+** (Pluszeichen) neben Verfügbare Konfigurationen.

1. Geben Sie im Dialogfeld Framework erstellen eine **Titel**, wählen Sie die **Adobe Target Framework** und klicken Sie auf **Erstellen**.

   <!-- ![config-target-framework-dialog](assets/config-target-framework-dialog.png) -->

   Die Framework-Seite wird geöffnet. Der Sidekick stellt Komponenten bereit, die Informationen aus dem [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md) die Sie zuordnen können.

   <!-- ![chlimage_1-162](assets/chlimage_1-162.png) -->

1. Ziehen Sie die ClientContext-Komponente mit den Daten, die Sie für die Zuordnung nutzen möchten, auf das Ablageziel. Alternativ hierzu können Sie die **ContextHub-Store**-Komponente auf das Framework ziehen.

   >[!NOTE]
   >
   >Bei der Zuordnung werden Parameter über einfache Zeichenfolgen an mbox übergeben. Es ist nicht möglich, Arrays aus ContextHub zuzuordnen.

   Verwenden Sie beispielsweise **Profildaten** über Ihre Sitebesucher, um Ihre Target-Kampagne zu steuern, ziehen Sie die **Profildaten** -Komponente auf der Seite. Es werden die Profildatenvariablen angezeigt, die für die Zuordnung zu Target-Parametern verfügbar sind.

   <!-- ![chlimage_1-163](assets/chlimage_1-163.png) -->

1. Wählen Sie die Variablen aus, die für das Adobe Target-System sichtbar sein sollen, indem Sie das Kontrollkästchen **Freigeben** in den entsprechenden Spalten auswählen.

   <!-- ![chlimage_1-164](assets/chlimage_1-164.png) -->

   >[!NOTE]
   >
   >Parameter können nur in einer Richtung synchronisiert werden: von AEM nach Adobe Target.

Ihr Framework wird erstellt. Verwenden Sie die Sidekick-Option **Framework aktivieren**, um das Framework auf der Veröffentlichungsinstanz zu replizieren.

<!--
### Associating Activities With the Target Cloud Configuration  {#associating-activities-with-the-target-cloud-configuration}

Associate your [AEM activities](/help/sites-cloud/authoring/personalization/activities.md) with your Target cloud configuration so that you can mirror the activities in [Adobe Target](https://experienceleague.adobe.com/docs/target/using/experiences/offers/manage-content.html).

>[!NOTE]
>
>What types of activities are available is determined by the following:
>
>* If the **xt_only** option is enabled on the Adobe Target tenant (clientcode) used on the AEM side to connect to Adobe Target, then you can create **only** XT activities in AEM.
>
>* If the **xt_only** options is **not** enabled on the Adobe Target tenant (clientcode), then you can create **both** XT and A/B activities in AEM.
>
>**Additional note:** **xt_only** options is a setting applied on a certain Target tenant (clientcode) and can only be modified directly in Adobe Target. You cannot enable or disable this option in AEM.
-->

<!--
### Associating the Target Framework With Your Site {#associating-the-target-framework-with-your-site}

After you create a Target framework in AEM, associate your web pages with the framework. The targeted components on the pages send the framework-defined data to Adobe Target for tracking. (See [Content Targeting](/help/sites-cloud/authoring/personalization/targeted-content.md).)

When you associate a page with the framework, the child pages inherit the association.

1. In the **Sites** console, navigate to the site that you want to configure.
1. Using either [quick actions](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions) or [selection mode](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources), select **View Properties.**
1. Select the **Cloud Services** tab.
1. Tap/click **Edit**.
1. Tap/click **Add Configuration** under **Cloud Service Configurations** and select **Adobe Target**.

  ![chlimage_1-165](assets/chlimage_1-165.png)

1. Select the framework you want under **Configuration Reference**.

   >[!NOTE]
   >
   >Make sure that you select the specific **framework** that you created and not the Target cloud configuration under which it was created.

1. Tap/click **Done**.
1. Activate the root page of the website to replicate it to the publish server. (See [How To Publish Pages](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).)

   >[!NOTE]
   >
   >If the framework you attached to the page was not activated yet, a wizard opens which allows you to publish it as well.
-->

<!--
### Troubleshooting Target Connection Problems {#troubleshooting-target-connection-problems}

Perform the following tasks to troubleshoot problems that occur when connecting to Target:

* Make sure that the user credentials that you provide are correct.
* Make sure that the AEM instance can connect to the Target server. For example, make sure that firewall rules are not blocking outbound AEM connections, or that AEM is configured to use necessary proxies.
* Look for helpful messages in the AEM error log. The error.log file is located in the **crx-quickstart/logs** directory where AEM is installed.
* When editing the activity in Adobe Target, the URL is pointing to localhost. Work around this by setting the AEM externalizer to the correct URL.
-->

## Exportieren eines Experience Fragments in Adobe Target {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Für Medienassets wie Bilder wird nur ein Verweis in Target exportiert. Das Asset selbst bleibt in AEM Assets gespeichert und wird aus der AEM-Veröffentlichungsinstanz bereitgestellt.
>
>Daher muss das Experience Fragment mit allen zugehörigen Assets veröffentlicht werden, bevor es in Target exportiert wird.

So exportieren Sie ein Experience Fragment von AEM nach Target (nach dem Angeben der Cloud-Konfiguration):

1. Navigieren Sie zur Experience Fragment-Konsole.
1. Wählen Sie das Experience Fragment, das Sie als Ziel exportieren möchten.

   >[!NOTE]
   >
   >Es muss eine Web-Variante des Experience Fragments sein.

1. Tippen/klicken Sie auf **Nach Adobe Target exportieren**.

   >[!NOTE]
   >
   >Wenn das Experience Fragment bereits exportiert wurde, wählen Sie **In Adobe Target aktualisieren**.

1. Tippen/klicken Sie auf **Exportieren, ohne veröffentlichen** bzw. auf **Veröffentlichen**.

   >[!NOTE]
   >
   >Wenn Sie **Veröffentlichen** auswählen, wird das Experience Fragment sofort veröffentlicht und an Target gesendet.

1. Tippen/klicken **OK** im Bestätigungsdialogfeld.

   Ihr Experience Fragment sollte jetzt in Target enthalten sein.

   >[!NOTE]
   >
   >In der [Listenansicht](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#details-of-your-experience-fragment) der Konsole und in den **Eigenschaften** werden **verschiedene Details** des Exports angezeigt.

   >[!NOTE]
   >
   >Beim Anzeigen eines Experience Fragments in Adobe Target gibt das *Datum der letzten Änderung* an, wann das Fragment zuletzt in AEM geändert wurde. Es ist nicht das Datum, an dem das Fragment zuletzt in Adobe Target exportiert wurde.

>[!NOTE]
>
>Alternativ können Sie den Export aus dem Seiteneditor mithilfe ähnlicher Befehle im Menü [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) durchführen.

## Verwenden von Experience Fragments in Adobe Target {#using-your-experience-fragments-in-adobe-target}

Nach dem Ausführen der vorherigen Aufgaben wird das Experience Fragment auf der Seite Angebote in Target angezeigt. In der [entsprechenden Target-Dokumentation](https://experiencecloud.adobe.com/resources/help/de_DE/target/target/aem-experience-fragments.html) erfahren Sie, was Sie dort erreichen können.

>[!NOTE]
>
>Beim Anzeigen eines Experience Fragments in Adobe Target gibt das *Datum der letzten Änderung* an, wann das Fragment zuletzt in AEM geändert wurde. Es ist nicht das Datum, an dem das Fragment zuletzt in Adobe Target exportiert wurde.

## Löschen eines bereits nach Adobe Target exportierten Experience Fragments {#deleting-an-experience-fragment-already-exported-to-adobe-target}

Das Löschen eines Experience Fragments, das bereits nach Target exportiert wurde, kann zu Problemen führen, wenn das Fragment bereits in einem Angebot in Target verwendet wird. Durch das Löschen des Fragments ist das Angebot nicht mehr verwendbar, da der Fragmentinhalt von AEM bereitgestellt wird.

So vermeiden Sie solche Situationen:

* Wenn das Experience Fragment derzeit nicht in einer Aktivität verwendet wird, kann der Benutzer das Fragment ohne Warnmeldung in AEM löschen.
* Wenn das Experience Fragment derzeit von einer Aktivität in Target verwendet wird, warnt eine Fehlermeldung den AEM-Benutzer vor möglichen Konsequenzen, die das Löschen des Fragments für die Aktivität nach sich zieht.

   Die Fehlermeldung in AEM verbietet dem Benutzer nicht das (erzwungene) Löschen des Experience Fragments. Wenn das Experience Fragment gelöscht wird:

   * Das Target-Angebot mit AEM Experience Fragment kann unerwünschtes Verhalten zeigen

      * Das Angebot wird wahrscheinlich weiterhin gerendert, da die Experience Fragment-HTML an Target gepusht wurde
      * Verweise im Experience Fragment funktionieren möglicherweise nicht ordnungsgemäß, wenn referenzierte Assets auch in AEM gelöscht wurden.
   * Natürlich sind alle weiteren Änderungen am Experience Fragment nicht möglich, da das Experience Fragment nicht mehr in AEM vorhanden ist.
