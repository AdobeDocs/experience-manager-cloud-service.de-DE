---
title: Eigenschaften des Micro-Front-End-Inhaltsfragment-Selektors für Adobe Experience Manager as a Cloud Service
description: Eigenschaften zum Konfigurieren des Micro-Front-End-Inhaltsfragment-Selektors zum Suchen, Suchen und Abrufen von Inhaltsfragmenten aus Ihrer Anwendung.
role: Admin, User
source-git-commit: 32e1b3cef768b420f32b70202ddadc80db2b74e8
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 48%

---


# Inhaltsfragment-Selektor - Verwandte Eigenschaften {#content-fragment-selector-related-properties}

Mit dem Micro-Front-End-Inhaltsfragment-Selektor können Sie Inhaltsfragmente im Repository durchsuchen und in Ihrer Anwendung verwenden.

Sie können die folgenden Eigenschaften verwenden, um anzupassen, wie der Inhaltsfragment-Selektor gerendert wird und wie er verwendet werden kann:

## Eigenschaften des Inhaltsfragment-Selektors {#content-fragment-selector-properties}

| Eigenschaft | Typ | Erforderlich | Standard | Beschreibung |
|--- |--- |--- |--- |--- |
| `imsToken` | Zeichenfolge | Nein | | Für die Authentifizierung verwendetes IMS-Token |
| `repoId` | Zeichenfolge | Nein | | Für die Authentifizierung verwendete Repository-ID. |
| `orgId` | Zeichenfolge | Ja | | Für die Authentifizierung verwendete Organisations-ID. |
| `locale` | Zeichenfolge | Nein | | Gebietsschema-Daten. |
| `env` | Umgebung | Nein | | Bereitstellungsumgebung des Inhaltsfragment-Selektors. |
| `filters` | FragmentFilter | Nein | | Für die Liste der Inhaltsfragmente anzuwendende Filter. Standardmäßig werden Fragmente unter `/content/dam` angezeigt. Standardwert: `{ folder: "/content/dam" }` |
| `isOpen` | Boolesch | Ja | `false` | Trigger Markieren Sie, um den Selektor zu öffnen oder zu schließen. |
| `onDismiss` | () => void | Ja | | Funktion, die aufgerufen werden soll, wenn **Verwerfen** ausgewählt ist. |
| `onSubmit` | ({ contentFragments: `{id: string, path: string}[]`, domainNames: `string[]` }) => void | Funktion, die aufgerufen wird, wenn **Auswählen** nach Auswahl eines oder mehrerer Inhaltsfragmente verwendet wird. <br><br>Die Funktion erhält:<br><ul><li> die ausgewählten Inhaltsfragmente mit `id` und `path` Feldern</li><li>und Domain-Namen, die mit der Programm-ID und der Umgebungs-ID des Repositorys verknüpft sind und den Status `ready` und die `tier` Veröffentlichung haben</li></ul><br>Wenn keine Domain-Namen vorhanden sind, wird die Veröffentlichungsinstanz als Fallback-Domain verwendet. |
| `theme` | „Leicht“ | „Dunkel“ | Nein | | Design des Inhaltsfragment-Selektors. Das Standarddesign ist auf das Design der UnifiedShell-Umgebung festgelegt. |
| `selectionType` | „single“ | „Mehrere“ | Nein | `single` | Auswahltyp, der verwendet werden kann, um die Auswahl für den Fragment-Selektor einzuschränken. |
| `dialogSize` | „Vollbild“ | „fullscreenTakeover“ | Nein | `fullscreen` | Optionale Eigenschaft zum Steuern der Dialogfeldgröße. |
| `waitForImsToken` | Boolesch | Nein | `false` | Gibt an, ob der Inhaltsfragmentselektor im Kontext des SUSI-Flusses gerendert wird und warten muss, bis der `imsToken` bereit ist. |
| `imsAuthInfo` | IMS-AuthInfo | Nein | | Objekt, das die IMS-Authentifizierungsinformationen des angemeldeten Benutzers enthält |
| `runningInUnifiedShell` | Boolesch | Nein | | Gibt an, ob der Inhaltsfragmentselektor unter UnifiedShell oder eigenständig ausgeführt wird. |
| `readonlyFilters` | ResourceReadOnlyFiltersField | Nein | | Schreibgeschützte Filter, die für die Inhaltsliste angewendet werden können und nicht entfernt werden können. |

## ImsAuthProps-Eigenschaften {#imsauthprops-properties}

Die `ImsAuthProps` definieren die Authentifizierungsinformationen und den Fluss, den der Inhaltsfragment-Selektor zum Abrufen eines `imsToken` verwendet. Durch Festlegen dieser Eigenschaften können Sie steuern, wie sich der Authentifizierungsfluss verhält, und Listener für verschiedene Authentifizierungsereignisse registrieren.

