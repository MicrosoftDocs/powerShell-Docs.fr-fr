---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Module d’importation
ms.openlocfilehash: efb82cb938f7b044b863a8192f4c66673d47a4e0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201926"
---
# <span data-ttu-id="fc62d-103">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="fc62d-103">Import-Module</span></span>

## <span data-ttu-id="fc62d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fc62d-104">SYNOPSIS</span></span>
<span data-ttu-id="fc62d-105">Ajoute des modules à la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-105">Adds modules to the current session.</span></span>

## <span data-ttu-id="fc62d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fc62d-106">SYNTAX</span></span>

### <span data-ttu-id="fc62d-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="fc62d-107">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="fc62d-108">PSSession</span><span class="sxs-lookup"><span data-stu-id="fc62d-108">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="fc62d-109">CimSession</span><span class="sxs-lookup"><span data-stu-id="fc62d-109">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="fc62d-110">UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="fc62d-110">UseWindowsPowerShell</span></span>

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="fc62d-111">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="fc62d-111">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="fc62d-112">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="fc62d-112">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="fc62d-113">FullyQualifiedNameAndUseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="fc62d-113">FullyQualifiedNameAndUseWindowsPowerShell</span></span>

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="fc62d-114">Assembly</span><span class="sxs-lookup"><span data-stu-id="fc62d-114">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="fc62d-115">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="fc62d-115">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## <span data-ttu-id="fc62d-116">Description</span><span class="sxs-lookup"><span data-stu-id="fc62d-116">DESCRIPTION</span></span>

