---
title: Bereitschaftsphase in Cloud Acceleration Manager
description: Diese Seite bietet einen Überblick über die Bereitschaftsphase in Cloud Acceleration Manager.
exl-id: 2583985b-0358-433c-9d31-38e2c60dc3dc
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 51%

---

# Bereitschaftsphase in Cloud Acceleration Manager {#readiness-phase-cam}

Nachdem Sie ein Projekt in Cloud Acceleration Manager erstellt haben, können Sie jetzt mit der Bewertung Ihrer aktuellen Adobe Experience Manager (AEM)-Implementierung in der Bereitschaftsphase beginnen.

Die Bereitschaftsphase umfasst:

* [Best-Practices-Analyse](#best-practices-analysis)
* [Planung und Einrichtung](#planning-setup)

Führen Sie die folgenden Schritte aus, um in die Bereitschaftsphase zu gelangen:

1. Klicken Sie auf Ihre Projektkarte.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/cam-landing1.png)

1. Navigieren Sie auf der Projekt-Landingpage zum **Bereitschaft** wie in der folgenden Abbildung dargestellt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Weitere Informationen finden Sie unter Erstellen und Verwalten eines Projekts in Cloud Acceleration Manager .

## Verwenden der Karte „Best-Practices-Analyse“ {#best-practices-analysis}

1. Klicks **Überprüfen** aus dem **Best Practices-Analyse** Karte.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/readiness-2.png)

1. Laden Sie Best Practices Analyzer (BPA) herunter.

   >[!NOTE]
   >Um Auswirkungen auf geschäftskritische Instanzen zu vermeiden, empfiehlt Adobe, BPA in einer Autorenumgebung auszuführen. Die Umgebung sollte der Produktionsumgebung in den Bereichen Anpassungen, Konfigurationen, Inhalte und Benutzeranwendungen so nahe wie möglich sein. Alternativ kann BPA in einem Klon der Autoren-Produktionsumgebung ausgeführt werden.

   1. Navigieren Sie zum [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) und laden Sie den Best Practices Analyzer als ZIP-Datei herunter.

      >[!NOTE]
      >Lesen Sie [Verwenden von Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en#imp-considerations), um zu erfahren, wie Sie BPA ausführen.

   1. Exportieren des Berichts im CSV-Format

1. Klicks **Neuen Bericht hochladen** damit Sie den BPA-Bericht in CAM hochladen können.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-3.png)

   >[!IMPORTANT]
   >Der Bericht kann nicht hochgeladen werden, wenn Sie sich im Inkognito-Modus des Browsers befinden.

1. Nachdem Sie einen neuen Bericht hochgeladen haben, können Sie den Bericht Best Practices-Analyse sehen.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

1. Überprüfen Sie das Dashboard zur Best-Practices-Analyse in CAM. Siehe [Überprüfen des Berichts zur Best Practices-Analyse](#analysis-report) für weitere Details.

   >[!NOTE]
   >Durch das Hochladen eines neuen Berichts werden alle Bewertungen zurückgesetzt.

### Verwenden der Druckvorschau {#print-preview-cam}

Sie können in Cloud Acceleration Manager die Druckvorschau-Option auswählen, um eine druckbare Vorschau der Berichte anzuzeigen oder den Bericht zur einfachen Freigabe in einem PDF-Format zu drucken.

Führen Sie dazu folgende Schritte durch:

1. Klicken Sie auf **Druckvorschau** Symbol.

   ![Bild](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview1.png)

1. Klicken Sie auf der neuen Registerkarte mit dem Bericht in einer druckbaren Vorschau auf **Drucken** , um den Bericht in einem PDF-Format zu drucken.

   >[!IMPORTANT]
   >
   >* Die Option **Als PDF speichern** wird für die oben genannte Funktion empfohlen und unterstützt.
   >* Wenn die Druckschaltfläche des Browsers verwendet wird, wird nur eine Seite gedruckt.

   ![Bild](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview2.png)

### Verwenden von „Trendlinie anzeigen“ {#trendline-view-cam}

Wenn Sie mehr als einen Best Practices Analyzer-Bericht (BPA) in ein Projekt hochladen, können Sie die Option **Trendlinie anzeigen** zum Anzeigen und Vergleichen von Ergebnissen aus historischen BPA-Berichten auswählen.

Gehen Sie wie folgt vor, um Berichte über die Trendlinienoption anzuzeigen:

>[!NOTE]
>Wenn Sie mehr als einen BPA-Bericht in ein Projekt hochladen, wird die **...** Symbol.

1. Navigieren Sie zu Ihrem Projekt und klicken Sie auf **Überprüfen** aus dem **Best Practices-Analyse** in der **Bereitschaft** Phase.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klicken Sie auf **...**.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

   >[!IMPORTANT]
   >Der angezeigte Bericht ist immer der Bericht mit dem neuesten Berichtsdatum.

1. Klicken Sie in der Dropdownliste auf **Trendlinie anzeigen**, wie in der folgenden Abbildung dargestellt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view2.png)

