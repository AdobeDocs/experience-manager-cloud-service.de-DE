---
title: Externe Abhängigkeiten für vorhandene Installationen entfernen
description: Installieren [!DNL Workfront for Experience Manager enhanced connector]
feature: Integrations
source-git-commit: b61915a27968b11472ae458d7be3d73f3449fbbe
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 1%

---


# Externe Abhängigkeiten für vorhandene Installationen entfernen {#remove-external-depedencies}

Adobe empfiehlt, Konfigurationsschritte für bestehende erweiterte Connector-Installationen für Workfront auszuführen, um die Abhängigkeiten von Hoodoo-Verteilungspunkten zu entfernen.

>[!NOTE]
>
>Führen Sie die Konfigurationsschritte nur aus, wenn Sie den erweiterten Connector für Workfront vor März 2022 installiert haben. Es gibt keine Abhängigkeiten von Hoodoo-Verteilungspunkten für neue erweiterte Connector-Installationen für Workfront ab März 2022.

So entfernen Sie die externen Abhängigkeiten:

1. Entfernen Sie die folgende Hoodoo-Repository-Konfiguration aus dem übergeordneten `pom.xml`:

   ```XML
     <repository>
        <id>hoodoo-maven</id>
        <name>Hoodoo Repository</name>
        <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
     </repository>
   ```

1. Entfernen Sie die folgende Serverkonfiguration aus der `settings.xml` Datei verfügbar unter `./cloudmanager/maven/settings.xml`:

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

1. Führen Sie die [neue Installationsschritte](workfront-connector-install.md).

