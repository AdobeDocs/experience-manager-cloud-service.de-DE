---
title: Konfigurieren von umgebungsspezifischen REST-Endpunkten für dasselbe adaptive Formular | Adobe Experience Manager as a Cloud Service
description: Erfahren Sie, wie Sie dasselbe adaptive Formular an verschiedene REST-Übermittlungsendpunkte in Ihren Entwicklungs-, Staging- und Produktionsumgebungen weiterleiten können, ohne das Formular zu ändern.
feature: Adaptive Forms, Core Components
role: User, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: 40410875-96d0-4728-8cbd-b1e1dfa438c4
source-git-commit: ee79ef0d9b1101a245ea918c8ce46d502e98fdb3
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 4%

---


# Konfigurieren Sie umgebungsspezifische REST-Endpunkte für dasselbe adaptive Formular

Wenn Sie ein adaptives Formular von der Entwicklung über die Staging-Umgebung zur Produktion weiterleiten, muss das Formular in der Regel an einen *anderen* REST-Endpunkt in jeder Umgebung gesendet werden, während das Formular selbst identisch bleibt. Durch die Hartcodierung der Endpunkt-URL in der Übermittlungsaktion des Formulars wird dies nicht mehr möglich, da dieselbe URL anschließend mit dem Formular in jede Umgebung weitergeleitet wird.

