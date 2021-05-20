---
title: Konfigurieren der Kontoumgebung
description: AEM bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren
exl-id: 1b948f0b-85b9-478a-8b7e-61495c1d57b6
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 100%

---

# Konfigurieren der Kontoumgebung  {#configuring-your-account-environment}

AEM bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren.

Mit der Option [Benutzer](#user-settings) in der [Kopfzeile](/help/sites-cloud/authoring/getting-started/basic-handling.md#the-header) und dem verbundenen Dialogfeld [Benutzereinstellungen](#my-preferences) können Sie Benutzeroptionen bearbeiten.

Beginnen Sie, indem Sie in der Kopfzeile die Option [Benutzer](#user-settings) aufrufen.

## Benutzereinstellungen {#user-settings}

Im Dialogfeld **Benutzereinstellungen** haben Sie Zugriff auf folgende Optionen:

* Identität annehmen als
   * Mit der Funktion „Identität annehmen als“ kann ein Benutzer im Namen eines anderen Benutzers arbeiten. <!--With the [Impersonate as](/help/sites-administering/security.md#impersonating-another-user) functionality, a user can work on behalf of another user.-->
* Profil
   * Über das Profil können Sie bequem über einen Link auf Ihre Benutzereinstellungen zugreifen. <!--Offers a convenient link to your [user settings](/help/sites-administering/security.md))-->
* [Benutzereinstellungen](#my-preferences)
   * Hier können verschiedene auf den jeweiligen Benutzer zugeschnittene Einstellungen festgelegt werden.

![Benutzereinstellungen](/help/sites-cloud/authoring/assets/user-settings.png)

### Benutzereinstellungen{#my-preferences}

Auf das Dialogfeld **Benutzereinstellungen** kann über die Option [Benutzer](#user-settings) in der Kopfzeile zugegriffen werden.

Jeder Benutzer kann bestimmte Eigenschaften für sich selbst festlegen.

![Benutzereinstellungen](/help/sites-cloud/authoring/assets/user-preferences.png)

* **Sprache**

   Hiermit wird die Sprache definiert, in der die Benutzeroberfläche der Autorenumgebung angezeigt werden soll. Wählen Sie die gewünschte Sprache aus der Liste der verfügbaren Sprachen aus.

* **Fensterverwaltung**

   Hiermit wird das Verhalten oder das Öffnen von Fenstern definiert. Wählen Sie eine der folgenden beiden Optionen aus:

   * **Mehrere Fenster** (Standard)

      * Seiten werden in einem neuen Fenster geöffnet.
   * **Einfaches Fenster**

      * Seiten werden im aktuellen Fenster geöffnet.


* **Desktop-Aktionen für Assets anzeigen**

   Für diese Option ist das AEM-Desktop-Programm erforderlich.

* **Anmerkungsfarbe**

   Hiermit wird die Standardfarbe für Anmerkungen definiert.

   * Klicken Sie auf den Farbblock, um die Musterauswahl zur Festlegung einer Farbe zu öffnen.
   * Alternativ dazu können Sie in das Feld den Hexcode für die gewünschte Farbe eingeben.

* **Darstellung des relativen Datums**

   Zur besseren Lesbarkeit rendert AEM Daten der letzten sieben Tage als relative Daten (z. B. „vor drei Tagen“) und ältere Daten als genaue Datumsangaben (z. B. 20. März 2017).

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

   Diese Option aktiviert Tastaturbefehle. Diese sind zwar standardmäßig aktiviert, können aber deaktiviert werden, etwa wenn für einen Benutzer bestimmte Anforderungen in Bezug auf die Barrierefreiheit bestehen.

* **Asset-Homepage aktivieren**

   Diese Option ist nur verfügbar, wenn der Systemadministrator die Asset-Homepage-Nutzung für das gesamte Unternehmen aktiviert hat.

* **Stock-Konfiguration**

   Mit dieser Option können Sie die bevorzugte Adobe Stock-Konfiguration angeben. Sie ist nur verfügbar, wenn Ihr Systemadministrator die [Adobe Stock-Integration](/help/assets/aem-assets-adobe-stock.md) aktiviert hat.
