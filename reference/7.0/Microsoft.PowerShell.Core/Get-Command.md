---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 12cf373e5e53a45f7cdadd5e3a9f3fec7a7a8bb8
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201949"
---
# <span data-ttu-id="dddfb-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="dddfb-103">Get-Command</span></span>

## <span data-ttu-id="dddfb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="dddfb-104">SYNOPSIS</span></span>
<span data-ttu-id="dddfb-105">Obtient toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="dddfb-105">Gets all commands.</span></span>

## <span data-ttu-id="dddfb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dddfb-106">SYNTAX</span></span>

### <span data-ttu-id="dddfb-107">CmdletSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="dddfb-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="dddfb-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="dddfb-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## <span data-ttu-id="dddfb-109">Description</span><span class="sxs-lookup"><span data-stu-id="dddfb-109">DESCRIPTION</span></span>

<span data-ttu-id="dddfb-110">L' `Get-Command` applet de commande obtient toutes les commandes qui sont installées sur l’ordinateur, y compris les applets de commande, les alias, les fonctions, les filtres, les scripts et les applications.</span><span class="sxs-lookup"><span data-stu-id="dddfb-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="dddfb-111">`Get-Command` Obtient les commandes des modules PowerShell et des commandes qui ont été importées à partir d’autres sessions.</span><span class="sxs-lookup"><span data-stu-id="dddfb-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="dddfb-112">Pour obtenir uniquement les commandes qui ont été importées dans la session active, utilisez le paramètre **ListImported** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="dddfb-113">Sans paramètres, `Get-Command` obtient toutes les applets de commande, fonctions et alias installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dddfb-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="dddfb-114">`Get-Command *` Obtient tous les types de commandes, y compris tous les fichiers non-PowerShell dans la variable d’environnement PATH ( `$env:Path` ), qu’elle répertorie dans le type de commande de l’application.</span><span class="sxs-lookup"><span data-stu-id="dddfb-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="dddfb-115">`Get-Command` qui utilise le nom exact de la commande, sans caractères génériques, importe automatiquement le module qui contient la commande afin que vous puissiez utiliser la commande immédiatement.</span><span class="sxs-lookup"><span data-stu-id="dddfb-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="dddfb-116">Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la `$PSModuleAutoLoadingPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="dddfb-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="dddfb-117">Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="dddfb-118">`Get-Command` obtient ses données directement à partir du code de commande, contrairement `Get-Help` à, qui obtient ses informations à partir des rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="dddfb-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="dddfb-119">À compter de Windows PowerShell 5,0, les résultats de l’applet de commande `Get-Command` affichent une colonne de **version** par défaut.</span><span class="sxs-lookup"><span data-stu-id="dddfb-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="dddfb-120">Une nouvelle propriété de **version** a été ajoutée à la classe **CommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="dddfb-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="dddfb-121">EXAMPLES</span></span>

