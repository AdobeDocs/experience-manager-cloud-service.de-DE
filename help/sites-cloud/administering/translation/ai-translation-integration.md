---
title: Konfigurieren der KI-Übersetzungsintegration
description: Erfahren Sie, wie Sie Adobe Experience Manager mithilfe von Übersetzungs-Cloud-Services und dem Translation Integration Framework mit Azure OpenAI für die agentische Übersetzung verbinden.
feature: Language Copy
role: Admin
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
solution: Experience Manager Sites
source-git-commit: cb7dcc07a5913d6c7e88e0eec03f0003f1e3997a
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# Konfigurieren der KI-Übersetzungsintegration {#ai-translation-integration}

Mit der KI-Übersetzungsintegration können Sie ein **großes Sprachmodell (LLM)** Übersetzungs-Service für Inhalte verwenden, die Sie in Adobe Experience Manager erstellen. Sie verbinden AEM mit Ihrem LLM-Anbieter (beginnend mit Microsoft Azure OpenAI), verwenden dieselben [Übersetzungs-Workflows](/help/sites-cloud/administering/translation/overview.md) wie für andere Connectoren und laden optional **Übersetzungsstil-Handbücher** hoch, damit AEM Regeln generieren kann, die den Ton, die Terminologie und die Markensprache über Gebietsschemata hinweg konsistent halten.

Hintergrundinformationen zu Übersetzungsprojekten, Cloud-Konfigurationen und zum Translation Integration Framework finden Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](overview.md) und [Konfigurieren des Translation Integration Framework](integration-framework.md).

## So passt die KI-Übersetzung in AEM {#how-ai-translation-fits-in-aem}

Große Sprachmodelle können ganze Passagen übersetzen, wobei der Kontext, der Ton und die Idiome im Vordergrund stehen, anstatt Wort-für-Wort-Ersetzung. Wenn Sie die KI-Übersetzungsintegration konfigurieren, agiert der LLM als **Übersetzungsdienst eines Drittanbieters** auf dieselbe Weise wie andere Anbieter, mit denen Sie über AEM eine Verbindung herstellen. Sie geben Ihre **eigene Lizenz und Anmeldedaten** für den LLM-Service an.

Die anfängliche Unterstützung verbindet AEM mit **Azure OpenAI**. Adobe plant, in einer späteren Version die Unterstützung für weitere Anbieter hinzuzufügen.

