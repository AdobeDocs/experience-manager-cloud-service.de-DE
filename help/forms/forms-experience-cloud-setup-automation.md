---
title: Aktivieren Sie Adobe Analytics für ein adaptives Formular mithilfe der Automatisierung des Experience Cloud-Setups.
description: Experience Cloud Setup Automation hilft, Adobe Analytics mit einem adaptiven Formular zu verbinden. Es hilft beim Tracking und Analysieren der Benutzerinteraktion mit einem adaptiven Formular und bietet Einblicke in die Interaktionen und Interaktionen der Besucher.
source-git-commit: 96b3986f73ab71bad02b00ddc699aeecd498aebd
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 2%

---


# Aktivieren Sie Adobe Analytics für ein adaptives Formular mithilfe der Automatisierung des Experience Cloud-Setups. {#integrate-adobe-analytics-to-aem-forms-with-experience-cloud-setup-automation}

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

![Analytics-Bericht](assets/analytics-report.png)


Detaillierte Informationen zu den einzelnen Metriken finden Sie unter [Anzeigen und Verstehen von AEM Forms Analytics-Berichten](/help/forms/view-understand-aem-forms-analytics-reports.md)

## Voraussetzungen {#prerequisites}

<!--
Analytics, Data Collection (Formerly Adobe Launch), and Experience Manager (experience.adobe.com)
-->

Für die Automatisierung des Experience Cloud-Setups in Adobe Experience Manager Forms ist ein **Adobe Analytics-Lizenz**, **Datenerfassung (früher Adobe Launch)** zur Verwaltung von Tracking-Skripten und Integration mit der **Experience Platform Launch (API)** für optimierte Datenerfassung und Erstellung von Einblicken.

Wenn Sie über eine aktive Lizenz für Experience Cloud Setup Automation, Adobe Analytics und Experience Platform Launch API verfügen, sollten Sie deren Verfügbarkeit in Ihrer Entwicklerkonsole überprüfen.

Um zu überprüfen, ob die oben genannten für Ihre as a Cloud Service Forms-Umgebung verfügbar sind, besuchen Sie die [Entwicklerkonsole](https://developer.adobe.com/console/projects), navigieren Sie zum Projekt und suchen Sie Ihr Projekt mit der Programm-ID, beispielsweise für die Umgebung mit URL `https://author-p45913-e175111-cmstg.adobeaemcloud.com/index.html`, die Programm-ID lautet `p45913-e175111`. Stellen Sie sicher, dass die Experience Cloud Setup Automation, Adobe Analytics und Experience Platform Launch API aufgelistet sind. Wenn diese aufgelistet sind, können Sie Adobe Analytics für Ihre adaptive Forms aktivieren.

![Voraussetzung für die Integration von Forms Analytics](assets/analytics-aem.png)

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

![Integrierte AEM Analytics](assets/analytics-aem-integrated.png)

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

   ![Bericht anzeigen](assets/activ-aa.png)

1. Klicks **Adobe Analytics** , um Ihren Bericht anzuzeigen und Leistungsdaten zu analysieren.

