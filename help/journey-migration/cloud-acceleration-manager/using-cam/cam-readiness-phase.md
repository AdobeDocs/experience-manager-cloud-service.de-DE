---
title: Bereitschaftsphase in Cloud Acceleration Manager
description: Diese Seite bietet einen Überblick über die Bereitschaftsphase in Cloud Acceleration Manager.
exl-id: 2583985b-0358-433c-9d31-38e2c60dc3dc
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1057'
ht-degree: 100%

---

# Bereitschaftsphase in Cloud Acceleration Manager {#readiness-phase-cam}

Nachdem Sie ein Projekt in Cloud Acceleration Manager erstellt haben, können Sie jetzt mit der Bewertung Ihrer aktuellen AEM-Implementierung in der Bereitschaftsphase beginnen.

Die Bereitschaftsphase umfasst:

* [Best-Practices-Analyse](#best-practices-analysis)
* [Planung und Einrichtung](#planning-setup)

Führen Sie die folgenden Schritte aus, um in die Bereitschaftsphase zu gelangen:

1. Klicken Sie auf Ihre Projektkarte, um die Projekt-Landingpage zu öffnen.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/cam-landing1.png)

1. Navigieren Sie zum Abschnitt **Bereitschaft**, wie in der folgenden Abbildung dargestellt.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Weitere Informationen finden Sie unter „Erstellen und Verwalten eines Projekts in Cloud Acceleration Manager“.

## Verwenden der Karte „Best-Practices-Analyse“ {#best-practices-analysis}

Gehen Sie wie folgt vor, um die Karte „Best-Practices-Analyse“ zu verwenden:

1. Klicken Sie auf der Karte **Best-Practices-Analyse** auf die Schaltfläche **Überprüfen**.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-2.png)

1. Gehen Sie wie folgt vor, um Best Practices Analyzer (BPA) herunterzuladen.

   >[!NOTE]
   >Um Auswirkungen auf geschäftskritische Instanzen zu vermeiden, wird empfohlen, BPA in einer Autoren-Umgebung auszuführen, die der Produktions-Umgebung im Hinblick auf Anpassungen, Konfigurationen, Inhalte und Anwenderprogrammen möglichst nahekommt. Alternativ kann BPA in einem Klon der Autoren-Produktionsumgebung ausgeführt werden.

   1. Navigieren Sie zum [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-Portal und laden Sie den Best Practices Analyzer als ZIP-Datei herunter.

      >[!NOTE]
      >Lesen Sie [Verwenden von Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=de#imp-considerations), um zu erfahren, wie Sie BPA ausführen.

   1. Exportieren des Berichts im CSV-Format

1. Klicken Sie auf **Neuen Bericht hochladen**, um den BPA-Bericht in CAM hochzuladen.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-3.png)

   >[!IMPORTANT]
   >Der Bericht kann nicht hochgeladen werden, wenn Sie sich im Inkognito-Modus des Browsers befinden.

1. Sobald Sie einen neuen Bericht hochgeladen haben, wird der Bericht zur Best-Practices-Analyse angezeigt.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

1. Überprüfen Sie das Dashboard zur Best-Practices-Analyse in CAM. Weitere Informationen finden Sie im folgenden Abschnitt [Überprüfen des Berichts zur Best-Practices-Analyse](#analysis-report).

   >[!NOTE]
   >Durch das Hochladen eines neuen Berichts werden alle Bewertungen zurückgesetzt.

### Verwenden der Druckvorschau {#print-preview-cam}

Sie können in Cloud Acceleration Manager die Druckvorschau-Option auswählen, um eine druckbare Vorschau der Berichte anzuzeigen oder den Bericht zur einfachen Freigabe in einem PDF-Format zu drucken.

Führen Sie dazu folgende Schritte durch:

1. Klicken Sie auf das Symbol **Druckvorschau**, wie unten dargestellt.

   ![image](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview1.png)

1. Wenn Sie auf **Druckvorschau** klicken, wird eine neue Registerkarte geöffnet, auf der der Bericht wird in einer druckbaren Vorschau angezeigt. Klicken Sie auf **Drucken**, um den Bericht in einem PDF-Format zu drucken.

   >[!IMPORTANT]
   >* Die Option **Als PDF speichern** wird für die oben genannte Funktion empfohlen und unterstützt.
   >* Wenn die Schaltfläche „Drucken“ des Browsers verwendet wird, wird nur eine Seite gedruckt.


   ![image](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview2.png)

### Verwenden von „Trendlinie anzeigen“ {#trendline-view-cam}

Wenn Sie mehr als einen Best Practices Analyzer-Bericht (BPA) in ein Projekt hochladen, können Sie die Option **Trendlinie anzeigen** zum Anzeigen und Vergleichen von Ergebnissen aus historischen BPA-Berichten auswählen.

Gehen Sie wie folgt vor, um Berichte über die Trendlinienoption anzuzeigen:

>[!NOTE]
>Wenn Sie mehr als einen BPA-Bericht in ein Projekt hochladen, wird das Symbol **...** angezeigt.

1. Navigieren Sie zu Ihrem Projekt und klicken Sie auf der Karte **Best-Practices-Analyse** in der Phase **Bereitschaft** auf **Überprüfen**.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klicken Sie auf das Symbol **...**, um die Dropdown-Liste anzuzeigen.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

   >[!IMPORTANT]
   >Der angezeigte Bericht ist immer der Bericht mit dem neuesten Berichtsdatum.

1. Klicken Sie auf **Trendzeile anzeigen**, wie in der Abbildung unten gezeigt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view2.png)

1. Ein Klick auf **Trendzeile anzeigen** öffnet die Trend-Zeilenansicht des Berichts, wie in der folgenden Abbildung dargestellt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view3a.png)


   >[!NOTE]
   >Der Trend-Zeilenbericht zeigt die Ergebnisse der historischen BPA-Berichte in einer grafischen Darstellung an.
   >
   >Es werden zwei Diagramme angezeigt, die den Trend zeigen:
   >1. **Berichtsergebnis-Trend**
   >1. **Benutzerdefinierte Komponenten und Vorlagen-Trend**
   >
   >Sie können die grafische Ansicht über die Dropdown-Liste hinzufügen oder ändern, wie in der folgenden Abbildung dargestellt:
   >![image](/help/journey-migration/cloud-acceleration-manager/assets/reports-bpa1.png)


