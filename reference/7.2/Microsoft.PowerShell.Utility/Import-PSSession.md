---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: 1a87783f9d12d852d3a6809e9457a55ad6e7be50
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597322"
---
# <span data-ttu-id="ef3ae-102">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef3ae-102">Import-PSSession</span></span>

## <span data-ttu-id="ef3ae-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ef3ae-103">SYNOPSIS</span></span>
<span data-ttu-id="ef3ae-104">Importe des commandes à partir d'une autre session dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-104">Imports commands from another session into the current session.</span></span>

## <span data-ttu-id="ef3ae-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="ef3ae-105">SYNTAX</span></span>

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## <span data-ttu-id="ef3ae-106">Description</span><span class="sxs-lookup"><span data-stu-id="ef3ae-106">DESCRIPTION</span></span>

<span data-ttu-id="ef3ae-107">L' `Import-PSSession` applet de commande importe des commandes, telles que des applets de commande, des fonctions et des alias, à partir d’une session PSSession sur un ordinateur local ou distant dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-107">The `Import-PSSession` cmdlet imports commands , such as cmdlets, functions, and aliases, from a PSSession on a local or remote computer into the current session.</span></span> <span data-ttu-id="ef3ae-108">Vous pouvez importer n’importe quelle commande que l' `Get-Command` applet de commande peut trouver dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-108">You can import any command that the `Get-Command` cmdlet can find in the PSSession.</span></span>

<span data-ttu-id="ef3ae-109">Utilisez une `Import-PSSession` commande pour importer des commandes à partir d’un shell personnalisé, tel qu’un shell Microsoft Exchange Server, ou à partir d’une session qui comprend des modules et des composants logiciels enfichables Windows PowerShell ou d’autres éléments qui ne sont pas dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-109">Use an `Import-PSSession` command to import commands from a customized shell, such as a Microsoft Exchange Server shell, or from a session that includes Windows PowerShell modules and snap-ins or other elements that are not in the current session.</span></span>

<span data-ttu-id="ef3ae-110">Pour importer des commandes, utilisez d’abord l' `New-PSSession` applet de commande pour créer une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-110">To import commands, first use the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="ef3ae-111">Utilisez ensuite l' `Import-PSSession` applet de commande pour importer les commandes.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-111">Then, use the `Import-PSSession` cmdlet to import the commands.</span></span> <span data-ttu-id="ef3ae-112">Par défaut, `Import-PSSession` importe toutes les commandes, à l’exception des commandes qui ont les mêmes noms que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-112">By default, `Import-PSSession` imports all commands except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="ef3ae-113">Pour importer toutes les commandes, utilisez le paramètre **AllowClobber**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-113">To import all the commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="ef3ae-114">Vous pouvez utiliser des commandes importées comme vous utiliseriez n'importe quelle commande de la session.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-114">You can use imported commands just as you would use any command in the session.</span></span> <span data-ttu-id="ef3ae-115">Quand vous utilisez une commande importée, la partie importée de la commande s'exécute implicitement dans la session à partir de laquelle elle a été importée.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-115">When you use an imported command, the imported part of the command runs implicitly in the session from which it was imported.</span></span> <span data-ttu-id="ef3ae-116">Toutefois, les opérations à distance sont gérées entièrement par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-116">However, the remote operations are handled entirely by Windows PowerShell.</span></span> <span data-ttu-id="ef3ae-117">Vous ne devez même pas vous en rendre compte, sauf que vous devez conserver la connexion à l'autre session (PSSession) ouverte.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-117">You need not even be aware of them, except that you must keep the connection to the other session (PSSession) open.</span></span> <span data-ttu-id="ef3ae-118">Si vous la fermez, les commandes importées ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-118">If you close it, the imported commands are no longer available.</span></span>

<span data-ttu-id="ef3ae-119">Étant donné que les commandes importées peuvent durer plus longtemps que les commandes locales, `Import-PSSession` ajoute un paramètre **AsJob** à chaque commande importée.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-119">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="ef3ae-120">Ce paramètre vous permet d'exécuter la commande en tant que tâche en arrière-plan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-120">This parameter allows you to run the command as a Windows PowerShell background job.</span></span> <span data-ttu-id="ef3ae-121">Pour plus d’informations, consultez [à propos des_tâches](../Microsoft.PowerShell.Core/about/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="ef3ae-121">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md).</span></span>

<span data-ttu-id="ef3ae-122">Lorsque vous utilisez `Import-PSSession` , Windows PowerShell ajoute les commandes importées à un module temporaire qui existe uniquement dans votre session et retourne un objet qui représente le module.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-122">When you use `Import-PSSession`, Windows PowerShell adds the imported commands to a temporary module that exists only in your session and returns an object that represents the module.</span></span> <span data-ttu-id="ef3ae-123">Pour créer un module permanent que vous pouvez utiliser dans les sessions ultérieures, utilisez l’applet de commande `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-123">To create a persistent module that you can use in future sessions, use the `Export-PSSession` cmdlet.</span></span>

<span data-ttu-id="ef3ae-124">L' `Import-PSSession` applet de commande utilise la fonctionnalité de communication à distance implicite de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-124">The `Import-PSSession` cmdlet uses the implicit remoting feature of Windows PowerShell.</span></span> <span data-ttu-id="ef3ae-125">Lorsque vous importez des commandes dans la session active, elles s’exécutent implicitement dans la session d’origine ou dans une session similaire sur l’ordinateur d’origine.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-125">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

