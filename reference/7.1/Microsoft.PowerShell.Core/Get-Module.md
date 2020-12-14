---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 1f06d1e7114a84ea89097167b188ded605f81aa0
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564535"
---
# <span data-ttu-id="705f4-102">Get-Module</span><span class="sxs-lookup"><span data-stu-id="705f4-102">Get-Module</span></span>

## <span data-ttu-id="705f4-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="705f4-103">SYNOPSIS</span></span>
<span data-ttu-id="705f4-104">Répertorie les modules importés dans la session active ou qui peuvent être importés à partir du PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="705f4-104">List the modules imported in the current session or that can be imported from the PSModulePath.</span></span>

## <span data-ttu-id="705f4-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="705f4-105">SYNTAX</span></span>

### <span data-ttu-id="705f4-106">Loaded (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="705f4-106">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="705f4-107">Disponible</span><span class="sxs-lookup"><span data-stu-id="705f4-107">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="705f4-108">PsSession</span><span class="sxs-lookup"><span data-stu-id="705f4-108">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="705f4-109">CimSession</span><span class="sxs-lookup"><span data-stu-id="705f4-109">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="705f4-110">Description</span><span class="sxs-lookup"><span data-stu-id="705f4-110">DESCRIPTION</span></span>

<span data-ttu-id="705f4-111">L' `Get-Module` applet de commande répertorie les modules PowerShell qui ont été importés ou qui peuvent être importés dans une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="705f4-111">The `Get-Module` cmdlet lists the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span> <span data-ttu-id="705f4-112">Sans paramètres, `Get-Module` obtient les modules qui ont été importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="705f4-112">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span> <span data-ttu-id="705f4-113">Le paramètre **listAvailable** permet de répertorier les modules qui peuvent être importés à partir des chemins d’accès spécifiés dans la variable d’environnement PSModulePath ( `$env:PSModulePath` ).</span><span class="sxs-lookup"><span data-stu-id="705f4-113">The **ListAvailable** parameter is used to list the modules that are available to be imported from the paths specified in the PSModulePath environment variable (`$env:PSModulePath`).</span></span>

