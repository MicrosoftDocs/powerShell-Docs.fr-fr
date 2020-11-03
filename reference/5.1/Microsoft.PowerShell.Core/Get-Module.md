---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 4098b40c01085b266fa279107e5795b1283705cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202301"
---
# <span data-ttu-id="e1dfd-103">Get-Module</span><span class="sxs-lookup"><span data-stu-id="e1dfd-103">Get-Module</span></span>

## <span data-ttu-id="e1dfd-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e1dfd-104">SYNOPSIS</span></span>
<span data-ttu-id="e1dfd-105">Obtient les modules qui ont été importés ou peuvent être importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-105">Gets the modules that have been imported or that can be imported into the current session.</span></span>

## <span data-ttu-id="e1dfd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1dfd-106">SYNTAX</span></span>

### <span data-ttu-id="e1dfd-107">Loaded (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="e1dfd-107">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="e1dfd-108">Disponible</span><span class="sxs-lookup"><span data-stu-id="e1dfd-108">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="e1dfd-109">PsSession</span><span class="sxs-lookup"><span data-stu-id="e1dfd-109">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="e1dfd-110">CimSession</span><span class="sxs-lookup"><span data-stu-id="e1dfd-110">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable] [-Refresh]
 -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>] [<CommonParameters>]
```

## <span data-ttu-id="e1dfd-111">Description</span><span class="sxs-lookup"><span data-stu-id="e1dfd-111">DESCRIPTION</span></span>

<span data-ttu-id="e1dfd-112">L' `Get-Module` applet de commande obtient les modules PowerShell qui ont été importés ou qui peuvent être importés dans une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-112">The `Get-Module` cmdlet gets the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span>
<span data-ttu-id="e1dfd-113">L’objet de module qui `Get-Module` retourne contient des informations précieuses sur le module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-113">The module object that `Get-Module` returns contains valuable information about the module.</span></span>
<span data-ttu-id="e1dfd-114">Vous pouvez également diriger les objets de module vers d’autres applets de commande, telles que les `Import-Module` applets de commande et `Remove-Module` .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-114">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="e1dfd-115">Sans paramètres, `Get-Module` obtient les modules qui ont été importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-115">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span>
<span data-ttu-id="e1dfd-116">Pour récupérer tous les modules installés, spécifiez le paramètre **listAvailable** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-116">To get all installed modules, specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="e1dfd-117">`Get-Module` Obtient les modules, mais ne les importe pas.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-117">`Get-Module` gets modules, but it does not import them.</span></span>
<span data-ttu-id="e1dfd-118">À compter de Windows PowerShell 3,0, les modules sont importés automatiquement lorsque vous utilisez une commande dans le module, mais une `Get-Module` commande ne déclenche pas d’importation automatique.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-118">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span>
<span data-ttu-id="e1dfd-119">Vous pouvez également importer les modules dans votre session à l’aide de l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-119">You can also import the modules into your session by using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="e1dfd-120">À compter de Windows PowerShell 3,0, vous pouvez importer et importer des modules à partir de sessions à distance dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-120">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span>
<span data-ttu-id="e1dfd-121">Cette stratégie utilise la fonctionnalité de communication à distance implicite de PowerShell et équivaut à utiliser l’applet de commande `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-121">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="e1dfd-122">Lorsque vous utilisez des commandes dans des modules importés à partir d’une autre session, les commandes s’exécutent implicitement dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-122">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="e1dfd-123">Cette fonctionnalité vous permet de gérer l’ordinateur distant à partir de la session locale.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-123">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="e1dfd-124">En outre, à compter de Windows PowerShell 3,0, vous pouvez utiliser `Get-Module` et `Import-Module` pour récupérer et importer des modules Common Information Model (CIM), dans lesquels les applets de commande sont définies dans des fichiers de définition d’applet de commande (CDXML).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-124">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span>
<span data-ttu-id="e1dfd-125">Cette fonctionnalité vous permet d’utiliser des applets de commande qui sont implémentées dans des assemblys de code non managé, telles que celles écrites en C++.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="e1dfd-126">Grâce à ces nouvelles fonctionnalités, `Get-Module` les `Import-Module` applets de commande et deviennent des outils principaux pour gérer des entreprises hétérogènes qui incluent des ordinateurs qui exécutent le système d’exploitation Windows et les ordinateurs qui exécutent d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-126">With these new features, the `Get-Module` and `Import-Module` cmdlets become primary tools for managing heterogeneous enterprises that include computers that run the Windows operating system and computers that run other operating systems.</span></span>

