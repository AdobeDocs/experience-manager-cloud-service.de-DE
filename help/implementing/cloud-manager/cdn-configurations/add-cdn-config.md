---
title: Hinzufügen einer CDN-Konfiguration
description: Erfahren Sie, wie Sie eine CDN-Konfiguration für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung hinzufügen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: 70f99cfb2cd00278d9ebbb7972ef455af7a87a1b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 6%

---


# Hinzufügen einer CDN-Konfiguration {#add-cdn}

Um eine Domäne mit einem SSL-Zertifikat im von Adobe verwalteten CDN in Ihrem Programm zu verknüpfen, müssen Sie eine CDN-Konfiguration (Content Delivery Network) hinzufügen.

Bei von Adobe verwalteten CDNs sind bei Verwendung von DV-Zertifikaten nur Sites mit ACME-Validierung zulässig.

>[!IMPORTANT]
>
>Haben Sie [einen benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) hinzugefügt und [ein SSL-Zertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) hinzugefügt? Andernfalls müssen Sie diese beiden Aufgaben ausführen, bevor Sie eine CDN-Konfiguration hinzufügen können.

**Hinzufügen einer CDN-Konfiguration:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie im linken Navigationsbereich unter **Dienste** auf **CDN-Konfigurationen**.

1. Klicken Sie in der rechten oberen Ecke der Seite &quot;CDN-Konfigurationen&quot;auf **Hinzufügen**.

   ![CDN-Dialogfeld konfigurieren](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

1. Wählen Sie im Dialogfeld **CDN konfigurieren** in der Dropdownliste **Origin** eine der folgenden Optionen aus:

   | Ursprung | Beschreibung |
   | --- | --- |
   | Sites | Wählen Sie eine Edge Delivery-Site aus. |
   | Umgebung | Wählen Sie eine bestimmte Cloud Service-Umgebung aus, die Sie im Rahmen Ihrer AEM-Einrichtung als Ziel auswählen möchten.<br> Wählen Sie in der Dropdownliste **Ebene** eine der folgenden Optionen aus:<br> ・ Wählen Sie **Publish** aus, um eine Live-Produktionsumgebung auszuwählen, in der Inhalte an Endbenutzer bereitgestellt werden.<br> ・ Wählen Sie **Vorschau** für Staging- oder Nicht-Produktionsumgebungen aus, in denen Sie Änderungen testen, bevor sie live geschaltet werden. |

1. Wählen Sie Ihren CDN-Typ aus, indem Sie eine der folgenden Optionen auswählen:

   | CDN-Typ | Beschreibung |
   | --- | --- |
   | Von Adobe verwaltetes CDN | a. Wählen Sie in der Dropdownliste **Domäne** den Domänennamen aus, den Sie verwenden möchten.<br>Keine verifizierten Domänen in der Dropdown-Liste verfügbar? Siehe [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).<br>b. Wählen Sie in der Dropdown-Liste SSL-Zertifikat ein Zertifikat aus, das Sie verwenden möchten.<br>Keine SSL-Zertifikate in der Dropdown-Liste verfügbar? Siehe [Hinzufügen eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
   | Andere CDN-Anbieter. | Wählen Sie diese Option aus, wenn Sie einen eigenen CDN-Anbieter und nicht das für Sie verfügbare Adobe-verwaltete CDN verwenden.<br>Wählen Sie in der Dropdownliste **Domäne** den Domänennamen aus, den Sie verwenden möchten.<br>Keine verfügbaren SSL-Zertifikate in der Dropdownliste? Siehe [Hinzufügen eines benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |

1. Klicken Sie auf **Speichern**.