<span data-ttu-id="705f4-114">L’objet de module qui `Get-Module` retourne contient des informations précieuses sur le module.</span><span class="sxs-lookup"><span data-stu-id="705f4-114">The module object that `Get-Module` returns contains valuable information about the module.</span></span> <span data-ttu-id="705f4-115">Vous pouvez également diriger les objets de module vers d’autres applets de commande, telles que les `Import-Module` applets de commande et `Remove-Module` .</span><span class="sxs-lookup"><span data-stu-id="705f4-115">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="705f4-116">`Get-Module` répertorie les modules, mais ne les importe pas.</span><span class="sxs-lookup"><span data-stu-id="705f4-116">`Get-Module` lists modules, but it does not import them.</span></span> <span data-ttu-id="705f4-117">À compter de Windows PowerShell 3,0, les modules sont importés automatiquement lorsque vous utilisez une commande dans le module, mais une `Get-Module` commande ne déclenche pas d’importation automatique.</span><span class="sxs-lookup"><span data-stu-id="705f4-117">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span> <span data-ttu-id="705f4-118">Vous pouvez également importer les modules dans votre session à l’aide de l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="705f4-118">You can also import the modules into your session using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="705f4-119">À compter de Windows PowerShell 3,0, vous pouvez importer et importer des modules à partir de sessions à distance dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="705f4-119">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span> <span data-ttu-id="705f4-120">Cette stratégie utilise la fonctionnalité de communication à distance implicite de PowerShell et équivaut à utiliser l’applet de commande `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="705f4-120">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="705f4-121">Lorsque vous utilisez des commandes dans des modules importés à partir d’une autre session, les commandes s’exécutent implicitement dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="705f4-121">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="705f4-122">Cette fonctionnalité vous permet de gérer l’ordinateur distant à partir de la session locale.</span><span class="sxs-lookup"><span data-stu-id="705f4-122">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="705f4-123">En outre, à compter de Windows PowerShell 3,0, vous pouvez utiliser `Get-Module` et `Import-Module` pour récupérer et importer des modules Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="705f4-123">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules.</span></span> <span data-ttu-id="705f4-124">Les modules CIM définissent des applets de commande dans des fichiers CDXML (cmdlet Definition XML).</span><span class="sxs-lookup"><span data-stu-id="705f4-124">CIM modules define cmdlets in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="705f4-125">Cette fonctionnalité vous permet d’utiliser des applets de commande qui sont implémentées dans des assemblys de code non managé, telles que celles écrites en C++.</span><span class="sxs-lookup"><span data-stu-id="705f4-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="705f4-126">La communication à distance implicite peut être utilisée pour gérer des ordinateurs distants sur lesquels la communication à distance PowerShell est activée.</span><span class="sxs-lookup"><span data-stu-id="705f4-126">Implicit remoting can be used to manage remote computers that have PowerShell remoting enabled.</span></span>
<span data-ttu-id="705f4-127">Créez une session **PSSession** sur l’ordinateur distant, puis utilisez le paramètre **PSSession** de `Get-Module` pour obtenir les modules PowerShell dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="705f4-127">Create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the remote session.</span></span> <span data-ttu-id="705f4-128">Lorsque vous importez un module à partir de la session à distance, les commandes importées s’exécutent dans la session sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-128">When you import a module from the remote session the imported commands run in the session on the remote computer.</span></span>

<span data-ttu-id="705f4-129">Vous pouvez utiliser une stratégie similaire pour gérer les ordinateurs sur lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="705f4-129">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="705f4-130">Celles-ci incluent les ordinateurs qui n’exécutent pas le système d’exploitation Windows et les ordinateurs qui disposent de PowerShell mais sur lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="705f4-130">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="705f4-131">Commencez par créer une session CIM sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-131">Start by creating a CIM session on the remote computer.</span></span> <span data-ttu-id="705f4-132">Une session CIM est une connexion à Windows Management Instrumentation (WMI) sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-132">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span> <span data-ttu-id="705f4-133">Utilisez ensuite le paramètre **CIMSession** de `Get-Module` pour récupérer les modules CIM à partir de la session CIM.</span><span class="sxs-lookup"><span data-stu-id="705f4-133">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span> <span data-ttu-id="705f4-134">Lorsque vous importez un module CIM à l’aide de l' `Import-Module` applet de commande, puis exécutez les commandes importées, les commandes s’exécutent implicitement sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-134">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span> <span data-ttu-id="705f4-135">Vous pouvez utiliser cette stratégie WMI et CIM pour gérer l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-135">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="705f4-136">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="705f4-136">EXAMPLES</span></span>

### <span data-ttu-id="705f4-137">Exemple 1 : récupérer les modules importés dans la session active</span><span class="sxs-lookup"><span data-stu-id="705f4-137">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="705f4-138">Cette commande obtient les modules qui ont été importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="705f4-138">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="705f4-139">Exemple 2 : récupérer les modules installés et les modules disponibles</span><span class="sxs-lookup"><span data-stu-id="705f4-139">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="705f4-140">Cette commande obtient les modules qui sont installés sur l'ordinateur et peuvent être importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="705f4-140">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="705f4-141">`Get-Module` recherche les modules disponibles dans le chemin d’accès spécifié par la variable d’environnement **$env :P smodulepath** .</span><span class="sxs-lookup"><span data-stu-id="705f4-141">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span> <span data-ttu-id="705f4-142">Pour plus d'informations sur **PSModulePath**, consultez [about_Modules](About/about_Modules.md) et [about_Environment_Variables](About/about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="705f4-142">For more information about **PSModulePath**, see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="705f4-143">Exemple 3 : récupération de tous les fichiers exportés</span><span class="sxs-lookup"><span data-stu-id="705f4-143">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="705f4-144">Cette commande obtient tous les fichiers exportés pour tous les modules disponibles.</span><span class="sxs-lookup"><span data-stu-id="705f4-144">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="705f4-145">Exemple 4 : obtenir un module par son nom complet</span><span class="sxs-lookup"><span data-stu-id="705f4-145">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="705f4-146">Cette commande obtient le module **Microsoft. PowerShell. Management** en spécifiant le nom complet du module à l’aide du paramètre **FullyQualifiedName** .</span><span class="sxs-lookup"><span data-stu-id="705f4-146">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span> <span data-ttu-id="705f4-147">La commande dirige ensuite les résultats vers l' `Format-Table` applet de commande pour mettre en forme les résultats sous la forme d’une table dont le **nom** et la **version** sont les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="705f4-147">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="705f4-148">Exemple 5 : obtenir les propriétés d’un module</span><span class="sxs-lookup"><span data-stu-id="705f4-148">Example 5: Get properties of a module</span></span>

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

<span data-ttu-id="705f4-149">Cette commande obtient les propriétés de l’objet **PSModuleInfo** `Get-Module` retourné par.</span><span class="sxs-lookup"><span data-stu-id="705f4-149">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span> <span data-ttu-id="705f4-150">Il existe un objet pour chaque fichier de module.</span><span class="sxs-lookup"><span data-stu-id="705f4-150">There is one object for each module file.</span></span>

<span data-ttu-id="705f4-151">Vous pouvez utiliser les propriétés pour mettre en forme et filtrer les objets de module.</span><span class="sxs-lookup"><span data-stu-id="705f4-151">You can use the properties to format and filter the module objects.</span></span> <span data-ttu-id="705f4-152">Pour plus d’informations sur les propriétés, consultez [Propriétés de PSModuleInfo](/dotnet/api/system.management.automation.psmoduleinfo).</span><span class="sxs-lookup"><span data-stu-id="705f4-152">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="705f4-153">La sortie comprend les nouvelles propriétés, telles que **Author** et **CompanyName**, qui ont été introduites dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="705f4-153">The output includes the new properties, such as **Author** and **CompanyName**, that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="705f4-154">Exemple 6 : regrouper tous les modules par nom</span><span class="sxs-lookup"><span data-stu-id="705f4-154">Example 6: Group all modules by name</span></span>

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

<span data-ttu-id="705f4-155">Cette commande obtient tous les fichiers de module, importés et disponibles, puis les regroupe par nom de module.</span><span class="sxs-lookup"><span data-stu-id="705f4-155">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="705f4-156">Cela vous permet d'afficher les fichiers de module exportés par chaque script.</span><span class="sxs-lookup"><span data-stu-id="705f4-156">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="705f4-157">Exemple 7 : afficher le contenu d’un manifeste de module</span><span class="sxs-lookup"><span data-stu-id="705f4-157">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="705f4-158">Ces commandes affichent le contenu du manifeste de module pour le module **BitsTransfer** de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="705f4-158">These commands display the contents of the module manifest for the Windows PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="705f4-159">Les modules n’ont pas besoin d’avoir des fichiers manifestes.</span><span class="sxs-lookup"><span data-stu-id="705f4-159">Modules are not required to have manifest files.</span></span> <span data-ttu-id="705f4-160">Lorsqu’ils ont un fichier manifeste, le fichier manifeste est requis uniquement pour inclure un numéro de version.</span><span class="sxs-lookup"><span data-stu-id="705f4-160">When they do have a manifest file, the manifest file is required only to include a version number.</span></span> <span data-ttu-id="705f4-161">Toutefois, les fichiers manifeste fournissent souvent des informations utiles sur un module, ses spécifications et son contenu.</span><span class="sxs-lookup"><span data-stu-id="705f4-161">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

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

<span data-ttu-id="705f4-162">La première commande obtient l'objet PSModuleInfo qui représente le module BitsTransfer.</span><span class="sxs-lookup"><span data-stu-id="705f4-162">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="705f4-163">Elle enregistre l’objet dans la `$m` variable.</span><span class="sxs-lookup"><span data-stu-id="705f4-163">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="705f4-164">La deuxième commande utilise l' `Get-Content` applet de commande pour récupérer le contenu du fichier manifeste dans le chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="705f4-164">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="705f4-165">Elle utilise la notation par points pour obtenir le chemin d'accès du fichier manifeste, stocké dans la propriété Path de l'objet.</span><span class="sxs-lookup"><span data-stu-id="705f4-165">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="705f4-166">La sortie affiche le contenu du manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="705f4-166">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="705f4-167">Exemple 8 : répertorier les fichiers dans le répertoire du module</span><span class="sxs-lookup"><span data-stu-id="705f4-167">Example 8: List files in module directory</span></span>

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

<span data-ttu-id="705f4-168">Cette commande répertorie les fichiers dans le répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="705f4-168">This command lists the files in the directory of the module.</span></span> <span data-ttu-id="705f4-169">Il s'agit d'une autre façon de déterminer ce que contient le module avant son importation.</span><span class="sxs-lookup"><span data-stu-id="705f4-169">This is another way to determine what is in a module before you import it.</span></span> <span data-ttu-id="705f4-170">Certains modules peuvent avoir des fichiers d'aide ou des fichiers Lisez-moi qui décrivent le module.</span><span class="sxs-lookup"><span data-stu-id="705f4-170">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="705f4-171">Exemple 9 : obtenir les modules installés sur un ordinateur</span><span class="sxs-lookup"><span data-stu-id="705f4-171">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="705f4-172">Ces commandes obtiennent les modules installés sur l'ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="705f4-172">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="705f4-173">La première commande utilise l' `New-PSSession` applet de commande pour créer une **session PSSession** sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="705f4-173">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="705f4-174">La commande enregistre la **session PSSession** dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="705f4-174">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="705f4-175">La deuxième commande utilise les paramètres **PSSession** et **listAvailable** de `Get-Module` pour récupérer les modules dans la **session PSSession** dans la `$s` variable.</span><span class="sxs-lookup"><span data-stu-id="705f4-175">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="705f4-176">Si vous dirigez des modules à partir d’autres sessions vers l’applet de commande `Import-Module` , `Import-Module` importe le module dans la session active à l’aide de la fonctionnalité de communication à distance implicite.</span><span class="sxs-lookup"><span data-stu-id="705f4-176">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span> <span data-ttu-id="705f4-177">Cela équivaut à utiliser l’applet de commande `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="705f4-177">This is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="705f4-178">Vous pouvez utiliser les applets de commande du module dans la session active, mais les commandes qui utilisent ces applets de commande s'exécutent en réalité dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="705f4-178">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span> <span data-ttu-id="705f4-179">Pour plus d’informations, consultez [`Import-Module`](Import-Module.md) et [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span><span class="sxs-lookup"><span data-stu-id="705f4-179">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="705f4-180">Exemple 10 : gérer un ordinateur qui n’exécute pas le système d’exploitation Windows</span><span class="sxs-lookup"><span data-stu-id="705f4-180">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="705f4-181">Les commandes de cet exemple vous permettent de gérer les systèmes de stockage d’un ordinateur distant qui n’exécute pas le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="705f4-181">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="705f4-182">Dans cet exemple, comme l'administrateur de l'ordinateur a installé le fournisseur WMI pour la découverte de module, les commandes CIM peuvent utiliser les valeurs par défaut, qui sont conçues pour le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="705f4-182">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

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

