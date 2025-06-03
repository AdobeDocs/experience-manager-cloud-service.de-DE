---
title: Repository Modernizer (CAM)
description: Erfahren Sie, wie Sie bestehende Projektpakete umstrukturieren und mit der für Adobe Experience Manager as a Cloud Service definierten Projektstruktur kompatibel machen.
feature: Migration
role: Admin
source-git-commit: 317ee65786d48d7b92d95c7c6b8782f617d6e346
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 20%

---


# Repository Modernizer (CAM) {#repo-modernizer-cam}

Repository Modernizer ist ein Service-Programm, das entwickelt wurde, um bestehende Projektpakete umzustrukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden, um mit der Projektstruktur kompatibel zu sein, die für Adobe Experience Manager as a Cloud Service definiert wurde.

## Einführung {#introduction}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für Ihre AEM-Projekte. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind. Im Allgemeinen erfordert AEM eine Trennung von **Inhalt** und **Code** in diskrete Unterpakete, um die Trennung zwischen veränderlichen und unveränderlichen Inhalten zu berücksichtigen. Weitere Informationen über die neue AEM-Projektstruktur für den Cloud Service finden Sie unter [AEM-Projektstruktur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de).

Der Repository Modernizer erstellt eine kompatible AEM Cloud Service-Projektstruktur, indem er die folgende Bereitstellungsstruktur erstellt:

- Das `ui.apps`-Paket wird unter `/apps` bereitgestellt und enthält den gesamten Code.

- `ui.content` Paket wird in zur Laufzeit beschreibbaren Bereichen bereitgestellt (z. B. `/content`, `/conf`, `/home` oder alles, was nicht `/apps` ist) und enthält alle Inhalte und Konfigurationen.

- Das Paket `all` ist ein Container-Paket, das die Unterpakete `ui.apps` und `ui.content` enthält.