<span data-ttu-id="e1dfd-127">Pour gérer les ordinateurs distants qui exécutent le système d’exploitation Windows pour lequel PowerShell et la communication à distance PowerShell sont activés, créez une **session PSSession** sur l’ordinateur distant, puis utilisez le paramètre **PSSession** de `Get-Module` pour obtenir les modules PowerShell dans la **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-127">To manage remote computers that run the Windows operating system that have PowerShell and PowerShell remoting enabled, create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the **PSSession** .</span></span>
<span data-ttu-id="e1dfd-128">Lorsque vous importez les modules, puis utilisez les commandes importées dans la session active, les commandes s’exécutent implicitement dans la session **PSSession** sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-128">When you import the modules, and then use the imported commands in the current session, the commands run implicitly in the **PSSession** on the remote computer.</span></span>
<span data-ttu-id="e1dfd-129">Vous pouvez utiliser cette stratégie pour gérer l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-129">You can use this strategy to manage the remote computer.</span></span>

<span data-ttu-id="e1dfd-130">Vous pouvez utiliser une stratégie similaire pour gérer les ordinateurs sur lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-130">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="e1dfd-131">Celles-ci incluent les ordinateurs qui n’exécutent pas le système d’exploitation Windows et les ordinateurs qui disposent de PowerShell mais sur lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-131">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="e1dfd-132">Commencez par créer une session CIM sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-132">Start by creating a CIM session on the remote computer.</span></span>
<span data-ttu-id="e1dfd-133">Une session CIM est une connexion à Windows Management Instrumentation (WMI) sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-133">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>
<span data-ttu-id="e1dfd-134">Utilisez ensuite le paramètre **CIMSession** de `Get-Module` pour récupérer les modules CIM à partir de la session CIM.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-134">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span>
<span data-ttu-id="e1dfd-135">Lorsque vous importez un module CIM à l’aide de l' `Import-Module` applet de commande, puis exécutez les commandes importées, les commandes s’exécutent implicitement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-135">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span>
<span data-ttu-id="e1dfd-136">Vous pouvez utiliser cette stratégie WMI et CIM pour gérer l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-136">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="e1dfd-137">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e1dfd-137">EXAMPLES</span></span>

### <span data-ttu-id="e1dfd-138">Exemple 1 : récupérer les modules importés dans la session active</span><span class="sxs-lookup"><span data-stu-id="e1dfd-138">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="e1dfd-139">Cette commande obtient les modules qui ont été importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-139">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="e1dfd-140">Exemple 2 : récupérer les modules installés et les modules disponibles</span><span class="sxs-lookup"><span data-stu-id="e1dfd-140">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="e1dfd-141">Cette commande obtient les modules qui sont installés sur l'ordinateur et peuvent être importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-141">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="e1dfd-142">`Get-Module` recherche les modules disponibles dans le chemin d’accès spécifié par la variable d’environnement **$env :P smodulepath** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-142">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span>
<span data-ttu-id="e1dfd-143">Pour plus d'informations sur **PSModulePath** , consultez [about_Modules](About/about_Modules.md) et [about_Environment_Variables](About/about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-143">For more information about **PSModulePath** , see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="e1dfd-144">Exemple 3 : récupération de tous les fichiers exportés</span><span class="sxs-lookup"><span data-stu-id="e1dfd-144">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="e1dfd-145">Cette commande obtient tous les fichiers exportés pour tous les modules disponibles.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-145">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="e1dfd-146">Exemple 4 : obtenir un module par son nom complet</span><span class="sxs-lookup"><span data-stu-id="e1dfd-146">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="e1dfd-147">Cette commande obtient le module **Microsoft. PowerShell. Management** en spécifiant le nom complet du module à l’aide du paramètre **FullyQualifiedName** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-147">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span>
<span data-ttu-id="e1dfd-148">La commande dirige ensuite les résultats vers l' `Format-Table` applet de commande pour mettre en forme les résultats sous la forme d’une table dont le **nom** et la **version** sont les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-148">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="e1dfd-149">Exemple 5 : obtenir les propriétés d’un module</span><span class="sxs-lookup"><span data-stu-id="e1dfd-149">Example 5: Get properties of a module</span></span>

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

