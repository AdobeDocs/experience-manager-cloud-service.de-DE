---
title: Wichtige Änderungen an Adobe Experience Manager (AEM) als Cloud-Dienst
description: Wichtige Änderungen an Adobe Experience Manager (AEM) als Cloud-Dienst
translation-type: tm+mt
source-git-commit: e76de9b84931dced6383570e384ffdb6fb334daf

---


# Wichtige Änderungen an Adobe Experience Manager (AEM) als Cloud-Dienst {#notable-changes-aem-cloud}

Der AEM Cloud-Dienst bietet viele neue Funktionen und Möglichkeiten zur Verwaltung Ihrer AEM-Projekte. Es gibt jedoch eine Reihe von Unterschieden zwischen AEM-Sites vor Ort oder im Adobe Managed Service im Vergleich zum AEM Cloud-Dienst. Dieses Dokument hebt die wichtigen Unterschiede hervor.

>[!NOTE]
>In diesem Dokument werden die wesentlichen Änderungen an AEM als Ganzes hervorgehoben. Lösungsspezifische Änderungen finden Sie unter:
>
>* [Wichtige Änderungen an AEM-Sites im AEM Cloud-Dienst](/help/sites-cloud/sites-cloud-changes.md)
>* [Wichtige Änderungen an AEM Assets im AEM Cloud-Dienst](/help/assets/assets-cloud-changes.md)


Die wichtigsten Unterschiede sind in folgenden Bereichen festzustellen:

