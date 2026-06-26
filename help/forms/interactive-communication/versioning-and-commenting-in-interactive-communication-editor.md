---
title: Versionierung und Kommentare im Editor für interaktive Kommunikation
description: Mit der Versionierung und den Kommentaren im Editor für interaktive Kommunikation in AEM Forms können Unternehmen dynamische, datengesteuerte Dokumente für die personalisierte Kundenkommunikation erstellen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: ca9917c0-d8bb-4381-afab-7ab888d992e8
source-git-commit: b11e1b28aabba9e03553dc9e9394bff111facfee
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 1%

---


# Versionierung und Kommentare im Editor für interaktive Kommunikation

Interaktive Kommunikationen ermöglichen es Unternehmen, dynamische, datengesteuerte Dokumente für die personalisierte Kundenkommunikation zu erstellen. Um eine bessere Zusammenarbeit, Governance und kontrollierte Veröffentlichungs-Workflows zu unterstützen, bietet der Editor für interaktive Kommunikation Versionierungs-, Prüf- und Kommentarfunktionen.

Mit diesen Funktionen können Autoren mehrere Iterationen einer interaktiven Kommunikation verwalten, das Feedback von Prüfern erfassen, zu früheren Versionen zurückkehren und während des gesamten Inhaltslebenszyklus ein klares Audit-Protokoll führen.

## Versionierung für interaktive Kommunikation

Mit der Versionierung im Editor für interaktive Kommunikation können Autoren:

- Erstellen mehrerer Versionen einer interaktiven Kommunikation

- Inkrementelle Änderungen mit aussagekräftigen Beschriftungen und Kommentaren speichern

- Auf eine frühere Version zurücksetzen

- Unterschiede visuell vergleichen

- Verwalten Sie saubere Governance für Prüfungs-, Genehmigungs- und Versionszyklen.

Dadurch wird sichergestellt, dass Autorinnen und Autoren interaktive Kommunikationsentwürfe experimentieren, iterieren und verfeinern können, während der gesamte historische Kontext erhalten bleibt.

## Erstellen einer Version einer interaktiven Kommunikation

Verwenden Sie die Versionierung, wenn Sie den aktuellen Status einer interaktiven Kommunikation beibehalten möchten, bevor Sie Aktualisierungen vornehmen.

So erstellen Sie eine neue Version:

1. Navigieren Sie zu **Forms und Dokumente** und wählen Sie die interaktive Kommunikation aus, die Sie versionieren möchten.

1. Wählen Sie in der linken oberen Ecke der Asset-Ansicht den Umschalter für die Leiste und dann **Zeitleiste** aus den Bedienfeldoptionen aus.

   ![Version 1 erstellen](/help/forms/interactive-communication/assets/create-version1.png)

1. Das Bedienfeld **Zeitleiste** wird auf der linken Seite geöffnet und zeigt den Aktivitätsverlauf für die ausgewählte interaktive Kommunikation an, einschließlich Anmerkungen und früherer Versionen.

   Beispielsweise kann die Zeitleiste nach einem Überprüfungszyklus Anmerkungen wie **Adresse aktualisieren** und **Fahrzeugmodell aktualisieren** zusammen mit anderen Aktivitätseinträgen anzeigen.

   ![Version 2 erstellen](/help/forms/interactive-communication/assets/create-version2.png)

1. Klicken Sie am unteren Rand des **Zeitleiste** auf **Als Version speichern**.

1. Geben **im Dialogfeld „Neue Version erstellen** eine Versionsbeschriftung und einen optionalen Kommentar ein, der den Zweck oder die Änderungen in dieser Version beschreibt.

   Geben Sie beispielsweise **Einschließlich des neuen Banklogos** als Versionskommentar ein.

   ![Version 3 erstellen](/help/forms/interactive-communication/assets/create-version3.png)

1. Klicken Sie auf **Erstellen**.

   Der Eintrag Neue Version wird in der Zeitleiste angezeigt und eine Erfolgsmeldung bestätigt, dass die Version erstellt wurde.

   ![Version 4 erstellen](/help/forms/interactive-communication/assets/create-version4.png)

Der Versionsliste wird ein neuer Versionseintrag hinzugefügt, der den aktuellen Status der interaktiven Kommunikation erfasst.

## Aktualisieren einer Version

Jedes Mal, wenn Sie die interaktive Kommunikation ändern und speichern, können Sie eine neue Version erstellen, um den aktualisierten Status zu erfassen.

