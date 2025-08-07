---
title: Betriebliche Telemetrie für Edge Delivery Services for AEM Forms as a Cloud Service
description: Die betriebliche Telemetrie für Edge Delivery Services for AEM Forms as a Cloud Service beinhaltet das fortlaufende Tracking und die Analyse von Benutzerinteraktionen mit Formularen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 100%

---

# Betriebliche Telemetrie für Edge Delivery Services for AEM Forms as a Cloud Service

Mit der betrieblichen Telemetrie können Sie authentische Einblicke in die Interaktion der Besuchenden mit Ihren Adobe Experience Manager(AEM)-Websites gewinnen. Dieses integrierte Tool liefert wertvolle Daten, um das Benutzerverhalten zu verstehen, Leistungsprobleme zu diagnostizieren und die Effektivität von Website-Experimenten zu messen. Die betriebliche Telemetrie geht über synthetische Tests hinaus, indem Interaktionen mit der realen Nutzung erfasst werden und ein präziseres Bild der Leistung Ihrer Site geboten wird.

Betriebliche Telemetrie priorisiert jedoch die Privatsphäre von Besuchenden. Es werden Sampling-Verfahren verwendet, um Daten von einer repräsentativen Teilmenge von Benutzenden zu sammeln und sicherzustellen, dass keine personenbezogenen Daten (PII) erfasst werden. Darüber hinaus wurde die betriebliche Telemetrie unter Berücksichtigung der Datenminimierung entwickelt und erfasst nur die wesentlichen Metriken, die für die Leistungsanalyse erforderlich sind. Mit diesem Ansatz können Sie Ihre AEM-Sites optimieren und gleichzeitig das Vertrauen der Benutzenden wahren.


## Voraussetzungen

Sie können das Monitoring-Dashboard für Edge Delivery Services for AEM Forms as a Cloud Service anzeigen, indem Sie auf die folgende URL zugreifen:

https://data.aem.live/?ext=forms

![Anmeldebildschirm für betriebliche Telemetrie für Edge Delivery Services for Forms](/help/edge/assets/rum-login-screen.png)

Geben Sie Folgendes ein, um sich auf dem Monitoring-Dashboard für Edge Delivery Services for AEM Forms as a Cloud Service anzumelden:

- **URL**: Die URL ist spezifisch für die Benutzer-Site oder -Domain. Die Benutzenden haben die Möglichkeit, die Site oder Domain zu filtern, um das Dashboard gemäß ihren Anforderungen anzuzeigen.

- **Domain-Schlüssel**: Die Benutzenden generieren den Domain-Schlüssel manuell. Wenden Sie sich an den Adobe-Support, um Domain-Schlüssel für Ihre Formulare zu erhalten.

### Monitoring-Dashboard für Edge Delivery Services for AEM Forms as a Cloud Service

Nachdem Sie die URL und die Domain-Schlüssel auf dem Anmeldebildschirm eingegeben haben, erhalten Sie Zugriff auf das Monitoring-Dashboard für Edge Delivery Services for AEM Forms as a Cloud Service.

Die folgende Abbildung zeigt das Dashboard für Edge Delivery Services for AEM Forms as a Cloud Service:

![Dashboard der betrieblichen Telemetrie für Forms](/help/edge/assets/rum-forms-dashboard.png)

### Verschiedene Schlüsselmetriken des Dashboards für Formulare {#different-metrics-operational-telemetry-dashboard-forms}

Dieses Dashboard bietet wichtige Einblicke in die Interaktion der Besuchenden mit Formularen auf Ihrer Adobe Experience Manager(AEM)-Website. Durch die Überwachung dieser Metriken können Sie zu verbessernde Bereiche identifizieren und Ihre Formulare für ein besseres Anwendererlebnis und bessere Konversionsraten optimieren:

- **Formularansichten**: Verfolgen Sie, wie oft Formulare insgesamt angezeigt werden
- **Formularübermittlungen**: Verfolgen Sie die Gesamtzahl der abgeschlossenen Übermittlungen

- **Largest Contentful Paint**: Es zeigt die Geschwindigkeit an, mit der die URL geladen wird, und gibt die Zeit an, die benötigt wird, um das größte Inhaltselement, das im Viewport sichtbar ist, ab dem Moment zu rendern, in dem die Benutzerin bzw. der Benutzer die URL anfordert. Dieses größte Inhaltselement kann z. B. ein Bild, ein Video oder ein großes Textelement auf Blockebene sein. Die Leistungsbewertungen für die Ladegeschwindigkeit von URLs werden wie folgt kategorisiert:
   - **Gut**: Wenn die Ladezeit 2,5 Sekunden oder weniger beträgt.
   - **In Ordnung**: Wenn die Ladezeit mehr als 2,5 Sekunden, aber höchstens 4 Sekunden beträgt.
   - **Schlecht**: Wenn die Ladezeit 4 Sekunden überschreitet.

- **Kumulative Layout-Verschiebung**: Sie misst die Gesamtsumme aller einzelnen Layout-Verschiebungswerte für jede unerwartete Layout-Verschiebung, die während der gesamten Lebensdauer der Seite auftritt. Dies spielt eine entscheidende Rolle bei der Ermittlung der Leistung einer Seite, da Seitenelemente, die sich ändern, während Benutzende versuchen, mit ihnen zu interagieren, zu einem schlechten Benutzererlebnis führen. Dieser Wert reicht von null bis zu einer beliebigen positiven Zahl: Null bedeutet keine Verschiebung, während eine höhere Zahl bedeutet, dass es entsprechend mehr Layout-Verschiebungen auf der Seite gibt. Die Leistungsmetriken zur Bewertung der Layout-Verschiebungswerte werden wie folgt kategorisiert:

   - **Gut**: Wenn der Layout-Verschiebungswert 0,1 oder weniger beträgt.
   - **In Ordnung**: Wenn der Layout-Verschiebungswert mehr als 0,1, aber höchstens 0,25 beträgt.
   - **Schlecht**: Wenn der Layout-Verschiebungswert 0,25 überschreitet.

- **Interaktion bis zur nächsten Darstellung**: Es wird bewertet, wie schnell eine Seite auf Benutzerinteraktionen reagiert, unter Berücksichtigung der Zeit, die es dauert, bis die Seite während des Besuchs auf Klicks, Tippen und Tastatureingaben reagiert. Der Endwert ist die längste beobachtete Interaktion, unabhängig von etwaigen Anomalien. Die Leistungsmetriken für „Interaktion bis zur nächsten Darstellung“ sind wie folgt kategorisiert:
   - **Gut**: Wenn die Dauer zwischen Benutzeraktionen 200 Millisekunden (ms) oder weniger beträgt.
   - **In Ordnung**: Wenn die Dauer mehr als 200 ms, aber höchstens 500 ms beträgt.
   - **Schlecht**: Wenn die Dauer 500 ms überschreitet.

## Verwertbare Erkenntnisse

Durch die Analyse dieser Metriken können Sie Möglichkeiten für Folgendes identifizieren:

- Vereinfachen von Formularen und Reduzieren der Felderanzahl.
- Verbessern der Formularklarheit mit klaren Anweisungen und Beschriftungen.
- Optimieren des Formular-Layouts für die Reaktivität auf Mobilgeräten.
- Beheben technischer Probleme, die das Laden von Formularen verlangsamen.

Wenn Sie sich auf diese Bereiche konzentrieren, können Sie Formulare erstellen, die einfacher zu benutzen sind und die Besuchenden zum Ausfüllen anregen, was letztendlich zu höheren Konversionsraten führt.


