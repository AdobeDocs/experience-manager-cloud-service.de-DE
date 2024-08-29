---
title: Versionshinweise für Version 2024.7.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2024.7.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: 2edaca5637c735645e2b761377b9681d9b48daa1
workflow-type: tm+mt
source-wordcount: '1518'
ht-degree: 100%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2024.7.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2024.7.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2022 oder 2023 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.7.0) war der 25. Juli 2024. Die nächste Version (2024.8.0) ist für den 29. August 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2024.7.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version Juli 2024:

>[!VIDEO](https://video.tv.adobe.com/v/3431707?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in Experience Manager Sites {#new-feature-sites}

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzen Sie GenAI über die neue Funktion [Varianten generieren](/help/generative-ai/generate-variations.md) von AEM, die jetzt in Cloud Service verfügbar ist. „Varianten generieren“ hilft Ihnen bei der Erstellung und Skalierung von Inhalten durch den Einsatz generativer KI. Wenden Sie sich an Ihr Adobe-Accountteam, um sich für das Programm zu erkundigen.

**Durchsuchen von Assets in der Inhaltsfragmentkonsole**

Inhaltsautorinnen und -autoren können jetzt Bilder und andere Assets durchsuchen, anzeigen und bearbeiten, ohne die Inhaltsfragmentkonsole verlassen zu müssen.

![Durchsuchen von Assets](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Möchten Sie die Funktion ausprobieren und Feedback geben? Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an aemcs-headless-adopter@adobe.com senden, um am Early-Adopter-Programm teilzunehmen.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Hochladen von Assets mit dem Asset-Wähler**

Der Asset-Wähler bietet Inhaltsautorinnen und Inhaltsautoren jetzt die Möglichkeit, endgültige Assets direkt aus dem Wähler hochzuladen. Dies erfolgt entweder durch Ziehen der Assets oder durch Durchsuchen des lokalen Dateisystems. Dadurch können Sie endgültige Assets aus der Anwendung Ihrer Wahl in das DAM hochladen.

### Neue Funktionen in der Assets-Ansicht {#assets-view-new-features}

**Integration der Inhaltsurhebernachweise**

Experience Manager Assets unterstützt jetzt Inhaltsurhebernachweise für unterstützte Bildformate. Hier finden Sie Informationen zur Herkunft des Assets und seiner Erstellung, einschließlich Informationen dazu, ob es mit GenAI geändert wurde.

![Inhaltsurhebernachweise](/help/assets/assets/content-credentials.png)

**Visuelle Vorschau des Ordnerinhalts**

Experience Manager Assets zeigt jetzt beim Durchsuchen von oder Suchen nach Inhalten eine visuelle Vorschau der Ordnerinhalte in der Ordnerminiaturansicht an, wodurch es leichter wird, die im AEM Assets-Repository verfügbaren Assets zu finden.

<!--


**Content Credentials**

Content Credentials feature in Assets view now provides detailed asset provenance data adhered to an asset. This helps to trace the enroute edits along the asset's lifecycle to prevent users from deception through deliberately tempered assets. This ensures content authenticity among users and fosters trust through transparency.

When looking at the asset details, any image with content credentials added, such as those created with GenAI, displays the manifest details in a dedicated panel. If the asset is downloaded, published, or shared, the credentials remain intact with the asset.

![check publish status1](/help/release-notes/assets/content-credentials.png)

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in AEM Forms {#forms-new-prerelease-features}

#### Verbesserter visueller Regeleditor für auf Kernkomponenten basierende adaptive Formulare

Autorinnen und Autoren adaptiver Formulare können wiederholbare Formularfelder in vorkonfigurierten Funktionen verwenden, die im visuellen Regeleditor für Kernkomponenten verfügbar sind, um komplexe Geschäftslogik in den Formularen zu erstellen, ohne dass Anpassungen erforderlich sind oder das Entwicklungs-Team um Unterstützung gebeten werden muss.

### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen eine einmalige Möglichkeit, vor allen anderen einen exklusiven Zugang zu bahnbrechenden Neuerungen zu erhalten und ihre weitere Entwicklung mitzugestalten. Das Programm bietet Zugriff auf verschiedene Innovationen.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### Erstellen adaptiver Formulare mit dem universellen Editor

Nutzen Sie den [universellen Editor](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) von Adobe Experience Manager, um adaptive Formulare mithilfe von Drag-and-Drop-Authoring mit WYSIWYG zu erstellen, und zwar sowohl für Headless- als auch für Headful-Anmeldeerlebnisse. Bereitgestellt wird diese Funktion über Edge Delivery Services. Autorinnen und Autoren adaptiver Formulare können ganz einfach Experimente für Varianten der Formulare auf den Web-Seiten erstellen, sie starten und ermitteln, welche Erlebnisse die besten Ergebnisse für Endbenutzende bringen.

>[!IMPORTANT]
>
> Wenn Sie Interesse haben, am Early-Access-Programm von Adobe für Early-Access-Innovationen teilzunehmen, senden Sie einfach eine E-Mail von Ihrer offiziellen Adresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) und bitten Sie um Zugriff. Sie können Zugriff auf alle oder auf spezifische Innovationen anfordern.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Bereinigen von Inhalten im CDN mit einem selbst erstellten API-Schlüssel {#purge-cdn}

Das Festlegen von TTL mithilfe des HTTP Cache-Control-Headers ist ein effektiver Ansatz, um die Leistung bei der Inhaltsbereitstellung und die Aktualität der Inhalte aufeinander abzustimmen. Wenn aktualisierte Inhalte jedoch sofort bereitgestellt werden müssen, kann es von Vorteil sein, den CDN-Cache direkt zu bereinigen.

[Erfahren Sie](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token), wie Sie mit der Cloud Manager-Konfigurations-Pipeline ein API-Bereinigungs-Token selbst konfigurieren können, damit Sie eine der folgenden Variationen zum [Aufrufen der Bereinigungs-APIs](/help/implementing/dispatcher/cdn-cache-purge.md) verwenden können:
* Einzelne URL
* Mehrere URLs unter Verwendung eines Tags
* Vollständige CDN-Cache-Bereinigung

### Selbst durchgeführte Konfiguration des X-AEM-Edge-Key für das kundenseitig verwaltete CDN {#customermanaged-keys}

Zuvor war ein Support-Ticket erforderlich, um den X-AEM-Edge-Key zu generieren, der für die Konfiguration eines kundenseitig verwalteten CDN erforderlich war. Dies kann jetzt selbst durchgeführt werden. Zu diesem Zweck wird der Schlüsselwert in einer Konfigurationsdatei deklariert, die mithilfe der Konfigurations-Pipeline bereitgestellt wird. Dadurch werden beim Onboarding in eine neue Umgebung alle Verzögerungen beseitigt. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

### Warnhinweise für Traffic-Filterregeln {#traffic-filter-rules-alerts}

Mit Traffic-Filterregeln, die die optional lizenzierbaren Regeln für eine WAF (Web Application Firewall) enthalten, können Sie konfigurieren, welcher Traffic erlaubt oder verweigert werden soll.

Jetzt können Sie [sich Warnhinweise zusenden lassen](/help/security/traffic-filter-rules-including-waf.md#traffic-filter-rules-alerts), wenn Ihre Traffic-Filterregeln ausgelöst werden. E-Mail-Benachrichtigungen durch das Aktionszentrum informieren Sie darüber, wenn bestimmte Traffic-Bedingungen eintreten, damit Sie geeignete Maßnahmen treffen können.

### Early-Adopter-Programme im Zusammenhang mit der Inhaltsbereitstellung {#foundation-early-adopter}

Senden Sie eine E-Mail an **<aemcs-cdn-config-adopter@adobe.com>**, die angibt, für welche der unten aufgeführten Programme Sie sich interessieren.

#### Standardauthentifizierung beim CDN (Early-Adopter-Programm) {#basicauth-cdn}

Schützen Sie bestimmte Inhaltsressourcen mithilfe eines einfachen Authentifizierungsdialogfelds als Popup, das einen Benutzernamen und ein Passwort erforderlich macht. Diese Funktion ist in erster Linie für leichte Authentifizierungsfälle wie die Überprüfung von Inhalten durch geschäftliche Stakeholder und nicht als umfassende Lösung für Zugriffsrechte von Endbenutzenden gedacht. Die Liste der Benutzernamen und Passwörter wird über eine Konfigurationsdatei in Git verwaltet, die über die Konfigurations-Pipeline bereitgestellt wird – mit Verweis auf die geheimen Cloud Manager-Umgebungsvariablen. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### Client-seitige Weiterleitungen (Early-Adopter-Programm) {#client-side-redirects-early-adopter}

Konfigurieren Sie Client-seitige Weiterleitungen vom Typ 301/302 in der Verwaltung des Quell-Codes und stellen Sie sie im CDN bereit. [Weitere Informationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Beachten Sie, dass im Zusammenhang mit der [CDN-Konfiguration](/help/implementing/dispatcher/cdn-configuring-traffic.md) mehrere weitere Funktionen bereits verfügbar sind, einschließlich Anfrage- und Antworttransformationen und Routing des Traffics zu Nicht-AEM-Sites.

#### Business-Anwenderinnen und -Anwender können Umleitungen außerhalb von Git deklarieren (Early-Adopter-Programm) {#apache-rewritemaps-early-adopter}

Ähnlich wie bei AEM 6.5 erfassen Apache/Dispatcher Rewrite-Zuordnungen, die an einem bestimmten Speicherort im Veröffentlichungs-Repository abgelegt werden, und laden sie, ohne dass eine Pipeline auf Web-Ebene ausgeführt werden muss. So können geschäftliche Anwenderinnen und Anwender Umleitungen mithilfe einer Tabelle oder einer Benutzeroberfläche deklarieren, z. B. mit ACS Commons Redirect Map Manager oder einer benutzerdefinierten Anwendung. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) für das Laden dynamischer Inhalte (Early-Adopter-Programm) {#esi-early-adopter}

Das von Adobe verwaltete CDN unterstützt jetzt [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), eine Markup-Sprache für die dynamische Zusammenführung von Web-Inhalten auf Edge-Ebene. Durch die Einbeziehung von ESI-Snippets können Sie die gesamte HTML-Seite im CDN mit höheren TTLs zwischenspeichern und gleichzeitig diejenigen kleineren Abschnitte, die höhere Intervall-Updates (niedrigere TTLs) erfordern, öfter aus der Quelle abrufen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

### Aktionszentrum – Benachrichtigungen zum Inhaltsstatus – Early-Adopter-Programm {#actions-center-notifications}

Das [Aktionszentrum](/help/operations/actions-center.md) sendet E-Mail-Benachrichtigungen, wenn wichtige Vorfälle auftreten oder wenn etwas in Ihrem Code oder in Ihrer Konfiguration festgestellt wird, das proaktive Maßnahmen erfordert. Adobe hat jetzt mehrere neue Arten von Benachrichtigungen im Zusammenhang mit dem Status Ihrer Inhalte eingeführt. Diese Funktion ist über ein Early-Adopter-Programm verfügbar. Wenden Sie sich an die Adobe-Kundenunterstützung, wenn Sie teilnehmen möchten.

#### Seiten enthalten eine große Anzahl von Knoten {#page-nodes}

Eine große Anzahl von Knoten kann die Performance beim Rendern beeinträchtigen und die Seitenladezeiten verkürzen. Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn eine große Anzahl von Knoten auf einer Seite festgestellt wird. So können Sie die erforderlichen Schritte unternehmen, um die Gesamtzahl der Knoten auf einer Seite zu reduzieren.

#### Große Anzahl an ausgeführten Workflow-Instanzen {#running-workflows}

Die Performance der Workflow-Engine wird beeinträchtigt, wenn in der Autorenumgebung eine große Anzahl von ausgeführten Workflows vorliegt. Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn eine große Anzahl an ausgeführten Workflow-Instanzen erkannt wird. So können Sie einen Bereinigungsauftrag konfigurieren, um unnötige laufende Workflows zu beenden.

#### Benutzende, die direkt zu benutzerdefinierten Gruppen hinzugefügt wurden {#users-customgroups}

Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn Benutzende direkt benutzerdefinierten Gruppen hinzugefügt werden. So können Sie die Best Practices von IMS befolgen, indem Sie Benutzende zu relevanten IMS-Gruppen hinzufügen und diese IMS-Gruppen dann als Mitglieder in AEM-Gruppen aufnehmen.

#### Fehlende JCR-Inhalte {#jcr-content}

Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn festgestellt wird, dass JCR-Inhalte fehlen. So können Sie die fehlenden Inhalte hinzufügen und damit den Ausfall bestimmter AEM Assets-Funktionen verhindern.

#### Abgeschlossene Workflows die nicht bereinigt wurden {#workflows}

Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn abgeschlossene Workflows, die älter als 90 Tage sind, nicht bereinigt wurden. Dieser Ansatz optimiert die Leistung Ihrer Workflow-Engine, da die Anzahl der Workflow-Instanzen reduziert wird.

#### Fehlende Sling-Ressource {#sling-resource}

Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn festgestellt wird, dass eine Sling-Ressource fehlt. So können Sie die fehlende Ressource hinzufügen und damit den Ausfall bestimmter AEM Assets-Funktionen verhindern.

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2406-release/whats-new-2024-06-0).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Universeller Editor {#universal-editor}

Eine vollständige Liste der Versionen des universellen Editors finden Sie [hier](/help/release-notes/universal-editor/current.md).

## Generieren von Varianten {#generate-variations}

Eine vollständige Liste der Versionen für das Generieren von Varianten finden Sie [hier](/help/generative-ai/release-notes-generate-variations.md).

## Versionshinweise zu Experience Cloud {#experience-cloud}

Informationen zu Versionen anderer Experience Cloud-Anwendungen finden Sie [hier](https://experienceleague.adobe.com/de/docs/release-notes/experience-cloud/current).
