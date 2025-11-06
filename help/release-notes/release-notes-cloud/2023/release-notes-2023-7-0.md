---
title: Versionshinweise für Version 2023.7.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.7.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 7866d94c-e54c-4bb2-aaa6-66c019e46336
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 100%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.7.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.7.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.4.0) war der 27. Juli 2023. Die nächste Version (2023.8.0) ist für den 31. August 2023 geplant.

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2023.7.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version Juli 2023:

>[!VIDEO](https://video.tv.adobe.com/v/3422016/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

* MSM für Inhaltsfragmente. AEM Multisite Manager ist jetzt für Inhaltsfragmente verfügbar, sodass Inhaltsfragmente in Live Copies für die Massenverteilung von Inhalten erstellt werden können. Die detaillierten Vererbungssteuerelemente sind bis zur Ebene der Inhaltsfragmente und Varianten verfügbar.

### Neue Funktionen in der Vorabversion von [!DNL Experience Manager Sites] {#prerelease-sites}

* Über die [Inhaltsfragmentkonsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=de) können Benutzende nun Tags anzeigen und nach Tags suchen, die als Metadaten auf Inhaltsfragmente angewendet werden. Benutzende müssen nicht mehr zur Assets-Benutzeroberfläche wechseln, um diese Funktion zu nutzen. Dadurch werden Kontextwechsel reduziert und die Effizienz verbessert.

![Tagging in der Inhaltsfragmentkonsole](/help/assets/content-fragments-console-tags.png)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

**Verbessertes KI-Framework für Smart-Tags für Bilder**

Experience Manager Assets verwendet jetzt ein verbessertes Framework mit künstlicher Intelligenz für Smart-Tags für Bilder. Diese inhaltsbezogene Intelligenz führt zu einer besseren Relevanz und Genauigkeit von Smart-Tags, die für alle Bild-Assets bei der Aufnahme verfügbar sind.

**Konfigurieren der Spaltenanzeige für die Assets-Listenansicht**

Assets Essentials bietet jetzt die Möglichkeit, die Spalten auszuwählen, die in der Assets-Listenansicht angezeigt werden, z. B. Status, Format, Dimensionen, Größe usw.

![Konfigurieren der Spalten](/help/release-notes/assets/configure-columns.png)

**Sortieren von Suchergebnissen nach Relevanz**

Assets Essentials sortiert die Suchergebnisse nun standardmäßig nach Relevanz. Sie können die gesuchten Assets in aufsteigender oder absteigender Reihenfolge nach `Name`, `Relevance`, `Size`, `Modified` und `Created` sortieren.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Vorkonfigurierte Designs**](/help/forms/using-themes-in-core-components.md) **und Vorlagen**: Starten Sie Ihren Formularerstellungsprozess mit unseren neuen, gebrauchsfertig vorkonfigurierten Designs und Vorlagen, die sowohl auf erfahrene Profis als auch auf neue Formularautorinnen und -autoren zugeschnitten sind. Diese sorgfältig kuratierten Designs und Vorlagen wurden mit den Kernkomponenten für adaptive Formulare nahtlos erstellt und ermöglichen Ihnen die rasche Erstellung von Formularen für gängige Anwendungsfälle.

* **[React-Komponenten für Headless-Formulare](https://github.com/adobe/aem-forms-headless-components/tree/main/packages/react-vanilla-components)**: Sie können jetzt Ausgabedarstellungen adaptiver Headless-Formulare mit den bereitgestellten vordefinierten React-Komponenten in der Vorschau anzeigen und anpassen. Diese Komponenten nutzen BEM-Klassen aus den Kernkomponenten adaptiver Formulare für die Formatierung, sodass Sie das Erscheinungsbild mühelos an Ihre spezifischen Anforderungen anpassen können.

* [**Adaptive Formulare mit wiederholbaren Abschnitten erstellen**](/help/forms/create-forms-repeatable-sections.md): Sie können jetzt die Komponenten [Akkordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html?lang=de), [Assistent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html?lang=de), [Bedienfeld](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) und [horizontale Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html?lang=de) in einem auf Kernkomponenten basierenden adaptiven Formular verwenden, um mehrere Dateneinträge zu erfassen. Mit diesen wiederholbaren Abschnitten können Sie problemlos mehrere Dateneinträge bereitstellen. Dies ist nützlich, wenn die erforderlichen Dateninstanzen im Voraus unbekannt sind. Ein Formularbefüller kann problemlos Abschnitte hinzufügen oder entfernen, Formulare an verschiedene Dateneingabeszenarien anpassen und die Erfassung mehrfacher Vorkommen desselben Dateneintrags vereinfachen.


### Vorabversionsfunktionen, die in [!DNL Forms] verfügbar sind {#pre-release-features-available-in-forms-channel}

* [**Unterstützung für Google reCAPTCHA Enterprise**](/help/forms/captcha-adaptive-forms.md): Verwenden Sie Google reCAPTCHA Enterprise in einem adaptiven Formular, um einen besseren Schutz vor betrügerischen Aktivitäten und Spam zu bieten und so ein sichereres Anwendererlebnis zu ermöglichen. Dank erweiterter Risikoanalyse und nahtloser Integration können echte Benutzende problemlos Formulare absenden, während Bots effektiv blockiert werden.

  >[!VIDEO](https://video.tv.adobe.com/v/3422097/adaptive-forms-recaptcha-core-components-captcha/?quality=12&learn=on)

### Early-Adopter-Programm für adaptive Headless-Formulare {#forms-early-adopter}

Die Benutzung von [adaptiven Headless-Formularen](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de) ermöglicht es Entwicklerinnen und Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, für die der Zugriff und die Interaktion über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche möglich ist. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

* Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
* Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an `aem-forms-headless@adobe.com` senden, um am Early-Adopter-Programm teilzunehmen.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Aktionszentrum {#actions-center}

Abonnieren Sie E-Mail-Benachrichtigungen, die Sie warnen, wenn kritische Vorfälle auftreten, die sofortiges Handeln erfordern, und außerdem personalisierte Empfehlungen zur Optimierung Ihrer Site enthalten. Das [Aktionszentrum](/help/operations/actions-center.md) dient als zentrale Anlaufstelle, an der Sie diese Warnhinweise überprüfen können, z. B. blockierte Replikationswarteschlangen oder ablaufende Anmeldeinformationen, und sie als aufgelöst markieren können.

![Screenshot des Aktionszentrums](/help/assets/assets/actions-center.png)

### CDN und WAF-Regeln – Early-Adopter-Programm {#waf-early-adopter}

Filtern Sie den Traffic im CDN anhand von:

* Anfragekopfzeilen und -eigenschaften (z. B. IP-Adresse)
* Traffic-Muster, die bekanntermaßen mit bösartigem Traffic verknüpft sind

Möchten Sie die Funktion ausprobieren und Feedback geben? Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an **aemcs-waf-adopter@adobe.com** senden, um am Early-Adopter-Programm teilzunehmen. Die Plätze sind begrenzt.

Weitere Informationen zur Funktion finden Sie im Artikel [hier](/help/security/traffic-filter-rules-including-waf.md).

### Sonstige Foundation-Änderungen {#other-foundation-changes}

* In der Woche vom 7. August gibt AEM den Fehlercode 429 anstelle des Fehlercodes 503 zurück, wenn Anforderungen an AEM Instanzen ein gesundes Maß überschreiten. [Weitere Informationen](/help/implementing/developing/introduction/development-guidelines.md)

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
