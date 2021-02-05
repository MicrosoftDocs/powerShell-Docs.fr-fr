---
title: Modules de script
description: Les modules de script offrent un moyen simple d’empaqueter des scripts et des fonctions dans un outil réutilisable.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: c557c071bc202a4216a77e7e5ae0bd73b4bc014b
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99598957"
---
# <a name="chapter-10---script-modules"></a><span data-ttu-id="efc59-103">Chapitre 10 – Modules de script</span><span class="sxs-lookup"><span data-stu-id="efc59-103">Chapter 10 - Script modules</span></span>

<span data-ttu-id="efc59-104">Si vous prévoyez d’utiliser régulièrement vos fonctions d’une ligne et vos scripts dans PowerShell, il est plus important encore de les transformer en outils réutilisables.</span><span class="sxs-lookup"><span data-stu-id="efc59-104">Turning your one-liners and scripts in PowerShell into reusable tools becomes even more important if it's something that you're going to use frequently.</span></span> <span data-ttu-id="efc59-105">En empaquetant vos fonctions dans un module de script, vous leur apportez une touche plus professionnelle et vous facilitez leur partage.</span><span class="sxs-lookup"><span data-stu-id="efc59-105">Packaging your functions in a script module makes them look and feel more professional and makes them easier to share.</span></span>

## <a name="dot-sourcing-functions"></a><span data-ttu-id="efc59-106">Fonctions de type « dot sourcing »</span><span class="sxs-lookup"><span data-stu-id="efc59-106">Dot-Sourcing Functions</span></span>

<span data-ttu-id="efc59-107">Ce que nous n’avons pas évoqué dans le chapitre précédent, ce sont les fonctions de type « dot sourcing ».</span><span class="sxs-lookup"><span data-stu-id="efc59-107">Something that we didn't talk about in the previous chapter is dot-sourcing functions.</span></span> <span data-ttu-id="efc59-108">Quand une fonction contenue dans un script ne fait pas partie d’un module, la seule façon de la charger en mémoire est de faire un appel de source de type « dot sourcing » pour le fichier `.PS1` dans lequel elle est enregistrée.</span><span class="sxs-lookup"><span data-stu-id="efc59-108">When a function in a script isn't part of a module, the only way to load it into memory is to dot-source the `.PS1` file that it's saved in.</span></span>

