---
title: Prinzipalansicht für die Berechtigungsverwaltung
description: Erfahren Sie mehr über die neue Touch-Benutzeroberfläche, die die Berechtigungsverwaltung erleichtert.
feature: Security
role: Admin
source-git-commit: 66ec051a2412fdbfb18dec5b79c6d5d5ca496216
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 66%

---


# Prinzipalansicht für die Berechtigungsverwaltung {#principal-view-for-permissions-management}

## Übersicht {#overview}

AEM führt die Berechtigungsverwaltung für Benutzende und Gruppen ein. Die Hauptfunktionalität bleibt mit der klassischen Benutzeroberfläche identisch, ist jedoch benutzerfreundlicher und effizienter.

## Zugriff auf die Benutzeroberfläche {#accessing-the-ui}

Die Berechtigungsverwaltung, die auf der neuen Benutzeroberfläche basiert, wird wie unten dargestellt unter „Sicherheit“ auf der Karte für Berechtigungen aufgerufen:

![Benutzeroberfläche für die Berechtigungsverwaltung](assets/screen_shot_2019-03-17at63333pm.png)

Die neue Ansicht erleichtert die Anzeige aller Berechtigungen und Einschränkungen für einen bestimmten Prinzipal auf allen Pfaden, auf denen Berechtigungen explizit gewährt wurden. Dadurch entfällt die Notwendigkeit,

CRXDE zum Verwalten erweiterter Berechtigungen und Einschränkungen zu verwenden. Er wurde in derselben Ansicht konsolidiert.

![Berechtigungsansicht](assets/permissionView.png)

Es gibt einen Filter, mit dem die Art der Prinzipale ausgewählt werden kann, um **Benutzende**, **Gruppen** oder **Alle** anzuzeigen und nach jedem Prinzipal zu suchen **.**

![Suche nach Prinzipaltypen](assets/image2019-3-20_23-52-51.png)

## Anzeigen von Berechtigungen für einen Prinzipal {#viewing-permissions-for-a-principal}

Im linken Rahmen können Benutzende nach unten scrollen, um einen Prinzipal zu finden oder basierend auf dem ausgewählten Filter nach einer Gruppe oder einer Einzelperson zu suchen:

![Berechtigungen für einen Prinzipal anzeigen](assets/doi-1.png)

Wenn Sie auf den Namen klicken, werden die zugewiesenen Berechtigungen auf der rechten Seite angezeigt. Der Berechtigungsbereich zeigt die Liste der Zugriffssteuerungseinträge für bestimmte Pfade sowie konfigurierte Einschränkungen an.

![ACL-Liste anzeigen](assets/permissionsList.png)

## Hinzufügen eines neuen Zugriffssteuerungseintrags (Access Control Entry, ACE) für einen Prinzipal {#adding-new-access-control-entry-for-a-principal}

Neue Berechtigungen können durch Hinzufügen eines Zugriffssteuerungseintrags hinzugefügt werden. Klicken Sie einfach auf die Schaltfläche zum Hinzufügen eines Zugriffssteuerungseintrags.

![Neue ACL für einen Prinzipal hinzufügen](assets/patru.png)

Dadurch wird das unten dargestellte Fenster angezeigt. Der nächste Schritt besteht in der Auswahl eines Pfades, in dem die Berechtigung konfiguriert werden muss.

![Berechtigungspfad konfigurieren](assets/cinci-1.png)

Hier wird ein Pfad ausgewählt, in dem Sie eine Berechtigung für **dam-users** konfigurieren können:

![Beispielkonfiguration für dam-users](assets/sase-1.png)

Nachdem der Pfad ausgewählt wurde, wechselt der Workflow zurück zu diesem Bildschirm, wobei der Benutzer dann eine oder mehrere Berechtigungen aus den verfügbaren Namespaces (z. B. `jcr`, `rep` oder `crx`) auswählen kann, wie weiter unten dargestellt.

Berechtigungen können hinzugefügt werden, indem Sie mithilfe des Textfelds suchen und dann aus der Liste auswählen.

