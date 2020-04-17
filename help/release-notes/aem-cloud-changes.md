---
title: Wesentliche Änderungen an Adobe Experience Manager (AEM) as a Cloud Service
description: Wesentliche Änderungen an Adobe Experience Manager (AEM) as a Cloud Service
translation-type: ht
source-git-commit: e76de9b84931dced6383570e384ffdb6fb334daf

---


# Wesentliche Änderungen an Adobe Experience Manager (AEM) as a Cloud Service {#notable-changes-aem-cloud}

AEM Cloud Service bietet viele neue Funktionen und Möglichkeiten zur Verwaltung Ihrer AEM-Projekte. Es gibt jedoch eine Reihe von Unterschieden zwischen AEM Sites On-Premise oder in Adobe Managed Services im Vergleich zu AEM Cloud Service. In diesem Dokument wird auf die wichtigsten Unterschiede eingegangen.

>[!NOTE]
>In diesem Dokument werden die wesentlichen Änderungen an AEM als Ganzes hervorgehoben. Lösungsspezifische Änderungen finden Sie hier:
>
>* [Wesentliche Änderungen an AEM Sites in AEM Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Westentliche Änderungen an AEM Assets in AEM Cloud Service](/help/assets/assets-cloud-changes.md)


Die wichtigsten Unterschiede sind in folgenden Bereichen festzustellen:

