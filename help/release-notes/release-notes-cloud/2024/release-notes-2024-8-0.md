---
title: Versionshinweise für Version 2024.8.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2024.8.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
exl-id: dd1d4b8f-8331-4e97-a754-37e720974db6
source-git-commit: 4b8086920bc3e3b9c5ed2a74934645fbc69acf71
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 98%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2024.8.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2024.8.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2022 oder 2023 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.8.0) ist der 29. August 2024. Die nächste Version mit neuen Funktionen (2024.9.0) ist für den 26. September 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2024.8.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version vom August 2024:

>[!VIDEO](https://video.tv.adobe.com/v/3433381?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in Experience Manager Sites {#new-feature-sites}

**AEM-Authoring für Edge Delivery Services**

Die vorhandene Sites-Funktion [Vererbung](/help/sites-cloud/authoring/universal-editor/inheritance.md) wird jetzt unterstützt, einschließlich:

* [AEM-Launches](/help/sites-cloud/authoring/launches/overview.md)
* [MSM](/help/sites-cloud/administering/msm/overview.md) auf Seitenebene

Darüber hinaus werden jetzt die folgenden Seitenverwaltungsfunktionen unterstützt:

* [AEM-Tags](/help/sites-cloud/authoring/sites-console/tags.md) können als [Taxonomie](/help/edge/wysiwyg-authoring/taxonomy.md) nach Edge Delivery Services exportiert werden.
* [Vorlagen](/help/sites-cloud/authoring/universal-editor/templates.md) für Edge Delivery Services werden bald verfügbar sein.

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzen Sie GenAI über die neue Funktion [Varianten generieren](/help/generative-ai/generate-variations.md) von AEM, die jetzt in Cloud Service verfügbar ist. „Varianten generieren“ hilft Ihnen bei der Erstellung und Skalierung von Inhalten durch den Einsatz generativer KI. Wenden Sie sich an Ihr Adobe-Accountteam, um sich für das Programm zu erkundigen.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#assets-view-new-features}

**Aktualisierte Adobe Firefly-Bildgenerierung**

Assets as a Cloud Service verwendet jetzt das neueste Widget von Firefly, mit dem Sie Bilder in verschiedenen Stilen mithilfe von Adobe Firefly generieren können. Indem Sie mit dem integrierten Firefly-Editor Stil, Komposition, Dimensionen und mehr definieren, können Sie schnell die benötigten Assets erstellen und speichern und sie direkt im AEM Assets-Repository verwenden.

![Adobe Firefly-Bildgenerierung](/help/assets/assets/bugatti-type-57.png)

**Unterstützung von PSB-Dateien**

Assets as a Cloud Service unterstützt jetzt neben der bestehenden Unterstützung für PSD-Dateien auch große Photoshop-Dokumente (PSB-Dateien).

### Neue Verbesserungen in Content Hub {#content-hub-new-enhancements}

* Bessere Handhabung langer Dateinamen, einfaches Anzeigen des kompletten Namens über eine QuickInfo.
* Verbesserte Miniaturansichten, die nun das Seitenverhältnis des Inhalts besser anpassen und einen größeren Inhaltsbereich abdecken.
* Benutzerdefiniertes Miniaturbild-Erlebnis aus AEM mit Content Hub unterstützt.
* Verbesserungen bei der Farbsuche.
* Verbesserungen bei der Konfiguration von Suchvorgängen.
* Die Informationsseite von Sammlungen wurde verbessert, sodass sie den Namen der Erstellenden widerspiegelt.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Vorabveröffentlichungsfunktionen in AEM Forms {#forms-new-prerelease-features}

#### Automatisches Speichern eines Entwurfs für auf Kernkomponenten basierende adaptive Formulare

Benutzende profitieren jetzt von einer Funktion zum automatischen Speichern, mit der ein teilweise ausgefülltes Formular automatisch als Entwurf gespeichert wird. Sie können später zurückkehren, um das Ausfüllen des Formulars auf demselben oder einem anderen Gerät abzuschließen. Diese Funktion verbessert die Konversionsraten für Unternehmen, indem Formularabbrüche reduziert werden, da Benutzende nicht mit dem Ausfüllen von Formularen von Anfang an beginnen müssen.


### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### AEM Forms-KI-Assistent

Die generative KI für adaptive Formulare bietet eine völlig neue Leistungsstärke und erleichtert Ihre Formularentwicklungsprozesse. Dadurch können Sie schneller als je zuvor bessere Formulare erstellen.

![Generativer KI-Assistent, adaptive Formulare](/help/forms/assets/generative-ai-assistant.png)

Die folgenden generativen KI-Funktionen stehen zur Verfügung:

* **KI-Assistent für Produktanfragen**: Erhalten Sie sofortige Antworten auf Ihre Fragen zu AEM Forms. Der KI-Assistent fungiert als Ihre persönliche Wissensdatenbank und bietet hilfreiche Anleitungen und Empfehlungen direkt innerhalb der Plattform.

* **Erstellung von adaptiven Formularen**: Erstellen Sie mühelos vollständige Formulare mit generativen KI-Prompts. Unsere generative KI generiert automatisch benutzerfreundliche Formulare, durch die Abbrüche reduziert werden und das Erlebnis personalisiert wird.

* **Bereichsgenerierung für Forms**: Generieren Sie Formularabschnitte, die auf bestimmte Datenerfassungsanforderungen zugeschnitten sind. Generieren Sie beispielsweise Abschnitte zum Erfassen von Zahlungsinformationen, Kundenpräferenzen oder Reisedetails.

* **Ändern von Formular-Layouts**: Experimentieren Sie mit verschiedenen Layouts und Designs mithilfe von generativen KI-Prompts. Probieren Sie verschiedene Layouts wie Assistenten- oder Registerkartenansichten aus, um Ihr Formular optimal zu gestalten. Verwenden Sie generative KI-Prompts, um die Reaktivität Ihrer Formulare auf Mobilgeräten zu optimieren und visuell ansprechende Formulare zu erstellen, die von Benutzenden gern verwendet werden.

* **Konfigurieren der Übermittlungsaktion**: Verwenden Sie generative KI-Prompts, um mühelos eine Übermittlungsaktion für Ihr Formular zu konfigurieren. Treffen Sie Ihre Wahl aus einer Bibliothek vordefinierter Übermittlungsaktionen oder aus einer Liste von benutzerdefinierten Übermittlungsaktionen, die von Ihrem eigenen Entwicklungs-Team erstellt und bereitgestellt wurden.

>[!IMPORTANT]
>
> Wenn Sie Interesse haben, dem Early-Access-Programm für Innovationen beizutreten, senden Sie einfach von Ihrer offiziellen Adresse aus eine E-Mail mit der Liste der Funktionen, die Sie interessieren, an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com).


## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Early-Adopter-Programme im Zusammenhang mit der Inhaltsbereitstellung {#foundation-early-adopter}

Senden Sie eine E-Mail an **<aemcs-cdn-config-adopter@adobe.com>**, die angibt, für welche der unten aufgeführten Programme Sie sich interessieren.

#### Standardauthentifizierung beim CDN (Early-Adopter-Programm) {#basicauth-cdn}

Schützen Sie bestimmte Inhaltsressourcen mithilfe eines einfachen Authentifizierungsdialogfelds als Popup, das einen Benutzernamen und ein Passwort erforderlich macht. Diese Funktion ist in erster Linie für leichte Authentifizierungsfälle wie die Überprüfung von Inhalten durch geschäftliche Stakeholder und nicht als umfassende Lösung für Zugriffsrechte von Endbenutzenden gedacht. Die Liste der Benutzernamen und Passwörter wird über eine Konfigurationsdatei in Git verwaltet, die über die Konfigurations-Pipeline bereitgestellt wird – mit Verweis auf die geheimen Cloud Manager-Umgebungsvariablen. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### Server-seitige Weiterleitungen (Early-Adopter-Programm) {#server-side-redirects-early-adopter}

Konfigurieren Sie Server-seitige 301/302-Weiterleitungen in der Quell-Code-Verwaltung und stellen Sie sie im CDN bereit. [Weitere Informationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Beachten Sie, dass im Zusammenhang mit der [CDN-Konfiguration](/help/implementing/dispatcher/cdn-configuring-traffic.md) mehrere weitere Funktionen bereits verfügbar sind, einschließlich Anfrage- und Antworttransformationen und Routing des Traffics zu Nicht-AEM-Sites.

#### Business-Anwenderinnen und -Anwender können Umleitungen außerhalb von Git deklarieren (Early-Adopter-Programm) {#apache-rewritemaps-early-adopter}

Ähnlich wie bei AEM 6.5 erfassen Apache/Dispatcher Rewrite-Zuordnungen, die an einem bestimmten Speicherort im Veröffentlichungs-Repository abgelegt werden, und laden sie, ohne dass eine Pipeline auf Web-Ebene ausgeführt werden muss. So können geschäftliche Anwenderinnen und Anwender Umleitungen mithilfe einer Tabelle oder einer Benutzeroberfläche deklarieren, z. B. mit ACS Commons Redirect Map Manager oder einer benutzerdefinierten Anwendung. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) für das Laden dynamischer Inhalte (Early-Adopter-Programm) {#esi-early-adopter}

Das von Adobe verwaltete CDN unterstützt jetzt [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), eine Markup-Sprache für die dynamische Zusammenführung von Web-Inhalten auf Edge-Ebene. Durch die Einbeziehung von ESI-Snippets können Sie die gesamte HTML-Seite im CDN mit höheren TTLs zwischenspeichern und gleichzeitig diejenigen kleineren Abschnitte, die höhere Intervall-Updates (niedrigere TTLs) erfordern, öfter aus der Quelle abrufen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

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
