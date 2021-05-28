---
title: Versionshinweise für Version 2021.3.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2021.3.0
source-git-commit: 3ff105507f4d42f5858a7e3a4c703d9135b36e5b
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 58%

---


# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.3.0 von [!DNL Adobe Experience Manager] wurde am 25. März 2021 veröffentlicht.
Die folgende Version (2021.4.0) wird am 29. April 2021 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* [Eine PWA-Version einer Website](/help/sites-cloud/authoring/features/enable-pwa.md) kann jetzt über eine einfache Konfiguration auf Projektebene aktiviert werden.
* Inhaltsfragmentmodellerweiterungen - jetzt ist es möglich, mehrzeilige Textdatentypen als Listen mit mehreren Feldern zu definieren.
* Verbesserungen des Inhaltsfragmente-Editors - verschachtelte untergeordnete Fragmente werden jetzt im Breadcrumb angezeigt und die Ansicht von Veröffentlichungs-, Speichern- und Speichern- und Ausstiegsaktionen wurde verbessert.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] erweitert die Funktion &quot;Connected Assets&quot;, um die Verwendung von  [!DNL Dynamic Media] Bildern in den unterstützten Kernkomponenten zu unterstützen. Siehe [Verwenden von Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md).
* Experience Manager-Administratoren können die Erfassung von Assets zu einem bestimmten Zeitpunkt planen. Administratoren können außerdem wiederkehrende Erfassungsvorgänge basierend auf Datum und Uhrzeit planen. Siehe [Massenaufnahme von Assets](/help/assets/add-assets.md#asset-bulk-ingestor).

### Fehlerbehebungen in [!DNL Assets] {#bug-fixes-assets}

* Die Copyright-Seite wird nicht angezeigt, wenn versucht wird, mehrere Assets herunterzuladen, die mit Rechten verwaltet werden. (CQ-4314403)
* Bei der Auswahl, eine INDD-Datei zu bearbeiten, ändert sich die Auflösung unerwartet. (CQ-4317376)
* Nur die letzte Seite der InDesign-Vorlage befindet sich in der PDF-Ausgabe. (CQ-4317305)
* Die Tag-Auswahl dauert lange, bis sie geöffnet wird, wenn die Auswahl Teil eines komplexen Metadatenschemas ist. (CQ-4316426)
* Beim Hochladen eines Assets mit demselben Dateinamen wie ein vorhandener wird das Dialogfeld für den Namenskonflikt nicht angezeigt, um den Benutzer aufzufordern, eine Version zu erstellen. (CQ-4315424)
* Die Eigenschaften von Ordnermetadaten können über das Popup-Menü auf der Eigenschaftsseite eines Ordners festgelegt und gespeichert werden. Während die Auswahl im Repository gespeichert wird, wird sie nicht angezeigt, wenn die Ordnermetadaten-Eigenschaften erneut geöffnet werden. (CQ-4314429)
* Assets mit Dateinamen, die Leerzeichen oder Sonderzeichen enthalten, werden über den Browser hochgeladen. (CQ-4318381)

## [!DNL Adobe Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

AEM Forms hat im Laufe der Jahre vielen Unternehmen dabei geholfen, großartige Onboarding- und Registrierungserfahrungen zu bieten. Diese Erlebnisse haben Unternehmen dabei geholfen, Leads in Verkäufe umzuwandeln, erfasste Kundendaten zu verarbeiten, responsive Erlebnisse basierend auf dem Zielgruppenprofil bereitzustellen und vieles mehr. AEM Forms ist jetzt als Cloud-Service verfügbar.

Sie können [AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) verwenden, um digitale Formulare zu erstellen, Formulare mit vorhandenen Datenquellen zu verbinden, Formulare mit Adobe Sign zu integrieren, E-Signaturen zu Formularen hinzuzufügen, Datensatzdokument (DoR) zu generieren, um gesendete Formulare als PDF-Dateien zu archivieren. Der Dienst kann auch Ihre bestehenden PDF forms in digitale Formulare konvertieren. Neben den standardmäßigen AEM Forms-Funktionen bietet der Dienst mehrere Cloud-native Funktionen wie automatische Skalierung, Ausfallzeiten bei Upgrades und Cloud-native Entwicklungsumgebungen. Lesen Sie [diesen Blogpost](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html) , um mehr über die Funktionen und Funktionen von AEM Forms as a Cloud Service zu erfahren.

Sie können sich an Ihren Kundenbetreuer wenden, um eine Demo zu erhalten oder sich für den Dienst anzumelden.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Unterstützung für Magento 2.4.2

* Die Produktdetailkomponente kann jetzt auf jeder Inhaltsseite verwendet und konfiguriert werden

* Freigabe der CIF Venia-Referenz-Website 2021.03.25, die die aktuelle CIF-Kernkomponenten Version 1.9.0 enthält. Weitere Informationen finden Sie unter [CIF Venia-Referenz-Website](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25).

* Version 1.9.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0).


## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0.

## Veröffentlichungsdatum {#release-date-cm-march}

Die Version 2021.3.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. März 2021 veröffentlicht.
Die nächste Version ist für den 08. April 2021 geplant.

### Neue Funktionen {#what-is-new-march}

* Kunden mit Umgebungen mit bereits bestehenden Konfigurationen für benutzerdefinierte Domain-Namen für [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) und [benutzerdefinierte Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) erhalten eine Meldung über ihre bereits bestehenden Konfigurationen und können diese über die Benutzeroberfläche selbst verwalten.

