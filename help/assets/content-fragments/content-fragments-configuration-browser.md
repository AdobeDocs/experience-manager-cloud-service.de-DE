---
title: Inhaltsfragmente – Konfigurations-Browser (Assets – Inhaltsfragmente)
description: Erfahren Sie, wie Sie Inhaltsfragmentfunktionen im Konfigurations-Browser aktivieren.
exl-id: 9fc911de-1d33-4811-8f58-ea21ce94bedb
source-git-commit: 1fc57dacbf811070664d5f5aaa591dd705516fa8
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 37%

---

# Inhaltsfragmente – Konfigurations-Browser{#content-fragments-configuration-browser}

Erfahren Sie, wie Sie bestimmte Inhaltsfragmentfunktionen im Konfigurationsbrowser für die Verwendung AEM leistungsstarken Headless-Bereitstellungsfunktionen aktivieren.

## Aktivieren der Funktionen für Inhaltsfragmente für Ihre Instanz {#enable-content-fragment-functionality-instance}

Bevor Sie Inhaltsfragmente verwenden, müssen Sie die **Konfigurationsbrowser** aktivieren:

* **Inhaltsfragmentmodelle** – obligatorisch
* **GraphQL: Beständige Abfragen** – optional

>[!CAUTION]
>
>Wenn Sie **Inhaltsfragmentmodelle** nicht aktivieren:
>
>* die **Erstellen** ist nicht zum Erstellen von Modellen verfügbar.
>* kann [Wählen Sie die Sites-Konfiguration aus, um den zugehörigen Endpunkt zu erstellen.](/help/headless/graphql-api/graphql-endpoint.md).

Um die Funktion für Inhaltsfragmente zu aktivieren, müssen Sie die folgenden Schritte ausführen:

* Aktivieren der Verwendung der Inhaltsfragmentfunktionalität über den Konfigurationsbrowser
* Wenden Sie die Konfiguration auf Ihren Assets-Ordner an.

### Aktivieren der Funktionen für Inhaltsfragmente im Konfigurations-Browser {#enable-content-fragment-functionality-in-configuration-browser}

Verwendung bestimmter [Inhaltsfragmentfunktionalität](#creating-a-content-fragment-model), **must** sie zunächst über die **Konfigurationsbrowser**:

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Konfigurationsbrowser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[Unterkonfigurationen](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (eine in einer anderen Konfiguration verschachtelte Konfiguration) werden vollständig für die Verwendung mit Inhaltsfragmenten, Inhaltsfragmentmodellen und GraphQL-Abfragen unterstützt.
>
>Beachten Sie Folgendes:
>
>
>* Nach dem Erstellen von Modellen in einer Unterkonfiguration ist es NICHT möglich, das Modell in eine andere Unterkonfiguration zu verschieben oder zu kopieren.
>
>* Ein GraphQL-Endpunkt basiert (noch) auf einer übergeordneten (Stamm-)Konfiguration.
>
>* Beständige Abfragen werden (noch) gespeichert und sind für die übergeordnete (Stamm-)Konfiguration relevant.


1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann den **Konfigurations-Browser**.

1. Öffnen Sie über **Erstellen** das Dialogfeld, in dem Sie:

   1. einen **Titel** angeben,
   1. Die **Name** wird zum Knotennamen im Repository.
      * Sie wird automatisch anhand des Titels generiert und entsprechend angepasst [AEM Benennungskonventionen.](/help/implementing/developing/introduction/naming-conventions.md)
      * Sie können sie bei Bedarf anpassen.
   1. Um ihre Verwendung zu aktivieren, wählen Sie
      * **Inhaltsfragmentmodelle**
      * **GraphQL – Persistente Abfragen**

      ![Konfiguration definieren](assets/cfm-conf-01.png)

1. Wählen Sie **Erstellen** aus, um die Definition zu speichern.

<!-- 1. Select the location appropriate to your website. -->

### Anwenden der Konfiguration auf Ihren Assets-Ordner {#apply-the-configuration-to-your-assets-folder}

Wenn die Konfiguration **Global** für die Inhaltsfragmentfunktionalität aktiviert ist, gilt sie für jeden Assets-Ordner.

Um andere Konfigurationen (d. h. ohne globale Konfigurationen) mit einem vergleichbaren Asset-Ordner zu verwenden, müssen Sie die Verbindung definieren. Diese Verbindung wird hergestellt, indem Sie die entsprechende **Konfiguration** im **Cloud Services** des **Ordnereigenschaften** des entsprechenden Ordners.

![Konfiguration anwenden](assets/cfm-conf-02.png)