<span data-ttu-id="ef3ae-126">À compter de Windows PowerShell 3,0, vous pouvez utiliser la `Import-Module` cmdlet pour importer des modules à partir d’une session à distance dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-126">Beginning in Windows PowerShell 3.0, you can use the `Import-Module` cmdlet to import modules from a remote session into the current session.</span></span> <span data-ttu-id="ef3ae-127">Cette fonctionnalité utilise la communication à distance implicite.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-127">This feature uses implicit remoting.</span></span> <span data-ttu-id="ef3ae-128">Cela équivaut à utiliser `Import-PSSession` pour importer des modules sélectionnés à partir d’une session à distance dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-128">It is equivalent to using `Import-PSSession` to import selected modules from a remote session into the current session.</span></span>

## <span data-ttu-id="ef3ae-129">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ef3ae-129">EXAMPLES</span></span>

### <span data-ttu-id="ef3ae-130">Exemple 1 : importer toutes les commandes à partir d’une session PSSession</span><span class="sxs-lookup"><span data-stu-id="ef3ae-130">Example 1: Import all commands from a PSSession</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

<span data-ttu-id="ef3ae-131">Cette commande importe toutes les commandes d'une session PSSession sur l'ordinateur Server01 dans la session active, à l'exception des commandes qui ont le même nom que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-131">This command imports all commands from a PSSession on the Server01 computer into the current session, except for commands that have the same names as commands in the current session.</span></span>

<span data-ttu-id="ef3ae-132">Comme cette commande n'utilise pas le paramètre **CommandName**, elle importe également toutes les données de mise en forme requises pour les commandes importées.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-132">Because this command does not use the **CommandName** parameter, it also imports all of the formatting data required for the imported commands.</span></span>

### <span data-ttu-id="ef3ae-133">Exemple 2 : importer des commandes qui se terminent par une chaîne spécifique</span><span class="sxs-lookup"><span data-stu-id="ef3ae-133">Example 2: Import commands that end with a specific string</span></span>

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

<span data-ttu-id="ef3ae-134">Ces commandes importent les commandes dont les noms se terminent par « -test » à partir d'une session PSSession dans la session locale, puis indiquent comment utiliser une applet de commande importée.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-134">These commands import the commands with names that end in "-test" from a PSSession into the local session, and then they show how to use an imported cmdlet.</span></span>

<span data-ttu-id="ef3ae-135">La première commande utilise l' `New-PSSession` applet de commande pour créer une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-135">The first command uses the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="ef3ae-136">Elle enregistre la session PSSession dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-136">It saves the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="ef3ae-137">La deuxième commande utilise l' `Import-PSSession` applet de commande pour importer des commandes de la session PSSession dans dans `$S` la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-137">The second command uses the `Import-PSSession` cmdlet to import commands from the PSSession in `$S` into the current session.</span></span> <span data-ttu-id="ef3ae-138">Elle utilise le paramètre **CommandName** pour spécifier des commandes avec le nom Test et le paramètre **FormatTypeName** pour importer les données de mise en forme pour les commandes Test.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-138">It uses the **CommandName** parameter to specify commands with the Test noun and the **FormatTypeName** parameter to import the formatting data for the Test commands.</span></span>

<span data-ttu-id="ef3ae-139">Les troisième et quatrième commandes utilisent les commandes importées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-139">The third and fourth commands use the imported commands in the current session.</span></span> <span data-ttu-id="ef3ae-140">Comme les commandes importées sont en réalité ajoutées à la session active, vous utilisez la syntaxe locale pour les exécuter.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-140">Because imported commands are actually added to the current session, you use the local syntax to run them.</span></span> <span data-ttu-id="ef3ae-141">Vous n’avez pas besoin d’utiliser l' `Invoke-Command` applet de commande pour exécuter une commande importée.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-141">You do not need to use the `Invoke-Command` cmdlet to run an imported command.</span></span>

### <span data-ttu-id="ef3ae-142">Exemple 3 : importer des applets de commande à partir d’une session PSSession</span><span class="sxs-lookup"><span data-stu-id="ef3ae-142">Example 3: Import cmdlets from a PSSession</span></span>

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

<span data-ttu-id="ef3ae-143">Cet exemple montre que vous pouvez utiliser les applets de commande importées comme vous utiliseriez des applets de commande locales.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-143">This example shows that you can use imported cmdlets just as you would use local cmdlets.</span></span>

<span data-ttu-id="ef3ae-144">Ces commandes importent les `New-Test` applets de commande et `Get-Test` à partir d’une session PSSession sur l’ordinateur SERVEUR01 et l' `Set-Test` applet de commande à partir d’une session PSSession sur l’ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-144">These commands import the `New-Test` and `Get-Test` cmdlets from a PSSession on the Server01 computer and the `Set-Test` cmdlet from a PSSession on the Server02 computer.</span></span>

<span data-ttu-id="ef3ae-145">Même si les applets de commande ont été importées à partir de différentes sessions PSSession, vous pouvez diriger un objet d'une applet de commande vers une autre sans erreur.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-145">Even though the cmdlets were imported from different PSSessions, you can pipe an object from one cmdlet to another without error.</span></span>

### <span data-ttu-id="ef3ae-146">Exemple 4 : exécuter une commande importée en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="ef3ae-146">Example 4: Run an imported command as a background job</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

<span data-ttu-id="ef3ae-147">Cet exemple montre comment exécuter une commande importée en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-147">This example shows how to run an imported command as a background job.</span></span>

