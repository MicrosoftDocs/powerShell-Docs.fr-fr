---
title: Modules de script
description: Les modules de script offrent un moyen simple d’empaqueter des scripts et des fonctions dans un outil réutilisable.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438280"
---
# <a name="chapter-10---script-modules"></a>Chapitre 10 – Modules de script

Si vous prévoyez d’utiliser régulièrement vos fonctions d’une ligne et vos scripts dans PowerShell, il est plus important encore de les transformer en outils réutilisables. En empaquetant vos fonctions dans un module de script, vous leur apportez une touche plus professionnelle et vous facilitez leur partage.

## <a name="dot-sourcing-functions"></a>Fonctions de type « dot sourcing »

Ce que nous n’avons pas évoqué dans le chapitre précédent, ce sont les fonctions de type « dot sourcing ». Quand une fonction contenue dans un script ne fait pas partie d’un module, la seule façon de la charger en mémoire est de faire un appel de source de type « dot sourcing » pour le fichier `.PS1` dans lequel elle est enregistrée.

La fonction suivante a été enregistrée sous le nom `Get-MrPSVersion.ps1`.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

Quand vous exécutez le script, il ne se passe rien.

```powershell
.\Get-MrPSVersion.ps1
```

Si vous essayez d’appeler la fonction, elle génère un message d’erreur.

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

Pour savoir si des fonctions sont chargées en mémoire, vous pouvez vérifier si elles existent sur le PSDrive **Function**.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

Ce qui pose problème dans l’appel du script qui contient la fonction, c’est que cette dernière est chargée dans l’étendue du _script_. Quand le script se termine, cette étendue est supprimée et la fonction qu’elle contient l’est aussi.

La fonction doit être chargée dans l’étendue _Global_. Pour cela, il suffit de faire un appel de source de type « dot sourcing » sur le script qui contient la fonction. Le chemin relatif peut être utilisé.

```powershell
. .\Get-MrPSVersion.ps1
```

Le chemin complet peut aussi être utilisé.

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

Si une partie du chemin est stockée dans une variable, elle peut être combinée avec le reste du chemin.
Il n’y a aucune raison d’utiliser la concaténation de chaînes pour combiner la variable avec le reste du chemin.

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

À présent, un simple examen de PSDrive **Function** permet de constater que la fonction `Get-MrPSVersion` existe bien.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a>Modules de script

Dans PowerShell, un module de script est simplement un fichier qui contient une ou plusieurs fonctions enregistrées sous forme de fichier `.PSM1` et non de fichier `.PS1`.

Comment crée-t-on un module de script ? Vous vous dites probablement avec une commande nommée `New-Module`. Ce n’est pas tout à fait cela. Il existe bel et bien dans PowerShell une commande nommée `New-Module`, mais elle permet de créer non pas un module de script, mais un module dynamique. Pensez à toujours lire l’aide qui se rapporte à une commande, même si vous pensez avoir trouvé la commande dont vous avez besoin.

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

Dans le chapitre précédent, j’ai précisé que les fonctions devaient utiliser des verbes approuvés au risque de générer un message d’avertissement pendant l’importation du module. Le code suivant utilise l’applet de commande `New-Module` pour créer un module dynamique en mémoire. Ce module montre l’avertissement de verbe non approuvé.

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

Pour rappel, même si l’applet de commande `New-Module` a été utilisée dans l’exemple précédent, ce n’est pas la commande à utiliser pour créer des modules de script dans PowerShell.

Enregistrez les deux fonctions suivantes dans un fichier nommé `MyScriptModule.psm1`.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

Essayez d’appeler une des fonctions.

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Un message d’erreur affirmant que la fonction est introuvable est généré. Si vous examinez le PSDrive **Function** comme précédemment, vous constaterez qu’elle ne s’y trouve pas non plus.

Vous pouvez importer manuellement le fichier avec l’applet de commande `Import-Module`.

```powershell
Import-Module C:\MyScriptModule.psm1
```

La fonctionnalité de chargement automatique de module a été introduite dans PowerShell version 3. Pour tirer parti du chargement automatique de module, il est nécessaire d’enregistrer un module de script dans un dossier qui possède le même nom de base que le fichier `.PSM1` et à un emplacement spécifié dans `$env:PSModulePath`.

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

Les résultats sont difficiles à lire. Comme les chemins sont séparés par un point-virgule, vous pouvez scinder (« split ») les résultats de façon à retourner chaque chemin sur une ligne distincte. Cela facilite la lecture.

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

