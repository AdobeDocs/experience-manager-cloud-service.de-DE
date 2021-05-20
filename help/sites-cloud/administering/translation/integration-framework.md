---
title: Konfigurieren des Frameworks für die Übersetzungsintegration
description: Erfahren Sie, wie Sie das Framework für die Übersetzungsintegration für die Integration mit Übersetzungsdiensten von Drittanbietern konfigurieren.
feature: Sprachkopie
role: Administrator
exl-id: 6e74cdee-7965-4087-a733-e9d81c4aa7c2
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 43%

---

# Konfigurieren des Frameworks für die Übersetzungsintegration {#configuring-the-translation-integration-framework}

Das Framework für die Übersetzungsintegration integriert Übersetzungsdienstleistungen von Drittanbietern, um die Übersetzung von AEM-Inhalten zu orchestrieren. Es umfasst drei grundlegende Schritte.

1. [Verbinden Sie sich mit Ihrem Übersetzungsdienstleister.](#connecting-to-a-translation-service-provider)
1. [Erstellen Sie eine Framework-Konfiguration für die Übersetzungsintegration.](#creating-a-translation-integration-configuration)
1. [Verknüpfen Sie die Cloudkonfigurationen mit Ihren Seiten.](#configuring-pages-for-translation)

Einen Überblick über die Funktionen zur Übersetzung von Inhalten in AEM finden Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](overview.md).

## Herstellen einer Verbindung zu einem Übersetzungsdienstleister {#connecting-to-a-translation-service-provider}

Erstellen Sie eine Cloudkonfiguration, die AEM an Ihren Übersetzungsdienstleister anbindet. AEM beinhaltet standardmäßig die Funktion [Verbindung zu Microsoft Translator](connect-ms-translator.md) herstellen.

Die folgenden Übersetzungsanbieter stellen eine Implementierung der AEM-API für Übersetzungsprojekte bereit.

* [Microsoft Translator](connect-ms-translator.md)
* [Translations.com](https://exchange.adobe.com/experiencecloud.details.90104.globallink-connect-plus-for-aem.html)  (Adobe Exchange Premier Partner)
* [Clay Tablet Technologies](https://exchange.adobe.com/experiencecloud.details.90064.clay-tablet-translation-for-experience-manager.html)
* [Lionbridge](https://exchange.adobe.com/experiencecloud.details.100064.lionbridge-connector-for-experience-manager-63.html)
* [Memsource](https://exchange.adobe.com/experiencecloud.details.103166.memsource-connector-for-adobe-experience-manager.html)
* [Cloudwords](https://exchange.adobe.com/experiencecloud.details.90019.html)
* [CrossLang NV](https://exchange.adobe.com/experiencecloud.details.90049.crosslang-xtm-for-adobe-experience-manager.html)
* [Lingotek](https://exchange.adobe.com/experiencecloud.details.90088.lingotek-collaborative-translation-platform.html)
* [Smartling](https://exchange.adobe.com/experiencecloud.details.90101.smartling-connector-for-adobe-experience-manager.html)
* [SDL](https://exchange.adobe.com/experiencecloud.details.100110.sdl-translation-management.html)
* [Systran](https://exchange.adobe.com/experiencecloud.details.90233.systran-for-adobe-experience-manager.html)

Wenn Sie ein Connector-Paket installiert haben, können Sie eine Cloudkonfiguration für den Connector erstellen. In der Regel müssen Sie Ihre Anmeldedaten für die Authentifizierung beim Übersetzungsdienst angeben. Weitere Informationen zum Hinzufügen einer Cloudkonfiguration für den Microsoft Translator-Connector finden Sie unter [Integrieren mit Microsoft Translator](connect-ms-translator.md).

Sie können mehrere Cloudkonfigurationen für denselben Connector erstellen, falls erforderlich. Beispielsweise können Sie eine Konfiguration für jedes Konto oder Projekt erstellen, das Sie bei einem Anbieter haben.

Nach der Konfiguration einer Verbindung können Sie die Framework-Konfiguration für die Übersetzungsintegration erstellen, von der diese Verbindung genutzt wird.

## Erstellen einer Konfiguration für die Übersetzungsintegration {#creating-a-translation-integration-configuration}

Erstellen Sie eine Framework-Konfiguration für die Übersetzungsintegration, um festzulegen, wie Ihre Inhalte übersetzt werden sollen. Die Konfiguration enthält die folgenden Informationen:

* Welcher Übersetzungsanbieter verwendet werden soll
* Ob menschliche oder maschinelle Übersetzung durchgeführt werden soll
* Ob andere Inhalte übersetzt werden sollen, die mit einer Seite oder einem Asset verknüpft sind, z. B. Tags

Nachdem Sie eine Framework-Konfiguration erstellt haben, verknüpfen Sie die Cloudkonfiguration mit den Seiten, die Sie gemäß der Konfiguration übersetzen möchten. Wenn der Übersetzungsvorgang gestartet wird, geht der Übersetzungsworkflow entsprechend der verknüpften Framework-Konfiguration vor.

Wenn für verschiedene Bereiche Ihrer Website unterschiedliche Übersetzungsanforderungen vorliegen, erstellen Sie entsprechend mehrere Framework-Konfigurationen. Eine mehrsprachige Website kann beispielsweise englische, spanische und japanische Sprachkopien enthalten. Der Website-Eigentümer nutzt zwei verschiedene Übersetzungsdienstleister für die englische und die deutsche Übersetzung. Daher werden zwei verschiedene Konfigurationen des Frameworks erstellt. Jede Konfiguration nutzt einen anderen Übersetzungsdienstleister.

Nachdem Sie ein Framework für die Übersetzungsintegration konfiguriert haben, können Sie [es mit den Seiten](preparation.md) verknüpfen, die es verwenden.

>[!TIP]
>
>Einen Überblick über die Funktionen zur Übersetzung von Inhalten in AEM finden Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](overview.md).

Eine einzelne Konfiguration des Frameworks steuert, wie Seiteninhalte und Assets übersetzt werden.

![Übersetzungskonfiguration](../assets/translation-configuration.png) 

So erstellen Sie eine neue Übersetzungskonfiguration:

1. Klicken oder tippen Sie im globalen Navigationsmenü [a1/> auf **Tools -> Cloud Services -&amp; Übersetzungs-Cloud Services**.](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation)
1. Navigieren Sie zu der Stelle, an der Sie die Konfiguration in Ihrer Inhaltsstruktur erstellen möchten. Dies basiert häufig auf einer bestimmten Site oder kann global sein.
1. Geben Sie die folgenden Informationen in die Felder ein und klicken oder tippen Sie auf **Erstellen**:
   1. Wählen Sie **Konfigurationstyp** in der Dropdown-Liste aus.
   1. Geben Sie einen **Titel** für Ihre Konfiguration ein. Der **Titel** gibt die Konfiguration in der Konsole **Cloud Services** sowie in den Dropdown-Listen für Seiteneigenschaften an.
   1. Geben Sie optional einen **Namen** ein, der für den Repository-Knoten verwendet werden soll, der die Konfiguration speichert.
1. Konfigurieren Sie im Fenster **Konfiguration bearbeiten** die Eigenschaften auf den Registerkarten **Sites** und **Assets** und klicken oder tippen Sie dann auf **Speichern und schließen**.

### Website-Konfigurationseigenschaften {#sites-configuration-properties}

Die Registerkarte **Sites** steuert, wie die Übersetzung von Seiteninhalten ausgeführt wird.

| Eigenschaft | Beschreibung |
|---|---|
| Übersetzungs-Workflow | Diese Eigenschaft definiert die Übersetzungsmethode, die das Framework für Site-Inhalte durchführt:<br>- Maschinelle Übersetzung: Der Übersetzungsanbieter führt die Übersetzung mithilfe der maschinellen Übersetzung in Echtzeit durch.<br>- Menschliche Übersetzung: Der Übersetzungsdienstleister bekommt die Inhalte zugesendet und lässt sie durch Übersetzer übersetzen.<br>- Nicht übersetzen: Inhalt wird nicht zur Übersetzung gesendet. Damit können Sie bestimmte Inhaltszweige überspringen, die nicht übersetzt, aber mit den neuesten Inhalten aktualisiert werden sollen. |
| Übersetzungsanbieter | Diese Eigenschaft definiert den Übersetzungsanbieter, der die Übersetzung durchführt. Ein Provider wird in der Liste angezeigt, wenn der entsprechende Connector installiert ist. |
| Inhaltskategorie | (Nur maschinelle Übersetzung) Diese Eigenschaft ist eine Kategorie, die den zu übersetzenden Inhalt beschreibt. Die Kategorie kann beeinflussen, welche Terminologie und welche Formulierungen bei der Übersetzung von Inhalten verwendet werden. |
| Tags übersetzen | Diese Option ermöglicht die Übersetzung von Tags, die mit der Seite verknüpft sind. |
| Seiten-Assets übersetzen | Diese Eigenschaft definiert, wie Assets übersetzt werden, die zu Komponenten aus dem Dateisystem hinzugefügt oder aus Assets referenziert werden:<br>- Nicht übersetzen: Seiten-Assets werden nicht übersetzt.<br>- Verwendung des Übersetzungs-Workflows für Sites: Assets werden gemäß den Konfigurationseigenschaften auf der  **** Sitestab verarbeitet.<br>- Workflow für die Übersetzung von Assets verwenden: Assets werden entsprechend den auf der  **** Assetstab konfigurierten Eigenschaften verarbeitet. |
| Übersetzung automatisch ausführen | Aktivieren Sie diese Eigenschaft, um Übersetzungsaufträge automatisch auszuführen, nachdem Übersetzungsprojekte erstellt wurden. Bei dieser Option haben Sie keine Möglichkeit, den Übersetzungsauftrag zu prüfen und seinen Umfang zu ermitteln. |

### Assets-Konfigurationseigenschaften {#assets-configuration-properties}

Asset-Eigenschaften steuern, wie Assets konfiguriert werden. Weitere Informationen zum Übersetzen von Assets finden Sie unter [Erstellen von Sprachkopien für Assets](/help/assets/translate-assets.md).

| Eigenschaft | Beschreibung |
|---|---|
| Übersetzungs-Workflow | Diese Eigenschaft wählt den Übersetzungstyp aus, den das Framework für Assets durchführt:<br>- Maschinelle Übersetzung: Der Übersetzungsanbieter führt die Übersetzung mithilfe der maschinellen Übersetzung sofort durch.<br>- Menschliche Übersetzung: Der Übersetzungsdienstleister bekommt die Inhalte automatisch zugesendet und lässt sie durch Übersetzer übersetzen.<br>-Nicht übersetzen: Assets werden nicht zur Übersetzung gesendet. |
| Übersetzungsanbieter | Diese Eigenschaft definiert den Übersetzungsanbieter, der die Übersetzung durchführt. Ein Provider wird in der Liste angezeigt, wenn der entsprechende Connector installiert ist. |
| Inhaltskategorie | (Nur maschinelle Übersetzung) Diese Eigenschaft beschreibt den Inhalt, den Sie übersetzen. Die Kategorie kann beeinflussen, welche Terminologie und welche Formulierungen bei der Übersetzung von Inhalten verwendet werden. |
| Assets übersetzen | Aktivieren Sie diese Eigenschaft, um Assets in das Übersetzungsprojekt einzubeziehen. |
| Metadaten übersetzen | Aktivieren Sie diese Eigenschaft, um Asset-Metadaten zu übersetzen. |
| Tags übersetzen | Aktivieren Sie diese Eigenschaft, um Tags zu übersetzen, die mit dem Asset verknüpft sind. |
| Übersetzung automatisch ausführen | Wählen Sie diese Eigenschaft aus, um Übersetzungsaufträge nach der Erstellung von Übersetzungsprojekten automatisch auszuführen. Bei dieser Option haben Sie keine Möglichkeit, den Übersetzungsauftrag zu prüfen und seinen Umfang zu ermitteln. |

## Konfigurieren von Seiten für Übersetzungen {#configuring-pages-for-translation}

Um die Übersetzung Ihrer Quellseiten in andere Sprachen zu konfigurieren, verknüpfen Sie die Seiten mit den folgenden Cloudkonfigurationen:

* mit der Cloudkonfiguration, die AEM an Ihren Übersetzungsdienstleister anbindet
* mit dem Framework für die Übersetzungsintegration, das die Details der Übersetzung konfiguriert

Beachten Sie, dass die Cloudkonfiguration des Frameworks für die Übersetzungsintegration festlegt, mit welcher Cloudkonfiguration die Verbindung mit dem Dienstleister hergestellt wird. Wenn Sie eine Quellseite mit der Cloudkonfiguration eines Frameworks verknüpfen, muss die Seite mit der Cloudkonfiguration des Dienstleisters verknüpft sein, die die Cloudkonfiguration des Frameworks nutzt.

Wenn Sie eine Seite mit einer Cloudkonfiguration verknüpfen, erben die untergeordneten Elemente der Seite diese Verknüpfung. Wenn Sie beispielsweise die Seite `/content/wknd/language-masters/en/magazine` mit einem Übersetzungsintegrations-Framework verknüpfen, werden die Seite `magazine` und die untergeordneten Seiten darunter entsprechend dem Framework übersetzt.

Bei Bedarf können Sie die Verknüpfung auf einer untergeordneten Seite überschreiben. Zum Beispiel geht es beim Inhalt einer Website hauptsächlich um Reisen und Lebensstil. Ein Zweig an Seiten beschreibt dagegen das Unternehmen. In einem solchen Fall kann die Stammseite der Site mit einem Framework für die Integration von Übersetzungen verknüpft sein, das die maschinelle Übersetzung mithilfe der Kategorie &quot;Lifestyle&quot;angibt, während die Zweigstelle, die das Unternehmen beschreibt, ein Framework verwendet, das maschinelle Übersetzung unter Verwendung der Kategorie &quot;Allgemein&quot;durchführt.

### Verknüpfen einer Seite mit einem Übersetzungsdienstleister {#associating-a-page-with-a-translation-provider}

Verknüpfen Sie eine Seite mit Ihrem Übersetzungsdienstleister, um die Seite und ihre untergeordneten Seiten zu übersetzen.

1. Wählen Sie in der Sites-Konsole die zu konfigurierende Seite aus und klicken oder tippen Sie auf **Eigenschaften anzeigen**.
1. Klicken oder tippen Sie auf die Registerkarte **Cloud Services** .
1. Wählen Sie im Dropdown-Menü **Konfiguration hinzufügen** die Konfiguration aus.
1. Klicken oder tippen Sie auf **Speichern und schließen**.

### Verknüpfen von Seiten mit einem Framework für die Übersetzungsintegration {#associating-pages-with-a-translation-integration-framework}

Verknüpfen Sie eine Seite mit dem Framework für die Übersetzungsintegration, das festlegt, wie die Übersetzung der Seite und der untergeordneten Seiten durchgeführt werden soll.

1. Wählen Sie in der Sites-Konsole die zu konfigurierende Seite aus und klicken oder tippen Sie auf **Eigenschaften anzeigen**.
1. Klicken oder tippen Sie auf die Registerkarte **Cloud Services** .
1. Wählen Sie im Dropdown-Menü **Konfiguration hinzufügen** die Konfiguration aus.
1. Klicken oder tippen Sie auf **Speichern und schließen**.
