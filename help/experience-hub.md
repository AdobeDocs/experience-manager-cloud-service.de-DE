---
title: Info zu Experience Hub
description: Erfahren Sie mehr über die Adobe Experience Hub-Seite.
landing-page-description: Erfahren Sie mehr über Experience Hub, eine zentrale Anlaufstelle für den Zugriff auf alle Funktionen von AEM.
solution: Experience Manager
feature: Authoring, AI Assistant, Central Interface Components, Getting Started, Onboarding, Programs, Workflows
feature-set: Experience Cloud,Experience Manager Sites,Experience Cloud Services
role: Admin, Developer, User
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: a1b0eed7-b74c-4e72-8399-c473bbda9245
source-git-commit: e31b3f6a249d6b0a5836f42b5cf8725e1339b117
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 65%

---

# Info zu Experience Hub {#aem-experience-hub}

Experience Hub dient als zentraler Ausgangspunkt für die Verwaltung von Content, Assets und Websites in Adobe Experience Manager. Experience Hub wurde für ein personalisiertes Erlebnis konzipiert und ermöglicht Ihnen die nahtlose Navigation im AEM-Ökosystem entsprechend Ihren Rollen und Zielen. Es bietet wichtige Einblicke und empfohlene Aktionen, mit denen Sie Ihre Ziele effizient erreichen können. Mit einem klaren, rollenbasierten Layout gewährleistet Experience Hub schnellen Zugriff auf wichtige Tools und ermöglicht so ein optimiertes und effektives Erlebnis für alle AEM-Funktionen.

