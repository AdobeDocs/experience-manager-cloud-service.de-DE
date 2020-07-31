---
title: Konfigurieren und Verwenden von Asset-Microservices für die Asset-Verarbeitung
description: Erfahren Sie, wie Sie die Cloud-nativen Asset-Microservices konfigurieren und verwenden, um Assets skaliert zu verarbeiten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f5ebd1ae28336e63d8f3a89d7519cf74b46a3bfd
workflow-type: tm+mt
source-wordcount: '2208'
ht-degree: 57%

---


# Asset-Mikrodienste und verarbeitende Profil verwenden {#get-started-using-asset-microservices}

<!--
* Current capabilities of asset microservices offered. If workers have names then list the names and give a one-liner description. (The feature-set is limited for now and continues to grow. So will this article continue to be updated.)
* How to access the microservices. UI. API. Is extending possible right now?
* Detailed list of what file formats and what processing is supported by which workflows/workers process.
* How/where can admins check what's already configured and provisioned.
* How to create new config or request for new provisioning/purchase.

* [DO NOT COVER?] Exceptions or limitations or link back to lack of parity with AEM 6.5.
-->

Asset-Mikrodienste bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud-Diensten. Adobe verwaltet die Dienste für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen.

Die Verarbeitung von Assets hängt von der Konfiguration in den **[!UICONTROL Verarbeitungsprofilen]** ab, die eine Standardeinstellung bieten und es einem Administrator ermöglichen, spezifischere Asset-Verarbeitungskonfigurationen hinzuzufügen. Administratoren können die Konfigurationen von Nachbearbeitungs-Workflows erstellen und verwalten, einschließlich optionaler Anpassungen. Die Anpassung von Workflows ermöglicht Erweiterbarkeit und vollständige Anpassung.

Mit Asset-Microservices können Sie eine [breite Palette von Dateitypen](/help/assets/file-format-support.md) verarbeiten, die mehr Formate standardmäßig abdecken, als dies mit früheren Versionen von Experience Manager möglich war. Beispielsweise ist jetzt das Extrahieren von Miniaturansichten von PSD- und PSB-Formaten möglich, für die zuvor Lösungen von Drittanbietern wie ImageMagick erforderlich waren.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Eine allgemeine Ansicht der Asset-Verarbeitung](assets/asset-microservices-flow.png "Eine allgemeine Ansicht der Asset-Verarbeitung")

>[!NOTE]
>
>The asset processing described here replaces the `DAM Update Asset` workflow model that exists in the previous versions of [!DNL Experience Manager]. Die meisten Schritte zum Generieren von Standardausgaben und zum Erstellen von Metadaten werden durch die Verarbeitung von Asset-Microservices ersetzt. Die verbleibenden Schritte können, falls vorhanden, durch die Konfiguration des Nacharbeitungs-Workflows ersetzt werden.

## Optionen für die Verarbeitung von Assets {#get-started}

Experience Manager ermöglicht die folgenden Verarbeitungsstufen.

