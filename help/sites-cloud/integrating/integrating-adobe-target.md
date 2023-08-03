---
title: Integrieren mit Adobe Target
description: Erfahren Sie, wie Sie Adobe Target mit AEM as a Cloud Service integrieren.
feature: Administering
role: Admin
exl-id: cf243fb6-5563-427f-a715-8b14fa0b0fc2
source-git-commit: f7ffe727ecc7f1331c1c72229a5d7f940070c011
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 67%

---

# Integrieren mit Adobe Target{#integrating-with-adobe-target}

Als Teil der Adobe Experience Cloud ermöglicht Adobe Target Ihnen die Steigerung der Inhaltsrelevanz durch Targeting und Messungen über alle Kanäle hinweg. Die Integration von Adobe Target und AEM as a Cloud Service erfordert Folgendes:

* Die Verwendung der Touch-optimierte Benutzeroberfläche, um eine Target-Konfiguration in AEM as a Cloud Service zu erstellen (IMS-Konfiguration erforderlich)
* Das Hinzufügen und Konfigurieren von Adobe Target als Erweiterung in [Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html?lang=de)

Adobe Experience Platform Launch ist erforderlich, um Client-seitige Eigenschaften für Analytics und Target auf AEM-Seiten zu verwalten (JS-Bibliotheken/-Tags). Allerdings ist die Integration mit Launch für das Erlebnis-Targeting erforderlich.

Für den Export von Experience Fragments und/oder Inhaltsfragmenten nach Target benötigen Sie nur die [Adobe Target-Konfiguration und IMS](/help/sites-cloud/integrating/integration-adobe-target-ims.md).

>[!NOTE]
>
>Kunden, die kein Target-Konto haben, können zum Experience Cloud Zugriff auf das Target Foundation Pack anfordern. Das Foundation Pack ermöglicht eine eingeschränkte Verwendung von Target.

## Erstellen der Adobe Target-Konfiguration {#create-configuration}

1. Navigieren Sie zu **Tools** > **Cloud Services**.
   ![Navigation](assets/cloudservice1.png "Navigation")
2. Wählen Sie **Adobe Target** aus.
3. Klicken Sie auf die Schaltfläche **Erstellen**.
   ![Erstellen](assets/tenant1.png "Erstellen")
4. Geben Sie die Details ein (siehe unten) und wählen Sie **Verbinden** aus.
   ![Verbinden](assets/open_screen1.png "Verbinden")

### IMS-Konfiguration {#ims-configuration}

Um Target ordnungsgemäß in AEM und Experience Platform Launch zu integrieren, ist eine IMS-Konfiguration für Launch und Target erforderlich. Während die IMS-Konfiguration für Experience Platform Launch in AEM as a Cloud Service vorkonfiguriert ist, muss die Target-IMS-Konfiguration erstellt werden (nachdem Target bereitgestellt wurde). Siehe [IMS-Konfiguration für die Integration mit Adobe Target](/help/sites-cloud/integrating/integration-adobe-target-ims.md) und das Video [Integrieren von Experience Platform Launch und AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html?lang=de) , um zu erfahren, wie Sie die Target-IMS-Konfiguration erstellen.

### Adobe Target-Mandanten-ID und Adobe Target-Clientcode {#tenant-client}

Beachten Sie beim Konfigurieren der Adobe Target Mandanten-ID- und Adobe Target Client Code-Felder Folgendes:

1. Für die meisten Kunden sind die Mandanten-ID und der Clientcode identisch. Das heißt, beide Felder enthalten die gleichen Informationen und sind identisch. Achten Sie darauf, dass Sie die Mandanten-ID in beide Felder eingeben.
2. Sollten Sie über ältere Werte verfügen, können Sie auch verschiedene Werte in die Felder „Mandanten-ID“ und „Clientcode“ eingeben.

In beiden Fällen:

* Standardmäßig wird der Clientcode (wenn er zuerst eingegeben wird) automatisch in das Feld „Mandanten-ID“ kopiert.
* Bei Bedarf können Sie den standardmäßigen Mandanten-ID-Satz ändern.
* Backend-Aufrufe an Target basieren auf der Mandanten-ID und die clientseitigen Aufrufe an Target basieren auf dem Client-Code.

Wie bereits erwähnt, tritt der erste Fall in AEM as a Cloud Service häufiger auf. Stellen Sie in beiden Fällen sicher, dass **beide** Felder die richtigen Informationen entsprechend Ihren Anforderungen enthalten.

>[!NOTE]
>
> Wenn Sie eine bestehende Target-Konfiguration ändern möchten:
>
> 1. Geben Sie die Mandantenkennung erneut ein.
> 2. Stellen Sie eine erneute Verbindung zu Target her.
> 3. Speichern Sie die Konfiguration.

### Bearbeiten der Target-Konfiguration {#edit-target-configuration}

Um die Target-Konfiguration zu deaktivieren, führen Sie die folgenden Schritte aus:

