---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 5f2752f53fb5f74b6436548c3bd4fa731d2b02d5
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879233"
---
# <span data-ttu-id="0d106-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="0d106-103">Get-Command</span></span>

## <span data-ttu-id="0d106-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0d106-104">SYNOPSIS</span></span>
<span data-ttu-id="0d106-105">Obtient toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="0d106-105">Gets all commands.</span></span>

## <span data-ttu-id="0d106-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="0d106-106">SYNTAX</span></span>

### <span data-ttu-id="0d106-107">CmdletSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="0d106-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="0d106-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="0d106-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## <span data-ttu-id="0d106-109">Description</span><span class="sxs-lookup"><span data-stu-id="0d106-109">DESCRIPTION</span></span>

<span data-ttu-id="0d106-110">L' `Get-Command` applet de commande obtient toutes les commandes qui sont installées sur l’ordinateur, y compris les applets de commande, les alias, les fonctions, les filtres, les scripts et les applications.</span><span class="sxs-lookup"><span data-stu-id="0d106-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="0d106-111">`Get-Command` Obtient les commandes des modules PowerShell et des commandes qui ont été importées à partir d’autres sessions.</span><span class="sxs-lookup"><span data-stu-id="0d106-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="0d106-112">Pour obtenir uniquement les commandes qui ont été importées dans la session active, utilisez le paramètre **ListImported**.</span><span class="sxs-lookup"><span data-stu-id="0d106-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="0d106-113">Sans paramètres, `Get-Command` obtient toutes les applets de commande, fonctions et alias installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0d106-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="0d106-114">`Get-Command *` Obtient tous les types de commandes, y compris tous les fichiers non-PowerShell dans la variable d’environnement PATH ( `$env:Path` ), qu’elle répertorie dans le type de commande de l’application.</span><span class="sxs-lookup"><span data-stu-id="0d106-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="0d106-115">`Get-Command` qui utilise le nom exact de la commande, sans caractères génériques, importe automatiquement le module qui contient la commande afin que vous puissiez utiliser la commande immédiatement.</span><span class="sxs-lookup"><span data-stu-id="0d106-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="0d106-116">Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la `$PSModuleAutoLoadingPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="0d106-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="0d106-117">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="0d106-118">`Get-Command` obtient ses données directement à partir du code de commande, contrairement `Get-Help` à, qui obtient ses informations à partir des rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="0d106-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="0d106-119">À compter de Windows PowerShell 5,0, les résultats de l’applet de commande `Get-Command` affichent une colonne de **version** par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d106-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="0d106-120">Une nouvelle propriété de **version** a été ajoutée à la classe **CommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="0d106-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="0d106-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0d106-121">EXAMPLES</span></span>