1. Klicken **Trendlinie anzeigen** öffnet die Trendansicht des Berichts.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view3a.png)


   >[!NOTE]
   >Der Trend-Zeilenbericht zeigt die Ergebnisse der historischen BPA-Berichte in einer grafischen Darstellung an.
   >
   >Es werden zwei Diagramme angezeigt, die den Trend der Metrik zeigen:
   > 
   >1. **Berichtsergebnis-Trend**
   >1. **Benutzerdefinierte Komponenten und Vorlagen-Trend**
   >
   >Sie können die grafische Ansicht über die Dropdown-Liste hinzufügen oder ändern, wie in der folgenden Abbildung dargestellt:
   >![image](/help/journey-migration/cloud-acceleration-manager/assets/reports-bpa1.png)


### Überprüfen des Best Practices Analyzer-Berichts {#analysis-report}

Sehen Sie sich die folgenden Karten auf der Seite Bericht zu Best Practices-Analysen an:

![Bild](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Mit jeder Karte können Sie:
>
>* zugehörige Registerkarte öffnen
>* Erstellen von Lesezeichen für alle Berichtregisterkarten (einschließlich Filterung) für die Freigabe oder den künftigen Abruf
>* Verwenden des Detailsymbols, um die Details der einzelnen Berichtsergebnisse anzuzeigen

#### Berichteigenschaften {#report-properties}

Die Karte **Berichteigenschaften** enthält Informationen zu Berichteigenschaften wie Berichtsdatum, Dauer, Filtern, Upload-Datum und AEM-Details (Adobe Experience Manager).

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-properties.png)

#### Berichtsübersicht {#report-overview}

Die Karte **Berichtsübersicht** enthält die Berichtsergebnisse und Schweregrade, die bei der Beurteilung der Bereitschaft für die Umstellung auf AEM as a Cloud Service gelten, wie in der folgenden Abbildung dargestellt.

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-overview.png)

Durch Klicken auf diesen Bericht wird das **Bericht** Registerkarte.

![Bild](/help/journey-migration/cloud-acceleration-manager/assets/report-overview2.png)

Sie können den Bericht nach Wichtigkeit, Untertyp oder Anzahl filtern.

![Bild](/help/journey-migration/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Siehe [Interpretieren des Best Practices Analyzer-Berichts](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=de) um mehr über die Kategorien und Wichtigkeitsstufen der Ergebnisse zu erfahren.

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

1. Klicks **Ansicht** aus dem **Planung und Einrichtung** Karte. Diese Karte enthält alle relevanten Inhalte, die Sie bei der Planung und Einrichtung Ihrer AEM unterstützen.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-view.png)

1. Ein Inhaltskarussell zeigt alle relevanten Informationen für diese Phase der Migration an.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-5-planning.png)

### Löschen eines Best-Practices-Analyseberichts aus der Trendline-Ansicht {#delete-trendline}

>[!IMPORTANT]
>Ein Bericht kann nur gelöscht werden, wenn mehr als ein Bericht in ein Projekt hochgeladen wurde.

1. Navigieren Sie zu Ihrem Projekt und klicken Sie auf **Überprüfen** aus dem **Best Practices-Analyse** in der **Bereitschaft** Phase.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klicken Sie auf **...**.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

1. Klicken Sie in der Dropdownliste auf **Trendlinie anzeigen**, wie in der folgenden Abbildung dargestellt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view2.png)

1. Klicken Sie auf das Löschsymbol im **Trendbericht** angezeigt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view5a.png)

1. Klicks **Löschen** , um den Löschvorgang zu bestätigen.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view6a.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie sich bei Cloud Acceleration Manager anmelden und ein Projekt erstellen, können Sie jetzt den nächsten Schritt im [Implementierungsphase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=en).
