---
title: Inhaltsfragmente - Einrichtung
description: Erfahren Sie, wie Sie Inhaltsfragmente und GraphQL für die Verwendung mit AEM Headless-Bereitstellungsfunktionen und Seitenbearbeitung aktivieren.
feature: Content Fragments
role: Developer, Architect
exl-id: 3974d698-1e7d-4a5f-a6d5-cbf8d96b4095
source-git-commit: 19685cb952a890731bd7d75a2adf3cfd841a465f
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 39%

---

# Inhaltsfragmente - Einrichtung {#content-fragments-setup}

Inhaltsfragmente in Adobe Experience Manager (AEM) as a Cloud Service ermöglichen die Vorbereitung von Inhalten für die Verwendung an mehreren Orten und über mehrere Kanäle. Dies eignet sich ideal für Headless-Bereitstellung und Seitenbearbeitung.

Um Ihre Instanz für die Inhaltsfragmentfunktionalität zu aktivieren, müssen Sie Folgendes aktivieren:

* **Inhaltsfragmentmodelle** – obligatorisch

  >[!CAUTION]
  >
  >Wenn Sie **Inhaltsfragmentmodelle** nicht aktivieren:
  >
  >* ist die Option **Erstellen** für das Erstellen von Modellen nicht verfügbar.
  >* können Sie die [Sites-Konfiguration nicht auswählen, um den entsprechenden Endpunkt zu erstellen](/help/headless/graphql-api/graphql-endpoint.md).

* **GraphQL: Beständige Abfragen** – optional

Das Einrichten der Instanz erfolgt:

* von [Aktivieren der Funktionalität im Konfigurationsbrowser](#enable-content-fragment-functionality-configuration-browser)
* then [Anwenden der Konfiguration auf Ihre einzelnen Assets-Ordner](#apply-the-configuration-to-your-folder)

## Aktivieren der Funktion &quot;Inhaltsfragment&quot;im Konfigurationsbrowser {#enable-content-fragment-functionality-configuration-browser}

Um die Funktion &quot;Inhaltsfragment&quot;von Inhaltsfragmentmodellen und von GraphQL beständigen Abfragen zu verwenden, müssen Sie **must** sie zunächst über die **Konfigurationsbrowser**:

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Konfigurationsbrowser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[Unterkonfigurationen](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (eine Konfiguration, die in einer anderen Konfiguration verschachtelt ist) werden vollständig zur Verwendung mit Inhaltsfragmenten, Inhaltsfragmentmodellen und GraphQL-Abfragen unterstützt.
>
>Beachten Sie Folgendes:
>
>* Nach dem Erstellen von Modellen in einer Unterkonfiguration ist es NICHT möglich, das Modell in eine andere Unterkonfiguration zu verschieben oder zu kopieren.
>
>* Ein GraphQL-Endpunkt basiert (weiterhin) auf einer übergeordneten (Stamm-)Konfiguration.
>
>* Beständige Abfragen werden (weiterhin) gespeichert und sind für die übergeordnete (Stamm-)Konfiguration relevant.

1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann den **Konfigurations-Browser**.

1. Öffnen Sie über **Erstellen** das Dialogfeld, in dem Sie:

   1. einen **Titel** angeben,
   1. Bei Erstellung wird die **Name** wird zum Knotennamen im Repository.
Sie können einen Namen eingeben. Wenn Sie das Feld leer lassen, wird es automatisch basierend auf dem Titel generiert und dann entsprechend angepasst. [AEM Benennungskonventionen](/help/implementing/developing/introduction/naming-conventions.md); Sie können das Ergebnis bei Bedarf anpassen.
   1. Um ihre Verwendung zu aktivieren, wählen Sie
      * **Inhaltsfragmentmodelle**
      * **GraphQL – Persistente Abfragen**

      ![Konfiguration definieren](assets/cf-setup-create-conf.png)

1. Wählen Sie **Erstellen** aus, um die Definition zu speichern.

## Wenden Sie die Konfiguration auf Ihren Ordner an {#apply-the-configuration-to-your-folder}

Wann die Konfiguration **global** für die Funktion &quot;Inhaltsfragment&quot;aktiviert ist, gilt sie dann für jeden Ordner &quot;Assets&quot;, auf den über die **Assets** Konsole.

Um andere Konfigurationen (also keine globalen) mit einem vergleichbaren Asset-Ordner zu verwenden, müssen Sie die Verbindung definieren. Wählen Sie dazu die entsprechende **Konfiguration** im **Cloud Service** des **Ordnereigenschaften** des entsprechenden Ordners.

![Konfiguration anwenden](assets/cf-setup-apply-conf.png)
