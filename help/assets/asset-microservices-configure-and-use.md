---
title: Asset-Mikrodienste für die Asset-Verarbeitung konfigurieren und verwenden
description: Erfahren Sie, wie Sie die Cloud-nativen Asset-Mikrodienste konfigurieren und verwenden, um Assets im Maßstab zu verarbeiten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Erste Schritte mit Asset-Microservices {#get-started-using-asset-microservices}

<!--
* Current capabilities of asset microservices offered. If workers have names then list the names and give a one-liner description. (The feature-set is limited for now and continues to grow. So will this article continue to be updated.)
* How to access the microservices. UI. API. Is extending possible right now?
* Detailed list of what file formats and what processing is supported by which workflows/workers process.
* How/where can admins check what's already configured and provisioned.
* How to create new config or request for new provisioning/purchase.

* [DO NOT COVER?] Exceptions or limitations or link back to lack of parity with AEM 6.5.
-->

Asset Microservices bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud-Diensten. Adobe verwaltet die Dienste für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen.

Die Verarbeitung von Assets hängt von der Konfiguration in **[!UICONTROL verarbeitenden Profilen]** ab, die eine Standardeinstellung bereitstellen und es einem Administrator ermöglichen, eine spezifischere Asset-Verarbeitungskonfiguration hinzuzufügen. Administratoren können die Konfigurationen der Workflows für die Nachbearbeitung erstellen und verwalten, einschließlich optionaler Anpassungen. Die Anpassung von Workflows ermöglicht Erweiterbarkeit und vollständige Anpassung.

Darunter befindet sich ein Fluss auf hoher Ebene für die Asset-Verarbeitung.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![asset-microservices-flow](assets/asset-microservices-flow.png)

>[!NOTE]
>
> Die hier beschriebene Asset-Verarbeitung ersetzt das `DAM Update Asset` Workflow-Modell, das in früheren Versionen von Experience Manager vorhanden ist. Die meisten Schritte zum Generieren von Standarddarstellungen und zum Erstellen von Metadaten werden durch die Verarbeitung von Asset-Mikrodiensten ersetzt, und die verbleibenden Schritte können, falls vorhanden, durch die Konfiguration des Arbeitsablaufs nach der Verarbeitung ersetzt werden.

## Erste Schritte mit der Asset-Verarbeitung {#get-started}

Die Asset-Verarbeitung mit Asset-Mikrodiensten wird mit einer Standardkonfiguration vorkonfiguriert, sodass die vom System benötigten Standarddarstellungen verfügbar sind. Außerdem stellen Sie sicher, dass Vorgänge zur Extraktion und Extraktion von Metadaten verfügbar sind. Beginn können Assets sofort hochladen oder aktualisieren. Die Basisverarbeitung ist standardmäßig verfügbar.

Für bestimmte Anforderungen an die Generierung von Darstellungen oder die Verarbeitung von Assets kann ein AEM-Administrator zusätzliche [!UICONTROL Verarbeitungs-Profil]erstellen. Die Benutzer können einem bestimmten Profil ein oder mehrere dieser Elemente zuweisen, um eine weitere Verarbeitung zu erhalten. Angenommen, Sie erstellen Web-, Mobil- und Tablet-spezifische Darstellungen. Im folgenden Video wird das Erstellen und Anwenden von [!UICONTROL Verarbeitungs-Profilen] und der Zugriff auf die erstellten Darstellungen erläutert.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)