### <span data-ttu-id="0d106-122">Exemple 1 : recevoir des applets de commande, des fonctions et des alias</span><span class="sxs-lookup"><span data-stu-id="0d106-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="0d106-123">Cette commande obtient les applets de commande, fonctions et alias PowerShell installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0d106-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="0d106-124">Exemple 2 : récupérer des commandes dans la session active</span><span class="sxs-lookup"><span data-stu-id="0d106-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="0d106-125">Cette commande utilise le paramètre **ListImported** pour récupérer uniquement les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="0d106-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="0d106-126">Exemple 3 : obtenir des applets de commande et les afficher dans l’ordre</span><span class="sxs-lookup"><span data-stu-id="0d106-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="0d106-127">Cette commande obtient toutes les applets de commande, les trie par ordre alphabétique en fonction du nom de l'applet de commande, et les affiche ensuite dans des groupes basés sur le nom.</span><span class="sxs-lookup"><span data-stu-id="0d106-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="0d106-128">Cet affichage peut vous aider à trouver les applets de commande d'une tâche.</span><span class="sxs-lookup"><span data-stu-id="0d106-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="0d106-129">Exemple 4 : obtenir des commandes dans un module</span><span class="sxs-lookup"><span data-stu-id="0d106-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="0d106-130">Cette commande utilise le paramètre **module** pour récupérer les commandes dans les modules Microsoft. PowerShell. Security et Microsoft. PowerShell. Utility.</span><span class="sxs-lookup"><span data-stu-id="0d106-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="0d106-131">Exemple 5 : obtenir des informations sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="0d106-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="0d106-132">Cette commande obtient des informations sur l’applet de commande `Get-AppLockerPolicy` .</span><span class="sxs-lookup"><span data-stu-id="0d106-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="0d106-133">Elle importe également le module **AppLocker**, qui ajoute toutes les commandes du module **AppLocker** à la session active.</span><span class="sxs-lookup"><span data-stu-id="0d106-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="0d106-134">Quand un module est importé automatiquement, l’effet est identique à l’utilisation de l’applet de commande Import-Module.</span><span class="sxs-lookup"><span data-stu-id="0d106-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="0d106-135">Le module peut ajouter des commandes, des types et des fichiers de mise en forme, puis exécuter des scripts dans la session.</span><span class="sxs-lookup"><span data-stu-id="0d106-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="0d106-136">Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la `$PSModuleAutoLoadingPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="0d106-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="0d106-137">Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="0d106-138">Exemple 6 : obtenir la syntaxe d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="0d106-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="0d106-139">Cette commande utilise les paramètres **argumentlist** et **Syntax** pour récupérer la syntaxe de l’applet de commande `Get-ChildItem` quand elle est utilisée dans le lecteur Cert :.</span><span class="sxs-lookup"><span data-stu-id="0d106-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="0d106-140">Le lecteur Cert : est un lecteur PowerShell que le fournisseur de certificats ajoute à la session.</span><span class="sxs-lookup"><span data-stu-id="0d106-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="0d106-141">Lorsque vous comparez la syntaxe affichée dans la sortie avec la syntaxe qui s’affiche lorsque vous omettez le paramètre **args** (**argumentlist**), vous constatez que le **fournisseur de certificats** ajoute un paramètre dynamique, **CodeSigningCert**, à l’applet de commande `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="0d106-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** (**ArgumentList**) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert**, to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="0d106-142">Pour plus d’informations sur le fournisseur de certificats, consultez [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="0d106-143">Exemple 7 : récupération des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="0d106-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="0d106-144">La commande de l’exemple utilise la `Get-DynamicParameters` fonction pour récupérer les paramètres dynamiques que le fournisseur de certificats ajoute à l’applet de commande `Get-ChildItem` lorsqu’il est utilisé dans le lecteur Cert :.</span><span class="sxs-lookup"><span data-stu-id="0d106-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command -Name $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="0d106-145">`Get-DynamicParameters`Dans cet exemple, la fonction obtient les paramètres dynamiques d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="0d106-146">Il s'agit d'une alternative à la méthode utilisée dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="0d106-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="0d106-147">Un paramètre dynamique peut être ajouté à une applet de commande par une autre applet de commande ou un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0d106-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="0d106-148">Exemple 8 : récupération de toutes les commandes de tous les types</span><span class="sxs-lookup"><span data-stu-id="0d106-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="0d106-149">Cette commande obtient toutes les commandes de tous les types sur l’ordinateur local, y compris les fichiers exécutables dans les chemins d’accès de la variable d’environnement **path** ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="0d106-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="0d106-150">Elle retourne un objet **ApplicationInfo** (System.Management.Automation.ApplicationInfo) pour chaque fichier, au lieu d'un objet **FileInfo** (System.IO.FileInfo).</span><span class="sxs-lookup"><span data-stu-id="0d106-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="0d106-151">Exemple 9 : obtenir des applets de commande à l’aide d’un nom et d’un type de paramètre</span><span class="sxs-lookup"><span data-stu-id="0d106-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="0d106-152">Cette commande obtient les applets de commande qui ont un paramètre dont le nom comprend auth et dont le type est **AuthenticationMechanism**.</span><span class="sxs-lookup"><span data-stu-id="0d106-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism**.</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="0d106-153">Vous pouvez vous servir d'une commande similaire à celle-ci pour rechercher les applets de commande qui vous permettent de spécifier la méthode utilisée pour authentifier l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d106-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="0d106-154">Le paramètre **ParameterType** distingue les paramètres qui acceptent une valeur **AuthenticationMechanism** par rapport à ceux qui acceptent un paramètre **AuthenticationLevel**, même quand ils ont des noms similaires.</span><span class="sxs-lookup"><span data-stu-id="0d106-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="0d106-155">Exemple 10 : recevoir un alias</span><span class="sxs-lookup"><span data-stu-id="0d106-155">Example 10: Get an alias</span></span>