<span data-ttu-id="e1dfd-150">Cette commande obtient les propriétés de l’objet **PSModuleInfo** `Get-Module` retourné par.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-150">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span>
<span data-ttu-id="e1dfd-151">Il existe un objet pour chaque fichier de module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-151">There is one object for each module file.</span></span>

<span data-ttu-id="e1dfd-152">Vous pouvez utiliser les propriétés pour mettre en forme et filtrer les objets de module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-152">You can use the properties to format and filter the module objects.</span></span>
<span data-ttu-id="e1dfd-153">Pour plus d’informations sur les propriétés, consultez [Propriétés de PSModuleInfo](/dotnet/api/system.management.automation.psmoduleinfo).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-153">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="e1dfd-154">La sortie comprend les nouvelles propriétés, telles que **Author** et **CompanyName** , qui ont été introduites dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-154">The output includes the new properties, such as **Author** and **CompanyName** , that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="e1dfd-155">Exemple 6 : regrouper tous les modules par nom</span><span class="sxs-lookup"><span data-stu-id="e1dfd-155">Example 6: Group all modules by name</span></span>

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

<span data-ttu-id="e1dfd-156">Cette commande obtient tous les fichiers de module, importés et disponibles, puis les regroupe par nom de module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-156">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="e1dfd-157">Cela vous permet d'afficher les fichiers de module exportés par chaque script.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-157">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="e1dfd-158">Exemple 7 : afficher le contenu d’un manifeste de module</span><span class="sxs-lookup"><span data-stu-id="e1dfd-158">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="e1dfd-159">Ces commandes affichent le contenu du manifeste de module pour le module **BitsTransfer** de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-159">These commands display the contents of the module manifest for the Windows PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="e1dfd-160">Les modules n’ont pas besoin d’avoir des fichiers manifestes.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-160">Modules are not required to have manifest files.</span></span>
<span data-ttu-id="e1dfd-161">Lorsqu’ils ont un fichier manifeste, le fichier manifeste est requis uniquement pour inclure un numéro de version.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-161">When they do have a manifest file, the manifest file is required only to include a version number.</span></span>
<span data-ttu-id="e1dfd-162">Toutefois, les fichiers manifeste fournissent souvent des informations utiles sur un module, ses spécifications et son contenu.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-162">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

<span data-ttu-id="e1dfd-163">La première commande obtient l'objet PSModuleInfo qui représente le module BitsTransfer.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-163">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="e1dfd-164">Elle enregistre l’objet dans la `$m` variable.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-164">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="e1dfd-165">La deuxième commande utilise l' `Get-Content` applet de commande pour récupérer le contenu du fichier manifeste dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-165">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="e1dfd-166">Elle utilise la notation par points pour obtenir le chemin d'accès du fichier manifeste, stocké dans la propriété Path de l'objet.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-166">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="e1dfd-167">La sortie affiche le contenu du manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-167">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="e1dfd-168">Exemple 8 : répertorier les fichiers dans le répertoire du module</span><span class="sxs-lookup"><span data-stu-id="e1dfd-168">Example 8: List files in module directory</span></span>

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

