---
title: Asset-Mikrodienste konfigurieren und verwenden
description: Konfigurieren und verwenden Sie die Cloud-nativen Asset-Mikrodienste, um Assets im Maßstab zu verarbeiten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 3207151a76c51637551907d15a34f1a6b7450d02
workflow-type: tm+mt
source-wordcount: '2511'
ht-degree: 45%

---


# Asset-Mikrodienste und verarbeitende Profil {#get-started-using-asset-microservices} verwenden

Asset-Mikrodienste bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud-nativen Anwendungen (auch als &quot;Arbeiter&quot;bezeichnet). Adobe verwaltet die Dienste für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen.

Mithilfe von Asset-Mikrodiensten können Sie eine [breite Palette von Dateitypen](/help/assets/file-format-support.md) verarbeiten, die mehr vordefinierte Formate abdeckt, als mit früheren Versionen von [!DNL Experience Manager] möglich sind. Beispielsweise ist jetzt das Extrahieren von Miniaturansichten von PSD- und PSB-Formaten möglich, für die zuvor Lösungen von Drittanbietern wie ImageMagick erforderlich waren.

Die Asset-Verarbeitung hängt von der Konfiguration in **[!UICONTROL Verarbeitende Profil]** ab. Experience Manager bietet eine grundlegende Standardeinstellung und ermöglicht es Administratoren, eine spezifischere Asset-Verarbeitungskonfiguration hinzuzufügen. Administratoren erstellen, warten und ändern die Konfigurationen der Workflows nach der Verarbeitung, einschließlich optionaler Anpassungen. Durch Anpassen der Workflows können Entwickler das Standardangebot erweitern.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Eine allgemeine Ansicht der Asset-Verarbeitung](assets/asset-microservices-flow.png "Eine allgemeine Ansicht der Asset-Verarbeitung")

>[!NOTE]
>
>Die hier beschriebene Asset-Verarbeitung ersetzt das Workflow-Modell `DAM Update Asset`, das in früheren Versionen von [!DNL Experience Manager] vorhanden ist. Die meisten Schritte zum Generieren von Standardausgaben und zum Erstellen von Metadaten werden durch die Verarbeitung von Asset-Microservices ersetzt. Die verbleibenden Schritte können, falls vorhanden, durch die Konfiguration des Nacharbeitungs-Workflows ersetzt werden.

## Verstehen Sie die Optionen für die Verarbeitung von Assets {#get-started}

Experience Manager ermöglicht die folgenden Verarbeitungsstufen.

