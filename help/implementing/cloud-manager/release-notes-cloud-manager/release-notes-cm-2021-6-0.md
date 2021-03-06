---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.6.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
feature: Release Information
exl-id: 9a0a53d3-31d4-493d-ba2e-b4bb22f60351
source-git-commit: 4b76fbbb1b58324065b39d6928027759b0897246
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.6.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.6.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.6.0 von Cloud Manager in AEM as a Cloud Service wurde am 10. Juni 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Der Vorschau-Service wird fortlaufend für alle Programme bereitgestellt. Kunden werden im Produkt benachrichtigt, wenn ihr Programm für den Vorschau-Service aktiviert ist. Weitere Informationen finden Sie unter [Zugriff auf den Vorschau-Service](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

* Maven-Abhängigkeiten, die während des Build-Schritts heruntergeladen wurden, werden jetzt zwischen Pipeline-Ausführungen zwischengespeichert. Diese Funktion wird in den nächsten Wochen für Kunden aktiviert.

* Der Name des Programms kann jetzt im Dialogfeld „Programm bearbeiten“ bearbeitet werden.

* Der standardmäßige Name der Verzweigung, der sowohl bei der Projekterstellung als auch im Standard-Push-Befehl über „Git-Workflows verwalten“ verwendet wird, wurde zu `main` geändert.

* Die Bearbeitung des Programmerlebnisses in der Benutzeroberfläche wurde aktualisiert.

* Die Qualitätsregel `ImmutableMutableMixCheck` wurde aktualisiert, um `/oak:index`-Knoten als unveränderlich zu klassifizieren.

* Die Qualitätsregeln `CQBP-84` und `CQBP-84--dependencies` wurden in einer einzigen Regel zusammengefasst. Im Rahmen dieser Konsolidierung werden beim Überprüfen von Abhängigkeiten Probleme in Abhängigkeiten von Drittanbietern genauer identifiziert, die zur AEM-Laufzeit bereitgestellt werden.

* Um Verwirrung zu vermeiden, wurden die Segmentzeilen „AEM veröffentlichen“ und „Dispatcher veröffentlichen“ auf der Seite „Umgebungsdetails“ konsolidiert.

   ![](/help/implementing/cloud-manager/release-notes-cloud-manager/assets/aem-dispatcher.png)

* Es wurde eine neue Code-Qualitätsregel hinzugefügt, um die Struktur von `damAssetLucene` -Indizes zu überprüfen. Weitere Informationen finden Sie unter [Benutzerdefinierte DAM-Asset Lucene-Oak-Indizes](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check).

* Auf der Seite „Umgebungsdetails“ werden jetzt mehrere Domain-Namen für Veröffentlichungs- und Vorschau-Services angezeigt (sofern zutreffend). Weitere Informationen finden Sie unter [Umgebungsdetails](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de#viewing-environment).

### Fehlerbehebungen {#bug-fixes}

* JCR-Knoten-Definitionen, die einen Zeilenumbruch nach dem Namen des Stammelements enthielten, werden jetzt korrekt geparst.

* Die List-Repositorys-API filtert jetzt auch gelöschte Repositorys.

* Wenn für den Zeitplanschritt ein ungültiger Wert angegeben wurde, wird jetzt die richtige Fehlermeldung angezeigt.

* Dem Benutzer wird neben einer IP-Zulassungsliste kein grüner *aktiver* Status mehr angezeigt, wenn diese Konfiguration nicht bereitgestellt wurde.

* Die Produktions-Pipeline wird nicht mehr durch Programmbearbeitungssequenzen an der Erstellung oder Bearbeitung gehindert.

* Einige Programmbearbeitungssequenzen konnten dazu führen, dass auf der Seite **Überblick** eine irreführende Meldung angezeigt wurde, die besagt, dass die Programmeinrichtung erneut auszuführen ist.
