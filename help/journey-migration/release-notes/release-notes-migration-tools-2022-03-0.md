---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.3.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.3.0
feature: Release Information
exl-id: ab43605d-d46e-43de-b71f-fab610609550
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 63%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.3.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.3.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.26 wurde am 16. März 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, nicht verarbeitete Assets zu erkennen. Wenn nicht verarbeitete Assets erkannt werden, müssen diese Assets entweder auf &quot;verarbeitet&quot;gesetzt oder aus dem Migrationssatz während der Inhaltsübertragung entfernt werden, um zu vermeiden, dass bei der Inhaltsaufnahme Probleme auftreten.
* Möglichkeit, festzustellen, ob Inhalte über mehr als 1000 Vanity-URLs verfügen. Die Verwendung einer hohen Anzahl von Vanity-URLs empfiehlt sich nicht, da dies die Dispatcher- und Veröffentlichungs-Server belastet.
* Möglichkeit, Probleme im Zusammenhang mit Oak-Index-Definitionen zu identifizieren und Inkompatibilitäten mit AEM as a Cloud Service zu erkennen.
* Möglichkeit, die Verwendung von Externalizer-Konfigurationen zu erkennen und darüber zu berichten. In AEM as a Cloud Service Externalizer werden Konfigurationen von Cloud Manager festgelegt. Daher müssen vorhandene Externalizer-Konfigurationen überarbeitet werden, um die Kompatibilität zu gewährleisten.

### Fehlerbehebungen {#bug-fixes-bpa}

* In einigen Szenarien konnte BPA nicht ausgeführt werden, da FormsSelectiveFeaturesAnalysis einen Assertionsfehler ausgab.
* BPA meldete Befunde im Zusammenhang mit dem WRK-Muster als SCHWERWIEGEND anstelle von KRITISCH.
* BPA meldete fälschlicherweise Ergebnisse im Zusammenhang mit Oak-Indexdefinitionen in ui.apps als CRITICAL.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.9.0 wurde am 28. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Schutzmaßnahme Größenüberprüfung: Die Funktion „Größenüberprüfung“ des Content Transfer Tools hilft bei der Reduzierung fehlgeschlagener Inhaltsübertragungen. Mit der Funktion &quot;Größe überprüfen&quot;können Benutzer feststellen, ob im `crx-quickstart` -Unterverzeichnis vor der Extraktion. Außerdem können sie die Größe des Migrationssatzes schätzen und überprüfen, ob er unterstützt wird. Wenn eine oder beide Prüfungen verletzt werden, sehen Benutzer Warnungen in der CTT-Benutzeroberfläche. Mit dieser Schutzmaßnahme können Sie Fehler bei der Inhaltsübertragung vermeiden und Migrationsoptionen proaktiv mit der Adobe-Kundenunterstützung besprechen. Siehe [Bestimmen der Größe des Migrationssatzes und des Festplattenspeichers](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de#migration-set-size) für weitere Details.
