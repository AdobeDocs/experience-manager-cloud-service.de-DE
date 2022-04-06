---
title: Häufig gestellte Fragen zu Cloud Manager
description: Hier finden Sie as a Cloud Service Antworten auf die am häufigsten gestellten Fragen zu Cloud Manager AEM .
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 11ac22974524293ce3e4ceaa26e59fe75ea387e6
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 20%

---


# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Dieses Dokument enthält Antworten auf die am häufigsten gestellten Fragen zu Cloud Manager in AEM as a Cloud Service.

## Kann Java 11 mit Cloud Manager-Builds verwendet werden? {#java-11-cloud-manager}

Ihr AEM Cloud Manager-Build schlägt möglicherweise fehl, wenn versucht wird, den Build von Java 8 auf 11 zu wechseln. Das Problem kann viele Ursachen haben. Die häufigsten Ursachen werden in diesem Abschnitt beschrieben.

* Fügen Sie die `maven-toolchains-plugin` mit den richtigen Einstellungen für Java 11.
   * Dies wird dokumentiert [here](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/using-the-wizard.md#getting-started).
   * Siehe beispielsweise [Projekt-Beispielcode für ein wkend-Projekt](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Wenn der folgende Fehler auftritt, müssen Sie `maven-scr-plugin` und konvertieren Sie alle OSGi-Anmerkungen in OSGi R6-Anmerkungen.
   * Anweisungen finden Sie [hier.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   ```text
   [main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
   ```

* Bei Cloud Manager-Builds muss die `maven-enforcer-plugin` schlägt fehl mit Fehler `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Dies ist ein bekanntes Problem, da Cloud Manager eine andere Version von Java verwendet, um den maven-Befehl auszuführen, anstatt Code zu kompilieren. Vorerst auslassen `requireJavaVersion` von `maven-enforcer-plugin` -Konfigurationen.

## Die Code-Qualitätsprüfung ist fehlgeschlagen und unsere Implementierung ist blockiert. Gibt es eine Möglichkeit, diese Überprüfung zu umgehen? {#deployment-stuck}

Alle Fehler bei der Überprüfung der Code-Qualität mit Ausnahme der Sicherheitsbewertung sind nicht kritische Metriken, sodass sie umgangen werden können, indem die Elemente in der Ergebnisbenutzeroberfläche erweitert werden.

Ein Benutzer im [Bereitstellungs-Manager, Programm-Manager oder Business Owner](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md) -Rolle kann die Probleme überschreiben. In diesem Fall wird die Pipeline fortgesetzt. Diese Verwendungszwecke können auch Probleme akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.

Siehe Dokument . [Tests der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md) für weitere Details.

## Kann ich SNAPSHOT für die Version des Maven-Projekts verwenden? Wie funktioniert die Versionierung der Pakete und Bundle-JAR-Dateien für Staging- und Produktionsimplementierungen? {#snapshot-version}

Die folgenden Szenarien behandeln die Versionierung von Paket- und Bundle-JAR-Dateien für Staging- und Produktionsimplementierungen.

* Bei Entwicklerbereitstellungen die Git-Verzweigung `pom.xml` -Dateien müssen `-SNAPSHOT` am Ende des `<version>` -Wert.
   * Dadurch kann die nachfolgende Bereitstellung weiterhin installiert werden, wenn sich die Version nicht geändert hat. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

* In Staging- und Produktionsimplementierungen wird eine automatische Version wie [dokumentiert.](/help/implementing/cloud-manager/managing-code/project-version-handling.md)

* Legen Sie für die benutzerdefinierte Versionierung in Staging- und Produktionsbereitstellungen eine geeignete dreiteilige Maven-Version wie `1.0.0`. Erhöhen Sie die Version jedes Mal, wenn Sie sie in der Produktion bereitstellen.

* Cloud Manager fügt seine Version automatisch den Staging- und Produktions-Builds hinzu und erstellt eine Git-Verzweigung. Es ist keine spezielle Konfiguration notwendig. Wenn Sie keine Maven-Version wie zuvor beschrieben festlegen, ist die Bereitstellung weiterhin erfolgreich und es wird automatisch eine Version festgelegt.

* Sie können die Version auf `-SNAPSHOT` für Staging- und Produktions-Builds oder -Bereitstellungen ohne Probleme. Cloud Manager legt automatisch eine ordnungsgemäße Versionsnummer fest und erstellt ein Tag für Sie in Git. Falls erforderlich, kann auf dieses Tag später verwiesen werden.

* Wenn Sie einen experimentellen Code in einer Entwicklungsumgebung ausprobieren möchten, können Sie eine neue Git-Verzweigung erstellen und die Pipeline so einrichten, dass sie diese Verzweigung verwendet.
   * Dies ist nützlich, wenn Bereitstellungen fehlschlagen und Sie mit älteren Versionen des Codes testen möchten, um festzustellen, welche Änderung den Fehler verursacht hat.

   * Der folgende git-Befehl erstellt eine Remote-Verzweigung mit dem Namen `testbranch1` auf der Grundlage der bereits existierenden Verpflichtung `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Diese Verzweigung kann in Cloud Manager verwendet werden, ohne dass andere Verzweigungen betroffen sind.

   ```shell
   git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1
   ```

   * Siehe [Git-Dokumentation](https://git-scm.com/book/en/v2/Git-Internals-Git-References) für weitere Details.

   * Wenn Sie die Testverzweigung später löschen möchten, verwenden Sie den Befehl „delete“:

   ```shell
   git push origin --delete testbranch1
   ```

## Mein Maven-Build schlägt bei Cloud Manager-Implementierungen fehl, er wird jedoch ohne Fehler lokal erstellt. Was ist los? {#maven-build-fail}

Weitere Informationen finden Sie unter [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Was kann ich tun, wenn eine Cloud Manager-Bereitstellung im Bereitstellungsschritt in AEM as a Cloud Service fehlschlägt? {#cloud-manager-deployment-cloud-service}

Der häufigste Grund für das Fehlschlagen einer Bereitstellung liegt in unzureichenden Berechtigungen für die `sling-distribution-importer` Benutzer. In diesem Fall schlägt der Bereitstellungsschritt während einer Cloud Manager-Bereitstellung fehl und es werden Fehler wie die folgenden generiert.

```text
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item
org.apache.sling.distribution.common.DistributionException: Error processing distribution package
dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.
Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.
Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.
```

In diesem Fall wird die `sling-distribution-importer` Der Benutzer benötigt zusätzliche Berechtigungen für die Inhaltspfade, die in der `ui.content package`.  Dies bedeutet normalerweise, dass Sie Berechtigungen für beide `/conf` und `/var`.

Die Lösung besteht darin, eine [OSGi-Konfiguration von RepositoryInitializer](/help/implementing/deploying/overview.md#repoint) Skript zu Ihrem App-Bereitstellungspaket hinzufügen, um ACLs für die `sling-distribution-importer` Benutzer.

Im vorherigen Beispielfehler wird das Paket `myapp-base.ui.content-*.zip` enthält Inhalte unter `/conf` und `/var/workflow`. Damit die Bereitstellung erfolgreich ist, müssen die Berechtigungen für die `sling-distribution-importer` unter diesen Pfaden benötigt.

Hier ist ein Beispiel [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) einer solchen OSGi-Konfiguration, die zusätzliche Berechtigungen für die `sling-distribution-importer` Benutzer.  Diese Konfiguration fügt Berechtigungen unter `/var`.  Diese XML-Datei unter [1] muss dem Programmpaket unter `/apps/myapp/config` hinzugefügt werden (wobei „myapp“ der Ordner ist, in dem Ihr Programm-Code gespeichert wird).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

Wenn das Hinzufügen einer OSGi-Konfiguration des RepositoryInitializer den Fehler nicht behoben hat, kann dies auf eines dieser zusätzlichen Probleme zurückzuführen sein.

* Die Bereitstellung schlägt möglicherweise aufgrund einer fehlerhaften OSGi-Konfiguration fehl, die einen vordefinierten Dienst beschädigt.
   * Überprüfen Sie die Protokolle während der Bereitstellung, um festzustellen, ob offensichtliche Fehler vorliegen.

* Die Bereitstellung kann aufgrund falscher Dispatcher- oder Apache-Konfigurationen fehlschlagen.
   * Stellen Sie sicher, dass Sie Ihre Apache- und Dispatcher-Konfigurationen lokal testen, indem Sie das im SDK enthaltene Docker-Bild verwenden.
   * Informationen zum Einrichten des Dispatcher-Docker-Containers für einfache lokale Tests finden Sie unter [Dispatcher in der Cloud](/help/implementing/dispatcher/disp-overview.md#content-delivery).

* Die Bereitstellung kann aufgrund eines anderen Fehlers während der Replikation der Inhaltspakete (Sling-Verteilung) von der Autoren- auf die Veröffentlichungsinstanz fehlschlagen.
   * Führen Sie diese Schritte aus, um das Problem bei einem lokalen Setup zu simulieren.
      1. Installieren Sie eine Autoren- und Veröffentlichungsinstanz lokal mit den neuesten AEM SDK-JARs.
      1. Melden Sie sich bei der Autoreninstanz an.
      1. Navigieren Sie zu **Instrumente** -> **Implementierung** -> **Distribution**.
      1. Verteilen Sie die Inhaltspakete, die Teil der Codebasis sind, und überprüfen Sie, ob die Warteschlange mit einem Fehler blockiert wird.

## Ich kann eine Variable nicht mit einem aio-Befehl festlegen. Was kann ich tun? {#set-variable}

Sie können eine `403` Fehler wie der folgende beim Versuch, Pipeline-Variablen aufzulisten oder festzulegen über `aio` Befehle.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In diesem Fall muss der Benutzer, der diese Befehle ausführt, zum **Implementierung verwalten** Rolle in der Admin Console.

Weitere Informationen finden Sie unter [API-Berechtigungen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md).
