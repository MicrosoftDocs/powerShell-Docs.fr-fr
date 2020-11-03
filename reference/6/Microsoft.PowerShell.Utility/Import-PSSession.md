---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: ef5bf676e261e7a4267980a3e87753724ca9bf42
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203773"
---
# <span data-ttu-id="7a17d-103">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="7a17d-103">Import-PSSession</span></span>

## <span data-ttu-id="7a17d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7a17d-104">SYNOPSIS</span></span>
<span data-ttu-id="7a17d-105">Importe des commandes à partir d'une autre session dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-105">Imports commands from another session into the current session.</span></span>

## <span data-ttu-id="7a17d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7a17d-106">SYNTAX</span></span>

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## <span data-ttu-id="7a17d-107">Description</span><span class="sxs-lookup"><span data-stu-id="7a17d-107">DESCRIPTION</span></span>

<span data-ttu-id="7a17d-108">L’applet de commande **Import-PSSession** importe des commandes, telles que des applets de commande, des fonctions et des alias, à partir d’une session PSSession sur un ordinateur local ou distant dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-108">The **Import-PSSession** cmdlet imports commands , such as cmdlets, functions, and aliases, from a PSSession on a local or remote computer into the current session.</span></span>
<span data-ttu-id="7a17d-109">Vous pouvez importer n’importe quelle commande que l’applet de commande Get-Command peut trouver dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7a17d-109">You can import any command that the Get-Command cmdlet can find in the PSSession.</span></span>

<span data-ttu-id="7a17d-110">Utilisez une commande **Import-PSSession** pour importer des commandes à partir d’un shell personnalisé, tel qu’un shell Microsoft Exchange Server, ou à partir d’une session qui comprend des modules et des composants logiciels enfichables PowerShell ou d’autres éléments qui ne sont pas dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-110">Use an **Import-PSSession** command to import commands from a customized shell, such as a Microsoft Exchange Server shell, or from a session that includes PowerShell modules and snap-ins or other elements that are not in the current session.</span></span>

<span data-ttu-id="7a17d-111">Pour importer des commandes, utilisez d’abord l’applet de commande New-PSSession pour créer une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7a17d-111">To import commands, first use the New-PSSession cmdlet to create a PSSession.</span></span>
<span data-ttu-id="7a17d-112">Utilisez ensuite l'applet de commande **Import-PSSession** pour importer les commandes.</span><span class="sxs-lookup"><span data-stu-id="7a17d-112">Then, use the **Import-PSSession** cmdlet to import the commands.</span></span>
<span data-ttu-id="7a17d-113">Par défaut, **Import-PSSession** importe toutes les commandes à l'exception de celles qui ont le même nom que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-113">By default, **Import-PSSession** imports all commands except for commands that have the same names as commands in the current session.</span></span>
<span data-ttu-id="7a17d-114">Pour importer toutes les commandes, utilisez le paramètre *AllowClobber* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-114">To import all the commands, use the *AllowClobber* parameter.</span></span>

<span data-ttu-id="7a17d-115">Vous pouvez utiliser des commandes importées comme vous utiliseriez n'importe quelle commande de la session.</span><span class="sxs-lookup"><span data-stu-id="7a17d-115">You can use imported commands just as you would use any command in the session.</span></span>
<span data-ttu-id="7a17d-116">Quand vous utilisez une commande importée, la partie importée de la commande s'exécute implicitement dans la session à partir de laquelle elle a été importée.</span><span class="sxs-lookup"><span data-stu-id="7a17d-116">When you use an imported command, the imported part of the command runs implicitly in the session from which it was imported.</span></span>
<span data-ttu-id="7a17d-117">Toutefois, les opérations à distance sont gérées entièrement par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a17d-117">However, the remote operations are handled entirely by PowerShell.</span></span>
<span data-ttu-id="7a17d-118">Vous ne devez même pas vous en rendre compte, sauf que vous devez conserver la connexion à l'autre session (PSSession) ouverte.</span><span class="sxs-lookup"><span data-stu-id="7a17d-118">You need not even be aware of them, except that you must keep the connection to the other session (PSSession) open.</span></span>
<span data-ttu-id="7a17d-119">Si vous la fermez, les commandes importées ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="7a17d-119">If you close it, the imported commands are no longer available.</span></span>

<span data-ttu-id="7a17d-120">Comme l'exécution des commandes importées peut prendre plus de temps que celle des commandes locales, **Import-PSSession** ajoute un paramètre *AsJob* à chaque commande importée.</span><span class="sxs-lookup"><span data-stu-id="7a17d-120">Because imported commands might take longer to run than local commands, **Import-PSSession** adds an *AsJob* parameter to every imported command.</span></span>
<span data-ttu-id="7a17d-121">Ce paramètre vous permet d’exécuter la commande en tant que tâche en arrière-plan PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a17d-121">This parameter allows you to run the command as a PowerShell background job.</span></span>
<span data-ttu-id="7a17d-122">Pour plus d'informations, consultez about_Jobs.</span><span class="sxs-lookup"><span data-stu-id="7a17d-122">For more information, see about_Jobs.</span></span>

<span data-ttu-id="7a17d-123">Quand vous utilisez **Import-PSSession** , PowerShell ajoute les commandes importées à un module temporaire qui existe uniquement dans votre session et retourne un objet qui représente le module.</span><span class="sxs-lookup"><span data-stu-id="7a17d-123">When you use **Import-PSSession** , PowerShell adds the imported commands to a temporary module that exists only in your session and returns an object that represents the module.</span></span>
<span data-ttu-id="7a17d-124">Pour créer un module permanent que vous pouvez utiliser dans les sessions ultérieures, utilisez l’applet de commande Export-PSSession.</span><span class="sxs-lookup"><span data-stu-id="7a17d-124">To create a persistent module that you can use in future sessions, use the Export-PSSession cmdlet.</span></span>

<span data-ttu-id="7a17d-125">L’applet de commande **Import-PSSession** utilise la fonctionnalité de communication à distance implicite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a17d-125">The **Import-PSSession** cmdlet uses the implicit remoting feature of PowerShell.</span></span>
<span data-ttu-id="7a17d-126">Lorsque vous importez des commandes dans la session active, elles s’exécutent implicitement dans la session d’origine ou dans une session similaire sur l’ordinateur d’origine.</span><span class="sxs-lookup"><span data-stu-id="7a17d-126">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

<span data-ttu-id="7a17d-127">À compter de Windows PowerShell 3,0, vous pouvez utiliser l’applet de commande Import-Module pour importer des modules à partir d’une session à distance dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-127">Beginning in Windows PowerShell 3.0, you can use the Import-Module cmdlet to import modules from a remote session into the current session.</span></span>
<span data-ttu-id="7a17d-128">Cette fonctionnalité utilise la communication à distance implicite.</span><span class="sxs-lookup"><span data-stu-id="7a17d-128">This feature uses implicit remoting.</span></span>
<span data-ttu-id="7a17d-129">Elle revient à utiliser **Import-PSSession** pour importer les modules sélectionnés à partir d'une session à distance dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-129">It is equivalent to using **Import-PSSession** to import selected modules from a remote session into the current session.</span></span>

