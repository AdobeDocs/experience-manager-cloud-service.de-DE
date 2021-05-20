---
title: Verwendung der CIF-Produkt- und Kategorieauswahl
description: Erfahren Sie, wie Sie mit der CIF-Produkt- und Kategorieauswahl in Ihren Commerce-Komponenten für Kunden Autoren und Marketing-Experten unterstützen können, um effizient mit Commerce-Produkten und -Katalogdaten zu arbeiten.
sub-product: Commerce
topics: Development
version: cloud-service
activity: develop
audience: developer
feature: Commerce Integration Framework
exl-id: 30f1f263-1b78-46ae-99ed-61861c488b2a
source-git-commit: ef4abc74b90da80bfe556306f8ac93078b4958c7
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---

# AEM Content &amp; Commerce Authoring-Wähler {#cif-pickers}

AEM Content &amp; Commerce Authoring bietet eine Reihe von Authoring-Tools, mit denen AEM Autoren und Marketing-Experten effizient mit Commerce-Produktdaten und -Katalogen arbeiten können. Die Produktauswahl und die Kategorieauswahl sind Teil des CIF-Add-ons und werden von den CIF-Kernkomponenten verwendet. Projekte können diese Auswahl in jedem Komponentendialogfeld verwenden, um Produkte oder Kategorien auszuwählen.

## Produktauswahl {#product-picker}

Um die Produktauswahl in einer Projektkomponente zu verwenden, muss ein Entwickler `commerce/gui/components/common/cifproductfield` zu einem Komponentendialogfeld hinzufügen. Verwenden Sie beispielsweise Folgendes für cq:dialog:

```xml
<product jcr:primaryType="nt:unstructured"
    sling:resourceType="commerce/gui/components/common/cifproductfield"
    fieldDescription="The product or product variant displayed by the teaser"
    fieldLabel="Select Product"
    filter="folderOrProductOrVariant"
    name="./selection"
    selectionId="sku"/>
```

Das Produktfeld ermöglicht die Navigation zu dem Produkt, das ein Benutzer über die verschiedenen Ansichten auswählen möchte. Standardmäßig gibt das Produktfeld die Kennung des Produkts zurück, kann jedoch mithilfe des Attributs `selectionId` konfiguriert werden.

Das Produktauswahlfeld unterstützt die folgenden optionalen Eigenschaften:

- selectionId (id, uid, sku, slug, CombinedSlug, CombinedSku) - ermöglicht die Auswahl des Produktattributs, das vom Picker zurückgegeben werden soll (Standard = id). Bei Verwendung der SKU wird die SKU des ausgewählten Produkts zurückgegeben, während die kombinierte SKU verwendet wird, und es wird eine Zeichenfolge wie base#variant mit der SKU des Basisprodukts und der ausgewählten Variante oder eine einzelne SKU zurückgegeben, wenn ein Basisprodukt ausgewählt ist.
- filter (folderOrProduct, folderOrProductOrVariant) - filtert den Inhalt, der vom Picker während der Navigation in der Produktstruktur gerendert werden soll. folderOrProduct - rendert Ordner und Produkte. folderOrProductOrVariant - rendert Ordner, Produkt- und Produktvarianten. Wenn ein Produkt oder eine Produktvariante gerendert wird, kann sie auch in der Auswahl ausgewählt werden. (default = folderOrProduct)
- multiple (true, false) - Aktivieren der Auswahl eines oder mehrerer Produkte (Standard = false)
- emptyText - zum Konfigurieren des leeren Textwerts des Picker-Felds

Darüber hinaus werden auch standardmäßige Eigenschaften von Dialogfeldfeldern wie `name`, `fieldLabel` oder `fieldDescription` unterstützt.

Für die Komponente `cifproductfield` ist die clientlib cif.shell.picker erforderlich. Um einem Dialogfeld eine clientlib hinzuzufügen, können Sie die Eigenschaft extraClientlibs verwenden.

Ein vollständiges Arbeitsbeispiel für `cifproductfield` finden Sie im Projekt [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/_cq_dialog/.content.xml) . Siehe auch [Anpassen von Dialogfeldern](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs) in der Dokumentation zu AEM Kernkomponenten .

## Kategorieauswahl {#category-picker}

Die Kategorieauswahl kann auch in einem Komponentendialogfeld auf ähnliche Weise wie die Produktauswahl verwendet werden.

Das folgende Snippet kann in einer cq:dialog -Konfiguration verwendet werden:

```xml
<category jcr:primaryType="nt:unstructured" 
    sling:resourceType="commerce/gui/components/common/cifcategoryfield" 
    fieldLabel="Category" 
    name="./categoryId" 
    selectionId="uid" />
```

Das Kategorieauswahlfeld unterstützt die folgenden optionalen Eigenschaften:

- selectionId(id, uid, slug, idAndUrlPath, uidAndUrlPath) - ermöglicht die Auswahl des Kategorieattributs, das vom Picker zurückgegeben werden soll (Standard = id). idAndUrlPath &amp; uidAndUrlPath sind spezielle Optionen, mit denen die Kategorie id/uid und url_path durch einen | Zeichen wie z.B. 1|men/tops.
- multiple (true, false) - Aktivieren der Auswahl einer oder mehrerer Kategorien (Standard = false)

Darüber hinaus werden auch standardmäßige Eigenschaften von Dialogfeldfeldern wie `name`, `fieldLabel` oder `fieldDescription` unterstützt.

Wie die Komponente `cifproductfield` erfordert die Komponente `cifcategoryfield` auch die clientlib cif.shell.picker . Um eine clientlib zu einem Dialogfeld hinzuzufügen, können Sie die Eigenschaft `extraClientlibs` verwenden. Siehe [Anpassen von Dialogfeldern](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs) in der Dokumentation zu AEM Kernkomponenten .

Ein vollständiges Arbeitsbeispiel für `cifcategoryfield` finden Sie im Projekt [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/featuredcategorylist/v1/featuredcategorylist/_cq_dialog/.content.xml) .
