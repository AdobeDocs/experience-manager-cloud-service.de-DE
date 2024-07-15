---
title: Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen
description: Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 0%

---

# Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen {#new-dynaminc-media-apis-frequently-asked-questions}

+++**Sind alle Assets im Experience Manager Assets as a Cloud Service-Repository für die Suche und Bereitstellung mit Dynamic Media mit OpenAPI-Funktionen verfügbar?**

Nein, es sind nur die [genehmigte und die neueste Version der Assets](/help/assets/approved-assets.md) für die Suche und Bereitstellung mit Dynamic Media mit OpenAPI-Funktionen verfügbar, wodurch die Markenkonsistenz über alle Kanäle und Anwendungen hinweg gewährleistet ist.

+++

+++**Wie können Administratoren neue und vorhandene Assets, die einem Ordner hinzugefügt wurden, als genehmigt markieren?**

Der Status eines Assets in Experience Manager Assets wird durch die Eigenschaft `jcr:content/metadata/dam:status` gesteuert. Die Werte dieser Eigenschaft können wie folgt lauten:

* Genehmigt

* Abgelehnt

* Geforderte Änderungen

Experience Manager Assets unterscheidet den Status Genehmigt anhand von ![Assets genehmigen](assets/thumbs-up-icon.svg) , der auf der Asset-Karte verfügbar ist, wie in der folgenden Abbildung dargestellt:

![Symbol für genehmigte Assets](/help/assets/assets/approved-assets-thumbs-up.png)

