---
ms.date: 02/03/2020
keywords: powershell,core
title: Modifications avec rupture dans PowerShell 6.0
ms.openlocfilehash: 47ed14cceed86e4dd04a8e0079af00f6a98988ea
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "76995464"
---
# <a name="breaking-changes-for-powershell-6x"></a>Modifications avec rupture dans PowerShell 6.x

## <a name="features-no-longer-available-in-powershell-core"></a>Fonctionnalités qui ne sont plus disponibles dans PowerShell Core

### <a name="modules-not-shipped-for-powershell-6x"></a>Modules non livrés pour PowerShell 6.x

Pour différentes raisons de compatibilité, les modules suivants ne sont pas inclus dans PowerShell 6.

- ISE
- Microsoft.PowerShell.LocalAccounts
- Microsoft.PowerShell.ODataUtils
- Microsoft.PowerShell.Operation.Validation
- PSScheduledJob
- PSWorkflow
- PSWorkflowUtility

### <a name="powershell-workflow"></a>PowerShell Workflow

[PowerShell Workflow][workflow] est une fonctionnalité de Windows PowerShell qui s’appuie sur [Windows Workflow Foundation (WF)][workflow-foundation] et permet de créer des runbooks robustes pour les tâches de longue durée ou parallélisées.

En raison du manque de support pour Windows Workflow Foundation dans .NET Core, nous ne prendrons plus en charge PowerShell Workflow dans PowerShell Core.

À l’avenir, nous aimerions activer le parallélisme/la concurrence natif(ve) dans le langage PowerShell sans utiliser PowerShell Workflow.

S’il est nécessaire d’utiliser des points de contrôle pour reprendre un script après le redémarrage du système d’exploitation, nous vous recommandons d’utiliser Planificateur de tâches pour exécuter un script au démarrage du système d’exploitation, mais le script doit conserver son propre état (par exemple, le rendre persistant dans un fichier).

[workflow]: /powershell/scripting/components/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Composants logiciels enfichables personnalisés

[Les composants logiciels enfichables PowerShell][snapin] sont les prédécesseurs des modules PowerShell qui ne bénéficient pas d’une adoption répandue dans la communauté PowerShell.

En raison de la complexité de la prise en charge des composants logiciels enfichables et leur sous-utilisation au sein de la communauté, nous ne prenons plus en charge les composants logiciels enfichables personnalisés dans PowerShell Core.

Aujourd’hui, cela arrête les modules `ActiveDirectory` et `DnsClient` dans Windows et Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Cmdlets WMI v1

En raison de la complexité de la prise en charge de deux ensembles de modules basés sur WMI, nous avons supprimé les cmdlets WMI v1 de PowerShell :

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

Au lieu de cela, nous vous recommandons d’utiliser les cmdlets CIM (également appelés WMI v2) qui offrent le même fonctionnement avec des fonctionnalités et une syntaxe nouvelles :

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

En raison de l’utilisation des API non prises en charge, `Microsoft.PowerShell.LocalAccounts` a été supprimé de PowerShell jusqu’à ce qu’une meilleure solution soit trouvée.

### <a name="new-webserviceproxy-cmdlet-removed"></a>Cmdlet `New-WebServiceProxy` supprimée

.NET Core ne prend pas en charge l’infrastructure de communication Windows, qui fournit des services pour l’utilisation du protocole SOAP. Cette cmdlet a été supprimée, car elle nécessite SOAP.

### <a name="-transaction-cmdlets-removed"></a>Cmdlets `*-Transaction` supprimées

Ces cmdlets ont une utilisation très limitée. Il a été décidé de ne plus les prendre en charge.

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a>Cmdlets de sécurité non disponibles sur les plateformes autres que Windows

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a>`*-Computer` et autres cmdlets spécifiques à Windows

En raison de l’utilisation d’API non prises en charge, les applets de commande suivantes ont été supprimées de PowerShell Core jusqu’à ce qu’une meilleure solution soit trouvée.

