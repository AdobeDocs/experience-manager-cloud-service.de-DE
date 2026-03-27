---
title: Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation
description: Entdecken Sie die zugehörige Benutzeroberfläche im Editor für interaktive Kommunikation, indem Sie kundenorientierten Agenten die Erstellung personalisierter, konformer Kommunikationen ermöglichen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: 9ba58659-b14c-4ebc-a6d9-e56a4b6aa48b
source-git-commit: f889498f9ee5e71a4d3695dbfbe194d1bbb11488
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 4%

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

Entwirft und verwaltet die interaktive Kommunikation und konfiguriert sie für die Associate-Benutzeroberfläche (einschließlich Aktivierung der Associate-Ansicht und optionalem Workflow).

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
> Associates müssen Teil der Gruppe **forms-Associates** sein. Für Autoren, die auch über die Benutzeroberfläche „Verknüpfen“ in der Autoreninstanz übermitteln, fügen Sie sie **workflow-users** hinzu.

## Dynamische Anwendungsfälle

Die Associate-Benutzeroberfläche unterstützt die sofortige Erstellung personalisierter Dokumente, die für Branchen mit Echtzeitwartung von entscheidender Bedeutung sind.

| Branche | Beispiel-Anwendungsfälle |
|----------|-------------------|
| **Finanzdienstleistungen** | Generieren von Echtzeit-Kreditbestätigungsschreiben, Risikoprofilzusammenfassungen und Kontoerstellung. |
| **Versicherung** | Erstellen Sie sofortige Versicherungsnachweis-Karten oder eine Zusammenfassung der Schadensfalldisposition. |
| **Gesundheitswesen** | Erstellen Sie Zusammenfassungen des Behandlungsplans des Patienten mit berechneten Kopien und Zeitplänen. |
| **Öffentlicher Sektor** | Erstellen von Polizeiprüfungsberichten, Belegen des Bürgerdienstes, Beschwerdebriefen und Zusammenfassungen der Fallaktualisierung vor Ort. |
| **Regierung** | Erstellen Sie Zusammenfassungen zum Antragsstatus, Service-Genehmigungsschreiben und Echtzeit-Kommunikation für Registrierungen für Sozialhilfesysteme. |

## Aktivieren der Associate-Benutzeroberfläche

Autoren aktivieren die Benutzeroberfläche „Verknüpfen“ und konfigurieren in „Einstellungen für interaktive Kommunikation **optional einen Workflow für Übermittlungen**:

1. **Verknüpfte Ansicht aktivieren** - Markieren Sie unter **Eigenschaften verknüpfen** die Option **Bearbeitung verknüpfter Ansichten aktivieren**, klicken Sie dann auf **Änderungen anwenden** und speichern Sie das Dokument.
2. **Workflow konfigurieren (optional)** - Aktivieren Sie **Workflow** **„Workflow für Update konfigurieren**, wählen Sie ein Workflow-Modell aus und legen Sie optional eine Erfolgsmeldung und eine Umleitungs-URL fest.
3. **Bearbeitbare Felder konfigurieren** - Aktivieren Sie die Felder, die Verknüpfungen bearbeiten und Validierungen festlegen können.
4. **Veröffentlichen und freigeben** - Veröffentlichen Sie die IC und teilen Sie den Link mit Partnern.

Schrittweise Anweisungen mit Screenshots und dem Verhalten bei Übermittlung/Workflow (Autor in Autor vs. Verknüpfen in Veröffentlichung) finden Sie unter [Aktivieren und Konfigurieren der Benutzeroberfläche „Verknüpfen“ für interaktive Kommunikation](/help/forms/interactive-communication/enable-configure-associate-ui.md). Informationen zum Erstellen eines Workflows, der PDF aus IC-Übermittlungen generiert, finden Sie unter [Übermittlungs-Workflow für die Associate-Benutzeroberfläche - IC-Generierung der PDF-Ausgabe](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md).

Die **Associate-Benutzeroberfläche** schließt die Lücke zwischen der strukturierten Inhaltserstellung und der Echtzeit-Kundeninteraktion.\
Durch die Kombination von intuitivem Design, robuster Backend-Konfiguration und strikter Compliance-Kontrolle können Unternehmen **schnelle, genaue und personalisierte Kommunikation** skaliert bereitstellen.

## Siehe auch

- [Aktivieren und Konfigurieren der Associate-Benutzeroberfläche für interaktive Kommunikation](/help/forms/interactive-communication/enable-configure-associate-ui.md)
- [Integrieren der Associate-Benutzeroberfläche in Ihr Programm](/help/forms/interactive-communication/invoke-associate-ui.md)
- [Übermittlungs-Workflow für Associate UI - IC-Generierung der PDF-Ausgabe](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md)