* Benutzer mit den erforderlichen Berechtigungen können jetzt ein Programm bearbeiten, sodass sie Folgendes selbstständig ausführen können:

   * Fügen Sie Sites-Lösungen zu einem vorhandenen Programm mit Assets hinzu oder umgekehrt.
   * Entfernen Sie Sites oder Assets aus einem vorhandenen Programm mit sowohl Sites als auch Assets.
   * Hinzufügen einer zweiten, nicht verwendeten Lösungsberechtigung entweder für ein vorhandenes Programm oder als neues Programm.

* Die Bezeichnung **AEM-Push-Updates** wird jetzt sowohl für die Bildschirme *Pipeline-Ausführung* als auch *Aktivität* angezeigt.

* Wenn eine Umgebung in den Ruhezustand versetzt wurde, aber auch ein AEM-Update verfügbar ist, hat der Status **Ruhezustand** Vorrang vor **Update verfügbar**.

* Die Benutzer können nun ihre Cloud Manager-Rolle(n) anzeigen, indem sie die Option „Cloud Manager-Rolle(n) anzeigen“ auswählen, nachdem sie zum Symbol „Benutzerprofil“ (oben rechts) der Unified Shell navigiert sind.

* Die Bezeichnung **Antrag auf Genehmigung** wurde aus Gründen der Klarheit in **Produktionsgenehmigung** umbenannt.

* Die Bezeichnung **Version** wurde im Ausführungsbildschirm der Produktions-Pipeline in **Git-Tag** umbenannt.

* Die Bezeichnungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr tatsächliches Verhalten widerzuspiegeln: **Sofort abbrechen** und **Sofort genehmigen**.

* Die Listen zum Entfernen von Klassen und Methoden wurden auf der Grundlage der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

* Die Cloud Manager-Produktions-Pipeline enthält jetzt die Funktion [Benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Fehlerbehebungen {#bug-fixes-cm-march}

* Die Paketversionierung wurde in einigen Fällen während AEM-Push-Aktualisierung übersprungen.

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* In unklaren Situationen kann der Standardprogrammname, der beim Öffnen des Dialogfelds „Programm hinzufügen“ generiert wird, ein Duplikat eines vorhandenen Programmnamens sein.

* Wenn der Benutzer unmittelbar nach dem Start einer Pipeline von der Seite für die Pipeline-Ausführung weg navigiert, wird gelegentlich eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich startet.

* Der Build-Schritt wurde unnötigerweise neu gestartet, wenn Kunden-Builds zu ungültigen Paketen führten.

* Gelegentlich wird dem Benutzer neben einer IP-Zulassungsliste möglicherweise ein grüner „aktiver“ Status angezeigt, auch wenn diese Konfiguration nicht bereitgestellt wurde.

* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 1.3.4 des Content Transfer Tool wurde am 19. März 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-ctt}

* CTT übersprungen Inhalte aus Ordnern mit demselben Namen, aber mit einem Bindestrich im Namen. Dieses Problem wurde behoben.

### Veröffentlichungsdatum {#release-date-ctt-march}

Das Content Transfer Tool 1.3.0 wurde am 4. März 2021 veröffentlicht.

### Neue Funktionen im Content Transfer Tool {#what-is-new-ctt-march}

* CTT wird jetzt in `/apps` anstatt in `/libs` installiert. Browser-Lesezeichen zu bestimmten Seiten sind möglicherweise nicht mehr gültig.
* Wenn CTT installiert ist, muss der Benutzer eine zusätzliche Ebene aufrufen, um zur Seite für den Inhaltstransfer zu gelangen. Weitere Informationen finden Sie unter [Verwenden des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de).

### Fehlerbehebungen {#bug-fixes-ctt-march}

* Beim Migrieren von Inhalten aus einem bestimmten Pfad zog CTT nicht verwandte Ressourcen ein. Dieses Problem wurde behoben

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Die Version 2.1.8 von Best Practices Analyzer wurde am 22. März 2021 veröffentlicht.

### Neue Funktionen in Best Practices Analyzer {#what-is-new-bpa}

* Möglichkeit, ACS Commons-Ergebnisse aus dem BPA-Bericht in der Benutzeroberfläche sowie aus dem als CSV-Datei exportierten Bericht herauszufiltern.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in den Code-Refaktorierungs-Tools {#what-is-new-crt}

* Neue Funktionen und Verbesserungen für Repository Modernizer. Die neueste Version finden Sie in der [GitHub-Ressource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).
   * Normalisieren von OSGi-Konfigurationen (außer RepoInit-Konfigurationen) auf das bevorzugte .cfg.json-Format.
   * Umbenennen von OSGi-Konfigurationsordnern in das angegebene Format.
   * Generieren des Projekts „ui.apps.structure“.
   * Erstellen des Analysemoduls.

* Neue Funktionen und Verbesserungen für Dispatcher Converter. Weitere Informationen finden Sie in der [GitHub-Ressource: Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter).
   * Erstellen von separaten Dateien für verschiedene Einschlüsse, anstatt Inhalte einzufügen.
   * Möglichkeit, sowohl den Ordnerpfad von vhosts als auch den Pfad zu vhost-Dateien zu verarbeiten.
   * Generieren von Farm-Dateien mit großen Kundenkonfigurationen im Bereich von 600 und mehr.
