---
title: Integrieren mit Adobe Target
description: 'Integrieren mit Adobe Target '
feature: Administering
role: Admin
exl-id: cf243fb6-5563-427f-a715-8b14fa0b0fc2
source-git-commit: 421ad8506435e8538be9c83df0b78ad8f222df0c
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 99%

---

# Integrieren mit Adobe Target{#integrating-with-adobe-target}

Als Teil von Adobe Experience Cloud ermöglicht Adobe Target Ihnen die Verbesserung der Content-Relevanz durch Targeting und Messungen über alle Kanäle hinweg. Die Integration von Adobe Target und AEM as a Cloud Service erfordert Folgendes:

* Die Verwendung der Touch-optimierte Benutzeroberfläche, um eine Target-Konfiguration in AEM as a Cloud Service zu erstellen (IMS-Konfiguration erforderlich)
* Das Hinzufügen und Konfigurieren von Adobe Target als Erweiterung in [Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html?lang=de)

Adobe Experience Platform Launch ist erforderlich, um Client-seitige Eigenschaften für Analytics und Target auf AEM-Seiten zu verwalten (JS-Bibliotheken/-Tags). Allerdings ist für „Erlebnis-Targeting“ die Integration mit Experience Platform Launch erforderlich. Für den Export von Experience Fragments in Target benötigen Sie nur die Adobe Target-Konfiguration und IMS.

>[!NOTE]
>
>Kunden mit Adobe Experience Manager as a Cloud Service, die kein Target-Konto haben, können Zugriff auf Target Foundation Pack für Experience Cloud anfordern. Das Foundation Pack ermöglicht eine eingeschränkte Verwendung von Target.

## Erstellen der Adobe Target-Konfiguration {#create-configuration}

1. Navigieren Sie zu **Tools** > **Cloud Services**.
   ![Navigation](assets/cloudservice1.png "Navigation")
2. Wählen Sie **Adobe Target** aus.
3. Klicken Sie auf die Schaltfläche **Erstellen**.
   ![Erstellen](assets/tenant1.png "Erstellen")
4. Geben Sie die Details ein (siehe unten) und wählen Sie **Verbinden** aus.
   ![Verbinden](assets/open_screen1.png "Verbinden")

### IMS-Konfiguration {#ims-configuration}

Um Target ordnungsgemäß in AEM und Experience Platform Launch zu integrieren, ist eine IMS-Konfiguration für Launch und Target erforderlich. Während die IMS-Konfiguration für Experience Platform Launch in AEM as a Cloud Service vorkonfiguriert ist, muss die Target-IMS-Konfiguration erstellt werden (nachdem Target bereitgestellt wurde). Sehen Sie sich [dieses Video](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html) und [diese Seite](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/integration-ims-adobe-io.html?lang=de) an, um zu erfahren, wie Sie die Target-IMS-Konfiguration erstellen.

### Adobe Target-Mandanten-ID und Adobe Target-Clientcode {#tenant-client}

Beachten Sie beim Konfigurieren der Felder für die Adobe Target-Mandanten-ID und den Adobe Target-Clientcode Folgendes:

1. Für die meisten Kunden sind die Mandanten-ID und der Clientcode identisch. Das bedeutet, dass beide Felder die gleichen Werte enthalten. Achten Sie darauf, dass Sie die Mandanten-ID in beide Felder eingeben.
2. Sollten Sie über ältere Werte verfügen, können Sie auch verschiedene Werte in die Felder „Mandanten-ID“ und „Clientcode“ eingeben.

Beachten Sie in beiden Fällen Folgendes:

* Standardmäßig wird der Clientcode (wenn er zuerst eingegeben wird) automatisch in das Feld „Mandanten-ID“ kopiert.
* Sie haben die Möglichkeit, den Standardwert für die Mandanten-ID zu ändern.
* Dementsprechend basieren die Backend-Target-Aufrufe auf der Mandanten-ID und die Client-seitigen Target-Aufrufe auf dem Clientcode.

Wie bereits erwähnt, tritt der erste Fall in AEM as a Cloud Service häufiger auf. Stellen Sie in beiden Fällen sicher, dass **beide** Felder die richtigen Informationen entsprechend Ihren Anforderungen enthalten.

>[!NOTE]
>
> Wenn Sie eine bestehende Target-Konfiguration ändern möchten:
>
> 1. Geben Sie die Mandanten-ID erneut ein.
> 2. Stellen Sie zu Target eine neue Verbindung her.
> 3. Speichern Sie die Konfiguration.


### Bearbeiten der Target-Konfiguration {#edit-target-configuration}

Um die Target-Konfiguration zu deaktivieren, führen Sie die folgenden Schritte aus:

1. Wählen Sie eine vorhandene Konfiguration aus und klicken Sie auf **Eigenschaften**.
2. Bearbeiten Sie die Eigenschaften.
3. Wählen Sie **Erneute Verbindung zu Adobe Target herstellen** aus.
4. Klicken Sie auf **Speichern und schließen**.

### Hinzufügen einer Konfiguration zu einer Site {#add-configuration}

Um eine Konfiguration für die Touch-optimierte Benutzeroberfläche auf eine Site anzuwenden, wechseln Sie zu: **Sites** → **Beliebige Site-Seite auswählen** → **Eigenschaften** → **Erweitert** → **Konfiguration** → Konfigurationsmandanten auswählen.

## Integrieren von Adobe Target mit AEM Sites mithilfe von Adobe Experience Platform Launch {#integrate-target-launch}

AEM bietet eine vorkonfigurierte Integration mit Experience Platform Launch. Durch Hinzufügen der Adobe Target-Erweiterung zu Experience Platform Launch können Sie die Funktionen von Adobe Target auf AEM-Web-Seiten verwenden. Target-Bibliotheken werden nur mit Launch gerendert.

