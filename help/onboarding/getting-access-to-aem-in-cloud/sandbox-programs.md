---
title: Sandbox-Programme – Cloud Service
description: Sandbox-Programme – Cloud Service
translation-type: tm+mt
source-git-commit: 8383dc023b35cf76f7dc0e41cedef8cfab7753aa
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 100%

---


# Sandbox-Programme {#sandbox-programs}

## Einführung {#introduction}

Ein Sandbox-Programm ist eines von zwei Programmtypen, die in AEM Cloud Service verfügbar sind; das andere ist ein Standardprogramm.

Sandboxes werden normalerweise für Schulungen, laufende Demos, Aktivierungen oder Proof of Concepts (POCs) erstellt. Sie sind nicht dazu gedacht, Live-Traffic zu übertragen. Sie unterliegen nicht den [AEM as a Cloud Service-Verpflichtungen](https://www.adobe.com/legal/service-commitments.html).

Die in einer Sandbox erstellten Umgebungen sind nicht für automatische Skalierung konfiguriert. Daher sind sie nicht für Leistungs- oder Belastungstests geeignet.

Sandbox-Programme umfassen Sites und Assets und werden automatisch mit einem Git-Repository, einer Entwicklungsumgebung und einer Nicht-Produktions-Pipeline gefüllt.  Das Git-Repository wird basierend auf dem AEM-Projektarchetyp mit einem Beispielprojekt gefüllt.

Weitere Informationen zu den Programmtypen finden Sie unter [Einführung zu Programmen und Programmtypen](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md).

### Attribute von Sandbox-Programmen {#attributes-sandbox}

Sandbox-Programme haben die folgenden Attribute:

1. **Programmerstellung:** Die Erstellung von Sandbox-Programmen umfasst die automatische:
   * Einrichtung eines Projekts mit Beispiel-Code und -Inhalt
   * Schaffung einer Entwicklungsumgebung
   * Erstellung einer Nicht-Produktions-Pipeline, die in der Entwicklungsumgebung bereitgestellt wird (übergeordnete Verzweigung, die in der Entwicklungsumgebung bereitgestellt wird)

1. **Lösungen:** Sandbox-Programme beinhalten AEM Sites und Assets.

1. **AEM-Updates:** AEM-Updates können in Sandbox-Programmen manuell auf Umgebungen angewendet werden und werden nicht automatisch gesendet.

1. **Ruhezustand:** Umgebungen in einem Sandbox-Programm werden automatisch in den Ruhezustand versetzt, wenn in einem bestimmten Zeitraum keine Aktivität erkannt wurde. In den Ruhezustand versetzte Umgebungen können manuell wieder aktiviert werden.

### Erstellen eines Sandbox-Programms {#creating-sandbox-program}

Mit einem Assistenten zum Erstellen von Programmen können Sie ein Sandbox-Programm erstellen.

Weitere Informationen zum Erstellen eines Sandbox-Programms finden Sie unter [Erstellen eines Sandbox-Programms](/help/onboarding/getting-access-to-aem-in-cloud/creating-a-program.md#create-sandbox-program).

### Erstellen von Sandbox-Umgebungen {#creating-sandbox-environments}

Sandbox-Programme werden beim Erstellen des Programms automatisch an eine Entwicklungsumgebung gesendet. Die Entwicklungsumgebung umfasst standardmäßig eine Erstellungs- und eine Veröffentlichungsstufe.

Der Satz aus Produktions- und Staging-Umgebung kann dem Sandbox-Programm manuell hinzugefügt werden, sobald der Anwender bereit ist, eine Produktions-Pipeline einzurichten.

Weitere Informationen zum manuellen Erstellen einer Umgebung finden Sie unter [Hinzufügen von Umgebungen](/help/implementing/cloud-manager/manage-environments.md).

### Löschen von Sandbox-Umgebungen {#deleting-sandbox-environments}

Anwender mit den erforderlichen Berechtigungen können eine Entwicklungs- oder Produktions-/Staging-Umgebung bzw. entsprechende Sätze löschen.

Weitere Informationen zum Löschen einer Umgebung finden Sie unter [Löschen von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#deleting-environment).


## Ruhezustand und Reaktivieren von Sandbox-Umgebungen {#hibernating-introduction}

Sandbox-Programmumgebungen werden in den *Ruhezustand* versetzt, wenn in einem bestimmten Zeitraum keine Aktivität erkannt wurde.

>[!NOTE]
>Ruhezustand gibt es nur bei Sandbox-Programmumgebungen. Bei regulären Programmumgebungen gibt es keinen Ruhezustand.

### Ruhezustand {#hibernation-introduction}

Der Ruhezustand kann entweder automatisch oder manuell aktiviert werden. Es kann einige Minuten dauern, bis Sandbox-Programmumgebungen in den *Ruhezustand* wechseln. Daten werden im Ruhezustand beibehalten.

Der Ruhezustand wird wie folgt kategorisiert:

* **Automatisch:** Sandbox-Programmumgebungen werden nach acht Stunden Inaktivität automatisch in den Ruhezustand versetzt, d. h. weder der Erstellungs- noch der Veröffentlichungs-Service erhalten Anfragen.

* **Manuell**: Als Anwender können Sie eine Sandbox-Programmumgebung manuell löschen; dies ist jedoch nicht erforderlich, da nach einer bestimmten Inaktivitätsdauer (acht Stunden) automatisch der Ruhezustand eintritt.

>[!CAUTION]
>In der neuesten Version haben Sie bei Verknüpfung mit der Developer Console direkt aus Cloud Manager keine Option, um eine Sandbox-Programmumgebung in den Ruhezustand zu versetzen. Fügen Sie zur Problemumgehung in der Developer Console das folgende Muster am Ende der URL `#release-cm-p1234-e5678 where 1234` hinzu: 1234 ist Ihre *Programm-ID* und 5678 Ihre *Umgebungs-ID*.

#### Verwenden des manuellen Ruhezustands {#using-manual-hibernation}

Sie können Ihr Sandbox-Programm in der Developer Console auf zwei Arten manuell in den Ruhezustand versetzen:

* Bildschirm mit Umgebungsdetails
* Bildschirm mit Umgebungsliste

>[!NOTE]
>Der Zugriff auf die Developer Console für ein Sandbox-Programm steht allen Anwendern von Cloud Manager zur Verfügung.

Gehen Sie wie folgt vor, um Ihre Sandbox-Programmumgebungen manuell in den Ruhezustand zu versetzen:

1. Navigieren Sie zur **Developer Console**.
Unter [Zugreifen auf die Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) finden Sie Informationen zum Zugriff auf die **Developer Console** (über die Karte **Umgebungen**).
   >[!IMPORTANT]
   >Wenn Sie die **Developer Console** direkt über Cloud Manager verknüpfen, erhalten Sie keine Option, um eine Sandbox-Programmumgebung in den Ruhezustand zu versetzen. Fügen Sie zur Problemumgehung in der Developer Console das folgende Muster am Ende der URL `#release-cm-p1234-e5678 where 1234` hinzu: 1234 ist Ihre *Programm-ID* und 5678 Ihre *Umgebungs-ID*.

1. Klicken Sie auf **Ruhezustand**, wie in der Abbildung unten gezeigt:

   ![](assets/hibernate-1.png)

   Oder

   Klicken Sie auf den Link **Umgebungen** links oben, um die Liste der Umgebungen anzuzeigen, und klicken Sie dann auf **Ruhezustand**, wie in der folgenden Abbildung gezeigt:

   ![](assets/hibernate-1b.png)

1. Klicken Sie auf **Ruhezustand**, um den Schritt zu bestätigen.

   ![](assets/hibernate-2.png)

1. Nach erfolgreicher Aktivierung des Ruhezustands wird im Bildschirm **Developer Console** eine Benachrichtigung zur Fertigstellung des Ruhezustands für Ihre Umgebung angezeigt.

   ![](assets/hibernate-4.png)


### Deaktivieren des Ruhezustands {#de-hibernation-introduction}

1. Navigieren Sie zur **Developer Console**.
Unter [Zugreifen auf die Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) finden Sie Informationen zum Zugriff auf die **Developer Console** (über die Karte **Umgebungen**).

   >[!IMPORTANT]
   >Wenn Sie die **Developer Console** direkt über Cloud Manager verknüpfen, haben Sie keine Option, um den Ruhezustand einer Sandbox-Programmumgebung zu deaktivieren. Fügen Sie zur Problemumgehung in der Developer Console das folgende Muster am Ende der URL `#release-cm-p1234-e5678 where 1234` hinzu: 1234 ist Ihre *Programm-ID* und 5678 Ihre *Umgebungs-ID*.

   >[!NOTE]
   >Alternativ können Sie zur **Developer Console** navigieren, um den Ruhezustand zu deaktivieren, indem Sie auf den Erstellungs- oder Veröffentlichungs-Service einer bereits im Ruhestand befindlichen Umgebung zugreifen. In dem Fall wird eine Landingpage mit einem Link zur Developer Console angezeigt. Weitere Informationen finden Sie unten im Abschnitt „Zugreifen auf eine im Ruhezustand befindliche Umgebung“.

   >[!IMPORTANT]
   >Zugriff auf die Developer Console wird über die **Cloud Manager – Entwicklerrolle** in der **Admin Console** definiert. Ein Anwender mit den Berechtigungen der Entwicklerrolle kann den Ruhezustand einer Sandbox-Programmumgebung deaktivieren.

1. Klicken Sie auf **Ruhezustand deaktivieren**, wie in der Abbildung unten gezeigt:

   ![](assets/de-hibernation-img1.png)

   Oder

   Klicken Sie oben links auf den Link **Umgebungen**, um die Liste der Umgebungen anzuzeigen, und klicken Sie dann auf **Ruhezustand deaktivieren**, wie in der Abbildung unten dargestellt.

   ![](assets/de-hibernate-1b.png)


1. Klicken Sie auf **Ruhezustand deaktivieren**, um den Schritt zu bestätigen.

   ![](assets/de-hibernation-img2.png)

1. Sie erhalten eine Benachrichtigung, dass die Deaktivierung des Ruhezustands begonnen hat, und werden über den Fortschritt informiert.

   ![](assets/de-hibernation-img3.png)

1. Nach Abschluss des Vorgangs ist die Sandbox-Programmumgebung wieder aktiv.

   ![](assets/de-hibernation-img4.png)

#### Berechtigungen zum Deaktivieren des Ruhezustands {#permissions-de-hibernate}

Jeder Anwender mit einem Produktprofil, das Zugriff auf AEM as a Cloud Service gewährt, sollte auf die **Developer Console** zugreifen und somit die Umgebung reaktivieren können.

#### Zugreifen auf eine im Ruhezustand befindliche Umgebung {#accessing-hibernated-environment}

Bei Browser-Anfragen an die Erstellungs- oder Veröffentlichungsebene einer im Ruhezustand befindlichen Umgebung wird dem Anwender eine Landingpage angezeigt, die den Ruhezustand der Umgebung beschreibt, wie in der folgenden Abbildung dargestellt:

![](assets/de-hibernation-img5.png)

### Wichtige Überlegungen {#important-considerations}

Für im Ruhezustand befindliche oder reaktivierte Umgebungen gelten einige wichtige Aspekte:

* Ein Anwender kann eine Pipeline verwenden, um benutzerdefinierten Code für im Ruhezustand befindliche Umgebungen bereitzustellen. Die Umgebung verbleibt im Ruhezustand; der neue Code wird in der Umgebung angezeigt, sobald der Ruhezustand deaktiviert wird.

* AEM-Upgrades können auf im Ruhezustand befindliche Umgebungen angewendet werden; sie können von Kunden in Cloud Manager manuell ausgelöst werden. Die Umgebung verbleibt im Ruhezustand; die neue Version erscheint in der Umgebung, sobald der Ruhezustand deaktiviert wurde.

>[!NOTE]
>Derzeit gibt Cloud Manager nicht an, ob sich eine Umgebung im Ruhezustand befindet.

## AEM-Updates für Sandbox-Umgebungen {#aem-updates-sandbox}

Weitere Informationen finden Sie unter [AEM-Versions-Updates](/help/implementing/deploying/aem-version-updates.md).

Ein Anwender kann AEM-Updates in einem Sandbox-Programm manuell auf Umgebungen anwenden.

Informationen zum Aktualisieren einer Umgebung finden Sie unter [Aktualisieren von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment).

>[!NOTE]
>* Ein manuelles Update ist nur möglich, wenn die Zielumgebung über eine ordnungsgemäß konfigurierte Pipeline verfügt.
>* Bei einem manuellen Update der *Produktions*- oder *Staging*-Umgebung wird jeweils automatisch auch die andere Umgebung aktualisiert. Der Satz aus Produktions- und Staging-Umgebung muss sich in derselben AEM-Version befinden.






