---
title: AEM AS A CLOUD SERVICE DEVELOPER CONSOLE - BETA
description: Informationen zu CRXDE Lite und AEM as a Cloud Service Developer Console.
feature: Developing
role: Admin, Architect, Developer
exl-id: 4b0fc3e9-b7c4-4c95-bd97-8b24e4d5cb3d
source-git-commit: 11c52f6782df3b608bedd4b120c145a7a80a0702
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 4%

---

# AEM as a Cloud Service Developer Console (Beta) {#developer-console}

>[!NOTE]
>
>In diesem Artikel wird ein überarbeitetes Erlebnis für die AEM Cloud Service-Developer Console beschrieben, die sich jetzt in der Beta-Phase befindet. Einige Kunden können darauf zugreifen, indem sie oben in der klassischen Benutzeroberfläche auf eine Schaltfläche klicken. Adobe begrüßt jedes Feedback von Ihnen, indem es es an `aemcs-new-devconsole-ui-beta@adobe.com` sendet. Weitere Informationen zur klassischen AEM Developer Console finden Sie [diesem Artikel](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

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

* Eine Übersicht über die OSGi-Bundles, die im ausgewählten Umgebungstyp bereitgestellt werden. Sie ermöglicht eine Volltextsuche.
* Es ist nützlich, Informationen über den tatsächlichen Status von Bundles in der Umgebung zu erhalten. Sie können Informationen wie exportierte Pakete, importierte Pakete, verwendete Services und mehr erhalten.
* Entwickler möchten die tatsächliche Umgebung überprüfen und überprüfen, ob das Bundle das tut, was sie erwarten.
* **Anwendungsbeispiel:** Ein Versionsbereich einer Abhängigkeit ist in Ihrem Bundle angegeben. Etwas läuft schief in der Abhängigkeit. Sie möchten überprüfen, welche Version der Abhängigkeit in Ihr Bundle verkabelt wird. Um dies zu überprüfen, navigieren Sie zu den Bundle-Details und verwenden Sie Bundles/Pakete importieren , um zu überprüfen, welche Bundle-Version oder Paketversion zur Laufzeit verwendet wird. Mit diesen Informationen können Sie den Versionsbereich Ihrer Maven-Abhängigkeiten anpassen oder Ihren Code anpassen.

## Java-Pakete {#java-packages}

![Registerkarte „Java-Pakete“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Eine Suchaufforderung, mit der Sie nach Paketen suchen können, die im OSGi-System der Umgebung aktiv sind. An diesem Speicherort können Sie sehen, welches Bundle das Paket exportiert (oder bereitstellt), und Sie können sehen, welches Bundle das Paket importiert (oder verwendet). Sie können auch nach doppelten Paketen (dasselbe Paket, verschiedene Versionen) suchen, die in einigen Fällen Probleme verursachen können.
* **Anwendungsfall:** Ein benutzerdefinierter Dienst, der den [dynamischen Klassenlader) verwendet, ](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) eine Klasse, ohne eine Version anzugeben. Da mehrere Bundles verschiedene Versionen exportieren, variiert die Implementierung, was zu Verhaltensänderungen führt. Der Entwickler möchte überprüfen, welche Pakete sich in der Umgebung befinden, ohne das Funktionsmodell zu analysieren. Sie suchen nach dem Paket und zeigen alle exportierten Versionen an. Diese Fähigkeit gibt ihnen die Informationen, um einen besseren Versionsbereich einzugeben.

## Servlets {#servlets}

![Registerkarte „Servlets“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

* Eine Suchaufforderung, in der Sie einen Pfad mit Selektoren und eine Erweiterung mit GET oder POST angeben können. Anschließend werden die Ergebnisse der Servlets in der Reihenfolge ihrer Präferenz bereitgestellt, die die Anfrage in Sling verarbeitet.
* **Anwendungsbeispiel:** Sie verfügen über ein OSGi-Servlet, das bei einer Anfrage aktiviert und die Ausgabe in die Antwort druckt. Anstelle der erwarteten Ausgabe gibt die Antwort jedoch leer zurück. Sie müssen überprüfen, ob ein anderes Servlet aufgrund spezifischerer Selektoren, `resourceType`, Erweiterungen oder Rankings Vorrang vor Ihrem Servlet hat. Sie suchen nach dem erwarteten Pfad und finden heraus, dass ein anderes Servlet mit einem höheren Rang aktiv ist. Anschließend entscheiden Sie, ob Sie Ihr Servlet im Rang höher einstufen können, indem Sie beispielsweise Selektoren hinzufügen.

## Dienste {#services}

![Registerkarte „Services“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/services-dev-console.png)

* Ähnlich wie die OSGi-Komponentenansicht, aber basierend auf Services. Sie können schnell suchen, welche Services mit bestimmten Eigenschaften bereitgestellt werden.

## OSGi-Komponenten {#osgi-components}

![Registerkarte „OSGi-Komponenten“ in der Benutzeroberfläche der Entwicklungskonsole](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* Eine Übersicht über die OSGi-Komponenten, die im ausgewählten Umgebungstyp vorhanden sind. Sie ermöglicht eine Volltextsuche.
* Sie können den Live-Status von OSGi-Komponenten in der Umgebung abrufen. Sie können sehen, welche Services erfüllt werden, das Bundle, das es bereitstellt, und den Aktivierungstyp (sofort oder verzögert).
* **Anwendungsbeispiel 1:** Als Entwicklungsperson müssen Sie überprüfen, ob eine mit einer Konfiguration aktivierte Komponente in einer bestimmten Umgebung aktiv ist. Der Grund dafür ist, dass das erwartete Verhalten nicht auftritt. Sie können einfach die Komponente bei der Suche nachschlagen und überprüfen, ob die Komponente aktiv ist oder nicht.
* **Anwendungsbeispiel 2:** Sie möchten sehen, welche vordefinierten Komponenten in der Umgebung verfügbar sind, und die unterstützten Services ermitteln. Auf diese Weise erfahren Sie mehr über Adobe Experience Manager as a Cloud Service. Sie können sie in der Komponentenliste auschecken.

## Integrationen {#integrations}

![Registerkarte „Integrationen“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

* Admins haben die Möglichkeit, Service-Anmeldeinformationen und Entwickler-Token zu generieren, umzubenennen und zu löschen.

## Repository {#repository}

* Öffnet den [Repository-](/help/implementing/developing/tools/repository-browser.md).

## Status-Dumps/Abfragen {#status-dumps-queries}

![Registerkarte „Status-Dumps/Abfragen“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

* Ein Volltext- oder JSON-Dump des aktuellen Status von Bundles, Paketen, Konfigurationen, Services, Komponenten, Sling-Aufträgen oder Oak-Definitionen.
* Dies ist besonders nützlich, wenn der Entwickler einen unerwarteten Status entdeckt hat und diesen Status für andere Entwickler kommunizieren oder dokumentieren möchte. Beim Herunterladen des Speicherauszugs erhalten Sie einen Schnappschuss des Status zur späteren Bezugnahme.

## Konfigurationen {#configurations}

![Registerkarte „Konfigurationen“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* Eine durchsuchbare Liste der Konfigurationen, die in der Umgebung aktiv sind. Welche Eigenschaften von den Konfigurationen bereitgestellt werden, können Sie auf der Detailseite sehen.
* **Anwendungsbeispiel:** Ein Entwickler möchte sicherstellen, dass die angegebenen Konfigurationen tatsächlich in der Umgebung vorhanden sind. Wenn die Konfiguration fehlt, können sie das Funktionsmodell oder den Konfigurationsausführungsmodus oder -ordner überprüfen.

Bei Produktionsprogrammen steuert die &quot;Cloud Manager - Entwicklerrolle“ in der Adobe Admin Console den Zugriff auf die AEM as a Cloud Service-Developer Console. Bei Sandbox-Programmen kann jeder Benutzer mit einem Produktprofil, das AEM-Zugriff gewährt, die Developer Console verwenden. Für alle Programme ist die &quot;Cloud Manager - Entwicklerrolle“ für Status-Dumps und den Zugriff auf den Repository-Browser erforderlich. Um Daten sowohl aus dem Autoren- als auch aus dem Veröffentlichungs-Service anzeigen zu können, müssen Benutzende in beiden Services auch dem Produktprofil AEM-Benutzende oder AEM-Administrierende zugewiesen sein.

Weitere Informationen zum Einrichten von Anwenderberechtigungen finden Sie in der [Dokumentation für Cloud Manager](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/users-and-roles).

