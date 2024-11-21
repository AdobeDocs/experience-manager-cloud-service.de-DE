---
title: Wie kann ich Formulare in der Vorschau veröffentlichen oder die Veröffentlichung rückgängig machen?
description: Erfahren Sie, wie Sie Formulare in der AEM-Autorenumgebung veröffentlichen oder deren Veröffentlichung rückgängig machen können, um eine Vorschau der Instanzen anzuzeigen oder sie zu veröffentlichen. Unabhängig davon, ob Sie Ihre Formulare in einer Staging-Umgebung testen oder für Endbenutzer live bereitstellen, AEM bietet optimierte Tools für die effiziente Verwaltung dieses Prozesses.
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


# &#x200B; Verwalten der Veröffentlichung in Experience Manager Forms

Als Adobe Experience Manager Forms-Administrator können Sie Formulare aus Ihrer Autoreninstanz in Experience Manager Forms veröffentlichen. Sie können die Veröffentlichung eines Formulars oder Ordners zu einem späteren Zeitpunkt planen. Nach der Veröffentlichung können Benutzer auf die Formulare zugreifen und sie ausfüllen.

Sie können Formulare entweder mit der Option Publish veröffentlichen oder Veröffentlichung rückgängig machen, oder die Option Veröffentlichung verwalten , die in der Benutzeroberfläche von Experience Manager Forms verfügbar ist. Wenn Sie nachfolgende Änderungen an den Originalformularen oder -ordnern in Experience Manager Forms vornehmen, werden die Änderungen erst dann in der Veröffentlichungsinstanz übernommen, wenn Sie von Experience Manager Forms aus erneut veröffentlichen. Dadurch wird sichergestellt, dass laufende Änderungen nicht in der Veröffentlichungsinstanz verfügbar sind. In der Veröffentlichungsinstanz sind nur Änderungen verfügbar, die von einem Administrator veröffentlicht wurden.

## Option &quot;Publish forms using Publish&quot;

Mit der Veröffentlichungsoption können Sie ein Formular sofort veröffentlichen. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie ein Formular aus, das Sie veröffentlichen möchten. Klicken Sie in der Symbolleiste auf die Option Publish , sehen Sie sich alle Referenz-Assets an, die mit dem Formular veröffentlicht werden sollen, und klicken Sie auf Publish.

Screenshot eines Computers

Automatisch generierte Beschreibung

## Publish oder Rückgängigmachen der Veröffentlichung von Formularen mithilfe von &quot;Veröffentlichung verwalten&quot;


Mithilfe der Funktion Veröffentlichung verwalten können Sie Inhalte in dem ausgewählten Ziel veröffentlichen oder dessen Veröffentlichung rückgängig machen, Inhalte aus dem Ordner &quot;Formulare und Dokumente&quot;zur Veröffentlichungsliste hinzufügen, Verweise zur Veröffentlichung auswählen und die Veröffentlichung zu einem späteren Zeitpunkt planen.


Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie ein Formular aus, das Sie veröffentlichen möchten. Klicken Sie in der Symbolleiste auf die Option Veröffentlichung verwalten .


Screenshot eines Computers

Automatisch generierte Beschreibung



Die folgenden Optionen sind in der Benutzeroberfläche &quot;Veröffentlichung verwalten&quot;verfügbar:

* Aktionen

   * Publish: Publish forms zum ausgewählten Ziel
   * Veröffentlichung rückgängig machen: Veröffentlichung von Formularen am Ziel rückgängig machen

* Ziel

   * Publish: Publish forms to Experience Manager Forms (AEM) Publish-Instanz.
   * Vorschau: Publish forms to Experience Manager Forms (AEM)-Vorschauinstanz.

* Planung wird durchgeführt

   * Jetzt: Publish forms sofort
   * Später: Publish forms basierend auf dem Aktivierungsdatum oder der Aktivierungszeit



Um fortzufahren, klicken Sie auf **Weiter**. Verwenden Sie auf der Registerkarte Umfang die Optionen Inhalt hinzufügen , um weitere Inhalte für die Veröffentlichung hinzuzufügen. Sie können beispielsweise weitere Forms- oder Datensatzdokumentdateien hinzufügen.