### <span data-ttu-id="dddfb-122">Exemple 1 : recevoir des applets de commande, des fonctions et des alias</span><span class="sxs-lookup"><span data-stu-id="dddfb-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="dddfb-123">Cette commande obtient les applets de commande, fonctions et alias PowerShell installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dddfb-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="dddfb-124">Exemple 2 : récupérer des commandes dans la session active</span><span class="sxs-lookup"><span data-stu-id="dddfb-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="dddfb-125">Cette commande utilise le paramètre **ListImported** pour récupérer uniquement les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="dddfb-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="dddfb-126">Exemple 3 : obtenir des applets de commande et les afficher dans l’ordre</span><span class="sxs-lookup"><span data-stu-id="dddfb-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="dddfb-127">Cette commande obtient toutes les applets de commande, les trie par ordre alphabétique en fonction du nom de l'applet de commande, et les affiche ensuite dans des groupes basés sur le nom.</span><span class="sxs-lookup"><span data-stu-id="dddfb-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="dddfb-128">Cet affichage peut vous aider à trouver les applets de commande d'une tâche.</span><span class="sxs-lookup"><span data-stu-id="dddfb-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="dddfb-129">Exemple 4 : obtenir des commandes dans un module</span><span class="sxs-lookup"><span data-stu-id="dddfb-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="dddfb-130">Cette commande utilise le paramètre **module** pour récupérer les commandes dans les modules Microsoft. PowerShell. Security et Microsoft. PowerShell. Utility.</span><span class="sxs-lookup"><span data-stu-id="dddfb-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="dddfb-131">Exemple 5 : obtenir des informations sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dddfb-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="dddfb-132">Cette commande obtient des informations sur l’applet de commande `Get-AppLockerPolicy` .</span><span class="sxs-lookup"><span data-stu-id="dddfb-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="dddfb-133">Elle importe également le module **AppLocker** , qui ajoute toutes les commandes du module **AppLocker** à la session active.</span><span class="sxs-lookup"><span data-stu-id="dddfb-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="dddfb-134">Quand un module est importé automatiquement, l’effet est identique à l’utilisation de l’applet de commande Import-Module.</span><span class="sxs-lookup"><span data-stu-id="dddfb-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="dddfb-135">Le module peut ajouter des commandes, des types et des fichiers de mise en forme, puis exécuter des scripts dans la session.</span><span class="sxs-lookup"><span data-stu-id="dddfb-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="dddfb-136">Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la `$PSModuleAutoLoadingPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="dddfb-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="dddfb-137">Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="dddfb-138">Exemple 6 : obtenir la syntaxe d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dddfb-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="dddfb-139">Cette commande utilise les paramètres **argumentlist** et **Syntax** pour récupérer la syntaxe de l’applet de commande `Get-ChildItem` quand elle est utilisée dans le lecteur Cert :.</span><span class="sxs-lookup"><span data-stu-id="dddfb-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="dddfb-140">Le lecteur Cert : est un lecteur PowerShell que le fournisseur de certificats ajoute à la session.</span><span class="sxs-lookup"><span data-stu-id="dddfb-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="dddfb-141">Lorsque vous comparez la syntaxe affichée dans la sortie avec la syntaxe qui s’affiche lorsque vous omettez le paramètre **args** ( **argumentlist** ), vous constatez que le **fournisseur de certificats** ajoute un paramètre dynamique, **CodeSigningCert** , à l’applet de commande `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="dddfb-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** ( **ArgumentList** ) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert** , to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="dddfb-142">Pour plus d’informations sur le fournisseur de certificats, consultez [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="dddfb-143">Exemple 7 : récupération des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="dddfb-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="dddfb-144">La commande de l’exemple utilise la `Get-DynamicParameters` fonction pour récupérer les paramètres dynamiques que le fournisseur de certificats ajoute à l’applet de commande `Get-ChildItem` lorsqu’il est utilisé dans le lecteur Cert :.</span><span class="sxs-lookup"><span data-stu-id="dddfb-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="dddfb-145">`Get-DynamicParameters`Dans cet exemple, la fonction obtient les paramètres dynamiques d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="dddfb-146">Il s'agit d'une alternative à la méthode utilisée dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="dddfb-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="dddfb-147">Un paramètre dynamique peut être ajouté à une applet de commande par une autre applet de commande ou un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="dddfb-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="dddfb-148">Exemple 8 : récupération de toutes les commandes de tous les types</span><span class="sxs-lookup"><span data-stu-id="dddfb-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="dddfb-149">Cette commande obtient toutes les commandes de tous les types sur l’ordinateur local, y compris les fichiers exécutables dans les chemins d’accès de la variable d’environnement **path** ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="dddfb-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="dddfb-150">Elle retourne un objet **ApplicationInfo** (System.Management.Automation.ApplicationInfo) pour chaque fichier, au lieu d'un objet **FileInfo** (System.IO.FileInfo).</span><span class="sxs-lookup"><span data-stu-id="dddfb-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="dddfb-151">Exemple 9 : obtenir des applets de commande à l’aide d’un nom et d’un type de paramètre</span><span class="sxs-lookup"><span data-stu-id="dddfb-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="dddfb-152">Cette commande obtient les applets de commande qui ont un paramètre dont le nom comprend auth et dont le type est **AuthenticationMechanism** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism** .</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="dddfb-153">Vous pouvez vous servir d'une commande similaire à celle-ci pour rechercher les applets de commande qui vous permettent de spécifier la méthode utilisée pour authentifier l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dddfb-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="dddfb-154">Le paramètre **ParameterType** distingue les paramètres qui acceptent une valeur **AuthenticationMechanism** par rapport à ceux qui acceptent un paramètre **AuthenticationLevel** , même quand ils ont des noms similaires.</span><span class="sxs-lookup"><span data-stu-id="dddfb-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="dddfb-155">Exemple 10 : recevoir un alias</span><span class="sxs-lookup"><span data-stu-id="dddfb-155">Example 10: Get an alias</span></span>

