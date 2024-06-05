---
title: Häufig gestellte Fragen zu Cloud Manager
description: Hier finden Sie Antworten auf die am häufigsten gestellten Fragen zu Cloud Manager in AEM as a Cloud Service.
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 100%

---


# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Dieses Dokument enthält Antworten auf die am häufigsten gestellten Fragen zu Cloud Manager in AEM as a Cloud Service.

## Kann Java™ 11 mit Cloud Manager-Builds verwendet werden? {#java-11-cloud-manager}

Ja. Fügen Sie das `maven-toolchains-plugin` mit den richtigen Einstellungen für Java™ 11 hinzu.

Der Prozess wird [hier](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/using-the-wizard.md#getting-started) dokumentiert.

Ein Beispiel finden Sie unter [WKND-Beispielprojekt-Code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Mein Build schlägt mit einer Fehlermeldung über das maven-scr-plugin fehl, nachdem ich von Java™ 8 zu Java™ 11 gewechselt habe. Was kann ich tun? {#build-fails-maven-scr-plugin}

Ihr AEM Cloud Manager-Build schlägt möglicherweise fehl beim Versuch, den Build von Java™ 8 auf 11 zu wechseln. Wenn der unten stehende Fehler auftritt, müssen Sie das `maven-scr-plugin` entfernen und alle OSGi-Anmerkungen in OSGi R6-Anmerkungen konvertieren.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 > [Help 1]
```

Anweisungen zum Entfernen dieses Plug-ins finden Sie [hier](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Mein Build schlägt mit einer Fehlermeldung über die RequireJavaVersion fehl, nachdem ich von Java™ 8 zu Java™ 11 gewechselt habe. Was kann ich tun? {#build-fails-requirejavaversion}

Bei Cloud Manager-Builds kann das `maven-enforcer-plugin` mit diesem Fehler fehlschlagen.

```text
"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion".
```

Dies ist ein bekanntes Problem, das darauf zurückzuführen ist, dass Cloud Manager eine andere Java™-Version verwendet, um den Maven-Befehl auszuführen, als den Code zu kompilieren. Lassen Sie einfach `requireJavaVersion` in den Konfigurationen Ihres `maven-enforcer-plugin` weg.

## Die Code-Qualitätsprüfung ist fehlgeschlagen und unsere Bereitstellung ist blockiert. Gibt es eine Möglichkeit, diese Überprüfung zu umgehen? {#deployment-stuck}

Ja. Alle Fehler bei der Überprüfung der Code-Qualität mit Ausnahme der Sicherheitseinstufung sind nicht kritische Metriken, sodass sie als Teil einer Bereitstellungs-Pipeline übersprungen werden können, indem die Elemente in der Ergebnis-Benutzeroberfläche erweitert werden.

Benutzer mit der Rolle [Bereitstellungs-Manager, Projekt-Manager oder Geschäftsinhaber](/help/onboarding/aem-cs-team-product-profiles.md#cloud-manager-product-profiles) können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.

Weitere Informationen finden Sie in den Dokumenten [Testen der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md#three-tiered-gate) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#non-production-pipelines).

## Kann ich SNAPSHOT für die Version des Maven-Projekts verwenden? {#use-snapshot}

Ja. Bei Entwicklerbereitstellungen müssen die `pom.xml`-Dateien der Git-Verzweigung am Ende des `<version>`-Werts `-SNAPSHOT` enthalten.

Dadurch kann die nachfolgende Bereitstellung weiterhin installiert werden, wenn sich die Version nicht geändert hat. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

Sie können die Version für Staging- und Produktions-Builds oder -Bereitstellungen auch auf `-SNAPSHOT` setzen. Cloud Manager legt automatisch eine geeignete Versionsnummer fest und erstellt für Sie in Git ein Tag. Falls erforderlich, kann auf dieses Tag später verwiesen werden.

Weitere Informationen zur Versionsverwaltung finden Sie [hier dokumentiert](/help/implementing/cloud-manager/managing-code/project-version-handling.md).

## Wie funktioniert die Paket-Versionierung für Staging- und Produktionsbereitstellungen? {#snapshot-version}

Bei der Staging- und Produktionsbereitstellung wird wie [hier dokumentiert](/help/implementing/cloud-manager/managing-code/project-version-handling.md) eine automatische Version erzeugt.

Für die benutzerdefinierte Versionierung in Staging- und Produktionsbereitstellungen legen Sie eine korrekte dreiteilige Maven-Version wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie sie in der Produktion bereitstellen.

Cloud Manager fügt Staging- und Produktions-Builds automatisch eine eigene Version hinzu und erstellt sogar eine Git-Verzweigung. Es ist keine spezielle Konfiguration notwendig. Wenn Sie keine Maven-Version wie zuvor beschrieben festlegen, ist die Bereitstellung trotzdem erfolgreich und eine Version wird automatisch festgelegt.

## Mein Maven-Build schlägt bei Cloud Manager-Bereitstellungen fehl, lokal wird er jedoch ohne Fehler erstellt. Was läuft da schief? {#maven-build-fail}

Weitere Informationen dazu finden Sie in [dieser Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Was ist zu tun, wenn die Implementierung von Cloud Manager beim Bereitstellungsschritt in der AEM as a Cloud Service-Umgebung fehlschlägt? {#cloud-manager-deployment-cloud-service}

Der häufigste Grund für fehlgeschlagene Bereitstellungen liegt in unzureichenden Berechtigungen für den `sling-distribution-importer`-Benutzer. In diesem Fall schlägt der Bereitstellungsschritt während einer Cloud Manager-Implementierung fehl und es werden Fehler wie die folgenden erzeugt.

```text
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item
org.apache.sling.distribution.common.DistributionException: Error processing distribution package
dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.
Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.
Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.
```

Benutzerinnen und Benutzer von `sling-distribution-importer` benötigen zusätzliche Berechtigungen für die im `ui.content package` definierten Inhaltspfade. Das bedeutet in der Regel, dass Sie sowohl für `/conf` als auch für `/var` Berechtigungen hinzufügen müssen.

Die Lösung besteht darin, Ihrem Programm-Bereitstellungspaket ein [RepositoryInitializer OSGi-Konfigurations](/help/implementing/deploying/overview.md#repoint)-Skript hinzuzufügen, um ACLs für die `sling-distribution-importer`-Benutzerinnen und -Benutzer hinzuzufügen.

Im obigen Beispielfehler enthält das Paket `myapp-base.ui.content-*.zip` Inhalte unter `/conf` und `/var/workflow`. Damit die Bereitstellung erfolgreich ist, werden Berechtigungen für den `sling-distribution-importer` unter diesen Pfaden benötigt.

Hier ist ein Beispiel für eine [`org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config`](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config)-OSGi-Konfiguration, die zusätzliche Berechtigungen für Benutzerinnen und Benutzer von `sling-distribution-importer` hinzufügt. Die Konfiguration fügt Berechtigungen unter `/var` hinzu. Eine solche Konfiguration muss dem Anwendungspaket unter `/apps/myapp/config` hinzugefügt werden (wobei myapp der Ordner ist, in dem Ihr Anwendungscode gespeichert ist).

## Meine Cloud Manager-Implementierung schlägt beim Bereitstellungsschritt in AEM as a Cloud Service fehl und ich habe bereits eine OSGi-Konfiguration für RepositoryInitializer hinzugefügt. Was kann ich sonst noch tun? {#build-failures}

Wenn das [Hinzufügen einer OSGi-Konfiguration für RepositoryInitializer](#cloud-manager-deployment-cloud-service) den Fehler nicht behoben hat, kann dies auf eines dieser zusätzlichen Probleme zurückzuführen sein.

* Die Bereitstellung schlägt möglicherweise aufgrund einer fehlerhaften OSGi-Konfiguration fehl, die einen vorkonfigurierten Service beschädigt.
   * Überprüfen Sie die Protokolle während der Bereitstellung, um festzustellen, ob offensichtliche Fehler vorliegen.

* Die Bereitstellung kann aufgrund falscher Dispatcher- oder Apache-Konfigurationen fehlschlagen.
   * Achten Sie darauf, Ihre Apache- und Dispatcher-Konfigurationen lokal mit dem im SDK enthaltenen Docker-Image zu testen.
   * Informationen zum Einrichten des Dispatcher-Docker-Containers für einfache lokale Tests finden Sie unter [Dispatcher in der Cloud](/help/implementing/dispatcher/disp-overview.md#content-delivery).

* Die Bereitstellung könnte aufgrund eines anderen Fehlers während der Replikation der Inhaltspakete (Sling-Verteilung) von den Authoring- zu den Publishing-Instanzen fehlschlagen.
   * Führen Sie diese Schritte aus, um das Problem bei einem lokalen Setup zu simulieren.
      1. Installieren Sie eine Authoring- und eine Publishing-Instanz (unter Verwendung der neuesten AEM SDK-jars).
      1. Melden Sie sich bei der Authoring-Instanz an.
      1. Gehen Sie zu **Tools** > **Bereitstellung** > **Verteilung**.
      1. Verteilen Sie die Inhaltspakete, die Teil der Code-Basis sind, und überprüfen Sie, ob die Warteschlange mit einem Fehler blockiert wird.

## Ich kann eine Variable nicht mit einem aio-Befehl festlegen. Was kann ich tun? {#set-variable}

Wenn Sie versuchen, Pipeline-Variablen über `aio`-Befehle aufzulisten oder festzulegen, erhalten Sie möglicherweise einen `403`-Fehler wie den folgenden.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In diesem Fall müssen die Personen, die diese Befehle ausführen, in der Admin Console zur Rolle der **Bereitstellungs-Manager** hinzugefügt werden.

Weitere Informationen finden Sie unter [API-Berechtigungen](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/).