<span data-ttu-id="705f4-183">La première commande utilise l' `New-CimSession` applet de commande pour créer une session sur l’ordinateur distant RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="705f4-183">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="705f4-184">La session se connecte à WMI sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-184">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="705f4-185">La commande enregistre la session CIM dans la `$cs` variable.</span><span class="sxs-lookup"><span data-stu-id="705f4-185">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="705f4-186">La deuxième commande utilise la session CIM dans la `$cs` variable pour exécuter une `Get-Module` commande sur l’ordinateur RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="705f4-186">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="705f4-187">La commande utilise le paramètre Name pour spécifier le module Storage.</span><span class="sxs-lookup"><span data-stu-id="705f4-187">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="705f4-188">La commande utilise un opérateur de pipeline (|) pour envoyer le module de stockage à l’applet de commande `Import-Module` , qui l’importe dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="705f4-188">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="705f4-189">La troisième commande exécute l' `Get-Command` applet de commande sur la `Get-Disk` commande dans le module Storage.</span><span class="sxs-lookup"><span data-stu-id="705f4-189">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="705f4-190">Lorsque vous importez un module CIM dans la session locale, PowerShell convertit les fichiers CDXML qui représentent le module CIM en scripts PowerShell, qui apparaissent sous la forme de fonctions dans la session locale.</span><span class="sxs-lookup"><span data-stu-id="705f4-190">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="705f4-191">La quatrième commande exécute la `Get-Disk` commande.</span><span class="sxs-lookup"><span data-stu-id="705f4-191">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="705f4-192">Bien que la commande soit tapée dans la session locale, elle s'exécute implicitement sur l'ordinateur distant à partir duquel elle a été importée.</span><span class="sxs-lookup"><span data-stu-id="705f4-192">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="705f4-193">La commande récupère des objets de l'ordinateur distant et les retourne à la session locale.</span><span class="sxs-lookup"><span data-stu-id="705f4-193">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="705f4-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="705f4-194">PARAMETERS</span></span>

