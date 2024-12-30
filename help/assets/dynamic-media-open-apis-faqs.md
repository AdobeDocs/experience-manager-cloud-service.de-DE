---
title: Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen
description: Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen
role: User
exl-id: 3450e050-4b0b-4184-8e71-5e667d9ca721
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 100%

---

# Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen {#new-dynaminc-media-apis-frequently-asked-questions}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Das Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch zu Dynamic Media mit OpenAPI-Funktionen als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

+++**Sind alle Assets im Experience Manager Assets as a Cloud Service-Repository für die Suche und Bereitstellung mit Dynamic Media mit OpenAPI-Funktionen verfügbar?**

Nein, nur die [genehmigte und die neueste Version der Assets](/help/assets/approve-assets.md) sind für die Suche und Bereitstellung mit Dynamic Media mit OpenAPI-Funktionen verfügbar. Auf diese Weise wird die Markenkonsistenz in allen Kanälen und Anwendungen sichergestellt.

+++

+++**Wie können Admins neue und vorhandene Assets, die einem Ordner hinzugefügt wurden, als genehmigt markieren?**

Der Status eines Assets in Experience Manager Assets wird durch die Eigenschaft `jcr:content/metadata/dam:status` gesteuert. Die Werte dieser Eigenschaft können wie folgt lauten:

* Genehmigt

* Abgelehnt

* Änderungen angefordert

Experience Manager Assets kennzeichnet den Status „Genehmigt“ mithilfe eines auf der Asset-Karte verfügbaren Symbols „Genehmigt“, wie in den folgenden Bildern für Admin- und Asset-Ansicht dargestellt:

**Admin-Ansicht**

![Genehmigte Assets in der Admin-Ansicht](/help/assets/assets/approved-assets-thumbs-up.png)

**Assets-Ansicht**

![Genehmigte Assets in der Assets-Ansicht](/help/assets/assets/approved-assets-thumbs-up-assets-view.png)


Informationen zum Genehmigen aller Assets in einem Ordner finden Sie in den Anweisungen zum [Genehmigen mehrerer Assets in einem Ordner](/help/assets/approve-assets.md#bulk-approve-assets). Es gibt auch ein Video, in dem der gesamte Prozess dargestellt ist.

Nachdem Sie einen Ordner für die Massengenehmigung eingerichtet haben, werden alle neuen Assets, die zum Ordner hinzugefügt werden, automatisch genehmigt. Alle vorhandenen Assets werden nach der erneuten Verarbeitung von Assets genehmigt. Anweisungen zur erneuten Verarbeitung von Assets finden Sie unter [Erneutes Verarbeiten digitaler Assets](/help/assets/reprocessing.md). Wenn Sie nicht genehmigte Assets aus einem anderen Ordner kopieren oder verschieben, müssen Sie [die Assets erneut verarbeiten](/help/assets/reprocessing.md).

Das Asset wird als `Rejected` markiert, wenn die bzw. der Admin die Werte `Rejected` oder `Changes requested` angibt. Experience Manager Assets kennzeichnet den Status „Abgelehnt“ mit ![Assets ablehnen](/help/assets/assets/do-not-localize/reject-assets.svg). Dieses Symbol ist auf der Asset-Karte in der Admin-Ansicht verfügbar.

Gleichermaßen kennzeichnet Experience Manager Assets den Status „Abgelehnt“ in der Assets-Ansicht mithilfe des folgenden Status „Abgelehnt “auf der Asset-Karte:

![Abgelehnte Assets in der Assets-Ansicht](/help/assets/assets/rejected-assets-admin-view.png)


+++

+++**Wie können Sie dafür sorgen, dass die Rollen für Assets in der Admin-Ansicht in Experience Manager mithilfe der Benutzer- oder Gruppen-ID von Adobe IMS (Adobe Identity Management Services) festgelegt werden, um das Bereitstellungs- und Sucherlebnis sicher zu gestalten?**

Benutzende, die Zugriff auf die Adobe Experience Manager-Autorenumgebung benötigen, werden in der Admin Console von Adobe als Adobe IMS-Benutzende verwaltet. Informationen darüber, was Adobe IMS-Benutzende sind und wie sie in der Admin Console aufgerufen und verwaltet werden, finden Sie unter [Adobe IMS-Benutzende](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users).

+++

+++**Können Sie mehrere Assets gleichzeitig in einem Ordner genehmigen?**

Ja, Sie können mehrere Assets in einem Ordner gleichzeitig genehmigen.

Führen Sie die folgenden Schritte aus, um mehrere Assets gleichzeitig in der [!DNL Experience Manager Assets Admin view] zu genehmigen:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Scrollen Sie auf der Registerkarte **[!UICONTROL Allgemein]** nach unten zu **[!UICONTROL Überprüfungsstatus]**.
1. Ändern Sie den Überprüfungsstatus in **[!UICONTROL Genehmigt]**.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

So genehmigen Sie gleichzeitig mehrere Assets in einem Ordner in der Assets-Ansicht:

1. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Massenbearbeitung von Metadaten]**.

