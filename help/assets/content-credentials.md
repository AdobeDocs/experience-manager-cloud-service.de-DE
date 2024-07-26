---
title: Content credentials-Integration
description: Content credentials, die in AEM Assets integriert sind und in der Assets-Ansicht enthalten sind, können einen Kontext in den Verlauf eines Assets bieten, einschließlich dessen, wie es erstellt wurde und wer an dessen Erstellung beteiligt war. Wie eine Nährwertkennzeichnung für digitale Inhalte können Content credentials dazu beitragen, Transparenz zu erhöhen und Vertrauen in die Zielgruppen zu schaffen.
role: User
source-git-commit: 1c0ffe9d6e45f1d6b3574d1ac5611b2c2e2d00e0
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---


# Inhaltsurhebernachweise {#content-credentials}

Marken machen sich mehr denn je Gedanken um die Transparenz von Inhalten, die Offenlegung von KI und die Verhinderung der Manipulation von Assets. Die Content Authenticity Initiative (CAI) von Adobe erstellt Tools, die mit dem technischen Standard [Coalition for Content Provenance and Authenticity](https://c2pa.org/specifications/specifications/1.1/specs/C2PA_Specification.html#_trust_model) (C2PA) konform sind. Content credentials, eine neue Art verschlüsselter, manipulationssicherer Metadaten, können Viewer dabei unterstützen, die Herkunft von Inhalten zu verstehen und die Integrität von Marken-Assets sicherzustellen. Sie können eine breite Palette von Herkunftsdaten enthalten, die Einblicke in die Geschichte eines digitalen Assets bieten.

Diese Informationen können Folgendes umfassen:

* **Aussteller oder Unterzeichner:** Informationen über die Entität oder das Unternehmen, die bzw. das die digitale Signatur zum Zertifizieren des Assets ausgestellt hat.
* **Ausstellungsdatum:** Das Datum, an dem die Inhaltsberechtigung auf das Asset angewendet wurde.
* **Guthaben und Nutzung:** Informationen über den Produzenten des Assets, einschließlich Name, Social-Media-Handles oder anderen identitätsbezogenen Informationen.
* **Verarbeitung:** Aufzeichnungen aller Änderungen oder Änderungen, die am Asset vorgenommen wurden.
* **Gerätedetails:** Informationen über die App oder das Gerät, mit der bzw. dem das Asset erstellt oder bearbeitet wird.
* **Verwendetes AI-Tool:** Wenn generative KI zum Bearbeiten oder Erstellen des Assets verwendet wurde, kann der Name des verwendeten Modells enthalten sein.
* **Weitere relevante Informationen:** Zusätzliche Daten können ebenfalls enthalten sein, um mehr Kontext zum Verlauf eines Assets zu bieten.

Für eine vollständige Ansicht kann [Verify](https://contentcredentials.org/verify) einen umfassenderen Einblick in den Asset-Verlauf bieten.

Adobe Experience Manager Assets unterstützt jetzt Content credentials, sodass Benutzer Content credentials direkt in der Assets-Ansicht von AEM sehen können. Bei der Anzeige der Asset-Details zeigt jedes Bild mit Content credentials (z. B. mit GenAI-Diensten erstellte Bilder) die Manifestdetails in einem dedizierten Bedienfeld an. Wenn das Asset heruntergeladen, veröffentlicht oder freigegeben wird, bleiben die Content credentials mit dem Asset intakt.

![Assets](/help/assets/assets/content-credentials.png)

## Content credentials aufrufen {#access-content-credentials}

1. Wechseln Sie zur Benutzeroberfläche der Assets-Ansicht und klicken Sie im linken Bereich auf **Assets** .
1. Navigieren Sie zu einem Ordner und wählen Sie das gewünschte Asset aus.
1. Klicken Sie auf **Details** und wählen Sie im rechten Bereich die Option `Cr pin` aus. Auf der Registerkarte Content credentials werden die folgenden Informationen zum Asset angezeigt.
   1. **Generiertes Bild:** Datum und Uhrzeit, zu der Content credentials angewendet wurden.
   1. **Inhaltszusammenfassung:** Gibt an, ob das Asset teilweise oder vollständig von AI generiert wurde oder wie es bearbeitet wurde.
      ![content credentials](/help/assets/assets/content-credentials1.png)
   1. **Prozess:** Details zu der Anwendung, dem Gerät und dem KI-Tool (z. B. Adobe Firefly), die zum Generieren des Assets verwendet werden, sowie zu nachfolgenden Änderungen.
      ![process](/help/assets/assets/CR-Process.png)
   1. **Über diese Content credentials:** Name des Emittenten zusammen mit Datum und Uhrzeit der Ausgabe.
      ![Emittent](/help/assets/assets/CR-issuer.png)
