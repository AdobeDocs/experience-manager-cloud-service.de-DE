---
title: AEM as a Cloud Service – Team- und Produktprofile
description: Erfahren Sie, wie Sie über AEM as a Cloud Service Team- und Produktprofile erstellen und den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren oder einschränken.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
feature: Onboarding
role: Admin, User, Developer
source-git-commit: c8534ddf84998377ee63575403417165ccec2dbd
workflow-type: tm+mt
source-wordcount: '2059'
ht-degree: 34%

---


# AEM as a Cloud Service – Team- und Produktprofile {#product-profiles}

Erfahren Sie, wie Sie über AEM as a Cloud Service Team- und Produktprofile erstellen und den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren oder einschränken.

## Produktprofile {#profiles}

Wenn Sie einem Benutzer Zugriff auf eine bestimmte Adobe-Lösung gewähren, möchten Sie ihm nicht unbedingt uneingeschränkten Zugriff gewähren. Mit Produktprofilen kann jeder Lösung ein eigener Satz von Benutzerberechtigungen zugewiesen werden. Diese sind über die [Admin Console](/help/journey-onboarding/admin-console.md) verfügbar und zugänglich.

Die Adobe Admin Console verfügt über eine strukturierte Hierarchie von Produkten, Produktinstanzen und Produktprofilen, in der den internen Benutzern eines Unternehmens eine Mitgliedschaft zugewiesen werden kann, sodass sie auf die lizenzierten Lösungen und Funktionen zugreifen können.

<!-- Alexandru: Drafting for now 

Your AEM as a Cloud Service team members are added and assigned to one or more of the following product profiles via the Admin Console during onboarding.

* **AEM Administrators**: An AEM administrator is typically assigned to developers, in particular developers who need access to, for example, the development environments. The AEM administrator's product profile is used to grant administrator privileges in the associated AEM instance.

* **AEM Users**: AEM users are the users in your organization who use AEM as a Cloud Service generally to create content. These users need to access AEM to do their tasks. The AEM users product profile is typically assigned to an AEM content author who creates and reviews the content. This content can be of many types such as pages, assets, publications, and so on. The AEM users product profile shown below is assigned to these members.

![Product profiles](/help/onboarding/assets/admin-console-profiles.png) -->

## AEM as a Cloud Service-Produktprofile {#aem-product-profiles}

AEM as a Cloud Service ist ein vollständig Cloud-natives Angebot, das AEM als Service bereitstellt. Es bietet AEM auf Cloud-native Weise mit neuen Attributen wie „always on“ (immer aktiv), „always current“ (immer aktuell), „always secure“ (immer sicher) und „always at scale“ (immer skaliert). Gleichzeitig wird das wichtigste Wertversprechen aufrecht erhalten, das AEM als anpassbare Plattform für Kunden bereitstellt und es Teams in Unternehmen ermöglicht, sich in ihre Entwicklungs- und Bereitstellungsverfahren zu integrieren. Weitere Informationen zu AEM as a Cloud Service finden Sie in der [Einführung in Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md).

### Produktinstanzen auf Unternehmensebene {#org-level-product-instances}

>[!NOTE]
>
> Einige der in diesem Artikel beschriebenen Produktinstanzen und Produktprofile werden möglicherweise nur für neu erstellte Umgebungen angezeigt. Ein zukünftiger Mechanismus wird auch die Aktualisierung bestehender Umgebungen ermöglichen.

Wenn Adobe die Lizenzierung einer AEM-Lösung zum ersten Mal verarbeitet, werden in Adobe Admin Console unter dem Adobe Experience Manager as a Cloud Service-Produkt zwei Produktinstanzen angezeigt:

* **AEM Org-Level** - enthält ein oder mehrere Produktprofile, die den Zugriff auf Funktionen darstellen, die auf alle AEM Umgebungen übertragen werden, und nicht nur auf eine einzige.
* **Cloud Manager** - enthält Produktprofile, die verschiedenen Zugriffsebenen auf Cloud Manager-Funktionen entsprechen.

<!--
>[!NOTE]
>
>For existing programs, the AEM Org-Level Product Instance is created upon selecting the **Update product** profiles action for a given environment.
-->

![Produktinstanzen auf Org-Ebene](/help/onboarding/assets/orglevel.png)

Innerhalb der AEM Produktinstanz auf Organisationsebene ist ein Produktprofil mit dem Namen AEM Berichterstattungen auf Organisationsebene, das derzeit nicht verwendet wird, in Zukunft aber möglicherweise den Zugriff auf das Abrufen von Informationen zu AEM Produktlizenzen darstellt.