<span data-ttu-id="dddfb-156">Cet exemple montre comment utiliser l' `Get-Command` applet de commande avec un alias.</span><span class="sxs-lookup"><span data-stu-id="dddfb-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="dddfb-157">Bien qu’il soit généralement utilisé sur les applets de commande et les fonctions, il `Get-Command` obtient également les scripts, les fonctions, les alias et les fichiers exécutables.</span><span class="sxs-lookup"><span data-stu-id="dddfb-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="dddfb-158">La sortie de la commande montre l'affichage spécial de la valeur de propriété **Name** pour les alias.</span><span class="sxs-lookup"><span data-stu-id="dddfb-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="dddfb-159">L'affichage montre l'alias et le nom de commande complet.</span><span class="sxs-lookup"><span data-stu-id="dddfb-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="dddfb-160">Exemple 11 : récupération de toutes les instances de la commande Notepad</span><span class="sxs-lookup"><span data-stu-id="dddfb-160">Example 11: Get all instances of the Notepad command</span></span>

<span data-ttu-id="dddfb-161">Cet exemple utilise le paramètre **All** de l' `Get-Command` applet de commande pour afficher toutes les instances de la commande « Notepad » sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="dddfb-161">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the "Notepad" command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="dddfb-162">Le paramètre **All** est utile quand il existe plusieurs commandes portant le même nom dans la session.</span><span class="sxs-lookup"><span data-stu-id="dddfb-162">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="dddfb-163">À compter de Windows PowerShell 3,0, par défaut, lorsque la session comprend plusieurs commandes portant le même nom, `Get-Command` obtient uniquement la commande qui s’exécute lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-163">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="dddfb-164">Avec le paramètre **All** , `Get-Command` obtient toutes les commandes portant le nom spécifié et les retourne dans l’ordre de priorité d’exécution.</span><span class="sxs-lookup"><span data-stu-id="dddfb-164">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="dddfb-165">Pour exécuter une autre commande que la première de la liste, tapez le chemin d'accès complet de la commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-165">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="dddfb-166">Pour plus d’informations sur la priorité des commandes, consultez [about_Command_Precedence](About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-166">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="dddfb-167">Exemple 12 : obtenir le nom d’un module qui contient une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dddfb-167">Example 12: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="dddfb-168">Cette commande obtient le nom du module dans lequel l’applet de commande `Get-Date` provient.</span><span class="sxs-lookup"><span data-stu-id="dddfb-168">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="dddfb-169">La commande utilise la propriété **ModuleName** de toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="dddfb-169">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="dddfb-170">Ce format de commande fonctionne sur les commandes dans les modules PowerShell, même s’ils ne sont pas importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="dddfb-170">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="dddfb-171">Exemple 13 : obtenir des applets de commande et des fonctions qui ont un type de sortie</span><span class="sxs-lookup"><span data-stu-id="dddfb-171">Example 13: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="dddfb-172">Cette commande obtient les applets de commande et les fonctions qui ont un type de sortie, ainsi que le type d'objet qu'elles retournent.</span><span class="sxs-lookup"><span data-stu-id="dddfb-172">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="dddfb-173">La première partie de la commande obtient toutes les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-173">The first part of the command gets all cmdlets.</span></span>
<span data-ttu-id="dddfb-174">Un opérateur de pipeline (|) envoie les applets de commande à l’applet de commande `Where-Object` , qui sélectionne uniquement celles dans lesquelles la propriété **OutputType** est remplie.</span><span class="sxs-lookup"><span data-stu-id="dddfb-174">A pipeline operator (|) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span>
<span data-ttu-id="dddfb-175">Un autre opérateur de pipeline envoie les objets d’applet de commande sélectionnés à l’applet de commande `Format-List` , qui affiche le nom et le type de sortie de chaque applet de commande dans une liste.</span><span class="sxs-lookup"><span data-stu-id="dddfb-175">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="dddfb-176">La propriété **OutputType** d'un objet **CommandInfo** a une valeur non null uniquement quand le code de l'applet de commande définit l'attribut **OutputType** de cette dernière.</span><span class="sxs-lookup"><span data-stu-id="dddfb-176">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="dddfb-177">Exemple 14 : obtenir des applets de commande qui prennent un type d’objet spécifique comme entrée</span><span class="sxs-lookup"><span data-stu-id="dddfb-177">Example 14: Get cmdlets that take a specific object type as input</span></span>

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