* [/apps und /libs sind zur Laufzeit unveränderlich](#apps-libs-immutable)
* [OSGi-Pakete und -Einstellungen müssen Repository-basiert sein](#osgi)
* [Änderungen am Publishing-Repository sind nicht zulässig](#changes-to-publish-repo)
* [Benutzerdefinierte Ausführungsmodi sind nicht zulässig](#custom-runmodes)
* [Entfernung von Replikations-Agenten](#replication-agents)
* [Entfernung der klassischen Benutzeroberfläche](#classic-ui)
* [Bereitstellung auf Publishing-Seite](#publish-side-delivery)
* [Asset-Handhabung und -Bereitstellung](#asset-handling)

## /apps und /libs sind zur Laufzeit unveränderlich {#apps-libs-immutable}

Alle Inhalte und Unterordner in `/apps` und `/libs` sind schreibgeschützt. Funktionen oder benutzerdefinierter Code, die dort Änderungen vornehmen sollen, werden fehlschlagen. Es wird ein Fehler zurückgegeben, der besagt, dass diese Inhalte schreibgeschützt sind und der Schreibvorgang nicht abgeschlossen werden konnte. Dies wirkt sich auf eine Reihe von Bereichen von AEM aus:

* Änderungen in `/libs` sind überhaupt nicht zulässig.
   * Dies ist keine neue Regel, wurde jedoch in früheren On-Premise-Versionen von AEM nicht erzwungen.
* Überlagerungen für Bereiche in `/libs`, die überlagert werden dürfen, sind innerhalb von `/apps` weiterhin zulässig.
   * Solche Überlagerungen müssen über die CI/CD-Pipeline von Git stammen.
* Design-Informationen für statische Vorlagen, die in `/apps` gespeichert sind, können nicht über die Benutzeroberfläche bearbeitet werden.
   * Es wird empfohlen, stattdessen bearbeitbare Vorlagen zu verwenden.
   * Sind weiterhin statische Vorlagen erforderlich, müssen die Konfigurationsinformationen über die CI/CD-Pipeline von Git stammen.
* MSM-Blueprint und benutzerdefinierte MSM-Roll-out Konfigurationen müssen von Git über die CI/CD-Pipeline installiert werden.
* Änderungen an der I18n-Übersetzung müssen von Git über die CI/CD-Pipeline vorgenommen werden.

## OSGi-Pakete und -Einstellungen müssen Repository-basiert sein {#osgi}

Die Web-Konsole, die in früheren Versionen von AEM zum Ändern der OSGi-Einstellungen verwendet wird, ist in AEM Cloud Service nicht verfügbar. Daher müssen Änderungen an OSGi über die CI/CD-Pipeline vorgenommen werden.

* Änderungen an OSGi-Einstellungen können nur über Git-Persistenz als JCR-basierte OSGi-Einstellungen vorgenommen werden.
* Neue oder aktualisierte OSGi-Pakete müssen über Git als Teil des CI/CD-Pipeline-Build-Prozesses eingeführt werden.

## Änderungen am Publishing-Repository sind nicht zulässig {#changes-to-publish-repo}

Direkte Änderungen am Publishing-Repository sind in AEM Cloud Service nicht zulässig. In früheren Versionen von AEM On-Premise oder AEM in AMS können Code-Änderungen direkt am Publishing-Repository vorgenommen werden, um beispielsweise Benutzer zu erstellen, das Benutzerprofil zu aktualisieren und Knoten zu erstellen. Dies ist nicht mehr möglich und kann wie folgt gehandhabt werden:

* Für Inhalts- und inhaltsbasierte Konfiguration: Nehmen Sie die Änderungen an der Autoreninstanz vor und veröffentlichen Sie diese.
* Für Code und Konfiguration: Nehmen Sie die Änderungen im GIT-Repository vor und führen Sie die CI/CD-Pipeline aus, um sie einzuführen.
* Für benutzerbezogene Daten, z. B. Formularübermittlungen oder Profildaten: Verwenden Sie den Unified Profile Service aus Experience Cloud Platform oder einen anderen sitzungsbasierten Speicher eines Drittanbieters.

## Benutzerdefinierte Ausführungsmodi sind nicht zulässig {#custom-runmodes}

Für AEM Cloud Service stehen die folgenden Ausführungsmodi standardmäßig zur Verfügung:

* `author`
* `publish`
* `prod`
* `author.prod`
* `publish.prod`
* `stage`
* `author.stage`
* `publish.stage`
* `dev`
* `author.dev`
* `publish.dev`

Zusätzliche oder benutzerdefinierte Ausführungsmodi sind in AEM Cloud Service nicht möglich.

## Entfernung von Replikations-Agenten {#replication-agents}

In AEM Cloud Service werden Inhalte über [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) veröffentlicht. Die in früheren Versionen von AEM verwendeten Replikations-Agenten werden nicht mehr verwendet oder bereitgestellt, was sich möglicherweise auf die folgenden Bereiche bestehender AEM-Projekte auswirken könnte:

* Benutzerdefinierte Workflows, die Inhalte beispielsweise an Replikations-Agenten von Vorschau-Servern senden.
* Anpassung an Replikations-Agenten zur Umwandlung von Inhalten
* Verwendung der Rückwärtsreplikation, um Inhalte aus der Veröffentlichung zurück an den Autor zu senden

## Entfernung der klassischen Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche ist in AEM Cloud Service nicht mehr verfügbar.

## Bereitstellung auf Publishing-Seite {#publish-side-delivery}

HTTP-Beschleunigung einschließlich CDN und Traffic-Management für Autoren- und Veröffentlichungsdienste werden standardmäßig in AEM Cloud Service bereitgestellt.

Für den Projektübergang von AMS oder eine On-Premise-Installation empfiehlt Adobe dringend, das integrierte CDN zu nutzen, da die Funktionen in AEM Cloud Service für das bereitgestellte CDN optimiert sind.

## Asset-Handhabung und -Bereitstellung {#asset-handling}

Asset-Uploads, -Handhabung und -Downloads wurden in AEM Cloud Service optimiert, um eine effizientere Skalierung und schnellere Uploads und Downloads zu ermöglichen. Allerdings kann es Auswirkungen auf vorhandenen benutzerspezifischen Code geben.

* Der Standard-Workflow **DAM-Update-Asset** vorheriger AEM-Versionen ist nicht mehr verfügbar.
* Website-Komponenten, die eine Binärdatei **ohne Umwandlung** bereitstellen, sollten den direkten Download verwenden.
   * Das Sling GET-Servlet wurde entsprechend der Standardeinstellung geändert.
* Website-Komponenten, die eine Binärdatei **mit Umwandlung** bereitstellen (z. B. Größenanpassung über Servlet), können weiterhin wie bisher ausgeführt werden.
* Für Assets, die über Package Manager eingehen, ist eine manuelle erneute Verarbeitung mithilfe der Aktion **Assets erneut verarbeiten** über die AEM Assets-Benutzeroberfläche erforderlich.
