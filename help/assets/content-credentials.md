---
title: Integration von Content Credentials
description: Content Credentials sind in AEM Assets integriert und in der Assets-Ansicht enthalten. Sie können Kontext für den Verlauf eines Assets bieten, einschließlich Informationen dazu, wie es erstellt wurde und wer an dessen Erstellung beteiligt war. Content Credentials können, ähnlich einer Nährwertkennzeichnung für digitale Inhalte, dazu beitragen, die Transparenz zu erhöhen und Vertrauen bei den Zielgruppen zu schaffen.
role: User
exl-id: 27c25ae0-4477-40c3-85c8-3e0aa725aba7
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 94%

---

# Content Credentials {#content-credentials}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

Marken machen sich mehr denn je Gedanken um die Transparenz von Inhalten, die Offenlegung von KI und die Verhinderung der Manipulation von Assets. Die Content Authenticity Initiative (CAI) von Adobe erstellt Tools, die mit dem technischen Standard der [Coalition for Content Provenance and Authenticity](https://c2pa.org/specifications/specifications/1.1/specs/C2PA_Specification.html#_trust_model) (C2PA) konform sind. Content Credentials sind eine neue Art verschlüsselter, manipulationssicherer Metadaten. Sie können Betrachtende dabei unterstützen, die Herkunft von Inhalten zu verstehen und dazu beitragen, die Integrität von Marken-Assets sicherzustellen. Sie können eine breite Palette von Herkunftsdaten enthalten, die Einblicke in den Verlauf eines digitalen Assets bieten.

Diese Daten können Folgendes beinhalten:

* **Aussteller oder Unterzeichner:** Informationen über die Entität oder Firma, die die digitale Signatur zum Zertifizieren oder Unterzeichnen des Assets ausgestellt hat.
* **Ausstellungsdatum:** Das Datum, an dem die Content Credential auf das Asset angewendet wurde.
* **Namensnennung und Nutzung:** Informationen über den Ersteller des Assets, einschließlich Name, Social-Media-Handles oder anderen identitätsbezogenen Informationen.
* **Verlauf:** Die Dokumentation aller Bearbeitungen oder Änderungen, die am Asset vorgenommen wurden.
* **Gerätedetails:** Informationen über die App oder das Gerät, mit der bzw. dem das Asset erstellt oder bearbeitet wurde.
* **Verwendetes KI-Tool:** Wenn generative KI zum Bearbeiten oder Erstellen des Assets verwendet wurde, kann der Name des verwendeten Modells enthalten sein.
* **Sonstige relevante Informationen:** Zusätzliche Daten können ebenfalls enthalten sein, um mehr Kontext zum Verlauf eines Assets zu bieten.

Die Option [Überprüfen](https://contentcredentials.org/verify) bietet Ihnen mit einem umfassenderen Einblick in den Asset-Verlauf eine vollständige Ansicht.

Adobe Experience Manager Assets unterstützt jetzt Content Credentials, sodass Benutzende Content Credentials direkt in der Assets-Ansicht von AEM sehen können. Bei der Anzeige der Asset-Details zeigt jedes Bild mit Content Credentials (z. B. mit GenAI-Diensten erstellte Bilder) die Manifest-Details in einem dedizierten Bedienfeld an. Wenn das Asset heruntergeladen, veröffentlicht oder freigegeben wird, bleiben die Content Credentials zusammen mit dem Asset intakt.

![Assets](/help/assets/assets/content-credentials.png)

## Zugriff auf Content Credentials {#access-content-credentials}

1. Wechseln Sie zur Benutzeroberfläche der Assets-Ansicht und klicken Sie im linken Bereich auf **Assets**.
1. Navigieren Sie zu einem Ordner und wählen Sie das gewünschte Asset aus.
1. Klicken Sie auf **Details** und wählen Sie im Bereich ganz rechts die Option `Cr pin` aus. Auf der Registerkarte „Content Credentials“ werden die folgenden Informationen zum Asset angezeigt.
   1. **Generiertes Bild:** Datum und Uhrzeit, zu der die Content Credentials angewendet wurden.
   1. **Inhaltszusammenfassung:** Gibt an, ob das Asset teilweise oder vollständig von KI generiert wurde oder wie es bearbeitet wurde.

      ![Content Credentials](/help/assets/assets/content-credentials1.png)
   1. **Verlauf:** Details zu der Anwendung, dem Gerät und dem KI-Tool (z. B. Adobe Firefly), die zum Generieren des Assets verwendet wurden, sowie zu nachfolgend gemachten Änderungen.

      ![Verlauf](/help/assets/assets/CR-Process.png)
   1. **Informationen zu diesen Content Credentials:** Name des Ausstellers zusammen mit Datum und Uhrzeit der Ausstellung.

      ![Aussteller](/help/assets/assets/CR-issuer.png)
