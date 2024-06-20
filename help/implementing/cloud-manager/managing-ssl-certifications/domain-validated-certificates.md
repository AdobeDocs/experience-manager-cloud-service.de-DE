---
title: DV-Zertifikate (Domain Validated)
description: Erfahren Sie, wie Sie in Cloud Manager Repositorys mit Domain-Validierung (DV) verwalten.
exl-id: 7f2c71b6-15c3-4919-9f51-a3e26d0d48d4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 100%

---

# DV-Zertifikate (Domain Validated) {#domain-validated-certificates}

Erfahren Sie, wie Sie in Cloud Manager Repositorys mit Domain-Validierung (DV) verwalten.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/implementing/cloud-manager/release-notes/current.md#early-adoption) verfügbar.

## Einführung {#introduction}

Mit Cloud Manager können Sie SSL-Zertifikate mit Domain-Validierung (DV) erstellen und verwalten.  Dadurch erhalten Sie die schnellste, einfachste und kostengünstigste Lösung, um eine sichere Website für Ihr Online-Business zu erstellen.

Zertifikate mit Domain-Validierung sind für [Produktions- und Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) verfügbar.

## Hinzufügen einer benutzerdefinierten Domain {#adding-domain}

Um ein Zertifikat mit Domain-Validierung (DV) hinzuzufügen, müssen Sie zunächst Ihre benutzerdefinierte Domain konfigurieren. Der Prozess entspricht weitgehend dem im Dokument [Einführung in benutzerdefinierte Domain-Namen beschriebenen.](/help/implementing/cloud-manager/custom-domain-names/introduction.md) Diese Funktion wurde jedoch etwas erweitert.

1. Beim Überprüfen der Domain können Sie zwischen der Verwendung von durch Adobe verwalteten oder selbst verwalteten Zertifikaten für die Domain wählen. Wählen Sie **von Adobe verwaltetes Zertifikat**, um später ein DV-Zertifikat hinzuzufügen.

   ![Auswählen von „Von Adobe verwaltet“](assets/verify-domain-dialog.png)

1. Um ein von Adobe verwaltetes Zertifikat zu verwenden, müssen Sie Ihrem DNS einen CNAME-Eintrag hinzufügen, wie im Dialogfeld **Domain verifizieren** beschrieben.

   ![Hinzufügen eines CNAME-Eintrags](assets/verify-domain-dialog-adobe-managed.png)

1. Nachdem die Domain erstellt wurde, tippen oder klicken Sie in der Liste der Domains auf die Schaltfläche mit den Auslassungspunkten und wählen Sie **Überprüfen**, um die Domain zu überprüfen.

   ![Verifizieren der Domain](assets/verify-domain.png)

## Hinzufügen eines DV-Zertifikats {#adding}

Nachdem Sie Ihre Domain richtig konfiguriert haben, tippen oder klicken Sie im Fenster „SSL-Zertifikate“ auf die Schaltfläche **SSL-Zertifikat hinzufügen**.

![Hinzufügen eines DC-Zertifikats](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

1. Wählen Sie die Option **Von Adobe verwaltet (DV)**.
1. Geben Sie in der Dropdown-Liste **Domains auswählen** den Domain-Namen an.
1. Tippen oder klicken Sie auf **Speichern**.

Nachdem das Zertifikat erfolgreich hinzugefügt wurde, weist es den Status „Ausstehend“ mit einem gelben Warnzeichen an seinem Namen im Fenster **SSL-Zertifikate** auf.

![Ausstehendes DV-Zertifikat](assets/pending-dv-certificate.png)

Sobald das Zertifikat erfolgreich ausgestellt wurde, ist im Fenster **SSL-Zertifikate** ein grünes Häkchen neben seinem Namen zu sehen.

![Ausgestelltes DV-Zertifikat](assets/issued-dv-certificate.png)

Weitere Informationen zum Fenster „SSL-Zertifikate“ und zum Hinzufügen von SSL-Zertifikaten finden Sie im Dokument [Hinzufügen eines SSL-Zertifikats.](add-ssl-certificate.md)

## Hinzufügen einer CDN-Konfiguration {#add-cdn}

Dieser Schritt muss abgeschlossen sein, um eine Domain mit SSL mithilfe von Fastly CDN zu konfigurieren.

Führen Sie die folgenden Schritte aus, um eine CDN-Konfiguration mit Cloud Manager hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie die Registerkarte **CDN-Konfigurationen** aus und klicken oder tippen Sie in der Symbolleiste auf **Hinzufügen**.

1. Geben Sie im Dialogfeld **CDN konfigurieren** die erforderlichen Informationen an.

   * Wählen Sie den **Ursprung** aus. Dabei kann es sich um Folgendes handeln:
      * Eine Cloud Service-Umgebung
      * Eine Edge Delivery Services-Site
   * Wählen Sie Ihren CDN-Typ aus.
   * Wählen Sie die Domain aus.
   * Wählen Sie das SSL-Zertifikat aus.
      * Nur für von Adobe verwaltete CDNs erforderlich.

   ![Dialogfeld „CDN konfigurieren“](assets/configure-cdn-dialog.png)

>
>
>Bei von Adobe verwalteten CDNs sind bei Verwendung von DV-Zertifikaten nur Sites mit ACME-Validierung zulässig.