Wenn eine Forms Communication Solution lizenziert ist, wird auch unter der AEM Produktinstanz auf Organisationsebene ein entsprechendes Produktprofil angezeigt.

![Produktprofil der Reporter](/help/onboarding/assets/org-level-reporters.png)

### Produktinstanzen auf Umgebungs- und Ebenen-Ebene {#environment-and-tier-level-product-instances}

Nach der Bereitstellung neuer Programme mit einer oder mehreren AEM Umgebungen werden zwei Produktinstanzen pro Umgebung angezeigt, die Produktprofile für Autoren- bzw. Veröffentlichungsinstanzen enthalten.

![Umgebungsproduktinstanzen](/help/onboarding/assets/env-productinstances.png)

Im Folgenden finden Sie die Produktprofile in einer Autorenproduktinstanz für ein Unternehmen, das eine Umgebung in einem Programm mit AEM Sites bereitgestellt hat:

![Sites-Produktinstanzen](/help/onboarding/assets/sites-product-instances.png)

In der folgenden Tabelle wird eine Liste der möglichen Produktprofile unter einer umgebungsebenenspezifischen Produktinstanz beschrieben.

<table style="table-layout:auto">
    <tr>
        <th>Produktinstanz</th>
        <th>Namenskonvention</th>
        <th>Standarddienst</th>
        <th>Beschreibung</th>
    </tr>
    <tr>
        <td>AEM Author</td>
        <td>AEM Sites Content Manager - author - program <code>id</code> - environment <code>id</code></td>
        <td>AEM Sites Content Manager</td>
        <td>
            <ul>
                <li>Dient für den kontrollierten Zugriff auf AEM Sites-Autorenfunktionen in dieser Umgebung. Benutzer in diesem Produktprofil sind Mitglieder der AEM Sites-Inhaltsautor-AEM, die automatisch in AEM erstellt wird. Die AEM Gruppenberechtigungen sollten in AEM mit der gewünschten Zugriffsebene konfiguriert werden.</li><br>
                <li>Wenn der Standarddienst ausgewählt bleibt
                    <ul>
                        <li>-Benutzer in diesem Produktprofil sind auch Mitglieder der AEM "AEM Sites Content Manager - Service".</li>
                      <!--  <li>users in this product profile will have access to AEM Sites Content Management API.</li>
                        <li>an Adobe Developer Console API OAuth S2S project containing AEM Sites Content Management API can optionally be scoped to this environment.</li>-->
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM-Administratoren - author - Programm <code>id</code> - Umgebung <code>id</code></td>
        <td>AEM Administratoren</td>
        <td>
            <ul>
                <li>Für uneingeschränkten Zugriff auf AEM Funktionen der Autoren- und Veröffentlichungsumgebung vorgesehen. Benutzer in diesem Produktprofil sind Mitglieder der AEM Administrator-AEM -Gruppe, die automatisch in AEM erstellt wird.</li><br>
                <li>Wenn der Standarddienst ausgewählt bleibt
                    <ul>
                        <li>Benutzer in diesem Produktprofil sind auch Mitglieder der AEM "AEM Administratoren - Dienst"</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Benutzer - Autor - Programm <code>id</code> - Umgebung <code>id</code></td>
        <td>AEM-Benutzende</td>
        <td>
            <ul>
                <li>Dient für sehr eingeschränkten Zugriff auf AEM Funktionen der Autorenumgebung. Benutzer in diesem Produktprofil sind Mitglieder der Gruppe "Mitarbeiter", AEM automatisch in AEM erstellt wird.</li><br>
                <li>Wenn der Standarddienst ausgewählt bleibt
                    <ul>
                        <li>Benutzer in diesem Produktprofil sind auch Mitglieder der AEM "AEM Benutzer - Dienst"</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Reporter - author - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Reporter</td>
        <td>
            <ul>
                <li>Derzeit nicht verwendet, aber in Zukunft kann Zugriff auf Berichtsinformationen über die Autorenstufe für diese Umgebung bieten.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Assets Collaborator - author - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Assets-Mitwirkende</td>
        <td>
        <ul>
                <li>Für schreibgeschützten Zugriff auf DAM vorgesehen. Benutzer in diesem Produktprofil sind Mitglieder der Gruppe "Mitarbeiter", AEM automatisch in AEM erstellt wird.
                </li>
                <li>
                Außerdem bietet es die Berechtigungen der Adobe Expreß zum Erstellen von Asset-Varianten.
                </li>
          <ul>
    </tr>
    <tr>
        <td></td>
        <td>AEM Assets Power User - author - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Assets Power Users</td>