>[!NOTE]
>
> Die Projektstruktur basiert auf _Archetyp 48_ für Pakete und deren `pom.xml/filter.xml files`. Weitere Informationen finden Sie unter [Archetype 48](https://github.com/adobe/aem-project-archetype).

Repository Modernizer unterstützt jetzt auch die folgenden Projekttypen:

- **MULTI_PROJECT**: Stellt ein Multimodulprojekt ohne gemeinsames übergeordnetes POM, einen Dispatcher und alle Module dar.
- **SINGLE_**: Stellt ein einzelnes Projekt dar.
- **NESTED_PROJECT**: Stellt ein Multimodulprojekt mit einem gemeinsamen übergeordneten POM, Dispatcher und allen Modulen dar.
- **MONOLITHIC_PROJECT**: Stellt ein Hauptprojekt mit einem oder mehreren Unterprojekten dar.

## Verwenden von Repository Modernizer {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

- Der Repository Modernizer wird jetzt automatisch vom Refaktorierungs-Service auf der Registerkarte „Refaktorierungs-Auftrag“ aufgerufen. Kunden müssen lediglich ihr Projekt hochladen und den Refaktorierungsauftrag mit Trigger versehen - es ist keine zusätzliche Einrichtung erforderlich.

## Fehlercode-Referenz

Wenn bei der Verwendung von Repository Modernizer ein Fehler-Code auftritt, finden Sie in der folgenden Tabelle Details und empfohlene Aktionen.

| Fehler-Code | Meldung | Beschreibung | Benutzeraktion erforderlich? |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| RM-100 | Fehler beim Konvertieren der OSGi-Konfigurationsdatei {0} in das .cfg.json-Format. Überprüfen Sie die vorhandene Konfigurationsdatei, bevor Sie es erneut versuchen. | Dieser Fehler tritt auf, wenn bei der Umwandlung einer OSGi-Konfigurationsdatei in das .cfg.json-Format ein Problem auftritt. | Ja |
| RM-101 | Fehler beim Kopieren von Inhalten aus: {0} | Dieser Fehler tritt auf, wenn beim Versuch, Inhalte aus der angegebenen Quelle zu kopieren, ein Fehler auftritt. | Nein |
| RM-102 | Fehler beim Versuch, die Datei {0} von {1} nach {2} zu verschieben. | Dieser Fehler tritt auf, wenn beim Verschieben einer Datei von einem Speicherort an einen anderen ein Problem auftritt. | Nein |
| RM-103 | Der angegebene Pfad konnte nicht in eine gültige Datei aufgelöst werden: {0} | Dieser Fehler tritt auf, wenn die Datei am angegebenen Speicherort nicht gefunden wird. | Nein |
| RM-104 | Bei der Iteration über den Inhalt von {0} ist ein Fehler aufgetreten. | Dieser Fehler tritt beim Durchlaufen von Dateien oder Verzeichnissen auf und weist auf ein Problem beim Zugriff auf oder bei der Verarbeitung von Inhalten hin. | Nein |
| RM-105 | Fehler beim Analysieren der XML-Datei: {0}. Validieren Sie die XML-Datei, bevor Sie es erneut versuchen. | Dieser Fehler tritt auf, wenn beim Analysieren der XML-Datei ein Fehler auftritt. | Ja |
| RM-106 | Fehler beim Schreiben in die XML-Datei: {0}. | Dieser Fehler tritt auf, wenn beim Schreiben in die XML-Datei ein Problem auftritt. | Nein |
| RM-107 | Keine Inhaltspakete im vorhandenen Projekt gefunden: {0}. Bitte überprüfen, ob das richtige Projekt hochgeladen wurde. | Dieser Fehler weist darauf hin, dass im vorhandenen Projekt keine Inhaltspakete gefunden wurden. | Ja |
| RM-108 | POM-Datei nicht im erwarteten Pfad gefunden: {0}. Es wird erwartet, dass sich die POM-Datei des Projekts oder Moduls direkt als untergeordnete Datei in seinem Verzeichnis befindet. | Dieser Fehler tritt auf, wenn die POM-Datei nicht am erwarteten Speicherort gefunden wird. | Ja |
| RM-109 | Fehler beim Analysieren der Datei pom.xml: {0}. Bitte die POM-Datei validieren und dann erneut versuchen. | Dieser Fehler tritt auf, wenn beim Parsen der Datei „pom.xml“ ein Problem auftritt. | Ja |
| RM-110 | Fehler beim Schreiben in die Datei pom.xml: {0}. | Dieser Fehler tritt auf, wenn ein Problem beim Schreiben in die POM-Datei vorliegt. | Nein |
| RM-111 | Fehler beim Schreiben in die Berichtsdatei. | Dieser Fehler tritt auf, wenn beim Schreiben in die Berichtsdatei ein Fehler auftritt. | Nein |
| RM-112 | {0} wurde in der POM-Datei der Repository-Struktur unter ({1}) nicht gefunden | Dieser Fehler tritt auf, wenn die erwartete Konfiguration nicht in der AEM-Projektarchetypvorlage gefunden wird. | Nein |
| RM-113 | Fehler beim Versuch, die AEM-Projektarchetypvorlagen in das Ziel zu kopieren. | Dieser Fehler tritt auf, wenn beim Kopieren der AEM-Projektarchetypvorlagen in das Ziel ein Problem auftritt. | Nein |
| RM-115 | Fehler beim Herstellen der Verbindung mit Azure Blob Storage. | Dieser Fehler tritt auf, wenn ein Problem beim Herstellen einer Verbindung mit Azure Blob Storage besteht. | Nein |
| RM-116 | Fehler beim Hochladen der Datei {0} in Azure Blob Storage. | Dieser Fehler tritt auf, wenn beim Hochladen einer Datei in Azure Blob Storage ein Problem auftritt. | Nein |
| RM-117 | Fehler beim Versuch, die Datei {0} vom Azure Blob-Speicher herunterzuladen. | Dieser Fehler tritt auf, wenn beim Herunterladen einer Datei aus Azure Blob Storage ein Problem auftritt. | Nein |
| RM-118 | E/A-Fehler bei der Verarbeitung von : {0}. | Dieser Fehler tritt auf, wenn beim Lesen oder Schreiben in eine Projektdatei ein Problem auftritt. | Nein |
| RM-119 | E/A-Fehler beim Versuch, die Ergebnisse für das Hochladen auf Azure zu archivieren. | Dieser Fehler tritt auf, wenn bei der Archivierung der vom Prozess generierten Ergebnisse ein Fehler auftritt. | Nein |
| RM-120 | E/A-Fehler beim Versuch, die Archivierung der bereitgestellten Projekt-ZIP rückgängig zu machen. Bitte überprüfen, ob die angegebene Projekt-ZIP gültig ist. | Dieser Fehler tritt auf, wenn beim Aufheben der Archivierung des angegebenen Kundenprojekts ein Fehler auftritt. | Ja |
| RM-121 | Fehler beim Schreiben in die Konfigurationsdatei. | Dieser Fehler tritt auf, wenn beim Schreiben in die Konfigurationsdatei ein Fehler auftritt. | Nein |
| RM-122 | Nicht unterstützter Anfragetyp: {0}. | Dieser Fehler tritt auf, wenn der Anfragetyp vom System nicht unterstützt wird. Bitte den Anfragetyp überprüfen und erneut versuchen. | Nein |

## Verstehen der Prioritäten des Ergebnisberichts

Beim Herunterladen des vom Tool „Repository Modernizer“ generierten Ergebnisberichts wird jedem Ergebnis eine **Priorität“**. Diese Prioritäten helfen Ihnen, die Dringlichkeit und die Auswirkungen jedes Problems zu verstehen:

| Priorität | Beschreibung |
| -------- | ----------------------------------------------------------------------------------------------- |
| CRITICAL | Muss aufgelöst werden, um das Projekt erfolgreich zu erstellen. |
| HOCH | Sollte aufgelöst werden, um sicherzustellen, dass die Funktionalität in AEM nicht beschädigt wird. |
| NORMAL | Sollte entschlossen werden, um die Vernunft und Vollständigkeit der Modernisierung insgesamt zu gewährleisten. |
| NIEDRIG | Für die manuelle Überprüfung; diese Ergebnisse sind informativer Natur und erfordern möglicherweise kein sofortiges Handeln. |

>[!NOTE]
> 
>Um einen reibungslosen Modernisierungs- und Bereitstellungsprozess sicherzustellen, wird empfohlen, vorrangig Ergebnisse zu ermitteln.
