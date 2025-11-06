---
title: AEM as a Cloud Service Developer Console – Beta
description: Weitere Informationen zu CRX/DE Lite und AEM as a Cloud Service Developer Console
feature: Developing
role: Admin, Developer
exl-id: 4b0fc3e9-b7c4-4c95-bd97-8b24e4d5cb3d
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 100%

---

# AEM as a Cloud Service Developer Console (Beta) {#developer-console}

>[!NOTE]
>
>In diesem Artikel wird ein überarbeitetes Erlebnis für die AEM Cloud Service Developer Console beschrieben, die sich jetzt in der Beta-Phase befindet. Einige Kundinnen und Kunden können darauf zugreifen, indem sie oben in der klassischen Benutzeroberfläche auf eine Schaltfläche klicken. Adobe freut sich über jedes Feedback von Ihnen, das Sie an `aemcs-new-devconsole-ui-beta@adobe.com` senden. Informationen zur klassischen AEM Developer Console finden Sie [in diesem Artikel](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

Die AEM as a Cloud Service Developer Console enthält eine Reihe von Tools zum Debugging in Cloud-Umgebungen. Der Zugriff darauf erfolgt in Cloud Manager über einen Link in der jeweiligen Umgebung.

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

Entwicklerinnen und Entwickler können auf die unten beschriebenen Funktionen zugreifen:

## OSGi-Bundles {#osgi-bundles}

![Bildschirm „Neue OSGi-Bundles“ in der Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* Eine Übersicht über die OSGi-Bundles, die im ausgewählten Umgebungstyp bereitgestellt werden. Sie unterstützt eine Volltextsuche.
* Dies ist hilfreich, um Informationen über den tatsächlichen Status von Bundles in der Umgebung zu erhalten. Sie können Informationen wie exportierte Pakete, importierte Pakete, verwendete Dienste und mehr erhalten.
* Entwicklerinnen und Entwickler möchten die tatsächliche Umgebung verifizieren und prüfen, ob das Bundle wie erwartet funktioniert.
* **Anwendungsbeispiel:** In Ihrem Bundle ist ein Versionsbereich einer Abhängigkeit angegeben. Etwas läuft schief in der Abhängigkeit. Sie möchten überprüfen, welche Version der Abhängigkeit mit Ihrem Bundle verknüpft ist. Hierfür navigieren Sie zu den Bundle-Details und prüfen bei den importierten Bundles/Paketen, welche Bundle-Version oder Paketversion zur Laufzeit verwendet wird. Mit diesen Informationen können Sie den Versionsbereich Ihrer Maven-Abhängigkeiten anpassen oder Ihren Code ändern.

## Java-Pakete {#java-packages}

![Registerkarte „Java-Pakete“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Ein Such-Prompt, mit dem Sie nach Paketen suchen können, die im OSGi-System der Umgebung aktiv sind. Hier können Sie sehen, welches Bundle das Paket exportiert (oder bereitstellt) und welches Bundle das Paket importiert (oder verwendet). Sie können auch nach doppelten Paketen (dasselbe Paket, verschiedene Versionen) suchen, die in einigen Fällen Probleme verursachen können.
* **Anwendungsbeispiel:** Ein benutzerdefinierter Dienst, der das [dynamische Klassenladeprogramm](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) verwendet, lädt eine Klasse ohne Versionsangabe. Da mehrere Bundles verschiedene Versionen exportieren, variiert die Implementierung, was zu Verhaltensänderungen führt. Das Entwicklungs-Team möchte überprüfen, welche Pakete sich in der Umgebung befinden, ohne das Funktionsmodell zu analysieren. Sie suchen nach dem Paket und zeigen alle exportierten Versionen an. Dadurch erhalten sie die benötigten Informationen, um einen besseren Versionsbereich einzugeben.

## Servlets {#servlets}

![Registerkarte „Servlets“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

* Ein Such-Prompt, in den Sie einen Pfad mit Selektoren und eine Erweiterung mit GET oder POST angeben können. Anschließend werden die Ergebnisse der Servlets in der Reihenfolge ihrer Präferenz bereitgestellt, die die Anfrage in Sling verarbeitet.
* **Anwendungsbeispiel:** Sie verfügen über ein OSGi-Servlet, das bei einer Anfrage aktiviert wird und den Output in der Antwort ausgibt. Anstelle des erwarteten Outputs wird jedoch eine leere Antwort zurückgegeben. Sie müssen überprüfen, ob ein anderes Servlet aufgrund von spezifischeren Selektoren, `resourceType`, Erweiterungen oder Rankings Vorrang vor Ihrem Servlet hat. Sie suchen nach dem erwarteten Pfad und finden heraus, dass ein anderes Servlet mit einem höheren Rang aktiv ist. Anschließend entscheiden Sie, ob Sie Ihr Servlet im Rang höher einstufen können, indem Sie beispielsweise Selektoren hinzufügen.

## Dienste {#services}

![Registerkarte „Dienste“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/services-dev-console.png)

* Ähnlich wie die Ansicht „OSGi-Komponenten“, aber basierend auf Diensten. Sie können schnell suchen, welche Dienste mit bestimmten Eigenschaften bereitgestellt werden.

## OSGi-Komponenten {#osgi-components}

![Registerkarte „OSGi-Komponenten“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* Eine Übersicht über die OSGi-Komponenten, die im ausgewählten Umgebungstyp vorhanden sind. Sie unterstützt eine Volltextsuche.
* Sie können den Live-Status von OSGi-Komponenten in der Umgebung abrufen. Sie können die bedienten Dienste das bereitstellende Bundle und den Aktivierungstyp (sofort oder verzögert) sehen.
* **Anwendungsbeispiel 1:** Als Mitglied des Entwicklungs-Teams müssen Sie überprüfen, ob eine mit einer Konfiguration aktivierte Komponente in einer bestimmten Umgebung aktiv ist. Grund dafür ist, dass das erwartete Verhalten nicht eintritt. Sie können einfach die Komponente über die Suche abrufen und überprüfen, ob die Komponente aktiv ist oder nicht.
* **Anwendungsbeispiel 2:** Sie möchten sehen, welche vorkonfigurierten Komponenten in der Umgebung verfügbar sind, und die unterstützten Dienste ermitteln. Auf diese Weise erfahren Sie mehr über Adobe Experience Manager as a Cloud Service. Sie können sie in der Komponentenliste prüfen.

## Integrationen {#integrations}

![Registerkarte „Integrationen“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

* Admins haben die Möglichkeit, Dienst-Anmeldeinformationen und Entwickler-Token zu generieren, umzubenennen und zu löschen.

## Repository {#repository}

* Öffnet den [Repository-Browser](/help/implementing/developing/tools/repository-browser.md).

## Status-Dumps/Abfragen {#status-dumps-queries}

![Registerkarte „Status-Dumps/Abfragen“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

* Ein Volltext- oder JSON-Dump des aktuellen Status von Bundles, Paketen, Konfigurationen, Diensten, Komponenten, Sling-Aufträgen oder Oak-Definitionen.
* Dies ist besonders nützlich, wenn das Entwicklungs-Team einen unerwarteten Status entdeckt hat und diesen Status für andere Entwickelnde kommunizieren oder dokumentieren möchte. Durch Herunterladen des Speicher-Dumps erhalten Sie einen Status-Schnappschuss zur künftigen Referenz.

## Konfigurationen {#configurations}

![Registerkarte „Konfigurationen“ in der Benutzeroberfläche der Developer Console](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* Eine durchsuchbare Liste der Konfigurationen, die in der Umgebung aktiv sind. Welche Eigenschaften durch die Konfigurationen bereitgestellt werden, können Sie auf der Detailseite sehen.
* **Anwendungsbeispiel:** Ein Mitglied des Entwicklungs-Teams möchte sicherstellen, dass die angegebenen Konfigurationen tatsächlich in der Umgebung vorhanden sind. Wenn die Konfiguration fehlt, kann es das Funktionsmodell oder den Konfigurationsausführungsmodus oder -ordner überprüfen.

Bei Produktionsprogrammen steuert die „Cloud Manager – Entwicklerrolle“ in der Adobe Admin Console den Zugriff auf die AEM as a Cloud Service-Developer Console. Bei Sandbox-Programmen können alle Benutzerinnen und Benutzer mit einem Produktprofil, das AEM-Zugriff gewährt, die Developer Console verwenden. Für alle Programme ist die „Cloud Manager – Entwicklerrolle“ für Status-Dumps und den Zugriff auf den Repository-Browser erforderlich. Um Daten sowohl aus dem Autoren- als auch aus dem Veröffentlichungsdienst anzeigen zu können, müssen Benutzende in beiden Diensten auch dem Produktprofil AEM-Benutzende oder AEM-Admins zugewiesen sein.

Weitere Informationen zum Einrichten von Anwenderberechtigungen finden Sie in der [Dokumentation für Cloud Manager](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/users-and-roles).

