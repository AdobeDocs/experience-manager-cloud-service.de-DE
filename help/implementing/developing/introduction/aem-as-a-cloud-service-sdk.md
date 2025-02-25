---
title: AEM as a Cloud Service-SDK
description: Ein Überblick über das AEM as a Cloud Service Software Development Kit.
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 82f5078740b2cf6ac481d83df40bbbc4fb3c1a77
workflow-type: tm+mt
source-wordcount: '1246'
ht-degree: 48%

---

# Das AEM as a Cloud Service-SDK {#aem-as-a-cloud-service-sdk}

Das AEM as a Cloud Service-SDK besteht aus den folgenden Artefakten:

* **Quickstart-JAR** - Die für die lokale Entwicklung verwendete AEM-Laufzeit.
* **Java™-API-JAR**: die Java™-JAR-/Maven-Abhängigkeit, die alle zulässigen Java™-APIs verfügbar macht, die zur Entwicklung für AEM as a Cloud Service verwendet werden können. Zuvor als UberJar bezeichnet.
* **Javadoc-JAR** - Die Java-Dokumente für die Java™-API-JAR-Datei.
* **Dispatcher Tools**: der Satz von Tools, die der lokalen Entwicklung mit Dispatcher dienen. Separate Artefakte für UNIX® und Windows.

Darüber hinaus werden manche Kundinnen und Kunden, die zuvor AEM 6.5 oder frühere Versionen bereitgestellt haben, die unten stehenden Artefakte verwenden. Wenn die lokale Kompilierung mit der Schnellstart-JAR-Datei nicht funktioniert und Sie vermuten, dass sie auf das Entfernen von Benutzeroberflächen aus der von AEM bereitgestellten as a Cloud Service zurückzuführen ist, wenden Sie sich an den Kunden-Support. Sie können feststellen, ob Sie Zugang benötigen. Dies erfordert Änderungen im Backend.

* **6.5 Veraltete Java™-API-JAR** - Ein zusätzlicher Satz von Benutzeroberflächen, die seit AEM 6.5 entfernt wurden.
* **6.5 Veraltetes JavaDoc-JAR** - Die Java-Dokumente für den zusätzlichen Satz von Schnittstellen.

>[!NOTE]
> 
> AEM as a Cloud Service und SDK unterscheiden sich in einer Reihe von Bereichen. Für Situationen, in denen schnelle und iterative Änderungen erforderlich sind, hat Adobe schnelle Entwicklungsumgebungen (Rapid Development Environments) eingeführt. Weitere Informationen finden Sie unter [Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md).

## Erstellen für das SDK {#building-for-the-sdk}

Das AEM as a Cloud Service-SDK wird zum Erstellen und Bereitstellen von benutzerdefiniertem Code verwendet. Siehe die [Dokumentation zum AEM-Projektarchetyp](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/using). Im Allgemeinen werden die folgenden Schritte ausgeführt:

* **Code kompilieren** - Source-Code wird kompiliert und generiert die resultierenden Inhaltspakete.
* **Artefakte erstellen** - Artefakte werden während dieses Prozesses erstellt.
* **Bundles analysieren** - Bundles werden mit dem Maven Analyzer-Plug-in analysiert, das nach Problemen im Maven-Projekt sucht, z. B. nach fehlenden Abhängigkeiten.
* **Artefakte bereitstellen** - Artefakte werden auf dem lokalen Server bereitgestellt.

Cloud Manager führt dieselben Schritte bei der Bereitstellung in Cloud-Umgebungen aus. Die lokale Durchführung von Builds ermöglicht eine lokale Entwicklung und Prüfung. Entwickler können Code- oder Strukturprobleme effizient identifizieren, bevor sie sich zur Quell-Code-Verwaltung verpflichten. Dadurch werden Verzögerungen verhindert, die durch das Auslösen von Cloud Manager-Bereitstellungen verursacht werden. Dies kann länger dauern.

