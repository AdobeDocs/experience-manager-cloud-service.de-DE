---
title: Dynatrace OneAgent
description: Erfahren Sie, wie Sie Dynatracs OneAgent mit AEM as a Cloud Service verwenden.
source-git-commit: 2e70c8be73915bea860b98e02c08772bb4f5dcd2
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Dynatrace OneAgent {#dynatrace-oneagent}

Adobe bietet die Möglichkeit, den OneAgent von Dynatrace zu verwenden, um AEM im Rahmen einer Unternehmensimplementierung as a Cloud Service zu überwachen, die Ursache potenzieller Probleme zu ermitteln und Maßnahmen zu ergreifen, um diese bei Bedarf zu beheben. <!-- When GA, add: Read this [Dynatrace article](https://www.dynatrace.com/hub/detail/adobe-experience-manager/) about AEM monitoring to learn more. -->

## Integration von OneAgent in AEM as a Cloud Service {#integrating-oneagent-with-aem-as-a-cloud-service}

Dynatraktion OneAgent-Kunden können ihre AEM überwachen, indem sie über ein Support-Ticket eine Konnektivität anfordern.

Die für Verbindungsanfragen erforderlichen Details werden nachfolgend beschrieben:

| **Feld** | **Beschreibung** |
|---|---|
| URL der dynamischen Umgebung | Ihre URL der dynamischen Umgebung.<br><br>Für Dynatrace SaaS-Kunden lautet das Format `https://<environment>.live.dynatrace.com`.<br><br>Für Dynatrace Managed -Kunden lautet das Format `https://<your-managed-url>/e/<environmentId>` |
| Dynamic Environment ID | Ihre Dynamic Environment ID, die Sie in der Umgebungs-URL finden. |
| Dynatraktische Umgebungstoken | Ihr OneAgent-Umgebungstoken. Weitere Informationen zur Erstellung finden Sie in der Dokumentation zu Dynatrakien .<br><br>Dies sollte als geheim betrachtet werden. Verwenden Sie daher geeignete Sicherheitspraktiken. Zum Beispiel schützen Passwörter sie auf einer Website wie **zerobin.net**, auf die das Kundensupport-Ticket zusammen mit dem Kennwort verweisen kann. |
| Dynatraktions-API-Zugriffstoken | Das API-Zugriffstoken Ihrer Dynatraktionsumgebung. Weitere Informationen zur Erstellung finden Sie in der Dokumentation zu Dynatrakien .<br><br>Dies sollte als geheim betrachtet werden, sodass geeignete Sicherheitspraktiken zum Einsatz kommen. Zum Beispiel schützen Passwörter sie auf einer Website wie **zerobin.net**, auf die das Kundensupport-Ticket zusammen mit dem Kennwort verweisen kann.<br><br>Hinweis: Dies ist nur für Dynatrace Managed erforderlich. |
| Zielhafen für Dynatrakien | Der Zielanschluss von Dynatrace.<br><br>Hinweis: Dies ist nur für Dynatrace Managed erforderlich. |
| AEM Umgebungs-ID(s) | Die AEM Umgebungs-ID(s) für die Überwachung durch Dynatraktion. |