- `Get-Clipboard`
- `Set-Clipboard`
- `Add-Computer`
- `Checkpoint-Computer`
- `Remove-Computer`
- `Restore-Computer`
- `Reset-ComputerMachinePassword`
- `Disable-ComputerRestore`
- `Enable-ComputerRestore`
- `Get-ComputerRestorePoint`
- `Test-ComputerSecureChannel`
- `Get-ControlPanelItem`
- `Show-ControlPanelItem`
- `Get-HotFix`
- `Clear-RecycleBin`
- `Update-List`
- `Out-Printer`
- `ConvertFrom-String`
- `Convert-String`

### <a name="-counter-cmdlets"></a>Cmdlets `*-Counter`

En raison de l’utilisation des API non prises en charge, `*-Counter` a été supprimé de PowerShell jusqu’à ce qu’une meilleure solution soit trouvée.

### <a name="-eventlog-cmdlets"></a>Cmdlets `*-EventLog`

En raison de l’utilisation des API non prises en charge, `*-EventLog` a été supprimé de PowerShell Core jusqu’à ce qu’une meilleure solution soit trouvée. `Get-WinEvent` et `Create-WinEvent` sont disponibles pour obtenir et créer des événements sur Windows.

### <a name="cmdlets-that-use-wpf-removed"></a>Les cmdlets qui utilisent WPF ont été supprimées

WPF n’est pas pris en charge sur CoreCLR. Les cmdlets suivantes sont affectées :

- `Show-Command`
- `Out-GridView`
- Le paramètre **showwindow** de `Get-Help`

### <a name="some-dsc-cmdlets-removed"></a>Certaines cmdlets DSC supprimées

- `Get-DscConfiguration`
- `Publish-DscConfiguration`
- `Restore-DscConfiguration`
- `Start-DscConfiguration`
- `Stop-DscConfiguration`
- `Test-DscConfiguration`
- `Update-DscConfiguration`
- `Remove-DscConfigurationDocument`
- `Get-DscConfigurationStatus`
- `Disable-DscDebug`
- `Enable-DscDebug`
- `Get-DscLocalConfigurationManager`
- `Set-DscLocalConfigurationManager`
- `Invoke-DscResource`

## <a name="enginelanguage-changes"></a>Modifications apportées au moteur/langage

### <a name="rename-powershellexe-to-pwshexe-5101"></a>Renommer `powershell.exe` pour `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Afin d’offrir aux utilisateurs une solution déterministe pour appeler PowerShell Core sur Windows (par opposition à Windows PowerShell), le fichier binaire PowerShell Core a été remplacé par `pwsh.exe` sur Windows et `pwsh` sur les autres plateformes.

