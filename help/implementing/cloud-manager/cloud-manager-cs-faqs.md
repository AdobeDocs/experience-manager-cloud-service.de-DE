---
title: Cloud Manager - Häufig gestellte Fragen zu Cloud Services
seo-title: Häufig gestellte Fragen zu Cloud Manager
description: Tipps zur Fehlerbehebung finden Sie in den häufig gestellten Fragen zu Cloud Manager für Cloud Services .
seo-description: Auf dieser Seite erhalten Sie Antworten auf häufig gestellte Fragen zu Cloud Services und Cloud Manager
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 3%

---

# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen zu Cloud Manager für Cloud Services.

## Ist die Verwendung von Java 11 mit Cloud Manager-Builds möglich? {#java-11-cloud-manager}

Der Build von AEM Cloud Manager schlägt beim Versuch fehl, den Build von Java 8 auf 11 zu wechseln. Das Problem kann viele Ursachen haben. Die häufigsten Ursachen sind nachfolgend beschrieben:

* Fügen Sie das maven-toolchain-plugin mit den richtigen Einstellungen für Java 11 hinzu, wie in [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started) beschrieben.  Siehe beispielsweise den Beispielcode für das Projekt [wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Wenn der folgende Fehler auftritt, müssen Sie die Verwendung von `maven-scr-plugin` entfernen und alle OSGi-Anmerkungen in OSGi R6-Anmerkungen konvertieren. Anweisungen finden Sie unter [hier](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Bei Cloud Manager-Builds schlägt das Maven-Enforcer-Plug-in mit dem Fehler `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"` fehl. Dies ist ein bekanntes Problem, da Cloud Manager eine andere Version von Java verwendet, um den Maven-Befehl im Vergleich zum Kompilierungscode auszuführen. Lassen Sie zunächst `requireJavaVersion` aus Ihren Maven-Enforcer-Plug-in-Konfigurationen weg.

## Unsere Implementierung hängt davon ab, dass die Überprüfung der Code-Qualität fehlgeschlagen ist. Gibt es eine Möglichkeit, diese Prüfung zu umgehen? {#deployment-stuck}

Alle Fehler bei der Code-Qualität mit Ausnahme von *Sicherheitsbewertung* sind nicht kritische Metriken, sodass sie umgangen werden können, indem die Elemente in der Ergebnis-Benutzeroberfläche erweitert werden.

Benutzer mit der Rolle [Bereitstellungsmanager, Projektmanager oder Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt oder sie können die Probleme akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.  Weitere Informationen finden Sie unter [Dreistufige Akzeptanztests beim Ausführen einer Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#how-to-use).


## Können wir SNAPSHOT in der Version des Maven-Projekts verwenden? Wie funktioniert die Versionierung der Pakete und Bundle-JAR-Dateien für Staging- und Produktionsimplementierungen? {#snapshot-version}

In den folgenden Szenarien erfahren Sie mehr über die Versionierung der Pakete und Bundle-JAR-Dateien für Staging- und Produktionsimplementierungen:

1. Bei Entwicklerbereitstellungen muss die Git-Verzweigung `pom.xml` -Dateien `-SNAPSHOT` am Ende des Wertes `<version>` enthalten. Dies ermöglicht eine nachfolgende Bereitstellung, bei der die Version nicht geändert wird, um weiterhin installiert zu werden. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

1. In der Staging- und Produktionsimplementierung wird eine automatische Version generiert, wie dokumentiert [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Legen Sie für die benutzerdefinierte Versionierung in Staging- und Produktionsbereitstellungen eine 3-teilige geeignete Maven-Version wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie eine andere Bereitstellung für die Produktion durchführen müssen.

1. Cloud Manager fügt seine Version automatisch zu Staging- und Produktions-Builds hinzu und erstellt sogar eine Git-Verzweigung. Es ist keine spezielle Konfiguration erforderlich. Wenn Schritt 3 oben übersprungen wird, funktioniert die Bereitstellung weiterhin einwandfrei und eine Version wird automatisch festgelegt.

1. Es gibt keine Probleme, wenn Sie die Version für Staging- und Produktions-Builds oder -Bereitstellungen mit `-SNAPSHOT` belassen. Cloud Manager legt automatisch eine ordnungsgemäße Versionsnummer fest und erstellt ein Tag für Sie in Git. Auf dieses Tag kann bei Bedarf später verwiesen werden.

1. Wenn Sie einen experimentellen Code in der Entwicklungsumgebung ausprobieren möchten, können Sie eine neue Git-Verzweigung erstellen und die Pipeline so einrichten, dass sie diese andere Verzweigung verwendet. Dies ist nützlich, wenn Bereitstellungen fehlschlagen und Sie mit älteren Versionen des Codes testen möchten, um zu sehen, wann er fehlschlug.

   Der folgende Git-Befehl erstellt eine Remote-Verzweigung mit dem Namen *testbranch1* für einen bestimmten bereits vorhandenen Commit `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Diese spezielle Verzweigung kann in Cloud Manager verwendet werden, ohne dass andere Verzweigungen betroffen sind:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Weitere Informationen finden Sie in der [Git-Dokumentation](https://git-scm.com/book/en/v2/Git-Internals-Git-References) .

   Wenn Sie die Testverzweigung später löschen möchten, verwenden Sie den Befehl zum Löschen :

   `git push origin --delete testbranch1`

## Maven-Build schlägt in Cloud Manager fehl, wird jedoch fehlerfrei lokal erstellt. Debugging? {#maven-build-fail}

Weitere Informationen finden Sie unter [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) .

## Was ist zu tun, wenn die Implementierung von Cloud Manager beim Bereitstellungsschritt in AEM as a Cloud Service Environment fehlschlägt? {#cloud-manager-deployment-cloud-service}

Der häufigste Grund für das Fehlschlagen von Bereitstellungen liegt in unzureichenden Berechtigungen für den Benutzer *sling-distribution-importer* .
Im folgenden Beispiel erfahren Sie mehr über Probleme, Ursachen und Lösungen:

****
Problem Bei einer Cloud Manager-Bereitstellung in AEM as a Cloud Service-Umgebungen schlägt der Bereitstellungsschritt fehl und es werden Fehler wie die folgenden beobachtet.

`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10`
`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item`
`org.apache.sling.distribution.common.DistributionException: Error processing distribution package`
`dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.`
`Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.`
`Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.`

**Ursache**

Der Benutzer sling-distribution-importer benötigt zusätzliche Berechtigungen für die Inhaltspfade, die im ui.content-Paket definiert sind.  Dies bedeutet normalerweise, dass wir Berechtigungen für /conf und /var hinzufügen müssen.

****
LösungDie Lösung dafür besteht darin, Ihrem App-Bereitstellungspaket ein  [RepositoryInitializer-OSGi-](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de#deploying) Konfigurationsskript hinzuzufügen, um ACLs für den Benutzer sling-distribution-importer hinzuzufügen.
Im obigen Beispielfehler enthält das Paket myapp-base.ui.content-*.zip Inhalte unter `/conf` und `/var/workflow`. Damit die Bereitstellung nicht fehlschlägt, müssen wir Berechtigungen für den Sling-Distribution-Importer unter diesen Pfaden hinzufügen.
Hier ist ein Beispiel [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) einer solchen OSGi-Konfiguration, die zusätzliche Berechtigungen für den Benutzer sling-distribution-importer hinzufügt.  Diese Konfiguration fügt Berechtigungen unter /var hinzu.  Diese XML-Datei unter [1] muss zum Anwendungspaket unter `/apps/myapp/config` hinzugefügt werden (wobei myapp der Ordner ist, in dem Ihr Anwendungs-Code gespeichert ist).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

1. Wenn *sling-distribution-importer* nicht die Ursache ist, schlägt die Bereitstellung möglicherweise aufgrund einer fehlerhaften OSGi-Konfiguration fehl, die einen vordefinierten Dienst unterbricht. Überprüfen Sie die Protokolle während der Implementierung, um festzustellen, ob offensichtliche Fehler vorliegen.

1. Die Bereitstellung kann aufgrund falscher Dispatcher- oder Apache-Konfigurationen fehlschlagen. Stellen Sie sicher, dass Sie Ihre Apache-Konfigurationen und Dispatcher-Konfigurationen lokal mit dem im SDK enthaltenen Docker-Bild testen. Informationen zum Einrichten des Dispatcher-Docker-Containers für einfache lokale Tests finden Sie unter [Dispatcher in der Cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=de#content-delivery).

1. Die Bereitstellung kann aufgrund eines anderen Fehlers während der Replikation der Inhaltspakete (Sling-Verteilung) von der Autoren- auf die Veröffentlichungsinstanz fehlschlagen.

   Gehen Sie wie folgt vor, um dies bei einer lokalen Einrichtung zu simulieren:

   * Installieren einer Autoren- und Veröffentlichungsinstanz (unter Verwendung der neuesten AEM SDK-JARs)
   * Melden Sie sich bei der Autoreninstanz an
   * Gehen Sie zu **Tools** -> **Bereitstellung** -> **Verteilung**
   * Verteilen Sie die Inhaltspakete, die Teil der Codebasis sind, und überprüfen Sie, ob die Warteschlange mit einem Fehler blockiert wird.

## Pipeline-Variablen können nicht über aio Cloud Manager festgelegt werden. Wie können diese Probleme behoben werden? {#set-variable}

Wenn Sie beim Versuch, Pipeline-Variablen über ähnliche Befehle wie die folgenden aufzulisten oder festzulegen, den Fehler `403` erhalten, müssen Sie in der Admin Console als *Bereitstellungsmanager* Cloud Manager -Produktrolle hinzugefügt werden.\
Weitere Informationen finden Sie unter [API-Berechtigungen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) .

Verwandte Befehle und Fehler:

`$ aio cloudmanager:list-pipeline-variables 222`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1`

`setting variables... !`

*Fehler*: `Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)`