<span data-ttu-id="fc62d-117">L' `Import-Module` applet de commande ajoute un ou plusieurs modules à la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-117">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="fc62d-118">À compter de PowerShell 3,0, les modules installés sont automatiquement importés dans la session lorsque vous utilisez des commandes ou des fournisseurs dans le module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-118">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="fc62d-119">Toutefois, vous pouvez toujours utiliser la `Import-Module` commande pour importer un module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-119">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="fc62d-120">Vous pouvez désactiver l’importation automatique de modules à l’aide de la `$PSModuleAutoloadingPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="fc62d-120">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="fc62d-121">Pour plus d’informations sur la `$PSModuleAutoloadingPreference` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="fc62d-121">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="fc62d-122">Un module est un package qui contient des membres qui peuvent être utilisés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc62d-122">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="fc62d-123">Les membres incluent des applets de commande, des fournisseurs, des scripts, des fonctions, des variables et d’autres outils et fichiers.</span><span class="sxs-lookup"><span data-stu-id="fc62d-123">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="fc62d-124">Après avoir importé un module, vous pouvez utiliser ses membres dans votre session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-124">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="fc62d-125">Pour plus d’informations sur les modules, consultez [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="fc62d-125">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="fc62d-126">Par défaut, `Import-Module` importe tous les membres que le module exporte, mais vous pouvez utiliser les paramètres **alias** , **Function** , **applets** de commande et **variables** pour limiter les membres qui sont importés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-126">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias** , **Function** , **Cmdlet** , and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="fc62d-127">Le paramètre **NoClobber** empêche `Import-Module` d’importer des membres qui ont les mêmes noms que les membres de la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-127">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="fc62d-128">`Import-Module` importe un module uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-128">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="fc62d-129">Pour importer le module dans chaque nouvelle session, ajoutez une `Import-Module` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc62d-129">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="fc62d-130">Pour plus d'informations sur les profils, consultez [about_Profiles](About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="fc62d-130">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="fc62d-131">Vous pouvez gérer les ordinateurs Windows distants pour lesquels la communication à distance PowerShell est activée en créant une **session PSSession** sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-131">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="fc62d-132">Utilisez ensuite le paramètre **PSSession** de `Import-Module` pour importer les modules installés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-132">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="fc62d-133">Vous pouvez maintenant utiliser les commandes importées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-133">You can now use the imported commands in the current session.</span></span> <span data-ttu-id="fc62d-134">Les commandes s’exécutent implicitement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-134">The commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="fc62d-135">À compter de Windows PowerShell 3,0, vous pouvez utiliser `Import-Module` pour importer des modules Common Information Model (CIM), dans lesquels les applets de commande sont définies dans des fichiers de définition d’applet de commande (CDXML).</span><span class="sxs-lookup"><span data-stu-id="fc62d-135">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="fc62d-136">Cette fonctionnalité vous permet d'utiliser les applets de commande qui sont implémentées dans des assemblys de code non managé, telles que celles écrites en C++.</span><span class="sxs-lookup"><span data-stu-id="fc62d-136">This feature allows you to use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="fc62d-137">Pour les ordinateurs distants sur lesquels la communication à distance PowerShell n’est pas activée, y compris les ordinateurs qui n’exécutent pas le système d’exploitation Windows, vous pouvez utiliser le paramètre **CIMSession** de `Import-Module` pour importer des modules CIM à partir de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-137">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="fc62d-138">Les commandes importées s’exécutent implicitement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-138">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="fc62d-139">Un **CIMSession** est une connexion à Windows Management Instrumentation (WMI) sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-139">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="fc62d-140">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fc62d-140">EXAMPLES</span></span>

### <span data-ttu-id="fc62d-141">Exemple 1 : importer les membres d’un module dans la session active</span><span class="sxs-lookup"><span data-stu-id="fc62d-141">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="fc62d-142">Cet exemple importe les membres du module **PSDiagnostics** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-142">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="fc62d-143">Exemple 2 : importer tous les modules spécifiés par le chemin d’accès du module</span><span class="sxs-lookup"><span data-stu-id="fc62d-143">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="fc62d-144">Cet exemple importe tous les modules disponibles dans le chemin d’accès spécifié par la `$env:PSModulePath` variable d’environnement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-144">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="fc62d-145">Exemple 3 : importer les membres de plusieurs modules dans la session active</span><span class="sxs-lookup"><span data-stu-id="fc62d-145">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="fc62d-146">Cet exemple importe les membres des modules **PSDiagnostics** et **DISM** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-146">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="fc62d-147">L' `Get-Module` applet de commande obtient les modules **PSDiagnostics** et **DISM** et enregistre les objets dans la `$m` variable.</span><span class="sxs-lookup"><span data-stu-id="fc62d-147">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="fc62d-148">Le paramètre **listAvailable** est obligatoire lorsque vous obtenez des modules qui ne sont pas encore importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-148">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="fc62d-149">Le paramètre **ModuleInfo** de `Import-Module` est utilisé pour importer les modules dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-149">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="fc62d-150">Exemple 4 : importer tous les modules spécifiés par un chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="fc62d-150">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="fc62d-151">Cet exemple utilise un chemin d’accès explicite pour identifier le module à importer.</span><span class="sxs-lookup"><span data-stu-id="fc62d-151">This example uses an explicit path to identify the module to import.</span></span>

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

<span data-ttu-id="fc62d-152">L’utilisation du paramètre **Verbose** entraîne le `Import-Module` signalement de la progression au cours du chargement du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-152">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="fc62d-153">Sans le paramètre **Verbose** , **PassThru** ou **AsCustomObject** , `Import-Module` ne génère pas de sortie lors de l’importation d’un module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-153">Without the **Verbose** , **PassThru** , or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="fc62d-154">Exemple 5 : limiter les membres de module importés dans une session</span><span class="sxs-lookup"><span data-stu-id="fc62d-154">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="fc62d-155">Cet exemple montre comment limiter les membres de module qui sont importés dans la session et l’effet de cette commande sur la session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-155">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="fc62d-156">Le paramètre de **fonction** limite les membres importés à partir du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-156">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="fc62d-157">Vous pouvez également utiliser les paramètres **alias** , **variable** et **applet** de commande pour restreindre les autres membres qu’un module importe.</span><span class="sxs-lookup"><span data-stu-id="fc62d-157">You can also use the **Alias** , **Variable** , and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="fc62d-158">L' `Get-Module` applet de commande obtient l’objet qui représente le module **PSDiagnostics** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-158">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="fc62d-159">La propriété **ExportedCmdlets** répertorie toutes les applets de commande exportées par le module, même si elles n’ont pas été importées.</span><span class="sxs-lookup"><span data-stu-id="fc62d-159">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

<span data-ttu-id="fc62d-160">L’utilisation du paramètre **module** de l' `Get-Command` applet de commande affiche les commandes qui ont été importées à partir du module **PSDiagnostics** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-160">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="fc62d-161">Les résultats confirment que seules `Disable-PSTrace` les `Enable-PSTrace` applets de commande et ont été importées.</span><span class="sxs-lookup"><span data-stu-id="fc62d-161">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="fc62d-162">Exemple 6 : importer les membres d’un module et ajouter un préfixe</span><span class="sxs-lookup"><span data-stu-id="fc62d-162">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="fc62d-163">Cet exemple importe le module **PSDiagnostics** dans la session active, ajoute un préfixe aux noms des membres, puis affiche les noms des membres préfixés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-163">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="fc62d-164">Le paramètre **prefix** de `Import-Module` ajoute le préfixe **x** à tous les membres qui sont importés à partir du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-164">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="fc62d-165">Le préfixe s’applique uniquement aux membres de la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-165">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="fc62d-166">Il ne modifie pas le module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-166">It does not change the module.</span></span> <span data-ttu-id="fc62d-167">Le paramètre **PassThru** retourne un objet de module qui représente le module importé.</span><span class="sxs-lookup"><span data-stu-id="fc62d-167">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

<span data-ttu-id="fc62d-168">`Get-Command` Obtient les membres qui ont été importés à partir du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-168">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="fc62d-169">La sortie indique que les membres de module ont été correctement préfixés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-169">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="fc62d-170">Exemple 7 : obtenir et utiliser un objet personnalisé</span><span class="sxs-lookup"><span data-stu-id="fc62d-170">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="fc62d-171">Cet exemple montre comment récupérer et utiliser l’objet personnalisé retourné par **import-module** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-171">This example demonstrates how to get and use the custom object returned by **Import-Module** .</span></span>

<span data-ttu-id="fc62d-172">Les objets personnalisés incluent des membres synthétiques représentant chacun des membres de module importés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-172">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="fc62d-173">Par exemple, les applets de commande et les fonctions dans un module sont converties en méthodes de script de l'objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fc62d-173">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="fc62d-174">Les objets personnalisés sont utiles pour l’écriture de scripts.</span><span class="sxs-lookup"><span data-stu-id="fc62d-174">Custom objects are useful in scripting.</span></span> <span data-ttu-id="fc62d-175">Ils sont également utiles quand plusieurs objets importés ont le même nom.</span><span class="sxs-lookup"><span data-stu-id="fc62d-175">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="fc62d-176">Utiliser la méthode de script d'un objet équivaut à spécifier le nom qualifié complet d'un membre importé, y compris son nom de module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-176">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="fc62d-177">Le paramètre **AsCustomObject** peut être utilisé uniquement lors de l’importation d’un module de script.</span><span class="sxs-lookup"><span data-stu-id="fc62d-177">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="fc62d-178">Utilisez `Get-Module` pour déterminer lequel des modules disponibles est un module de script.</span><span class="sxs-lookup"><span data-stu-id="fc62d-178">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

<span data-ttu-id="fc62d-179">Le module de script **Show-Calendar** est importé à l’aide du paramètre **AsCustomObject** pour demander un objet personnalisé et le paramètre **PassThru** pour retourner l’objet.</span><span class="sxs-lookup"><span data-stu-id="fc62d-179">The **Show-Calendar** script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="fc62d-180">L’objet personnalisé résultant est enregistré dans la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="fc62d-180">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="fc62d-181">La `$a` variable est dirigée vers l' `Get-Member` applet de commande pour afficher les propriétés et les méthodes de l’objet enregistré.</span><span class="sxs-lookup"><span data-stu-id="fc62d-181">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="fc62d-182">La sortie montre une méthode de script **Show-Calendar** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-182">The output shows a **Show-Calendar** script method.</span></span>

<span data-ttu-id="fc62d-183">Pour appeler la méthode de script **Show-Calendar** , le nom de la méthode doit être placé entre guillemets, car le nom contient un trait d’Union.</span><span class="sxs-lookup"><span data-stu-id="fc62d-183">To call the **Show-Calendar** script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="fc62d-184">Exemple 8 : réimporter un module dans la même session</span><span class="sxs-lookup"><span data-stu-id="fc62d-184">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="fc62d-185">Cet exemple montre comment utiliser le paramètre **force** de `Import-Module` lorsque vous réimportez un module dans la même session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-185">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="fc62d-186">Le paramètre **force** supprime le module chargé, puis le réimporte.</span><span class="sxs-lookup"><span data-stu-id="fc62d-186">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="fc62d-187">La première commande importe le module **PSDiagnostics** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-187">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="fc62d-188">La deuxième commande réimporte le module, cette fois en utilisant le paramètre **Prefix** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-188">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="fc62d-189">Sans le paramètre **force** , la session inclut deux copies de chaque applet de commande **PSDiagnostics** , l’une avec le nom standard et l’autre avec le nom préfixé.</span><span class="sxs-lookup"><span data-stu-id="fc62d-189">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="fc62d-190">Exemple 9 : exécuter des commandes qui ont été masquées par des commandes importées</span><span class="sxs-lookup"><span data-stu-id="fc62d-190">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="fc62d-191">Cet exemple montre comment exécuter des commandes qui ont été masquées par des commandes importées.</span><span class="sxs-lookup"><span data-stu-id="fc62d-191">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="fc62d-192">Le module **TestModule** comprend une fonction nommée `Get-Date` qui retourne l’année et le jour de l’année.</span><span class="sxs-lookup"><span data-stu-id="fc62d-192">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

<span data-ttu-id="fc62d-193">La première `Get-Date` applet de commande retourne un objet **DateTime** avec la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="fc62d-193">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="fc62d-194">Après l’importation du module **TestModule** , `Get-Date` retourne l’année et le jour de l’année.</span><span class="sxs-lookup"><span data-stu-id="fc62d-194">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="fc62d-195">L’utilisation du paramètre **All** de `Get-Command` affiche toutes les `Get-Date` commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-195">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="fc62d-196">Les résultats montrent qu’il y a deux `Get-Date` commandes dans la session, une fonction du module **TestModule** et une applet de commande du module **Microsoft. PowerShell. Utility** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-196">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="fc62d-197">Comme les fonctions sont prioritaires sur les applets de commande, la `Get-Date` fonction du module **TestModule** s’exécute à la place de l’applet de commande `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="fc62d-197">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="fc62d-198">Pour exécuter la version d’origine de `Get-Date` , vous devez qualifier le nom de la commande avec le nom du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-198">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="fc62d-199">Pour plus d’informations sur la priorité des commandes dans PowerShell, consultez [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="fc62d-199">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="fc62d-200">Exemple 10 : importer une version minimale d’un module</span><span class="sxs-lookup"><span data-stu-id="fc62d-200">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="fc62d-201">Cet exemple importe le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-201">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="fc62d-202">Elle utilise le paramètre **MinimumVersion** de `Import-Module` pour importer uniquement la version 2.0.0 ou ultérieure du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-202">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="fc62d-203">Vous pouvez également utiliser le paramètre **RequiredVersion** pour importer une version particulière d’un module, ou utiliser les paramètres **module** et **version** du `#Requires` mot clé pour exiger une version particulière d’un module dans un script.</span><span class="sxs-lookup"><span data-stu-id="fc62d-203">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="fc62d-204">Exemple 11 : importer à l’aide d’un nom complet</span><span class="sxs-lookup"><span data-stu-id="fc62d-204">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="fc62d-205">Cet exemple importe une version spécifique d’un module à l’aide de FullyQualifiedName.</span><span class="sxs-lookup"><span data-stu-id="fc62d-205">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### <span data-ttu-id="fc62d-206">Exemple 12 : importer à l’aide d’un chemin d’accès complet</span><span class="sxs-lookup"><span data-stu-id="fc62d-206">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="fc62d-207">Cet exemple importe une version spécifique d’un module à l’aide du chemin d’accès qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="fc62d-207">This example imports a specific version of a module using the fully qualified path.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### <span data-ttu-id="fc62d-208">Exemple 13 : importer un module à partir d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="fc62d-208">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="fc62d-209">Cet exemple montre comment utiliser l' `Import-Module` applet de commande pour importer un module à partir d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-209">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="fc62d-210">Cette commande utilise la fonctionnalité de communication à distance implicite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc62d-210">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="fc62d-211">Quand vous importez des modules à partir d'une autre session, vous pouvez utiliser les applets de commande dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-211">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="fc62d-212">Toutefois, les commandes qui utilisent les applets de commande s’exécutent dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="fc62d-212">However, commands that use the cmdlets run in the remote session.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

<span data-ttu-id="fc62d-213">`New-PSSession` crée une session à distance ( **PSSession** ) sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="fc62d-213">`New-PSSession` creates a remote session ( **PSSession** ) to the Server01 computer.</span></span> <span data-ttu-id="fc62d-214">La **session PSSession** est enregistrée dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="fc62d-214">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="fc62d-215">Le `Get-Module` fait d’exécuter avec le paramètre **PSSession** indique que le module **netsecurity** est installé et disponible sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-215">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="fc62d-216">Cette commande revient à utiliser l' `Invoke-Command` applet de commande pour exécuter la `Get-Module` commande dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="fc62d-216">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="fc62d-217">Par exemple : (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="fc62d-217">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="fc62d-218">L’exécution `Import-Module` de avec le paramètre **PSSession** importe le module **netsecurity** à partir de l’ordinateur distant dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-218">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="fc62d-219">L' `Get-Command` applet de commande est utilisée pour récupérer les commandes qui commencent par le **pare-feu** d' **extraction** et d’inclusion dans le module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-219">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="fc62d-220">La sortie confirme que le module et ses applets de commande ont été importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-220">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="fc62d-221">Ensuite, l' `Get-NetFirewallRule` applet de commande obtient Windows Remote Management règles de pare-feu sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="fc62d-221">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="fc62d-222">Cela équivaut à utiliser l' `Invoke-Command` applet de commande pour s’exécuter `Get-NetFirewallRule` sur la session à distance.</span><span class="sxs-lookup"><span data-stu-id="fc62d-222">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="fc62d-223">Exemple 14 : gérer le stockage sur un ordinateur distant sans système d’exploitation Windows</span><span class="sxs-lookup"><span data-stu-id="fc62d-223">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="fc62d-224">Dans cet exemple, l’administrateur de l’ordinateur a installé le fournisseur WMI de détection de module, qui vous permet d’utiliser des commandes CIM conçues pour le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="fc62d-224">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="fc62d-225">L' `New-CimSession` applet de commande crée une session sur l’ordinateur distant nommé RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="fc62d-225">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="fc62d-226">La session se connecte au service WMI sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-226">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="fc62d-227">La session CIM est enregistrée dans la `$cs` variable.</span><span class="sxs-lookup"><span data-stu-id="fc62d-227">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="fc62d-228">`Import-Module` utilise le **CimSession** dans `$cs` pour importer le module CIM de **stockage** à partir de l’ordinateur RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="fc62d-228">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="fc62d-229">L' `Get-Command` applet `Get-Disk` de commande affiche la commande dans le module de **stockage** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-229">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="fc62d-230">Lorsque vous importez un module CIM dans la session locale, PowerShell convertit les fichiers CDXML pour chaque commande en scripts PowerShell, qui apparaissent sous la forme de fonctions dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="fc62d-230">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="fc62d-231">Bien que `Get-Disk` soit tapé dans la session locale, l’applet de commande s’exécute implicitement sur l’ordinateur distant à partir duquel elle a été importée.</span><span class="sxs-lookup"><span data-stu-id="fc62d-231">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="fc62d-232">La commande retourne des objets de l’ordinateur distant à la session locale.</span><span class="sxs-lookup"><span data-stu-id="fc62d-232">The command returns objects from the remote computer to the local session.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## <span data-ttu-id="fc62d-233">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fc62d-233">PARAMETERS</span></span>

### <span data-ttu-id="fc62d-234">-Alias</span><span class="sxs-lookup"><span data-stu-id="fc62d-234">-Alias</span></span>

<span data-ttu-id="fc62d-235">Spécifie les alias que cette applet de commande importe à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-235">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="fc62d-236">Entrez une liste séparée par des virgules des alias.</span><span class="sxs-lookup"><span data-stu-id="fc62d-236">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="fc62d-237">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-237">Wildcard characters are permitted.</span></span>

<span data-ttu-id="fc62d-238">Au moment de leur importation, certains modules exportent automatiquement les alias sélectionnés dans votre session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-238">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="fc62d-239">Ce paramètre vous permet d'effectuer votre choix parmi les alias exportés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-239">This parameter lets you select from among the exported aliases.</span></span>

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

### <span data-ttu-id="fc62d-240">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="fc62d-240">-ArgumentList</span></span>

<span data-ttu-id="fc62d-241">Spécifie un tableau d’arguments, ou valeurs de paramètre, qui sont passés à un module de script pendant la `Import-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="fc62d-241">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="fc62d-242">Ce paramètre n’est valide que lorsque vous importez un module de script.</span><span class="sxs-lookup"><span data-stu-id="fc62d-242">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="fc62d-243">Vous pouvez également faire référence au paramètre **argumentlist** par son alias, **args** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-243">You can also refer to the **ArgumentList** parameter by its alias, **args** .</span></span> <span data-ttu-id="fc62d-244">Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="fc62d-244">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="fc62d-245">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="fc62d-245">-AsCustomObject</span></span>

<span data-ttu-id="fc62d-246">Indique que cette applet de commande retourne un objet personnalisé avec des membres qui représentent les membres de module importés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-246">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="fc62d-247">Ce paramètre n'est valide que pour les modules de script.</span><span class="sxs-lookup"><span data-stu-id="fc62d-247">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="fc62d-248">Quand vous utilisez le paramètre **AsCustomObject** , `Import-Module` importe les membres de module dans la session, puis retourne un objet **PSCustomObject** au lieu d’un objet **PSModuleInfo** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-248">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="fc62d-249">Vous pouvez enregistrer l'objet personnalisé dans une variable et utiliser la notation par points pour appeler les membres.</span><span class="sxs-lookup"><span data-stu-id="fc62d-249">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-250">-Assembly</span><span class="sxs-lookup"><span data-stu-id="fc62d-250">-Assembly</span></span>

<span data-ttu-id="fc62d-251">Spécifie un tableau d’objets d’assembly.</span><span class="sxs-lookup"><span data-stu-id="fc62d-251">Specifies an array of assembly objects.</span></span> <span data-ttu-id="fc62d-252">Cette applet de commande importe les applets de commande et les fournisseurs implémentés dans les objets d’assembly spécifiés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-252">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="fc62d-253">Entrez une variable qui contient les objets d'assembly ou une commande qui crée des objets d'assembly.</span><span class="sxs-lookup"><span data-stu-id="fc62d-253">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="fc62d-254">Vous pouvez également diriger un objet assembly vers `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="fc62d-254">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="fc62d-255">Quand vous utilisez ce paramètre, seuls les applets de commande et les fournisseurs implémentés par les assemblys spécifiés sont importés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-255">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="fc62d-256">Si le module contient d’autres fichiers, ils ne sont pas importés et il se peut que vous ne soyez pas membre important du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-256">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="fc62d-257">Utilisez ce paramètre pour déboguer et tester le module, ou quand vous êtes invité à l’utiliser par l’auteur du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-257">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-258">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="fc62d-258">-CimNamespace</span></span>

<span data-ttu-id="fc62d-259">Spécifie l'espace de noms d'un autre fournisseur CIM qui expose des modules CIM.</span><span class="sxs-lookup"><span data-stu-id="fc62d-259">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="fc62d-260">La valeur par défaut est l'espace de noms du fournisseur WMI pour la découverte de module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-260">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="fc62d-261">Utilisez ce paramètre pour importer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas un système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="fc62d-261">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="fc62d-262">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fc62d-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-263">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="fc62d-263">-CimResourceUri</span></span>

<span data-ttu-id="fc62d-264">Spécifie un autre emplacement pour les modules CIM.</span><span class="sxs-lookup"><span data-stu-id="fc62d-264">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="fc62d-265">La valeur par défaut est l’URI de ressource du fournisseur WMI de détection de module sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-265">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="fc62d-266">Utilisez ce paramètre pour importer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas un système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="fc62d-266">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="fc62d-267">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fc62d-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-268">-CimSession</span><span class="sxs-lookup"><span data-stu-id="fc62d-268">-CimSession</span></span>

<span data-ttu-id="fc62d-269">Spécifie une session CIM sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-269">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="fc62d-270">Entrez une variable qui contient la session CIM ou une commande qui obtient la session CIM, telle qu’une commande [CimSession](../CimCmdlets/Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="fc62d-270">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="fc62d-271">`Import-Module` utilise la connexion de session CIM pour importer des modules à partir de l’ordinateur distant dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-271">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="fc62d-272">Lorsque vous utilisez les commandes du module importé dans la session active, les commandes s’exécutent sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-272">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="fc62d-273">Vous pouvez utiliser ce paramètre pour importer des modules à partir d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows, et d’ordinateurs Windows qui disposent de PowerShell, mais pour lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="fc62d-273">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="fc62d-274">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fc62d-274">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-275">-Applet de commande</span><span class="sxs-lookup"><span data-stu-id="fc62d-275">-Cmdlet</span></span>

<span data-ttu-id="fc62d-276">Spécifie un tableau d’applets de commande importées par cette applet de commande à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-276">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="fc62d-277">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-277">Wildcard characters are permitted.</span></span>

<span data-ttu-id="fc62d-278">Au moment de leur importation, certains modules exportent automatiquement les applets de commande sélectionnées dans votre session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-278">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="fc62d-279">Ce paramètre vous permet d'effectuer votre choix parmi les applets de commande exportées.</span><span class="sxs-lookup"><span data-stu-id="fc62d-279">This parameter lets you select from among the exported cmdlets.</span></span>

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

### <span data-ttu-id="fc62d-280">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="fc62d-280">-DisableNameChecking</span></span>

<span data-ttu-id="fc62d-281">Indique que cette applet de commande supprime le message qui vous avertit lorsque vous importez une applet de commande ou une fonction dont le nom comprend un verbe non approuvé ou un caractère interdit.</span><span class="sxs-lookup"><span data-stu-id="fc62d-281">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="fc62d-282">Par défaut, lorsqu’un module que vous importez exporte des applets de commande ou des fonctions qui ont des verbes non approuvés dans leurs noms, PowerShell affiche le message d’avertissement suivant :</span><span class="sxs-lookup"><span data-stu-id="fc62d-282">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="fc62d-283">AVERTISSEMENT : certains noms de commandes importés incluent des verbes non approuvés qui peuvent les rendre moins détectables.</span><span class="sxs-lookup"><span data-stu-id="fc62d-283">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="fc62d-284">Utilisez le paramètre Verbose pour obtenir plus d'informations ou tapez Get-Verb pour afficher la liste des verbes approuvés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-284">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="fc62d-285">Ce message n'est qu'un avertissement.</span><span class="sxs-lookup"><span data-stu-id="fc62d-285">This message is only a warning.</span></span> <span data-ttu-id="fc62d-286">Le module entier est toujours importé, y compris les commandes non conformes.</span><span class="sxs-lookup"><span data-stu-id="fc62d-286">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="fc62d-287">Bien que le message soit affiché aux utilisateurs du module, le problème d'affectation de noms doit être corrigé par l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-287">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-288">-Force</span><span class="sxs-lookup"><span data-stu-id="fc62d-288">-Force</span></span>

<span data-ttu-id="fc62d-289">Ce paramètre entraîne le chargement ou le rechargement d’un module au-dessus de celui en cours.</span><span class="sxs-lookup"><span data-stu-id="fc62d-289">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-290">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="fc62d-290">-FullyQualifiedName</span></span>

<span data-ttu-id="fc62d-291">Spécifie le nom qualifié complet du module sous la forme d’une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="fc62d-291">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="fc62d-292">La valeur peut être une combinaison de chaînes et de tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="fc62d-292">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="fc62d-293">La table de hachage a les clés suivantes.</span><span class="sxs-lookup"><span data-stu-id="fc62d-293">The hash table has the following keys.</span></span>

- <span data-ttu-id="fc62d-294">`ModuleName` - **Obligatoire** Spécifie le nom du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-294">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="fc62d-295">`GUID` - **Facultatif** Spécifie le GUID du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-295">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="fc62d-296">Il est également **nécessaire** de spécifier l’une des trois clés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="fc62d-296">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="fc62d-297">Ces clés ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="fc62d-297">These keys can't be used together.</span></span>
  - <span data-ttu-id="fc62d-298">`ModuleVersion` -Spécifie une version minimale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-298">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="fc62d-299">`RequiredVersion` -Spécifie une version exacte et obligatoire du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-299">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="fc62d-300">`MaximumVersion` -Spécifie la version maximale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-300">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedNameAndPSSession, FullyQualifiedName, FullyQualifiedNameAndWinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-301">-Fonction</span><span class="sxs-lookup"><span data-stu-id="fc62d-301">-Function</span></span>

<span data-ttu-id="fc62d-302">Spécifie un tableau de fonctions que cette applet de commande importe à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-302">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="fc62d-303">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-303">Wildcard characters are permitted.</span></span> <span data-ttu-id="fc62d-304">Au moment de leur importation, certains modules exportent automatiquement les fonctions sélectionnées dans votre session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-304">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="fc62d-305">Ce paramètre vous permet d'effectuer votre choix parmi les fonctions exportées.</span><span class="sxs-lookup"><span data-stu-id="fc62d-305">This parameter lets you select from among the exported functions.</span></span>

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

### <span data-ttu-id="fc62d-306">-Global</span><span class="sxs-lookup"><span data-stu-id="fc62d-306">-Global</span></span>

<span data-ttu-id="fc62d-307">Indique que cette applet de commande importe des modules dans l’état de session global pour qu’ils soient disponibles pour toutes les commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-307">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="fc62d-308">Par défaut, lorsque l' `Import-Module` applet de commande est appelée à partir de l’invite de commandes, d’un fichier de script ou d’un scriptblock, toutes les commandes sont importées dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="fc62d-308">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="fc62d-309">Lorsqu’elle est appelée à partir d’un autre module, `Import-Module` l’applet de commande importe les commandes d’un module, y compris les commandes des modules imbriqués, dans l’état de session du module appelant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-309">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="fc62d-310">Vous devez éviter `Import-Module` d’appeler à partir d’un module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-310">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="fc62d-311">Au lieu de cela, déclarez le module cible comme un module imbriqué dans le manifeste du module parent.</span><span class="sxs-lookup"><span data-stu-id="fc62d-311">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="fc62d-312">La déclaration des modules imbriqués améliore la détectabilité des dépendances.</span><span class="sxs-lookup"><span data-stu-id="fc62d-312">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="fc62d-313">Le paramètre **Global** équivaut au paramètre **Scope** avec la valeur **Global** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-313">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global** .</span></span>

<span data-ttu-id="fc62d-314">Pour restreindre les commandes qu’un module exporte, utilisez une `Export-ModuleMember` commande dans le module de script.</span><span class="sxs-lookup"><span data-stu-id="fc62d-314">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-315">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="fc62d-315">-MaximumVersion</span></span>

<span data-ttu-id="fc62d-316">Spécifie une version maximale.</span><span class="sxs-lookup"><span data-stu-id="fc62d-316">Specifies a maximum version.</span></span> <span data-ttu-id="fc62d-317">Cette applet de commande importe uniquement une version du module qui est inférieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fc62d-317">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="fc62d-318">Si aucune version n’est qualifiée, `Import-Module` retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="fc62d-318">If no version qualifies, `Import-Module` returns an error.</span></span>

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-319">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="fc62d-319">-MinimumVersion</span></span>

<span data-ttu-id="fc62d-320">Spécifie une version minimale.</span><span class="sxs-lookup"><span data-stu-id="fc62d-320">Specifies a minimum version.</span></span> <span data-ttu-id="fc62d-321">Cette applet de commande importe uniquement une version du module qui est supérieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fc62d-321">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="fc62d-322">Utilisez le nom de paramètre **MinimumVersion** ou son alias, **Version** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-322">Use the **MinimumVersion** parameter name or its alias, **Version** .</span></span> <span data-ttu-id="fc62d-323">Si aucune version n’est qualifiée, `Import-Module` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="fc62d-323">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="fc62d-324">Pour spécifier une version exacte, utilisez le paramètre **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-324">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="fc62d-325">Vous pouvez également utiliser les paramètres **module** et **version** du mot clé **#Requires** pour exiger une version spécifique d’un module dans un script.</span><span class="sxs-lookup"><span data-stu-id="fc62d-325">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="fc62d-326">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fc62d-326">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-327">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="fc62d-327">-ModuleInfo</span></span>

<span data-ttu-id="fc62d-328">Spécifie un tableau d’objets de module à importer.</span><span class="sxs-lookup"><span data-stu-id="fc62d-328">Specifies an array of module objects to import.</span></span> <span data-ttu-id="fc62d-329">Entrez une variable qui contient les objets de module ou une commande qui obtient les objets de module, tels que la commande suivante : `Get-Module -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="fc62d-329">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="fc62d-330">Vous pouvez également diriger les objets de module vers `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="fc62d-330">You can also pipe module objects to `Import-Module`.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-331">-Name</span><span class="sxs-lookup"><span data-stu-id="fc62d-331">-Name</span></span>

<span data-ttu-id="fc62d-332">Spécifie les noms des modules à importer.</span><span class="sxs-lookup"><span data-stu-id="fc62d-332">Specifies the names of the modules to import.</span></span> <span data-ttu-id="fc62d-333">Entrez le nom du module ou le nom d’un fichier dans le module, tel qu’un `.psd1` fichier, `.psm1` , `.dll` ou `.ps1` .</span><span class="sxs-lookup"><span data-stu-id="fc62d-333">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="fc62d-334">Les chemins d'accès aux fichiers sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="fc62d-334">File paths are optional.</span></span> <span data-ttu-id="fc62d-335">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-335">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="fc62d-336">Vous pouvez également diriger les noms de module et les noms de fichiers vers `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="fc62d-336">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="fc62d-337">Si vous omettez un chemin d’accès, `Import-Module` recherche le module dans les chemins d’accès enregistrés dans la `$env:PSModulePath` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="fc62d-337">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="fc62d-338">Spécifiez uniquement le nom du module chaque fois que possible.</span><span class="sxs-lookup"><span data-stu-id="fc62d-338">Specify only the module name whenever possible.</span></span> <span data-ttu-id="fc62d-339">Quand vous spécifiez un nom de fichier, seuls les membres qui sont implémentés dans ce fichier sont importés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-339">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="fc62d-340">Si le module contient d’autres fichiers, ils ne sont pas importés et il se peut que vous ne soyez pas membre important du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-340">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="fc62d-341">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="fc62d-341">-NoClobber</span></span>

<span data-ttu-id="fc62d-342">Empêche l’importation des commandes qui ont les mêmes noms que les commandes existantes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-342">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="fc62d-343">Par défaut, `Import-Module` importe toutes les commandes de module exportées.</span><span class="sxs-lookup"><span data-stu-id="fc62d-343">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="fc62d-344">Les commandes qui ont le même nom peuvent masquer ou remplacer des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-344">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="fc62d-345">Pour éviter les conflits de nom de commande dans une session, utilisez les paramètres **Prefix** ou **NoClobber** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-345">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="fc62d-346">Pour plus d'informations sur les conflits de nom et la priorité des commandes, consultez « Modules et conflits de noms » dans [about_Modules](about/about_Modules.md) et [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="fc62d-346">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="fc62d-347">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fc62d-347">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-348">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fc62d-348">-PassThru</span></span>

<span data-ttu-id="fc62d-349">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fc62d-349">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="fc62d-350">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="fc62d-350">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-351">-Prefix</span><span class="sxs-lookup"><span data-stu-id="fc62d-351">-Prefix</span></span>

<span data-ttu-id="fc62d-352">Spécifie un préfixe que cette applet de commande ajoute aux noms des membres de module importés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-352">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="fc62d-353">Utilisez ce paramètre pour éviter les conflits de noms qui peuvent se produire quand des membres différents dans la session ont le même nom.</span><span class="sxs-lookup"><span data-stu-id="fc62d-353">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="fc62d-354">Ce paramètre ne modifie pas le module, et il n’affecte pas les fichiers que le module importe pour son propre usage.</span><span class="sxs-lookup"><span data-stu-id="fc62d-354">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="fc62d-355">Ils sont appelés modules imbriqués.</span><span class="sxs-lookup"><span data-stu-id="fc62d-355">These are known as nested modules.</span></span> <span data-ttu-id="fc62d-356">Cette applet de commande affecte uniquement les noms des membres dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-356">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="fc62d-357">Par exemple, si vous spécifiez le préfixe UTC, puis importez une applet de commande `Get-Date` , l’applet de commande est connue dans la session en tant que `Get-UTCDate` , et elle n’est pas confondue avec l’applet de commande d’origine `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="fc62d-357">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="fc62d-358">La valeur de ce paramètre est prioritaire sur la propriété **DefaultCommandPrefix** du module, qui spécifie le préfixe par défaut.</span><span class="sxs-lookup"><span data-stu-id="fc62d-358">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

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

### <span data-ttu-id="fc62d-359">-PSSession</span><span class="sxs-lookup"><span data-stu-id="fc62d-359">-PSSession</span></span>

<span data-ttu-id="fc62d-360">Spécifie une session PowerShell managée par l’utilisateur ( **PSSession** ) à partir de laquelle cette applet de commande importe des modules dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-360">Specifies a PowerShell user-managed session ( **PSSession** ) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="fc62d-361">Entrez une variable qui contient une **session PSSession** ou une commande qui obtient une **session PSSession** , telle qu’une `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="fc62d-361">Enter a variable that contains a **PSSession** or a command that gets a **PSSession** , such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="fc62d-362">Quand vous importez un module à partir d'une autre session dans la session active, vous pouvez utiliser les applets de commande du module dans la session active, tout comme vous utiliseriez des applets de commande à partir d'un module local.</span><span class="sxs-lookup"><span data-stu-id="fc62d-362">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="fc62d-363">Les commandes qui utilisent les applets de commande distantes s’exécutent dans la session à distance, mais les détails de l’accès distant sont gérés en arrière-plan par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc62d-363">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="fc62d-364">Ce paramètre utilise la fonctionnalité de communication à distance implicite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc62d-364">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="fc62d-365">Cela équivaut à utiliser l' `Import-PSSession` applet de commande pour importer des modules particuliers à partir d’une session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-365">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="fc62d-366">`Import-Module` Impossible d’importer les modules PowerShell Core à partir d’une autre session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-366">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="fc62d-367">Les modules PowerShell Core portent des noms qui commencent par Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc62d-367">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="fc62d-368">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fc62d-368">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-369">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="fc62d-369">-RequiredVersion</span></span>

<span data-ttu-id="fc62d-370">Spécifie une version du module que cette applet de commande importe.</span><span class="sxs-lookup"><span data-stu-id="fc62d-370">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="fc62d-371">Si la version n’est pas installée, `Import-Module` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="fc62d-371">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="fc62d-372">Par défaut, `Import-Module` importe le module sans vérifier le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="fc62d-372">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="fc62d-373">Pour spécifier une version minimale, utilisez le paramètre **MinimumVersion** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-373">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="fc62d-374">Vous pouvez également utiliser les paramètres **module** et **version** du mot clé **#Requires** pour exiger une version spécifique d’un module dans un script.</span><span class="sxs-lookup"><span data-stu-id="fc62d-374">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="fc62d-375">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fc62d-375">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="fc62d-376">Les scripts qui utilisent **RequiredVersion** pour importer des modules inclus avec les versions existantes du système d’exploitation Windows ne s’exécutent pas automatiquement dans les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="fc62d-376">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="fc62d-377">En effet, les numéros de version de module PowerShell dans les versions ultérieures du système d’exploitation Windows sont plus élevés que les numéros de version de module dans les versions existantes du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="fc62d-377">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-378">-Étendue</span><span class="sxs-lookup"><span data-stu-id="fc62d-378">-Scope</span></span>

<span data-ttu-id="fc62d-379">Spécifie une étendue dans laquelle cette applet de commande importe le module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-379">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="fc62d-380">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="fc62d-380">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fc62d-381">**Global** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-381">**Global** .</span></span> <span data-ttu-id="fc62d-382">disponible pour toutes les commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-382">Available to all commands in the session.</span></span> <span data-ttu-id="fc62d-383">Équivalent au paramètre **Global** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-383">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="fc62d-384">**Local** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-384">**Local** .</span></span> <span data-ttu-id="fc62d-385">Disponible uniquement dans l'étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="fc62d-385">Available only in the current scope.</span></span>

<span data-ttu-id="fc62d-386">Par défaut, lorsque l' `Import-Module` applet de commande est appelée à partir de l’invite de commandes, d’un fichier de script ou d’un scriptblock, toutes les commandes sont importées dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="fc62d-386">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="fc62d-387">Vous pouvez utiliser le paramètre **-scope** avec la valeur **local** pour importer le contenu du module dans la portée du script ou du scriptblock.</span><span class="sxs-lookup"><span data-stu-id="fc62d-387">You can use the **-Scope** parameter with the value of **Local** to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="fc62d-388">Lorsqu’elle est appelée à partir d’un autre module, `Import-Module` l’applet de commande importe les commandes d’un module, y compris les commandes des modules imbriqués, dans l’état de session de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-388">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="fc62d-389">La spécification de `-Scope Global` ou `-Global` indique que cette applet de commande importe des modules dans l’état de session global pour qu’ils soient disponibles pour toutes les commandes de la session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-389">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="fc62d-390">Le paramètre **Global** est équivalent au paramètre **scope** avec la valeur global.</span><span class="sxs-lookup"><span data-stu-id="fc62d-390">The **Global** parameter is equivalent to the **Scope** parameter with a value of Global.</span></span>

<span data-ttu-id="fc62d-391">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fc62d-391">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-392">-Variable</span><span class="sxs-lookup"><span data-stu-id="fc62d-392">-Variable</span></span>

<span data-ttu-id="fc62d-393">Spécifie un tableau de variables que cette applet de commande importe du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-393">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="fc62d-394">Entrez une liste de variables.</span><span class="sxs-lookup"><span data-stu-id="fc62d-394">Enter a list of variables.</span></span> <span data-ttu-id="fc62d-395">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-395">Wildcard characters are permitted.</span></span>

<span data-ttu-id="fc62d-396">Au moment de leur importation, certains modules exportent automatiquement les variables sélectionnées dans votre session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-396">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="fc62d-397">Ce paramètre vous permet d'effectuer votre choix parmi les variables exportées.</span><span class="sxs-lookup"><span data-stu-id="fc62d-397">This parameter lets you select from among the exported variables.</span></span>

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

### <span data-ttu-id="fc62d-398">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="fc62d-398">-SkipEditionCheck</span></span>

<span data-ttu-id="fc62d-399">Ignore la vérification sur le `CompatiblePSEditions` champ.</span><span class="sxs-lookup"><span data-stu-id="fc62d-399">Skips the check on the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="fc62d-400">Permet de charger un module à partir du `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` répertoire du module dans PowerShell Core quand ce module ne spécifie pas `Core` dans le `CompatiblePSEditions` champ de manifeste.</span><span class="sxs-lookup"><span data-stu-id="fc62d-400">Allows loading a module from the `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory into PowerShell Core when that module does not specify `Core` in the `CompatiblePSEditions` manifest field.</span></span>

<span data-ttu-id="fc62d-401">Lorsque vous importez un module à partir d’un autre chemin d’accès, ce commutateur n’a aucun effet, car la vérification n’est pas effectuée.</span><span class="sxs-lookup"><span data-stu-id="fc62d-401">When importing a module from another path, this switch does nothing, since the check is not performed.</span></span> <span data-ttu-id="fc62d-402">Sur Linux et macOS, ce commutateur ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="fc62d-402">On Linux and macOS, this switch does nothing.</span></span>

<span data-ttu-id="fc62d-403">Pour plus d’informations, consultez [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span><span class="sxs-lookup"><span data-stu-id="fc62d-403">For more information, see [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span></span>

> [!WARNING]
> <span data-ttu-id="fc62d-404">`Import-Module -SkipEditionCheck` l’importation d’un module risque toujours d’échouer.</span><span class="sxs-lookup"><span data-stu-id="fc62d-404">`Import-Module -SkipEditionCheck` is still likely to fail to import a module.</span></span> <span data-ttu-id="fc62d-405">Même si elle réussit, l’appel d’une commande à partir du module peut échouer plus tard lorsqu’elle essaie d’utiliser une API incompatible.</span><span class="sxs-lookup"><span data-stu-id="fc62d-405">Even if it does succeed, invoking a command from the module may later fail when it tries to use an incompatible API.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, PSSession, CimSession, FullyQualifiedNameAndPSSession, FullyQualifiedName, Assembly, ModuleInfo
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-406">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="fc62d-406">-UseWindowsPowerShell</span></span>

<span data-ttu-id="fc62d-407">Charge le module à l’aide de la fonctionnalité de compatibilité Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc62d-407">Loads module using Windows PowerShell Compatibility functionality.</span></span> <span data-ttu-id="fc62d-408">Pour plus d’informations, consultez [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) .</span><span class="sxs-lookup"><span data-stu-id="fc62d-408">See [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WinCompat, FullyQualifiedNameAndWinCompat
Aliases: UseWinPS

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc62d-409">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc62d-409">CommonParameters</span></span>

<span data-ttu-id="fc62d-410">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fc62d-410">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fc62d-411">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fc62d-411">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fc62d-412">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fc62d-412">INPUTS</span></span>

### <span data-ttu-id="fc62d-413">System. String, System. Management. Automation. PSModuleInfo, System. Reflection. assembly</span><span class="sxs-lookup"><span data-stu-id="fc62d-413">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="fc62d-414">Vous pouvez diriger un nom de module, un objet de module ou un objet d’assembly vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fc62d-414">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="fc62d-415">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fc62d-415">OUTPUTS</span></span>

### <span data-ttu-id="fc62d-416">None, System. Management. Automation. PSModuleInfo ou System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="fc62d-416">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="fc62d-417">Par défaut, `Import-Module` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="fc62d-417">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="fc62d-418">Si vous spécifiez le paramètre **PassThru** , l’applet de commande génère un objet **System. Management. Automation. PSModuleInfo** qui représente le module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-418">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="fc62d-419">Si vous spécifiez le paramètre **AsCustomObject** , il génère un objet **PSCustomObject** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-419">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="fc62d-420">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fc62d-420">NOTES</span></span>

- <span data-ttu-id="fc62d-421">Avant de pouvoir importer un module, le module doit être installé sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fc62d-421">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="fc62d-422">Autrement dit, le répertoire de module doit être copié vers un répertoire qui est accessible à votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fc62d-422">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="fc62d-423">Pour plus d’informations, consultez [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="fc62d-423">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="fc62d-424">Vous pouvez également utiliser les paramètres **PSSession** et **CIMSession** pour importer des modules qui sont installés sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="fc62d-424">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="fc62d-425">Toutefois, les commandes qui utilisent les applets de commande dans ces modules s’exécutent dans la session à distance sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fc62d-425">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="fc62d-426">Si vous importez des membres portant le même nom et le même type dans votre session, PowerShell utilise par défaut le membre importé en dernier.</span><span class="sxs-lookup"><span data-stu-id="fc62d-426">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="fc62d-427">Les variables et les alias sont remplacés, et les originaux ne sont pas accessibles.</span><span class="sxs-lookup"><span data-stu-id="fc62d-427">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="fc62d-428">Les fonctions, les applets de commande et les fournisseurs sont simplement occultés par les nouveaux membres.</span><span class="sxs-lookup"><span data-stu-id="fc62d-428">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="fc62d-429">Ils sont accessibles en qualifiant le nom de commande avec le nom de son composant logiciel enfichable, module ou chemin d’accès de fonction.</span><span class="sxs-lookup"><span data-stu-id="fc62d-429">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="fc62d-430">Pour mettre à jour les données de mise en forme pour les commandes qui ont été importées à partir d’un module, utilisez l’applet de commande `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="fc62d-430">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="fc62d-431">`Update-FormatData` met également à jour les données de mise en forme pour les commandes de la session qui ont été importées à partir de modules.</span><span class="sxs-lookup"><span data-stu-id="fc62d-431">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="fc62d-432">Si le fichier de mise en forme d’un module est modifié, vous pouvez exécuter une `Update-FormatData` commande pour mettre à jour les données de mise en forme des commandes importées.</span><span class="sxs-lookup"><span data-stu-id="fc62d-432">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="fc62d-433">Vous n’avez pas besoin de réimporter le module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-433">You don't need to import the module again.</span></span>

- <span data-ttu-id="fc62d-434">À compter de Windows PowerShell 3,0, les commandes de base qui sont installées avec PowerShell sont empaquetées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="fc62d-434">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="fc62d-435">Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables ( **PSSnapins** ).</span><span class="sxs-lookup"><span data-stu-id="fc62d-435">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="fc62d-436">L’exception est **Microsoft. PowerShell. Core** , qui est toujours un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="fc62d-436">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="fc62d-437">En outre, les sessions à distance, telles que celles démarrées par l’applet de commande `New-PSSession` , sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.</span><span class="sxs-lookup"><span data-stu-id="fc62d-437">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="fc62d-438">Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez la [méthode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span><span class="sxs-lookup"><span data-stu-id="fc62d-438">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="fc62d-439">`Import-Module` Impossible d’importer les modules PowerShell Core à partir d’une autre session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-439">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="fc62d-440">Les modules PowerShell Core portent des noms qui commencent par `Microsoft.PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="fc62d-440">The PowerShell Core modules have names that begin with `Microsoft.PowerShell`.</span></span>

- <span data-ttu-id="fc62d-441">Dans Windows PowerShell 2,0, certaines des valeurs de propriété de l’objet de module, telles que les valeurs de propriété **ExportedCmdlets** et **NestedModules** , n’ont pas été remplies tant que le module n’a pas été importé et n’étaient pas disponibles sur l’objet de module retourné par le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="fc62d-441">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported and were not available on the module object that the **PassThru** parameter returns.</span></span> <span data-ttu-id="fc62d-442">Dans Windows PowerShell 3,0, toutes les valeurs de propriété de module sont remplies.</span><span class="sxs-lookup"><span data-stu-id="fc62d-442">In Windows PowerShell 3.0, all module property values are populated.</span></span>

- <span data-ttu-id="fc62d-443">Si vous tentez d’importer un module qui contient des assemblys en mode mixte qui ne sont pas compatibles avec Windows PowerShell 3,0, `Import-Module` retourne un message d’erreur semblable à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="fc62d-443">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="fc62d-444">Import-Module : l’assembly en mode mixte est généré avec la version’v 2.0.50727 'du runtime et ne peut pas être chargé dans le runtime 4,0 sans informations de configuration supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="fc62d-444">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="fc62d-445">Cette erreur se produit lorsqu’un module conçu pour Windows PowerShell 2,0 contient au moins un assembly de module mixte, autrement dit un assembly qui inclut du code managé et non managé, tel que C++ et C#.</span><span class="sxs-lookup"><span data-stu-id="fc62d-445">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly, that is, an assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="fc62d-446">Pour importer un module qui contient des assemblys en mode mixte, démarrez Windows PowerShell 2,0 à l’aide de la commande suivante, puis réessayez d’exécuter la `Import-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="fc62d-446">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="fc62d-447">Pour utiliser la fonctionnalité de session CIM, l'ordinateur distant doit disposer de l'accès distant WS-Management et de Windows Management Instrumentation (WMI), qui est l'implémentation Microsoft du modèle CIM (Common Information Model) standard.</span><span class="sxs-lookup"><span data-stu-id="fc62d-447">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="fc62d-448">L'ordinateur doit également disposer du fournisseur WMI pour la découverte de module ou un autre fournisseur CIM qui a les mêmes fonctionnalités de base.</span><span class="sxs-lookup"><span data-stu-id="fc62d-448">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="fc62d-449">Vous pouvez utiliser la fonctionnalité de session CIM sur les ordinateurs qui n’exécutent pas de système d’exploitation Windows et sur les ordinateurs Windows qui disposent de PowerShell, mais pour lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="fc62d-449">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="fc62d-450">Vous pouvez également utiliser les paramètres CIM pour obtenir des modules CIM à partir d’ordinateurs sur lesquels la communication à distance PowerShell est activée, y compris l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fc62d-450">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="fc62d-451">Lorsque vous créez une session CIM sur l’ordinateur local, PowerShell utilise DCOM au lieu de WMI pour créer la session.</span><span class="sxs-lookup"><span data-stu-id="fc62d-451">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="fc62d-452">Par défaut, `Import-Module` importe les modules dans la portée globale même en cas d’appel à partir d’une portée descendante.</span><span class="sxs-lookup"><span data-stu-id="fc62d-452">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="fc62d-453">L’étendue de niveau supérieur et toutes les portées descendantes ont accès aux éléments exportés du module.</span><span class="sxs-lookup"><span data-stu-id="fc62d-453">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="fc62d-454">Dans une portée descendante, `-Scope Local` limite l’importation à cette portée et à toutes ses étendues descendantes.</span><span class="sxs-lookup"><span data-stu-id="fc62d-454">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="fc62d-455">Les étendues parentes ne voient pas les membres importés.</span><span class="sxs-lookup"><span data-stu-id="fc62d-455">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="fc62d-456">`Get-Module` affiche tous les modules chargés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fc62d-456">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="fc62d-457">Cela comprend les modules chargés localement dans une portée descendante.</span><span class="sxs-lookup"><span data-stu-id="fc62d-457">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="fc62d-458">Utilisez `Get-Command -Module modulename` pour voir quels membres sont chargés dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="fc62d-458">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="fc62d-459">Si le module comprend des définitions de classe et d’énumération, utilisez `using module` au début de votre script.</span><span class="sxs-lookup"><span data-stu-id="fc62d-459">If the module includes class and enum definitions, use `using module` at the beginning of your script.</span></span> <span data-ttu-id="fc62d-460">Cela a pour importation les scripts, y compris les définitions de classe et d’énumération.</span><span class="sxs-lookup"><span data-stu-id="fc62d-460">This import the scripts, including the class and enum definitions.</span></span> <span data-ttu-id="fc62d-461">Pour plus d’informations, consultez [about_Using](About/about_Using.md).</span><span class="sxs-lookup"><span data-stu-id="fc62d-461">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="fc62d-462">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fc62d-462">RELATED LINKS</span></span>

[<span data-ttu-id="fc62d-463">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="fc62d-463">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="fc62d-464">Get-Module</span><span class="sxs-lookup"><span data-stu-id="fc62d-464">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="fc62d-465">New-Module</span><span class="sxs-lookup"><span data-stu-id="fc62d-465">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="fc62d-466">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="fc62d-466">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="fc62d-467">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="fc62d-467">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