### Inhalt hinzufügen

Durch das Veröffentlichen in Experience Manager Forms können Sie der Veröffentlichungsliste weitere Inhalte (Formulare, Assets und Ordner) hinzufügen. Sie können der Liste weitere Formulare, Assets oder Ordner aus dem Ordner &quot;formsanddocuments&quot;hinzufügen. Es ist jedoch nicht möglich, Assets aus mehreren Ordnern gleichzeitig hinzuzufügen.

Screenshot eines Computers

Automatisch generierte Beschreibung

Klicken Sie auf die Schaltfläche **Inhalt hinzufügen** , um weitere Inhalte hinzuzufügen. Sie können mehrere Assets aus einem Ordner hinzufügen oder mehrere Ordner gleichzeitig hinzufügen. Es ist jedoch nicht möglich, Assets aus mehreren Ordnern gleichzeitig hinzuzufügen.

Um die Verweise zu konfigurieren, die für ein Formular oder andere Assets veröffentlicht werden sollen, wählen Sie das Formular oder das Asset aus und klicken Sie auf Veröffentlichte Verweise.

Screenshot eines Computers

Automatisch generierte Beschreibung

Deaktivieren Sie im Dialogfeld Veröffentlichte Verweise die Option Assets, die Sie nicht veröffentlichen möchten, und klicken Sie auf Fertig .


Screenshot eines Computers

Automatisch generierte Beschreibung


## Publish oder spätere Rückgängigmachen der Veröffentlichung eines Formulars


Neben der Möglichkeit, Formulare zu einem späteren Zeitpunkt zu veröffentlichen oder die Veröffentlichung rückgängig zu machen, ermöglicht die Option Veröffentlichen oder Veröffentlichung rückgängig machen auch die Konfiguration eines Workflows. Die Formulare werden nach Abschluss des Workflows veröffentlicht oder nicht veröffentlicht. So planen Sie die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung eines Formulars:

1. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie das Formular aus, das Sie für die Veröffentlichung planen möchten.
1. Klicken Sie in der Symbolleiste auf die Option Veröffentlichung verwalten .
1. Klicken Sie auf Publish oder Veröffentlichung in Aktion rückgängig machen und wählen Sie dann das Ziel aus, in dem Sie den Inhalt veröffentlichen oder dessen Veröffentlichung rückgängig machen möchten.

   * Vorschau: Verwenden Sie die Option Vorschau , um die Veröffentlichung in einer Experience Manager Forms-Vorschauumgebung rückgängig zu machen. Die Experience Manager Forms-Vorschauumgebungen werden zum Testen unter Entwicklungsformularen verwendet.
   * Publish: Verwenden Sie die Option Experience Manager Forms Publish , um das Formular an die Experience Manager Forms-Veröffentlichungsumgebung zu senden, nachdem das Formular für die Verwendung in einer Produktionsumgebung bereit ist.


1. Wählen Sie Später unter Planung aus.

1. Wählen Sie ein Aktivierungsdatum aus und geben Sie Datum und Uhrzeit an. Klicken Sie auf Weiter.

   Screenshot eines Computers

   Automatisch generierte Beschreibung

1. Fügen Sie im Tab Perimeter Inhalt hinzu (falls erforderlich). Klicken Sie auf Weiter.

   Screenshot eines Computers

   Automatisch generierte Beschreibung

1, (Optional) Geben Sie auf der Registerkarte Workflows einen Workflow-Titel an. Klicken Sie auf Publish Später.

Screenshot eines Computers

Automatisch generierte Beschreibung

## Bestimmen des Veröffentlichungsstatus

Es gibt mehrere Möglichkeiten, den Veröffentlichungsstatus zu ermitteln:

* Melden Sie sich bei der Zielinstanz an, um die veröffentlichten Formulare und anderen Assets zu überprüfen (je nach geplantem Datum oder Uhrzeit).

* Verwenden Sie die Timeline-Ansicht, um den Veröffentlichungsstatus zu ermitteln.

* Verwenden Sie das Seiteninformationsmenü im adaptiven Forms-Editor.