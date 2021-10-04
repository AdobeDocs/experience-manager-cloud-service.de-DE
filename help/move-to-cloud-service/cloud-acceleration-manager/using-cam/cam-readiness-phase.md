---
title: Bereitschaftsphase in Cloud Acceleration Manager
description: Diese Seite bietet einen Überblick über die Bereitschaftsphase in Cloud Acceleration Manager.
exl-id: 91a13cae-4934-42e8-9538-896fd72f5acb
source-git-commit: 090902d65a9bd4c4d83722534a2d9fb78bac314d
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 11%

---

# Bereitschaftsphase in Cloud Acceleration Manager {#readiness-phase-cam}

Nachdem Sie ein Projekt in Cloud Acceleration Manager erstellt haben, können Sie jetzt mit der Bewertung Ihrer aktuellen AEM-Implementierung in der Bereitschaftsphase beginnen.

Die Bereitschaftsphase umfasst:

* [Best Practices-Analyse](#best-practices-analysis)
* [Planung und Einrichtung](#planning-setup)

Gehen Sie wie folgt vor, um zur Bereitschaftsphase zu navigieren:

1. Klicken Sie auf Ihre Projektkarte, um die Projekt-Landingpage zu öffnen.

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-landing1.png)

1. Navigieren Sie zum Abschnitt **Bereitschaft** , wie in der folgenden Abbildung dargestellt.

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-1.png)

   >[!NOTE]
   >Weitere Informationen finden Sie unter Erstellen und Verwalten eines Projekts in Cloud Acceleration Manager .

## Verwenden der Analyse-Karte mit Best Practices {#best-practices-analysis}

Gehen Sie wie folgt vor, um die Karte Best Practices für die Analyse zu verwenden:

1. Klicken Sie auf die Schaltfläche **Überprüfen** in der Karte **Best Practices Analysis** .

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-2.png)

1. Führen Sie diese Schritte aus, um Best Practices Analyzer (BPA) herunterzuladen.

   >[!NOTE]
   >Um Auswirkungen auf geschäftskritische Instanzen zu vermeiden, wird empfohlen, BPA in einer Autoren-Umgebung auszuführen, die der Produktions-Umgebung im Hinblick auf Anpassungen, Konfigurationen, Inhalte und Anwenderprogrammen möglichst nahekommt. Alternativ kann BPA in einem Klon der Autoren-Produktionsumgebung ausgeführt werden.

   1. Navigieren Sie zum Portal [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) und laden Sie den Best Practices Analyzer als ZIP-Datei herunter.

      >[!NOTE]
      >Lesen Sie [Verwenden von Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en#imp-considerations) , um zu erfahren, wie Sie BPA ausführen.

   1. Bericht im CSV-Format exportieren

1. Klicken Sie auf **Laden Sie den neuen Bericht** hoch, um den BPA-Bericht in CAM hochzuladen.

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-3.png)

   >[!IMPORTANT]
   >Der Bericht kann nicht hochgeladen werden, wenn Sie sich im Inkognito-Modus des Browsers befinden.

1. Nachdem Sie einen neuen Bericht hochgeladen haben, wird der Bericht Best Practices-Analyse angezeigt.

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