<span data-ttu-id="efc59-109">La fonction suivante a été enregistrée sous le nom `Get-MrPSVersion.ps1`.</span><span class="sxs-lookup"><span data-stu-id="efc59-109">The following function has been saved as `Get-MrPSVersion.ps1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

<span data-ttu-id="efc59-110">Quand vous exécutez le script, il ne se passe rien.</span><span class="sxs-lookup"><span data-stu-id="efc59-110">When you run the script, nothing happens.</span></span>

```powershell
.\Get-MrPSVersion.ps1
```

<span data-ttu-id="efc59-111">Si vous essayez d’appeler la fonction, elle génère un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="efc59-111">If you try to call the function, it generates an error message.</span></span>

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

<span data-ttu-id="efc59-112">Pour savoir si des fonctions sont chargées en mémoire, vous pouvez vérifier si elles existent sur le PSDrive **Function**.</span><span class="sxs-lookup"><span data-stu-id="efc59-112">You can determine if functions are loaded into memory by checking to see if they exist on the **Function** PSDrive.</span></span>

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

<span data-ttu-id="efc59-113">Ce qui pose problème dans l’appel du script qui contient la fonction, c’est que cette dernière est chargée dans l’étendue du _script_.</span><span class="sxs-lookup"><span data-stu-id="efc59-113">The problem with calling the script that contains the function is that the functions are loaded in the _Script_ scope.</span></span> <span data-ttu-id="efc59-114">Quand le script se termine, cette étendue est supprimée et la fonction qu’elle contient l’est aussi.</span><span class="sxs-lookup"><span data-stu-id="efc59-114">When the script completes, that scope is removed and the function is removed with it.</span></span>

<span data-ttu-id="efc59-115">La fonction doit être chargée dans l’étendue _Global_.</span><span class="sxs-lookup"><span data-stu-id="efc59-115">The function needs to be loaded into the _Global_ scope.</span></span> <span data-ttu-id="efc59-116">Pour cela, il suffit de faire un appel de source de type « dot sourcing » sur le script qui contient la fonction.</span><span class="sxs-lookup"><span data-stu-id="efc59-116">That can be accomplished by dot-sourcing the script that contains the function.</span></span> <span data-ttu-id="efc59-117">Le chemin relatif peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="efc59-117">The relative path can be used.</span></span>

```powershell
. .\Get-MrPSVersion.ps1
```

<span data-ttu-id="efc59-118">Le chemin complet peut aussi être utilisé.</span><span class="sxs-lookup"><span data-stu-id="efc59-118">The fully qualified path can also be used.</span></span>

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

<span data-ttu-id="efc59-119">Si une partie du chemin est stockée dans une variable, elle peut être combinée avec le reste du chemin.</span><span class="sxs-lookup"><span data-stu-id="efc59-119">If a portion of the path is stored in a variable, it can be combined with the remainder of the path.</span></span>
<span data-ttu-id="efc59-120">Il n’y a aucune raison d’utiliser la concaténation de chaînes pour combiner la variable avec le reste du chemin.</span><span class="sxs-lookup"><span data-stu-id="efc59-120">There's no reason to use string concatenation to combine the variable together with the remainder of the path.</span></span>

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

<span data-ttu-id="efc59-121">À présent, un simple examen de PSDrive **Function** permet de constater que la fonction `Get-MrPSVersion` existe bien.</span><span class="sxs-lookup"><span data-stu-id="efc59-121">Now when I check the **Function** PSDrive, the `Get-MrPSVersion` function exists.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a><span data-ttu-id="efc59-122">Modules de script</span><span class="sxs-lookup"><span data-stu-id="efc59-122">Script Modules</span></span>

<span data-ttu-id="efc59-123">Dans PowerShell, un module de script est simplement un fichier qui contient une ou plusieurs fonctions enregistrées sous forme de fichier `.PSM1` et non de fichier `.PS1`.</span><span class="sxs-lookup"><span data-stu-id="efc59-123">A script module in PowerShell is simply a file containing one or more functions that's saved as a `.PSM1` file instead of a `.PS1` file.</span></span>

<span data-ttu-id="efc59-124">Comment crée-t-on un module de script ?</span><span class="sxs-lookup"><span data-stu-id="efc59-124">How do you create a script module?</span></span> <span data-ttu-id="efc59-125">Vous vous dites probablement avec une commande nommée `New-Module`.</span><span class="sxs-lookup"><span data-stu-id="efc59-125">You're probably guessing with a command named something like `New-Module`.</span></span> <span data-ttu-id="efc59-126">Ce n’est pas tout à fait cela.</span><span class="sxs-lookup"><span data-stu-id="efc59-126">Your assumption would be wrong.</span></span> <span data-ttu-id="efc59-127">Il existe bel et bien dans PowerShell une commande nommée `New-Module`, mais elle permet de créer non pas un module de script, mais un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="efc59-127">While there is a command in PowerShell named `New-Module`, that command creates a dynamic module, not a script module.</span></span> <span data-ttu-id="efc59-128">Pensez à toujours lire l’aide qui se rapporte à une commande, même si vous pensez avoir trouvé la commande dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="efc59-128">Always be sure to read the help for a command even when you think you've found the command you need.</span></span>

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

<span data-ttu-id="efc59-129">Dans le chapitre précédent, j’ai précisé que les fonctions devaient utiliser des verbes approuvés au risque de générer un message d’avertissement pendant l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="efc59-129">In the previous chapter, I mentioned that functions should use approved verbs otherwise they'll generate a warning message when the module is imported.</span></span> <span data-ttu-id="efc59-130">Le code suivant utilise l’applet de commande `New-Module` pour créer un module dynamique en mémoire.</span><span class="sxs-lookup"><span data-stu-id="efc59-130">The following code uses the `New-Module` cmdlet to create a dynamic module in memory.</span></span> <span data-ttu-id="efc59-131">Ce module montre l’avertissement de verbe non approuvé.</span><span class="sxs-lookup"><span data-stu-id="efc59-131">This module demonstrates the unapproved verb warning.</span></span>

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

<span data-ttu-id="efc59-132">Pour rappel, même si l’applet de commande `New-Module` a été utilisée dans l’exemple précédent, ce n’est pas la commande à utiliser pour créer des modules de script dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efc59-132">Just to reiterate, although the `New-Module` cmdlet was used in the previous example, that's not the command for creating script modules in PowerShell.</span></span>

<span data-ttu-id="efc59-133">Enregistrez les deux fonctions suivantes dans un fichier nommé `MyScriptModule.psm1`.</span><span class="sxs-lookup"><span data-stu-id="efc59-133">Save the following two functions in a file named `MyScriptModule.psm1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

