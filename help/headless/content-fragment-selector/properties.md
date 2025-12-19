---
title: Eigenschaften des Micro-Frontend-Inhaltsfragment-Selektors für Adobe Experience Manager as a Cloud Service
description: Eigenschaften zum Konfigurieren des Micro-Frontend-Inhaltsfragment-Selektors zum Suchen, Finden und Abrufen von Inhaltsfragmenten in Ihrer Anwendung.
role: Admin, User
exl-id: c81b5256-09fb-41ce-9581-f6d1ad316ca4
source-git-commit: 58995ae9c29d5a76b3f94de43f2bafecdaf7cf68
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 63%

---

# Inhaltsfragment-Selektor – Verwandte Eigenschaften {#content-fragment-selector-related-properties}

Über den Micro-Frontend-Inhaltsfragment-Selektor können Sie Inhaltsfragmente im Repository durchsuchen bzw. suchen und in Ihrer Anwendung verwenden.

Sie können mithilfe der folgenden Eigenschaften anpassen, wie der Inhaltsfragment-Selektor gerendert wird und wie er eingesetzt werden kann:

## Eigenschaften des Inhaltsfragment-Selektors {#content-fragment-selector-properties}

| Eigenschaft | Typ | Erforderlich | Standard | Beschreibung |
|--- |--- |--- |--- |--- |
| `ref` | fragmentSelectorRef | | | Verweis auf die `ContentFragmentSelector`-Instanz, die den Zugriff auf bereitgestellte Funktionen wie `reload` ermöglicht. |
| `imsToken` | Zeichenfolge | Nein | | Für die Authentifizierung verwendetes IMS-Token Wenn dies nicht angegeben wird, wird der IMS-Anmeldefluss initiiert. |
| `repoId` | Zeichenfolge | Nein | | Repository-ID für den Fragmentselektor. Wenn angegeben, stellt der Selektor automatisch eine Verbindung zum angegebenen Repository her, und das Dropdown-Menü des Repositorys wird ausgeblendet. Wenn kein Repository angegeben wird, kann der Benutzer ein Repository aus der Liste der verfügbaren Repositorys auswählen, auf die er Zugriff hat. |
| `defaultRepoId` | Zeichenfolge | Nein | | Repository-ID, die beim Anzeigen des Repository-Selektors standardmäßig ausgewählt wird. Wird nur verwendet, wenn `repoId` nicht angegeben wird. Wenn `repoId` festgelegt ist, wird der Repository-Selektor ausgeblendet und dieser Wert ignoriert. |
| `orgId` | Zeichenfolge | Nein | | Für die Authentifizierung verwendete Organisations-ID. Wenn kein Wert angegeben ist, kann der Benutzer ein Repository aus verschiedenen Organisationen auswählen, auf die er Zugriff hat. Wenn der Benutzer keinen Zugriff auf ein Repository oder eine Organisation hat, wird der Inhalt nicht geladen. |
| `locale` | Zeichenfolge | Nein | „en-US“ | Gebietsschema. |
| `env` | Zeichenfolge | Nein | | Bereitstellungsumgebung. Siehe den `Env` für zulässige Umgebungsnamen. |
| `filters` | Fragmentfilter | Nein | `{ folder: "/content/dam" }` | Auf die Liste der Inhaltsfragmente anzuwendende Filter Standardmäßig werden Fragmente unter `/content/dam` angezeigt. |
| `isOpen` | Boolesch | Nein | `false` | Markierung, um zu steuern, ob der Selektor geöffnet oder geschlossen ist. |
| `noWrap` | Boolesch | Nein | `false` | Bestimmt, ob der Fragmentselektor ohne Umbruchsdialogfeld gerendert wird. Wenn auf `true` gesetzt, wird der Fragmentselektor direkt in den übergeordneten Container eingebettet. Nützlich für die Integration der -Auswahl in benutzerdefinierte Layouts oder Workflows. |
| `onSelectionChange` | ({ contentFragments: `ContentFragmentSelection`, domainName?: `string`, tenantInfo?: `string`, repoId?: `string`, deliveryRepos?: `DeliveryRepository[]` }) => void | Nein | | Die Rückruffunktion wird ausgelöst, wenn sich die Auswahl von Inhaltsfragmenten ändert. Stellt die aktuell ausgewählten Fragmente, den Domain-Namen, Mandanteninformationen, Repository-ID und Versand-Repositorys bereit. |
| `onDismiss` | () => void | Nein | | Rückruffunktion, die ausgelöst wird, wenn die Abweisungsaktion ausgeführt wird (z. B. Schließen des Selektors). |
| `onSubmit` | ({ contentFragments: `ContentFragmentSelection`, domainName?: `string`, tenantInfo?: `string`, repoId?: `string`, deliveryRepos?: `DeliveryRepository[]` }) => void | Nein | | Die Rückruffunktion wird ausgelöst, wenn der Benutzer seine Auswahl bestätigt. Empfängt die ausgewählten Inhaltsfragmente, den Domain-Namen, die Mandanteninformationen, die Repository-ID und die Versand-Repositorys. |
| `theme` | „hell“ oder „dunkel“ | Nein | | Design für den Fragmentselektor. Standardmäßig ist dies auf das UnifiedShell-Umgebungsdesign festgelegt. |
| `selectionType` | „einfach“ oder „mehrfach“ | Nein | `single` | Der Auswahltyp kann verwendet werden, um die Auswahl für den Fragmentselektor einzuschränken. |
| `dialogSize` | „fullscreen“ oder „fullscreenTakeover“ | Nein | `fullscreen` | Optionale Prop zur Steuerung der Dialogfeldgröße. |
| `runningInUnifiedShell` | Boolesch | Nein | | Ob DestinationSelector unter UnifiedShell oder eigenständig ausgeführt wird. |
| `readonlyFilters` | ResourceReadonlyFiltersField[] | Nein | | Schreibgeschützte Filter, die auf die Liste der Inhaltsfragmente angewendet werden. Diese Filter können vom Benutzer nicht entfernt werden. |
| `selectedFragments` | InhaltsfragmentIdentifier[] | Nein | `[]` | Die anfängliche Auswahl von Inhaltsfragmenten, die beim Öffnen des Selektors vorausgewählt werden sollen. |
| `hipaaEnabled` | Boolesch | Nein | `false` | Gibt an, ob die HIPAA-Konformität aktiviert ist. |
| `inventoryView` | InventoryViewType | Nein | `table` | Standardansichtstyp des Inventars, der im Selektor verwendet werden soll. |
| `inventoryViewToggleEnabled` | Boolesch | Nein | `false` | Gibt an, ob der Umschalter für die Bestandsansicht aktiviert ist, sodass Benutzende zwischen Tabellen- und Rasteransichten wechseln können. |

