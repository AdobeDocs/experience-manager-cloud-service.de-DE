---
title: Arbeiten mit Git-Repositorys aus mehreren Quellen
description: Arbeiten mit Git-Repositorys aus mehreren Quellen – Cloud Services
translation-type: tm+mt
source-git-commit: e8cfe8eeec697fe74da02e178a89fc7a0e22d441
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 100%

---


# Arbeiten mit Git-Repositorys aus mehreren Quellen {#working-with-multiple-source-git-repos}


## Synchronisieren von kundenverwalteten Git-Repositorys {#syncing-customer-managed-git-repositories}

Anstatt direkt mit dem Git-Repository von Cloud Manager zu arbeiten, können Kunden mit ihrem eigenen Git-Repository oder mehreren eigenen Git-Repositorys arbeiten. In diesen Fällen sollte ein automatisierter Synchronisierungsprozess eingerichtet werden, um sicherzustellen, dass das Git-Repository von Cloud Manager stets auf dem neuesten Stand gehalten wird. Je nachdem, wo das Git-Repository des Kunden gehostet wird, kann eine GitHub-Aktion oder Continuous-Integration-Lösung wie Jenkins zum Einrichten der Automatisierung verwendet werden. Bei einer bereits bestehenden Automatisierung kann jeder Push an ein kundeneigenes Git-Repository automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Eine solche Automatisierung für ein einzelnes kundeneigenes Git-Repository kann direkt erfolgen. Bei mehreren Repositorys muss die Automatisierung hingegen entsprechend eingerichtet werden. Die Inhalte aus mehreren Git-Repositorys müssen verschiedenen Ordnern im Git-Repository von Cloud Manager zugeordnet werden.  Das Git-Repository von Cloud Manager muss mit einem Maven-Stamm-POM bereitgestellt werden, in dem die verschiedenen Unterprojekte im Abschnitt mit den Module aufgelistet werden.

Im Folgenden finden Sie ein Beispiel-POM für zwei kundeneigene Git-Repositorys: Das erste Projekt wird in das Verzeichnis `project-a` verschoben, das Verzeichnis `project-b`.

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

Ein solches Stamm-POM wird an eine Verzweigung im Git-Repository von Cloud Manager übergeben. Anschließend müssen die beiden Projekte so eingerichtet sein, dass Änderungen automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Beispielsweise kann eine GitHub-Aktion durch einen Push an eine Verzweigung in Projekt A ausgelöst werden. Die Aktion checkt Projekt A und das Git-Repository von Cloud Manager aus und kopiert alle Inhalte aus Projekt A in das Verzeichnis `project-a` im Git-Repository von Cloud Manager und übernimmt dann die Änderung. Beispielsweise wird eine Änderung an der Hauptverzweigung in Projekt A automatisch an die Hauptverzweigung im Git-Repository von Cloud Manager übergeben. Es könnte auch eine Zuordnung zwischen Verzweigungen geben. Zum Beispiel, wenn ein Push zu einer Verzweigung namens „dev“ in Projekt A zu einer Verzweigung mit der Bezeichnung „development“ im Git-Repository von Cloud Manager verschoben. Ähnliche Schritte sind für Projekt B erforderlich.

Je nach Verzweigungsstrategie und Workflows kann die Synchronisierung für verschiedene Verzweigungen konfiguriert werden. Wenn das verwendete Git-Repository kein Konzept wie GitHub-Aktionen bereitstellt, ist auch eine Integration über Jenkins (oder eine ähnliche Lösung) möglich. In diesem Fall löst ein Webhook einen Jenkins-Auftrag aus, der die Aufgabe ausführt.

Gehen Sie wie folgt vor, um eine neue (dritte) Quelle oder ein neues Repository hinzuzufügen:

1. Fügen Sie eine neue GitHub-Aktion zum neuen Repository hinzu, um Änderungen von diesem Repository in das Git-Repository von Cloud Manager zu übertragen.
1. Führen Sie diese Aktion mindestens einmal aus, um sicherzustellen, dass sich der Projekt-Code im Git-Repository von Cloud Manager befindet.
1. Fügen einen Verweis auf das neue Verzeichnis im Maven-POM im Git-Repository von Cloud Manager hinzu.


## GitHub-Beispielaktion {#sample-github-action}

Hierbei handelt es sich um eine GitHub-Beispielaktion, die durch einen Push an die Hauptverzweigung ausgelöst und dann in ein Unterverzeichnis des Git-Repository von Cloud Manager verschoben wird. Die GitHub-Aktionen müssen mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung herstellen und zum Git-Repository von Cloud Manager übertragen werden zu können.

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

Wie oben gezeigt, ist die Verwendung einer GitHub-Aktion sehr flexibel. Es können jegliche Zuordnungen zwischen Verzweigungen der Git-Repositorys sowie jede Zuordnung der separaten Git-Projekte in das Verzeichnis-Layout des Hauptprojekts erfolgen.

>[!NOTE]
>Das obige Skript verwendet `git add`, um das Repository zu aktualisieren, bei dem davon ausgegangen wird, dass dies Löschvorgänge umfasst. Abhängig von der Standardkonfiguration von Git muss dies durch `git add --all` ersetzt werden.

## Jenkins-Beispielauftrag {#sample-jenkins-job}

Hierbei handelt es sich um ein Beispielskript, das in einem Jenkins-Auftrag oder einem ähnlichem Auftrag verwendet werden kann. Er wird durch eine Änderung in einem Git-Repository ausgelöst. Der Jenkins-Auftrag überprüft den neuesten Status des Projekts oder der Verzweigung und löst dann dieses Skript aus.

Dieses Skript überprüft wiederum das Git-Repository von Cloud Manager und übergibt den Projekt-Code an ein Unterverzeichnis.

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

Wie oben gezeigt, ist die Verwendung eines Jenkins-Auftrags sehr flexibel. Es können jegliche Zuordnungen zwischen Verzweigungen der Git-Repositorys sowie jede Zuordnung der separaten Git-Projekte in das Verzeichnis-Layout des Hauptprojekts erfolgen.

>[!NOTE]
>Das obige Skript verwendet `git add`, um das Repository zu aktualisieren, bei dem davon ausgegangen wird, dass dies Löschvorgänge umfasst. Abhängig von der Standardkonfiguration von Git muss dies durch `git add --all` ersetzt werden.