## <span data-ttu-id="7a17d-130">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="7a17d-130">EXAMPLES</span></span>

### <span data-ttu-id="7a17d-131">Exemple 1 : importer toutes les commandes à partir d’une session PSSession</span><span class="sxs-lookup"><span data-stu-id="7a17d-131">Example 1: Import all commands from a PSSession</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

<span data-ttu-id="7a17d-132">Cette commande importe toutes les commandes d'une session PSSession sur l'ordinateur Server01 dans la session active, à l'exception des commandes qui ont le même nom que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-132">This command imports all commands from a PSSession on the Server01 computer into the current session, except for commands that have the same names as commands in the current session.</span></span>

<span data-ttu-id="7a17d-133">Comme cette commande n'utilise pas le paramètre *CommandName* , elle importe également toutes les données de mise en forme requises pour les commandes importées.</span><span class="sxs-lookup"><span data-stu-id="7a17d-133">Because this command does not use the *CommandName* parameter, it also imports all of the formatting data required for the imported commands.</span></span>

### <span data-ttu-id="7a17d-134">Exemple 2 : importer des commandes qui se terminent par une chaîne spécifique</span><span class="sxs-lookup"><span data-stu-id="7a17d-134">Example 2: Import commands that end with a specific string</span></span>

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

<span data-ttu-id="7a17d-135">Ces commandes importent les commandes dont les noms se terminent par « -test » à partir d'une session PSSession dans la session locale, puis indiquent comment utiliser une applet de commande importée.</span><span class="sxs-lookup"><span data-stu-id="7a17d-135">These commands import the commands with names that end in "-test" from a PSSession into the local session, and then they show how to use an imported cmdlet.</span></span>

<span data-ttu-id="7a17d-136">La première commande utilise l’applet de commande New-PSSession pour créer une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7a17d-136">The first command uses the New-PSSession cmdlet to create a PSSession.</span></span>
<span data-ttu-id="7a17d-137">Elle enregistre la session PSSession dans la variable $S.</span><span class="sxs-lookup"><span data-stu-id="7a17d-137">It saves the PSSession in the $S variable.</span></span>

<span data-ttu-id="7a17d-138">La deuxième commande utilise l’applet de commande **Import-PSSession** pour importer des commandes à partir de la session pssession dans $S dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-138">The second command uses the **Import-PSSession** cmdlet to import commands from the PSSession in $S into the current session.</span></span>
<span data-ttu-id="7a17d-139">Elle utilise le paramètre *CommandName* pour spécifier des commandes avec le nom Test et le paramètre *FormatTypeName* pour importer les données de mise en forme pour les commandes Test.</span><span class="sxs-lookup"><span data-stu-id="7a17d-139">It uses the *CommandName* parameter to specify commands with the Test noun and the *FormatTypeName* parameter to import the formatting data for the Test commands.</span></span>

<span data-ttu-id="7a17d-140">Les troisième et quatrième commandes utilisent les commandes importées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-140">The third and fourth commands use the imported commands in the current session.</span></span>
<span data-ttu-id="7a17d-141">Comme les commandes importées sont en réalité ajoutées à la session active, vous utilisez la syntaxe locale pour les exécuter.</span><span class="sxs-lookup"><span data-stu-id="7a17d-141">Because imported commands are actually added to the current session, you use the local syntax to run them.</span></span>
<span data-ttu-id="7a17d-142">Vous n’avez pas besoin d’utiliser l’applet de commande Invoke-Command pour exécuter une commande importée.</span><span class="sxs-lookup"><span data-stu-id="7a17d-142">You do not need to use the Invoke-Command cmdlet to run an imported command.</span></span>

### <span data-ttu-id="7a17d-143">Exemple 3 : importer des applets de commande à partir d’une session PSSession</span><span class="sxs-lookup"><span data-stu-id="7a17d-143">Example 3: Import cmdlets from a PSSession</span></span>

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

<span data-ttu-id="7a17d-144">Cet exemple montre que vous pouvez utiliser les applets de commande importées comme vous utiliseriez des applets de commande locales.</span><span class="sxs-lookup"><span data-stu-id="7a17d-144">This example shows that you can use imported cmdlets just as you would use local cmdlets.</span></span>

<span data-ttu-id="7a17d-145">Ces commandes importent les applets de commande New-Test et Get-Test à partir d'une session PSSession sur l'ordinateur Server01 et l'applet de commande Set-Test à partir d'une session PSSession sur l'ordinateur Server02.</span><span class="sxs-lookup"><span data-stu-id="7a17d-145">These commands import the New-Test and Get-Test cmdlets from a PSSession on the Server01 computer and the Set-Test cmdlet from a PSSession on the Server02 computer.</span></span>

<span data-ttu-id="7a17d-146">Même si les applets de commande ont été importées à partir de différentes sessions PSSession, vous pouvez diriger un objet d'une applet de commande vers une autre sans erreur.</span><span class="sxs-lookup"><span data-stu-id="7a17d-146">Even though the cmdlets were imported from different PSSessions, you can pipe an object from one cmdlet to another without error.</span></span>

### <span data-ttu-id="7a17d-147">Exemple 4 : exécuter une commande importée en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="7a17d-147">Example 4: Run an imported command as a background job</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

<span data-ttu-id="7a17d-148">Cet exemple montre comment exécuter une commande importée en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7a17d-148">This example shows how to run an imported command as a background job.</span></span>

<span data-ttu-id="7a17d-149">Comme l'exécution des commandes importées peut prendre plus de temps que celle des commandes locales, **Import-PSSession** ajoute un paramètre *AsJob* à chaque commande importée.</span><span class="sxs-lookup"><span data-stu-id="7a17d-149">Because imported commands might take longer to run than local commands, **Import-PSSession** adds an *AsJob* parameter to every imported command.</span></span>
<span data-ttu-id="7a17d-150">Le paramètre *AsJob* vous permet d'exécuter la commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7a17d-150">The *AsJob* parameter lets you run the command as a background job.</span></span>

<span data-ttu-id="7a17d-151">La première commande crée une session PSSession sur l’ordinateur SERVEUR01 et enregistre l’objet PSSession dans la variable $S.</span><span class="sxs-lookup"><span data-stu-id="7a17d-151">The first command creates a PSSession on the Server01 computer and saves the PSSession object in the $S variable.</span></span>