Le nom abrégé est également cohérent avec la désignation des shells sur les plateformes non Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193"></a>Ne pas insérer de sauts de ligne en sortie (sauf pour les tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Auparavant, la sortie était alignée sur la largeur de la console et des sauts de ligne étaient ajoutés à la largeur de fin de la console, ce qui signifie que la sortie n’était pas reformatée comme prévu si le terminal était redimensionné. Cette modification n’a pas été appliquée aux tables, car les sauts de ligne sont nécessaires pour garantir l’alignement des colonnes.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432"></a>Ignorer la vérification de l’élément null pour les collections avec un élément de type valeur [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Pour le paramètre `Mandatory` et les attributs `ValidateNotNull` et `ValidateNotNullOrEmpty`, ignorer la vérification de l’élément null si le type d’élément de la collection est de type valeur.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369"></a>Modifier `$OutputEncoding` pour utiliser l’encodage `UTF-8 NoBOM` plutôt qu’ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

L’encodage précédent, ASCII (7 bits) causait une modification incorrecte de la sortie dans certains cas. Cette modification vise à faire de `UTF-8 NoBOM` la valeur par défaut, qui conserve la sortie Unicode avec un encodage pris en charge par la plupart des outils et systèmes d’exploitation.

### <a name="remove-allscope-from-most-default-aliases-5268"></a>Supprimer `AllScope` de la plupart des alias par défaut [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Pour accélérer la création d’étendue, `AllScope` a été supprimé de la plupart des alias par défaut. `AllScope` a été conservé pour quelques alias fréquemment utilisés, où la recherche était plus rapide.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113"></a>`-Verbose` et `-Debug` ne remplacent plus `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Auparavant, si `-Verbose` ou `-Debug` était spécifié, il remplaçait le comportement de `$ErrorActionPreference`. Avec cette modification, `-Verbose` et `-Debug` n’affectent plus le comportement de `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Modifications apportées aux cmdlets

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320"></a>Invoke-RestMethod ne retourne pas d’informations utiles quand aucune donnée n’est retournée. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Lorsqu’une API retourne simplement `null`, Invoke-RestMethod sérialisait cet élément comme la chaîne `"null"` au lieu de `$null`. Cette modification résout la logique dans `Invoke-RestMethod` pour sérialiser correctement une seule valeur JSON valide `null` de manière littérale en tant que `$null`.

### <a name="remove--protocol-from--computer-cmdlets-5277"></a>Supprimer `-Protocol` des cmdlets `*-Computer`[#5277](https://github.com/PowerShell/PowerShell/issues/5277)

En raison de problèmes avec l’accès à distance RPC dans CoreFX (en particulier sur les plateformes non Windows) et en vue de garantir une expérience cohérente de la communication à distance dans PowerShell, le paramètre `-Protocol` a été supprimé des cmdlets `\*-Computer`. DCOM n’est plus pris en charge pour la communication à distance. Les applets de commande suivantes prennent en charge seulement la communication à distance WSMAN :

- Rename-Computer
- Restart-Computer
- Stop-Computer

### <a name="remove--computername-from--service-cmdlets-5090"></a>Supprimer `-ComputerName` des cmdlets `*-Service`[#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Pour favoriser l’utilisation cohérente de PSRP, le paramètre `-ComputerName` a été supprimé des cmdlets `*-Service`.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197"></a>Corriger `Get-Item -LiteralPath a*b` si `a*b` n’existe pas réellement pour retourner l’erreur [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Auparavant, `-LiteralPath` avec un caractère générique le traitait de la même façon que `-Path` et si le caractère générique ne trouvait aucun fichier, il s’arrêtait en mode silencieux. Le comportement correct doit être que `-LiteralPath` est littéral, donc si le fichier n’existe pas, il doit afficher une erreur. La modification consiste à traiter les caractères génériques utilisés avec `-Literal` en tant qu’éléments littéraux.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134"></a>`Import-Csv` doit appliquer `PSTypeNames` lors de l’importation lorsque les informations de type sont présentes dans le CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Auparavant, les objets exportés utilisant `Export-CSV` avec `TypeInformation` importé avec `ConvertFrom-Csv` ne conservaient pas les informations de type. Cette modification ajoute des informations de type au membre `PSTypeNames` s’il est disponible dans le fichier CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131"></a>`-NoTypeInformation` doit prendre la valeur par défaut `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Cette modification a été apportée suite à des commentaires client sur le comportement par défaut de `Export-CSV` pour inclure les informations de type.

Auparavant, la cmdlet affichait un commentaire en tant que première ligne contenant le nom du type de l’objet. La modification consiste à supprimer cela par défaut, car cette opération n’est pas comprise par la plupart des outils. Utilisez `-IncludeTypeInformation` pour conserver le comportement précédent.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112"></a>Les cmdlets web doivent signaler lorsque `-Credential` est envoyé via des connexions non chiffrées [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Lorsque vous utilisez HTTP, le contenu, notamment les mots de passe, est envoyé en texte clair. Cette modification consiste à ne pas autoriser ce comportement par défaut et à retourner une erreur si les informations d’identification sont transmises de façon non sécurisée. Les utilisateurs peuvent contourner cela à l’aide du commutateur `-AllowUnencryptedAuthentication`.

## <a name="api-changes"></a>Modifications d'API

### <a name="remove-addtypecommandbase-class-5407"></a>Classe `AddTypeCommandBase` supprimée [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

La classe `AddTypeCommandBase` a été supprimée de `Add-Type` pour améliorer les performances. Cette classe est utilisée uniquement par la cmdlet Add-Type et ne devrait pas affecter les utilisateurs.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080"></a>Unifier les cmdlets avec le paramètre `-Encoding` de type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding` avec la valeur `Byte` a été supprimé des cmdlets du fournisseur de système de fichiers. Un nouveau paramètre, `-AsByteStream`, est désormais utilisé pour spécifier qu’un flux d’octets est requis en tant qu’entrée ou que la sortie est un flux d’octets.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055"></a>Ajouter un meilleur message d’erreur si le paramètre `-UFormat` est vide ou null [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Auparavant, lors de l’envoi d’une chaîne de format vide à `-UFormat`, un message d’erreur inutile s’affichait. Une erreur plus descriptive a été ajoutée.

### <a name="clean-up-console-code-4995"></a>Nettoyer le code de la console [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Les fonctionnalités suivantes ont été supprimées car elles ne sont pas prises en charge dans PowerShell Core, et il n’est pas prévu d’ajouter leur prise en charge, car elles existent pour des raisons d’héritage pour Windows PowerShell : commutateur et code `-psconsolefile`, commutateur et code `-importsystemmodules`, et code de modification de police.

### <a name="removed-runspaceconfiguration-support-4942"></a>Prise en charge de `RunspaceConfiguration` supprimée [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Auparavant, lors de la création d’une instance d’exécution PowerShell par programmation à l’aide de l’API, vous pouviez utiliser [`RunspaceConfiguration`][runspaceconfig] hérité ou [`InitialSessionState`][iss] plus récent. Cette modification supprime la prise en charge de `RunspaceConfiguration` et prend uniquement en charge `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923"></a>`CommandInvocationIntrinsics.InvokeScript` lie les arguments à `$input` au lieu de `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

En raison d’une position incorrecte d’un paramètre, les arguments étaient passés en tant qu’entrée au lieu d’arguments.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903"></a>Supprimer le commutateur `-showwindow` non pris en charge de `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` s’appuie sur WPF, qui n’est pas pris en charge dans CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866"></a>Autoriser l’utilisation de * dans le chemin du registre pour `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Auparavant, `-LiteralPath` avec un caractère générique le traitait de la même façon que `-Path` et si le caractère générique ne trouvait aucun fichier, il s’arrêtait en mode silencieux. Le comportement correct doit être que `-LiteralPath` est littéral, donc si le fichier n’existe pas, il doit afficher une erreur. La modification consiste à traiter les caractères génériques utilisés avec `-Literal` en tant qu’éléments littéraux.

### <a name="fix-set-service-failing-test-4802"></a>Corriger l’échec au test de `Set-Service`[#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Auparavant, si `New-Service -StartupType foo` était utilisé, `foo` était ignoré et le service était créé avec un certain type de démarrage par défaut. Cette modification vise à lever explicitement une erreur pour un type de démarrage non valide.

### <a name="rename-isosx-to-ismacos-4700"></a>Renommer `$IsOSX` par `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

L’affectation de noms dans PowerShell doit être cohérente avec notre affectation de noms et conforme à l’utilisation d’Apple de macOS au lieu de OSX. Toutefois, pour une lisibilité et une cohérence optimales, nous conservons la casse Pascal.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573"></a>Uniformiser le message d’erreur lorsqu’un script non valide est transmis à -File, erreur optimisée lors de l’envoi d’un argument ambigu [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Modifier les codes de sortie de `pwsh.exe` pour se conformer aux conventions Unix

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302-4303"></a>Suppression de `LocalAccount` et des cmdlets des modules `Diagnostics`. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

En raison d’API non prises en charge, le module `LocalAccounts` et les cmdlets `Counter` dans le module `Diagnostics` ont été supprimés jusqu’à ce qu’une meilleure solution soit trouvée.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036"></a>L’exécution du script PowerShell avec un paramètre bool ne fonctionne pas [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Auparavant, l’utilisation de **powershell.exe** (désormais **pwsh.exe**) pour exécuter un script PowerShell à l’aide de `-File` ne fournissait aucun moyen de transmettre `$true`/`$false` comme valeurs de paramètre. La prise en charge de `$true`/`$false` comme valeurs analysées des paramètres a été ajoutée. Les valeurs de commutateur sont également prises en charge, car la syntaxe actuellement documentée ne fonctionne pas.

### <a name="remove-clrversion-property-from-psversiontable-4027"></a>Supprimer la propriété `ClrVersion` de `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

La propriété `ClrVersion` de `$PSVersionTable` n’est pas utile avec CoreCLR, les utilisateurs finaux ne doivent pas utiliser cette valeur pour déterminer la compatibilité.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019"></a>Modifier le paramètre positionnel pour `powershell.exe` de `-Command` par `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Autoriser shebang à utiliser PowerShell sur les plateformes non Windows. Cela signifie que sur les systèmes Unix, vous pouvez rendre un script exécutable qui appelle PowerShell automatiquement au lieu d’appeler explicitement `pwsh`. Cela signifie également que vous pouvez faire des choses comme `powershell foo.ps1` ou `powershell fooScript` sans spécifier `-File`. Toutefois, cette modification nécessite désormais que vous indiquiez explicitement `-c` ou `-Command` quand vous essayez de faire des choses comme `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958"></a>Implémenter l’analyse d’échappement Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u####`` ou `` `u{####}`` est converti en caractère Unicode correspondant. Pour générer un `` `u`` littéral, appliquer l’échappement au guillemet inversé : ``` ``u```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940"></a>Modifier l’encodage `New-ModuleManifest` sur `UTF8NoBOM` pour les plateformes non Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Auparavant, `New-ModuleManifest` créait les manifestes psd1 en UTF-16 avec BOM, causant un problème pour les outils Linux. Cette modification avec rupture modifie l’encodage de `New-ModuleManifest` sur UTF (sans BOM) pour les plateformes non Windows.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780"></a>Empêcher la récurrence de `Get-ChildItem` dans des liens symboliques (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Cette modification aligne `Get-ChildItem` avec `ls -r` Unix et les commandes natives `dir /s` Windows. Comme les commandes mentionnées, la cmdlet affiche des liens symboliques vers les répertoires trouvés lors de la récursivité, mais elle n’est pas récursive dans ceux-ci.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706"></a>Corriger `Get-Content -Delimiter` pour ne pas inclure le délimiteur dans les lignes retournées [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Auparavant, la sortie lors de l’utilisation de `Get-Content -Delimiter` était incohérente et peu pratique, car elle nécessitait un traitement supplémentaire des données pour supprimer le délimiteur. Cette modification supprime le délimiteur dans les lignes retournées.

### <a name="implement-format-hex-in-c-3320"></a>Implémenter Format-Hex dans C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

Le paramètre `-Raw` est désormais un « no-op » (c’est-à-dire, qu’il ne fait rien). À l’avenir, l’ensemble de la sortie sera affiché avec une représentation réelle des nombres incluant tous les octets pour son type (ce que le paramètre `-Raw` faisait formellement avant cette modification).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319"></a>PowerShell en tant que shell par défaut ne fonctionne pas avec la commande de script [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

Sous Unix, une convention stipule que les shells doivent accepter `-i` pour un shell interactif et de nombreux outils attendent ce comportement (`script` par exemple, et lorsque PowerShell est défini en tant que shell par défaut), et appelle le shell avec le commutateur `-i`. Il s’agit d’une modification avec rupture, car `-i` pouvait auparavant être utilisé en tant que paramètre abrégé pour correspondre à `-inputformat`, qui doit maintenant être `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167"></a>Correction typographique dans le nom de la propriété Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` était mal orthographié en tant que `BiosSeralNumber` et a été remplacé par l’orthographe correcte.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024"></a>Ajouter les cmdlets `Get-StringHash` et `Get-FileHash`[#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Cette modification indique que certains algorithmes de hachage ne sont pas pris en charge par CoreFX, donc ils ne sont plus disponibles :

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672"></a>Ajouter la validation sur les cmdlets `Get-*` où la transmission de $null retourne tous les objets au lieu de l’erreur [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

La transmission de `$null` à l’un des éléments ci-dessous génère maintenant une erreur :

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482"></a>Ajouter le support Format de fichier journal étendu W3C dans `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Auparavant, la cmdlet `Import-Csv` ne pouvait pas être utilisée pour importer directement les fichiers journaux au format de journal étendu W3C et une action supplémentaire était nécessaire. Avec cette modification, le format de journal étendu W3C est pris en charge.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035"></a>Problème de liaison de paramètre avec `ValueFromRemainingArguments` dans les fonctions PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` retourne désormais les valeurs sous forme de tableau au lieu d’une seule valeur qui est elle-même un tableau.

### <a name="buildversion-is-removed-from-psversiontable-1415"></a>`BuildVersion` est supprimé de `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Suppression de la propriété `BuildVersion` de `$PSVersionTable`. Cette propriété était liée à la version de build Windows. Au lieu de cela, nous vous recommandons d’utiliser `GitCommitId` pour récupérer la version de build exacte de PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Modifications apportées aux cmdlets web

L’API .NET sous-jacente des cmdlets web a été remplacée par `System.Net.Http.HttpClient`. Cette modification offre de nombreux avantages. Toutefois, cette modification, ainsi qu’un manque d’interopérabilité avec Internet Explorer, ont causé plusieurs modifications avec rupture dans `Invoke-WebRequest` et `Invoke-RestMethod`.

- `Invoke-WebRequest` prend désormais en charge l’analyse HTML de base uniquement. `Invoke-WebRequest` retourne toujours un objet `BasicHtmlWebResponseObject`. Les propriétés `ParsedHtml` et `Forms` ont été supprimées.
- Les valeurs `BasicHtmlWebResponseObject.Headers` sont maintenant `String[]` au lieu de `String`.
- `BasicHtmlWebResponseObject.BaseResponse` est désormais un objet `System.Net.Http.HttpResponseMessage`.
- La propriété `Response` sur les exceptions de cmdlet web est désormais un objet `System.Net.Http.HttpResponseMessage`.
- L’analyse d’en-tête RFC stricte est désormais la valeur par défaut pour les paramètres `-Headers` et `-UserAgent`. Vous pouvez contourner ceci avec `-SkipHeaderValidation`.
- Les schémas d’URI `file://` et `ftp://` ne sont plus pris en charge.
- Les paramètres `System.Net.ServicePointManager` ne sont plus respectés.
- Aucune authentification par certificat n’est actuellement disponible sur macOS.
- L’utilisation de `-Credential` sur un URI `http://` génère une erreur. Utilisez un URI `https://` ou fournissez le paramètre `-AllowUnencryptedAuthentication` pour supprimer l’erreur.
- `-MaximumRedirection` génère désormais une erreur avec fin d’exécution quand les tentatives de redirection dépassent la limite fournie au lieu de retourner les résultats de la dernière redirection.
- Dans PowerShell 6.2, une modification a été apportée pour sélectionner par défaut à le codage UTF-8 pour les réponses JSON. Lorsqu’un jeu de caractères n’est pas fourni pour une réponse JSON, le codage par défaut doit être UTF-8 par RFC 8259.
