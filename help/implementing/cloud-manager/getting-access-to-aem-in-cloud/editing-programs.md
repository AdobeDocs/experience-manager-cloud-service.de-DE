---
title: Bearbeiten von Programmen
description: Erfahren Sie, wie Sie Ihre Produktions- und Sandbox-Programme bearbeiten, um ihre Optionen nach der Erstellung anzupassen.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: c3f3693793922f965a59dd693b69a7df9ea96cda
workflow-type: tm+mt
source-wordcount: '1346'
ht-degree: 20%

---


# Bearbeiten von Programmen {#editing-programs}

Um Programme zu verwalten und zu bearbeiten, beginnen Sie bei der Konsole [**Meine Programme**](/help/implementing/cloud-manager/navigation.md). Die Seite **Meine Programme** bietet einen Überblick über alle Programme, auf die Sie Zugriff haben. Bei der Auswahl eines einzelnen Programms **die Seite** Programmübersicht“ einen Überblick über die Details des Programms.

Von der **Programmübersicht** aus können Benutzende mit den erforderlichen Berechtigungen [Produktionsprogramme, die in Ihrer Organisation erstellt wurden](creating-production-programs.md) und [Sandbox-Programme, die in Ihrer Organisation erstellt wurden](creating-sandbox-programs.md), bearbeiten. Durch die Bearbeitung eines Programms haben Sie folgende Möglichkeiten:


* Aktivieren oder deaktivieren Sie den **WAF-DDOS** Schutz auf der Registerkarte **Sicherheit**.
* Fügen Sie die Sites-Lösung einem vorhandenen Programm mit Assets hinzu und fügen Sie Assets einem vorhandenen Programm mit Sites hinzu.
* Entfernen Sie Sites oder Assets aus einem vorhandenen Programm, das sowohl Sites als auch Assets enthält.
* Hinzufügen einer nicht verwendeten Lösungsberechtigung für ein vorhandenes Programm oder Erstellen eines neuen Programms.
* Markieren Sie Produktionsprogramme zum Löschen.
* Löschen von Sandbox-Programmen.

## Berechtigungen {#permissions}

Sie müssen die Rolle **Geschäftsinhaber** haben, um Programme zu bearbeiten, Sandbox-Programme zu löschen, Produktionsprogramme zum Löschen zu markieren und auf das Lizenz-Dashboard zuzugreifen.

## Bearbeiten eines Programms {#editing}

Jedes Mal, wenn ein Programm bearbeitet wird, einschließlich des Hinzufügens oder Entfernens einer Lösung oder eines Add-ons, werden diese Änderungen erst nach der nächsten Bereitstellung wirksam.

**Bearbeiten eines Programms:**

