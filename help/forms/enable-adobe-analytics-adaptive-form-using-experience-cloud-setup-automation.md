---
title: Wie wird Adobe Analytics für ein adaptives Formular aktiviert?
description: Experience Cloud Setup Automation hilft, Adobe Analytics mit einem adaptiven Formular zu verbinden, um Einblicke in Besucherinteraktionen und Interaktionen zu verfolgen.
keywords: Aktivieren Sie Adobe Analytics für ein adaptives Formular mithilfe der Automatisierung des Experience Cloud-Setups, aktivieren Sie Adobe Analytics in Forms, Adobe Analytics in Adaptive Forms, Forms Analytics-Integration, Forms und Adobe Analytics
exl-id: 0e1aa040-08b4-4c1a-b247-ad6fff410187
source-git-commit: fa107ee89deb217ada2cfbcccb4602a7a6aff125
workflow-type: tm+mt
source-wordcount: '1576'
ht-degree: 7%

---

# Aktivieren Sie Adobe Analytics für ein adaptives Formular mithilfe der Automatisierung des Experience Cloud-Setups. {#integrate-adobe-analytics-to-aem-forms-with-experience-cloud-setup-automation}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Dieser Artikel |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/configure-analytics-forms-documents.html) |

Mit der Automatisierung der Experience Cloud-Einrichtung können Sie Adobe Analytics mit Adaptive Forms verbinden, wodurch Benutzerinteraktionen mit Ihren Formularen verfolgt und analysiert und Einblicke in Besucherinteraktionen und Interaktionen geboten werden können. Experience Cloud Setup Automation hilft auch bei der Überwachung der Formularleistung, bei der Metriken wie Abschlusszeiten und Abbruchpunkte bewertet werden. Diese Analyse hilft, Formulare für ein besseres Benutzererlebnis zu optimieren und dabei das Benutzerverhalten anhand des Anmeldestatus (z. B. anonyme Benutzer) zu unterscheiden, um allgemeine Trends und Muster zu identifizieren.

## Vorteile der Integration von Adobe Analytics in Adaptive Forms {#advantages-of-integrating-adobe-analytics-with-aem-forms}

* **Einblicke in das Verhalten der Endbenutzer**: Adobe Analytics hilft dabei, Einblicke in das Verhalten der Endbenutzer zu erhalten, zeigt Benutzeraktionen, Abbrüche und Abschlussraten auf und ermöglicht so ein tieferes Verständnis der Interaktion von Einzelanwendern mit Formularen.
* **Benutzern ohne technischen Hintergrund Einblicke ermöglichen**: Dank der benutzerfreundlichen Benutzeroberfläche von Adobe Analytics können auch technisch nicht versierte Benutzer auf Formulardaten zugreifen und diese interpretieren, wodurch datengesteuerte Entscheidungen zur Verbesserung der Registrierungserfahrung gefördert werden.
* **Optimierung des Datenerfassungserlebnisses basierend auf der Nutzung**: Unternehmen können mühelos Schmerzpunkte bei der Datenerfassung identifizieren, was zu gezielten Verbesserungen führt, die die Benutzerfreundlichkeit des Formulars verbessern und die erfolgreiche Übermittlung steigern.

## Umfang der adaptiven Forms-Nutzungsmetriken {#scope-of-adaptive-forms-usage-metrics}

Adobe Analytics bietet eine umfassende Palette von Leistungsmetriken für adaptive Forms, die wertvolle Einblicke in die Formularnutzung bieten. Diese Metriken sind:

* **Formularwiedergaben, Formularübermittlungen, Überprüfungsfehler und Unique Visitors**, sodass Sie die Nutzung und Effektivität Ihrer Formulare bewerten können.

* **Besuchereinblicke** die Besuchs- und Sendefrequenzen sowie Unique Visitor-Zählungen umfasst und einen umfassenden Überblick über Ihre Formular-Audience bietet.

