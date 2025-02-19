---
title: Internationalisierung von UI-Zeichenfolgen
description: AEM stellt eine Konsole für die Verwaltung der verschiedenen Übersetzungen von Texten bereit, die in der Komponentenbenutzeroberfläche verwendet werden.
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4b363473-3c5e-4d8e-97d6-b7b96ccf9e58
source-git-commit: f7aeec56d2eb10cdeb7efe63ffb15ed8af6a36e0
workflow-type: ht
source-wordcount: '654'
ht-degree: 100%

---

# Verwalten von Wörterbüchern mithilfe des Übersetzers{#using-translator-to-manage-dictionaries}

AEM stellt eine Konsole für die Verwaltung der verschiedenen Übersetzungen von Texten bereit, die auf der Komponentenbenutzeroberfläche verwendet werden. Diese Konsole ist verfügbar unter:

`https://<hostname>:<port-number>/libs/cq/i18n/gui/translator.html`

Mithilfe des Übersetzer-Tools können Sie englischsprachige Zeichenfolgen und die dazugehörigen Übersetzungen verwalten. Die Wörterbücher werden im Repository erstellt, z. B. `/apps/myproject/i18n`.

Das Übersetzer-Tool und die Wörterbücher, die Sie verwalten, dienen zur Darstellung der Komponentenbenutzeroberfläche in verschiedenen Sprachen. Wenn Sie Seiten übersetzen möchten, finden Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-cloud/administering/translation/overview.md) weitere Informationen dazu.

## Erstellen eines Wörterbuchs {#creating-a-dictionary}

Entwickelnde können i18n-Wörterbücher in AEM erstellen, um lokalisierte Komponentenzeichenfolgen zu verwalten. Wörterbücher sind normalerweise Teil des Komponenten-Codes in `/apps`. Im Folgenden finden Sie ein Beispiel aus dem AEM-WKND-Code mit einem Schlüssel-Wert-Paar, das in allen WKND-Komponenten verwendet wird.

```
{
  "&copy; {0} WKND Site Site. All rights reserved." : "&copy; {0} WKND Site Site. Tous droits réservés."
}
```

Entwickelnde können zusätzliche Wörterbücher erstellen, indem sie einen Stammknoten (`sling:Folder`) für ein neues Wörterbuch hinzufügen, in dem Sprachdefinitionen für Komponentenzeichenfolgen gespeichert werden.

```shell
/apps/myProject/i18n [sling:Folder]
    - de.json [nt:file] [mix:language]
        + jcr:language = de
    - fr.json [nt:file] [mix:language]
        + jcr:language = fr
```

