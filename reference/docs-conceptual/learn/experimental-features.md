---
ms.date: 09/14/2020
title: Utilisation des fonctionnalités expérimentales dans PowerShell
description: Répertorie les fonctionnalités expérimentales actuellement disponibles et leur mode d’utilisation.
ms.openlocfilehash: 74623240bfb19022ae342a5d23e2ed4f455afa45
ms.sourcegitcommit: 30c0c1563f8e840f24b65297e907f3583d90e677
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90574468"
---
# <a name="using-experimental-features-in-powershell"></a>Utilisation des fonctionnalités expérimentales dans PowerShell

La prise en charge des Fonctionnalités expérimentales dans PowerShell fournit un mécanisme permettant aux fonctionnalités expérimentales de coexister avec les fonctionnalités stables existantes dans PowerShell ou les modules PowerShell.

Une fonctionnalité expérimentale est une fonctionnalité dans laquelle la conception n’est pas finalisée. Les utilisateurs peuvent tester la fonctionnalité et fournir des commentaires. Lorsqu’une fonctionnalité expérimentale est finalisée, les modifications apportées à la conception deviennent des changements cassants.

> [!CAUTION]
> Les fonctionnalités expérimentales ne sont pas destinées à être utilisées en production, car les changements peuvent être cassants. Les fonctionnalités expérimentales ne sont pas officiellement prises en charge. Toutefois, nous apprécions de recevoir des commentaires et des rapports de bogues. Vous pouvez consigner les problèmes dans le [référentiel source GitHub](https://github.com/PowerShell/PowerShell/issues/new/choose).

Pour plus d’informations sur l’activation ou la désactivation de ces fonctionnalités, consultez [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).

## <a name="available-features"></a>Fonctionnalités disponibles

Cet article décrit les fonctionnalités expérimentales disponibles et leur mode d’utilisation.

|                            Nom                            |   6.2   |   7.0   |   7.1   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: |
| PSTempDrive (standard dans PS 7.0+)                        | &check; |         |         |
| PSUseAbbreviationExpansion (standard dans PS 7.0+)         | &check; |         |         |
| PSCommandNotFoundSuggestion                                | &check; | &check; | &check; |
| PSImplicitRemotingBatching                                 | &check; | &check; | &check; |
| Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace |         | &check; | &check; |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; | &check; |
| PSNullConditionalOperators (standard dans PS 7.1+)         |         | &check; |         |
| PSUnixFileStat (non-Windows uniquement)                          |         | &check; | &check; |
| PSNativePSPathResolution (standard dans PS 7.1+)           |         |         |         |
| PSCultureInvariantReplaceOperator                          |         |         | &check; |
| PSNotApplyErrorActionToStderr                              |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a>Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace

Dans PowerShell 7.0, l’expérience active le paramètre **BreakAll** sur les cmdlets `Debug-Runspace` et `Debug-Job` pour permettre aux utilisateurs de décider s’ils veulent que PowerShell s’arrête immédiatement à l’emplacement actuel lorsqu’ils attachent un débogueur.

Dans PowerShell 7.1, cette expérimentation ajoute également le paramètre **Runspace** aux applets de commande `*-PSBreakpoint`.

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

Le paramètre **Runspace** spécifie un objet **Runspace** pour interagir avec des points d’arrêt dans l’instance d’exécution spécifiée.

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

Dans cet exemple, un travail est démarré et un point d’arrêt est défini pour s’arrêter lors de l’exécution du `Set-PSBreakPoint`. L’instance d’exécution est stockée dans une variable et passée à la commande `Get-PSBreakPoint` avec le paramètre **Runspace**. Vous pouvez ensuite inspecter le point d’arrêt dans la variable `$breakpoint`.

## <a name="pscommandnotfoundsuggestion"></a>PSCommandNotFoundSuggestion

Recommande des commandes potentielles en fonction de la recherche de correspondance approximative après **CommandNotFoundException**.

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a>PSCultureInvariantReplaceOperator

Lorsque l’opérande gauche dans une instruction opérateur `-replace` n’est pas une chaîne, cet opérande est converti en chaîne.

Lorsque cette fonctionnalité est désactivée, l’opérateur `-replace` effectue une conversion de chaîne dépendante de la culture.
Par exemple, si votre culture est définie sur Français (fr), la valeur `1.2` est convertie en chaîne `1,2`.

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

Avec la fonctionnalité activée :

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a>PSDesiredStateConfiguration.InvokeDscResource

Active la compilation en MOF sur les systèmes non-Windows et permet l’utilisation de `Invoke-DSCResource` sans LCM.

## <a name="psimplicitremotingbatching"></a>PSImplicitRemotingBatching

Cette fonctionnalité examine la commande tapée dans l’interpréteur de commandes, et si toutes les commandes sont des commandes proxy de communication à distance implicites qui forment un pipeline simple, les commandes sont regroupées et appelées en tant que pipeline à distance unique.

Exemple :

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

Comme indiqué ci-dessus, avec la fonctionnalité de traitement par lot activée, les trois commandes proxy de communication à distance implicite, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, s’exécutent dans la session à distance et le résultat du pipeline est les seules données retournées au client. Cela réduit la quantité de données qui circulent entre le client et la session à distance, et réduit également la quantité de sérialisation et de désérialisation d’objets.

## <a name="psnativepspathresolution"></a>PSNativePSPathResolution

Si un chemin PSDrive qui utilise le fournisseur FileSystem est passé à une commande native, le chemin du fichier résolu est passé à la commande native. Cela signifie qu’une commande comme `code temp:/test.txt` fonctionne à présent comme prévu.

En outre, sur Windows, si le chemin commence par `~`, il est résolu en chemin d’accès complet et transmis à la commande native. Dans les deux cas, le chemin est normalisé aux séparateurs de répertoire pour le système d’exploitation approprié.

- Si le chemin n’est pas PSDrive ou `~` (sur Windows), la normalisation de chemin d’accès ne se produit pas
- Si le chemin est placé entre guillemets simples, il n’est pas résolu et traité comme littéral

> [!NOTE]
> Cette fonctionnalité a été déplacée de la phase expérimentale et est une fonctionnalité standard de PowerShell 7.1 et versions ultérieures.

## <a name="psnotapplyerroractiontostderr"></a>PSNotApplyErrorActionToStderr

Lorsque cette fonctionnalité expérimentale est activée, les enregistrements d’erreurs redirigés à partir de commandes natives, par exemple lors de l’utilisation d’opérateurs de redirection (`2>&1`), ne sont pas écrits dans la variable `$Error` et la variable de préférence `$ErrorActionPreference` n’affecte pas la sortie redirigée.

De nombreuses commandes natives écrivent dans `stderr` en tant que flux de remplacement pour obtenir des informations supplémentaires. Ce comportement peut entraîner une confusion lors de l’examen des erreurs, ou les informations de sortie supplémentaires peuvent être perdues pour l’utilisateur si `$ErrorActionPreference` est défini sur un état qui désactive la sortie.

Quand une commande native a un code de sortie différent de zéro, `$?` a la valeur `$false`. Si le code de sortie est égal à zéro, `$?` a la valeur `$true`.

## <a name="psnullconditionaloperators"></a>PSNullConditionalOperators

Introduit de nouveaux opérateurs pour les opérateurs d’accès de membre conditionnel Null, `?.` et `?[]`. Les opérateurs d’accès de membre Null peuvent être utilisés sur des types scalaires et des types tableau. Retourne la valeur du membre ayant fait l’objet d’un accès si la variable n’est pas Null. Si la valeur de la variable est Null, retourne la valeur Null.

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

La propriété `propname` fait l’objet d’un accès et sa valeur est retournée uniquement si `$x` n’est pas Null. De même, l’indexeur est utilisé uniquement si `$x` n’a pas la valeur Null. Si `$x` est Null, alors Null est retourné.

Les opérateurs `?.` et `?[]` sont des opérateurs d’accès de membre et n’autorisent pas d’espace entre le nom de la variable et l’opérateur.

Étant donné que PowerShell autorise `?` dans le cadre du nom de la variable, toute suppression d’ambiguïté est nécessaire lorsque les opérateurs sont utilisés sans espace entre le nom de la variable et l’opérateur. Pour lever l’ambiguïté, les variables doivent utiliser `{}` autour du nom de la variable, par exemple : `${x?}?.propertyName` ou `${y}?[0]`.

> [!NOTE]
> Cette fonctionnalité a été déplacée de la phase expérimentale et est une fonctionnalité standard de PowerShell 7.1 et versions ultérieures.

## <a name="pstempdrive"></a>PSTempDrive

Crée le PSDrive `TEMP:` mappé au chemin du répertoire temporaire de l’utilisateur.

> [!NOTE]
> Cette fonctionnalité a été déplacée de la phase expérimentale et est une fonctionnalité standard de PowerShell 7 et versions ultérieures.

## <a name="psunixfilestat"></a>PSUnixFileStat

Cette fonctionnalité offre un nouveau comportement permettant d’inclure des données de l’API **stat** Unix dans la sortie du fournisseur de système de fichiers pour faciliter l’affichage des fichiers plus similaire à Unix. Elle ajoute une nouvelle propriété de note dans le fournisseur du système de fichiers nommé **UnixStat** qui inclut une expression commune de l’API `stat(2)` à partir du système de type Unix sous-jacent.

La sortie de `Get-ChildItem` suivant doit ressembler à ce qui suit :

```powershell
dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

Cette fonctionnalité permet la saisie semi-automatique par tabulation des cmdlets et des fonctions abrégées :

Par exemple :

- `i-psdf<tab>` retourne `Import-PowerShellDataFile`.
- `u-akvmssdr<tab>` retourne `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`

Cela ne fonctionne que pour la saisie semi-automatique par tabulation (utilisation interactive), donc `i-psdf` n’est pas un nom de cmdlet valide dans un script.

> [!NOTE]
> Cette fonctionnalité a été déplacée de la phase expérimentale et est une fonctionnalité standard de PowerShell 7 et versions ultérieures.
