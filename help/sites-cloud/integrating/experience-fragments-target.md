---
title: Exportieren von Experience Fragments nach Adobe Target
description: Erfahren Sie, wie Sie Ihre Experience Fragments in Adobe Target exportieren können, um Erlebnisse zu testen und zu personalisieren.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 752d91f9-13a6-40c2-9425-7d18dafe9205
solution: Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '2198'
ht-degree: 99%

---

# Exportieren von Experience Fragments nach Adobe Target{#exporting-experience-fragments-to-adobe-target}

>[!CAUTION]
>
>* Die AEM Experience Fragments werden in den Standardarbeitsbereich von Adobe Target exportiert.
>* AEM muss gemäß den Anweisungen unter [Integration mit Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md) mit Adobe Target integriert werden.

Sie können [Experience Fragments](/help/sites-cloud/authoring/fragments/content-fragments.md), die in Adobe Experience Manager as a Cloud Service (AEM) erstellt wurden, nach Adobe Target (Target) exportieren. Diese können dann als Angebote in Target-Aktivitäten verwendet werden, um Erlebnisse in großem Maßstab zu testen und zu personalisieren.

Es gibt drei Formatoptionen für den Export eines Experience Fragments nach Adobe Target:

* HTML (Standard): Unterstützung der Bereitstellung von Web- und Hybridinhalten
* JSON: Unterstützung der Headless-Inhaltsbereitstellung
* HTML und JSON

Um Ihre Instanz für den Export AEM Experience Fragments nach Adobe Target vorzubereiten, müssen Sie Folgendes tun:

