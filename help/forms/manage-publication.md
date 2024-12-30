---
title: Wie werden Formulare in Vorschau- oder Veröffentlichungsinstanzen veröffentlicht bzw. deren Veröffentlichung rückgängig gemacht?
description: Erfahren Sie, wie Sie Formulare in der AEM-Autorenumgebung veröffentlichen oder die Veröffentlichung rückgängig machen können, um Instanzen in der Vorschau anzuzeigen oder zu veröffentlichen. Unabhängig davon, ob Sie Ihre Formulare in einer Staging-Umgebung testen oder für Endbenutzer live bereitstellen, bietet AEM optimierte Tools, um diesen Prozess effizient zu verwalten.
Keywords: 6.5 forms to cloud service, 6.5 forms to cs, manage publication, , AEM Forms 6.5 to Cloud Service, AEM form migration to cloud service, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
contentOwner: khsingh
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
source-git-commit: 242dcbc5bb541dfac601454fb75dec3bdff1ea64
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 7%

---


# &#x200B;Veröffentlichung in Experience Manager Forms verwalten

Als Adobe Experience Manager Forms-Administrator können Sie Formulare von Ihrer Autoreninstanz in Experience Manager Forms veröffentlichen. Sie können die Veröffentlichung eines Formulars oder Ordners zu einem späteren Zeitpunkt planen. Nach der Veröffentlichung können Benutzer auf die Formulare zugreifen und sie ausfüllen.

Sie können Formulare mit der Option Publish oder Veröffentlichung verwalten , die in der Benutzeroberfläche von Experience Manager Forms verfügbar ist, veröffentlichen oder die Veröffentlichung rückgängig machen. Wenn Sie in Experience Manager Forms nachfolgende Änderungen an den Originalformularen oder -ordnern vornehmen, werden die Änderungen erst dann in der Veröffentlichungsinstanz übernommen, wenn Sie von Experience Manager Forms aus erneut veröffentlichen. Dadurch wird sichergestellt, dass laufende Änderungen nicht in der Veröffentlichungsinstanz verfügbar sind. Nur von einem Administrator veröffentlichte Änderungen sind in der Veröffentlichungsinstanz verfügbar.

## Publish Forms mit Publish-Option

Mit der Option „Veröffentlichen“ können Sie ein Formular sofort veröffentlichen. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie ein Formular aus, das Sie veröffentlichen möchten. Klicken Sie auf die Option Publish in der Symbolleiste, sehen Sie sich alle Referenz-Assets an, die mit dem Formular veröffentlicht werden sollen, und klicken Sie auf Publish.

Ein Screenshot eines Computers

Automatisch erstellte Beschreibung

## Publish oder Rückgängigmachen der Veröffentlichung von Formularen mit „Veröffentlichung verwalten“


Mit „Veröffentlichung verwalten“ können Sie Inhalte am ausgewählten Ziel veröffentlichen oder die Veröffentlichung rückgängig machen, Inhalte aus dem gesamten Ordner „Formulare und Dokumente“ zur Veröffentlichungsliste hinzufügen, Verweise zur Veröffentlichung auswählen und die Veröffentlichung für ein späteres Datum oder eine spätere Uhrzeit planen.


Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie ein Formular aus, das Sie veröffentlichen möchten. Klicken Sie in der Symbolleiste auf Veröffentlichung verwalten .


Ein Screenshot eines Computers

Automatisch erstellte Beschreibung



Die folgenden Optionen sind in der Benutzeroberfläche „Veröffentlichung verwalten“ verfügbar:

* Aktionen

   * Publish: Publish-Formulare zum ausgewählten Ziel
   * Veröffentlichung rückgängig machen: Veröffentlichung von Formularen im Ziel aufheben

* Ziel

   * Publish: Publish-Instanz von Publish Forms in Experience Manager Forms (AEM).
   * Vorschau: Vorschau für Publish Forms in Experience Manager Forms (AEM).

* Planung wird durchgeführt

   * Jetzt: Publish-Formulare sofort
   * Später: Publish-Formulare basierend auf Aktivierungsdatum oder -zeit



Um fortzufahren, klicken Sie auf **Weiter**. Verwenden Sie auf der Registerkarte Umfang die Optionen Inhalt hinzufügen , um weitere Inhalte für die Veröffentlichung hinzuzufügen. Sie können beispielsweise weitere Forms- oder Datensatzdokumentdateien hinzufügen.

