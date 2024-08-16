---
title: Universal Editor 2024.08.13 - Versionshinweise
description: Dies sind die Versionshinweise für die Version 2024.08.13 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: aad4d0353fb5e2eacb518b72e935def931d0798a
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# Universal Editor 2024.08.13 - Versionshinweise {#release-notes}

Dies sind die Versionshinweise für die Version des universellen Editors vom 13. August 2024.

>[!TIP]
>
>Die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service finden Sie auf [dieser Seite.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Neue Funktionen {#what-is-new}

* **Benutzerdefinierte Datentypen**: Ordnen Sie den Editor Ihren individuellen Datenanforderungen zu und erstellen Sie benutzerdefinierte Felder im Eigenschaftenbereich.
   * Unabhängig davon, ob Sie eine benutzerdefinierte Produktauswahl für Commerce-Anwendungsfälle entwickeln oder eine Dropdown-Liste mit Werten aus Ihren Backends ausfüllen, bietet diese Funktion Ihnen die nötige Kontrolle über die Daten, die Autoren zum Erstellen von Inhalten verwenden.
* **Container-übergreifendes Ziehen und Ablegen**: Nutzen Sie mehr Flexibilität bei der Layout-Komposition, indem Sie Komponenten per Drag &amp; Drop](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components) im Bereich [Inhaltsstruktur ](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) über verschiedene Container verschieben können.[
* **Optimierte GitHub-Integration**: Das Caching für GitHub-Antworten wurde eingeführt, was den Abruf von Tags und die `universal-editor-cors-library` erheblich beschleunigt und so zu einem schnelleren und reibungsloseren Benutzererlebnis führt.
* **Managed Services RPM Package**: Adobe bietet jetzt ein RPM-Paket, um die Bereitstellung und Verwaltung des Universal Editor Service zu optimieren, die Wartung zu vereinfachen und den Betriebsaufwand für verwaltete Dienste zu reduzieren.
* **Konfigurierbare Validierung des IMS-Tokens**: Um die Flexibilität bei der Tokenverwaltung zu erhöhen, ist die Validierung des IMS-Tokens jetzt optional.
   * Mit dieser Konfigurationsoption können Sie die Validierung nach Bedarf deaktivieren und so Ihre Cloud-Gateway-Setups vereinfachen.
* **Splunk-Integration**: Die Splunk-Protokollierung wurde in den [Universal Editor-Dienst für die lokale Entwicklung integriert und ](/help/implementing/universal-editor/local-dev.md) verbessert die Überwachung und Diagnose.
   * Diese Integration stellt eine effiziente Protokollverfolgung, reibungslosere Vorgänge und eine schnellere Fehlerbehebung sicher.

## Fehlerbehebungen {#bug-fixes}

* **Verbessertes Publishing-Feedback**: Wenn die Veröffentlichung aufgrund unzureichender Berechtigungen fehlschlägt, wurde das Feedback für den Benutzer während der Veröffentlichung verbessert, um eine klare Warnung anzuzeigen, anstatt einfach nur einen Fehler anzuzeigen.
* **Verbesserte URL-Handhabung**: Es wurden Probleme behoben, die bei falscher URL-Kodierung/-Dekodierung auftraten und Veröffentlichungsfehler verursachten.
* **Präzise Datenverarbeitung**: Ein Problem, bei dem Fließkommazahlen fälschlicherweise als Ganzzahlen gespeichert wurden, wurde behoben, um eine präzise Datenverarbeitung in Ihrem gesamten Inhalt sicherzustellen.
* **Sicherheit und Stabilität**: Sicherheitslücken in den Docker-Bildern wurden behoben und die Testabdeckung für kritische Komponenten wie den Komponenten-Picker und Breadcrumbs wurde implementiert, was zu einem sichereren, stabileren und zuverlässigeren Editor-Erlebnis führte.