| Option | Beschreibung | Anwendungsfälle |
|---|---|---|
| [Standardkonfiguration](#default-config) | Es ist verfügbar und kann nicht geändert werden. Diese Konfiguration bietet eine sehr einfache Funktion zur Darstellung. | <ul> <li>Standardminiaturen, die von der [!DNL Assets]-Benutzeroberfläche verwendet werden (48, 140 und 319 Pixel) </li> <li> Große Vorschau (Webdarstellung - 1280 Pixel) </li><li> Metadaten und Text-Extraktion.</li></ul> |
| [Benutzerdefinierte Konfiguration](#standard-config) | Von Administratoren über die Benutzeroberfläche konfiguriert. Bietet weitere Optionen für die Generierung von Darstellungen durch Erweitern der Standardoption. Erweitern Sie die vordefinierte Option, um verschiedene Formate und Darstellungen bereitzustellen. | <ul><li>FPO-Darstellung. </li> <li>Dateiformat und Auflösung von Bildern ändern</li> <li> Bedingt auf konfigurierte Dateitypen anwenden. </li> </ul> |
| [Benutzerdefiniertes Profil](#custom-config) | Konfiguriert von Administratoren über die Benutzeroberfläche, um benutzerdefinierten Code über benutzerdefinierte Anwendungen zum Aufrufen von [Asset compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html) zu verwenden. Unterstützt komplexere Anforderungen in einer Cloud-nativen und skalierbaren Methode. | Siehe [Zulässige Anwendungsfälle](#custom-config). |

<!-- To create custom processing profiles specific to your custom requirements, say to integrate with other systems, see [post-processing workflows](#post-processing-workflows).
-->

## Unterstützte Dateiformate {#supported-file-formats}

Asset Microservices bieten Unterstützung für eine Vielzahl von Dateiformaten, um Metadaten zu verarbeiten, zu generieren oder zu extrahieren. Die vollständige Liste der MIME-Typen und die für jeden Typ unterstützten Funktionen finden Sie unter [Unterstützte Dateiformate](file-format-support.md).

## Standardkonfiguration {#default-config}

Einige Standardwerte sind vorkonfiguriert, um sicherzustellen, dass die in Experience Manager erforderlichen Standarddarstellungen verfügbar sind. Die Standardkonfiguration stellt außerdem sicher, dass die Vorgänge zur Extraktion und Extraktion von Metadaten verfügbar sind. Benutzer können sofort mit dem Hochladen oder Aktualisieren von Assets beginnen. Die grundlegende Verarbeitung ist standardmäßig verfügbar.

Bei der Standardkonfiguration wird nur das grundlegendste verarbeitende Profil konfiguriert. Ein solches Profil ist auf der Benutzeroberfläche nicht sichtbar und Sie können es nicht ändern. Es wird immer ausgeführt, um hochgeladene Assets zu verarbeiten. Ein solches standardmäßiges Profil zur Verarbeitung stellt sicher, dass die grundlegende Verarbeitung, die für [!DNL Experience Manager] erforderlich ist, für alle Assets abgeschlossen ist.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## Standardkonfiguration {#standard-config}

[!DNL Experience Manager] bietet Funktionen zum Generieren speziellerer Darstellungen für gängige Formate gemäß den Anforderungen des Benutzers. Ein Administrator kann weitere [!UICONTROL Verarbeitungsvariablen ] erstellen, um die Erstellung solcher Profil zu erleichtern. Die Benutzer weisen dann einem oder mehreren der verfügbaren Profil bestimmten Ordnern zu, um die zusätzliche Verarbeitung abzuschließen. Beispielsweise kann die zusätzliche Verarbeitung Darstellungen für Web, Mobil und Tablet generieren. Das folgende Video zeigt, wie Sie [!UICONTROL Verarbeitungsprofile] erstellen und anwenden und auf die erstellten Ausgabeformate zugreifen.

* **Darstellungsbreite und -höhe**: Die Angabe der Breite und Höhe der Darstellung bietet die maximale Größe des generierten Ausgabebilds. Asset Microservices versucht, die größtmögliche Darstellung zu erstellen, deren Breite und Höhe nicht größer als die angegebene Breite bzw. Höhe ist. Das Seitenverhältnis wird beibehalten, d. h. es entspricht dem Original. Ein leerer Wert bedeutet, dass bei der Asset-Verarbeitung die Pixelabmessungen des Originals berücksichtigt werden.

* **MIME-Typeinschlussregeln**: Wenn ein Asset mit einem bestimmten MIME-Typ verarbeitet wird, wird der MIME-Typ zunächst mit dem ausgeschlossenen MIME-Typwert für die Darstellungsspezifikation verglichen. Wenn es mit dieser Liste übereinstimmt, wird dieses spezifische Ausgabeformat nicht für das Asset generiert (Blockierungsliste). Andernfalls wird der Mime-Typ mit dem eingeschlossenen Mime-Typ verglichen. Wenn er mit der Liste übereinstimmt, wird das Ausgabeformat generiert (Zulassungsliste).

* **Spezielle FPO-Darstellung**: Beim Platzieren großer Assets aus  [!DNL Experience Manager] in  [!DNL Adobe InDesign] Dokumente wartet ein Kreativprofi eine Weile, nachdem er ein Asset  [platziert](https://helpx.adobe.com/de/indesign/using/placing-graphics.html) hat. Inzwischen wird der Benutzer daran gehindert, [!DNL InDesign] zu verwenden. Dies unterbricht den kreativen Fluss und wirkt sich negativ auf das Kundenerlebnis aus. Mit der Adobe können kleinere Darstellungen in [!DNL InDesign]-Dokumenten vorübergehend platziert werden. Diese können später durch Assets mit voller Auflösung bei Bedarf ersetzt werden. [!DNL Experience Manager] bietet Ausgabeversionen, die nur für die Platzierung (FPO) verwendet werden. Diese FPO-Darstellungen haben eine kleine Dateigröße, weisen aber dasselbe Seitenverhältnis auf.

Das Verarbeitungsprofil kann eine FPO-Wiedergabe (nur für Platzierung) enthalten. In der -[!DNL Adobe Asset Link][Dokumentation](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) erfahren Sie, ob Sie das Programm für Ihr Verarbeitungsprofil aktivieren müssen. Weitere Informationen finden Sie in der [vollständigen Dokumentation von Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html).

### Standardmäßige Profil {#create-standard-profile} erstellen

Gehen Sie wie folgt vor, um ein Profil für die Standardverarbeitung zu erstellen:

1. Administratoren greifen auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Profil für die Verarbeitung]** zu. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Namen ein, der Ihnen beim Anwenden auf einen Ordner hilft, das Profil eindeutig zu identifizieren.
1. Um FPO-Darstellungen zu generieren, aktivieren Sie auf der Registerkarte **[!UICONTROL Standard]** die Option **[!UICONTROL FPO-Darstellung erstellen]**. Geben Sie einen Wert zwischen 1 und 100 ein.****
1. Um andere Darstellungen zu erstellen, klicken Sie auf **[!UICONTROL Hinzufügen Neu]** und geben Sie die folgenden Informationen ein:

   * Dateiname jeder Darstellung.
   * Dateiformat (PNG, JPEG, GIF oder WebP) jeder Darstellung.
   * Breite und Höhe der einzelnen Darstellungen in Pixel. Wenn die Werte nicht angegeben werden, wird die vollständige Pixelgröße des Originalbilds verwendet.
   * Qualität in Prozent jeder JPEG- und WebP-Darstellung.
   * Eingeschlossene und ausgeschlossene MIME-Typen zur Definition der Anwendbarkeit eines Profils.

   ![processing-profiles-adding](assets/processing-profiles-image.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

<!-- TBD: Update the video link when a new video is available from Tech Marketing.

The following video demonstrates the usefulness and usage of standard profile.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)
-->

<!-- This image was removed per cqdoc-15624, as requested by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) 
 -->

## Benutzerspezifisches Profil und Anwendungsfälle {#custom-config}

Das [!DNL Asset Compute Service] unterstützt eine Vielzahl von Anwendungsfällen, z. B. die Standardverarbeitung, die Verarbeitung von Adoben-spezifischen Formaten wie Photoshop-Dateien und die Implementierung einer benutzerdefinierten oder organisationsspezifischen Verarbeitung. Die zuvor erforderliche Anpassung des DAM Update Asset-Workflows wird entweder automatisch oder über die Konfiguration der verarbeitenden Profil durchgeführt. Wenn die Geschäftsanforderungen von diesen Verarbeitungsoptionen nicht erfüllt werden, empfiehlt Adobe die Entwicklung und Erweiterung der Standardfunktionen mit [!DNL Asset Compute Service]. Eine Übersicht finden Sie unter [Erweiterbarkeit und Verwendungszeitpunkt](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung einer benutzerdefinierten Anwendung nur dann, wenn die Geschäftsanforderungen nicht mit den Standardkonfigurationen oder dem Standard-Profil erfüllt werden können.

Sie können Bild-, Video-, Dokument- und andere Dateiformate in verschiedene Ausgabedarstellungen umwandeln, einschließlich Miniaturansichten, extrahiertem Text und Metadaten sowie Archiven.

Entwickler können die [!DNL Asset Compute Service] verwenden, um [benutzerdefinierte Anwendungen](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html) zu erstellen, die den unterstützten Anwendungsfällen entsprechen. [!DNL Experience Manager] Sie können diese benutzerdefinierten Anwendungen über die Benutzeroberfläche aufrufen, indem Sie benutzerdefinierte Profil verwenden, die Administratoren konfigurieren. [!DNL Asset Compute Service] unterstützt die folgenden Anwendungsfälle beim Aufrufen externer Dienste:

* Verwenden Sie [!DNL Adobe Photoshop] [ImageCutout-API](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#imagecutout) und speichern Sie das Ergebnis als Darstellung.
* Rufen Sie Drittanbietersysteme auf, um Daten zu aktualisieren, z. B. ein PIM-System.
* Verwenden Sie die [!DNL Photoshop]-API, um verschiedene Darstellungen basierend auf der Photoshop-Vorlage zu generieren.
* Verwenden Sie [Adobe Lightroom API](https://github.com/AdobeDocs/lightroom-api-docs#supported-features), um die erfassten Assets zu optimieren und diese als Darstellungen zu speichern.

>[!NOTE]
>
>Sie können die Standardmetadaten nicht mit den benutzerdefinierten Anwendungen bearbeiten. Sie können nur benutzerdefinierte Metadaten ändern.

### Benutzerdefiniertes Profil {#create-custom-profile} erstellen

Gehen Sie wie folgt vor, um ein benutzerdefiniertes Profil zu erstellen:

1. Administratoren greifen auf **[!UICONTROL Tools > Assets > Processing Profils]** zu. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Benutzerdefiniert]**. Klicken Sie auf **[!UICONTROL Hinzufügen Neu]**. Geben Sie den gewünschten Dateinamen der Darstellung ein.
1. Geben Sie die folgenden Informationen ein.

   * Dateiname jeder Darstellung und eine unterstützte Dateierweiterung.
   * [Endpunkt-URL einer benutzerdefinierten Firefly-App](https://experienceleague.adobe.com/docs/asset-compute/using/extend/deploy-custom-application.html). Die App muss aus demselben Unternehmen stammen wie das Experience Manager-Konto.
   * hinzufügen Serviceparameter an [Übergeben zusätzliche Informationen oder Parameter an die benutzerdefinierte Anwendung](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html#extend).
   * MIME-Typen wurden eingeschlossen und ausgeschlossen, um die Verarbeitung auf einige bestimmte Dateiformate zu beschränken.

   Klicken Sie auf **[!UICONTROL Speichern]**.

Bei den benutzerdefinierten Anwendungen handelt es sich um Headless-[Project Firefly](https://github.com/AdobeDocs/project-firefly)-Apps. Die benutzerdefinierte Anwendung ruft alle angegebenen Dateien ab, wenn sie mit einem verarbeitenden Profil eingerichtet wurden. Die Anwendung muss die Dateien filtern.

>[!CAUTION]
>
>Wenn die Firefly-App und das [!DNL Experience Manager]-Konto nicht aus demselben Unternehmen stammen, funktioniert die Integration nicht.

### Beispiel für ein benutzerdefiniertes Profil {#custom-profile-example}

Zur Veranschaulichung der Verwendung von benutzerdefiniertem Profil sollten wir einen Verwendungsfall erwägen, um Kampagnen mit benutzerdefiniertem Text zu versehen. Sie können ein verarbeitendes Profil erstellen, das die Photoshop-API zum Bearbeiten der Bilder nutzt.

Mit der asset compute Service-Integration kann Experience Manager diese Parameter mithilfe des Felds [!UICONTROL Dienstparameter] an die benutzerdefinierte Anwendung übergeben. Die benutzerdefinierte Anwendung ruft dann die Photoshop API auf und übergibt diese Werte an die API. Sie können beispielsweise Schriftartnamen, Textfarbe, Gewichtung und Textgröße übergeben, um den benutzerdefinierten Text den Kampagnen hinzuzufügen.

![custom-processing-Profil](assets/custom-processing-profile.png)

*Abbildung: Verwenden Sie  [!UICONTROL das ] Feld &quot;Dienstparameter&quot;, um zusätzliche Informationen an vordefinierte Parameter zu übergeben, die in der benutzerdefinierten Anwendung erstellt wurden. In diesem Beispiel werden beim Hochladen von Kampagnen die Bilder mit `Jumanji`-Text in `Arial-BoldMT`-Schrift aktualisiert.*

## Verwenden Sie verarbeitende Profil zur Verarbeitung von Elementen {#use-profiles}

Erstellen Sie die zusätzlichen benutzerdefinierten Verarbeitungsprofile und wenden Sie sie auf bestimmte Ordner an, damit Experience Manager sie für Assets verarbeitet, die in diese Ordner hochgeladen oder in diesen aktualisiert wurden. Das standardmäßige integrierte Verarbeitungsprofil wird immer ausgeführt, ist jedoch auf der Benutzeroberfläche nicht sichtbar. Wenn Sie ein benutzerdefiniertes Profil hinzufügen, werden beide Profil zur Verarbeitung der hochgeladenen Assets verwendet.

Verwenden Sie eine der folgenden Methoden, um Verarbeitungsprofile auf Ordner anzuwenden:

* Administratoren können unter **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Profil für die Verarbeitung]** eine Definition für verarbeitende Profil auswählen und die Aktion **[!UICONTROL Profil auf Ordner(s)]** anwenden. Dadurch wird ein Inhalts-Browser geöffnet, mit dem Sie zu bestimmten Ordnern navigieren, diese auswählen und die Anwendung des Profils bestätigen können.
* Die Benutzer können einen Ordner in der Benutzeroberfläche &quot;Assets&quot;auswählen, mit der Aktion **[!UICONTROL Properties]** den Bildschirm &quot;Ordnereigenschaften&quot;öffnen, auf die Registerkarte **[!UICONTROL Processing Profils]** klicken und in der Popup-Liste das entsprechende Profil für die Verarbeitung für diesen Ordner auswählen. Klicken Sie auf **[!UICONTROL Speichern &amp; Schließen]**, um die Änderungen zu speichern.
   ![Anwenden des Verarbeitungs-Profils auf einen Ordner auf der Registerkarte &quot;Asset-Eigenschaften&quot;](assets/folder-properties-processing-profile.png)

>[!TIP]
>
>Es kann nur ein verarbeitendes Profil auf einen Ordner angewendet werden. Um weitere Ausgabedarstellungen zu generieren, fügen Sie dem bestehenden Verarbeitungsprofil weitere Darstellungsdefinitionen hinzu.

Nachdem ein Verarbeitungsprofil auf einen Ordner angewendet wurde, werden alle neuen Assets, die in diesen Ordner oder in dessen Unterordnern hochgeladen (oder aktualisiert) werden, mit dem konfigurierten zusätzlichen Verarbeitungsprofil verarbeitet. Diese Verarbeitung erfolgt zusätzlich zum Standardprofil.

>[!NOTE]
>
>Ein Verarbeitungsprofil, das auf einen Ordner angewendet wird, funktioniert für die gesamte Struktur, kann aber mit einem anderen Profil überschrieben werden, das auf einen Unterordner angewendet wird. Wenn Assets in einen Ordner hochgeladen werden, prüft Experience Manager die Eigenschaften des zugehörigen Ordners auf ein Verarbeitungsprofil. Wenn nichts angewendet wird, wird in einem übergeordneten Ordner in der Hierarchie geprüft, ob ein Verarbeitungsprofil angewendet werden soll.

Um sicherzustellen, dass Assets verarbeitet werden, müssen Sie die generierten Darstellungen in der Ansicht [!UICONTROL Ausgabeformate] in der linken Leiste Vorschau haben. Öffnen Sie die Asset-Vorschau und öffnen Sie die linke Leiste, um auf die Ansicht **[!UICONTROL Ausgabeformate]** zuzugreifen. Die spezifischen Ausgabeformate im Verarbeitungsprofil, für die der Typ des jeweiligen Assets mit den Einschlussregeln des MIME-Typs übereinstimmt, sollten sichtbar und zugänglich sein.

![Zusätzliche-Ausgabedarstellungen](assets/renditions-additional-renditions.png)

*Abbildung: Beispiel zweier zusätzlicher Ausgabedarstellungen, die von einem Verarbeitungsprofil generiert wurden, das auf den übergeordneten Ordner angewendet wurde.*

## Nachbearbeitungs-Workflows {#post-processing-workflows}

In Fällen, in denen zusätzliche Verarbeitung von Assets erforderlich ist, die mit den Verarbeitungsprofilen nicht erreicht werden können, können der Konfiguration zusätzliche Nachbearbeitungs-Workflows hinzugefügt werden. Dies ermöglicht es, zusätzlich zu der konfigurierbaren Verarbeitung mithilfe von Asset-Microservices eine vollständig angepasste Verarbeitung hinzuzufügen.

Workflows werden, sofern konfiguriert, nach Abschluss der Verarbeitung von microservices automatisch von [!DNL Experience Manager] ausgeführt. Es ist nicht notwendig, Workflow-Starter manuell hinzuzufügen, um sie auszulösen. Zu den Beispielen gehören:

* Benutzerdefinierte Workflow-Schritte zur Verarbeitung von Assets.
* Integrationen, um Assets von externen Systemen Metadaten oder Eigenschaften hinzuzufügen, z. B. Produkt- oder Prozessinformationen.
* Zusätzliche Verarbeitung durch externe Dienste.

Das Hinzufügen einer Workflow-Konfiguration für die Nachbearbeitung zu Experience Manager umfasst die folgenden Schritte:

* Erstellen eines oder mehrerer Workflow-Modelle. In den Dokumenten wird dies als *Workflow-Modelle für die Nachbearbeitung* erwähnt, bei denen es sich jedoch um normale Workflow-Modelle für Experience Manager handelt.
* Hinzufügen spezifischer Workflow-Schritte zu diesen Modellen. Die Schritte werden basierend auf einer Workflow-Modellkonfiguration für die Assets ausgeführt.
* Fügen Sie am Ende den Schritt [!UICONTROL Abgeschlosser Prozess zum DAM-Workflow eines Asset-Updates] hinzu. Durch Hinzufügen dieses Schritts wird sichergestellt, dass Experience Manager weiß, wann die Verarbeitung abgeschlossen ist, und das Asset als verarbeitet markiert werden kann, d. h., dass beim Asset der Wert *Neu* angezeigt wird.
* Erstellen Sie eine Konfiguration für den Custom Workflow Runner Service, mit der die Ausführung eines Nachbearbeitungs-Workflow-Modells entweder nach Pfad (Speicherort für Ordner) oder nach regulären Ausdrücken konfiguriert werden kann.

### Erstellen von Nachbearbeitungs-Workflow-Modellen {#create-post-processing-workflow-models}

Nachbearbeitungs-Workflow-Modelle sind normale [!DNL Experience Manager] Workflow-Modelle. Erstellen Sie verschiedene Modelle, wenn Sie für verschiedene Repository-Standorte oder Asset-Typen eine unterschiedliche Verarbeitung benötigen.

Verarbeitungsschritte sollten je nach Bedarf hinzugefügt werden. Sie können alle verfügbaren unterstützten Schritte sowie alle benutzerdefinierten Workflow-Schritte verwenden.

Stellen Sie sicher, dass der letzte Schritt jedes Nachbearbeitungs-Workflows `DAM Update Asset Workflow Completed Process` ist. Der letzte Schritt stellt sicher, dass Experience Manager weiß, wann die Asset-Verarbeitung abgeschlossen ist.

### Konfigurieren der Ausführung von Nachbearbeitungs-Workflows {#configure-post-processing-workflow-execution}

Um die Nachbearbeitungs-Workflow-Modelle zu konfigurieren, die für Assets ausgeführt werden sollen, die nach Abschluss der Verarbeitung der Asset-Microservices in das System hochgeladen oder aktualisiert werden, muss der Custom Workflow Runner-Dienst konfiguriert werden.

Der Custom Workflow Runner Service (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) ist ein OSGi-Dienst und bietet zwei Konfigurationsoptionen:

* Nachbearbeitungs-Workflows nach Pfad (`postProcWorkflowsByPath`): Es können mehrere Workflow-Modelle basierend auf unterschiedlichen Repository-Pfaden aufgeführt werden. Pfade und Modelle sollten durch einen Doppelpunkt voneinander getrennt werden. Einfache Repository-Pfade werden unterstützt und sollten einem Workflow-Modell im `/var`-Pfad zugeordnet werden. Beispiel: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* Nachbearbeitungs-Workflows nach Ausdruck (`postProcWorkflowsByExpression`): Es können mehrere Workflow-Modelle basierend auf unterschiedlichen regulären Ausdrücken aufgelistet werden. Ausdrücke und Modelle sollten durch einen Doppelpunkt getrennt werden. Der reguläre Ausdruck sollte direkt auf den Asset-Knoten verweisen und nicht auf eine der Ausgaben oder Dateien. Beispiel: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>Die Konfiguration von Custom Workflow Runner ist eine Konfiguration eines OSGi-Dienstes. Informationen zum Bereitstellen einer OSGi-Konfiguration finden Sie unter [Bereitstellung in Experience Manager](/help/implementing/deploying/overview.md).
>OSGi-Webkonsole ist im Gegensatz zu lokalen und verwalteten Dienstbereitstellungen von [!DNL Experience Manager] nicht direkt in den Cloud-Dienstbereitstellungen verfügbar.

Weitere Informationen dazu, welcher standardmäßige Workflow-Schritt im Nachbearbeitungs-Workflow verwendet werden kann, finden Sie unter [Workflow-Schritte im Nachbearbeitungs-Workflow](developer-reference-material-apis.md#post-processing-workflows-steps) in der Entwicklerreferenz.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Berücksichtigen Sie beim Entwickeln von Workflows Ihre Anforderungen für alle Arten von Ausgabedarstellungen. Wenn Sie der Meinung sind, dass eine Ausgabedarstellung in Zukunft nicht erforderlich sein wird, entfernen Sie den Erstellungsschritt aus dem Workflow. Ausgabedarstellungen können später nicht mehr stapelweise gelöscht werden. Unerwünschte Ausgabedarstellungen können nach längerer Nutzung von [!DNL Experience Manager] viel Speicherplatz beanspruchen. Bei einzelnen Assets können Sie Ausgabedarstellungen manuell aus der Benutzeroberfläche entfernen. Bei mehreren Assets können Sie [!DNL Experience Manager] so anpassen, dass entweder bestimmte Ausgabedarstellungen gelöscht oder die Assets gelöscht und die gelöschten Assets erneut hochgeladen werden.
* Derzeit ist die Unterstützung auf das Generieren von Darstellungen beschränkt. Das Generieren neuer Assets wird nicht unterstützt.

>[!MORELIKETHIS]
>
>* [Einführung in den Asset compute-Dienst](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html).
>* [Verstehen Sie die Erweiterbarkeit und wann sie](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html) verwendet werden soll.
>* [Erstellen benutzerdefinierter Anwendungen](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html).
>* [Unterstützte MIME-Typen für verschiedene Anwendungsfälle](/help/assets/file-format-support.md).


<!-- TBD: 
* How/where can admins check what's already configured and provisioned.
* How/where to request for new provisioning/purchase.
-->