1. Melden Sie sich bei Cloud Manager unter [experience.adobe.com](https://experience.adobe.com) an.
1. Klicken Sie **Abschnitt „Schnellzugriff** auf **Experience Manager**.
1. Klicken Sie im linken Panel auf **Cloud Manager**.
1. Wählen Sie das entsprechende Unternehmen aus.
1. Klicken Sie auf der **Meine**&quot; auf das Programm, das Sie bearbeiten möchten.
1. Klicken Sie oben links auf der Seite auf den Namen des Programms und wählen Sie dann **Programm bearbeiten** aus.

   ![Option „Programm bearbeiten“ im Dropdown-Menü des Programms](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/edit-program.png)

1. Legen **im Dialogfeld** bearbeiten auf den Registerkarten die gewünschten Optionen fest.

   ![Registerkarte „Allgemein“](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/edit-program-dialog-box.png)

   Die zur Bearbeitung des Programms verfügbaren Optionen sind mit denen zum Erstellen des Programms identisch.

   * Sie können konfigurieren, ob eine Veröffentlichungsebene für neue Umgebungen (Beta) bereitgestellt wird. Siehe [Flexible Veröffentlichungsebene (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).
   * Einzelheiten zu den einzelnen Optionen finden Sie unter [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) und [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).
   * Um die Web Application Firewall (WAF) jederzeit zu aktivieren oder zu deaktivieren, wählen Sie die Registerkarte **Sicherheit** aus und aktivieren oder deaktivieren Sie dann das Kontrollkästchen **WAF-DDOS-**. Wenn Sie dieses Kontrollkästchen aktivieren, wird die Funktion aktiviert. Zusätzlich zu einigen CVE-Schutzfunktionen (Automatic Common Vulnerabilities and Expositions) müssen Sie jedoch die WAF-Regeln über Cloud Manager bereitstellen, um vollen Schutz zu erhalten. Wenn WAF-Regeln lizenziert werden, dieses Kontrollkästchen jedoch nicht aktiviert ist, ist die Funktion nicht aktiv. Weitere Informationen finden Sie unter [Traffic-Filterregeln einschließlich WAF-Regeln](/help/security/traffic-filter-rules-including-waf.md).

     >[!NOTE]
     >Um sicherzustellen, dass die Funktion aktiv ist, überprüfen Sie die [CDN](//help/security/traffic-filter-rules-including-waf.md#cdn-logs)Protokolle, sobald Traffic auf die Site fließt. Suchen Sie nach Protokolleinträgen, die eine `rules`-Eigenschaft mit einem `waf` enthalten. Zum Beispiel:
     >
     >`"rules": "waf=SQLI"`
     >
     >Dieses Attribut wird angezeigt, sobald WAF aktiv ist, sogar bevor WAF-Regeln bereitgestellt werden.

     ![Dialogfeld „Programm bearbeiten“ mit Optionen auf der Registerkarte „Sicherheit“](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/cmk-edit-programs.png)

   * Auf derselben Registerkarte **Sicherheit** können Sie **Kundenseitig verwaltete Schlüssel** für ein vorhandenes Programm aktivieren.

     CMK kann nach der Aktivierung nicht deaktiviert werden. Konfigurieren Sie nach der Aktivierung von CMK Ihre Verschlüsselungsschlüssel in Experience Hub. Siehe [Konfigurieren von CMK in Experience Hub](#configure-cmk-experience-hub).

   * [Zusätzliche Optionen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#options) sind für Ihr Produktionsprogramm verfügbar, je nach den Berechtigungen Ihrer Organisation.

1. Klicken Sie auf **Aktualisieren**, um Ihre Änderungen zu speichern.

## Konfigurieren von CMK in Experience Hub {#configure-cmk-experience-hub}

Nachdem CMK für ein Programm aktiviert wurde, stellt Cloud Manager einen direkten Link zur CMK-Konfigurationsseite in Experience Hub bereit, über die Sie Folgendes einrichten können
Verschlüsselungsschlüssel, ohne das Programm verlassen zu müssen.

Nachdem CMK für eine Umgebung erfolgreich konfiguriert wurde, wird auf der Seite mit den Umgebungsdetails das Status-Badge **CMK-Konfiguration** angezeigt. Wenn CMK für das Programm aktiviert ist, aber noch nicht für eine bestimmte Umgebung konfiguriert wurde, wird das Badge nicht auf der Detailseite dieser Umgebung angezeigt.

**So konfigurieren Sie CMK in Experience Hub:**

1. Suchen Sie auf **Seite** Meine Programme“ die Programmkarte mit aktiviertem CMK.
2. Klicken Sie auf ![Auslassungszeichen - Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und dann auf **CMK konfigurieren**.

   ![Programmkarte mit dem CMK-Symbol, um aktiviert anzugeben, dann die Option CMK konfigurieren im Menü mit den Auslassungspunkten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/cmk-configure-edit-program-dlg.png)

   Experience Hub öffnet die CMK-Konfigurationsseite, auf der Sie Details zum Azure-Schlüsseltresor und Informationen zum Verschlüsselungsschlüssel angeben können.

   Die vollständigen Konfigurationsschritte finden Sie unter [Einrichten kundenverwalteter Schlüssel für AEM as a Cloud Service](/help/security/customer-managed-keys.md).

## Ein Produktionsprogramm zum Löschen markieren {#delete-production-program}

Das Löschen eines Produktionsprogramms erfolgt in zwei Phasen. Ein Geschäftsinhaber markiert das Programm zum Löschen, wodurch ein Trigger für einen Validierungs- und Stilllegungszeitraum entsteht. Das Programm wird dann nach Ablauf der Stilllegungszeit dauerhaft entfernt.

Wenn ein Produktionsprogramm zum Löschen markiert wird, geschieht Folgendes:

* Die mit dem Produktionsprogramm verknüpfte Gutschrift wird an den Kunden zurückgegeben.
* Alle zum Produktionsprogramm gehörenden Umgebungen werden entfernt.

Bevor das Markieren zum Löschen initiiert wird, prüft das System, ob das Produktionsprogramm zum Löschen geeignet ist. Wenn die Markierung fehlschlägt, wechselt das Produktionsprogramm stattdessen in einen `Failed to mark for deletion`.

>[!NOTE]
>
>Sandbox-Programme sind von diesem Prozess nicht betroffen. Informationen zum Löschen eines Sandbox-Programms finden Sie [Löschen eines Sandbox-Programms](#delete-sandbox-program).

**So markieren Sie ein Produktionsprogramm zum Löschen:**

1. Melden Sie sich bei Cloud Manager unter [experience.adobe.com](https://experience.adobe.com) an.
1. Klicken Sie **Abschnitt „Schnellzugriff** auf **Experience Manager**.
1. Klicken Sie im linken Panel auf **Cloud Manager**.
1. Wählen Sie das entsprechende Unternehmen aus.
1. Klicken Sie auf der **Meine**&quot; für das Produktionsprogramm, das Sie zum Löschen markieren möchten, auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und dann auf **Programm löschen**.

   ![Die Auswahl von Programm löschen aus der Dropdown-Liste eines Produktionsprogramms ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete1.png)*Beispielproduktionsprogramm wie oben gezeigt dient nur zu Veranschaulichungszwecken.*

1. Überprüfen Sie im Dialogfeld **Produktionsprogramm zum Löschen markieren** die Warnung, die die mit Ihrem Programm verbundenen Ressourcen auflistet, einschließlich Produktions-, Staging- und Entwicklungsumgebungen.

   ![Dialogfeld „Produktionsprogramm löschen“](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete2.png)


   >[!NOTE]
   >
   >Wenn das Produktionsprogramm Sperrressourcen enthält, z. B. Umgebungen, die derzeit aktualisiert werden, ist **Schaltfläche** Zum Löschen markieren“ deaktiviert. Warten Sie, bis alle Programmressourcen entsperrt wurden, bevor Sie das Programm zum Löschen markieren können.
   >
   >![Das Dialogfeld „Produktionsprogramm zum Löschen markieren“ zeigt an, dass das Programm nicht gelöscht werden kann, da es über Sperrressourcen verfügt](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete2b.png)


1. Geben Sie zur Bestätigung den Programmnamen wie im Dialogfeld angezeigt ein, und klicken Sie dann auf **Zum Löschen markieren**.

   Nach der Bestätigung zeigt das Produktionsprogramm während der Ausführung **Prozesses den Status** Zur Löschung kennzeichnen“ an.

   ![Markierung zum Löschstatus](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete3.png)

   Nach Abschluss des Vorgangs wird die Karte des Produktionsprogramms auf **Zum Löschen markiert** mit einem zugehörigen Warnhinweis-Badge aktualisiert.

   ![Zum Löschstatus markiert mit zugehörigem Warnhinweis-Badge](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete4.png)

1. Klicken Sie auf der Karte des Produktionsprogramms auf das Warnhinweis-Badge, um das geplante Datum der endgültigen Entfernung anzuzeigen.

   ![Anzeige des geplanten Termins für die endgültige Entfernung des Produktionsprogramms](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-markfordelete5.png)

   Nach Ablauf der Stilllegungszeit wird das Programm dauerhaft entfernt und kann nicht wiederhergestellt werden.

### Markierung eines Produktionsprogramms beim Löschen aufheben {#unmark-from-deletion}

Sie können ein Produktionsprogramm, das zum Löschen *markiert* wiederherstellen, solange die dauerhafte Entfernung noch nicht erfolgt ist.

>[!IMPORTANT]
>
>Um ein Produktionsprogramm wiederherzustellen, das zur Löschung markiert wurde, muss der Kunde über verfügbare Credits verfügen.

**So heben Sie die Markierung eines Produktionsprogramms beim Löschen auf:**

1. Suchen Sie auf der **Meine**&quot; die Karte für das Produktionsprogramm, auf der &quot;**zum Löschen markiert** angezeigt wird.

1. Klicken Sie auf der Karte „Produktionsprogramm“ auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und dann auf **Markierung zum Löschen aufheben**.

   ![Aufheben der Markierung des geplanten Datums für die endgültige Entfernung des Produktionsprogramms](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/production-program-unmarkfordelete6.png)

   Das Produktionsprogramm ist nicht zum Löschen markiert.

## Löschen eines Sandbox-Programms {#delete-sandbox-program}

Durch das Löschen eines Sandbox-Programms werden alle damit verbundenen Umgebungen und Pipelines entfernt.

>[!TIP]
>
>Benutzende mit den Rollen **Geschäftsinhaber** oder **Bereitstellungs-Manager** können alternativ ihre Produktions- und Staging-Umgebungen anstelle des gesamten Sandbox-Programms löschen.

**So löschen Sie ein Sandbox-Programm:**

1. Melden Sie sich bei Cloud Manager unter [experience.adobe.com](https://experience.adobe.com) an.
1. Klicken Sie **Abschnitt „Schnellzugriff** auf **Experience Manager**.
1. Klicken Sie im linken Panel auf **Cloud Manager**.
1. Wählen Sie das entsprechende Unternehmen aus.

1. Klicken Sie auf **[Seite „Meine](#my-programs)**&quot; auf das Sandbox-Programm, das Sie bearbeiten möchten, um seine Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Sandbox-Programms und wählen Sie **Programm löschen**.

   ![Option „Programm löschen“](assets/delete-sandbox1.png)

Alternativ können Sie auf der Übersichtsseite von Cloud Manager auf ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Karte Ihres Sandbox-Programms auf &quot;![&quot; klicken und **Programm löschen** auswählen.

![Sandbox aus Programmkarte löschen](assets/delete-sandbox2.png)
