---
title: Wie kann Adobe Analytics für eine schnelle Analyse eines adaptiven Formulars aktiviert werden?
description: Die Automatisierung der Experience Cloud-Einrichtung hilft Ihnen, Adobe Analytics mit einem adaptiven Formular zu verbinden, um schnell Analysen und Einblicke in die Interaktionen und das Engagement der Besucherinnen und Besucher zu erhalten.
keywords: Aktivieren von Adobe Analytics für ein adaptives Formular mithilfe der Automatisierung der Einrichtung von Experience Cloud, Aktivieren von Adobe Analytics in Forms, Adobe Analytics in Adaptive Forms, Forms Analytics Integration, Forms und Adobe Analytics
feature: Adaptive Forms
role: Admin, User
exl-id: 0e1aa040-08b4-4c1a-b247-ad6fff410187
source-git-commit: a58f7e8de662255e3fce1c168b2293a72a9863df
workflow-type: tm+mt
source-wordcount: '1597'
ht-degree: 98%

---

# (Veraltet) Aktivieren von Adobe Analytics für ein adaptives Formular mithilfe der Experience Cloud-Setup-Automatisierung {#integrate-adobe-analytics-to-aem-forms-with-experience-cloud-setup-automation}

>[!CAUTION]
>
>Die Funktion zur Automatisierung der Einrichtung von Experience Cloud wird nicht mehr unterstützt.


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Dieser Artikel |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/configure-analytics-forms-documents.html?lang=de) |

Die Automatisierung der Experience Cloud-Einrichtung hilft Ihnen, Adobe Analytics mit einem adaptiven Formular zu verbinden, was eine schnelle Analyse der Benutzerinteraktion mit Ihren Formularen ermöglicht und Einblicke in die Interaktionen und das Engagement Besucherinnen und Besucher bietet. Die Automatisierung der Experience Cloud-Einrichtung hilft auch bei der Überwachung der Formularleistung, bei der Metriken wie Abschlusszeiten und Abbruchpunkte bewertet werden. Diese Analyse hilft, Formulare für ein besseres Benutzererlebnis zu optimieren und dabei das Benutzerverhalten anhand des Anmeldestatus (z. B. anonyme Benutzende) zu unterscheiden, um allgemeine Trends und Muster zu identifizieren.

## Vorteile der Integration von Adobe Analytics in Adaptive Forms {#advantages-of-integrating-adobe-analytics-with-aem-forms}

* **Einblicke in das Verhalten der Endbenutzenden**: Adobe Analytics hilft dabei, Einblicke in das Verhalten der Endbenutzenden zu erhalten, zeigt Benutzeraktionen, Abbrüche und Abschlussraten auf und ermöglicht so ein tieferes Verständnis der Interaktion von Einzelpersonen mit Formularen.
* **Ermöglichen von Einblicken für Benutzende ohne technischen Hintergrund**: Dank der benutzerfreundlichen Benutzeroberfläche von Adobe Analytics können auch technisch nicht versierte Benutzende auf Formulardaten zugreifen und diese interpretieren, wodurch datengesteuerte Entscheidungen zur Verbesserung der Registrierungserfahrung gefördert werden.
* **Optimierung des Datenerfassungserlebnisses basierend auf der Nutzung**: Unternehmen können mühelos Schmerzpunkte bei der Datenerfassung identifizieren, was zu gezielten Verbesserungen führt, die die Benutzerfreundlichkeit des Formulars steigern und die Zahl der erfolgreichen Übermittlungen erhöhen.

## Umfang der Nutzungsmetriken von adaptiven Formularen {#scope-of-adaptive-forms-usage-metrics}

Adobe Analytics bietet eine umfassende Palette von Leistungsmetriken für adaptive Formulare, die wertvolle Einblicke in die Nutzung von Formularen liefern. Diese Metriken sind:

* **Formularwiedergaben, Formularübermittlungen, Überprüfungsfehler und Unique Visitors**, sodass Sie die Nutzung und Effektivität Ihrer Formulare bewerten können.

* **Besuchereinblicke**, die die Besuchs- und Absendehäufigkeit sowie die Anzahl der Unique Visitors umfassen und einen umfassenden Überblick über Ihre Formularzielgruppe bieten.

