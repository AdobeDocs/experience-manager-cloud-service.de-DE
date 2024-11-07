---
title: Versionshinweise für Cloud Manager 2024.11.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Version von Cloud Manager 2024.11.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: db661281831dcb07491dca16e73e835b487814a6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 29%

---

# Versionshinweise für Cloud Manager 2024.11.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Erfahren Sie mehr über die Version von Cloud Manager 2024.11.0 in AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2024.11.0 von Cloud Manager in AEM as a Cloud Service wurde am 7. November 2024 veröffentlicht.

Die nächste geplante Version ist der 5. Dezember 2024.

## Neue Funktionen {#what-is-new}

* Erleben Sie die neueste Innovation in Edge Delivery Services mit AEM Cloud Service-now, die Sie in Ihrem Sandbox-Programm untersuchen können. [Mehr erfahren](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md#auto-creation) <!-- (CMGR-62319) -->
* Die Seite &quot;Domäneneinstellungen&quot;in AEM Cloud Manager enthält jetzt eine Suchfunktion, mit der Sie Domänen nach Namen schnell finden können. Sie können Suchbegriffe in das Suchfeld eingeben, um übereinstimmende Domänen zu filtern und anzuzeigen, wodurch die effiziente Verwaltung mehrerer Domänen erleichtert wird. Darüber hinaus bietet die Seite Statusfilter wie **Verified** und **Not Verified**, um die Suchergebnisse weiter einzugrenzen. <!-- (CMGR-62615) -->

![Suchfeld in den Domäneneinstellungen](/help/implementing/cloud-manager/assets/domain-settings-search.png)

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adopter-Programm von Cloud Manager teil und nutzen Sie die Möglichkeit, zukünftige Funktionen zu testen.

### AEM {#aem-home}

AEM Home ist ein neuer, zentralisierter Ausgangspunkt für die Verwaltung von Inhalten, Assets und Sites in Adobe Experience Manager. AEM Startseite ist auf ein personalisiertes Erlebnis zugeschnitten und hilft Benutzern, anhand ihrer Rollen und Ziele nahtlos in das AEM Ökosystem zu navigieren. Es wurde als Ihr Leitfaden konzipiert und bietet wichtige Einblicke und empfohlene Maßnahmen, um die gewünschten Ergebnisse effizient zu erzielen. Durch die Präsentation einer klaren, personalgesteuerten Roadmap stellt AEM Home sicher, dass Benutzer schnell finden, was sie zur Erreichung ihrer Ziele benötigen, und so ein optimiertes und effektiveres Erlebnis über alle AEM Funktionen hinweg unterstützen.

AEM Home steht frühen Anwendern zur Verfügung und bietet einen ersten Einblick in ein erweitertes Erlebnis, das Workflows optimiert, Ziele priorisiert und Ergebnisse vorantreibt. Wenn Sie sich anmelden, haben Sie die Möglichkeit, die Entwicklung von AEM Home zu gestalten, indem Sie Feedback geben, das die Entwicklung beeinflusst, um der AEM Community am besten zu dienen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie eine E-Mail von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse an [Grp-AemHome@adobe.com](mailto:Grp-AemHome@adobe.com). Stellen Sie sicher, dass Sie die folgenden Informationen angeben:

* Die Rolle, die Ihrem Profil am besten entspricht: Inhaltsautor, Entwickler, Business Owner, Administrator oder Sonstige (geben Sie eine Beschreibung an).
* Ihre primäre AEM für den Zugriff: AEM Sites, AEM Assets, AEM Forms, Cloud Manager oder Sonstige (Beschreibung angeben).

### Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

Die Funktion **Bringen Sie Ihren eigenen Git mit** wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Unternehmens-GitHub-Repositorys. Wenn Sie diese neuen Repositorys hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit der konstanten Code-Synchronisation mit dem Adobe-Repository. Sie bietet weiterhin die Möglichkeit, Pull-Anfragen zu überprüfen, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind vorkonfigurierte Code-Qualitätsprüfungen für Pull-Anfragen ausschließlich für von GitHub gehostete Repositorys verfügbar. Es ist jedoch ein Update in Arbeit, um diese Funktionen auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Stellen Sie sicher, dass Sie angeben, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder Enterprise-Repository-Struktur befinden. —>


## Fehlerbehebungen

* In einem kürzlich veröffentlichten Update wurde ein Problem in SonarQube behoben, bei dem hartcodierte Kennwörter in bestimmten Fällen nicht erkannt wurden. Die Fehlerbehebung enthält jetzt eine erweiterte Musterprüfung und passt sich an die standardmäßigen Erkennungsstandards in SonarQube an. <!-- CMGR-62682 -->
* Wenn Sie versuchen, ein SSL-Zertifikat in Cloud Manager zu aktualisieren, wird nach dem Klicken auf **[!UICONTROL Aktualisieren]** im Dialogfeld **[!UICONTROL Anzeigen und Aktualisieren des SSL-Zertifikats]** ein unbekannter Fehler angezeigt. <!-- CMGR-62848 -->
* In Cloud Manager schlug die Aktualisierung des SSL-Zertifikats mit dem Fehler &quot;Das neue Zertifikat stimmt nicht mit den vorhandenen Domänen überein&quot;fehl, selbst wenn die Domänen identisch waren, aber Unterschiede in der Schreibweise aufwiesen (Groß- oder Kleinschreibung). In der Aktualisierung wird bei Domänen nun nicht mehr zwischen Groß- und Kleinschreibung unterschieden, was an RFC-Standards ausgerichtet ist. <!-- CMGR-62844 -->
* In Cloud Manager blieben IP-Zulassungslisten-Bindungen in einem laufenden Zustand, da Fremdschlüssellinks zu Domänenkonfigurationen fehlten. Durch die Korrektur wird nun sichergestellt, dass IP-Zulassungslisten-Bindungen korrekt mit den zugehörigen Domänenkonfigurationen verknüpft werden. <!-- CMGR-62838 -->
* Cloud Manager validiert den OCSP-Status (Online Certificate Status Protocol) eines SSL-Zertifikats. Adobe empfiehlt, die Integrität Ihres Zertifikats auch lokal mithilfe eines Tools wie `openssl verify -untrusted intermediate.pem certificate.pem` zu überprüfen, bevor Sie es über Cloud Manager installieren. Weitere Informationen finden Sie in der Dokumentation zu den [SSL-Zertifikatanforderungen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates#requirements). <!-- CMGR-62341  -->



<!-- ## Known issues {#known-issues} -->