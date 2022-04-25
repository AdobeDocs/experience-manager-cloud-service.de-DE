---
title: Versionshinweise für Cloud Manager 2022.4.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2022.4.0 in AEM as a Cloud Service.
feature: Release Information
source-git-commit: 53c0e566525c0c3a301bde85f71a43129bb85afc
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 48%

---


# Versionshinweise für Cloud Manager 2022.4.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager 2022.4.0 AEM as a Cloud Service dokumentiert.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2022.4.0 wurde am AEM as a Cloud Service 7. April 2022 veröffentlicht. Die nächste Version soll am 5. Mai 2022 veröffentlicht werden.

## Neue Funktionen {#what-is-new}

* Verbesserungen an der Dauer und Erfolgsrate der Pipeline-Erstellungsschritte wurden implementiert und werden schrittweise bis zum April für alle Kunden eingeführt.
* Sie können jetzt eine Git-Verzweigung einfach finden, indem Sie die ersten Zeichen des Namens in das Eingabefeld im Pipeline-Assistenten zum Hinzufügen und Bearbeiten eingeben und aus den vorgeschlagenen Übereinstimmungen für beide auswählen [production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) und [Nicht-Produktion](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) Pipelines.
* Kurz nach der Veröffentlichung im April wird Indien bei der Definition der Cloud-Region während der Erstellung von Umgebungen zur Auswahl stehen.
* Die Seite **Pipelines** bietet jetzt Seitennummerierung, um die Benutzerfreundlichkeit für Programme mit einer großen Anzahl von Pipelines zu verbessern.
   * In der Tabelle werden 50 Zeilen pro Seite angezeigt.
* Der von Cloud Manager verwendete [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) wurde auf Version 36 aktualisiert.
* Oracle JDK ist jetzt das Standard-JDK für Entwicklung und Ausführung von AEM. Der Build-Prozess von Cloud Manager wechselt automatisch zur Verwendung von Oracle JDK, auch wenn in der Maven-Toolchain explizit eine alternative Option ausgewählt ist.
   * Weitere Informationen zum Umstieg auf Oracle JDK finden Sie in der [Dokumentation zur Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support).
   * In den [häufig gestellten Fragen zur Java-Support-Richtlinie für Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) finden Sie Antworten auf häufige Fragen zu diesem Wechsel.
* Die Pipelineausführung schlägt jetzt schneller fehl, indem ältere AEM während des Validierungsschritts erkannt werden. Benutzern wird in der Benutzeroberfläche eine Meldung angezeigt, die sie anleitet.

## Fehlerbehebungen {#bug-fixes}

* Das im UI-Test -Schritt erstellte Protokoll kann jetzt über die Benutzeroberfläche heruntergeladen werden.
* Web-Tier-Konfigurationspipelines können jetzt nur Pakete aus Web-Tier-Konfigurationsausführungen wiederverwenden.
* Den Meldungen in der Benutzeroberfläche zur Aktualisierung von AEM in einer veralteten Umgebung wurde mehr Klarheit hinzugefügt.
