---
title: Erste Schritte mit dem Editor für interaktive Kommunikation (IC)
description: Interaktive Kommunikation ermöglicht es Unternehmen, personalisierte, datengesteuerte Kommunikation zu entwerfen und bereitzustellen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: b30b3634-0457-4c29-84d3-78f1429b98d1
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 7%

---

# Erste Schritte mit dem Editor für interaktive Kommunikation (IC)

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

Der **Editor für interaktive Kommunikation** in Adobe Experience Manager (AEM) Forms ermöglicht es Unternehmen, personalisierte, datengesteuerte Kommunikationen wie Auszüge, Rechnungen und Briefe über digitale Kanäle und Druckkanäle hinweg zu entwerfen und bereitzustellen. Dieses Handbuch bietet einen Überblick über die ersten Schritte - vom Onboarding bis zur Navigation in der Benutzeroberfläche des IC-Editors.


## Onboarding und Zugriff

### Zugriffsanforderungen

Um die interaktive Kommunikation zu verwenden, stellen Sie sicher, dass Ihre AEM Forms as a Cloud Service-Umgebung das **AEM Forms-Add-on** enthält und dass Ihr Konto über die entsprechenden Berechtigungen verfügt.

### Browser überprüfen

Um die unterstützten Browser und Client-Plattformen zu erfahren, folgen Sie dem verknüpften Artikel [Unterstützte Client-Plattformen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/overview/supported-platforms)

>[!NOTE]
>
> **Unterstützung für Browser mit schnellen Versionszyklen:**
> Die Versionen von Firefox, Chrome und Edge werden regelmäßig aktualisiert. Adobe ist bestrebt, die Unterstützungsebene wie oben aufgeführt für die künftigen Versionen dieser Browser aufrechtzuerhalten.

### Konfigurieren von Benutzerrollen und Berechtigungen

Der Zugriff auf IC Editor-Funktionen wird durch [Benutzerrollen innerhalb von AEM](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions) gesteuert. Im Folgenden finden Sie die Schlüsselrollen, die bei der Erstellung und Verwaltung interaktiver Kommunikationen eine Rolle spielen:

| **Rolle** | **Beschreibung** | **Schlüsselberechtigungen** |
| --------------------- | ---------------------------------------------------------- | -------------------------------------------- |
| **Formularautor** | Erstellt und bearbeitet interaktive Kommunikationen. | ICs erstellen, bearbeiten, in der Vorschau anzeigen und veröffentlichen. |
| **Vorlagenerstellung** | Entwirft wiederverwendbare Vorlagen für interaktive Kommunikation. | Erstellen und sperren Sie Vorlagen, definieren Sie Layouts. |
| **Administrator** | Verwaltet Benutzerzugriff, Berechtigungen und Konfigurationen. | Rollen zuweisen, Vorlagen verwalten, ICs veröffentlichen. |
| **FDM-Autor** | [Erstellt und verwaltet Formulardatenmodelle (FDM) ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/create-form-data-models) Datenintegration. | Erstellen, Bearbeiten und Konfigurieren von Datenquellen und Modellen. |

>[!NOTE]
>
> Stellen Sie sicher, dass Benutzende Teil der entsprechenden AEM-Gruppen sind (z. B. `forms-user`, `fdm-author`, `template-authors`), um auf die entsprechenden Funktionen zuzugreifen.

## Zugriff auf den IC-Editor

1. Melden Sie sich bei Ihrer **AEM Forms as a Cloud Service**-Instanz an.
2. Navigieren Sie zu **Forms > Interaktive Kommunikation**.
3. Klicken Sie **Erstellen** → **Interaktive Kommunikation**.
4. Wählen Sie **Vorlage** konfigurieren Sie Datenquellen und klicken Sie auf **Erstellen**, um den **Editor für interaktive Kommunikation** zu öffnen.

Der Editor bietet eine einheitliche Umgebung für das Entwerfen, Anzeigen und Verwalten von Druck- und Webversionen der Kommunikation.

## Navigieren in der Benutzeroberfläche

