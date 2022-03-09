---
title: Verwenden mehrerer Repositorys
description: Erfahren Sie, wie Sie bei der Arbeit mit Cloud Manager mehrere Git-Repositorys verwalten.
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
source-git-commit: a7555507f4fb0fb231e27d7c7a6413b4ec6b94e6
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 6%

---

# Verwenden mehrerer Repositorys {#working-with-multiple-source-git-repos}

Erfahren Sie, wie Sie bei der Arbeit mit Cloud Manager mehrere Git-Repositorys verwalten.

## Synchronisieren von kundenverwalteten Git-Repositorys {#syncing-customer-managed-git-repositories}

Anstatt direkt mit dem Git-Repository von Cloud Manager zu arbeiten, [-Kunden können mit einem eigenen Git-Repository arbeiten](integrating-with-git.md) oder mehreren eigenen Git-Repositorys. In diesen Fällen sollte ein automatisierter Synchronisierungsprozess eingerichtet werden, um sicherzustellen, dass das Git-Repository von Cloud Manager stets auf dem neuesten Stand gehalten wird.

Je nachdem, wo das Git-Repository des Kunden gehostet wird, kann zur Einrichtung der Automatisierung eine GitHub-Aktion oder eine kontinuierliche Integrationslösung wie Jenkins verwendet werden. Mit einer vorhandenen Automatisierung kann jeder Push an ein kundeneigenes Git-Repository automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Während eine solche Automatisierung für ein einzelnes kundeneigenes Git-Repository unkompliziert ist, erfordert die Konfiguration für mehrere Repositorys eine Ersteinrichtung. Die Inhalte aus mehreren Git-Repositorys müssen verschiedenen Ordnern innerhalb des einzelnen Cloud Manager-Git-Repositorys zugeordnet werden.  Das Git-Repository von Cloud Manager muss mit einem Maven-Stamm bereitgestellt werden `pom.xml`, in der die verschiedenen Unterprojekte im Abschnitt Module aufgelistet werden.

Im Folgenden finden Sie ein Beispiel `pom.xml` Datei für zwei kundeneigene Git-Repositorys.

* Das erste Projekt wird in das Verzeichnis namens `project-a`.
* Das zweite Projekt wird in den Ordner namens `project-b`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
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

Diese Wurzel `pom.xml` wird in eine Verzweigung im Git-Repository von Cloud Manager gepusht. Anschließend müssen die beiden Projekte so eingerichtet sein, dass Änderungen automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Eine mögliche Lösung wäre die folgende.

1. Eine GitHub-Aktion kann durch eine Push-Benachrichtigung an eine Verzweigung in Projekt A ausgelöst werden.
1. Die Aktion checkt Projekt A und das Cloud Manager-Git-Repository aus und kopiert alle Inhalte aus Projekt A in das Verzeichnis `project-a` im Git-Repository von Cloud Manager.
1. Dann wird die Aktion die Änderung übergeben.

Beispielsweise wird eine Änderung an der Hauptverzweigung in Projekt A automatisch an die Hauptverzweigung im Git-Repository von Cloud Manager übergeben. Natürlich kann es eine Zuordnung zwischen Verzweigungen geben, wie eine Push-Benachrichtigung zu einer Verzweigung mit dem Namen `dev` in Projekt A an eine Verzweigung mit dem Namen `development` im Git-Repository von Cloud Manager. Ähnliche Schritte sind für Projekt B erforderlich.

Je nach Verzweigungsstrategie und Workflows kann die Synchronisierung für verschiedene Verzweigungen konfiguriert werden. Wenn das verwendete Git-Repository kein Konzept bereitstellt, das GitHub-Aktionen ähnelt, ist auch eine Integration über Jenkins (oder Ähnliches) möglich. In diesem Fall Trigger ein Webhook einen Jenkins-Job, der die Arbeit ausführt.

Führen Sie diese Schritte aus, um eine neue, dritte Quelle oder ein neues Repository hinzuzufügen.

1. Fügen Sie dem neuen Repository eine neue GitHub-Aktion hinzu, die Änderungen von diesem Repository in das Git-Repository von Cloud Manager überträgt.
1. Führen Sie diese Aktion mindestens einmal aus, um sicherzustellen, dass sich der Projekt-Code im Git-Repository von Cloud Manager befindet.
1. Fügen Sie im Maven-Stammordner einen Verweis zum neuen Ordner hinzu. `pom.xml` im Git-Repository von Cloud Manager.

## GitHub-Beispielaktion {#sample-github-action}

Dies ist eine GitHub-Beispielaktion, die durch einen Push an die Hauptverzweigung ausgelöst wird und dann in ein Unterverzeichnis des Git-Repositorys von Cloud Manager pusht. Die GitHub-Aktionen müssen mit zwei Geheimnissen versehen werden: `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung zum Git-Repository von Cloud Manager herstellen und pushen zu können.

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
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

Die Verwendung einer GitHub-Aktion ist sehr flexibel. Jede Zuordnung zwischen Zweigen der Git-Repositorys sowie jede Zuordnung der einzelnen Git-Projekte zum Verzeichnis-Layout des Hauptprojekts können durchgeführt werden.

>[!NOTE]
>
>Das Beispielskript verwendet `git add` , um das Repository zu aktualisieren. Dabei wird davon ausgegangen, dass Entfernungen enthalten sind. Abhängig von der Standardkonfiguration von Git muss dies möglicherweise durch `git add --all`.

## Jenkins-Beispielauftrag {#sample-jenkins-job}

Dies ist ein Beispielskript, das in einem Jenkins-Auftrag oder ähnlichen Aufgaben verwendet werden kann und den folgenden Ablauf aufweist:

1. Sie wird durch eine Änderung in einem Git-Repository ausgelöst.
1. Der Jenkins-Job überprüft den aktuellen Status dieses Projekts oder Zweigs.
1. Der Auftrag Trigger dann dieses Skript.
1. Dieses Skript checkt wiederum das Git-Repository von Cloud Manager aus und schreibt den Projekt-Code in ein Unterverzeichnis.

Der Jenkins-Job muss mit zwei Geheimnissen ausgestattet werden, `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung zum Git-Repository von Cloud Manager herstellen und pushen zu können.

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

Die Verwendung eines Jenkins-Auftrags ist sehr flexibel. Jede Zuordnung zwischen Zweigen der Git-Repositorys sowie jede Zuordnung der einzelnen Git-Projekte zum Verzeichnis-Layout des Hauptprojekts können durchgeführt werden.

>[!NOTE]
>
>Das Beispielskript verwendet `git add` , um das Repository zu aktualisieren. Dabei wird davon ausgegangen, dass Entfernungen enthalten sind. Abhängig von der Standardkonfiguration von Git muss dies möglicherweise durch `git add --all`.