<td>
        <ul>
                <li>Für schreibgeschützten Zugriff auf DAM vorgesehen. Benutzer in diesem Produktprofil sind Mitglieder der Gruppe "Mitarbeiter", AEM automatisch in AEM erstellt wird.
                </li>
                <li>
                Außerdem bietet es die Berechtigungen der Adobe Expreß zum Erstellen von Asset-Varianten.
                </li>
          <ul>
</td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms Content Manager - author - program <code>id</code> - environment <code>id</code></td>
        <td>AEM Forms Content Manager</td>
        <td>
            <ul>
                <li>Dient für den kontrollierten Zugriff auf AEM Forms-Autorenfunktionen in dieser Umgebung. Benutzer in diesem Produktprofil sind Mitglieder der Gruppe AEM Forms forms-users AEM , die automatisch in AEM erstellt wird.</li><br>
                <li>Wenn der Standarddienst ausgewählt bleibt
                    <ul>
                        <li>-Benutzer in diesem Produktprofil sind auch Mitglieder der AEM "AEM Forms Content Manager - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms-Entwickler - Autor - Programm <code>id</code> - Umgebung <code>id</code></td>
        <td>AEM Forms-Entwickler</td>
        <td>
            <ul>
                <li>Dient für den kontrollierten Zugriff auf AEM Forms-Autorenfunktionen in dieser Umgebung. Benutzer in diesem Produktprofil sind Mitglieder der AEM Gruppe AEM Forms forms-power-users , die automatisch in AEM erstellt wird. Diese Benutzer haben zusätzlich zu den normalen Formularerstellungsaufgaben auch die Berechtigung, XDPs hochzuladen und Formulardatenmodelle zu erstellen.</li><br>
                <li>Wenn der Standarddienst ausgewählt bleibt
                    <ul>
                        <li>-Benutzer in diesem Produktprofil sind auch Mitglieder der AEM "AEM Forms Developers - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms Communications Service-Benutzer - author - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Forms Communications-Dienstbenutzer</td>
        <td>
            <ul>
                <li>Dient für den kontrollierten Zugriff auf AEM Forms Communications Services-Funktionen in dieser Umgebung. Benutzer in diesem Produktprofil sind Mitglieder der Gruppe AEM Forms forms-users AEM , die automatisch in AEM erstellt wird.</li><br>
                <li>Wenn der Standarddienst ausgewählt bleibt
                    <ul>
                        <li>Benutzer in diesem Produktprofil gehören auch zur AEM "AEM Forms Communications Service-Benutzer - Dienst".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>AEM Publish</td>
        <td>AEM Benutzer - Veröffentlichung - Programm <code>id</code> - Umgebung <code>id</code></td>
        <td>AEM-Benutzende</td>
        <td>
            <ul>
                <li>Dient für sehr eingeschränkten Zugriff auf AEM Funktionen der Autorenumgebung. Benutzer in diesem Produktprofil sind Mitglieder der AEM Gruppe "Contrib", die automatisch in AEM erstellt wird</li><br>
                <li>Wenn der Standarddienst ausgewählt bleibt
                    <ul>
                        <li>Benutzer in diesem Produktprofil sind auch Mitglieder der AEM "AEM Benutzer - Dienst".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Reporter - publish - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Reporter</td>
        <td>
            <ul>
                <li>Derzeit nicht verwendet, aber in Zukunft kann Zugriff auf Berichtsinformationen über die Veröffentlichungsstufe für diese Umgebung bieten.</li>
            </ul>
        </td>
    </tr>
   <tr>
        <td></td>
        <td>AEM Forms Communications Service-Benutzer - Veröffentlichung - Programm <code>id</code> - Umgebung <code>id</code></td>
        <td>AEM Forms Communications-Dienstbenutzer</td>
        <td>
            <ul>
                <li>Dient für den kontrollierten Zugriff auf AEM Forms Communications Services-Funktionen in dieser Umgebung. Benutzer in diesem Produktprofil sind Mitglieder der Gruppe AEM Forms forms-users AEM , die automatisch in AEM erstellt wird.</li><br>
                <li>Wenn der Standarddienst ausgewählt bleibt
                    <ul>
                        <li>Benutzer in diesem Produktprofil gehören auch zur AEM "AEM Forms Communications Service-Benutzer - Dienst".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