Siehe auch [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

Überblick über den AEM Experience Hub-Arbeitsbereich (2 Minuten, 40 Sekunden)

>[!VIDEO](https://video.tv.adobe.com/v/3475190/?learn=on&enablevpops)

<!--
Available as a private beta, Experience Hub offers an optimized experience focused on improving workflows, prioritizing goals, and delivering results. Opting in lets you influence Experience Hub's development by providing feedback that helps shape its future and enhances its value for the entire AEM community.
-->

## Übersicht über Experience Hub {#aem-experience-hub-about}

1. Klicken Sie zunächst auf [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home), um die Startseite zu öffnen.

   ![Startseite von Adobe Experience Cloud](/help/implementing/cloud-manager/assets/experience-cloud-experiencemanager.png)

1. Klicken Sie in der Gruppierung **Schnellzugriff** auf [**Experience Manager**](https://experience.adobe.com).
1. Beim ersten Zugriff weist das System Ihnen die Voreinstellung **Inhaltsautor/in** zu (sichtbar in der oberen rechten Ecke der Seite). Sie steuert die Widgets, Navigationselemente und Inhalte, die Sie sehen.

   Sie können diese Voreinstellung jederzeit ändern.

   ![Die Dropdown-Liste mit der Inhaltsautorenvorgabe ist ausgewählt](/help/implementing/cloud-manager/assets/experience-hub-role-selection.png)

Die Adobe Experience Manager-Seite wurde mit verbesserter Navigation und interaktiven Widgets überarbeitet. Die vorherige Sammlung von Lösungskarten bot Zugriff auf Tools wie die folgenden:

* Universeller Editor
* Cloud Manager
* Cloud Acceleration Manager
* Software Distribution
* Adobe Extension Manager
* Brand Portal

>[!IMPORTANT]
>
>Die angezeigten Widgets, Tools und Artefakte hängen von der Benutzerrolle, den Berechtigungen und dem AEM-Bereitstellungstyp (AEM as a Cloud Service oder Managed Services 6.5/6.5 LTS) ab.

Diese Lösungen wurden jetzt in die Hauptnavigation unter &quot;**&quot;** &quot;**&quot;**. Neue Navigationselemente bieten schnellen Zugriff auf AEM-Funktionen, die mit Ihren aktivierten Lösungen verknüpft sind. Zu Assets, Sites, Forms, Inhaltsfragmenten, Launches und mehr springen.

![Experience Hub-Umgebungen](/help/implementing/cloud-manager/assets/experience-hub-author-environments.png)

Verwenden Sie diese Funktionen in Ihrer primären Produktionsumgebung. Wenn Sie Zugriff auf mehrere AEM-Instanzen haben, wählen Sie die Umgebung aus, die Sie ansprechen möchten.

![Produktions- und Staging-Umgebungen](/help/implementing/cloud-manager/assets/experience-hub-prod-stage.png)

Die Experience Hub-Seite, die als zentraler Hub für Adobe Experience Manager dient, wird erweitert und enthält zusätzliche Widgets und Aktionen, die auf jede Benutzerrolle (Voreinstellung) zugeschnitten sind. Die Seite ist vollständig anpassbar und ermöglicht so die Auswahl des optimalen Layouts für Ihren Bildschirm. Widgets können so gefiltert werden, dass nur ausgewählte Widgets auf der Hauptseite angezeigt werden. Das sorgt für ein personalisiertes Erlebnis.

![Experience Hub angepasst](/help/implementing/cloud-manager/assets/experience-hub-custom.png)

Widgets können auch in der Größe angepasst und auf der Seite neu positioniert werden, um Ihren Anforderungen und Voreinstellungen gerecht zu werden.

![Experience Hub-Widgets](/help/implementing/cloud-manager/assets/experience-hub-widgets.png)

Im **Authoring-**&quot; werden alle AEM-Umgebungen aufgelistet, auf die Sie zugreifen können, sowie Verknüpfungen zu ihren Lösungen und Seiten. Um bestimmte Umgebungen an der Spitze der Liste zu halten, heften Sie sie an.

Im Abschnitt **Zuletzt verwendet** (siehe Abbildung unten) werden die Seiten aufgelistet, die Sie kürzlich in AEM besucht haben. Je nach Lizenzierung Ihres Mandanten enthält das Widget Elemente wie Programm, Pipeline-Ausführung und verschiedene Editoren.

**Schnellverknüpfungen** in der Nähe der oberen linken Ecke der Seite bieten eine konfigurierbare Liste von Tastaturbefehlen, mit denen Sie tägliche Aufgaben starten können. Die Liste kann angepasst werden. Zudem zielt jede Aktion auf die ausgewählte AEM-Umgebung ab.

![Authoring-Umgebungen](/help/implementing/cloud-manager/assets/experience-hub-recents.png)

![Experience Hub-Schnellverknüpfungen](/help/implementing/cloud-manager/assets/experience-hub-quick-shortcuts.png)

Wenn keine AEM Cloud Service- oder Managed Services-Produktionsumgebungen vorhanden sind, erscheinen die Auswahloptionen abgeblendet und nicht verfügbar.

![Experience Hub-Umgebungen, die nicht in der Produktion sind](/help/implementing/cloud-manager/assets/experience-hub-no-prod-environs.png)

## Häufig gestellte Fragen (FAQ) {#faq}

+++**Wie konfiguriere ich kundenseitig verwaltete Schlüssel von Experience Hub?**

Wenn CMK für Ihr Programm aktiviert ist, stellt Experience Hub einen direkten Link zur CMK-Konfigurationsseite bereit. Wählen Sie **CMK konfigurieren** aus Ihrer Programmkarte oder aus den Schnellbefehlen aus. Die vollständigen Konfigurationsschritte finden Sie unter [Einrichten kundenverwalteter Schlüssel für AEM as a Cloud Service](/help/security/customer-managed-keys.md).

+++

+++**Was ist der Hauptzweck von Adobe Experience Hub in Adobe Experience Manager?**

Adobe Experience Hub dient als zentraler Ausgangspunkt für die Verwaltung von Content, Assets und Websites in Adobe Experience Manager und bietet ein personalisiertes Erlebnis, das auf Benutzerrollen und Zielen basiert.

+++

+++**Wie passt sich Experience Hub an verschiedene Benutzerrollen an?**

Experience Hub zeigt rollenbasierte Ansichten und Schnellaktionen für Autoren, Asset-Bibliothekare, Administratoren und IT-Personal. Jede Rolle erhält raschen Zugriff auf die benötigten Tools und Funktionen.

+++

+++**Welche Funktionen bieten Navigation und Layout von Experience Hub?**

Experience Hub nutzt einen einheitlichen linken Navigationsbereich, um Kernfunktionen von AEM, anpassbare Widgets und Schnellaktionen zu organisieren. Durch dieses Layout entsteht ein organisierter, effizienter Arbeitsbereich.

+++

+++**Wie können Benutzende ihren Experience Hub-Arbeitsbereich personalisieren?**

Benutzende können Widgets hinzufügen, entfernen, neu anordnen und ihre Größe ändern sowie Schnellaktionen anpassen, um den Arbeitsbereich an ihre Bedürfnisse und Präferenzen anzupassen.

+++

+++**Welche Aktionstypen können mit Experience Hub schnell ausgeführt werden?**

Experience Hub bietet für gängige Aufgaben Tastaturbefehle mit einem Klick, die auf die Rolle des Benutzers zugeschnitten sind.

+++

+++**Wie erleichtert Experience Hub die Navigation zu verschiedenen AEM-Funktionen?**

Die Hauptnavigation von Experience Hub unter **Tools** oder **Services** bietet schnellen Zugriff auf AEM-Funktionen wie Assets, Sites, Forms, Inhaltsfragmente und Launches.

+++

+++**Welche Rolle spielen Widgets in Experience Hub?**

Widgets in Experience Hub sind anpassbare Elemente, die Benutzenden helfen, ihre Arbeit effizient zu verwalten (z. B. Tracking kürzlicher Aktivitäten und aktuelle Informationen über Produktaktualisierungen).

+++

+++**Wie können Benutzende mithilfe von Experience Hub verschiedene AEM-Umgebungen verwalten?**

Benutzende können die Umgebung auswählen, die als Ziel verwendet werden soll, und Favoriten anheften, um sie an der Spitze zu halten. Tastaturbefehle öffnen Lösungen und Seiten innerhalb dieser Umgebungen.

+++

+++**Welche Rolle spielt der KI-Assistent in AEM?**

Der KI-Assistent in AEM steht Benutzenden zur Verfügung, die bestimmte Kriterien erfüllen, und bietet zusätzliche Unterstützung und Erkenntnisse innerhalb des Unternehmens.

+++

+++**Was passiert, wenn es keine AEM Cloud Service- oder Managed Services-Umgebungen in der Produktion gibt?**

Wenn es keine Produktionsumgebungen gibt, erscheinen die Auswahloptionen in Experience Hub abgeblendet und sind nicht verfügbar.

+++

## KI-Assistent in AEM

Für Kunden, die [vorausgesetzte Kriterien erfüllt haben](/help/implementing/cloud-manager/ai-assistant-in-aem.md#get-access) steht der KI-Assistent in AEM den Benutzenden ihres Unternehmens zur Verfügung. Siehe [KI-Assistent in AEM](/help/implementing/cloud-manager/ai-assistant-in-aem.md).