<span data-ttu-id="7a17d-152">La deuxième commande utilise **Import-PSSession** pour importer les applets de commande de test de la session pssession dans $S dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-152">The second command uses **Import-PSSession** to import the Test cmdlets from the PSSession in $S into the current session.</span></span>

<span data-ttu-id="7a17d-153">La troisième commande utilise le paramètre *AsJob* de l'applet de commande New-Test importée pour exécuter une commande New-Test en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7a17d-153">The third command uses the *AsJob* parameter of the imported New-Test cmdlet to run a New-Test command as a background job.</span></span>
<span data-ttu-id="7a17d-154">La commande enregistre l'objet de tâche retourné par New-Test dans la variable $batch.</span><span class="sxs-lookup"><span data-stu-id="7a17d-154">The command saves the job object that New-Test returns in the $batch variable.</span></span>

<span data-ttu-id="7a17d-155">La quatrième commande utilise l’applet de commande Receive-Job pour obtenir les résultats de la tâche dans la variable $batch.</span><span class="sxs-lookup"><span data-stu-id="7a17d-155">The fourth command uses the Receive-Job cmdlet to get the results of the job in the $batch variable.</span></span>

### <span data-ttu-id="7a17d-156">Exemple 5 : importer des applets de commande et des fonctions à partir d’un module PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a17d-156">Example 5: Import cmdlets and functions from a PowerShell module</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

<span data-ttu-id="7a17d-157">Cet exemple montre comment importer les applets de commande et les fonctions à partir d’un module PowerShell sur un ordinateur distant dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-157">This example shows how to import the cmdlets and functions from a PowerShell module on a remote computer into the current session.</span></span>

<span data-ttu-id="7a17d-158">La première commande crée une session PSSession sur l’ordinateur SERVEUR01 et l’enregistre dans la variable $S.</span><span class="sxs-lookup"><span data-stu-id="7a17d-158">The first command creates a PSSession on the Server01 computer and saves it in the $S variable.</span></span>

<span data-ttu-id="7a17d-159">La deuxième commande utilise l’applet de commande **Invoke-Command** pour exécuter une commande Import-Module dans la session PSSession dans $S.</span><span class="sxs-lookup"><span data-stu-id="7a17d-159">The second command uses the **Invoke-Command** cmdlet to run an Import-Module command in the PSSession in $S.</span></span>

<span data-ttu-id="7a17d-160">En règle générale, le module est ajouté à toutes les sessions par une commande **import-module** dans un profil PowerShell, mais les profils ne sont pas exécutés dans sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="7a17d-160">Typically, the module would be added to all sessions by an **Import-Module** command in a PowerShell profile, but profiles are not run in PSSessions.</span></span>

<span data-ttu-id="7a17d-161">La troisième commande utilise le paramètre *module*  d' **Import-PSSession** pour importer les applets de commande et les fonctions du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-161">The third command uses the *Module*  parameter of **Import-PSSession** to import the cmdlets and functions in the module into the current session.</span></span>

### <span data-ttu-id="7a17d-162">Exemple 6 : créer un module dans un fichier temporaire</span><span class="sxs-lookup"><span data-stu-id="7a17d-162">Example 6: Create a module in a temporary file</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="7a17d-163">Cet exemple montre que **Import-PSSession** crée un module dans un fichier temporaire sur le disque.</span><span class="sxs-lookup"><span data-stu-id="7a17d-163">This example shows that **Import-PSSession** creates a module in a temporary file on disk.</span></span>
<span data-ttu-id="7a17d-164">Il montre également que toutes les commandes sont converties en fonctions avant leur importation dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-164">It also shows that all commands are converted into functions before they are imported into the current session.</span></span>

<span data-ttu-id="7a17d-165">La commande utilise l’applet de commande **Import-PSSession** pour importer une applet de commande Get-Date et une fonction SearchHelp dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-165">The command uses the **Import-PSSession** cmdlet to import a Get-Date cmdlet and a SearchHelp function into the current session.</span></span>

<span data-ttu-id="7a17d-166">L'applet de commande **Import-PSSession** retourne un objet **PSModuleInfo** qui représente le module temporaire.</span><span class="sxs-lookup"><span data-stu-id="7a17d-166">The **Import-PSSession** cmdlet returns a **PSModuleInfo** object that represents the temporary module.</span></span>
<span data-ttu-id="7a17d-167">La valeur de la propriété **Path** montre que **Import-PSSession** a créé un fichier de module de script (.psm1) à un emplacement temporaire.</span><span class="sxs-lookup"><span data-stu-id="7a17d-167">The value of the **Path** property shows that **Import-PSSession** created a script module (.psm1) file in a temporary location.</span></span>
<span data-ttu-id="7a17d-168">La propriété **ExportedFunctions** montre que l'applet de commande **Get-Date** et la fonction SearchHelp ont toutes deux été importées en tant que fonctions.</span><span class="sxs-lookup"><span data-stu-id="7a17d-168">The **ExportedFunctions** property shows that the **Get-Date** cmdlet and the SearchHelp function were both imported as functions.</span></span>

### <span data-ttu-id="7a17d-169">Exemple 7 : exécuter une commande qui est masquée par une commande importée</span><span class="sxs-lookup"><span data-stu-id="7a17d-169">Example 7: Run a command that is hidden by an imported command</span></span>

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

<span data-ttu-id="7a17d-170">Cet exemple montre comment exécuter une commande qui est masquée par une commande importée.</span><span class="sxs-lookup"><span data-stu-id="7a17d-170">This example shows how to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="7a17d-171">La première commande importe une applet de commande Get-Date à partir de la session PSSession dans la variable $S.</span><span class="sxs-lookup"><span data-stu-id="7a17d-171">The first command imports a Get-Date cmdlet from the PSSession in the $S variable.</span></span>
<span data-ttu-id="7a17d-172">Comme la session active inclut une applet de commande **Get-Date** , le paramètre *AllowClobber* est requis dans la commande.</span><span class="sxs-lookup"><span data-stu-id="7a17d-172">Because the current session includes a **Get-Date** cmdlet, the *AllowClobber* parameter is required in the command.</span></span>

<span data-ttu-id="7a17d-173">La deuxième commande utilise le paramètre **All** de l’applet de commande Get-Command pour récupérer toutes les commandes d' **extraction** de la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-173">The second command uses the **All** parameter of the Get-Command cmdlet to get all **Get-Date** commands in the current session.</span></span>
<span data-ttu-id="7a17d-174">La sortie indique que la session inclut l'applet de commande **Get-Date** d'origine et une fonction **Get-Date** .</span><span class="sxs-lookup"><span data-stu-id="7a17d-174">The output shows that the session includes the original **Get-Date** cmdlet and a **Get-Date** function.</span></span>
<span data-ttu-id="7a17d-175">La fonction de **récupération** exécute l’applet de commande **« obtient-date »** importée dans la session PSSession dans $S.</span><span class="sxs-lookup"><span data-stu-id="7a17d-175">The **Get-Date** function runs the imported **Get-Date** cmdlet in the PSSession in $S.</span></span>