### Überprüfen des Best Practices Analyzer-Berichts {#analysis-report}

Sehen Sie sich die folgenden Karten auf der Seite „Bericht zur Best-Practices-Analyse“ an:

![image](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Jede Karte bietet folgende Möglichkeiten:
>* Klicken auf die Karte, um die zugehörige Registerkarte zu öffnen
>* Erstellen von Lesezeichen für alle Berichtregisterkarten (einschließlich Filterung) für die Freigabe oder den künftigen Abruf
>* Verwenden des Detailsymbols, um die Details der einzelnen Berichtsergebnisse anzuzeigen


#### Berichteigenschaften {#report-properties}

Die Karte **Berichteigenschaften** enthält Informationen zu Berichteigenschaften wie Berichtsdatum, Dauer, Filtern, Upload-Datum und AEM-Details (Adobe Experience Manager).

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-properties.png)

#### Berichtsübersicht {#report-overview}

Die Karte **Berichtsübersicht** enthält die Berichtsergebnisse und Schweregrade, die bei der Beurteilung der Bereitschaft für die Umstellung auf AEM as a Cloud Service gelten, wie in der folgenden Abbildung dargestellt.

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-overview.png)

Wenn Sie auf diesen Bericht klicken, wird die Registerkarte **Bericht** geöffnet.

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-overview2.png)

Sie können den Bericht nach Wichtigkeit, Untertyp oder Anzahl filtern.

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Unter [Interpretieren des Best Practices Analyzer-Berichts](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=de) erfahren Sie mehr über die Ergebniskategorien und Wichtigkeitsstufen.

#### Best-Practices-Bewertung {#best-practices-assessment}

Die Option zur Best-Practices-Bewertung bietet eine Bewertung Ihrer aktuellen AEM-Instanz und Anleitungen zu den nächsten Schritten zur Übernahme von Best Practices für AEM. Auf dieser Registerkarte können Sie die folgenden Informationen überprüfen:

* Übersicht über die AEM-Instanz
* Benutzerdefinierte Komponenten und Vorlagen
* Zusätzliche Ergebnisse
* Langsame Abfragen
* Wartungsaufgaben

#### Bewertung der Migrationskomplexität {#migration-complexity-assessment}

Die Option zur Bewertung der Migrationskomplexität bietet eine Bewertung der Komplexität bei der Migration der bestehenden AEM-Implementierung zu AEM as a Cloud Service.

Auf dieser Registerkarte können Sie die folgenden Informationen überprüfen:

* Übersicht über die AEM-Instanz
* Bewertung
* Überlegungen zur Inhaltsmigration

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Verwenden der Karte „Planung und Einrichtung“ {#planning-setup}

In diesem Abschnitt erhalten Sie Informationen zur Aktivitätskarte „Planung und Einrichtung“.

1. Klicken Sie auf der Karte **Planung und Einrichtung** auf die Schaltfläche **Ansicht**. Diese Karte enthält alle relevanten Inhalte für die Planung und Einrichtung Ihrer AEM-Migration.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-view.png)

1. Ein Inhaltskarussell zeigt alle relevanten Informationen für diese Phase der Migration an.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-5-planning.png)

### Löschen eines Best-Practices-Analyseberichts {#delete-trendline}

Gehen Sie wie folgt vor, um einen Bericht aus der Trendlinienansicht zu löschen:

>[!IMPORTANT]
>Ein Bericht kann nur gelöscht werden, wenn mehr als ein Bericht in ein Projekt hochgeladen wurde.

1. Navigieren Sie zu Ihrem Projekt und klicken Sie auf der Karte **Best-Practices-Analyse** in der Phase **Bereitschaft** auf **Überprüfen**.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klicken Sie auf das Symbol **...**, um die Dropdown-Liste anzuzeigen.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

1. Klicken Sie auf **Trendlinie anzeigen**, wie in der Abbildung unten gezeigt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view2.png)

1. Klicken Sie auf das Löschsymbol im **Trendlinienbericht**.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view5a.png)

1. Klicken Sie auf **Löschen**, um das Löschen zu bestätigen.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view6a.png)

## Wie geht es weiter {#whats-next}

Sobald Sie wissen, wie Sie sich bei Cloud Acceleration Manager anmelden und ein Projekt erstellen, können Sie sich mit dem nächsten Schritt beschäftigen: der [Implementierungsphase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=de).
