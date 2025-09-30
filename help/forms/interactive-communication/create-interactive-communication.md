---
title: Erstellen einer interaktiven Kommunikation
description: Erstellen Sie personalisierte, datengesteuerte Kommunikation. Entdecken Sie wichtige Funktionen, Onboarding-Schritte und Anwendungsfälle in der Praxis mit Handbüchern und Tutorials.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: c23145c9-078d-4b03-a8f4-2d835cdd1592
source-git-commit: 8f25010ed57bd76acac7c56533ba8e37913511b7
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 11%

---


# Erstellen einer interaktiven Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

Interaktive Kommunikation ermöglicht Ihnen das Erstellen, Verwalten und Bereitstellen personalisierter und interaktiver Kommunikation, einschließlich Kundendienst, Abrechnung, Onboarding-Dokumenten, Angebotsbriefen, Kontoaktualisierungen und mehr. Sie wurde entwickelt, um alle Szenarien zu unterstützen, in denen dynamische, benutzerspezifische Inhalte das Kommunikationserlebnis branchenübergreifend verbessern.

Angenommen, Sie müssen Tausenden von Kunden einen Kontoauszug, eine Versicherungspolice oder eine Stromrechnung senden. Jedes hat dasselbe Layout, aber personalisierte Daten. Interaktive Kommunikation (IC) ermöglicht dies effizient.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/introimg.png)

Die manuelle Erstellung dieser Dokumente kann zeitaufwendig sein und führt oft zu Inkonsistenzen, insbesondere wenn Personalisierung und Datenintegration erforderlich sind. Mit dem Editor für interaktive Kommunikation können Benutzer den Prozess der Erstellung interaktiver Kommunikation optimieren.

## Voraussetzung

* [Stellen Sie sicher, dass der Autor Mitglied der Gruppe forms-users ist](/help/forms/setup-forms-cloud-service.md#configure-users)

## Erstellen einer interaktiven Kommunikation

Wählen Sie aus verschiedenen Szenarien, um eine interaktive Kommunikation zu erstellen, basierend auf dem erforderlichen Grad der Wiederverwendung und Datenintegration:

+++ Erstellen einer leeren interaktiven Kommunikation

Das Erstellen einer leeren interaktiven Kommunikation ermöglicht es Ihnen, von Grund auf neu zu beginnen, ideal, wenn Sie die volle Kontrolle über Layout, Struktur und Logik wünschen.
Schritte zum Befolgen:

1. Öffnen Sie Ihre **Adobe Experience Manager (AEM) Forms as a Cloud Service-**.
1. Navigieren Sie zu **Forms > Forms und Dokumente**.
1. Klicken Sie **Erstellen > Interaktive Kommunikation**.

   ![IC-Dokument suchen](/help/forms/interactive-communication/assets/comm.png)

1. Lassen Sie im Erstellungsbildschirm das Feld &quot;**&quot;**.

   ![IC-Dokument suchen](/help/forms/interactive-communication/assets/create-ic-document.png)

1. Füllen Sie andere Details wie Titel, Name, Autor usw. aus.
1. Klicken Sie **Erstellen**, um die Editor-Benutzeroberfläche für interaktive Kommunikation aufzurufen und mit der Gestaltung zu beginnen.
1. Dadurch wird der IC-Editor geöffnet, in dem Sie mit der Gestaltung Ihrer Kommunikation beginnen können.
+++

+++ Erstellen einer vorlagenbasierten interaktiven Kommunikation

Die Verwendung einer Vorlage beschleunigt den Entwurf, indem konsistente Layout-Elemente wie Kopf- und Fußzeilen, Logos oder Standardformatierung wiederverwendet werden.
Vorlagen stellen die Markenkonsistenz sicher und sparen Zeit für häufig verwendete Kommunikationstypen. Führen Sie die folgenden Schritte aus:

1. Öffnen Sie die AEM Forms as a Cloud Service-Instanz.
1. Wechseln Sie zu **Forms > Forms und Dokumente** und klicken Sie auf **Erstellen > Interaktive Kommunikation**.
1. Wählen Sie im Erstellungsformular **Option** aktivierte Vorlage aus der Dropdown-Liste aus.
1. Füllen Sie andere Details wie Titel, Name, Autor usw. aus.
1. Klicken Sie **Erstellen**, um Ihre Kommunikation mit der ausgewählten Vorlagenstruktur zu gestalten.
1. Dadurch wird der IC-Editor geöffnet, in dem Sie mit der Gestaltung Ihrer Kommunikation beginnen können.
+++

+++ Erstellen einer interaktiven Kommunikation mit Daten

Dateninteraktive Kommunikation personalisiert Inhalte automatisch mithilfe von Backend-Daten.
Ideal für Auszüge, Rechnungen oder Benachrichtigungen, bei denen die Struktur konstant bleibt, die Daten jedoch je nach Empfänger variieren. Schritte zum Befolgen:

1. Öffnen Sie die AEM Forms as a Cloud Service-Instanz.
1. Wechseln Sie zu **Forms > Forms und Dokumente** und klicken Sie auf **Erstellen > Interaktive Kommunikation**.
1. Verknüpfen Sie im Feld **Formulardatenmodell** Ihr vordefiniertes **FDM (Formulardatenmodell)**.
1. Füllen Sie andere Details wie Titel, Name, Autor usw. aus.
1. Verwenden Sie **Datenmodell** innerhalb des Editors, um Felder an dynamische Daten (z. B. Kundenname, Saldo, Kontonummer) zu binden.
1. Verwenden Sie **Inhaltsbereiche,** und **Fragmente**, um Daten nach Bedarf zu strukturieren und zu wiederholen.
1. Vorschau mit **PDF-Vorschau** und Abschließen der Kommunikation für den Versand.
1. Dadurch wird der IC-Editor geöffnet, in dem Sie mit der Gestaltung Ihrer Kommunikation beginnen können.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/ic-ui.png)
+++

Beginnen Sie mit der Erstellung interaktiver Kommunikationen, um Ihre Workflows zu optimieren und wirkungsvolle, benutzerspezifische Erlebnisse bereitzustellen.

## Nächste Schritte

[Erstellen einer interaktiven Kommunikationsvorlage](/help/forms/interactive-communication/create-interactive-communication-template.md)
[Erstellen eines interaktiven Kommunikationsfragments](/help/forms/interactive-communication/create-interactive-communication-fragment.md)
