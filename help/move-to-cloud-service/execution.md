---
title: Ausführungsphase
description: Ausführungsphase
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 15%

---


# Ausführung {#execution-phase}

Vor dem Beginn der Ausführungsphase sollten Sie an Bord des Cloud-Dienstes sein. Sie müssen sich auch mit Cloud Manager vertraut machen, da dies der einzige Mechanismus für die Bereitstellung von Code für den AEM Cloud-Dienst ist.

Cloud Manager ermöglicht Unternehmen die Selbstverwaltung von AEM in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen.

Weitere Informationen finden Sie in den folgenden Ressourcen:

* [Einstieg in Experience Manager als Cloud-Dienst](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/home.html) , um die Ressourcen zur Selbsthilfe zur Einbindung von Experience Manager als Cloud-Dienst zu verstehen.

* [Integration von Git mit Adobe Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) , um mehr über die Verwendung eines Single Git-Repositorys zur Bereitstellung von Code zu erfahren.

* [Adobe Experience as a Cloud-Dienstkonfiguration](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/security/ims-support.html#aem-configuration) , um mehr über die Verwaltung von Produkten und den Benutzerzugriff in der Admin-Konsole zu erfahren.


## Einführung {#introduction}

Die genauen Schritte Ihrer Transition zum Cloud-Dienst hängen von den erworbenen Systemen und den von Ihnen angewandten Verfahren zur Softwareentwicklung ab.

Die folgende Abbildung zeigt die wichtigsten Schritte in der Ausführungsphase:

![image](/help/move-to-cloud-service/assets/exec-image1.png)

## Inhaltsübertragung {#content-transfer}

Um Inhalte von Ihrer aktuellen AEM-Instanz auf Ihre Cloud-Dienstinstanz zu übertragen, können Sie das Adobe Content Transfer Tool verwenden.

Mit diesem Tool können Sie die gewünschte Inhaltsuntergruppe angeben, die Sie von Ihrer AEM-Quell-Instanz auf Ihre AEM Cloud-Dienstinstanz übertragen möchten.

>[!NOTE]
>Es wird empfohlen, häufige Differenzial-Content-Uploads durchzuführen, um die Einfrierzeit für Inhalte für die endgültige Übertragung von differenziellen Inhalten zu verkürzen, bevor Sie mit Cloud Service live gehen.

Weitere Informationen finden Sie im [Inhaltsübermittlungstool](/help/move-to-cloud-service/content-transfer-tool/overview-content-transfer-tool.md) .

>[!IMPORTANT]
>Die Mindestsystemanforderung für das Content Transfer Tool ist AEM 6.3 + und JAVA 8. Wenn Sie eine niedrigere AEM-Version verwenden, müssen Sie Ihr Inhalts-Repository auf AEM 6.5 aktualisieren, um das Content Transfer Tool verwenden zu können.

## Codeumgestaltung {#code-refactor}

Für das Entwickeln und Ausführen von Code in AEM als Cloud-Dienst ist eine Änderung der Einstellungen erforderlich. Es sollte beachtet werden, dass Code widerstandsfähig sein muss, zumal eine Instanz jederzeit gestoppt werden kann. Code, der in Cloud Service ausgeführt wird, muss wissen, dass er immer in einem Cluster ausgeführt wird. Das bedeutet, dass immer mehr als eine Instanz ausgeführt wird.

Für AEM Maven-Projekte sind bestimmte Änderungen erforderlich, um mit AEM als Cloud-Dienst kompatibel zu sein. AEM als Cloud-Dienst erfordert die Trennung von *Inhalt* und *Code* in separate Pakete zur Bereitstellung in AEM.

* `/apps` und `/libs` werden als unveränderliche Bereiche von AEM betrachtet, da sie nach dem Start von AEM (d. h. zur Laufzeit) nicht mehr geändert (erstellt, aktualisiert, gelöscht) werden können . Jeder Versuch, einen unveränderlichen Bereich zur Laufzeit zu ändern, schlägt fehl.

* Alles andere im Repository, `/content`, `/conf`, `/var`, `/home`, `/etc`, `/oak:index`, `/system`, `/tmp` usw. sind alles veränderliche Bereiche, d. h. sie können zur Laufzeit geändert werden.

Refer to [Recommended Package Structure](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#recommended-package-structure) for more details.

Es gibt einige zusätzliche Entwicklungsrichtlinien, die Sie beachten müssen, wenn Sie AEM als Cloud-Dienst entwickeln. Weitere Informationen finden Sie in den Richtlinien [zur Entwicklung von](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) AEM als Cloud-Dienst.

Ab der Planungsphase sollten Sie über eine Liste von Bereichen verfügen, die umgestaltet werden müssen, um mit Cloud Service kompatibel zu sein. Sie sollten auch die [Entwicklungsrichtlinien](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) lesen, um weitere Informationen dazu zu erhalten, wie Code für den Wechsel zum Cloud-Dienst umgerechnet und optimiert werden kann.

Um einige Aufgaben zur Codeumgestaltung zu beschleunigen, können Sie die folgenden Tools verwenden:

* [Migration zum Asset Workflow](/help/move-to-cloud-service/moving-to-aem-assets/asset-workflow-migration-tool.md)
* [Dispatcher Converter](/help/move-to-cloud-service/refactoring-tools/dispatcher-transformation-utility-tools.md)
* [Modernisierungstools](/help/move-to-cloud-service/refactoring-tools/aem-modernization-tools.md)

Es wird empfohlen, den Code lokal neu zu faktorieren und zu testen, bevor er über Cloud Manager Git in eine Cloud-Service-Umgebung getrieben wird.

Weitere Informationen finden Sie in der [AEM SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#aem-as-a-cloud-service-sdk) -Dokumentation.

Nachfolgend sind einige zusätzliche Ressourcen aufgeführt:

* Sehen Sie sich die Installation des Dispatcher SDK an, um zu erfahren, wie Sie Dispatcher SDK installieren:

   > [!VIDEO](https://video.tv.adobe.com/v/30601)

* Sehen Sie unter Dispatcher-SDK konfigurieren nach, um Informationen zum Konfigurieren des Dispatcher-SDK zu erhalten:

   > [!VIDEO](https://video.tv.adobe.com/v/30602)

* Überprüfen Sie die Dokumentation [zur Einrichtung](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) lokaler Entwicklungstools, um eine lokale Entwicklungs-Umgebung einzurichten.


Um Ihre laufende Codeentwicklung auf Ihrem aktiven AEM zusammen mit der Code-Refactoring-Aufgabe im Rahmen Ihrer Transition zu verwalten, wird empfohlen, einen Code-Freeze-Zeitraum einzuplanen, bis Sie die Umstrukturierung Ihres Maven-Projekts abgeschlossen haben, damit es mit AEM als Cloud-Dienst kompatibel ist.

Nach Abschluss der Projektumstrukturierung können Sie die neue Codeentwicklung auf der Grundlage dieser neuen Struktur fortsetzen. Dadurch werden Fehler in der Cloud Manager-Pipeline bei der Codebereitstellung und beim Testen reduziert.

>[!NOTE]
>Die Aufgaben &quot;Inhaltsübermittlung&quot;und &quot;Codeumformung&quot;wurden nicht sequenziell ausgeführt. Diese Aufgaben können unabhängig voneinander durchgeführt werden. Die richtige Projektstruktur ist jedoch erforderlich, um sicherzustellen, dass der Inhalt in Ihrer Cloud-Dienst-Umgebung erfolgreich wiedergegeben wird.

## Best Practices für die Codebereitstellung und das Testen {#best-practices}

Cloud Manager für Cloud Services -Pipeline-Ausführungen unterstützen die Ausführung von Tests, die für die Staging-Umgebung ausgeführt werden.

Informationen zum Schreiben von Testskripten und zur empfohlenen Abdeckung von mindestens 50 % finden Sie unter [Codequalitätstests](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/understand-test-results.html#code-quality-testing) .

Weitere Informationen zu benutzerspezifischen Code-Qualitätsregeln, die von Cloud Manager ausgeführt werden, der auf Best Practices von AEM Engineering basiert, finden Sie unter [Grundlegendes zu benutzerspezifischen Code-Qualitätsregeln](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/custom-code-quality-rules.html) .

Die Verwendung von Cloud Manager ist der einzige Mechanismus zur Bereitstellung von Code in Cloud-Service-Umgebung.

Gehen Sie wie folgt vor, um zu erfahren, wie Sie Ihren Code mit Cloud Manager verwalten und bereitstellen.

* [Verwalten von Umgebungen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html)

* [Konfigurieren der CI/CD-Pipeline](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html)

* [Bereitstellen des Codes](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html)

## Best Practices für die Go-Live-Vorbereitung {#go-live}

Um eine reibungslose und erfolgreiche Live-Übertragung auf AEM als Cloud-Dienst sicherzustellen, sollten Sie die folgenden Schritte in Erwägung ziehen:

* Planen des Code- und Einfrierzeitraums für Inhalte
* Endgültige Inhaltsauffüllung durchführen
* Vollständige Testdurchläufe
* Ausführen von Leistungs- und Sicherheitstests
* Überschneiden