<span data-ttu-id="7a17d-176">La troisième commande exécute une commande **Get-Date** .</span><span class="sxs-lookup"><span data-stu-id="7a17d-176">The third command runs a **Get-Date** command.</span></span>
<span data-ttu-id="7a17d-177">Étant donné que les fonctions sont prioritaires sur les applets de commande, PowerShell exécute la fonction d' **extraction de date** , qui retourne une date julienne.</span><span class="sxs-lookup"><span data-stu-id="7a17d-177">Because functions take precedence over cmdlets, PowerShell runs the imported **Get-Date** function, which returns a Julian date.</span></span>

<span data-ttu-id="7a17d-178">Les quatrième et cinquième commandes montrent comment utiliser un nom qualifié pour exécuter une commande qui est masquée par une commande importée.</span><span class="sxs-lookup"><span data-stu-id="7a17d-178">The fourth and fifth commands show how to use a qualified name to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="7a17d-179">La quatrième commande obtient le nom du composant logiciel enfichable PowerShell qui a ajouté l’applet de commande de l’extension de **Date** d’origine à la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-179">The fourth command gets the name of the PowerShell snap-in that added the original **Get-Date** cmdlet to the current session.</span></span>

<span data-ttu-id="7a17d-180">La cinquième commande utilise le nom qualifié du composant logiciel enfichable de l'applet de commande **Get-Date** pour exécuter une commande **Get-Date** .</span><span class="sxs-lookup"><span data-stu-id="7a17d-180">The fifth command uses the snap-in-qualified name of the **Get-Date** cmdlet to run a **Get-Date** command.</span></span>

<span data-ttu-id="7a17d-181">Pour plus d'informations sur la priorité des commandes et les commandes masquées, consultez about_Command_Precedence.</span><span class="sxs-lookup"><span data-stu-id="7a17d-181">For more information about command precedence and hidden commands, see about_Command_Precedence.</span></span>

### <span data-ttu-id="7a17d-182">Exemple 8 : importer des commandes qui ont une chaîne spécifique dans leurs noms</span><span class="sxs-lookup"><span data-stu-id="7a17d-182">Example 8: Import commands that have a specific string in their names</span></span>

```
PS C:\> Import-PSSession -Session $S -CommandName *Item* -AllowClobber
```

<span data-ttu-id="7a17d-183">Cette commande importe les commandes dont les noms incluent l’élément de la session PSSession dans $S.</span><span class="sxs-lookup"><span data-stu-id="7a17d-183">This command imports commands whose names include Item from the PSSession in $S.</span></span>
<span data-ttu-id="7a17d-184">Étant donné que la commande comprend le paramètre *CommandName* mais pas le paramètre *FormatTypeData* , seule la commande est importée.</span><span class="sxs-lookup"><span data-stu-id="7a17d-184">Because the command includes the *CommandName* parameter but not the *FormatTypeData* parameter, only the command is imported.</span></span>

<span data-ttu-id="7a17d-185">Utilisez cette commande quand vous utilisez **Import-PSSession** pour exécuter une commande sur un ordinateur distant et que vous avez déjà les données de mise en forme pour la commande dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-185">Use this command when you are using **Import-PSSession** to run a command on a remote computer and you already have the formatting data for the command in the current session.</span></span>

### <span data-ttu-id="7a17d-186">Exemple 9 : utiliser le paramètre module pour détecter les commandes qui ont été importées dans la session</span><span class="sxs-lookup"><span data-stu-id="7a17d-186">Example 9: Use the Module parameter to discover which commands were imported into the session</span></span>

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

<span data-ttu-id="7a17d-187">Cette commande montre comment utiliser le paramètre *module* de la **commande « obtenir-Command »** pour déterminer les commandes qui ont été importées dans la session par une commande **Import-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="7a17d-187">This command shows how to use the *Module* parameter of **Get-Command** to find out which commands were imported into the session by an **Import-PSSession** command.</span></span>

<span data-ttu-id="7a17d-188">La première commande utilise l’applet de commande **Import-PSSession** pour importer des commandes dont les noms incluent « bits » de la session PSSession dans la variable $S.</span><span class="sxs-lookup"><span data-stu-id="7a17d-188">The first command uses the **Import-PSSession** cmdlet to import commands whose names include "bits" from the PSSession in the $S variable.</span></span>
<span data-ttu-id="7a17d-189">La commande **Import-PSSession** retourne un module temporaire et la commande enregistre le module dans la variable $m.</span><span class="sxs-lookup"><span data-stu-id="7a17d-189">The **Import-PSSession** command returns a temporary module, and the command saves the module in the $m variable.</span></span>

<span data-ttu-id="7a17d-190">La deuxième commande utilise l’applet de commande Get-Command pour récupérer les commandes exportées par le module dans la variable $M.</span><span class="sxs-lookup"><span data-stu-id="7a17d-190">The second command uses the Get-Command cmdlet to get the commands that are exported by the module in the $M variable.</span></span>

<span data-ttu-id="7a17d-191">Le paramètre *Module* prend une valeur de chaîne, qui est conçue pour le nom du module.</span><span class="sxs-lookup"><span data-stu-id="7a17d-191">The *Module* parameter takes a string value, which is designed for the module name.</span></span>
<span data-ttu-id="7a17d-192">Toutefois, lorsque vous envoyez un objet de module, PowerShell utilise la méthode **ToString** sur l’objet de module, qui retourne le nom du module.</span><span class="sxs-lookup"><span data-stu-id="7a17d-192">However, when you submit a module object, PowerShell uses the **ToString** method on the module object, which returns the module name.</span></span>

<span data-ttu-id="7a17d-193">La commande d' **extraction de commande** est l’équivalent de `Get-Command $M.Name` «.</span><span class="sxs-lookup"><span data-stu-id="7a17d-193">The **Get-Command** command is the equivalent of `Get-Command $M.Name`".</span></span>

## <span data-ttu-id="7a17d-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7a17d-194">PARAMETERS</span></span>

### <span data-ttu-id="7a17d-195">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="7a17d-195">-AllowClobber</span></span>

<span data-ttu-id="7a17d-196">Indique que cette applet de commande importe les commandes spécifiées, même si elles ont les mêmes noms que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-196">Indicates that this cmdlet imports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="7a17d-197">Si vous importez une commande portant le même nom qu'une commande dans la session active, la commande importée masque ou remplace les commandes d'origine.</span><span class="sxs-lookup"><span data-stu-id="7a17d-197">If you import a command with the same name as a command in the current session, the imported command hides or replaces the original commands.</span></span>
<span data-ttu-id="7a17d-198">Pour plus d'informations, consultez about_Command_Precedence.</span><span class="sxs-lookup"><span data-stu-id="7a17d-198">For more information, see about_Command_Precedence.</span></span>

