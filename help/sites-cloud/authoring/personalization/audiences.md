---
title: Verwalten von Zielgruppen
description: 'Die Konsole „Zielgruppen“ ermöglicht das Erstellen, Organisieren und Verwalten von Zielgruppen für Ihr Adobe Target-Konto und das Verwalten von Segmenten für ContextHub  '
exl-id: dff72c15-afcd-4b16-a711-e9ca3010e3ec
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 100%

---

# Verwalten von Zielgruppen{#managing-audiences}

Die Konsole „Zielgruppen“ ermöglicht das Erstellen, Organisieren und Verwalten von Zielgruppen für Ihr Adobe Target-Konto und das Verwalten von Segmenten für ContextHub:

* Zielgruppen hinzufügen – entweder Adobe Target-Zielgruppen oder ContextHub-Segmente.
* Verwalten von Zielgruppen

Zielgruppen werden in ContextHub als *Segment* bezeichnet und sind Besuchergruppen, die durch bestimmte Kriterien definiert werden und mit denen bestimmt wird, wer welche zielgerichteten Inhalte zu sehen bekommt. Bei der Zielgruppenbestimmung von Aktivitäten können Zielgruppen entweder direkt während des Verfahrens der Zielgruppenbestimmung ausgewählt werden oder es können neue Zielgruppen in der Konsole „Zielgruppen“ erstellt werden.

In der Zielgruppen-Konsole werden die Zielgruppen nach Marken geordnet.

Zielgruppen stehen im Targeting-Modus für [das Verfassen zielgerichteter Inhalte](/help/sites-cloud/authoring/personalization/targeted-content.md) zur Verfügung. In diesem Modus können außerdem auch Zielgruppen erstellt werden (Zielgruppen für Adobe Target müssen hingegen in der Konsole „Zielgruppen“ erstellt werden). Zielgruppen, die Sie im Targeting-Modus erstellen, werden in der Zielgruppen-Konsole angezeigt.

Zielgruppen werden mit einer Beschriftung angezeigt, die beschreibt, welche Art von Zielgruppe definiert ist:

* CH – ContextHub-Segment
* AT – Adobe Target-Zielgruppe

## Erstellen von ContextHub-Segmenten mit der Konsole „Zielgruppen“ {#creating-a-contexthub-segment-in-the-audiences-console}

Sie können ContextHub-Segmente entweder in der Konsole „Zielgruppen“ oder während des Targeting-Verfahrens erstellen.

So erstellen Sie ContextHub-Segmente in der Konsole „Zielgruppen“:

1. Wählen Sie in der Navigationskonsole **Personalisierung** aus. Wählen Sie **Zielgruppen** aus.
1. Wählen Sie **ContextHub-Segment erstellen** aus.

   ![Erstellen eines Segments](/help/sites-cloud/authoring/assets/audiences-create-segment.png)

1. Geben Sie im Dialogfeld **Neues ContextHub-Segment** einen Titel ein, passen Sie die Verstärkung an und klicken Sie auf **Erstellen**. Das neue ContextHub-Segment erscheint in der Zielgruppenliste.

   >[!NOTE]
   >
   >Sie können die geänderte Liste sortieren, indem Sie **Geändert** auswählen, um eine neu erstellte Zielgruppe in absteigender Reihenfolge anzuzeigen.

Weitere Informationen zum Erstellen von Segmenten mit ContextHub finden Sie in der Dokumentation zum Konfigurieren der Segmentierung mit ContextHub. <!--For further detail about creating segments using ContextHub, see [Configuring Segmentation with ContextHub](/help/sites-administering/segmentation.md).-->

## Erstellen von Adobe Target-Zielgruppen mit der Konsole „Zielgruppen“ {#creating-an-adobe-target-audience-using-the-audience-console}

Sie können Adobe Target-Zielgruppen mithilfe der Zielgruppen-Konsole direkt in AEM erstellen.

Zielgruppen werden durch Regeln definiert, die bestimmen, wer in einer Zielgruppenbestimmungs-Aktivität enthalten ist. Eine Zielgruppendefinition kann mehrere Regeln enthalten und jede Regel kann mehrere Parameter enthalten.

Wenn Sie mehr als eine Regel verwenden, werden diese Regeln durch den booleschen Operator AND kombiniert. Das bedeutet, dass jedes potenzielle Mitglied der Zielgruppe alle definierten Bedingungen erfüllen muss, um in die Aktivität aufgenommen zu werden. Wenn Sie beispielsweise eine Betriebssystemregel und eine Browser-Regel definieren, werden nur Besucherinnen und Besucher, die sowohl das definierte Betriebssystem als auch den definierten Browser verwenden, in die Aktivität aufgenommen.

>[!NOTE]
>
>Wird Ihnen die Option **Target-Zielgruppe erstellen** unter **Erstellen** nicht angezeigt, verfügen Sie nicht über die nötigen Berechtigungen zur Erstellung von Zielgruppen. Sie müssen unter `/etc/segmentation` über Schreibrechte verfügen, um Zielgruppen erstellen zu können. Inhaltsautoren der Gruppe verfügen standardmäßig über Schreibrechte.

So erstellen Sie eine Adobe Target-Zielgruppe:

