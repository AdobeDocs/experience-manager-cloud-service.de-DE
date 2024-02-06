---
title: Dynatrace
description: Erfahren Sie, wie Sie Dynatrace mit AEM as a Cloud Service nutzen
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
source-git-commit: fec3aa6debec49014406ab241c3ce0338ec5a1d2
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 97%

---

# Dynatrace {#dynatrace}

Adobe bietet die Möglichkeit, Dynatrace zur Überwachung von AEM as a Cloud Service im Rahmen einer Unternehmensbereitstellung, zur Identifizierung potenzieller Problemursachen und zur Behebung dieser Probleme zu nutzen.

Dynatrace ermöglicht die nahtlose Überwachung sämtlicher AEM-Programme. Dynatrace bietet umfassenden Einblick in das Endbenutzererlebnis durch automatische Ermittlung der genutzten AEM-Programme und Visualisierung ihrer Abhängigkeiten von der Website über den Container bis zum Cloud-Service. Bringen Sie durch die Verknüpfung mit End-to-end-Traces auf allen Ebenen und Echtzeit-Benutzerüberwachung Ihre auf AEM-Content gestützten Erlebnisse auf die nächste Stufe – ohne Lücken oder blinde Flecken. Wenn Anomalien auftreten, diagnostiziert Dynatrace sie mit der KI-Engine Davis in Echtzeit und ermittelt den ursächlichen fehlerhaften Code, bevor Kundschaft betroffen ist. Dadurch wird auch die mittlere Reparaturzeit minimiert.

Weitere Informationen zu Dynatrace finden Sie unter [Integration von Adobe AEM Cloud Service](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![Performance-Metriken in der AEM-Autoren- und -Veröffentlichungsumgebung](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Integration von Dynatrace mit AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Dynatrace-Kunden können ihre AEM-Umgebungen überwachen, indem sie über ein Support-Ticket eine Verbindung anfragen.

Im Folgenden finden Sie die für Verbindungsanfragen erforderlichen Details:

| **Feld** | **Beschreibung** |
|---|---|
| [!DNL Dynatrace Environment URL] | Die URL Ihrer Dynatrace-Umgebung.<br><br>Für Dynatrace SaaS-Kunden lautet das Format `https://<your-environment-id>.live.dynatrace.com`.<br><br>Für Dynatrace Managed-Kunden lautet das Format `https://<your-managed-url>/e/<environmentId>` |
| [!DNL Dynatrace Environment ID] | Die ID Ihrer Dynatrace-Umgebung. Weitere Informationen zum Erhalt finden Sie unter [Abrufen von Informationen zur Dynatrace-Umgebung](#get-dynatrace-env-info). |
| [!DNL Dynatrace Environment Token] | Ihr Token für die Dynatrace-Umgebung. Weitere Informationen zum Erhalt finden Sie unter [Abrufen von Informationen zur Dynatrace-Umgebung](#get-dynatrace-env-info).<br><br>Dieses Token sollte als geheim behandelt werden. Verwenden Sie daher entsprechende Sicherheitsmaßnahmen. Schützen Sie es zum Beispiel mit einem Passwort auf einer Website wie **zerobin.net**, auf die das Kunden-Support-Ticket verweisen kann. |
| [!DNL Dynatrace API access token] | Das API-Zugriffs-Token Ihrer Dynatrace-Umgebung.  Weitere Informationen zur Erstellung finden Sie unter [Erstellen eines Dynatrace-API-Zugriffs-Tokens](#create-dynatrace-access-token).<br><br>Dieses Token sollte als geheim behandelt werden. Verwenden Sie daher entsprechende Sicherheitsmaßnahmen. Schützen Sie es zum Beispiel mit einem Passwort auf einer Website wie **zerobin.net**, auf die das Kunden-Support-Ticket verweisen kann.<br><br>Hinweis: Dies ist nur für Dynatrace Managed erforderlich. |
| [!DNL Dynatrace ActiveGate Port] | Ihr Dynatrace ActiveGate-Port, mit dem die AEM-Integration eine Verbindung herstellen soll.<br><br>Hinweis: Dies ist nur für Dynatrace Managed erforderlich. |
| [!DNL Dynatrace ActiveGate Network Zone] | Ihre [Dynatrace ActiveGate-Netzwerkzone](https://docs.dynatrace.com/docs/manage/network-zones) zur effizienten Weiterleitung von AEM-Überwachungsdaten über Rechenzentren und Netzwerkregionen hinweg.<br><br>Hinweis: Eine Dynatrace ActiveGate-Netzwerkzone ist optional. |
| [!DNL AEM Environment ID(s)] | Die AEM-Umgebungs-ID(s), die Dynatrace überwachen soll. |

>[!NOTE]
>
>Nach der Integration von Dynatrace fließen keine Daten mehr an andere APM-Tools wie New Relic, wenn diese zuvor aktiviert waren.


## Erstellen eines Dynatrace-API-Zugriffs-Tokens {#create-dynatrace-access-token}

1. Melden Sie sich bei Ihrer Dynatrace-Umgebung an.
1. Im [!DNL Dynatrace] Menü, navigieren Sie zu [!DNL Manage] > [!DNL Access tokens].
1. Auswählen [!DNL Generate new token].
1. Definieren Sie eine [!DNL token name].

1. Optional: Legen Sie eine [!DNL expiration date]. Stellen Sie sicher, dass Sie ein neues Token generieren, bevor es abläuft.
1. Legen Sie die [!DNL token scope] nach [!DNL PaaS integration - Installer download]
1. Auswählen [!DNL Generate token].
1. Kopieren Sie das generierte Zugriffs-Token und speichern Sie es an einem sicheren Ort.


## Abrufen von Informationen zur Dynatrace-Umgebung {#get-dynatrace-env-info}

1. Führen Sie die folgende API-Anfrage an Ihre Dynatrace-Umgebung aus:

`curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"`

Ersetzen Sie \&lt;environmentUrl\> mit der URL Ihrer Dynatrace-Umgebung und \&lt;accessToken\> mit Ihrem erstellten API-Zugriffs-Token.

1. Kopieren Sie \&lt;environmentId\> und \&lt;environmentToken\> aus der Antwort-Payload und speichern Sie sie an einem sicheren Ort.

```
{
   "tenantUUID": "<environmentId>",
   "tenantToken": "<environmentToken>",
   "communicationEndpoints": [
   ... 
   ],
   "formattedCommunicationEndpoints": "<endpoints>" 
}
```