| Eigenschaftsname | Beschreibung |
|--- |--- |
| `imsClientId` | Ein Zeichenfolgenwert, der die für Authentifizierungszwecke verwendete IMS-Client-ID darstellt. Dieser Wert wird von Adobe bereitgestellt und ist spezifisch für Ihre Adobe AEM CS-Organisation. |
| `imsScope` | Beschreibt die bei der Authentifizierung verwendeten Bereiche. Die Bereiche bestimmen den Umfang des Zugriffs, den die Anwendung auf die Ressourcen Ihrer Organisation hat. Mehrere Bereiche werden durch Kommas voneinander getrennt. |
| `redirectUrl` | Stellt die URL dar, an die Benutzende nach der Authentifizierung weitergeleitet werden. Dieser Wert wird normalerweise auf die aktuelle URL der Anwendung gesetzt. Wenn kein `redirectUrl` angegeben wird, verwendet `ImsAuthService` die zum Registrieren des `imsClientId` verwendete redirectUrl |
| `modalMode` | Ein boolescher Wert, der angibt, ob der Authentifizierungsfluss in einem Modal (Popup-Fenster) angezeigt werden soll oder nicht. Wenn `true` festgelegt ist, wird der Authentifizierungsfluss in einem Popup-Fenster angezeigt. Wenn auf `false` festgelegt, wird der Authentifizierungsfluss beim vollständigen Neuladen der Seite angezeigt.<br>**Hinweis:** Für ein besseres Anwendererlebnis können Sie diesen Wert dynamisch steuern, wenn Popup-Fenster des Browsers deaktiviert sind. |
| `onImsServiceInitialized` | Eine Rückruffunktion, die aufgerufen wird, wenn der Adobe IMS-Authentifizierungsdienst initialisiert wird. Diese Funktion akzeptiert einen Parameter namens `service`, ein Objekt, das den Adobe IMS-Dienst darstellt. Siehe [`ImsAuthService`](#imsauthservice-ims-auth-service) für weitere Informationen. |
| `onAccessTokenReceived` | Eine Rückruffunktion, die aufgerufen wird, wenn ein `imsToken` vom Adobe IMS-Authentifizierungsdienst empfangen wird. Diese Funktion akzeptiert einen Parameter namens `imsToken`, eine Zeichenfolge, die das Zugriffstoken darstellt. |
| `onAccessTokenExpired` | Eine Rückruffunktion, die aufgerufen wird, wenn ein Zugriffstoken abgelaufen ist. Diese Funktion wird normalerweise verwendet, um einen neuen Authentifizierungsfluss auszulösen und so ein neues Zugriffstoken zu erhalten. |
| `onErrorReceived` | Eine Rückruffunktion, die aufgerufen wird, wenn während der Authentifizierung ein Fehler auftritt. Diese Funktion akzeptiert zwei Parameter: den Fehlertyp und die Fehlermeldung. Der Fehlertyp ist eine Zeichenfolge, die den Fehlertyp darstellt, und die Fehlermeldung ist eine Zeichenfolge, die die Fehlermeldung darstellt. |

## Eigenschaften des IMS-Authentifizierungsdienstes {#imsauthservice-properties}

Die `ImsAuthService`-Klasse verarbeitet den Authentifizierungsfluss für den Inhaltsfragment-Selektor. Sie ist für den Erhalt eines `imsToken` über den Adobe IMS-Authentifizierungsdienst verantwortlich. Die `imsToken` wird verwendet, um den Benutzer zu authentifizieren und den Zugriff auf das Adobe Experience Manager (AEM) CS-Repository zu autorisieren. ImsAuthService verwendet die `ImsAuthProps`-Eigenschaften, um den Authentifizierungsfluss zu steuern und Listener für verschiedene Authentifizierungsereignisse zu registrieren. Sie können die praktische `registerContentFragmentSelectorAuthService` verwenden, um die `ImsAuthService`-Instanz mit dem Inhaltsfragment-Selektor zu registrieren. Die folgenden Funktionen sind in der `ImsAuthService`-Klasse verfügbar. Wenn Sie jedoch die Funktion `registerContentFragmentSelectorAuthService` verwenden, müssen Sie diese Funktionen nicht direkt aufrufen.

| Funktionsname | Beschreibung |
|--- |--- |
| `isSignedInUser` | Bestimmt, ob die Person derzeit beim Dienst angemeldet ist, und gibt entsprechend einen booleschen Wert zurück. |
| `getImsToken` | Ruft den `imsToken` für den aktuell angemeldeten Benutzer ab, der zum Authentifizieren von Anforderungen an andere Services verwendet werden kann, z. B. zum Generieren von Assets _Ausgabedarstellung._ |
| `signIn` | Startet den Anmeldeprozess für die Person. Diese Funktion verwendet die `ImsAuthProps`, um die Authentifizierung entweder in einem Popup oder beim vollständigen Neuladen der Seite anzuzeigen. |
| `signOut` | Meldet die Person vom Dienst ab, macht ihr Authentifizierungs-Token ungültig und fordert sie auf, sich erneut anzumelden, um auf geschützte Ressourcen zuzugreifen. Durch Aufrufen dieser Funktion wird die aktuelle Seite neu geladen. |
| `refreshToken` | Aktualisiert das Authentifizierungs-Token für die derzeit angemeldete Person, verhindert das Ablaufen des Tokens und stellt einen unterbrechungsfreien Zugriff auf geschützte Ressourcen sicher. Gibt ein neues Authentifizierungs-Token zurück, das für nachfolgende Anforderungen verwendet werden kann. |