Informationen zum Ändern des vorhandenen Profils finden Sie unter [Konfigurationen für Asset-Mikrodienste](#configure-asset-microservices).
Informationen zum Erstellen benutzerdefinierter Profil für die Verarbeitung, z. B. zur Integration in andere Systeme, finden Sie unter [Nachbearbeitung Workflows](#post-processing-workflows).

## Konfigurationen für Asset Microservices {#configure-asset-microservices}

Um Asset-Mikrodienste zu konfigurieren, können Administratoren die Konfigurationsoberfläche unter **[!UICONTROL &quot;Extras&quot;> &quot;Assets&quot;> &quot;Profil]** bearbeiten&quot;verwenden.

### Standardkonfiguration {#default-config}

Bei der Standardkonfiguration wird nur das Profil für die Standardverarbeitung konfiguriert. Das Profil für die Standardverarbeitung ist auf der Benutzeroberfläche nicht sichtbar und kann nicht geändert werden. Es wird immer ausgeführt, um hochgeladene Assets zu verarbeiten. Mit einem Profil für die Standardverarbeitung wird sichergestellt, dass die gesamte grundlegende Verarbeitung, die für Experience Manager erforderlich ist, für alle Assets abgeschlossen ist.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png) -->

Das Profil für die Standardverarbeitung bietet die folgende Verarbeitungskonfiguration:

* Standardmäßige Miniaturansichten, die von der Asset-Benutzeroberfläche verwendet werden (48, 140 und 319 px)
* Große Vorschau (Webdarstellung - 1280 px)
* Metadatenextraktion
* Extraktion von Text

### Unterstützte Dateiformate {#supported-file-formats}

Asset Microservices bieten Unterstützung für eine Vielzahl von Dateiformaten, was die Möglichkeit betrifft, Darstellungen zu generieren oder Metadaten zu extrahieren. Die vollständige Liste finden Sie unter [Unterstützte Dateiformate](file-format-support.md) .

### Hinzufügen zusätzlicher Profil {#processing-profiles}

Mit der Aktion &quot; **[!UICONTROL Erstellen]** &quot;können weitere Profil zur Verarbeitung hinzugefügt werden.

Jede Konfiguration des verarbeitenden Profils enthält eine Liste von Darstellungen. Für jede Darstellung können Sie Folgendes angeben:

* Darstellungsname.
* Unterstütztes Ausgabeformat, z. B. JPEG, PNG oder GIF.
* Darstellungsbreite und -höhe in Pixel. Wenn sie nicht angegeben ist, wird die vollständige Pixelgröße des Originalbilds verwendet.
* Darstellungsqualität von JPEG in Prozent.
* Eingeschlossene und ausgeschlossene MIME-Typen zur Definition der Anwendbarkeit eines Profils.

![processing-Profils-adding](assets/processing-profiles-adding.png)

Wenn Sie ein neues Profil erstellen und speichern, wird es zur Liste der konfigurierten Profil hinzugefügt. Sie können diese verarbeitenden Profil auf Ordner in der Ordnerhierarchie anwenden, um sie beim Hochladen von Assets und bei der Verarbeitung von Assets effektiv zu gestalten.

<!-- Removed per cqdoc-15624 request by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) -->

#### Darstellungsbreite und -höhe {#rendition-width-height}

Die Angabe der Breite und Höhe der Darstellung bietet die maximale Größe des generierten Ausgabebilds. Asset Microservice versucht, die größtmögliche Darstellung zu erstellen, deren Breite und Höhe nicht größer als die angegebene Breite bzw. Höhe ist. Das Seitenverhältnis wird beibehalten, d. h. es entspricht dem Original.

Ein leerer Wert bedeutet, dass bei der Asset-Verarbeitung die Pixelabmessungen des Originals berücksichtigt werden.

#### MIME-Typeinschlussregeln {#mime-type-inclusion-rules}

Wenn ein Asset mit einem bestimmten MIME-Typ verarbeitet wird, wird der MIME-Typ zunächst mit dem ausgeschlossenen MIME-Typwert für die Darstellungsspezifikation verglichen. Wenn es mit dieser Liste übereinstimmt, wird diese spezifische Darstellung nicht für das Asset generiert (&quot;Blacklisting&quot;).

Andernfalls wird der MIME-Typ mit dem mitgelieferten MIME-Typ verglichen. Wenn er mit der Liste übereinstimmt, wird die Darstellung generiert (&quot;Whitelisting&quot;).

#### Spezielle FPO-Darstellung {#special-fpo-rendition}