<span data-ttu-id="dddfb-178">Cette commande recherche les applets de commande qui acceptent des objets de carte réseau en entrée.</span><span class="sxs-lookup"><span data-stu-id="dddfb-178">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="dddfb-179">Vous pouvez utiliser ce format de commande pour rechercher les applets de commande qui acceptent le type d'objet retourné par une commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-179">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="dddfb-180">La commande utilise la propriété intrinsèque **PSTypeNames** de tous les objets, qui obtient les types décrivant l'objet.</span><span class="sxs-lookup"><span data-stu-id="dddfb-180">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="dddfb-181">Pour obtenir la propriété **PSTypeNames** d'une carte réseau, et non la propriété **PSTypeNames** d'une collection de cartes réseau, la commande utilise une notation de tableau. Ainsi, elle obtient la première carte réseau retournée par l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-181">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

### <span data-ttu-id="dddfb-182">Exemple 15 : obtenir des commandes à l’aide d’une correspondance approximative</span><span class="sxs-lookup"><span data-stu-id="dddfb-182">Example 15: Get commands using a fuzzy match</span></span>

<span data-ttu-id="dddfb-183">Dans cet exemple, le nom de la commande a délibérément une faute de frappe comme « commnd ».</span><span class="sxs-lookup"><span data-stu-id="dddfb-183">In this example, the name of the command deliberately has a typo as 'get-commnd'.</span></span>
<span data-ttu-id="dddfb-184">À l’aide du `-UseFuzzyMatching` commutateur, l’applet de commande déterminait que la meilleure correspondance était `Get-Command` suivie par d’autres commandes natives sur le système qui étaient une correspondance similaire.</span><span class="sxs-lookup"><span data-stu-id="dddfb-184">Using the `-UseFuzzyMatching` switch, the cmdlet determined that the best match was `Get-Command` followed by other native commands on the system that were a similar match.</span></span>

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

## <span data-ttu-id="dddfb-185">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dddfb-185">PARAMETERS</span></span>

### <span data-ttu-id="dddfb-186">-All</span><span class="sxs-lookup"><span data-stu-id="dddfb-186">-All</span></span>