<span data-ttu-id="ef3ae-148">Étant donné que les commandes importées peuvent durer plus longtemps que les commandes locales, `Import-PSSession` ajoute un paramètre **AsJob** à chaque commande importée.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-148">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="ef3ae-149">Le paramètre **AsJob** vous permet d'exécuter la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-149">The **AsJob** parameter lets you run the command as a background job.</span></span>

<span data-ttu-id="ef3ae-150">La première commande crée une session PSSession sur l’ordinateur SERVEUR01 et enregistre l’objet PSSession dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-150">The first command creates a PSSession on the Server01 computer and saves the PSSession object in the `$S` variable.</span></span>

<span data-ttu-id="ef3ae-151">La deuxième commande utilise `Import-PSSession` pour importer les applets de commande de test de la session PSSession dans `$S` dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-151">The second command uses `Import-PSSession` to import the Test cmdlets from the PSSession in `$S` into the current session.</span></span>

<span data-ttu-id="ef3ae-152">La troisième commande utilise le paramètre **AsJob** de l’applet de commande importée `New-Test` pour exécuter une `New-Test` commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-152">The third command uses the **AsJob** parameter of the imported `New-Test` cmdlet to run a `New-Test` command as a background job.</span></span> <span data-ttu-id="ef3ae-153">La commande enregistre l’objet de traitement qui `New-Test` retourne dans la `$batch` variable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-153">The command saves the job object that `New-Test` returns in the `$batch` variable.</span></span>

<span data-ttu-id="ef3ae-154">La quatrième commande utilise l' `Receive-Job` applet de commande pour obtenir les résultats de la tâche dans la `$batch` variable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-154">The fourth command uses the `Receive-Job` cmdlet to get the results of the job in the `$batch` variable.</span></span>

### <span data-ttu-id="ef3ae-155">Exemple 5 : importer des applets de commande et des fonctions à partir d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef3ae-155">Example 5: Import cmdlets and functions from a Windows PowerShell module</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

<span data-ttu-id="ef3ae-156">Cet exemple montre comment importer les applets de commande et fonctions à partir d'un module Windows PowerShell sur un ordinateur distant dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-156">This example shows how to import the cmdlets and functions from a Windows PowerShell module on a remote computer into the current session.</span></span>

<span data-ttu-id="ef3ae-157">La première commande crée une session PSSession sur l’ordinateur SERVEUR01 et l’enregistre dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-157">The first command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span>

