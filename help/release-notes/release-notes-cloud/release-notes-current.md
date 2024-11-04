---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 9bb2d38feea2690bc112611d429dad22e7bcd278
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 58%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2022 oder 2023 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.10.0) ist der Freitag, 31. Oktober 2024. Die nächste Version (2024.11.0) ist für den Freitag, 21. November 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- ## Release Video {#release-video}

Have a look at the October 2024 Release Overview video for a summary of the features added in the 2024.10.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**Modernisierte Seitenereignisse**

Die folgenden AEM Sites-Seitenereignisse sind jetzt als extern nutzbare Ereignisse verfügbar, die auf der AEM as a Cloud Service Eventing Platform basieren. Die Ereignisse können über Adobe I/O verarbeitet werden, um mit externen Prozessen zu interagieren.
* Seite veröffentlicht
* Seite nicht veröffentlicht
* Seite gelöscht

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzen Sie GenAI über die neue Funktion [Varianten generieren](/help/generative-ai/generate-variations.md) von AEM, die jetzt in Cloud Service verfügbar ist. „Varianten generieren“ hilft Ihnen bei der Erstellung und Skalierung von Inhalten durch den Einsatz generativer KI. Wenden Sie sich an Ihr Adobe-Accountteam, um sich für das Programm zu erkundigen.

**AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten**