<span data-ttu-id="e1dfd-169">Cette commande répertorie les fichiers dans le répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-169">This command lists the files in the directory of the module.</span></span>
<span data-ttu-id="e1dfd-170">Il s'agit d'une autre façon de déterminer ce que contient le module avant son importation.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-170">This is another way to determine what is in a module before you import it.</span></span>
<span data-ttu-id="e1dfd-171">Certains modules peuvent avoir des fichiers d'aide ou des fichiers Lisez-moi qui décrivent le module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-171">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="e1dfd-172">Exemple 9 : obtenir les modules installés sur un ordinateur</span><span class="sxs-lookup"><span data-stu-id="e1dfd-172">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="e1dfd-173">Ces commandes obtiennent les modules installés sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-173">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="e1dfd-174">La première commande utilise l' `New-PSSession` applet de commande pour créer une **session PSSession** sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-174">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="e1dfd-175">La commande enregistre la **session PSSession** dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-175">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="e1dfd-176">La deuxième commande utilise les paramètres **PSSession** et **listAvailable** de `Get-Module` pour récupérer les modules dans la **session PSSession** dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-176">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="e1dfd-177">Si vous dirigez des modules à partir d’autres sessions vers l’applet de commande `Import-Module` , `Import-Module` importe le module dans la session active à l’aide de la fonctionnalité de communication à distance implicite.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-177">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span>
<span data-ttu-id="e1dfd-178">Cela équivaut à utiliser l’applet de commande `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-178">This is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="e1dfd-179">Vous pouvez utiliser les applets de commande du module dans la session active, mais les commandes qui utilisent ces applets de commande s'exécutent en réalité dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-179">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span>
<span data-ttu-id="e1dfd-180">Pour plus d’informations, consultez [`Import-Module`](Import-Module.md) et [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-180">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="e1dfd-181">Exemple 10 : gérer un ordinateur qui n’exécute pas le système d’exploitation Windows</span><span class="sxs-lookup"><span data-stu-id="e1dfd-181">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="e1dfd-182">Les commandes de cet exemple vous permettent de gérer les systèmes de stockage d’un ordinateur distant qui n’exécute pas le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-182">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="e1dfd-183">Dans cet exemple, comme l'administrateur de l'ordinateur a installé le fournisseur WMI pour la découverte de module, les commandes CIM peuvent utiliser les valeurs par défaut, qui sont conçues pour le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-183">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

<span data-ttu-id="e1dfd-184">La première commande utilise l' `New-CimSession` applet de commande pour créer une session sur l’ordinateur distant RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-184">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="e1dfd-185">La session se connecte à WMI sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-185">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="e1dfd-186">La commande enregistre la session CIM dans la `$cs` variable.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-186">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="e1dfd-187">La deuxième commande utilise la session CIM dans la `$cs` variable pour exécuter une `Get-Module` commande sur l’ordinateur RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-187">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="e1dfd-188">La commande utilise le paramètre Name pour spécifier le module Storage.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-188">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="e1dfd-189">La commande utilise un opérateur de pipeline (|) pour envoyer le module de stockage à l’applet de commande `Import-Module` , qui l’importe dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-189">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="e1dfd-190">La troisième commande exécute l' `Get-Command` applet de commande sur la `Get-Disk` commande dans le module Storage.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-190">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="e1dfd-191">Lorsque vous importez un module CIM dans la session locale, PowerShell convertit les fichiers CDXML qui représentent le module CIM en scripts PowerShell, qui apparaissent sous la forme de fonctions dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-191">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="e1dfd-192">La quatrième commande exécute la `Get-Disk` commande.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-192">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="e1dfd-193">Bien que la commande soit tapée dans la session locale, elle s'exécute implicitement sur l'ordinateur distant à partir duquel elle a été importée.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-193">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="e1dfd-194">La commande récupère des objets de l'ordinateur distant et les retourne à la session locale.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-194">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="e1dfd-195">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1dfd-195">PARAMETERS</span></span>

### <span data-ttu-id="e1dfd-196">-All</span><span class="sxs-lookup"><span data-stu-id="e1dfd-196">-All</span></span>

<span data-ttu-id="e1dfd-197">Indique que cette applet de commande obtient tous les modules de chaque dossier de module, y compris les modules imbriqués, les fichiers manifeste (. psd1), les fichiers de module de script (. psm1) et les fichiers de module binaire (. dll).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-197">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span>
<span data-ttu-id="e1dfd-198">Sans ce paramètre, `Get-Module` obtient uniquement le module par défaut dans chaque dossier de module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-198">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1dfd-199">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="e1dfd-199">-CimNamespace</span></span>

<span data-ttu-id="e1dfd-200">Spécifie l'espace de noms d'un autre fournisseur CIM qui expose des modules CIM.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-200">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span>
<span data-ttu-id="e1dfd-201">La valeur par défaut est l'espace de noms du fournisseur WMI pour la découverte de module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-201">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="e1dfd-202">Utilisez ce paramètre pour récupérer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-202">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="e1dfd-203">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e1dfd-204">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="e1dfd-204">-CimResourceUri</span></span>

<span data-ttu-id="e1dfd-205">Spécifie un autre emplacement pour les modules CIM.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-205">Specifies an alternate location for CIM modules.</span></span>
<span data-ttu-id="e1dfd-206">La valeur par défaut est l’URI de ressource du fournisseur WMI de détection de module sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-206">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="e1dfd-207">Utilisez ce paramètre pour récupérer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-207">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="e1dfd-208">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e1dfd-209">-CimSession</span><span class="sxs-lookup"><span data-stu-id="e1dfd-209">-CimSession</span></span>

<span data-ttu-id="e1dfd-210">Spécifie une session CIM sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-210">Specifies a CIM session on the remote computer.</span></span>
<span data-ttu-id="e1dfd-211">Entrez une variable qui contient la session CIM ou une commande qui obtient la session CIM, telle qu’une commande [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-211">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="e1dfd-212">`Get-Module` utilise la connexion de session CIM pour récupérer les modules à partir de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-212">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span>
<span data-ttu-id="e1dfd-213">Lorsque vous importez le module à l’aide de l' `Import-Module` applet de commande et que vous utilisez les commandes du module importé dans la session active, les commandes s’exécutent en réalité sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-213">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="e1dfd-214">Vous pouvez utiliser ce paramètre pour obtenir des modules d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows, ainsi que des ordinateurs qui ont PowerShell, mais sur lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-214">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="e1dfd-215">Le paramètre **CimSession** obtient tous les modules de la session **CIMSession** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-215">The **CimSession** parameter gets all modules in the **CIMSession** .</span></span>
<span data-ttu-id="e1dfd-216">Toutefois, vous pouvez importer uniquement les modules CIM ou CDXML (Cmdlet Definition XML).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-216">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

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

### <span data-ttu-id="e1dfd-217">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e1dfd-217">-FullyQualifiedName</span></span>

<span data-ttu-id="e1dfd-218">Spécifie les noms des modules sous la forme d’objets **ModuleSpecification** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-218">Specifies names of modules in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="e1dfd-219">Ces objets sont décrits dans la section Notes du [constructeur ModuleSpecification (Hashtable)](https://msdn.microsoft.com/library/jj136290) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-219">These objects are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library.</span></span>
<span data-ttu-id="e1dfd-220">Par exemple, le paramètre **FullyQualifiedName** accepte un nom de module qui est spécifié dans les formats suivants :</span><span class="sxs-lookup"><span data-stu-id="e1dfd-220">For example, the **FullyQualifiedName** parameter accepts a module name that is specified in the following formats:</span></span>

- <span data-ttu-id="e1dfd-221">@ {ModuleName = "ModuleName"; ModuleVersion = "version_number"}</span><span class="sxs-lookup"><span data-stu-id="e1dfd-221">@{ModuleName = "modulename"; ModuleVersion = "version_number"}</span></span>
- <span data-ttu-id="e1dfd-222">@ {ModuleName = "ModuleName"; ModuleVersion = "version_number"; Guid = "GUID"}</span><span class="sxs-lookup"><span data-stu-id="e1dfd-222">@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}</span></span>

<span data-ttu-id="e1dfd-223">**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-223">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="e1dfd-224">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedName** dans la même commande qu’un paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-224">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

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

### <span data-ttu-id="e1dfd-225">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="e1dfd-225">-ListAvailable</span></span>

<span data-ttu-id="e1dfd-226">Indique que cette applet de commande obtient tous les modules installés.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-226">Indicates that this cmdlet gets all installed modules.</span></span>
<span data-ttu-id="e1dfd-227">`Get-Module` Obtient les modules dans les chemins d’accès figurant dans la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-227">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span>
<span data-ttu-id="e1dfd-228">Sans ce paramètre, `Get-Module` obtient uniquement les modules répertoriés dans la variable d’environnement **PSModulePath** et qui sont chargés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-228">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span>
<span data-ttu-id="e1dfd-229">**ListAvailable** ne retourne pas d'informations sur les modules qui ne figurent pas dans la variable d'environnement **PSModulePath** , même si ces modules sont chargés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-229">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1dfd-230">-Name</span><span class="sxs-lookup"><span data-stu-id="e1dfd-230">-Name</span></span>

<span data-ttu-id="e1dfd-231">Spécifie les noms ou modèles de nom des modules que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-231">Specifies names or name patterns of modules that this cmdlet gets.</span></span>
<span data-ttu-id="e1dfd-232">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-232">Wildcard characters are permitted.</span></span>
<span data-ttu-id="e1dfd-233">Vous pouvez également rediriger les noms vers `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-233">You can also pipe the names to `Get-Module`.</span></span>
<span data-ttu-id="e1dfd-234">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedName** dans la même commande qu’un paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-234">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="e1dfd-235">Le **nom** ne peut pas accepter un GUID de module comme valeur.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-235">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="e1dfd-236">Pour retourner des modules en spécifiant un GUID, utilisez **FullyQualifiedName** à la place.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-236">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="e1dfd-237">-PSEdition</span><span class="sxs-lookup"><span data-stu-id="e1dfd-237">-PSEdition</span></span>

