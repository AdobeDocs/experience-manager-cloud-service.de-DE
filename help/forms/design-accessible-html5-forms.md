---
title: Entwerfen barrierefreier HTML5-Formulare
description: HTML5-Formulare verwenden den ARIA-HTML5-Standard für Barrierefreiheit. Diese Formulare unterstützen die Registerkartennavigation und sind zertifiziert für ihre Kompatibilität mit den gängigen Bildschirmlesehilfen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: fca2f9b2-11a2-4db0-a370-c4046f32be63
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 92%

---

# Entwerfen barrierefreier HTML5-Formulare {#designing-accessible-html-forms}

<span class="preview"> Die HTML5 Forms-Funktion wird als Teil des Early Access-Programms angeboten. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen (geschäftlichen) E-Mail-ID an aem-forms-ea@adobe.com.
</span>

Für HTML5-Formulare wird der ARIA-HTML5-Standard für Barrierefreiheit verwendet, um die HTML-Formulare barrierefrei zu gestalten. Diese Formulare unterstützen die Registerkartennavigation (außer Mozilla Firefox) und sind zertifiziert für ihre Kompatibilität mit den gängigen Bildschirmlesehilfen. Um ein HTML5-Formular mit Barrierefreiheitsmerkmalen zu generieren, entwerfen Sie die XFA-Formularvorlage nach einigen grundlegenden Entwurfsrichtlinien. Die Entwurfsrichtlinien umfassen das Konfigurieren der richtigen Registerkartenreihenfolge und die Bereitstellung des Sprechtext-Inhalts für jedes Formularsteuerelement. AEM Forms Designer unterstützt das Festlegen dieser Formularsteuerungsattribute zum Erstellen eines barrierefreien PDF- und HTML5-Formulars.

*Hinweis: Die Registerkartennavigation deckt keine geschützten Felder ab, wie etwa Berechnungsfelder, die Wertesummen anzeigen. Damit die Bildschirmlesehilfe den Wert eines geschützten Felds liest, platzieren Sie ein leeres, schreibgeschütztes Feld entweder auf oder neben dem geschützten Feld. Weisen Sie den Wert des geschützten Feldes dem neuen, schreibgeschützten Feld zu. Die Bildschirmlesehilfe oder die Registerkartennavigation kann dieses schreibgeschützte Feld erfassen und als Wert des geschützten Felds wiedergeben.*

AEM Forms Designer enthält verschiedene Sprechtextoptionen, die an Bildschirmlesehilfen übergeben werden können. Benutzende können für jedes Objekt in einem Formular eine oder mehrere Einstellungen für den Text der Bildschirmlesehilfe angeben:

* Benutzerdefinierter Bildschirmlesehilfen-Text, der mithilfe der Palette „Barrierefreiheit“ festgelegt werden kann. Autorinnen und Autoren können die Namen von Schaltflächen und Feldern sowie deren Zweck kommentieren.
* QuickInfos, die in der Palette „Barrierefreiheit“ festgelegt werden können.
* Beschriftungen für Felder im Formular.
* Namen von Objekten (wie für die Option „Name“ der Registerkarte „Bindung“ angegeben).

![Barrierefreiheit](assets/accessibility.png)

Wenn mehrere Optionen wie QuickInfos, Bildschirmlesehilfen-Text und Beschriftung in einem Formularsteuerelement zur Verfügung stehen, verwendet die Bildschirmlesehilfe nur eine dieser Eigenschaften. Die Standardreihenfolge ist: Benutzerdefinierter Bildschirmlesehilfen-Text, QuickInfo, Beschriftung und Name. Diese Standardreihenfolge können Sie über die Option Bildschirmlesehilfen-**Rangfolge** in der Palette „Ein-/Ausgabehilfe“ außer Kraft setzen.
