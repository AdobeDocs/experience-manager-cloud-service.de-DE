---
title: AEM Assets-Aktivierungsbericht (Beta)
description: Definitionen für Beta-Metriken (AEM Assets Activation Report), die Aktivierungen (Downloads, Freigaben) und Verteilungen (Dynamic Media, Sites) umfassen.“
role: Admin
hide: true
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
source-git-commit: 49f94bdbd1c0fdd96e6d42c534900334af5c946d
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# AEM Assets-Aktivierungsbericht (Beta): Metrikdefinitionen

## Grundlegendes zu Ihren Asset-Leistungsmetriken

Jedes Asset in Ihrem AEM Assets-System erzählt eine Geschichte: vom Hochladen und Genehmigen bis zu dem Moment, in dem es einen Käufer als Produktbild, freigegebener Link oder Hero-Banner erreicht. Diese Journey ist der Antrieb für Milliarden von Markenimpressionen, und es ist entscheidend, sie zu verstehen, um den Wert Ihrer Asset-Investition zu erschließen.

In diesem Artikel werden die Metriken hinter dieser Journey aufgeschlüsselt und die Art und Weise gruppiert, wie Ihre Teams tatsächlich mit Assets arbeiten:

- **Aktivierungen (von Mitarbeitern und Partnern initiiert)**: Downloads, Freigaben und Aktivierungen in Ihrer AEM Assets (Assets View und Content Hub).
- **Distributionen (extern für Endbenutzer)**: Bereitstellung in der Welt über Kanäle wie Dynamic Media und AEM Sites.

Gemeinsam verbinden diese Metriken interne Asset-Aktivitäten mit externer Reichweite und Interaktion und helfen Ihnen dabei zu erkennen, wie Ihre Inhaltsvorgänge in echte Geschäftsergebnisse übersetzt werden.

Dies ist nur der Anfang Ihres Journey mit AEM Assets, und diese Metriken werden sich parallel dazu weiterentwickeln. Wir würden Ihr Feedback benötigen, während Sie sie verwenden, damit wir diese Berichte für Sie nützlicher gestalten können.

**Hinweis**: Wenn Sie diese mit Adobe Product/Engineering überprüfen oder Feedback einholen möchten, senden Sie eine E-Mail an `GRP-AEM-DAM-METRICS-BETA@ADOBE.COM`.

| | Metrik | Definition |
|---|---|---|
| **Aktivierungen** | **Downloads (Assets-Ansicht)** | Die Häufigkeit, mit der Assets direkt aus der AEM Assets-Kernumgebung heruntergeladen werden, z. B. von internen Benutzenden, die Dateien über die Assets-Ansichtsoberfläche durchsuchen und herunterladen. |
| | **Freigaben (Assets-Ansicht)** | Die Anzahl der Freigaben (über freigebbare Links, die generiert wurden) in der AEM Assets-Ansicht, um externen oder nicht authentifizierten Benutzenden direkten Zugriff auf bestimmte Assets, Ordner oder Sammlungen zu gewähren, ohne sich anmelden zu müssen. |
| | **Downloads (Content Hub)** | Die Häufigkeit, mit der Assets von Benutzenden über Content Hub heruntergeladen werden, die Self-Service-Benutzeroberfläche, über die umfassendere Teams genehmigte, markenfertige Assets durchsuchen und herunterladen können. |
| | **Freigaben (Content Hub)** | Die Anzahl der Freigaben (über freigebbare Links, die generiert wurden) innerhalb von Content Hub, um anderen Benutzenden direkten Zugriff auf ausgewählte Assets oder Sammlungen zu gewähren. |
| | **Für Content Hub aktivieren** | Die Aktion des Genehmigens/Veröffentlichens eines Assets aus AEM Assets, damit es für Endbenutzende in Content Hub verfügbar wird. In Content Hub werden nur genehmigte Assets angezeigt. |
| | **Für Dynamic Media aktivieren** | Veröffentlichung eines Assets aus AEM Assets im Dynamic Media-Service, sodass es zu Ausgabedarstellungen verarbeitet und in Echtzeit über die Bild-/Video-Pipeline von Dynamic Media und das CDN bereitgestellt werden kann. |
| **Verteilungen** | **Dynamic Media-Versandanfragen** | Die Gesamtzahl der Fälle, in denen ein Asset über alle Kanäle mit Dynamic Media angefordert und bereitgestellt wurde. |
| | **Eindeutige Assets-Server für Dynamic Media** | Die Anzahl der einzelnen Assets, die in einem bestimmten Zeitraum mindestens einmal über Dynamic Media bereitgestellt wurden, gezählt einmal pro Asset, unabhängig davon, wie oft es angefordert wurde oder wie viele verschiedene Ausgabedarstellungen davon bereitgestellt wurden. |
| | **Eindeutige Dynamic Media-Transformationen** | Die Anzahl der eindeutigen Varianten Ihrer Assets, die über Dynamic Media in einem bestimmten Zeitraum bereitgestellt wurden. Hier wird gezeigt, wie sich Ihre Inhalte geräteübergreifend, in der Bildschirmgröße und in Anwendungsfällen anpassen. |
| | **In Sites veröffentlichen** | Die Aktion des Veröffentlichens eines Assets über AEM Assets, damit es zur Verwendung auf Live-AEM Sites-Seiten verfügbar wird. |