<span data-ttu-id="0d106-156">Cet exemple montre comment utiliser l' `Get-Command` applet de commande avec un alias.</span><span class="sxs-lookup"><span data-stu-id="0d106-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command -Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="0d106-157">Bien qu’il soit généralement utilisé sur les applets de commande et les fonctions, il `Get-Command` obtient également les scripts, les fonctions, les alias et les fichiers exécutables.</span><span class="sxs-lookup"><span data-stu-id="0d106-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="0d106-158">La sortie de la commande montre l'affichage spécial de la valeur de propriété **Name** pour les alias.</span><span class="sxs-lookup"><span data-stu-id="0d106-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="0d106-159">L'affichage montre l'alias et le nom de commande complet.</span><span class="sxs-lookup"><span data-stu-id="0d106-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="0d106-160">Exemple 11 : récupération d’une syntaxe à partir d’un alias</span><span class="sxs-lookup"><span data-stu-id="0d106-160">Example 11: Get Syntax from an alias</span></span>

<span data-ttu-id="0d106-161">Cet exemple montre comment récupérer la syntaxe avec le nom standard d’un alias.</span><span class="sxs-lookup"><span data-stu-id="0d106-161">This example shows how to get the syntax along with the standard name of an alias.</span></span>

<span data-ttu-id="0d106-162">La sortie de la commande affiche l’alias étiqueté avec le nom standard, suivi de la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0d106-162">The output of the command shows the labeled alias with the standard name, followed by the syntax.</span></span>

```powershell
Get-Command -Name dir -Syntax
```

