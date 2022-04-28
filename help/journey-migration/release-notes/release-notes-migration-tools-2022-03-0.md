---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.3.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.3.0
feature: Release Information
exl-id: ab43605d-d46e-43de-b71f-fab610609550
source-git-commit: 87e3291b4a72c24fc6cf8df488df305f1a078ea5
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 27%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.3.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service 2022.3.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.26 wurde am 16. März 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, nicht verarbeitete Assets zu erkennen. Wenn nicht verarbeitete Assets erkannt werden, müssen diese Assets entweder auf &quot;Verarbeitet&quot;gesetzt oder aus dem Migrationssatz während der Inhaltstransfer entfernt werden, um Probleme bei der Inhaltsaufnahme zu vermeiden.
* Möglichkeit, festzustellen, ob Inhalt über mehr als 1000 Vanity-URLs verfügt. Die Verwendung einer hohen Anzahl von Vanity-URLs empfiehlt sich nicht, da Dispatcher- und Publish-Server geladen werden.
* Möglichkeit, Probleme im Zusammenhang mit Oak-Indexdefinitionen zu identifizieren und Inkompatibilitäten mit AEM as a Cloud Service zu erkennen.
* Möglichkeit, die Verwendung von Externalizer-Konfigurationen zu erkennen und darüber zu berichten. In AEM werden as a Cloud Service Externalizer-Konfigurationen von Cloud Manager festgelegt. Daher müssen vorhandene Externalizer-Konfigurationen überarbeitet werden, um die Kompatibilität zu gewährleisten.

### Fehlerbehebungen {#bug-fixes-bpa}

* In einigen Szenarien konnte BPA nicht ausgeführt werden, da FormsSelectiveFeaturesAnalysis einen Assertionsfehler ausgab. Dieses Problem wurde behoben.
* BPA meldete Ergebnisse im Zusammenhang mit dem WRK-Muster als MAJOR anstelle von CRITICAL. Dieses Problem wurde behoben.
* BPA meldete fälschlicherweise Ergebnisse im Zusammenhang mit OAK-Indexdefinitionen in ui.apps als CRITICAL an. Dieses Problem wurde behoben.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.9.0 wurde am 28. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Schutzmechanismen für die Größe überprüfen - Die Funktion &quot;Prüfgröße für Content Transfer Tool&quot;hilft bei der Reduzierung fehlgeschlagener Inhaltstransfers.  Mit der Funktion &quot;Größe überprüfen&quot;können Benutzer 1) feststellen, ob sie über ausreichend Festplattenspeicher im `crx-quickstart` -Unterverzeichnis vor der Extraktion und 2) schätzen die Größe des Migrationssatzes und überprüfen Sie, ob es unterstützt wird. Wenn eine oder beide Prüfungen verletzt werden, werden Benutzern Warnungen in der CTT-Benutzeroberfläche angezeigt. Mit dieser Limits können Sie Fehler bei der Inhaltstransfer vermeiden und Migrationsoptionen proaktiv mit der Adobe-Kundenunterstützung besprechen. Siehe [Bestimmen der Größe des Migrationssatzes und des Festplattenspeichers](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en#migration-set-size) für weitere Details.