### <span data-ttu-id="705f4-195">-All</span><span class="sxs-lookup"><span data-stu-id="705f4-195">-All</span></span>

<span data-ttu-id="705f4-196">Indique que cette applet de commande obtient tous les modules de chaque dossier de module, y compris les modules imbriqués, les fichiers manifeste (. psd1), les fichiers de module de script (. psm1) et les fichiers de module binaire (. dll).</span><span class="sxs-lookup"><span data-stu-id="705f4-196">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span> <span data-ttu-id="705f4-197">Sans ce paramètre, `Get-Module` obtient uniquement le module par défaut dans chaque dossier de module.</span><span class="sxs-lookup"><span data-stu-id="705f4-197">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

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

### <span data-ttu-id="705f4-198">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="705f4-198">-CimNamespace</span></span>

<span data-ttu-id="705f4-199">Spécifie l'espace de noms d'un autre fournisseur CIM qui expose des modules CIM.</span><span class="sxs-lookup"><span data-stu-id="705f4-199">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="705f4-200">La valeur par défaut est l'espace de noms du fournisseur WMI pour la découverte de module.</span><span class="sxs-lookup"><span data-stu-id="705f4-200">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="705f4-201">Utilisez ce paramètre pour récupérer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="705f4-201">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="705f4-202">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="705f4-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="705f4-203">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="705f4-203">-CimResourceUri</span></span>

