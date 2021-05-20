---
title: Versionshinweise für Version 2021.3.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2021.3.0
source-git-commit: 63b7c11683425cc20851ee5a16ee099511429b17
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 14%

---


# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] als Cloud Service.

>[!NOTE]
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Dokumentationsaktualisierungen, die nicht direkt mit einer Version in Zusammenhang stehen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

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

Sie können [AEM Forms as a Cloud Service](https://experienceleague.corp.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) verwenden, um digitale Formulare zu erstellen, Formulare mit vorhandenen Datenquellen zu verbinden, Formulare mit Adobe Sign zu integrieren, E-Signaturen zu Formularen hinzuzufügen, Datensatzdokument (DoR) zu generieren, um gesendete Formulare als PDF-Dateien zu archivieren. Der Dienst kann auch Ihre bestehenden PDF forms in digitale Formulare konvertieren. Neben den standardmäßigen AEM Forms-Funktionen bietet der Dienst mehrere Cloud-native Funktionen wie automatische Skalierung, Ausfallzeiten bei Upgrades und Cloud-native Entwicklungsumgebungen. Lesen Sie [diesen Blogpost](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html) , um mehr über die Funktionen und Funktionen von AEM Forms as a Cloud Service zu erfahren.

Sie können sich an Ihren Kundenbetreuer wenden, um eine Demo zu erhalten oder sich für den Dienst anzumelden.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Unterstützung für Magento 2.4.2

* Die Produktdetailkomponente kann jetzt auf jeder Inhaltsseite verwendet und konfiguriert werden

* Freigabe der CIF Venia-Referenz-Website 2021.03.25, die die aktuelle CIF-Kernkomponenten Version 1.9.0 enthält. Weitere Informationen finden Sie unter [CIF Venia-Referenz-Website](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25).

* Version 1.9.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0).


## Cloud Manager {#cloud-manager}

In diesem Abschnitt werden die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0 beschrieben.

## Veröffentlichungsdatum {#release-date-cm-march}

Die Version 2021.3.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. März 2021 veröffentlicht.
Die nächste Version ist für den 8. April 2021 geplant.

### Neue Funktionen {#what-is-new-march}

* Kunden mit Umgebungen mit bereits vorhandenen Konfigurationen für benutzerdefinierte Domänennamen für [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) und [Benutzerdefinierte Domänennamen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) sehen eine Meldung über ihre bisherigen Konfigurationen und können über die Benutzeroberfläche selbst versorgen.

* Benutzer mit den erforderlichen Berechtigungen können jetzt ein Programm bearbeiten, sodass sie Folgendes selbstständig erledigen können:

   * Fügen Sie Sites-Lösungen zu einem vorhandenen Programm mit Assets hinzu oder umgekehrt.
   * Entfernen Sie Sites oder Assets aus einem vorhandenen Programm mit sowohl Sites als auch Assets.
   * Fügen Sie eine zweite, nicht verwendete Lösungsberechtigung hinzu, entweder zu einem vorhandenen Programm oder als neues Programm.

* **AEM** Aktualisierungsfeld Push wird jetzt sowohl für die  *Pipeline-* Ausführung als auch für die  ** Aktivitätsbildschirme angezeigt.

* Wenn eine Umgebung in den Ruhezustand versetzt wird, aber auch eine AEM Aktualisierung verfügbar ist, hat der Status **Ruhezustand** Vorrang vor **Update verfügbar**.

* Benutzer können nun ihre Cloud Manager-Rollen sehen, indem sie die Option &quot;Cloud Manager-Rolle(n) anzeigen&quot;auswählen, nachdem sie zum Benutzerprofilsymbol (oben rechts) von Unified Shell navigiert sind.

* Der Titel **Antrag auf Genehmigung** wurde zur besseren Übersichtlichkeit in **Produktionsgenehmigung** umbenannt.

* Der Titel **Version** wurde im Bildschirm zur Ausführung der Produktions-Pipeline in **Git-Tag** umbenannt.

* Die Bezeichnungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr tatsächliches Verhalten widerzuspiegeln: **Sofort abbrechen** und **Sofort genehmigen**.

* Die Listen zur veralteten Klasse und Methode wurden basierend auf der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

* Die Cloud Manager-Produktions-Pipeline enthält jetzt die Funktion [Benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Fehlerbehebungen {#bug-fixes-cm-march}

* Die Paketversionierung wurde in einigen Fällen während AEM Push-Upgrades übersprungen.

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* In undurchsichtigen Situationen kann der beim Öffnen des Dialogfelds Programm hinzufügen generierte Standard-Programmname ein Duplikat eines vorhandenen Programmnamens sein.

* Wenn der Benutzer die Pipeline-Ausführungsseite gelegentlich unmittelbar nach dem Start einer Pipeline verlässt, wird eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich gestartet wird.

* Der Build-Schritt wurde unnötigerweise neu gestartet, wenn Kunden-Builds zu ungültigen Paketen führten.

* Gelegentlich kann der Benutzer einen grünen &quot;aktiven&quot;Status neben einer IP-Zulassungsliste sehen, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 1.3.4 des Content Transfer Tool wurde am 19. März 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-ctt}

* CTT übersprungen Inhalte aus Ordnern mit demselben Namen, aber mit einem Bindestrich im Namen. Dieses Problem wurde behoben.

### Veröffentlichungsdatum {#release-date-ctt-march}

Die Version 1.3.0 des Content Transfer Tool wurde am 4. März 2021 veröffentlicht.

### Neue Funktionen im Content Transfer Tool {#what-is-new-ctt-march}

* Die CTT installiert jetzt auf `/apps` anstelle von `/libs` Browser-Lesezeichen für bestimmte Seiten, möglicherweise sind sie nicht mehr gültig.
* Wenn CTT installiert ist, muss der Benutzer eine zusätzliche Ebene navigieren, um zur Seite Inhaltstransfer zu gelangen. Weitere Informationen finden Sie unter [Verwenden des Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) .

### Fehlerbehebungen {#bug-fixes-ctt-march}

* Beim Migrieren von Inhalten aus einem bestimmten Pfad zog CTT nicht verwandte Ressourcen ein. Dieses Problem wurde behoben

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Die Version 2.1.8 von Best Practices Analyzer wurde am 22. März 2021 veröffentlicht.

### Neue Funktionen in Best Practices Analyzer {#what-is-new-bpa}

* Möglichkeit, ACS Commons-Ergebnisse aus dem BPA-Bericht in der Benutzeroberfläche sowie aus dem als CSV-Datei exportierten Bericht herauszufiltern.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in Code-Refaktorierungs-Tools {#what-is-new-crt}

* Neue Funktionen und Verbesserungen für Repository Modernizer. Siehe [GitHub-Ressource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) für die neueste Version.
   * Normalisieren Sie OSGi-Konfigurationen (außer RepoInit-Konfigurationen) in das bevorzugte .cfg.json-Format.
   * Benennen Sie die OSGi-Konfigurationsordner in das angegebene Format um.
   * Generieren Sie das Projekt ui.apps.structure .
   * Erstellen Sie das Analysemodul.

* Neue Funktionen und Verbesserungen für Dispatcher Converter. Siehe [GitHub-Ressource: Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * Erstellung separater Dateien für verschiedene Einschlüsse anstelle des Auskleidens des Inhalts.
   * Möglichkeit, sowohl den Ordnerpfad von vhosts als auch den Pfad zu vhost-Dateien zu verarbeiten.
   * Generieren von Farm-Dateien mit großen Kundenkonfigurationen im Bereich von 600 und mehr.