</table>

Beachten Sie, dass für jedes Produktprofil standardmäßig ein zugewiesener Produktprofildienst aktiviert ist. Sofern Sie keine komplexen Zugriffsanforderungen haben, wird empfohlen, nur den Standarddienst auszuwählen. Eine entsprechende AEM wird in AEM mit der Benennungsregel `<Product Profile Prefix> - Service` erstellt (z. B. **AEM Sites Content Manager - Service**), und die Benutzer in den übergeordneten Produktprofilen werden automatisch Mitglieder dieser entsprechenden AEM Gruppe.

Die mit dem Dienst verknüpfte AEM Gruppe in AEM verfügt über den aggregierten Satz von Benutzern, die in allen zugehörigen Produktprofilen dieses Dienstes für diese Umgebungs-Tier-Kombination vorhanden sind.

![Dienste](/help/onboarding/assets/services.png)

Die folgende Abbildung stellt die AEM Gruppen dar, die das Produktprofil und den Service der Autorenstufe von AEM Sites Content Manager widerspiegeln.

![AEM Zuordnung von Gruppe zu Dienst](/help/onboarding/assets/profile-to-service-mapping.png)

>[!NOTE]
>
>Jeder Benutzer, der einem AEM as a Cloud Service-Produktprofil zugewiesen ist, hat über die Rolle **Cloud Manager-Benutzer** schreibgeschützten Zugriff auf Cloud Manager.
>
>Benutzer nur mit der Rolle **Cloud Manager-Benutzer** können sich bei Cloud Manager anmelden und zu den AEM-Autorenumgebungen navigieren (falls vorhanden), indem sie die Menüoptionen unter **Programme** verwenden. Die Rolle **Cloud Manager-Benutzer** reicht nicht aus, um auf Programmdetails zuzugreifen. Wenn ein solcher Zugriff erforderlich ist, müssen Benutzende von ihrem Systemadministrator zusätzliche Rollen erhalten.

>[!WARNING]
>
>Der **AEM-Admin**-Produktprofilname darf nicht geändert werden. Das Ändern des **AEM-Admin**-Produktprofilnamens entfernt Adminrechte von allen Benutzenden, die diesem Profil zugewiesen sind.

>[!TIP]
>
>* Weitere Informationen zu AEM-Produktprofilen finden Sie unter [Zuweisen von AEM-Produktprofilen](/help/journey-onboarding/assign-profiles-aem.md).
>* Weitere Informationen zum Onboarding-Prozess finden Sie in der [Onboarding-Tour](/help/journey-onboarding/overview.md).

### Hinzufügen von Produktprofilen für bestehende Umgebungen {#adding-product-profiles-for-existing-environments}

In Umgebungen, die vor Anfang November 2024 erstellt wurden, fehlt möglicherweise die in den obigen Abschnitten beschriebene Produktinstanz auf Org-Level sowie bestimmte Produktprofile. Bei bestehenden Produktprofilen fehlt auch der Dienst-Umschalter. Es wird empfohlen, diese Produktprofile zu aktualisieren. Dies ist eine Voraussetzung für den Zugriff auf einige zukünftige APIs.

Wenn für eine oder mehrere Umgebungen in einem Programm die Produktprofile aktualisiert werden müssen, wird in Cloud Manager der nachstehende Hinweis angezeigt. Beachten Sie, dass eine Umgebung auf der neuesten AEM Version basieren muss, bevor ihre Produktprofile aktualisiert werden können.

![Modernisieren von Produktprofilen](/help/onboarding/assets/modernize-product-profiles.png)

Durch Klicken auf die Schaltfläche **Produktprofile hinzufügen** wird ein Menü mit Optionen zum Hinzufügen neuer Produktprofile zu allen im Programm oder in einzelnen Umgebungen verfügbaren Umgebungen geöffnet.

![Umgebungen ersetzen](/help/onboarding/assets/choose-env-r.png)

Klicken Sie auf **Alle Umgebungen** , um die neuen Produktprofile zu allen Umgebungen im Programm hinzuzufügen. Klicken Sie alternativ auf &quot;**Individuelle Umgebungen**&quot;, um die neuen Produktprofile zu ausgewählten Umgebungen hinzuzufügen. Dadurch wird der Benutzer zu einer Umgebungslistenseite geleitet, auf der über das Symbol &quot;**Mehr Optionen**&quot;die Aktion &quot;**Produktprofile hinzufügen**&quot;ausgewählt werden kann.