Die Benutzeroberfläche **Editor für interaktive**) bietet Autorinnen und Autoren intuitiven Zugriff auf alle Design-Tools und Konfigurationsoptionen.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/navigate-the-interface.png)

### &#x200B;1. Symbolleiste oben

![IC-Dokument suchen](/help/forms/interactive-communication/assets/tool-bar.png)

**Location:** oberster Abschnitt

**Zweck:** Ermöglicht den Zugriff auf die Umgebung und globale Aktionen.

**Enthält:**

Zeigt die **Adobe Experience Cloud-Umgebung** (z. B. Staging) zusammen mit den **Projekttitel**, **Beta-**, **Benachrichtigungen** und **Profilsteuerelementen** für die Verwaltung von Benutzereinstellungen und Umgebungszugriff.

### &#x200B;2. Registerkartenleiste (Design/Master-Registerkarten und Dateisteuerelemente)

![IC-Dokument suchen](/help/forms/interactive-communication/assets/tab-bar.png)

**Speicherort:** unter der oberen Kopfzeile

**Zweck:** Verwalten von Ansichten und Kommunikationsdateien.

**Enthält:**

**Registerkarten** Wechseln Sie zwischen **Entwurfsansicht** und **Masterseitenansicht** für Layout und wiederverwendbares Elementdesign

**Dateiname:** Zeigt den Titel der aktuellen Kommunikation an (z. B. ic-11)

**Steuerelemente anzeigen:** Optionen wie Regel, Erstellung, Zoom (85 %), Rückgängig/Wiederholen, Löschen, PDF-Vorschau und Speichern

### &#x200B;3. Linkes Bedienfeld (Navigations- und Komponenten-Tools)

![IC-Dokument suchen](/help/forms/interactive-communication/assets/left-panel.png)

**Speicherort** Linke Seite der Benutzeroberfläche

**Zweck** Zugriff auf Projektstruktur, wiederverwendbare Assets und Datenbindungen.

**Enthält:**

* **Startseite:** Leitet den Benutzer zum Hauptbildschirm der interaktiven Kommunikation (IC), auf dem Sie vorhandene ICs und Ordner anzeigen und verwalten können.

* **Menübereich** Zeigt ansichtsbezogene Optionen wie Lineale, Objektgrenzen, Am Raster ausrichten, Am Objekt ausrichten und XDP-Importfunktion an.

* **Hierarchieansicht:** Zeigt die Komponentenstruktur der Kommunikation an und zeigt die Organisation von Seiten, Bereichen und Teilformularen an.

* **Komponentenbibliothek:** Enthält Design-Elemente wie Text, Bild, Teilformular und Barcode, die auf die Arbeitsfläche gezogen werden können.

* **Fragmente:** Ermöglicht die Wiederverwendung vordefinierter Design- und Inhaltsbausteine in mehreren Kommunikationen.

* **Datenmodell:** die Kommunikation mit den zugrunde liegenden Formulardatenmodellen (FDM), um dynamische Daten zu binden.

### &#x200B;4. Central Workspace (Design-Arbeitsfläche)

![IC-Dokument suchen](/help/forms/interactive-communication/assets/canvas.png)

**Speicherort** Mitte der Schnittstelle

**Zweck:** Primärer Arbeitsbereich zum Entwerfen interaktiver Kommunikationen.

**Funktionen:**

* Drag-and-Drop von Komponenten aus der Bibliothek

* Anordnen und Formatieren des visuellen Layouts

* Hinzufügen oder Bearbeiten von Seiten, Teilformularen und Feldern

* Navigieren zwischen Seiten (z. B. „1 von 1„) mithilfe der Steuerelemente unten links

* Vorschau des endgültigen Layouts vor der Veröffentlichung

### &#x200B;5. Rechter Bereich (Eigenschaftenbereich)

![IC-Dokument suchen](/help/forms/interactive-communication/assets/right-panel.png)

**Standort** Rechte Bildschirmseite

**Zweck:** Anpassen des Verhaltens und Stils von Komponenten.

**Enthält:**

* Allgemeine Einstellungen (Name, Typ, Fluss/Position)

* Layout- und Darstellungsoptionen

* Steuerelemente für Paginierung, Position, Präsenz und Datenbindung
