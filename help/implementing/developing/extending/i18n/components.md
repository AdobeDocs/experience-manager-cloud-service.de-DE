---
title: Internationalisieren von Komponenten
description: Internationalisieren Sie Komponenten und Dialogfelder, damit die zugehörigen Zeichenfolgen ihrer Benutzeroberflächen in unterschiedlichen Sprachen angezeigt werden können
topic-tags: components
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: b55f7260628f759de2718290624cdc82da7a2961
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 83%

---

# Internationalisieren von Komponenten{#internationalizing-components}

Internationalisieren Sie Komponenten und Dialogfelder, damit die zugehörigen Zeichenfolgen der Benutzeroberfläche in unterschiedlichen Sprachen angezeigt werden können. Komponenten, die für die Internationalisierung konzipiert sind, ermöglichen die Externalisierung, Übersetzung und den anschließenden Import von UI-Zeichenfolgen in das Repository. Zur Laufzeit bestimmen die Spracheinstellungen der Benutzenden oder das Gebietsschema der Seite, welche Sprache in der Benutzeroberfläche angezeigt wird.

![i18n-components-1.png](/help/implementing/developing/extending/assets/i18n-comp1.png)

Verwenden Sie den folgenden Prozess, um Ihre Komponenten zu internationalisieren und die Benutzeroberfläche in verschiedenen Sprachen bereitzustellen:

1. [Implementieren Sie Ihre Komponenten mit Code, der Zeichenfolgen internationalisiert.](/help/implementing/developing/extending/i18n/dev.md)Ihr Code identifiziert die zu übersetzenden Zeichenfolgen und wählt die Sprache aus, die zur Laufzeit angezeigt werden soll.
1. Erstellen Sie Wörterbücher und fügen Sie die zu übersetzenden englischen Zeichenfolgen hinzu.
1. Exportieren Sie das Wörterbuch in das XLIFF-Format, übersetzen Sie die Zeichenfolgen und importieren Sie dann die XLIFF-Dateien wieder in AEM.
1. Integrieren Sie das Wörterbuch in die Versionsverwaltung Ihrer Anwendung.

>[!NOTE]
>
>Die hier beschriebenen Methoden zur Internationalisierung von Komponenten sind für die Übersetzung statischer Zeichenfolgen gedacht. Wenn von Änderungen der Komponentenzeichenfolgen ausgegangen wird, sollten Sie herkömmliche Übersetzungs-Workflows verwenden. Wenn Autorinnen bzw. Autoren beispielsweise eine UI-Zeichenfolge mithilfe von Eigenschaften im Dialogfeld „Bearbeiten“ einer Komponente bearbeiten können, sollten Sie kein Sprachwörterbuch verwenden, um die Zeichenfolge zu internationalisieren.

## Sprachwörterbücher {#language-dictionaries}

Das AEM-Internationalisierungs6Framework verwendet Wörterbücher im Repository, um englische Zeichenfolgen und deren Übersetzungen in andere Sprachen zu speichern. Englisch ist die Standardsprache für das Framework. Zeichenfolgen werden anhand ihrer englischen Version identifiziert. In der Regel verwenden Internationalisierungs-Frameworks alphanumerische IDs für UI-Zeichenfolgen. Die Verwendung der englischen Version der Zeichenfolge als ID bietet mehrere Vorteile:

* Code ist leicht zu lesen.
* Die Standardsprache ist immer verfügbar.

Übersetzungsänderungen müssen von Git über die [CI/CD-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) in AEM as a Cloud Service stammen.

![i18n-components-2](/help/implementing/developing/extending/assets/i18n-comp2.png)


### Überschreiben von Zeichenfolgen in Systemwörterbüchern {#overlaying-strings-in-system-dictionaries}

Wenn Ihre Komponenten Zeichenfolgen verwenden, die in den AEM-Systemwörterbüchern enthalten sind, duplizieren Sie die Zeichenfolge in Ihrem eigenen Wörterbuch. Alle Komponenten verwenden dann die Zeichenfolgen aus Ihrem Wörterbuch.

Beachten Sie, dass sich nicht vorhersagen lässt, welche Übersetzung verwendet wird, wenn Zeichenfolgen in Wörterbüchern unter dem Knoten `/apps` doppelt vorliegen.
