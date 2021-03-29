---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
translation-type: tm+mt
source-git-commit: 8331ecb0797f878067a4f83d97e6ec2f62bb551a
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 14%

---


# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (aktuelle) Version von [!DNL Experience Manager] als Cloud Service erläutert.

>[!NOTE]
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Letzte Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!DNL Adobe Experience Manager] als Cloud Service 2021.3.0 ist der 25. März 2021.
Die folgende Version (2021.4.0) wird am 29. April 2021 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* [Eine PWA-Version einer Website](/help/sites-cloud/authoring/features/enable-pwa.md) kann jetzt über eine einfache Konfiguration auf Projektebene aktiviert werden.
* Erweiterungen des Inhaltsfragmentmodells - jetzt können mehrzeilige Textdatentypen als Listen mit mehreren Feldern definiert werden.
* UX-Erweiterungen im Content Fragment Editor - verschachtelte untergeordnete Fragmente werden jetzt in Breadcrumb angezeigt und die Ansicht der Aktionen zum Veröffentlichen, Speichern und Speichern und Beenden wurde verbessert.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] erweitert die Funktion &quot;Connected Assets&quot;, um die Verwendung von  [!DNL Dynamic Media] Bildern in den unterstützten Kernkomponenten zu unterstützen. Siehe [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md) verwenden.
* Experience Manager-Administratoren können die Erfassung von Massenelementen zu einem bestimmten Zeitpunkt planen. Administratoren können außerdem wiederholte Erfassungsvorgänge auf der Grundlage von Datum und Uhrzeit planen. Siehe [Erfassung von Massenelementen](/help/assets/add-assets.md#asset-bulk-ingestor).

### Fehlerbehebungen in [!DNL Assets] {#bug-fixes-assets}

* Die Copyright-Seite wird nicht angezeigt, wenn versucht wird, mehrere durch Rechte verwaltete Assets herunterzuladen. (CQ-4314403)
* Wenn Sie sich entscheiden, eine INDD-Datei zu bearbeiten, ändert sich die Auflösung unerwartet. (CQ-4317376)
* Nur die letzte Seite der InDesign-Vorlage befindet sich in der PDF-Darstellung. (CQ-4317305)
* Die Tag-Auswahl dauert lange, bis sie geöffnet wird, wenn die Auswahl zu einem komplexen Metadaten-Schema gehört. (CQ-4316426)
* Beim Hochladen von Assets mit demselben Dateinamen wie eine vorhandene wird das Dialogfeld zum Namenskonflikt nicht angezeigt, um den Benutzer zum Erstellen einer Version aufzufordern. (CQ-4315424)
* Eigenschaften von Ordnern-Metadaten können im Popupmenü auf der Seite Eigenschaften eines Ordners festgelegt und gespeichert werden. Während die Auswahl im Repository gespeichert wird, wird sie nicht angezeigt, wenn die Metadateneigenschaften des Ordners erneut geöffnet werden. (CQ-4314429)
* Assets mit Dateinamen, die Leerzeichen oder Sonderzeichen enthalten, werden über den Browser hochgeladen. (CQ-4318381)

## [!DNL Adobe Experience Manager Forms] als  [!DNL Cloud Service] {#forms}

AEM Forms hat im Laufe der Jahre vielen Unternehmen dabei geholfen, großartige Einstiegs- und Registrierungserfahrungen zu machen. Diese Erlebnisse haben Unternehmen dabei unterstützt, Interessenten in Verkäufe umzuwandeln, erfasste Kundendaten zu verarbeiten, reaktionsfähige Erlebnisse basierend auf dem Profil der Audience bereitzustellen und vieles mehr. AEM Forms ist jetzt als Cloud-Dienst verfügbar.

Sie können [AEM Forms als Cloud Service](https://experienceleague.corp.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) verwenden, um digitale Formulare zu erstellen, Formulare mit vorhandenen Datenquellen zu verbinden, Formulare mit Adobe Sign zu integrieren und E-Signaturen zu Formularen hinzuzufügen, Dokument aus Datensatz (DoR) zu generieren, um gesendete Formulare als PDF-Dateien zu archivieren. Der Dienst kann auch Ihre vorhandenen PDF forms in digitale Formulare konvertieren. Zusätzlich zu den standardmäßigen AEM Forms-Funktionen bietet der Dienst mehrere Cloud-native Funktionen wie automatische Skalierung, kostenlose Ausfallzeiten für Upgrades und Cloud-native Umgebung für die Entwicklung. Lesen Sie [diesen Blog-Beitrag](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html), um mehr über die Funktionen und Funktionen von AEM Forms als Cloud Service zu erfahren.

Sie können sich an Ihren Kundenbetreuer wenden, um eine Demo zu erhalten oder sich für den Service zu registrieren.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Unterstützung für Magento 2.4.2

* Die Produktdetailkomponente kann jetzt auf jeder Inhaltsseite verwendet und konfiguriert werden

* Freigabe der CIF Venia-Referenz-Website 2021.03.25, die die aktuelle CIF-Kernkomponenten Version 1.9.0 enthält. Weitere Informationen finden Sie unter [CIF Venia-Referenz-Website](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25).

* Version 1.9.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0).


## Cloud Manager {#cloud-manager}

In diesem Abschnitt werden die Versionshinweise für Cloud Manager in AEM als Cloud Service 2021.3.0 beschrieben.

### Veröffentlichungsdatum {#release-date-cm-march}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2021.3.0 ist der 11. März 2021.
Die nächste Version ist für den 08. April 2021 geplant.

### Neue Funktionen {#what-is-new-march}

* Kunden mit Umgebung mit bereits vorhandenen Konfigurationen für benutzerdefinierte Domänennamen für [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) und [Benutzerspezifische Domänennamen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) erhalten eine Meldung über ihre vorherigen Konfigurationen und können sich über die Benutzeroberfläche selbst versorgen.

* Benutzer mit erforderlichen Berechtigungen können jetzt ein Programm bearbeiten, sodass sie Folgendes selbstständig ausführen können:

   * hinzufügen Sites-Lösung auf ein vorhandenes Programm mit Assets oder umgekehrt.
   * Entfernen Sie Sites oder Assets aus einem vorhandenen Programm mit sowohl Sites als auch Assets.
   * hinzufügen zweite, nicht verwendete Lösungsberechtigung entweder für ein vorhandenes Programm oder als neues Programm.

* **AEM Push-** Aktualisierungsbildschirm wird jetzt sowohl für  *Pipeline-* Ausführung als auch für  ** Aktivitäten angezeigt.

* Wenn eine Umgebung ausgeblendet wird, aber auch ein AEM Update verfügbar ist, hat der Status **Hibernated** Vorrang vor **Update available**.

* Die Benutzer können nun ihre Cloud Manager-Rolle(en) anzeigen, indem sie die Option &quot;Ansicht Cloud Manager-Rolle(en)&quot;wählen, nachdem sie zum Symbol &quot;User Profil&quot;(oben rechts) von Unified Shell navigiert sind.

* Die Beschriftung **Antrag auf Genehmigung** wurde zur besseren Klarheit in **Produktionsgenehmigung** umbenannt.

* Die Beschriftung **Version** wurde im Bildschirm &quot;Produktions-Pipeline-Ausführung&quot;in **Git-Tag** umbenannt.

* Die Beschriftungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr wahres Verhalten widerzuspiegeln: **Sofort abbrechen** und **Sofort genehmigen**.

* Die Listen zum Entfernen von Klassen und Methoden wurden auf der Grundlage der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

* Die Cloud Manager-Produktionspipeline umfasst jetzt die Funktion [Benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Fehlerbehebungen {#bug-fixes-cm-march}

* Die Paketversion wurde in einigen Fällen während AEM Push-Aktualisierung übersprungen.

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* In undurchsichtigen Situationen kann der beim Öffnen des Dialogfelds &quot;Hinzufügen Programm&quot;generierte Standardname für das Programm ein Duplikat eines vorhandenen Programms sein.

* Wenn der Benutzer unmittelbar nach dem Start einer Pipeline von der Seite für die Ausführung der Pipeline wegnavigiert, wird gelegentlich eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich Beginn ist.

* Der Build-Schritt wurde unnötigerweise neu gestartet, wenn Kundenbuilds zu ungültigen Paketen führten.

* Gelegentlich wird dem Benutzer auch dann ein grüner &quot;aktiver&quot;Status neben einer IP-Zulassungsliste angezeigt, wenn diese Konfiguration nicht bereitgestellt wurde.

* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt}

Das Veröffentlichungsdatum für das Inhaltsübermittlungswerkzeug v1.3.4 ist der 19. März 2021.

### Fehlerbehebungen {#bug-fixes-ctt}

* CTT übersprungen Inhalte aus Ordnern mit demselben Namen, jedoch mit einem Bindestrich im Namen. Dieses Problem wurde behoben.

### Veröffentlichungsdatum {#release-date-ctt-march}

Das Veröffentlichungsdatum für das Inhaltsübermittlungstool v1.3.0 ist der 04. März 2021.

### Neue Funktionen in Content Transfer Tool {#what-is-new-ctt-march}

* CTT installiert nun auf `/apps` anstelle von `/libs` Browser-Lesezeichen auf bestimmten Seiten möglicherweise nicht mehr gültig.
* Wenn CTT installiert ist, muss der Benutzer eine zusätzliche Ebene aufrufen, um zur Seite &quot;Content Transfer&quot;zu gelangen. Weitere Informationen finden Sie unter [Inhaltsübermittlungstool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) verwenden.

### Fehlerbehebungen {#bug-fixes-ctt-march}

* Beim Migrieren von Inhalten aus einem bestimmten Pfad zog CTT nicht verwandte Ressourcen ein. Dieses Problem wurde behoben

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Das Veröffentlichungsdatum für Best Practices Analyzer v2.1.8 ist der 22. März 2021.

### Neue Funktionen in Best Practices Analyzer {#what-is-new-bpa}

* Möglichkeit, ACS-Commons-Ergebnisse aus dem BPA-Bericht in der Benutzeroberfläche sowie aus dem als CSV-Datei exportierten Bericht herauszufiltern.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in den Code Refactoring Tools {#what-is-new-crt}

* Neue Funktionen und Verbesserungen für Repository Modernizer. Siehe [GitHub-Ressource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) für die neueste Version.
   * Normalisieren Sie OSGi-Konfigurationen (außer RepoInit-Konfigurationen) auf das bevorzugte .cfg.json-Format.
   * Benennen Sie OSGi-Konfigurationsordner in das angegebene Format um.
   * Generieren Sie das Projekt ui.apps.structure.
   * Erstellen Sie das Analysemodul.

* Neue Funktionen und Verbesserungen für Dispatcher Converter. Siehe [GitHub-Ressource: Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * Erstellen von separaten Dateien für verschiedene Einschlüsse anstelle der Auskleidung des Inhalts.
   * Möglichkeit, sowohl den Ordnerpfad von vhosts als auch den Pfad zu vhost-Dateien zu verarbeiten.
   * Generieren von Bauerndateien mit großen Kundenkonfigurationen im Bereich von 600 und mehr.