<span data-ttu-id="7a17d-199">Par défaut, **Import-PSSession** n'importe pas les commandes qui ont le même nom que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-199">By default, **Import-PSSession** does not import commands that have the same name as commands in the current session.</span></span>

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

### <span data-ttu-id="7a17d-200">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="7a17d-200">-ArgumentList</span></span>

<span data-ttu-id="7a17d-201">Spécifie un tableau de commandes qui résulte de l’utilisation des arguments spécifiés (valeurs de paramètre).</span><span class="sxs-lookup"><span data-stu-id="7a17d-201">Specifies an array of commands that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="7a17d-202">Par exemple, pour importer la variante de la commande Get-Item dans le certificat (CERT :) dans la session PSSession dans $S, tapez `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .</span><span class="sxs-lookup"><span data-stu-id="7a17d-202">For instance, to import the variant of the Get-Item command in the certificate (Cert:) drive in the PSSession in $S, type `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

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

### <span data-ttu-id="7a17d-203">-Certificat</span><span class="sxs-lookup"><span data-stu-id="7a17d-203">-Certificate</span></span>

<span data-ttu-id="7a17d-204">Spécifie le certificat client qui est utilisé pour signer les fichiers de format (\*.Format.ps1xml) ou fichiers de module de script (.psm1) dans le module temporaire créé par **Import-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="7a17d-204">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the temporary module that **Import-PSSession** creates.</span></span>

<span data-ttu-id="7a17d-205">Entrez une variable qui contient un certificat, ou bien une commande ou une expression qui obtient le certificat.</span><span class="sxs-lookup"><span data-stu-id="7a17d-205">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="7a17d-206">Pour rechercher un certificat, utilisez l’applet de commande Get-PfxCertificate ou utilisez l’applet de commande Get-ChildItem dans le certificat (CERT :) unités.</span><span class="sxs-lookup"><span data-stu-id="7a17d-206">To find a certificate, use the Get-PfxCertificate cmdlet or use the Get-ChildItem cmdlet in the Certificate (Cert:) drive.</span></span>
<span data-ttu-id="7a17d-207">Si le certificat n'est pas valide ou n'a pas une autorité suffisante, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="7a17d-207">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="7a17d-208">-CommandName</span><span class="sxs-lookup"><span data-stu-id="7a17d-208">-CommandName</span></span>

<span data-ttu-id="7a17d-209">Spécifie les commandes avec les noms ou modèles de noms spécifiés.</span><span class="sxs-lookup"><span data-stu-id="7a17d-209">Specifies commands with the specified names or name patterns.</span></span>
<span data-ttu-id="7a17d-210">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7a17d-210">Wildcards are permitted.</span></span>
<span data-ttu-id="7a17d-211">Utilisez *CommandName* ou son alias, *Name* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-211">Use *CommandName* or its alias, *Name* .</span></span>

<span data-ttu-id="7a17d-212">Par défaut, **Import-PSSession** importe toutes les commandes de la session, à l'exception de celles qui ont le même nom que les commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-212">By default, **Import-PSSession** imports all commands from the session, except for commands that have the same names as commands in the current session.</span></span>
<span data-ttu-id="7a17d-213">Cela empêche les commandes importées de masquer ou de remplacer des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="7a17d-213">This prevents imported commands from hiding or replacing commands in the session.</span></span>
<span data-ttu-id="7a17d-214">Pour importer toutes les commandes, y compris celles qui masquent ou remplacent d'autres commandes, utilisez le paramètre *AllowClobber* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-214">To import all commands, even those that hide or replace other commands, use the *AllowClobber* parameter.</span></span>

<span data-ttu-id="7a17d-215">Si vous utilisez le paramètre *CommandName* , les fichiers de mise en forme pour les commandes ne sont pas importés, sauf si vous utilisez le paramètre *FormatTypeName* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-215">If you use the *CommandName* parameter, the formatting files for the commands are not imported unless you use the *FormatTypeName* parameter.</span></span>
<span data-ttu-id="7a17d-216">De même, si vous utilisez le paramètre *FormatTypeName* , aucune commande n'est importée, sauf si vous utilisez le paramètre *CommandName* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-216">Similarly, if you use the *FormatTypeName* parameter, no commands are imported unless you use the *CommandName* parameter.</span></span>

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

### <span data-ttu-id="7a17d-217">-CommandType</span><span class="sxs-lookup"><span data-stu-id="7a17d-217">-CommandType</span></span>

<span data-ttu-id="7a17d-218">Spécifie le type d’objets de commande.</span><span class="sxs-lookup"><span data-stu-id="7a17d-218">Specifies the type of command objects.</span></span>
<span data-ttu-id="7a17d-219">La valeur par défaut est Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a17d-219">The default value is Cmdlet.</span></span>
<span data-ttu-id="7a17d-220">Utilisez *CommandType* ou son alias, *Type* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-220">Use *CommandType* or its alias, *Type* .</span></span>
<span data-ttu-id="7a17d-221">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="7a17d-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7a17d-222">Affecté.</span><span class="sxs-lookup"><span data-stu-id="7a17d-222">Alias.</span></span>
<span data-ttu-id="7a17d-223">Alias PowerShell dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="7a17d-223">The PowerShell aliases in the remote session.</span></span>
- <span data-ttu-id="7a17d-224">Tout le monde.</span><span class="sxs-lookup"><span data-stu-id="7a17d-224">All.</span></span>
<span data-ttu-id="7a17d-225">Applets de commande et fonctions dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="7a17d-225">The cmdlets and functions in the remote session.</span></span>
- <span data-ttu-id="7a17d-226">console.</span><span class="sxs-lookup"><span data-stu-id="7a17d-226">Application.</span></span>
<span data-ttu-id="7a17d-227">Tous les fichiers autres que les fichiers PowerShell dans les chemins d’accès qui sont répertoriés dans la variable d’environnement PATH ($env :p Hemin) dans la session à distance, y compris les fichiers. txt,. exe et. dll.</span><span class="sxs-lookup"><span data-stu-id="7a17d-227">All the files other than PowerShell files in the paths that are listed in the Path environment variable ($env:path) in the remote session, including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="7a17d-228">PolicySchedule.</span><span class="sxs-lookup"><span data-stu-id="7a17d-228">Cmdlet.</span></span>
<span data-ttu-id="7a17d-229">Applets de commande dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="7a17d-229">The cmdlets in the remote session.</span></span>
<span data-ttu-id="7a17d-230">« Cmdlet » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7a17d-230">"Cmdlet" is the default.</span></span>
- <span data-ttu-id="7a17d-231">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="7a17d-231">ExternalScript.</span></span>
<span data-ttu-id="7a17d-232">Fichiers .ps1 dans les chemins d'accès répertoriés dans la variable d'environnement Path ($env:path) dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="7a17d-232">The .ps1 files in the paths listed in the Path environment variable ($env:path) in the remote session.</span></span>
- <span data-ttu-id="7a17d-233">Filtre et fonction.</span><span class="sxs-lookup"><span data-stu-id="7a17d-233">Filter and Function.</span></span>
<span data-ttu-id="7a17d-234">Fonctions PowerShell dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="7a17d-234">The PowerShell functions in the remote session.</span></span>
- <span data-ttu-id="7a17d-235">Script.</span><span class="sxs-lookup"><span data-stu-id="7a17d-235">Script.</span></span>
<span data-ttu-id="7a17d-236">Blocs de scripts dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="7a17d-236">The script blocks in the remote session.</span></span>

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