<span data-ttu-id="dddfb-187">Indique que cette applet de commande obtient toutes les commandes, y compris les commandes du même type qui ont le même nom.</span><span class="sxs-lookup"><span data-stu-id="dddfb-187">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="dddfb-188">Par défaut, `Get-Command` obtient uniquement les commandes qui s’exécutent lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-188">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="dddfb-189">Pour plus d’informations sur la méthode utilisée par PowerShell pour sélectionner la commande à exécuter quand plusieurs commandes portent le même nom, consultez [about_Command_Precedence](About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-189">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="dddfb-190">Pour plus d’informations sur les noms de commande qualifiés du module et l’exécution de commandes qui ne s’exécutent pas par défaut en raison d’un conflit de noms, consultez [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-190">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="dddfb-191">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="dddfb-191">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="dddfb-192">Dans Windows PowerShell 2,0, `Get-Command` obtient toutes les commandes par défaut.</span><span class="sxs-lookup"><span data-stu-id="dddfb-192">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

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

### <span data-ttu-id="dddfb-193">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="dddfb-193">-ArgumentList</span></span>

<span data-ttu-id="dddfb-194">Spécifie un tableau d’arguments.</span><span class="sxs-lookup"><span data-stu-id="dddfb-194">Specifies an array of arguments.</span></span> <span data-ttu-id="dddfb-195">Cette applet de commande obtient des informations sur une applet de commande ou une fonction quand elle est utilisée avec les paramètres spécifiés (« arguments »).</span><span class="sxs-lookup"><span data-stu-id="dddfb-195">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="dddfb-196">L'alias d' **ArgumentList** est **Args** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-196">The alias for **ArgumentList** is **Args** .</span></span>

<span data-ttu-id="dddfb-197">Pour détecter les paramètres dynamiques disponibles uniquement quand certains autres paramètres sont utilisés, affectez la valeur de **argumentlist** aux paramètres qui déclenchent les paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="dddfb-197">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="dddfb-198">Pour détecter les paramètres dynamiques qu’un fournisseur ajoute à une applet de commande, définissez la valeur du paramètre **argumentlist** sur un chemin d’accès dans le lecteur du fournisseur, par exemple WSMan :, HKLM : ou CERT :.</span><span class="sxs-lookup"><span data-stu-id="dddfb-198">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="dddfb-199">Lorsque la commande est une applet de commande du fournisseur PowerShell, entrez un seul chemin d’accès dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-199">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="dddfb-200">Les applets de commande du fournisseur retournent uniquement les paramètres dynamiques du premier chemin d’accès de la valeur **argumentlist** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-200">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList** .</span></span> <span data-ttu-id="dddfb-201">Pour plus d’informations sur les applets de commande du fournisseur, consultez [about_Providers](About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-201">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

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

### <span data-ttu-id="dddfb-202">-CommandType</span><span class="sxs-lookup"><span data-stu-id="dddfb-202">-CommandType</span></span>

<span data-ttu-id="dddfb-203">Spécifie les types de commandes que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="dddfb-203">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="dddfb-204">Entrez un ou plusieurs types de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-204">Enter one or more command types.</span></span> <span data-ttu-id="dddfb-205">Utilisez **CommandType** ou son alias, **Type** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-205">Use **CommandType** or its alias, **Type** .</span></span> <span data-ttu-id="dddfb-206">Par défaut, `Get-Command` obtient toutes les applets de commande, fonctions et alias.</span><span class="sxs-lookup"><span data-stu-id="dddfb-206">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="dddfb-207">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="dddfb-207">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dddfb-208">Affecté.</span><span class="sxs-lookup"><span data-stu-id="dddfb-208">Alias.</span></span> <span data-ttu-id="dddfb-209">Obtient les alias de toutes les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dddfb-209">Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="dddfb-210">Pour plus d’informations, consultez [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-210">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="dddfb-211">Tout le monde.</span><span class="sxs-lookup"><span data-stu-id="dddfb-211">All.</span></span> <span data-ttu-id="dddfb-212">obtient tous les types de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-212">Gets all command types.</span></span> <span data-ttu-id="dddfb-213">Cette valeur de paramètre est l’équivalent de `Get-Command *` .</span><span class="sxs-lookup"><span data-stu-id="dddfb-213">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="dddfb-214">console.</span><span class="sxs-lookup"><span data-stu-id="dddfb-214">Application.</span></span> <span data-ttu-id="dddfb-215">Obtient les fichiers non-PowerShell dans les chemins d’accès figurant dans la variable **d’environnement PATH** ($env :p Hemin), y compris les fichiers. txt,. exe et. dll.</span><span class="sxs-lookup"><span data-stu-id="dddfb-215">Gets non-PowerShell files in paths listed in the **Path** environment variable ($env:path), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="dddfb-216">Pour plus d’informations sur la variable **d’environnement PATH** , consultez about_Environment_Variables.</span><span class="sxs-lookup"><span data-stu-id="dddfb-216">For more information about the **Path** environment variable, see about_Environment_Variables.</span></span>
- <span data-ttu-id="dddfb-217">PolicySchedule.</span><span class="sxs-lookup"><span data-stu-id="dddfb-217">Cmdlet.</span></span> <span data-ttu-id="dddfb-218">obtient toutes les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-218">Gets all cmdlets.</span></span>
- <span data-ttu-id="dddfb-219">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="dddfb-219">ExternalScript.</span></span> <span data-ttu-id="dddfb-220">obtient tous les fichiers .ps1 des chemins d'accès répertoriés dans la variable d'environnement **Path** ($env:path).</span><span class="sxs-lookup"><span data-stu-id="dddfb-220">Gets all .ps1 files in the paths listed in the **Path** environment variable ($env:path).</span></span>
- <span data-ttu-id="dddfb-221">Filtre et fonction.</span><span class="sxs-lookup"><span data-stu-id="dddfb-221">Filter and Function.</span></span> <span data-ttu-id="dddfb-222">Obtient tous les filtres et fonctions avancés et simples PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dddfb-222">Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="dddfb-223">Script.</span><span class="sxs-lookup"><span data-stu-id="dddfb-223">Script.</span></span> <span data-ttu-id="dddfb-224">obtient tous les blocs de script.</span><span class="sxs-lookup"><span data-stu-id="dddfb-224">Gets all script blocks.</span></span> <span data-ttu-id="dddfb-225">Pour accéder aux scripts PowerShell (fichiers. ps1), utilisez la valeur ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="dddfb-225">To get PowerShell scripts (.ps1 files), use the ExternalScript value.</span></span>

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

### <span data-ttu-id="dddfb-226">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="dddfb-226">-FullyQualifiedModule</span></span>

<span data-ttu-id="dddfb-227">Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** , décrits dans la section **Notes** du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="dddfb-227">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="dddfb-228">Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié dans l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="dddfb-228">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="dddfb-229">**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="dddfb-229">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="dddfb-230">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-230">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="dddfb-231">Les deux paramètres s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="dddfb-231">The two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="dddfb-232">-ListImported</span><span class="sxs-lookup"><span data-stu-id="dddfb-232">-ListImported</span></span>

<span data-ttu-id="dddfb-233">Indique que cette applet de commande obtient uniquement les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="dddfb-233">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="dddfb-234">À compter de PowerShell 3,0, par défaut, `Get-Command` obtient toutes les commandes installées, y compris, mais sans s’y limiter, les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="dddfb-234">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="dddfb-235">Dans PowerShell 2,0, elle obtient uniquement les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="dddfb-235">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="dddfb-236">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="dddfb-236">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="dddfb-237">-Module</span><span class="sxs-lookup"><span data-stu-id="dddfb-237">-Module</span></span>

<span data-ttu-id="dddfb-238">Spécifie un tableau de modules.</span><span class="sxs-lookup"><span data-stu-id="dddfb-238">Specifies an array of modules.</span></span> <span data-ttu-id="dddfb-239">Cette applet de commande obtient les commandes provenant des modules spécifiés.</span><span class="sxs-lookup"><span data-stu-id="dddfb-239">This cmdlet gets the commands that came from the specified modules.</span></span>
<span data-ttu-id="dddfb-240">Entrez les noms des modules ou des objets de module.</span><span class="sxs-lookup"><span data-stu-id="dddfb-240">Enter the names of modules or module objects.</span></span>

<span data-ttu-id="dddfb-241">Ce paramètre accepte les valeurs de chaîne, mais la valeur de ce paramètre peut également être un objet **PSModuleInfo** , tel que les objets `Get-Module` `Import-PSSession` retournés par les applets de commande et.</span><span class="sxs-lookup"><span data-stu-id="dddfb-241">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** object, such as the objects that the `Get-Module` and `Import-PSSession` cmdlets return.</span></span>

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

### <span data-ttu-id="dddfb-242">-Name</span><span class="sxs-lookup"><span data-stu-id="dddfb-242">-Name</span></span>

<span data-ttu-id="dddfb-243">Spécifie un tableau de noms.</span><span class="sxs-lookup"><span data-stu-id="dddfb-243">Specifies an array of names.</span></span> <span data-ttu-id="dddfb-244">Cette applet de commande obtient uniquement les commandes qui portent le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="dddfb-244">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="dddfb-245">Entrez un nom ou un modèle de nom.</span><span class="sxs-lookup"><span data-stu-id="dddfb-245">Enter a name or name pattern.</span></span> <span data-ttu-id="dddfb-246">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="dddfb-246">Wildcard characters are permitted.</span></span>

<span data-ttu-id="dddfb-247">Pour obtenir les commandes qui ont le même nom, utilisez le paramètre **All** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-247">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="dddfb-248">Lorsque deux commandes portent le même nom, par défaut, `Get-Command` obtient la commande qui s’exécute lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-248">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

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

### <span data-ttu-id="dddfb-249">-Substantif</span><span class="sxs-lookup"><span data-stu-id="dddfb-249">-Noun</span></span>

<span data-ttu-id="dddfb-250">Spécifie un tableau de noms de commandes.</span><span class="sxs-lookup"><span data-stu-id="dddfb-250">Specifies an array of command nouns.</span></span> <span data-ttu-id="dddfb-251">Cette applet de commande obtient les commandes, qui incluent des applets de commande, des fonctions et des alias, dont les noms incluent le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="dddfb-251">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="dddfb-252">Entrez un ou plusieurs noms ou modèles de noms.</span><span class="sxs-lookup"><span data-stu-id="dddfb-252">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="dddfb-253">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="dddfb-253">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="dddfb-254">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="dddfb-254">-ParameterName</span></span>

<span data-ttu-id="dddfb-255">Spécifie un tableau de noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="dddfb-255">Specifies an array of parameter names.</span></span> <span data-ttu-id="dddfb-256">Cette applet de commande obtient les commandes de la session qui ont les paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="dddfb-256">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="dddfb-257">Entrez les noms des paramètres ou les alias des paramètres.</span><span class="sxs-lookup"><span data-stu-id="dddfb-257">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="dddfb-258">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="dddfb-258">Wildcard characters are supported.</span></span>

<span data-ttu-id="dddfb-259">Les paramètres **ParameterName** et **ParameterType** recherchent uniquement les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="dddfb-259">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="dddfb-260">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="dddfb-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="dddfb-261">-ParameterType</span><span class="sxs-lookup"><span data-stu-id="dddfb-261">-ParameterType</span></span>

<span data-ttu-id="dddfb-262">Spécifie un tableau de noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="dddfb-262">Specifies an array of parameter names.</span></span> <span data-ttu-id="dddfb-263">Cette applet de commande obtient les commandes de la session qui ont des paramètres du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="dddfb-263">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="dddfb-264">Entrez le nom complet ou partiel d'un type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="dddfb-264">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="dddfb-265">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="dddfb-265">Wildcard characters are supported.</span></span>

<span data-ttu-id="dddfb-266">Les paramètres **ParameterName** et **ParameterType** recherchent uniquement les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="dddfb-266">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="dddfb-267">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="dddfb-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="dddfb-268">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="dddfb-268">-ShowCommandInfo</span></span>

<span data-ttu-id="dddfb-269">Indique que cette applet de commande affiche les informations de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-269">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="dddfb-270">Ce paramètre a été introduit dans Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="dddfb-270">This parameter was introduced in Windows PowerShell 5.0.</span></span>

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

### <span data-ttu-id="dddfb-271">-Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dddfb-271">-Syntax</span></span>

<span data-ttu-id="dddfb-272">Indique que cette applet de commande obtient uniquement les données spécifiées suivantes sur la commande :</span><span class="sxs-lookup"><span data-stu-id="dddfb-272">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="dddfb-273">Alias.</span><span class="sxs-lookup"><span data-stu-id="dddfb-273">Aliases.</span></span> <span data-ttu-id="dddfb-274">Obtient le nom standard.</span><span class="sxs-lookup"><span data-stu-id="dddfb-274">Gets the standard name.</span></span>
- <span data-ttu-id="dddfb-275">Applets.</span><span class="sxs-lookup"><span data-stu-id="dddfb-275">Cmdlets.</span></span> <span data-ttu-id="dddfb-276">Obtient la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="dddfb-276">Gets the syntax.</span></span>
- <span data-ttu-id="dddfb-277">Fonctions et filtres.</span><span class="sxs-lookup"><span data-stu-id="dddfb-277">Functions and filters.</span></span> <span data-ttu-id="dddfb-278">Obtient la définition de la fonction.</span><span class="sxs-lookup"><span data-stu-id="dddfb-278">Gets the function definition.</span></span>
- <span data-ttu-id="dddfb-279">Scripts et applications ou fichiers.</span><span class="sxs-lookup"><span data-stu-id="dddfb-279">Scripts and applications or files.</span></span> <span data-ttu-id="dddfb-280">Obtient le chemin d’accès et le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="dddfb-280">Gets the path and filename.</span></span>

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

### <span data-ttu-id="dddfb-281">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="dddfb-281">-TotalCount</span></span>

<span data-ttu-id="dddfb-282">Spécifie le nombre de commandes à récupérer.</span><span class="sxs-lookup"><span data-stu-id="dddfb-282">Specifies the number of commands to get.</span></span> <span data-ttu-id="dddfb-283">Vous pouvez utiliser ce paramètre pour limiter la sortie d'une commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-283">You can use this parameter to limit the output of a command.</span></span>

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

### <span data-ttu-id="dddfb-284">-UseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="dddfb-284">-UseAbbreviationExpansion</span></span>

<span data-ttu-id="dddfb-285">Indique l’utilisation de la correspondance des caractères dans la commande pour rechercher des caractères majuscules dans une commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-285">Indicates using matching of the characters in the command to find with uppercase characters in a command.</span></span> <span data-ttu-id="dddfb-286">Par exemple, `i-psdf` correspond à `Import-PowerShellDataFile` chaque caractère à trouver correspond à un caractère majuscule dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="dddfb-286">For example, `i-psdf` would match `Import-PowerShellDataFile` as each of the characters to find matches an uppercase character in the result.</span></span> <span data-ttu-id="dddfb-287">En cas d’utilisation de ce type de correspondance, les caractères génériques n’aboutissent à aucune correspondance.</span><span class="sxs-lookup"><span data-stu-id="dddfb-287">When using this type of match, any wildcards will result in no matches.</span></span>

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

### <span data-ttu-id="dddfb-288">-UseFuzzyMatching</span><span class="sxs-lookup"><span data-stu-id="dddfb-288">-UseFuzzyMatching</span></span>

<span data-ttu-id="dddfb-289">Indique l’utilisation d’un algorithme de correspondance approximative lors de la recherche de commandes.</span><span class="sxs-lookup"><span data-stu-id="dddfb-289">Indicates using a fuzzy matching algorithm when finding commands.</span></span> <span data-ttu-id="dddfb-290">L’ordre de la sortie provient de la correspondance la plus proche à la plus petite correspondance probable.</span><span class="sxs-lookup"><span data-stu-id="dddfb-290">The order of the output is from closest match to least likely match.</span></span> <span data-ttu-id="dddfb-291">Les caractères génériques ne doivent pas être utilisés avec la correspondance approximative, car ils tentent de faire correspondre les commandes qui peuvent contenir ces caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="dddfb-291">Wildcards should not be used with fuzzy matching as it will attempt to match commands that may contain those wildcard characters.</span></span>

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

### <span data-ttu-id="dddfb-292">-Verbe</span><span class="sxs-lookup"><span data-stu-id="dddfb-292">-Verb</span></span>

<span data-ttu-id="dddfb-293">Spécifie un tableau de verbes de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-293">Specifies an array of command verbs.</span></span> <span data-ttu-id="dddfb-294">Cette applet de commande obtient les commandes, qui incluent des applets de commande, des fonctions et des alias, dont les noms incluent le verbe spécifié.</span><span class="sxs-lookup"><span data-stu-id="dddfb-294">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="dddfb-295">Entrez un ou plusieurs verbes ou modèles de verbes.</span><span class="sxs-lookup"><span data-stu-id="dddfb-295">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="dddfb-296">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="dddfb-296">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="dddfb-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dddfb-297">CommonParameters</span></span>

<span data-ttu-id="dddfb-298">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dddfb-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dddfb-299">Pour plus d’informations, consultez [about_CommonParameters](About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-299">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="dddfb-300">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="dddfb-300">INPUTS</span></span>

### <span data-ttu-id="dddfb-301">System.String</span><span class="sxs-lookup"><span data-stu-id="dddfb-301">System.String</span></span>

<span data-ttu-id="dddfb-302">Vous pouvez diriger les noms de commandes vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-302">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="dddfb-303">SORTIES</span><span class="sxs-lookup"><span data-stu-id="dddfb-303">OUTPUTS</span></span>

### <span data-ttu-id="dddfb-304">System. Management. Automation. CommandInfo</span><span class="sxs-lookup"><span data-stu-id="dddfb-304">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="dddfb-305">Cette applet de commande retourne des objets dérivés de la classe **CommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-305">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="dddfb-306">Le type d’objet retourné dépend du type de commande que `Get-Command` obtient.</span><span class="sxs-lookup"><span data-stu-id="dddfb-306">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="dddfb-307">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="dddfb-307">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="dddfb-308">Représente des alias.</span><span class="sxs-lookup"><span data-stu-id="dddfb-308">Represents aliases.</span></span>

### <span data-ttu-id="dddfb-309">System. Management. Automation. ApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="dddfb-309">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="dddfb-310">Représente des applications et des fichiers.</span><span class="sxs-lookup"><span data-stu-id="dddfb-310">Represents applications and files.</span></span>

### <span data-ttu-id="dddfb-311">System. Management. Automation. CmdletInfo</span><span class="sxs-lookup"><span data-stu-id="dddfb-311">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="dddfb-312">Représente des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-312">Represents cmdlets.</span></span>

### <span data-ttu-id="dddfb-313">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="dddfb-313">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="dddfb-314">Représente des fonctions et des filtres.</span><span class="sxs-lookup"><span data-stu-id="dddfb-314">Represents functions and filters.</span></span>

## <span data-ttu-id="dddfb-315">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="dddfb-315">NOTES</span></span>

* <span data-ttu-id="dddfb-316">Quand plusieurs commandes portant le même nom sont disponibles pour la session, `Get-Command` retourne la commande qui s’exécute lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="dddfb-316">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="dddfb-317">Pour obtenir les commandes portant le même nom, listées dans ordre d’exécution, utilisez le paramètre **All** .</span><span class="sxs-lookup"><span data-stu-id="dddfb-317">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="dddfb-318">Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-318">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
* <span data-ttu-id="dddfb-319">Quand un module est importé automatiquement, l’effet est identique à l’utilisation de l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="dddfb-319">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="dddfb-320">Le module peut ajouter des commandes, des types et des fichiers de mise en forme, puis exécuter des scripts dans la session.</span><span class="sxs-lookup"><span data-stu-id="dddfb-320">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="dddfb-321">Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la `$PSModuleAutoLoadingPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="dddfb-321">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="dddfb-322">Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="dddfb-322">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="dddfb-323">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="dddfb-323">RELATED LINKS</span></span>

[<span data-ttu-id="dddfb-324">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="dddfb-324">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="dddfb-325">Get-Help</span><span class="sxs-lookup"><span data-stu-id="dddfb-325">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="dddfb-326">Get-Member</span><span class="sxs-lookup"><span data-stu-id="dddfb-326">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="dddfb-327">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="dddfb-327">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="dddfb-328">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="dddfb-328">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="dddfb-329">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="dddfb-329">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)