<span data-ttu-id="ef3ae-158">La deuxième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Import-Module` commande dans la session PSSession dans `$S` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-158">The second command uses the `Invoke-Command` cmdlet to run an `Import-Module` command in the PSSession in `$S`.</span></span>

<span data-ttu-id="ef3ae-159">En règle générale, le module est ajouté à toutes les sessions par une `Import-Module` commande dans un profil Windows PowerShell, mais les profils ne sont pas exécutés dans sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-159">Typically, the module would be added to all sessions by an `Import-Module` command in a Windows PowerShell profile, but profiles are not run in PSSessions.</span></span>

<span data-ttu-id="ef3ae-160">La troisième commande utilise le paramètre **module** de `Import-PSSession` pour importer les applets de commande et les fonctions du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-160">The third command uses the **Module** parameter of `Import-PSSession` to import the cmdlets and functions in the module into the current session.</span></span>

### <span data-ttu-id="ef3ae-161">Exemple 6 : créer un module dans un fichier temporaire</span><span class="sxs-lookup"><span data-stu-id="ef3ae-161">Example 6: Create a module in a temporary file</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="ef3ae-162">Cet exemple montre que `Import-PSSession` crée un module dans un fichier temporaire sur le disque.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-162">This example shows that `Import-PSSession` creates a module in a temporary file on disk.</span></span> <span data-ttu-id="ef3ae-163">Il montre également que toutes les commandes sont converties en fonctions avant leur importation dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-163">It also shows that all commands are converted into functions before they are imported into the current session.</span></span>

<span data-ttu-id="ef3ae-164">La commande utilise l' `Import-PSSession` applet de commande pour importer une applet de commande `Get-Date` et une fonction SearchHelp dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-164">The command uses the `Import-PSSession` cmdlet to import a `Get-Date` cmdlet and a SearchHelp function into the current session.</span></span>

<span data-ttu-id="ef3ae-165">L' `Import-PSSession` applet de commande retourne un objet **PSModuleInfo** qui représente le module temporaire.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-165">The `Import-PSSession` cmdlet returns a **PSModuleInfo** object that represents the temporary module.</span></span> <span data-ttu-id="ef3ae-166">La valeur de la propriété **path** indique que `Import-PSSession` a créé un fichier de module de script (. psm1) dans un emplacement temporaire.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-166">The value of the **Path** property shows that `Import-PSSession` created a script module (.psm1) file in a temporary location.</span></span> <span data-ttu-id="ef3ae-167">La propriété **ExportedFunctions** montre que l' `Get-Date` applet de commande et la fonction SearchHelp ont été importées en tant que fonctions.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-167">The **ExportedFunctions** property shows that the `Get-Date` cmdlet and the SearchHelp function were both imported as functions.</span></span>

### <span data-ttu-id="ef3ae-168">Exemple 7 : exécuter une commande qui est masquée par une commande importée</span><span class="sxs-lookup"><span data-stu-id="ef3ae-168">Example 7: Run a command that is hidden by an imported command</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

<span data-ttu-id="ef3ae-169">Cet exemple montre comment exécuter une commande qui est masquée par une commande importée.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-169">This example shows how to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="ef3ae-170">La première commande importe une `Get-Date` applet de commande à partir de la session PSSession dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-170">The first command imports a `Get-Date` cmdlet from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="ef3ae-171">Étant donné que la session active comprend une `Get-Date` applet de commande, le paramètre **AllowClobber** est requis dans la commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-171">Because the current session includes a `Get-Date` cmdlet, the **AllowClobber** parameter is required in the command.</span></span>

<span data-ttu-id="ef3ae-172">La deuxième commande utilise le paramètre **All** de l' `Get-Command` applet de commande pour récupérer toutes les `Get-Date` commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-172">The second command uses the **All** parameter of the `Get-Command` cmdlet to get all `Get-Date` commands in the current session.</span></span> <span data-ttu-id="ef3ae-173">La sortie indique que la session comprend l’applet de commande d’origine `Get-Date` et une `Get-Date` fonction.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-173">The output shows that the session includes the original `Get-Date` cmdlet and a `Get-Date` function.</span></span> <span data-ttu-id="ef3ae-174">La `Get-Date` fonction exécute l’applet de commande importée `Get-Date` dans la session PSSession dans `$S` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-174">The `Get-Date` function runs the imported `Get-Date` cmdlet in the PSSession in `$S`.</span></span>

<span data-ttu-id="ef3ae-175">La troisième commande exécute une `Get-Date` commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-175">The third command runs a `Get-Date` command.</span></span> <span data-ttu-id="ef3ae-176">Étant donné que les fonctions sont prioritaires sur les applets de commande, Windows PowerShell exécute la fonction importée `Get-Date` , qui retourne une date julienne.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-176">Because functions take precedence over cmdlets, Windows PowerShell runs the imported `Get-Date` function, which returns a Julian date.</span></span>

<span data-ttu-id="ef3ae-177">Les quatrième et cinquième commandes montrent comment utiliser un nom qualifié pour exécuter une commande qui est masquée par une commande importée.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-177">The fourth and fifth commands show how to use a qualified name to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="ef3ae-178">La quatrième commande récupère le nom du composant logiciel enfichable Windows PowerShell qui a ajouté l’applet de commande d’origine `Get-Date` à la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-178">The fourth command gets the name of the Windows PowerShell snap-in that added the original `Get-Date` cmdlet to the current session.</span></span>

<span data-ttu-id="ef3ae-179">La cinquième commande utilise le nom qualifié du composant logiciel enfichable de l' `Get-Date` applet de commande pour exécuter une `Get-Date` commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-179">The fifth command uses the snap-in-qualified name of the `Get-Date` cmdlet to run a `Get-Date` command.</span></span>

<span data-ttu-id="ef3ae-180">Pour plus d'informations sur la priorité des commandes et les commandes masquées, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ef3ae-180">For more information about command precedence and hidden commands, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="ef3ae-181">Exemple 8 : importer des commandes qui ont une chaîne spécifique dans leurs noms</span><span class="sxs-lookup"><span data-stu-id="ef3ae-181">Example 8: Import commands that have a specific string in their names</span></span>

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

<span data-ttu-id="ef3ae-182">Cette commande importe les commandes dont les noms incluent l’élément de la session PSSession dans `$S` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-182">This command imports commands whose names include Item from the PSSession in `$S`.</span></span> <span data-ttu-id="ef3ae-183">Étant donné que la commande comprend le paramètre **CommandName** mais pas le paramètre **FormatTypeData** , seule la commande est importée.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-183">Because the command includes the **CommandName** parameter but not the **FormatTypeData** parameter, only the command is imported.</span></span>

<span data-ttu-id="ef3ae-184">Utilisez cette commande lorsque vous utilisez `Import-PSSession` pour exécuter une commande sur un ordinateur distant et que vous avez déjà les données de mise en forme pour la commande dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-184">Use this command when you are using `Import-PSSession` to run a command on a remote computer and you already have the formatting data for the command in the current session.</span></span>

### <span data-ttu-id="ef3ae-185">Exemple 9 : utiliser le paramètre module pour détecter les commandes qui ont été importées dans la session</span><span class="sxs-lookup"><span data-stu-id="ef3ae-185">Example 9: Use the Module parameter to discover which commands were imported into the session</span></span>

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

<span data-ttu-id="ef3ae-186">Cette commande montre comment utiliser le paramètre **module** de `Get-Command` pour déterminer les commandes qui ont été importées dans la session par une `Import-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-186">This command shows how to use the **Module** parameter of `Get-Command` to find out which commands were imported into the session by an `Import-PSSession` command.</span></span>

<span data-ttu-id="ef3ae-187">La première commande utilise l' `Import-PSSession` applet de commande pour importer des commandes dont les noms incluent « bits » de la session PSSession dans la `$S` variable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-187">The first command uses the `Import-PSSession` cmdlet to import commands whose names include "bits" from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="ef3ae-188">La `Import-PSSession` commande retourne un module temporaire et la commande enregistre le module dans la `$m` variable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-188">The `Import-PSSession` command returns a temporary module, and the command saves the module in the `$m` variable.</span></span>

<span data-ttu-id="ef3ae-189">La deuxième commande utilise l' `Get-Command` applet de commande pour récupérer les commandes exportées par le module dans la `$M` variable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-189">The second command uses the `Get-Command` cmdlet to get the commands that are exported by the module in the `$M` variable.</span></span>

