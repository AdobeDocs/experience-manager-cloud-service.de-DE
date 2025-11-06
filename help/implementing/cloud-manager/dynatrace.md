---
title: Dynatrace
description: Erfahren Sie, wie Sie Dynatrace mit AEM as a Cloud Service nutzen
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 69%

---

# Dynatrace {#dynatrace}

Adobe bietet die Möglichkeit, Dynatrace zur Überwachung von AEM as a Cloud Service im Rahmen einer Unternehmensbereitstellung, zur Identifizierung potenzieller Problemursachen und zur Behebung dieser Probleme zu nutzen.

Dynatrace ermöglicht die nahtlose Überwachung sämtlicher AEM-Programme. Dynatrace erkennt Ihre AEM-Apps und zeigt deren Pfade von der Website über den Container bis hin zum Cloud-Service an, um das Anwendererlebnis anzuzeigen. Bringen Sie durch die Verknüpfung mit End-to-end-Traces auf allen Ebenen und Echtzeit-Benutzerüberwachung Ihre auf AEM-Inhalte gestützten Erlebnisse auf die nächste Stufe – ohne Lücken oder blinde Flecken. Wenn Anomalien auftreten, diagnostiziert Dynatrace diese in Echtzeit mit der Davis-KI-Engine. Dadurch wird die Grundursache bis zum fehlerhaften Code ermittelt, bevor Ihre Kunden betroffen sind, wodurch die durchschnittliche Reparaturzeit minimiert wird.

Weitere Informationen zu Dynatrace finden Sie unter [Integration von Adobe AEM Cloud Service](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![Performance-Metriken in der AEM-Autoren- und -Veröffentlichungsumgebung](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Integration von Dynatrace mit AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Dynatrace-Kunden können ihre AEM-Umgebungen überwachen, indem sie über ein Support-Ticket eine Verbindung anfragen.

Im Folgenden finden Sie die für Verbindungsanfragen erforderlichen Details:

| **Feld** | **Beschreibung** |
|---|---|
| [!DNL Dynatrace Environment URL] | Die URL Ihrer Dynatrace-Umgebung.<br><br>Für Dynatrace SaaS-Kunden lautet das Format `https://<your-environment-id>.live.dynatrace.com`.<br><br>Für Dynatrace Managed-Kunden lautet das Format `https://<your-managed-url>/e/<environmentId>` |
| [!DNL Dynatrace Environment ID] | Die ID Ihrer Dynatrace-Umgebung. Lesen Sie [Wie erhalte ich meine Dynatrace-Verbindungsdetails?](#how-do-i-get-my-dynatrace-connection-details), wie man es bekommt. |
| [!DNL Dynatrace Environment Token] | Ihr Token für die Dynatrace-Umgebung. Lesen Sie [Wie erhalte ich meine Dynatrace-Verbindungsdetails?](#how-do-i-get-my-dynatrace-connection-details), wie man es bekommt.<br><br>Dieses Token sollte als geheim betrachtet werden. Verwenden Sie daher geeignete Sicherheitsverfahren. Schützen Sie es zum Beispiel mit einem Passwort auf einer Website wie **zerobin.net**, auf die das Kunden-Support-Ticket verweisen kann. |
| [!DNL Dynatrace API access token] | Das API-Zugriffs-Token Ihrer Dynatrace-Umgebung. Informationen [&#x200B; Erstellen finden Sie unter „Erstellen eines Dynatrace](#create-dynatrace-access-token)API-Zugriffstokens“.<br><br>Dieses Token sollte als Geheimnis betrachtet werden. Verwenden Sie daher geeignete Sicherheitsverfahren. Beispielsweise kann es auf einer Website wie &quot;**.net“, auf** das Support-Ticket verweisen kann, zusammen mit dem Kennwort durch ein Passwort geschützt werden.<br> |
| [!DNL Dynatrace ActiveGate Port] | Ihr Dynatrace ActiveGate-Port, mit dem die AEM-Integration eine Verbindung herstellen soll.<br><br>Dieser Port ist nur für Dynatrace Managed erforderlich. |
| [!DNL Dynatrace ActiveGate Network Zone] | Ihre [Dynatrace ActiveGate-Netzwerkzone](https://docs.dynatrace.com/docs/manage/network-zones) zur effizienten Weiterleitung von AEM-Überwachungsdaten über Rechenzentren und Netzwerkregionen hinweg.<br><br>Hinweis: Eine Dynatrace ActiveGate-Netzwerkzone ist optional. |
| [!DNL AEM Environment IDs] | Die AEM-Umgebungs-ID oder -IDs, die von Dynatrace überwacht werden sollen. |

>[!NOTE]
>
>Nach der Integration von Dynatrace fließen die Daten nicht mehr in andere APM-Tools wie New Relic, wenn diese zuvor aktiviert waren.

## FAQs {#faq}

### Welche Lizenz benötige ich für Dynatrace AEM Monitoring? {#which-license-do-i-need-for-AEM-monitoring}

Für Dynatrace AEM Monitoring ist eine Dynatrace-Lizenz erforderlich. Die Dynatrace AEM-Lizenzierung basiert auf der [Full-Stack-Überwachung für Kubernetes-Container](https://docs.dynatrace.com/docs/shortlink/dps-hosts#gib-hour-calculation-for-containers-and-application-only-monitoring). Die Speichergrößen der überwachten AEM-Container (Author- und Publish-Service) werden automatisch erkannt.

Die Adobe-Bereitstellungsspezifikationen pro AEM-Umgebung sind:

* Produktion: Im Durchschnitt 4 Container mit je 16 GB Speicher
* Produktionsfremd: Im Durchschnitt 4 Container mit je 8 GB Speicher

Weitere Informationen zur Dynatrace-Lizenzierung finden Sie unter [Dynatrace Platform-Abonnement](https://docs.dynatrace.com/docs/shortlink/dynatrace-platform-subscription).

### Wie erhalte ich meine Dynatrace-Verbindungsdetails? {#how-do-i-get-my-dynatrace-connection-details}

1. Führen Sie die folgende API-Anfrage an Ihre Dynatrace-Umgebung aus:

   ```
   curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"
   ```


   Ersetzen Sie `<environmentUrl>` durch die URL Ihrer Dynatrace-Umgebung und `<accessToken>` durch Ihr erstelltes API-Zugriffs-Token.

1. Kopieren Sie `<environmentId>` und `<environmentToken>` aus der Antwort-Payload und speichern Sie sie an einem sicheren Ort.

   ```
   {
      "tenantUUID": "<environmentId>",
      "tenantToken": "<environmentToken>",
      "communicationEndpoints": [...]
   }
   ```

### Erstellen eines Dynatrace-API-Zugriffs-Tokens {#create-dynatrace-access-token}

1. Melden Sie sich bei Ihrer Dynatrace-Umgebung an.
1. Wechseln Sie zu **[!DNL Access tokens]** und klicken Sie dann auf die Option **[!DNL Generate new token]**.
1. Definieren Sie einen [!DNL token name].
1. Setzen Sie den Token-Umfang auf **[!DNL PaaS integration - Installer download]**.
1. Wählen Sie **[!DNL Generate token]**.
1. Kopieren Sie das generierte Zugriffs-Token und speichern Sie es an einem sicheren Ort.





