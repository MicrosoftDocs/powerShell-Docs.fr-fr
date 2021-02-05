---
title: Fonctions
description: Les fonctions PowerShell vous permettent de créer des outils réutilisables dans des scripts.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e4734b556a78f67c54152dad93eada536dd1c928
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598337"
---
# <a name="chapter-9---functions"></a>Chapitre 9 : Fonctions

Si vous écrivez des one-liners ou des scripts PowerShell que vous devez ensuite souvent modifier pour des scénarios différents, vous aurez probablement intérêt à les transformer en fonctions réutilisables.

Dans la mesure du possible, je préfère écrire des fonctions, car elles sont davantage orientées outil. Je peux ajouter les fonctions dans un module de script, placer ce module dans `$env:PSModulePath`et appeler les fonctions sans avoir à localiser l’emplacement physique où elles sont enregistrées. Avec PowerShellGet, partager ces modules dans un dépôt NuGet est très simple. PowerShellGet est fourni avec PowerShell version 5.0 et versions ultérieures. Il est disponible en téléchargement pour PowerShell version 3.0 et versions ultérieures.

Ne compliquez pas les choses. Privilégiez la simplicité et choisissez le moyen le plus rapide pour effectuer une tâche. N’utilisez pas d’alias ni de paramètres positionnels dans du code que vous comptez réutiliser. Mettez en forme votre code dans un souci d’en faciliter la lecture. Ne codez pas les valeurs en dur, utilisez des paramètres et des variables. N’écrivez pas de code inutile, même s’il n’a aucun effet gênant. Cela rend les choses plus complexes inutilement. Le souci du détail est essentiel quand vous écrivez du code PowerShell.

## <a name="naming"></a>Dénomination

Quand vous nommez vos fonctions dans PowerShell, utilisez un nom [casse Pascal][] avec un verbe approuvé et un nom au singulier. Je recommande également d’ajouter un préfixe au nom. Par exemple : `<ApprovedVerb>-<Prefix><SingularNoun>`.

Dans PowerShell, il existe une liste spécifique de verbes approuvés que vous pouvez obtenir à l’aide de la commande `Get-Verb`.

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

Dans l’exemple précédent, j’ai trié les résultats sur la colonne **Verb**. La colonne **Group** vous donne une idée de la façon dont ces verbes sont utilisés. Il est important de choisir un verbe approuvé dans PowerShell quand des fonctions sont ajoutées à un module. Si vous avez choisi un verbe non approuvé, le module génère un message d’avertissement au moment du chargement. Ce message d’avertissement donne une image peu professionnelle à vos fonctions. De plus, les verbes non approuvés rendent vos fonctions plus difficiles à détecter.

## <a name="a-simple-function"></a>Une fonction simple

Dans PowerShell, une fonction se déclare avec le mot clé function suivi du nom de la fonction, d’une accolade ouvrante et d’une accolade fermante. Le code que la fonction exécutera est placé entre ces deux accolades.

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

Cette fonction est un exemple simple qui retourne la version de PowerShell.

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Il y a souvent des conflits de noms entre les fonctions portant un nom comme `Get-Version` et les commandes par défaut dans PowerShell ou les commandes que d’autres utilisateurs écrivent. C’est la raison pour laquelle je vous recommande d’ajouter un préfixe au nom de vos fonctions, qui permet de limiter le risque de conflits de noms. Dans l’exemple suivant, je vais utiliser le préfixe « PS ».

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

En dehors du nom, cette fonction est identique à la précédente.

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Même en préfixant le nom avec un élément comme PS, le risque de conflits de noms reste présent. Je préfixe généralement mes noms de fonctions avec mes initiales. Établissez une convention et respectez-la.

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

Cette fonction est identique aux deux précédentes si ce n’est l’usage d’un nom plus judicieux pour éviter le plus possible les conflits de noms avec d’autres commandes PowerShell.

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Une fois les fonctions chargées en mémoire, vous les voyez sur le PSDrive **Function**.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

Si vous souhaitez supprimer ces fonctions de votre session active, vous devez les supprimer du PSDrive **Function** ou fermer et rouvrir PowerShell.

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

Vérifiez que les fonctions ont bien été supprimées.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