<span data-ttu-id="ef3ae-190">Le paramètre **Module** prend une valeur de chaîne, qui est conçue pour le nom du module.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-190">The **Module** parameter takes a string value, which is designed for the module name.</span></span> <span data-ttu-id="ef3ae-191">Toutefois, quand vous envoyez un objet de module, Windows PowerShell utilise la méthode **ToString** sur l'objet de module, qui retourne le nom du module.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-191">However, when you submit a module object, Windows PowerShell uses the **ToString** method on the module object, which returns the module name.</span></span>

<span data-ttu-id="ef3ae-192">La `Get-Command` commande est l’équivalent de `Get-Command $M.Name` «.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-192">The `Get-Command` command is the equivalent of `Get-Command $M.Name`".</span></span>

## <span data-ttu-id="ef3ae-193">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ef3ae-193">PARAMETERS</span></span>

### <span data-ttu-id="ef3ae-194">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="ef3ae-194">-AllowClobber</span></span>

<span data-ttu-id="ef3ae-195">Indique que cette applet de commande importe les commandes spécifiées, même si elles ont les mêmes noms que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-195">Indicates that this cmdlet imports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="ef3ae-196">Si vous importez une commande portant le même nom qu'une commande dans la session active, la commande importée masque ou remplace les commandes d'origine.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-196">If you import a command with the same name as a command in the current session, the imported command hides or replaces the original commands.</span></span> <span data-ttu-id="ef3ae-197">Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ef3ae-197">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="ef3ae-198">Par défaut, `Import-PSSession` n’importe pas les commandes qui portent le même nom que les commandes de la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-198">By default, `Import-PSSession` does not import commands that have the same name as commands in the current session.</span></span>

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

### <span data-ttu-id="ef3ae-199">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="ef3ae-199">-ArgumentList</span></span>