Informationen zum Genehmigen aller Assets in einem Ordner finden Sie in den Anweisungen zum [Massen-Genehmigen von Assets in einem Ordner](/help/assets/approved-assets.md#bulk-approve-assets). Es gibt auch ein Video, das den gesamten Prozess darstellt.

Nachdem Sie einen Ordner für die Massengenehmigung eingerichtet haben, werden alle neuen Assets, die zum Ordner hinzugefügt werden, automatisch genehmigt. Alle vorhandenen Assets werden nach der erneuten Verarbeitung von Assets genehmigt. Anweisungen zur erneuten Verarbeitung von Assets finden Sie unter [Erneutes Verarbeiten digitaler Assets](/help/assets/reprocessing.md) . Wenn Sie nicht genehmigte Assets aus einem anderen Ordner kopieren oder verschieben, müssen Sie die Assets erneut verarbeiten.](/help/assets/reprocessing.md)[

Das Asset wird als `Rejected` markiert, wenn der Administrator die Werte `Rejected` oder `Changes requested` angibt. Experience Manager Assets unterscheidet den Status &quot;Abgelehnt&quot;mit ![Assets zurückweisen](/help/assets/assets/do-not-localize/reject-assets.svg) , der auf der Asset-Karte verfügbar ist.

+++

+++**Wie können Sie die Benutzer- oder Gruppen-ID von Adobe IMS (Adobe Identity Management Services) dazu bringen, die Rollen für Assets in der Experience Manager-Admin-Ansicht festzulegen, um die Bereitstellung und das Sucherlebnis sicherzustellen?**

Benutzer, die Zugriff auf die Experience Manager-Autorenumgebung benötigen, werden in der Adobe-Admin Console als Adobe IMS-Benutzer verwaltet. Informationen dazu, was Adobe IMS-Benutzer sind und wie sie in Admin Console aufgerufen und verwaltet werden, finden Sie unter [Adobe IMS-Benutzer](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=en).

+++

+++**Können Sie mehrere Assets gleichzeitig in einem Ordner genehmigen?**

Ja, Sie können mehrere Assets in einem Ordner gleichzeitig genehmigen.

Führen Sie die folgenden Schritte aus, um mehrere Assets gleichzeitig in [!DNL Experience Manager Assets] zu genehmigen:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Scrollen Sie auf der Registerkarte **[!UICONTROL Einfach]** nach unten zu **[!UICONTROL Prüfungsstatus]**.
1. Ändern Sie den Prüfungsstatus in &quot;**[!UICONTROL Genehmigt]**&quot;.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

+++

+++**Wie kann ich die Asset-Bereitstellung sichern und nach den Dynamic Media OpenAPIs suchen?**

Die zentrale Asset-Verwaltung in Experience Manager ermöglicht es DAM-Administratoren oder Brand Manager, den Zugriff auf Assets zu verwalten. Sie können den Zugriff einschränken, indem sie Rollen für genehmigte Assets auf der Autorenseite, insbesondere auf der AEM as a Cloud Service-Autoreninstanz, konfigurieren.

Endbenutzer, die nach Versand-URLs suchen oder diese verwenden, können nach erfolgreichem Bestehen des Autorisierungsprozesses Zugriff auf eingeschränkte Assets erhalten.

Weitere Informationen finden Sie unter [Beschränken des Zugriffs auf Assets in Experience Manager](restrict-assets-delivery.md#authoring).

+++

+++**Wie erhalten Sie Berechtigungen zum Bearbeiten des Genehmigungsstatus eines Assets?**

Als DAM-Benutzer sind Sie möglicherweise nicht berechtigt, [Assets zu genehmigen](approved-assets.md#approve-assets). Um die Berechtigungen zum Bearbeiten des Genehmigungsstatus eines Assets zu erhalten, können Administratoren das standardmäßige oder jedes andere Metadatenschema bearbeiten, das auf den Asset-Ordner angewendet wird, um dem Feld **[!UICONTROL Prüfungsstatus]** Bearbeitungsberechtigungen zu erteilen. Weitere Informationen finden Sie unter [Deaktivieren der Bearbeitung für das Feld Prüfungsstatus](approved-assets.md#configuration) .

+++

+++**Inwiefern unterscheidet sich Dynamic Media mit OpenAPI-Funktionen von Dynamic Media-Lösungen?**

Dynamic Media mit OpenAPI-Funktionen und Dynamic Media sind unterschiedliche Lösungen, die jeweils spezielle Bereitstellungsfunktionen bieten. Es ist unbedingt erforderlich, Ihre spezifischen Anforderungen gründlich zu überprüfen, um die am besten geeignete Lösung zu finden, die Ihren Anforderungen entspricht.

Im Folgenden finden Sie einige der wichtigsten Unterschiede zwischen Dynamic Media mit OpenAPI-Funktionen und Dynamic Media:

| Dynamic Media mit OpenAPI-Funktionen | Dynamic Media |
|---|---|
| [Nur mit Assets as a Cloud Service verfügbar](/help/assets/new-dynamic-media-overview.md#prerequisites-new-dynaminc-media-apis) | Auch mit On-Premise oder Adobe Managed Services mit zusätzlichen Konfigurations- und Bereitstellungsschritten verfügbar. |
| [Eingeschränkter Satz unterstützter Bild-Modifikatoren wie Breite, Höhe, Drehen, Spiegeln, Qualität und Format](/help/assets/deliver-assets-apis.md) | Rich Set verfügbarer Bild-Modifikatoren |
| [Eingeschränkte Asset-Bereitstellung basierend auf Benutzern und Rollen](/help/assets/restrict-assets-delivery.md) | In Dynamic Media veröffentlichte Assets stehen allen Benutzern zur Verfügung |
| Unterstützt smartes Zuschneiden von Bildern | Unterstützt smartes Zuschneiden von Bildern und Videos |
| Stack basierend auf OpenAPI-Spezifikationen, mit denen die meisten Entwickler übereinstimmen. Die AEM Assets-Erweiterbarkeit wird durch die Verwendung von [Micro Frontend Asset Selector](/help/assets/asset-selector.md) wirklich einfach. | SOAP-basierte APIs, die bei der Entwicklung von Integrationsanpassungen zu einer Barriere werden. |
| Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Bereitstellungs-URLs übernommen. Mit einem kurzen TTL-Wert (Time-to-Live) von 10 Minuten, der für Dynamic Media mit OpenAPI-Funktionen über CDN konfiguriert wurde, werden Aktualisierungen in weniger als 10 Minuten auf allen Authoring- und veröffentlichten Benutzeroberflächen sichtbar. | Empfohlene CDN TTL von 10 Stunden. Sie können den TTL-Wert mithilfe der Aktion zur Cache-Invalidierung überschreiben. |
| Nur genehmigte Assets sind für die Asset-Bereitstellung an nachgelagerte Anwendungen verfügbar, sodass für markengenehmigte Assets digitale Erlebnisse aktiviert werden. Bereitgestellte Assets berücksichtigen den Asset-Ablaufstatus in der -Autoreninstanz des AEM as a Cloud Service-Repositorys. | Alle Aktualisierungen eines von Dynamic Media veröffentlichten Assets werden ohne Genehmigungs-Workflow automatisch veröffentlicht, was in digitalen Erlebnissen nicht für markengenehmigte Assets sorgt. Kein inhärentes Asset-Ablaufdatum. Ein Asset bleibt öffentlich, bis es aus dem AEM as a Cloud Service-Repository gelöscht wird. |
| Nutzungsberichte basieren auf der Anzahl der bereitgestellten Assets. | Nutzungsberichte sind nicht verfügbar. |

+++

+++**Wie kann Dynamic Media mit OpenAPI-Funktionen die Einschränkungen der Funktion &quot;Connected Assets&quot;beheben?**

In der folgenden Tabelle sind die wichtigsten Unterschiede zwischen den beiden Lösungen aufgeführt:

| Dynamic Media mit OpenAPI-Funktionen | Connected Assets |
|---|---|
| Assets in der Remote-DAM-Bereitstellung ist in AEM as a Cloud Service verfügbar. | Assets in der Remote-DAM-Bereitstellung kann auf AEM as a Cloud Service oder Adobe Managed Services verfügbar sein. |
| Asset-Binärdateien werden nicht kopiert, wenn Assets in einer Remote-DAM-Bereitstellung in einer AEM Sites-Instanz verfügbar sind. | Asset-Binärdateien werden kopiert, wenn Assets in einer Remote-DAM-Bereitstellung auf einer AEM Sites-Instanz verfügbar sind. |
| Unterstützung aller Asset-Formattypen, die von AEM Assets unterstützt werden. | Keine Unterstützung für Videos. |
| Unterstützt smartes Zuschneiden von Bildern. | Unterstützung für smarte Zuschnitte und Bildvorgaben in Dynamic Media. |
| Sie können Dynamic Media in der lokalen Sites-Bereitstellung verwenden, während Sie Assets aus der Remote-DAM-Bereitstellung abrufen. | Dynamic Media in der lokalen Sites-Bereitstellung ist schreibgeschützt. |
| Die Anzahl der mit einer Remote-DAM-Bereitstellung verbundenen AEM Sites-Instanzen ist nicht beschränkt. Sie können [den Zugriff auf Assets in der Sites-Instanz einschränken, indem Sie die Rollen ](/help/assets/restrict-assets-delivery.md) für genehmigte Assets auf Remote-DAM konfigurieren. | Beschränkung der Verbindung von maximal 4 AEM Sites-Instanzen mit der Remote-DAM-Bereitstellung. Eine erhöhte Zahl erfordert zusätzliche Tests. |
| Sowohl der Asset-Selektor als auch Dynamic Media mit OpenAPI-Funktionen sind erweiterbar, um benutzerdefinierte Integrationen zu ermöglichen. | Connected Assets APIs sind nicht erweiterbar, um benutzerdefinierte Integrationen zuzulassen. |
| Alle Änderungen an genehmigten Assets, die in der Remote-DAM-Bereitstellung verfügbar sind, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden innerhalb eines kurzen TTL-Werts (Time-to-Live) von 10 Minuten automatisch in der Sites-Instanz übernommen. | Asset-Aktualisierungen bei Remote-DAM-Implementierungen werden automatisch über Lebenszyklusereignisse verarbeitet, im Vergleich zu Dynamic Media mit OpenAPI-Funktionen jedoch viel mehr Zeit in Anspruch nehmen. |
| Asset-Metadaten auf Remote-DAM sind auch in der AEM Sites-Instanz verfügbar. | Asset-Metadaten auf Remote-DAM sind in der AEM Sites-Instanz nicht verfügbar. |

+++



