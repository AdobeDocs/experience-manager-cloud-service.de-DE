---
title: Bereitschaftsphase in Cloud Acceleration Manager
description: Diese Seite bietet einen Überblick über die Bereitschaftsphase in Cloud Acceleration Manager.
exl-id: 2583985b-0358-433c-9d31-38e2c60dc3dc
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: ht
source-wordcount: '1045'
ht-degree: 100%

---

# Bereitschaftsphase in Cloud Acceleration Manager {#readiness-phase-cam}

Nachdem Sie ein Projekt in Cloud Acceleration Manager (CAM) erstellt haben, können Sie jetzt mit der Bewertung Ihrer aktuellen Adobe Experience Manager-Implementierung (AEM) in der Bereitschaftsphase beginnen.

Die Bereitschaftsphase umfasst:

* [Best-Practices-Analyse](#best-practices-analysis)
* [Planung und Einrichtung](#planning-setup)

Führen Sie die folgenden Schritte aus, um in die Bereitschaftsphase zu gelangen:

1. Klicken Sie auf Ihre Projektkarte.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/cam-landing1.png)

1. Navigieren Sie auf der Landingpage des Projekts zum Abschnitt **Bereitschaft**, wie in der Abbildung unten gezeigt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Weitere Informationen finden Sie unter „Erstellen und Verwalten eines Projekts in Cloud Acceleration Manager“.

## Verwenden der Karte „Best-Practices-Analyse“ {#best-practices-analysis}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_bpa"
>title="Best-Practices-Analyse-Bericht"
>abstract="Der BPA-Bericht kann in CAM hochgeladen werden, um eine Analyse der Migration zu AEM as a Cloud Service zu erstellen."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer" text="Verwenden von Best Practices Analyzer"

1. Klicken Sie in der Karte **Best Practices-Analyse** auf **Überprüfen**.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/readiness-2.png)

1. Laden Sie Best Practices Analyzer (BPA) herunter.

   >[!NOTE]
   >Um Auswirkungen auf geschäftskritische Instanzen zu vermeiden, empfiehlt Adobe, BPA in einer Autorenumgebung auszuführen. Die Umgebung sollte der Produktionsumgebung in den Bereichen Anpassungen, Konfigurationen, Inhalte und Benutzeranwendungen so nahe wie möglich kommen. Alternativ kann BPA in einem Klon der Autoren-Produktionsumgebung ausgeführt werden.

   1. Navigieren Sie zum [Software-Verteilungs](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html?fulltext=best*)-Portal und laden Sie den Best Practices Analyzer als ZIP-Datei herunter.

      >[!NOTE]
      >Lesen Sie [Verwenden von Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=de#imp-considerations), um zu erfahren, wie Sie BPA ausführen.

1. Klicken Sie in CAM auf **Upload-Schlüssel abrufen**, damit Sie den Schlüssel erhalten, mit dem Sie Ihr System so konfigurieren, dass BPA-Berichte automatisch direkt in CAM hochgeladen werden.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/readiness-3b.png)

   >[!IMPORTANT]
   >Der Bericht kann nach wie vor manuell hochgeladen werden, aber mithilfe des Upload-Schlüssels wird der Vorgang optimiert. Beachten Sie, dass der Bericht nicht manuell hochgeladen werden kann, wenn Sie sich im Inkognito-Modus des Browsers befinden.

1. Nachdem ein neuer Bericht hochgeladen wurde, können Sie den Best-Practices-Analyse-Bericht in CAM sehen.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

   >[!NOTE]
   >Beim Hochladen mehrerer unterschiedlicher Berichte wird immer der Bericht mit dem jüngsten Erstellungsdatum (nicht Upload-Datum) detailliert angezeigt.

1. Überprüfen und erkunden Sie das Dashboard zur Best-Practices-Analyse in CAM. Siehe [Überprüfen des Berichts zur Best Practices-Analyse](#analysis-report) für weitere Details.

   >[!NOTE]
   >Durch das Hochladen eines neuen Berichts werden alle Bewertungen zurückgesetzt, wenn dieser neuer als der zuvor geladene Bericht ist.

### Verwenden der Druckvorschau {#print-preview-cam}

Sie können in Cloud Acceleration Manager die Druckvorschau-Option auswählen, um eine druckbare Vorschau der Berichte anzuzeigen oder den Bericht zur einfachen Weitergabe in einem PDF-Format zu drucken.

Führen Sie dazu folgende Schritte durch:

1. Klicken Sie auf die Aktion **Druckvorschau**.

   ![Bild](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview1b.png)

1. Klicken Sie auf der neuen Registerkarte mit dem Bericht in einer druckbaren Vorschau auf **Drucken**, um den Bericht in einem PDF-Format zu drucken.

   >[!IMPORTANT]
   >
   >* Die Option **Als PDF speichern** wird für die oben genannte Funktion empfohlen und unterstützt.
   >* Wenn die Schaltfläche „Drucken“ des Browsers verwendet wird, wird nur eine Seite gedruckt.

   ![Bild](/help/journey-migration/best-practices-analyzer/assets/bpa-printpreview2.png)

### Verwenden von „Trendlinie anzeigen“ {#trendline-view-cam}

Wenn Sie mehr als einen unterschiedlichen Best Practices Analyzer(BPA)-Bericht in ein Projekt hochladen, können Sie durch Auswahl der Option **Trend-Linie anzeigen** die Ergebnisse aus historischen BPA-Berichten anzeigen und vergleichen.

Gehen Sie wie folgt vor, um Berichte über die Trend-Linien-Option anzuzeigen:

>[!NOTE]
>Wenn Sie mehr als einen unterschiedlichen BPA-Bericht in ein Projekt hochladen, wird das Symbol **...** angezeigt. Berichte gelten als identisch (nicht unterschiedlich), wenn Host und Erstellungszeit identisch sind.

1. Navigieren Sie zu Ihrem Projekt und klicken Sie auf der Karte **Best Practices-Analyse** in der Phase **Bereitschaft** auf **Überprüfen**.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klicken Sie in der Dropdown-Liste **Ansicht** auf **Trend-Linienbericht**, wie in der Abbildung unten gezeigt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1b.png)