>[!NOTE]
>
>Das AEM as a Cloud Service SDK sollte mit einer Distribution und Version von Java erstellt werden, die von der [Build-Umgebung von Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) unterstützt wird. AEM as a Cloud Service-Kunden können das Oracle JDK über das [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) herunterladen. Aufgrund der Lizenzierungs- und Support-Bedingungen von Adobe für Oracle Java-Technologie in Adobe Experience Manager-Projekten wurde der Java 11-Support bis September 2026 verlängert.

## Zugriff auf das AEM as a Cloud Service-SDK {#accessing-the-aem-as-a-cloud-service-sdk}

* Sie können das Symbol **Über Adobe Experience Manager&quot; von AEM Admin Console**, um herauszufinden, welche Version von AEM Sie in der Produktionsumgebung ausführen.
* Die Schnellstart-JAR- und Dispatcher-Tools können als ZIP-Datei vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) heruntergeladen werden. Der Zugriff auf die SDK-Listen ist auf Personen beschränkt, die Umgebungen auf AEM Managed Services oder AEM as a Cloud Service haben.
* Die Java™-API-JAR- und JavaDoc-JAR-Datei können über Maven-Tools heruntergeladen werden, entweder über die Befehlszeile oder mit der von Ihnen bevorzugten IDE.
* Die Maven-Projekt-POMs sollten auf das folgende API-JAR-Paket verweisen. Auch auf die Abhängigkeit von Unterpaketen sollte verwiesen werden.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version>
  <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Der Versionseintrag für das SDK muss mit der Version von AEM as a Cloud Service übereinstimmen. Sie können sehen, welche Version Sie verwenden, indem Sie sich bei AEM anmelden. Navigieren Sie in der rechten oberen Ecke des Bildschirms zum Fragezeichen und klicken Sie auf **[!UICONTROL Über Adobe Experience Manager]**.


## Aktualisieren eines lokalen Projekts mit einer neuen SDK-Version {#refreshing-a-local-project-with-a-new-skd-version}

Wann sollte das lokale Projekt mit einem neuen SDK aktualisiert werden?

Adobe *empfiehlt* die Aktualisierung nach einer monatlichen Wartungsversion.

Es ist *optional*, nach jeder täglichen Wartungsversion zu aktualisieren. Kundinnen und Kunden werden darüber informiert, wenn ihre Produktionsinstanz erfolgreich auf eine neue AEM-Version aktualisiert wurde. Bei den täglichen Wartungsversionen ist nicht zu erwarten, dass sich das neue SDK erheblich verändert hat (wenn überhaupt). Adobe empfiehlt jedoch, die lokale AEM-Entwicklungsumgebung gelegentlich mit der neuesten SDK zu aktualisieren und dann das benutzerdefinierte Programm neu zu erstellen und zu testen. Die monatliche Wartungsversion umfasst in der Regel wirkungsvollere Änderungen, sodass Entwicklerinnen und Entwickler umgehend aktualisieren, neu erstellen und testen sollten.

**So aktualisieren Sie ein lokales Projekt mit einer neuen SDK-Version:**

1. Stellen Sie sicher, dass alle nützlichen Inhalte in die Quell-Code-Verwaltung übertragen werden. Oder in einem veränderlichen Inhaltspaket für den späteren Import gespeichert.
1. Inhalte lokaler Entwicklungstests müssen separat gespeichert werden, damit sie nicht im Rahmen des Cloud Manager-Pipeline-Build bereitgestellt werden. Der Grund dafür ist, dass sie nur für die lokale Entwicklung verwendet werden.
1. Beenden Sie den derzeit laufenden Schnellstart.
1. Verschieben Sie den Ordner `crx-quickstart` zur sicheren Aufbewahrung in einen anderen Ordner.
1. Beachten Sie die neue AEM-Version, die in Cloud Manager vermerkt ist (sie wird verwendet, um die neue Schnellstart-JAR-Version für den weiteren Download zu identifizieren).
1. Laden Sie die Schnellstart-JAR-Datei, deren Version mit der AEM-Produktionsversion übereinstimmt, vom Software Distribution-Portal herunter.
1. Erstellen Sie einen ganz neuen Ordner und platzieren Sie darin die neue Schnellstart-JAR.
1. Starten Sie den neuen Schnellstart mit den gewünschten Ausführungsmodi (entweder Umbenennen der Datei oder Übergeben in Ausführungsmodi über `-r`).
Stellen Sie sicher, dass im Ordner keine Überreste des alten Schnellstarts vorhanden sind.
1. Erstellen Sie Ihre AEM-Anwendung.
1. Stellen Sie Ihre AEM-Anwendung mithilfe von Package Manager auf lokalem AEM bereit.
1. Installieren Sie alle veränderlichen Inhaltspakete, die für lokale Umgebungstests mithilfe von Package Manager erforderlich sind.
1. Entwickeln Sie nach Bedarf weiter und stellen Sie Änderungen bereit.

