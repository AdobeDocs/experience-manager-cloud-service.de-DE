---
title: Echtzeit-Benutzerüberwachung für Edge Delivery Services für AEM Forms as a Cloud Service
description: Die Echtzeit-Benutzerüberwachung für Edge Delivery Services für AEM Forms as a Cloud Service umfasst die fortlaufende Verfolgung und Analyse von Benutzerinteraktionen mit Formularen.
feature: Edge Delivery Services
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 4a534f4335376673c362ef91a877e67a523be560
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 44%

---


# Echtzeit-Benutzerüberwachung für Edge Delivery Services für AEM Forms as a Cloud Service

Mit der Echtzeit-Benutzerüberwachung (Real User Monitoring, RUM) können Sie Einblicke in die Interaktion der Besucher mit Ihren Adobe Experience Manager (AEM)-Websites erhalten. Dieses integrierte Tool bietet wertvolle Daten, um das Benutzerverhalten zu verstehen, Leistungsprobleme zu diagnostizieren und die Effektivität von Website-Experimenten zu messen. RUM geht über synthetische Tests hinaus, indem reale Benutzerinteraktionen erfasst werden und ein genaueres Bild der Leistung Ihrer Site vermittelt wird.

RUM priorisiert jedoch die Privatsphäre der Besucher. Es werden Stichprobenverfahren verwendet, um Daten von einer repräsentativen Untergruppe von Benutzern zu sammeln und sicherzustellen, dass keine personenbezogenen Daten (PII) erfasst werden. Darüber hinaus wird RUM unter Berücksichtigung der Datenminimierung entwickelt und erfasst nur die wesentlichen Metriken, die für die Leistungsanalyse erforderlich sind. Mit diesem Ansatz können Sie Ihre AEM-Sites optimieren und gleichzeitig das Vertrauen der Benutzer wahren.


## Voraussetzungen

Sie können das Monitoring-Dashboard für Edge Delivery Services für AEM Forms as a Cloud Service anzeigen, indem Sie auf die folgende URL zugreifen:

https://data.aem.live/?ext=forms

![RUM-Anmeldebildschirm für Edge Delivery Services für Forms](/help/edge/assets/rum-login-screen.png)

Geben Sie Folgendes ein, um sich beim Monitoring-Dashboard für Edge Delivery Services von AEM Forms as a Cloud Service anzumelden:

* **URL**: Die URL ist spezifisch für die Benutzer-Site oder -Domain. Die Benutzenden haben die Möglichkeit, die Site oder Domain zu filtern, um das Dashboard gemäß ihren Anforderungen anzuzeigen.

* **Domain-Schlüssel**: Der Benutzer generiert den Domänenschlüssel manuell.

Informationen zur Verwendung der Domain-Schlüssel finden Sie im Abschnitt [Authentifizierung](https://www.aem.live/developer/rum#authentication) Dokumentation.

### Überwachen des Dashboards für Edge Delivery Services für AEM Forms as a Cloud Service

Nach Eingabe der URL- und Domain-Schlüssel in den Anmeldebildschirm erhalten Sie Zugriff auf das Monitoring-Dashboard für Edge Delivery Services von AEM Forms as a Cloud Service.

Die folgende Abbildung zeigt das RUM-Dashboard für Edge Delivery Services für AEM Forms as a Cloud Service:

![RUM-Dashboard für Forms](/help/edge/assets/rum-forms-dashboard.png)

### Verschiedene Schlüsselmetriken des Dashboards für Forms {#different-metrics-rum-dashboard-forms}

Dieses Dashboard bietet wichtige Einblicke in die Interaktion der Besucher mit Formularen auf Ihrer Adobe Experience Manager (AEM)-Website. Durch die Überwachung dieser Metriken können Sie Bereiche zur Verbesserung identifizieren und Ihre Formulare für ein besseres Benutzererlebnis und Konversionsraten optimieren:

* **Formularansichten**: Verfolgen Sie die Gesamtanzahl der angezeigten Formulare.
* **Formularübermittlungen**: Tracking der Gesamtzahl abgeschlossener Übermittlungen

* **Largest Contentful Paint**: Es zeigt die Geschwindigkeit an, mit der die URL geladen wird, und gibt die Zeit an, die benötigt wird, um das größte Inhaltselement, das im Viewport sichtbar ist, ab dem Moment zu rendern, in dem die Benutzerin bzw. der Benutzer die URL anfordert. Dieses größte Inhaltselement kann z. B. ein Bild, ein Video oder ein großes Textelement auf Blockebene sein. Die Leistungsbewertungen für die Ladegeschwindigkeit von URLs werden wie folgt kategorisiert:
   * **Gut**: Wenn die Ladezeit 2,5 Sekunden oder weniger beträgt.
   * **In Ordnung**: Wenn die Ladezeit mehr als 2,5 Sekunden, aber höchstens 4 Sekunden beträgt.
   * **Schlecht**: Wenn die Ladezeit 4 Sekunden überschreitet.

* **Kumulative Layout-Verschiebung**: Sie misst die Gesamtsumme aller einzelnen Layout-Verschiebungswerte für jede unerwartete Layout-Verschiebung, die während der gesamten Lebensdauer der Seite auftritt. Dies spielt eine entscheidende Rolle bei der Ermittlung der Leistung einer Seite, da Seitenelemente, die sich ändern, während Benutzende versuchen, mit ihnen zu interagieren, zu einem schlechten Benutzererlebnis führen. Dieser Wert reicht von null bis zu einer beliebigen positiven Zahl: Null bedeutet keine Verschiebung, während eine höhere Zahl bedeutet, dass es entsprechend mehr Layout-Verschiebungen auf der Seite gibt. Die Leistungsmetriken zur Bewertung der Layout-Verschiebungswerte werden wie folgt kategorisiert:

   * **Gut**: Wenn der Layout-Verschiebungswert 0,1 oder weniger beträgt.
   * **In Ordnung**: Wenn der Layout-Verschiebungswert mehr als 0,1, aber höchstens 0,25 beträgt.
   * **Schlecht**: Wenn der Layout-Verschiebungswert 0,25 überschreitet.

* **Interaktion bis zur nächsten Darstellung**: Es wird bewertet, wie schnell eine Seite auf Benutzerinteraktionen reagiert, unter Berücksichtigung der Zeit, die es dauert, bis die Seite während des Besuchs auf Klicks, Tippen und Tastatureingaben reagiert. Der Endwert ist die längste beobachtete Interaktion, unabhängig von etwaigen Anomalien. Die Leistungsmetriken für „Interaktion bis zur nächsten Darstellung“ sind wie folgt kategorisiert:
   * **Gut**: Wenn die Dauer zwischen Benutzeraktionen 200 Millisekunden (ms) oder weniger beträgt.
   * **In Ordnung**: Wenn die Dauer mehr als 200 ms, aber höchstens 500 ms beträgt.
   * **Schlecht**: Wenn die Dauer 500 ms überschreitet.

## Ausführbare Insights

Durch die Analyse dieser Metriken können Sie Möglichkeiten identifizieren:

* Vereinfachen Sie Formulare und reduzieren Sie die Anzahl der Felder.
* Verbessern Sie die Formularklarheit mit klaren Anweisungen und Beschriftungen.
* Optimieren Sie das Formularlayout für Mobilgerät.
* Beheben technischer Probleme, die das Laden von Formularen verlangsamen.

Wenn Sie sich auf diese Bereiche konzentrieren, können Sie Formulare erstellen, die einfacher zu verwenden sind, und Besucher dazu ermutigen, sie auszufüllen, was letztendlich zu höheren Konversionsraten führt.