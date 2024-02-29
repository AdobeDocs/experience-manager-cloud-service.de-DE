---
description: Dieses Tutorial enthält Anweisungen zum Erstellen eines Abschnitts eines Formulars, der wiederholbar ist
title: Wiederholbare Abschnitte in Edge Delivery Services
feature: Edge Delivery Services
source-git-commit: 3b24d0cd4099e0b8eb48c977f460b25c168af220
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# Wiederholbare Abschnitte in der Edge-Bereitstellung

Ein wiederholbarer Abschnitt ist eine Komponente eines Formulars, das mehrmals dupliziert oder repliziert wird, um Informationen für mehrere Vorkommen derselben Daten zu sammeln.

Betrachten Sie beispielsweise ein Formular, mit dem Informationen von Benutzern erfasst werden, die einen Kredit beantragen. Mit dem Formular können Benutzer persönliche Informationen bereitstellen, einschließlich Details zu den Mitliedern. Benutzer können Details für Mitbewerber eingeben, wobei dieser Abschnitt wiederholbar ist.

![Wiederholbare Abschnitte in Formularen](/help/forms/assets/eds-repeatable.png)

## Voraussetzungen

Richten Sie das GitHub-Projekt des Edge Delivery Service (EDS) mithilfe AEM Textbausteine ein und klonen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer. Siehe [Entwickler-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/build/tutorial.html) für Details.

## Wiederholbare Abschnitte in der Edge-Bereitstellung

Nehmen wir ein Beispiel für ein Kreditantragsformular. Mit dem Formular können Benutzer personenbezogene Daten senden. Sie können Details, die beide Antragsteller verwenden, mit wiederholbaren Abschnitten einbeziehen, mit der Möglichkeit, mindestens drei weitere Abschnitte hinzuzufügen.

>[!NOTE]
>
> * Sie können eine Microsoft Excel-Datei auf Ihrer SharePoint-Site oder auf Ihrem Google-Laufwerk erstellen, um die Feldsätze in einem Formular wiederholbar zu machen.
> * In diesem Fall nehmen wir ein Beispiel für eine Microsoft SharePoint. Um Ihren SharePoint-Ordner als Inhaltsquelle festzulegen, führen Sie die Schritte wie unter [Verwendung von Sharepoint](https://www.aem.live/docs/setup-customer-sharepoint).


So fügen Sie wiederholbare Abschnitte in der Edge-Bereitstellung hinzu:

1. [Erstellen eines Formulars mit Microsoft Excel](#author-form)
2. [Vorschau erstellen und Formular veröffentlichen](#preview-form)

### Erstellen eines Formulars mit Microsoft Excel {#author-form}

1. Wechseln Sie zu Ihrem Microsoft SharePoint-Konto und öffnen oder erstellen Sie AEM Projektverzeichnis für die Edge-Bereitstellung.
2. Öffnen Sie eine vorhandene Microsoft Excel-Datei oder erstellen Sie eine neue.
In diesem Beispiel verwenden wir eine Excel-Tabelle mit dem Namen `loan-application.xlsx` erstellt in der Microsoft SharePoint-Site.
3. Fügen Sie neue Spalten mit der Bezeichnung `Repeatable`, `Min`, und `Max` in Ihrer Microsoft Excel-Datei.
4. Geben Sie den Wert für die `Repeatable` column as `True` für das Feldset, das wiederholbar sein soll.
5. Geben Sie die Werte für die `Min` und `Max` Spalten. Die `Min` -Wert die Mindestanzahl von Vorkommen darstellt, für die das Bedienfeld wiederholt wird, während die `Max` -Wert die maximale Anzahl von Vorkommen, für die das Bedienfeld wiederholt.
6. Speichern Sie Ihre Microsoft Excel-Datei.

>[!NOTE]
>
> Hier finden Sie die [Darlehensantrag](/help/forms/assets/loan-application.xlsx) Excel-Tabelle für Ihre Referenz.

### Vorschau/Veröffentlichung des Formulars mit Ihrem Edge Delivery Service

1. Öffnen oder erstellen Sie eine neue Dokumentdatei auf einer Microsoft SharePoint-Site, um die Excel-Arbeitsmappe mit einer `Form Block`. Öffnen Sie beispielsweise die `index` und fügen Sie eine `Form Block`.
2. Öffnen Sie die Eingabeaufforderung, navigieren Sie zu Ihrem AEM Edge Delivery-Projektverzeichnis auf Ihrem lokalen Computer und führen Sie den Befehl als `aem up`.

Auf das Formular kann unter `https://localhost:3000`, wobei durch Klicken auf `Add` -Schaltfläche fügt einen neuen wiederholbaren Abschnitt zur Eingabe der Details des Mitbewerbers hinzu. Sie können den wiederholbaren Abschnitt auch löschen, indem Sie auf die `Delete` Schaltfläche.

>[!NOTE]
>
> Wenn beim Zugriff auf Ihr Formular auf localhost der Fehler &quot;Seite nicht gefunden&quot;auftritt, fügen Sie den Ordnernamen der Microsoft SharePoint-Site vor der URL hinzu, unter der sich Ihr Formular befindet. Beispiel: `http://localhost:3000/<dir-name>/`




