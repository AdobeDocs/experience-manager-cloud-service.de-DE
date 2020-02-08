---
title: Asset-Mikrodienste für die Asset-Verarbeitung konfigurieren und verwenden
description: Erfahren Sie, wie Sie die Cloud-nativen Asset-Mikrodienste konfigurieren und verwenden, um Assets im Maßstab zu verarbeiten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Erste Schritte mit Asset Microservices {#get-started-using-asset-microservices}

<!--

* Current capabilities of asset microservices offered. If workers have names then list the names and give a one-liner description. (The feature-set is limited for now and continues to grow. So will this article continue to be updated.)
* How to access the microservices. UI. API. Is extending possible right now?
* Detailed list of what file formats and what processing is supported by which workflows/workers process.
* How/where can admins check what's already configured and provisioned.
* How to create new config or request for new provisioning/purchase.

* [DO NOT COVER?] Exceptions or limitations or link back to lack of parity with AEM 6.5.

-->

Asset-Mikrodienste bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud-Diensten, die von Adobe verwaltet werden, um eine optimale Verarbeitung verschiedener Asset-Typen und Verarbeitungsoptionen zu gewährleisten.

Die Asset-Verarbeitung wird auf der Grundlage der Konfiguration in den **[!UICONTROL Verarbeitungsprofilen]** durchgeführt, die ein Standardset bereitstellen und dem Administrator erlauben, eine spezifischere Asset-Verarbeitungskonfiguration hinzuzufügen. Um Erweiterbarkeit und vollständige Anpassung zu ermöglichen, ermöglicht die Verarbeitung von Assets eine optionale Konfiguration von Arbeitsabläufen nach der Verarbeitung, die dann vom Administrator erstellt und gepflegt werden.

Nachstehend wird ein übergeordneter Fluss zur Asset-Verarbeitung in Experience Manager als Cloud-Dienst dargestellt.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![asset-microservices-flow](assets/asset-microservices-flow.png)

>[!NOTE]
>
> Für Kunden, die von früheren Versionen von Experience Manager aktualisieren: Die in diesem Abschnitt beschriebene Asset-Verarbeitung ersetzt das Workflow-Modell &quot;DAM Update Asset&quot;, das zuvor für die Verarbeitung von Assets verwendet wurde. Die meisten Schritte zum Generieren von Standarddarstellungen und zum Erstellen von Metadaten werden durch die Verarbeitung von Asset-Mikrodiensten ersetzt. Die verbleibenden Schritte können, falls vorhanden, durch die Konfiguration des Arbeitsablaufs nach der Verarbeitung ersetzt werden.

## Erste Schritte mit der Asset-Verarbeitung {#get-started}

Die Asset-Verarbeitung mit Asset-Mikrodiensten wird mit einer Standardkonfiguration vorkonfiguriert, sodass die vom System benötigten Standarddarstellungen verfügbar sind. Außerdem stellen Sie sicher, dass Metadaten-Extraktion und Textextraktion verfügbar sind. Benutzer können sofort mit dem Hochladen oder Aktualisieren von Assets beginnen. Die grundlegende Verarbeitung ist standardmäßig verfügbar.

Für bestimmte Anforderungen an die Generierung und Verarbeitung von Ausgabeformaten kann ein AEM-Administrator zusätzliche [!UICONTROL Verarbeitungsprofile]erstellen. Benutzer können einem bestimmten Ordner ein oder mehrere der verfügbaren Profile zuweisen, um eine weitere Verarbeitung zu erhalten. Angenommen, Sie erstellen Web-, Mobil- und Tablet-spezifische Darstellungen. Das folgende Video zeigt, wie Sie [!UICONTROL Verarbeitungsprofile] erstellen und anwenden und auf die erstellten Darstellungen zugreifen.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)