<span data-ttu-id="e1dfd-238">Obtient les modules qui prennent en charge l’édition spécifiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-238">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="e1dfd-239">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="e1dfd-239">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e1dfd-240">Bureau</span><span class="sxs-lookup"><span data-stu-id="e1dfd-240">Desktop</span></span>
- <span data-ttu-id="e1dfd-241">Core</span><span class="sxs-lookup"><span data-stu-id="e1dfd-241">Core</span></span>

<span data-ttu-id="e1dfd-242">L’applet de commande Get-Module vérifie la propriété **CompatiblePSEditions** de l’objet **PSModuleInfo** pour la valeur spécifiée et retourne uniquement les modules qui l’ont définie.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-242">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="e1dfd-243">**Édition Desktop :** repose sur le .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et Bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-243">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
> - <span data-ttu-id="e1dfd-244">**Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-244">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

```yaml
Type: System.String
Parameter Sets: PsSession, Available
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1dfd-245">-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1dfd-245">-PSSession</span></span>

<span data-ttu-id="e1dfd-246">Obtient les modules de la session PowerShell managée par l’utilisateur spécifiée ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-246">Gets the modules in the specified user-managed PowerShell session ( **PSSession** ).</span></span>
<span data-ttu-id="e1dfd-247">Entrez une variable qui contient la session, une commande qui obtient la session, telle qu’une `Get-PSSession` commande, ou une commande qui crée la session, telle qu’une `New-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-247">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="e1dfd-248">Lorsque la session est connectée à un ordinateur distant, vous devez spécifier le paramètre **listAvailable** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-248">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="e1dfd-249">Une `Get-Module` commande qui utilise le paramètre **PSSession** équivaut à utiliser l' `Invoke-Command` applet de commande pour exécuter une `Get-Module -ListAvailable` commande dans une **session PSSession** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-249">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession** .</span></span>

