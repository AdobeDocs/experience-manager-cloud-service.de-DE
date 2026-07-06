---
title: Entfernen von externen Abhängigkeiten für vorhandene Installationen
description: Entfernen von externen Abhängigkeiten für vorhandene Installationen
feature: Workfront Integrations and Apps
exl-id: 5b28ce97-2719-47b8-a386-77d4aaddbe81
role: Admin
source-git-commit: 230ca753bd5f3d5b26b30a962a526dc0edfc9bd4
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%

---

# Entfernen von externen Abhängigkeiten für vorhandene Installationen {#remove-external-depedencies}

Adobe empfiehlt die Ausführung von Konfigurationsschritten für bestehende erweiterte Connector-Installationen für Workfront, um die Abhängigkeiten von Hoodoo-Verteilungspunkten zu beseitigen.

>[!NOTE]
>
>Führen Sie die Konfigurationsschritte nur aus, wenn Sie den erweiterten Connector für Workfront vor März 2022 installiert haben. Es gibt keine Abhängigkeiten von Hoodoo-Verteilungspunkten für neue erweiterte Connector-Installationen für Workfront ab März 2022.

So entfernen Sie die externen Abhängigkeiten:

1. Entfernen Sie die folgende Hoodoo-Repository-Konfiguration aus der übergeordneten `pom.xml`:

   ```XML
     <repository>
        <id>hoodoo-maven</id>
        <name>Hoodoo Repository</name>
        <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
     </repository>
   ```

1. Entfernen Sie die folgende Serverkonfiguration aus der Datei `settings.xml`, verfügbar unter `./cloudmanager/maven/settings.xml`:

   ```XML
         <server>
            <id>hoodoo-maven</id>
            <configuration>
               <httpHeaders>
                     <property>
                        <name>Deploy-Token</name>
                        <value>xxxxxxxxxxxxxxxx</value>
                     </property>
               </httpHeaders>
            </configuration>
         </server>
   ```

1. Führen Sie die [neuen Installationsschritte](workfront-connector-install.md) aus.


**Siehe auch**

* [Assets übersetzen](/help/assets/translate-assets.md)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](/help/assets/file-format-support.md)
* [Suchen von Assets](/help/assets/search-assets.md)
* [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](/help/assets/asset-reports.md)
* [Metadatenschemata](/help/assets/metadata-schemas.md)
* [Herunterladen von Assets](/help/assets/download-assets-from-aem.md)
* [Verwalten von Metadaten](/help/assets/manage-metadata.md)
* [Verwalten von Dynamic Media-Vorlagen](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Verwalten von Berichten](/help/assets/manage-reports-assets-view.md)
* [Suchfacetten](/help/assets/search-facets.md)
* [Verwalten von Sammlungen](/help/assets/manage-collections.md)
* [Massenimport von Metadaten](/help/assets/metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
