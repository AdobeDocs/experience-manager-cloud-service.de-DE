---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 894c5df2cdc6637bae9b4b8f2cbdd1f1162b3942
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 68%

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

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.9.0) ist der Freitag, 26. September 2024. Die nächste Version mit neuen Funktionen (2024.10.0) ist für den Freitag, 31. Oktober 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!--  ## Release Video {#release-video}

Have a look at the September 2024 Release Overview video for a summary of the features added in the 2024.9.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3433381?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in Experience Manager Sites {#new-feature-sites}

#### Übersetzungsmanagement {#translation-management}

AEM Übersetzungs-Workflows und API-Aktionen jetzt Trigger-Ereignisse, um Einblicke in die Zustandsänderungen von Übersetzungsaufträgen zu erhalten. Benutzer können diese Ereignisse über die Adobe Developer Console abonnieren. Weitere Informationen zur AEM Übersetzungsmanagement-API finden Sie unter [hier](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/translation/) .

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzen Sie GenAI über die neue Funktion [Varianten generieren](/help/generative-ai/generate-variations.md) von AEM, die jetzt in Cloud Service verfügbar ist. „Varianten generieren“ hilft Ihnen bei der Erstellung und Skalierung von Inhalten durch den Einsatz generativer KI. Wenden Sie sich an Ihr Adobe-Accountteam, um sich für das Programm zu erkundigen.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Early-Access-Funktion in Dynamic Media {#dm-early-access}

**KI-generierte Videountertitel**

Bei KI-generierten Videountertiteln in Adobe Dynamic Media wird künstliche Intelligenz eingesetzt, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion soll die Barrierefreiheit und das Benutzererlebnis verbessern, indem akkurate Untertitel in Echtzeit bereitgestellt werden. Die KI analysiert die Audiospur des Videos, um Sprache zu transkribieren und Untertitel zu erstellen, die zwecks Korrektheit oder Anpassung bearbeitet werden können. Diese Untertitel dienen der Barrierefreiheit und machen Videos für Zielgruppen attraktiver, die textbasierte Videounterstützung nutzen bzw. bevorzugen.

Um frühzeitig Zugang zur Unterstützung für KI-generierte Untertitel in Ihrem Dynamic Media-Konto zu erhalten, [erstellen und senden Sie eine Anfrage an den Adobe-Kunden-Support.](/help/assets/dynamic-media/video.md##enable-dash)

### Neue Funktionen in der Asset-Auswahl {#asset-selector-new-features}

Der Asset-Selektor unterstützt jetzt das Durchsuchen von Sammlungen, um Ihr gewünschtes Asset zu finden.
![Sammlungen des Asset-Wählers](/help/assets/assets/collections-rail-modal-view.png)

### Neue Funktionen in Content Hub {#content-hub-new-features}

Administratoren können jetzt steuern, ob abgelaufene Assets in Content Hub sichtbar sein sollen. Wenn die abgelaufenen Assets sichtbar gemacht werden, können sie auch definieren, ob Benutzer sie herunterladen können.

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

* Kategoriebegrenzung anpassen.

### Fehlerbehebungen {#bug-fixes-cif}

* Commerce-Felder sind nicht ordnungsgemäß mit dem Assets-Metadatenschema-Editor integriert.
* Problem mit dem Multifield für Karussellprodukte für Drag &amp; Drop.
* Problem mit Karussellkategorie-Multifield für Drag &amp; Drop.
* Ein Klick funktioniert nicht für die Menüs auf der Seite Seiteninformationen auf der Kategorie- und Produkt-Editor-Seite.
* Die Bestellnummer ist auf der Bestellbestätigungsseite nicht sichtbar.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Edge Side Includes (ESI) zum Laden dynamischer Inhalte {#esi}

Das von Adobe verwaltete CDN unterstützt jetzt [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), eine Markup-Sprache für die dynamische Zusammenführung von Web-Inhalten auf Edge-Ebene. Durch die Einbeziehung von ESI-Snippets können Sie die gesamte HTML-Seite im CDN mit höheren TTLs zwischenspeichern und gleichzeitig diejenigen kleineren Abschnitte, die höhere Intervall-Updates (niedrigere TTLs) erfordern, öfter aus der Quelle abrufen. Diese Funktion wird schrittweise eingeführt.

### Grundlegende Authentifizierung im CDN {#basicauth-cdn}

Schützen Sie bestimmte Inhaltsressourcen mithilfe eines einfachen Authentifizierungsdialogfelds als Popup, das einen Benutzernamen und ein Passwort erforderlich macht. Diese Funktion ist in erster Linie für leichte Authentifizierungsfälle wie die Überprüfung von Inhalten durch geschäftliche Stakeholder und nicht als umfassende Lösung für Zugriffsrechte von Endbenutzenden gedacht. Die Liste der Benutzernamen und Kennwörter wird über eine Konfigurationsdatei in Git verwaltet, die über die Config Pipeline bereitgestellt wird, mit einem Verweis auf die Cloud Manager-Umgebungsvariablen des geheimen Typs. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

### Clientseitige Umleitungen {#client-side-redirects}

Deklarieren Sie [Browserumleitungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) in einem Konfigurationsdatei-Git, das im CDN bereitgestellt und ausgewertet wird. Dies kann für Szenarien nützlich sein, z. B. das Löschen von Seiten, die Änderung der Site-Struktur und die SEO-Optimierung.

### Neue AEM Developer Console (Public Beta) {#aem-developer-console-beta}

Probieren Sie ein umgestaltetes [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) aus, das ein interaktiveres Erlebnis für das Debugging von Code in Cloud-Umgebungen bietet.

Jeder kann auf die öffentliche Beta-Version zugreifen, indem er in der aktuellen AEM Developer Console auf die Schaltfläche *Neue verfügbare Konsole* klickt. Adobe begrüßt Feedback, das Sie per E-Mail an **<aemcs-new-devconsole-ui-beta@adobe.com>** senden können.

![OSGi-Paketbildschirm in AEM Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

### Business-Anwenderinnen und -Anwender können Umleitungen außerhalb von Git deklarieren (Early-Adopter-Programm) {#apache-rewritemaps-early-adopter}

Ähnlich wie AEM 6.5 erfasst Apache/Dispatcher Umschreibungen, die an einem bestimmten Speicherort im Publishing-Repository platziert werden, und lädt sie, ohne dass eine Pipeline auf der Web-Ebene ausgeführt werden muss. Mit diesem Ansatz können Geschäftsbenutzer Umleitungen mithilfe einer Tabelle oder einer Benutzeroberfläche deklarieren, z. B. ACS Commons Redirect Map Manager oder einer benutzerdefinierten Anwendung. Treten Sie dem frühen Adopter-Programm bei, indem Sie **<aemcs-cdn-config-adopter@adobe.com>** per E-Mail versenden.

### Konfigurieren einer Pipeline für RDE (Frühkindliche Betreuung, Betreuung und Betreuung) {#config-pipeline-rdes-early-adopter}

Die [Konfigurations-Pipeline](/help/operations/config-pipeline.md) wird verwendet, um YAML-Dateikonfigurationen bereitzustellen, einschließlich CDN-Optionen (Traffic-Filterregeln, Anforderung-/Antworttransformationen usw.). Treten Sie dem frühen Adopter-Programm bei, indem Sie **<aemcs-cdn-config-adopter@adobe.com>** per E-Mail versenden, um dieselben Konfigurationen für RDEs (Rapid Development Environments) bereitzustellen, die eine CLI verwenden.

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