Wenn es Inhalte gibt, die mit jeder neuen AEM-Schnellstartversion installiert werden sollen, fügen Sie sie in einem Inhaltspaket und der Quell-Code-Verwaltung des Projekts hinzu. Installieren Sie sie dann jedes Mal.

Adobe empfiehlt, die SDK häufig zu aktualisieren, z. B. alle zwei Wochen. Entsorgen Sie außerdem den vollständigen lokalen Status täglich, damit Sie sich nicht versehentlich auf statusbehaftete Daten in der Anwendung verlassen müssen.

Wenn Sie CryptoSupport für Cloud-Services, die SMTP-Mail-Konfiguration oder die CryptoSupport-API verwenden, werden verschlüsselte Eigenschaften mit einem Schlüssel gesichert. Weitere Informationen finden Sie in der [Dokumentation zur CryptoSupport-API](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html). Dieser Schlüssel wird beim ersten Start einer AEM-Umgebung automatisch generiert. Während die Cloud-Implementierung dafür sorgt, dass der umgebungsspezifische CryptoKey automatisch wiederverwendet wird, muss der CryptoKey in die lokale Entwicklungsumgebung injiziert werden.

Standardmäßig ist AEM so konfiguriert, dass die Schlüsseldaten im Datenordner eines Ordners gespeichert werden. Um die Wiederverwendung bei der Entwicklung zu vereinfachen, kann der AEM-Prozess jedoch beim ersten Starten mit &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot; initialisiert werden. Dieser Prozess generiert die Verschlüsselungsdaten bei &quot;`/etc/key`&quot;.

**Wiederverwenden von Inhaltspaketen, die die verschlüsselten Werte enthalten:**

* Wenn Sie die lokale Datei quickstart.jar zum ersten Mal starten, fügen Sie unbedingt den folgenden Parameter hinzu: &quot;`-Dcom.adobe.granite.crypto.file.disable=true`.“ Adobe empfiehlt optional, dass Sie es immer hinzufügen.
* Erstellen Sie beim ersten Starten einer Instanz ein Paket, das einen Filter für den Stamm &quot;`/etc/key`&quot; enthält. Dieses Paket enthält das Geheimnis, das in allen Umgebungen wiederverwendet wird, in denen sie wiederverwendet werden sollen.
* Exportieren Sie alle veränderlichen Inhalte, die geheime Daten enthalten. Oder suchen Sie die verschlüsselten Werte über `/crx/de`, um sie zum Paket hinzuzufügen, das in allen Installationen wiederverwendet wird.
* Installieren Sie das in den Schritten 2 und 3 erstellte Paket jedes Mal, wenn Sie eine neue Instanz starten (entweder um sie durch eine neue Version zu ersetzen oder weil mehrere Entwicklungsumgebungen die Anmeldeinformationen zum Testen gemeinsam nutzen sollen). Auf diese Weise können Sie den Inhalt wiederverwenden, ohne dass eine manuelle Neukonfiguration erforderlich ist. Das liegt daran, dass der CryptoKey jetzt synchronisiert ist.