1. Lesen und lesen Sie das Dashboard Best Practices Analysis in CAM. Weitere Informationen finden Sie im folgenden Abschnitt [Bericht zu Best Practices für die Analyse](#analysis-report) .

   >[!NOTE]
   >Durch das Hochladen eines neuen Berichts werden alle Bewertungen zurückgesetzt.

1. Klicken Sie auf das Symbol **Druckvorschau**, wie unten dargestellt, um die Freigabe zu erleichtern.

   ![Bild](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview1.png)

1. Wenn Sie auf **Druckvorschau** klicken, wird eine neue Registerkarte mit den Berichten geöffnet, die in einer druckbaren Vorschau angezeigt werden. Klicken Sie auf **Print**, um den Bericht zur einfachen Freigabe in ein PDF-Format zu drucken.

   >[!IMPORTANT]
   >* Die Option **Als PDF speichern** wird für die oben genannten Funktionen empfohlen und unterstützt.
   >* Wenn die Druckschaltfläche des Browsers verwendet wird, wird nur eine Seite gedruckt.


   ![Bild](/help/move-to-cloud-service/best-practices-analyzer/assets/bpa-printpreview2.png)

### Überprüfen des Berichts zur Best Practices-Analyse {#analysis-report}

Sehen Sie sich die folgenden Karten auf der Seite Best Practices Analysis Report an:

![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/cam-bpareport.png)

>[!NOTE]
> Jede Karte bietet folgende Möglichkeiten:
>* Klicken Sie auf jede Karte, um die zugehörige Registerkarte zu öffnen
>* Lesezeichen für alle Berichtregisterkarten (einschließlich Filterung) zum Freigeben oder künftigen Abruf
>* Verwenden Sie das Detailsymbol, um die Details der einzelnen Berichtsfindungen anzuzeigen.


#### Berichteigenschaften {#report-properties}

Die Karte **Berichteigenschaften** enthält Informationen zu Berichtseigenschaften wie Berichtsdatum, -dauer, Filter, Upload-Datum und Adobe Experience Manager (AEM)-Details.

![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-properties.png)

#### Berichtübersicht {#report-overview}

Diese Karte **Berichtsübersicht** enthält die Berichtsergebnisse und Schweregrade, die bei der Beurteilung der Bereitschaft zur Umstellung auf AEM als Cloud Service gelten, wie in der folgenden Abbildung dargestellt.

![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview.png)

Wenn Sie auf diesen Bericht klicken, wird der Tab **Bericht** geöffnet.

![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview2.png)

Sie können den Bericht nach Wichtigkeit, Untertyp oder Anzahl filtern.

![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/report-overview3.png)

>[!NOTE]
>Unter [Interpretieren des Berichts &quot;Best Practices Analyzer&quot;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=en) erfahren Sie mehr über die Kategorien von Befunden und die Wichtigkeitsstufen.

#### Best Practices-Bewertung {#best-practices-assessment}

Die Option &quot;Best Practices-Bewertung&quot;bietet eine Bewertung Ihrer aktuellen AEM und bietet Anleitungen zu den nächsten Schritten zur Übernahme AEM Best Practices. Sie können die folgenden Informationen auf dieser Registerkarte überprüfen:

* Übersicht über AEM
* Benutzerdefinierte Komponenten und Vorlagen
* Zusätzliche Ergebnisse
* Langsame Abfragen
* Wartungsaufgaben

#### Bewertung der Migrationskomplexität {#migration-complexity-assessment}

Die Option zur Bewertung der Migrationskomplexität bietet eine Bewertung der Komplexität bei der Migration der bestehenden AEM-Implementierung zu AEM als Cloud Service.

Sie können die folgenden Informationen auf dieser Registerkarte überprüfen:

* Übersicht über AEM
* Bewertung
* Überlegungen zur Inhaltsmigration

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/migration-complexity-1.png)

## Verwenden der Planungs- und Einrichtungskarte {#planning-setup}

In diesem Abschnitt erfahren Sie mehr zur Karte Planung und Einrichtung .

1. Klicken Sie auf die Schaltfläche **Ansicht** auf der Karte **Planung und Einrichtung**. Diese Karte enthält alle relevanten Inhalte, die Ihnen bei der Planung und Einrichtung Ihrer AEM helfen.

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-view.png)

1. In einem Inhaltskarussell werden alle relevanten Informationen für diese Phase der Migration-Journey angezeigt.

   ![Bild](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5-planning.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie sich bei Cloud Acceleration Manager anmelden und ein Projekt erstellen, können Sie nun den nächsten Schritt in der [Implementierungsphase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=en) überprüfen.