<span data-ttu-id="705f4-204">Spécifie un autre emplacement pour les modules CIM.</span><span class="sxs-lookup"><span data-stu-id="705f4-204">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="705f4-205">La valeur par défaut est l’URI de ressource du fournisseur WMI de détection de module sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-205">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="705f4-206">Utilisez ce paramètre pour récupérer des modules CIM à partir d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="705f4-206">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="705f4-207">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="705f4-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="705f4-208">-CimSession</span><span class="sxs-lookup"><span data-stu-id="705f4-208">-CimSession</span></span>

<span data-ttu-id="705f4-209">Spécifie une session CIM sur l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-209">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="705f4-210">Entrez une variable qui contient la session CIM ou une commande qui obtient la session CIM, telle qu’une commande [CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="705f4-210">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="705f4-211">`Get-Module` utilise la connexion de session CIM pour récupérer les modules à partir de l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-211">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span> <span data-ttu-id="705f4-212">Lorsque vous importez le module à l’aide de l' `Import-Module` applet de commande et que vous utilisez les commandes du module importé dans la session active, les commandes s’exécutent en réalité sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="705f4-212">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="705f4-213">Vous pouvez utiliser ce paramètre pour obtenir des modules d’ordinateurs et d’appareils qui n’exécutent pas le système d’exploitation Windows, ainsi que des ordinateurs qui ont PowerShell, mais sur lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="705f4-213">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="705f4-214">Le paramètre **CimSession** obtient tous les modules de la session **CIMSession**.</span><span class="sxs-lookup"><span data-stu-id="705f4-214">The **CimSession** parameter gets all modules in the **CIMSession**.</span></span> <span data-ttu-id="705f4-215">Toutefois, vous pouvez importer uniquement les modules CIM ou CDXML (Cmdlet Definition XML).</span><span class="sxs-lookup"><span data-stu-id="705f4-215">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

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

### <span data-ttu-id="705f4-216">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="705f4-216">-FullyQualifiedName</span></span>

<span data-ttu-id="705f4-217">Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** .</span><span class="sxs-lookup"><span data-stu-id="705f4-217">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="705f4-218">Consultez la section Notes du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="705f4-218">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="705f4-219">Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié dans l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="705f4-219">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="705f4-220">**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="705f4-220">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="705f4-221">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** .</span><span class="sxs-lookup"><span data-stu-id="705f4-221">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="705f4-222">les deux paramètres s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="705f4-222">the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="705f4-223">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="705f4-223">-ListAvailable</span></span>

<span data-ttu-id="705f4-224">Indique que cette applet de commande obtient tous les modules installés.</span><span class="sxs-lookup"><span data-stu-id="705f4-224">Indicates that this cmdlet gets all installed modules.</span></span> <span data-ttu-id="705f4-225">`Get-Module` Obtient les modules dans les chemins d’accès figurant dans la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="705f4-225">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span> <span data-ttu-id="705f4-226">Sans ce paramètre, `Get-Module` obtient uniquement les modules répertoriés dans la variable d’environnement **PSModulePath** et qui sont chargés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="705f4-226">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span> <span data-ttu-id="705f4-227">**ListAvailable** ne retourne pas d'informations sur les modules qui ne figurent pas dans la variable d'environnement **PSModulePath**, même si ces modules sont chargés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="705f4-227">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

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

### <span data-ttu-id="705f4-228">-Name</span><span class="sxs-lookup"><span data-stu-id="705f4-228">-Name</span></span>

