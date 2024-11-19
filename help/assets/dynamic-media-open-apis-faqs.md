---
title: Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen
description: Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen
role: User
exl-id: 3450e050-4b0b-4184-8e71-5e667d9ca721
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 2%

---

# Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen {#new-dynaminc-media-apis-frequently-asked-questions}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch für Dynamic Media mit OpenAPI-Funktionen PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

+++**Sind alle Assets im Experience Manager Assets as a Cloud Service-Repository für die Suche und Bereitstellung mit Dynamic Media mit OpenAPI-Funktionen verfügbar?**

Nein, es sind nur die [genehmigte und die neueste Version der Assets](/help/assets/approve-assets.md) für die Suche und Bereitstellung mit Dynamic Media mit OpenAPI-Funktionen verfügbar, wodurch die Markenkonsistenz über alle Kanäle und Anwendungen hinweg gewährleistet ist.

+++

+++**Wie können Administratoren neue und vorhandene Assets, die einem Ordner hinzugefügt wurden, als genehmigt markieren?**

Der Status eines Assets in Experience Manager Assets wird durch die Eigenschaft `jcr:content/metadata/dam:status` gesteuert. Die Werte dieser Eigenschaft können wie folgt lauten:

* Genehmigt

* Abgelehnt

* Geforderte Änderungen

Experience Manager Assets unterscheidet den Status Genehmigt mithilfe eines auf der Asset-Karte verfügbaren genehmigten Symbols, wie in den folgenden Bildern für Admin- und Asset-Ansichten dargestellt:

**Admin-Ansicht**

![Genehmigte Assets in der Admin-Ansicht](/help/assets/assets/approved-assets-thumbs-up.png)

**Assets-Ansicht**

![Genehmigte Assets in der Assets-Ansicht](/help/assets/assets/approved-assets-thumbs-up-assets-view.png)


Informationen zum Genehmigen aller Assets in einem Ordner finden Sie in den Anweisungen zum [Massen-Genehmigen von Assets in einem Ordner](/help/assets/approve-assets.md#bulk-approve-assets). Es gibt auch ein Video, das den gesamten Prozess darstellt.

Nachdem Sie einen Ordner für die Massengenehmigung eingerichtet haben, werden alle neuen Assets, die zum Ordner hinzugefügt werden, automatisch genehmigt. Alle vorhandenen Assets werden nach der erneuten Verarbeitung von Assets genehmigt. Anweisungen zur erneuten Verarbeitung von Assets finden Sie unter [Erneutes Verarbeiten digitaler Assets](/help/assets/reprocessing.md) . Wenn Sie nicht genehmigte Assets aus einem anderen Ordner kopieren oder verschieben, müssen Sie die Assets erneut verarbeiten.](/help/assets/reprocessing.md)[

Das Asset wird als `Rejected` markiert, wenn der Administrator die Werte `Rejected` oder `Changes requested` angibt. Experience Manager Assets unterscheidet den Status &quot;Abgelehnt&quot;mit ![Assets zurückweisen](/help/assets/assets/do-not-localize/reject-assets.svg) , der auf der Asset-Karte in der Admin-Ansicht verfügbar ist.

Gleichermaßen unterscheidet Experience Manager Assets den Status Abgelehnt in der Assets-Ansicht mithilfe des folgenden Status Abgelehnt auf der Asset-Karte:

![Abgelehnte Assets in der Assets-Ansicht](/help/assets/assets/rejected-assets-admin-view.png)


+++

+++**Wie können Sie die Benutzer- oder Gruppen-ID von Adobe IMS (Adobe Identity Management Services) dazu bringen, die Rollen für Assets in der Experience Manager-Admin-Ansicht festzulegen, um die Bereitstellung und das Sucherlebnis sicherzustellen?**

Benutzer, die Zugriff auf die Experience Manager-Autorenumgebung benötigen, werden in der Adobe-Admin Console als Adobe IMS-Benutzer verwaltet. Informationen dazu, was Adobe IMS-Benutzer sind und wie sie in Admin Console aufgerufen und verwaltet werden, finden Sie unter [Adobe IMS-Benutzer](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=en).

+++

+++**Können Sie mehrere Assets gleichzeitig in einem Ordner genehmigen?**

Ja, Sie können mehrere Assets in einem Ordner gleichzeitig genehmigen.

Führen Sie die folgenden Schritte aus, um mehrere Assets gleichzeitig in [!DNL Experience Manager Assets Admin view] zu genehmigen:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Scrollen Sie auf der Registerkarte **[!UICONTROL Einfach]** nach unten zu **[!UICONTROL Prüfungsstatus]**.
1. Ändern Sie den Prüfungsstatus in &quot;**[!UICONTROL Genehmigt]**&quot;.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

So genehmigen Sie mehrere Assets gleichzeitig in einem Ordner in der Assets-Ansicht:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Massenmetadaten bearbeiten]**.

