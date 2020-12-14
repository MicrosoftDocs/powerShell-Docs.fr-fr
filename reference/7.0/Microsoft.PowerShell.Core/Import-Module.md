---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Module d’importation
ms.openlocfilehash: 218a4cb447c85a7362efebe9b50a917703cccc35
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564443"
---
# <span data-ttu-id="49ce7-102">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="49ce7-102">Import-Module</span></span>

## <span data-ttu-id="49ce7-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="49ce7-103">SYNOPSIS</span></span>
<span data-ttu-id="49ce7-104">Ajoute des modules à la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-104">Adds modules to the current session.</span></span>

## <span data-ttu-id="49ce7-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="49ce7-105">SYNTAX</span></span>

### <span data-ttu-id="49ce7-106">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="49ce7-106">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="49ce7-107">PSSession</span><span class="sxs-lookup"><span data-stu-id="49ce7-107">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="49ce7-108">CimSession</span><span class="sxs-lookup"><span data-stu-id="49ce7-108">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="49ce7-109">UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="49ce7-109">UseWindowsPowerShell</span></span>

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="49ce7-110">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="49ce7-110">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="49ce7-111">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="49ce7-111">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="49ce7-112">FullyQualifiedNameAndUseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="49ce7-112">FullyQualifiedNameAndUseWindowsPowerShell</span></span>

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="49ce7-113">Assembly</span><span class="sxs-lookup"><span data-stu-id="49ce7-113">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="49ce7-114">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="49ce7-114">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## <span data-ttu-id="49ce7-115">Description</span><span class="sxs-lookup"><span data-stu-id="49ce7-115">DESCRIPTION</span></span>