Sie konfigurieren sowohl die LLM-Verbindung als auch optionale Stilhandbücher in **Übersetzungs-Cloud** Services zusammen mit Ihren anderen Übersetzungskonfigurationen. Sie können verschiedene Übersetzungs-Services für verschiedene [Cloud-Konfigurationen](/help/sites-cloud/administering/translation/integration-framework.md#creating-a-translation-integration-configuration) verwenden. Beispielsweise kann eine Konfiguration eine KI-Übersetzung verwenden, während eine andere einen herkömmlichen Connector für maschinelle Übersetzung verwendet.

## Konfigurieren von Übersetzungs-Cloud-Services {#configure-translation-cloud-services}

Richten Sie die KI-Übersetzung im selben Bereich ein, in dem Sie andere Übersetzungs-Cloud-Konfigurationen verwalten.

1. Wählen Sie im [globalen Navigationsmenü](/help/sites-cloud/authoring/basic-handling.md#global-navigation) die Option **Tools** > **Cloud Services** > **Übersetzungs-Cloud-Services**.
1. Öffnen oder erstellen Sie die Konfiguration, in der Sie die KI-Übersetzung aktivieren möchten (einschließlich der `/conf/global`, ob die Funktion allgemein gelten soll).

![Konsole der Übersetzungs-Cloud-Services , die anzeigt, wo Übersetzungskonfigurationen verwaltet werden.](assets/ai-translation-integration/aem_ai-translation_translation-cloud-services.png)

## Konfigurieren der LLM-Verbindung {#configure-the-llm-connection}

Die **Agentenübersetzungskonfiguration** enthält einen Abschnitt **LLM-Konfiguration** in dem Sie Ihren Anbieter verbinden.

1. Öffnen Sie die KI-Übersetzungskonfiguration für Ihren Eintrag Übersetzungs-Cloud-Services .
1. Wählen Sie **[!UICONTROL LLM Config]** aus.
1. Wählen Sie Ihren Anbieter aus (z. B. **Azure OpenAI**).
1. Geben Sie die erforderlichen Anmeldeinformationen und Endpunktdetails für Ihr Abonnement ein (**API-Schlüssel**, **API-Version**, **Basispfad**, **Bereitstellungsname** und alle anderen Felder, die Ihr Anbieter benötigt).
1. Speichern Sie die Konfiguration.

![Bildschirm für die Agentenübersetzungskonfiguration mit der Registerkarte „LLM-Konfiguration“ und den Feldern &quot;Azure OpenAI“.](assets/ai-translation-integration/aem_ai-translation_agentic-translation-llm-config.png)

## Hinzufügen von stilistischen Handbüchern und generierten Regeln für Übersetzungen {#add-translation-style-guides-and-generated-rules}

Sie können **Stil-Handbuch für Übersetzungen** Dokumente hochladen (in der Regel eines pro Zielsprache). AEM analysiert jeden Leitfaden und erstellt **Übersetzungsregeln** um die Ergebnisse an Ihre Marke und Ihre sprachlichen Erwartungen anzupassen.

1. Wählen **unter „Agentenmäßige**&quot; die Option **[!UICONTROL LLM-Richtlinien]** aus.
1. Wählen Sie ein Gebietsschema aus und verwenden **[!UICONTROL Hochladen]**, um ein Stilhandbuchdokument für diese Sprache hinzuzufügen.
1. Während AEM ein Handbuch verarbeitet, zeigt eine Statusanzeige den Fortschritt an (**Verarbeitung**, **abgeschlossen** oder **abgebrochen**).
1. Überprüfen oder bearbeiten Sie die generierten Regeln im Editor (z. B. JSON zur Erfassung von Ton, Terminologie und Beispielen).

![Registerkarte „LLM-Richtlinien“ mit der Liste der Gebietsschemata und den generierten Übersetzungsregeln für eine ausgewählte Sprache.](assets/ai-translation-integration/aem_ai-translation_agentic-translation-llm-guidelines.png)

## Festlegen der Standardübersetzungsmethode im Framework {#set-the-default-translation-method-in-the-framework}

Nachdem die Cloud-Konfiguration gespeichert wurde, registrieren Sie **agentische Übersetzung** als Standardverhalten in Ihrer Konfiguration [Translation Integration Framework](integration-framework.md), wenn Sie Übersetzungsprojekte erstellen. Sie können die Methode bei Bedarf pro Projekt ändern.

![Registerkarte Sites des Translation Integration Framework mit Optionen für Übersetzungsmethoden, einschließlich der agentischen Übersetzung.](assets/ai-translation-integration/aem_ai-translation_translation-integration-framework-default.png)

## Ausführen von Übersetzungsprojekten {#run-translation-projects}

Sobald die KI-Übersetzung konfiguriert und mit Ihren Seiten verknüpft ist, [&#x200B; Sie Übersetzungsprojekte auf &#x200B;](managing-projects.md) gleiche Weise wie bei anderen Übersetzungsdienstleistern erstellen und ausführen. Inhalte von Seiten, Inhaltsfragmenten und Assets entsprechen Ihren Übersetzungsregeln und Framework-Einstellungen.

>[!NOTE]
>
>Die KI-Übersetzungsintegration ist **nicht** über den [KI-Assistenten in der Chat](/help/implementing/cloud-manager/ai-assistant-in-aem.md)Benutzeroberfläche von Adobe Experience Manager oder über die Benutzeroberfläche des Experience Production Agent verfügbar. Verwenden Sie die in diesem Artikel beschriebenen Übersetzungs-Workflows und Konsolen.

