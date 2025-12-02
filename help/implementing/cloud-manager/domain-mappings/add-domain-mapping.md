---
title: Hinzufügen einer Domain-Zuordnung
description: Erfahren Sie, wie Sie eine Domain-Zuordnung für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung hinzufügen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: 4935fbf5f0eb10f2f17280fb32f07d99f69eb875
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 51%

---


# Informationen zum Hinzufügen einer Domain-Zuordnung {#add-domain-mapping}

Um eine Domain mit einem SSL-Zertifikat im von Adobe verwalteten CDN in Ihrem Programm zu verknüpfen, müssen Sie eine CDN(Content Delivery Network)-Konfiguration hinzufügen.

Bei von Adobe verwalteten CDNs sind bei Verwendung von DV-SSL-Zertifikaten nur Sites mit ACME-Validierung zulässig.

>[!IMPORTANT]
>
>Haben Sie [einen benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) bzw. [ein SSL-Zertifikat hinzugefügt](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)? Andernfalls müssen Sie diese beiden Aufgaben ausführen, bevor Sie eine CDN-Konfiguration hinzufügen können.

Siehe auch [Von Adobe verwaltetes CDN](https://www.aem.live/docs/byo-cdn-adobe-managed).

**So fügen Sie eine Domain-Zuordnung hinzu:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Führen Sie je nach Anwendungsfall einen der folgenden Schritte aus:

   | Anwendungsfall | Schritte |
   | --- | --- |
   | CDN-Konfiguration zu einer *vorhandenen* Edge Delivery-Site in Cloud Manager hinzufügen | a. Klicken Sie im linken Seitenmenü unter **Services** auf ![Web-Seiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery-Sites**.<br>b. Klicken Sie in der Edge Delivery-Tabelle am Ende einer Zeile, der keine Domain zugeordnet ist, auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).<br>c. Klicken Sie auf **CDN konfigurieren**. |
   | CDN-Konfiguration in Cloud Manager hinzufügen | Klicken Sie im linken Seitenmenü unter **Services** auf ![Symbol für soziale Netzwerke](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Domain-Zuordnungen**.<br>b. Klicken Sie oben rechts auf der Seite „Domain-Zuordnungen“ auf **Hinzufügen**. |

1. Wählen **im Dialogfeld „Domain** CDN zuordnen“ einen der folgenden CDN-Typen aus:

   * **Adobe Managed CDN (empfohlen)** - Für diese Konfiguration wird ein von Adobe verwaltetes CDN verwendet. Es umfasst eine automatisierte Einrichtung und Verwaltung sowie integrierte Sicherheitsfunktionen.
   * **Anderer CDN-**: Für diese Konfiguration wird ein selbstverwaltetes CDN-Provider-Netzwerk verwendet.

1. Gehen Sie je nach ausgewähltem CDN-Typ im vorherigen Schritt wie folgt vor:

   * **Adobe Managed CDN**

     ![Dialogfeld „Domain dem CDN zuordnen“ mit aktiviertem Optionsfeld „Von Adobe verwaltetes CDN“](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-adobe-managed.png)

      1. Wählen Sie in **Dropdown** Liste „Herkunft“ eine der folgenden Optionen aus:

         | Dropdown-Liste „Herkunft“ | Beschreibung |
         | --- | --- |
         | Sites | Wählen Sie eine Edge Delivery-Site aus. |
         | Umgebung | Wählen Sie eine bestimmte Cloud Service-Umgebung aus, die im Rahmen Ihrer AEM-Einrichtung als Ziel festgelegt werden soll.<br> Wählen Sie in der Dropdown-Liste **Ebene** eine der folgenden Optionen aus:<br>• Wählen Sie **Veröffentlichen** aus, um eine Live-Produktionsumgebung als Ziel festzulegen, in der Inhalte an Endbenutzende bereitgestellt werden.<br>• Wählen Sie **Vorschau** für Staging- oder produktionsfremde Umgebungen aus, in denen Sie Änderungen testen, bevor sie live geschaltet werden. |

      1. Wählen Sie in **Dropdown** Liste „Domain“ den Domain-Namen aus, den Sie verwenden möchten.<br>Keine verifizierten Domains in der Dropdown-Liste verfügbar? Siehe [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

      1. Wählen **in der Dropdown** Liste „SSL-Zertifikat“ ein Zertifikat aus, das Sie verwenden möchten.<br>Keine SSL-Zertifikate in der Dropdown-Liste verfügbar? Siehe [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).

      1. Klicken Sie auf **Speichern**.

   * **Anderer CDN-Anbieter**

     ![Dialogfeld „Domain dem CDN zuordnen“ mit aktiviertem Optionsfeld „Von Adobe verwaltetes CDN“](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-other-provider.png)

     Verwenden Sie die aufgelisteten Konfigurationsschritte, um die erforderlichen Einstellungen in Ihrem CDN anzuwenden und die Zuordnung zu bestätigen. Siehe auch [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

      1. Klicken Sie **Ich habe mein CDN konfiguriert**.

   <!-- OLD IMAGE/UI (/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)-->

   <!-- In the **Domain** field, enter the customer-facing hostname you want to serve (for example, `www.example.com`) -->

1. Adobe empfiehlt, die Domain-Zuordnung zu testen.

## Testen der Domain-Zuordnung {#test-domain-mapping}

Sie können überprüfen, ob eine neue Domain-Zuordnung im von Adobe verwalteten CDN vorhanden ist, ohne auf eine öffentliche DNS-Verbreitung zu warten.

Führen Sie einen **curl**-Befehl aus, der die DNS-Auflösung überschreibt und direkt auf den CDN-Edge verweist:

```bash
curl -svo /dev/null https://www.example.com \
--resolve www.example.com:443:151.101.3.10
```

* Ersetzen Sie `www.example.com` durch Ihre Domain.
* Die IP-Adresse `151.101.3.10` ist eine der IPs, die für den Zugriff auf AEM Cloud Service verwendet werden können. Siehe auch [APEX-Eintrag](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-apex-record).

Das Flag `--resolve` erzwingt die Anfrage an die angegebene IP-Adresse und gibt erst dann Erfolg zurück, wenn das Zertifikat und das Routing für Ihre Domain ordnungsgemäß installiert wurden.