* **Gerätetyp** Daten, die Sie über die Geräte informieren, die Benutzer für den Zugriff auf Ihre Formulare verwenden.

* **Geografische Aufgliederung** zeigt die regionale Verteilung der Formularbenutzer an.

* **Traffic-Quellen** und **Beliebte Formulare** Metriken, die aus den Top-Referrer-Domänen und den am häufigsten besuchten Formularen bestehen, helfen Ihnen dabei zu verstehen, woher Ihr Traffic stammt und welche Formulare am beliebtesten sind.

* **Benutzeraktivität in Top-Formularen** bietet Einblicke in Feldbesuche, Formularwiedergaben, Überprüfungsfehler, abgebrochene Formulare und Formularübermittlungen, sodass Sie das Benutzerverhalten analysieren können.

* **Zeitleiste für die Formularbesuchszeit** , die eine zeitleistenbasierte Ansicht der Benutzerinteraktion mit Ihren Formularen bietet.

* **Gebiete, die Besucherunterstützung erfordern** Metriken, die Hilfeansichten, Prüffehlerinstanzen und Feldbesuchsfrequenzen enthalten und hervorheben, wo Benutzer beim Ausfüllen von Formularen Hilfe benötigen.

![Analytics-Bericht](assets/analytics-report.png){width="100%"}


Detaillierte Informationen zu den einzelnen Metriken finden Sie unter [Anzeigen und Verstehen von AEM Forms Analytics-Berichten](/help/forms/view-understand-aem-forms-analytics-reports.md)

## Voraussetzungen {#prerequisites}

<!--
Analytics, Data Collection (Formerly Adobe Launch), and Experience Manager (experience.adobe.com)
-->

Für die Automatisierung des Experience Cloud-Setups ist ein **Adobe Analytics-Lizenz**, **Datenerfassung (früher Adobe Launch)** zur Verwaltung von Tracking-Skripten und **Experience Manager Forms-Lizenz** für optimierte Datenaggregation und Insight-Generierung.

Wenn Sie über eine aktive Lizenz für **Adobe Analytics** und **Experience Manager Forms**, und Sie haben eine Integration mit **Datenerfassung (früher Adobe Launch)** sollten Sie ihre Verfügbarkeit in Ihrer Entwicklerkonsole überprüfen.