<span data-ttu-id="ef3ae-200">Spécifie un tableau de commandes qui résulte de l’utilisation des arguments spécifiés (valeurs de paramètre).</span><span class="sxs-lookup"><span data-stu-id="ef3ae-200">Specifies an array of commands that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="ef3ae-201">Par exemple, pour importer la variante de la `Get-Item` commande dans le certificat (CERT :) dans la session PSSession dans `$S` , tapez `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-201">For instance, to import the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef3ae-202">-Certificat</span><span class="sxs-lookup"><span data-stu-id="ef3ae-202">-Certificate</span></span>

<span data-ttu-id="ef3ae-203">Spécifie le certificat client utilisé pour signer les fichiers de format (\* .Format.ps1XML) ou les fichiers de module de script (. psm1) dans le module temporaire `Import-PSSession` créé par.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-203">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the temporary module that `Import-PSSession` creates.</span></span>

<span data-ttu-id="ef3ae-204">Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-204">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="ef3ae-205">Pour rechercher un certificat, utilisez l' `Get-PfxCertificate` applet de commande ou utilisez l' `Get-ChildItem` applet de commande dans le certificat (CERT :) unités.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-205">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="ef3ae-206">Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-206">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef3ae-207">-CommandName</span><span class="sxs-lookup"><span data-stu-id="ef3ae-207">-CommandName</span></span>

<span data-ttu-id="ef3ae-208">Spécifie les commandes avec les noms ou modèles de noms spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-208">Specifies commands with the specified names or name patterns.</span></span> <span data-ttu-id="ef3ae-209">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-209">Wildcards are permitted.</span></span> <span data-ttu-id="ef3ae-210">Utilisez **CommandName** ou son alias, **Name**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-210">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="ef3ae-211">Par défaut, `Import-PSSession` importe toutes les commandes de la session, à l’exception des commandes qui ont les mêmes noms que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-211">By default, `Import-PSSession` imports all commands from the session, except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="ef3ae-212">Cela empêche les commandes importées de masquer ou de remplacer des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-212">This prevents imported commands from hiding or replacing commands in the session.</span></span> <span data-ttu-id="ef3ae-213">Pour importer toutes les commandes, y compris celles qui masquent ou remplacent d'autres commandes, utilisez le paramètre **AllowClobber**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-213">To import all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="ef3ae-214">Si vous utilisez le paramètre **CommandName**, les fichiers de mise en forme pour les commandes ne sont pas importés, sauf si vous utilisez le paramètre **FormatTypeName**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-214">If you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="ef3ae-215">De même, si vous utilisez le paramètre **FormatTypeName**, aucune commande n'est importée, sauf si vous utilisez le paramètre **CommandName**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-215">Similarly, if you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef3ae-216">-CommandType</span><span class="sxs-lookup"><span data-stu-id="ef3ae-216">-CommandType</span></span>

<span data-ttu-id="ef3ae-217">Spécifie le type d’objets de commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-217">Specifies the type of command objects.</span></span> <span data-ttu-id="ef3ae-218">La valeur par défaut est Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-218">The default value is Cmdlet.</span></span> <span data-ttu-id="ef3ae-219">Utilisez **CommandType** ou son alias, **Type**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-219">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="ef3ae-220">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="ef3ae-220">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ef3ae-221">Affecté.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-221">Alias.</span></span> <span data-ttu-id="ef3ae-222">Alias Windows PowerShell dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-222">The Windows PowerShell aliases in the remote session.</span></span>
- <span data-ttu-id="ef3ae-223">Tout le monde.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-223">All.</span></span> <span data-ttu-id="ef3ae-224">Applets de commande et fonctions dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-224">The cmdlets and functions in the remote session.</span></span>
- <span data-ttu-id="ef3ae-225">console.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-225">Application.</span></span> <span data-ttu-id="ef3ae-226">Tous les fichiers autres que Windows-PowerShell fichiers dans les chemins d’accès qui sont répertoriés dans la variable d’environnement PATH ( `$env:path` ) dans la session à distance, y compris les fichiers. txt,. exe et. dll.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-226">All the files other than Windows-PowerShell files in the paths that are listed in the Path environment variable (`$env:path`) in the remote session, including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="ef3ae-227">PolicySchedule.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-227">Cmdlet.</span></span> <span data-ttu-id="ef3ae-228">Applets de commande dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-228">The cmdlets in the remote session.</span></span> <span data-ttu-id="ef3ae-229">« Cmdlet » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-229">"Cmdlet" is the default.</span></span>
- <span data-ttu-id="ef3ae-230">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-230">ExternalScript.</span></span> <span data-ttu-id="ef3ae-231">Fichiers. ps1 dans les chemins d’accès figurant dans la variable d’environnement PATH ( `$env:path` ) dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-231">The .ps1 files in the paths listed in the Path environment variable (`$env:path`) in the remote session.</span></span>
- <span data-ttu-id="ef3ae-232">Filtre et fonction.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-232">Filter and Function.</span></span> <span data-ttu-id="ef3ae-233">Fonctions Windows PowerShell dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-233">The Windows PowerShell functions in the remote session.</span></span>
- <span data-ttu-id="ef3ae-234">Script.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-234">Script.</span></span> <span data-ttu-id="ef3ae-235">Blocs de scripts dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-235">The script blocks in the remote session.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef3ae-236">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="ef3ae-236">-DisableNameChecking</span></span>

<span data-ttu-id="ef3ae-237">Indique que cette applet de commande supprime le message qui vous avertit lorsque vous importez une applet de commande ou une fonction dont le nom comprend un verbe non approuvé ou un caractère interdit.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-237">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="ef3ae-238">Par défaut, lorsqu’un module que vous importez exporte des applets de commande ou des fonctions qui ont des verbes non approuvés dans leurs noms, Windows PowerShell affiche le message d’avertissement suivant :</span><span class="sxs-lookup"><span data-stu-id="ef3ae-238">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, the Windows PowerShell displays the following warning message:</span></span>

<span data-ttu-id="ef3ae-239">"AVERTISSEMENT : certains noms de commandes importés incluent des verbes non approuvés qui peuvent les rendre moins détectables.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-239">"WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="ef3ae-240">Utilisez le paramètre Verbose pour plus d’informations ou tapez `Get-Verb` pour afficher la liste des verbes approuvés.»</span><span class="sxs-lookup"><span data-stu-id="ef3ae-240">Use the Verbose parameter for more detail or type `Get-Verb` to see the list of approved verbs."</span></span>

<span data-ttu-id="ef3ae-241">Ce message n'est qu'un avertissement.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-241">This message is only a warning.</span></span> <span data-ttu-id="ef3ae-242">Le module entier est toujours importé, y compris les commandes non conformes.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-242">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="ef3ae-243">Bien que le message soit affiché aux utilisateurs du module, le problème d'affectation de noms doit être corrigé par l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-243">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="ef3ae-244">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="ef3ae-244">-FormatTypeName</span></span>

<span data-ttu-id="ef3ae-245">Spécifie les instructions de mise en forme pour les types d’Microsoft .NET Framework spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-245">Specifies formatting instructions for the specified Microsoft .NET Framework types.</span></span>
<span data-ttu-id="ef3ae-246">Entrez les noms des types.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-246">Enter the type names.</span></span>
<span data-ttu-id="ef3ae-247">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-247">Wildcards are permitted.</span></span>

<span data-ttu-id="ef3ae-248">La valeur de ce paramètre doit être le nom d’un type retourné par une `Get-FormatData` commande dans la session à partir de laquelle les commandes sont importées.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-248">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="ef3ae-249">Pour récupérer toutes les données de mise en forme dans la session à distance, tapez `*` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-249">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="ef3ae-250">Si la commande n’inclut pas le paramètre **CommandName** ou **FormatTypeName** , `Import-PSSession` importe les instructions de mise en forme pour tous les types de .NET Framework retournés par une `Get-FormatData` commande dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-250">If the command does not include either the **CommandName** or **FormatTypeName** parameter, `Import-PSSession` imports formatting instructions for all .NET Framework types returned by a `Get-FormatData` command in the remote session.</span></span>

<span data-ttu-id="ef3ae-251">Si vous utilisez le paramètre **FormatTypeName**, aucune commande n'est importée, sauf si vous utilisez le paramètre **CommandName**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-251">If you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="ef3ae-252">De même, si vous utilisez le paramètre **CommandName**, les fichiers de mise en forme pour les commandes ne sont pas importés, sauf si vous utilisez le paramètre **FormatTypeName**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-252">Similarly, if you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef3ae-253">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="ef3ae-253">-FullyQualifiedModule</span></span>

<span data-ttu-id="ef3ae-254">Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** (décrits dans la section Notes du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) dans le kit de développement logiciel (SDK) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-254">Specifies modules with names that are specified in the form of **ModuleSpecification** objects (described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) in the PowerShell SDK.</span></span> <span data-ttu-id="ef3ae-255">Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié au format :</span><span class="sxs-lookup"><span data-stu-id="ef3ae-255">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

- <span data-ttu-id="ef3ae-256">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` ou</span><span class="sxs-lookup"><span data-stu-id="ef3ae-256">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` or</span></span>
- <span data-ttu-id="ef3ae-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span></span>

<span data-ttu-id="ef3ae-258">**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-258">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="ef3ae-259">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-259">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="ef3ae-260">Les deux paramètres s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-260">The two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef3ae-261">-Module</span><span class="sxs-lookup"><span data-stu-id="ef3ae-261">-Module</span></span>

<span data-ttu-id="ef3ae-262">Spécifie et tableau de commandes dans les modules et composants logiciels enfichables Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-262">Specifies and array of commands in the Windows PowerShell snap-ins and modules.</span></span> <span data-ttu-id="ef3ae-263">Entrez les noms de composant logiciel enfichable et de module.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-263">Enter the snap-in and module names.</span></span> <span data-ttu-id="ef3ae-264">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-264">Wildcards are not permitted.</span></span>

<span data-ttu-id="ef3ae-265">`Import-PSSession` Impossible d’importer des fournisseurs à partir d’un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-265">`Import-PSSession` cannot import providers from a snap-in.</span></span>

<span data-ttu-id="ef3ae-266">Pour plus d'informations, consultez [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) et [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="ef3ae-266">For more information, see [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) and [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef3ae-267">-Prefix</span><span class="sxs-lookup"><span data-stu-id="ef3ae-267">-Prefix</span></span>

<span data-ttu-id="ef3ae-268">Spécifie un préfixe pour les noms des commandes importées.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-268">Specifies a prefix to the nouns in the names of imported commands.</span></span>

<span data-ttu-id="ef3ae-269">Utilisez ce paramètre pour éviter les conflits de noms qui peuvent se produire quand des commandes différentes dans la session ont le même nom.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-269">Use this parameter to avoid name conflicts that might occur when different commands in the session have the same name.</span></span>

<span data-ttu-id="ef3ae-270">Par exemple, si vous spécifiez le préfixe Remote, puis importez une applet de commande `Get-Date` , l’applet de commande est connue dans la session en tant que `Get-RemoteDate` , et elle n’est pas confondue avec l’applet de commande d’origine `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-270">For instance, if you specify the prefix Remote and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-RemoteDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef3ae-271">-Session</span><span class="sxs-lookup"><span data-stu-id="ef3ae-271">-Session</span></span>