1. Wählen Sie in der Navigationskonsole **Personalisierung** aus. Wählen Sie **Zielgruppen** aus.

   ![Navigieren zu Zielgruppen](/help/sites-cloud/authoring/assets/audiences-navigation.png)

1. Wählen Sie in der Navigationskonsole **Erstellen** und anschließend **Target-Zielgruppe erstellen** aus.

   ![Erstellen einer Target-Zielgruppe](/help/sites-cloud/authoring/assets/audiences-create-target.png)

1. Wählen Sie im Dialogfeld **Adobe Target-Konfiguration** die Zielgruppenkonfiguration aus und wählen Sie dann **OK** aus.
1. Wählen Sie im Bereich für Regel Nr. 1 auf den Attributtyp und geben Sie in die verfügbaren Felder Attributinformationen ein. Wenn Sie fertig sind, wählen Sie das Häkchen rechts neben dem Attribut aus, um es zu speichern. Weitere Informationen zu allen Attributen finden Sie unter [Attribute und zugehörige Optionen](#attributes-and-their-options).
1. Klicken Sie auf **Regel hinzufügen**, um eine weitere Regel hinzuzufügen. Geben Sie so viele Regeln wie erforderlich ein. Regeln werden mit dem booleschen Operator UND kombiniert. Das bedeutet, dass die Zielgruppe alle Anforderungen jeder Regel erfüllen muss, um für eine Aktivität zugelassen zu werden.
1. Wählen Sie **Weiter** aus.
1. Geben Sie einen Namen für die Zielgruppe ein und wählen Sie **Speichern** aus.
1. Wählen Sie **Speichern** aus. Ihre Zielgruppe wird nun in der Zielgruppenliste angezeigt.

### Attribute und zugehörige Optionen {#attributes-and-their-options}

Sie können Targeting-Regeln für jedes der folgenden Attribute erstellen:

| **Attribut** | **Beschreibung** | **Für weitere Informationen** |
|---|---|---|
| **Mobilgerät** | Targeting von Mobilgeräten anhand von Parametern wie Mobilgerät, Gerätetyp, Geräteanbieterfirma, Bildschirmmaße (in Pixeln) usw. | Siehe [Mobile-Dokumentation](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/mobile.html?lang=de) in Adobe Target. |
| **Benutzerdefiniert** | Benutzerdefinierte Parameter sind Mbox-Parameter. Wenn Sie Mbox-Parameter an Mboxes übergeben oder die Funktion „targetPageParams“ verwenden, werden diese Parameter hier angezeigt und können in Zielgruppen verwendet werden. | Siehe [Dokumentation zu benutzerdefinierten Parametern](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/custom-parameters.html?lang=de) in Adobe Target. |
| **BS** | Sie können Besucherinnen und Besucher, die ein bestimmtes Betriebssystem verwenden, als Ziel auswählen. | Targeting von Benutzerinnen und Benutzern, die Linux, Macintosh oder Windows verwenden. |
| **Seiten der Site** | Targeting von Besucherinnen und Besuchern, die sich auf einer bestimmten Seite befinden oder die einen bestimmten mBox-Parameter aufweisen. | Weitere Informationen finden Sie in der [Dokumentation für Website-Seiten](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/site-pages.html?lang=de) für Adobe Target. |
| **Browser** | Sie können Benutzerinnen und Benutzer, die beim Besuch Ihrer Seite einen bestimmten Browser oder bestimmte Browser-Optionen verwenden, als Ziel auswählen. | Weitere Informationen finden Sie in der [Dokumentation für Browser-Optionen](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/browser.html?lang=de) für Adobe Target. |
| **Besucherprofil** | Targeting von Besucherinnen und Besuchern, die bestimmte Profilparameter erfüllen. | Weitere Informationen finden Sie in der [Dokumentation für Besucherprofile](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/visitor-profile.html?lang=de) für Adobe Target. |
| **Traffic-Quellen** | Targeting von Besuchern auf Grundlage der Suchmaschine oder Landingpage, von der sie auf Ihre Site geleitet werden | Weitere Informationen finden Sie in der [Dokumentation für Traffic-Quellen](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/traffic-sources.html?lang=de) für Adobe Target. |

## Bearbeiten von Zielgruppen mithilfe der Konsole „Zielgruppen“ {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>Sie können nur Adobe Target-Zielgruppen bearbeiten, die in derselben AEM-Instanz erstellt wurden, in der Sie gerade arbeiten. Zielgruppen, die in anderen AEM-Umgebungen erstellt wurden, können nicht bearbeitet werden.

ContextHub-Zielgruppen lassen sich beliebig mit der Konsole „Zielgruppen“ bearbeiten. Sie können zudem Adobe Target-Zielgruppen bearbeiten, jedoch nur diejenigen, die in AEM erstellt wurden:

1. Wählen Sie in der Navigationskonsole **Personalisierung** aus. Wählen Sie **Zielgruppen** aus.
1. Wählen Sie das Symbol neben dem zu bearbeitenden ContextHub-Segment aus und wählen Sie **Bearbeiten** aus.
1. Bearbeiten Sie die gewünschten Einstellungen im Editor. Weitere Informationen finden Sie in der ContextHub-Dokumentation. <!--See the [ContextHub](/help/sites-administering/contexthub-config.md) documentation for more information.-->
