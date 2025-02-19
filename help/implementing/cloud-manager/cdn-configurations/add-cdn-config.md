---
title: Hinzufügen einer CDN-Konfiguration
description: Erfahren Sie, wie Sie eine CDN-Konfiguration für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung hinzufügen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: 70ee0ca9e7bb37abc6b82413fc02e37347893011
workflow-type: ht
source-wordcount: '453'
ht-degree: 100%

---


# Hinzufügen einer CDN-Konfiguration {#add-cdn}

Um eine Domain mit einem SSL-Zertifikat im von Adobe verwalteten CDN in Ihrem Programm zu verknüpfen, müssen Sie eine CDN(Content Delivery Network)-Konfiguration hinzufügen.

Bei von Adobe verwalteten CDNs sind bei Verwendung von DV-SSL-Zertifikaten nur Sites mit ACME-Validierung zulässig.

>[!IMPORTANT]
>
>Haben Sie [einen benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) bzw. [ein SSL-Zertifikat hinzugefügt](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)? Andernfalls müssen Sie diese beiden Aufgaben ausführen, bevor Sie eine CDN-Konfiguration hinzufügen können.

Siehe auch [Von Adobe verwaltetes CDN](https://www.aem.live/docs/byo-cdn-adobe-managed).

**So fügen Sie eine CDN-Konfiguration hinzu:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Führen Sie je nach Anwendungsfall einen der folgenden Schritte aus:

   | Anwendungsfall | Schritte |
   | --- | --- |
   | CDN-Konfiguration zu einer *vorhandenen* Edge Delivery-Site in Cloud Manager hinzufügen | a. Klicken Sie im linken Seitenmenü unter **Services** auf ![Web-Seiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery-Sites**.<br>b. Klicken Sie in der Edge Delivery-Tabelle am Ende einer Zeile, der keine Domain zugeordnet ist, auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).<br>c. Klicken Sie auf **CDN konfigurieren**. |
   | CDN-Konfiguration in Cloud Manager hinzufügen | Klicken Sie im linken Seitenmenü unter **Services** auf ![Symbol für soziale Netzwerke](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Domain-Zuordnungen**.<br>b. Klicken Sie oben rechts auf der Seite „Domain-Zuordnungen“ auf **Hinzufügen**. |

1. Wählen Sie im Dialogfeld **CDN konfigurieren** in der Dropdown-Liste **Herkunft** eine der folgenden Optionen aus:

   ![Dialogfeld „CDN konfigurieren“](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

   | Ursprung | Beschreibung |
   | --- | --- |
   | Sites | Wählen Sie eine Edge Delivery-Site aus. |
   | Umgebung | Wählen Sie eine bestimmte Cloud Service-Umgebung aus, die im Rahmen Ihrer AEM-Einrichtung als Ziel festgelegt werden soll.<br> Wählen Sie in der Dropdown-Liste **Ebene** eine der folgenden Optionen aus:<br>• Wählen Sie **Veröffentlichen** aus, um eine Live-Produktionsumgebung als Ziel festzulegen, in der Inhalte an Endbenutzende bereitgestellt werden.<br>• Wählen Sie **Vorschau** für Staging- oder produktionsfremde Umgebungen aus, in denen Sie Änderungen testen, bevor sie live geschaltet werden. |

1. Legen Sie Ihren CDN-Typ und die zugehörige Konfiguration fest, indem Sie eine der folgenden Optionen auswählen:

   | CDN-Typ | Konfigurationsdetails |
   | --- | --- |
   | Von Adobe verwaltetes CDN | Gehen Sie unter **Konfigurationsdetails** wie folgt vor:<br>a. Wählen Sie in der Dropdown-Liste **Domain** den Domain-Namen aus, der verwendet werden soll.<br>Keine verifizierten Domains in der Dropdown-Liste verfügbar? Siehe [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).<br>b. Wählen Sie in der Dropdown-Liste **SSL-Zertifikat** ein Zertifikat aus, das verwendet werden soll.<br>Keine SSL-Zertifikate in der Dropdown-Liste verfügbar? Siehe [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
   | Anderer CDN-Anbieter | Wählen Sie diese Option aus, wenn Sie einen eigenen CDN-Anbieter und nicht das für Sie verfügbare von Adobe verwaltete CDN verwenden.<br>Wählen Sie unter **Konfigurationsdetails** in der Dropdown-Liste **Domain** den Domain-Namen aus, der verwendet werden soll.<br>Keine verifizierten Domains in der Dropdown-Liste verfügbar? Siehe [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |

1. Klicken Sie auf **Speichern**.