1. Wählen Sie **[!UICONTROL Genehmigt]** im Feld **[!UICONTROL Status]** aus, das im Abschnitt [!UICONTROL Eigenschaften] im rechten Bereich verfügbar ist.

1. Klicken Sie auf **[!UICONTROL Speichern]**.


+++

+++**Wie kann ich die Asset-Bereitstellung sichern und nach den Dynamic Media OpenAPIs suchen?**

Die zentrale Asset-Verwaltung in Experience Manager ermöglicht es DAM-Administratoren oder Brand Manager, den Zugriff auf Assets zu verwalten. Sie können den Zugriff einschränken, indem sie Rollen konfigurieren oder Aktivierungs- und Deaktivierungszeiten für genehmigte Assets auf der Autorenseite, insbesondere auf der AEM as a Cloud Service-Autoreninstanz, festlegen.

Endbenutzer, die nach Versand-URLs suchen oder diese verwenden, können nach erfolgreichem Bestehen des Autorisierungsprozesses Zugriff auf eingeschränkte Assets erhalten.

Weitere Informationen finden Sie unter [Beschränken des Zugriffs auf Assets in Experience Manager](restrict-assets-delivery.md#authoring).

+++

+++**Wie erhalten Sie Berechtigungen zum Bearbeiten des Genehmigungsstatus eines Assets?**

Als DAM-Benutzer sind Sie möglicherweise nicht berechtigt, [Assets zu genehmigen](approve-assets.md#approve-assets). Um die Berechtigungen zum Bearbeiten des Genehmigungsstatus eines Assets zu erhalten, können Administratoren das standardmäßige oder jedes andere Metadatenschema bearbeiten, das auf den Asset-Ordner angewendet wird, um dem Feld **[!UICONTROL Prüfungsstatus]** Bearbeitungsberechtigungen zu erteilen. Weitere Informationen finden Sie unter [Deaktivieren der Bearbeitung für das Feld Prüfungsstatus](approve-assets.md#configuration) .

+++

+++**Inwiefern unterscheidet sich Dynamic Media mit OpenAPI-Funktionen von Dynamic Media-Lösungen?**

Dynamic Media mit OpenAPI-Funktionen und Dynamic Media sind unterschiedliche Lösungen, die jeweils spezielle Bereitstellungsfunktionen bieten. Es ist unbedingt erforderlich, Ihre spezifischen Anforderungen gründlich zu überprüfen, um die am besten geeignete Lösung zu finden, die Ihren Anforderungen entspricht.

Die allgemeine Anleitung von Adobe besteht darin, Dynamic Media mit OpenAPI Stack für alle Anwendungsfälle der Integration (Erstanbieter- oder Drittanbieter-Apps) zu nutzen. Wenn bereits eine Integration mit Dynamic Media Stack vorhanden ist, wird empfohlen, sie nicht zu ändern, da die OpenAPI-Stack-URLs in der Struktur unterschiedlich sind. Verwenden Sie den OpenAPI-Stack nur für alle neuen Anwendungsfälle der Integration. Wenn Ihr Anwendungsfall erweiterte Modifikatoren erfordert, die nicht mit dem OpenAPI-Stack verfügbar sind, vermeiden Sie den OpenAPI-Stack, bis Adobe die Lücke schließt. Selbst für die grundlegende native Bereitstellung von AEM Assets-Cloud Services kann der OpenAPI-Stapel ausgewertet werden, solange Ihr Anwendungsfall mit den Modifikatoren abgedeckt ist, die mit dem OpenAPI-Stapel verfügbar sind. Abschließend können Dynamic Media und Dynamic Media mit OpenAPI-Stack je nach Art des Anwendungsfalls nebeneinander bestehen.

Im Folgenden finden Sie einige der wichtigsten Unterschiede zwischen Dynamic Media mit OpenAPI-Funktionen und Dynamic Media:

| Dynamic Media mit OpenAPI-Funktionen | Dynamic Media |
|---|---|
| [Nur mit Assets as a Cloud Service verfügbar](/help/assets/dynamic-media-open-apis-overview.md#prerequisites-dynaminc-media-open-apis) | Auch mit On-Premise oder Adobe Managed Services mit zusätzlichen Konfigurations- und Bereitstellungsschritten verfügbar. |
| [Eingeschränkter Satz unterstützter Bild-Modifikatoren wie Breite, Höhe, Drehen, Spiegeln, Qualität und Format](/help/assets/deliver-assets-apis.md) | Rich Set verfügbarer Bild-Modifikatoren |
| [Eingeschränkte Asset-Bereitstellung basierend auf Benutzern, Rollen, Datum und Uhrzeit](/help/assets/restrict-assets-delivery.md) | In Dynamic Media veröffentlichte Assets stehen allen Benutzern zur Verfügung |
| Die meisten Entwickler sind mit OpenAPI-Spezifikationen vertraut. Die AEM Assets-Erweiterbarkeit wird durch die Verwendung von [Micro-Frontend-Asset-Selektor](/help/assets/overview-asset-selector.md) wirklich einfach. | SOAP-basierte APIs, die bei der Entwicklung von Integrationsanpassungen zu einer Barriere werden. |
| Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Bereitstellungs-URLs übernommen. Mit einem kurzen TTL-Wert (Time-to-Live) von 10 Minuten, der für Dynamic Media mit OpenAPI-Funktionen über CDN konfiguriert wurde, werden Aktualisierungen in weniger als 10 Minuten auf allen Authoring- und veröffentlichten Benutzeroberflächen sichtbar. | Empfohlene CDN TTL von 10 Stunden. Sie können den TTL-Wert mithilfe der Aktion zur Cache-Invalidierung überschreiben. |
| Nur genehmigte Assets sind für die Asset-Bereitstellung an nachgelagerte Anwendungen verfügbar, sodass für markengenehmigte Assets digitale Erlebnisse aktiviert werden. | Alle Aktualisierungen eines von Dynamic Media veröffentlichten Assets werden ohne Genehmigungs-Workflow automatisch veröffentlicht, was in digitalen Erlebnissen nicht für markengenehmigte Assets sorgt. |
| Nutzungsberichte basieren auf der Anzahl der bereitgestellten Assets. Diese Funktion wird in Kürze verfügbar sein. | Nutzungsberichte sind nicht verfügbar. Diese Funktion wird in Kürze verfügbar sein. |
| Assets, das im Assets as a Cloud Service-Repository als abgelaufen markiert ist, steht nachgelagerten Anwendungen nicht mehr zur Verfügung. | Kein inhärentes Asset-Ablaufdatum. Ein Asset bleibt öffentlich, bis es aus dem AEM as a Cloud Service-Repository gelöscht wird. |
| Bildvorgaben und Funktionen für smartes Zuschneiden von Videos werden nicht unterstützt. | Unterstützt Bildvorgaben und Funktionen für smartes Zuschneiden von Videos. |
| Dynamische Videokodierungen, die sicherstellen, dass die besten Kodierungen basierend auf dem Eingabevideo bereitgestellt werden. Für die Bereitstellung nativer Videos ist kein Setup erforderlich. | Standard-3-Kodierungen unabhängig vom Eingangsvideo (können sich auf die Leistung der Videobereitstellung auswirken). Sie müssen manuell verschiedene Kodierungen für unterschiedliche Video-Bitraten einrichten. |
| Es ist schwierig, Asset-UID-basierte URLs zu erraten (ermöglicht die URL-Verschleierung), SEO ist jedoch optimiert. | URL-Verschleierung nur für URL-Abfrageparameter verfügbar. Assets IDs (Asset-Namen) in URLs können erkannt werden. |

+++

+++**Wie geht Dynamic Media mit OpenAPI-Funktionen auf die Einschränkungen der Funktion &quot;Connected Assets&quot;ein?**

In der folgenden Tabelle sind die wichtigsten Unterschiede zwischen den beiden Lösungen aufgeführt:

| Dynamic Media mit OpenAPI-Funktionen | Connected Assets |
|---|---|
| Assets in der Remote-DAM-Bereitstellung ist in AEM as a Cloud Service verfügbar. | Assets in der Remote-DAM-Bereitstellung kann auf AEM as a Cloud Service oder Adobe Managed Services verfügbar sein. |
| Asset-Binärdateien werden nicht kopiert, wenn Assets in einer Remote-DAM-Bereitstellung in einer AEM Sites-Instanz verfügbar sind. | Asset-Binärdateien werden kopiert, wenn Assets in einer Remote-DAM-Bereitstellung auf einer AEM Sites-Instanz verfügbar sind. |
| Unterstützung aller Asset-Formattypen, die von AEM Assets unterstützt werden. | Keine Unterstützung für Videos. |
| Sie können Dynamic Media in der lokalen Sites-Bereitstellung verwenden, während Sie Assets aus der Remote-DAM-Bereitstellung abrufen. | Dynamic Media in der lokalen Sites-Bereitstellung ist schreibgeschützt. |
| Die Anzahl der mit einer Remote-DAM-Bereitstellung verbundenen AEM Sites-Instanzen ist nicht beschränkt. Sie können [den Zugriff auf Assets in der Sites-Instanz einschränken, indem Sie die Rollen ](/help/assets/restrict-assets-delivery.md) für genehmigte Assets auf Remote-DAM konfigurieren. | Beschränkung der Verbindung von maximal 4 AEM Sites-Instanzen mit der Remote-DAM-Bereitstellung. Eine erhöhte Zahl erfordert zusätzliche Tests. |
| Sowohl der Asset-Selektor als auch Dynamic Media mit OpenAPI-Funktionen sind erweiterbar, um benutzerdefinierte Integrationen zu ermöglichen. | Connected Assets APIs sind nicht erweiterbar, um benutzerdefinierte Integrationen zuzulassen. |
| Alle Änderungen an genehmigten Assets, die in der Remote-DAM-Bereitstellung verfügbar sind, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden innerhalb eines kurzen TTL-Werts (Time-to-Live) von 10 Minuten automatisch in der Sites-Instanz übernommen. | Asset-Aktualisierungen bei Remote-DAM-Implementierungen werden automatisch über Lebenszyklusereignisse verarbeitet, im Vergleich zu Dynamic Media mit OpenAPI-Funktionen jedoch viel mehr Zeit in Anspruch nehmen. |
| Asset-Metadaten auf Remote-DAM sind auch in der AEM Sites-Instanz verfügbar. | Asset-Metadaten auf Remote-DAM sind in der AEM Sites-Instanz nicht verfügbar. |

+++
