---
title: Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation
description: Entdecken Sie die zugehörige Benutzeroberfläche im Editor für interaktive Kommunikation, indem Sie kundenorientierten Agenten die Erstellung personalisierter, konformer Kommunikationen ermöglichen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 234b6dc747bbba21e9249d526bf894860572dfe5
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 3%

---


# Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

Die **Associate-Benutzeroberfläche** ist eine spezielle, vereinfachte Benutzeroberfläche, die auf dem Editor für interaktive Kommunikation (IC) aufbaut. Es wurde für kundenorientierte Fachleute wie Außendienstmitarbeiter und Service-Agenten entwickelt, um während Live-Interaktionen in Echtzeit personalisierte, konforme und genaue Kommunikation zu generieren.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/associate-ui-preview.png)

## Benutzeroberfläche zuordnen

Die Benutzeroberfläche von Associate bietet einen sauberen, aus zwei Bereichen bestehenden Arbeitsbereich, der eine schnelle und sichere Kommunikationserstellung ermöglicht:

### Linkes Bedienfeld: Dateneingabe

- Mitarbeiter geben kundenspezifische Informationen ein oder bestätigen diese.
- Validierungen, Hilfstexte und Pflichtfelder dienen als Anleitung für die korrekte Eingabe.

### Rechtes Bedienfeld: Echtzeitvorschau

- Zeigt eine sofortige Vorschau des endgültigen Dokuments an.
- Wird automatisch aktualisiert, wenn der Associate Daten eingibt.

### Sofortige Dokumenterstellung

- Abgeschlossene Kommunikation erzeugen oder herunterladen.

## Benutzerrollen und Zuständigkeiten

Die Associate-Benutzeroberfläche wird von drei Kernrollen gesteuert, die jeweils unterschiedliche Zuständigkeiten haben:

### 1. Administrator

Verantwortlich für die Systemeinrichtung, Governance, Backend-Integrationen und den Benutzerzugriff.

| Verantwortung | Fokus |
|---------------|-------|
| Systemkonfiguration | Richtet die Kern-Infrastruktur, Benutzergruppen, Formulardatenmodelle (FDM), Ausgabe ein. |
| Governance und Sicherheit | Verwaltet Benutzerberechtigungen und stellt die Systemkonformität sicher. |
| Integrationsverwaltung | Pflegt Backend-Integrationen und Live-Kundendatenverbindungen. |

### &#x200B;2. Autor

Entwirft und verwaltet die interaktive Kommunikation über die Benutzeroberfläche „Verknüpfen“. ß

| Verantwortung | Fokus |
|---------------|-------|
| IC-Authoring und -Design | Erstellt Layout, Branding und eine konforme Dokumentstruktur. |
| Feldkonfiguration | Ordnet Datenfelder zu und definiert bearbeitbare, obligatorische und schreibgeschützte Felder. |
| Veröffentlichung und Aktivierung | Veröffentlicht die ID und teilt den Link für den Associate-Zugriff. |

### &#x200B;3. assoziieren

Verwendet die Associate-Benutzeroberfläche, um Kunden zu unterstützen, Informationen zu aktualisieren und konforme Kommunikation zu generieren.


| Verantwortung | Fokus |
|---------------|-------|
| Datenbestätigung | Füllen oder validieren Sie Kundendaten über das linke Eingabefeld. |
| Vorschau und Validierung | Stellt die Genauigkeit mithilfe des Echtzeitvorschau-Bedienfelds sicher. |
| Bereitstellung | Erzeugt PDF/E-Mail und sendet sie über genehmigte Kanäle. |

>[!NOTE]
>
> Der Associate-Partner muss Teil der Gruppe **forms-Associates** sein.

## Dynamische Anwendungsfälle

Die Associate-Benutzeroberfläche unterstützt die sofortige Erstellung personalisierter Dokumente, die für Branchen mit Echtzeitwartung von entscheidender Bedeutung sind.

| Branche | Beispiel-Anwendungsfälle |
|----------|-------------------|
| **Finanzdienstleistungen** | Generieren von Echtzeit-Kreditbestätigungsschreiben, Risikoprofilzusammenfassungen und Kontoerstellung. |
| **Versicherung** | Erstellen Sie sofortige Versicherungsnachweis-Karten oder eine Zusammenfassung der Schadensfalldisposition. |
| **Gesundheitswesen** | Erstellen Sie Zusammenfassungen des Behandlungsplans des Patienten mit berechneten Kopien und Zeitplänen. |
| **Öffentlicher Sektor** | Erstellen von Polizeiprüfungsberichten, Belegen des Bürgerdienstes, Beschwerdebriefen und Zusammenfassungen der Fallaktualisierung vor Ort. |
| **Regierung** | Erstellen Sie Zusammenfassungen zum Antragsstatus, Service-Genehmigungsschreiben und Echtzeit-Kommunikation für Registrierungen für Sozialhilfesysteme. |

## Aktivieren des Workflows „Benutzeroberfläche verknüpfen“

Der Autor kann die folgenden Schritte ausführen, um eine interaktive Kommunikation (IC) für den Zugriff auf die Associate-Benutzeroberfläche zu konfigurieren und zu veröffentlichen:

>[!NOTE]
>
> Unterstützte Komponenten für Zuordnung: Datumsfeld, numerisches Feld, Textfeld, DateTimeField, DateField, Checkbox, Optionsfeld, Dropdown.

### IC erstellen

Entwerfen und konfigurieren Sie die interaktive Kommunikation, um sicherzustellen, dass Branding, Datenbindungen, Compliance-Regeln und Integrationen korrekt festgelegt sind.

### Aktivieren der Associate-Benutzeroberfläche

Aktivieren Sie in der oberen Aktionsleiste die Option Benutzeroberfläche verknüpfen , um die Benutzeroberfläche für verknüpfungsgesteuerte Ereignisse verfügbar zu machen.

### Aktivieren der Benutzeroberfläche „Verknüpfen“ in der Komponente

### Konfigurieren bearbeitbarer Felder

Aktivieren Sie im Abschnitt Erforderliche Felder die Felder, die Verknüpfungen bearbeiten können.
Legen Sie Validierungen fest, um eine genaue und kontrollierte Dateneingabe zu gewährleisten.

### IC veröffentlichen

Nachdem Sie alle Konfigurationen abgeschlossen haben, veröffentlichen Sie die interaktive Kommunikation, um sicheren Zugriff zu erhalten.

### Freigeben der veröffentlichten ID für Associates

Stellen Sie dem Associate den veröffentlichten IC-Link zur Verfügung, über den er sich authentifizieren, kundenspezifische Informationen eingeben und die endgültige Kommunikation mit gültigen Eingaben generieren kann.

Die **Associate-Benutzeroberfläche** schließt die Lücke zwischen der strukturierten Inhaltserstellung und der Echtzeit-Kundeninteraktion.\
Durch die Kombination von intuitivem Design, robuster Backend-Konfiguration und strikter Compliance-Kontrolle können Unternehmen **schnelle, genaue und personalisierte Kommunikation** skaliert bereitstellen.
