---
title: Häufig gestellte Fragen zu Cloud Manager – Cloud Services
seo-title: Cloud Manager FAQs
description: Weitere Tipps zur Fehlerbehebung finden Sie in den häufig gestellte Fragen zu Cloud Manager für Cloud Services
seo-description: Follow this page to get answers on Cloud Manager - Cloud Services FAQs
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 100%

---

# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen zu Cloud Manager für Cloud Services.

## Kann Java 11 mit Cloud Manager-Builds verwendet werden? {#java-11-cloud-manager}

AEM Cloud Manager-Build schlägt fehl beim Versuch, den Build von Java 8 auf 11 umzuschalten. Das Problem kann viele Ursachen haben. Die häufigsten Ursachen werden nachfolgend beschrieben:

* Fügen Sie das maven-toolchain-plugin mit den richtigen Einstellungen für Java 11 hinzu, wie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=de#getting-started) beschrieben.  Ein Beispiel finden Sie unter [wknd-Beispielprojekt-Code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Wenn der unten stehende Fehler auftritt, müssen Sie die Verwendung von `maven-scr-plugin` entfernen und alle OSGi-Anmerkungen in OSGi R6-Anmerkungen konvertieren. Anweisungen finden Sie [hier](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Bei Cloud Manager-Builds schlägt das Maven-Enforcer-Plug-in mit dem Fehler `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"` fehl. Dies ist ein bekanntes Problem, da Cloud Manager eine andere Version von Java verwendet, um den maven-Befehl auszuführen, anstatt Code zu kompilieren. Verwenden Sie `requireJavaVersion` vorerst nicht in Ihren maven-enforcer-plugin-Konfigurationen.

## Unsere Bereitstellung ist blockiert, da die Überprüfung der Code-Qualität fehlgeschlagen ist. Gibt es eine Möglichkeit, diese Überprüfung zu umgehen? {#deployment-stuck}

Alle Code-Qualitätsfehler mit Ausnahme der *Sicherheitseinstufung* sind nicht kritische Metriken, sodass sie durch Erweitern der Elemente in der Ergebnisoberfläche umgangen werden können.