Um zu überprüfen, ob die oben genannten für Ihre as a Cloud Service Forms-Umgebung verfügbar sind, besuchen Sie die [Entwicklerkonsole](https://developer.adobe.com/console/projects), navigieren Sie zum Projekt und suchen Sie Ihr Projekt mit der Programm-ID - Umgebungs-ID, beispielsweise für die Umgebung mit URL `https://author-p45913-e175111-cmstg.adobeaemcloud.com/index.html`, Programm-ID - Umgebungs-ID ist `p45913-e175111`. Stellen Sie sicher, dass die Experience Cloud Setup Automation, Adobe Analytics und Experience Platform Launch API aufgelistet sind. Wenn diese aufgelistet sind, können Sie Adobe Analytics für Ihre adaptive Forms aktivieren.

![Voraussetzung für die Integration von Forms Analytics](assets/analytics-aem.png){width="100%"}

<!-- 
>[!NOTE]
> If you have an active licenses for Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API, you should verify their availability within your developer console.
-->

<!-- For more information about your available integrations, see [troubleshooting Adaptive Forms with Analytics Integration](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/view-understand-aem-forms-analytics-reports.html)
-->

## Konfigurieren von Adobe Analytics {#configure-adobe-analytics}

Führen Sie die folgenden Schritte aus, um Adobe Analytics für Ihre adaptive Forms zu aktivieren und zu konfigurieren:

* [Aktivieren von Adobe Analytics für adaptive Forms basierend auf Foundation-Komponenten](#integrate-adobe-analytics-with-aem-forms-for-foundation-component)
* [Aktivieren Sie Adobe Analytics für adaptive Forms basierend auf Kernkomponenten.](#integrate-adobe-analytics-with-aem-forms-for-core-components)

>[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)


<!--
>[!NOTE]
>
> This is the demo video for **Foundation Component**. In **Core Component** you are required to perform similar steps but the container is not chosen for forms.
-->

### Aktivieren von Adobe Analytics mit Adaptive Forms für Foundation-Komponente {#integrate-adobe-analytics-with-aem-forms-for-foundation-component}

1. Erstellen Sie einen Konfigurationscontainer für Cloud Services:
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
   1. Wählen oder erstellen Sie einen Konfigurations-Container aus und aktivieren Sie den Ordner für **[!UICONTROL Cloud-Konfigurationen]**.
   1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.
1. Wechseln Sie in Ihrer AEM-Instanz zu **[Forms]** >> **[Forms und Dokument]**.
1. Wählen Sie **[!UICONTROL Formular]** >> **[!UICONTROL Eigenschaften]**, im **[!UICONTROL Konfigurations-Container]**, wählen Sie den Konfigurationscontainer aus, den Sie erstellt oder in der **[!UICONTROL Konfigurationsbrowser]** in Schritt 1.
1. Wählen Sie das Aufgabenbedienfeld in der linken Leiste aus und klicken Sie auf **Einrichten von Analytics** und **Aktivieren von Adobe Analytics**.
1. Geben Sie den Namen an, den Sie für die Report Suite bevorzugen, klicken Sie auf **[!UICONTROL Nächste]** und **[!UICONTROL Speichern]**.
1. Nachdem Sie das Projekt gespeichert haben, wird das Setup einige Zeit lang ausgeführt, bis Adobe Analytics mit Ihrem adaptiven Formular integriert wurde. Sie können auch die **Integrationsstatus**.

   >[!NOTE]
   >
   >Wenn die Einrichtung länger als 15 Minuten dauert, versuchen Sie erneut, die Analyse für Ihre Formulare zu aktivieren.

1. Wechseln Sie in Ihrer AEM-Instanz zu **[!UICONTROL Forms]** >> **[Forms und Dokument]** und wählen Sie **[!UICONTROL Formular]**, sehen Sie, dass Adobe Analytics in Ihr Formular integriert ist, wie in der Abbildung unten dargestellt.
1. Jetzt können Sie Ihre [Adobe Analytics-Bericht für adaptive Formulare](#view-adobe-analytics-report).

![Integrierte AEM Analytics](assets/analytics-aem-integrated.png){width="100%"}


### Aktivieren von Adobe Analytics mit adaptiver Forms für Kernkomponenten {#integrate-adobe-analytics-with-aem-forms-for-core-components}

1. Wechseln Sie in Ihrer AEM-Instanz zu **[!UICONTROL Forms]** >> **[!UICONTROL Forms und Dokument]** und wählen Sie **[!UICONTROL Formular]**.
1. Wählen Sie das Aufgabenbedienfeld links aus und klicken Sie auf **Einrichten von Analytics** und **Aktivieren von Adobe Analytics**.
1. Geben Sie den Namen an, den Sie für die Report Suite bevorzugen, klicken Sie auf **[!UICONTROL Nächste]** und **[!UICONTROL Speichern]**.
1. Nachdem Sie das Projekt gespeichert haben, wird das Setup einige Zeit lang ausgeführt, bis Adobe Analytics mit Ihrem adaptiven Formular integriert wurde. Sie können auch die **Integrationsstatus**.

   >[!NOTE]
   >
   >Wenn die Einrichtung länger als 15 Minuten dauert, versuchen Sie erneut, die Analyse für Ihre Formulare zu aktivieren.

1. Wechseln Sie in Ihrer AEM-Instanz zu **[!UICONTROL Forms]** >> **[!UICONTROL Forms und Dokument]** und wählen Sie **[!UICONTROL Formular]**, sehen Sie, dass Adobe Analytics in Ihr Formular integriert ist.
1. Jetzt können Sie Ihre [Adobe Analytics-Bericht für adaptive Formulare](#view-adobe-analytics-report).

## Anzeigen des Berichts &quot;Adaptive Forms Adobe Analytics&quot; {#view-adobe-analytics-report}

1. Wechseln Sie in Ihrer AEM-Instanz zu **[!UICONTROL Forms]** >> **[!UICONTROL Forms und Dokument]**.
1. Wählen Sie das Formular aus. Sie sehen, dass Adobe Analytics wie auf der linken Seite gezeigt integriert ist und für Adobe Analytics aktiviert ist.

   ![Bericht anzeigen](assets/activ-aa.png){width="100%"}

1. Klicks **Adobe Analytics** , um Ihren Bericht anzuzeigen und Leistungsdaten zu analysieren.

Informationen zum Verbinden eines adaptiven Formulars mit Adobe Analytics mithilfe der manuellen Methode finden Sie unter [Integrieren von AEM Forms mit Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md).

## Aktivieren von Analytics für adaptive Forms in Sites {#Connect-Analytics-to-Adaptive-Forms-in-Sites}

Durch die Konfiguration der Analyse für Ihr adaptives Formular in AEM Sites können Sie Benutzerinteraktionen und Übermittlungen von Formularen auf Ihrer Seite &quot;Sites&quot;verfolgen. Durch die nahtlose Integration von Analysen in Ihre Sites Forms erhalten Sie wertvolle Einblicke in das Benutzerverhalten, die Konversionsraten und Bereiche, in denen Ihr Formular verbessert werden kann.

### Voraussetzungen {#Prerequisites-to-connect-forms-analytics-to-sites}

Um in Adaptive Forms für AEM Sites eine Verbindung herzustellen und Analysen zu aktivieren, müssen Sie sicherstellen, dass Ihre AEM Sites über eine aktive Adobe Analytics verfügt.

### Verbinden des adaptiven Forms in Sites zur Aktivierung von Analytics {#Connect-analytics-to-adaptive-forms}

Schließen Sie die `customfooterlibs` Client-Bibliothek zur AEM Sites-Seite mithilfe des AEM-/Git-Repository und der Bereitstellungs-Pipeline.

1. Öffnen Sie Ihren [AEM Forms-Archetyp oder Ihr geklontes Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)-Projekt in einem Texteditor. Beispielsweise in Visual Studio Code.

1. Navigieren Sie zur Seite Ihrer Sites, auf der Ihr adaptives Formular vorhanden ist, z. B. In diesem Demoprojekt haben wir `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.

1. Kopieren Sie den Wert von `sling:resourceSuperType`. Der Wert lautet beispielsweise `core/wcm/components/page/v3/page`.

   ![Sling-Ressource](/help/forms/assets/slingresource.png){width="100%"}

1. Erstellen Sie eine ähnliche Struktur am Speicherort `ui.apps/src/main/content/jcr_root/apps` genauso wie `core/wcm/components/page/v3/page`.

   ![Überlagerungsstruktur](/help/forms/assets/overlaystructure.png){width="100%"}

1. Hinzufügen einer `customfooterlibs.html` -Datei.

   ```
   // customheaderlibs.html
   <sly data-sly-use.page="com.adobe.cq.wcm.core.components.models.Page">
   <sly data-sly-test="${page.data && page.dataLayerClientlibIncluded}" data-sly-call="${clientlib.js @ categories='core.forms.components.commons.v1.datalayer', async=true}"></sly>
   </sly>
   ```

   Die `customfooterlibs.html` wird für JavaScript verwendet.

1. [Führen Sie die Pipeline aus](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=de), um die Änderungen bereitzustellen.

### Aktivieren von Form Analytics-Regeln für Forms in Sites {#bind-forms-analytics-rules-to-forms-in-sites}

1. Besuchen Sie die **Adobe Experience Platform-Datenerfassung**.
1. Klicks **Tags** auf der linken Seite.
1. Durchsuchen Sie Ihr Projekt mit der Programm-ID, wie in der Abbildung unten dargestellt, beispielsweise nach der Umgebung mit URL `https://author-p45921-e175111-cmstg.adobeaemcloud.com/index.html`, die Programm-ID lautet `45921`.

   ![Search-your-form-in-data-collection](/help/forms/assets/aep-data-collection.png){width="100%"}

1. Konfiguration hinzufügen für **Formularregeln** und **Datenelemente** wie unten angegeben:

#### Hinzufügen von Formularregeln {#form-rules}

1. Wählen Sie das Formular aus und fügen Sie **Neue Eigenschaft** oben rechts oder klicken Sie auf Ihr Formular.
1. Klicken Sie auf der Eigenschaftenseite auf **Regeln** und wählen Sie Ereignisse für Ihr Formular aus. In der Beispielbild unten ist dies **Formularereignisse**.

   ![Search-your-form-in-data-collection](/help/forms/assets/aep-form-event-properties.png){width="100%"}

1. Wählen Sie alle Ereignisse Ihres Formulars aus und **copy** in der rechten oberen Leiste.
1. Nachdem Sie die **Regel kopieren** -Popup angezeigt, in das Sie Ihre Sites-Seite mit der Projekt-ID durchsuchen, um die Formularregeln einzufügen.

   ![Copy-form-rules](/help/forms/assets/copy-form-rules.png){width="100%"}

1. Klicks **copy** , um die Formularregeln auf die Seite &quot;Sites&quot;einzufügen.

#### Hinzufügen von Datenelementen {#data-elements}

1. Wählen Sie das Formular aus und fügen Sie **Neue Eigenschaft** oben rechts oder klicken Sie auf Ihr Formular.
1. Klicken Sie auf der Eigenschaftenseite auf **Datenelemente** und wählen Sie Ereignisse für Ihr Formular aus.
1. Wählen Sie alle Ereignisse Ihres Formulars aus und **copy** in der oberen rechten Leiste.
1. Nachdem Sie die **Regel kopieren** -Popup angezeigt, in das Sie Ihre Sites-Seite mit der Projekt-ID durchsuchen, um die Formularregeln einzufügen.
1. Klicks **copy** , um die Formularregeln auf die Seite &quot;Sites&quot;einzufügen.

   ![Form-data-elements](/help/forms/assets/form-data-elements.png){width="100%"}

Nachdem Sie Ihre Formular- und Sites-Regeln durch die oben genannten Schritte gebunden haben, führen Sie die folgenden Schritte aus, um Analytics auf der Seite &quot;Sites&quot;für Ihr adaptives Formular zu aktivieren:

1. Klicks **Veröffentlichungsfluss** auf der linken Seite.
1. Klicks **Bibliothek hinzufügen** und geben Sie den gewünschten Namen ein.
1. Im **Umgebung** rechts in der Dropdown-Liste **development**.
1. Klicken Sie auf **Alle geänderten Ressourcen**.
1. Klicks **Speichern und in Entwicklung erstellen**.

![Veröffentlichung in der Entwicklung](/help/forms/assets/publish-to-dev.png){width="100%"}


<!--

## Best Practices

1.    Verify that Adobe Analytics is enabled on all the forms activated for Adobe Analytics.

1.    Check the Adobe Analytics report periodically to gain insights into user behavior and form performance. For instance, you may set the cadence to 15 days or the period you prefer to choose for report analysis. This enables you to improve the forms enrollment experience.

1.    Enable Analytics for all or most of your forms for tracking and analyzing user interaction with your forms and to gain insights into visitor interactions and engagement.

1. Check your forms performance after you update your form fields or components.

1.    Share Analytics report with your peer groups for review, you can schedule your report for a later time.

-->

## Siehe auch {#see-also}

* [Anzeigen und Verstehen der Analyseberichte für adaptive Forms](/help/forms/view-understand-aem-forms-analytics-reports.md)
* [Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Integrieren von AEM Forms mit Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md)
