---
title: AEM als Cloud Service SDK
description: 'Noch auszufüllen '
translation-type: tm+mt
source-git-commit: a7dc007230632bf8343004794b2bc4c5baaf4e05

---


# AEM als Cloud Service SDK {#aem-as-a-cloud-service-sdk}

Das AEM als Cloud Service SDK besteht aus den folgenden Artefakten:

* **Quickstart-JAR** - Die für die lokale Entwicklung verwendete AEM-Laufzeit
* **Java-API-JAR** - Die Java-Jar-/Maven-Abhängigkeit, die alle zulässigen Java-APIs verfügbar macht, die zur Entwicklung für AEM als Cloud-Dienst verwendet werden können. Zuvor als Uberjar bezeichnet
* **Javadoc Jar** - Die JavaScript-Dateien für Java API Jar
* **Dispatcher Tools** - Der Satz von Werkzeugen, die zur lokalen Entwicklung gegen Dispatcher verwendet werden. Separate Artefakte für Unix und Fenster

Darüber hinaus verwenden einige Kunden, die zuvor mit AEM 6.5 oder früher bereitgestellt wurden, die unten stehenden Artefakte. Wenn die lokale Kompilierung nicht mit der Quickstart-JAR-Datei funktioniert und Sie vermuten, dass dies auf Schnittstellen zurückzuführen ist, die aus AEM entfernt wurden, die als Cloud-Dienst bereitgestellt wurden, wenden Sie sich an den Kundensupport, um zu ermitteln, ob Sie Zugriff benötigen. Dies erfordert Änderungen im Backend.

* **6.5 Veraltete Java-API-JAR** - ein zusätzlicher Satz von Schnittstellen, die seit AEM 6.5 entfernt wurden
* **6.5 Veraltete Javadoc-Jar** - die JavaScript-Dateien für den zusätzlichen Satz an Interfaces

## Zugriff auf AEM als Cloud Service SDK {#accessing-the-aem-as-a-cloud-service-sdk}

* Sie können das Symbol &quot; **Info zu Adobe Experience Manager** &quot;der AEM-Admin-Konsole überprüfen, um die Version von AEM zu ermitteln, die Sie in der Produktion ausführen.
* Die Schnellstart-JAR- und Dispatcher-Tools können als ZIP-Datei vom [Software Distribution Portal](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html)heruntergeladen werden. Beachten Sie, dass der Zugriff auf die SDK-Listen auf diejenigen mit AEM Managed Services oder AEM als Cloud-Dienstumgebungen beschränkt ist.
* Die Java-API-JAR- und Java-JAR-Dateien können über Maven Tooling heruntergeladen werden, entweder mit der Befehlszeile oder mit Ihrer bevorzugten IDE.
* Das Masterprojekt sollte auf das folgende API-JAR-Paket verweisen. Diese Abhängigkeit sollte auch in allen Teilpaketformularen referenziert werden.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version> 
  <scope>provided</scope>
</dependency>
```

> [!NOTE] Der Versionseintrag für das SDK sollte mit der Version von AEM als Cloud-Dienst übereinstimmen. Sie können sehen, welche Version Sie verwenden, indem Sie sich bei AEM anmelden, dann das Fragezeichen in der oberen rechten Ecke des Bildschirms aufrufen und **[!UICONTROL Info zu Adobe Experience Manager auswählen.]**

* Die Remote-Koordinate für das Maven-Repository, in dem das Paket gehostet wird, sollte in der Pom-Datei enthalten sein.

```
<repository>
    <id>adobe-aem-releases</id>
    <name>Adobe AEM Repository</name>
    <url>https://downloads.experiencecloud.adobe.com/content/maven/public</url>
    <releases>
        <enabled>true</enabled>
        <updatePolicy>never</updatePolicy>
    </releases>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