Beim Platzieren von Assets in großen Größen aus AEM in Adobe InDesign-Dokumenten muss ein Kreativprofi nach dem [Platzieren eines Assets](https://helpx.adobe.com/de/indesign/using/placing-graphics.html)eine Weile warten. In der Zwischenzeit wird der Benutzer daran gehindert, InDesign zu verwenden. Dies unterbricht den kreativen Fluss und beeinträchtigt die Benutzererfahrung. Adobe ermöglicht die zeitweilige Platzierung kleiner Darstellungen in InDesign-Dokumenten. Diese können später bei Bedarf durch Assets mit voller Auflösung ersetzt werden. Experience Manager bietet Darstellungen, die nur für die Platzierung verwendet werden (FPO). Diese FPO-Darstellungen haben eine kleine Dateigröße, haben aber dasselbe Seitenverhältnis.

Das verarbeitende Profil kann eine FPO-Darstellung (nur für Platzierung) enthalten. Informationen dazu, ob Sie es für Ihr verarbeitendes Profil aktivieren müssen, finden Sie in der Adobe Asset Link- [Dokumentation](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) . Weitere Informationen finden Sie in der Dokumentation zum [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html).

## Verwenden von Asset-Mikrodiensten zur Verarbeitung von Assets {#use-asset-microservices}

Erstellen Sie die zusätzlichen, benutzerdefinierten Verarbeitungsordner und wenden Sie sie auf bestimmte Profil an, damit Experience Manager Assets verarbeiten kann, die in diese  hochgeladen oder aktualisiert werden. Das standardmäßige, integrierte Standard-Profil für die Verarbeitung wird immer ausgeführt, ist jedoch auf der Benutzeroberfläche nicht sichtbar. Wenn Sie ein benutzerdefiniertes Profil hinzufügen, werden beide Profil zur Verarbeitung der hochgeladenen Assets verwendet.

Es gibt zwei Möglichkeiten, verarbeitende Profil auf Ordner anzuwenden:

* Administratoren können unter **[!UICONTROL &quot;Extras&quot;> &quot;Assets&quot;> &quot;Profil]** für die Verarbeitung&quot;eine Definition für verarbeitendes Profil auswählen und die Aktion &quot;Profil auf Ordner **[!UICONTROL anwenden&quot;verwenden]** . Dadurch wird ein Inhaltsbrowser geöffnet, mit dem Sie zu bestimmten Ordnern navigieren, diese auswählen und die Anwendung des Profils bestätigen können.
* Benutzer können einen Ordner in der Benutzeroberfläche „Assets“ auswählen, die Aktion **[!UICONTROL Eigenschaften]** zum Öffnen der Ordnereigenschaften verwenden, auf die Registerkarte **[!UICONTROL Verarbeitungsprofile]** klicken und in der Dropdownliste das richtige Verarbeitungsprofil für diesen Ordner auswählen. Die Auswahl wird bei der Aktion **[!UICONTROL Speichern und Schließen]** gespeichert.

>[!NOTE]
>
>Auf einen bestimmten Profil kann nur ein Verarbeitungsordner angewendet werden. Wenn Sie weitere Darstellungen erstellen müssen, können Sie dem verarbeitenden Profil weitere Darstellungsdefinitionen hinzufügen.

Nachdem ein verarbeitendes Profil auf einen Ordner angewendet wurde, werden alle neuen Assets, die in diesem  hochgeladen (oder aktualisiert) wurden, oder die Unterordner des Ordners verarbeitet, indem das konfigurierte zusätzliche Profil für die Verarbeitung verwendet wird. Diese zusätzliche Verarbeitung erfolgt zusätzlich zum standardmäßigen Profil. Wenn Sie mehrere Profil auf einen Ordner anwenden, werden die hochgeladenen oder aktualisierten Assets mit jedem dieser Profil verarbeitet.

>[!NOTE]
>
>Wenn Assets in einen Ordner hochgeladen werden, prüft Experience Manager die Eigenschaften des zugehörigen Ordners auf ein verarbeitendes Profil. Wenn keine Option angewendet wird, wird sie in der Ordnerstruktur angezeigt, bis ein verarbeitendes Profil angewendet wurde, und verwendet es für das Asset. Das bedeutet, dass ein auf einen Ordner angewendetes Profil für die gesamte Struktur funktioniert, jedoch überschrieben werden kann, wenn ein anderes Profil auf einen Unterordner angewendet wird.

Benutzer können überprüfen, ob die Verarbeitung tatsächlich stattgefunden hat, indem sie ein neu hochgeladenes Asset öffnen, für das die Verarbeitung abgeschlossen ist, die Asset-Vorschau öffnen und auf die Ansicht **[!UICONTROL Ausgabeformate]** der linken Leiste klicken. Die spezifischen Darstellungen im verarbeitenden Profil, für die der Typ des jeweiligen Assets mit den MIME-Einschlussregeln übereinstimmt, sollten sichtbar und zugänglich sein.

![Zusätzliche Darstellungen](assets/renditions-additional-renditions.png)*Abbildung: Beispiel zweier zusätzlicher Darstellungen, die von einem verarbeitenden Profil generiert wurden, das auf den übergeordneten Ordner angewendet wurde*

## Workflows nach der Verarbeitung {#post-processing-workflows}

Wenn zusätzliche Verarbeitung von Assets erforderlich ist, die mit den verarbeitenden Profilen nicht erreicht werden können, können zusätzliche Workflows zur Konfiguration hinzugefügt werden. Dies ermöglicht das Hinzufügen einer vollständig angepassten Verarbeitung zusätzlich zur konfigurierbaren Verarbeitung mithilfe von Asset Microservices.

Nach Abschluss der Verarbeitung werden Workflows, sofern konfiguriert, automatisch von AEM ausgeführt, nachdem die Verarbeitung der Mikrodienste abgeschlossen ist. Workflow-Starter müssen nicht manuell hinzugefügt werden, um sie auszulösen.

Beispiele dafür sind:

* benutzerdefinierte Workflow-Schritte zur Verarbeitung von Assets, z. B. Java-Code zur Generierung von Darstellungen aus proprietären Dateiformaten.
* Integrationen, um Assets von externen Systemen Metadaten oder Eigenschaften hinzuzufügen, z. B. Produkt- oder Prozessinformationen.
* zusätzliche Verarbeitung durch externe Dienste

Das Hinzufügen einer Workflow-Konfiguration für die Nachbearbeitung zu Experience Manager umfasst die folgenden Schritte:

* Erstellen eines oder mehrerer Workflow-Modelle. Sie werden als &quot;Workflow-Modelle nach der Verarbeitung&quot;bezeichnet, es handelt sich jedoch um normale AEM-Workflow-Modelle.
* Hinzufügen spezifischer Workflow-Schritte zu diesen Modellen. Diese Schritte werden basierend auf der Konfiguration des Workflow-Modells für die Assets ausgeführt.
* Der letzte Schritt eines solchen Modells muss der `DAM Update Asset Workflow Completed Process` Schritt sein. Dies ist erforderlich, um sicherzustellen, dass AEM weiß, dass die Verarbeitung beendet wurde und das Asset als verarbeitet (&quot;Neu&quot;) gekennzeichnet werden kann.
* Erstellen einer Konfiguration für den benutzerdefinierten Workflow Runner-Dienst, mit der die Ausführung eines Workflow-Nachbearbeitungs-Modells entweder nach Pfad (Ordnerspeicherort) oder regulärem Ausdruck konfiguriert werden kann

### Erstellen von Workflow-Modellen für die Nachbearbeitung {#create-post-processing-workflow-models}

Workflow-Modelle nach der Verarbeitung sind normale AEM-Workflow-Modelle. Erstellen Sie verschiedene Modelle, wenn Sie unterschiedliche Verarbeitungsschritte für verschiedene Repository-Speicherorte oder Asset-Typen benötigen.

Verarbeitungsschritte sollten je nach Bedarf hinzugefügt werden. Sie können alle verfügbaren unterstützten Schritte sowie alle benutzerdefinierten Workflow-Schritte verwenden.

Stellen Sie sicher, dass der letzte Schritt jedes Workflows der Nachbearbeitung `DAM Update Asset Workflow Completed Process`ist. Der letzte Schritt hilft sicherzustellen, dass Experience Manager weiß, wann die Asset-Verarbeitung abgeschlossen ist.

### Workflow-Ausführung nach der Verarbeitung konfigurieren {#configure-post-processing-workflow-execution}

Um die Workflow-Modelle für die Nachbearbeitung so zu konfigurieren, dass sie für Assets ausgeführt werden, die nach Abschluss der Verarbeitung der Asset-Mikrodienste im System hochgeladen oder aktualisiert wurden, muss der Custom Workflow Runner-Dienst konfiguriert werden.

Der Custom Workflow Runner-Dienst (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) ist ein OSGi-Dienst und bietet zwei Optionen für die Konfiguration:

* Nachbearbeitung Workflows Pfad (`postProcWorkflowsByPath`): Es können mehrere Workflow-Modelle aufgeführt werden, die auf unterschiedlichen Repository-Pfaden basieren. Pfade und Modelle sollten durch einen Doppelpunkt voneinander getrennt werden. Einfache Repository-Pfade werden unterstützt und sollten einem Workflow-Modell im `/var` Pfad zugeordnet werden. Beispiel: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* Nachbearbeitung Workflows nach Ausdruck (`postProcWorkflowsByExpression`): Es können mehrere Workflow-Modelle basierend auf unterschiedlichen regulären Ausdrücken aufgelistet werden. Ausdruck und Modelle sollten durch einen Doppelpunkt getrennt werden. Der reguläre Ausdruck sollte direkt auf den Asset-Knoten und nicht auf eine der Darstellungen oder Dateien verweisen. Beispiel: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>Die Konfiguration des benutzerdefinierten Workflow Runner ist eine Konfiguration eines OSGi-Dienstes. Informationen zum Bereitstellen einer OSGi-Konfiguration finden Sie unter [Bereitstellung in Experience Manager](/help/implementing/deploying/overview.md) .
> OSGi-Webkonsole ist im Gegensatz zu lokalen und verwalteten Services-Bereitstellungen von AEM nicht direkt in den Cloud-Dienstbereitstellungen verfügbar.

Weitere Informationen darüber, welcher standardmäßige Workflow-Schritt im Arbeitsablauf für die Nachbearbeitung verwendet werden kann, finden Sie unter [Workflow-Schritte im Arbeitsablauf](developer-reference-material-apis.md#post-processing-workflows-steps) für die Nachbearbeitung in der Developer-Referenz.