### Inhalt hinzufügen

Durch das Veröffentlichen in Experience Manager Forms können Sie der Veröffentlichungsliste weitere Inhalte (Formulare, Assets und Ordner) hinzufügen. Sie können der Liste über den Ordner „Formulare und Dokumente“ weitere Formulare, Assets oder Ordner hinzufügen. Es ist jedoch nicht möglich, Assets aus mehreren Ordnern gleichzeitig hinzuzufügen.

Ein Screenshot eines Computers

Automatisch erstellte Beschreibung

Klicken Sie auf **Schaltfläche** Inhalt hinzufügen“, um weitere Inhalte hinzuzufügen. Sie können mehrere Assets aus einem Ordner hinzufügen oder mehrere Ordner gleichzeitig hinzufügen. Es ist jedoch nicht möglich, Assets aus mehreren Ordnern gleichzeitig hinzuzufügen.

Um die zu veröffentlichenden oder nicht zu veröffentlichenden Verweise für ein Formular oder andere Assets zu konfigurieren, wählen Sie das Formular oder Asset aus und klicken Sie auf Veröffentlichte Verweise .

Ein Screenshot eines Computers

Automatisch erstellte Beschreibung

Deaktivieren Sie im Dialogfeld Veröffentlichte Verweise die Assets, deren Veröffentlichung Sie nicht rückgängig machen möchten, und klicken Sie auf Fertig.


Ein Screenshot eines Computers

Automatisch erstellte Beschreibung


## Publish oder Rückgängigmachen der Veröffentlichung eines Formulars


Mit der Option „Später veröffentlichen“ oder „Veröffentlichung aufheben“ können Sie Formulare nicht nur zu einem späteren Zeitpunkt veröffentlichen, sondern auch einen Workflow konfigurieren. Die Formulare werden nach Abschluss des Workflows veröffentlicht bzw. ihre Veröffentlichung wird rückgängig gemacht. So planen Sie die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung eines Formulars:

1. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie das Formular aus, für das Sie die Veröffentlichung planen möchten.
1. Klicken Sie in der Symbolleiste auf Veröffentlichung verwalten .
1. Klicken Sie auf Publish oder Veröffentlichung in Aktion rückgängig machen und wählen Sie dann das Ziel aus, in dem Sie die Veröffentlichung des Inhalts vornehmen oder die Veröffentlichung rückgängig machen möchten.

   * Vorschau: Verwenden Sie die Option „Vorschau“, um die Veröffentlichung in einer Experience Manager Forms-Vorschau-Umgebung zu veröffentlichen oder rückgängig zu machen. Die Experience Manager Forms-Vorschauumgebungen werden zum Testen unter „Entwicklungsformulare“ verwendet.
   * Publish: Verwenden Sie die Option Experience Manager Forms Publish , um das Formular an die Experience Manager Forms-Veröffentlichungsumgebung zu senden, nachdem das Formular in einer Produktionsumgebung einsatzbereit ist.


1. Wählen Sie Später unter Planung aus.

1. Wählen Sie ein Aktivierungsdatum aus und geben Sie das Datum und die Uhrzeit an. Klicken Sie auf Weiter.

   Ein Screenshot eines Computers

   Automatisch erstellte Beschreibung

1. Klicken Sie auf der Registerkarte Umfang auf Inhalt hinzufügen (falls erforderlich). Klicken Sie auf Weiter.

   Ein Screenshot eines Computers

   Automatisch erstellte Beschreibung

1, (Optional) Geben Sie auf der Registerkarte „Workflows“ einen Workflow-Titel an. Klicken Sie auf Publish Later.

Ein Screenshot eines Computers

Automatisch erstellte Beschreibung

## Bestimmen des Veröffentlichungsstatus

Es gibt mehrere Möglichkeiten, den Veröffentlichungsstatus zu bestimmen:

* Melden Sie sich bei der Zielinstanz an, um die veröffentlichten Formulare und anderen Assets zu überprüfen (je nach geplantem Datum oder Uhrzeit).

* Verwenden Sie die Zeitleisten -Ansicht, um den Veröffentlichungsstatus zu bestimmen.

* Verwenden Sie das Menü Seiteninformationen im Editor für adaptive Forms.