Si les fonctions ont été chargées avec un module, le module peut être déchargé pour supprimer les fonctions.

```powershell
Remove-Module -Name <ModuleName>
```

L’applet de commande `Remove-Module` supprime les modules en mémoire dans votre session PowerShell active, elle ne les supprime pas de votre système ou du disque.

## <a name="parameters"></a>Paramètres

N’attribuez pas de valeurs de manière statique ! Utilisez des paramètres et des variables. Pour nommer vos paramètres, utilisez les mêmes noms de paramètres que les applets de commande par défaut chaque fois que cela est possible.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Pourquoi ai-je utilisé **ComputerName** et non **Computer**, **ServerName** ou **Host** comme nom de paramètre ? C’est parce que je voulais que ma fonction suive les conventions des applets de commande par défaut.

Je vais créer une fonction pour obtenir toutes les commandes sur un système et retourner le nombre d’entre elles qui ont des noms de paramètres spécifiques.

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

Comme vous pouvez le voir dans les résultats ci-dessous, 39 commandes ont un paramètre **ComputerName**. Il n’y a pas d’applets de commande avec les paramètres **Computer**, **ServerName**, **Host** ou **Machine**.

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

Je vous recommande aussi d’utiliser la même casse dans vos noms de paramètres que les applets de commande par défaut. Par exemple, utilisez `ComputerName`, pas `computername`. Ainsi, vos fonctions auront l’apparence des applets de commande par défaut. Les personnes qui sont déjà familiarisées avec PowerShell ne seront pas dépaysées.

L' `param` instruction vous permet de définir un ou plusieurs paramètres. Les définitions des paramètres sont séparées par une virgule ( `,` ). Pour plus d’informations, consultez [about_Functions_Advanced_Parameters][].

## <a name="advanced-functions"></a>Fonctions avancées

Transformer une fonction dans PowerShell en fonction avancée est une opération très simple. L’une des différences entre une fonction et une fonction avancée est que plusieurs paramètres courants sont automatiquement ajoutés aux fonctions avancées. **Verbose** et **Debug** sont deux de ces paramètres courants.

Je vais d’abord parler de la fonction `Test-MrParameter` qui a été utilisée dans la section précédente.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Ce que je veux vous montrer, c’est que la fonction `Test-MrParameter` n’a pas de paramètres courants. Il existe plusieurs façons de voir les paramètres courants. La première consiste à afficher la syntaxe à l’aide de `Get-Command`.

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

Une autre consiste à parcourir les paramètres avec `Get-Command`.

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

Vous ajoutez ensuite `CmdletBinding` pour transformer la fonction en fonction avancée.

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

L’ajout de `CmdletBinding` entraîne l’ajout automatique des paramètres courants. `CmdletBinding` requiert un bloc `param`, mais le bloc `param` peut être vide.

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

L’exploration des paramètres avec `Get-Command` affiche les noms de paramètres réels, y compris des paramètres courants.

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

`SupportsShouldProcess` ajoute les paramètres **WhatIf** et **Confirm**. Ces paramètres sont nécessaires uniquement pour les commandes de modification.

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Vous voyez maintenant les paramètres **WhatIf** et **Confirm**.

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Ici encore, vous pouvez utiliser `Get-Command` pour retourner une liste des noms de paramètres réels, avec ceux des paramètres courants plus WhatIf et Confirm.

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a>Validation des paramètres

La validation de l’entrée doit se faire très tôt. Quel intérêt y aurait-il à laisser votre code s’exécuter s’il ne trouve pas l’entrée valide dont il a besoin ?

Définissez toujours le type des variables utilisées pour vos paramètres (en clair, spécifiez un type de données).

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

Dans l’exemple précédent, j’ai spécifié **String** comme type de données pour le paramètre **ComputerName**. Un seul nom d’ordinateur peut donc être spécifié. Si plusieurs noms d’ordinateur sont spécifiés sous forme d’une liste séparée par des virgules, une erreur est générée.

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

Le problème avec la définition actuelle est qu’il est possible d’omettre la valeur du paramètre **ComputerName**, alors qu’une valeur est attendue pour que la fonction puisse s’exécuter. C’est là où l’attribut de paramètre `Mandatory` est utile.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