<span data-ttu-id="ef3ae-272">Spécifie la **session PSSession** à partir de laquelle les applets de commande sont importées.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-272">Specifies the **PSSession** from which the cmdlets are imported.</span></span> <span data-ttu-id="ef3ae-273">Entrez une variable qui contient un objet de session ou une commande qui obtient un objet de session, tel qu’une `New-PSSession` `Get-PSSession` commande ou.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-273">Enter a variable that contains a session object or a command that gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="ef3ae-274">Vous ne pouvez spécifier qu'une seule session.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-274">You can specify only one session.</span></span> <span data-ttu-id="ef3ae-275">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-275">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef3ae-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef3ae-276">CommonParameters</span></span>

<span data-ttu-id="ef3ae-277">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef3ae-278">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ef3ae-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef3ae-279">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ef3ae-279">INPUTS</span></span>

### <span data-ttu-id="ef3ae-280">None</span><span class="sxs-lookup"><span data-stu-id="ef3ae-280">None</span></span>

<span data-ttu-id="ef3ae-281">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-281">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="ef3ae-282">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ef3ae-282">OUTPUTS</span></span>

### <span data-ttu-id="ef3ae-283">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="ef3ae-283">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="ef3ae-284">`Import-PSSession` retourne le même objet de module que les `New-Module` applets de commande et `Get-Module` retournent.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-284">`Import-PSSession` returns the same module object that `New-Module` and `Get-Module` cmdlets return.</span></span>
<span data-ttu-id="ef3ae-285">Toutefois, le module importé est temporaire et existe uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-285">However, the imported module is temporary and exists only in the current session.</span></span> <span data-ttu-id="ef3ae-286">Pour créer un module permanent sur le disque, utilisez l’applet de commande `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-286">To create a permanent module on disk, use the `Export-PSSession` cmdlet.</span></span>

## <span data-ttu-id="ef3ae-287">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ef3ae-287">NOTES</span></span>