* **Gerätetyp**: Daten, die Sie über die Geräte informieren, die Benutzende für den Zugriff auf Ihre Formulare verwenden.

* **Geografische Aufschlüsselung** zeigt die regionale Verteilung der Benutzenden Ihrer Formulare.

* Die Metriken **Traffic-Quellen** und **Beliebte Formulare**, die aus den am häufigsten verweisenden Domains und den meistbesuchten Formularen bestehen, helfen Ihnen zu verstehen, woher Ihr Traffic stammt und welche Formulare am beliebtesten sind.

* **Die Benutzeraktivität in den Top-Formularen** bietet Einblicke in Feldbesuche, Formularwiedergaben, Validierungsfehler, abgebrochene Formulare und Formularübermittlungen, sodass Sie das Benutzerverhalten analysieren können.

* **Zeitleiste für die mit Formularen verbrachte Zeit**, welche eine zeitleistenbasierte Ansicht der Benutzerinteraktion mit Ihren Formularen bietet.

* **Bereiche, die Besucherunterstützung benötigen**: Metriken, die Hilfeansichten, Validierungsfehler und die Häufigkeit von Besuchen eines Feldes umfassen, zeigen auf, wo Benutzende beim Ausfüllen von Formularen möglicherweise Hilfe benötigen.

![Analytics-Bericht](assets/analytics-report.png){width="100%"}


Ausführliche Informationen zu den einzelnen Metriken finden Sie unter [Ansicht und Verständnis der AEM Forms Analytics-Berichte](/help/forms/view-understand-aem-forms-analytics-reports.md)

## Voraussetzungen {#prerequisites}

<!--
Analytics, Data Collection (Formerly Adobe Launch), and Experience Manager (experience.adobe.com)
-->

Die Automatisierung der Experience Cloud-Einrichtung erfordert eine **Adobe Analytics-Lizenz**, **Datenerfassung (ehemals Adobe Launch)** zur Verwaltung von Tracking-Skripten und eine **Experience Manager Forms-Lizenz** für eine optimierte Datenaggregation und Gewinnung von Erkenntnissen.

Wenn Sie eine aktive Lizenz für **Adobe Analytics** und **Experience Manager Forms** besitzen und eine Integration mit **Datenerfassung (früher Adobe Launch)** haben, sollten Sie deren Verfügbarkeit in Ihrer Developer Console überprüfen.

