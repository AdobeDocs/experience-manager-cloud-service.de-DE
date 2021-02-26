---
title: Cloud Manager - Häufig gestellte Fragen zu Cloud Services
seo-title: Häufig gestellte Fragen zu Cloud Manager
description: Weitere Tipps zur Fehlerbehebung finden Sie unter Häufig gestellte Fragen zu Cloud Services zu Cloud Manager
seo-description: Auf dieser Seite erhalten Sie Antworten zu den häufig gestellten Fragen zu Cloud Services zu Cloud Manager
translation-type: tm+mt
source-git-commit: 75a5ff02e5f7c0e0e3ba42c8559851d3c98c3c8d
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 3%

---


# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen zu Cloud Manager für Cloud Services.

## Kann Java 11 mit Cloud Manager-Builds verwendet werden? {#java-11-cloud-manager}

AEM Cloud Manager-Build schlägt fehl, wenn versucht wird, den Build von Java 8 auf 11 umzuschalten. Das Problem kann viele Ursachen haben, und die häufigsten Ursachen werden nachfolgend beschrieben:

* hinzufügen Sie das maven-toolchain-plugin mit den richtigen Einstellungen für Java 11, wie hier beschrieben [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Beispiel: Siehe [Arbeits-Beispielprojektcode](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Wenn der unten stehende Fehler auftritt, müssen Sie die Verwendung von `maven-scr-plugin` entfernen und alle OSGi-Anmerkungen in OSGi R6-Anmerkungen konvertieren. Anweisungen hierzu finden Sie unter [hier](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Bei Cloud Manager-Builds schlägt das Master-Plug-In mit dem Fehler `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"` fehl. Dies ist ein bekanntes Problem, da Cloud Manager eine andere Version von Java verwendet, um den maven-Befehl auszuführen, anstatt Code zu kompilieren. Für den Moment lassen Sie `requireJavaVersion` in Ihren maven-enforcer-plugin Konfigurationen aus.

## Die Bereitstellung ist blockiert, da die Überprüfung der Codequalität fehlgeschlagen ist. Gibt es eine Möglichkeit, diese Prüfung zu umgehen? {#deployment-stuck}

Alle Fehler bei der Codequalität mit Ausnahme von *Sicherheitsbewertung* sind nicht kritische Metriken, sodass sie umgangen werden können, indem die Elemente in der Ergebnis-Benutzeroberfläche erweitert werden.

Ein Benutzer mit der Rolle [Deployment Manager, Project Manager oder Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) kann die Probleme überschreiben. In diesem Fall wird die Pipeline fortgesetzt oder er kann die Probleme akzeptieren. In diesem Fall stoppt die Pipeline bei einem Fehler.  Weitere Informationen finden Sie unter [Drei-Stufen-Gates beim Ausführen einer Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#how-to-use).


## Können wir SNAPSHOT in der Version des Maven-Projekts verwenden? Wie funktioniert die Versionsverwaltung der Pakete und Bundle-JAR-Dateien für Bereitstellungen von Bühne und Produktion? {#snapshot-version}

In den folgenden Szenarien erfahren Sie mehr über die Versionsverwaltung der Pakete und Bundle-JAR-Dateien für Bereitstellungen von Bühne und Produktion:

1. Bei Entwicklerbereitstellungen müssen die Git-Verzweigungsdateien `pom.xml` am Ende des `<version>`-Werts `-SNAPSHOT` enthalten. Dies ermöglicht eine spätere Bereitstellung, bei der die Version nicht geändert wird, um weiterhin installiert zu werden. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

1. In der Stage- und Production-Bereitstellung wird eine automatische Version wie dokumentiert [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code) generiert.

1. Legen Sie für benutzerdefinierte Versionen in Bereitstellungen für Bühne und Produktion eine geeignete 3-teilige Version für maven wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie eine andere Bereitstellung für die Produktion durchführen müssen.

1. Cloud Manager fügt die Version automatisch zu Stage- und Production-Builds hinzu und erstellt sogar eine Git-Verzweigung. Es ist keine spezielle Konfiguration erforderlich. Wenn Schritt 3 oben übersprungen wird, funktioniert die Bereitstellung weiterhin einwandfrei und eine Version wird automatisch festgelegt.

1. Es gibt keine Probleme, wenn Sie die Version mit `-SNAPSHOT` für Stage- und Production-Builds oder Bereitstellungen verlassen. Cloud Manager legt automatisch eine korrekte Versionsnummer fest und erstellt ein Tag für Sie in Git. Auf dieses Tag kann später, falls erforderlich, verwiesen werden.

1. Wenn Sie einen experimentellen Code in der Entwicklungsumgebung ausprobieren möchten, können Sie eine neue Git-Verzweigung erstellen und die Pipeline so einrichten, dass sie diese andere Verzweigung verwendet. Dies ist nützlich, wenn Bereitstellungen fehlschlagen und Sie mit älteren Versionen des Codes testen möchten, um zu sehen, wann er kaputt ist.

   Mit dem folgenden Git-Befehl wird eine Remote-Verzweigung mit dem Namen *testverzweigung1* für einen bestimmten bereits vorhandenen Commit `485548e4fbafbc83b11c3cb12b035c9d26b6532b` erstellt.  Diese spezielle Verzweigung kann in Cloud Manager verwendet werden, ohne dass sich dies auf andere Verzweigungen auswirkt:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Weitere Informationen finden Sie in der [Git-Dokumentation](https://git-scm.com/book/en/v2/Git-Internals-Git-References).

   Wenn Sie die Testverzweigung später löschen möchten, verwenden Sie den Befehl zum Löschen:

   `git push origin --delete testbranch1`

## Maven Build schlägt in Cloud Manager bei der Bereitstellung fehl, wird aber lokal ohne Fehler erstellt. Debugging? {#maven-build-fail}

Weitere Informationen finden Sie unter [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Was ist zu tun, wenn die Bereitstellung von Cloud Manager im Bereitstellungsschritt bei AEM als Cloud Service-Umgebung fehlschlägt? {#cloud-manager-deployment-cloud-service}

Der häufigste Grund für einen Fehler bei der Bereitstellung liegt in unzureichenden Berechtigungen für den *sling-distribution-importer*-Benutzer.
Im folgenden Beispiel erfahren Sie, wie Sie ein Problem, eine Ursache und eine Lösung verstehen:

****
ProblemBei der Bereitstellung von Cloud Manager auf AEM als Cloud Service-Umgebungen schlägt der Bereitstellungsschritt fehl und es werden Fehler wie die folgenden festgestellt.

`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10`
`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item`
`org.apache.sling.distribution.common.DistributionException: Error processing distribution package`
`dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.`
`Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.`
`Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.`

**Ursache**

Der Benutzer von sling-distribution-importer benötigt zusätzliche Berechtigungen für die im Paket ui.content definierten Inhaltspfade.  Dies bedeutet in der Regel, dass wir Berechtigungen für /conf und /var hinzufügen müssen.

****
LösungDie Lösung hierfür besteht darin, Ihrem Apps-Bereitstellungspaket ein  [RepositoryInitializer OSGi-](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de#deploying) Konfigurationsskript hinzuzufügen, um ACLs für den Benutzer von sling-distribution-importer hinzuzufügen.
Im obigen Beispielfehler enthält das Paket myapp-base.ui.content-*.zip Inhalte unter `/conf` und `/var/workflow`. Damit die Bereitstellung nicht fehlschlägt, müssen wir Berechtigungen für Sling-Distribution-Importer unter diesen Pfaden hinzufügen.
Im Folgenden finden Sie ein Beispiel [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) einer solchen OSGi-Konfiguration, die zusätzliche Berechtigungen für den sling-distribution-importer-Benutzer hinzufügt.  Diese Konfiguration fügt Berechtigungen unter /var hinzu.  Diese XML-Datei unterhalb von [1] muss dem Anwendungspaket unter `/apps/myapp/config` hinzugefügt werden (wobei &quot;myapp&quot;der Ordner ist, in dem der Anwendungscode gespeichert ist).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

1. Wenn der *sling-distribution-importer* nicht die Ursache ist, schlägt die Bereitstellung möglicherweise aufgrund einer fehlerhaften OSGi-Konfiguration fehl, die einen Out-of-Box-Dienst ausschließt. Überprüfen Sie die Protokolle während der Bereitstellung, um festzustellen, ob offensichtliche Fehler vorliegen.

1. Die Bereitstellung kann aufgrund falscher Dispatcher- oder Apache-Konfigurationen fehlschlagen. Testen Sie Ihre Apache-Konfigurationen und Dispatcher-Konfigurationen lokal mithilfe des im SDK enthaltenen Docker-Bildes. Informationen zum Einrichten des Dispatcher Docker-Containers für einfache lokale Tests finden Sie unter [Dispatcher in der Cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=de#content-delivery).

1. Die Bereitstellung schlägt möglicherweise aufgrund eines anderen Fehlers während der Replikation der Inhaltspakete (Sling-Verteilung) vom Autor zu Veröffentlichungsinstanzen fehl.

   Führen Sie die folgenden Schritte aus, um dies bei einer lokalen Einrichtung zu simulieren:

   * Instanzen im Autor- und Veröffentlichungsmodus installieren (unter Verwendung der neuesten AEM SDK-Jars)
   * Melden Sie sich bei der Autoreninstanz an.
   * Gehen Sie zu **Tools** -> **Deployment** -> **Distribution**
   * Verteilen Sie die Inhaltspakete, die Teil der Code-Basis sind, und überprüfen Sie, ob die Warteschlange mit einem Fehler blockiert wird.

## Eine Variable kann nicht über festgelegte Pipelinevariablen des AIO Cloud Managers festgelegt werden. Wie können Sie diese Probleme beheben? {#set-variable}

Wenn beim Versuch, Pipelinevariablen über Befehle ähnlich wie die unten aufgeführten aufzulisten oder festzulegen, ein `403`-Fehler auftritt, müssen Sie als *Bereitstellungs-Manager* Cloud Manager-Produktrolle in der Admin Console hinzugefügt werden.\
Weitere Informationen finden Sie unter [API-Berechtigungen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md).

Zugehörige Befehle und Fehler:

`$ aio cloudmanager:list-pipeline-variables 222`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1`

`setting variables... !`

*Fehler*: `Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)`
