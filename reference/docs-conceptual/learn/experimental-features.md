---
ms.date: 12/14/2020
title: Utilisation des fonctionnalités expérimentales dans PowerShell
description: Répertorie les fonctionnalités expérimentales actuellement disponibles et leur mode d’utilisation.
ms.openlocfilehash: f97cea1dff4030da22be1efbe3cd5cbb7a9f3527
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685282"
---
# <a name="using-experimental-features-in-powershell"></a>Utilisation des fonctionnalités expérimentales dans PowerShell

La prise en charge des Fonctionnalités expérimentales dans PowerShell fournit un mécanisme permettant aux fonctionnalités expérimentales de coexister avec les fonctionnalités stables existantes dans PowerShell ou les modules PowerShell.

Une fonctionnalité expérimentale est une fonctionnalité dans laquelle la conception n’est pas finalisée. Les utilisateurs peuvent tester la fonctionnalité et fournir des commentaires. Lorsqu’une fonctionnalité expérimentale est finalisée, les modifications apportées à la conception deviennent des changements cassants.

> [!CAUTION]
> Les fonctionnalités expérimentales ne sont pas destinées à être utilisées en production, car les changements peuvent être cassants. Les fonctionnalités expérimentales ne sont pas officiellement prises en charge. Toutefois, nous apprécions de recevoir des commentaires et des rapports de bogues. Vous pouvez consigner les problèmes dans le [référentiel source GitHub](https://github.com/PowerShell/PowerShell/issues/new/choose).

Pour plus d’informations sur l’activation ou la désactivation de ces fonctionnalités, consultez [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).

## <a name="available-features"></a>Fonctionnalités disponibles

Cet article décrit les fonctionnalités expérimentales disponibles et leur mode d’utilisation.

|                            Nom                            |   6.2   |   7.0   |   7.1   |   7.2   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: | :-----: |
| PSTempDrive (standard dans PS 7.0+)                        | &check; |         |         |         |
| PSUseAbbreviationExpansion (standard dans PS 7.0+)         | &check; |         |         |         |
| PSNullConditionalOperators (standard dans PS 7.1+)         |         | &check; |         |         |
| PSUnixFileStat (non-Windows uniquement - standard dans PS 7.1+)  |         | &check; |         |         |
| PSCommandNotFoundSuggestion                                | &check; | &check; | &check; | &check; |
| PSImplicitRemotingBatching                                 | &check; | &check; | &check; | &check; |
| Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace |         | &check; | &check; | &check; |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; | &check; | &check; |
| PSNativePSPathResolution                                   |         |         | &check; | &check; |
| PSCultureInvariantReplaceOperator                          |         |         | &check; | &check; |
| PSNotApplyErrorActionToStderr                              |         |         | &check; | &check; |
| PSSubsystemPluginModel                                     |         |         | &check; | &check; |
| PSAnsiProgress                                             |         |         |         | &check; |
| PSAnsiRendering                                            |         |         |         | &check; |

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

## <a name="psansirendering"></a>PSAnsiRendering

Cette expérience a été ajoutée dans PowerShell 7.2. La fonctionnalité permet de modifier la façon dont le moteur PowerShell génère du texte et ajoute la variable automatique `$PSStyle` pour contrôler le rendu ANSI de la sortie de chaîne.

```powershell
PS> $PSStyle | Get-Member

   TypeName: System.Management.Automation.PSStyle

Name             MemberType Definition
----             ---------- ----------
Equals           Method     bool Equals(System.Object obj)
FormatHyperlink  Method     string FormatHyperlink(string text, uri link)
GetHashCode      Method     int GetHashCode()
GetType          Method     type GetType()
ToString         Method     string ToString()
Background       Property   System.Management.Automation.PSStyle+BackgroundColor Background {get;}
Blink            Property   string Blink {get;}
BlinkOff         Property   string BlinkOff {get;}
Bold             Property   string Bold {get;}
BoldOff          Property   string BoldOff {get;}
Foreground       Property   System.Management.Automation.PSStyle+ForegroundColor Foreground {get;}
Formatting       Property   System.Management.Automation.PSStyle+FormattingData Formatting {get;}
Hidden           Property   string Hidden {get;}
HiddenOff        Property   string HiddenOff {get;}
Italic           Property   string Italic {get;}
ItalicOff        Property   string ItalicOff {get;}
OutputRendering  Property   System.Management.Automation.OutputRendering OutputRendering {get;set;}
Progress         Property   System.Management.Automation.PSStyle+ProgressConfiguration Progress {get;}
Reset            Property   string Reset {get;}
Reverse          Property   string Reverse {get;}
ReverseOff       Property   string ReverseOff {get;}
Strikethrough    Property   string Strikethrough {get;}
StrikethroughOff Property   string StrikethroughOff {get;}
Underline        Property   string Underline {get;}
UnderlineOff     Property   string UnderlineOff {get;}
```

Les membres de base retournent des chaînes de séquences d’échappement ANSI mappées à leurs noms. Les valeurs peuvent être définies de façon à autoriser la personnalisation.

Pour plus d’informations, consultez [about_Automatic_Variables](/reference/7.2/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

> [!NOTE]
> Pour les développeurs C#, vous pouvez accéder à `PSStyle` en tant que singleton. L’utilisation se présente comme suit :
>
> ```csharp
> string output = $"{PSStyle.Instance.Foreground.Red}{PSStyle.Instance.Bold}Hello{PSStyle.Instance.Reset}";
> ```
>
> `PSStyle` existe dans l’espace de noms System.Management.Automation.

Avec l’accès à `$PSStyle`, cela introduit des changements dans le moteur PowerShell. Le système de mise en forme de PowerShell est mis à jour pour respecter `$PSStyle.OutputRendering`.

- Le type `StringDecorated` est ajouté pour gérer les chaînes d’échappement ANSI.
- La propriété booléenne `string IsDecorated` est ajoutée pour retourner si la chaîne contient des séquences d’échappement ANSI selon si la chaîne contient des caractères ESC ou C1 CSI.
- La propriété `Length` retourne _uniquement_ la longueur du texte sans les séquences d’échappement ANSI.
- La méthode `StringDecorated Substring(int contentLength)` retourne une sous-chaîne commençant à l’index 0 jusqu’à la longueur du contenu qui ne fait pas partie des séquences d’échappement ANSI. C’est nécessaire pour que la mise en forme de la table tronque les chaînes et conserve les séquences d’échappement ANSI qui n’occupent pas un espace de caractère imprimable.
- La méthode `string ToString()` reste la même et retourne la version en texte clair de la chaîne.
- La méthode `string ToString(bool Ansi)` retourne la chaîne incorporée ANSI brute si le paramètre `Ansi` a la valeur true. Dans le cas contraire, une version en texte en clair avec des séquences d’échappement ANSI supprimées est retournée.

`FormatHyperlink(string text, uri link)` retourne une chaîne contenant une séquence d’échappement ANSI utilisée pour décorer les liens hypertexte. Certains hôtes de terminal, comme le [Terminal Windows](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701), prennent en charge ce balisage, ce qui permet de cliquer sur le texte rendu dans le terminal.

## <a name="psansiprogress"></a>PSAnsiProgress

Cette expérience a été ajoutée dans PowerShell 7.2. La fonctionnalité ajoute le membre `$PSStyle.Progress` et vous permet de contrôler le rendu de la barre d’affichage de la progression.

- `$PSStyle.Progress.Style` – Chaîne ANSI définissant le style de rendu.
- `$PSStyle.Progress.MaxWidth` – Définit la largeur maximale de l’affichage. Défini sur `0` pour la largeur de la console.
  La valeur par défaut est `120`
- `$PSStyle.Progress.View` – Énumération avec les valeurs `Minimal` et `Classic`. `Classic` est le rendu existant sans modification. `Minimal` est le rendu minimal à une seule ligne. `Minimal` est la valeur par défaut.

L’exemple suivant met à jour le style de rendu pour obtenir une barre de progression minimale.

```powershell
$PSStyle.Progress.View.Minimal
```

> [!NOTE]
> La fonctionnalité expérimentale **PSAnsiRendering** doit être activée pour que vous puissiez utiliser cette fonctionnalité.

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

> [!NOTE]
> Cette fonctionnalité a été déplacée de la phase expérimentale et est une fonctionnalité standard de PowerShell 7.1 et versions ultérieures.

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

Cette fonctionnalité permet la saisie semi-automatique par tabulation des cmdlets et des fonctions abrégées :

Par exemple :

- `i-psdf<tab>` retourne `Import-PowerShellDataFile`.
- `u-akvmssdr<tab>` retourne `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`

Cela ne fonctionne que pour la saisie semi-automatique par tabulation (utilisation interactive), donc `i-psdf` n’est pas un nom de cmdlet valide dans un script.

> [!NOTE]
> Cette fonctionnalité a été déplacée de la phase expérimentale et est une fonctionnalité standard de PowerShell 7 et versions ultérieures.

## <a name="pssubsystempluginmodel"></a>PSSubsystemPluginModel

Cette fonctionnalité active le modèle de plug-in de sous-système dans PowerShell. La fonctionnalité permet de diviser les composants de `System.Management.Automation.dll` en sous-systèmes individuels qui résident dans leur propre assembly. Cette division réduit l’encombrement de disque du moteur PowerShell principal et permet à ces composants de devenir des fonctionnalités facultatives pour une installation PowerShell minimale.

Actuellement, seul le sous-système **CommandPredictor** est pris en charge. Ce sous-système est utilisé avec le module PSReadLine pour fournir des plug-ins de prédiction personnalisés. À l’avenir, **Job**, **CommandCompleter**, **Remoting** et d’autres composants pourraient être divisés en assemblys de sous-système en dehors de `System.Management.Automation.dll`.

La fonctionnalité expérimentale comprend une nouvelle applet de commande, [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem). Cette applet de commande est disponible uniquement lorsque la fonctionnalité est activée. Cette applet de commande retourne des informations sur les sous-systèmes disponibles sur le système.