>[!NOTE]
>
>Eine vollständige Liste der Berechtigungen und Beschreibungen finden Sie unter [Verwaltung von Benutzenden, Gruppen und Zugriffsrechten](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/security/user-group-ac-admin#access-right-management).

![Suchberechtigung für einen bestimmten Pfad.](assets/image2019-3-21_0-5-47.png) ![Fügen Sie neuen Eintrag für „dam-users“ hinzu, wie durch einen in vertikalen Spalten ausgewählten Pfad gezeigt.](assets/image2019-3-21_0-6-53.png)

Nachdem die Liste der Berechtigungen ausgewählt wurde, lässt sich der Berechtigungstyp auswählen: „Ablehnen“ oder „Zulassen“, wie unten dargestellt.

![Berechtigung auswählen](assets/screen_shot_2019-03-17at63938pm.png) ![Berechtigung auswählen](assets/screen_shot_2019-03-17at63947pm.png)

## Verwenden von Einschränkungen {#using-restrictions}

Zusätzlich zur Liste der Berechtigungen und dem Berechtigungstyp für einen bestimmten Pfad können auf diesem Bildschirm auch Einschränkungen für fein abgestufte Zugriffssteuerungsmöglichkeiten hinzugefügt werden:

![Einschränkungen hinzufügen](assets/image2019-3-21_1-4-14.png)

>[!NOTE]
>
>Weitere Informationen zu den einzelnen Beschränkungen finden Sie in der [Jackrabbit Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html).

Einschränkungen können wie unten dargestellt hinzugefügt werden, indem Sie den Einschränkungstyp auswählen, den Wert eingeben und auf das **+**-Symbol klicken.

![Einschränkungstyp hinzufügen](assets/sapte-1.png) ![Einschränkungstyp hinzufügen](assets/opt-1.png)

Der neue ACE wird in der Zugriffssteuerungsliste wie unten dargestellt angezeigt. Beachten Sie, dass `jcr:write` eine aggregierte Berechtigung ist, die `jcr:removeNode` enthält. Diese Berechtigung wurde oben hinzugefügt, wird aber unten nicht angezeigt, da sie unter `jcr:write` aufgeführt wird.

## Bearbeiten von ACEs {#editing-aces}

Zugriffssteuerungseinträge können bearbeitet werden, indem Sie einen Prinzipal auswählen und dann den zu bearbeitenden ACE.

Hier können Sie beispielsweise den unten stehenden Eintrag für **dam-users** bearbeiten, indem Sie auf das Stiftsymbol rechts klicken:

![Einschränkung hinzufügen](assets/image2019-3-21_0-35-39.png)

Der Bearbeitungsbildschirm wird mit vorausgewählten konfigurierten ACEs-Voreinstellungen angezeigt. Diese können gelöscht werden, indem Sie auf das Kreuzsymbol neben ihnen klicken. Sie können auch neue Berechtigungen für den angegebenen Pfad hinzufügen, wie unten dargestellt.

![Eintrag bearbeiten](assets/noua-1.png)

Hier wird die Berechtigung `addChildNodes` für **dam-users** auf dem bestimmten Pfad hinzugefügt.

![Berechtigung hinzufügen](assets/image2019-3-21_0-45-35.png)

Änderungen können gespeichert werden, indem Sie oben rechts auf die Schaltfläche **Speichern** klicken. Die geänderten Berechtigungen für **dam-users** werden wie unten dargestellt übernommen:

![Speichern Sie die Änderungen](assets/zece-1.png)

## Löschen von ACEs {#deleting-aces}

Zugriffssteuerungseinträge können gelöscht werden, um alle Berechtigungen zu entfernen, die einem Prinzipal für einen bestimmten Pfad erteilt wurden. Das X-Symbol neben dem ACE kann wie unten gezeigt zum Löschen verwendet werden:

![Löschen von ACEs](assets/image2019-3-21_0-53-19.png) ![Löschen von ACEs](assets/unspe.png)

## Berechtigungsansicht {#permissions-view}

### Berechtigungsansicht für Touch-optimierte Benutzeroberfläche {#touch-ui-permisions-view}

Admins benötigen eine granularere Kontrolle und Einsicht in die Berechtigungszuweisungen auf Knotenebene, um die Sicherheit und Verwaltung in AEM zu verbessern. Zuvor war nur eine prinzipalbasierte Ansicht der Berechtigungen verfügbar, wodurch die Möglichkeit eingeschränkt wurde zu sehen, wie ACLs auf bestimmte Knoten oder gefilterte Ansichten angewendet werden. Der neue Knoten und die gefilterte Ansicht bieten eine detaillierte und kontextualisierte Perspektive auf Berechtigungszuweisungen, die eine bessere Verwaltung und Prüfung von Sicherheitskonfigurationen ermöglicht. Diese Funktion verbessert die administrative Aufsicht und vereinfacht die Berechtigungsverwaltung, verbessert die Sicherheit, reduziert Fehlkonfigurationen und optimiert die Benutzerzugriffssteuerung in AEM.


Sie können auf die Ansicht der Touch-optimierten Benutzeroberfläche für Berechtigungen zugreifen, indem Sie auf **Tools - Sicherheit - Berechtigungen** klicken, wie unten dargestellt:

![Karte für die Touch-optimierte Benutzeroberfläche](assets/image-2025-2-5_15-37-59.png)

Sobald Sie die Berechtigungsansicht gestartet haben, können Sie je nach Ihren bevorzugten Anzeigeoptionen in **&#x200B;**&#x200B;oberen rechten Ecke **Knotenansicht“ oder** Gefilterte Ansicht“ klicken.

#### Knotenansicht

In dieser Ansicht werden ACLs für jeden einzelnen Knoten (Pfad) angezeigt. Es enthält Informationen zu folgenden Themen:

Lokale ACLs für den ausgewählten Knoten.
Effektive ACLs, einschließlich ACLs, die auf jeden übergeordneten Knoten bis zum Stamm (/) angewendet werden.
Benutzende haben die Möglichkeit, ACLs hinzuzufügen, zu entfernen oder zu aktualisieren. Wenn auf einen Pfad geklickt wird, werden im linken Bereich die untergeordneten Elemente angezeigt, während auf der rechten Seite eine Tabellenansicht aller mit diesem Pfad verknüpften ACLs angezeigt wird.

![Knotenansicht](assets/image-2025-2-5_15-26-2.png)

#### Gefilterte Ansicht

In dieser Ansicht können Benutzer effizient nach Berechtigungen für einen angegebenen Pfad und Prinzipale suchen. In dieser Ansicht können Benutzende den Typ der Berechtigungen, die einer Gruppe von Prinzipalen für den ausgewählten Pfad gewährt werden, einfach bestimmen.
Darüber hinaus bietet die gefilterte Ansicht Einblicke in effektive ACLs. Es werden die mit dem übergeordneten Knoten des ausgewählten Pfads verknüpften ACLs angezeigt, wobei der ausgewählte Prinzipal und alle allgemeinen Prinzipale berücksichtigt werden.

![Filteransicht](assets/FilteredView.png)

### Die Repository-Browser-Berechtigungsansicht {#the-repository-browser-permissions-view}

Der Zugriff auf die Berechtigungsansicht ist auch über den [Repository-Browser](/help/implementing/developing/tools/repository-browser.md) möglich.

Sie können wie folgt darauf zugreifen:

1. Öffnen Sie die Entwicklerkonsole, klicken Sie auf die Registerkarte **Repository-**) und dann auf **Repository-Browser öffnen**

   ![Starten des Repository-Browsers](assets/image-2025-2-5_15-38-47.png)