<span data-ttu-id="705f4-229">Spécifie les noms ou modèles de nom des modules que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="705f4-229">Specifies names or name patterns of modules that this cmdlet gets.</span></span> <span data-ttu-id="705f4-230">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="705f4-230">Wildcard characters are permitted.</span></span> <span data-ttu-id="705f4-231">Vous pouvez également rediriger les noms vers `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="705f4-231">You can also pipe the names to `Get-Module`.</span></span> <span data-ttu-id="705f4-232">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedName** dans la même commande qu’un paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="705f4-232">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="705f4-233">Le **nom** ne peut pas accepter un GUID de module comme valeur.</span><span class="sxs-lookup"><span data-stu-id="705f4-233">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="705f4-234">Pour retourner des modules en spécifiant un GUID, utilisez **FullyQualifiedName** à la place.</span><span class="sxs-lookup"><span data-stu-id="705f4-234">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

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

### <span data-ttu-id="705f4-235">-PSEdition</span><span class="sxs-lookup"><span data-stu-id="705f4-235">-PSEdition</span></span>

<span data-ttu-id="705f4-236">Obtient les modules qui prennent en charge l’édition spécifiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="705f4-236">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="705f4-237">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="705f4-237">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="705f4-238">Bureau</span><span class="sxs-lookup"><span data-stu-id="705f4-238">Desktop</span></span>
- <span data-ttu-id="705f4-239">Base</span><span class="sxs-lookup"><span data-stu-id="705f4-239">Core</span></span>

<span data-ttu-id="705f4-240">L’applet de commande Get-Module vérifie la propriété **CompatiblePSEditions** de l’objet **PSModuleInfo** pour la valeur spécifiée et retourne uniquement les modules qui l’ont définie.</span><span class="sxs-lookup"><span data-stu-id="705f4-240">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="705f4-241">**Édition Desktop :** repose sur .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et le Bureau Windows.</span><span class="sxs-lookup"><span data-stu-id="705f4-241">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
> - <span data-ttu-id="705f4-242">**Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="705f4-242">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

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

### <span data-ttu-id="705f4-243">-PSSession</span><span class="sxs-lookup"><span data-stu-id="705f4-243">-PSSession</span></span>

<span data-ttu-id="705f4-244">Obtient les modules de la session PowerShell managée par l’utilisateur spécifiée (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="705f4-244">Gets the modules in the specified user-managed PowerShell session (**PSSession**).</span></span> <span data-ttu-id="705f4-245">Entrez une variable qui contient la session, une commande qui obtient la session, telle qu’une `Get-PSSession` commande, ou une commande qui crée la session, telle qu’une `New-PSSession` commande.</span><span class="sxs-lookup"><span data-stu-id="705f4-245">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="705f4-246">Lorsque la session est connectée à un ordinateur distant, vous devez spécifier le paramètre **listAvailable** .</span><span class="sxs-lookup"><span data-stu-id="705f4-246">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="705f4-247">Une `Get-Module` commande qui utilise le paramètre **PSSession** équivaut à utiliser l' `Invoke-Command` applet de commande pour exécuter une `Get-Module -ListAvailable` commande dans une **session PSSession**.</span><span class="sxs-lookup"><span data-stu-id="705f4-247">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession**.</span></span>

<span data-ttu-id="705f4-248">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="705f4-248">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="705f4-249">-Actualiser</span><span class="sxs-lookup"><span data-stu-id="705f4-249">-Refresh</span></span>

<span data-ttu-id="705f4-250">Indique que cette applet de commande actualise le cache des commandes installées.</span><span class="sxs-lookup"><span data-stu-id="705f4-250">Indicates that this cmdlet refreshes the cache of installed commands.</span></span> <span data-ttu-id="705f4-251">Le cache de commande est créé au démarrage de la session.</span><span class="sxs-lookup"><span data-stu-id="705f4-251">The command cache is created when the session starts.</span></span> <span data-ttu-id="705f4-252">Elle permet `Get-Command` à l’applet de commande d’extraire des commandes des modules qui ne sont pas importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="705f4-252">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="705f4-253">Ce paramètre est conçu pour le développement et les scénarios de test dans lesquels le contenu des modules a changé depuis le début de la session.</span><span class="sxs-lookup"><span data-stu-id="705f4-253">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="705f4-254">Lorsque vous spécifiez le paramètre **Refresh** dans une commande, vous devez spécifier **listAvailable**.</span><span class="sxs-lookup"><span data-stu-id="705f4-254">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable**.</span></span>

<span data-ttu-id="705f4-255">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="705f4-255">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="705f4-256">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="705f4-256">-SkipEditionCheck</span></span>

<span data-ttu-id="705f4-257">Ignore la vérification du `CompatiblePSEditions` champ.</span><span class="sxs-lookup"><span data-stu-id="705f4-257">Skips the check of the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="705f4-258">Par défaut, Get-Module ignore les modules `%windir%\System32\WindowsPowerShell\v1.0\Modules` qui ne sont pas spécifiés dans `Core` le champ dans le répertoire `CompatiblePSEditions` .</span><span class="sxs-lookup"><span data-stu-id="705f4-258">By default, Get-Module will omit modules in the `%windir%\System32\WindowsPowerShell\v1.0\Modules` directory that do not specify `Core` in the `CompatiblePSEditions` field.</span></span> <span data-ttu-id="705f4-259">Lorsque ce commutateur est défini, les modules sans `Core` sont inclus, de sorte que les modules sous le chemin d’accès du module Windows PowerShell qui sont incompatibles avec PowerShell Core sont retournés.</span><span class="sxs-lookup"><span data-stu-id="705f4-259">When this switch is set, modules without `Core` will be included, so that modules under the Windows PowerShell module path that are incompatible with PowerShell Core will be returned.</span></span>

<span data-ttu-id="705f4-260">Sur macOS et Linux, ce paramètre n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="705f4-260">On macOS and Linux, this parameter does nothing.</span></span>

<span data-ttu-id="705f4-261">Pour plus d’informations, consultez [about_PowerShell_Editions](About/about_PowerShell_Editions.md) .</span><span class="sxs-lookup"><span data-stu-id="705f4-261">See [about_PowerShell_Editions](About/about_PowerShell_Editions.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="705f4-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="705f4-262">CommonParameters</span></span>

<span data-ttu-id="705f4-263">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="705f4-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="705f4-264">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="705f4-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="705f4-265">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="705f4-265">INPUTS</span></span>

### <span data-ttu-id="705f4-266">System.String</span><span class="sxs-lookup"><span data-stu-id="705f4-266">System.String</span></span>

<span data-ttu-id="705f4-267">Vous pouvez diriger les noms de module vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="705f4-267">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="705f4-268">SORTIES</span><span class="sxs-lookup"><span data-stu-id="705f4-268">OUTPUTS</span></span>

### <span data-ttu-id="705f4-269">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="705f4-269">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="705f4-270">Cette applet de commande retourne des objets qui représentent des modules.</span><span class="sxs-lookup"><span data-stu-id="705f4-270">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="705f4-271">Lorsque vous spécifiez le paramètre **listAvailable** , `Get-Module` retourne un objet **ModuleInfoGrouping** , qui est un type d’objet **PSModuleInfo** qui a les mêmes propriétés et méthodes.</span><span class="sxs-lookup"><span data-stu-id="705f4-271">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="705f4-272">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="705f4-272">NOTES</span></span>

- <span data-ttu-id="705f4-273">À compter de Windows PowerShell 3,0, les commandes de base qui sont incluses dans PowerShell sont empaquetées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="705f4-273">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="705f4-274">L’exception est **Microsoft. PowerShell. Core**, qui est un composant logiciel enfichable (**PSSnapin**).</span><span class="sxs-lookup"><span data-stu-id="705f4-274">The exception is **Microsoft.PowerShell.Core**, which is a snap-in (**PSSnapin**).</span></span> <span data-ttu-id="705f4-275">Par défaut, seul le composant logiciel enfichable **Microsoft.PowerShell.Core** est ajouté à la session.</span><span class="sxs-lookup"><span data-stu-id="705f4-275">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="705f4-276">Les modules sont importés automatiquement à la première utilisation, et vous pouvez utiliser l' `Import-Module` applet de commande pour les importer.</span><span class="sxs-lookup"><span data-stu-id="705f4-276">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>

- <span data-ttu-id="705f4-277">Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables (**PSSnapins**).</span><span class="sxs-lookup"><span data-stu-id="705f4-277">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins (**PSSnapins**).</span></span> <span data-ttu-id="705f4-278">L’exception est **Microsoft. PowerShell. Core**, qui est toujours un composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="705f4-278">The exception is **Microsoft.PowerShell.Core**, which is always a snap-in.</span></span> <span data-ttu-id="705f4-279">En outre, les sessions à distance, telles que celles démarrées par l’applet de commande `New-PSSession` , sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.</span><span class="sxs-lookup"><span data-stu-id="705f4-279">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="705f4-280">Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez [méthode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span><span class="sxs-lookup"><span data-stu-id="705f4-280">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="705f4-281">`Get-Module` Obtient uniquement les modules dans les emplacements stockés dans la valeur de la variable d’environnement **PSModulePath** ($env :P smodulepath).</span><span class="sxs-lookup"><span data-stu-id="705f4-281">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="705f4-282">L' `Import-Module` applet de commande peut importer des modules dans d’autres emplacements, mais vous ne pouvez pas utiliser l' `Get-Module` applet de commande pour les récupérer.</span><span class="sxs-lookup"><span data-stu-id="705f4-282">The `Import-Module` cmdlet can import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>

- <span data-ttu-id="705f4-283">En outre, à compter de PowerShell 3,0, de nouvelles propriétés ont été ajoutées à l’objet `Get-Module` retourné, ce qui facilite l’apprentissage des modules, même avant leur importation.</span><span class="sxs-lookup"><span data-stu-id="705f4-283">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="705f4-284">Toutes les propriétés sont remplies avant l’importation.</span><span class="sxs-lookup"><span data-stu-id="705f4-284">All properties are populated before importing.</span></span> <span data-ttu-id="705f4-285">Celles-ci incluent les propriétés **ExportedCommands**, **ExportedCmdlets** et **ExportedFunctions** qui répertorient les commandes exportées par le module.</span><span class="sxs-lookup"><span data-stu-id="705f4-285">These include the **ExportedCommands**, **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>

- <span data-ttu-id="705f4-286">Le paramètre **listAvailable** obtient uniquement les modules correctement formés, c’est-à-dire les dossiers qui contiennent au moins un fichier dont le nom de base est identique au nom du dossier du module.</span><span class="sxs-lookup"><span data-stu-id="705f4-286">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="705f4-287">Le nom de base est le nom sans l’extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="705f4-287">The base name is the name without the file name extension.</span></span> <span data-ttu-id="705f4-288">Les dossiers qui contiennent des fichiers portant des noms différents sont considérés comme des conteneurs, mais pas des modules.</span><span class="sxs-lookup"><span data-stu-id="705f4-288">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="705f4-289">Pour obtenir les modules qui sont implémentés en tant que fichiers DLL, mais qui ne sont pas placés dans un dossier de module, spécifiez à la fois **listAvailable** et **tous** les paramètres.</span><span class="sxs-lookup"><span data-stu-id="705f4-289">To get modules that are implemented as DLL files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="705f4-290">Pour utiliser la fonctionnalité de session CIM, l'ordinateur distant doit disposer de l'accès distant WS-Management et de Windows Management Instrumentation (WMI), qui est l'implémentation Microsoft du modèle CIM (Common Information Model) standard.</span><span class="sxs-lookup"><span data-stu-id="705f4-290">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="705f4-291">L'ordinateur doit également disposer du fournisseur WMI pour la découverte de module ou d'un autre fournisseur WMI ayant les mêmes fonctionnalités de base.</span><span class="sxs-lookup"><span data-stu-id="705f4-291">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="705f4-292">Vous pouvez utiliser la fonctionnalité de session CIM sur les ordinateurs qui n’exécutent pas le système d’exploitation Windows et sur les ordinateurs Windows qui disposent de PowerShell, mais sur lesquels la communication à distance PowerShell n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="705f4-292">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="705f4-293">Vous pouvez également utiliser les paramètres CIM pour obtenir des modules CIM à partir d’ordinateurs sur lesquels la communication à distance PowerShell est activée.</span><span class="sxs-lookup"><span data-stu-id="705f4-293">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="705f4-294">Cela comprend l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="705f4-294">This includes the local computer.</span></span> <span data-ttu-id="705f4-295">Lorsque vous créez une session CIM sur l’ordinateur local, PowerShell utilise DCOM au lieu de WMI pour créer la session.</span><span class="sxs-lookup"><span data-stu-id="705f4-295">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="705f4-296">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="705f4-296">RELATED LINKS</span></span>

[<span data-ttu-id="705f4-297">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="705f4-297">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="705f4-298">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="705f4-298">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="705f4-299">about_Modules</span><span class="sxs-lookup"><span data-stu-id="705f4-299">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="705f4-300">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="705f4-300">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="705f4-301">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="705f4-301">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="705f4-302">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="705f4-302">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="705f4-303">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="705f4-303">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="705f4-304">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="705f4-304">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="705f4-305">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="705f4-305">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
