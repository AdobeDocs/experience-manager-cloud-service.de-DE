---
title: Versionshinweise für Version 2024.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2024.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 75ecd154-112a-4468-9962-de50bb1f4cd0
source-git-commit: 1481983bde41bda51e725930bae492aa599b6c93
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 91%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2024.9.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2024.9.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2022 oder 2023 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.9.0) ist der 26. September 2024. Die nächste Version mit neuen Funktionen (2024.10.0) ist für den 31. Oktober 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2024.9.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version von September 2024:

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in Experience Manager Sites {#new-feature-sites}

#### Übersetzungs-Management {#translation-management}

AEM-Übersetzungs-Workflows und API-Aktionen lösen jetzt Ereignisse aus, um Einblicke in Statusänderungen von Übersetzungsaufträgen zu bieten. Benutzende können diese Ereignisse über die Adobe Developer Console abonnieren. Weitere Informationen zur AEM-Übersetzungs-Management-API finden Sie [hier](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/translation/).

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzen Sie GenAI über die neue Funktion [Varianten generieren](/help/generative-ai/generate-variations.md) von AEM, die jetzt in Cloud Service verfügbar ist. „Varianten generieren“ hilft Ihnen bei der Erstellung und Skalierung von Inhalten durch den Einsatz generativer KI. Wenden Sie sich an Ihr Adobe-Accountteam, um sich für das Programm zu erkundigen.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Early-Access-Funktion in Dynamic Media {#dm-early-access}

**KI-generierte Videountertitel**

Bei KI-generierten Videountertiteln in Adobe Dynamic Media wird künstliche Intelligenz eingesetzt, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion hat das Ziel, die Barrierefreiheit und das Benutzererlebnis zu verbessern, indem akkurate Untertitel in Echtzeit bereitgestellt werden. Die KI analysiert die Audiospur des Videos, um Sprache zu transkribieren und Untertitel zu erstellen, die zwecks Korrektheit oder Anpassung bearbeitet werden können. Diese Untertitel dienen der Barrierefreiheit und machen Videos für Zielgruppen attraktiver, die textbasierte Videounterstützung nutzen bzw. bevorzugen.

Um frühzeitig Zugang zur Unterstützung für KI-generierte Untertitel in Ihrem Dynamic Media-Konto zu erhalten, [erstellen und senden Sie eine Anfrage an den Adobe-Kunden-Support.](/help/assets/dynamic-media/video.md##enable-dash)

### Neue Funktionen in der Asset-Auswahl {#asset-selector-new-features}

Die Asset-Auswahl unterstützt jetzt das Durchsuchen von Sammlungen, um Ihr gewünschtes Asset zu finden.
![Sammlungen der Asset-Auswahl](/help/assets/assets/collections-rail-modal-view.png)

### Neue Funktionen in Content Hub {#content-hub-new-features}

Admins können jetzt steuern, ob abgelaufene Assets in Content Hub sichtbar sein sollen. Wenn die abgelaufenen Assets sichtbar gemacht werden, können sie auch festlegen, ob Benutzende diese herunterladen können.

![Abgelaufene Assets in Content Hub](/help/assets/assets/view-download-expired-assets.png)

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

### Verbesserungen {#improvements-fixes-cif}

* Kategorielimit anpassen.

### Fehlerbehebungen {#bug-fixes-cif}

* Commerce-Felder sind nicht ordnungsgemäß mit dem Metadatenschema-Editor von Assets integriert.
* Problem mit dem Karussell-Produkte-Multifield für Drag-and-Drop.
* Problem mit Karussellkategorie-Multifield für Drag-and-Drop.
* Ein-Klick funktioniert nicht für die Menüs in den Seiteninformationen auf der Kategorie- und Produkteditorseite.
* Die Bestellnummer ist nicht auf der Bestellbestätigungsseite sichtbar.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Edge Side Includes (ESI) für das Laden dynamischer Inhalte {#esi}

Das von Adobe verwaltete CDN unterstützt jetzt [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), eine Markup-Sprache für die dynamische Zusammenführung von Web-Inhalten auf Edge-Ebene. Durch die Einbeziehung von ESI-Snippets können Sie die gesamte HTML-Seite im CDN mit höheren TTLs zwischenspeichern und gleichzeitig diejenigen kleineren Abschnitte, die höhere Intervall-Updates (niedrigere TTLs) erfordern, öfter aus der Quelle abrufen. Diese Funktion wird schrittweise eingeführt.

### Grundlegende Authentifizierung im CDN {#basicauth-cdn}

Schützen Sie bestimmte Inhaltsressourcen mithilfe eines einfachen Authentifizierungsdialogfelds als Popup, das einen Benutzernamen und ein Passwort erforderlich macht. Diese Funktion ist in erster Linie für leichte Authentifizierungsfälle wie die Überprüfung von Inhalten durch geschäftliche Stakeholder und nicht als umfassende Lösung für Zugriffsrechte von Endbenutzenden gedacht. Die Liste der Benutzernamen und Kennwörter wird über eine Konfigurationsdatei in Git verwaltet, die über die Konfigurations-Pipeline bereitgestellt wird, mit einem Verweis auf Cloud Manager-Umgebungsvariablen vom Typ „Geheime Daten“. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

### Server-seitige Weiterleitungen {#server-side-redirects}

Deklarieren Sie [Browser-Umleitungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors) in einer Konfigurationsdatei für Git, die im CDN bereitgestellt und ausgewertet werden. Dies kann für Szenarien wie das Löschen von Seiten, eine geänderte Site-Struktur und die SEO-Optimierung nützlich sein.

### Neue AEM Developer Console (öffentliche Beta-Version) {#aem-developer-console-beta}

Probieren Sie die neu gestaltete [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) aus, die ein interaktiveres Erlebnis für das Debugging von Code in Cloud-Umgebungen bietet.

Jeder kann auf die öffentliche Beta-Version zugreifen, indem in der aktuellen AEM Developer Console auf die Schaltfläche *Neue Konsole verfügbar* geklickt wird. Adobe freut sich über Feedback, das Sie per E-Mail an **<aemcs-new-devconsole-ui-beta@adobe.com>** senden können.

![Bildschirm „OSGi-Bundles“ in AEM Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

### Business-Anwenderinnen und -Anwender können Umleitungen außerhalb von Git deklarieren (Early-Adopter-Programm) {#apache-rewritemaps-early-adopter}

Ähnlich wie bei AEM 6.5 nehmen Apache/Dispatcher Neuschreibungs-Zuordnungen auf, die an einem bestimmten Speicherort im Veröffentlichungs-Repository abgelegt werden, und laden sie, ohne dass eine Pipeline auf Web-Ebene ausgeführt werden muss. So können Business-Anwenderinnen und -Anwender Umleitungen mithilfe einer Tabelle oder einer Benutzeroberfläche deklarieren, z. B. mit ACS Commons Redirect Map Manager oder einer benutzerdefinierten Anwendung. Treten Sie dem Early-Adopter-Programm bei, indem Sie eine E-Mail an **<aemcs-cdn-config-adopter@adobe.com>** senden.

### Konfigurations-Pipeline für RDEs (Early-Adopter-Programm) {#config-pipeline-rdes-early-adopter}

Die [Konfigurations-Pipeline](/help/operations/config-pipeline.md) wird verwendet, um YAML-Dateikonfigurationen bereitzustellen, einschließlich CDN-Optionen (Traffic-Filterregeln, Anfrage-/Antworttransformationen usw.). Treten Sie dem Early-Adopter-Programm bei, indem Sie eine E-Mail an **<aemcs-cdn-config-adopter@adobe.com>** senden, um dieselben Konfigurationen für schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs) bereitzustellen, die eine CLI verwenden.

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
