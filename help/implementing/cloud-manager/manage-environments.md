---
title: Verwalten von Umgebungen - Cloud-Dienst
description: Verwalten von Umgebungen - Cloud-Dienst
translation-type: tm+mt
source-git-commit: 81f993325b80c0de17d6032a45ebd61c22169d39

---


# Verwalten von Umgebungen {#manage-environments}

Im folgenden Abschnitt werden die Umgebungstypen beschrieben, die ein Benutzer erstellen kann, und die Möglichkeiten zum Erstellen einer Umgebung durch den Benutzer beschrieben.

## Umgebungstypen {#environment-types}

Ein Benutzer mit den erforderlichen Berechtigungen kann die folgenden Umgebungstypen erstellen (innerhalb der Grenzen dessen, was dem jeweiligen Mandanten zur Verfügung steht).

* **Produktions- und Stage-Umgebung**:
Die Produktions- und Produktionsstufe ist als Duo verfügbar und wird für Test- und Produktionszwecke verwendet.

* **Entwicklung**: Eine Entwicklungsumgebung kann zu Entwicklungs- und Testzwecken geschaffen werden und wird nur mit Nicht-Produktionsleitungen in Verbindung gebracht.

   >[!NOTE]
   >Eine Entwicklungsumgebung, die automatisch in einem Sandbox-Programm erstellt wird, wird so konfiguriert, dass sie Sites und Assets-Lösungen enthält.

   In der folgenden Tabelle sind die Umgebungstypen und ihre Attribute zusammengefasst:

   | Name | Autorenebene | Veröffentlichungsstufe | Benutzer kann | Benutzer kann | Pipeline, die mit der Umgebung verknüpft werden kann |
   |--- |--- |--- |--- |---|---|
   | Produktion | Ja | Ja, wenn Sites enthalten sind | Ja | Nein | Produktionsleitung |
   | Bühne | Ja | Ja, wenn Sites enthalten sind | Ja | Nein | Produktionsleitung |
   | Entwicklung | Ja | Ja, wenn Sites enthalten sind | Ja | Ja | Produktionsfremde Pipeline |

   >[!NOTE]
   >
Die Produktions- und Produktionsstufe ist als Duo verfügbar und wird für Test- und Produktionszwecke verwendet.  Benutzer können nicht nur eine Stage- oder Produktionsumgebung erstellen.

## Hinzufügen einer Umgebung {#adding-environments}


1. Der Benutzer klickt auf die Schaltfläche Umgebung **hinzufügen** , um eine Umgebung hinzuzufügen.

   ![](assets/add-environment.png)

1. Das Dialogfeld &quot;Umgebung **** hinzufügen&quot;wird angezeigt. Der Benutzer muss Details wie **Umgebungstyp** , **Umgebungsname** und **Umgebungsbeschreibung** übermitteln (je nach dem Ziel des Benutzers, die Umgebung innerhalb der Grenzen des für den jeweiligen Mandanten verfügbaren Bereichs zu erstellen).

   ![](assets/add-environment2.png)

   >[!NOTE]
   >Beim Erstellen einer Umgebung werden eine oder mehrere *Integrationen* in Adobe I/O erstellt. Diese sind für Kunden sichtbar, die Zugriff auf die Adobe-E/A-Konsole haben, und dürfen nicht gelöscht werden. Dies wird in der Beschreibung in der Adobe-E/A-Konsole nicht berücksichtigt.

   ![](assets/add-environment-image1.png)

1. Klicken Sie auf **Speichern** , um eine Umgebung mit den ausgefüllten Kriterien hinzuzufügen.  Jetzt wird im Bildschirm &quot; *Übersicht* &quot;die Karte angezeigt, von der aus Sie Ihre Pipeline einrichten können.

   >[!NOTE]
   >Falls Sie noch keine Pipeline für die Nicht-Produktion eingerichtet haben, wird im Bildschirm &quot; *Übersicht* &quot;die Karte angezeigt, von der aus Sie Ihre Nicht-Produktionspipeline erstellen können.


## Umgebung aktualisieren {#updating-dev-environment}

Updates der Stage- und Produktionsumgebungen werden automatisch von Adobe verwaltet.

Updates für Entwicklungsumgebungen werden von den Benutzern des Programms verwaltet. Wenn in einer Umgebung nicht die neueste öffentlich verfügbare AEM-Version ausgeführt wird, zeigt der Status auf der Umgebungskarte auf dem Startbildschirm die **AKTUALISIERUNG** an.

![](assets/manage-environments2.png)
)

Wenn dieser Status angezeigt wird, ist die Option **Aktualisieren** im Dropdown-Menü sowohl auf der Umgebungskarte als auch im Menü **Verwalten** verfügbar, wenn Sie auf **Details** aus der Karte **UMWELT** klicken.

![](assets/add-environment4.png)

Durch Auswahl dieser Option aus dem Dropdown-Menü kann ein Deployment Manager die mit dieser Umgebung verknüpfte Pipeline auf die neueste Version aktualisieren und dann die Pipeline ausführen.

Wenn die Pipeline bereits aktualisiert wurde, wird der Benutzer aufgefordert, die Pipeline auszuführen.
