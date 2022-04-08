---
title: Dispatcher in der Cloud
description: 'Dispatcher in der Cloud '
feature: Dispatcher
exl-id: 6d78026b-687e-434e-b59d-9d101349a707
source-git-commit: cebeabc56ad3f55bae4ca5d51c7a630480b40577
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Dispatcher in der Cloud {#Dispatcher-in-the-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispoverview"
>title="Dispatcher in der Cloud"
>abstract="Auf dieser Seite wird beschrieben, wie man die Dispatcher-Tools und die unterstützten Apache-Module herunterlädt und extrahiert und einen allgemeinen Überblick über den alten und den flexiblen Modus erhält."

## Einführung {#apache-and-dispatcher-configuration-and-testing}

Auf dieser Seite werden die Dispatcher-Tools sowie deren Download und Extraktion, die unterstützten Apache-Module beschrieben. Außerdem erhalten Sie einen Überblick über den alten und den flexiblen Modus. Darüber hinaus gibt es weitere Verweise zur Validierung und zum Debugging sowie zur Migration der Dispatcher-Konfiguration von AMS zu AEM as a Cloud Service.. Siehe auch [dieses Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-dispatcher-cloud.html) Weitere Informationen zur Bereitstellung von Dispatcher-Dateien in einer Cloud Service-Umgebung.

## Dispatcher Tools {#dispatcher-sdk}

Die Dispatcher Tools sind Teil des gesamten AEM as a Cloud Service-SDK und bieten:

* eine Vanilla-Dateistruktur mit den Konfigurationsdateien, die in ein Maven-Projekt für Dispatcher aufgenommen werden sollen.
* Tools für Kunden zur Überprüfung, ob die Dispatcher-Konfiguration nur von AEM as a Cloud Service unterstützte Anweisungen enthält.        Darüber hinaus überprüfen die Tools auch, ob die Syntax korrekt ist, damit Apache erfolgreich gestartet werden kann.
* ein Docker-Image, das den Dispatcher lokal aufruft.

## Herunterladen und Extrahieren der Tools {#extracting-the-sdk}

Die Dispatcher Tools, die zum [AEM as a Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) gehören, können aus einer ZIP-Datei im [Software-Verteilungs](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html)-Portal heruntergeladen werden. Jede neue Konfiguration, die in dieser neuen Version der Dispatcher-Tools verfügbar ist, kann für die Implementierung in Cloud-Umgebungen verwendet werden, in denen diese Version von AEM as a Cloud Service oder höher ausgeführt wird.

Entpacken Sie das SDK, das die Dispatcher-Tools für macOS/Linux und Windows enthält.

Machen Sie unter **macOS/Linux** das Dispatcher Tool-Artefakt ausführbar und führen Sie es aus. Es extrahiert die Dispatcher Tools-Dateien selbst unter dem Verzeichnis, in dem Sie sie gespeichert haben (wobei `version` die Version der Dispatcher Tools ist).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

Extrahieren Sie unter **Windows** das ZIP-Archiv für die Dispatcher-Tools.

## Validierung und Debugging mit den Dispatcher-Tools {#validation-debug}

Mit den Dispatcher-Tools können Sie die Dispatcher-Konfiguration Ihres Projekts überprüfen und debuggen. Auf den unten referenzierten Seiten erfahren Sie mehr darüber, wie Sie diese Tools verwenden können, je nachdem, ob die Dispatcher-Konfiguration Ihres Projekts im flexiblen Modus oder im alten Modus strukturiert ist:

* **Flexibler Modus**: Der empfohlene Modus und der Standard für [AEM-Archetyp 28](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) und höher, der auch von Cloud Manager für neue Umgebungen verwendet wird, die nach der Cloud Manager-Version 2021.7.0 erstellt wurden. Kunden können diesen Modus aktivieren, indem sie den Ordner und die Datei `opt-in/USE_SOURCES_DIRECTLY` hinzufügen. Durch die Verwendung dieses flexibleren Modus gibt es keine Einschränkungen in der Dateistruktur unter dem Ordner „rewrites“, der im alten Modus eine einzelne `rewrite.rules`-Datei erforderte. Außerdem gibt es keine Beschränkung für die Anzahl der Regeln, die Sie hinzufügen können. Weitere Informationen zur Ordnerstruktur und zur lokalen Validierung finden Sie unter [Validieren und Debugging mit den Dispatcher-Tools](/help/implementing/dispatcher/validation-debug.md).

* **Alter Modus**: Weitere Informationen zur Ordnerstruktur und lokalen Validierung für den alten Modus der Dispatcher-Konfiguration finden Sie unter [Validieren und Debugging mit den Dispatcher-Tools (alt)](/help/implementing/dispatcher/validation-debug-legacy.md).

Weitere Informationen zum Migrieren vom alten Konfigurationsmodell zum flexibleren Konfigurationsmodell, das ab AEM-Archetyp 28 bereitgestellt wird, finden Sie in [dieser Dokumentation](/help/implementing/dispatcher/validation-debug.md#migrating).

## Unterstützte Apache-Module {#supported-directives}

In der folgenden Tabelle werden die unterstützten Apache-Module angezeigt:

| Modulname | Referenzseite |
|---|---|
| `core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/core.html) |
| `mod_access_compat` | [https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html) |
| `mod_alias` | [https://httpd.apache.org/docs/2.4/mod/mod_alias.html](https://httpd.apache.org/docs/2.4/mod/mod_alias.html) |
| `mod_allowmethods` | [https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html](https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html) |
| `mod_authn_core` | [https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html) |
| `mod_authn_file` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_file.html) |
| `mod_authz_core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html) |
| `mod_authz_groupfile` | [https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html) |
| `mod_deflate` | [https://httpd.apache.org/docs/2.4/mod/mod_deflate.html](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html) |
| `mod_dir` | [https://httpd.apache.org/docs/2.4/mod/mod_dir.html](https://httpd.apache.org/docs/2.4/mod/mod_dir.html) |
| `mod_env` | [https://httpd.apache.org/docs/2.4/mod/mod_env.html](https://httpd.apache.org/docs/2.4/mod/mod_env.html) |
| `mod_filter` | [https://httpd.apache.org/docs/2.4/mod/mod_filter.html](https://httpd.apache.org/docs/2.4/mod/mod_filter.html) |
| `mod_headers` | [https://httpd.apache.org/docs/2.4/mod/mod_headers.html](https://httpd.apache.org/docs/2.4/mod/mod_headers.html) |
| `mod_mime` | [https://httpd.apache.org/docs/2.4/mod/mod_mime.html](https://httpd.apache.org/docs/2.4/mod/mod_mime.html) |
| `mod_proxy` | [https://httpd.apache.org/docs/2.4/mod/mod_proxy.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html) |
| `mod_proxy_http` | [https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html) |
| `mod_remoteip` | [https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html](https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html) |
| `mod_reqtimeout` | [https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) |
| `mod_rewrite` | [https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) |
| `mod_security` | [https://modsecurity.org/](https://modsecurity.org/) |
| `mod_setenvif` | [https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) |
| `mod_ssl (only the SSLProxyEngine directive)` | [https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine) |
| `mod_substitute` | [https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |

Kunden können keine beliebigen Module hinzufügen. Es werden jedoch ggf. zusätzliche Module in Betracht gezogen, die in Zukunft in das Produkt aufgenommen werden. Die Kunden können die Liste der für eine bestimmte Dispatcher-Version verfügbaren Anweisungen finden, indem sie den Zulassungslistenbefehl des Validators im SDK ausführen.

Die in den Apache-Konfigurationsdateien zulässigen Anweisungen können aufgelistet werden, indem Sie den Zulassungslistenbefehl des Validators ausführen:

```
$ validator allowlist
Cloud manager validator 2.0.4
 
Allowlisted directives:
  <Directory>
  ...
  
```

## Ordnerstruktur {#folder-structure}

Die Struktur des Apache- und Dispatcher-Ordners des Projekts unterscheidet sich geringfügig je nachdem, welcher Modus vom Projekt verwendet wird, wie im Abschnitt [Validierung und Debugging mithilfe der Dispatcher-Tools](#validation-debug) oben beschrieben.

## Migrieren der Dispatcher-Konfiguration aus AMS {#ams-aem}

Weitere Informationen zum Migrieren der Dispatcher-Konfiguration von AMS zu AEM as a Cloud Service finden Sie auf der Seite [Migrieren der Dispatcher-Konfiguration von AMS zu AEM](/help/implementing/dispatcher/ams-aem.md) as a Cloud Service.