Um zu überprüfen, ob die oben genannten Funktionen für Ihre Forms as a Cloud Service-Umgebung verfügbar sind, besuchen Sie die [Developer Console](https://developer.adobe.com/console/projects), navigieren Sie zu „Projekt“ und suchen Sie Ihr Projekt mit der Programm-ID – Umgebungs-ID, z. B. für die Umgebung mit der URL `https://author-p45913-e175111-cmstg.adobeaemcloud.com/index.html`, Programm-ID – Umgebungs-ID ist `p45913-e175111`. Stellen Sie sicher, dass die Automatisierung der Experience Cloud-Einrichtung, Adobe Analytics und Experience Platform Launch API aufgelistet sind. Wenn diese aufgelistet sind, können Sie Adobe Analytics für eine schnelle Analyse Ihrer adaptiven Formulare aktivieren.

![Voraussetzungen für die Forms Analytics-Integration](assets/analytics-aem.png){width="100%"}

<!-- 
>[!NOTE]
> If you have an active licenses for Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API, you should verify their availability within your developer console.
-->

<!-- For more information about your available integrations, see [troubleshooting Adaptive Forms with Analytics Integration](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/view-understand-aem-forms-analytics-reports.html?lang=de)
-->

## Konfigurieren von Adobe Analytics {#configure-adobe-analytics}

Führen Sie die folgenden Schritte aus, um Adobe Analytics zu aktivieren und zu konfigurieren, damit Sie Ihre adaptiven Formulare schnell analysieren können:

* [Aktivieren von Adobe Analytics für adaptive Formulare basierend auf Foundation-Komponenten](#integrate-adobe-analytics-with-aem-forms-for-foundation-component)
* [Aktivieren von Adobe Analytics für adaptive Formulare auf der Basis von Kernkomponenten](#integrate-adobe-analytics-with-aem-forms-for-core-components)

>[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)


<!--
>[!NOTE]
>
> This is the demo video for **Foundation Component**. In **Core Component** you are required to perform similar steps but the container is not chosen for forms.
-->

### Aktivieren von Adobe Analytics mit adaptiven Formularen für Foundation-Komponente {#integrate-adobe-analytics-with-aem-forms-for-foundation-component}

1. Erstellen eines Konfigurations-Containers für Cloud-Dienste:
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Wählen oder erstellen Sie einen Konfigurations-Container und aktivieren Sie den Ordner für **[!UICONTROL Cloud-Konfigurationen]**.
   1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.
1. Wechseln Sie in Ihrer AEM-Instanz zu **[Forms]** >> **[Forms und Dokument]**.
1. Wählen Sie Ihr **[!UICONTROL Formular]** >> **[!UICONTROL Eigenschaften]**. Wählen Sie im Bereich **[!UICONTROL Konfigurations-Container]** den Konfigurations-Container, den Sie in Schritt 1 im **[!UICONTROL Konfigurations-Browser]** erstellt oder ausgewählt haben.
1. Wählen Sie das Aufgabenbedienfeld in der linken Leiste aus und klicken Sie auf **Analytics einrichten** und **Adobe Analytics aktivieren**.
1. Geben Sie den Namen an, den Sie für die Report Suite bevorzugen, klicken Sie auf **[!UICONTROL Weiter]** und **[!UICONTROL Speichern]**.
1. Sobald Sie das Projekt gespeichert haben, läuft die Einrichtung einige Zeit, bis die Integration von Adobe Analytics mit Ihrem adaptiven Formular erfolgt. Sie können auch den **Integrationsstatus** überprüfen.

   >[!NOTE]
   >
   >Wenn die Einrichtung länger als 15 Minuten dauert, versuchen Sie erneut, Analytics für Ihre Formulare zu aktivieren.

1. Wechseln Sie in Ihrer AEM-Instanz zu **[!UICONTROL Forms]** >> **[Formulare und Dokument]** und wählen Sie **[!UICONTROL Formular]**. Sie sehen, dass Adobe Analytics in Ihr Formular integriert ist, wie in der Abbildung unten dargestellt.
1. Jetzt können Sie Ihren [Adobe Analytics-Bericht für adaptive Formulare](#view-adobe-analytics-report) ansehen.

![Integriertes AEM Analytics](assets/analytics-aem-integrated.png){width="100%"}


### Aktivieren von Adobe Analytics mit adaptiven Formularen für Kernkomponenten {#integrate-adobe-analytics-with-aem-forms-for-core-components}

1. Wechseln Sie in Ihrer AEM-Instanz zu **[!UICONTROL Forms]** >> **[!UICONTROL Formulare und Dokument]** und wählen Sie **[!UICONTROL Formular]**.
1. Wählen Sie das Aufgabenbedienfeld links aus und klicken Sie auf **Analytics einrichten** und **Adobe Analytics aktivieren**.
1. Geben Sie den Namen an, den Sie für die Report Suite bevorzugen, klicken Sie auf **[!UICONTROL Weiter]** und dann auf **[!UICONTROL Speichern]**.
1. Sobald Sie das Projekt gespeichert haben, läuft die Einrichtung einige Zeit, bis die Integration von Adobe Analytics mit Ihrem adaptiven Formular erfolgt. Sie können auch den **Integrationsstatus** überprüfen.

   >[!NOTE]
   >
   >Wenn die Einrichtung länger als 15 Minuten dauert, versuchen Sie erneut, Analytics für Ihre Formulare zu aktivieren.

1. Wechseln Sie in Ihrer AEM-Instanz zu **[!UICONTROL Formulare]** >> **[!UICONTROL Formulare und Dokument]** und wählen Sie **[!UICONTROL Formular]**. Sie sehen, dass Adobe Analytics in Ihr Formular integriert ist.
1. Jetzt können Sie Ihren [Adobe Analytics-Bericht für adaptive Formulare](#view-adobe-analytics-report) ansehen.

## Anzeigen des Berichts für adaptive Formulare von Adobe Analytics {#view-adobe-analytics-report}

1. Wechseln Sie auf Ihrer AEM-Instanz zu **[!UICONTROL Formulare]** >> **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie Ihr Formular aus. Sie sehen, dass Adobe Analytics integriert ist, wie auf der linken Seite gezeigt, zu den für Adobe Analytics aktivierten Formularen.

   ![Bericht anzeigen](assets/activ-aa.png){width="100%"}

1. Klicken Sie auf **Adobe Analytics**, um Ihren Bericht anzuzeigen und die Leistungsdaten zu analysieren.

Informationen zum Verbinden eines adaptiven Formulars mit Adobe Analytics mithilfe der manuellen Methode finden Sie unter [Integrieren von AEM Forms mit Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md).

## Aktivieren von Analytics für adaptive Formulare in Sites {#Connect-Analytics-to-Adaptive-Forms-in-Sites}

Die Konfiguration von Schnellanalyse für Ihr adaptives Formular in AEM Sites hilft Ihnen, Benutzerinteraktionen und Formularübermittlungen auf Formulare in Ihren Sites-Seiten zu verfolgen. Durch die nahtlose Integration von Analytics in Ihre Sites-Formulare erhalten Sie wertvolle Einblicke in das Benutzerverhalten, die Konversionsraten und Bereiche, in denen Ihr Formular verbessert werden kann.

### Voraussetzungen {#Prerequisites-to-connect-forms-analytics-to-sites}

Um eine Verbindung zu adaptiven Formularen für AEM-Sites herzustellen und Analytics zu aktivieren, müssen Sie sicherstellen, dass Ihre AEM-Sites über ein aktives Adobe Analytics verfügen.

### Verbinden des adaptiven Formulars in Sites zur Aktivierung von Analytics {#Connect-analytics-to-adaptive-forms}

Um ein adaptives Formular in eine AEM Sites-Seite zu integrieren und Analytics für eine Schnellanalyse zu aktivieren, binden Sie die Client-Bibliothek `customfooterlibs` mithilfe des AEM-Archetyps/Git-Repositorys und der Bereitstellungs-Pipeline in die AEM Sites-Seite ein.

1. Öffnen Sie Ihren [AEM Forms-Archetyp oder Ihr geklontes Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)-Projekt in einem Texteditor. Beispielsweise in Visual Studio Code.

1. Navigieren Sie zu der Seite Ihrer Sites, auf der sich Ihr adaptives Formular befindet. In diesem Demoprojekt haben wir zum Beispiel `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.

1. Kopieren Sie den Wert von `sling:resourceSuperType`. Der Wert lautet beispielsweise `core/wcm/components/page/v3/page`.

   ![Sling-Ressource](/help/forms/assets/slingresource.png){width="100%"}

1. Erstellen Sie eine ähnliche Struktur am Speicherort `ui.apps/src/main/content/jcr_root/apps` genauso wie `core/wcm/components/page/v3/page`.

   ![Überlagerungsstruktur](/help/forms/assets/overlaystructure.png){width="100%"}

1. Fügen Sie eine Datei `customfooterlibs.html` hinzu.

   ```
   // customheaderlibs.html
   <sly data-sly-use.page="com.adobe.cq.wcm.core.components.models.Page">
   <sly data-sly-test="${page.data && page.dataLayerClientlibIncluded}" data-sly-call="${clientlib.js @ categories='core.forms.components.commons.v1.datalayer', async=true}"></sly>
   </sly>
   ```

   `customfooterlibs.html` wird für JavaScript verwendet.

1. [Führen Sie die Pipeline aus](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=de), um die Änderungen bereitzustellen.

### Aktivieren von Form Analytics-Regeln für Formulare in Sites {#bind-forms-analytics-rules-to-forms-in-sites}

1. Besuchen Sie die **Adobe Experience Platform-Datenerfassung**.
1. Klicken Sie auf **Tags** auf der linken Seite.
1. Suchen Sie Ihr Projekt mit der Programm-ID, wie in der Abbildung unten dargestellt. Für die Umgebung mit der URL `https://author-p45921-e175111-cmstg.adobeaemcloud.com/index.html` lautet die Programm-ID z. B. `45921`.

   ![Search-your-form-in-data-collection](/help/forms/assets/aep-data-collection.png){width="100%"}

1. Fügen Sie die Konfiguration für **Formularregeln** und **Datenelemente** wie unten angegeben hinzu:

#### Hinzufügen von Formularregeln {#form-rules}

1. Wählen Sie Ihr Formular aus und fügen Sie eine **Neue Eigenschaft** oben rechts hinzu, oder klicken Sie auf Ihr Formular.
1. Klicken Sie auf der Eigenschaftsseite auf **Regeln** und wählen Sie Ereignisse für Ihr Formular aus. Im Beispielbild unten ist es **Formularereignisse**.

   ![Search-your-form-in-data-collection](/help/forms/assets/aep-form-event-properties.png){width="100%"}

1. Wählen Sie alle Ereignisse Ihres Formulars aus und **kopieren** Sie dasjenige in der rechten oberen Leiste.
1. Nach dem Kopieren erscheint ein Popup **Regel kopieren**, in dem Sie Ihre Sites-Seite mit der Projekt-ID durchsuchen können, um die Formularregeln einzufügen.

   ![Copy-form-rules](/help/forms/assets/copy-form-rules.png){width="100%"}

1. Klicken Sie auf **Kopieren**, um die Formularregeln auf der Sites-Seite einzufügen.

#### Hinzufügen von Datenelementen {#data-elements}

1. Wählen Sie Ihr Formular aus und fügen Sie eine **Neue Eigenschaft** oben rechts hinzu, oder klicken Sie auf Ihr Formular.
1. Klicken Sie auf der Eigenschaftenseite auf **Datenelemente** und wählen Sie Ereignisse für Ihr Formular aus.
1. Wählen Sie alle Ereignisse Ihres Formulars aus und **kopieren** Sie sie in der rechten oberen Leiste.
1. Nach dem Kopieren erscheint ein Popup **Regel kopieren**, in dem Sie Ihre Sites-Seite mit der Projekt-ID durchsuchen können, um die Formularregeln einzufügen.
1. Klicken Sie auf **Kopieren**, um die Formularregeln auf der Sites-Seite einzufügen.

   ![Form-data-elements](/help/forms/assets/form-data-elements.png){width="100%"}

Nachdem Sie Ihre Formular- und Sites-Regeln durch die oben genannten Schritte gebunden haben, führen Sie die folgenden Schritte aus, um Analytics auf der Sites-Seite für Ihr adaptives Formular zu aktivieren:

1. Klicken Sie auf **Veröffentlichungsfluss** auf der linken Seite.
1. Klicken Sie auf **Bibliothek hinzufügen** und geben Sie den von Ihnen gewünschten Namen ein.
1. Wählen Sie in der Dropdown-Liste **Umgebung** auf der rechten Seite die Option **Entwicklung**.
1. Klicken Sie auf **Alle geänderten Ressourcen hinzufügen**.
1. Klicken Sie auf **Speichern und in Entwicklung erstellen**.

![publish-to-development](/help/forms/assets/publish-to-dev.png){width="100%"}


<!--

## Best Practices

1.    Verify that Adobe Analytics is enabled on all the forms activated for Adobe Analytics.

1.    Check the Adobe Analytics report periodically to gain insights into user behavior and form performance. For instance, you may set the cadence to 15 days or the period you prefer to choose for report analysis. This enables you to improve the forms enrollment experience.

1.    Enable Analytics for all or most of your forms for tracking and analyzing user interaction with your forms and to gain insights into visitor interactions and engagement.

1. Check your forms performance after you update your form fields or components.

1.    Share Analytics report with your peer groups for review, you can schedule your report for a later time.

-->

## Siehe auch {#see-also}

* [Anzeigen und Verstehen der Analytics-Berichte von adaptiven Formularen](/help/forms/view-understand-aem-forms-analytics-reports.md)
* [Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Integrieren von AEM Forms mit Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md)
