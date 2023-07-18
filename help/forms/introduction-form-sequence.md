---
title: Wie wird eine mehrstufige Formularsequenz erstellt?
description: Mit [!DNL Experience Manager Forms] können Sie eine Sequenz von Formularbereichen definieren, damit die Benutzer in einem adaptiven Formular navigieren und es ausfüllen können. Vertiefen Sie Ihre Kenntnisse, indem Sie sich an einem Anwendungsfall als Beispiel für das Erstellen einer mehrstufigen Formularsequenz orientieren.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 6b3f9131-db6b-451b-a932-b57d809222eb
source-git-commit: b6dcb6308d1f4af7a002671f797db766e5cfe9b5
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 75%

---

# Einführung in die mehrteilige Formularsequenz {#introduction-to-multi-step-form-sequence}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/introduction-form-sequence.html) |
| AEM as a Cloud Service | Dieser Artikel |

Mit adaptiven Formularen können Formularautoren ein müheloses mehrstufiges Datenerfassungserlebnis schaffen. Es bietet integrierte Unterstützung für das Erstellen mehrerer Bedienfelder und das Verknüpfen jedes Bedienfelds mit verschiedenen Navigationsmustern. Formularverfasser können Formularfelder in logischen Abschnitten gruppieren und eine Gruppe als Bedienfeld darstellen. Die gesamte Navigation zwischen den Bedienfeldern wird mithilfe des Bedienfeldlayouts gesteuert. Autoren können die Bedienfelder in unterschiedlichen Layouts anordnen, beispielsweise nacheinander mithilfe des Assistenten-Layouts oder ad hoc mithilfe des Registerkarten-Layouts. Informationen zu Bedienfeld-Layouts finden Sie unter [Layout-Möglichkeiten für adaptive Formulare](layout-capabilities-adaptive-forms.md).

In einer typischen Form beim Ausfüllen sind mehr Schritte erforderlich als nur das Erfassen von Daten. Eine vollständige Formularübermittlung kann andere Schritte umfassen, z. B. das digitale Signieren des Formulars, das Überprüfen der im Formular eingegebenen Informationen, das Verarbeiten von Zahlungen usw. Sie unterscheidet sich von Fall zu Fall.

Wenn in Ihrem Fall bestimmte Schritte für die Datenerfassung ausgeführt werden müssen oder aufgrund von Bestimmungen vorgeschrieben sind, bietet [!DNL Experience Manager Forms] die Möglichkeit, diese allgemeine Struktur bei allen Formularen zu erzwingen. Mit der Implementierung der vorher festgelegten Formularstruktur wird die Sequenz für ein Formular definiert. ![Beispiel für eine mehrstufige Formularsequenz](assets/formpipeline.png)

Beispiel für eine mehrstufige Formularsequenz

Nehmen wir ein Fallbeispiel, in dem Sie für ein Formular eine Sequenz der Schritte „Ausfüllen“, „Überprüfen“, „Signieren“ und „Bestätigen“ erstellen müssen. Die Schritte zum Erstellen einer solchen Sequenz lauten wie folgt:

1. Definieren Sie eine Formularvorlage und fügen Sie ihr den erforderlichen Bereich hinzu. Für jeden Schritt der Sequenz sollte ein Bedienfeld vorhanden sein. Sie können jedoch untergeordnete Bedienfelder in ein Bedienfeld einbinden.

   In diesem Beispiel können wir die folgenden Bedienfelder hinzufügen:

   * **[!UICONTROL Füllung]**: Sie enthält Formularfelder zur Datenerfassung. Hier können Sie verschachtelte untergeordnete Bedienfelder einfügen, um Abschnitte für verschiedene Arten von Informationen zu erstellen, z. B. persönlicher, familiärer, finanzieller Art usw.

   <!--* **[!UICONTROL Verify]**: It contains the **[!UICONTROL Verify]** component that can be used in an XFA-based Adaptive Form. It displays the information captured in the Fill panel in read-only mode for verification.-->


   * **[!UICONTROL E-sign]**: Enthält die Komponente **[!UICONTROL Sign]**, die in einem XFA-basierten adaptiven Formular verwendet werden kann. Damit werden die folgenden Services zum Signieren bereitgestellt:

      * Adobe Document Cloud eSignature-Services
      * Freihändige Unterschrift

   * **[!UICONTROL Bestätigung]**: Enthält die Komponente **[!UICONTROL Zusammenfassung]**, in der die Übermittlung in einer Meldung bestätigt wird, nachdem der Benutzer das Formular signiert hat und in der Sequenz den Bestätigungsschritt (Zusammenfassung) erreicht hat. Autoren können den Text der Komponente [!UICONTROL Zusammenfassung] konfigurieren, eine Dankesmeldung oder einen Link zur erstellten PDF-Datei anzeigen usw.

1. Wählen Sie für das Layout des Stammbedienfelds **[!UICONTROL Assistent]** aus.
1. Führen Sie die restlichen Schritte aus, um die Formularvorlage zu erstellen. <!-- For more information, see [Creating a custom Adaptive Form template](custom-adaptive-forms-templates.md). -->

Nachdem Sie die Formularsequenz in der Formularvorlage definiert haben, können Sie sie zum Erstellen von Formularen verwenden, deren Grundstruktur der gegenwärtig definierten Sequenz entspricht. Sie haben jedoch immer die Möglichkeit, das Formular Ihren Bedürfnissen anzupassen.
