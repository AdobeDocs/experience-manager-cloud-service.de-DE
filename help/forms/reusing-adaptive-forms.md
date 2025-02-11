---
title: Wie kann ich die Metadateneigenschaften eines adaptiven Formulars wiederverwenden?
description: Entdecken Sie, wie Sie ein vorhandenes adaptives Formular effizient wiederverwenden können, um ein neues zu erstellen.
seo-description: You can reuse an existing Adaptive Form to create new Adaptive Forms.
feature: Adaptive Forms, Foundation Components
exl-id: fb8cf3a9-fd19-46bf-b40e-2af76ca68b9f
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: ht
source-wordcount: '601'
ht-degree: 100%

---

# Wiederverwenden von Metadateneigenschaften eines adaptiven Formulars {#reusing-adaptive-forms}

>[!NOTE]
>
> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für die Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/creating-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben.


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/reusing-adaptive-forms.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Wenn Sie für ein neues adaptives Formular einige der Eigenschaften eines vorhandenen adaptiven Formulars verwenden möchten, können Sie einfach die Funktion zum Kopieren/Einfügen verwenden. Darüber hinaus können Sie das neue adaptive Formular in den gewünschten Ordnerpfad einfügen. Alle Metadateneigenschaften werden repliziert und die XFAs und XSDs für XFA- und XSD-basierte adaptive Formulare werden ebenfalls kopiert.

>[!NOTE]
>
>Status- und Überprüfungsdetails werden nicht kopiert. Wenn Ihr adaptives Formular zum Beispiel veröffentlicht wird und Sie es dann kopieren, befindet sich das eingefügte adaptive Formular im unveröffentlichten Status. Ebenso wenig wird, wenn ein kopiertes Asset überprüft wird, das eingefügte Asset derselben Überprüfung unterzogen.

## Kopieren eines adaptiven Formulars {#copy-an-adaptive-form}

Kopieren Sie ein adaptives Formular mithilfe eines der folgenden Verfahren:

1. Klicken Sie in Schnellaktionen auf das Symbol ![aem6forms_copy](assets/aem6forms_copy.png) zum Kopieren.

   >[!NOTE]
   >
   >Schnellaktionen sind die Aktionselemente, die beim Zeigen mit der Maus auf eine Miniaturansicht angezeigt werden.

1. Wählen Sie das adaptive Formular aus. Der Auswahlprozess unterscheidet sich je nach Ansicht.

   Wenn Sie sich in der Kartenansicht befinden, wechseln Sie zum Auswahlmodus, indem Sie auf das Auswahlsymbol ![aem6forms_check-circle](assets/aem6forms_check-circle.png) und dann auf alle adaptiven Formulare klicken, die kopiert werden sollen.

   Wenn Sie sich in der Listenansicht befinden, aktivieren Sie die Kontrollkästchen der gewünschten adaptiven Formulare, um sie auszuwählen.

   >[!NOTE]
   >
   >Alle ausgewählten Assets müssen adaptive Formulare sein, da die Funktion zum Kopieren/Einfügen nur bei adaptiven Formularen unterstützt wird. Außerdem müssen sich alle ausgewählten Elemente im selben Ordner befinden.

   Nach dem Auswählen der Assets klicken Sie in der Symbolleiste auf das Symbol ![aem6forms_copy](assets/aem6forms_copy.png) zum Kopieren, um das ausgewählte adaptive Formular zu kopieren.

## Einfügen eines adaptiven Formulars {#paste-an-adaptive-form}

Beim Klicken auf die Aktion zum Kopieren wird der Auswahlmodus automatisch beendet und das Symbol ![Paste](assets/Smock_Paste_18_N.svg) zum Einfügen wird angezeigt. Wechseln Sie nun zum gewünschten Ordnerpfad und klicken Sie auf das Symbol ![Paste](assets/Smock_Paste_18_N.svg) zum Einfügen, um das kopierte adaptive Formular einzufügen.

Wenn Sie in denselben Ordner einfügen oder sich im Zielordner eine weitere Datei mit demselben Knotennamen (mit dem sie im CRX-Repository gespeichert ist) befindet, wird am Suffix eine 1 angehängt (zum Beispiel wird „myaf“ zu „myaf1“ und wenn sich „myaf1“ am selben Speicherort befindet, wird „myaf“ zu „myaf2“). Alle anderen Eigenschaften bleiben genauso wie beim ursprünglichen adaptiven Formular.

Nachdem Sie auf das Symbol ![Paste](assets/Smock_Paste_18_N.svg) zum Einfügen geklickt haben, wird es wieder ausgeblendet. Sie können jeweils nur einmal einfügen. Wenn Sie vom selben Asset erneut eine Kopie erstellen möchten, kopieren Sie es erneut.

## Ändern der Inhalte eines neuen adaptiven Formulars {#change-contents-of-new-adaptive-form}

Wenn Sie eingefügte adaptive Formulare anders als das kopierte Formular gestalten möchten, können ihre Inhalte mithilfe folgender Methoden geändert werden:

1. **Ändern der Metadateneigenschaften:**

   Sie können die Metadateneigenschaften des adaptiven Formulars ändern, z. B. Titel und Beschreibung. Weitere Informationen zu Metadateneigenschaften und dazu, wie diese geändert werden können, finden Sie unter [Verwalten von Formularmetadaten](manage-form-metadata.md).

1. **Ändern von XFA/XSD für XFA-/XSD-basierte adaptive Formulare:**

   Sie können die in adaptiven Formularen verwendete XFA/XSD ändern. Informationen zum Ändern dieser adaptiven Formulare finden Sie unter [Verwalten von Formularmetadaten](manage-form-metadata.md).

1. **Neu veröffentlichen:**

   Das eingefügte Asset unterscheidet sich vom kopierten Asset. Sie können es als neues Asset veröffentlichen, um es für Endbenutzende verfügbar zu machen. Unter <!-- see [Publishing and unpublishing forms](publishing-unpublishing-forms.md) --> erfahren Sie, wie ein Asset veröffentlicht wird,


## Siehe auch {#see-also}

{{see-also}}