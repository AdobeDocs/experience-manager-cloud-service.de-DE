---
title: So importieren Sie eine Markenrichtlinie
description: Verwenden des Adobe Governance-Agenten zum Importieren einer Markenrichtlinie
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 94d671ebbd5aeb5992fdbc9d779ffbca51f82585
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 0%

---


# So importieren Sie eine Markenrichtlinie {#how-to-import-a-brand-policy}

## Überblick {#overview}

Eine Markenrichtlinie definiert die Regeln, Standards und Einschränkungen, die sicherstellen, dass alle von Adobe Experience Manager erstellten oder aktualisierten Inhalte mit der Markenidentität eines Unternehmens konsistent bleiben. Dazu gehören in der Regel Tonfall, Terminologie, visuelle Richtlinien und redaktionelle Regeln.

Der Governance-Agent verwendet Markenrichtlinien als eine wahre Informationsquelle, um vorhandene Seiten zu analysieren und die Inhaltserstellung zu lenken. Kunden können ihre eigenen ursprünglichen Markenrichtlinien bereitstellen, die der Governance-Agent automatisch in KI-lesbare Richtlinienprüfungen konvertiert. Diese Prüfungen werden dann verwendet, um Inhalte zu validieren und dem Produktionsagenten ein zuverlässiges, durchsetzbares Framework zur Verfügung zu stellen, um Seiten zu generieren oder zu aktualisieren, die weiterhin mit der Marke ausgerichtet sind.

## Was ist eine Markenrichtlinie im Governance Agent? {#what-is-a-brand-policy-in-the-governance-agent}

Im Kontext des Governance-Agenten ist eine Markenrichtlinie eine strukturierte Darstellung Ihrer Markenregeln, die von KI verstanden und durchgesetzt werden kann. Der Governance Agent verlangt von den Kunden nicht, ihre Richtlinien in einem technischen Format umzuschreiben, sondern akzeptiert Markenrichtlinien in ihrer ursprünglichen Form (z. B. Dokumente, Richtlinien oder Regelbeschreibungen).

Nach dem Import wird die Richtlinie in eine Reihe von KI-Richtlinienprüfungen umgewandelt, die Folgendes können:

* Vorhandene Seiten analysieren, um Markeninkonsistenzen zu erkennen
* Markieren von Abweichungen von Ton, Terminologie oder obligatorischen Regeln
* Klare Leitlinien für nachgelagerte Agenten
* Sicherstellen, dass generierte oder aktualisierte Inhalte vom Design her markenkonform bleiben

Dieser Ansatz ermöglicht es Teams, ihre bestehende Markendokumentation wiederzuverwenden und gleichzeitig von automatisierter Governance und skalierbarer Inhaltserstellung zu profitieren.

## Wie Markenrichtlinien verwendet werden {#how-brand-policies-are-used}

Nachdem eine Markenrichtlinie importiert wurde:

* Der Governance-Agent interpretiert und normalisiert die Richtlinie in durchsetzbare KI-Prüfungen
* Seiten können anhand der Richtlinie analysiert werden, um Lücken oder Verstöße zu identifizieren
* Der Produktionsagent verwendet diese Prüfungen als Einschränkungen beim Generieren oder Aktualisieren von Inhalten
* Die Markenkonformität wird konsistent, wiederholbar und kann über Sites und Teams hinweg geprüft werden


## Importieren einer Markenrichtlinie {#import-a-brand-policy}

So importieren Sie eine Marke in den Governance Agent:

1. Erstellen Sie eine Marke, indem Sie einen Namen und eine Hauptdomäne angeben. Klicken Sie dazu auf die Schaltfläche **Governance-Kontext** im Navigationsbereich auf der linken Seite in Ihrer Experience Manager-Startseite und drücken Sie dann die Schaltfläche **+ Marke hinzufügen** wie unten dargestellt:

   ![Hinzufügen einer neuen Marke](/help/ai-in-aem/agents/governance/assets/add_brand.png){width="70%"}

1. Legen Sie den Namen der Marke und eine Beschreibung im folgenden Fenster fest

   ![Benennung der Marke](/help/ai-in-aem/agents/governance/assets/add_brand_dialogue.png){width="60%"}

1. Neue Marken werden im Status Entwurf erstellt. Stellen Sie sicher, dass Sie die neu erstellte Marke in den Status Aktiv ändern, indem Sie auf die Karte Ihrer Marke klicken, auf Bearbeiten (Stift) in der oberen rechten Ecke des Bildschirms klicken, den **Status** im folgenden Fenster auf **Aktiv** setzen und auf **Änderungen speichern** klicken. Sie müssen die Marken aktivieren, indem Sie sie auf Aktiv setzen, bevor Sie sie verwenden können.

   ![Setzen Sie den Markenstatus auf Aktiv](/help/ai-in-aem/agents/governance/assets/set_brand_active.png){width="60%"}