Les trois premiers chemins de la liste sont les chemins par défaut. Le dernier chemin a été ajouté pendant l’installation de SQL Server Management Studio. Pour que le chargement automatique de module fonctionne, le fichier `MyScriptModule.psm1` doit se trouver dans un dossier nommé `MyScriptModule` directement à l’intérieur de l’un de ces chemins.

Pas si vite. Ici, mon chemin utilisateur actuel n’est pas le premier de la liste. Je n’utilise presque jamais ce chemin puisque je me connecte à Windows sous un nom d’utilisateur différent de celui que j’utilise pour exécuter PowerShell. Cela signifie qu’il ne se trouve pas dans mon dossier Documents normal.

Le deuxième chemin est le chemin **AllUsers**. C’est à cet emplacement que je stocke tous mes modules.

Le troisième chemin se trouve en dessous de `C:\Windows\System32`. Seul Microsoft devrait stocker des modules à cet emplacement, car il se trouve dans le dossier du système d’exploitation.

Une fois le fichier `.PSM1` sur le bon le chemin, le module se charge automatiquement dès lors que l’une de ses commandes est appelée.

## <a name="module-manifests"></a>Manifestes de module

Tous les modules doivent avoir un manifeste de module. Un manifeste de module contient des métadonnées sur votre module.
Un fichier de manifeste de module a pour extension `.PSD1`. Tous les fichiers dont l’extension est `.PSD1` ne sont pas nécessairement des manifestes de module. Ils peuvent aussi notamment servir à stocker la partie environnement d’une configuration DSC. La création d’un manifeste de module s’effectue à l’aide de `New-ModuleManifest`. **Path** est la seule valeur obligatoire. Ceci dit, le module ne fonctionnera pas si **RootModule** n’est pas spécifié. Vous avez tout intérêt à spécifier **Author** et **Description** dans le cas où vous décideriez de charger votre module dans un dépôt NuGet avec PowerShellGet, car ces valeurs sont obligatoire dans ce scénario.

La version d’un module sans manifeste est 0.0. Il s’agit d’une indication très claire que le module n’a pas de manifeste.

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

Le manifeste de module peut être créé avec toutes les informations recommandées.

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

Si l’une de ces informations manque pendant la création initiale du manifeste de module, il est possible de l’ajouter ou de la mettre à jour par la suite à l’aide de `Update-ModuleManifest`. Évitez de recréer le manifeste avec `New-ModuleManifest` après l’avoir déjà créé, car le GUID changera.

## <a name="defining-public-and-private-functions"></a>Définition de fonctions publiques et privées

Vous pouvez souhaiter donner un caractère privé à vos fonctions d’assistance et les rendre uniquement accessibles à d’autres fonctions au sein du module. Elles ne sont pas censées être accessibles aux utilisateurs de votre module. Il est possible de le faire de différentes façons.

Si vous ne suivez pas les bonnes pratiques et que vous ne disposez que d’un fichier `.PSM1`, la seule option qui s’offre à vous est d’utiliser l’applet de commande `Export-ModuleMember`.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

Dans l’exemple précédent, seule la fonction `Get-MrPSVersion` est accessible aux utilisateurs de votre module, mais la fonction `Get-MrComputerName` est accessible aux autres fonctions au sein du module proprement dit.

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

Si vous avez ajouté un manifeste de module à votre module (et avez tout intérêt à le faire), je vous recommande de spécifier chacune des fonctions que vous voulez exporter dans la section **FunctionsToExport** du manifeste de module.

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

Il n’est pas nécessaire d’utiliser à la fois `Export-ModuleMember` dans le fichier `.PSM1` et la section **FunctionsToExport** du manifeste de module. Il suffit d’utiliser l’une ou l’autre.

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez appris à transformer vos fonctions en module de script dans PowerShell. Vous avez aussi découvert quelques-unes des bonnes pratiques à suivre pour créer des modules de script, notamment celle qui consiste à créer un manifeste de module pour votre module de script.

## <a name="review"></a>Révision

1. Comment créez-vous un module de script dans PowerShell ?
1. Pourquoi est-il important que vos fonctions utilisent un verbe approuvé ?
1. Comment créez-vous un manifeste de module dans PowerShell ?
1. Quelles sont les deux options qui permettent d’exporter uniquement certaines fonctions à partir de votre module ?
1. Quelles sont les conditions à remplir pour que vos modules se chargent automatiquement quand une commande est appelée ?

## <a name="recommended-reading"></a>Lecture recommandée

- [How to Create PowerShell Script Modules and Module Manifests][]
- [about_Modules][]
- [New-ModuleManifest][]
- [Export-ModuleMember][]

<!-- link references -->
[How to Create PowerShell Script Modules and Module Manifests]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
