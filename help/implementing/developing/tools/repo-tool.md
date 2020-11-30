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

Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. The AEM Repo Tool is similar to the [Jackrabbit FileVault Maven plugin](https://jackrabbit.apache.org/filevault-package-maven-plugin), but is faster, has minimal dependencies, and is a simple bash script.

Dieses Tool vereinfacht die Übertragung von Dateien für den Entwickler und kann auch in Eclipse und IntelliJ integriert werden, um die Entwicklung noch effizienter zu machen.

## Überblick{#overview}

For a given path inside a `jcr_root` FileVault structure on the filesystem, the AEM Repo Tool creates a package with a single filter for the entire subtree and pushes that to the server (similar to FTP `put`), fetches it from the server ( `get`) or compares the differences ( `status` and `diff`).

The tool does not support multiple filter paths or FileVault&#39;s `filter.xml`.

>[!CAUTION]
>
>Beachten Sie, dass das AEM Repo Tool immer die gesamte angegebene Datei bzw. das gesamte angegebene Verzeichnis überschreibt.

## Download und Dokumentation {#download-and-documentation}

The [AEM Repo Tool is available on GitHub via this link](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) along with detailed installation and usage instructions.

Wenn Sie den Quellcode des AEM Repo Tools herunterladen möchten, sehen Sie sich das unten verlinkte GitHub-Projekt an.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Open Tools-Projekt auf GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip) herunter.
