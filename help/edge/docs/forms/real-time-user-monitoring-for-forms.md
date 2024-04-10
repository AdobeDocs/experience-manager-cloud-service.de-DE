---
title: Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms
description: Die Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms umfasst die fortlaufende Verfolgung und Analyse von Benutzerinteraktionen mit Formularen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms

Adobe Experience Manager verwendet Real User Monitoring (RUM), um Besucherinteraktionen mit Adobe Experience Manager-gesteuerten Sites zu verstehen. Dies hilft bei der Diagnose von Leistungsproblemen und der Messung der Experimenteffektivität. Die echte Benutzerüberwachung wahrt den Datenschutz der Besucher, indem sie Stichprobenverfahren verwendet, um sicherzustellen, dass von den besuchten Websites keine personenbezogenen Daten erfasst werden. Es ist nicht zulässig, personenbezogene Daten zur RUM-Datenerfassung hinzuzufügen. Die echte Benutzerüberwachung in Adobe Experience Manager wurde entwickelt, um die Privatsphäre der Besucher zu wahren und die Datenerfassung zu minimieren.

## Vorteile der Verwendung der Echtzeit-Benutzerüberwachung für Edge Delivery Services Forms {#advantages}

AEM verwendet die Echtzeit-Benutzerüberwachung für Folgendes:

* So identifizieren und beheben Sie Leistungsengpässe auf Sites.
* So schätzen Sie die Anzahl der Seitenansichten auf Kunden-Sites
* Um die Interaktion von Adobe Experience Manager mit Analysen, Targeting oder externen Bibliotheken auf derselben Seite zu verstehen, verbessern Sie die Kompatibilität.

## Voraussetzungen

Sie können das Dashboard zur Benutzerüberwachung in Echtzeit für Edge Delivery Services Forms über die folgende URL aufrufen: https://data.aem.live/?ext=forms

![RUM-Anmeldebildschirm für Edge Delivery Services Forms ](/help/edge/assets/rum-login-screen.png)

Geben Sie Folgendes ein, um sich bei Ihrem Echtzeit-Benutzerüberwachungs-Dashboard für Edge Delivery Services Forms anzumelden:
* **URL**: Die URL ist spezifisch für die Site oder Domain des Benutzers. Die Benutzer haben die Möglichkeit, die Site oder Domain zu filtern, um das Dashboard gemäß ihren Anforderungen anzuzeigen.
* **Domain-Schlüssel**: Der Benutzer generiert den Domain-Schlüssel manuell. Hilfe oder Anfragen finden Sie in der [RUM-Domain-Schlüssel generieren](https://aemcs-workspace.adobe.com/rum/generate-domain-key) Dokumentation.

### Dashboard zur Benutzerüberwachung in Echtzeit für Edge Delivery Services Forms

Nachdem Sie die URL und den Domain-Schlüssel in den Anmeldebildschirm eingegeben haben, erhalten Sie Zugriff auf das Echtzeit-Benutzerüberwachungs-Dashboard für Edge Delivery Services Forms.

Die folgende Abbildung zeigt das RUM-Dashboard für Edge Delivery Services Forms:

![RUM Forms Dashboard](/help/edge/assets/rum-forms-dashboard.png)

### Verschiedene Schlüsselmetriken des RUM-Dashboards für Forms {#different-metrics-rum-dashboard-forms}

Sie können Besucherinteraktionen mit Adobe Experience Manager-gesteuerten Sites anhand der folgenden Schlüsselmetriken bewerten:

* **FormViews**: Dies ist die Gesamtzahl der Formulare, die für eine URL innerhalb des angegebenen Datumsbereichs gerendert wurden.
* **FormSubmission**: Dies ist die Gesamtzahl der Formulare, die für eine URL innerhalb des angegebenen Datumsbereichs gesendet wurden.
* **Größte inhaltsreiche Farbe**: Zeigt die Geschwindigkeit, mit der die URL geladen wird, und gibt die Zeit an, die benötigt wird, um das größte Inhaltselement im Viewport sichtbar zu machen, von dem Moment an, in dem der Benutzer die URL anfordert. Bei diesem größten Inhaltselement kann es sich um ein Bild, Video oder ein wesentliches Textelement auf Blockebene handeln. Die Leistungsbewertungen für die URL-Ladegeschwindigkeit werden wie folgt kategorisiert:
   * **Gut**: Wenn die Ladezeit 2,5 Sekunden oder weniger beträgt.
   * **Okay**: Wenn die Ladezeit mehr als 2,5 Sekunden, aber 4 Sekunden oder weniger beträgt.
   * **Schlecht**: Wenn die Ladezeit 4 Sekunden überschreitet

* **Kumulative Layout-Verschiebung**: Er misst die Gesamtsumme aller individuellen Layout-Shift-Scores für jede unerwartete Layout-Verschiebung, die während der gesamten Lebensdauer der Seite auftritt. Sie spielt eine entscheidende Rolle bei der Identifizierung der Leistung einer Seite, da sie zu einem schlechten Benutzererlebnis führt, wenn Seitenelemente sich ändern, während Benutzende versuchen, mit ihnen zu interagieren. Diese Punktzahl reicht von null bis zu einer beliebigen positiven Zahl: Null zeigt an, dass keine Verschiebung stattfindet, während eine höhere Zahl mehr Layout-Verschiebungen auf der Seite bedeutet. Die Leistungsmetriken, die zur Bewertung der Bewertungen der Layout-Verschiebung verwendet werden, sind wie folgt kategorisiert:

   * **Gut**: Wenn die Bewertung für die Layout-Verschiebung 0,1 oder weniger beträgt.
   * **Okay**: Wenn der Wert für die Layout-Verschiebung größer als 0,1, aber 0,25 oder weniger ist.
   * **Schlecht**: Wenn die Bewertung für die Layout-Verschiebung 0,25 überschreitet.

* **Interaktion mit nächster Zeichnung**: Es wird bewertet, wie schnell eine Seite auf Benutzerinteraktionen reagiert, wobei berücksichtigt wird, wie lange die Seite benötigt, um auf Klicks, Tippen und Tastatureingaben während des Besuchs eines Benutzers auf der Seite zu reagieren. Der Endwert ist die längste beobachtete Interaktion, wobei alle Anomalien ignoriert werden. Die Leistungsmetriken für Interaction to Next Paint sind wie folgt kategorisiert:
   * **Gut**: Wenn die Dauer zwischen Benutzeraktionen 200 Millisekunden (ms) oder weniger beträgt.
   * **Okay**: wenn die Dauer mehr als 200 ms, aber 500 ms oder weniger beträgt.
   * **Schlecht**: Wenn die Dauer 500 ms überschreitet.

