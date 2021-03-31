---
title: Asset-Microservices konfigurieren und verwenden
description: Konfigurieren und verwenden Sie die Cloud-nativen Asset-Microservices, um Assets mit hoher Skalierung zu verarbeiten.
contentOwner: AG
feature: asset compute-Mikrodienste, Workflow, Asset-Verarbeitung
role: Architekt, Administrator
translation-type: tm+mt
source-git-commit: 8093f6cec446223af58515fd8c91afa5940f9402
workflow-type: tm+mt
source-wordcount: '2584'
ht-degree: 99%

---


# Asset-Microservices und Verarbeitungsprofile verwenden {#get-started-using-asset-microservices}

Asset-Microservices erlauben eine skalierbare und zuverlässige Verarbeitung von Assets mithilfe von Cloud-nativen Programmen (auch als „sekundäre Programme“ bezeichnet). Adobe verwaltet die Service für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen.

Mit Asset-Microservices können Sie eine [breite Palette von Dateitypen](/help/assets/file-format-support.md) verarbeiten, die mehr Formate standardmäßig abdecken, als dies mit früheren Versionen von [!DNL Experience Manager] möglich war. Beispielsweise ist jetzt das Extrahieren von Miniaturansichten von PSD- und PSB-Formaten möglich, für die zuvor Lösungen von Drittanbietern wie ImageMagick erforderlich waren.

Die Asset-Verarbeitung hängt von der Konfiguration in **[!UICONTROL Verarbeitungsprofilen]** ab. Experience Manager bietet eine einfache Standardeinrichtung und ermöglicht es Administratoren, spezifischere Asset-Verarbeitungskonfigurationen hinzuzufügen. Administratoren können die Konfigurationen von Nachbearbeitungs-Workflows erstellen, verwalten und ändern, einschließlich optionaler Anpassungen. Durch Anpassen der Workflows können Entwickler das Standardangebot erweitern.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Eine allgemeine Ansicht der Asset-Verarbeitung](assets/asset-microservices-flow.png "Eine allgemeine Ansicht der Asset-Verarbeitung")

>[!NOTE]
>
>Die hier beschriebene Asset-Verarbeitung ersetzt das `DAM Update Asset`-Workflow-Modell, das in früheren Versionen von [!DNL Experience Manager] verwendet wurde. Die meisten Schritte zum Generieren von Standardausgabedarstellungen und zum Erstellen von Metadaten werden durch die Verarbeitung von Asset-Microservices ersetzt. Die verbleibenden Schritte können, falls vorhanden, durch die Konfiguration des Nachverarbeitungs-Workflows ersetzt werden.

## Optionen zur Asset-Verarbeitung verstehen {#get-started}

Experience Manager unterstützt die folgenden Verarbeitungsstufen.

