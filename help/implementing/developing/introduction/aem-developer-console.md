---
title: AEM as a Cloud Service Developer Console (Beta)
description: Informationen zu CRX/DE Lite und AEM as a Cloud Service Developer Console
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 16379d9cb7cdf876502205c12a233a95b410a67a
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 27%

---


# AEM as a Cloud Service Developer Console (Beta) {#developer-console}

>[!NOTE]
>
>In diesem Artikel wird ein überarbeitetes Erlebnis für die AEM Cloud Service Developer Console beschrieben, die sich jetzt in der Beta-Phase befindet und von einigen Kunden durch Klicken auf eine Schaltfläche oben in der klassischen Benutzeroberfläche zur Verfügung gestellt wird. Wir freuen uns über jedes Feedback, das Sie an `aemcs-new-devconsole-ui-beta@adobe.com` senden können. Informationen zum klassischen AEM Developer Console finden Sie in [diesem Artikel](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

## Entwicklungs-Tools für AEM as a Cloud Service {#aem-as-a-cloud-service-development-tools}

>[!NOTE]
>Die AEM as a Cloud Service Developer Console sollte nicht mit der ähnlich benannten [*Adobe Developer Console*](https://developer.adobe.com/developer-console/) verwechselt werden.
>

Kunden können in der Entwicklungsumgebung der Autorenebene auf CRXDE Lite zugreifen, jedoch nicht in der Staging- oder Produktionsumgebung. Das unveränderliche Repository (`/libs`, `/apps`) kann zur Laufzeit nicht in beschrieben werden. Ein entsprechender Versuch führt zu Fehlern.

Stattdessen kann der Repository-Browser von der AEM as a Cloud Service Developer Console aus gestartet werden und bietet eine schreibgeschützte Ansicht des Repositorys für alle Umgebungen auf den Ebenen „Autor“, „Veröffentlichung“ und „Vorschau“. Weitere Informationen finden Sie im [Repository-Browser](/help/implementing/developing/tools/repository-browser.md).

Eine Reihe von Tools zum Debuggen von AEM as a Cloud Service-Entwicklungsumgebungen sind in der AEM as a Cloud Service Developer Console für RDE-, Entwicklungs-, Staging- und Produktionsumgebungen verfügbar. Die URL kann durch Anpassen der Author- und Publish-Service-URLs wie folgt festgelegt werden:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als Abkürzung kann der folgende Cloud Manager CLI-Befehl verwendet werden, um die AEM als Cloud Service Developer Console auf der Grundlage eines unten beschriebenen Umgebungsparameters zu starten:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Weitere Informationen finden Sie in den [Versionsinformationen](/help/release-notes/home.md).

Entwickler können Statusinformationen generieren und verschiedene Ressourcen auflösen.

Wie unten dargestellt, umfassen die verfügbaren Statusinformationen den Status von Paketen, Komponenten, OSGi-Konfigurationen, Oak-Indizes, OSGi-Services und Sling-Jobs.

### OSGi-Bundles {#osgi-bundles}

![Neuer OSGi-Paketbildschirm in der Entwicklerkonsole](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* Dadurch erhalten Sie eine Übersicht über OSGI-Bundles, die auf dem ausgewählten Umgebungstyp bereitgestellt werden. Sie ermöglicht eine Volltextsuche.
* Es ist nützlich, Informationen über den tatsächlichen Zustand von Bundles in der Umgebung zu erhalten. Sie erhalten Informationen wie exportierte Packages, importierte Packages, verwendete Dienste und mehr.
* Entwickler möchten die tatsächliche Umgebung überprüfen und überprüfen, ob das Bundle das tut, was sie erwarten.
* **Anwendungsbeispiel:** Ein Versionsbereich einer Abhängigkeit wird in Ihrem Bundle angegeben. In der Abhängigkeit läuft etwas schief. Sie möchten überprüfen, welche Version der Abhängigkeit in Ihrem Bundle verdrahtet wird. Um dies zu überprüfen, gehen Sie zu den Bundle-Details und verwenden Sie zum Importieren von Bundles/Paketen , um zu überprüfen, welche Bundle-Version oder Paketversion zur Laufzeit verwendet wird, um herauszufinden. Mit diesen Informationen können Sie Ihren Maven-Abhängigkeitsversionsbereich anpassen oder Ihren Code anpassen.

### Java-Pakete {#java-packages}

![Registerkarte &quot;Java-Pakete&quot;in der Benutzeroberfläche der Entwicklungskonsole](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Dadurch erhalten Sie eine Suchaufforderung, mit der Sie Pakete suchen können, die im OSGi-System der Umgebung aktiv sind. In diesem Verzeichnis können Sie sehen, welches Paket das Paket exportiert (oder bereitstellt), und Sie können sehen, welches Paket das Paket importiert (oder verwendet). Sie können auch nach doppelten Paketen (gleiches Paket, verschiedene Versionen) suchen, was in einigen Fällen Probleme verursachen kann.
* **Anwendungsbeispiel:** Ein benutzerdefinierter Dienst, der den [dynamischen Klassenlader](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) verwendet, lädt eine Klasse, ohne eine Version anzugeben. Diese wird von mehreren Bundles mit verschiedenen Versionen exportiert, wodurch die Implementierung anders ist und sich das Verhalten ändert. Der Entwickler möchte sehen, welche Pakete sich in der Umgebung befinden, ohne das Funktionsmodell zu analysieren. Daher sucht er nach diesem Paket und sieht alle exportierten Versionen. Dadurch erhalten sie Informationen, um einen besseren Versionsbereich einzugeben.

### Servlets {#servlets}

Registerkarte &quot;![Servlets&quot;in der Benutzeroberfläche der Entwicklungskonsole](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

* Dies bietet eine Suchaufforderung, an der Sie einen Pfad mit Selektoren und eine Erweiterung mit GET oder POST angeben können. Anschließend werden Ergebnisse von Servlets in der Reihenfolge ihrer Voreinstellung bereitgestellt, die die Anfrage in Sling verarbeiten.
* **Anwendungsbeispiel:** Sie haben ein OSGi-Servlet, das bei einer Anfrage aktiviert werden soll und etwas an die Antwort drucken soll, aber stattdessen erhalten Sie eine leere Antwort. Sie müssen überprüfen, ob ein anderes Servlet aufgrund spezifischerer Selektoren, `resourceType`, Erweiterungen oder Rangfolge Vorrang vor Ihrem Servlet hat. Sie suchen nach dem erwarteten Pfad und stellen fest, dass ein anderes Servlet mit einem höheren Rang aktiv ist. Dann entscheiden Sie, ob Sie Ihr Servlet oben im Rang platzieren können, indem Sie beispielsweise Selektoren hinzufügen.

### Dienste {#services}

![Registerkarte &quot;Dienste&quot;in der Benutzeroberfläche der Entwicklerkonsole](/help/implementing/developing/introduction/assets/services-dev-console.png)

* Ähnlich wie die Ansicht &quot;OSGi Components&quot;, jedoch basierend auf Diensten. Sie können schnell suchen, welche Dienste mit bestimmten Eigenschaften bereitgestellt werden.

### OSGi-Komponenten {#osgi-components}

![Registerkarte &quot;OSGi-Komponenten&quot;in der Benutzeroberfläche der Entwicklungskonsole](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* Dadurch erhalten Sie eine Übersicht über die OSGi-Komponenten, die im ausgewählten Umgebungstyp vorhanden sind. Sie ermöglicht eine Volltextsuche.
* Sie können den Live-Status von OSGi-Komponenten in der Umgebung abrufen. Sie können sehen, welche Dienste sie erfüllt, das bereitgestellte Bundle und den Aktivierungstyp (unmittelbar oder verzögert).
* **Anwendungsbeispiel 1:** Als Entwickler möchten Sie überprüfen, ob eine mit einer Konfiguration aktivierte Komponente in einer bestimmten Umgebung aktiv ist oder nicht, da Sie nicht das erwartete Verhalten erhalten. Sie suchen einfach die Komponente in der Suche und überprüfen, ob die Komponente aktiv ist oder nicht.
* **Anwendungsbeispiel 2:** Sie möchten sehen, welche nativen Komponenten in der Umgebung vorhanden sind und welche Dienste sie erfüllen, um mehr über Adobe Experience Manager as a Cloud Service zu erfahren. Sie können sie in der Komponentenliste auschecken.

### Integrationen {#integrations}

![Registerkarte &quot;Integrationen&quot;in der Benutzeroberfläche der Entwicklungskonsole](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

* Bietet Administratoren die Möglichkeit, Service-Anmeldeinformationen und Entwickler-Token zu generieren, umzubenennen und zu löschen.

### Repository {#repository}

* Öffnet den [Repository-Browser](/help/implementing/developing/tools/repository-browser.md).

### Status-Dumps/Abfragen {#status-dumps-queries}

![Tab Statusdups/Abfragen in der Benutzeroberfläche der Entwicklerkonsole](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

* Gibt einen Volltext- oder JSON-Dump des aktuellen Status von Bundles, Paketen, Konfigurationen, Diensten, Komponenten, Sling-Aufträgen oder Oak-Definitionen.
* Dies kann besonders dann nützlich sein, wenn der Entwickler einen unerwarteten Status entdeckt hat und dies für andere Entwickler kommunizieren oder dokumentieren möchte. Durch das Herunterladen des Dump erhalten Sie eine Momentaufnahme des Status, der später referenziert werden kann.

### Konfigurationen {#configurations}

![Registerkarte &quot;Konfigurationen&quot;in der Benutzeroberfläche der Entwicklungskonsole](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* Auf diese Weise erhalten Sie eine durchsuchbare Liste von Konfigurationen, die in der Umgebung aktiv sind. Auf der Detailseite können Sie sehen, welche Eigenschaften von den Konfigurationen bereitgestellt werden.
* **Anwendungsbeispiel:** Ein Entwickler möchte sicherstellen, dass die angegebenen Konfigurationen tatsächlich in der Umgebung vorhanden sind. Wenn die Konfiguration fehlt, können sie das Funktionsmodell oder den Konfigurations-Ausführungsmodus oder -ordner überprüfen.

Bei Produktionsprogrammen wird der Zugriff auf die AEM as a Cloud Service Developer Console durch die Rolle „Cloud Manager – Entwicklerrolle“ in der Adobe Admin Console definiert, während bei Sandbox-Programmen die AEM as a Cloud Service Developer Console allen Benutzenden zur Verfügung steht, deren Produktprofil ihnen Zugriff auf AEM as a Cloud Service gewährt. Für alle Programme ist „Cloud Manager - Entwicklerrolle“ für Status-Dumps erforderlich, und der Repository Browser und die Benutzenden müssen auch in den Produktprofilen „AEM-Benutzer“ oder „AEM-Administrator“ sowohl für die Authoring- als auch für die Publishing-Services definiert sein, um Daten von beiden Services anzeigen zu können. Weitere Informationen zum Einrichten von Anwenderberechtigungen finden Sie in der [Dokumentation für Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=de).