---
title: AEM as a Cloud Service Developer Console (Beta)
description: Erfahren Sie mehr über CRX/DE Lite und AEM as a Cloud Service Developer Console
feature: Developing
role: Admin, Architect, Developer
exl-id: 4b0fc3e9-b7c4-4c95-bd97-8b24e4d5cb3d
source-git-commit: 4eb0feecbc5d0f090789bd3023e366ef4eb620db
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 14%

---

# AEM as a Cloud Service Developer Console (Beta) {#developer-console}

>[!NOTE]
>
>In diesem Artikel wird ein überarbeitetes Erlebnis für AEM Cloud Service Developer Console beschrieben, das sich jetzt in der Beta-Phase befindet und für einige Kunden verfügbar ist, indem Sie oben in der klassischen Benutzeroberfläche auf eine Schaltfläche klicken. Wir freuen uns über Ihr Feedback an `aemcs-new-devconsole-ui-beta@adobe.com`. Weitere Informationen zur klassischen AEM Developer Console finden Sie [diesem Artikel](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

AEM as a Cloud Service Developer Console enthält eine Reihe von Tools zum Debugging in Cloud-Umgebungen. Auf ihn kann über einen Link pro Umgebung in Cloud Manager zugegriffen werden.

>[!NOTE]
>Die AEM as a Cloud Service Developer Console sollte nicht mit der ähnlich benannten [*Adobe Developer Console*](https://developer.adobe.com/developer-console/) verwechselt werden.
>


<!--
There are multiple ways of accessing it:

1. Launch from Cloud Manager  

1. Type a url that can be determined by adjusting the Author or Publish service urls as follows:
   ```  
   https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com
   ```  

1. As a shortcut, the following Cloud Manager CLI command can be used to launch the AEM as a Cloud Service Developer Console based on an environment parameter described below:    
   ```
   aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>
   ```
-->

Entwickler können auf die unten beschriebenen Funktionen zugreifen:

## OSGi-Bundles {#osgi-bundles}

![Bildschirm „Neue OSGi-Bundles“ in der Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* Dadurch erhalten Sie einen Überblick über die OSGi-Bundles, die für den ausgewählten Umgebungstyp bereitgestellt werden. Sie ermöglicht eine Volltextsuche.
* Es ist nützlich, Informationen über den tatsächlichen Status von Bundles in der Umgebung zu erhalten. Sie können Informationen wie exportierte Pakete, importierte Pakete, verwendete Services und mehr erhalten.
* Entwickler möchten die tatsächliche Umgebung überprüfen und überprüfen, ob das Bundle das tut, was sie erwarten.
* **Anwendungsbeispiel:** Ein Versionsbereich einer Abhängigkeit ist in Ihrem Bundle angegeben. Etwas läuft schief in der Abhängigkeit. Sie möchten überprüfen, welche Version der Abhängigkeit in Ihr Bundle verkabelt wird. Um dies zu überprüfen, gehen Sie zu den Bundle-Details und verwenden Sie den Import von Bundles/Paketen, um zu überprüfen, welche Bundle-Version oder Paketversion zur Laufzeit verwendet wird, um dies herauszufinden. Mit diesen Informationen können Sie Ihren Maven-Abhängigkeits-Versionsbereich anpassen oder Ihren Code anpassen.

## Java-Pakete {#java-packages}

![Registerkarte „Java-Pakete“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Dies bietet eine Suchaufforderung, mit der Sie nach Paketen suchen können, die im OSGi-System der Umgebung aktiv sind. An diesem Speicherort können Sie sehen, welches Bundle das Paket exportiert (oder bereitstellt), und Sie können sehen, welches Bundle das Paket importiert (oder verwendet). Sie können auch nach doppelten Paketen (dasselbe Paket, verschiedene Versionen) suchen, die in einigen Fällen Probleme verursachen können.
* **Anwendungsbeispiel:** Ein benutzerdefinierter Dienst, der den [dynamischen Klassenlader](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) verwendet, lädt eine Klasse, ohne eine Version anzugeben, die von mehreren Bundles mit unterschiedlichen Versionen exportiert wird, was zu einer unterschiedlichen Implementierung und einer Änderung des Verhaltens führt. Der Entwickler möchte sehen, welche Pakete sich in der Umgebung befinden, ohne das Funktionsmodell zu analysieren, sodass er nach diesem Paket sucht und alle exportierten Versionen sehen kann. Dadurch erhalten sie die Informationen, um einen besseren Versionsbereich einzugeben.

## Servlets {#servlets}

![Registerkarte „Servlets“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

* Dies bietet eine Suchaufforderung, in der Sie einen Pfad mit Selektoren und eine Erweiterung mit GET oder POST angeben können. Anschließend werden die Ergebnisse der Servlets in der Reihenfolge ihrer Bevorzugung bereitgestellt, die die Anfrage in Sling verarbeitet.
* **Anwendungsbeispiel:** Sie haben ein OSGi-Servlet, das für eine Anfrage aktiviert werden sollte, und drucken etwas in die Antwort, erhalten aber stattdessen eine leere Antwort. Sie müssen überprüfen, ob ein anderes Servlet aufgrund spezifischerer Selektoren, `resourceType`, Erweiterungen oder Rankings Vorrang vor Ihrem Servlet hat. Sie suchen nach dem erwarteten Pfad und finden heraus, dass ein anderes Servlet mit einem höheren Rang aktiv ist. Anschließend entscheiden Sie, ob Sie Ihr Servlet im Rang höher einstufen können, indem Sie beispielsweise Selektoren hinzufügen.

## Dienste {#services}

![Registerkarte „Services“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/services-dev-console.png)

* Ähnlich wie die OSGi-Komponentenansicht, aber basierend auf Services. Sie können schnell suchen, welche Services mit bestimmten Eigenschaften bereitgestellt werden.

## OSGi-Komponenten {#osgi-components}

![Registerkarte „OSGi-Komponenten“ in der Benutzeroberfläche der Entwicklungskonsole](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* Dadurch wird ein Überblick über die OSGi-Komponenten in den ausgewählten Umgebungstypen erstellt. Sie ermöglicht eine Volltextsuche.
* Sie können den Live-Status von OSGi-Komponenten in der Umgebung abrufen. Sie können sehen, welche Services erfüllt werden, das Bundle, das es bereitstellt, und den Aktivierungstyp (sofort oder verzögert).
* **Anwendungsbeispiel 1:** Als Entwickler möchten Sie überprüfen, ob eine Komponente, die mit einer Konfiguration aktiviert wird, in einer bestimmten Umgebung aktiv ist oder nicht, da Sie nicht das erwartete Verhalten zeigen. Sie können einfach die Komponente bei der Suche nachschlagen und überprüfen, ob die Komponente aktiv ist oder nicht.
* **Anwendungsbeispiel 2:** Sie möchten wissen, welche vorkonfigurierten Komponenten in der Umgebung vorhanden sind und welche Services erfüllt werden, um mehr über Adobe Experience Manager as a Cloud Service zu erfahren. Sie können sie in der Komponentenliste auschecken.

## Integrationen {#integrations}

![Registerkarte „Integrationen“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

* Ermöglicht Administratoren das Generieren, Umbenennen und Löschen von Service-Anmeldeinformationen und Entwickler-Token.

## Repository {#repository}

* Öffnet den [Repository-](/help/implementing/developing/tools/repository-browser.md).

## Status-Dumps/Abfragen {#status-dumps-queries}

![Registerkarte „Status-Dumps/Abfragen“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

* Gibt einen vollständigen Text- oder JSON-Dump des aktuellen Status von Bundles, Paketen, Konfigurationen, Services, Komponenten, Sling-Aufträgen oder Oak-Definitionen an.
* Dies kann besonders dann nützlich sein, wenn der Entwickler einen unerwarteten Status entdeckt hat und diesen für andere Entwickler kommunizieren oder dokumentieren möchte. Beim Herunterladen des Speicherauszugs erhalten Sie einen Schnappschuss des Status zur späteren Bezugnahme.

## Konfigurationen {#configurations}

![Registerkarte „Konfigurationen“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* Dadurch erhalten Sie eine durchsuchbare Liste von Konfigurationen, die in der Umgebung aktiv sind. Welche Eigenschaften von den Konfigurationen bereitgestellt werden, können Sie auf der Detailseite sehen.
* **Anwendungsbeispiel:** Ein Entwickler möchte sicherstellen, dass die von ihm angegebenen Konfigurationen tatsächlich in der Umgebung vorhanden sind. Wenn die Konfiguration fehlt, können sie das Funktionsmodell oder den Konfigurationsausführungsmodus oder -ordner überprüfen.

Bei Produktionsprogrammen wird der Zugriff auf die AEM as a Cloud Service Developer Console durch die Rolle „Cloud Manager – Entwicklerrolle“ in der Adobe Admin Console definiert, während bei Sandbox-Programmen die AEM as a Cloud Service Developer Console allen Benutzenden zur Verfügung steht, deren Produktprofil ihnen Zugriff auf AEM as a Cloud Service gewährt. Für alle Programme ist „Cloud Manager - Entwicklerrolle“ für Status-Dumps erforderlich, und der Repository Browser und die Benutzenden müssen auch in den Produktprofilen „AEM-Benutzer“ oder „AEM-Administrator“ sowohl für die Authoring- als auch für die Publishing-Services definiert sein, um Daten von beiden Services anzeigen zu können. Weitere Informationen zum Einrichten von Anwenderberechtigungen finden Sie in der [Dokumentation für Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=de).