<span data-ttu-id="e1dfd-250">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-250">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1dfd-251">-Actualiser</span><span class="sxs-lookup"><span data-stu-id="e1dfd-251">-Refresh</span></span>

<span data-ttu-id="e1dfd-252">Indique que cette applet de commande actualise le cache des commandes installées.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-252">Indicates that this cmdlet refreshes the cache of installed commands.</span></span>
<span data-ttu-id="e1dfd-253">Le cache de commande est créé au démarrage de la session.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-253">The command cache is created when the session starts.</span></span>
<span data-ttu-id="e1dfd-254">Elle permet `Get-Command` à l’applet de commande d’extraire des commandes des modules qui ne sont pas importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-254">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="e1dfd-255">Ce paramètre est conçu pour le développement et les scénarios de test dans lesquels le contenu des modules a changé depuis le début de la session.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-255">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="e1dfd-256">Lorsque vous spécifiez le paramètre **Refresh** dans une commande, vous devez spécifier **listAvailable** .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-256">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable** .</span></span>

<span data-ttu-id="e1dfd-257">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PsSession, Available, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1dfd-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1dfd-258">CommonParameters</span></span>

<span data-ttu-id="e1dfd-259">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1dfd-260">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1dfd-261">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e1dfd-261">INPUTS</span></span>