Benutzer mit der Rolle [Implementierungs-Manager, Projekt-Manager oder Geschäftsinhaber](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=de#requirements) können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.  Weitere Informationen finden Sie unter [Dreistufige Gates beim Ausführen einer Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#how-to-use).


## Können wir SNAPSHOT in der Version des Maven-Projekts verwenden? Wie funktioniert die Versionierung der Pakete und der JAR-Paketdateien für Staging- und Produktionsbereitstellungen? {#snapshot-version}

In den folgenden Szenarien erfahren Sie mehr über die Versionierung der Pakete und JAR-Paketdateien für Staging- und Produktionsbereitstellungen:

1. Bei Entwicklerbereitstellungen müssen die `pom.xml`-Dateien der Git-Verzweigung `-SNAPSHOT` am Ende des `<version>`-Werts enthalten. Dies ermöglicht nachfolgend eine Bereitstellung, bei der die Version nicht geändert und dennoch installiert wird. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

1. Bei der Staging- und Produktionsbereitstellung wird wie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=den#managing-code) beschrieben eine automatische Version generiert.

1. Legen Sie für die benutzerdefinierte Versionierung in Staging- und Produktionsbereitstellungen eine geeignete dreiteilige Maven-Version wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie eine andere Bereitstellung für die Produktion durchführen müssen.

1. Cloud Manager fügt Staging- und Produktions-Builds automatisch eine eigene Version hinzu und erstellt sogar eine Git-Verzweigung. Es ist keine spezielle Konfiguration notwendig. Wenn Schritt 3 oben übersprungen wird, funktioniert die Bereitstellung dennoch einwandfrei und es wird automatisch eine Version festgelegt.

1. Es gibt keine Probleme, wenn Sie die Version für Staging- und Produktions-Builds oder -Bereitstellungen `-SNAPSHOT` überlassen. Cloud Manager legt automatisch eine geeignete Versionsnummer fest und erstellt ein Tag für Sie in Git. Falls erforderlich, kann auf dieses Tag später verwiesen werden.

1. Wenn Sie einen experimentellen Code für die Entwicklungsumgebung ausprobieren möchten, können Sie eine neue Git-Verzweigung erstellen und die Pipeline so einrichten, dass diese andere Verzweigung verwendet wird. Dies ist nützlich, wenn Bereitstellungen fehlschlagen und Sie ältere Versionen des Codes testen möchten, um zu sehen, wann der Fehler erstmals aufgetreten ist.

   Der unten stehende Git-Befehl erstellt eine Remote-Verzweigung mit dem Namen *testbranch1* gegen einen bestimmten bereits vorhandenen Commit `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Diese spezielle Verzweigung kann in Cloud Manager verwendet werden, ohne dass sich dies auf andere Verzweigungen auswirkt:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Weitere Informationen finden Sie in der [Git-Dokumentation](https://git-scm.com/book/en/v2/Git-Internals-Git-References).

   Wenn Sie die Testverzweigung später löschen möchten, verwenden Sie den Befehl „delete“:

   `git push origin --delete testbranch1`

## Der Maven-Build schlägt in Cloud Manager-Bereitstellungen fehl, wird jedoch ohne Fehler lokal erstellt. Vorgehensweise beim Debugging? {#maven-build-fail}

Weitere Informationen finden Sie unter [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Was ist zu tun, wenn die Bereitstellung von Cloud Manager beim Bereitstellungsschritt in der AEM as a Cloud Service-Umgebung fehlschlägt? {#cloud-manager-deployment-cloud-service}

Der häufigste Grund für fehlgeschlagene Bereitstellungen liegt in unzureichenden Berechtigungen für den *sling-distribution-importer*-Benutzer.
Im folgenden Beispiel erfahren Sie, wie Problem, Ursache und Lösung aussehen:

**Problem**
Bei der Bereitstellung von Cloud Manager in der AEM as a Cloud Service-Umgebung schlägt der Bereitstellungsschritt fehl und es werden Fehler wie die folgenden festgestellt.

`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10`
`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item`
`org.apache.sling.distribution.common.DistributionException: Error processing distribution package`
`dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.`
`Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.`
`Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.`

**Ursache**

Der sling-distribution-Importer-Benutzer benötigt zusätzliche Berechtigungen für die im ui.content-Paket definierten Inhaltspfade.  Das bedeutet in der Regel, dass wir sowohl für „/conf“ als auch für „/var“ Berechtigungen hinzufügen müssen.

**Lösung**
Die Lösung besteht darin, Ihrem Programm-Bereitstellungspaket ein [RepositoryInitializer OSGi-](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de#deploying)-Konfigurationsskript hinzuzufügen, um ACLs für den sling-distribution-importer-Benutzer hinzuzufügen.
Im obigen Beispielfehler enthält das Paket myapp-base.ui.content-*.zip Inhalte unter `/conf` und `/var/workflow`. Damit die Bereitstellung nicht fehlschlägt, müssten wir Berechtigungen für sling-distribution-importer unter diesen Pfaden hinzufügen.
Hier ist ein Beispiel für [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) einer solchen OSGi-Konfiguration, die zusätzliche Berechtigungen für den sling-distribution-importer-Benutzer hinzufügt.  Diese Konfiguration fügt Berechtigungen unter „/var“ hinzu.  Diese XML-Datei unter [1] muss dem Programmpaket unter `/apps/myapp/config` hinzugefügt werden (wobei „myapp“ der Ordner ist, in dem Ihr Programm-Code gespeichert wird).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

1. Wenn der *sling-distribution-importer* nicht die Ursache ist, schlägt die Bereitstellung möglicherweise fehl, weil eine OSGi-Konfiguration fehlerhaft ist, die einen vorkonfigurierten Service unterbricht. Überprüfen Sie die Protokolle während der Bereitstellung, um festzustellen, ob offensichtliche Fehler vorliegen.

1. Die Bereitstellung kann aufgrund falscher Dispatcher- oder Apache-Konfigurationen fehlschlagen. Achten Sie darauf, Ihre Apache-Konfigurationen und Dispatcher-Konfigurationen lokal mit dem im SDK enthaltenen Docker-Image zu testen. Informationen zum Einrichten des Dispatcher-Docker-Containers für einfache lokale Tests finden Sie unter [Dispatcher in der Cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=de#content-delivery).

1. Die Bereitstellung könnte aufgrund eines anderen Fehlers während der Replikation der Inhaltspakete (Sling-Verteilung) vom den Autoren- zu den Veröffentlichungsinstanzen fehlschlagen.

   Gehen Sie wie folgt vor, um dies in einer lokalen Einrichtung zu simulieren:

   * Installieren Sie eine Autoren- und Veröffentlichungsinstanz (unter Verwendung der neuesten AEM SDK-Jars).
   * Melden Sie sich bei der Autoreninstanz an.
   * Gehen Sie zu **Tools** > **Bereitstellung** > **Verteilung**.
   * Verteilen Sie die Inhaltspakete, die Teil der Code-Basis sind, und überprüfen Sie, ob die Warteschlange mit einem Fehler blockiert wird.

## Es ist nicht möglich, eine Variable über AIO-Cloud Manager Pipeline-Variablen festzulegen. Wie können diese Probleme behoben werden? {#set-variable}

Wenn beim Versuch, Pipeline-Variablen über Befehle wie die folgenden aufzulisten oder festzulegen, der Fehler `403` auftritt, müssen Sie in der Admin Console in der Cloud Manager-Produktrolle *Bereitstellungs-Manager* hinzugefügt werden.\
Weitere Informationen finden Sie unter [API-Berechtigungen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md).

Weitere Befehle und Fehler:

`$ aio cloudmanager:list-pipeline-variables 222`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1`

`setting variables... !`

*Fehler*: `Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)`