<span data-ttu-id="efc59-134">Essayez d’appeler une des fonctions.</span><span class="sxs-lookup"><span data-stu-id="efc59-134">Try to call one of the functions.</span></span>

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

<span data-ttu-id="efc59-135">Un message d’erreur affirmant que la fonction est introuvable est généré.</span><span class="sxs-lookup"><span data-stu-id="efc59-135">An error message is generated saying the function can't be found.</span></span> <span data-ttu-id="efc59-136">Si vous examinez le PSDrive **Function** comme précédemment, vous constaterez qu’elle ne s’y trouve pas non plus.</span><span class="sxs-lookup"><span data-stu-id="efc59-136">You could also check the **Function** PSDrive just like before and you'll find that it doesn't exist there either.</span></span>

<span data-ttu-id="efc59-137">Vous pouvez importer manuellement le fichier avec l’applet de commande `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="efc59-137">You could manually import the file with the `Import-Module` cmdlet.</span></span>

```powershell
Import-Module C:\MyScriptModule.psm1
```

<span data-ttu-id="efc59-138">La fonctionnalité de chargement automatique de module a été introduite dans PowerShell version 3.</span><span class="sxs-lookup"><span data-stu-id="efc59-138">The module autoloading feature was introduced in PowerShell version 3.</span></span> <span data-ttu-id="efc59-139">Pour tirer parti du chargement automatique de module, il est nécessaire d’enregistrer un module de script dans un dossier qui possède le même nom de base que le fichier `.PSM1` et à un emplacement spécifié dans `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="efc59-139">To take advantage of module autoloading, a script module needs to be saved in a folder with the same base name as the `.PSM1` file and in a location specified in `$env:PSModulePath`.</span></span>

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="efc59-140">Les résultats sont difficiles à lire.</span><span class="sxs-lookup"><span data-stu-id="efc59-140">The results are difficult to read.</span></span> <span data-ttu-id="efc59-141">Comme les chemins sont séparés par un point-virgule, vous pouvez scinder (« split ») les résultats de façon à retourner chaque chemin sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="efc59-141">Since the paths are separated by a semicolon, you can split the results to return each path on a separate line.</span></span> <span data-ttu-id="efc59-142">Cela facilite la lecture.</span><span class="sxs-lookup"><span data-stu-id="efc59-142">This makes them easier to read.</span></span>

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="efc59-143">Les trois premiers chemins de la liste sont les chemins par défaut.</span><span class="sxs-lookup"><span data-stu-id="efc59-143">The first three paths in the list are the default.</span></span> <span data-ttu-id="efc59-144">Le dernier chemin a été ajouté pendant l’installation de SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="efc59-144">When SQL Server Management Studio was installed, it added the last path.</span></span> <span data-ttu-id="efc59-145">Pour que le chargement automatique de module fonctionne, le fichier `MyScriptModule.psm1` doit se trouver dans un dossier nommé `MyScriptModule` directement à l’intérieur de l’un de ces chemins.</span><span class="sxs-lookup"><span data-stu-id="efc59-145">For module autoloading to work, the `MyScriptModule.psm1` file needs to be located in a folder named `MyScriptModule` directly inside one of those paths.</span></span>

