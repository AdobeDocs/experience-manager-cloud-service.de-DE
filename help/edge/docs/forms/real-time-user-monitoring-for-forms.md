---
title: Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms
description: Die Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms beinhaltet die fortlaufende Verfolgung und Analyse von Benutzerinteraktionen mit Formularen.
feature: Edge Delivery Services
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---


# Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms

Adobe Experience Manager verwendet die Echtzeit-Benutzerüberwachung (RUM), um die Benutzerinteraktionen mit Adobe Experience Manager-gesteuerten Sites zu verstehen. Dies hilft bei der Diagnose von Leistungsproblemen und der Effektivität von Testversuchen. Die Echtzeit-Benutzerüberwachung wahrt den Besucherdatenschutz, indem sie die Sampling-Techniken nutzt und sicherstellt, dass keine personenbezogenen Daten von den besuchten Sites erfasst werden. Personenbezogene Daten dürfen nicht zur RUM-Datenerfassung hinzugefügt werden. Die Echtzeit-Benutzerüberwachung in Adobe Experience Manager dient der Wahrung des Datenschutzes der Besucher und der Minimierung der Datenerfassung.

## Vorteile der Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms {#advantages}

AEM verwendet die Echtzeit-Benutzerüberwachung für Folgendes:

* Ermitteln und Beheben von Leistungsengpässen auf Sites.
* So schätzen Sie die Anzahl der Seitenansichten für Kunden-Sites
* Um die Interaktion von Adobe Experience Manager mit Analyse-, Targeting- oder externen Bibliotheken auf derselben Seite zu verstehen, wird die Kompatibilität verbessert.

## Voraussetzungen

Sie können das Echtzeit-Dashboard zur Benutzerüberwachung für Edge Delivery Services Forms anzeigen, indem Sie auf die folgende URL zugreifen: https://data.aem.live/?ext=forms

![RUM-Anmeldebildschirm für Edge Delivery Services Forms ](/help/edge/assets/rum-login-screen.png)

Geben Sie Folgendes ein, um sich beim Echtzeit-Dashboard zur Benutzerüberwachung für Edge Delivery Services Forms anzumelden:
* **URL**: Die URL ist spezifisch für die Benutzersite oder Domäne. Die Benutzer haben die Möglichkeit, die Site oder Domäne zu filtern, um das Dashboard gemäß ihren Anforderungen anzuzeigen.
* **Domain-Schlüssel**: Der Benutzer generiert den Domänenschlüssel manuell. Hilfe und Anfragen finden Sie im Abschnitt [RUM-Domänenschlüssel generieren](https://aemcs-workspace.adobe.com/rum/generate-domain-key) Dokumentation.

### Dashboard zur Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms

Nachdem Sie die URL und den Domain-Schlüssel in den Anmeldebildschirm eingegeben haben, erhalten Sie Zugriff auf das Echtzeit-Dashboard zur Benutzerüberwachung für Edge Delivery Services Forms.

Die folgende Abbildung zeigt das RUM-Dashboard für Edge Delivery Services Forms:

![RUM Forms Dashboard](/help/edge/assets/rum-forms-dashboard.png)

### Verschiedene Schlüsselmetriken des RUM-Dashboards für Forms {#different-metrics-rum-dashboard-forms}

Sie können die Besucherinteraktionen mit Adobe Experience Manager-gesteuerten Sites mithilfe der folgenden Schlüsselmetriken bewerten:

* **Formularansichten**: Dies ist die Gesamtzahl der für eine URL innerhalb des angegebenen Datumsbereichs wiedergegebenen Formulare.
* **Formularübermittlung**: Dies ist die Gesamtzahl der Formulare, die für eine URL innerhalb des angegebenen Datumsbereichs gesendet wurden.
* **Größtes inhaltsreiches Bild**: Zeigt die Geschwindigkeit an, mit der die URL geladen wird. Sie gibt die Zeit an, die zum Rendern des größten Inhaltselements benötigt wird, das ab dem Zeitpunkt, zu dem der Benutzer die URL anfordert, im Viewport sichtbar ist. Dieses größte Inhaltselement kann ein Bild, ein Video oder ein erhebliches Textelement auf Blockebene sein. Die Leistungsbewertungen für die Ladegeschwindigkeit von URLs werden wie folgt kategorisiert:
   * **Gut**: Wenn die Ladezeit 2,5 Sekunden oder weniger beträgt.
   * **Okay**: Wenn die Ladezeit mehr als 2,5 Sekunden, aber 4 Sekunden oder weniger beträgt.
   * **Bad**: Wenn die Ladezeit 4 Sekunden überschreitet

* **Kumulative Layoutverschiebung**: Sie misst die Gesamtsumme aller einzelnen Layoutverschiebungswerte für jede unerwartete Layoutverschiebung, die während der gesamten Lebensdauer der Seite auftritt. Es spielt eine entscheidende Rolle bei der Ermittlung der Leistung einer Seite, da Seitenelemente, die sich ändern, während ein Benutzer versucht, mit ihnen zu interagieren, zu einem schlechten Benutzererlebnis führen. Diese Punktzahl reicht von null bis zu einer beliebigen positiven Zahl: Null bedeutet keine Verschiebung, während eine höhere Zahl bedeutet, dass sich das Layout auf der Seite weiter verlagert. Die Leistungsmetriken zur Bewertung der Layoutverschiebungswerte werden wie folgt kategorisiert:

   * **Gut**: Wenn der Layoutverschiebungswert 0,1 oder weniger beträgt.
   * **Okay**: Wenn der Layoutverschiebungswert größer als 0,1, aber 0,25 oder kleiner ist.
   * **Bad**: Wenn der Layoutverschiebungswert 0,25 überschreitet.

* **Interaktion mit der nächsten Farbe**: Es wird bewertet, wie schnell eine Seite auf Benutzerinteraktionen reagiert, unter Berücksichtigung der Zeit, die es dauert, bis die Seite während des Besuchs eines Benutzers auf der Seite auf Klicks, Tippen und Tastatureingaben reagiert. Der Endwert ist die längste beobachtete Interaktion, unabhängig von etwaigen Anomalien. Die Leistungsmetriken für Interaction to Next Paint sind wie folgt kategorisiert:
   * **Gut**: Wenn die Dauer zwischen Benutzeraktionen 200 Millisekunden (ms) oder weniger beträgt.
   * **Okay**: Bei einer Dauer von mehr als 200 ms bis 500 ms oder weniger.
   * **Bad**: Wenn die Dauer 500 ms überschreitet.
