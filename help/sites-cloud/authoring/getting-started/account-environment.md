---
title: Konfigurieren der Kontoumgebung
description: AEM bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren
exl-id: 1b948f0b-85b9-478a-8b7e-61495c1d57b6
source-git-commit: 47910a27118a11a8add6cbcba6a614c6314ffe2a
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 79%

---

# Konfigurieren der Kontoumgebung {#configuring-your-account-environment}

AEM bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren.

Mit der Option [Benutzer](#user-settings) in der [Kopfzeile](/help/sites-cloud/authoring/getting-started/basic-handling.md#the-header) und dem verbundenen Dialogfeld [Benutzereinstellungen](#my-preferences) können Sie Benutzeroptionen bearbeiten.

Beginnen Sie, indem Sie in der Kopfzeile die Option [Benutzer](#user-settings) aufrufen.

## Benutzereinstellungen {#user-settings}

Die **Benutzer** Über das Dialogfeld &quot;Einstellungen&quot;haben Sie Zugriff auf:

* Identität annehmen als
   * Mit der Funktion „Identität annehmen als“ kann ein Benutzer im Namen eines anderen Benutzers arbeiten. <!--With the [Impersonate as](/help/sites-administering/security.md#impersonating-another-user) functionality, a user can work on behalf of another user.-->
* Profil
   * Über das Profil können Sie bequem über einen Link auf Ihre Benutzereinstellungen zugreifen. <!--Offers a convenient link to your [user settings](/help/sites-administering/security.md))-->
* [Benutzereinstellungen](#my-preferences)
   * Hier können verschiedene auf den jeweiligen Benutzer zugeschnittene Einstellungen festgelegt werden.

![Benutzereinstellungen](/help/sites-cloud/authoring/assets/user-settings.png)

### Benutzereinstellungen {#my-preferences}

Auf das Dialogfeld **Benutzereinstellungen** kann über die Option [Benutzer](#user-settings) in der Kopfzeile zugegriffen werden.

Jeder Benutzer kann bestimmte Eigenschaften für sich selbst festlegen.

![Benutzereinstellungen](/help/sites-cloud/authoring/assets/user-preferences.png)

* **Sprache**

   Dadurch wird die Sprache definiert, die für die Benutzeroberfläche der Authoring-Umgebung verwendet werden soll. Wählen Sie in der Liste die gewünschte Sprache aus.

* **Fensterverwaltung**

   Dies definiert das Verhalten oder das Öffnen von Fenstern. Wählen Sie eine der folgenden beiden Optionen aus:

   * **Mehrere Fenster** (Standard)

      * Seiten werden in einem neuen Fenster geöffnet.
   * **Einfaches Fenster**

      * Seiten werden im aktuellen Fenster geöffnet.


* **Desktop-Aktionen für Assets anzeigen**

   Für diese Option ist das AEM-Desktop-Programm erforderlich.

* **Anmerkungsfarbe**

   Dadurch wird die Standardfarbe definiert, die beim Erstellen von Anmerkungen verwendet wird.

   * Klicken Sie auf den Farbblock, um die Musterauswahl zu öffnen und eine Farbe auszuwählen.
   * Alternativ dazu können Sie in das Feld den Hexcode für die gewünschte Farbe eingeben.

* **Darstellung des relativen Datums**

   Zur besseren Lesbarkeit rendert AEM Daten der letzten sieben Tage als relative Datumsangaben (z. B. „vor drei Tagen“) und ältere Daten als genaue Datumsangaben (z. B. 20. März 2017).

   Diese Option definiert, wie Daten im System angezeigt werden. Die folgenden Optionen sind verfügbar:

   * **Immer exaktes Datum anzeigen**: Es wird immer das genaue Datum angezeigt (niemals ein relatives Datum).
   * **1 Tag**: Das relative Datum wird für Datumsangaben innerhalb eines Tages angezeigt; ansonsten wird das genaue Datum angegeben.
   * **7 Tage (Standard)**: Das relative Datum wird für Datumsangaben innerhalb eines Zeitraums von sieben Tages angezeigt; ansonsten wird das genaue Datum angegeben.
   * **1 Monat**: Das relative Datum wird für Datumsangaben innerhalb eines Monats angezeigt; ansonsten wird das genaue Datum angegeben.
   * **1 Jahr**: Das relative Datum wird für Datumsangaben innerhalb eines Jahres angezeigt; ansonsten wird das genaue Datum angegeben.
   * **Immer relatives Datum anzeigen**: Es werden niemals genaue Datumsangaben, sondern nur relative Daten angezeigt.

* **Tastaturbefehle aktivieren**

   AEM unterstützt verschiedene Tastaturbefehle, die eine effizientere Bearbeitung ermöglichen.

   * [Tastaturbefehle für die Seitenbearbeitung](/help/sites-cloud/authoring/fundamentals/keyboard-shortcuts.md)
   * [Tastaturbefehle für Konsolen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md)

   Diese Option aktiviert Tastaturbefehle. Sie sind standardmäßig aktiviert, können aber deaktiviert werden, z. B. wenn ein Benutzer bestimmte Barrierefreiheitsanforderungen hat.

* **Asset-Homepage aktivieren**

   Diese Option ist nur verfügbar, wenn der Systemadministrator die Asset-Homepage-Nutzung für das gesamte Unternehmen aktiviert hat.

* **Stock-Konfiguration**

   Mit dieser Option können Sie die bevorzugte Adobe Stock-Konfiguration angeben. Sie ist nur verfügbar, wenn Ihr Systemadministrator die [Adobe Stock-Integration](/help/assets/aem-assets-adobe-stock.md) aktiviert hat.
