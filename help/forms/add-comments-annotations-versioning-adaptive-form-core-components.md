---
title: Fügen Sie einem Formular Versionen, Kommentare und Anmerkungen hinzu.
description: Verwenden Sie die Kernkomponenten des adaptiven Formulars, um einem adaptiven Formular Kommentare, Anmerkungen und Versionierungen hinzuzufügen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Adaptive Forms, Core Components
exl-id: 84b95a19-c804-41ad-8f4b-5868c8444cc0
role: User, Developer, Admin
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 2%

---

# Versionierung, Überprüfen und Kommentieren eines adaptiven Formulars

<!--Before you can use versionings, comments, and annotations in an Adaptive Form, you must ensure you have [enabled Adaptive Form Core Components](
https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/enable-adaptive-forms-core-components).-->

<!--Adaptive Form Core Components facilitates to add versionings, comments, and annotations to a form. These features helps form authors and users to enhance the form development process where they can create multiple versions of a form, collaborate and add their comments to a form, and add annotations to form components.-->

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, auf die über unseren [Vorabveröffentlichungskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features) zugegriffen werden kann. </span>


Kernkomponenten für adaptive Formulare bieten Funktionen, mit denen Formularautoren Versionierung, Kommentar und Anmerkungen in Formulare integrieren können. Diese Funktionen dienen dazu, den Formularentwicklungsprozess zu optimieren, indem Benutzer mehrere Versionen eines Formulars erstellen und verwalten, durch Kommentare an gemeinsamen Diskussionen teilnehmen und Anmerkungen an bestimmte Formularkomponenten anhängen können, wodurch die gesamte Erfahrung bei der Formularerstellung verbessert wird.


## Versionierung adaptiver Formulare {#adaptive-form-versioning}

Die Versionierung adaptiver Formulare hilft beim Hinzufügen von Versionen zu einem Formular. Formularautoren können einfach mehrere Versionen eines Formulars erstellen und schließlich die Version verwenden, die für die Geschäftsziele geeignet ist. Darüber hinaus können Formularbenutzer das Formular auch auf die vorherigen Versionen zurücksetzen. Außerdem können Autoren zwei Versionen eines Formulars vergleichen, indem sie eine Vorschau davon anzeigen. So können sie Formulare aus der Perspektive der Benutzeroberfläche besser analysieren. Im Folgenden werden die einzelnen Funktionen für die Versionierung adaptiver Formulare genauer beschrieben:

### Formularversion erstellen {#create-a-form-version}

Gehen Sie wie folgt vor, um eine Formularversion zu erstellen:

1. Erstellen Sie ein Formular oder verwenden Sie ein vorhandenes Formular.
1. Navigieren Sie in AEM Benutzeroberfläche zu &quot;**[!UICONTROL Formular]**>**[!UICONTROL Forms &amp; Dokumente]**&quot;und wählen Sie Ihr **Formular** aus.
1. Wählen Sie im Dropdown-Menü &quot;Auswahl&quot;im linken Bereich **[!UICONTROL Versionen]** aus.
   ![Formular auswählen](select-a-form.png)
1. Klicken Sie im unteren Bereich auf der linken Seite auf die Punkte **drei Punkte** und klicken Sie auf **[!UICONTROL Als Version speichern]**.
1. Geben Sie nun eine Beschriftung für die Formularversion an und Sie können Informationen über das Formular durch den Kommentar angeben.
   ![Erstellen einer Formularversion](create-a-form-version.png)

### Formularversion aktualisieren {#update-a-form-version}

Wenn Sie das adaptive Formular bearbeiten und aktualisieren, fügen Sie dem Formular eine neue Version hinzu. Führen Sie die im letzten Abschnitt angegebenen Schritte aus, um eine neue Version des Formulars zu benennen, wie in der Abbildung dargestellt:

![Aktualisieren einer Formularversion](update-a-form-version.png)

### Formularversion wiederherstellen {#revert-a-form-version}

Um eine Formularversion wieder auf die vorherige Version zurückzusetzen, wählen Sie eine Formularversion aus und klicken Sie auf **[!UICONTROL Auf diese Version zurücksetzen]**.

![Formularversion zurücksetzen](revert-form-version.png)

### Vergleichen von Formularversionen {#compare-form-versions}

Formularautoren können zwei verschiedene Versionen eines Formulars zu Vorschauzwecken vergleichen. Um Versionen zu vergleichen, wählen Sie eine beliebige Formularversion aus und klicken Sie auf **[!UICONTROL Mit aktueller Version vergleichen]**. Es werden zwei verschiedene Formularversionen im Vorschaumodus angezeigt.

![Vergleichen von Formularversionen](compare-form-versions.png)

## Kommentare hinzufügen {#add-comments}

Bei einer Überprüfung handelt es sich um einen Mechanismus, mit dem ein oder mehrere Überprüfer Formulare kommentieren können. Jeder Formularbenutzer kann ein Formular kommentieren oder durch Kommentare ein Formular überprüfen. Um einen Kommentar für ein Formular zu erhalten, wählen Sie ein **[!UICONTROL Formular]** aus und fügen Sie dem Formular einen **[!UICONTROL Kommentar]** hinzu.

>[!NOTE]
> Wenn Sie, wie oben beschrieben, Kommentare in Kernkomponenten adaptiver Formulare verwenden, ist die Formularfunktion [Erstellen und Verwalten von Überprüfungen für Formulare](/help/forms/create-reviews-forms.md) deaktiviert.


![Hinzufügen von Kommentaren zu einem Formular](form-comments.png)

## Hinzufügen von Anmerkungen {#adaptive-form-annotations}

In vielen Fällen müssen Benutzer von Formulargruppen Anmerkungen zu einem Formular hinzufügen, um diese zu überprüfen, z. B. auf einer bestimmten Registerkarte eines Formulars oder von Komponenten eines Formulars. In solchen Fällen können Autoren Anmerkungen verwenden. Gehen Sie wie folgt vor, um einem Formular Anmerkungen hinzuzufügen:

1. Öffnen Sie ein Formular im Modus **[!UICONTROL Bearbeiten]** .

1. Klicken Sie auf das Symbol **Hinzufügen** in der oberen rechten Leiste, wie im Bild angegeben.
   ![Anmerkung](annotation.png)

1. Klicken Sie auf das Symbol **Hinzufügen** in der oberen linken Leiste, wie im Bild angegeben, um die Anmerkung hinzuzufügen.
   ![Anmerkung hinzufügen](add-annotation.png)

1. Jetzt können Sie Kommentare hinzufügen und Zeichnungen mit mehreren Farben zeichnen, um Komponenten zu bilden.

1. Um alle Anmerkungen anzuzeigen, die Sie einem Formular hinzugefügt haben, wählen Sie das Formular aus und sehen Sie die Anmerkungen, die im linken Bereich hinzugefügt wurden, wie im Bild dargestellt.

   ![Siehe hinzugefügte Anmerkungen](see-annotations.png)

## Siehe auch {#see-also}

{{see-also}}
