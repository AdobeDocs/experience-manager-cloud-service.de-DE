---
title: Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms
description: Die Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms beinhaltet das fortlaufende Tracking und die Analyse von Benutzerinteraktionen mit Formularen.
feature: Edge Delivery Services
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 100%

---


# Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms

Adobe Experience Manager verwendet Real User Monitoring (RUM), um die Besucherinteraktionen mit Adobe Experience Manager-gesteuerten Sites zu verstehen. Dies hilft bei der Diagnose von Leistungsproblemen und der Bewertung der Effektivität von Experimenten. Real User Monitoring wahrt den Besucherdatenschutz, indem Sampling-Techniken genutzt werden und sichergestellt wird, dass keine personenbezogenen Daten von den besuchten Sites erfasst werden. Personenbezogene Daten dürfen nicht zur RUM-Datenerfassung hinzugefügt werden. Real User Monitoring in Adobe Experience Manager dient der Wahrung des Datenschutzes der Besucherinnen und Besucher und der Minimierung der Datenerfassung.

## Vorteile der Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms {#advantages}

AEM verwendet die Echtzeit-Benutzerüberwachung für Folgendes:

* Identifizieren und Beheben von Leistungsengpässen bei Sites.
* Schätzen der Anzahl der Seitenansichten auf Kunden-Sites
* Verständnis der Interaktion von Adobe Experience Manager mit Analytics, Targeting oder externen Bibliotheken auf derselben Seite, um die Kompatibilität zu verbessern.

## Voraussetzungen

Sie können das Dashboard zur Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms anzeigen, indem Sie auf die folgende URL zugreifen: 
https://data.aem.live/?ext=forms

![RUM-Anmeldebildschirm für Edge Delivery Services Forms ](/help/edge/assets/rum-login-screen.png)

Geben Sie Folgendes ein, um sich auf dem Dashboard für die Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms anzumelden:
* **URL**: Die URL ist spezifisch für die Benutzer-Site oder -Domain. Die Benutzenden haben die Möglichkeit, die Site oder Domain zu filtern, um das Dashboard gemäß ihren Anforderungen anzuzeigen.
* **Domain-Schlüssel**: Die Benutzenden generieren den Domain-Schlüssel manuell. Wenn Sie Hilfe benötigen oder Fragen haben, lesen Sie bitte die Dokumentation [Generieren des RUM-Domain-Schlüssels](https://aemcs-workspace.adobe.com/rum/generate-domain-key).

### Dashboard für die Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms

Nachdem Sie die URL und den Domain-Schlüssel in den Anmeldebildschirm eingegeben haben, erhalten Sie Zugriff auf das Dashboard für die Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms.

Die folgende Abbildung zeigt das RUM-Dashboard für Edge Delivery Services Forms:

![RUM-Dashboard für Forms](/help/edge/assets/rum-forms-dashboard.png)

### Verschiedene Schlüsselmetriken des RUM-Dashboards für Forms {#different-metrics-rum-dashboard-forms}

Sie können die Besucherinteraktionen mit Adobe Experience Manager-gesteuerten Sites mithilfe der folgenden Schlüsselmetriken bewerten:

* **Formviews**: Dies ist die Gesamtzahl der für eine URL innerhalb des angegebenen Datumsbereichs wiedergegebenen Formulare.
* **Formsubmission**: Dies ist die Gesamtzahl der Formulare, die für eine URL innerhalb des angegebenen Datumsbereichs übermittelt wurden.
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