```Output
dir (alias) -> Get-ChildItem

dir [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]

dir [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="0d106-163">Exemple 12 : récupération de toutes les instances de la commande Notepad</span><span class="sxs-lookup"><span data-stu-id="0d106-163">Example 12: Get all instances of the Notepad command</span></span>

<span data-ttu-id="0d106-164">Cet exemple utilise le paramètre **All** de l' `Get-Command` applet de commande pour afficher toutes les instances de la `Notepad` commande sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0d106-164">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the `Notepad` command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="0d106-165">Le paramètre **All** est utile quand il existe plusieurs commandes portant le même nom dans la session.</span><span class="sxs-lookup"><span data-stu-id="0d106-165">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="0d106-166">À compter de Windows PowerShell 3,0, par défaut, lorsque la session comprend plusieurs commandes portant le même nom, `Get-Command` obtient uniquement la commande qui s’exécute lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-166">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="0d106-167">Avec le paramètre **All** , `Get-Command` obtient toutes les commandes portant le nom spécifié et les retourne dans l’ordre de priorité d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0d106-167">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="0d106-168">Pour exécuter une autre commande que la première de la liste, tapez le chemin d'accès complet de la commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-168">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="0d106-169">Pour plus d’informations sur la priorité des commandes, consultez [about_Command_Precedence](About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-169">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="0d106-170">Exemple 13 : obtenir le nom d’un module qui contient une applet de commande</span><span class="sxs-lookup"><span data-stu-id="0d106-170">Example 13: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="0d106-171">Cette commande obtient le nom du module dans lequel l’applet de commande `Get-Date` provient.</span><span class="sxs-lookup"><span data-stu-id="0d106-171">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="0d106-172">La commande utilise la propriété **ModuleName** de toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="0d106-172">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="0d106-173">Ce format de commande fonctionne sur les commandes dans les modules PowerShell, même s’ils ne sont pas importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="0d106-173">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="0d106-174">Exemple 14 : obtenir des applets de commande et des fonctions qui ont un type de sortie</span><span class="sxs-lookup"><span data-stu-id="0d106-174">Example 14: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="0d106-175">Cette commande obtient les applets de commande et les fonctions qui ont un type de sortie, ainsi que le type d'objet qu'elles retournent.</span><span class="sxs-lookup"><span data-stu-id="0d106-175">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="0d106-176">La première partie de la commande obtient toutes les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-176">The first part of the command gets all cmdlets.</span></span> <span data-ttu-id="0d106-177">Un opérateur de pipeline ( `|` ) envoie les applets de commande à l’applet de commande `Where-Object` , qui sélectionne uniquement celles dans lesquelles la propriété **OutputType** est remplie.</span><span class="sxs-lookup"><span data-stu-id="0d106-177">A pipeline operator (`|`) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span> <span data-ttu-id="0d106-178">Un autre opérateur de pipeline envoie les objets d’applet de commande sélectionnés à l’applet de commande `Format-List` , qui affiche le nom et le type de sortie de chaque applet de commande dans une liste.</span><span class="sxs-lookup"><span data-stu-id="0d106-178">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="0d106-179">La propriété **OutputType** d'un objet **CommandInfo** a une valeur non null uniquement quand le code de l'applet de commande définit l'attribut **OutputType** de cette dernière.</span><span class="sxs-lookup"><span data-stu-id="0d106-179">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="0d106-180">Exemple 15 : obtenir des applets de commande qui prennent un type d’objet spécifique comme entrée</span><span class="sxs-lookup"><span data-stu-id="0d106-180">Example 15: Get cmdlets that take a specific object type as input</span></span>

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

<span data-ttu-id="0d106-181">Cette commande recherche les applets de commande qui acceptent des objets de carte réseau en entrée.</span><span class="sxs-lookup"><span data-stu-id="0d106-181">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="0d106-182">Vous pouvez utiliser ce format de commande pour rechercher les applets de commande qui acceptent le type d'objet retourné par une commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-182">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="0d106-183">La commande utilise la propriété intrinsèque **PSTypeNames** de tous les objets, qui obtient les types décrivant l'objet.</span><span class="sxs-lookup"><span data-stu-id="0d106-183">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="0d106-184">Pour obtenir la propriété **PSTypeNames** d'une carte réseau, et non la propriété **PSTypeNames** d'une collection de cartes réseau, la commande utilise une notation de tableau. Ainsi, elle obtient la première carte réseau retournée par l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-184">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

### <span data-ttu-id="0d106-185">Exemple 16 : obtenir des commandes à l’aide d’une correspondance approximative</span><span class="sxs-lookup"><span data-stu-id="0d106-185">Example 16: Get commands using a fuzzy match</span></span>

<span data-ttu-id="0d106-186">Dans cet exemple, le nom de la commande a délibérément une faute de frappe comme « commnd ».</span><span class="sxs-lookup"><span data-stu-id="0d106-186">In this example, the name of the command deliberately has a typo as 'get-commnd'.</span></span>
<span data-ttu-id="0d106-187">À l’aide du `-UseFuzzyMatching` commutateur, l’applet de commande déterminait que la meilleure correspondance était `Get-Command` suivie par d’autres commandes natives sur le système qui étaient une correspondance similaire.</span><span class="sxs-lookup"><span data-stu-id="0d106-187">Using the `-UseFuzzyMatching` switch, the cmdlet determined that the best match was `Get-Command` followed by other native commands on the system that were a similar match.</span></span>

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## <span data-ttu-id="0d106-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0d106-188">PARAMETERS</span></span>

### <span data-ttu-id="0d106-189">-All</span><span class="sxs-lookup"><span data-stu-id="0d106-189">-All</span></span>

<span data-ttu-id="0d106-190">Indique que cette applet de commande obtient toutes les commandes, y compris les commandes du même type qui ont le même nom.</span><span class="sxs-lookup"><span data-stu-id="0d106-190">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="0d106-191">Par défaut, `Get-Command` obtient uniquement les commandes qui s’exécutent lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-191">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="0d106-192">Pour plus d’informations sur la méthode utilisée par PowerShell pour sélectionner la commande à exécuter quand plusieurs commandes portent le même nom, consultez [about_Command_Precedence](About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-192">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="0d106-193">Pour plus d’informations sur les noms de commande qualifiés du module et l’exécution de commandes qui ne s’exécutent pas par défaut en raison d’un conflit de noms, consultez [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-193">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="0d106-194">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d106-194">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="0d106-195">Dans Windows PowerShell 2,0, `Get-Command` obtient toutes les commandes par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d106-195">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-196">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="0d106-196">-ArgumentList</span></span>

<span data-ttu-id="0d106-197">Spécifie un tableau d’arguments.</span><span class="sxs-lookup"><span data-stu-id="0d106-197">Specifies an array of arguments.</span></span> <span data-ttu-id="0d106-198">Cette applet de commande obtient des informations sur une applet de commande ou une fonction quand elle est utilisée avec les paramètres spécifiés (« arguments »).</span><span class="sxs-lookup"><span data-stu-id="0d106-198">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="0d106-199">L'alias d'**ArgumentList** est **Args**.</span><span class="sxs-lookup"><span data-stu-id="0d106-199">The alias for **ArgumentList** is **Args**.</span></span>

<span data-ttu-id="0d106-200">Pour détecter les paramètres dynamiques disponibles uniquement quand certains autres paramètres sont utilisés, affectez la valeur de **argumentlist** aux paramètres qui déclenchent les paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="0d106-200">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="0d106-201">Pour détecter les paramètres dynamiques qu’un fournisseur ajoute à une applet de commande, définissez la valeur du paramètre **argumentlist** sur un chemin d’accès dans le lecteur du fournisseur, par exemple WSMan :, HKLM : ou CERT :.</span><span class="sxs-lookup"><span data-stu-id="0d106-201">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="0d106-202">Lorsque la commande est une applet de commande du fournisseur PowerShell, entrez un seul chemin d’accès dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-202">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="0d106-203">Les applets de commande du fournisseur retournent uniquement les paramètres dynamiques du premier chemin d’accès de la valeur **argumentlist**.</span><span class="sxs-lookup"><span data-stu-id="0d106-203">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList**.</span></span> <span data-ttu-id="0d106-204">Pour plus d’informations sur les applets de commande du fournisseur, consultez [about_Providers](About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-204">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-205">-CommandType</span><span class="sxs-lookup"><span data-stu-id="0d106-205">-CommandType</span></span>

<span data-ttu-id="0d106-206">Spécifie les types de commandes que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="0d106-206">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="0d106-207">Entrez un ou plusieurs types de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-207">Enter one or more command types.</span></span> <span data-ttu-id="0d106-208">Utilisez **CommandType** ou son alias, **Type**.</span><span class="sxs-lookup"><span data-stu-id="0d106-208">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="0d106-209">Par défaut, `Get-Command` obtient toutes les applets de commande, fonctions et alias.</span><span class="sxs-lookup"><span data-stu-id="0d106-209">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="0d106-210">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="0d106-210">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0d106-211">Affecté.</span><span class="sxs-lookup"><span data-stu-id="0d106-211">Alias.</span></span> <span data-ttu-id="0d106-212">Obtient les alias de toutes les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d106-212">Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="0d106-213">Pour plus d’informations, consultez [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-213">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="0d106-214">Tout le monde.</span><span class="sxs-lookup"><span data-stu-id="0d106-214">All.</span></span> <span data-ttu-id="0d106-215">obtient tous les types de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-215">Gets all command types.</span></span> <span data-ttu-id="0d106-216">Cette valeur de paramètre est l’équivalent de `Get-Command *` .</span><span class="sxs-lookup"><span data-stu-id="0d106-216">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="0d106-217">console.</span><span class="sxs-lookup"><span data-stu-id="0d106-217">Application.</span></span> <span data-ttu-id="0d106-218">Obtient les fichiers non-PowerShell dans les chemins d’accès figurant dans la variable **d’environnement PATH** ($env :p Hemin), y compris les fichiers. txt,. exe et. dll.</span><span class="sxs-lookup"><span data-stu-id="0d106-218">Gets non-PowerShell files in paths listed in the **Path** environment variable ($env:path), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="0d106-219">Pour plus d’informations sur la variable **d’environnement PATH** , consultez about_Environment_Variables.</span><span class="sxs-lookup"><span data-stu-id="0d106-219">For more information about the **Path** environment variable, see about_Environment_Variables.</span></span>
- <span data-ttu-id="0d106-220">PolicySchedule.</span><span class="sxs-lookup"><span data-stu-id="0d106-220">Cmdlet.</span></span> <span data-ttu-id="0d106-221">obtient toutes les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-221">Gets all cmdlets.</span></span>
- <span data-ttu-id="0d106-222">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="0d106-222">ExternalScript.</span></span> <span data-ttu-id="0d106-223">obtient tous les fichiers .ps1 des chemins d'accès répertoriés dans la variable d'environnement **Path** ($env:path).</span><span class="sxs-lookup"><span data-stu-id="0d106-223">Gets all .ps1 files in the paths listed in the **Path** environment variable ($env:path).</span></span>
- <span data-ttu-id="0d106-224">Filtre et fonction.</span><span class="sxs-lookup"><span data-stu-id="0d106-224">Filter and Function.</span></span> <span data-ttu-id="0d106-225">Obtient tous les filtres et fonctions avancés et simples PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d106-225">Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="0d106-226">Script.</span><span class="sxs-lookup"><span data-stu-id="0d106-226">Script.</span></span> <span data-ttu-id="0d106-227">obtient tous les blocs de script.</span><span class="sxs-lookup"><span data-stu-id="0d106-227">Gets all script blocks.</span></span> <span data-ttu-id="0d106-228">Pour accéder aux scripts PowerShell (fichiers. ps1), utilisez la valeur ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="0d106-228">To get PowerShell scripts (.ps1 files), use the ExternalScript value.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-229">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="0d106-229">-FullyQualifiedModule</span></span>

<span data-ttu-id="0d106-230">Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** , décrits dans la section **Notes** du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="0d106-230">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="0d106-231">Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié dans l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="0d106-231">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="0d106-232">**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="0d106-232">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="0d106-233">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** .</span><span class="sxs-lookup"><span data-stu-id="0d106-233">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="0d106-234">Les deux paramètres s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="0d106-234">The two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-235">-ListImported</span><span class="sxs-lookup"><span data-stu-id="0d106-235">-ListImported</span></span>

<span data-ttu-id="0d106-236">Indique que cette applet de commande obtient uniquement les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="0d106-236">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="0d106-237">À compter de PowerShell 3,0, par défaut, `Get-Command` obtient toutes les commandes installées, y compris, mais sans s’y limiter, les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="0d106-237">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="0d106-238">Dans PowerShell 2,0, elle obtient uniquement les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="0d106-238">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="0d106-239">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d106-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-240">-Module</span><span class="sxs-lookup"><span data-stu-id="0d106-240">-Module</span></span>

<span data-ttu-id="0d106-241">Spécifie un tableau de modules.</span><span class="sxs-lookup"><span data-stu-id="0d106-241">Specifies an array of modules.</span></span> <span data-ttu-id="0d106-242">Cette applet de commande obtient les commandes provenant des modules spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0d106-242">This cmdlet gets the commands that came from the specified modules.</span></span>
<span data-ttu-id="0d106-243">Entrez les noms des modules ou des objets de module.</span><span class="sxs-lookup"><span data-stu-id="0d106-243">Enter the names of modules or module objects.</span></span>

<span data-ttu-id="0d106-244">Ce paramètre accepte les valeurs de chaîne, mais la valeur de ce paramètre peut également être un objet **PSModuleInfo** , tel que les objets `Get-Module` `Import-PSSession` retournés par les applets de commande et.</span><span class="sxs-lookup"><span data-stu-id="0d106-244">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** object, such as the objects that the `Get-Module` and `Import-PSSession` cmdlets return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="0d106-245">-Name</span><span class="sxs-lookup"><span data-stu-id="0d106-245">-Name</span></span>

<span data-ttu-id="0d106-246">Spécifie un tableau de noms.</span><span class="sxs-lookup"><span data-stu-id="0d106-246">Specifies an array of names.</span></span> <span data-ttu-id="0d106-247">Cette applet de commande obtient uniquement les commandes qui portent le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d106-247">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="0d106-248">Entrez un nom ou un modèle de nom.</span><span class="sxs-lookup"><span data-stu-id="0d106-248">Enter a name or name pattern.</span></span> <span data-ttu-id="0d106-249">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0d106-249">Wildcard characters are permitted.</span></span>

<span data-ttu-id="0d106-250">Pour obtenir les commandes qui ont le même nom, utilisez le paramètre **All**.</span><span class="sxs-lookup"><span data-stu-id="0d106-250">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="0d106-251">Lorsque deux commandes portent le même nom, par défaut, `Get-Command` obtient la commande qui s’exécute lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-251">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0d106-252">-Substantif</span><span class="sxs-lookup"><span data-stu-id="0d106-252">-Noun</span></span>

<span data-ttu-id="0d106-253">Spécifie un tableau de noms de commandes.</span><span class="sxs-lookup"><span data-stu-id="0d106-253">Specifies an array of command nouns.</span></span> <span data-ttu-id="0d106-254">Cette applet de commande obtient les commandes, qui incluent des applets de commande, des fonctions et des alias, dont les noms incluent le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d106-254">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="0d106-255">Entrez un ou plusieurs noms ou modèles de noms.</span><span class="sxs-lookup"><span data-stu-id="0d106-255">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="0d106-256">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0d106-256">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="0d106-257">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="0d106-257">-ParameterName</span></span>

<span data-ttu-id="0d106-258">Spécifie un tableau de noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0d106-258">Specifies an array of parameter names.</span></span> <span data-ttu-id="0d106-259">Cette applet de commande obtient les commandes de la session qui ont les paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0d106-259">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="0d106-260">Entrez les noms des paramètres ou les alias des paramètres.</span><span class="sxs-lookup"><span data-stu-id="0d106-260">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="0d106-261">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0d106-261">Wildcard characters are supported.</span></span>

<span data-ttu-id="0d106-262">Les paramètres **ParameterName** et **ParameterType** recherchent uniquement les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="0d106-262">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="0d106-263">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d106-263">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0d106-264">-ParameterType</span><span class="sxs-lookup"><span data-stu-id="0d106-264">-ParameterType</span></span>

<span data-ttu-id="0d106-265">Spécifie un tableau de noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0d106-265">Specifies an array of parameter names.</span></span> <span data-ttu-id="0d106-266">Cette applet de commande obtient les commandes de la session qui ont des paramètres du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d106-266">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="0d106-267">Entrez le nom complet ou partiel d'un type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="0d106-267">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="0d106-268">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0d106-268">Wildcard characters are supported.</span></span>

<span data-ttu-id="0d106-269">Les paramètres **ParameterName** et **ParameterType** recherchent uniquement les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="0d106-269">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="0d106-270">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="0d106-270">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0d106-271">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="0d106-271">-ShowCommandInfo</span></span>

<span data-ttu-id="0d106-272">Indique que cette applet de commande affiche les informations de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-272">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="0d106-273">Ce paramètre a été introduit dans Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="0d106-273">This parameter was introduced in Windows PowerShell 5.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-274">-Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d106-274">-Syntax</span></span>

<span data-ttu-id="0d106-275">Indique que cette applet de commande obtient uniquement les données spécifiées suivantes sur la commande :</span><span class="sxs-lookup"><span data-stu-id="0d106-275">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="0d106-276">Alias.</span><span class="sxs-lookup"><span data-stu-id="0d106-276">Aliases.</span></span> <span data-ttu-id="0d106-277">Obtient le nom standard et la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0d106-277">Gets the standard name and syntax.</span></span>
- <span data-ttu-id="0d106-278">Applets.</span><span class="sxs-lookup"><span data-stu-id="0d106-278">Cmdlets.</span></span> <span data-ttu-id="0d106-279">Obtient la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0d106-279">Gets the syntax.</span></span>
- <span data-ttu-id="0d106-280">Fonctions et filtres.</span><span class="sxs-lookup"><span data-stu-id="0d106-280">Functions and filters.</span></span> <span data-ttu-id="0d106-281">Obtient la définition de la fonction.</span><span class="sxs-lookup"><span data-stu-id="0d106-281">Gets the function definition.</span></span>
- <span data-ttu-id="0d106-282">Scripts et applications ou fichiers.</span><span class="sxs-lookup"><span data-stu-id="0d106-282">Scripts and applications or files.</span></span> <span data-ttu-id="0d106-283">Obtient le chemin d’accès et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="0d106-283">Gets the path and filename.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-284">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="0d106-284">-TotalCount</span></span>

<span data-ttu-id="0d106-285">Spécifie le nombre de commandes à récupérer.</span><span class="sxs-lookup"><span data-stu-id="0d106-285">Specifies the number of commands to get.</span></span> <span data-ttu-id="0d106-286">Vous pouvez utiliser ce paramètre pour limiter la sortie d'une commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-286">You can use this parameter to limit the output of a command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-287">-UseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="0d106-287">-UseAbbreviationExpansion</span></span>

<span data-ttu-id="0d106-288">Indique l’utilisation de la correspondance des caractères dans la commande pour rechercher des caractères majuscules dans une commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-288">Indicates using matching of the characters in the command to find with uppercase characters in a command.</span></span> <span data-ttu-id="0d106-289">Par exemple, `i-psdf` correspond à `Import-PowerShellDataFile` chaque caractère à trouver correspond à un caractère majuscule dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="0d106-289">For example, `i-psdf` would match `Import-PowerShellDataFile` as each of the characters to find matches an uppercase character in the result.</span></span> <span data-ttu-id="0d106-290">En cas d’utilisation de ce type de correspondance, les caractères génériques n’aboutissent à aucune correspondance.</span><span class="sxs-lookup"><span data-stu-id="0d106-290">When using this type of match, any wildcards will result in no matches.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-291">-UseFuzzyMatching</span><span class="sxs-lookup"><span data-stu-id="0d106-291">-UseFuzzyMatching</span></span>

<span data-ttu-id="0d106-292">Indique l’utilisation d’un algorithme de correspondance approximative lors de la recherche de commandes.</span><span class="sxs-lookup"><span data-stu-id="0d106-292">Indicates using a fuzzy matching algorithm when finding commands.</span></span> <span data-ttu-id="0d106-293">L’ordre de la sortie provient de la correspondance la plus proche à la plus petite correspondance probable.</span><span class="sxs-lookup"><span data-stu-id="0d106-293">The order of the output is from closest match to least likely match.</span></span> <span data-ttu-id="0d106-294">Les caractères génériques ne doivent pas être utilisés avec la correspondance approximative, car ils tentent de faire correspondre les commandes qui peuvent contenir ces caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="0d106-294">Wildcards should not be used with fuzzy matching as it will attempt to match commands that may contain those wildcard characters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0d106-295">-Verbe</span><span class="sxs-lookup"><span data-stu-id="0d106-295">-Verb</span></span>

<span data-ttu-id="0d106-296">Spécifie un tableau de verbes de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-296">Specifies an array of command verbs.</span></span> <span data-ttu-id="0d106-297">Cette applet de commande obtient les commandes, qui incluent des applets de commande, des fonctions et des alias, dont les noms incluent le verbe spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d106-297">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="0d106-298">Entrez un ou plusieurs verbes ou modèles de verbes.</span><span class="sxs-lookup"><span data-stu-id="0d106-298">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="0d106-299">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0d106-299">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="0d106-300">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0d106-300">CommonParameters</span></span>

<span data-ttu-id="0d106-301">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0d106-301">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0d106-302">Pour plus d’informations, consultez [about_CommonParameters](About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-302">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0d106-303">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0d106-303">INPUTS</span></span>

### <span data-ttu-id="0d106-304">System.String</span><span class="sxs-lookup"><span data-stu-id="0d106-304">System.String</span></span>

<span data-ttu-id="0d106-305">Vous pouvez diriger les noms de commandes vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-305">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="0d106-306">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0d106-306">OUTPUTS</span></span>

### <span data-ttu-id="0d106-307">System. Management. Automation. CommandInfo</span><span class="sxs-lookup"><span data-stu-id="0d106-307">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="0d106-308">Cette applet de commande retourne des objets dérivés de la classe **CommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="0d106-308">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="0d106-309">Le type d’objet retourné dépend du type de commande que `Get-Command` obtient.</span><span class="sxs-lookup"><span data-stu-id="0d106-309">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="0d106-310">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="0d106-310">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="0d106-311">Représente des alias.</span><span class="sxs-lookup"><span data-stu-id="0d106-311">Represents aliases.</span></span>

### <span data-ttu-id="0d106-312">System. Management. Automation. ApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="0d106-312">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="0d106-313">Représente des applications et des fichiers.</span><span class="sxs-lookup"><span data-stu-id="0d106-313">Represents applications and files.</span></span>

### <span data-ttu-id="0d106-314">System. Management. Automation. CmdletInfo</span><span class="sxs-lookup"><span data-stu-id="0d106-314">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="0d106-315">Représente des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-315">Represents cmdlets.</span></span>

### <span data-ttu-id="0d106-316">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="0d106-316">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="0d106-317">Représente des fonctions et des filtres.</span><span class="sxs-lookup"><span data-stu-id="0d106-317">Represents functions and filters.</span></span>

## <span data-ttu-id="0d106-318">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0d106-318">NOTES</span></span>

* <span data-ttu-id="0d106-319">Quand plusieurs commandes portant le même nom sont disponibles pour la session, `Get-Command` retourne la commande qui s’exécute lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="0d106-319">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="0d106-320">Pour obtenir les commandes portant le même nom, listées dans ordre d’exécution, utilisez le paramètre **All** .</span><span class="sxs-lookup"><span data-stu-id="0d106-320">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="0d106-321">Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-321">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
* <span data-ttu-id="0d106-322">Quand un module est importé automatiquement, l’effet est identique à l’utilisation de l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="0d106-322">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="0d106-323">Le module peut ajouter des commandes, des types et des fichiers de mise en forme, puis exécuter des scripts dans la session.</span><span class="sxs-lookup"><span data-stu-id="0d106-323">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="0d106-324">Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la `$PSModuleAutoLoadingPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="0d106-324">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="0d106-325">Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="0d106-325">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="0d106-326">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0d106-326">RELATED LINKS</span></span>

[<span data-ttu-id="0d106-327">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="0d106-327">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="0d106-328">Get-Help</span><span class="sxs-lookup"><span data-stu-id="0d106-328">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="0d106-329">Get-Member</span><span class="sxs-lookup"><span data-stu-id="0d106-329">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="0d106-330">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="0d106-330">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="0d106-331">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="0d106-331">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="0d106-332">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="0d106-332">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)

