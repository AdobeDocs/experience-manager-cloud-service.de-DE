---
title: Wie erstelle ich eine mehrstufige Formularsequenz?
description: Mit [!DNL Experience Manager Forms]können Sie eine Sequenz von Formularfeldern definieren, damit Benutzer in einem adaptiven Formular navigieren und es ausfüllen können.
role: User
level: Intermediate
feature: Adaptive Forms, Foundation Components
exl-id: 6b3f9131-db6b-451b-a932-b57d809222eb
source-git-commit: 0eac90a8f120a9c7655e68533d4b0a32292621e1
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 75%

---

# Einführung in die mehrteilige Formularsequenz {#introduction-to-multi-step-form-sequence}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/creating-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/introduction-form-sequence.html) |
| AEM as a Cloud Service | Dieser Artikel |

Mit adaptiven Formularen können Formularautoren ein müheloses mehrstufiges Datenerfassungserlebnis schaffen. Es bietet integrierte Unterstützung für das Erstellen mehrerer Panels und das Verknüpfen jedes Panels mit verschiedenen Navigationsmustern. Formularautorinnen und -autoren können Formularfelder in logischen Abschnitten gruppieren und eine Gruppe als Panel darstellen. Die gesamte Navigation zwischen den Bedienfeldern wird mithilfe des Bedienfeldlayouts gesteuert. Autoren können die Bedienfelder in verschiedenen Layouts anordnen, z. B. durch sequenzielles Platzieren mit dem Assistentenlayout oder durch Importieren mit dem Registerkartenlayout. Informationen zu Bedienfeld-Layouts finden Sie unter [Layout-Möglichkeiten für adaptive Formulare](layout-capabilities-adaptive-forms.md).

In einer typischen Form beim Ausfüllen sind mehr Schritte erforderlich als nur das Erfassen von Daten. Eine vollständige Formularübermittlung kann andere Schritte umfassen, z. B. das digitale Signieren des Formulars, das Überprüfen der im Formular eingegebenen Informationen, das Verarbeiten von Zahlungen usw. Sie unterscheidet sich von Fall zu Fall.

Wenn in Ihrem Fall bestimmte Schritte für die Datenerfassung ausgeführt werden müssen oder aufgrund von Bestimmungen vorgeschrieben sind, bietet [!DNL Experience Manager Forms] die Möglichkeit, diese allgemeine Struktur bei allen Formularen zu erzwingen. Mit der Implementierung der vorher festgelegten Formularstruktur wird die Sequenz für ein Formular definiert. ![Beispiel für eine mehrstufige Formularsequenz](assets/formpipeline.png)

Beispiel für eine mehrstufige Formularsequenz

Nehmen wir ein Fallbeispiel, in dem Sie für ein Formular eine Sequenz der Schritte „Ausfüllen“, „Überprüfen“, „Signieren“ und „Bestätigen“ erstellen müssen. Die Schritte zum Erstellen einer solchen Sequenz lauten wie folgt:

1. Definieren Sie eine Formularvorlage und fügen Sie ihr den erforderlichen Bereich hinzu. Für jeden Schritt der Sequenz sollte ein Bedienfeld vorhanden sein. Sie können jedoch untergeordnete Bedienfelder in ein Bedienfeld einbinden.

   In diesem Beispiel können wir die folgenden Bedienfelder hinzufügen:

   * **[!UICONTROL Ausfüllen]**: Enthält Formularfelder zum Erfassen von Daten. Hier können Sie verschachtelte untergeordnete Bedienfelder einfügen, um Abschnitte für verschiedene Arten von Informationen zu erstellen, z. B. persönlicher, familiärer, finanzieller Art usw.

   <!--* **[!UICONTROL Verify]**: It contains the **[!UICONTROL Verify]** component that can be used in an XFA-based Adaptive Form. It displays the information captured in the Fill panel in read-only mode for verification.-->


   * **[!UICONTROL E-sign]**: Enthält die Komponente **[!UICONTROL Sign]**, die in einem XFA-basierten adaptiven Formular verwendet werden kann. Damit werden die folgenden Services zum Signieren bereitgestellt:

      * Adobe Document Cloud eSignature-Services
      * Freihändige Unterschrift

   * **[!UICONTROL Bestätigung]**: Enthält die Komponente **[!UICONTROL Zusammenfassung]**, in der die Übermittlung in einer Meldung bestätigt wird, nachdem der Benutzer das Formular signiert hat und in der Sequenz den Bestätigungsschritt (Zusammenfassung) erreicht hat. Autoren können den Text der Komponente [!UICONTROL Zusammenfassung] konfigurieren, eine Dankesmeldung oder einen Link zur erstellten PDF-Datei anzeigen usw.

1. Wählen Sie für das Layout des Stammbedienfelds **[!UICONTROL Assistent]** aus.
1. Führen Sie die restlichen Schritte aus, um die Formularvorlage zu erstellen. <!-- For more information, see [Creating a custom Adaptive Form template](custom-adaptive-forms-templates.md). -->

Nachdem Sie die Formularsequenz in der Formularvorlage definiert haben, können Sie sie zum Erstellen von Formularen verwenden, deren Grundstruktur der gegenwärtig definierten Sequenz entspricht. Sie haben jedoch immer die Möglichkeit, das Formular Ihren Bedürfnissen anzupassen.


## Siehe auch {#see-also}

{{see-also}}