<span data-ttu-id="efc59-146">Pas si vite.</span><span class="sxs-lookup"><span data-stu-id="efc59-146">Not so fast.</span></span> <span data-ttu-id="efc59-147">Ici, mon chemin utilisateur actuel n’est pas le premier de la liste.</span><span class="sxs-lookup"><span data-stu-id="efc59-147">For me, my current user path isn't the first one in the list.</span></span> <span data-ttu-id="efc59-148">Je n’utilise presque jamais ce chemin puisque je me connecte à Windows sous un nom d’utilisateur différent de celui que j’utilise pour exécuter PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efc59-148">I almost never use that path since I log into Windows with a different user than the one I use to run PowerShell.</span></span> <span data-ttu-id="efc59-149">Cela signifie qu’il ne se trouve pas dans mon dossier Documents normal.</span><span class="sxs-lookup"><span data-stu-id="efc59-149">That means it's not located in my normal Documents folder.</span></span>

<span data-ttu-id="efc59-150">Le deuxième chemin est le chemin **AllUsers**.</span><span class="sxs-lookup"><span data-stu-id="efc59-150">The second path is the **AllUsers** path.</span></span> <span data-ttu-id="efc59-151">C’est à cet emplacement que je stocke tous mes modules.</span><span class="sxs-lookup"><span data-stu-id="efc59-151">This is the location where I store all of my modules.</span></span>

<span data-ttu-id="efc59-152">Le troisième chemin se trouve en dessous de `C:\Windows\System32`.</span><span class="sxs-lookup"><span data-stu-id="efc59-152">The third path is underneath `C:\Windows\System32`.</span></span> <span data-ttu-id="efc59-153">Seul Microsoft devrait stocker des modules à cet emplacement, car il se trouve dans le dossier du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="efc59-153">Only Microsoft should be storing modules in that location since it resides within the operating systems folder.</span></span>

<span data-ttu-id="efc59-154">Une fois le fichier `.PSM1` sur le bon le chemin, le module se charge automatiquement dès lors que l’une de ses commandes est appelée.</span><span class="sxs-lookup"><span data-stu-id="efc59-154">Once the `.PSM1` file is located in the correct path, the module will load automatically when one of its commands is called.</span></span>

## <a name="module-manifests"></a><span data-ttu-id="efc59-155">Manifestes de module</span><span class="sxs-lookup"><span data-stu-id="efc59-155">Module Manifests</span></span>

<span data-ttu-id="efc59-156">Tous les modules doivent avoir un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="efc59-156">All modules should have a module manifest.</span></span> <span data-ttu-id="efc59-157">Un manifeste de module contient des métadonnées sur votre module.</span><span class="sxs-lookup"><span data-stu-id="efc59-157">A module manifest contains metadata about your module.</span></span>
<span data-ttu-id="efc59-158">Un fichier de manifeste de module a pour extension `.PSD1`.</span><span class="sxs-lookup"><span data-stu-id="efc59-158">The file extension for a module manifest file is `.PSD1`.</span></span> <span data-ttu-id="efc59-159">Tous les fichiers dont l’extension est `.PSD1` ne sont pas nécessairement des manifestes de module.</span><span class="sxs-lookup"><span data-stu-id="efc59-159">Not all files with a `.PSD1` extension are module manifests.</span></span> <span data-ttu-id="efc59-160">Ils peuvent aussi notamment servir à stocker la partie environnement d’une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="efc59-160">They can also be used for things such as storing the environmental portion of a DSC configuration.</span></span> <span data-ttu-id="efc59-161">La création d’un manifeste de module s’effectue à l’aide de `New-ModuleManifest`.</span><span class="sxs-lookup"><span data-stu-id="efc59-161">`New-ModuleManifest` is used to create a module manifest.</span></span> <span data-ttu-id="efc59-162">**Path** est la seule valeur obligatoire.</span><span class="sxs-lookup"><span data-stu-id="efc59-162">**Path** is the only value that's required.</span></span> <span data-ttu-id="efc59-163">Ceci dit, le module ne fonctionnera pas si **RootModule** n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="efc59-163">However, the module won't work if **RootModule** isn't specified.</span></span> <span data-ttu-id="efc59-164">Vous avez tout intérêt à spécifier **Author** et **Description** dans le cas où vous décideriez de charger votre module dans un dépôt NuGet avec PowerShellGet, car ces valeurs sont obligatoire dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="efc59-164">It's a good idea to specify **Author** and **Description** in case you decide to upload your module to a NuGet repository with PowerShellGet since those values are required in that scenario.</span></span>