### <span data-ttu-id="e1dfd-262">System.String</span><span class="sxs-lookup"><span data-stu-id="e1dfd-262">System.String</span></span>

<span data-ttu-id="e1dfd-263">Vous pouvez diriger les noms de module vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-263">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="e1dfd-264">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e1dfd-264">OUTPUTS</span></span>

### <span data-ttu-id="e1dfd-265">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="e1dfd-265">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="e1dfd-266">Cette applet de commande retourne des objets qui représentent des modules.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-266">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="e1dfd-267">Lorsque vous spécifiez le paramètre **listAvailable** , `Get-Module` retourne un objet **ModuleInfoGrouping** , qui est un type d’objet **PSModuleInfo** qui a les mêmes propriétés et méthodes.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-267">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="e1dfd-268">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e1dfd-268">NOTES</span></span>

- <span data-ttu-id="e1dfd-269">À compter de Windows PowerShell 3,0, les commandes de base qui sont incluses dans PowerShell sont empaquetées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-269">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="e1dfd-270">L’exception est **Microsoft. PowerShell. Core** , qui est un composant logiciel enfichable ( **PSSnapin** ).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-270">The exception is **Microsoft.PowerShell.Core** , which is a snap-in ( **PSSnapin** ).</span></span> <span data-ttu-id="e1dfd-271">Par défaut, seul le composant logiciel enfichable **Microsoft.PowerShell.Core** est ajouté à la session.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-271">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span>
<span data-ttu-id="e1dfd-272">Les modules sont importés automatiquement à la première utilisation, et vous pouvez utiliser l' `Import-Module` applet de commande pour les importer.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-272">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>
- <span data-ttu-id="e1dfd-273">À compter de Windows PowerShell 3,0, les commandes de base qui sont installées avec PowerShell sont empaquetées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-273">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="e1dfd-274">Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables ( **PSSnapins** ).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-274">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="e1dfd-275">L’exception est **Microsoft. PowerShell. Core** , qui est toujours un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-275">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="e1dfd-276">En outre, les sessions à distance, telles que celles démarrées par l’applet de commande `New-PSSession` , sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-276">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="e1dfd-277">Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez [méthode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) dans MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-277">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) in the MSDN library.</span></span>