### <span data-ttu-id="7a17d-237">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="7a17d-237">-DisableNameChecking</span></span>

<span data-ttu-id="7a17d-238">Indique que cette applet de commande supprime le message qui vous avertit lorsque vous importez une applet de commande ou une fonction dont le nom comprend un verbe non approuvé ou un caractère interdit.</span><span class="sxs-lookup"><span data-stu-id="7a17d-238">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="7a17d-239">Par défaut, lorsqu’un module que vous importez exporte des applets de commande ou des fonctions qui ont des verbes non approuvés dans leurs noms, PowerShell affiche le message d’avertissement suivant :</span><span class="sxs-lookup"><span data-stu-id="7a17d-239">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, the PowerShell displays the following warning message:</span></span>

<span data-ttu-id="7a17d-240">"AVERTISSEMENT : certains noms de commandes importés incluent des verbes non approuvés qui peuvent les rendre moins détectables.</span><span class="sxs-lookup"><span data-stu-id="7a17d-240">"WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span>
<span data-ttu-id="7a17d-241">Utilisez le paramètre Verbose pour plus d'informations ou tapez Get-Verb pour obtenir la liste des verbes approuvés. »</span><span class="sxs-lookup"><span data-stu-id="7a17d-241">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs."</span></span>

<span data-ttu-id="7a17d-242">Ce message n'est qu'un avertissement.</span><span class="sxs-lookup"><span data-stu-id="7a17d-242">This message is only a warning.</span></span>
<span data-ttu-id="7a17d-243">Le module entier est toujours importé, y compris les commandes non conformes.</span><span class="sxs-lookup"><span data-stu-id="7a17d-243">The complete module is still imported, including the non-conforming commands.</span></span>
<span data-ttu-id="7a17d-244">Bien que le message soit affiché aux utilisateurs du module, le problème d'affectation de noms doit être corrigé par l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="7a17d-244">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="7a17d-245">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="7a17d-245">-FormatTypeName</span></span>

<span data-ttu-id="7a17d-246">Spécifie les instructions de mise en forme pour les types d’Microsoft .NET Framework spécifiés.</span><span class="sxs-lookup"><span data-stu-id="7a17d-246">Specifies formatting instructions for the specified Microsoft .NET Framework types.</span></span>
<span data-ttu-id="7a17d-247">Entrez les noms des types.</span><span class="sxs-lookup"><span data-stu-id="7a17d-247">Enter the type names.</span></span>
<span data-ttu-id="7a17d-248">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7a17d-248">Wildcards are permitted.</span></span>

<span data-ttu-id="7a17d-249">La valeur de ce paramètre doit être le nom d'un type qui est retourné par une commande Get-FormatData dans la session à partir de laquelle les commandes sont importées.</span><span class="sxs-lookup"><span data-stu-id="7a17d-249">The value of this parameter must be the name of a type that is returned by a Get-FormatData command in the session from which the commands are being imported.</span></span>
<span data-ttu-id="7a17d-250">Pour obtenir toutes les données de mise en forme dans la session à distance, tapez \*.</span><span class="sxs-lookup"><span data-stu-id="7a17d-250">To get all of the formatting data in the remote session, type \*.</span></span>

<span data-ttu-id="7a17d-251">Si la commande n’inclut pas le paramètre *CommandName* ou *FormatTypeName* , **Import-PSSession** importe les instructions de mise en forme pour tous les types de .NET Framework retournés par une commande **FormatData** dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="7a17d-251">If the command does not include either the *CommandName* or *FormatTypeName* parameter, **Import-PSSession** imports formatting instructions for all .NET Framework types returned by a **Get-FormatData** command in the remote session.</span></span>

<span data-ttu-id="7a17d-252">Si vous utilisez le paramètre *FormatTypeName* , aucune commande n'est importée, sauf si vous utilisez le paramètre *CommandName* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-252">If you use the *FormatTypeName* parameter, no commands are imported unless you use the *CommandName* parameter.</span></span>

<span data-ttu-id="7a17d-253">De même, si vous utilisez le paramètre *CommandName* , les fichiers de mise en forme pour les commandes ne sont pas importés, sauf si vous utilisez le paramètre *FormatTypeName* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-253">Similarly, if you use the *CommandName* parameter, the formatting files for the commands are not imported unless you use the *FormatTypeName* parameter.</span></span>

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

### <span data-ttu-id="7a17d-254">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="7a17d-254">-FullyQualifiedModule</span></span>