<span data-ttu-id="efc59-165">La version d’un module sans manifeste est 0.0.</span><span class="sxs-lookup"><span data-stu-id="efc59-165">The version of a module without a manifest is 0.0.</span></span> <span data-ttu-id="efc59-166">Il s’agit d’une indication très claire que le module n’a pas de manifeste.</span><span class="sxs-lookup"><span data-stu-id="efc59-166">This is a dead giveaway that the module doesn't have a manifest.</span></span>

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

<span data-ttu-id="efc59-167">Le manifeste de module peut être créé avec toutes les informations recommandées.</span><span class="sxs-lookup"><span data-stu-id="efc59-167">The module manifest can be created with all of the recommended information.</span></span>

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

<span data-ttu-id="efc59-168">Si l’une de ces informations manque pendant la création initiale du manifeste de module, il est possible de l’ajouter ou de la mettre à jour par la suite à l’aide de `Update-ModuleManifest`.</span><span class="sxs-lookup"><span data-stu-id="efc59-168">If any of this information is missed during the initial creation of the module manifest, it can be added or updated later using `Update-ModuleManifest`.</span></span> <span data-ttu-id="efc59-169">Évitez de recréer le manifeste avec `New-ModuleManifest` après l’avoir déjà créé, car le GUID changera.</span><span class="sxs-lookup"><span data-stu-id="efc59-169">Don't recreate the manifest using `New-ModuleManifest` once it's already created because the GUID will change.</span></span>

## <a name="defining-public-and-private-functions"></a><span data-ttu-id="efc59-170">Définition de fonctions publiques et privées</span><span class="sxs-lookup"><span data-stu-id="efc59-170">Defining Public and Private Functions</span></span>

<span data-ttu-id="efc59-171">Vous pouvez souhaiter donner un caractère privé à vos fonctions d’assistance et les rendre uniquement accessibles à d’autres fonctions au sein du module.</span><span class="sxs-lookup"><span data-stu-id="efc59-171">You may have helper functions that you may want to be private and only accessible by other functions within the module.</span></span> <span data-ttu-id="efc59-172">Elles ne sont pas censées être accessibles aux utilisateurs de votre module.</span><span class="sxs-lookup"><span data-stu-id="efc59-172">They are not intended to be accessible to users of your module.</span></span> <span data-ttu-id="efc59-173">Il est possible de le faire de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="efc59-173">There are a couple of different ways to accomplish this.</span></span>

<span data-ttu-id="efc59-174">Si vous ne suivez pas les bonnes pratiques et que vous ne disposez que d’un fichier `.PSM1`, la seule option qui s’offre à vous est d’utiliser l’applet de commande `Export-ModuleMember`.</span><span class="sxs-lookup"><span data-stu-id="efc59-174">If you're not following the best practices and only have a `.PSM1` file, then your only option is to use the `Export-ModuleMember` cmdlet.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

<span data-ttu-id="efc59-175">Dans l’exemple précédent, seule la fonction `Get-MrPSVersion` est accessible aux utilisateurs de votre module, mais la fonction `Get-MrComputerName` est accessible aux autres fonctions au sein du module proprement dit.</span><span class="sxs-lookup"><span data-stu-id="efc59-175">In the previous example, only the `Get-MrPSVersion` function is available to the users of your module, but the `Get-MrComputerName` function is available to other functions within the module itself.</span></span>

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