| Konfiguration | Beschreibung | Anwendungsfälle |
|---|---|---|
| [Standardkonfiguration](#default-config) | Es ist verfügbar und kann nicht geändert werden. Diese Konfiguration bietet eine sehr einfache Funktion zur Darstellung. | Standardminiaturen, die von der [!DNL Assets] Benutzeroberfläche verwendet werden (48, 140 und 319 px); Große Vorschau (Webdarstellung - 1280 px); Metadaten und Text-Extraktion. |
| [Standardkonfiguration](#standard-config) | Konfiguriert von Administratoren nur über die Benutzeroberfläche. Bietet mehr Optionen für die Generierung von Darstellungen als die oben genannte Standardkonfiguration. | Format und Auflösung von Bildern ändern; FPO-Darstellungen erstellen. |
| [Benutzerdefinierte Konfiguration](#custom-config) | Konfiguriert von Administratoren über die Benutzeroberfläche zum Aufrufen von benutzerdefinierten Workern, die komplexere Anforderungen unterstützen. Verwendet eine Cloud-native [!DNL Asset Compute Service]. | Siehe [Zulässige Anwendungsfälle](#custom-config). |

Informationen zum Erstellen benutzerdefinierter Verarbeitungsprofile, die spezifisch für Ihre benutzerdefinierten Anforderungen sind, wie z. B. zur Integration in andere Systeme, finden Sie unter [Nacharbeitungs-Workflows](#post-processing-workflows).

## Unterstützte Dateiformate {#supported-file-formats}

Asset-Microservices bieten Unterstützung für eine Vielzahl von Dateiformaten, um Ausgabeformate zu generieren oder Metadaten zu extrahieren. Die vollständige Liste finden Sie unter [Unterstützte Dateiformate](file-format-support.md) .

## Standardkonfiguration {#default-config}

Einige Standardwerte sind vorkonfiguriert, um sicherzustellen, dass die in Experience Manager erforderlichen Standarddarstellungen verfügbar sind. Die Standardkonfiguration stellt außerdem sicher, dass die Vorgänge zur Extraktion und Extraktion von Metadaten verfügbar sind. Benutzer können sofort mit dem Hochladen oder Aktualisieren von Assets beginnen. Die grundlegende Verarbeitung ist standardmäßig verfügbar.

Bei der Standardkonfiguration wird nur das grundlegendste verarbeitende Profil konfiguriert. Ein solches Profil ist auf der Benutzeroberfläche nicht sichtbar und Sie können es nicht ändern. Es wird immer ausgeführt, um hochgeladene Assets zu verarbeiten. Such a default processing profile ensures that the basic processing required by [!DNL Experience Manager] is completed on all assets.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## Standard-Profil {#standard-config}

[!DNL Experience Manager] bietet Funktionen zum Generieren speziellerer Darstellungen für gängige Formate gemäß den Anforderungen des Benutzers. Ein Administrator kann zusätzliche [!UICONTROL Verarbeitungsfunktionen] erstellen, um die Erstellung solcher Darstellungen zu erleichtern. Die Benutzer weisen dann einem oder mehreren der verfügbaren Profil bestimmten Ordnern zu, um die zusätzliche Verarbeitung abzuschließen. Beispielsweise kann die zusätzliche Verarbeitung Darstellungen für Web, Mobil und Tablet generieren. Das folgende Video zeigt, wie Sie [!UICONTROL Verarbeitungsprofile] erstellen und anwenden und auf die erstellten Ausgabeformate zugreifen.

* **Darstellungsbreite und -höhe**: Die Angabe der Breite und Höhe der Darstellung bietet die maximale Größe des generierten Ausgabebilds. Asset Microservices versucht, die größtmögliche Darstellung zu erstellen, deren Breite und Höhe nicht größer als die angegebene Breite bzw. Höhe ist. Das Seitenverhältnis wird beibehalten, d. h. es entspricht dem Original. Ein leerer Wert bedeutet, dass bei der Asset-Verarbeitung die Pixelabmessungen des Originals berücksichtigt werden.

* **MIME-Typeinschlussregeln**: Wenn ein Asset mit einem bestimmten MIME-Typ verarbeitet wird, wird der MIME-Typ zunächst mit dem ausgeschlossenen MIME-Typwert für die Darstellungsspezifikation verglichen. Wenn es mit dieser Liste übereinstimmt, wird dieses spezifische Ausgabeformat nicht für das Asset generiert (Blockierungsliste). Andernfalls wird der Mime-Typ mit dem eingeschlossenen Mime-Typ verglichen. Wenn er mit der Liste übereinstimmt, wird das Ausgabeformat generiert (Zulassungsliste).

* **Spezielle FPO-Darstellung**: Beim Platzieren großer Assets aus [!DNL Experience Manager] in [!DNL Adobe InDesign] Dokumente wartet ein Kreativprofi eine Weile, nachdem er ein Asset [platziert](https://helpx.adobe.com/de/indesign/using/placing-graphics.html)hat. Meanwhile, the user is blocked from using [!DNL InDesign]. Dies unterbricht den kreativen Fluss und wirkt sich negativ auf das Kundenerlebnis aus. Adobe enables temporarily placing small-sized renditions in [!DNL InDesign] documents to begin with, which can be replaced with full-resolution assets on-demand later. [!DNL Experience Manager] bietet Ausgabeversionen, die nur für die Platzierung (FPO) verwendet werden. Diese FPO-Darstellungen haben eine kleine Dateigröße, weisen aber dasselbe Seitenverhältnis auf.

Das Verarbeitungsprofil kann eine FPO-Wiedergabe (nur für Platzierung) enthalten. In der -[!DNL Adobe Asset Link][Dokumentation](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) erfahren Sie, ob Sie das Programm für Ihr Verarbeitungsprofil aktivieren müssen. Weitere Informationen finden Sie in der [vollständigen Dokumentation von Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html).

### Standardmäßiges Profil erstellen {#create-standard-profile}

Gehen Sie wie folgt vor, um ein Profil für die Standardverarbeitung zu erstellen:

1. Administratoren greifen auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Assets]** > **[!UICONTROL VerarbeitungsProfil]** zu. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Namen ein, der Ihnen beim Anwenden auf einen Ordner hilft, das Profil eindeutig zu identifizieren.
1. Um FPO-Darstellungen zu erstellen, aktivieren Sie auf der Registerkarte &quot; **[!UICONTROL Standard]** &quot;die Option &quot; **[!UICONTROL FPO-Darstellung]** erstellen&quot;. Geben Sie einen **[!UICONTROL Qualitätswert]** zwischen 1 und 100 ein.
1. Um andere Darstellungen zu erstellen, klicken Sie auf **[!UICONTROL Hinzufügen Neu]** und geben Sie die folgenden Informationen ein:

   * Dateiname jeder Darstellung.
   * Dateiformat (PNG, JPEG oder GIF) jeder Darstellung.
   * Breite und Höhe der einzelnen Darstellungen in Pixel. Wenn die Werte nicht angegeben werden, wird die vollständige Pixelgröße des Originalbilds verwendet.
   * Qualität in Prozent jeder JPEG-Darstellung.
   * Eingeschlossene und ausgeschlossene MIME-Typen zur Definition der Anwendbarkeit eines Profils.

   ![processing-profiles-adding](assets/processing-profiles-adding.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Das folgende Video zeigt den Nutzen und die Verwendung von Standard-Profil.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)

<!-- Removed per cqdoc-15624 request by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) 
 -->

## Benutzerspezifische Profil- und Anwendungsfälle {#custom-config}

<!-- **TBD items**:

* Overall cross-linking with the extensibility content.
* Mention how to get URL of worker. Worker URL for Dev, Stage, and Prod environments.
* Mention mapping of service parameters. Link to compute service article.
* Review from flow perspective shared in Jira ticket.
-->

Einige komplexe Anwendungsfälle für die Asset-Verarbeitung können nicht mit Standardkonfigurationen durchgeführt werden, da die Anforderungen der Organisationen unterschiedlich sind. Angebot [!DNL Asset Compute Service] zur Adobe solcher Anwendungsfälle. Es handelt sich um einen skalierbaren und erweiterbaren Dienst zur Verarbeitung digitaler Assets. Es kann Bild-, Video-, Dokument- und andere Dateiformate in verschiedene Darstellungen umwandeln, einschließlich Miniaturansichten, extrahiertem Text und Metadaten und Archiven.

Entwickler können den Asset Compute-Dienst verwenden, um spezialisierte benutzerdefinierte Mitarbeiter zu erstellen, die vordefinierten, komplexen Anwendungsfällen entsprechen. [!DNL Experience Manager] Sie können diese benutzerdefinierten Arbeiter über die Benutzeroberfläche aufrufen, indem Sie benutzerdefinierte Profil verwenden, die Administratoren konfigurieren. [!DNL Asset Compute Service] unterstützt die folgenden Anwendungsfälle beim Aufrufen externer Dienste:

* Rufen Sie [!DNL Adobe Photoshop] die Bildausschnitt-API auf und speichern Sie das Ergebnis als Darstellung.
* Rufen Sie Drittanbietersysteme auf, um Daten zu aktualisieren, z. B. ein PIM-System.
* Verwenden Sie die [!DNL Photoshop] API, um verschiedene Darstellungen basierend auf der Photoshop-Vorlage zu generieren.
* Verwenden Sie die [!DNL Adobe Lightroom] API, um die erfassten Assets zu optimieren und sie als Darstellungen zu speichern.

>[!NOTE]
>
>Sie können die Standardmetadaten nicht mit den benutzerdefinierten Workern bearbeiten. Sie können nur benutzerdefinierte Metadaten ändern.

### Create a custom profile {#create-custom-profile}

Gehen Sie wie folgt vor, um ein benutzerdefiniertes Profil zu erstellen:

1. Administratoren greifen auf **[!UICONTROL Werkzeuge > Assets > Profil]** für die Verarbeitung zu. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Click on **[!UICONTROL Custom]** tab. Click **[!UICONTROL Add New]**. Geben Sie den gewünschten Dateinamen der Darstellung ein.
1. Geben Sie die folgenden Informationen ein und klicken Sie auf **[!UICONTROL Speichern]**.

   * Dateiname jeder Darstellung und eine unterstützte Dateierweiterung.
   * Endpunkt-URL einer benutzerdefinierten Firefly-App. Die App muss aus demselben Unternehmen stammen wie das Experience Manager-Konto.
   * Hinzufügen Sie die Dienstparameter nach Bedarf.
   * Eingeschlossene und ausgeschlossene MIME-Typen zur Definition der Anwendbarkeit eines Profils.

![custom-processing-Profil](assets/custom-processing-profile.png)

>[!CAUTION]
>
>Wenn die Firefly-App und das [!DNL Experience Manager] -Konto nicht aus demselben Unternehmen stammen, funktioniert die Integration nicht.

## Verarbeitung von Profilen zur Verarbeitung von Assets {#use-profiles}

Erstellen Sie die zusätzlichen benutzerdefinierten Verarbeitungsprofile und wenden Sie sie auf bestimmte Ordner an, damit Experience Manager sie für Assets verarbeitet, die in diese Ordner hochgeladen oder in diesen aktualisiert wurden. Das standardmäßige integrierte Verarbeitungsprofil wird immer ausgeführt, ist jedoch auf der Benutzeroberfläche nicht sichtbar. Wenn Sie ein benutzerdefiniertes Profil hinzufügen, werden beide Profil zur Verarbeitung der hochgeladenen Assets verwendet.

Wenden Sie verarbeitende Profil auf Ordner mit einer der folgenden Methoden an:

* Administratoren können unter **[!UICONTROL Tools > Assets > Verarbeitungsprofile]** eine Definition des Verarbeitungsprofils auswählen und die Aktion **[!UICONTROL Profil auf Ordner anwenden]** verwenden. Dadurch wird ein Inhalts-Browser geöffnet, mit dem Sie zu bestimmten Ordnern navigieren, diese auswählen und die Anwendung des Profils bestätigen können.
* Users can select a folder in the Assets user interface, use **[!UICONTROL Properties]** action to open folder properties screen, click on the **[!UICONTROL Processing Profiles]** tab, and in the popup list, select the correct processing profile for that folder. Um die Änderungen zu speichern, klicken Sie auf **[!UICONTROL Speichern &amp; Schließen]**.

>[!NOTE]
>
>Nur ein Verarbeitungsprofil kann auf einen bestimmten Ordner angewendet werden. Um weitere Darstellungen zu generieren, fügen Sie dem bestehenden Profil weitere Darstellungsdefinitionen hinzu.

Nachdem ein Verarbeitungsprofil auf einen Ordner angewendet wurde, werden alle neuen Assets, die in diesen Ordner oder in dessen Unterordnern hochgeladen (oder aktualisiert) werden, mit dem konfigurierten zusätzlichen Verarbeitungsprofil verarbeitet. Diese Verarbeitung erfolgt zusätzlich zum standardmäßigen Profil. Wenn Sie mehrere Profile auf einen Ordner anwenden, werden die hochgeladenen oder aktualisierten Elemente mit jedem dieser Profile verarbeitet.

>[!NOTE]
>
>Ein auf einen Profil angewendetes Verarbeitungsordner funktioniert für die gesamte Struktur, kann jedoch überschrieben werden, wenn ein anderes Profil auf einen Unterordner angewendet wird. Wenn Assets in einen Ordner hochgeladen werden, prüft Experience Manager die Eigenschaften des zugehörigen Ordners auf ein Verarbeitungsprofil. Wenn keine Anwendung erfolgt, wird ein übergeordneter Profil in der Hierarchie auf die Anwendung eines Verarbeitungsordners überprüft.

Benutzer können überprüfen, ob die Verarbeitung tatsächlich stattgefunden hat, indem sie ein neu hochgeladenes Asset öffnen, für das die Verarbeitung abgeschlossen ist, die Asset-Vorschau öffnen und auf die Ansicht **[!UICONTROL Ausgabeformate]** in der linken Leiste klicken. Die spezifischen Ausgabeformate im Verarbeitungsprofil, für die der Typ des jeweiligen Assets mit den Einschlussregeln des MIME-Typs übereinstimmt, sollten sichtbar und zugänglich sein.

![additional-renditions](assets/renditions-additional-renditions.png)

*Abbildung: Beispiel für zwei zusätzliche Darstellungen, die von einem verarbeitenden Profil generiert wurden, das auf den übergeordneten Ordner angewendet wurde.*

## Nachbearbeitungs-Workflows {#post-processing-workflows}

In Fällen, in denen zusätzliche Verarbeitung von Assets erforderlich ist, die mit den Verarbeitungsprofilen nicht erreicht werden können, können der Konfiguration zusätzliche Nachbearbeitungs-Workflows hinzugefügt werden. Dies ermöglicht es, zusätzlich zu der konfigurierbaren Verarbeitung mithilfe von Asset-Microservices eine vollständig angepasste Verarbeitung hinzuzufügen.

Nachbearbeitungs-Workflows werden, falls konfiguriert, automatisch von AEM ausgeführt, nachdem die Verarbeitung der Microservices abgeschlossen ist. Es ist nicht notwendig, Workflow-Starter manuell hinzuzufügen, um sie auszulösen. Zu den Beispielen gehören:

* Benutzerdefinierte Workflow-Schritte zur Verarbeitung von Assets.
* Integrationen, um Assets von externen Systemen Metadaten oder Eigenschaften hinzuzufügen, z. B. Produkt- oder Prozessinformationen.
* Zusätzliche Verarbeitung durch externe Dienste.

Das Hinzufügen einer Workflow-Konfiguration für die Nachbearbeitung zu Experience Manager umfasst die folgenden Schritte:

* Erstellen eines oder mehrerer Workflow-Modelle. In den Dokumenten wird dies als *Workflow-Modelle für die Nachbearbeitung* erwähnt, bei denen es sich jedoch um normale Workflow-Modelle für Experience Manager handelt.
* Hinzufügen spezifischer Workflow-Schritte zu diesen Modellen. Die Schritte werden basierend auf einer Workflow-Modellkonfiguration für die Assets ausgeführt.
* Fügen Sie am Ende den Schritt [!UICONTROL Abgeschlosser Prozess zum DAM-Workflow eines Asset-Updates] hinzu. Durch Hinzufügen dieses Schritts wird sichergestellt, dass Experience Manager weiß, wann die Verarbeitung abgeschlossen ist, und das Asset als verarbeitet markiert werden kann, d. h., dass beim Asset der Wert *Neu* angezeigt wird.
* Erstellen Sie eine Konfiguration für den Custom Workflow Runner Service, mit der die Ausführung eines Nachbearbeitungs-Workflow-Modells entweder nach Pfad (Speicherort für Ordner) oder nach regulären Ausdrücken konfiguriert werden kann.

### Erstellen von Nachbearbeitungs-Workflow-Modellen {#create-post-processing-workflow-models}

Nachbearbeitungs-Workflow-Modelle sind normale AEM-Workflow-Modelle. Erstellen Sie verschiedene Modelle, wenn Sie für verschiedene Repository-Standorte oder Asset-Typen eine unterschiedliche Verarbeitung benötigen.

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
>Die OSGi-Web-Konsole ist im Gegensatz zu On-Premise- und Managed Services-Bereitstellungen von AEM nicht direkt in den Cloud Services-Bereitstellungen verfügbar.

Weitere Informationen dazu, welcher standardmäßige Workflow-Schritt im Nachbearbeitungs-Workflow verwendet werden kann, finden Sie unter [Workflow-Schritte im Nachbearbeitungs-Workflow](developer-reference-material-apis.md#post-processing-workflows-steps) in der Entwicklerreferenz.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Berücksichtigen Sie beim Entwickeln von Workflows Ihre Anforderungen für alle Arten von Ausgabedarstellungen. Wenn Sie der Meinung sind, dass eine Ausgabedarstellung in Zukunft nicht erforderlich sein wird, entfernen Sie den Erstellungsschritt aus dem Workflow. Ausgabedarstellungen können später nicht mehr stapelweise gelöscht werden. Unerwünschte Ausgabedarstellungen können nach längerer Nutzung von [!DNL Experience Manager] viel Speicherplatz beanspruchen. Bei einzelnen Assets können Sie Ausgabedarstellungen manuell aus der Benutzeroberfläche entfernen. Bei mehreren Assets können Sie [!DNL Experience Manager] so anpassen, dass entweder bestimmte Ausgabedarstellungen gelöscht oder die Assets gelöscht und die gelöschten Assets erneut hochgeladen werden.
* Derzeit ist die Unterstützung auf das Generieren von Darstellungen beschränkt. Das Generieren neuer Assets wird nicht unterstützt.