<span data-ttu-id="7a17d-255">Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** (décrits dans la section Notes du [constructeur ModuleSpecification (HASHTABLE)](https://msdn.microsoft.com/library/jj136290) dans MSDN Library).</span><span class="sxs-lookup"><span data-stu-id="7a17d-255">Specifies modules with names that are specified in the form of **ModuleSpecification** objects (described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library).</span></span>
<span data-ttu-id="7a17d-256">Par exemple, le paramètre *FullyQualifiedModule* accepte un nom de module qui est spécifié au format @ {ModuleName = "ModuleName"; ModuleVersion = "version_number"} ou @ {ModuleName = "ModuleName"; ModuleVersion = "version_number"; Guid = "GUID"}.</span><span class="sxs-lookup"><span data-stu-id="7a17d-256">For example, the *FullyQualifiedModule* parameter accepts a module name that is specified in the format @{ModuleName = "modulename"; ModuleVersion = "version_number"} or @{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.</span></span>
<span data-ttu-id="7a17d-257">**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="7a17d-257">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="7a17d-258">Vous ne pouvez pas spécifier le paramètre *FullyQualifiedModule* dans la même commande qu’un paramètre *module* ; les deux paramètres s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="7a17d-258">You cannot specify the *FullyQualifiedModule* parameter in the same command as a *Module* parameter; the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="7a17d-259">-Module</span><span class="sxs-lookup"><span data-stu-id="7a17d-259">-Module</span></span>

<span data-ttu-id="7a17d-260">Spécifie et tableau de commandes dans les modules et composants logiciels enfichables PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a17d-260">Specifies and array of commands in the PowerShell snap-ins and modules.</span></span>
<span data-ttu-id="7a17d-261">Entrez les noms de composant logiciel enfichable et de module.</span><span class="sxs-lookup"><span data-stu-id="7a17d-261">Enter the snap-in and module names.</span></span>
<span data-ttu-id="7a17d-262">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="7a17d-262">Wildcards are not permitted.</span></span>

<span data-ttu-id="7a17d-263">**Import-PSSession** ne peut pas importer des fournisseurs à partir d’un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="7a17d-263">**Import-PSSession** cannot import providers from a snap-in.</span></span>

<span data-ttu-id="7a17d-264">Pour plus d'informations, consultez about_PSSnapins et [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="7a17d-264">For more information, see about_PSSnapins and [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

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

### <span data-ttu-id="7a17d-265">-Prefix</span><span class="sxs-lookup"><span data-stu-id="7a17d-265">-Prefix</span></span>

<span data-ttu-id="7a17d-266">Spécifie un préfixe pour les noms des commandes importées.</span><span class="sxs-lookup"><span data-stu-id="7a17d-266">Specifies a prefix to the nouns in the names of imported commands.</span></span>

<span data-ttu-id="7a17d-267">Utilisez ce paramètre pour éviter les conflits de noms qui peuvent se produire quand des commandes différentes dans la session ont le même nom.</span><span class="sxs-lookup"><span data-stu-id="7a17d-267">Use this parameter to avoid name conflicts that might occur when different commands in the session have the same name.</span></span>

<span data-ttu-id="7a17d-268">Par exemple, si vous spécifiez le préfixe Remote, puis importez une applet de commande Get-Date, l’applet de commande est connue dans la session en tant que RemoteDate et n’est pas confondue avec l’applet de commande d’origine de l’opération d' **extraction** .</span><span class="sxs-lookup"><span data-stu-id="7a17d-268">For instance, if you specify the prefix Remote and then import a Get-Date cmdlet, the cmdlet is known in the session as Get-RemoteDate, and it is not confused with the original **Get-Date** cmdlet.</span></span>

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

### <span data-ttu-id="7a17d-269">-Session</span><span class="sxs-lookup"><span data-stu-id="7a17d-269">-Session</span></span>

<span data-ttu-id="7a17d-270">Spécifie la **session PSSession** à partir de laquelle les applets de commande sont importées.</span><span class="sxs-lookup"><span data-stu-id="7a17d-270">Specifies the **PSSession** from which the cmdlets are imported.</span></span>
<span data-ttu-id="7a17d-271">Entrez une variable qui contient un objet de session ou une commande qui obtient un objet de session, tel qu’une commande New-PSSession ou Get-PSSession.</span><span class="sxs-lookup"><span data-stu-id="7a17d-271">Enter a variable that contains a session object or a command that gets a session object, such as a New-PSSession or Get-PSSession command.</span></span>
<span data-ttu-id="7a17d-272">Vous ne pouvez spécifier qu'une seule session.</span><span class="sxs-lookup"><span data-stu-id="7a17d-272">You can specify only one session.</span></span>
<span data-ttu-id="7a17d-273">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7a17d-273">This parameter is required.</span></span>

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

### <span data-ttu-id="7a17d-274">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a17d-274">CommonParameters</span></span>

<span data-ttu-id="7a17d-275">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a17d-275">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a17d-276">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7a17d-276">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a17d-277">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="7a17d-277">INPUTS</span></span>

### <span data-ttu-id="7a17d-278">Aucun</span><span class="sxs-lookup"><span data-stu-id="7a17d-278">None</span></span>

<span data-ttu-id="7a17d-279">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7a17d-279">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="7a17d-280">SORTIES</span><span class="sxs-lookup"><span data-stu-id="7a17d-280">OUTPUTS</span></span>

### <span data-ttu-id="7a17d-281">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="7a17d-281">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="7a17d-282">**Import-PSSession** retourne le même objet de module que New-Module et les applets de commande Get-Module retournent.</span><span class="sxs-lookup"><span data-stu-id="7a17d-282">**Import-PSSession** returns the same module object that New-Module and Get-Module cmdlets return.</span></span>
<span data-ttu-id="7a17d-283">Toutefois, le module importé est temporaire et existe uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7a17d-283">However, the imported module is temporary and exists only in the current session.</span></span>
<span data-ttu-id="7a17d-284">Pour créer un module permanent sur le disque, utilisez l’applet de commande Export-PSSession.</span><span class="sxs-lookup"><span data-stu-id="7a17d-284">To create a permanent module on disk, use the Export-PSSession cmdlet.</span></span>

## <span data-ttu-id="7a17d-285">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="7a17d-285">NOTES</span></span>

* <span data-ttu-id="7a17d-286">**Import-PSSession** s’appuie sur l’infrastructure de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a17d-286">**Import-PSSession** relies on the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="7a17d-287">Pour utiliser cette applet de commande, l'ordinateur doit être configuré pour la communication à distance WS-Management.</span><span class="sxs-lookup"><span data-stu-id="7a17d-287">To use this cmdlet, the computer must be configured for WS-Management remoting.</span></span> <span data-ttu-id="7a17d-288">Pour plus d’informations, consultez about_Remote et about_Remote_Requirements.</span><span class="sxs-lookup"><span data-stu-id="7a17d-288">For more information, see about_Remote and about_Remote_Requirements.</span></span>
* <span data-ttu-id="7a17d-289">**Import-PSSession** n’importe pas les variables ou les fournisseurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a17d-289">**Import-PSSession** does not import variables or PowerShell providers.</span></span>
* <span data-ttu-id="7a17d-290">Quand vous importez des commandes qui ont le même nom que les commandes dans la session active, les commandes importées peuvent masquer des alias, des fonctions et des applets de commande dans la session, et peuvent remplacer des fonctions et variables dans la session.</span><span class="sxs-lookup"><span data-stu-id="7a17d-290">When you import commands that have the same names as commands in the current session, the imported commands can hide aliases, functions, and cmdlets in the session and they can replace functions and variables in the session.</span></span> <span data-ttu-id="7a17d-291">Pour éviter les conflits de noms, utilisez le paramètre *Prefix* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-291">To prevent name conflicts, use the *Prefix* parameter.</span></span> <span data-ttu-id="7a17d-292">Pour plus d'informations, consultez about_Command_Precedence.</span><span class="sxs-lookup"><span data-stu-id="7a17d-292">For more information, see about_Command_Precedence.</span></span>
* <span data-ttu-id="7a17d-293">**Import-PSSession** convertit toutes les commandes en fonctions avant de les importer.</span><span class="sxs-lookup"><span data-stu-id="7a17d-293">**Import-PSSession** converts all commands into functions before it imports them.</span></span> <span data-ttu-id="7a17d-294">Par conséquent, les commandes importées se comportent un peu différemment que si elles avaient conservé leur type de commande d'origine.</span><span class="sxs-lookup"><span data-stu-id="7a17d-294">As a result, imported commands behave a bit differently than they would if they retained their original command type.</span></span> <span data-ttu-id="7a17d-295">Par exemple, si vous importez une applet de commande à partir d'une session PSSession, puis une applet de commande avec le même nom à partir d'un module ou d'un composant logiciel enfichable, l'applet de commande qui est importée à partir de la session PSSession s'exécute toujours par défaut, car les fonctions sont prioritaires sur les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="7a17d-295">For example, if you import a cmdlet from a PSSession and then import a cmdlet with the same name from a module or snap-in, the cmdlet that is imported from the PSSession always runs by default because functions take precedence over cmdlets.</span></span> <span data-ttu-id="7a17d-296">À l'inverse, si vous importez un alias dans une session qui a un alias avec le même nom, l'alias d'origine est toujours utilisé, car les alias sont prioritaires sur les fonctions.</span><span class="sxs-lookup"><span data-stu-id="7a17d-296">Conversely, if you import an alias into a session that has an alias with the same name, the original alias is always used, because aliases take precedence over functions.</span></span> <span data-ttu-id="7a17d-297">Pour plus d'informations, consultez about_Command_Precedence.</span><span class="sxs-lookup"><span data-stu-id="7a17d-297">For more information, see about_Command_Precedence.</span></span>
* <span data-ttu-id="7a17d-298">**Import-PSSession** utilise l’applet de commande Write-Progress pour afficher la progression de la commande.</span><span class="sxs-lookup"><span data-stu-id="7a17d-298">**Import-PSSession** uses the Write-Progress cmdlet to display the progress of the command.</span></span> <span data-ttu-id="7a17d-299">Vous pouvez voir la barre de progression pendant l'exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="7a17d-299">You might see the progress bar while the command is running.</span></span>
* <span data-ttu-id="7a17d-300">Pour rechercher les commandes à importer, **Import-PSSession** utilise l’applet de commande Invoke-Command pour exécuter une commande Get-Command dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7a17d-300">To find the commands to import, **Import-PSSession** uses the Invoke-Command cmdlet to run a Get-Command command in the PSSession.</span></span> <span data-ttu-id="7a17d-301">Pour obtenir des données de mise en forme pour les commandes, elle utilise l’applet de commande Get-FormatData.</span><span class="sxs-lookup"><span data-stu-id="7a17d-301">To get formatting data for the commands, it uses the Get-FormatData cmdlet.</span></span> <span data-ttu-id="7a17d-302">Vous pouvez voir des messages d’erreur de ces applets de commande lorsque vous exécutez une commande **Import-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="7a17d-302">You might see error messages from these cmdlets when you run an **Import-PSSession** command.</span></span> <span data-ttu-id="7a17d-303">En outre, **Import-PSSession** ne peut pas importer de commandes à partir d’une session PSSession qui n’inclut pas les applets de commande obtenir-Command, obtenir-FormatData, Select-Object et Get-Help.</span><span class="sxs-lookup"><span data-stu-id="7a17d-303">Also, **Import-PSSession** cannot import commands from a PSSession that does not include the Get-Command, Get-FormatData, Select-Object, and Get-Help cmdlets.</span></span>
* <span data-ttu-id="7a17d-304">Les commandes importées présentent les mêmes restrictions que d'autres commandes à distance, notamment l'impossibilité de démarrer un programme avec une interface utilisateur, tel que le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="7a17d-304">Imported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>
* <span data-ttu-id="7a17d-305">Étant donné que les profils PowerShell ne sont pas exécutés dans sessions PSSession, les commandes qu’un profil ajoute à une session ne sont pas disponibles pour **Import-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="7a17d-305">Because PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to **Import-PSSession** .</span></span> <span data-ttu-id="7a17d-306">Pour importer des commandes à partir d'un profil, utilisez une commande Invoke-Command pour exécuter le profil dans la session PSSession manuellement avant d'importer des commandes.</span><span class="sxs-lookup"><span data-stu-id="7a17d-306">To import commands from a profile, use an Invoke-Command command to run the profile in the PSSession manually before importing commands.</span></span>
* <span data-ttu-id="7a17d-307">Le module temporaire créé par **Import-PSSession** peut inclure un fichier de mise en forme, même si la commande n'importe pas les données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="7a17d-307">The temporary module that **Import-PSSession** creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="7a17d-308">Si la commande n'importe pas de données de mise en forme, les fichiers de mise en forme éventuellement créés ne contiennent pas de données de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="7a17d-308">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>
* <span data-ttu-id="7a17d-309">Pour utiliser **Import-PSSession** , la stratégie d'exécution dans la session active ne peut pas être Restricted ni AllSigned, car le module temporaire créé par **Import-PSSession** contient des fichiers de script non signés qui sont interdits par ces stratégies.</span><span class="sxs-lookup"><span data-stu-id="7a17d-309">To use **Import-PSSession** , the execution policy in the current session cannot be Restricted or AllSigned, because the temporary module that **Import-PSSession** creates contains unsigned script files that are prohibited by these policies.</span></span> <span data-ttu-id="7a17d-310">Pour utiliser **Import-PSSession** sans modifier la stratégie d’exécution de l’ordinateur local, utilisez le paramètre *scope* de Set-ExecutionPolicy pour définir une stratégie d’exécution moins restrictive pour un seul processus.</span><span class="sxs-lookup"><span data-stu-id="7a17d-310">To use **Import-PSSession** without changing the execution policy for the local computer, use the *Scope* parameter of Set-ExecutionPolicy to set a less restrictive execution policy for a single process.</span></span>
* <span data-ttu-id="7a17d-311">Dans Windows PowerShell 2.0, les rubriques d'aide pour les commandes qui sont importées à partir d'une autre session n'incluent pas le préfixe que vous attribuez à l'aide du paramètre *Prefix* .</span><span class="sxs-lookup"><span data-stu-id="7a17d-311">In Windows PowerShell 2.0, help topics for commands that are imported from another session do not include the prefix that you assign by using the *Prefix* parameter.</span></span> <span data-ttu-id="7a17d-312">Pour obtenir de l'aide pour une commande importée dans Windows PowerShell 2.0, utilisez le nom de commande (sans préfixe) d'origine.</span><span class="sxs-lookup"><span data-stu-id="7a17d-312">To get help for an imported command in Windows PowerShell 2.0, use the original (non-prefixed) command name.</span></span>

## <span data-ttu-id="7a17d-313">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="7a17d-313">RELATED LINKS</span></span>

[<span data-ttu-id="7a17d-314">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="7a17d-314">Export-PSSession</span></span>](Export-PSSession.md)