>[!NOTE]
>
>Vorhandene (ältere) Frameworks funktionieren weiterhin, können jedoch nicht in der Touch-optimierten Benutzeroberfläche konfiguriert werden. Es wird empfohlen, die Variablenzuordnungskonfigurationen in Adobe Experience Platform Launch neu zu erstellen.

Die Schritte zur Integration als allgemeine Übersicht:

1. Erstellen einer Experience Platform Launch-Eigenschaft
2. Hinzufügen der erforderlichen Erweiterungen
3. Erstellen eines Datenelements (zum Erfassen von ContextHub-Parametern)
4. Erstellen einer Seitenregel
5. Erstellen und Veröffentlichen

### Erstellen einer Experience Platform Launch-Eigenschaft {#create-property}

Eine Eigenschaft ist ein Container, der mit Erweiterungen, Regeln und Datenelementen gefüllt ist.

1. Klicken Sie auf die Schaltfläche **Neue Eigenschaft**.
2. Geben Sie einen Namen für die Eigenschaft an.
3. Geben Sie als Domain die IP/den Host ein, auf der/dem Sie die Experience Platform Launch-Bibliothek laden möchten.
4. Klicken Sie auf die Schaltfläche **Speichern**.
   ![Experience Platform Launch-Eigenschaft](assets/properties_newproperty1.png "Experience Platform Launch-Eigenschaft")

### Hinzufügen der erforderlichen Erweiterungen {#add-extension}

**Erweiterungen** ist der Name des Containers, der die Core-Bibliothekseinstellungen verwaltet. Die Adobe Target-Erweiterung unterstützt Client-seitige Implementierungen, indem „at.js“ verwendet wird, das JavaScript-SDK von Target für das moderne Web. Sie müssen sowohl die **Adobe Target**- als auch die **Adobe ContextHub**-Erweiterung hinzufügen.

1. Wählen Sie die Option „Erweiterungskatalog“ aus und suchen Sie im Filter nach Target.
2. Wählen Sie **Adobe Target at.js** aus und klicken Sie auf die Option „Installieren“.
   ![Target-Suche](assets/search_ext1.png "Target-Suche")
3. Klicken Sie auf die Schaltfläche **Konfigurieren**. Beachten Sie das Konfigurationsfenster mit den importierten Target-Anmeldedaten und die at.js-Version für diese Erweiterung.
4. Wählen Sie **Speichern**, um die Target-Erweiterung zur Experience Platform Launch-Eigenschaft hinzuzufügen. Die Target-Erweiterung sollte unter **Installierte Erweiterungen** aufgeführt sein.
   ![Erweiterung speichern](assets/configure_extension1.png "Erweiterung speichern")
5. Wiederholen Sie die obigen Schritte, um nach der **Adobe ContextHub**-Erweiterung zu suchen und sie zu installieren (dies ist für die Integration mit ContextHub-Parametern erforderlich, abhängig vom jeweils durchgeführten Targeting).

### Erstellen eines Datenelements {#data-element}

**Datenelemente** sind die Platzhalter, denen Sie ContextHub-Parameter zuordnen können.

1. Wählen Sie **Datenelemente**.
2. Wählen Sie **Datenelement hinzufügen** aus.
3. Geben Sie den Namen des Datenelements an und ordnen Sie es einem ContextHub-Parameter zu.
4. Wählen Sie **Speichern** aus.
   ![Datenelement](assets/data_elem1.png "Datenelement")

### Erstellen einer Seitenregel {#page-rule}

Unter **Regel** können Folgen von Aktionen definiert und geordnet werden, die lokal zum Targeting ausgeführt werden.

1. Fügen Sie eine Reihe Aktionen hinzu, wie im Screenshot dargestellt.
   ![Aktionen](assets/rules1.png "Aktionen")
2. Fügen Sie unter „Parameter zu sämtlichen Mboxes hinzufügen“ das zuvor konfigurierte Datenelement (siehe Datenelement oben) zu dem Parameter hinzu, der im Mbox-Aufruf gesendet wird.
   ![Mbox](assets/map_data1.png "Aktionen")

### Erstellen und Veröffentlichen {#build-publish}

Weitere Informationen zum Erstellen und Veröffentlichen finden Sie auf dieser [Seite](https://experienceleague.adobe.com/docs/experience-manager-learn/aem-target-tutorial/aem-target-implementation/using-launch-adobe-io.html?lang=de).

## Unterschiede an der Inhaltsstruktur zwischen den Konfigurationen der klassischen und Touch-optimierten Benutzeroberfläche {#changes-content-structure}

<table style="table-layout:auto">
  <tr>
    <th>Änderung</th>
    <th>Konfiguration der klassischen Benutzeroberfläche</th>
    <th>Konfiguration der Touch-optimierten Benutzeroberfläche</th>
    <th>Folgen</th>
  </tr>
  <tr>
    <td>Speicherort der Target-Konfiguration</td>
    <td>/etc/cloudservices/testandtarget/</td>
    <td>/conf/tenant/settings/cloudservices/target/</td>
    <td> Zuvor waren unter „/etc/cloudservices/testandtarget“ mehrere Konfigurationen vorhanden. Inzwischen ist unter einem Mandanten nur jeweils eine Konfiguration zu finden.</td>
  </tr>
</table>

>[!NOTE]
>
>Ältere Konfigurationen werden für die bestehenden Kunden weiterhin unterstützt (ohne die Möglichkeit, neue zu erstellen oder zu bearbeiten). Ältere Konfigurationen sind Teil von Inhalts-Packages, die von Kunden mithilfe von VSTS hochgeladen werden.