* [/apps und /libs sind zur Laufzeit unveränderlich](#apps-libs-immutable)
* [OSGi-Pakete und -Einstellungen müssen Repository-basiert sein](#osgi)
* [Änderungen am Veröffentlichungs-Repository sind nicht zulässig](#changes-to-publish-repo)
* [Benutzerdefinierte Ausführungsmodi sind nicht zulässig](#custom-runmodes)
* [Entfernung von Replizierungsagenten](#replication-agents)
* [Entfernen der klassischen Benutzeroberfläche](#classic-ui)
* [Publish-Side-Bereitstellung](#publish-side-delivery)
* [Asset-Handhabung und -Bereitstellung](#asset-handling)

## /apps und /libs sind zur Laufzeit unveränderlich {#apps-libs-immutable}

Alle Inhalte und Unterordner in `/apps` und `/libs` sind schreibgeschützt. Funktionen oder benutzerdefinierter Code, die dort Änderungen vornehmen sollen, schlagen fehl. Es wird ein Fehler zurückgegeben, der besagt, dass solche Inhalte schreibgeschützt sind und der Schreibvorgang nicht abgeschlossen werden konnte. Dies hat Auswirkungen auf eine Reihe von Bereichen von AEM:

* Es `/libs` sind überhaupt keine Änderungen zulässig.
   * Dies ist keine neue Regel, wurde jedoch in früheren lokalen Versionen von AEM nicht erzwungen.
* Überlagerungen für Bereiche, in `/libs` denen Überlagerungen zulässig sind, sind innerhalb von zulässig `/apps`.
   * Solche Überlagerungen müssen von Git über die CI/CD-Pipeline kommen.
* Designinformationen für statische Vorlagen, die in gespeichert sind, `/apps` können nicht über die Benutzeroberfläche bearbeitet werden.
   * Es wird empfohlen, stattdessen bearbeitbare Vorlagen zu verwenden.
   * Sind weiterhin statische Vorlagen erforderlich, müssen die Konfigurationsinformationen über die CI/CD-Pipeline von Git stammen.
* MSM Blueprint und benutzerdefinierte MSM Roll-out Konfigurationen müssen von Git über die CI/CD-Pipeline installiert werden.
* Änderungen an der I18n-Übersetzung müssen von Git über die CI/CD-Pipeline vorgenommen werden.

## OSGi-Pakete und -Einstellungen müssen Repository-basiert sein {#osgi}

Die Webkonsole, die in früheren Versionen von AEM zum Ändern der OSGi-Einstellungen verwendet wird, ist im AEM Cloud-Dienst nicht verfügbar. Daher müssen Änderungen an OSGi über die CI/CD-Pipeline vorgenommen werden.

* Änderungen an OSGi-Einstellungen können nur über Git-Persistenz als JCR-basierte OSGi-Einstellungen vorgenommen werden.
* Neue oder aktualisierte OSGi-Pakete müssen über Git als Teil des CI/CD-Pipeline-Buildprozesses eingeführt werden.

## Änderungen am Veröffentlichungs-Repository sind nicht zulässig {#changes-to-publish-repo}

Direkte Änderungen am Veröffentlichungs-Repository sind im AEM Cloud-Dienst nicht zulässig. In früheren Versionen von AEM oder AEM on AMS vor Ort können Codeänderungen direkt am Veröffentlichungs-Repository vorgenommen werden, um beispielsweise Benutzer zu erstellen, das Benutzerprofil zu aktualisieren und Knoten zu erstellen. Dies ist nicht mehr möglich und kann wie folgt reduziert werden:

* Für inhalts- und inhaltsbasierte Konfiguration: nimmt die Änderungen an der Autoreninstanz vor und veröffentlicht sie.
* Für Code und Konfiguration: Nehmen Sie die Änderungen im GIT-Repository vor und führen Sie die CI/CD-Pipeline aus, um sie auszuführen.
* Für benutzerbezogene Daten, z. B. Formularübermittlungen oder Profildaten: Verwenden Sie den Unified Profile Service aus Experience Cloud-Plattform oder einem anderen sitzungsbasierten Store eines Drittanbieters.

## Benutzerdefinierte Ausführungsmodi sind nicht zulässig {#custom-runmodes}

Für den AEM Cloud-Dienst stehen die folgenden Ausführungsmodi standardmäßig zur Verfügung:

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

Zusätzliche oder benutzerdefinierte Ausführungsmodi sind im AEM Cloud-Dienst nicht möglich.

## Entfernung von Replizierungsagenten {#replication-agents}

Im AEM Cloud-Dienst werden Inhalte mithilfe der [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html)veröffentlicht. Die in früheren Versionen von AEM verwendeten Replizierungsagenten werden nicht mehr verwendet oder bereitgestellt, was sich möglicherweise auf die folgenden Bereiche bestehender AEM-Projekte auswirken könnte:

* Benutzerdefinierte Workflows, die Inhalte beispielsweise an Replizierungsagenten von Vorschauservern senden.
* Anpassung an Replizierungsagenten zur Inhaltsumwandlung
* Rückwärtsreplikation verwenden, um Inhalte von der Veröffentlichung zurück zum Autor zu bringen

## Entfernen der klassischen Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche ist im AEM Cloud-Dienst nicht mehr verfügbar.

## Publish-Side-Bereitstellung {#publish-side-delivery}

HTTP-Beschleunigung einschließlich CDN und Traffic-Management für Autor- und Veröffentlichungsdienste werden standardmäßig im AEM Cloud-Dienst bereitgestellt.

Für den Projektwechsel von AMS oder einer lokalen Installation empfiehlt Adobe dringend die Nutzung des integrierten CDN, da die Funktionen im AEM Cloud-Dienst für das bereitgestellte CDN optimiert sind.

## Asset-Handhabung und -Bereitstellung {#asset-handling}

Asset-Uploads, -Behandlungen und -Downloads wurden im AEM Cloud-Dienst optimiert, um eine effizientere Skalierung und schnellere Uploads und Downloads zu ermöglichen. Dies kann sich jedoch auf vorhandenen benutzerdefinierten Code auswirken.

* Die standardmäßige Workflow- **DAM-Asset-Aktualisierung** in früheren Versionen von AEM ist nicht mehr verfügbar.
* Website-Komponenten, die eine Binärdatei **ohne Konvertierung** bereitstellen, sollten einen direkten Download verwenden.
   * Das Sling GET-Servlet wurde entsprechend der Standardeinstellung geändert.
* Website-Komponenten, die eine Binärdatei **mit Transformation** bereitstellen (z. B. Größenanpassung über Servlet) können weiterhin wie bisher funktionieren.
* Für Assets, die über Package Manager eingehen, ist eine manuelle Neuverarbeitung mithilfe der Aktion &quot;Asset **neu verarbeiten&quot;** in der Benutzeroberfläche &quot;Assets&quot;erforderlich.