1. Wählen Sie eine vorhandene Konfiguration aus und klicken Sie auf **Eigenschaften**.
2. Bearbeiten Sie die Eigenschaften.
3. Wählen Sie **Erneute Verbindung zu Adobe Target herstellen** aus.
4. Klicken Sie auf **Speichern und schließen**.

### Hinzufügen einer Konfiguration zu einer Site {#add-configuration}

Um eine Konfiguration der Touch-Benutzeroberfläche auf eine Site anzuwenden, gehen Sie zu: **Sites** > **Eine beliebige Site-Seite auswählen** > **Eigenschaften** > **Erweitert** > **Konfiguration** > Wählen Sie den Konfigurationsmandanten aus.

## Integrieren von Adobe Target mit AEM Sites mithilfe von Adobe Experience Platform Launch {#integrate-target-launch}

AEM bietet eine vorkonfigurierte Integration mit Experience Platform Launch. Durch Hinzufügen der Adobe Target-Erweiterung zu Experience Platform Launch können Sie die Funktionen von Adobe Target auf AEM-Web-Seiten verwenden. Target-Bibliotheken werden nur mit Launch gerendert.

>[!NOTE]
>
>Vorhandene (ältere) Frameworks funktionieren weiterhin, können jedoch nicht in der Touch-optimierten Benutzeroberfläche konfiguriert werden. Adobe empfiehlt, die Variablenzuordnungskonfigurationen in Launch neu zu erstellen.

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

**Erweiterungen** sind der Container, der die Einstellungen der Hauptbibliothek verwaltet. Die Adobe Target-Erweiterung unterstützt Client-seitige Implementierungen, indem „at.js“ verwendet wird, das JavaScript-SDK von Target für das moderne Web. Fügen Sie beide **Adobe Target** und **Adobe ContextHub** Erweiterungen.

1. Wählen Sie die Option „Erweiterungskatalog“ aus und suchen Sie im Filter nach Target.
2. Wählen Sie **Adobe Target at.js** aus und klicken Sie auf die Option „Installieren“.
   ![Target-Suche](assets/search_ext1.png "Target-Suche")
3. Klicken Sie auf die Schaltfläche **Konfigurieren**. Beachten Sie das Konfigurationsfenster mit den importierten Target-Anmeldedaten und die at.js-Version für diese Erweiterung.
4. Wählen Sie **Speichern**, um die Target-Erweiterung zur Experience Platform Launch-Eigenschaft hinzuzufügen. Die Target-Erweiterung sollte unter **Installierte Erweiterungen** aufgeführt sein.
   ![Erweiterung speichern](assets/configure_extension1.png "Erweiterung speichern")
5. Wiederholen Sie die obigen Schritte, um nach dem **Adobe ContextHub** Erweiterung erstellen und installieren (diese Erweiterung ist für die Integration mit ContextHub-Parametern erforderlich, je nachdem, auf welcher Basis Targeting durchgeführt wird).

### Erstellen eines Datenelements {#data-element}

**Datenelemente** sind die Platzhalter, denen Sie ContextHub-Parameter zuordnen können.

1. Wählen Sie **Datenelemente**.
2. Wählen Sie **Datenelement hinzufügen** aus.
3. Geben Sie den Namen des Datenelements an und ordnen Sie es einem ContextHub-Parameter zu.
4. Wählen Sie **Speichern** aus.
   ![Datenelement](assets/data_elem1.png "Datenelement")

### Erstellen einer Seitenregel {#page-rule}

In **Regel** definiert und ordnet eine Abfolge von Aktionen an, die auf der Site ausgeführt werden, um Targeting zu erreichen.

1. Fügen Sie eine Reihe Aktionen hinzu, wie im Screenshot dargestellt.
   ![Aktionen](assets/rules1.png "Aktionen")
2. Fügen Sie unter Parameter zu allen Mboxes hinzufügen das zuvor konfigurierte Datenelement (siehe Datenelement oben) zum Parameter hinzu, der im Mbox-Aufruf gesendet wird.
   ![Mbox](assets/map_data1.png "Aktionen")

### Erstellen und Veröffentlichen {#build-publish}

Informationen zum Erstellen und Veröffentlichen finden Sie unter [page](https://experienceleague.adobe.com/docs/experience-manager-learn/aem-target-tutorial/aem-target-implementation/using-launch-adobe-io.html?lang=de).

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
    <td>/conf/tenant/settings/cloudconfigs/target/</td>
    <td> Zuvor waren unter „/etc/cloudservices/testandtarget“ mehrere Konfigurationen vorhanden. Inzwischen ist unter einem Mandanten nur jeweils eine Konfiguration zu finden.</td>
  </tr>
</table>

>[!NOTE]
>
>Alte Konfigurationen werden weiterhin für bestehende Kunden unterstützt (ohne die Option zum Bearbeiten oder Erstellen). Ältere Konfigurationen sind Teil von Inhaltspaketen, die von Kunden mit VSTS hochgeladen werden.