1. Wenn Sie auf **Trend-Linienbericht** klicken, wird die Trend-Linienansicht des Berichts geöffnet.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view3a.png)


   >[!NOTE]
   >Der Trend-Zeilenbericht zeigt die Ergebnisse der historischen BPA-Berichte in einer grafischen Darstellung an.
   >
   >Es werden zwei Diagramme angezeigt, die den Trend zeigen:
   > 
   >1. **Berichtsergebnis-Trend**
   >1. **Benutzerdefinierte Komponenten und Vorlagen-Trend**
   >
   >Sie können die grafische Ansicht über die Dropdown-Liste hinzufügen oder ändern, wie in der folgenden Abbildung dargestellt:
   >![image](/help/journey-migration/cloud-acceleration-manager/assets/reports-bpa1.png)


### Überprüfen des Best Practices Analyzer-Berichts {#analysis-report}

Sehen Sie sich die folgenden Karten auf der Seite „Bericht zur Best Practices-Analyse“ an:

![Bild](/help/journey-migration/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Mit jeder Karte können Sie:
>
>* die zugehörige Registerkarte öffnen
>* Erstellen von Lesezeichen für alle Berichtregisterkarten (einschließlich Filterung) für die Freigabe oder den künftigen Abruf
>* Verwenden des Detailsymbols, um die Details der einzelnen Berichtsergebnisse anzuzeigen

#### Berichteigenschaften {#report-properties}

Die Karte **Berichteigenschaften** enthält Informationen zu Berichteigenschaften wie Berichtsdatum, Dauer, Filtern, Upload-Datum und AEM-Details (Adobe Experience Manager).

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-properties.png)

#### Berichtsübersicht {#report-overview}

Die Karte **Berichtsübersicht** enthält die Berichtsergebnisse und Schweregrade, die bei der Beurteilung der Bereitschaft für die Umstellung auf AEM as a Cloud Service gelten, wie in der folgenden Abbildung dargestellt.

![image](/help/journey-migration/cloud-acceleration-manager/assets/report-overview.png)

Wenn Sie auf diesen Bericht klicken, öffnet sich die Registerkarte **Bericht**.

![Bild](/help/journey-migration/cloud-acceleration-manager/assets/report-overview2.png)

Sie können den Bericht nach Wichtigkeit, Untertyp oder Anzahl filtern.

![Bild](/help/journey-migration/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Unter [Interpretieren des Best Practices Analyzer-Berichts](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=de) erfahren Sie mehr über die Ergebniskategorien und Wichtigkeitsstufen.

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

1. Klicken Sie auf der Karte **Planung und Einrichtung** auf **Ansicht**. Diese Karte enthält alle relevanten Inhalte, die Ihnen helfen, Ihre AEM-Migration zu planen und einzurichten.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-view.png)

1. Ein Inhaltskarussell zeigt alle relevanten Informationen für diese Phase der Migration an.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/readiness-5-planning.png)

### Löschen eines Best Practices-Analyseberichts aus der Trend-Linienansicht {#delete-trendline}

>[!IMPORTANT]
>Ein Bericht kann nur gelöscht werden, wenn mehr als ein Bericht in ein Projekt hochgeladen wurde.

1. Navigieren Sie zu Ihrem Projekt und klicken Sie auf der Karte **Best Practices-Analyse** in der Phase **Bereitschaft** auf **Überprüfen**.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1a.png)

1. Klicken Sie auf **…**

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1.png)

1. Klicken Sie in der Dropdown-Liste auf **Trend-Linie anzeigen**, wie in der Abbildung unten gezeigt.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view1b.png)

1. Klicken Sie auf das Löschsymbol im Bildschirm **Trend-Linienbericht**.

   ![Bild](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view5a.png)

1. Klicken Sie auf **Löschen**, um den Löschvorgang zu bestätigen.

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/trendline-view6a.png)

## Wie es weitergeht: {#whats-next}

Sobald Sie wissen, wie Sie sich bei Cloud Acceleration Manager anmelden und ein Projekt erstellen, können Sie sich mit dem nächsten Schritt beschäftigen: der [Implementierungsphase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=de).