La syntaxe utilisée dans l’exemple précédent est compatible avec PowerShell 3.0 et versions ultérieures.
La syntaxe `[Parameter(Mandatory=$true)]` doit être utilisée à la place pour rendre la fonction compatible avec PowerShell version 2.0 et versions ultérieures. Maintenant que le paramètre **ComputerName** est rendu obligatoire, si aucun n’est spécifié, la fonction demandera d’en spécifier un.

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

Si vous voulez autoriser plusieurs valeurs pour le paramètre **ComputerName**, choisissez le type de données **String** et spécifiez-le entre deux crochets ouvert et fermé pour autoriser un tableau de chaînes.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

Vous voudrez peut-être spécifier une valeur par défaut à utiliser pour le paramètre **ComputerName** quand aucune valeur n’est spécifiée.
Le problème est que l’utilisation de valeurs par défaut n’est pas possible avec des paramètres obligatoires. À la place, vous devrez utiliser l’attribut de validation de paramètre `ValidateNotNullOrEmpty` avec une valeur par défaut.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

Même si vous définissez une valeur par défaut, évitez d’utiliser des valeurs statiques. Dans l’exemple précédent, `$env:COMPUTERNAME` est utilisé comme valeur par défaut, qui est automatiquement remplacée par le nom de l’ordinateur local si aucune valeur n’est fournie.

## <a name="verbose-output"></a>Sortie détaillée

Bien que les commentaires inline soient utiles, en particulier si vous écrivez du code complexe, ils ne sont jamais vus par les utilisateurs, sauf par ceux qui examinent le code de près.

La fonction illustrée dans l’exemple suivant contient un commentaire inline dans la boucle `foreach`. Ce commentaire particulier n’est pas difficile à localiser, mais imaginez ce que cela serait si la fonction incluait des centaines de lignes de code.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

Il est préférable d’utiliser la fonction `Write-Verbose` au lieu de commentaires inline.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

Quand la fonction est appelée sans le paramètre **Verbose**, la sortie détaillée ne s’affiche pas.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

Si elle est appelée avec le paramètre **Verbose**, la sortie détaillée s’affiche.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a>Entrée de pipeline

Si vous souhaitez que votre fonction accepte l’entrée de pipeline, vous devez ajouter du code supplémentaire. Comme mentionné plus haut dans ce livre, les commandes peuvent accepter l’entrée de pipeline **par valeur** (par type) ou **par nom de propriété**. Vous pouvez écrire vos fonctions comme des commandes natives pour qu’elles acceptent l’un de ces types d’entrée ou les deux.

Pour accepter l’entrée de pipeline **par valeur**, spécifiez l’attribut `ValueFromPipeline` pour ce paramètre particulier. Gardez à l’esprit que l’entrée de pipeline **par valeur** peut être acceptée uniquement par un seul paramètre de chaque type de données. Par exemple, si vous avez deux paramètres qui acceptent une entrée de type chaîne, un seul d’entre eux peut accepter l’entrée de pipeline **par valeur**. Si vous la spécifiez pour les deux paramètres chaîne, l’entrée de pipeline ne saura pas à quel paramètre elle doit être liée. C’est une autre raison pour laquelle je préfère appeler ce type d’entrée de pipeline _par type_ au lieu de **par valeur**.

L’entrée de pipeline fournit un seul élément à la fois, de la même façon que les éléments sont traités dans une boucle `foreach`.
Au minimum, un bloc `process` est requis pour traiter chacun de ces éléments si vous acceptez un tableau en entrée. Si vous acceptez une seule valeur en entrée, un bloc `process` n’est pas nécessaire, mais je vous conseille quand même de le spécifier par souci de cohérence.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

L’acceptation de l’entrée de pipeline **par nom de propriété** est similaire, à ceci près qu’elle est spécifiée avec l’attribut de paramètre `ValueFromPipelineByPropertyName` et qu’elle peut être spécifiée pour n’importe quel nombre de paramètres quel que soit le type de données. Ce qu’il faut retenir est que la sortie de la commande fournie en entrée doit avoir un nom de propriété qui correspond au nom du paramètre ou un alias de paramètre de votre fonction.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

