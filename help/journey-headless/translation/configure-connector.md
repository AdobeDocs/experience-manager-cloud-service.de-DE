---
title: Configure the Translation Connector
description: Learn how to connect AEM to a translation service.
exl-id: c91b2701-7ede-4d0b-93dd-3636c6638be2
source-git-commit: 3f6c96da3fd563b4c8db91ab1bc08ea17914a8c1
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 12%

---

# Configure the Translation Connector {#configure-connector}

Learn how to connect AEM to a translation service.

## Die bisherige Entwicklung {#story-so-far}

[](learn-about.md)

* Understand the importance of content structure to translation.
* Understand how AEM stores headless content.
* Be familiar with AEM&#39;s translation tools.

This article builds on those fundamentals so you can take the first configuration step and set up a translation service, which you will use later in the journey to translate your content.

## Ziel {#objective}

This document helps you understand how to set up an AEM connector to your chosen translation service. Nach dem Lesen sollten Sie:

* Understand the important parameters of the Translation Integration Framework in AEM.
* Be able to set up your own connection to your translation service.

## The Translation Integration Framework {#tif}

AEM&#39;s Translation Integration Framework (TIF) integrates with third-party translation services to orchestrate the translation of AEM content. Dies umfasst drei grundlegende Schritte.

1. Verbinden Sie sich mit Ihrem Übersetzungsdienstleister.
1. Erstellen Sie eine Framework-Konfiguration für die Übersetzungsintegration.
1. Associate the configuration with your content.

The following sections describe these steps in more detail.

## Herstellen einer Verbindung zu einem Übersetzungsdienstleister {#connect-translation-provider}

The first step is to choose which translation service you wish to use. There are many choices for human and machine translation services available to AEM. Most providers offer a translator package to be installed. [](#additional-resources)

>[!NOTE]
>
>The translation specialist is generally responsible for choosing which translation service to use, but the administrator typically is responsible for installing the required translation connector package.

For the purposes of this journey, we use the Microsoft Translator which AEM provides with a trial license out-of-the-box. [](#additional-resources)

If you choose another provider your administrator must install the connector package as per the instructions provided by the translation service.

>[!NOTE]
>
>Using the out-of-the-box Microsoft Translator in AEM does not require additional setup and works as-is without additional connector configuration.
>
>[](#create-config)[](#associate)
>
>[](#additional-resources)

## Erstellen einer Konfiguration für die Übersetzungsintegration {#create-config}

After the connector package for your preferred translation service is installed, you must create a Translation Integration Framework configuration for that service. Die Konfiguration enthält die folgenden Informationen:

* welcher Übersetzungsanbieter eingesetzt werden soll
* ob eine menschliche oder maschinelle Übersetzung erfolgen soll
* Whether to translate other content that is associated with the Content Fragment such as tags

So erstellen Sie eine neue Übersetzungskonfiguration:

1. ************
1. Navigieren Sie zu der Stelle in Ihrer Inhaltsstruktur, an der Sie die Konfiguration erstellen möchten. This is often based on a particular project or can be global.
   * For example, in this case, a configuration could be made globally to apply to all content, or just for the WKND project.

   ![](assets/translation-configuration-location.png)

1. ****
   1. Wählen Sie **Konfigurationstyp** in der Dropdown-Liste aus. ****
   1. Geben Sie einen **Titel** für Ihre Konfiguration ein. Mit dem **Titel** wird die Konfiguration auf der **Cloud Services**-Konsole und in Dropdown-Listen mit den Seiteneigenschaften identifiziert.
   1. Geben Sie optional einen **Namen** für den Repository-Knoten ein, auf dem die Konfiguration gespeichert wird.

   ![Erstellen einer Übersetzungskonfiguration](assets/create-translation-configuration.png)

1. ********

1. Remember that Content Fragments are stored as assets in AEM. ****

![](assets/translation-configuration.png)

1. Geben Sie die folgenden Informationen ein.

   1. ************ For the purposes of this journey we assume machine translation.
   1. ****
   1. ****
   1. ****
   1. ****
   1. ****
   1. ****
   1. ****

1. Tippen oder klicken Sie auf **Speichern und schließen**.

You have now configured the connector to your translation service.

## Associate the Configuration with Your Content {#associate}

AEM is a flexible and powerful tool and supports multiple, simultaneous translation services via multiple connectors and multiple configurations. Setting up such a configuration is beyond the scope of this journey. However this flexibility means that you must specify which connectors and configuration should be used to translate your content by associating ths configuration with your content.

To do this, navigate to the language root of your content. For our example purposes this is

```text
/content/dam/<your-project>/en
```

1. ************
1. ****
1. ****
1. ******** [](#connect-translation-provider)
1. ********
1. Tippen oder klicken Sie auf **Speichern und schließen**.

![](assets/select-cloud-service-configurations.png)

## Wie geht es weiter {#what-is-next}

Now that you have completed this part of the headless translation journey you should:

* Understand the important parameters of the Translation Integration Framework in AEM.
* Be able to set up your own connection to your translation service.

[](translation-rules.md)

## Zusätzliche Ressourcen {#additional-resources}

[](translation-rules.md)

* [](/help/sites-cloud/administering/translation/integration-framework.md)
* [](/help/sites-cloud/administering/translation/connect-ms-translator.md)