</repository>
```

## Aktualisieren eines lokalen Projekts mit einer neuen SDK-Version {#refreshing-a-local-prokect-with-a-new-skd-version}

Wann wird empfohlen, das lokale Projekt mit einem neuen SDK zu aktualisieren?

Es wird *empfohlen* , diese Version mindestens nach einem monatlichen Maintenance Release zu aktualisieren.

Es ist *optional* , das Update nach jedem Maintenance Release pro Tag durchzuführen. Kunden werden darüber informiert, wenn ihre Produktionsinstanz erfolgreich auf eine neue AEM-Version aktualisiert wurde. Bei den täglichen Maintenance Releases ist nicht zu erwarten, dass sich das neue SDK erheblich verändert hat, wenn überhaupt. Es wird dennoch empfohlen, die lokale AEM-Entwicklungsumgebung gelegentlich mit dem neuesten SDK zu aktualisieren und dann die benutzerdefinierte Anwendung neu zu erstellen und zu testen. Das monatliche Maintenance Release umfasst in der Regel wirkungsvollere Änderungen, sodass Entwickler sofort aktualisieren, neu erstellen und testen sollten.

Nachfolgend finden Sie die empfohlene Vorgehensweise zum Aktualisieren einer lokalen Umgebung:

1. Vergewissern Sie sich, dass alle nützlichen Inhalte entweder in der Quellcodeverwaltung für das Projekt bereitgestellt oder in einem flexiblen Inhaltspaket für den späteren Import verfügbar sind
1. Lokale Testinhalte für die Entwicklung müssen separat gespeichert werden, damit sie nicht im Rahmen des Cloud Manager-Pipeline-Builds bereitgestellt werden. Das liegt daran, dass sie nur für die lokale Entwicklung verwendet werden muss
1. Beenden Sie den derzeit ausgeführten Schnellstart
1. Verschieben Sie den `crx-quickstart` Ordner in einen anderen Ordner, um die Sicherheit zu gewährleisten
1. Notieren Sie die neue AEM-Version, die in Cloud Manager aufgeführt ist (mit dieser Version wird die neue QuickStart-Jar-Version identifiziert, die weiter heruntergeladen werden soll)
1. Laden Sie die QuickStart-JAR herunter, deren Version mit der Production AEM-Version im Software Distribution Portal übereinstimmt.
1. Erstellen Sie einen ganz neuen Ordner und legen Sie die neue QuickStart-Jar in
1. Beginnen Sie den neuen QuickStart mit den gewünschten Runmodi (entweder Dateien umbenennen oder Ausführungsmodi übergeben über `-r`).
   * Achten Sie darauf, dass der alte Schnellstart nicht mehr im Ordner verbleibt.
1. Erstellen der AEM-Anwendung
1. AEM-Anwendung über PackageManager auf lokaler AEM bereitstellen
1. Installieren Sie alle Pakete mit veränderlichem Inhalt, die für lokale Umgebungstests erforderlich sind, über PackageManager
1. Entwickeln Sie die Änderungen nach Bedarf weiter und stellen Sie sie bereit

Wenn Inhalte vorhanden sind, die mit jeder neuen AEM-Schnellstartversion installiert werden sollen, fügen Sie sie in ein Inhaltspaket und in die Quellcodeverwaltung des Projekts ein. Installieren Sie es dann jedes Mal.

Es wird empfohlen, das SDK häufig zu aktualisieren (z. B. alle zwei Wochen) und täglich den vollständigen lokalen Status zu deaktivieren, damit es nicht versehentlich von den Statusdaten in der Anwendung abhängt.

Wenn Sie von CryptoSupport abhängig sind ([entweder durch Konfiguration der Anmeldeinformationen von Cloudservices oder des SMTP Mail-Dienstes in AEM oder durch Verwendung der CryptoSupport-API in Ihrer Anwendung](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/crypto/CryptoSupport.html)), werden die verschlüsselten Eigenschaften durch einen Schlüssel verschlüsselt, der beim ersten Start einer AEM-Umgebung automatisch generiert wird. Während das Cloudsetup dafür sorgt, dass der umweltrelevante CryptoKey automatisch wiederverwendet wird, muss der Cryptokey in die lokale Entwicklungsumgebung injiziert werden.

Standardmäßig ist AEM so konfiguriert, dass die Schlüsseldaten im Datenordner eines Ordners gespeichert werden. Aus Gründen der einfacheren Wiederverwendung in der Entwicklung kann der AEM-Prozess beim ersten Start mit &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;initialisiert werden. Dadurch werden die Verschlüsselungsdaten bei &quot;`/etc/key`&quot;generiert.

Um Inhaltspakete mit verschlüsselten Werten wiederverwenden zu können, müssen Sie die folgenden Schritte ausführen:

* Wenn Sie die lokale Datei &quot;quickstart.jar&quot;starten, müssen Sie den folgenden Parameter hinzufügen: &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Es wird empfohlen, jedoch optional, sie immer hinzuzufügen.
* Beim ersten Starten einer Instanz erstellen Sie ein Paket, das einen Filter für den Stammordner &quot;`/etc/key`&quot;enthält. Dadurch wird das Geheimnis erhalten, das in allen Umgebungen wiederverwendet werden soll, in denen sie wiederverwendet werden sollen
* Exportieren Sie alle veränderlichen Inhalte, die Geheimnisse enthalten, oder suchen Sie die verschlüsselten Werte, `/crx/de` um sie dem Paket hinzuzufügen, das in allen Installationen wiederverwendet wird.
* Wenn Sie eine neue Instanz drehen (entweder um sie durch eine neue Version zu ersetzen oder weil mehrere Entwicklungsumgebungen die Anmeldeinformationen zum Testen gemeinsam verwenden sollten), installieren Sie das in den Schritten 2 und 3 erstellte Paket, um den Inhalt wiederverwenden zu können, ohne dass eine manuelle Neukonfiguration erforderlich ist. Das liegt daran, dass sich der Kryptoschlüssel jetzt in einer Synchronisierung befindet.