1. Klicken Sie im Repository-Browser auf die Registerkarte **Berechtigungen** .

   ![Registerkarte „Berechtigungen“](assets/image-2025-2-5_15-29-33.png)

**Hinweis**: Zum Anzeigen der Berechtigungen sind Administratorrechte erforderlich. Führen Sie die hier [ Schritte aus](/help/implementing/developing/tools/repository-browser.md#navigate-the-hierarchy-navigate-the-hierarchy) um auf die Berechtigungen zuzugreifen.

## Berechtigungskombinationen in der klassischen Benutzeroberfläche {#classic-ui-privilege-combinations}

In der neuen Benutzeroberfläche für Berechtigungen wird explizit der grundlegende Satz von Berechtigungen, anstelle vordefinierter Kombinationen verwendet, die nicht immer exakt die gewährten Berechtigungen wiedergegeben.

Das führte in der Vergangenheit zu Unklarheit, was genau konfiguriert wird. In der folgenden Tabelle finden Sie die Zuordnung zwischen den Berechtigungskombinationen aus der klassischen Benutzeroberfläche und den tatsächlichen Berechtigungen, aus denen sie bestehen:

<table>
 <tbody>
  <tr>
   <th>Berechtigungskombinationen in der klassischen Benutzeroberfläche</th>
   <th>Berechtigungen der Berechtigungs-Benutzeroberfläche</th>
  </tr>
  <tr>
   <td>Lesen</td>
   <td><code>jcr:read</code></td>
  </tr>
  <tr>
   <td>Ändern</td>
   <td><p><code>jcr:modifyProperties</code></p> <p><code>jcr:lockManagement</code></p> <p><code>jcr:versionManagement</code></p> </td>
  </tr>
  <tr>
   <td>Erstellen</td>
   <td><p><code>jcr:addChildNodes</code></p> <p><code>jcr:nodeTypeManagement</code></p> </td>
  </tr>
  <tr>
   <td>Löschen</td>
   <td><p><code>jcr:removeNode</code></p> <p><code>jcr:removeChildNodes</code></p> </td>
  </tr>
  <tr>
   <td>ACL lesen</td>
   <td><code>jcr:readAccessControl</code></td>
  </tr>
  <tr>
   <td>ACL bearbeiten</td>
   <td><code>jcr:modifyAccessControl</code></td>
  </tr>
  <tr>
   <td>Replizieren</td>
   <td><code>crx:replicate</code></td>
  </tr>
 </tbody>
</table>
