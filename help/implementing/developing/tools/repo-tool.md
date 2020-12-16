---
title: AEM Repo Tool
description: Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können.
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 51%

---


# AEM Repo Tool {#aem-repo-tool}

Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. Das AEM Repo-Tool ähnelt dem [Jackrabbit FileVault Maven-Plugin](https://jackrabbit.apache.org/filevault-package-maven-plugin), ist aber schneller, hat minimale Abhängigkeiten und ist ein einfaches Bash-Skript.

Dieses Tool vereinfacht die Übertragung von Dateien für den Entwickler und kann auch in Eclipse und IntelliJ integriert werden, um die Entwicklung noch effizienter zu machen.

## Überblick {#overview}

Für einen bestimmten Pfad innerhalb einer `jcr_root`-FileVault-Struktur auf dem Dateisystem erstellt das AEM Repo-Tool ein Paket mit einem einzigen Filter für die gesamte Substruktur und schiebt es auf den Server (ähnlich wie FTP `put`), ruft es vom Server ab ( `get`) oder vergleicht die Unterschiede ( `status` und `diff`).

Das Tool unterstützt nicht mehrere Filterpfade oder FileVault `filter.xml`.

>[!CAUTION]
>
>Beachten Sie, dass das AEM Repo Tool immer die gesamte angegebene Datei bzw. das gesamte angegebene Verzeichnis überschreibt.

## Download und Dokumentation {#download-and-documentation}

Das [AEM Repo Tool ist über diesen Link auf GitHub verfügbar, zusammen mit detaillierten Installations- und Gebrauchsanweisungen.](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo)

Wenn Sie den Quellcode des AEM Repo Tools herunterladen möchten, sehen Sie sich das unten verlinkte GitHub-Projekt an.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Open Tools-Projekt auf GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip) herunter.
