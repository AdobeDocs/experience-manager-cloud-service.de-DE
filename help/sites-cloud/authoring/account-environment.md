---
title: Konfigurieren der Kontoumgebung
description: Adobe Experience Manager (AEM) bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 1b948f0b-85b9-478a-8b7e-61495c1d57b6
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 99%

---

# Konfigurieren der Kontoumgebung {#configuring-your-account-environment}

Adobe Experience Manager (AEM) bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren

Mit der Option [Benutzer](#user-settings) in der [Kopfzeile](/help/sites-cloud/authoring/basic-handling.md#the-header) und dem verbundenen Dialogfeld [Benutzereinstellungen](#my-preferences) können Sie Benutzeroptionen bearbeiten.

Beginnen Sie, indem Sie in der Kopfzeile die Option [Benutzer](#user-settings) aufrufen.

## Benutzereinstellungen {#user-settings}

Im Dialogfeld **Benutzereinstellungen** können Sie auf Folgendes zugreifen:

* Identität annehmen als
   * Mit der Funktion „Identität annehmen als“ kann ein Benutzer im Namen eines anderen Benutzers arbeiten. <!--With the [Impersonate as](/help/sites-administering/security.md#impersonating-another-user) functionality, a user can work on behalf of another user.-->
* Profil
   * Über das Profil können Sie bequem über einen Link auf Ihre Benutzereinstellungen zugreifen. <!--Offers a convenient link to your [user settings](/help/sites-administering/security.md))-->
* [Benutzereinstellungen](#my-preferences)
   * Hier können verschiedene auf den jeweiligen Benutzer zugeschnittene Einstellungen festgelegt werden.

![Benutzereinstellungen](/help/sites-cloud/authoring/assets/user-settings.png)

### Benutzereinstellungen {#my-preferences}

Auf das Dialogfeld **Benutzereinstellungen** kann über die Option [Benutzer](#user-settings) in der Kopfzeile zugegriffen werden.

Jede Benutzerin und jeder Benutzer kann eigene, bevorzugte Eigenschaften festlegen.

![Benutzereinstellungen](/help/sites-cloud/authoring/assets/user-preferences.png)

* **Sprache**

  Dadurch wird die Sprache definiert, die für die Benutzeroberfläche der Autorenumgebung verwendet werden soll. Wählen Sie die gewünschte Sprache aus der verfügbaren Liste aus.

* **Fensterverwaltung**

  Dies definiert das Verhalten oder das Öffnen von Fenstern. Wählen Sie eine der folgenden beiden Optionen aus:

   * **Mehrere Fenster** (Standard)

      * Seiten werden in einem neuen Fenster geöffnet.

   * **Einfaches Fenster**

      * Seiten werden im aktuellen Fenster geöffnet.

* **Desktop-Aktionen für Assets anzeigen**

  Für diese Option ist die AEM-Desktop-App erforderlich.

* **Anmerkungsfarbe**

  Dadurch wird die Standardfarbe definiert, die beim Erstellen von Anmerkungen verwendet wird.

   * Klicken Sie auf den Farbblock, damit Sie die Musterauswahl öffnen und eine Farbe auswählen können.
   * Alternativ dazu können Sie in das Feld den Hexcode für die gewünschte Farbe eingeben.

* **Darstellung des relativen Datums**

  Zur besseren Lesbarkeit rendert AEM Daten der letzten sieben Tage als relative Datumsangaben (z. B. „Vor drei Tagen“) und ältere Daten als genaue Datumsangaben (z. B. 20. März 2017).

  Diese Option definiert, wie Daten im System angezeigt werden. Die folgenden Optionen sind verfügbar:

   * **Immer exaktes Datum anzeigen**: Es wird immer das genaue Datum angezeigt (niemals ein relatives Datum).
   * **1 Tag**: Das relative Datum wird für Datumsangaben innerhalb eines Tages angezeigt; ansonsten wird das genaue Datum angegeben.
   * **7 Tage (Standard)**: Das relative Datum wird für Datumsangaben innerhalb eines Zeitraums von sieben Tages angezeigt; ansonsten wird das genaue Datum angegeben.
   * **1 Monat**: Das relative Datum wird für Datumsangaben innerhalb eines Monats angezeigt; ansonsten wird das genaue Datum angegeben.
   * **1 Jahr**: Das relative Datum wird für Datumsangaben innerhalb eines Jahres angezeigt; ansonsten wird das genaue Datum angegeben.
   * **Immer relatives Datum anzeigen**: Es werden niemals genaue Datumsangaben, sondern nur relative Daten angezeigt.

* **Tastaturbefehle aktivieren**

  AEM unterstützt verschiedene Tastaturbefehle, die eine noch effizientere Bearbeitung ermöglichen.

   * [Tastaturbefehle für die Seitenbearbeitung](/help/sites-cloud/authoring/page-editor/keyboard-shortcuts.md)
   * [Tastaturbefehle für Konsolen](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md)

  Diese Option aktiviert Tastaturbefehle. Sie sind standardmäßig aktiviert, können aber deaktiviert werden, wenn z. B. Benutzende bestimmte Barrierefreiheitsanforderungen haben.

* **Asset-Homepage aktivieren**

  Diese Option ist nur verfügbar, wenn Systemadmins die Asset-Homepage-Nutzung für das gesamte Unternehmen aktiviert haben.

* **Stock-Konfiguration**

  Mit dieser Option können Sie die bevorzugte Adobe Stock-Konfiguration angeben. Sie ist nur verfügbar, wenn Ihre Systemadmins die [Adobe Stock-Integration](/help/assets/aem-assets-adobe-stock.md) aktiviert haben.
