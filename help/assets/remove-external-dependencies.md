---
title: Entfernen von externen Abhängigkeiten für vorhandene Installationen
description: Entfernen von externen Abhängigkeiten für vorhandene Installationen
feature: Workfront Integrations and Apps
exl-id: 5b28ce97-2719-47b8-a386-77d4aaddbe81
role: Admin
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '104'
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
