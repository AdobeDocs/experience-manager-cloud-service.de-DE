---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.12.0
description: Dies sind die Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2021.12.0.
feature: Release Information
source-git-commit: 6389dfaf1e4569a0e7bf2c6dbfa30bb003c4db5b
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 40%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.12.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2021.12.0 beschrieben.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version von Cloud Manager in AEM as a Cloud Service Version 2021.12.0 wurde am 16. Dezember 2021 veröffentlicht. Die nächste Version soll im Januar 2022 veröffentlicht werden.

### Neue Funktionen {#what-is-new}

* Der Commit-Hash, der bereits in der Benutzeroberfläche sichtbar ist, wird jetzt auch in der API bereitgestellt.
* Die Seite „Aktivitäten“ enthält jetzt ein Popup für die Ausführung von Pipelines, das eine Zusammenfassung der Pipelinedetails auf einen Blick bietet.
* Es wurden Aktualisierungen hinzugefügt, die zusätzliche Details enthalten, die auf der Seite „Aktivitäten“ beschrieben werden.
* Die Registerkarte „Lernen“ in Cloud Manager bietet jetzt schnellen Zugriff auf API-Handbücher und zugehörige Ressourcen.
* Ein Benutzer mit der Rolle „Implementierungs-Manager“ kann jetzt den Erstellungsassistenten für ein Projekt/eine Verzweigung für ein Repository ohne Verzweigungen über das Aktionsmenü auf der Seite „Repositorys“ starten.
* Der Implementierungs-Manager, der sich im Workflow zum Hinzufügen oder Bearbeiten einer Pipeline befindet, wird jetzt darüber informiert, wie eine Verzweigung oder ein Projekt erstellt werden kann, wenn das ausgewählte Repository keine Verzweigungen aufweist.
* Eine neue Cloud Manager-Self-Service-Funktion wurde hinzugefügt, um [Hinzufügen von Freiformvariablen und Geheimnissen auf Umgebungsebene.](/help/implementing/cloud-manager/environment-variables.md)
* Mit dem neuen [Referenz-Demos-Add-on](/help/journey-sites/demos-add-on/overview.md) (am 17. Dezember 2021 verfügbar) können die neuesten Democodegrundlagen für AEM Produkte installiert und für die Bereitstellung über die neue [Schnellerstellungs-Tool](/help/journey-sites/quick-site/overview.md) in Sites.
* Frontend-Pipelines unterstützen jetzt Pipelinevariablen.
* Screens kann jetzt im Dialogfeld Programmbearbeitung für alle Sandboxes aktiviert werden.
* Die Anleitungen, die von der Aktionskarte auf der Übersichtsseite bereitgestellt werden, wurden aktualisiert, um ihre Verbindung mit der vollständigen Produktions-Stack-Pipeline genau widerzuspiegeln.
* Die Seite &quot;Aktivität&quot;wurde erweitert, um zusätzliche Details zu Pipelines aufzurufen, einschließlich Quell-Code, Commit-ID usw.
* Beim Kopieren von TXT-Einträgen (&quot;TXT-Wert&quot;anstelle von &quot;TXT-Eintrag&quot;) wurde die Benutzeroberfläche geringfügig aktualisiert, um potenzielle Verwirrungen zu vermeiden.
* [Die Dokumentation zu Zertifikatfehlern](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-errors) wurde aktualisiert, um weitere Beispiele sowie Problembehebungsschritte zu enthalten.
* In der Frontend-Pipeline-Ausführung ist jetzt eine Option verfügbar, mit der sie vor der Bereitstellung in der Produktion abgelehnt oder genehmigt werden kann.
* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 32 aktualisiert.


### Fehlerbehebungen {#bug-fixes}

* Funktionale und UI-Test-Artefakte wurden nicht in das Build-Schritt-Protokoll aufgenommen.
* Auf die Protokolle für die Test-Schritte &quot;Produkt&quot;, &quot;Funktionen&quot;und &quot;Benutzeroberfläche&quot;konnte nicht über die öffentliche API zugegriffen werden.
* In seltenen Fällen ist der Link von der Umgebungsdetailseite zum Veröffentlichungs- oder Vorschaudienst nicht funktionsfähig.
* Full-Stack-Produktions-Pipelines erhalten weiterhin den Namen „Produktions-Pipeline“, selbst wenn der Benutzer einen anderen Namen in das Namensfeld eingibt.
