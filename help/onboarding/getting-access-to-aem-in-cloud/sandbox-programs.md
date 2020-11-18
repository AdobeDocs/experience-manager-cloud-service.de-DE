---
title: Sandbox-Programme - Cloud Service
description: Sandbox-Programme - Cloud Service
translation-type: tm+mt
source-git-commit: 8383dc023b35cf76f7dc0e41cedef8cfab7753aa
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 0%

---


# Sandbox-Programme {#sandbox-programs}

## Einführung {#introduction}

Ein Sandbox-Programm ist eines der beiden Programm, die in AEM Cloud Service verfügbar sind, das andere ein reguläres Programm.

Eine Sandbox wird normalerweise für Schulungen, laufende Demos, die Aktivierung oder den Testversand von Concept (POC) erstellt. Sie sind nicht dazu gedacht, Live-Verkehr zu transportieren. Sie unterliegen nicht den [AEM als Cloud Service-Verpflichtungen](https://www.adobe.com/legal/service-commitments.html).

Die in einer Sandbox erstellten Umgebung sind nicht für die automatische Skalierung konfiguriert. Daher sind sie nicht für Leistungs- oder Belastungsprüfungen geeignet.

Sandbox-Programm umfassen Sites und Assets und werden automatisch mit einem Git-Repository, einer Development-Umgebung und einer Nicht-Produktions-Pipeline gefüllt.  Das Git-Repository wird mit einem Beispielprojekt basierend auf dem AEM Project-Archetyp gefüllt.

Weitere Informationen zu den Programm-Typen finden Sie unter [Einführung zu Programmen und Programmen](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md) .

### Attribute von Sandbox-Programmen {#attributes-sandbox}

Sandbox-Programm haben die folgenden Attribute:

1. **Programm-Erstellung:** Die Erstellung des Sandbox-Programms erfolgt automatisch:
   * Einrichtung des Projekts mit Beispielcode und Inhalt
   * Schaffung einer Umgebung für die Entwicklung
   * Erstellung von Nicht-Produktionslinien-Pipeline, die zur Umgebung der Entwicklung bereitgestellt werden (Übergeordnet-Filiale, die zur Umgebung der Entwicklung verwendet werden)

1. **Lösungen:** Sandbox-Programme sind AEM Sites und Assets.

1. **AEM Updates:** AEM Updates können manuell auf Umgebung in einem Sandbox-Programm angewendet werden und werden nicht automatisch gesendet.

1. **Hibernation:** Umgebung in einem Sandbox-Programm werden automatisch ausgeblendet, wenn für einen bestimmten Zeitraum keine Aktivität erkannt wird. Hibernated-Umgebung können manuell entfernt werden.

### Erstellen eines Sandbox-Programms {#creating-sandbox-program}

Mit einem Assistenten zum Erstellen von Programmen können Sie ein Sandbox-Programm erstellen.

Weitere Informationen zum Erstellen eines Sandbox-Programms finden Sie unter [Erstellen eines Sandbox-Programms](/help/onboarding/getting-access-to-aem-in-cloud/creating-a-program.md#create-sandbox-program) .

### Erstellen von Sandbox-Umgebung {#creating-sandbox-environments}

Sandbox-Programm werden zum Zeitpunkt der Erstellung des Programms automatisch an eine Development-Umgebung gesendet. Die Development-Umgebung umfasst standardmäßig einen Autor und eine Veröffentlichungsstufe.

Der Produktions-Stage-Umgebung-Satz kann manuell dem Sandbox-Programm hinzugefügt werden, wenn der Anwender bereit ist, eine Produktionspipeline einzurichten.

Weitere Informationen zum manuellen Erstellen einer Umgebung finden Sie unter [Hinzufügen einer Umgebung](/help/implementing/cloud-manager/manage-environments.md) .

### Löschen von Sandbox-Umgebung {#deleting-sandbox-environments}

Benutzer mit den erforderlichen Berechtigungen können eine Entwicklungs- oder Produktions-/Stage-Umgebung oder -Sets löschen.

Weitere Informationen zum Löschen einer Umgebung finden Sie unter [Löschen der Umgebung](/help/implementing/cloud-manager/manage-environments.md#deleting-environment) .


## Hibernating- und EntHibernating-Sandbox-Umgebung {#hibernating-introduction}

Sandbox-Programm-Umgebung werden in den *Ruhezustand* versetzt, wenn für einen bestimmten Zeitraum keine Aktivität erkannt wird.

>[!NOTE]
>Hibernation ist einzigartig in Sandbox-Programm-Umgebung. Regelmäßige Umgebung des Programms führen nicht zu Hibernationen.

### Hibernation {#hibernation-introduction}

Eine Ruhezeit kann entweder automatisch oder manuell erfolgen. Es kann einige Minuten dauern, bis Sandbox-Programm-Umgebung in den *Ruhezustand* wechseln. Daten werden während der Winterzeit beibehalten.

Die Hibernation wird wie folgt kategorisiert:

* **Automatische** Sandbox-Programm-Umgebung werden nach acht Stunden Inaktivität automatisch ausgeblendet, d. h., weder der Autor noch der Veröffentlichungsdienst erhalten Anfragen.

* **Manuell**: Als Benutzer können Sie eine Sandbox-Programm-Umgebung manuell löschen, dies ist jedoch nicht erforderlich, da eine Ruhezeit nach einer bestimmten Inaktivität (acht Stunden) automatisch eintritt.

>[!CAUTION]
>In der neuesten Version haben Sie bei Verknüpfungen mit der Developer Console direkt aus Cloud Manager keine Möglichkeit, eine Sandbox-Programm-Umgebung zu löschen. Die Problemumgehung erfolgt einmal in der Developer Console. Fügen Sie am Ende der URL `#release-cm-p1234-e5678 where 1234` 1234 das folgende Muster hinzu: Ihre *Programm-ID* und 5678 Ihre *Umgebung-ID*.

#### Manuelle Bereinigung {#using-manual-hibernation}

Sie können Ihr Sandbox-Programm in der Developer Console auf zwei verschiedene Arten manuell löschen:

* Detailbildschirm der Umgebung
* Bildschirm zur Umgebung

>[!NOTE]
>Der Zugriff auf die Developer Console für ein Sandbox-Programm steht allen Benutzern von Cloud Manager zur Verfügung.

Gehen Sie wie folgt vor, um Ihre Sandbox-Programm-Umgebung manuell zu berühren:

1. Navigieren Sie zur **Developer Console**.
Informationen zum Zugriff auf die [Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) über die Karte für **Umgebung** finden Sie unter Zugriff auf die Developer Console **** .
   >[!IMPORTANT]
   >Wenn Sie eine **Developer Console** direkt über Cloud Manager verknüpfen, haben Sie keine Möglichkeit, eine Sandbox-Programm-Umgebung zu löschen. Die Problemumgehung erfolgt einmal in der Developer Console. Fügen Sie am Ende der URL `#release-cm-p1234-e5678 where 1234` 1234 das folgende Muster hinzu: Ihre *Programm-ID* und 5678 Ihre *Umgebung-ID*.

1. Click **Hibernate**, as shown in the figure below:

   ![](assets/hibernate-1.png)

   Oder

   Klicken Sie auf den Link **Umgebung** oben links, um die Liste der Umgebung Ansicht, und klicken Sie dann auf **Hibernate**, wie in der folgenden Abbildung gezeigt:

   ![](assets/hibernate-1b.png)

1. Klicken Sie auf **Hibernate** , um den Schritt zu bestätigen.

   ![](assets/hibernate-2.png)

1. Nach erfolgreichem Beenden des Ruhezustands wird im Bildschirm &quot; **Developer Console** &quot;die Benachrichtigung zum Abschluss des Ruhezustands für Ihre Umgebung angezeigt.

   ![](assets/hibernate-4.png)


### Enthibernation {#de-hibernation-introduction}

1. Navigieren Sie zur **Developer Console**.
Informationen zum Zugriff auf die [Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) über die Karte für **Umgebung** finden Sie unter Zugriff auf die Developer Console **** .

   >[!IMPORTANT]
   >Wenn Sie eine **Developer Console** direkt über Cloud Manager verknüpfen, haben Sie nicht die Möglichkeit, eine Sandbox-Programm-Umgebung zu deaktivieren. Die Problemumgehung erfolgt einmal in der Developer Console. Fügen Sie am Ende der URL `#release-cm-p1234-e5678 where 1234` 1234 das folgende Muster hinzu: Ihre *Programm-ID* und 5678 Ihre *Umgebung-ID*.

   >[!NOTE]
   >Alternativ können Sie zur **Developer Console** navigieren, um die Bereinigung zu deaktivieren, indem Sie versuchen, auf den Autor- oder Veröffentlichungsdienst einer bereits ausgeblendeten Umgebung zuzugreifen. In diesem Fall wird eine Landingpage mit einem Link zur Developer Console angezeigt. Weitere Informationen finden Sie im Abschnitt Zugriff auf eine ausgeblendete Umgebung.

   >[!IMPORTANT]
   >Der Zugriff auf die Developer Console wird durch die **Cloud Manager - Entwicklerrolle** in der **Admin Console** definiert. Ein Benutzer mit der Berechtigung für die Rolle &quot;Entwickler&quot;kann eine Sandbox-Programm-Umgebung deaktivieren.

1. Click on **De-hibernate**, as shown in the figure below:

   ![](assets/de-hibernation-img1.png)

   Oder

   Klicken Sie auf den Link **Umgebung** oben links, um die Liste der Umgebung Ansicht, und klicken Sie dann auf **Löschen**, wie in der Abbildung unten dargestellt

   ![](assets/de-hibernate-1b.png)


1. Klicken Sie auf **De Hibernate** , um den Schritt zu bestätigen.

   ![](assets/de-hibernation-img2.png)

1. Sie erhalten die Benachrichtigung, dass der Bereinigungsprozess begonnen hat, und Sie werden über den Fortschritt informiert.

   ![](assets/de-hibernation-img3.png)

1. Nach Abschluss des Vorgangs ist die Sandbox-Programm-Umgebung erneut aktiv.

   ![](assets/de-hibernation-img4.png)

#### Berechtigungen zum Deaktivieren von Bereinigungen {#permissions-de-hibernate}

Jeder Benutzer mit einem Profil, das ihm Zugriff auf AEM als Cloud Service gewährt, sollte auf die **Entwicklerkonsole** zugreifen können, sodass er die Umgebung dehibernieren kann.

#### Zugriff auf eine ausgeblendete Umgebung {#accessing-hibernated-environment}

Bei Browseranfragen zum Autoren- oder Veröffentlichungsstatus einer überzähligen Umgebung wird dem Benutzer eine Landingpage angezeigt, die den Status der Umgebung beschreibt, wie in der folgenden Abbildung dargestellt:

![](assets/de-hibernation-img5.png)

### Wichtige Überlegungen {#important-considerations}

Bei Umgebung mit Hibernationen und enthibernierten  sind nur wenige wichtige Aspekte:

* Ein Benutzer kann eine Pipeline verwenden, um benutzerdefinierten Code für ausgeblendete Umgebung bereitzustellen. Die Umgebung bleibt erhalten, und der neue Code wird in der Umgebung angezeigt, sobald er entfernt wurde.

* AEM Upgrades können auf ausgeblendete Umgebung angewendet werden, die Kunden manuell aus Cloud Manager auslösen können. Die Umgebung bleibt erhalten, und die neue Version erscheint in der Umgebung, sobald sie entfernt wurde.

>[!NOTE]
>Derzeit gibt Cloud Manager nicht an, ob eine Umgebung ausgeblendet ist.

## AEM Updates für Sandbox-Umgebung {#aem-updates-sandbox}

Refer to [AEM version updates](/help/implementing/deploying/aem-version-updates.md) for more details.

Ein Benutzer kann AEM Aktualisierungen manuell auf die Umgebung in einem Sandbox-Programm anwenden.

Informationen zum Aktualisieren einer Umgebung finden Sie unter [Aktualisieren der Umgebung](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) .

>[!NOTE]
>* Eine manuelle Aktualisierung kann nur ausgeführt werden, wenn die zielgerichtete Umgebung über eine ordnungsgemäß konfigurierte Pipeline verfügt.
>* Eine manuelle Aktualisierung auf *Produktions* - oder *Stage* -Umgebung wird automatisch aktualisiert. Der Produktions- und Stage-Umgebung-Satz muss sich auf derselben AEM befinden.