![Individuelle Umgebungen](/help/onboarding/assets/individual-environments.png)

Sie können ausgewählten Umgebungen auch Produktprofile hinzufügen, indem Sie zum Abschnitt Umgebungen auf der Seite Programmübersicht navigieren, auf das Symbol Weitere Optionen für eine Umgebung klicken und Produktprofile hinzufügen auswählen.

Der Status der Umgebung zeigt &quot;Hinzufügen von Produktprofilen&quot;an, während die neuen Produktprofile hinzugefügt werden, und zeigt anschließend &quot;Wird ausgeführt&quot;an, wenn der Prozess abgeschlossen ist.


## Cloud Manager-Produktprofile {#cloud-manager-product-profiles}

Cloud Manager verfügt über vorkonfigurierte Produktprofile, die man sich als rollenbasierte Berechtigungen vorstellen kann. Ihr(e) System-Admin ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, indem er/sie die Team-Mitglieder diesen Produktprofilen zuweist.

>[!TIP]
>
>Weitere Informationen finden Sie unter [Rollenbasierte Berechtigungen in Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

Jedem Produktprofil sind spezifische Berechtigungen zugeordnet.

* **Geschäftsinhaber**
   * In dieser Rolle haben Sie die Berechtigung, ein neues Programm hinzuzufügen oder ein Programm zu bearbeiten, eine Umgebung hinzuzufügen oder zu aktualisieren, Code in der AEM-Umgebung bereitzustellen oder Code-Qualitätsprüfungen durchzuführen.
   * Diese Person ist verantwortlich für die Definition von KPIs, die Genehmigung von Produktionbereitstellungen und das Überschreiben von gravierenden dreistufigen Fehlern, falls erforderlich.
* **Bereitstellungs-Manager**
   * In dieser Rolle sind Sie berechtigt, eine Umgebung hinzuzufügen oder zu aktualisieren, eine beliebige Pipeline auszuführen und Code in der AEM-Umgebung bereitzustellen oder Code-Qualitätsprüfungen durchzuführen.
   * Diese Person verwaltet die Bereitstellungsvorgänge mit Cloud Manager, um Staging- und Produktionsbereitstellungen durchzuführen, CI/CD-Pipeline zu bearbeiten, kann bei Bedarf gravierende dreistufige Fehler genehmigen und hat Zugriff auf das Git-Repository.
* **Entwickler**
   * In dieser Rolle sind Sie berechtigt, persönliche Zugriffs-Token für den Zugriff auf Git zu generieren.
   * Diese Person entwickelt und testet benutzerdefinierten Anwendungs-Code, verwendet Cloud Manager hauptsächlich zur Anzeige des Bereitstellungsstatus und kann für Code-Commits auf das Git-Repository zugreifen.
* **Programm-Manager**
   * In dieser Rolle sind Sie berechtigt, Pipelines zu planen, die dreistufigen Qualitäts-Gates außer Kraft zu setzen und Produktionsgenehmigungen zu erteilen.
   * Diese Person nutzt Cloud Manager, um die Einrichtung von Teams vorzunehmen, den Status zu überprüfen, KPIs einzusehen und ggf. gravierende dreistufige Fehler zu genehmigen.

Benutzende können mehreren Produktprofilen zugewiesen werden. Wenn Sie beispielsweise einem Benutzer bzw. einer Benutzerin die beiden Rollen **Geschäftsinhaber** und **Bereitstellungs-Manager** zuweisen, erhält er/sie die Summe aller dieser Berechtigungen.

Ihr Cloud Manager-Team umfasst mindestens:

* Einen **Geschäftsinhaber**, der in der Regel auch der/die System-Admin ist und die erste Person sein muss, die sich bei Cloud Manager anmeldet und darauf zugreift
* Einen **Bereitstellungs-Manager**
* **Einen Entwickler bzw. eine Entwicklerin**

>[!NOTE]
>
>Um Zugriff auf AEM as a Cloud Service zu erhalten, müssen Benutzende einem von zwei Produktprofilen angehören: `AEM Users` oder `AEM Administrators`. Die Berechtigungen zum Verwalten von Cloud Manager reichen nicht aus.

>[!TIP]
>
>* Weitere Informationen zu Cloud Manager-Produktprofilen finden Sie unter [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](/help/journey-onboarding/assign-profiles-cloud-manager.md).
>* Weitere Informationen zum Onboarding-Prozess finden Sie in der [Onboarding-Tour](/help/journey-onboarding/overview.md).
