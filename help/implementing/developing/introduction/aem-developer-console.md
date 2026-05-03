---
title: AEM as a Cloud Service Developer Console – Beta
description: Erfahren Sie mehr über AEM as a Cloud Service Developer Console und die zugehörigen schreibgeschützten Tools zum Debugging von Cloud-Umgebungen.
feature: Developing
role: Admin, Developer
exl-id: 4b0fc3e9-b7c4-4c95-bd97-8b24e4d5cb3d
source-git-commit: 51c14ba3c15e0136911003752253d21ed673a0eb
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 15%

---


# AEM as a Cloud Service Developer Console (Beta) {#developer-console}

AEM as a Cloud Service Developer Console enthält eine Reihe schreibgeschützter Tools zum Debugging von Cloud-Umgebungen. Auf ihn kann über einen Link pro Umgebung in Cloud Manager zugegriffen werden. Er bietet Funktionen zum Anzeigen von Bundles, OSGi-Einstellungen, Services und Servlets und mehr.

>[!NOTE]
>
>In diesem Artikel wird ein überarbeitetes Erlebnis für die AEM Cloud Service Developer Console beschrieben, die sich jetzt in der Beta-Phase befindet.
>
>* Nur eine begrenzte Benutzergruppe kann über eine Schaltfläche oben in der aktuellen Developer Console auf die neue Konsole zugreifen.
>* Adobe begrüßt jedes Feedback, das Sie an `aemcs-new-devconsole-ui-beta@adobe.com` senden können.
>* Die Dokumentation zur aktuellen AEM Developer Console finden Sie unter [diesem Artikel.](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console)
>* Der AEM as a Cloud Service Developer Console sollte nicht mit dem ähnlich benannten [*Adobe Developer Console verwechselt*.](https://developer.adobe.com/developer-console/)

>[!TIP]
>
>Die Developer Console ist schreibgeschützt. Wenn Sie an der lokalen Entwicklung mit der SDK arbeiten und OSGi-Einstellungen oder Repository-Inhalte ändern müssen, können Sie Folgendes verwenden:
>
>* [CRXDE Lite](/help/implementing/developing/tools/crxde.md)

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

## Voraussetzungen {#prerequisites}

Auf die Developer Console können nur Benutzer mit bestimmten Rollen in bestimmten Programmen zugreifen.

* Bei Produktionsprogrammen steuert die &quot;Cloud Manager - Entwicklerrolle“ in der Adobe Admin Console den Zugriff auf die Developer Console.
* Bei Sandbox-Programmen können alle Benutzerinnen und Benutzer mit einem Produktprofil, das AEM-Zugriff gewährt, die Developer Console verwenden.
* Für alle Programme ist die „Cloud Manager – Entwicklerrolle“ für Status-Dumps und den Zugriff auf den Repository-Browser erforderlich.

Um Daten sowohl aus dem Autoren- als auch aus dem Veröffentlichungs-Service anzeigen zu können, müssen Benutzende in beiden Services auch den Produktprofilen &quot;AEM-Benutzende“ oder &quot;AEM-Administrierende“ zugewiesen sein.

Weitere Informationen zum Einrichten von Benutzerberechtigungen finden Sie in der [Dokumentation zu Cloud Manager.](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/users-and-roles)

## Registerkarte OSGi-Pakete {#osgi-bundles}

Die Registerkarte **OSGi** Bundles“ bietet einen Überblick über die in der ausgewählten Umgebung bereitgestellten OSGi-Bundles und eine Volltextsuche.

![Bildschirm „Neue OSGi-Bundles“ in Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* Die Registerkarte enthält Informationen zum tatsächlichen Status von Bundles in der Umgebung, z. B. exportierte Pakete, importierte Pakete, verwendete Services und mehr.
* Es empfiehlt sich, den Status von Bundles zu überprüfen, um festzustellen, ob das Bundle das tut, was erwartet wird.

**Anwendungsbeispiel:** Angenommen, Sie geben einen Versionsbereich für eine Abhängigkeit in Ihrem Bundle an. Es gibt jedoch ein Problem mit der Abhängigkeit, und Sie müssen überprüfen, welche Version der Abhängigkeit vom Bundle tatsächlich verwendet wird. Öffnen Sie zum Überprüfen die Developer Console und klicken Sie auf der Registerkarte **OSGi-Bundles** auf einen Bundle-Namen, um auf die Bundle-Details zuzugreifen, und verwenden Sie das Akkordeon **Bundles importieren**, um zu überprüfen, welche Bundle-Version oder Paketversion zur Laufzeit verwendet wird. Mit diesen Informationen können Sie den Versionsbereich Ihrer Maven-Abhängigkeiten anpassen oder Ihren Code ändern.

## Registerkarte Java-Pakete {#java-packages}

Die **Java-Pakete** bietet ein Suchfeld, um nach Paketen zu suchen, die im OSGi-System der Umgebung aktiv sind.

![Registerkarte „Java-Pakete“ in der Developer Console-Benutzeroberfläche](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Sie können sehen, welches Bundle das Paket exportiert (oder bereitstellt), und Sie können sehen, welche Bundles das Paket importieren (oder verwenden).
* Sie können auch nach doppelten Paketen (dasselbe Paket, verschiedene Versionen) suchen, die in einigen Fällen Probleme verursachen können.

**Anwendungsbeispiel:** Angenommen, ein benutzerdefinierter Dienst, der den [dynamischen Klassenlader) verwendet, &#x200B;](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) eine Klasse, ohne eine Version anzugeben. Da mehrere Bundles verschiedene Versionen exportieren, variiert die Implementierung, was zu Verhaltensänderungen führt. Sie möchten überprüfen, welche Pakete sich in der Umgebung befinden, ohne das Funktionsmodell zu analysieren. Auf dieser Registerkarte können Sie nach dem Paket suchen und alle exportierten Versionen anzeigen. Anschließend können Sie einen besseren Versionsbereich verwenden.

## Registerkarte „Konfigurationen“ {#configurations}

Die **Konfigurationen** bietet eine durchsuchbare Liste von Konfigurationen, die in der Umgebung aktiv sind. Sie können sehen, welche Eigenschaften von den einzelnen Konfigurationen bereitgestellt werden, indem Sie darauf klicken und die Detailseite anzeigen.

![Registerkarte „Konfigurationen“ in der Developer Console-Benutzeroberfläche](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* **Anwendungsbeispiel** Angenommen, Sie möchten sicherstellen, dass die angegebenen Konfigurationen tatsächlich in der Umgebung vorhanden sind. Wenn Sie in der Konsole **Registerkarte** Konfigurationen“ suchen und die Konfiguration fehlt, können Sie das Funktionsmodell, den Konfigurationsausführungsmodus oder den Ordner überprüfen.

## Registerkarte Servlets {#servlets}

Die Registerkarte **Servlets** bietet ein Suchfeld, in dem Sie einen Pfad mit Selektoren und eine Erweiterung mit GET oder POST angeben können. Anschließend wird eine Liste von Servlets in der Reihenfolge ihrer Präferenz bereitgestellt, die die Anfrage in Sling verarbeitet.

![Registerkarte „Servlets“ in der Developer Console-Benutzeroberfläche](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

**Anwendungsbeispiel:** Angenommen, Sie verfügen über ein OSGi-Servlet, das bei einer Anfrage aktiviert und die Ausgabe in die Antwort druckt. Anstelle der erwarteten Ausgabe erhalten Sie jedoch eine leere Antwort. Sie müssen überprüfen, ob ein anderes Servlet aufgrund spezifischerer Selektoren, `resourceType`, Erweiterungen oder Rankings Vorrang vor Ihrem Servlet hat. Sie suchen nach dem erwarteten Pfad und finden ein anderes Servlet, das mit einem höheren Rang aktiv ist. Sie können dann entscheiden, ob Sie den Rang Ihres Servlets erhöhen können, indem Sie beispielsweise Selektoren hinzufügen.

## Registerkarte „Services“ {#services}

Die Registerkarte **Services** bietet einen Überblick über die in der ausgewählten Umgebung vorhandenen Services und eine Volltextsuche.

![Registerkarte „Services“ in der Developer Console-Benutzeroberfläche](/help/implementing/developing/introduction/assets/services-dev-console.png)

Klicken Sie auf einen Service, um dessen Details anzuzeigen.

## Registerkarte OSGi-Komponenten {#osgi-components}

Die Registerkarte **OSGi** Komponenten“ bietet einen Überblick über die OSGi-Komponenten, die im ausgewählten Umgebungstyp vorhanden sind, und bietet eine Volltextsuche. Sie können den Live-Status von OSGi-Komponenten in der Umgebung und die entsprechenden Services, das bereitstellende Bundle und den Aktivierungstyp (sofort oder verzögert) sehen.

![Registerkarte „OSGi-Komponenten“ in der Developer Console-Benutzeroberfläche](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* **Anwendungsbeispiel 1:** Angenommen, Sie müssen überprüfen, ob eine mit einer Konfiguration aktivierte Komponente in einer bestimmten Umgebung aktiv ist, da unerwartetes Verhalten auftritt. Sie können einfach die Komponente über die Suche abrufen und überprüfen, ob die Komponente aktiv ist oder nicht.
* **Anwendungsbeispiel 2:** Angenommen, Sie möchten sehen, welche vordefinierten Komponenten in der Umgebung verfügbar sind, und die unterstützten Services identifizieren, um mehr über Adobe Experience Manager as a Cloud Service zu erfahren. Sie können die Komponenten in der Komponentenliste überprüfen.

## Registerkarte Integrationen {#integrations}

Auf **Registerkarte** Integrationen“ können Administratoren Service-Anmeldeinformationen und Entwickler-Token generieren, umbenennen und löschen.

![Registerkarte „Integrationen“ in der Developer Console-Benutzeroberfläche](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

## Registerkarte „Repository“ {#repository}

Die Registerkarte **Repository** öffnet den [Repository-Browser.](/help/implementing/developing/tools/repository-browser.md)

## Registerkarte Status-Dumps/Abfragen {#status-dumps-queries}

Auf **Registerkarte „Status-Dumps/**&quot; können Sie einen Volltext- oder JSON-Dump des aktuellen Status von Bundles, Paketen, Konfigurationen, Services, Komponenten, Sling-Aufträgen oder Oak-Definitionen herunterladen.

![Registerkarte „Status-Dumps/Abfragen“ in der Developer Console-Benutzeroberfläche](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

Sie können auch das Tool [Abfrageleistung“ &#x200B;](/help/operations/query-and-indexing-best-practices.md#query-performance-tool)

* **Anwendungsbeispiel:** Diese Registerkarte ist besonders nützlich, wenn Sie auf einen unerwarteten Status stoßen und ihn für andere Entwickler kommunizieren oder dokumentieren möchten. Durch Herunterladen des Speicher-Dumps erhalten Sie einen Status-Schnappschuss zur künftigen Referenz.