Die [AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten](/help/headless/aem-rest-openapi-content-fragment-delivery.md) ist jetzt für AEM as a Cloud Service verfügbar.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Early-Access-Funktion in Dynamic Media {#dm-early-access}

**KI-generierte Videountertitel**

Bei KI-generierten Videountertiteln in Adobe Dynamic Media wird künstliche Intelligenz eingesetzt, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion soll die Barrierefreiheit und das Benutzererlebnis verbessern, indem akkurate Untertitel in Echtzeit bereitgestellt werden. Die KI analysiert die Audiospur des Videos, um Sprache zu transkribieren und Untertitel zu erstellen, die zwecks Korrektheit oder Anpassung bearbeitet werden können. Diese Untertitel dienen der Barrierefreiheit und machen Videos für Zielgruppen attraktiver, die textbasierte Videounterstützung nutzen bzw. bevorzugen.

Um frühzeitig Zugang zur Unterstützung für KI-generierte Untertitel in Ihrem Dynamic Media-Konto zu erhalten, [erstellen und senden Sie eine Anfrage an den Adobe-Kunden-Support.](/help/assets/dynamic-media/video.md##enable-dash)

### Neue Funktionen in der Assets-Ansicht {#assets-view-new-features}

**Terminierte Berichte**

Berichte können jetzt automatisch in der Assets-Ansicht zu einem wiederkehrenden Zeitpunkt oder zu einem späteren Zeitpunkt erstellt werden, was den Aufwand für datengesteuerte Einblicke verringert.

![ Terminierte Berichte -](/help/assets/assets/scheduled-reports-tab.png)

### Neue Funktionen in Content Hub {#content-hub-new-features}

**Digital Rights Management für lizenzierte Assets**

Unternehmen können jetzt die Lizenzkonformität erhöhen und das Risiko der Freigabe von Assets mit Lizenzbedingungen minimieren, indem sie DRM für lizenzierte Assets für Benutzer von Content Hub nutzen. Benutzer müssen die Lizenzbedingungen überprüfen und akzeptieren, bevor sie lizenzierte Assets herunterladen können. Weitere Informationen finden Sie unter [Verwalten lizenzierter Assets auf Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

![download-multiple-license](/help/assets/assets/download-multiple-license.png)

**Konfiguration der Asset-Karten-Metadaten**

Mit Content Hub können Sie jetzt die wichtigen Metadatenfelder konfigurieren, die Sie auf der Asset-Karte anzeigen müssen, und zwar bis zu sechs Felder. Weitere Informationen finden Sie im Abschnitt &quot;Asset-Karte&quot;unter [Content Hub konfigurieren](/help/assets/configure-content-hub-ui-options.md#asset-card).

![Schlüssel-Metadaten auf der Asset-Karte](/help/assets/assets/asset-card-key-metadata.png)

**Konfigurieren der Sichtbarkeit und des Downloads abgelaufener Assets**

Admins können jetzt steuern, ob abgelaufene Assets in Content Hub sichtbar sein sollen. Wenn die abgelaufenen Assets sichtbar gemacht werden, können sie auch definieren, ob Benutzer sie herunterladen können. Weitere Informationen finden Sie im Abschnitt Abgelaufene Assets unter [Content Hub konfigurieren](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub) .

![Abgelaufene Assets in Content Hub](/help/assets/assets/expired-assets-content-hub.png)

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

* **Erstellung von adaptiven Formularen**: Erstellen Sie mühelos vollständige Formulare mit generativen KI-Prompts. Die generative KI von Adobe generiert automatisch benutzerfreundliche Formulare, durch die Abbrüche reduziert werden und das Erlebnis personalisiert wird.

* **Bereichsgenerierung für Forms**: Generieren Sie Formularabschnitte, die auf bestimmte Datenerfassungsanforderungen zugeschnitten sind. Generieren Sie beispielsweise Abschnitte zum Erfassen von Zahlungsinformationen, Kundenpräferenzen oder Reisedetails.

* **Ändern von Formular-Layouts**: Experimentieren Sie mit verschiedenen Layouts und Designs mithilfe von generativen KI-Prompts. Probieren Sie verschiedene Layouts wie Assistenten- oder Registerkartenansichten aus, um Ihr Formular optimal zu gestalten. Verwenden Sie generative KI-Prompts, um die Reaktivität Ihrer Formulare auf Mobilgeräten zu optimieren und visuell ansprechende Formulare zu erstellen, die von Benutzenden gern verwendet werden.

* **Konfigurieren der Übermittlungsaktion**: Verwenden Sie generative KI-Prompts, um mühelos eine Übermittlungsaktion für Ihr Formular zu konfigurieren. Treffen Sie Ihre Wahl aus einer Bibliothek vorkonfigurierter Übermittlungsaktionen oder aus benutzerdefinierten Übermittlungsaktionen, die von Ihrem Entwicklungs-Team erstellt und bereitgestellt wurden.

>[!IMPORTANT]
>
> Möchten Sie am Early-Access-Programm für Forms-Innovationen teilnehmen? Senden Sie von Ihrer offiziellen E-Mail-Adresse eine Nachricht an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) mit der Liste der Funktionen, an denen Sie interessiert sind.

## CIF-Add-on {#cloud-services-cif}

### Fehlerbehebungen {#bug-fixes-cif}

* Die Benutzeroberflächentests funktionieren jetzt ordnungsgemäß mit den CIF-Kernkomponenten.
* Es wurde ein Problem behoben, durch das das URL-Format „Kategorie“ in der Cloud-Instanz nicht wie erwartet funktionierte.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Konfiguration zum Steuern der Formularübermittlung {#configuration-submissions}

Um die Formularübermittlung für Coral- oder Foundation-Formulare an bestimmten Stellen zu steuern, hat AEM eine neue Konfiguration eingeführt: `com.adobe.granite.ui.components.FormRestrict`. Diese Konfiguration besteht aus zwei Feldern:

1. **Zulässige Pfade hinzufügen**: Gibt die Pfade an, in denen Formularaktionen zulässig sind.
1. **Verhalten beschränken**: Bestimmt das Verhalten für eingeschränkte Pfade (Pfade, die nicht in der Zulassungsliste enthalten sind). Sie können zwischen zwei Optionen wählen:
   * **Popup** (Standard): Zeigt eine Popup-Benachrichtigung an.
   * **Prevent**:Blockiert die Übermittlung des Formulars.

>[!NOTE]
>
>Diese Konfiguration wird nicht für alle Coral- oder Foundation-Formulare unter `/apps`, `/libs`, `/mnt/overlay` und `/mnt/override` unterstützt.

### Self-Serve-Protokollweiterleitung mit erweiterter Netzwerkoption {#log-forwarding}

Während AEM (einschließlich Apache/Dispatcher) und CDN-Protokolle aus Cloud Manager heruntergeladen werden können, ist es für viele Unternehmen von Vorteil, diese Protokolle an ein bevorzugtes Protokollierungsziel zu streamen. AEM unterstützt jetzt die [Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md) an Azure Blob Storage, Datadog, HTTPS, Elasticsearch (und OpenSearch) und Splunk. AEM Protokolle können optional über erweiterte Netzwerkkonfigurationen weitergeleitet werden, z. B. über die Verwendung einer dedizierten IP-Adresse.

Diese Funktion wird von Benutzern auf Self-Service-Weise konfiguriert und mithilfe der [Config Pipeline](/help/operations/config-pipeline.md) bereitgestellt.

### Pipeline-freie URL-Umleitungen für Geschäftsbenutzer {#pipeline-free-redirects}

Browserseitige Umleitungen sind nützlich, wenn eine Webseite heruntergefahren wurde, verschoben wurde oder in anderen Szenarien. Mit [Pipeline-freien URL-Weiterleitungen](/help/implementing/dispatcher/pipeline-free-url-redirects.md) können Sie eine Apache-Umschreibungsmap-Datei an einem AEM Veröffentlichungsort platzieren, wo sie automatisch geladen wird - es ist nicht erforderlich, die Datei an die Quell-Code-Verwaltung zu übertragen oder eine Cloud Manager-Pipeline zu initiieren.

Zu den Optionen zum Veröffentlichen der Rewrite-Datei gehören das Hochladen als Asset, die Verwendung des ACS Commons Rewrite Map Manager oder die Interaktion mit einer benutzerdefinierten Benutzeroberfläche.

### Konfigurieren der Pipeline für RDEs {#config-pipeline-rdes}

Rapid Development Environments sind ein leistungsstarkes Tool zur schnellen Bereitstellung und zum Testen von Code und Konfiguration in einer Cloud-Umgebung. RDEs unterstützen jetzt die [Synchronisierung der Konfigurations-YAML-Dateien](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline), einschließlich CDN-Einstellungen wie Traffic-Filterregeln und Anforderung-/Antworttransformationen sowie der Protokollweiterleitung und anderen Konfigurationsoptionen. [Weitere Informationen finden Sie in der vollständigen Liste der unterstützten Konfigurationsoptionen](/help/operations/config-pipeline.md) .

### Neue Produktprofile {#new-product-profiles}

Wenn eine neue AEM erstellt wird, werden Produktprofile automatisch in der Adobe Admin Console angezeigt, sodass Administratoren Zugriff auf lizenzierte Lösungen und Funktionen zuweisen können.

Neue Umgebungen enthalten jetzt einen aktualisierten Satz von Produktprofilen, sodass sie mit künftigen Funktionen kompatibel sind, einschließlich der Generierung von API-Anmeldeinformationen in der Adobe Developer Console. Bestehende Umgebungen können ihre Produktprofile in einer zukünftigen Version aktualisieren. [Weitere Informationen](/help/onboarding/aem-cs-team-product-profiles.md).

### Neue AEM Developer Console (öffentliche Beta-Version) {#aem-developer-console-beta}

Probieren Sie die neu gestaltete [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) aus, die ein interaktiveres Erlebnis für das Debugging von Code in Cloud-Umgebungen bietet.

Jeder kann auf die öffentliche Beta-Version zugreifen, indem in der aktuellen AEM Developer Console auf die Schaltfläche *Neue Konsole verfügbar* geklickt wird. Adobe freut sich über Feedback, das Sie per E-Mail an **<aemcs-new-devconsole-ui-beta@adobe.com>** senden können.

![Bildschirm „OSGi-Bundles“ in AEM Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-release/2410-0-release/whats-new-2024-10-0).

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