In diesem Artikel wird beschrieben, wie Sie ein einzelnes, tragbares adaptives Formular beibehalten und dessen Aktion [An REST-Endpunkt übermitteln](/help/forms/configure-submit-action-restpoint.md) in jeder Umgebung zum richtigen Endpunkt auflösen können. Das Formular verweist auf eine REST *Konfiguration (nach Name* anstelle nach URL, und jede Umgebung liefert einen eigenen Wert für diese Konfiguration.

## Voraussetzungen {#prerequisites}

* Ein adaptives Formular, das auf Kernkomponenten basiert.
* Ein [Konfigurations-Container](/help/implementing/developing/introduction/configurations.md) der über den Konfigurations-Browser erstellt wurde (**Tools** > **Allgemein** > **Konfigurations-Browser**) mit **Cloud-Konfigurationen**.
* Berechtigung für den Zugriff auf **Tools** > **Cloud Services** und zur Promotion [Package Manager](/help/implementing/developing/tools/package-manager.md) in jeder Umgebung (oder einer [Cloud Manager-Bereitstellungs-Pipeline](/help/implementing/deploying/overview.md#deploying-content-packages-via-cloud-manager-and-package-manager)).

## Erstellen der RESTful-Dienstkonfiguration für das Staging {#create-rest-configuration}

>[!VIDEO](https://video.tv.adobe.com/v/3492383)

Erstellen Sie auf der Staging-Autoreninstanz die benannte Konfiguration, auf die Ihr Formular verweist. Legen Sie die **Service-Endpunkt-URL** für das Staging auf den REST- oder Webhook-Endpunkt fest.

1. Wechseln Sie zu **Tools** > **Cloud Services** > **Datenquellen**.

1. Wählen Sie Ihren Konfigurations-Container und dann **Erstellen** aus.

1. Geben Sie auf der Registerkarte **Allgemein** einen **Namen** für die Konfiguration ein (z. B. `restTest`). Verwenden Sie *Namen* jeder Umgebung, damit das Formular nach der Hochstufung konsistent aufgelöst wird.

1. Konfigurieren Sie auf **Registerkarte** Authentifizierungseinstellungen“:

   * **RESTful-Service auswählen**: **Service-Endpunkt**.
   * **Methodentyp**: **POST**.
   * **Service-Endpunkt-URL**: Die URL des Staging-Endpunkts (z. B. eine Webhook-URL, mit der Sie Übermittlungen aus dem Staging testen können).
   * **Content-**: z. B **„Mehrteilige Formulardaten**.
   * **Authentifizierungstyp**: nach Bedarf für Ihren Endpunkt (z. B. **None** oder **Basic Authentication**).

1. Klicken Sie auf **Speichern und schließen**.

## Richten Sie das adaptive Formular auf den Konfigurations-Container {#set-configuration-container}

>[!VIDEO](https://video.tv.adobe.com/v/3492384)

Verknüpfen Sie das Formular beim Staging mit dem Konfigurations-Container, der Ihre REST-Konfiguration enthält.

1. Wählen Sie in **Forms und** Ihr adaptives Formular aus und öffnen Sie **Eigenschaften**.

1. Legen Sie auf der Registerkarte **Standard** den **Konfigurations-Container** auf den Container fest, der Ihre RESTful-Dienstkonfiguration enthält (z. B. `/conf/restConfigTest`).

1. Klicken Sie auf **Speichern und schließen**.

## Konfigurieren der Aktion „An REST-Endpunkt übermitteln“ {#configure-submit-action}

>[!VIDEO](https://video.tv.adobe.com/v/3492385)

Konfigurieren Sie beim Staging das Formular so, dass es über die benannte REST-Konfiguration anstelle einer hartcodierten URL gesendet wird. Die vollständige Referenz für die Übermittlungsaktion finden Sie unter [Konfigurieren einer adaptiven Formularübermittlungsaktion für REST-Endpunkte](/help/forms/configure-submit-action-restpoint.md).

1. Öffnen Sie das adaptive Formular zur Bearbeitung, wählen Sie die Komponente **Guide-Container** aus und öffnen Sie die Eigenschaften **Container für adaptive Formulare**.

1. Öffnen Sie die **Übermittlung** und wählen Sie in der Dropdown-Liste **Übermittlungsaktion** die Option **An REST-Endpunkt übermitteln**.

1. Wählen **unter &quot;**&quot; die Option **POST-Anfrage aktivieren** aus.

1. Wählen Sie für **Option auswählen** die Option **Konfiguration** (nicht **URL**).

1. Wählen Sie Ihre benannte Konfiguration (z. B. `restTest`) in der Liste aus.

1. Wählen Sie **Fertig**.

Das Formular löst nun seinen Übermittlungsendpunkt über die benannte Konfiguration anstatt über eine feste URL auf.

## Formular von der Staging- zur Produktionsumgebung weiterleiten {#promote-across-environments}

Verschieben Sie nach dem Konfigurieren und Testen im Staging dasselbe Formular und denselben Konfigurations-Container in die Produktion. Sie können einen der folgenden Ansätze verwenden.

### Option 1: Autoren- und Paketansatz {#option-package}

>[!VIDEO](https://video.tv.adobe.com/v/3492386)

Verwenden Sie diese Option, wenn Autoren das Formular und die Konfiguration direkt in jeder Umgebung verwalten.

1. Erstellen Sie auf **Autoreninstanz** staging) ein Inhaltspaket in [Package Manager](/help/implementing/developing/tools/package-manager.md) das das Formular und den Konfigurations-Container enthält, z. B.:

   * `/content/dam/formsanddocuments/<your-form-path>`
   * `/content/forms/af/<your-form-path>`
   * `/conf/<your-config-container>` (enthält `.../settings/cloudconfigs/fdm/<your-config>`)

1. Laden Sie das Paket herunter und installieren Sie es auf **Autoreninstanz** Produktion).

>[!IMPORTANT]
>
>Das Paket installiert dieselbe Konfiguration in der Produktion, einschließlich der **Service-Endpunkt-URL** aus dem Staging. Lassen Sie diese Staging-URL nicht in der Produktion. Aktualisieren Sie den -Endpunkt in der Produktion nach der Installation, wie im nächsten Abschnitt beschrieben.

### Option 2: Ansatz zum kontextabhängigen Überschreiben (für die Automatisierung empfohlen) {#option-context-aware}

Verwenden Sie diese Option, wenn Sie eine Paketkonfiguration wünschen, deren Endpunkt, Benutzername und Kennwort pro Umgebung automatisch aufgelöst werden, ohne dass nach der Bereitstellung eine manuelle Bearbeitung erfolgt. Dieser Ansatz überschreibt Konfigurationseigenschaften mithilfe von Cloud Manager-Umgebungsvariablen.

Bei REST-Konfigurationen erstellen Sie normalerweise Umgebungsvariablen für die `serviceEndPoint`-, `userName`- und `password`-Eigenschaften und verweisen dann aus einer `OsgiConfigurationOverrideProvider` Konfigurationsdatei in Ihrem Projekt darauf.

Das vollständige Verfahren finden Sie unter [Kontextabhängige Cloud-Konfigurationen](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/forms/developing-for-cloud-service/context-aware-fdm).

## Aktualisieren der Endpunkt-URL in der Produktion {#configure-endpoint-on-production}

>[!VIDEO](https://video.tv.adobe.com/v/3492387)

Nach der Installation des Pakets in der Produktion stimmen das adaptive Formular und die REST-**(Name** (z. B. `restTest`) mit der Staging-Umgebung überein. Die **Service-Endpunkt-URL** in dieser Konfiguration verweist weiterhin auf den Staging-Endpunkt aus dem Paket. Öffnen Sie die Konfiguration in der Produktionsumgebung und ersetzen Sie sie durch die Produktions-Endpunkt-URL.

1. Gehen Sie in **Produktions**-Autoreninstanz zu **Tools** > **Cloud Services** > **Data Sources**.

1. Wählen Sie den bereitgestellten Konfigurations-Container aus (z. B. `restConfigTest`) und öffnen Sie dann die benannte Konfiguration (z. B. `restTest`).

1. Legen Sie auf der **Authentifizierungseinstellungen** den **Service-Endpunkt-URL** auf den Produktions-REST- oder Webhook-Endpunkt fest.

1. Klicken Sie auf **Speichern und schließen**.

Während des Tests erhalten Sie von einem Anforderungsinspektor wie einem Webhook-Erfassungs-Service eine eindeutige URL pro Umgebung, sodass Sie überprüfen können, welcher Endpunkt jede Übermittlung erhält.

## Routing überprüfen {#verify}

>[!VIDEO](https://video.tv.adobe.com/v/3492388)

Senden Sie dasselbe Formular aus der Staging- und Produktionsumgebung und bestätigen Sie, dass jede Umgebung an ihren eigenen Endpunkt postet - nicht an die URL der anderen Umgebung.

1. Öffnen Sie in **Autoreninstanz** staging) das adaptive Formular und senden Sie es mit Testdaten (geben Sie beispielsweise `stagetest` in ein Textfeld ein). Bestätigen Sie, dass die POST-Anfrage an der Endpunkt **URL** staging **Service) eingeht** die Sie im Staging konfiguriert haben.

1. Öffnen Sie in **Autoreninstanz** Produktion) dasselbe adaptive Formular und senden Sie es mit Testdaten (geben Sie beispielsweise `prodtest` in ein Textfeld ein). Bestätigen Sie, dass die POST-Anfrage an der **Produktions** Service **Endpunkt-URL eingeht** die Sie in der Produktion konfiguriert haben, nicht an der Staging-URL.

1. Bestätigen Sie, dass jede Anfrage den erwarteten Inhaltstyp verwendet (z. B **„Mehrteilige Formulardaten**) und die gesendeten Formulardaten enthält. Verwenden Sie einen echten, gesicherten Endpunkt (HTTPS) für die Produktion.

## Best Practices {#best-practices}

* Verwenden Sie eine identische Konfiguration **Name** in jeder Umgebung, damit das Formular nach der Hochstufung konsistent aufgelöst wird.
* Den Endpunkt **Wert** umgebungsspezifisch beibehalten. Hartcodieren Sie die URL einer einzelnen Umgebung niemals in die Übermittlungsaktion des Formulars.
* Stellen Sie bei Produktions-Endpunkten sicher, dass die URL sicher ist (HTTPS) und dass der Empfangspfad so konfiguriert ist, dass die POST-Anfrage entsprechend Ihrem Authentifizierungsmodell verarbeitet wird.
* Wenn die Bereitstellung wiederholbar und frei von manuellen Bearbeitungen nach der Bereitstellung sein soll, sollten Sie den Ansatz der kontextabhängigen Überschreibung bevorzugen.

## Verwandte Artikel {#related-articles}

* [Konfigurieren eines adaptiven Formulars für die REST-Endpunkt-Übermittlungsaktion](/help/forms/configure-submit-action-restpoint.md)
* [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md)
* [Kontextsensitive Cloud-Konfigurationen](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/forms/developing-for-cloud-service/context-aware-fdm)
* [Übermittlungsaktion für adaptive Formulare](/help/forms/aem-forms-submit-action.md)