<span data-ttu-id="efc59-176">Si vous avez ajouté un manifeste de module à votre module (et avez tout intérêt à le faire), je vous recommande de spécifier chacune des fonctions que vous voulez exporter dans la section **FunctionsToExport** du manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="efc59-176">If you've added a module manifest to your module (and you should), then I recommend specifying the individual functions you want to export in the **FunctionsToExport** section of the module manifest.</span></span>

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

<span data-ttu-id="efc59-177">Il n’est pas nécessaire d’utiliser à la fois `Export-ModuleMember` dans le fichier `.PSM1` et la section **FunctionsToExport** du manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="efc59-177">It's not necessary to use both `Export-ModuleMember` in the `.PSM1` file and the **FunctionsToExport** section of the module manifest.</span></span> <span data-ttu-id="efc59-178">Il suffit d’utiliser l’une ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="efc59-178">One or the other is sufficient.</span></span>

## <a name="summary"></a><span data-ttu-id="efc59-179">Résumé</span><span class="sxs-lookup"><span data-stu-id="efc59-179">Summary</span></span>

<span data-ttu-id="efc59-180">Dans ce chapitre, vous avez appris à transformer vos fonctions en module de script dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efc59-180">In this chapter you've learned how to turn your functions into a script module in PowerShell.</span></span> <span data-ttu-id="efc59-181">Vous avez aussi découvert quelques-unes des bonnes pratiques à suivre pour créer des modules de script, notamment celle qui consiste à créer un manifeste de module pour votre module de script.</span><span class="sxs-lookup"><span data-stu-id="efc59-181">You've also leaned some of the best practices for creating script modules such as creating a module manifest for your script module.</span></span>

## <a name="review"></a><span data-ttu-id="efc59-182">Révision</span><span class="sxs-lookup"><span data-stu-id="efc59-182">Review</span></span>

1. <span data-ttu-id="efc59-183">Comment créez-vous un module de script dans PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="efc59-183">How do you create a script module in PowerShell?</span></span>
1. <span data-ttu-id="efc59-184">Pourquoi est-il important que vos fonctions utilisent un verbe approuvé ?</span><span class="sxs-lookup"><span data-stu-id="efc59-184">Why is it important for your functions to use an approved verb?</span></span>
1. <span data-ttu-id="efc59-185">Comment créez-vous un manifeste de module dans PowerShell ?</span><span class="sxs-lookup"><span data-stu-id="efc59-185">How do you create a module manifest in PowerShell?</span></span>
1. <span data-ttu-id="efc59-186">Quelles sont les deux options qui permettent d’exporter uniquement certaines fonctions à partir de votre module ?</span><span class="sxs-lookup"><span data-stu-id="efc59-186">What are the two options for exporting only certain functions from your module?</span></span>
1. <span data-ttu-id="efc59-187">Quelles sont les conditions à remplir pour que vos modules se chargent automatiquement quand une commande est appelée ?</span><span class="sxs-lookup"><span data-stu-id="efc59-187">What is required for your modules to load automatically when a command is called?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="efc59-188">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="efc59-188">Recommended Reading</span></span>

- <span data-ttu-id="efc59-189">[How to Create PowerShell Script Modules and Module Manifests][]</span><span class="sxs-lookup"><span data-stu-id="efc59-189">[How to Create PowerShell Script Modules and Module Manifests][]</span></span>
- <span data-ttu-id="efc59-190">[about_Modules][]</span><span class="sxs-lookup"><span data-stu-id="efc59-190">[about_Modules][]</span></span>
- <span data-ttu-id="efc59-191">[New-ModuleManifest][]</span><span class="sxs-lookup"><span data-stu-id="efc59-191">[New-ModuleManifest][]</span></span>
- <span data-ttu-id="efc59-192">[Export-ModuleMember][]</span><span class="sxs-lookup"><span data-stu-id="efc59-192">[Export-ModuleMember][]</span></span>

<!-- link references -->
[How to Create PowerShell Script Modules and Module Manifests]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
