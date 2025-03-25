---
title: Verwenden von Regelsätzen zum Konvertieren von URLs
description: Erfahren Sie, wie Sie in Dynamic Media Regelsätze bereitstellen, um URLs zu konvertieren. Regelsätze sind Anweisungen, die in einer Skriptsprache (beispielsweise JavaScript) abgefasst werden. Sie werten XML-Daten aus und führen bestimmte Aktionen durch, falls die Daten die festgelegten Bedingungen erfüllen.
contentOwner: Rick Brough
feature: Rulesets,Troubleshooting,Upload,Best Practices
role: User
exl-id: f8010125-ba89-406a-bede-f6aa2f858c70
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 95%

---

# Verwenden von Regelsätzen zum Konvertieren von URLs {#using-rulesets-to-transform-urls}

In Dynamic Media haben Sie die Möglichkeit, Regelsätze bereitzustellen, um URLs zu konvertieren. Regelsätze sind Anweisungen, die in einer Skriptsprache (beispielsweise JavaScript) abgefasst werden. Sie werten XML-Daten aus und führen bestimmte Aktionen durch, falls die Daten die festgelegten Bedingungen erfüllen. Jede Regel besteht mindestens aus einer Bedingung und einer Aktion. Eine Regel vergleicht die XML-Daten mit den Bedingungen. Wenn eine Bedingung erfüllt ist, wird die entsprechende Aktion durchgeführt. Beispiele für Regelsätze:

* Hinzufügen eines Suffix vom MIME-Typ. Viele Services und Websites benötigen Bildsuffixe. So wird beispielsweise an eine URL das Suffix `.jpg` angefügt.
* Erstellen eines Ordnerpfads zur URL für SEO (Search Engine Optimization)-Zwecke

  Weitere Informationen finden Sie unter [Unterstützung von SEO durch Dynamic Media Classic](/help/assets/dynamic-media/assets/s7_seo.pdf).

* Hinzufügen von Metadaten zur URL für SEO (Search Engine Optimization)

  Weitere Informationen finden Sie unter [Unterstützung von SEO durch Dynamic Media Classic](/help/assets/dynamic-media/assets/s7_seo.pdf).

* Einstellen der Content-Disposition zum Auslösen eines Downloads
* Vereinfachen der URLs für Vorlagen zur Bildbearbeitung für die Personalisierung. Ändern Sie beispielsweise `rgb{XX,YY,ZZ}` in die RTF-fähige `\redXX\greenYY\blueZZ`

* Anfordern bestimmter zu kodierender Zeichen wie `$`, `{` und `}` und bestimmter für ImageServer zu dekodierender Zeichen. Facebook funktioniert beispielsweise nicht mit URLs, die Sonderzeichen enthalten.

Im Zusammenhang mit Dynamic Media können Websites, die ein XML-basiertes System zur Verwaltung von Asset-Informationen verwenden, XML-Dateien in Dynamic Media hochladen. Sie können eine dieser Dateien als Regelsatzdatei zur Vorverarbeitung für die Verarbeitung des Dynamic Media-Assets festlegen. Mit dieser Datei wird das Standard-URL-Protokollformat neu strukturiert und an die Geschäftslogik der in Dynamic Media integrierten Systeme angepasst. Sie geben eine XML-Datei an, die als Dateipfad für die Regeldefinitionen dienen soll.

>[!CAUTION]
>
>Verwenden Sie Regelsätze mit Vorsicht. Sie können verhindern, dass Dynamic Media-Inhalte auf Ihrer Website angezeigt werden.

Mit den als Beispiele verfügbaren Regelsätzen können Sie Ihren eigenen Regelsatz erstellen.
Siehe [Regelsatzreferenz](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/rule-set-reference/c-rule-set-reference).

Stellen Sie wie bei allen Regelsatzerstellungen sicher, dass Ihre XML-Datei gültig ist, bevor Sie sie mit einem XML-Validator-Programm wie xmlvalid hochladen.

Stellen Sie außerdem sicher, dass der Regelsatz zunächst in einer Staging-Umgebung getestet wurde, die sich nicht auf die Live-Produktionsumgebung auswirkt.
Für Produktions- und Testumgebungen sind in der Regel unterschiedliche Anmeldungen erforderlich.

Informationen zum Anmelden finden Sie unter dem [Adobe Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/getting-started/signing-out).

<!-- OBSOLETE CONTENT * **NA staging environment** login page: [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **EMEA staging environment** login page: [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **JAPAC staging environment** login page: [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/) -->



## Bereitstellen von XML-Regelsätzen {#deploy-xml-rule-sets}

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/getting-started/signing-out) und melden Sie sich bei Ihrem Konto an.

   Ihre Benutzer- und Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Sie nicht über diese Informationen verfügen, wenden Sie sich an den Support.

1. Laden Sie Ihre Regelsatzdatei wie folgt hoch:

   * Wählen Sie in der Symbolleiste für globale Navigation **[!UICONTROL Hochladen]** aus.
   * Wählen Sie auf der Seite **[!UICONTROL Hochladen]** in der linken oberen Ecke **[!UICONTROL Durchsuchen]** aus.
   * Navigieren Sie im Dialogfeld **[!UICONTROL Öffnen]** zu Ihrer Regelsatzdatei (XML).
   * Wählen Sie die Datei und dann **[!UICONTROL Öffnen]** aus.
   * Wählen Sie rechts auf der Seite **[!UICONTROL Hochladen]** einen Zielordner für die Regelsatzdatei aus.
   * Stellen Sie sicher, dass die Option „Nach Hochladen veröffentlichen“ am unteren Rand der Seite markiert ist.
   * Wählen Sie in der rechten unteren Ecke der Seite **[!UICONTROL Upload starten]** aus.
   * Wählen Sie in der globalen Navigationsleiste **[!UICONTROL Aufträge]** aus, um den Status der Upload-Aufträge zu prüfen. Wenn in der Spalte **[!UICONTROL Status]** auf der Seite **[!UICONTROL Auftrag]** der Status „Hochladen abgeschlossen“ angezeigt wird, fahren Sie mit den nächsten Schritten fort.

1. Navigieren Sie in der Navigationsleiste im oberen Teil der Seite zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Veröffentlichungseinrichtung]** > **[!UICONTROL Image-Server]**.
1. Suchen Sie auf der Seite **[!UICONTROL Veröffentlichung zum Image-Server]** in der Gruppe **[!UICONTROL Katalogverwaltung]** den Pfad **[!UICONTROL Dateipfad für Regeldefinitionen]** und wählen Sie **[!UICONTROL Auswählen]** aus.
1. Wählen Sie auf der Seite **[!UICONTROL Regeldefinitionsdatei (XML) auswählen]** die Regelsatzdatei und dann in der rechten unteren Ecke der Seite **[!UICONTROL Auswählen]** aus.
1. Wählen Sie in der rechten unteren Ecke der Seite „Einstellungen“ **[!UICONTROL Schließen]** aus.
1. Führen Sie einen Auftrag zur Veröffentlichung des Image-Servers aus.

   Die Bedingungen des Regelsatzes werden auf die Anforderungen an die Live-Image-Server von Dynamic Media angewendet.

   Wenn Sie Änderungen an der Regelsatzdatei vornehmen, werden die Änderungen sofort angewendet, wenn Sie die aktualisierte Regelsatzdatei erneut hochladen oder veröffentlichen.
