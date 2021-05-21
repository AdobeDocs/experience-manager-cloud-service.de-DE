---
title: Häufig gestellte Fragen zu Cloud Manager – Cloud Services
seo-title: Häufig gestellte Fragen zu Cloud Manager
description: Weitere Tipps zur Fehlerbehebung finden Sie in den häufig gestellte Fragen zu Cloud Manager für Cloud Services
seo-description: Auf dieser Seite erhalten Sie Antworten zu den häufig gestellten Fragen zu Cloud Manager – Cloud Services
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 100%

---

# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen zu Cloud Manager für Cloud Services.

## Kann Java 11 mit Cloud Manager-Builds verwendet werden? {#java-11-cloud-manager}

Ein AEM Cloud Manager-Build schlägt fehl, wenn versucht wird, den Build von Java 8 auf 11 umzustellen. Das Problem kann viele Ursachen haben, und die häufigsten werden nachfolgend beschrieben:

* Fügen Sie das maven-toolchains-Plug-in mit den richtigen Einstellungen für Java 11 hinzu, wie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=de#getting-started) dokumentiert.  Beispiel: Siehe den [Code des wknd-Beispielprojekts](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Wenn Sie auf den unten stehenden Fehler stoßen, müssen Sie die Verwendung von `maven-scr-plugin` entfernen und alle OSGi-Annotationen in OSGi R6-Annotationen konvertieren. Anweisungen finden Sie [hier](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Bei Cloud Manager-Builds schlägt das Maven-Enforcer-Plug-in mit dem Fehler `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"` fehl. Dies ist ein bekanntes Problem, das darauf zurückzuführen ist, dass Cloud Manager eine andere Java-Version verwendet, um den Maven-Befehl auszuführen, als den Code zu kompilieren. Lassen Sie vorerst `requireJavaVersion` aus Ihren maven-enforcer-Plug-in-Konfigurationen aus.

## Unsere Bereitstellung bleibt stecken, weil die Code-Qualitätsprüfung fehlgeschlagen ist. Gibt es eine Möglichkeit, diese Prüfung zu umgehen? {#deployment-stuck}

Alle Codequalitätsfehler mit Ausnahme der *Sicherheitseinstufung* sind nicht kritische Metriken, sodass sie durch Erweitern der Elemente in der Ergebnisoberfläche umgangen werden können.

Ein Benutzer mit der Rolle [Deployment Manager, Project Manager oder Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=de#requirements) kann die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.  Weitere Informationen finden Sie unter [Dreistufige Gates beim Ausführen einer Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#how-to-use).


## Können wir SNAPSHOT in der Version des Maven-Projekts verwenden? Wie funktioniert die Versionierung der Pakete und der Bundle-JAR-Dateien für Staging- und Entwicklungsbereitstellungen? {#snapshot-version}

In den folgenden Szenarien erfahren Sie mehr über die Versionierung der Pakete und Bundle-JAR-Dateien für Staging- und Entwicklungsbereitstellungen:

1. Bei Entwicklungsbereitstellungen muss die Git-Verzweigung `pom.xml`-Dateien `-SNAPSHOT` am Ende des `<version>`-Werts enthalten. Dadurch können spätere Bereitstellungen, bei denen sich die Version nicht ändert, trotzdem installiert werden. In Entwicklungsbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

1. In der Staging- und Produktionsbereitstellungen wird eine automatische Version generiert, wie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=den#managing-code) beschrieben.

1. Legen Sie für benutzerdefinierte Versionen in Staging- und Produktionsbereitstellungen eine 3-teilige Maven-Version wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie eine weitere Bereitstellung für die Produktion durchführen müssen.

1. Cloud Manager fügt seine Version automatisch zu Staging- und Produktions-Builds hinzu und erstellt sogar eine Git-Verzweigung. Es ist keine spezielle Konfiguration erforderlich. Wenn Schritt 3 oben übersprungen wird, funktioniert die Bereitstellung weiterhin einwandfrei und eine Version wird automatisch eingestellt.

1. Es gibt keine Probleme, wenn Sie die Version für Staging- und Produktions-Builds oder -Bereitstellungen bei `-SNAPSHOT` belassen. Cloud Manager legt automatisch eine korrekte Versionsnummer fest und erstellt ein Tag für Sie in Git. Falls erforderlich, kann auf dieses Tag später verwiesen werden.

1. Wenn Sie einen experimentellen Code für die Entwicklungsumgebung ausprobieren möchten, können Sie eine neue Git-Verzweigung erstellen und die Pipeline so einrichten, dass diese andere Verzweigung verwendet wird. Dies ist nützlich, wenn Bereitstellungen fehlschlagen und Sie mit älteren Versionen des Codes testen möchten, um zu sehen, wann der Fehler auftritt.

   Mit dem folgenden Git-Befehl wird eine Remote-Verzweigung mit dem Namen *testbranch1* für ein bestimmtes bereits vorhandenes Commit `485548e4fbafbc83b11c3cb12b035c9d26b6532b` erstellt.  Diese spezielle Verzweigung kann in Cloud Manager verwendet werden, ohne dass sich dies auf andere Verzweigungen auswirkt:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Weitere Informationen finden Sie in der [Git-Dokumentation](https://git-scm.com/book/de/v2/Git-Internals-Git-References).

   Wenn Sie die Testverzweigung später löschen möchten, verwenden Sie den Löschbefehl:

   `git push origin --delete testbranch1`

## Der Maven-Build schlägt in Cloud Manager-Bereitstellungen fehl, wird jedoch ohne Fehler lokal erstellt. Wie kann man das debuggen? {#maven-build-fail}

Weitere Informationen finden Sie in der [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

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

Wenn Sie eine `403`-Fehlermeldung erhalten, wenn Sie versuchen, Pipeline-Variablen über Befehle aufzulisten oder zu setzen, die den unten aufgeführten ähnlich sind, müssen Sie in der Admin Console mit der Cloud Manager-Produktrolle *Deployment Manager* hinzugefügt werden.\
Weitere Informationen finden Sie unter [API-Berechtigungen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md).

Verwandte Befehle und Fehler:

`$ aio cloudmanager:list-pipeline-variables 222`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1`

`setting variables... !`

*Fehler*: `Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)`
