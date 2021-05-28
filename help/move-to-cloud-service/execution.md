---
title: Ausführungsphase
description: Ausführungsphase
exl-id: 176dd79d-0d72-443c-87db-dab24fb48b96
source-git-commit: dfbd0f38017d02810da05ccadbc5f2fbd5826aa3
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 96%

---

# Ausführung {#execution-phase}

Bevor Sie mit der Ausführungsphase beginnen, sollten Sie Cloud Service integriert haben. Sie müssen sich auch mit Cloud Manager vertraut machen, da dies der einzige Mechanismus für die Bereitstellung von Code für AEM Cloud Service ist.

Cloud Manager ermöglicht Unternehmen die Selbstverwaltung von AEM in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen.

Weitere Informationen finden Sie in den folgenden Ressourcen:

* [Einstieg in Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/onboarding/home.html), um sich mit den Selbsthilferessourcen beim Einstieg in Experience Manager as a Cloud Service vertraut zu machen.

* [Integration von Git mit Adobe Cloud Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html), um mehr über die Verwendung eines Single Git-Repositorys zur Bereitstellung von Code zu erfahren.

* [Konfiguration von Adobe Experience as a Cloud Service ](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/security/ims-support.html#aem-configuration), um mehr über die Verwaltung von Produkten und den Benutzerzugriff in Admin Console zu erfahren.


## Einführung {#introduction}

Die genauen Schritte für die Umstellung auf Cloud Service hängen von den von Ihnen erworbenen Systemen und den von Ihnen befolgten Lebenszykluspraktiken für die Software-Entwicklung ab.

Die folgende Abbildung zeigt die wichtigsten Schritte in der Ausführungsphase:

![image](/help/move-to-cloud-service/assets/exec-image1.png)

## Inhaltstransfer {#content-transfer}

Um Inhalte von Ihrer aktuellen AEM-Instanz zu Ihrer Cloud Service-Instanz zu übertragen, können Sie das Adobe Content Transfer-Tool verwenden.

Mit diesem Tool können Sie die gewünschte Teilmenge Ihres Inhalts angeben, die Sie von Ihrer AEM-Quellinstanz auf Ihre AEM Cloud Service-Instanz übertragen möchten.

>[!NOTE]
>Es wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor der Cloud Service live geschaltet wird.

Weitere Informationen finden Sie unter [Content Transfer-Tool ](/help/move-to-cloud-service/content-transfer-tool/overview-content-transfer-tool.md).

>[!IMPORTANT]
>Die Systemanforderungen für das Content Transfer-Tool sind AEM 6.3 + und JAVA 8. Wenn Sie eine niedrigere AEM-Version verwenden, müssen Sie Ihr Content-Repository auf AEM 6.5 aktualisieren, um das Content Transfer-Tool verwenden zu können.

## Code-Umgestaltung {#code-refactor}

Für das Entwickeln und Ausführen von Code in AEM as a Cloud Service ist eine Änderung der Einstellungen erforderlich. Beachten Sie, dass der Code robust sein muss, insbesondere da eine Instanz jederzeit gestoppt werden kann. Code, der in Cloud Service ausgeführt wird, muss wissen, dass er immer in einem Cluster ausgeführt wird. Das bedeutet, dass immer mehr als eine Instanz ausgeführt wird.

Für AEM Maven-Projekte sind bestimmte Änderungen erforderlich, um mit AEM as a Cloud Service kompatibel zu sein. AEM as a Cloud Service erfordert für die Bereitstellung in AEM die Trennung von *Inhalt* und *Code* in separate Pakete.

* `/apps` und `/libs` werden als unveränderliche Bereiche von AEM betrachtet, da sie nach dem Start von AEM (d. h. zur Laufzeit) nicht mehr geändert (erstellt, aktualisiert, gelöscht) werden können . Jeder Versuch, einen unveränderlichen Bereich zur Laufzeit zu ändern, schlägt fehl.

* Alles andere im Repository, `/content`, `/conf`, `/var`, `/home`, `/etc`, `/oak:index`, `/system`, `/tmp` usw. sind alles veränderliche Bereiche, d. h. sie können zur Laufzeit geändert werden.

Weitere Informationen finden Sie unter [Empfohlene Paketstruktur](https://docs.adobe.com/content/help/de=DE/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#recommended-package-structure).

Es gibt einige zusätzliche Entwicklungsrichtlinien, die Sie beachten müssen, wenn Sie in AEM as a Cloud Service entwickeln. Weitere Informationen finden Sie in den [Entwicklungsrichtlinien für AEM as a Cloud Service](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/developing/development-guidelines.html).

Bereits in der Planungsphase sollten Sie über eine Liste von Bereichen verfügen, die überarbeitet werden müssen, damit sie mit Cloud Service kompatibel sind. Weitere Informationen zum Umgestalten und Optimieren von Code für die Umstellung auf Cloud Service finden Sie in den [Entwicklungsrichtlinien](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html).

Um einige Aufgaben zur Code-Umgestaltung zu beschleunigen, können Sie die folgenden Tools verwenden:

* [Asset-Workflow-Migration](/help/move-to-cloud-service/moving-to-aem-assets/asset-workflow-migration-tool.md)
* [Dispatcher Converter](/help/move-to-cloud-service/refactoring-tools/dispatcher-transformation-utility-tools.md)
* [Modernisierungs-Tools](/help/move-to-cloud-service/refactoring-tools/aem-modernization-tools.md)

Es wird empfohlen, den Code lokal umzugestalten und zu testen, bevor er über Cloud Manager Git in eine Cloud Service-Umgebung übertragen wird.

Weitere Informationen finden Sie in der Dokumentation zum [AEM-SDK](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/deploying/overview.html#aem-as-a-cloud-service-sdk).

Nachfolgend sind einige zusätzliche Ressourcen aufgeführt:

* Sehen Sie sich „Installieren des Dispatcher-SDK“ an, um zu verstehen, wie das Dispatcher-SDK installiert wird:

   >[!VIDEO](https://video.tv.adobe.com/v/30601)

* Sehen Sie sich „Konfigurieren des Dispatcher-SDK“ an, um zu verstehen, wie Dispatcher-SDK konfiguriert wird:

   >[!VIDEO](https://video.tv.adobe.com/v/30602)

* Lesen Sie die Dokumentation zur [Einrichtung der lokalen Entwicklung](https://docs.adobe.com/content/help/de-DE/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html), um eine lokale Entwicklungsumgebung einzurichten


Um Ihre laufende Code-Entwicklung in Ihrem aktiven AEM zusammen mit der Code-Umgestaltung als Teil Ihrer Umstellung zu verwalten, wird empfohlen, eine Code-Freeze-Periode einzuplanen, bis Sie die Umstrukturierung Ihres Maven-Projekts abgeschlossen haben, um mit AEM as a Cloud Service kompatibel zu sein.

Sobald die Projektumstrukturierung abgeschlossen ist, können Sie die Entwicklung neuen Codes anhand dieser neuen Struktur fortsetzen. Dadurch werden Cloud Manager-Pipeline-Fehler während der Code-Bereitstellung und des Testens reduziert.

>[!NOTE]
>Die Aufgaben zum Inhaltstransfer und zur Code-Umgestaltung müssen nicht sequenziell ausgeführt werden. Diese Aufgaben können unabhängig voneinander ausgeführt werden. Die richtige Projektstruktur ist jedoch erforderlich, um sicherzustellen, dass der Inhalt in Ihrer Cloud Service-Umgebung erfolgreich gerendert wird.

## Best Practices für die Bereitstellung und das Testen von Code {#best-practices}

Cloud Manager für Cloud Services-Pipeline-Ausführungen unterstützen die Ausführung von Tests, die für die Staging-Umgebung ausgeführt werden.

Weitere Informationen zum Schreiben von Testskripten und zur empfohlenen Abdeckung von mindestens 50 % finden Sie unter [Testen der Code-Qualität](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/developing/understand-test-results.html#code-quality-testing).

Weitere Informationen zu benutzerspezifischen Regeln für die Code-Qualität, die von Cloud Manager ausgeführt werden und auf der Grundlage von Best Practices von AEM Engineering erstellt wurden, finden Sie unter [Grundlegendes zu benutzerspezifischen Regeln für die Code-Qualität](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/using-cloud-manager/custom-code-quality-rules.html).

Die Verwendung von Cloud Manager ist der einzige Mechanismus zur Bereitstellung von Code in Cloud Service-Umgebungen.

Folgen Sie den unten stehenden Ressourcen, um zu erfahren, wie Sie Cloud Manager zur Verwaltung und Bereitstellung Ihres Codes verwenden können.

* [Verwalten von Umgebungen](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html)

* [Konfigurieren der CI/CD-Pipeline](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html)

* [Bereitstellen des Codes](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html)

## Best Practices für die Vorbereitung der Live-Schaltung {#go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_prep"
>title="Vorbereitung der Live-Schaltung"
>abstract="Um eine reibungslose und erfolgreiche Live-Schaltung von AEM als Cloud Service sicherzustellen, sollten Sie Code- und Inhaltsfrierzeiträume, Testdurchläufe, Content-Upups, Leistungstests, Sicherheitstests und mehr planen."

Um eine reibungslose und erfolgreiche Live-Schaltung von AEM as a Cloud Service sicherzustellen, sollten Sie die folgenden Schritte ausführen:

* Planen der Freeze-Periode von Code und Inhalt
* Ausführen der endgültigen Inhaltsauffüllung
* Abschließen der Testiterationen
* Ausführen von Leistungs- und Sicherheitstests
* Umstellen
