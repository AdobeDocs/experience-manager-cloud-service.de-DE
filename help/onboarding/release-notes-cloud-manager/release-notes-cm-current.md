---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
feature: Versionshinweise
source-git-commit: 04195582602c0cb4cc6d359dff6abfc8dbc24614
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 15%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.6.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.6.0.

>[!NOTE]
>Um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen, klicken Sie auf [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.6.0 von Cloud Manager in AEM wurde am 10. Juni 2021 veröffentlicht.
Die nächste Version ist für den 15. Juli 2021 geplant.

### Neuigkeiten {#what-is-new}

* Der Vorschaudienst wird fortlaufend für alle Programme bereitgestellt. Kunden werden im Produkt benachrichtigt, wenn ihr Programm für den Vorschaudienst aktiviert ist. Weitere Informationen finden Sie unter [Zugriff auf den Vorschaudienst](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) .

* Maven-Abhängigkeiten, die während des Build-Schritts heruntergeladen wurden, werden jetzt zwischen Pipeline-Ausführungen zwischengespeichert. Diese Funktion wird in den nächsten Wochen für Kunden aktiviert.

* Der Name des Programms kann jetzt im Dialogfeld Programm bearbeiten bearbeitet werden.

* Der standardmäßige Zweigname, der sowohl bei der Projekterstellung als auch im Standard-Push-Befehl über Git-Workflows verwalten verwendet wird, wurde in `main` geändert.

* Die Bearbeitung des Programmerlebnisses in der Benutzeroberfläche wurde aktualisiert.

* Die Qualitätsregel `ImmutableMutableMixCheck` wurde aktualisiert, um `/oak:index` -Knoten als unveränderlich zu klassifizieren.

* Die Qualitätsregeln `CQBP-84` und `CQBP-84--dependencies` wurden in einer einzigen Regel zusammengefasst. Im Rahmen dieser Konsolidierung werden beim Überprüfen von Abhängigkeiten Probleme in Abhängigkeiten von Drittanbietern, die zur AEM Laufzeit bereitgestellt werden, genauer identifiziert.

* Um Verwirrung zu vermeiden, wurden die Segmentzeilen Veröffentlichen AEM und Veröffentlichen des Dispatchers auf der Seite Umgebungsdetails konsolidiert.

   ![](/help/onboarding/release-notes-cloud-manager/assets/aem-dispatcher.png)

* Es wurde eine neue Code-Qualitätsregel hinzugefügt, um die Struktur von `damAssetLucene` -Indizes zu überprüfen. Weitere Informationen finden Sie unter [Benutzerdefinierte DAM-Asset Lucene Oak-Indizes](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) .

* Auf der Seite &quot;Umgebungsdetails&quot;werden jetzt mehrere Domänennamen für Veröffentlichungs- und Vorschaudienste angezeigt (sofern zutreffend). Weitere Informationen finden Sie unter [Umgebungsdetails](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) .

### Fehlerbehebungen {#bug-fixes}

* JCR-Knotendefinitionen, die einen Zeilenumbruch enthalten, nachdem der Stammelementname nicht korrekt analysiert wurde.

* Die List-Repositorys-API filtert keine gelöschten Repositorys.

* Eine falsche Fehlermeldung wurde angezeigt, wenn für den Zeitplanschritt ein ungültiger Wert angegeben wurde.

* Gelegentlich kann der Benutzer neben einer IP-Zulassungsliste den grünen Status *active* sehen, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Einige Programmbearbeitungssequenzen können dazu führen, dass die Produktions-Pipeline nicht erstellt oder bearbeitet werden kann.

* Einige Programmbearbeitungssequenzen können dazu führen, dass auf der Seite **Übersicht** eine irreführende Meldung angezeigt wird, um die Programmeinrichtung erneut auszuführen.