Informationen zum Ändern des vorhandenen Profils finden Sie unter [Konfigurationen für Asset-Mikrodienste](#configure-asset-microservices).
Informationen zum Erstellen benutzerdefinierter Verarbeitungsprofile, die spezifisch für Ihre benutzerdefinierten Anforderungen sind, wie z. B. zur Integration in andere Systeme, finden Sie unter Arbeitsabläufe [nach der Verarbeitung](#post-processing-workflows).

## Konfigurationen für Asset Microservices {#configure-asset-microservices}

Um Asset-Mikrodienste zu konfigurieren, können Administratoren die Konfigurationsoberfläche unter **[!UICONTROL Tools > Assets > Verarbeitungsprofile]** verwenden.

### Standardkonfiguration {#default-config}

Bei der Standardkonfiguration wird nur das [!UICONTROL Standard] -Verarbeitungsprofil konfiguriert. Es handelt sich um eine integrierte Version, die nicht verändert werden kann. Es wird immer ausgeführt, um sicherzustellen, dass die gesamte für die Anwendung erforderliche Verarbeitung stattfindet.

![processing-profiles-standard](assets/processing-profiles-standard.png)

Das Standard-Verarbeitungsprofil bietet die folgende Verarbeitungskonfiguration:

* Standardmäßige Miniaturansichten, die von der Asset-Benutzeroberfläche verwendet werden (48, 140 und 319 px)
* Große Vorschau (Webdarstellung - 1280 px)
* Metadatenextraktion
* Textextrahierung

### Unterstützte Dateiformate {#supported-file-formats}

Asset Microservices bieten Unterstützung für eine Vielzahl von Dateiformaten, was die Möglichkeit betrifft, Darstellungen zu erstellen oder Metadaten zu extrahieren. Die vollständige Liste finden Sie unter [Unterstützte Dateiformate](file-format-support.md) .

### Zusätzliche Verarbeitungsprofile hinzufügen {#processing-profiles}

Zusätzliche Verarbeitungsprofile können mit der Aktion **[!UICONTROL Erstellen]** hinzugefügt werden.

Jede Konfiguration des Verarbeitungsprofils enthält eine Liste der Darstellungen. Für jede Darstellung können Sie Folgendes angeben:

* Darstellungsname
* Darstellungsformat (JPEG, PNG oder GIF werden unterstützt)
* Darstellungsbreite und -höhe in Pixel (sofern nicht angegeben, wird die vollständige Pixelgröße des Originals angenommen)
* Darstellungsqualität (für JPEG) in Prozent
* Eingeschlossene und ausgeschlossene MIME-Typen definieren, für welche Asset-Typen das Verarbeitungsprofil gilt

![processing-profiles-adding](assets/processing-profiles-adding.png)

Wenn ein neues Verarbeitungsprofil gespeichert wird, wird es der Liste der konfigurierten Verarbeitungsprofile hinzugefügt. Diese Verarbeitungsprofile können dann auf Ordner in der Ordnerhierarchie angewendet werden, um sie für das Hochladen von Assets und die dort durchgeführten Assets effektiv zu gestalten.

![processing-profiles-list](assets/processing-profiles-list.png)

#### Darstellungsbreite und -höhe {#rendition-width-height}

Die Angabe der Breite und Höhe der Darstellung bietet die maximale Größe des generierten Ausgabebilds. Asset Microservice versucht, die größtmögliche Darstellung zu erstellen, deren Breite und Höhe nicht größer als die angegebene Breite bzw. Höhe ist. Das Seitenverhältnis wird beibehalten, d. h. es entspricht dem Original.

Ein leerer Wert bedeutet, dass bei der Asset-Verarbeitung die Pixelabmessungen des Originals berücksichtigt werden.

#### MIME-Typeinschlussregeln {#mime-type-inclusion-rules}

Wenn ein Asset mit einem bestimmten Mime-Typ verarbeitet wird, wird der Mime-Typ zunächst mit dem Wert für die ausgeschlossenen Mime-Typen für die Darstellungsspezifikation verglichen. Wenn es mit dieser Liste übereinstimmt, wird diese spezifische Darstellung nicht für das Asset generiert (&quot;Blacklisting&quot;).

Andernfalls wird der Mime-Typ mit dem eingeschlossenen Mime-Typ verglichen. Wenn er mit der Liste übereinstimmt, wird die Darstellung generiert (&quot;Whitelisting&quot;).

#### Spezielle FPO-Darstellung {#special-fpo-rendition}

Das Verarbeitungsprofil kann eine spezielle &quot;FPO-Darstellung&quot;enthalten, die verwendet wird, wenn [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) mit Adobe InDesign verwendet wird, um direkte Links zu Assets aus Experience Manager in InDesign-Dokumente zu platzieren.

In der Adobe Asset Link- [Dokumentation](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) erfahren Sie, ob Sie das Programm für Ihr Verarbeitungsprofil aktivieren müssen.

## Verwenden von Asset-Mikrodiensten zur Verarbeitung von Assets {#use-asset-microservices}

Nachdem zusätzliche Verarbeitungsprofile erstellt wurden, müssen sie auf bestimmte Ordner angewendet werden, damit Experience Manager sie bei der Verarbeitung von Assets verwendet, die in diesen Ordnern hochgeladen oder aktualisiert wurden. Das integrierte, standardmäßige Verarbeitungsprofil wird immer ausgeführt.

Es gibt zwei Möglichkeiten, Verarbeitungsprofile auf Ordner anzuwenden:

* Administratoren können unter **[!UICONTROL Extras > Assets > Verarbeitungsprofile]** eine Definition des Verarbeitungsprofils auswählen und die Aktion Profile auf Ordner **[!UICONTROL anwenden]** verwenden. Dadurch wird ein Inhaltsbrowser geöffnet, mit dem Sie zu bestimmten Ordnern navigieren, diese auswählen und die Anwendung des Profils bestätigen können.
* Die Benutzer können einen Ordner in der Benutzeroberfläche &quot;Assets&quot;auswählen, die Aktion &quot; **[!UICONTROL Eigenschaften]** &quot;zum Öffnen der Ordnereigenschaften verwenden, auf die Registerkarte &quot; **[!UICONTROL Verarbeitungsprofile]** &quot;klicken und in der Dropdown-Liste das richtige Verarbeitungsprofil für diesen Ordner auswählen. Die Auswahl wird bei der Aktion **[!UICONTROL Speichern und Schließen]** gespeichert.

>[!NOTE]
>
>Nur ein Verarbeitungsprofil kann auf einen bestimmten Ordner angewendet werden. Wenn Sie weitere Darstellungen erstellen müssen, können Sie dem Verarbeitungsprofil weitere Darstellungsdefinitionen hinzufügen.

Nachdem ein Verarbeitungsprofil auf einen Ordner angewendet wurde, werden alle neuen Assets, die in diesen Ordner oder in dessen Unterordnern hochgeladen (oder aktualisiert) wurden, mit dem konfigurierten zusätzlichen Verarbeitungsprofil verarbeitet. Diese zusätzliche Verarbeitung erfolgt zusätzlich zum Standardprofil. Wenn Sie mehrere Profile auf einen Ordner anwenden, werden die hochgeladenen oder aktualisierten Elemente mit jedem dieser Profile verarbeitet.

>[!NOTE]
>
>Wenn Assets in einen Ordner hochgeladen werden, prüft Experience Manager die Eigenschaften des zugehörigen Ordners auf ein Verarbeitungsprofil. Wenn keine Anwendung erfolgt, wird sie in der Ordnerstruktur angezeigt, bis ein Verarbeitungsprofil angewendet wurde, und verwendet es für das Asset. Das bedeutet, dass ein Verarbeitungsprofil, das auf einen Ordner angewendet wird, für die gesamte Struktur funktioniert, aber mit einem anderen Profil, das auf einen Unterordner angewendet wird, überschrieben werden kann.

Benutzer können überprüfen, ob die Verarbeitung tatsächlich stattgefunden hat, indem sie ein neu hochgeladenes Asset öffnen, für das die Verarbeitung abgeschlossen ist, die Asset-Vorschau öffnen und auf die **[!UICONTROL Ausgabeansicht]** der linken Leiste klicken. Die spezifischen Darstellungen im Verarbeitungsprofil, für die der Typ des jeweiligen Assets mit den Inklusionsregeln des Mime-Typs übereinstimmt, sollten sichtbar und zugänglich sein.

![Zusätzliche Darstellungen](assets/renditions-additional-renditions.png)*Abbildung: Beispiel zweier zusätzlicher Darstellungen, die von einem Verarbeitungsprofil generiert wurden, das auf den übergeordneten Ordner angewendet wurde*

## Arbeitsabläufe nach der Verarbeitung {#post-processing-workflows}

In Fällen, in denen zusätzliche Verarbeitung von Assets erforderlich ist, die mit den Verarbeitungsprofilen nicht erreicht werden können, können der Konfiguration zusätzliche Nachbearbeitungsarbeitsabläufe hinzugefügt werden. Dies ermöglicht das Hinzufügen einer vollständig angepassten Verarbeitung zusätzlich zur konfigurierbaren Verarbeitung mithilfe von Asset Microservices.

Nach der Verarbeitung ausgeführte Arbeitsabläufe nach der Verarbeitung werden, sofern konfiguriert, automatisch von AEM ausgeführt. Workflow-Starter müssen nicht manuell hinzugefügt werden, um sie auszulösen.

Beispiele dafür sind:

* benutzerdefinierte Workflow-Schritte zur Verarbeitung von Assets, z. B. Java-Code zur Generierung von Darstellungen aus proprietären Dateiformaten.
* Integrationen, um Assets von externen Systemen Metadaten oder Eigenschaften hinzuzufügen, z. B. Produkt- oder Prozessinformationen.
* zusätzliche Verarbeitung durch externe Dienste

Das Hinzufügen einer Workflow-Konfiguration für die Nachbearbeitung zu Experience Manager umfasst die folgenden Schritte:

* Erstellen eines oder mehrerer Workflow-Modelle. Sie werden als &quot;Workflow-Modelle nach der Verarbeitung&quot;bezeichnet, es handelt sich jedoch um normale AEM-Workflow-Modelle.
* Hinzufügen spezifischer Workflow-Schritte zu diesen Modellen. Diese Schritte werden basierend auf der Konfiguration des Workflow-Modells für die Assets ausgeführt.
* Der letzte Schritt eines solchen Modells muss der `DAM Update Asset Workflow Completed Process` Schritt sein. Dies ist erforderlich, um sicherzustellen, dass AEM weiß, dass die Verarbeitung beendet wurde und das Asset als verarbeitet (&quot;Neu&quot;) gekennzeichnet werden kann.
* Erstellen einer Konfiguration für den benutzerdefinierten Workflow Runner-Dienst, mit der die Ausführung eines Workflow-Modells für die Nachbearbeitung entweder nach Pfad (Ordnerspeicherort) oder regulärem Ausdruck konfiguriert werden kann

### Erstellen von Workflow-Modellen für die Nachbearbeitung

Workflow-Modelle nach der Verarbeitung sind normale AEM-Workflow-Modelle. Bitte erstellen Sie unterschiedliche, wenn Sie unterschiedliche Verarbeitungsschritte für verschiedene Repository-Speicherorte oder Asset-Typen benötigen.

Verarbeitungsschritte sollten je nach Bedarf hinzugefügt werden. Sie können alle unterstützten vordefinierten Schritte sowie alle benutzerdefinierten Workflow-Schritte verwenden.

Der letzte Schritt jedes Nachbearbeitungsablaufs muss der `DAM Update Asset Workflow Completed Process`sein. Dadurch wird sichergestellt, dass das Asset ordnungsgemäß als &quot;Verarbeitung abgeschlossen&quot;gekennzeichnet ist.

### Workflow-Ausführung nach der Verarbeitung konfigurieren

Um die Workflow-Modelle für die Nachbearbeitung so zu konfigurieren, dass sie für Assets ausgeführt werden, die nach Abschluss der Verarbeitung der Asset-Mikrodienste im System hochgeladen oder aktualisiert wurden, muss der Custom Workflow Runner-Dienst konfiguriert werden.

Der Custom Workflow Runner-Dienst (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) ist ein OSGi-Dienst und bietet zwei Optionen für die Konfiguration:

* Arbeitsabläufe nach der Verarbeitung nach Pfad (`postProcWorkflowsByPath`): Es können mehrere Workflow-Modelle basierend auf unterschiedlichen Repository-Pfaden aufgeführt werden. Pfade und Modelle sollten durch einen Doppelpunkt voneinander getrennt werden. Einfache Repository-Pfade werden unterstützt und sollten einem Workflow-Modell im `/var` Pfad zugeordnet werden. Beispiel: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* Arbeitsabläufe nach der Verarbeitung nach Ausdruck (`postProcWorkflowsByExpression`): Es können mehrere Workflow-Modelle basierend auf unterschiedlichen regulären Ausdrücken aufgelistet werden. Ausdrücke und Modelle sollten durch einen Doppelpunkt getrennt werden. Der reguläre Ausdruck sollte direkt auf den Asset-Knoten verweisen und nicht auf eine der Darstellungen oder Dateien. Beispiel: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>Die Konfiguration des benutzerdefinierten Workflow Runner ist eine Konfiguration eines OSGi-Dienstes. Informationen zum Bereitstellen einer OSGi-Konfiguration finden Sie unter [Bereitstellung in Experience Manager](/help/implementing/deploying/overview.md) .
> OSGi-Webkonsole ist im Gegensatz zu lokalen und verwalteten Services-Bereitstellungen von AEM nicht direkt in den Cloud-Dienstbereitstellungen verfügbar.

Weitere Informationen dazu, welche der Standard-Arbeitsablaufschritte im Arbeitsablauf für die Nachbearbeitung verwendet werden können, finden Sie unter [Arbeitsablaufschritte im Arbeitsablauf](developer-reference-material-apis.md#post-processing-workflows-steps) für die Nachbearbeitung in der Entwicklerreferenz.
