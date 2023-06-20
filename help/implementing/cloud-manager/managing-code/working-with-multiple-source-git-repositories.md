---
title: Verwenden mehrerer Repositorys
description: Erfahren Sie, wie Sie bei der Arbeit mit Cloud Manager mehrere Git-Repositorys verwalten.
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 98%

---

# Verwenden mehrerer Repositorys {#working-with-multiple-source-git-repos}

Erfahren Sie, wie Sie bei der Arbeit mit Cloud Manager mehrere Git-Repositorys verwalten.

## Synchronisieren von kundenverwalteten Git-Repositorys {#syncing-customer-managed-git-repositories}

Anstatt direkt mit dem Git-Repository von Cloud Manager zu arbeiten, können [Kunden mit ihrem eigenen Git-Repository](integrating-with-git.md) oder mehreren eigenen Git-Repositorys arbeiten. In diesen Fällen sollte ein automatisierter Synchronisierungsprozess eingerichtet werden, um sicherzustellen, dass das Git-Repository von Cloud Manager stets auf dem neuesten Stand gehalten wird.

Je nachdem, wo das Git-Repository des Kunden gehostet wird, kann eine GitHub-Aktion oder Continuous-Integration-Lösung wie Jenkins zum Einrichten der Automatisierung verwendet werden. Bei einer bereits vorhandenen Automatisierung kann jeder Push an ein im Kundenbesitz befindliches Git-Repository automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Während eine solche Automatisierung für ein einzelnes kundeneigenes Git-Repository geradlinig ist, erfordert die Automatisierung bei mehreren Repositorys eine anfängliche Einrichtung. Die Inhalte aus mehreren Git-Repositorys müssen verschiedenen Ordnern im Git-Repository von Cloud Manager zugeordnet werden.  Das Git-Repository von Cloud Manager muss mit einem Maven-Stamm-`pom.xml` bereitgestellt werden, in dem die verschiedenen Unterprojekte im Modul-Abschnitt aufgelistet werden.

Im Folgenden finden Sie eine Beispiel-`pom.xml`-Datei für zwei kundeneigene Git-Repositorys.

* Das erste Projekt wird in den Ordner namens `project-a`.
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

Eine solches Stamm-`pom.xml` wird an eine Verzweigung im Git-Repository von Cloud Manager übergeben. Anschließend müssen die beiden Projekte so eingerichtet sein, dass Änderungen automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Eine mögliche Lösung wäre die folgende.

1. Eine GitHub-Aktion kann durch eine Push-Benachrichtigung an eine Verzweigung in Projekt A ausgelöst werden.
1. Die Aktion checkt Projekt A und das Cloud Manager-Git-Repository aus und kopiert alle Inhalte aus Projekt A in das Verzeichnis `project-a` im Git-Repository von Cloud Manager.
1. Dann übergibt die Aktion die Änderung per Push.

Beispielsweise wird eine Änderung an der Hauptverzweigung in Projekt A automatisch an die Hauptverzweigung im Git-Repository von Cloud Manager übergeben. Es könnte auch eine Zuordnung zwischen Verzweigungen geben, z. B. wenn ein Push zu einer Verzweigung namens `dev` in Projekt A zu einer Verzweigung mit der Bezeichnung `development` im Git-Repository von Cloud Manager verschoben wird. Ähnliche Schritte sind für Projekt B erforderlich.

Je nach Verzweigungsstrategie und Workflows kann die Synchronisierung für verschiedene Verzweigungen konfiguriert werden. Wenn das verwendete Git-Repository kein Konzept wie GitHub-Aktionen bereitstellt, ist auch eine Integration über Jenkins (oder eine ähnliche Lösung) möglich. In diesem Fall löst ein Webhook einen Jenkins-Vorgang aus, der die Arbeit ausführt.

Gehen Sie wie folgt vor, um eine neue (dritte) Quelle oder ein neues Repository hinzuzufügen.

1. Fügen Sie eine neue GitHub-Aktion zum neuen Repository hinzu, um Änderungen von diesem Repository in das Git-Repository von Cloud Manager zu übertragen.
1. Führen Sie diese Aktion mindestens einmal aus, um sicherzustellen, dass sich der Projekt-Code im Git-Repository von Cloud Manager befindet.
1. Fügen Sie einen Verweis auf das neue Verzeichnis in der Maven-Stamm-`pom.xml` im Git-Repository von Cloud Manager hinzu.

## GitHub-Beispielaktion {#sample-github-action}

Hierbei handelt es sich um eine GitHub-Beispielaktion, die durch einen Push an die Hauptverzweigung ausgelöst und dann in ein Unterverzeichnis des Git-Repositorys von Cloud Manager gepusht wird. Die GitHub-Aktionen müssen mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, damit eine Verbindung hergestellt werden kann und eine Übertragung zum Git-Repository von Cloud Manager möglich ist.

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

Die Verwendung einer GitHub-Aktion ist sehr flexibel. Es können jegliche Zuordnungen zwischen Verzweigungen der Git-Repositorys sowie jede Zuordnung der separaten Git-Projekte in das Verzeichnis-Layout des Hauptprojekts erfolgen.

>[!NOTE]
>
>Das Beispielskript verwendet `git add`, um das Repository zu aktualisieren. Dabei wird davon ausgegangen, dass Entfernungen enthalten sind. Je nach der Standardkonfiguration von Git muss dies möglicherweise durch `git add --all` ersetzt werden.

## Jenkins-Beispielvorgang {#sample-jenkins-job}

Dies ist ein Beispielskript, das in einem Jenkins-Vorgang oder ähnlichen Aufgaben verwendet werden kann und den folgenden Ablauf aufweist:

1. Es wird durch eine Änderung in einem Git-Repository ausgelöst.
1. Der Jenkins-Vorgang überprüft den aktuellen Status dieses Projekts oder Zweigs.
1. Der Auftrag löst dann dieses Skript aus.
1. Dieses Skript überprüft wiederum das Git-Repository von Cloud Manager und übergibt den Projekt-Code an ein Unterverzeichnis.

Der Jenkins-Vorgang muss mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, damit eine Verbindung hergestellt werden kann und eine Übertragung zum Git-Repository von Cloud Manager möglich ist.

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

Die Verwendung eines Jenkins-Vorgangs ist sehr flexibel. Es können jegliche Zuordnungen zwischen Verzweigungen der Git-Repositorys sowie jede Zuordnung der separaten Git-Projekte in das Verzeichnis-Layout des Hauptprojekts erfolgen.

>[!NOTE]
>
>Das Beispielskript verwendet `git add`, um das Repository zu aktualisieren. Dabei wird davon ausgegangen, dass Entfernungen enthalten sind. Je nach der Standardkonfiguration von Git muss dies möglicherweise durch `git add --all` ersetzt werden.