| Option | Beschreibung | Anwendungsfälle |
|---|---|---|
| [Standardkonfiguration](#default-config) | Sie ist im Istzustand verfügbar und kann nicht geändert werden. Diese Konfiguration bietet eine sehr einfache Funktion zur Erstellung von Ausgabedarstellungen. | <ul> <li>Standardmäßige Miniaturansichten, die von der [!DNL Assets]-Benutzeroberfläche verwendet werden (48, 140 und 319 Pixel) </li> <li> Große Vorschau (Web-Ausgabedarstellung – 1.280 Pixel) </li><li> Metadaten und Textextraktion.</li></ul> |
| [Benutzerdefinierte Konfiguration](#standard-config) | Von Administratoren über die Benutzeroberfläche konfiguriert. Bietet weitere Optionen für die Generierung von Ausgabedarstellungen durch Erweitern der Standardoption. Erweitert die vordefinierte Option, um verschiedene Formate und Ausgabedarstellungen bereitzustellen. | <ul><li>FPO-Ausgabedarstellung. </li> <li>Dateiformat und Auflösung von Bildern ändern</li> <li> Bedingte Anwendung auf konfigurierte Dateitypen. </li> </ul> |
| [Benutzerdefiniertes Profil](#custom-config) | Von Administratoren über die Benutzeroberfläche konfiguriert, um benutzerdefinierten Code über benutzerdefinierte Programme zum Aufrufen des [Asset Compute-Service](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html?lang=de) zu verwenden. Unterstützt komplexere Anforderungen in einer Cloud-nativen und skalierbaren Methode. | Siehe [Zulässige Anwendungsfälle](#custom-config). |

<!-- To create custom processing profiles specific to your custom requirements, say to integrate with other systems, see [post-processing workflows](#post-processing-workflows).
-->

## Unterstützte Dateiformate {#supported-file-formats}

Asset-Microservices bieten Unterstützung für eine Vielzahl von Dateiformaten, um Daten zu verarbeiten, Ausgabedarstellungen zu generieren oder Metadaten zu extrahieren. Unter [Unterstützte Dateiformate](file-format-support.md) finden Sie eine vollständige Liste der MIME-Typen und der jeweils unterstützten Funktionen.

## Standardkonfiguration {#default-config}

Einige Standardwerte sind vorkonfiguriert, um sicherzustellen, dass die in Experience Manager erforderlichen Standardausgabedarstellungen verfügbar sind. Außerdem stellt die Standardkonfiguration sicher, dass Metadatenextraktion und Textextraktion verfügbar sind. Benutzer können sofort mit dem Hochladen oder Aktualisieren von Assets beginnen. Die grundlegende Verarbeitung ist standardmäßig verfügbar.

Bei der Standardkonfiguration wird nur das einfachste Verarbeitungsprofil konfiguriert. Solch ein Verarbeitungsprofil ist in der Benutzeroberfläche nicht sichtbar und kann nicht geändert werden. Es wird immer ausgeführt, um hochgeladene Assets zu verarbeiten. Mit einem standardmäßigen Verarbeitungsprofil wird sichergestellt, dass die von [!DNL Experience Manager] benötigte grundlegende Verarbeitung für alle Assets durchgeführt wird.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## Standardkonfiguration {#standard-config}

[!DNL Experience Manager] bietet Funktionen zum Generieren spezifischerer Ausgabedarstellungen für gängige Formate gemäß den Anforderungen des Benutzers. Ein Administrator kann zusätzliche [!UICONTROL Verarbeitungsprofile] anlegen, um die Erstellung solcher Ausgabedarstellungen zu erleichtern. Benutzer können dann eines oder mehrere der verfügbaren Profile bestimmten Ordnern zuweisen, um die zusätzliche Verarbeitung zu erhalten. Beispielsweise kann die zusätzliche Verarbeitung Ausgabedarstellungen für Web, Smartphone und Tablet generieren. Das folgende Video zeigt, wie Sie [!UICONTROL Verarbeitungsprofile] erstellen und anwenden und auf die erstellten Ausgabedarstellungen zugreifen.

* **Breite und Höhe der Ausgabedarstellung**: Eine Angabe der Breite und Höhe der Ausgabedarstellung sorgt für die maximale Größe des generierten Ausgabebilds. Asset-Microservices versuchen, die größtmögliche Ausgabedarstellung zu erstellen, dessen Breite und Höhe nicht größer als die angegebene Breite bzw. Höhe sind. Das Seitenverhältnis wird beibehalten, d. h. es entspricht dem Original. Ein leerer Wert bedeutet, dass bei der Asset-Verarbeitung die Pixelabmessungen des Originals berücksichtigt werden.

* **Einschlussregeln für MIME-Typen**: Wenn ein Asset mit einem bestimmten MIME-Typ verarbeitet wird, wird der MIME-Typ zunächst mit dem Wert für die ausgeschlossenen MIME-Typen für die Ausgabespezifikation verglichen. Wenn er mit dieser Liste übereinstimmt, wird diese spezifische Ausgabedarstellung nicht für das Asset generiert (Blockierungsliste). Andernfalls wird der MIME-Typ mit dem eingeschlossenen MIME-Typ verglichen. Wenn er mit der Liste übereinstimmt, wird die Ausgabedarstellung generiert (Zulassungsliste).

* **Spezielle FPO-Ausgabedarstellung**: Beim Platzieren großer Assets aus [!DNL Experience Manager] in [!DNL Adobe InDesign]-Dokumenten muss ein Kreativprofi eine ganze Weile warten, nachdem er [ein Asset platziert](https://helpx.adobe.com/de/indesign/using/placing-graphics.html) hat. In der Zwischenzeit kann der Benutzer [!DNL InDesign] nicht verwenden. Dies unterbricht den kreativen Fluss und wirkt sich negativ auf das Kundenerlebnis aus. Adobe ermöglicht die zeitweilige Platzierung kleinformatiger Ausgabedarstellungen in [!DNL InDesign]-Dokumenten. Diese können später bei Assets On-demand in voller Auflösung ersetzt werden. [!DNL Experience Manager] bietet Ausgabedarstellungen, die nur für die Platzierung verwendet werden (FPO). Diese FPO-Ausgabedarstellungen haben eine kleine Dateigröße, weisen aber dasselbe Seitenverhältnis auf.

Das Verarbeitungsprofil kann eine FPO-Ausgabedarstellung (nur für Platzierung) enthalten. In der [!DNL Adobe Asset Link] [Dokumentation](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) erfahren Sie, ob Sie es für Ihr Verarbeitungsprofil aktivieren müssen. Weitere Informationen finden Sie in der [vollständigen Dokumentation von Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html).

### Erstellen eines Standardprofils {#create-standard-profile}

Gehen Sie wie folgt vor, um ein Standardverarbeitungsprofil zu erstellen:

1. Administratoren greifen auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Verarbeitungsprofile]** zu. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Namen ein, der Ihnen hilft, das Profil beim Anwenden auf einen Ordner eindeutig zu identifizieren.
1. Um FPO-Ausgabedarstellungen zu erstellen, aktivieren Sie auf der Registerkarte **[!UICONTROL Standard]** die Option **[!UICONTROL FPO-Ausgabedarstellung erstellen]**. Geben Sie einen Wert für **[!UICONTROL Qualität]** zwischen 1 und 100 ein.
1. Um andere Ausgabedarstellungen zu erstellen, klicken Sie auf **[!UICONTROL Neu hinzufügen]** und geben Sie die folgenden Informationen ein:

   * Dateiname der jeweiligen Ausgabedarstellung.
   * Dateiformat (PNG, JPEG, GIF oder WebP) der jeweiligen Ausgabedarstellung.
   * Breite und Höhe der jeweiligen Ausgabedarstellung in Pixel. Wenn nichts angegeben wird, wird die volle Pixelgröße des Originalbilds verwendet.
   * Qualität in Prozent der jeweiligen JPEG- und WebP-Ausgabedarstellung.
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

## Benutzerdefiniertes Profil und Anwendungsfälle {#custom-config}

Der [!DNL Asset Compute Service] unterstützt eine Vielzahl von Anwendungsfällen, z. B. Standardverarbeitung, Verarbeitung von Adobe-spezifischen Formaten wie Photoshop-Dateien und Implementierung benutzerdefinierter oder unternehmensspezifischer Verarbeitungsformate. Die zuvor erforderliche Anpassung des DAM Update Asset-Workflows wird entweder automatisch oder über die Konfiguration von Verarbeitungsprofilen vorgenommen. Wenn diese Verarbeitungsoptionen geschäftlichen Anforderungen nicht gerecht werden, empfiehlt Adobe, die Standardfunktionen mit [!DNL Asset Compute Service] zu entwickeln und zu erweitern. Einen Überblick finden Sie unter [Erweiterbarkeit und Verwendungszeitpunkt](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html?lang=de).

>[!NOTE]
>
>Adobe empfiehlt die Verwendung eines benutzerdefinierten Programms nur dann, wenn die Geschäftsanforderungen mit den Standardkonfigurationen oder dem Standardprofil nicht erfüllt werden können.

Sie können Bild-, Video-, Dokument- und andere Dateiformate in verschiedene Ausgabedarstellungen umwandeln, einschließlich Miniaturansichten, extrahiertem Text und Metadaten sowie Archiven.

Entwickler können den [!DNL Asset Compute Service] verwenden, um [benutzerdefinierte Programme](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html?lang=de) für die unterstützten Anwendungsfälle zu erstellen. [!DNL Experience Manager] kann diese benutzerdefinierten Programme über die Benutzeroberfläche aufrufen, indem benutzerdefinierte Profile verwendet werden, die Administratoren konfigurieren. [!DNL Asset Compute Service] unterstützt die folgenden Anwendungsfälle beim Aufrufen externer Services:

* Verwenden Sie die [ImageCutout-API](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#imagecutout) von [!DNL Adobe Photoshop] und speichern Sie das Ergebnis als Ausgabedarstellung.
* Rufen Sie Drittanbietersysteme auf, um Daten zu aktualisieren, z. B. ein PIM-System.
* Verwenden Sie die [!DNL Photoshop]-API, um basierend auf der Photoshop-Vorlage verschiedene Ausgabedarstellungen zu erstellen.
* Verwenden Sie die [Adobe Lightroom-API](https://github.com/AdobeDocs/lightroom-api-docs#supported-features), um die erfassten Assets zu optimieren und als Ausgabedarstellungen zu speichern.

>[!NOTE]
>
>Sie können Standardmetadaten nicht mit den benutzerdefinierten Programmen bearbeiten. Sie können nur benutzerdefinierte Metadaten ändern.

### Benutzerdefiniertes Profil erstellen {#create-custom-profile}

Gehen Sie wie folgt vor, um ein benutzerdefiniertes Profil zu erstellen:

1. Administratoren greifen auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Verarbeitungsprofile]** zu. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Benutzerdefiniert]**. Klicken Sie auf **[!UICONTROL Neu hinzufügen]**. Geben Sie den gewünschten Dateinamen der Ausgabedarstellung ein.
1. Geben Sie die folgenden Informationen ein.

   * Dateiname der jeweiligen Ausgabedarstellung und eine unterstützte Dateierweiterung.
   * [Endpunkt-URL einer benutzerdefinierten Firefly-Mobile-App](https://experienceleague.adobe.com/docs/asset-compute/using/extend/deploy-custom-application.html?lang=de). Die Mobile App muss aus derselben Organisation stammen wie das Experience Manager-Konto.
   * Fügen Sie Service-Parameter hinzu, um [zusätzliche Informationen oder Parameter an das benutzerdefinierte Programm zu übergeben](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html?lang=de#extend).
   * Schließen Sie MIME-Typen ein und aus, um die Verarbeitung auf einige bestimmte Dateiformate zu beschränken.

   Klicken Sie auf **[!UICONTROL Speichern]**.

Bei den benutzerdefinierten Programmen handelt es sich um Headless-[Project Firefly](https://github.com/AdobeDocs/project-firefly)-Mobile-Apps. Das benutzerdefinierte Programm erhält alle angegebenen Dateien, wenn sie mit einem Verarbeitungsprofil eingerichtet wurden. Das Programm muss die Dateien filtern.

>[!CAUTION]
>
>Wenn die Firefly-Mobile-App und das [!DNL Experience Manager]-Konto nicht aus derselben Organisation stammen, funktioniert die Integration nicht.

### Beispiel für ein benutzerdefiniertes Profil {#custom-profile-example}

Zur Veranschaulichung der Nutzung eines benutzerdefinierten Profils sollten wir uns einen Anwendungsfall ansehen, bei dem Kampagnenbilder mit benutzerdefiniertem Text versehen werden. Sie können ein Verarbeitungsprofil erstellen, das die Photoshop-API zum Bearbeiten der Bilder verwendet.

Die Asset Compute-Service-Integration ermöglicht es Experience Manager, diese Parameter mithilfe des Felds [!UICONTROL Dienstparameter] an das benutzerdefinierte Programm zu übergeben. Das benutzerdefinierte Proramm ruft dann die Photoshop-API auf und übergibt die Werte an die API. Sie können beispielsweise Schriftartname, Textfarbe, Textstärke und Textgröße übergeben, um den benutzerdefinierten Text Kampagnenbildern hinzuzufügen.

<!-- TBD: Check screenshot against the interface. -->

![custom-processing-profile](assets/custom-processing-profile.png)

*Abbildung: Verwenden Sie das Feld [!UICONTROL Dienstparameter], um zusätzliche Informationen an vordefinierte Parameter zu übergeben, die in das benutzerdefinierte Programm eingebunden sind. In diesem Beispiel werden hochgeladene Kampagnenbilder mit `Jumanji`-Text in der `Arial-BoldMT`-Schriftart aktualisiert.*

## Verarbeitungsprofile zur Verarbeitung von Assets verwenden {#use-profiles}

Erstellen Sie die zusätzlichen benutzerdefinierten Verarbeitungsprofile und wenden Sie sie auf bestimmte Ordner an, damit Experience Manager sie für Assets verarbeitet, die in diese Ordner hochgeladen oder in diesen aktualisiert wurden. Das standardmäßige integrierte Verarbeitungsprofil wird immer ausgeführt, ist jedoch auf der Benutzeroberfläche nicht sichtbar. Wenn Sie ein benutzerdefiniertes Profil hinzufügen, werden beide Profil zur Verarbeitung der hochgeladenen Assets verwendet.

Verwenden Sie eine der folgenden Methoden, um Verarbeitungsprofile auf Ordner anzuwenden:

* Administratoren können unter **[!UICONTROL Tools]** > **[!UICONTROL Assets]** **[!UICONTROL Verarbeitungsprofile]** eine Verarbeitungsprofildefinition auswählen und die Aktion **[!UICONTROL Profil auf Ordner anwenden]** nutzen. Dadurch wird ein Inhalts-Browser geöffnet, mit dem Sie zu bestimmten Ordnern navigieren, diese auswählen und die Anwendung des Profils bestätigen können.
* Die Benutzer können einen Ordner in der Assets-Benutzeroberfläche auswählen, die Aktion **[!UICONTROL Eigenschaften]** zum Öffnen der Ordnereigenschaften verwenden, auf die Registerkarte **[!UICONTROL Verarbeitungsprofile]** klicken und in der Popup-Liste das richtige Verarbeitungsprofil für diesen Ordner auswählen. Klicken Sie auf **[!UICONTROL Speichern und schließen]**, um die Änderungen zu speichern.
   ![Verarbeitungsprofil auf der Registerkarte „Asset-Eigenschaften“ auf einen Ordner anwenden](assets/folder-properties-processing-profile.png)

>[!TIP]
>
>Auf einen Ordner kann nur ein Verarbeitungsprofil angewendet werden. Um weitere Ausgabedarstellungen zu generieren, fügen Sie dem bestehenden Verarbeitungsprofil weitere Darstellungsdefinitionen hinzu.

Nachdem ein Verarbeitungsprofil auf einen Ordner angewendet wurde, werden alle neuen Assets, die in diesen Ordner oder in dessen Unterordnern hochgeladen (oder aktualisiert) werden, mit dem konfigurierten zusätzlichen Verarbeitungsprofil verarbeitet. Diese Verarbeitung erfolgt zusätzlich zum Standardprofil.

>[!NOTE]
>
>Ein Verarbeitungsprofil, das auf einen Ordner angewendet wird, funktioniert für die gesamte Struktur, kann aber mit einem anderen Profil überschrieben werden, das auf einen Unterordner angewendet wird. Wenn Assets in einen Ordner hochgeladen werden, prüft Experience Manager die Eigenschaften des zugehörigen Ordners auf ein Verarbeitungsprofil. Wenn nichts angewendet wird, wird in einem übergeordneten Ordner in der Hierarchie geprüft, ob ein Verarbeitungsprofil angewendet werden soll.

Um sicherzustellen, dass Assets verarbeitet werden, müssen Sie die erzeugten Ausgabedarstellungen in der Ansicht [!UICONTROL Ausgabedarstellungen] in der linken Leiste als Vorschau anzeigen. Öffnen Sie die Asset-Vorschau und dann die linke Leiste, um auf die Ansicht **[!UICONTROL Ausgabedarstellungen]** zuzugreifen. Die spezifischen Ausgabedarstellungen im Verarbeitungsprofil, für die der Typ des jeweiligen Assets mit den Einschlussregeln des MIME-Typs übereinstimmt, sollten sichtbar und zugänglich sein.

![Zusätzliche-Ausgabedarstellungen](assets/renditions-additional-renditions.png)

*Abbildung: Beispiel zweier zusätzlicher Ausgabedarstellungen, die von einem Verarbeitungsprofil generiert wurden, das auf den übergeordneten Ordner angewendet wurde.*

## Nachbearbeitungs-Workflows {#post-processing-workflows}

In Fällen, in denen zusätzliche Verarbeitung von Assets erforderlich ist, die mit den Verarbeitungsprofilen nicht erreicht werden kann, können der Konfiguration zusätzliche Nachbearbeitungs-Workflows hinzugefügt werden. Dies ermöglicht es, zusätzlich zu der konfigurierbaren Verarbeitung mithilfe von Asset-Microservices eine vollständig angepasste Verarbeitung hinzuzufügen.

Nachbearbeitungs-Workflows werden, falls konfiguriert, automatisch von [!DNL Experience Manager] ausgeführt, nachdem die Verarbeitung der Microservices abgeschlossen ist. Es ist nicht notwendig, Workflow-Starter manuell hinzuzufügen, um die Workflows auszulösen. Zu den Beispielen gehören:

* Benutzerdefinierte Workflow-Schritte zur Verarbeitung von Assets.
* Integrationen, um Assets von externen Systemen Metadaten oder Eigenschaften hinzuzufügen, z. B. Produkt- oder Prozessinformationen.
* Zusätzliche Verarbeitung durch externe Services.

Gehen Sie wie folgt vor, um [!DNL Experience Manager] eine Workflow-Konfiguration für die Nachbearbeitung hinzuzufügen:

* Erstellen eines oder mehrerer Workflow-Modelle. Diese benutzerdefinierten Modelle werden in dieser Dokumentation als *Workflow-Modelle nach der Verarbeitung* bezeichnet. Es handelt sich um normale [!DNL Experience Manager]-Workflow-Modelle.
* Fügen Sie diesen Modellen die erforderlichen Workflow-Schritte hinzu. Überprüfen Sie die Schritte aus dem Standard-Workflow und fügen Sie dem benutzerdefinierten Workflow alle erforderlichen Standardschritte hinzu. Die Schritte werden basierend auf einer Workflow-Modellkonfiguration für die Assets ausgeführt. Wenn beispielsweise Smart-Tagging beim Hochladen von Assets automatisch erfolgen soll, fügen Sie den Schritt zum benutzerdefinierten Workflow-Modell für die Nachbearbeitung hinzu.
* Fügen Sie am Ende den Schritt [!UICONTROL Abgeschlossener Prozess zum DAM-Workflow eines Asset-Updates] hinzu. Durch Hinzufügen dieses Schritts wird sichergestellt, dass Experience Manager weiß, wann die Verarbeitung abgeschlossen ist, und das Asset als verarbeitet markiert werden kann, d. h., dass beim Asset der Wert *Neu* angezeigt wird.
* Erstellen Sie eine Konfiguration für den Custom Workflow Runner Service, mit der die Ausführung eines Nachbearbeitungs-Workflow-Modells entweder nach Pfad (Speicherort für Ordner) oder nach regulären Ausdrücken konfiguriert werden kann.

### Erstellen von Nachbearbeitungs-Workflow-Modellen {#create-post-processing-workflow-models}

Nachbearbeitungs-Workflow-Modelle sind normale [!DNL Experience Manager]-Workflow-Modelle. Erstellen Sie verschiedene Modelle, wenn Sie für verschiedene Repository-Standorte oder Asset-Typen eine unterschiedliche Verarbeitung benötigen.

Verarbeitungsschritte sollten je nach Bedarf hinzugefügt werden. Sie können alle verfügbaren unterstützten Schritte sowie alle benutzerdefinierten Workflow-Schritte verwenden.

Stellen Sie sicher, dass der letzte Schritt jedes Nachbearbeitungs-Workflows `DAM Update Asset Workflow Completed Process` ist. Der letzte Schritt stellt sicher, dass Experience Manager weiß, wann die Asset-Verarbeitung abgeschlossen ist.

### Konfigurieren der Ausführung von Nachbearbeitungs-Workflows {#configure-post-processing-workflow-execution}

Um die Nachbearbeitungs-Workflow-Modelle zu konfigurieren, die für Assets ausgeführt werden sollen, die nach Abschluss der Verarbeitung der Asset-Microservices in das System hochgeladen oder aktualisiert werden, muss der Custom Workflow Runner-Service konfiguriert werden.

Der Adobe CQ DAM Custom Workflow Runner (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) ist ein OSGi-Service und bietet zwei Konfigurationsoptionen:

* Nachbearbeitungs-Workflows nach Pfad (`postProcWorkflowsByPath`): Es können mehrere Workflow-Modelle basierend auf unterschiedlichen Repository-Pfaden aufgeführt werden. Pfade und Modelle sollten durch einen Doppelpunkt voneinander getrennt werden. Einfache Repository-Pfade werden unterstützt und sollten einem Workflow-Modell im `/var`-Pfad zugeordnet werden. Beispiel: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* Nachbearbeitungs-Workflows nach Ausdruck (`postProcWorkflowsByExpression`): Es können mehrere Workflow-Modelle basierend auf unterschiedlichen regulären Ausdrücken aufgelistet werden. Ausdrücke und Modelle sollten durch einen Doppelpunkt getrennt werden. Der reguläre Ausdruck sollte direkt auf den Asset-Knoten verweisen und nicht auf eine der Ausgabedarstellungen oder Dateien. Beispiel: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>Die Konfiguration von Custom Workflow Runner ist eine Konfiguration eines OSGi-Service. Informationen zum Bereitstellen einer OSGi-Konfiguration finden Sie unter [Bereitstellung in Experience Manager](/help/implementing/deploying/overview.md).
>Die OSGi-Web-Konsole ist im Gegensatz zu On-Premise- und Managed Services-Implementierungen von [!DNL Experience Manager] nicht direkt in den Cloud Services-Implementierungen verfügbar.

Weitere Informationen dazu, welcher standardmäßige Workflow-Schritt im Nachbearbeitungs-Workflow verwendet werden kann, finden Sie unter [Workflow-Schritte im Nachbearbeitungs-Workflow](developer-reference-material-apis.md#post-processing-workflows-steps) in der Entwicklerreferenz.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Berücksichtigen Sie beim Entwickeln von Workflows Ihre Anforderungen für alle Arten von Ausgabedarstellungen. Wenn Sie der Meinung sind, dass eine Ausgabedarstellung in Zukunft nicht erforderlich sein wird, entfernen Sie den Erstellungsschritt aus dem Workflow. Ausgabedarstellungen können später nicht mehr stapelweise gelöscht werden. Unerwünschte Ausgabedarstellungen können nach längerer Nutzung von [!DNL Experience Manager] viel Speicherplatz beanspruchen. Bei einzelnen Assets können Sie Ausgabedarstellungen manuell aus der Benutzeroberfläche entfernen. Bei mehreren Assets können Sie [!DNL Experience Manager] so anpassen, dass entweder bestimmte Ausgabedarstellungen gelöscht oder die Assets gelöscht und die gelöschten Assets erneut hochgeladen werden.
* Derzeit ist die Unterstützung auf das Erzeugen von Ausgabedarstellungen beschränkt. Das Erstellen neuer Assets wird nicht unterstützt.
* Derzeit beträgt die maximale Dateigröße für die Extraktion von Metadaten etwa 10 GB. Beim Hochladen sehr großer Assets schlägt die Metadatenextraktion manchmal fehl.

>[!MORELIKETHIS]
>
>* [Einführung in den Asset Compute-Service](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html).
>* [Erweiterbarkeit und Verwendungszeitpunkt](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html).
>* [So erstellen Sie benutzerdefinierte Programme](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html).
>* [Interstützte MIME-Typen für verschiedene Anwendungsfälle](/help/assets/file-format-support.md).


<!-- TBD: 
* How/where can admins check what's already configured and provisioned.
* How/where to request for new provisioning/purchase.
-->