1. Wählen Sie im rechten Bereich im Abschnitt [!UICONTROL Eigenschaften] im Feld **[!UICONTROL Status]** die Option **[!UICONTROL Genehmigt]** aus.

1. Klicken Sie auf **[!UICONTROL Speichern]**.


+++

+++**Wie kann ich die Asset-Bereitstellung sichern und nach den Dynamic Media OpenAPIs suchen?**

Die zentrale Asset-Governance in Experience Manager ermöglicht es DAM-Admins oder Markenverantwortlichen, den Zugriff auf Assets zu verwalten. Sie können den Zugriff einschränken, indem sie Rollen konfigurieren oder Aktivierungs- und Deaktivierungszeiten für genehmigte Assets auf der Autorenseite festlegen, insbesondere auf der AEM as a Cloud Service-Autoreninstanz.

Endbenutzende, die nach Bereitstellungs-URLs suchen oder diese verwenden, können nach erfolgreichem Durchlaufen des Autorisierungsprozesses Zugriff auf eingeschränkte Assets erhalten.

Weitere Informationen finden Sie unter [Beschränken des Zugriffs auf Assets in Experience Manager](restrict-assets-delivery.md#authoring).

+++

+++**Wie erhalten Sie Berechtigungen zum Bearbeiten des Genehmigungsstatus eines Assets?**

Als DAM-Benutzerin oder -Benutzer verfügen Sie möglicherweise nicht über die Berechtigungen für das [Genehmigen von Assets](approve-assets.md#approve-assets). Um die Berechtigungen für das Bearbeiten des Genehmigungsstatus eines Assets zu erhalten, können Admins das standardmäßige oder jedes andere Metadatenschema bearbeiten, das auf den Asset-Ordner angewendet wird, um dem Feld **[!UICONTROL Überprüfungsstatus]** Bearbeitungsberechtigungen zu erteilen. Weitere Informationen finden Sie unter [Deaktivieren der Bearbeitung für das Feld „Überprüfungsstatus“](approve-assets.md#configuration).

+++

+++**Inwiefern unterscheidet sich Dynamic Media mit OpenAPI-Funktionen von der Dynamic Media-Lösung?**

Dynamic Media mit OpenAPI-Funktionen und Dynamic Media sind unterschiedliche Lösungen, die jeweils spezielle Bereitstellungsfunktionen bieten. Sie müssen Ihre spezifischen Anforderungen unbedingt gründlich prüfen, um die am besten geeignete Lösung zu finden, die Ihren Anforderungen entspricht.

Die allgemeine Empfehlung von Adobe ist, Dynamic Media mit OpenAPI-Stack für alle Integrations-Anwendungsfälle (Erstanbieter- oder Drittanbieter-Apps) zu verwenden. Wenn bereits eine Integration mit Dynamic Media-Stack vorhanden ist, wird empfohlen, diese nicht zu ändern, da sich die OpenAPI-Stack-URLs in der Struktur unterscheiden. Verwenden Sie den OpenAPI-Stack nur für alle ganz neuen Integrations-Anwendungsfälle. Wenn Ihr Anwendungsfall erweiterte Modifikatoren erfordert, die nicht mit dem OpenAPI-Stack verfügbar sind, vermeiden Sie den OpenAPI-Stack, bis Adobe die Lücke schließt. Der OpenAPI-Stack kann selbst für die grundlegende native Bereitstellung von AEM Assets Cloud Services ausgewertet werden, solange Ihr Anwendungsfall mit den Modifikatoren abgedeckt ist, die mit dem OpenAPI-Stack verfügbar sind. Zusammenfassend betrachtet können Dynamic Media und Dynamic Media mit OpenAPI-Stack je nach Art des Anwendungsfalls nebeneinander bestehen.

Im Folgenden finden Sie einige der wichtigsten Unterschiede zwischen Dynamic Media mit OpenAPI-Funktionen und Dynamic Media:

| Dynamic Media mit OpenAPI-Funktionen | Dynamic Media |
|---|---|
| [Nur mit Assets as a Cloud Service verfügbar](/help/assets/dynamic-media-open-apis-overview.md#prerequisites-dynaminc-media-open-apis) | Auch mit On-Premise oder Adobe Managed Services mit zusätzlichen Konfigurations- und Bereitstellungsschritten verfügbar. |
| [Eingeschränkter Satz unterstützter Bildmodifikatoren wie Breite, Höhe, Drehung, Spiegelung, Qualität und Format](/help/assets/deliver-assets-apis.md) | Umfassender Satz verfügbarer Bildmodifikatoren |
| [Eingeschränkte Asset-Bereitstellung basierend auf Benutzenden, Rollen, Datum und Uhrzeit](/help/assets/restrict-assets-delivery.md) | In Dynamic Media veröffentlichte Assets stehen allen Benutzenden zur Verfügung |
| Die meisten Entwickelnden sind mit OpenAPI-Spezifikationen vertraut. Durch Verwendung des [Micro-Frontend-Asset-Wählers](/help/assets/overview-asset-selector.md) lassen sich AEM Assets ganz einfach erweitern. | SOAP-basierte APIs, die bei der Entwicklung von Integrationsanpassungen zu einer Barriere werden. |
| Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Bereitstellungs-URLs übernommen. Mit einem niedrigen Time-to-Live(TTL)-Wert von 10 Minuten für die Dynamic Media mit OpenAPI-Funktion per CDN werden Aktualisierungen in weniger als 10 Minuten in allen Authoring- und Publishing-Oberflächen sichtbar. | Empfohlene CDN-TTL von 10 Stunden. Sie können den TTL-Wert mithilfe der Aktion zur Cache-Invalidierung überschreiben. |
| Für die Asset-Bereitstellung an nachgelagerte Anwendungen sind nur genehmigte Assets verfügbar, sodass in digitalen Erlebnissen nur markenkonforme Assets verwendet werden können. | Alle Aktualisierungen eines von Dynamic Media veröffentlichten Assets werden ohne Genehmigungs-Workflow automatisch veröffentlicht. Hierdurch ist nicht gewährleistet, dass die Assets in digitalen Erlebnissen markenkonform sind. |
| Auf der Anzahl der bereitgestellten Assets basierende Nutzungsberichte. Diese Funktion ist in Kürze verfügbar. | Nutzungsberichte sind nicht verfügbar. Diese Funktion ist in Kürze verfügbar. |
| Assets, die im Assets as a Cloud Service-Repository als abgelaufen markiert sind, stehen nachgelagerten Anwendungen nicht mehr zur Verfügung. | Kein inhärenter Asset-Ablauf. Ein Asset bleibt öffentlich, bis es aus dem AEM as a Cloud Service-Repository gelöscht wird. |
| Bildvorgaben und Funktionen für den intelligenten Zuschnitt von Videos werden nicht unterstützt. | Bildvorgaben und Funktionen für den intelligenten Zuschnitt von Videos werden unterstützt. |
| Dynamische Videocodierungen, die sicherstellen, dass basierend auf dem Eingabevideo die besten Codierungen bereitgestellt werden. Für die native Videobereitstellung ist keine Einrichtung erforderlich. | Standard-3-Codierungen unabhängig vom Eingabevideo (können sich auf die Leistung der Videobereitstellung auswirken). Sie müssen verschiedene Codierungen für unterschiedliche Video-Bitraten manuell einrichten. |
| Das Erraten einer auf der Asset-UID basierenden URL ist schwierig (ermöglicht die URL-Verschleierung), dafür bietet sie eine SEO-Optimierung. | Die URL-Verschleierung ist nur für URL-Abfrageparameter verfügbar. Asset-IDs (Asset-Namen) in URLs können erkannt werden. |

+++

+++**Wie geht Dynamic Media mit OpenAPI-Funktionen mit den Einschränkungen der Funktion „Connected Assets“ um?**

In der folgenden Tabelle sind die wichtigsten Unterschiede zwischen den beiden Lösungen aufgeführt:

| Dynamic Media mit OpenAPI-Funktionen | Connected Assets |
|---|---|
| Assets in der Remote-DAM-Bereitstellung sind in AEM as a Cloud Service verfügbar. | Assets in der Remote-DAM-Bereitstellung können in AEM as a Cloud Service oder Adobe Managed Services verfügbar sein. |
| Asset-Binärdateien werden nicht kopiert, wenn Assets in einer Remote-DAM-Bereitstellung in einer AEM Sites-Instanz verfügbar sind. | Asset-Binärdateien werden kopiert, wenn Assets in einer Remote-DAM-Bereitstellung in einer AEM Sites-Instanz verfügbar sind. |
| Unterstützung aller Asset-Formattypen, die von AEM Assets unterstützt werden. | Keine Unterstützung für Videos. |
| Sie können Dynamic Media in der lokalen Sites-Bereitstellung verwenden, während Sie Assets aus der Remote-DAM-Bereitstellung abrufen. | Dynamic Media ist in der lokalen Sites-Bereitstellung schreibgeschützt. |
| Die Anzahl der mit einer Remote-DAM-Bereitstellung verbundenen AEM Sites-Instanzen ist nicht beschränkt. Sie können den Zugriff auf Assets in der Sites-Instanz einschränken, indem Sie [Rollen für genehmigte Assets im Remote-DAM konfigurieren](/help/assets/restrict-assets-delivery.md). | Die Verbindung von AEM Sites-Instanzen mit der Remote-DAM-Bereitstellung ist auf maximal 4 AEM Sites-Instanzen beschränkt. Eine höhere Anzahl erfordert zusätzliche Tests. |
| Sowohl der Asset-Wähler als auch Dynamic Media mit OpenAPI-Funktionen sind erweiterbar, um benutzerdefinierte Integrationen zu ermöglichen. | Connected Assets-APIs sind nicht erweiterbar, um benutzerdefinierte Integrationen zuzulassen. |
| Alle Änderungen an genehmigten Assets, die in der Remote-DAM-Bereitstellung verfügbar sind, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden innerhalb einer kurzen TTL (Time-to-Live) von 10 Minuten automatisch in der Sites-Instanz übernommen. | Asset-Aktualisierungen in der Remote-DAM-Bereitstellung werden automatisch über Lebenszyklusereignisse verarbeitet. Dies nimmt im Vergleich zu Dynamic Media mit OpenAPI-Funktionen jedoch deutlich mehr Zeit in Anspruch. |
| Asset-Metadaten im Remote-DAM sind auch in der AEM Sites-Instanz verfügbar. | Asset-Metadaten im Remote-DAM sind nicht in der AEM Sites-Instanz verfügbar. |

+++
