---
title: Erstellen von Regeln im Editor für interaktive Kommunikation
description: Mit Regeln erstellen im Editor für interaktive Kommunikation können Autoren dynamische Verhaltensweisen definieren, die Kommunikation interaktiv und intelligent machen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 9538ae2e-e0f5-4e85-943e-00fe99a64725
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 2%

---

# Regeleditor im Editor für interaktive Kommunikation


>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.


## &#x200B;1. Einführung


Der Regeleditor im Editor für interaktive Kommunikation ermöglicht es Autoren, dynamische Verhaltensweisen zu definieren, die Kommunikation interaktiv und intelligent machen. Regeln steuern, wie sich Felder basierend auf Benutzeraktionen oder zugrunde liegenden Daten verhalten, anzeigen oder berechnen, um sicherzustellen, dass jede Kommunikation personalisiert und kontextbezogen ist.


Von einfachen Sichtbarkeitseinstellungen bis hin zu komplexer bedingter Logik ermöglichen Regeln es Autoren, Erlebnisse bereitzustellen, die sich in Echtzeit anpassen und dadurch die Benutzerfreundlichkeit, Genauigkeit und Interaktion verbessern.


![IC-Dokument suchen](/help/forms/interactive-communication/assets/rule-creation.png)


## &#x200B;2. Eigenschaften


2.1 Einrichten von Feldeigenschaften und -verhalten


- **Eingabetypen:** Definieren Sie den Datentyp, den ein Feld akzeptiert, z. B. Text, Zahlen, Daten oder boolesche Werte, um eine ordnungsgemäße Validierung und Formatierung sicherzustellen.


- **Sichtbarkeitsregeln:**, ob ein Feld basierend auf Bedingungen sichtbar, ausgeblendet oder dynamisch angezeigt wird (z. B. „Rabattfeld nur anzeigen, wenn Promo-Code angewendet wird„).


- **Standardwerte:** Definieren Sie Werte in Feldern vorab (z. B. das heutige Datum, den Kundennamen aus dem Datenmodell), um Zeit zu sparen und die Genauigkeit zu verbessern.


2.2 Implementieren von Berechnungen, Validierungen und Regellogik


- **Feldlogik:** Automatisieren Sie Berechnungen und Feldbeziehungen, z. B. die Berechnung von Rechnungsbeträgen oder das automatische Ausfüllen abhängiger Felder.


- **Benutzerdefinierte Regeln:** Erstellen Sie mit dem Regeleditor eine erweiterte Logik für komplexe Szenarien wie Eignungsprüfungen oder stufenbasierte Preise.


- **Bedingte Aktionen** Definieren Sie Trigger, die auf Benutzereingaben oder Datenwerte reagieren, z. B. das Aktivieren/Deaktivieren von Feldern, das Anzeigen von Nachrichten oder das Verzweigen in verschiedene Abschnitte.


![IC-Dokument suchen](/help/forms/interactive-communication/assets/rule-creation1.png)


## &#x200B;3. Verwendung


Der Regeleditor wird häufig verwendet, um sicherzustellen, dass Formulare und Kommunikationen responsiv und kontextbezogen sind:


- **Dynamische Anzeige** Blenden Sie Abschnitte je nach Kundentyp oder ausgewählten Optionen ein oder aus.


- **Validierung:** Sie Fehler, indem Sie Formate, Bereiche oder obligatorische Eingaben überprüfen.


- **Automatische Berechnungen:** Vereinfachen Sie Benutzeraufgaben mit Formeln (z. B. Steuern, Summen oder Rabatte).


- **Workflow-Steuerung** Aktivieren Sie bestimmte Schaltflächen, Felder oder Aktionen nur, wenn die Voraussetzungen erfüllt sind.


- **Personalization:** Passen Sie die Kommunikation an das Profil, die Voreinstellungen oder die Eignungskriterien der Empfängerin bzw. des Empfängers an.


## 4. Best Practices


- **Regeln einfach halten:** Sie komplexe Logik in kleinere, modulare Regeln auf, um die Wartung zu vereinfachen.


- **Sichtbarkeitslogik priorisieren:** Sie unnötige Felder frühzeitig aus, um das Benutzererlebnis zu optimieren.


- **Gründlich testen:** Vorschau von Regeln mit mehreren Datensätzen, um die Genauigkeit zu bestätigen und Konflikte zu vermeiden.


- **Verwenden Sie die Standardwerte mit Bedacht:** Vorbefüllen von Feldern, die sich selten ändern, aber Flexibilität für die Bearbeitung zulassen.


- **Nutzen bedingter Aktionen:** Wenden Sie sie an, um die Interaktivität zu steigern, aber vermeiden Sie es, die Benutzer zu überfordern.


- **Dokumentenregeln:** Sie eine Aufzeichnung der Geschäftslogik, um Klarheit für Entwickler und Stakeholder zu gewährleisten.


Durch die sorgfältige Konfiguration von Regeln können Autoren Kommunikationen erstellen, die intelligent auf Daten und Benutzeraktionen reagieren. So werden Prozesse optimiert, Fehler reduziert und ein nahtloses, personalisiertes Erlebnis bereitgestellt.
