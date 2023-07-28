---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 5995c416328e6f340285004ec2e723cc9279dabd
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 27%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version der Funktion (2023.7.0) ist der 27. Juli 2023. Die nächste Version der Funktion (2023.8.0) ist für den 31. August 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht vom Juli 2023 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2023.7.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3422016/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

* MSM für Inhaltsfragmente. AEM Multisite-Manager ist jetzt für Inhaltsfragmente verfügbar, sodass Inhaltsfragmente in Live Copies für die Massenverteilung von Inhalten erstellt werden können. Die detaillierten Vererbungssteuerelemente sind bis zur Ebene der Inhaltsfragmente und Varianten verfügbar.

### Neue Funktionen in der Vorabversion von [!DNL Experience Manager Sites] {#prerelease-sites}

* Die [Inhaltsfragmentkonsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=en) ermöglicht es Benutzern nun, Tags anzuzeigen und nach Tags zu suchen, die als Metadaten auf Inhaltsfragmente angewendet werden. Benutzer müssen nicht mehr zur Assets-Benutzeroberfläche wechseln, um diese Funktion zu nutzen, wodurch der Kontextwechsel reduziert und die Effizienz verbessert wird.

![Tagging in der Inhaltsfragmentkonsole](/help/assets/content-fragments-console-tags.png)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Asset-Ansicht {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

**Verbessertes KI-Framework für Smart-Tags für Bilder**

Experience Manager Assets verwendet jetzt ein verbessertes Framework mit künstlicher Intelligenz für Smart-Tags für Bilder. Diese inhaltsbezogene Intelligenz führt zu einer besseren Relevanz und Genauigkeit von Smart-Tags, die für alle Bild-Assets bei der Benutzende verfügbar sind.

**Anzeige von Spalten für die Asset-Listenansicht konfigurieren**

Assets Essentials bietet jetzt die Möglichkeit, die Spalten auszuwählen, die in der Asset-Listenansicht angezeigt werden, z. B. Status, Format, Dimensionen, Größe usw.

![Konfigurieren der Spalten](/help/release-notes/assets/configure-columns.png)

**Sortieren von Suchergebnissen nach Relevanz**

Assets Essentials sortiert die Suchergebnisse nun standardmäßig nach Relevanz. Sie können die gesuchten Assets in aufsteigender oder absteigender Reihenfolge nach `Name`, `Relevance`, `Size`, `Modified` und `Created` sortieren.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Vorkonfigurierte Designs**](/help/forms/using-themes-in-core-components.md) **und Vorlagen**: Starten Sie Ihren Formularerstellungsprozess mit unseren einsatzbereiten OOTB-Designs und -Vorlagen, die auf erfahrene Profis und neue Formularautoren zugeschnitten sind. Nahtlos mit den Kernkomponenten von Adaptive Forms erstellt, ermöglichen Ihnen diese sorgfältig kuratierten Designs und Vorlagen die rasche Erstellung von Formularen für gängige Anwendungsfälle.

  ![Vordefinierte Vorlagen](/help/forms/assets/form-templates-ootb.png)

* **React-Komponenten für Headless Forms**: Sie können jetzt Headless-Adaptive Formularwiedergaben mit den vordefinierten React-Komponenten in der Vorschau anzeigen und anpassen. Diese Komponenten nutzen BEM-Klassen aus den adaptiven Forms-Kernkomponenten für die Formatierung, sodass Sie das Erscheinungsbild mühelos an Ihre spezifischen Anforderungen anpassen können.

* [**Adaptive Forms mit wiederholbaren Abschnitten erstellen**](/help/forms/create-forms-repeatable-sections.md): Jetzt können Sie [Akkordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Assistent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [Bedienfeld](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), und [Horizontale Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html) Komponenten, die auf dem adaptiven Formular basieren, wiederholbar für die Erfassung mehrerer Datensätze.  Mit diesen wiederholbaren Abschnitten können Sie mehrere Dateneinträge einfach bereitstellen. Dies ist nützlich, wenn die erforderlichen Dateninstanzen im Voraus unbekannt sind. Ein Formularbenutzer kann problemlos Abschnitte hinzufügen oder entfernen, sodass Formulare an verschiedene Dateneingabeszenarien angepasst werden können und die Erfassung mehrerer Vorkommen desselben Datensatzes vereinfacht wird.


### Funktionen zur Vorabversion sind verfügbar in [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* [**Enterprise-Unterstützung für Google reCAPTCHA**](/help/forms/captcha-adaptive-forms.md): Verwenden Sie Google reCAPTCHA Enterprise in einem adaptiven Formular, um einen verbesserten Schutz vor betrügerischer Aktivität und Spam zu bieten und so eine sicherere Benutzererfahrung zu bieten. Dank der erweiterten Risikoanalyse und nahtloser Integration können echte Benutzer problemlos Formulare senden, während Bots effektiv blockiert werden.

  >[!VIDEO](https://video.tv.adobe.com/v/3422097/adaptive-forms-recaptcha-core-components-captcha/?quality=12&learn=on)

### Early-Adopter-Programm für adaptive Headless-Formulare {#forms-early-adopter}

Verwendung [Headless Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de) , damit Ihre Entwickler interaktive Formulare erstellen, veröffentlichen und verwalten können, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

* Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
* Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können eine E-Mail an senden `aem-forms-headless@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Aktionszentrum {#actions-center}

Abonnieren Sie E-Mail-Benachrichtigungen, die Sie warnen, wenn kritische Vorfälle auftreten, die sofortiges Handeln erfordern, und auch mit personalisierten Empfehlungen zur Optimierung Ihrer Site. [Aktionszentrum](/help/operations/actions-center.md) dient als zentrale Anlaufstelle, an der Sie diese Warnhinweise überprüfen können, z. B. blockierte Replikationswarteschlangen oder ablaufende Anmeldeinformationen, und sie als aufgelöst markieren können.

![Screenshot des Aktionszentrums](/help/assets/assets/actions-center.png)

### CDN und WAF-Regeln für frühe Anwender {#waf-early-adopter}

Filtern Sie den Traffic im CDN anhand von:
* Anfragekopfzeilen und -eigenschaften (z. B. IP-Adresse)
* Traffic-Muster, die bekanntermaßen mit bösartigem Traffic verknüpft sind

Möchten Sie die Funktion ausprobieren und Feedback teilen? E-Mail an senden **aemcs-waf-adopter@adobe.com** von Ihrer offiziellen E-Mail-ID, um mehr über das Programm für frühe Anwender zu erfahren. Der Platz ist begrenzt.

Weitere Informationen zur Funktion finden Sie im Artikel . [here](/help/security/cdn-and-waf-rules.md).

### Sonstige Foundation-Änderungen {#other-foundation-changes}

* In der Woche vom 7. August gibt AEM den Fehlercode 429 anstelle des Fehlercodes 503 zurück, wenn Anforderungen an AEM Instanzen eine gesunde Stufe überschreiten. [Weitere Informationen](/help/implementing/developing/introduction/development-guidelines.md)

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