- <span data-ttu-id="e1dfd-278">`Get-Module` Obtient uniquement les modules dans les emplacements stockés dans la valeur de la variable d’environnement **PSModulePath** ($env :P smodulepath).</span><span class="sxs-lookup"><span data-stu-id="e1dfd-278">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="e1dfd-279">Vous pouvez utiliser le paramètre **path** de l' `Import-Module` applet de commande pour importer des modules dans d’autres emplacements, mais vous ne pouvez pas les récupérer à l’aide de l’applet de commande `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="e1dfd-279">You can use the **Path** parameter of the `Import-Module` cmdlet to import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>
- <span data-ttu-id="e1dfd-280">En outre, à compter de PowerShell 3,0, de nouvelles propriétés ont été ajoutées à l’objet `Get-Module` retourné, ce qui facilite l’apprentissage des modules, même avant leur importation.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-280">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="e1dfd-281">Toutes les propriétés sont remplies avant l’importation.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-281">All properties are populated before importing.</span></span> <span data-ttu-id="e1dfd-282">Celles-ci incluent les propriétés **ExportedCommands** , **ExportedCmdlets** et **ExportedFunctions** qui répertorient les commandes exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-282">These include the **ExportedCommands** , **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>
- <span data-ttu-id="e1dfd-283">Le paramètre **listAvailable** obtient uniquement les modules correctement formés, c’est-à-dire les dossiers qui contiennent au moins un fichier dont le nom de base est identique au nom du dossier du module.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-283">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="e1dfd-284">Le nom de base est le nom sans l’extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-284">The base name is the name without the file name extension.</span></span> <span data-ttu-id="e1dfd-285">Les dossiers qui contiennent des fichiers portant des noms différents sont considérés comme des conteneurs, mais pas des modules.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-285">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="e1dfd-286">Pour obtenir les modules qui sont implémentés en tant que fichiers. dll, mais qui ne sont pas placés dans un dossier de module, spécifiez à la fois **listAvailable** et **tous** les paramètres.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-286">To get modules that are implemented as .dll files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="e1dfd-287">Pour utiliser la fonctionnalité de session CIM, l'ordinateur distant doit disposer de l'accès distant WS-Management et de Windows Management Instrumentation (WMI), qui est l'implémentation Microsoft du modèle CIM (Common Information Model) standard.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-287">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="e1dfd-288">L'ordinateur doit également disposer du fournisseur WMI pour la découverte de module ou d'un autre fournisseur WMI ayant les mêmes fonctionnalités de base.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-288">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="e1dfd-289">Vous pouvez utiliser la fonctionnalité de session CIM sur les ordinateurs qui n’exécutent pas le système d’exploitation Windows et sur les ordinateurs Windows qui disposent de PowerShell, mais sur lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-289">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="e1dfd-290">Vous pouvez également utiliser les paramètres CIM pour obtenir des modules CIM à partir d’ordinateurs sur lesquels la communication à distance PowerShell est activée.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-290">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="e1dfd-291">Cela comprend l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-291">This includes the local computer.</span></span>
<span data-ttu-id="e1dfd-292">Lorsque vous créez une session CIM sur l’ordinateur local, PowerShell utilise DCOM au lieu de WMI pour créer la session.</span><span class="sxs-lookup"><span data-stu-id="e1dfd-292">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="e1dfd-293">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e1dfd-293">RELATED LINKS</span></span>

[<span data-ttu-id="e1dfd-294">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="e1dfd-294">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="e1dfd-295">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="e1dfd-295">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="e1dfd-296">about_Modules</span><span class="sxs-lookup"><span data-stu-id="e1dfd-296">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="e1dfd-297">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1dfd-297">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="e1dfd-298">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="e1dfd-298">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="e1dfd-299">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1dfd-299">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="e1dfd-300">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1dfd-300">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="e1dfd-301">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="e1dfd-301">Remove-Module</span></span>](Remove-Module.md)