<span data-ttu-id="49ce7-116">L' `Import-Module` applet de commande ajoute un ou plusieurs modules à la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-116">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="49ce7-117">À compter de PowerShell 3,0, les modules installés sont automatiquement importés dans la session lorsque vous utilisez des commandes ou des fournisseurs dans le module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-117">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="49ce7-118">Toutefois, vous pouvez toujours utiliser la `Import-Module` commande pour importer un module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-118">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="49ce7-119">Vous pouvez désactiver l’importation automatique de modules à l’aide de la `$PSModuleAutoloadingPreference` variable de préférence.</span><span class="sxs-lookup"><span data-stu-id="49ce7-119">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="49ce7-120">Pour plus d’informations sur la `$PSModuleAutoloadingPreference` variable, consultez [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-120">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="49ce7-121">Un module est un package qui contient des membres qui peuvent être utilisés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49ce7-121">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="49ce7-122">Les membres incluent des applets de commande, des fournisseurs, des scripts, des fonctions, des variables et d’autres outils et fichiers.</span><span class="sxs-lookup"><span data-stu-id="49ce7-122">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="49ce7-123">Après avoir importé un module, vous pouvez utiliser ses membres dans votre session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-123">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="49ce7-124">Pour plus d’informations sur les modules, consultez [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-124">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="49ce7-125">Par défaut, `Import-Module` importe tous les membres que le module exporte, mais vous pouvez utiliser les paramètres **alias**, **Function**, **applets** de commande et **variables** pour limiter les membres qui sont importés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-125">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias**, **Function**, **Cmdlet**, and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="49ce7-126">Le paramètre **NoClobber** empêche `Import-Module` d’importer des membres qui ont les mêmes noms que les membres de la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-126">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="49ce7-127">`Import-Module` importe un module uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-127">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="49ce7-128">Pour importer le module dans chaque nouvelle session, ajoutez une `Import-Module` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49ce7-128">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="49ce7-129">Pour plus d'informations sur les profils, consultez [about_Profiles](About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-129">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="49ce7-130">Vous pouvez gérer les ordinateurs Windows distants pour lesquels la communication à distance PowerShell est activée en créant une **session PSSession** sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-130">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="49ce7-131">Utilisez ensuite le paramètre **PSSession** de `Import-Module` pour importer les modules installés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-131">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="49ce7-132">Lorsque vous utilisez les commandes importées dans la session active, les commandes s’exécutent implicitement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-132">When you use the imported commands in the current session the commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="49ce7-133">À partir de Windows PowerShell 3,0, vous pouvez utiliser `Import-Module` pour importer des modules Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="49ce7-133">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules.</span></span> <span data-ttu-id="49ce7-134">Les modules CIM définissent des applets de commande dans des fichiers CDXML (cmdlet Definition XML).</span><span class="sxs-lookup"><span data-stu-id="49ce7-134">CIM modules define cmdlets in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="49ce7-135">Cette fonctionnalité vous permet d’utiliser des applets de commande qui sont implémentées dans des assemblys de code non managé, telles que celles écrites en C++.</span><span class="sxs-lookup"><span data-stu-id="49ce7-135">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="49ce7-136">Pour les ordinateurs distants sur lesquels la communication à distance PowerShell n’est pas activée, y compris les ordinateurs qui n’exécutent pas le système d’exploitation Windows, vous pouvez utiliser le paramètre **CIMSession** de `Import-Module` pour importer des modules CIM à partir de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-136">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="49ce7-137">Les commandes importées s’exécutent implicitement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-137">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="49ce7-138">Un **CIMSession** est une connexion à Windows Management Instrumentation (WMI) sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-138">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="49ce7-139">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="49ce7-139">EXAMPLES</span></span>

### <span data-ttu-id="49ce7-140">Exemple 1 : importer les membres d’un module dans la session active</span><span class="sxs-lookup"><span data-stu-id="49ce7-140">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="49ce7-141">Cet exemple importe les membres du module **PSDiagnostics** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-141">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="49ce7-142">Exemple 2 : importer tous les modules spécifiés par le chemin d’accès du module</span><span class="sxs-lookup"><span data-stu-id="49ce7-142">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="49ce7-143">Cet exemple importe tous les modules disponibles dans le chemin d’accès spécifié par la `$env:PSModulePath` variable d’environnement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-143">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="49ce7-144">Exemple 3 : importer les membres de plusieurs modules dans la session active</span><span class="sxs-lookup"><span data-stu-id="49ce7-144">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="49ce7-145">Cet exemple importe les membres des modules **PSDiagnostics** et **DISM** dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-145">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="49ce7-146">L' `Get-Module` applet de commande obtient les modules **PSDiagnostics** et **DISM** et enregistre les objets dans la `$m` variable.</span><span class="sxs-lookup"><span data-stu-id="49ce7-146">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="49ce7-147">Le paramètre **listAvailable** est obligatoire lorsque vous obtenez des modules qui ne sont pas encore importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-147">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="49ce7-148">Le paramètre **ModuleInfo** de `Import-Module` est utilisé pour importer les modules dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-148">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="49ce7-149">Exemple 4 : importer tous les modules spécifiés par un chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="49ce7-149">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="49ce7-150">Cet exemple utilise un chemin d’accès explicite pour identifier le module à importer.</span><span class="sxs-lookup"><span data-stu-id="49ce7-150">This example uses an explicit path to identify the module to import.</span></span>

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

<span data-ttu-id="49ce7-151">L’utilisation du paramètre **Verbose** entraîne le `Import-Module` signalement de la progression au cours du chargement du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-151">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="49ce7-152">Sans le paramètre **Verbose**, **PassThru** ou **AsCustomObject** , `Import-Module` ne génère pas de sortie lors de l’importation d’un module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-152">Without the **Verbose**, **PassThru**, or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="49ce7-153">Exemple 5 : limiter les membres de module importés dans une session</span><span class="sxs-lookup"><span data-stu-id="49ce7-153">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="49ce7-154">Cet exemple montre comment limiter les membres de module qui sont importés dans la session et l’effet de cette commande sur la session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-154">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="49ce7-155">Le paramètre de **fonction** limite les membres importés à partir du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-155">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="49ce7-156">Vous pouvez également utiliser les paramètres **alias**, **variable** et **applet** de commande pour restreindre les autres membres qu’un module importe.</span><span class="sxs-lookup"><span data-stu-id="49ce7-156">You can also use the **Alias**, **Variable**, and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="49ce7-157">L' `Get-Module` applet de commande obtient l’objet qui représente le module **PSDiagnostics** .</span><span class="sxs-lookup"><span data-stu-id="49ce7-157">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="49ce7-158">La propriété **ExportedCmdlets** répertorie toutes les applets de commande exportées par le module, même si elles n’ont pas été importées.</span><span class="sxs-lookup"><span data-stu-id="49ce7-158">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

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

<span data-ttu-id="49ce7-159">L’utilisation du paramètre **module** de l' `Get-Command` applet de commande affiche les commandes qui ont été importées à partir du module **PSDiagnostics** .</span><span class="sxs-lookup"><span data-stu-id="49ce7-159">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="49ce7-160">Les résultats confirment que seules `Disable-PSTrace` les `Enable-PSTrace` applets de commande et ont été importées.</span><span class="sxs-lookup"><span data-stu-id="49ce7-160">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="49ce7-161">Exemple 6 : importer les membres d’un module et ajouter un préfixe</span><span class="sxs-lookup"><span data-stu-id="49ce7-161">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="49ce7-162">Cet exemple importe le module **PSDiagnostics** dans la session active, ajoute un préfixe aux noms des membres, puis affiche les noms des membres préfixés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-162">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="49ce7-163">Le paramètre **prefix** de `Import-Module` ajoute le préfixe **x** à tous les membres qui sont importés à partir du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-163">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="49ce7-164">Le préfixe s’applique uniquement aux membres de la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-164">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="49ce7-165">Il ne modifie pas le module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-165">It does not change the module.</span></span> <span data-ttu-id="49ce7-166">Le paramètre **PassThru** retourne un objet de module qui représente le module importé.</span><span class="sxs-lookup"><span data-stu-id="49ce7-166">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

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

<span data-ttu-id="49ce7-167">`Get-Command` Obtient les membres qui ont été importés à partir du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-167">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="49ce7-168">La sortie indique que les membres de module ont été correctement préfixés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-168">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="49ce7-169">Exemple 7 : obtenir et utiliser un objet personnalisé</span><span class="sxs-lookup"><span data-stu-id="49ce7-169">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="49ce7-170">Cet exemple montre comment récupérer et utiliser l’objet personnalisé retourné par `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="49ce7-170">This example demonstrates how to get and use the custom object returned by `Import-Module`.</span></span>

<span data-ttu-id="49ce7-171">Les objets personnalisés incluent des membres synthétiques représentant chacun des membres de module importés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-171">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="49ce7-172">Par exemple, les applets de commande et les fonctions dans un module sont converties en méthodes de script de l'objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="49ce7-172">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="49ce7-173">Les objets personnalisés sont utiles pour l’écriture de scripts.</span><span class="sxs-lookup"><span data-stu-id="49ce7-173">Custom objects are useful in scripting.</span></span> <span data-ttu-id="49ce7-174">Ils sont également utiles quand plusieurs objets importés ont le même nom.</span><span class="sxs-lookup"><span data-stu-id="49ce7-174">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="49ce7-175">Utiliser la méthode de script d'un objet équivaut à spécifier le nom qualifié complet d'un membre importé, y compris son nom de module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-175">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="49ce7-176">Le paramètre **AsCustomObject** peut être utilisé uniquement lors de l’importation d’un module de script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-176">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="49ce7-177">Utilisez `Get-Module` pour déterminer lequel des modules disponibles est un module de script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-177">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

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

<span data-ttu-id="49ce7-178">Le `Show-Calendar` module de script est importé à l’aide du paramètre **AsCustomObject** pour demander un objet personnalisé et le paramètre **PassThru** pour retourner l’objet.</span><span class="sxs-lookup"><span data-stu-id="49ce7-178">The `Show-Calendar` script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="49ce7-179">L’objet personnalisé résultant est enregistré dans la `$a` variable.</span><span class="sxs-lookup"><span data-stu-id="49ce7-179">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="49ce7-180">La `$a` variable est dirigée vers l' `Get-Member` applet de commande pour afficher les propriétés et les méthodes de l’objet enregistré.</span><span class="sxs-lookup"><span data-stu-id="49ce7-180">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="49ce7-181">La sortie illustre une `Show-Calendar` méthode de script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-181">The output shows a `Show-Calendar` script method.</span></span>

<span data-ttu-id="49ce7-182">Pour appeler la `Show-Calendar` méthode de script, le nom de la méthode doit être placé entre guillemets, car le nom contient un trait d’Union.</span><span class="sxs-lookup"><span data-stu-id="49ce7-182">To call the `Show-Calendar` script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="49ce7-183">Exemple 8 : réimporter un module dans la même session</span><span class="sxs-lookup"><span data-stu-id="49ce7-183">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="49ce7-184">Cet exemple montre comment utiliser le paramètre **force** de `Import-Module` lorsque vous réimportez un module dans la même session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-184">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="49ce7-185">Le paramètre **force** supprime le module chargé, puis le réimporte.</span><span class="sxs-lookup"><span data-stu-id="49ce7-185">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="49ce7-186">La première commande importe le module **PSDiagnostics** .</span><span class="sxs-lookup"><span data-stu-id="49ce7-186">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="49ce7-187">La deuxième commande réimporte le module, cette fois en utilisant le paramètre **Prefix**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-187">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="49ce7-188">Sans le paramètre **force** , la session inclut deux copies de chaque applet de commande **PSDiagnostics** , l’une avec le nom standard et l’autre avec le nom préfixé.</span><span class="sxs-lookup"><span data-stu-id="49ce7-188">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="49ce7-189">Exemple 9 : exécuter des commandes qui ont été masquées par des commandes importées</span><span class="sxs-lookup"><span data-stu-id="49ce7-189">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="49ce7-190">Cet exemple montre comment exécuter des commandes qui ont été masquées par des commandes importées.</span><span class="sxs-lookup"><span data-stu-id="49ce7-190">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="49ce7-191">Le module **TestModule** comprend une fonction nommée `Get-Date` qui retourne l’année et le jour de l’année.</span><span class="sxs-lookup"><span data-stu-id="49ce7-191">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

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

<span data-ttu-id="49ce7-192">La première `Get-Date` applet de commande retourne un objet **DateTime** avec la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="49ce7-192">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="49ce7-193">Après l’importation du module **TestModule** , `Get-Date` retourne l’année et le jour de l’année.</span><span class="sxs-lookup"><span data-stu-id="49ce7-193">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="49ce7-194">L’utilisation du paramètre **All** de `Get-Command` affiche toutes les `Get-Date` commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-194">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="49ce7-195">Les résultats montrent qu’il y a deux `Get-Date` commandes dans la session, une fonction du module **TestModule** et une applet de commande du module **Microsoft. PowerShell. Utility** .</span><span class="sxs-lookup"><span data-stu-id="49ce7-195">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="49ce7-196">Comme les fonctions sont prioritaires sur les applets de commande, la `Get-Date` fonction du module **TestModule** s’exécute à la place de l’applet de commande `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="49ce7-196">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="49ce7-197">Pour exécuter la version d’origine de `Get-Date` , vous devez qualifier le nom de la commande avec le nom du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-197">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="49ce7-198">Pour plus d’informations sur la priorité des commandes dans PowerShell, consultez [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-198">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="49ce7-199">Exemple 10 : importer une version minimale d’un module</span><span class="sxs-lookup"><span data-stu-id="49ce7-199">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="49ce7-200">Cet exemple importe le module **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="49ce7-200">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="49ce7-201">Elle utilise le paramètre **MinimumVersion** de `Import-Module` pour importer uniquement la version 2.0.0 ou ultérieure du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-201">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="49ce7-202">Vous pouvez également utiliser le paramètre **RequiredVersion** pour importer une version particulière d’un module, ou utiliser les paramètres **module** et **version** du `#Requires` mot clé pour exiger une version particulière d’un module dans un script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-202">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="49ce7-203">Exemple 11 : importer à l’aide d’un nom complet</span><span class="sxs-lookup"><span data-stu-id="49ce7-203">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="49ce7-204">Cet exemple importe une version spécifique d’un module à l’aide de FullyQualifiedName.</span><span class="sxs-lookup"><span data-stu-id="49ce7-204">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

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

### <span data-ttu-id="49ce7-205">Exemple 12 : importer à l’aide d’un chemin d’accès complet</span><span class="sxs-lookup"><span data-stu-id="49ce7-205">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="49ce7-206">Cet exemple importe une version spécifique d’un module à l’aide du chemin d’accès qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="49ce7-206">This example imports a specific version of a module using the fully qualified path.</span></span>

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

### <span data-ttu-id="49ce7-207">Exemple 13 : importer un module à partir d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="49ce7-207">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="49ce7-208">Cet exemple montre comment utiliser l' `Import-Module` applet de commande pour importer un module à partir d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-208">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="49ce7-209">Cette commande utilise la fonctionnalité de communication à distance implicite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49ce7-209">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="49ce7-210">Quand vous importez des modules à partir d'une autre session, vous pouvez utiliser les applets de commande dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-210">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="49ce7-211">Toutefois, les commandes qui utilisent les applets de commande s’exécutent dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="49ce7-211">However, commands that use the cmdlets run in the remote session.</span></span>

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

<span data-ttu-id="49ce7-212">`New-PSSession` crée une session à distance (**PSSession**) sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="49ce7-212">`New-PSSession` creates a remote session (**PSSession**) to the Server01 computer.</span></span> <span data-ttu-id="49ce7-213">La **session PSSession** est enregistrée dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="49ce7-213">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="49ce7-214">Le `Get-Module` fait d’exécuter avec le paramètre **PSSession** indique que le module **netsecurity** est installé et disponible sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-214">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="49ce7-215">Cette commande revient à utiliser l' `Invoke-Command` applet de commande pour exécuter la `Get-Module` commande dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="49ce7-215">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="49ce7-216">Par exemple : (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="49ce7-216">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="49ce7-217">L’exécution `Import-Module` de avec le paramètre **PSSession** importe le module **netsecurity** à partir de l’ordinateur distant dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-217">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="49ce7-218">L' `Get-Command` applet de commande est utilisée pour récupérer les commandes qui commencent par le **pare-feu** d' **extraction** et d’inclusion dans le module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="49ce7-218">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="49ce7-219">La sortie confirme que le module et ses applets de commande ont été importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-219">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="49ce7-220">Ensuite, l' `Get-NetFirewallRule` applet de commande obtient Windows Remote Management règles de pare-feu sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="49ce7-220">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="49ce7-221">Cela équivaut à utiliser l' `Invoke-Command` applet de commande pour s’exécuter `Get-NetFirewallRule` sur la session à distance.</span><span class="sxs-lookup"><span data-stu-id="49ce7-221">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="49ce7-222">Exemple 14 : gérer le stockage sur un ordinateur distant sans système d’exploitation Windows</span><span class="sxs-lookup"><span data-stu-id="49ce7-222">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="49ce7-223">Dans cet exemple, l’administrateur de l’ordinateur a installé le fournisseur WMI de détection de module, qui vous permet d’utiliser des commandes CIM conçues pour le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="49ce7-223">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="49ce7-224">L' `New-CimSession` applet de commande crée une session sur l’ordinateur distant nommé RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="49ce7-224">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="49ce7-225">La session se connecte au service WMI sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-225">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="49ce7-226">La session CIM est enregistrée dans la `$cs` variable.</span><span class="sxs-lookup"><span data-stu-id="49ce7-226">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="49ce7-227">`Import-Module` utilise le **CimSession** dans `$cs` pour importer le module CIM de **stockage** à partir de l’ordinateur RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="49ce7-227">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="49ce7-228">L' `Get-Command` applet `Get-Disk` de commande affiche la commande dans le module de **stockage** .</span><span class="sxs-lookup"><span data-stu-id="49ce7-228">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="49ce7-229">Lorsque vous importez un module CIM dans la session locale, PowerShell convertit les fichiers CDXML pour chaque commande en scripts PowerShell, qui apparaissent sous la forme de fonctions dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="49ce7-229">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="49ce7-230">Bien que `Get-Disk` soit tapé dans la session locale, l’applet de commande s’exécute implicitement sur l’ordinateur distant à partir duquel elle a été importée.</span><span class="sxs-lookup"><span data-stu-id="49ce7-230">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="49ce7-231">La commande retourne des objets de l’ordinateur distant à la session locale.</span><span class="sxs-lookup"><span data-stu-id="49ce7-231">The command returns objects from the remote computer to the local session.</span></span>

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

## <span data-ttu-id="49ce7-232">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="49ce7-232">PARAMETERS</span></span>

### <span data-ttu-id="49ce7-233">-Alias</span><span class="sxs-lookup"><span data-stu-id="49ce7-233">-Alias</span></span>

<span data-ttu-id="49ce7-234">Spécifie les alias que cette applet de commande importe à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-234">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="49ce7-235">Entrez une liste séparée par des virgules des alias.</span><span class="sxs-lookup"><span data-stu-id="49ce7-235">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="49ce7-236">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-236">Wildcard characters are permitted.</span></span>

<span data-ttu-id="49ce7-237">Au moment de leur importation, certains modules exportent automatiquement les alias sélectionnés dans votre session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-237">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="49ce7-238">Ce paramètre vous permet d'effectuer votre choix parmi les alias exportés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-238">This parameter lets you select from among the exported aliases.</span></span>

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

### <span data-ttu-id="49ce7-239">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="49ce7-239">-ArgumentList</span></span>

<span data-ttu-id="49ce7-240">Spécifie un tableau d’arguments, ou valeurs de paramètre, qui sont passés à un module de script pendant la `Import-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="49ce7-240">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="49ce7-241">Ce paramètre n’est valide que lorsque vous importez un module de script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-241">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="49ce7-242">Vous pouvez également faire référence au paramètre **argumentlist** par son alias, **args**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-242">You can also refer to the **ArgumentList** parameter by its alias, **args**.</span></span> <span data-ttu-id="49ce7-243">Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="49ce7-243">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="49ce7-244">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="49ce7-244">-AsCustomObject</span></span>

<span data-ttu-id="49ce7-245">Indique que cette applet de commande retourne un objet personnalisé avec des membres qui représentent les membres de module importés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-245">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="49ce7-246">Ce paramètre n'est valide que pour les modules de script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-246">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="49ce7-247">Quand vous utilisez le paramètre **AsCustomObject** , `Import-Module` importe les membres de module dans la session, puis retourne un objet **PSCustomObject** au lieu d’un objet **PSModuleInfo** .</span><span class="sxs-lookup"><span data-stu-id="49ce7-247">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="49ce7-248">Vous pouvez enregistrer l'objet personnalisé dans une variable et utiliser la notation par points pour appeler les membres.</span><span class="sxs-lookup"><span data-stu-id="49ce7-248">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

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

### <span data-ttu-id="49ce7-249">-Assembly</span><span class="sxs-lookup"><span data-stu-id="49ce7-249">-Assembly</span></span>

<span data-ttu-id="49ce7-250">Spécifie un tableau d’objets d’assembly.</span><span class="sxs-lookup"><span data-stu-id="49ce7-250">Specifies an array of assembly objects.</span></span> <span data-ttu-id="49ce7-251">Cette applet de commande importe les applets de commande et les fournisseurs implémentés dans les objets d’assembly spécifiés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-251">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="49ce7-252">Entrez une variable qui contient les objets d'assembly ou une commande qui crée des objets d'assembly.</span><span class="sxs-lookup"><span data-stu-id="49ce7-252">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="49ce7-253">Vous pouvez également diriger un objet assembly vers `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="49ce7-253">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="49ce7-254">Quand vous utilisez ce paramètre, seuls les applets de commande et les fournisseurs implémentés par les assemblys spécifiés sont importés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-254">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="49ce7-255">Si le module contient d’autres fichiers, ils ne sont pas importés et il se peut que vous ne soyez pas membre important du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-255">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="49ce7-256">Utilisez ce paramètre pour déboguer et tester le module, ou quand vous êtes invité à l’utiliser par l’auteur du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-256">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

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

### <span data-ttu-id="49ce7-257">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="49ce7-257">-CimNamespace</span></span>

<span data-ttu-id="49ce7-258">Spécifie l'espace de noms d'un autre fournisseur CIM qui expose des modules CIM.</span><span class="sxs-lookup"><span data-stu-id="49ce7-258">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="49ce7-259">La valeur par défaut est l'espace de noms du fournisseur WMI pour la découverte de module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-259">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="49ce7-260">Utilisez ce paramètre pour importer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas un système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="49ce7-260">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="49ce7-261">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="49ce7-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="49ce7-262">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="49ce7-262">-CimResourceUri</span></span>

<span data-ttu-id="49ce7-263">Spécifie un autre emplacement pour les modules CIM.</span><span class="sxs-lookup"><span data-stu-id="49ce7-263">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="49ce7-264">La valeur par défaut est l’URI de ressource du fournisseur WMI de détection de module sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-264">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="49ce7-265">Utilisez ce paramètre pour importer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas un système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="49ce7-265">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="49ce7-266">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="49ce7-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="49ce7-267">-CimSession</span><span class="sxs-lookup"><span data-stu-id="49ce7-267">-CimSession</span></span>

<span data-ttu-id="49ce7-268">Spécifie une session CIM sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-268">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="49ce7-269">Entrez une variable qui contient la session CIM ou une commande qui obtient la session CIM, telle qu’une commande [CimSession](../CimCmdlets/Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="49ce7-269">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="49ce7-270">`Import-Module` utilise la connexion de session CIM pour importer des modules à partir de l’ordinateur distant dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-270">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="49ce7-271">Lorsque vous utilisez les commandes du module importé dans la session active, les commandes s’exécutent sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-271">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="49ce7-272">Vous pouvez utiliser ce paramètre pour importer des modules à partir d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows, et d’ordinateurs Windows qui disposent de PowerShell, mais pour lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="49ce7-272">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="49ce7-273">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="49ce7-273">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="49ce7-274">-Applet de commande</span><span class="sxs-lookup"><span data-stu-id="49ce7-274">-Cmdlet</span></span>

<span data-ttu-id="49ce7-275">Spécifie un tableau d’applets de commande importées par cette applet de commande à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-275">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="49ce7-276">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-276">Wildcard characters are permitted.</span></span>

<span data-ttu-id="49ce7-277">Au moment de leur importation, certains modules exportent automatiquement les applets de commande sélectionnées dans votre session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-277">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="49ce7-278">Ce paramètre vous permet d'effectuer votre choix parmi les applets de commande exportées.</span><span class="sxs-lookup"><span data-stu-id="49ce7-278">This parameter lets you select from among the exported cmdlets.</span></span>

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

### <span data-ttu-id="49ce7-279">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="49ce7-279">-DisableNameChecking</span></span>

<span data-ttu-id="49ce7-280">Indique que cette applet de commande supprime le message qui vous avertit lorsque vous importez une applet de commande ou une fonction dont le nom comprend un verbe non approuvé ou un caractère interdit.</span><span class="sxs-lookup"><span data-stu-id="49ce7-280">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="49ce7-281">Par défaut, lorsqu’un module que vous importez exporte des applets de commande ou des fonctions qui ont des verbes non approuvés dans leurs noms, PowerShell affiche le message d’avertissement suivant :</span><span class="sxs-lookup"><span data-stu-id="49ce7-281">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="49ce7-282">AVERTISSEMENT : certains noms de commandes importés incluent des verbes non approuvés qui peuvent les rendre moins détectables.</span><span class="sxs-lookup"><span data-stu-id="49ce7-282">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="49ce7-283">Utilisez le paramètre Verbose pour obtenir plus d'informations ou tapez Get-Verb pour afficher la liste des verbes approuvés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-283">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="49ce7-284">Ce message n'est qu'un avertissement.</span><span class="sxs-lookup"><span data-stu-id="49ce7-284">This message is only a warning.</span></span> <span data-ttu-id="49ce7-285">Le module entier est toujours importé, y compris les commandes non conformes.</span><span class="sxs-lookup"><span data-stu-id="49ce7-285">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="49ce7-286">Bien que le message soit affiché aux utilisateurs du module, le problème d'affectation de noms doit être corrigé par l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-286">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="49ce7-287">-Force</span><span class="sxs-lookup"><span data-stu-id="49ce7-287">-Force</span></span>

<span data-ttu-id="49ce7-288">Ce paramètre entraîne le chargement ou le rechargement d’un module au-dessus de celui en cours.</span><span class="sxs-lookup"><span data-stu-id="49ce7-288">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

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

### <span data-ttu-id="49ce7-289">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="49ce7-289">-FullyQualifiedName</span></span>

<span data-ttu-id="49ce7-290">Spécifie le nom qualifié complet du module sous la forme d’une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="49ce7-290">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="49ce7-291">La valeur peut être une combinaison de chaînes et de tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="49ce7-291">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="49ce7-292">La table de hachage a les clés suivantes.</span><span class="sxs-lookup"><span data-stu-id="49ce7-292">The hash table has the following keys.</span></span>

- <span data-ttu-id="49ce7-293">`ModuleName` - **Obligatoire** Spécifie le nom du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-293">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="49ce7-294">`GUID` - **Facultatif** Spécifie le GUID du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-294">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="49ce7-295">Il est également **nécessaire** de spécifier l’une des trois clés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="49ce7-295">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="49ce7-296">Ces clés ne peuvent pas être utilisées ensemble.</span><span class="sxs-lookup"><span data-stu-id="49ce7-296">These keys can't be used together.</span></span>
  - <span data-ttu-id="49ce7-297">`ModuleVersion` -Spécifie une version minimale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-297">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="49ce7-298">`RequiredVersion` -Spécifie une version exacte et obligatoire du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-298">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="49ce7-299">`MaximumVersion` -Spécifie la version maximale acceptable du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-299">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

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

### <span data-ttu-id="49ce7-300">-Fonction</span><span class="sxs-lookup"><span data-stu-id="49ce7-300">-Function</span></span>

<span data-ttu-id="49ce7-301">Spécifie un tableau de fonctions que cette applet de commande importe à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-301">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="49ce7-302">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-302">Wildcard characters are permitted.</span></span> <span data-ttu-id="49ce7-303">Au moment de leur importation, certains modules exportent automatiquement les fonctions sélectionnées dans votre session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-303">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="49ce7-304">Ce paramètre vous permet d'effectuer votre choix parmi les fonctions exportées.</span><span class="sxs-lookup"><span data-stu-id="49ce7-304">This parameter lets you select from among the exported functions.</span></span>

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

### <span data-ttu-id="49ce7-305">-Global</span><span class="sxs-lookup"><span data-stu-id="49ce7-305">-Global</span></span>

<span data-ttu-id="49ce7-306">Indique que cette applet de commande importe des modules dans l’état de session global pour qu’ils soient disponibles pour toutes les commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-306">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="49ce7-307">Par défaut, lorsque l' `Import-Module` applet de commande est appelée à partir de l’invite de commandes, d’un fichier de script ou d’un scriptblock, toutes les commandes sont importées dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="49ce7-307">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="49ce7-308">Lorsqu’elle est appelée à partir d’un autre module, `Import-Module` l’applet de commande importe les commandes d’un module, y compris les commandes des modules imbriqués, dans l’état de session du module appelant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-308">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="49ce7-309">Vous devez éviter `Import-Module` d’appeler à partir d’un module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-309">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="49ce7-310">Au lieu de cela, déclarez le module cible comme un module imbriqué dans le manifeste du module parent.</span><span class="sxs-lookup"><span data-stu-id="49ce7-310">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="49ce7-311">La déclaration des modules imbriqués améliore la détectabilité des dépendances.</span><span class="sxs-lookup"><span data-stu-id="49ce7-311">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="49ce7-312">Le paramètre **Global** équivaut au paramètre **Scope** avec la valeur **Global**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-312">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="49ce7-313">Pour restreindre les commandes qu’un module exporte, utilisez une `Export-ModuleMember` commande dans le module de script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-313">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

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

### <span data-ttu-id="49ce7-314">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="49ce7-314">-MaximumVersion</span></span>

<span data-ttu-id="49ce7-315">Spécifie une version maximale.</span><span class="sxs-lookup"><span data-stu-id="49ce7-315">Specifies a maximum version.</span></span> <span data-ttu-id="49ce7-316">Cette applet de commande importe uniquement une version du module qui est inférieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="49ce7-316">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="49ce7-317">Si aucune version n’est qualifiée, `Import-Module` retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="49ce7-317">If no version qualifies, `Import-Module` returns an error.</span></span>

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

### <span data-ttu-id="49ce7-318">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="49ce7-318">-MinimumVersion</span></span>

<span data-ttu-id="49ce7-319">Spécifie une version minimale.</span><span class="sxs-lookup"><span data-stu-id="49ce7-319">Specifies a minimum version.</span></span> <span data-ttu-id="49ce7-320">Cette applet de commande importe uniquement une version du module qui est supérieure ou égale à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="49ce7-320">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="49ce7-321">Utilisez le nom de paramètre **MinimumVersion** ou son alias, **Version**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-321">Use the **MinimumVersion** parameter name or its alias, **Version**.</span></span> <span data-ttu-id="49ce7-322">Si aucune version n’est qualifiée, `Import-Module` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="49ce7-322">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="49ce7-323">Pour spécifier une version exacte, utilisez le paramètre **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-323">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="49ce7-324">Vous pouvez également utiliser les paramètres **module** et **version** du mot clé **#Requires** pour exiger une version spécifique d’un module dans un script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-324">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="49ce7-325">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="49ce7-325">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="49ce7-326">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="49ce7-326">-ModuleInfo</span></span>

<span data-ttu-id="49ce7-327">Spécifie un tableau d’objets de module à importer.</span><span class="sxs-lookup"><span data-stu-id="49ce7-327">Specifies an array of module objects to import.</span></span> <span data-ttu-id="49ce7-328">Entrez une variable qui contient les objets de module ou une commande qui obtient les objets de module, tels que la commande suivante : `Get-Module -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="49ce7-328">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="49ce7-329">Vous pouvez également diriger les objets de module vers `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="49ce7-329">You can also pipe module objects to `Import-Module`.</span></span>

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

### <span data-ttu-id="49ce7-330">-Name</span><span class="sxs-lookup"><span data-stu-id="49ce7-330">-Name</span></span>

<span data-ttu-id="49ce7-331">Spécifie les noms des modules à importer.</span><span class="sxs-lookup"><span data-stu-id="49ce7-331">Specifies the names of the modules to import.</span></span> <span data-ttu-id="49ce7-332">Entrez le nom du module ou le nom d’un fichier dans le module, tel qu’un `.psd1` fichier, `.psm1` , `.dll` ou `.ps1` .</span><span class="sxs-lookup"><span data-stu-id="49ce7-332">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="49ce7-333">Les chemins d'accès aux fichiers sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="49ce7-333">File paths are optional.</span></span> <span data-ttu-id="49ce7-334">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-334">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="49ce7-335">Vous pouvez également diriger les noms de module et les noms de fichiers vers `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="49ce7-335">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="49ce7-336">Si vous omettez un chemin d’accès, `Import-Module` recherche le module dans les chemins d’accès enregistrés dans la `$env:PSModulePath` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="49ce7-336">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="49ce7-337">Spécifiez uniquement le nom du module chaque fois que possible.</span><span class="sxs-lookup"><span data-stu-id="49ce7-337">Specify only the module name whenever possible.</span></span> <span data-ttu-id="49ce7-338">Quand vous spécifiez un nom de fichier, seuls les membres qui sont implémentés dans ce fichier sont importés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-338">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="49ce7-339">Si le module contient d’autres fichiers, ils ne sont pas importés et il se peut que vous ne soyez pas membre important du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-339">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="49ce7-340">Bien qu’il soit possible d’importer un fichier de script ( `.ps1` ) en tant que module, les fichiers de script ne sont généralement pas structurés comme un fichier de modules de script ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="49ce7-340">While it is possible to import a script (`.ps1`) file as a module, script files are usually not structured like script modules file (`.psm1`) file.</span></span> <span data-ttu-id="49ce7-341">L’importation d’un fichier de script ne garantit pas qu’il est utilisable en tant que module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-341">Importing a script file does not guarantee that it is usable as a module.</span></span> <span data-ttu-id="49ce7-342">Pour plus d’informations, consultez [about_Modules](about/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-342">For more information, see [about_Modules](about/about_Modules.md).</span></span>

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

### <span data-ttu-id="49ce7-343">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="49ce7-343">-NoClobber</span></span>

<span data-ttu-id="49ce7-344">Empêche l’importation des commandes qui ont les mêmes noms que les commandes existantes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-344">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="49ce7-345">Par défaut, `Import-Module` importe toutes les commandes de module exportées.</span><span class="sxs-lookup"><span data-stu-id="49ce7-345">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="49ce7-346">Les commandes qui ont le même nom peuvent masquer ou remplacer des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-346">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="49ce7-347">Pour éviter les conflits de nom de commande dans une session, utilisez les paramètres **Prefix** ou **NoClobber**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-347">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="49ce7-348">Pour plus d'informations sur les conflits de nom et la priorité des commandes, consultez « Modules et conflits de noms » dans [about_Modules](about/about_Modules.md) et [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-348">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="49ce7-349">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="49ce7-349">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="49ce7-350">-PassThru</span><span class="sxs-lookup"><span data-stu-id="49ce7-350">-PassThru</span></span>

<span data-ttu-id="49ce7-351">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="49ce7-351">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="49ce7-352">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="49ce7-352">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="49ce7-353">-Prefix</span><span class="sxs-lookup"><span data-stu-id="49ce7-353">-Prefix</span></span>

<span data-ttu-id="49ce7-354">Spécifie un préfixe que cette applet de commande ajoute aux noms des membres de module importés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-354">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="49ce7-355">Utilisez ce paramètre pour éviter les conflits de noms qui peuvent se produire quand des membres différents dans la session ont le même nom.</span><span class="sxs-lookup"><span data-stu-id="49ce7-355">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="49ce7-356">Ce paramètre ne modifie pas le module, et il n’affecte pas les fichiers que le module importe pour son propre usage.</span><span class="sxs-lookup"><span data-stu-id="49ce7-356">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="49ce7-357">Ils sont appelés modules imbriqués.</span><span class="sxs-lookup"><span data-stu-id="49ce7-357">These are known as nested modules.</span></span> <span data-ttu-id="49ce7-358">Cette applet de commande affecte uniquement les noms des membres dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-358">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="49ce7-359">Par exemple, si vous spécifiez le préfixe UTC, puis importez une applet de commande `Get-Date` , l’applet de commande est connue dans la session en tant que `Get-UTCDate` , et elle n’est pas confondue avec l’applet de commande d’origine `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="49ce7-359">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="49ce7-360">La valeur de ce paramètre est prioritaire sur la propriété **DefaultCommandPrefix** du module, qui spécifie le préfixe par défaut.</span><span class="sxs-lookup"><span data-stu-id="49ce7-360">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

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

### <span data-ttu-id="49ce7-361">-PSSession</span><span class="sxs-lookup"><span data-stu-id="49ce7-361">-PSSession</span></span>

<span data-ttu-id="49ce7-362">Spécifie une session PowerShell managée par l’utilisateur (**PSSession**) à partir de laquelle cette applet de commande importe des modules dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-362">Specifies a PowerShell user-managed session (**PSSession**) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="49ce7-363">Entrez une variable qui contient une **session PSSession** ou une commande qui obtient une **session PSSession**, telle qu’une `Get-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="49ce7-363">Enter a variable that contains a **PSSession** or a command that gets a **PSSession**, such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="49ce7-364">Quand vous importez un module à partir d'une autre session dans la session active, vous pouvez utiliser les applets de commande du module dans la session active, tout comme vous utiliseriez des applets de commande à partir d'un module local.</span><span class="sxs-lookup"><span data-stu-id="49ce7-364">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="49ce7-365">Les commandes qui utilisent les applets de commande distantes s’exécutent dans la session à distance, mais les détails de l’accès distant sont gérés en arrière-plan par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49ce7-365">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="49ce7-366">Ce paramètre utilise la fonctionnalité de communication à distance implicite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49ce7-366">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="49ce7-367">Cela équivaut à utiliser l' `Import-PSSession` applet de commande pour importer des modules particuliers à partir d’une session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-367">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="49ce7-368">`Import-Module` Impossible d’importer les modules PowerShell Core à partir d’une autre session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-368">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="49ce7-369">Les modules PowerShell Core portent des noms qui commencent par Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49ce7-369">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="49ce7-370">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="49ce7-370">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="49ce7-371">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="49ce7-371">-RequiredVersion</span></span>

<span data-ttu-id="49ce7-372">Spécifie une version du module que cette applet de commande importe.</span><span class="sxs-lookup"><span data-stu-id="49ce7-372">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="49ce7-373">Si la version n’est pas installée, `Import-Module` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="49ce7-373">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="49ce7-374">Par défaut, `Import-Module` importe le module sans vérifier le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="49ce7-374">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="49ce7-375">Pour spécifier une version minimale, utilisez le paramètre **MinimumVersion**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-375">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="49ce7-376">Vous pouvez également utiliser les paramètres **module** et **version** du mot clé **#Requires** pour exiger une version spécifique d’un module dans un script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-376">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="49ce7-377">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="49ce7-377">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="49ce7-378">Les scripts qui utilisent **RequiredVersion** pour importer des modules inclus avec les versions existantes du système d’exploitation Windows ne s’exécutent pas automatiquement dans les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="49ce7-378">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="49ce7-379">En effet, les numéros de version de module PowerShell dans les versions ultérieures du système d’exploitation Windows sont plus élevés que les numéros de version de module dans les versions existantes du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="49ce7-379">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

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

### <span data-ttu-id="49ce7-380">-Étendue</span><span class="sxs-lookup"><span data-stu-id="49ce7-380">-Scope</span></span>

<span data-ttu-id="49ce7-381">Spécifie une étendue dans laquelle cette applet de commande importe le module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-381">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="49ce7-382">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="49ce7-382">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="49ce7-383">**Global**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-383">**Global**.</span></span> <span data-ttu-id="49ce7-384">disponible pour toutes les commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-384">Available to all commands in the session.</span></span> <span data-ttu-id="49ce7-385">Équivalent au paramètre **Global**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-385">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="49ce7-386">**Local**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-386">**Local**.</span></span> <span data-ttu-id="49ce7-387">Disponible uniquement dans l'étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="49ce7-387">Available only in the current scope.</span></span>

<span data-ttu-id="49ce7-388">Par défaut, lorsque l' `Import-Module` applet de commande est appelée à partir de l’invite de commandes, d’un fichier de script ou d’un scriptblock, toutes les commandes sont importées dans l’état de session global.</span><span class="sxs-lookup"><span data-stu-id="49ce7-388">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="49ce7-389">Vous pouvez utiliser le `-Scope Local` paramètre pour importer le contenu d’un module dans la portée du script ou du scriptblock.</span><span class="sxs-lookup"><span data-stu-id="49ce7-389">You can use the `-Scope Local` parameter to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="49ce7-390">Lorsqu’elle est appelée à partir d’un autre module, `Import-Module` l’applet de commande importe les commandes d’un module, y compris les commandes des modules imbriqués, dans l’état de session de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-390">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="49ce7-391">La spécification de `-Scope Global` ou `-Global` indique que cette applet de commande importe des modules dans l’état de session global pour qu’ils soient disponibles pour toutes les commandes de la session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-391">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="49ce7-392">Le paramètre **Global** équivaut au paramètre **Scope** avec la valeur **Global**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-392">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="49ce7-393">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="49ce7-393">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="49ce7-394">-Variable</span><span class="sxs-lookup"><span data-stu-id="49ce7-394">-Variable</span></span>

<span data-ttu-id="49ce7-395">Spécifie un tableau de variables que cette applet de commande importe du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-395">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="49ce7-396">Entrez une liste de variables.</span><span class="sxs-lookup"><span data-stu-id="49ce7-396">Enter a list of variables.</span></span> <span data-ttu-id="49ce7-397">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-397">Wildcard characters are permitted.</span></span>

<span data-ttu-id="49ce7-398">Au moment de leur importation, certains modules exportent automatiquement les variables sélectionnées dans votre session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-398">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="49ce7-399">Ce paramètre vous permet d'effectuer votre choix parmi les variables exportées.</span><span class="sxs-lookup"><span data-stu-id="49ce7-399">This parameter lets you select from among the exported variables.</span></span>

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

### <span data-ttu-id="49ce7-400">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="49ce7-400">-SkipEditionCheck</span></span>

<span data-ttu-id="49ce7-401">Ignore la vérification sur le `CompatiblePSEditions` champ.</span><span class="sxs-lookup"><span data-stu-id="49ce7-401">Skips the check on the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="49ce7-402">Permet de charger un module à partir du `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` répertoire du module dans PowerShell Core quand ce module ne spécifie pas `Core` dans le `CompatiblePSEditions` champ de manifeste.</span><span class="sxs-lookup"><span data-stu-id="49ce7-402">Allows loading a module from the `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory into PowerShell Core when that module does not specify `Core` in the `CompatiblePSEditions` manifest field.</span></span>

<span data-ttu-id="49ce7-403">Lorsque vous importez un module à partir d’un autre chemin d’accès, ce commutateur n’a aucun effet, car la vérification n’est pas effectuée.</span><span class="sxs-lookup"><span data-stu-id="49ce7-403">When importing a module from another path, this switch does nothing, since the check is not performed.</span></span> <span data-ttu-id="49ce7-404">Sur Linux et macOS, ce commutateur ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="49ce7-404">On Linux and macOS, this switch does nothing.</span></span>

<span data-ttu-id="49ce7-405">Pour plus d’informations, consultez [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-405">For more information, see [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span></span>

> [!WARNING]
> <span data-ttu-id="49ce7-406">`Import-Module -SkipEditionCheck` l’importation d’un module risque toujours d’échouer.</span><span class="sxs-lookup"><span data-stu-id="49ce7-406">`Import-Module -SkipEditionCheck` is still likely to fail to import a module.</span></span> <span data-ttu-id="49ce7-407">Même si elle réussit, l’appel d’une commande à partir du module peut échouer plus tard lorsqu’elle essaie d’utiliser une API incompatible.</span><span class="sxs-lookup"><span data-stu-id="49ce7-407">Even if it does succeed, invoking a command from the module may later fail when it tries to use an incompatible API.</span></span>

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

### <span data-ttu-id="49ce7-408">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="49ce7-408">-UseWindowsPowerShell</span></span>

<span data-ttu-id="49ce7-409">Charge le module à l’aide de la fonctionnalité de compatibilité Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49ce7-409">Loads module using Windows PowerShell Compatibility functionality.</span></span> <span data-ttu-id="49ce7-410">Pour plus d’informations, consultez [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) .</span><span class="sxs-lookup"><span data-stu-id="49ce7-410">See [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) for more information.</span></span>

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

### <span data-ttu-id="49ce7-411">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49ce7-411">CommonParameters</span></span>

<span data-ttu-id="49ce7-412">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="49ce7-412">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49ce7-413">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="49ce7-413">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49ce7-414">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="49ce7-414">INPUTS</span></span>

### <span data-ttu-id="49ce7-415">System. String, System. Management. Automation. PSModuleInfo, System. Reflection. assembly</span><span class="sxs-lookup"><span data-stu-id="49ce7-415">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="49ce7-416">Vous pouvez diriger un nom de module, un objet de module ou un objet d’assembly vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="49ce7-416">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="49ce7-417">SORTIES</span><span class="sxs-lookup"><span data-stu-id="49ce7-417">OUTPUTS</span></span>

### <span data-ttu-id="49ce7-418">None, System. Management. Automation. PSModuleInfo ou System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="49ce7-418">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="49ce7-419">Par défaut, `Import-Module` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="49ce7-419">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="49ce7-420">Si vous spécifiez le paramètre **PassThru** , l’applet de commande génère un objet **System. Management. Automation. PSModuleInfo** qui représente le module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-420">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="49ce7-421">Si vous spécifiez le paramètre **AsCustomObject** , il génère un objet **PSCustomObject** .</span><span class="sxs-lookup"><span data-stu-id="49ce7-421">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="49ce7-422">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="49ce7-422">NOTES</span></span>

- <span data-ttu-id="49ce7-423">Avant de pouvoir importer un module, le module doit être installé sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="49ce7-423">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="49ce7-424">Autrement dit, le répertoire de module doit être copié vers un répertoire qui est accessible à votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="49ce7-424">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="49ce7-425">Pour plus d’informations, consultez [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-425">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="49ce7-426">Vous pouvez également utiliser les paramètres **PSSession** et **CIMSession** pour importer des modules qui sont installés sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="49ce7-426">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="49ce7-427">Toutefois, les commandes qui utilisent les applets de commande dans ces modules s’exécutent dans la session à distance sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="49ce7-427">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="49ce7-428">Si vous importez des membres portant le même nom et le même type dans votre session, PowerShell utilise par défaut le membre importé en dernier.</span><span class="sxs-lookup"><span data-stu-id="49ce7-428">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="49ce7-429">Les variables et les alias sont remplacés, et les originaux ne sont pas accessibles.</span><span class="sxs-lookup"><span data-stu-id="49ce7-429">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="49ce7-430">Les fonctions, les applets de commande et les fournisseurs sont simplement occultés par les nouveaux membres.</span><span class="sxs-lookup"><span data-stu-id="49ce7-430">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="49ce7-431">Ils sont accessibles en qualifiant le nom de commande avec le nom de son composant logiciel enfichable, module ou chemin d’accès de fonction.</span><span class="sxs-lookup"><span data-stu-id="49ce7-431">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="49ce7-432">Pour mettre à jour les données de mise en forme pour les commandes qui ont été importées à partir d’un module, utilisez l’applet de commande `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="49ce7-432">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="49ce7-433">`Update-FormatData` met également à jour les données de mise en forme pour les commandes de la session qui ont été importées à partir de modules.</span><span class="sxs-lookup"><span data-stu-id="49ce7-433">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="49ce7-434">Si le fichier de mise en forme d’un module est modifié, vous pouvez exécuter une `Update-FormatData` commande pour mettre à jour les données de mise en forme des commandes importées.</span><span class="sxs-lookup"><span data-stu-id="49ce7-434">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="49ce7-435">Vous n’avez pas besoin de réimporter le module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-435">You don't need to import the module again.</span></span>

- <span data-ttu-id="49ce7-436">À compter de Windows PowerShell 3,0, les commandes de base qui sont installées avec PowerShell sont empaquetées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="49ce7-436">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="49ce7-437">Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables (**PSSnapins**).</span><span class="sxs-lookup"><span data-stu-id="49ce7-437">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins (**PSSnapins**).</span></span> <span data-ttu-id="49ce7-438">L’exception est **Microsoft. PowerShell. Core**, qui est toujours un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="49ce7-438">The exception is **Microsoft.PowerShell.Core**, which is always a snap-in.</span></span> <span data-ttu-id="49ce7-439">En outre, les sessions à distance, telles que celles démarrées par l’applet de commande `New-PSSession` , sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.</span><span class="sxs-lookup"><span data-stu-id="49ce7-439">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="49ce7-440">Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez la [méthode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span><span class="sxs-lookup"><span data-stu-id="49ce7-440">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="49ce7-441">Dans Windows PowerShell 2,0, certaines des valeurs de propriété de l’objet de module, telles que les valeurs de propriété **ExportedCmdlets** et **NestedModules** , n’ont pas été remplies tant que le module n’a pas été importé.</span><span class="sxs-lookup"><span data-stu-id="49ce7-441">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported.</span></span>

- <span data-ttu-id="49ce7-442">Si vous tentez d’importer un module qui contient des assemblys en mode mixte qui ne sont pas compatibles avec Windows PowerShell 3.0, `Import-Module` retourne un message d’erreur semblable à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="49ce7-442">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0+, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="49ce7-443">Import-Module : l’assembly en mode mixte est généré avec la version’v 2.0.50727 'du runtime et ne peut pas être chargé dans le runtime 4,0 sans informations de configuration supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="49ce7-443">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="49ce7-444">Cette erreur se produit lorsqu’un module conçu pour Windows PowerShell 2,0 contient au moins un assembly de module mixte.</span><span class="sxs-lookup"><span data-stu-id="49ce7-444">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly.</span></span> <span data-ttu-id="49ce7-445">Assembly de module mixte qui comprend du code managé et non managé, tel que C++ et C#.</span><span class="sxs-lookup"><span data-stu-id="49ce7-445">A mixed-module assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="49ce7-446">Pour importer un module qui contient des assemblys en mode mixte, démarrez Windows PowerShell 2,0 à l’aide de la commande suivante, puis réessayez d’exécuter la `Import-Module` commande.</span><span class="sxs-lookup"><span data-stu-id="49ce7-446">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="49ce7-447">Pour utiliser la fonctionnalité de session CIM, l'ordinateur distant doit disposer de l'accès distant WS-Management et de Windows Management Instrumentation (WMI), qui est l'implémentation Microsoft du modèle CIM (Common Information Model) standard.</span><span class="sxs-lookup"><span data-stu-id="49ce7-447">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="49ce7-448">L'ordinateur doit également disposer du fournisseur WMI pour la découverte de module ou un autre fournisseur CIM qui a les mêmes fonctionnalités de base.</span><span class="sxs-lookup"><span data-stu-id="49ce7-448">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="49ce7-449">Vous pouvez utiliser la fonctionnalité de session CIM sur les ordinateurs qui n’exécutent pas de système d’exploitation Windows et sur les ordinateurs Windows qui disposent de PowerShell, mais pour lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="49ce7-449">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="49ce7-450">Vous pouvez également utiliser les paramètres CIM pour obtenir des modules CIM à partir d’ordinateurs sur lesquels la communication à distance PowerShell est activée, y compris l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="49ce7-450">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="49ce7-451">Lorsque vous créez une session CIM sur l’ordinateur local, PowerShell utilise DCOM au lieu de WMI pour créer la session.</span><span class="sxs-lookup"><span data-stu-id="49ce7-451">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="49ce7-452">Par défaut, `Import-Module` importe les modules dans la portée globale même en cas d’appel à partir d’une portée descendante.</span><span class="sxs-lookup"><span data-stu-id="49ce7-452">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="49ce7-453">L’étendue de niveau supérieur et toutes les portées descendantes ont accès aux éléments exportés du module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-453">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="49ce7-454">Dans une portée descendante, `-Scope Local` limite l’importation à cette portée et à toutes ses étendues descendantes.</span><span class="sxs-lookup"><span data-stu-id="49ce7-454">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="49ce7-455">Les étendues parentes ne voient pas les membres importés.</span><span class="sxs-lookup"><span data-stu-id="49ce7-455">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="49ce7-456">`Get-Module` affiche tous les modules chargés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="49ce7-456">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="49ce7-457">Cela comprend les modules chargés localement dans une portée descendante.</span><span class="sxs-lookup"><span data-stu-id="49ce7-457">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="49ce7-458">Utilisez `Get-Command -Module modulename` pour voir quels membres sont chargés dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="49ce7-458">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="49ce7-459">`Import-Module` ne charge pas les définitions de classe et d’énumération dans le module.</span><span class="sxs-lookup"><span data-stu-id="49ce7-459">`Import-Module` does not load class and enum definitions in the module.</span></span> <span data-ttu-id="49ce7-460">Utilisez l' `using module` instruction au début de votre script.</span><span class="sxs-lookup"><span data-stu-id="49ce7-460">Use the `using module` statement at the beginning of your script.</span></span> <span data-ttu-id="49ce7-461">Cela importe le module, y compris les définitions de classe et d’énumération.</span><span class="sxs-lookup"><span data-stu-id="49ce7-461">This imports the module, including the class and enum definitions.</span></span> <span data-ttu-id="49ce7-462">Pour plus d’informations, consultez [about_Using](About/about_Using.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-462">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="49ce7-463">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="49ce7-463">RELATED LINKS</span></span>

[<span data-ttu-id="49ce7-464">about_Modules</span><span class="sxs-lookup"><span data-stu-id="49ce7-464">about_Modules</span></span>](about/about_Modules.md)

[<span data-ttu-id="49ce7-465">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="49ce7-465">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="49ce7-466">Get-Module</span><span class="sxs-lookup"><span data-stu-id="49ce7-466">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="49ce7-467">New-Module</span><span class="sxs-lookup"><span data-stu-id="49ce7-467">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="49ce7-468">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="49ce7-468">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="49ce7-469">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="49ce7-469">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
