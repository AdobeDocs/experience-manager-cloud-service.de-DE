---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 64d88b9af48f1c5736ef668ae00fb29e9bfad9f7
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 15%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 13206 {#release-13206}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 13206 zusammengefasst, das am 22. August 2023 veröffentlicht wurde. Diese Wartungsversion ersetzt die Versionen 13173 und 13099, um ein Problem zu beheben, das sich auf die Posteingangsfunktion auswirkt.

2023.8.0 Die Funktionsaktivierung stellt das vollständige Funktionssatz für dieses Maintenance Release bereit. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-13206}

- SITES-13906: GraphQL - Upgrade auf graphql-java 20.1.
- SITES-8972: GraphQL - Hinzufügen einer Optionsbeschriftung in JSON für den Auflistungsdatentyp.
- SITES-9689: GraphQL - Fügen Sie Titel und Beschreibung in JSON für den Content Reference-Datentyp hinzu.
- SITES-13052: Inhaltsfragmente - Exportieren von Inhaltsfragmenten in Adobe Target.

### Behobene Probleme {#fixed-issues-13206}

- SITES-14937: MSM - Rollout-Konfigurationen von übergeordnetem Wert übernehmen wird umgeschaltet, wenn auf Live Copies auf Speichern und schließen geklickt wird.
- SITES-14847: Inhaltsfragmente - Inhaltsfragmentlinks werden nicht hervorgehoben.
- SITES-11620: Inhaltsfragmente - Der Pfad &quot;Verweise&quot;ist in der Benutzeroberfläche leicht abgeschnitten.
- SITES-14171: GraphQL - Zirkuläre Referenzen sind für zwischengespeicherte Daten in einigen Fällen nicht beschädigt.
- SITES-14577: Experience Fragments - Bulk Publish funktioniert nicht für Live Copies.
- SITES-14341: Administrator-Benutzeroberfläche - Inkonsistentes Verhalten der Schaltfläche &quot;Eigenschaften&quot;, wenn Löschberechtigungen entfernt werden.
- SITES-11000: Administrator-Benutzeroberfläche - Verweise: Eingehende Links fehlen auf einigen Seiten.
- SITES-11559: Admin-Benutzeroberfläche - Verweise: Eingehende Links zeigen falsche Seiten an.
- SITES-14337: Admin-Benutzeroberfläche - Öffnen der Editor-Seite erzeugt in bestimmten Fällen einen Fehler.
- SITES-13425: ContextHub - Menüleiste wird beim Klicken auf die Schaltfläche ContextHub nicht angezeigt.
- CQ-4354266: Posteingangselemente können nicht geöffnet werden.
- CQ-4354279: Aktivitätsbericht kann nicht auf der Registerkarte Personalisierung angezeigt werden.
- FORMS-9971: Wenn ein adaptives Formular in einem anderen Gebietsschema wiedergegeben wird, wird die Sichtbarkeit von Komponenten ungenau interpretiert und angewendet.
- FORMS-9888: Wenn ein adaptives Formular so eingestellt ist, dass es bei der Formularübermittlung zu einer externen URL (Dankeseite) umgeleitet wird, kann es nicht zur externen URL umgeleitet werden.
- FORMS-9845: Nach dem Löschen eines Dropdown-Menüs mit dem Regeleditor bleiben die zuvor bereitgestellten Werte trotz der angeblichen Löschung erhalten.
- FORMS-9263: Wenn die Beschriftung eines Kontrollkästchens Sonderzeichen enthält und ein Benutzer auf das Kontrollkästchen klickt, wird das entsprechende Kontrollkästchen nicht aktiviert.
- FORMS-9254: Wenn ein Benutzer durch den Text der Komponente &quot;Geschäftsbedingungen&quot;blättert, wird das Kontrollkästchen innerhalb der Komponente automatisch aktiviert, auch bevor der Benutzer durch den gesamten Text gescrollt hat.
- FORMS-9045: Das Skript-Tag löst keine externen Fragmentverweise in der Basis-XDP auf.
- FORMS-9026: Beim Versuch, ein adaptives Formular mit einem JSON-Schema zu erstellen, das Enums mit leeren Zeichenfolgen enthält und ohne Fehler validiert, führt der Prozess zu einem Fehler. Nach dem Aktualisieren der Seite wird das Formular nicht ordnungsgemäß geladen, es zeigt ein leeres Formular zusammen mit einem Fehler in den Protokollen an.
- FORMS-8964: In Android™ Chrome/Firefox kann Text in der Textfeldkomponente nicht bearbeitet werden, wenn die maximale Zeichenbeschränkung erreicht ist.
- FORMS-8668: Übermäßige Java™-Stack-Dumps in Fehlerprotokollen, trotz funktionaler Formularwiedergabe, wodurch die Protokolldatei aufgebläht wird.
- FORMS-8554: Adaptive Forms mit aktiviertem verzögertem Laden funktioniert nicht im Vorschaumodus der Autoreninstanz.
- FORMS-8177: Wenn der Forms-Dienst aktiv ist, konnte die Ausnahme &quot;com.adobe.aem.formsndocuments.publish.AssetReferenceProvider konnte Asset-Abhängigkeiten nicht abrufen.&quot; auftritt. Der Fehler wird beim Deaktivieren des Formulardienstes ausgeblendet.
- FORMS-3691: Bei einigen Objekten fehlt das Scoping IIFE (Sofort aufgerufener Funktionsausdruck). Der primäre Zweck der Verwendung einer IIFE besteht darin, einen Bereich für Variablen innerhalb der Funktion zu erstellen, um zu verhindern, dass diese Variablen den globalen Umfang verschmutzen.
- SITES-15463: Sites-Vorlagen - Vorlagen können nicht veröffentlicht werden.

### Bekannte Probleme {#known-issues-13206}

- SITES-15359: Inhaltsfragmente - Das Variantennamensmuster stimmt nicht mit Varianten überein, die ```'_'``` in ihren Ressourcennamen.
- FORMS-10444: Adaptive Forms-Vorlagen - Vorlagen können nicht veröffentlicht werden (Problemumgehung: Verwenden Sie die Verteilungskonsole).
- CQ-4354191: Workflows - Benutzerdefinierter Starter kann aufgrund von auf nt:unstrukturierten Knoten vorhandenen Replikations-Metadaten mehrmals Trigger werden (Problemumgehung: Aktualisieren Sie Starter, um Replikations-Metadateneigenschaften auszuschließen, um Überschneidungen zu vermeiden).

### Eingebettete Technologien {#embedded-tech-13206}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [Oak-API 1.52.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