- <span data-ttu-id="ef3ae-288">`Import-PSSession` s’appuie sur l’infrastructure de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-288">`Import-PSSession` relies on the  PowerShell remoting infrastructure.</span></span> <span data-ttu-id="ef3ae-289">Pour utiliser cette applet de commande, l'ordinateur doit être configuré pour la communication à distance WS-Management.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-289">To use this cmdlet, the computer must be configured for WS-Management remoting.</span></span> <span data-ttu-id="ef3ae-290">Pour plus d’informations, consultez [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) et [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef3ae-290">For more information, see [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) and [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="ef3ae-291">`Import-PSSession` n’importe pas les variables ou les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-291">`Import-PSSession` does not import variables or  PowerShell providers.</span></span>
- <span data-ttu-id="ef3ae-292">Quand vous importez des commandes qui ont le même nom que les commandes dans la session active, les commandes importées peuvent masquer des alias, des fonctions et des applets de commande dans la session, et peuvent remplacer des fonctions et variables dans la session.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-292">When you import commands that have the same names as commands in the current session, the imported commands can hide aliases, functions, and cmdlets in the session and they can replace functions and variables in the session.</span></span> <span data-ttu-id="ef3ae-293">Pour éviter les conflits de noms, utilisez le paramètre **Prefix**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-293">To prevent name conflicts, use the **Prefix** parameter.</span></span> <span data-ttu-id="ef3ae-294">Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ef3ae-294">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="ef3ae-295">`Import-PSSession` convertit toutes les commandes en fonctions avant de les importer.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-295">`Import-PSSession` converts all commands into functions before it imports them.</span></span> <span data-ttu-id="ef3ae-296">Par conséquent, les commandes importées se comportent un peu différemment que si elles avaient conservé leur type de commande d'origine.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-296">As a result, imported commands behave a bit differently than they would if they retained their original command type.</span></span> <span data-ttu-id="ef3ae-297">Par exemple, si vous importez une applet de commande à partir d'une session PSSession, puis une applet de commande avec le même nom à partir d'un module ou d'un composant logiciel enfichable, l'applet de commande qui est importée à partir de la session PSSession s'exécute toujours par défaut, car les fonctions sont prioritaires sur les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-297">For example, if you import a cmdlet from a PSSession and then import a cmdlet with the same name from a module or snap-in, the cmdlet that is imported from the PSSession always runs by default because functions take precedence over cmdlets.</span></span> <span data-ttu-id="ef3ae-298">À l'inverse, si vous importez un alias dans une session qui a un alias avec le même nom, l'alias d'origine est toujours utilisé, car les alias sont prioritaires sur les fonctions.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-298">Conversely, if you import an alias into a session that has an alias with the same name, the original alias is always used, because aliases take precedence over functions.</span></span> <span data-ttu-id="ef3ae-299">Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ef3ae-299">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="ef3ae-300">`Import-PSSession` utilise l' `Write-Progress` applet de commande pour afficher la progression de la commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-300">`Import-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="ef3ae-301">Vous pouvez voir la barre de progression pendant l'exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-301">You might see the progress bar while the command is running.</span></span>
- <span data-ttu-id="ef3ae-302">Pour rechercher les commandes à importer, `Import-PSSession` utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-Command` commande dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-302">To find the commands to import, `Import-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="ef3ae-303">Pour obtenir des données de mise en forme pour les commandes, elle utilise l’applet de commande `Get-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-303">To get formatting data for the commands, it uses the `Get-FormatData` cmdlet.</span></span> <span data-ttu-id="ef3ae-304">Vous pouvez voir des messages d’erreur de ces applets de commande lorsque vous exécutez une `Import-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-304">You might see error messages from these cmdlets when you run an `Import-PSSession` command.</span></span> <span data-ttu-id="ef3ae-305">En outre, `Import-PSSession` ne peut pas importer de commandes à partir d’une session PSSession qui n’inclut pas les `Get-Command` applets de commande, `Get-FormatData` , `Select-Object` et `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-305">Also, `Import-PSSession` cannot import commands from a PSSession that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>
- <span data-ttu-id="ef3ae-306">Les commandes importées présentent les mêmes restrictions que d'autres commandes à distance, notamment l'impossibilité de démarrer un programme avec une interface utilisateur, tel que le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-306">Imported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>
- <span data-ttu-id="ef3ae-307">Étant donné que les profils Windows PowerShell ne sont pas exécutés dans sessions PSSession, les commandes qu’un profil ajoute à une session ne sont pas disponibles pour `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="ef3ae-307">Because Windows PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Import-PSSession`.</span></span> <span data-ttu-id="ef3ae-308">Pour importer des commandes à partir d’un profil, utilisez une `Invoke-Command` commande pour exécuter le profil dans la session PSSession manuellement avant d’importer des commandes.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-308">To import commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before importing commands.</span></span>
- <span data-ttu-id="ef3ae-309">Le module temporaire que `Import-PSSession` crée peut inclure un fichier de mise en forme, même si la commande n’importe pas de données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-309">The temporary module that `Import-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="ef3ae-310">Si la commande n'importe pas de données de mise en forme, les fichiers de mise en forme éventuellement créés ne contiennent pas de données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-310">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>
- <span data-ttu-id="ef3ae-311">Pour utiliser `Import-PSSession` , la stratégie d’exécution dans la session active ne peut pas être restreinte ou AllSigned, car le module temporaire qui `Import-PSSession` crée contient des fichiers de script non signés interdits par ces stratégies.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-311">To use `Import-PSSession`, the execution policy in the current session cannot be Restricted or AllSigned, because the temporary module that `Import-PSSession` creates contains unsigned script files that are prohibited by these policies.</span></span> <span data-ttu-id="ef3ae-312">Pour utiliser `Import-PSSession` sans modifier la stratégie d’exécution de l’ordinateur local, utilisez le paramètre **scope** de `Set-ExecutionPolicy` pour définir une stratégie d’exécution moins restrictive pour un seul processus.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-312">To use `Import-PSSession` without changing the execution policy for the local computer, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>
- <span data-ttu-id="ef3ae-313">Dans Windows PowerShell 2.0, les rubriques d'aide pour les commandes qui sont importées à partir d'une autre session n'incluent pas le préfixe que vous attribuez à l'aide du paramètre **Prefix**.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-313">In Windows PowerShell 2.0, help topics for commands that are imported from another session do not include the prefix that you assign by using the **Prefix** parameter.</span></span> <span data-ttu-id="ef3ae-314">Pour obtenir de l'aide pour une commande importée dans Windows PowerShell 2.0, utilisez le nom de commande (sans préfixe) d'origine.</span><span class="sxs-lookup"><span data-stu-id="ef3ae-314">To get help for an imported command in Windows PowerShell 2.0, use the original (non-prefixed) command name.</span></span>

## <span data-ttu-id="ef3ae-315">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ef3ae-315">RELATED LINKS</span></span>

[<span data-ttu-id="ef3ae-316">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef3ae-316">Export-PSSession</span></span>](Export-PSSession.md)