## ImsAuthProps-Eigenschaften {#imsauthprops-properties}

Die `ImsAuthProps`-Eigenschaften definieren die Authentifizierungsinformationen und den Fluss, mit dem der Inhaltsfragment-Selektor ein `imsToken` abruft. Durch Festlegen dieser Eigenschaften können Sie steuern, wie sich der Authentifizierungsfluss verhält, und Listener für verschiedene Authentifizierungsereignisse registrieren.

| Eigenschaftsname | Beschreibung |
|--- |--- |
| `imsClientId` | Ein Zeichenfolgenwert, der die für Authentifizierungszwecke verwendete IMS-Client-ID darstellt. Dieser Wert wird von Adobe bereitgestellt und ist spezifisch für Ihre Adobe AEM CS-Organisation. |
| `imsScope` | Beschreibt die bei der Authentifizierung verwendeten Bereiche. Die Bereiche bestimmen den Umfang des Zugriffs, den die Anwendung auf die Ressourcen Ihrer Organisation hat. Mehrere Bereiche werden durch Kommas voneinander getrennt. |
| `redirectUrl` | Stellt die URL dar, an die Benutzende nach der Authentifizierung weitergeleitet werden. Dieser Wert wird normalerweise auf die aktuelle URL der Anwendung gesetzt. Wenn keine `redirectUrl` angegeben wird, verwendet `ImsAuthService` die zum Registrieren der `imsClientId` verwendete redirectUrl. |
| `modalMode` | Ein boolescher Wert, der angibt, ob der Authentifizierungsfluss in einem Modal (Popup-Fenster) angezeigt werden soll oder nicht. Wenn `true` festgelegt ist, wird der Authentifizierungsfluss in einem Popup-Fenster angezeigt. Wenn `false` festgelegt ist, wird der Authentifizierungsfluss bei vollständigem Neuladen der Seite angezeigt. <br>**Hinweis:** Für ein besseres Anwendererlebnis können Sie diesen Wert dynamisch steuern, wenn Popup-Fenster des Browsers deaktiviert sind. |
| `onImsServiceInitialized` | Eine Rückruffunktion, die aufgerufen wird, wenn der Adobe IMS-Authentifizierungsdienst initialisiert wird. Diese Funktion akzeptiert einen Parameter namens `service`, ein Objekt, das den Adobe IMS-Dienst darstellt. Siehe [`ImsAuthService`](#imsauthservice-ims-auth-service) für weitere Informationen. |
| `onAccessTokenReceived` | Eine Rückruffunktion, die aufgerufen wird, wenn ein `imsToken` vom Adobe IMS-Authentifizierungsdienst empfangen wird. Diese Funktion akzeptiert einen Parameter namens `imsToken`, eine Zeichenfolge, die das Zugriffstoken darstellt. |
| `onAccessTokenExpired` | Eine Rückruffunktion, die aufgerufen wird, wenn ein Zugriffstoken abgelaufen ist. Diese Funktion wird normalerweise verwendet, um einen neuen Authentifizierungsfluss auszulösen und so ein neues Zugriffstoken zu erhalten. |
| `onErrorReceived` | Eine Rückruffunktion, die aufgerufen wird, wenn während der Authentifizierung ein Fehler auftritt. Diese Funktion akzeptiert zwei Parameter: den Fehlertyp und die Fehlermeldung. Der Fehlertyp ist eine Zeichenfolge, die den Fehlertyp darstellt, und die Fehlermeldung ist eine Zeichenfolge, die die Fehlermeldung darstellt. |

## Eigenschaften von ImsAuthService {#imsauthservice-properties}

Die Klasse `ImsAuthService` regelt den Authentifizierungsfluss für den Inhaltsfragment-Selektor. Sie ist für den Erhalt eines `imsToken` über den Adobe IMS-Authentifizierungsdienst verantwortlich. Das `imsToken` wird verwendet, um die Benutzerin oder den Benutzer zu authentifizieren und den Zugriff auf das Adobe Experience Manager (AEM) CS-Repository zu autorisieren. Der ImsAuthService verwendet die `ImsAuthProps`-Eigenschaften, um den Authentifizierungsfluss zu steuern und Listener für verschiedene Authentifizierungsereignisse zu registrieren. Sie können die praktische Funktion `registerContentFragmentSelectorAuthService` zum Registrieren der Instanz `ImsAuthService` beim Inhaltsfragment-Selektor verwenden. Die folgenden Funktionen sind in der Klasse `ImsAuthService` verfügbar. Wenn Sie jedoch die Funktion `registerContentFragmentSelectorAuthService` verwenden, müssen Sie diese Funktionen nicht direkt aufrufen.

| Funktionsname | Beschreibung |
|--- |--- |
| `isSignedInUser` | Bestimmt, ob die Person derzeit beim Dienst angemeldet ist, und gibt entsprechend einen booleschen Wert zurück. |
| `getImsToken` | Ruft das Authentifizierungs-`imsToken` für die derzeit angemeldete Person ab, das zum Authentifizieren von Anfragen bei anderen Diensten verwendet werden kann, z. B. zum Generieren von Asset-_Ausgabedarstellungen_. |
| `signIn` | Startet den Anmeldeprozess für die Person. Diese Funktion verwendet die `ImsAuthProps`, um die Authentifizierung in einem Popup oder beim vollständigem Neuladen einer Seite anzuzeigen. |
| `signOut` | Meldet die Person vom Dienst ab, macht ihr Authentifizierungs-Token ungültig und fordert sie auf, sich erneut anzumelden, um auf geschützte Ressourcen zuzugreifen. Durch Aufrufen dieser Funktion wird die aktuelle Seite neu geladen. |
| `refreshToken` | Aktualisiert das Authentifizierungs-Token für die derzeit angemeldete Person, verhindert das Ablaufen des Tokens und stellt einen unterbrechungsfreien Zugriff auf geschützte Ressourcen sicher. Gibt ein neues Authentifizierungs-Token zurück, das für nachfolgende Anforderungen verwendet werden kann. |
