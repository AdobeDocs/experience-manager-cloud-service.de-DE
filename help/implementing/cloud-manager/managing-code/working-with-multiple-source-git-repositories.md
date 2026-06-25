---
title: Verwenden mehrerer Repositorys
description: Erfahren Sie, wie Sie bei der Arbeit mit Cloud Manager mehrere Git-Repositorys verwalten.
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 40c7b033edde97cdc826efbe961105ca264525d9
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 61%

---

# Verwenden mehrerer Repositorys {#working-with-multiple-source-git-repos}

Erfahren Sie, wie Sie bei der Arbeit mit Cloud Manager mehrere Git-Repositorys verwalten.

## Synchronisieren von privaten Git-Repositorys {#syncing-customer-managed-git-repositories}

Anstatt direkt mit dem Git-Repository von Cloud Manager zu arbeiten[&#x200B; können Kunden mit ihrem eigenen privaten Git-Repository &#x200B;](integrating-with-git.md) mehreren privaten Git-Repositorys arbeiten. Richten Sie einen automatisierten Synchronisierungsprozess ein, um sicherzustellen, dass das Git-Repository in Cloud Manager immer auf dem neuesten Stand ist.

Je nachdem, wo das Git-Repository des Kunden gehostet wird, richtet eine GitHub-Aktion oder Continuous-Integration-Lösung wie Jenkins die Automatisierung ein. Bei vorhandener Automatisierung kann jeder Push an ein kundeneigenes Git-Repository automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Während eine solche Automatisierung für ein einzelnes kundeneigenes Git-Repository einfach ist, erfordert die Konfiguration für mehrere Repositorys eine Ersteinrichtung. Die Inhalte aus mehreren Git-Repositorys müssen verschiedenen Ordnern im einzigen Git-Repository von Cloud Manager zugeordnet werden. Das Git-Repository von Cloud Manager muss mit einer Maven-Stamm-Datei `pom.xml` bereitgestellt werden, in der die verschiedenen Unterprojekte im Modul-Abschnitt aufgelistet werden.

Im Folgenden finden Sie ein Beispiel einer Datei `pom.xml` für zwei kundeneigene Git-Repositorys.

* Das erste Projekt wird im Verzeichnis namens `project-a` abgelegt.
* Das zweite Projekt wird im Verzeichnis namens `project-b` abgelegt.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
  
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
  
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
  
</project>
```

Eine solche Stammdatei `pom.xml` wird per Push an eine Verzweigung im Git-Repository von Cloud Manager übergeben. Anschließend müssen die beiden Projekte so eingerichtet werden, dass Änderungen automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Folgendes ist eine mögliche Lösung.

1. Lösen Sie eine GitHub-Aktion durch eine Push-Benachrichtigung an eine Verzweigung in Projekt A aus.
1. Bei der Aktion werden Projekt A und das Cloud Manager-Git-Repository ausgecheckt. Dabei werden alle Inhalte aus Projekt A in das Verzeichnis `project-a` des Git-Repositorys von Cloud Manager kopiert.
1. Dann übergibt die Aktion und pusht die Änderung.

Beispielsweise wird eine Änderung in der Hauptverzweigung in Projekt A automatisch in die Hauptverzweigung im Git-Repository von Cloud Manager gepusht. Es gibt eine Zuordnung zwischen Verzweigungen, z. B. wenn ein Push zu einer Verzweigung namens `dev` in Projekt A zu einer Verzweigung mit der Bezeichnung `development` im Git-Repository von Cloud Manager verschoben wird. Ähnliche Schritte sind für Projekt B erforderlich.

Je nach Verzweigungsstrategie und Workflows kann die Synchronisierung für verschiedene Verzweigungen konfiguriert werden. Wenn das verwendete Git-Repository kein Konzept wie GitHub-Aktionen bereitstellt, ist auch eine Integration über Jenkins (oder Ähnliches) möglich. In diesem Fall führt ein Webhook einen Jenkins-Auftrag aus, der die Aufgabe ausführt.

Gehen Sie wie folgt vor, um eine neue, dritte Quelle oder ein neues Repository hinzuzufügen.

1. Fügen Sie eine GitHub-Aktion zum neuen Repository hinzu, um Änderungen von diesem Repository in das Git-Repository von Cloud Manager zu übertragen.
1. Um sicherzustellen, dass sich der Projekt-Code im Git-Repository von Cloud Manager befindet, führen Sie diese Aktion mindestens einmal durch.
1. Fügen Sie im Git-Repository von Cloud Manager in der Maven-Stamm-Datei `pom.xml` einen Verweis auf das neue Verzeichnis hinzu.



## Beispiel einer GitHub-Aktion {#sample-github-action}

Im Folgenden finden Sie ein Beispiel für eine GitHub-Aktion, die durch eine Push-Benachrichtigung an die Hauptverzweigung ausgelöst wird. Pushen Sie dann in ein Unterverzeichnis des Git-Repositorys von Cloud Manager. Die GitHub-Aktion muss mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, damit eine Verbindung hergestellt werden kann und eine Übertragung zum Git-Repository von Cloud Manager möglich ist.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} ${MAIN_REPOSITORY} ${MAIN_BRANCH} 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf ${MAIN_BRANCH}/${PROJECT_DIR} 
          mv sub ${MAIN_BRANCH}/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C ${MAIN_BRANCH} add -f ${PROJECT_DIR}
          git -C ${MAIN_BRANCH} commit -F ../commit.txt
          git -C ${MAIN_BRANCH} push
```

Die Verwendung einer GitHub-Aktion ist flexibel. Es können beliebige Zuordnungen zwischen Verzweigungen der Git-Repositorys sowie beliebige Zuordnungen der separaten Git-Projekte in das Verzeichnis-Layout des Hauptprojekts durchgeführt werden.

>[!NOTE]
>
>Das Beispielskript verwendet `git add` zum Staging von Dateien im Repository. Das Skript setzt voraus, dass das Entfernen von Daten verarbeitet wird. Ersetzen Sie sie je nach Standardkonfiguration von Git durch `git add --all`.

## Jenkins-Beispielauftrag {#sample-jenkins-job}

Das folgende ist ein Beispielskript, das in einem Jenkins-Auftrag oder ähnlichen Aufgaben verwendet werden kann und den folgenden Ablauf aufweist:

1. Eine Änderung in einem Git-Repository ist hierfür der Auslöser.
1. Der Jenkins-Auftrag überprüft den aktuellen Status dieses Projekts oder Zweigs.
1. Der Auftrag löst dann dieses Skript aus.
1. Dieses Skript überprüft wiederum das Git-Repository von Cloud Manager und übergibt den Projekt-Code an ein Unterverzeichnis.

Der Jenkins-Auftrag muss mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung herstellen und zum Git-Repository von Cloud Manager übertragen werden zu können.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

Die Verwendung eines Jenkins-Auftrags ist flexibel. Es können beliebige Zuordnungen zwischen Verzweigungen der Git-Repositorys sowie beliebige Zuordnungen der separaten Git-Projekte in das Verzeichnis-Layout des Hauptprojekts durchgeführt werden.

>[!NOTE]
>
>Das Beispielskript verwendet `git add`, um das Repository zu aktualisieren. Das Skript setzt voraus, dass Entfernungen verarbeitet werden. Je nach der Standardkonfiguration von Git muss dies möglicherweise durch `git add --all` ersetzt werden.