>[!NOTE]
>
>Dies ist die Struktur des [Sling-i18n-Moduls](https://sling.apache.org/site/internationalization-support.html).

Nach der Erstellung in einem AEM-GitHub-Repository können Wörterbücher über eine [AEM-CI/CD-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) bereitgestellt werden.

## Wörterbuchspeicherorte {#dictionary-locations}

Entwickelnde können ein Wörterbuch für die Ausgangssprache unter `/apps` oder `/content/cq:i18n` erstellen. Wenn Sie mit dem Beispiel-Code des AEM-Archetyps beginnen, befinden sich die ersten Wörterbücher normalerweise unter dem Pfad `/apps`. Wenn entsprechende Wörterbuchsprachkopien auch unter `/apps` gespeichert werden sollen, müssen diese Sprachkopien von Entwickelnden manuell im Komponenten-Code erstellt und gepflegt werden.

Alternativ wird im Rahmen des neuen AEM-Runtime-Übersetzungsprozesses für i18n-Wörterbücher übersetzte Wörterbücher unter `/content/cq:i18n/<projectName>` erstellt. Dies gilt unabhängig davon, ob das Quellwörterbuch unter `/apps` oder `/content` gespeichert ist.

Entscheidungen, wo i18n-Wörterbücher, Quell- und Sprachkopien zu finden sind, sollten anhand der folgenden Kriterien getroffen werden:

* `/apps`
   * Standardspeicherort für Wörterbücher mit Übersetzungen von Komponentenzeichenfolgen, gemäß AEM-Archetyp und WKND-Beispiel-Code
   * höchste Render-Reihenfolge pro Sling ([Ressourcenpaket-Suchhierarchien](https://sling.apache.org/documentation/bundles/internationalization-support-i18n.html#resourcebundle-hierarchies))
   * aber keine Bearbeitung oder Übersetzung von Wörterbüchern zur Laufzeit möglich, da `/apps` in AEM as a Cloud Service-Umgebungen unveränderlich ist

* `/content/cq:i18n`
   * alternativer Speicherort für i18n-Wörterbücher, falls
      * eine Übersetzung von Wörterbüchern zur Laufzeit erforderlich ist
      * ein Wörterbuch zur Laufzeit bearbeitbar sein muss
   * Standardspeicherort, an dem im Rahmen der Runtime-Übersetzung von Wörterbüchern Sprachkopien erstellt werden

Da `/apps` in der Sling-Render-Reihenfolge immer Vorrang vor `/content` hat, sollten Sie beachten, dass Wörterbücher mit identischen Schlüssel-Wert-Paaren nicht gleichzeitig unter `/apps` und `/content/cq:i18n` vorhanden sein dürfen, da das Wörterbuch unter `/content/cq:i18n` nie zum Rendern verwendet wird. Wenn eine Wörterbuchsprachkopie, d. h. ein Übersetzungsziel, bereits unter `/apps` vorhanden ist und diese zur Laufzeit in AEM as a Cloud Service übersetzbar gemacht werden soll, muss die ursprüngliche Wörterbuchsprachkopie unter `/apps` entweder nach `/content/cq:i18n` verschoben oder unter `/apps` gelöscht und unter `/content/cq:i18n` durch Übersetzen des Quellwörterbuchs automatisch neu erstellt werden. Bei diesem Übersetzungsprozess werden die Sprachkopien automatisch unter `/content/cq:i18n` erstellt.

## Automatisches Erstellen von Wörterbüchern {#automatic-creation}

AEM-Seiten und Experience Fragments, die AEM-Kernkomponenten enthalten, werden im Rahmen des neuen Wörterbuchübersetzungsprozesses auch auf Komponenten und Komponentenzeichenfolgen überprüft, die übersetzt werden sollen. Das System erstellt dann automatisch entsprechende neue Wörterbuchsprachkopien unter `/content/cq:i18n`. Dies gilt nicht für Inhaltsfragmente, da es sich dabei um reine, strukturierte Inhalte ohne die Verwendung von AEM-Kernkomponenten handelt.

## Exportieren eines Wörterbuchs {#exporting-a-dictionary}

Eine Runtime-Übersetzung von i18n-Wörterbüchern an `/apps`- oder `/libs`-Speicherorten in AEM as a Cloud Service ist zwar nicht möglich, da diese Speicherorte unveränderlich sind, diese Wörterbücher können aber zur Laufzeit für eine asynchrone Übersetzung außerhalb von AEM exportiert werden.

So exportieren Sie die Zeichenfolgen der Ausgangssprache eines Wörterbuchs in eine XLIFF-Datei:

1. Öffnen Sie das Übersetzungs-Tool `http://<host>:<port>/libs/cq/i18n/gui/translator.html`

   >[!NOTE]
   >
   >Das Tool ist nur über diese URL verfügbar und kann nicht über die Benutzeroberfläche des AEM-Produkts aufgerufen werden.

1. Wählen Sie im Dropdown-Menü „Wörterbücher“ das Wörterbuch aus, das exportiert werden soll.
1. Klicken Sie auf „XLIFF-Übersetzungen exportieren“ und dann auf die Option für einen vollständigen `<locale>`-XLIFF-Export.

## Importieren eines Wörterbuchs {#importing-a-dictionary}

So importieren Sie eine XLIFF-Datei in ein Wörterbuch, um das Wörterbuch zu füllen:

1. Öffnen Sie das Übersetzungs-Tool `http://<host>:<port>/libs/cq/i18n/gui/translator.html`
1. Klicken Sie auf „XLIFF-Übersetzungen importieren“.
1. Wählen Sie die zu importierende Datei aus und klicken Sie auf „OK“.
