---
title: AEM Repo Tool
description: Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können.
exl-id: fb887ba3-e40b-4ab1-b142-0748c6d9f18e
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---

# AEM Repo Tool {#aem-repo-tool}

Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. Das AEM Repo Tool ähnelt dem [Jackrabbit FileVault-Maven-Plug-in](https://jackrabbit.apache.org/filevault-package-maven-plugin), ist aber schneller, hat minimale Abhängigkeiten und besteht aus einem einfachen Bash-Skript.

Dieses Tool vereinfacht die Dateiübertragung für Entwickelnde und lässt sich auch in Eclipse und IntelliJ integrieren, um die Entwicklung noch effizienter zu gestalten.

## Übersicht {#overview}

Das AEM Repo Tool erstellt für einen angegebenen Pfad in einer `jcr_root`-FileVault-Struktur im Dateisystem ein Paket mit einem einzigen Filter für den gesamten untergeordneten Baum und pusht dieses Paket zum Server (ähnlich wie `put` bei FTP), ruft es vom Server ab (`get`) oder vergleicht die Unterschiede (`status` und `diff`).

Mehrere Filterpfade werden vom Tool ebenso wenig unterstützt wie `filter.xml` von FileVault.

>[!CAUTION]
>
>Das AEM Repo Tool überschreibt immer die gesamte angegebene Datei oder das angegebene Verzeichnis.

## Download und Dokumentation {#download-and-documentation}

Das [AEM Repo Tool ist unter diesem Link auf GitHub verfügbar](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo), zusammen mit detaillierten Installations- und Nutzungsanleitungen.

Wenn Sie die Quelle des AEM Repo Tools herunterladen möchten, sehen Sie sich das unten verlinkte GitHub-Projekt an.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt „Tools“ auf GitHub.](https://github.com/Adobe-Marketing-Cloud/tools)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip) herunter.