So fügen Sie nach der Bearbeitung eine neue Version hinzu:

1. Öffnen Sie **Forms und** und wählen Sie die interaktive Kommunikation aus.

1. Öffnen Sie **Bedienfeld** Zeitleiste“ in der linken Leiste.

1. Führen Sie die Schritte in [Erstellen einer Version einer interaktiven Kommunikation](#create-a-version-of-an-interactive-communication) aus, um den aktuellen Status mit einer neuen Beschriftung und einem neuen Kommentar zu speichern.

Dies hilft Teams, den Fortschritt zu verfolgen, und sorgt für Transparenz im Lebenszyklus.

## Auf eine frühere Version zurücksetzen

Wenn eine interaktive Kommunikation zu einer früheren Konfiguration zurückkehren muss:

1. Navigieren Sie zu **Forms und** und wählen Sie die interaktive Kommunikation aus.

1. Öffnen Sie **Bedienfeld** Zeitleiste“ in der linken Leiste.

1. Wählen Sie in der Zeitleiste die Version aus, die Sie wiederherstellen möchten. Wählen Sie beispielsweise **Bank Interactive Communication V1** mit dem Kommentar **Enthält neues Banklogo**.

   ![Version 1 zurücksetzen](/help/forms/interactive-communication/assets/create-version5.png)

1. Klicken Sie auf **Auf diese Version zurück**.

   Eine Erfolgsmeldung bestätigt, dass die interaktive Kommunikation in der ausgewählten Version wiederhergestellt wurde. In der Zeitleiste wird ein Eintrag **Seite wiederhergestellt** aufgezeichnet.

   ![Version 2 zurücksetzen](/help/forms/interactive-communication/assets/create-version6.png)

Die interaktive Kommunikation wird in der ausgewählten Version wiederhergestellt, sodass Autoren unerwünschte Änderungen rückgängig machen oder Fehler beheben können.

## Vergleichen von zwei Versionen

Sie können zwei beliebige Versionen einer interaktiven Kommunikation nebeneinander vergleichen, während PDF eine Vorschau anzeigt. So können Sie Unterschiede im Layout und im statischen Inhalt einfach erkennen, ohne jede Version einzeln zu öffnen.

Eine schrittweise Anleitung finden Sie unter [Versionen der interaktiven Kommunikation vergleichen](/help/forms/interactive-communication/howto/compare-interactive-communication-versions.md).

## Hinzufügen von Kommentaren zu einer interaktiven Kommunikation

Mithilfe von Kommentaren können Überprüfende und Autoren allgemeine Anmerkungen direkt über das Bedienfeld **Zeitleiste** in **Forms und Dokumente** hinzufügen.

Hinzufügen eines Kommentars:

1. Navigieren Sie zu **Forms und** und wählen Sie die interaktive Kommunikation aus.

1. Öffnen Sie **Bedienfeld** Zeitleiste“ in der linken Leiste.

1. Geben Sie Ihre Notiz in das **Kommentar** Feld am unteren Rand des Bedienfelds **Zeitleiste** ein und speichern Sie sie.

   Kommentare werden in der Zeitleiste neben Anmerkungen, Versionseinträgen und anderen Aktivitäten angezeigt. Beispielsweise kann die Zeitleiste nach einem Überprüfungszyklus Anmerkungen wie &quot;**-Adresse“** &quot;**-Modell aktualisieren“** allgemeinen Kommentaren und Versionsverlauf auflisten.

Für positioniertes Review-Feedback auf Komponentenebene - bei dem ein Reviewer einen Kommentar an ein bestimmtes Feld oder einen bestimmten Abschnitt auf der Arbeitsfläche heftet - verwenden Sie stattdessen die Funktion Anmerkungen . Siehe [Überprüfen und Kommentieren einer interaktiven Kommunikation](/help/forms/interactive-communication/howto/review-and-annotate-interactive-communication.md).

## Siehe auch

- [Versionen der interaktiven Kommunikation vergleichen](/help/forms/interactive-communication/howto/compare-interactive-communication-versions.md)
- [Überprüfen und Kommentieren einer interaktiven Kommunikation](/help/forms/interactive-communication/howto/review-and-annotate-interactive-communication.md)
- [Erstellen einer interaktiven Kommunikation](/help/forms/interactive-communication/create-interactive-communication.md)