1. Nachdem die Marke erstellt wurde, erstellen Sie eine Haupt-Domain im folgenden Fenster, indem Sie auf den Link **Domains** auf der linken Seite klicken:

   ![Konfigurieren einer Domain für die Marke](/help/ai-in-aem/agents/governance/assets/add_domain.png)

   >[!IMPORTANT]
   >
   >Genau wie neue Marken werden neue Domains mit dem Standardstatus Entwurf erstellt. Um dies zu ändern, wechseln Sie zu Ihrer Marke, klicken Sie auf **Domänen** und bearbeiten Sie dann Ihre Domain mit dem Stiftsymbol und legen Sie den Status auf **Aktiv** fest.

1. Nachdem Sie die Haupt-Domain konfiguriert haben, können Sie Ihr Markenrichtliniendokument hochladen, indem Sie in der **oberen linken Ecke des Fensters zu** Richtlinien“ wechseln und die Schaltfläche **+ Richtlinie hinzufügen**.

   ![Hinzufügen einer Richtlinie über die Karte „Marke“](/help/ai-in-aem/agents/governance/assets/add_policy_treeview.png)

   >[!NOTE]
   >
   >Alternativ können Sie auch Richtlinien hinzufügen, indem Sie zur Registerkarte **Richtlinien“ wechseln** den Link **+ Richtlinie hinzufügen**.

1. Klicken Sie im nächsten Fenster auf **PDF hochladen** und wählen Sie Ihre Markenrichtliniendokumente im PDF-Format aus.

   ![Laden Sie Ihr Markenrichtliniendokument hoch](/help/ai-in-aem/agents/governance/assets/upload_brand_policy_document.png){width="70%"}

   Der Governance-Agent analysiert Ihre Richtlinien zur Markenrichtlinie in natürlicher Sprache und extrahiert die aus dem Dokument erhaltenen Prüfungen und übersetzt sie in tatsächliche Aufgaben. Sobald das Dokument verarbeitet ist, können Sie eine Zusammenfassung des Imports einschließlich der Anzahl der Prüfungen und des Status der Richtlinie anzeigen, wie unten dargestellt:

   ![Ein Übersichtsfenster über den Status der Markenrichtlinie](/help/ai-in-aem/agents/governance/assets/policy_status.png)

1. Sobald Ihre Marke erstellt und Ihr Richtliniendokument hochgeladen wurde, können Sie eine detaillierte Ansicht pro Marke erhalten, indem Sie zur Registerkarte **Marken** wechseln und auf die Karte einer Marke klicken. Diese Ansicht können Sie zum Erstellen von Scheckkategorien verwenden, indem Sie auf die drei Punkte neben einer vorhandenen Kategorie klicken und **+ Kategorie hinzufügen** auswählen, wie im folgenden Screenshot gezeigt:

   ![Kategorie hinzufügen](/help/ai-in-aem/agents/governance/assets/add_category.png)

   Sie können diese Ansicht auch zum Erstellen, Bearbeiten und Löschen von Prüfungen verwenden, die in den folgenden Schritten beschrieben werden.

1. Um eine detailliertere Ansicht der einzelnen Prüfungen zu erhalten, können Sie zur Registerkarte **Prüfungen** wechseln und eine Liste jeder einzelnen Prüfung anzeigen, die aus Ihren Richtliniendokumenten extrahiert wurde. Sie können Prüfungen nach Marke oder Status filtern:

   ![Siehe individuelle Markenprüfungen](/help/ai-in-aem/agents/governance/assets/see_brand_checks.png)

   Darüber hinaus können Sie zusätzliche Details zu jeder einzelnen Prüfung anzeigen, indem Sie auf die drei Punkte (**…**) links neben der Prüfung klicken und **Details anzeigen**. Dadurch wird ein neues Fenster mit weiteren Informationen zur Prüfung geöffnet:

   ![Anzeigen der Details einzelner Prüfungen](/help/ai-in-aem/agents/governance/assets/view_check_details.png)

   Sie können Prüfungen auch löschen, indem Sie am selben Menüpunkt **Löschen** drücken oder durch Drücken von **Bearbeiten** bearbeiten:

   ![Bearbeiten einer Prüfung](/help/ai-in-aem/agents/governance/assets/edit_check.png)

1. Sie können eine Prüfung manuell hinzufügen, indem Sie **Prüfung hinzufügen** in der oberen linken Ecke des Fensters Prüfungen drücken:

   ![Hinzufügen einer Prüfung](/help/ai-in-aem/agents/governance/assets/add_check.png)

   Im folgenden Bildschirm können Sie Details konfigurieren, wie etwa:

   * Der Name der Prüfung
   * Die Regel, in natürlicher Sprache beschrieben
   * Die Kategorie
   * Die Bereiche, für die sie gilt

   ![Konfigurieren der Prüfungsdetails](/help/ai-in-aem/agents/governance/assets/add_check_window.png)

1. Um eine Liste der Domains und der Marken zu erhalten, mit denen sie verknüpft sind, klicken Sie auf die Registerkarte **Domains**. In diesem Abschnitt können Sie Domains in Ihrer Liste hinzufügen, löschen oder ändern.

