---
title: Internationalisierung von UI-Zeichenfolgen
description: AEM bietet eine Konsole für die Verwaltung der verschiedenen Textübersetzungen, die in der Komponentenbenutzeroberfläche verwendet werden.
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 14a6516872f842d099b902b9f633b1d6f984266d
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 14%

---


# Verwalten von Wörterbüchern mithilfe des Übersetzers{#using-translator-to-manage-dictionaries}

AEM stellt eine Konsole für die Verwaltung der verschiedenen Übersetzungen von Texten bereit, die auf der Komponentenbenutzeroberfläche verwendet werden. Diese Konsole ist verfügbar unter:

`https://<hostname>:<port-number>/libs/cq/i18n/gui/translator.html`

Mithilfe des Übersetzer-Tools können Sie englischsprachige Zeichenfolgen und die dazugehörigen Übersetzungen verwalten. Die Wörterbücher werden im Repository erstellt, z. B. `/apps/myproject/i18n`.

Das Übersetzer-Tool und die Wörterbücher, die Sie verwalten, dienen zur Darstellung der Komponentenbenutzeroberfläche in verschiedenen Sprachen. Wenn Sie Seiten übersetzen möchten, lesen Sie [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-cloud/administering/translation/overview.md).

## Erstellen eines Wörterbuchs {#creating-a-dictionary}

Entwickler können i18n-Wörterbücher in AEM erstellen, um lokalisierte Komponentenzeichenfolgen zu verwalten. Wörterbücher sind normalerweise Teil des Komponenten-Codes in `/apps`. Im Folgenden finden Sie ein Beispiel aus dem AEM-WKND-Code mit einem Schlüssel/Wert-Paar, das in allen WKND-Komponenten verwendet wird.

```
{
  "&copy; {0} WKND Site Site. All rights reserved." : "&copy; {0} WKND Site Site. Tous droits réservés."
}
```

Entwickler können zusätzliche Wörterbücher erstellen, indem sie einen Stammknoten (`sling:Folder`) für ein neues Wörterbuch hinzufügen, in dem Sprachdefinitionen für Komponentenzeichenfolgen gespeichert werden.

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

Nach der Erstellung in einem AEM-GitHub-Repository können Wörterbücher über eine AEM (CI/CD[Pipeline bereitgestellt ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

## Wörterbuchspeicherorte {#dictionary-locations}

Entwickler können ein Wörterbuch für die Ausgangssprache in `/apps` oder `/content/cq:i18n` erstellen. Wenn Sie mit dem Beispiel-Code des AEM-Archetyps beginnen, befinden sich die ersten Wörterbücher normalerweise im `/apps`. Wenn ein Ziel darin besteht, entsprechende Wörterbuchsprachkopien auch in `/apps` zu speichern, müssen diese Sprachkopien von Entwicklerinnen und Entwicklern manuell im Komponenten-Code erstellt und gepflegt werden.

Alternativ erstellt der neue AEM-Laufzeitübersetzungsprozess für i18n-Wörterbücher übersetzte Wörterbücher in `/content/cq:i18n/<projectName>`, unabhängig davon, ob das Quellwörterbuch in `/apps` oder `/content` gespeichert ist.

Entscheidungen, wo i18n-Wörterbücher, Quell- und Sprachkopien zu finden sind, sollten anhand der folgenden Kriterien getroffen werden:

* `/apps`
   * Standardspeicherort für Wörterbücher mit Übersetzungen von Komponentenzeichenfolgen, dem AEM-Archetyp und WKND-Beispielcode folgend
   * höchste Rendering-Reihenfolge pro Sling ([Ressourcenbündel-](https://sling.apache.org/documentation/bundles/internationalization-support-i18n.html#resourcebundle-hierarchies))
   * Allerdings ist keine Bearbeitung oder Übersetzung von Wörterbüchern zur Laufzeit möglich, da `/apps` in AEM as a Cloud Service-Umgebungen unveränderlich ist

* `/content/cq:i18n`
   * Alternativer Speicherort für i18n-Wörterbücher, wenn
      * Übersetzung von Wörterbüchern zur Laufzeit erforderlich
      * Die Möglichkeit, ein Wörterbuch zur Laufzeit zu bearbeiten, ist erforderlich
   * Standardspeicherort, an dem die Übersetzung des Laufzeitwörterbuchs Sprachkopien erstellt.

Da `/apps` `/content` in der Sling-Rendering-Reihenfolge immer ersetzt, sollten Sie beachten, dass Wörterbücher mit identischen Schlüssel/Wert-Paaren nicht gleichzeitig in `/apps` und `/content/cq:i18n` vorhanden sein dürfen, da das Wörterbuch in `/content/cq:i18n` nie zum Rendern verwendet wird. Wenn eine Wörterbuchsprachkopie, d. h. ein Übersetzungsziel, bereits in `/apps` vorhanden ist und das Ziel darin besteht, sie zur Laufzeit in AEM as a Cloud Service übersetzbar zu machen, muss die ursprüngliche Wörterbuchsprachkopie in `/apps` entweder nach `/content/cq:i18n` verschoben oder in `/apps` gelöscht und in `/content/cq:i18n` durch Übersetzen des Quellwörterbuchs automatisch neu erstellt werden. Dieser Übersetzungsprozess erstellt automatisch die Sprachkopien in `/content/cq:i18n`.

## Automatische Erstellung von Wörterbüchern {#automatic-creation}

Für AEM-Seiten und Experience Fragments, die AEM-Kernkomponenten enthalten, überprüft der neue Wörterbuchübersetzungsprozess diese Seiten oder Experience Fragments auch auf Komponenten und Komponentenzeichenfolgen, die übersetzt werden sollen. Das System erstellt dann automatisch entsprechende neue Sprachkopien des Wörterbuchs in `/content/cq:i18n`. Dies gilt nicht für Inhaltsfragmente, da es sich um reine, strukturierte Inhalte ohne die Verwendung von AEM-Kernkomponenten handelt.

## Exportieren eines Wörterbuchs {#exporting-a-dictionary}

Während die Laufzeitübersetzung von i18n-Wörterbüchern an `/apps`- oder `/libs`-Speicherorten in AEM as a Cloud Service nicht möglich ist, da diese Speicherorte unveränderlich sind, können diese Wörterbücher zur Laufzeit für eine asynchrone Übersetzung außerhalb von AEM weiterhin exportiert werden.

So exportieren Sie die Zeichenfolgen der Ausgangssprache eines Wörterbuchs in eine XLIFF-Datei:

1. Öffnen Sie das Übersetzungs-Tool `http://<host>:<port>/libs/cq/i18n/gui/translator.html`

   >[!NOTE]
   >
   >Das Tool ist nur über diese URL verfügbar und kann nicht über die Benutzeroberfläche des AEM-Produkts aufgerufen werden.

1. Wählen Sie im Dropdown-Menü „Wörterbücher“ das Wörterbuch aus, das exportiert werden soll.
1. Klicken Sie auf XLIFF-Übersetzung exportieren und dann auf Vollständige XLIFF-`<locale>` exportieren.

## Importieren eines Wörterbuchs {#importing-a-dictionary}

So importieren Sie eine XLIFF-Datei in ein Wörterbuch zum Ausfüllen des Wörterbuchinhalts:

1. Öffnen Sie das Übersetzungs-Tool `http://<host>:<port>/libs/cq/i18n/gui/translator.html`
1. Klicken Sie auf Importieren und dann auf XLIFF-Übersetzungen.
1. Wählen Sie die zu importierende Datei aus und klicken Sie auf „OK“.