Les blocs `BEGIN` et `END` sont facultatifs. `BEGIN` est spécifié avant le bloc `PROCESS` et est utilisé pour effectuer tout travail initial avant que les éléments ne soient reçus du pipeline. Il est important de comprendre ce point. Les valeurs reçues ne sont pas accessibles dans le bloc `BEGIN`. Le bloc `END` est spécifié après le bloc `PROCESS` et est utilisé pour le nettoyage une fois que tous les éléments reçus ont été traités.

## <a name="error-handling"></a>Gestion des erreurs

La fonction illustrée dans l’exemple suivant génère une exception non prise en charge quand un ordinateur ne peut pas être contacté.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

Il y a plusieurs manières de gérer les erreurs dans PowerShell. L’utilisation de `Try/Catch` est le moyen le plus moderne.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

Bien que la fonction illustrée dans l’exemple précédent utilise la gestion des erreurs, elle génère également une exception non prise en charge, car la commande ne génère pas d’erreur avec fin d’exécution. Il est important de comprendre aussi ce point. Seules les erreurs avec fin d’exécution sont interceptées. Spécifiez le paramètre **ErrorAction** avec la valeur **Stop** pour transformer une erreur sans fin d’exécution en erreur avec fin d’exécution.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

Ne modifiez pas la variable `$ErrorActionPreference` globale sauf si cela est absolument nécessaire. Si vous utilisez du code comme .NET directement dans votre fonction PowerShell, vous ne pouvez pas spécifier le paramètre **ErrorAction** dans la commande elle-même. Dans ce scénario, vous devrez peut-être modifier temporairement la variable `$ErrorActionPreference` globale ; si vous le faites, n’oubliez pas de rétablir la variable initiale tout de suite après avoir essayé la commande.

## <a name="comment-based-help"></a>Aide basée sur les commentaires

Une bonne pratique reconnue est d’ajouter une aide basée sur les commentaires à vos fonctions afin que les personnes avec lesquelles vous partagez les fonctions sachent comment les utiliser.

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

Quand vous ajoutez une aide basée sur les commentaires à vos fonctions, l’aide associée peut être obtenue de la même façon que les commandes intégrées par défaut.

Toute la syntaxe à respecter pour écrire une fonction dans PowerShell peut paraître très compliquée, surtout pour les développeurs débutants. Souvent, quand je ne me souviens pas de la syntaxe d’un élément, j’ouvre une deuxième copie de l’environnement ISE sur un autre moniteur pour voir l’extrait de code « Cmdlet (advanced function) - Complete » pendant que je tape le code de ma fonction. Vous pouvez accéder aux extraits de code dans PowerShell ISE en appuyant sur les touches <kbd>Ctrl</kbd>+<kbd>J</kbd>.

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez appris les bases de l’écriture de fonctions dans PowerShell. Vous avez appris comment transformer une fonction en fonction avancée, et vous avez vu certains des points les plus importants à connaître pour écrire des fonctions PowerShell, comme la validation de paramètres, la sortie détaillée, l’entrée de pipeline, la gestion des erreurs et l’aide basée sur les commentaires.

## <a name="review"></a>Révision

1. Comment pouvez-vous obtenir une liste des verbes approuvés dans PowerShell ?
1. Comment pouvez-vous transformer une fonction PowerShell en fonction avancée ?
1. Quand devez-vous ajouter les paramètres **WhatIf** et **Confirm** à vos fonctions PowerShell ?
1. Comment faites-vous pour transformer une erreur sans fin d’exécution en erreur avec fin d’exécution ?
1. Pourquoi devez-vous ajouter une aide basée sur les commentaires à vos fonctions ?

## <a name="recommended-reading"></a>Lecture recommandée

- [about_Functions][]
- [about_Functions_Advanced_Parameters][]
- [about_CommonParameters][]
- [about_Functions_CmdletBindingAttribute][]
- [about_Functions_Advanced][]
- [about_Try_Catch_Finally][]
- [about_Comment_Based_Help][]
- [Vidéo : PowerShell Toolmaking with Advanced Functions and Script Modules][]

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[Vidéo : PowerShell Toolmaking with Advanced Functions and Script Modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Casse Pascal]: /dotnet/standard/design-guidelines/capitalization-conventions