* [Integrieren mit Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Hinzufügen der Cloud-Konfiguration](#add-the-cloud-configuration)
* [Hinzufügen der Legacy-Konfiguration](#add-the-legacy-configuration)

Danach können Sie:

* [Ein Experience Fragment nach Adobe Target exportieren](#exporting-an-experience-fragment-to-adobe-target)
* [Ihr Experience Fragments in Adobe Target verwenden ](#using-your-experience-fragments-in-adobe-target)
* Und auch [Ein bereits nach Adobe Target exportiertes Experience Fragment löschen](#deleting-an-experience-fragment-already-exported-to-adobe-target)

Experience Fragments können in den Standardarbeitsbereich in Adobe Target oder in benutzerdefinierte Arbeitsbereiche für Adobe Target exportiert werden.

>[!NOTE]
>
>Die Adobe Target-Arbeitsbereiche sind nicht in Adobe Target selbst vorhanden. Sie werden in Adobe IMS (Identity Management System) definiert und verwaltet und dann zur lösungsübergreifenden Verwendung mithilfe der Adobe-Entwicklerkonsole ausgewählt.

>[!NOTE]
>
>Adobe Target-Arbeitsbereiche können verwendet werden, um es Mitgliedern einer Organisation (Gruppe) zu ermöglichen, Angebote und Aktivitäten nur für diese Organisation zu erstellen und zu verwalten, ohne anderen Benutzern Zugriff zu gewähren. Zum Beispiel länderspezifische Organisationen innerhalb eines globalen Konzerns.

>[!NOTE]
>
>Weitere Informationen finden Sie in den folgenden Themen:
>
>* [Adobe Target-Entwicklung](https://developers.adobetarget.com/)
>* [Kernkomponenten – Experience Fragments](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)
>* [Adobe Target – Wie verwende ich Adobe Experience Manager (AEM) Experience Fragments?](https://experienceleague.adobe.com/docs/target/using/experiences/offers/aem-experience-fragments.html?lang=de)
>* [AEM 6.5 –Manuelles Konfigurieren der Integration mit Adobe Target – Erstellen einer Target Cloud-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-configuring.html?lang=de#creating-a-target-cloud-configuration)

## Voraussetzungen {#prerequisites}

Verschiedene Aktionen sind erforderlich:

1. Sie müssen [AEM mit Adobe Target integrieren](/help/sites-cloud/integrating/integrating-adobe-target.md).

1. Experience Fragments werden aus der AEM-Autoreninstanz exportiert. Daher müssen Sie auf der Autoreninstanz [den AEM Link Externalizer konfigurieren](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer), um sicherzustellen, dass alle Verweise im Experience Fragment für die Webbereitstellung externalisiert werden.

   >[!NOTE]
   >
   >Für das Umschreiben von Links, die nicht von der Standardeinstellung abgedeckt werden, ist der [Experience Fragment Link Rewriter Provider](/help/implementing/developing/extending/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) verfügbar. Dadurch können für Ihre Instanz benutzerdefinierte Regeln entwickelt werden.

## Hinzufügen der Cloud-Konfiguration {#add-the-cloud-configuration}

Bevor Sie ein Fragment exportieren, müssen Sie die **Cloud-Konfiguration** für **Adobe Target** zum Fragment oder Ordner hinzufügen. Dies ermöglicht Ihnen auch:

* die für den Export zu verwendenden Formatoptionen anzugeben
* einen Target-Arbeitsbereich als Ziel auszuwählen
* eine Externalizer-Domain zum Umschreiben von Verweisen im Experience Fragment auszuwählen (optional)

Die erforderlichen Optionen können in den **Seiteneigenschaften** des erforderlichen Ordners bzw. Fragments (oder von beiden) ausgewählt werden. Die Spezifikation wird nach Bedarf vererbt.

1. Navigieren Sie zur **Experience Fragment**-Konsole.

1. Öffnen Sie die **Seiteneigenschaften** für den entsprechenden Ordner oder das Fragment.

   >[!NOTE]
   >
   >Wenn Sie die Cloud-Konfiguration zum übergeordneten Ordner des Experience Fragments hinzufügen, wird die Konfiguration von allen untergeordneten Elementen geerbt.
   >
   >Wenn Sie die Cloud-Konfiguration zum Experience Fragment selbst hinzufügen, wird die Konfiguration an alle Variationen vererbt.

1. Wählen Sie die Registerkarte **Cloud-Services** aus.

1. Wählen Sie unter **Cloud Service-Konfiguration** in der Dropdown-Liste den Eintrag **Adobe Target**.

   >[!NOTE]
   >
   >Das JSON-Format eines Experience Fragment-Angebots kann angepasst werden. Definieren Sie dazu eine kundenspezifische Experience Fragment-Komponente und kommentieren Sie dann, wie die Eigenschaften im Komponenten-Sling-Modell exportiert werden.
   >
   >Siehe Kernkomponente: [Kernkomponenten – Experience Fragments](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/experience-fragment.html?lang=de)

1. Wählen Sie unter **Adobe Target** Folgendes aus:

   * die passende Konfiguration
   * die Option für das erforderliche Format
   * einen Adobe Target-Arbeitsbereich
   * falls erforderlich – die Externalizer-Domain

   >[!CAUTION]
   >
   >Die Externalizer-Domain ist optional.
   >
   > Ein AEM Externalizer wird konfiguriert, wenn die exportierten Inhalte auf eine bestimmte *publish* Domain verweisen sollen. Weitere Informationen finden Sie unter [Konfigurieren des AEM Link Externalizer](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer).
   >
   > Beachten Sie außerdem, dass Externalizer-Domains nur für den Inhalt des Experience Fragments, das an Target gesendet wird, relevant sind und nicht Metadaten wie Inhalte zum Anzeigen von Angeboten.

   Zum Beispiel für einen Ordner:

   ![Ordner – Cloud Services](assets/xf-target-integration-01.png "Ordner – Cloud Services")

1. **Speichern und schließen**.

## Hinzufügen der Legacy-Konfiguration {#add-the-legacy-configuration}

<!-- This is effectively the Manually Integrating with Adobe Target {#manually-integrating-with-adobe-target} section from 6.5 -->

>[!IMPORTANT]
>
>Das Hinzufügen einer neuen Legacy-Konfiguration ist ein Sonderszenario, das nur für den Export von Experience Fragments unterstützt wird.

Nachdem Sie [die Cloud-Konfiguration für die Verwendung von Experience Platform Launch hinzugefügt](#add-the-cloud-configuration) haben, müssen Sie die Integration von AEM mit Adobe Target auch manuell mit einer Legacy-Konfiguration durchführen.

### Erstellen einer Target-Cloud-Konfiguration {#creating-a-target-cloud-configuration}

Um AEM die Interaktion mit Adobe Target zu ermöglichen, erstellen Sie eine Target-Cloud-Konfiguration. Um die Konfiguration zu erstellen, geben Sie den Adobe Target-Clientcode und die Benutzeranmeldeinformationen an.

Sie erstellen die Target-Cloud-Konfiguration nur einmal, da Sie die Konfiguration mit mehreren AEM-Kampagnen verknüpfen können. Wenn Sie mehrere Adobe Target-Clientcodes haben, erstellen Sie für jeden Clientcode eine Konfiguration.

Sie können die Cloud-Konfiguration so konfigurieren, dass Segmente aus Adobe Target synchronisiert werden. Wenn Sie die Synchronisierung aktivieren, werden Segmente im Hintergrund aus Target importiert, sobald die Cloud-Konfiguration gespeichert wurde.

Gehen Sie wie folgt vor, um eine Target-Cloud-Konfiguration in AEM zu erstellen:

1. Gehen Sie zu **Legacy Cloud Services**: Über **das AEM-Logo** > **Tools** > **Cloud-Services** zu **Legacy Cloud Services**.
Beispiel: ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))

   Die Übersichtsseite **Adobe Experience Cloud** wird geöffnet.

1. Klicken Sie im Abschnitt **Adobe Target** auf **Jetzt konfigurieren**.
1. Im Dialogfeld **Konfiguration erstellen**:

   1. Geben Sie der Konfiguration einen **Titel**.
   1. Wählen Sie die Vorlage **Adobe Target-Konfiguration** aus.
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
   >1. Select **Save All**.

   -->

1. Geben Sie im Dialogfeld **Adobe Target-Einstellungen** Werte für diese Eigenschaften an.

   * **Authentifizierung**: dies ist standardmäßig IMS (Benutzeranmeldedaten werden nicht mehr unterstützt)

   * **Client-Code**: Der Client-Code des Target-Kontos

   * **Mandanten-ID**: die Mandanten-ID

   * **IMS-Konfiguration**: Wählen Sie die gewünschte Konfiguration aus der Dropdown-Liste aus

   * **API-Typ**: standardmäßig auf REST gesetzt (XML ist veraltet)

   * **A4T-Analytics-Cloud-Konfiguration**: Wählen Sie die Analyse-Cloud-Konfiguration aus, die für Target-Aktivitätsziele und -metriken verwendet wird. Sie benötigen sie, wenn Sie Adobe Analytics als Quelle für das Reporting für bestimmte Inhalte verwenden.

     <!-- Is this needed?
     If you do not see your cloud configuration, see note in [Configuring A4T Analytics Cloud Configuration](#configuring-a-t-analytics-cloud-configuration).
     -->

   * **Präzises Targeting verwenden**: Dieses Kontrollkästchen ist standardmäßig aktiviert. Wenn diese Option aktiviert ist, wartet die Cloud-Service-Konfiguration auf das Laden des Kontexts, bevor der Inhalt geladen wird. Siehe folgenden Hinweis.

   * **Segmente aus Adobe Target synchronisieren**: Aktivieren Sie diese Option, um in Target definierte Segmente herunterzuladen und in AEM zu verwenden. Wählen Sie diese Option aus, wenn die Eigenschaft „API-Typ“ auf „REST“ festgelegt ist, da Inline-Segmente nicht unterstützt werden und Sie immer Segmente aus Target verwenden müssen. (Der AEM-Begriff „Segment“ ist gleichbedeutend mit dem Target-Begriff „Zielgruppe“.)

   * **Client-Bibliothek:** dies ist standardmäßig AT.js (mbox.js wird nicht mehr unterstützt)

     >[!NOTE]
     >
     >Die Target-Bibliotheksdatei [AT.js](https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works.html?lang=de) ist die neue Implementierungsbibliothek für Adobe Target. Sie ist sowohl auf typische Web-Implementierungen als auch auf Einzelseitenanwendungen ausgelegt.
     >
     >mbox.js ist veraltet und wird zu einem späteren Zeitpunkt entfernt.
     >
     >Adobe empfiehlt die Verwendung von „AT.js“ anstelle von „mbox.js“ als Client-Bibliothek.
     >
     >„AT.js“ bietet gegenüber der Bibliothek von „mbox.js“ verschiedene Verbesserungen:
     >
     >* Verbesserte Seitenladezeiten für Web-Implementierungen
     >* Verbesserte Sicherheit
     >* Bessere Implementierungsoptionen für Single Page Applications (SPA)
     >* „at.js“ enthält die Komponenten, die in „target.js“ enthalten waren, weshalb kein Aufruf mehr an „target.js“ erfolgt
     >
     >Sie können im Dropdown-Menü **Client-Bibliothek** die Datei „AT.js“ oder „mbox.js“ auswählen.

   * **Verwenden des Tag Management Systems zur Bereitstellung der Client-Bibliothek**: Wählen Sie diese Option, um die Client-Bibliothek aus Adobe Launch oder einem anderen Tag-Management-System (oder DTM, das nicht mehr unterstützt wird) zu verwenden.

   * **Benutzerdefinierte AT.js**: Durchsuchen, um Ihre benutzerdefinierte AT.js-Datei hochzuladen. Lassen Sie das Feld leer, um die Standardbibliothek zu verwenden.

     >[!NOTE]
     >
     >Wenn Sie den Opt-in für den Adobe Target-Konfigurationsassistenten durchführen, wird das „präzise Targeting“ aktiviert.
     >
     >Präzises Targeting bedeutet, dass für die Cloud-Service-Konfiguration gewartet wird, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Aus diesem Grund kann hinsichtlich der Leistung eine präzise Zielgruppenbestimmung eine Verzögerung von einigen Millisekunden verursachen, bevor das Laden des Inhalts erfolgt.
     >
     >Das präzise Targeting ist auf der Autoreninstanz immer aktiviert. In der Veröffentlichungsinstanz können Sie die präzise Zielgruppenerfassung aber global deaktivieren, indem Sie in der Cloud-Service-Konfiguration das Häkchen neben „Präzise Zielgruppenerfassung“ entfernen (**http://localhost:4502/etc/cloudservices.html**). Sie können das präzise Targeting auch für einzelne Komponenten aktivieren und deaktivieren, unabhängig von Ihrer Einstellung in der Cloud-Service-Konfiguration.
     >
     >Wenn Sie ***bereits*** Zielkomponenten erstellt haben und Sie diese Einstellung ändern, wirken sich Ihre Änderungen nicht auf diese Komponenten aus. Sie müssen alle Änderungen an diesen Komponenten direkt vornehmen.

1. Klicken Sie auf **Mit Adobe Target verbinden**, um die Verbindung mit Target zu initialisieren. Wenn die Verbindungsherstellung erfolgreich war, wird die Meldung **Die Verbindung wurde hergestellt** angezeigt. Klicken Sie auf **OK** und dann auf **OK.**

### Hinzufügen eines Target-Frameworks {#adding-a-target-framework}

<!-- Is this section needed? -->

Nachdem Sie die Target-Cloud-Konfiguration konfiguriert haben, fügen Sie ein Target-Framework hinzu. Das Framework bestimmt die Standardparameter, die von den verfügbaren [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md)-Komponenten an Adobe Target gesendet werden. Target nutzt die Parameter, um die Segmente zu ermitteln, die für den aktuellen Kontext gelten.

Sie können mehrere Frameworks für eine einzelne Target-Konfiguration erstellen. Mehrere Frameworks sind nützlich, wenn Sie für unterschiedliche Abschnitte Ihrer Website jeweils einen anderen Parametersatz an Target senden müssen. Erstellen Sie ein Framework für jeden Parametersatz, der gesendet werden muss. Verknüpfen Sie jeden Bereich Ihrer Website mit dem entsprechenden Framework. Beachten Sie, dass für eine Webseite nur jeweils ein Framework verwendet werden kann.

1. Klicken Sie auf der Seite für die Target-Konfiguration auf das Pluszeichen (**+**) neben „Verfügbare Konfigurationen“.

1. Geben Sie im Dialogfeld „Framework erstellen“ einen **Titel** an, wählen Sie die Option **Adobe Target-Framework** und klicken Sie auf **Erstellen**.

   <!-- ![config-target-framework-dialog](assets/config-target-framework-dialog.png) -->

   Die Framework-Seite wird geöffnet. Sidekick bietet Komponenten mit Informationen zu dem [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md), den Sie zuordnen können.

   <!-- ![Framework](assets/chlimage_1-162.png) -->

1. Ziehen Sie die ClientContext-Komponente mit den Daten, die Sie für die Zuordnung nutzen möchten, auf das Ablageziel. Alternativ hierzu können Sie die **ContextHub-Store**-Komponente auf das Framework ziehen.

   >[!NOTE]
   >
   >Bei der Zuordnung werden Parameter über einfache Zeichenfolgen an eine mBox übergeben. Es ist nicht möglich, Arrays aus ContextHub zuzuordnen.

   Ziehen Sie beispielsweise die Komponente **Profildaten** auf die Seite, um **Profildaten** zu Ihren Websitebesuchern zum Steuern Ihrer Target-Kampagne zu verwenden. Es werden die Profildatenvariablen angezeigt, die für die Zuordnung zu Target-Parametern verfügbar sind.

   <!-- ![Profile Data](assets/chlimage_1-163.png) -->

1. Wählen Sie die Variablen aus, die für das Adobe Target-System sichtbar sein sollen, indem Sie das Kontrollkästchen **Freigeben** in den entsprechenden Spalten auswählen.

   <!-- ![Share](assets/chlimage_1-164.png) -->

   >[!NOTE]
   >
   >Das Synchronisieren von Parametern erfolgt nur in eine Richtung, nämlich von AEM zu Adobe Target.

Ihr Framework wird erstellt. Um das Framework auf der Veröffentlichungsinstanz zu replizieren, verwenden Sie die Option **Framework aktivieren** aus dem Sidekick.

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
1. Using either [quick actions](/help/sites-cloud/authoring/basic-handling.md#quick-actions) or [selection mode](/help/sites-cloud/authoring/basic-handling.md#selecting-resources), select **View Properties.**
1. Select the **Cloud Services** tab.
1. Select **Edit**.
1. Select **Add Configuration** under **Cloud Service Configurations** and select **Adobe Target**.

  ![Cloud Service Configuration](assets/chlimage_1-165.png)

1. Select the framework you want under **Configuration Reference**.

   >[!NOTE]
   >
   >Make sure that you select the specific **framework** that you created and not the Target cloud configuration under which it was created.

1. Select **Done**.
1. Activate the root page of the website to replicate it to the publish server. (See [How To Publish Pages](/help/sites-cloud/authoring/sites-console/publishing-pages.md).)

   >[!NOTE]
   >
   >If the framework you attached to the page was not activated yet, a wizard opens which lets you publish it as well.
-->

## Ein Experience Fragment nach Adobe Target exportieren {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Für Medien-Assets wie Bilder wird nur ein Verweis nach Target exportiert. Das Asset selbst bleibt in AEM Assets gespeichert und wird von der AEM-Veröffentlichungsinstanz bereitgestellt.
>
>Daher muss das Experience Fragment mit allen zugehörigen Assets veröffentlicht werden, bevor es nach Target exportiert wird.

So exportieren Sie ein Experience Fragment aus AEM nach Target (nach Angabe der Cloud-Konfiguration):

1. Navigieren Sie zur Experience Fragment-Konsole.
1. Wählen Sie das Experience Fragment aus, das Sie in nach Target exportieren möchten.

   >[!NOTE]
   >
   >Es muss sich um eine Experience Fragment Web-Variante handeln.

1. Wählen Sie **Nach Adobe Target exportieren** aus

   >[!NOTE]
   >
   >Wenn das Experience Fragment bereits exportiert wurde, wählen Sie **In Adobe Target aktualisieren**.

1. Wählen Sie **Exportieren ohne Veröffentlichung** bzw. **Veröffentlichen** aus.

   >[!NOTE]
   >
   >Wenn Sie **Veröffentlichen** auswählen, wird das Experience Fragment sofort veröffentlicht und an Target gesendet.

1. Wählen Sie im Bestätigungsdialogfeld **OK** aus.

   Ihr Experience Fragment sollte jetzt in Target enthalten sein.

   >[!NOTE]
   >
   >In der [Listenansicht](/help/sites-cloud/authoring/fragments/content-fragments.md#details-of-your-experience-fragment) der Konsole und in den **Eigenschaften** werden **verschiedene Details** des Exports angezeigt.

   >[!NOTE]
   >
   >Beim Anzeigen eines Experience Fragments in Adobe Target gibt *Zuletzt geändert* an, wann das Fragment zuletzt in AEM geändert wurde. Es ist nicht das Datum, an dem das Fragment zuletzt in Adobe Target exportiert wurde.

>[!NOTE]
>
>Alternativ können Sie den Export auch über den Seiteneditor durchführen, indem Sie vergleichbare Befehle im Menü [Seiteninformationen](/help/sites-cloud/authoring/page-editor/introduction.md#page-information) verwenden.

## Ihre Experience Fragments in Adobe Target verwenden {#using-your-experience-fragments-in-adobe-target}

Nach dem Ausführen der zuvor genannten Aufgaben wird das Experience Fragment auf der Seite „Angebote“ in Target angezeigt. Schauen Sie sich die [spezifische Target-Dokumentation](https://experiencecloud.adobe.com/resources/help/de_DE/target/target/aem-experience-fragments.html) an, um zu erfahren, was Sie dort erreichen können.

>[!NOTE]
>
>Beim Anzeigen eines Experience Fragments in Adobe Target gibt *Zuletzt geändert* an, wann das Fragment zuletzt in AEM geändert wurde. Es ist nicht das Datum, an dem das Fragment zuletzt in Adobe Target exportiert wurde.

## Löschen eines bereits nach Adobe Target exportierten Experience Fragments {#deleting-an-experience-fragment-already-exported-to-adobe-target}

Das Löschen eines Experience Fragments, das bereits in Target exportiert wurde, kann Probleme verursachen, wenn das Fragment bereits in einem Angebot in Target verwendet wird. Durch das Löschen des Fragments wird das Angebot unbrauchbar, da der Fragmentinhalt von AEM bereitgestellt wird.

So vermeiden Sie solche Situationen:

* Wenn das Experience Fragment derzeit nicht in einer Aktivität verwendet wird, ermöglicht AEM es den Benutzenden, das Fragment ohne Warnmeldung zu löschen.
* Wenn das Experience Fragment derzeit von einer Aktivität in Target verwendet wird, werden AEM-Benutzende durch eine Fehlermeldung über die möglichen Auswirkungen des Löschens des Fragments auf die Aktivität gewarnt.

  Die Fehlermeldung in AEM untersagt den Benutzenden nicht das (erzwungene) Löschen des Experience Fragments. Wenn das Experience Fragment gelöscht wurde, gilt Folgendes:

   * Das Target-Angebot mit dem AEM Experience Fragment kann unerwünschtes Verhalten zeigen

      * Das Angebot wird wahrscheinlich noch gerendert, da das Experience Fragment-HTML nach Target verschoben wurde
      * Verweise im Experience Fragment funktionieren möglicherweise nicht ordnungsgemäß, wenn referenzierte Assets auch in AEM gelöscht wurden.

   * Natürlich sind keine weiteren Änderungen am Experience Fragment möglich, da es nicht mehr in AEM vorhanden ist.
