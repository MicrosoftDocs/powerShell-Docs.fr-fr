---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: f4aec907a41378bbf49f744b66c5662aa3404beb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599142"
---
# <span data-ttu-id="16652-102">Update-Help</span><span class="sxs-lookup"><span data-stu-id="16652-102">Update-Help</span></span>

## <span data-ttu-id="16652-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="16652-103">SYNOPSIS</span></span>
<span data-ttu-id="16652-104">Télécharge et installe les derniers fichiers d'aide sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16652-104">Downloads and installs the newest help files on your computer.</span></span>

## <span data-ttu-id="16652-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="16652-105">SYNTAX</span></span>

### <span data-ttu-id="16652-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="16652-106">Path (Default)</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="16652-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="16652-107">LiteralPath</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="16652-108">Description</span><span class="sxs-lookup"><span data-stu-id="16652-108">DESCRIPTION</span></span>

<span data-ttu-id="16652-109">L' `Update-Help` applet de commande télécharge les fichiers d’aide les plus récents pour les modules PowerShell et les installe sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16652-109">The `Update-Help` cmdlet downloads the newest help files for PowerShell modules and installs them on your computer.</span></span> <span data-ttu-id="16652-110">Vous n’avez pas besoin de redémarrer PowerShell pour que le changement prenne effet.</span><span class="sxs-lookup"><span data-stu-id="16652-110">You need not restart PowerShell to make the change effective.</span></span> <span data-ttu-id="16652-111">Vous pouvez utiliser l' `Get-Help` applet de commande pour afficher les nouveaux fichiers d’aide immédiatement.</span><span class="sxs-lookup"><span data-stu-id="16652-111">You can use the `Get-Help` cmdlet to view the new help files immediately.</span></span>

<span data-ttu-id="16652-112">`Update-Help` vérifie la version des fichiers d’aide sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16652-112">`Update-Help` checks the version of the help files on your computer.</span></span> <span data-ttu-id="16652-113">Si vous n’avez pas de fichiers d’aide pour un module ou si vos fichiers d’aide sont obsolètes, `Update-Help` télécharge les fichiers d’aide les plus récents.</span><span class="sxs-lookup"><span data-stu-id="16652-113">If you don't have help files for a module or if your help files are outdated, `Update-Help` downloads the newest help files.</span></span> <span data-ttu-id="16652-114">Les fichiers d’aide peuvent être téléchargés et installés à partir d’Internet ou d’un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="16652-114">The help files can be downloaded and installed from the internet or a file share.</span></span>

<span data-ttu-id="16652-115">Sans paramètres, `Update-Help` met à jour les fichiers d’aide pour les modules de la session et pour tous les modules installés qui prennent en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="16652-115">Without parameters, `Update-Help` updates the help files for modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="16652-116">Les modules installés mais non chargés dans la session active sont inclus.</span><span class="sxs-lookup"><span data-stu-id="16652-116">Modules that are installed but not loaded in the current session are included.</span></span> <span data-ttu-id="16652-117">Les modules PowerShell sont stockés dans un emplacement répertorié dans la `$env:PSModulePath` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="16652-117">PowerShell modules are stored in a location listed in the `$env:PSModulePath` environment variable.</span></span> <span data-ttu-id="16652-118">Pour plus d’informations, voir [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="16652-118">For more information, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

<span data-ttu-id="16652-119">Vous pouvez utiliser le paramètre **module** pour mettre à jour les fichiers d’aide d’un module particulier.</span><span class="sxs-lookup"><span data-stu-id="16652-119">You can use the **Module** parameter to update help files for a particular module.</span></span> <span data-ttu-id="16652-120">Utilisez le paramètre **UICulture** pour télécharger les fichiers d’aide dans plusieurs langues et paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="16652-120">Use the **UICulture** parameter to download help files in multiple languages and locales.</span></span>

<span data-ttu-id="16652-121">Vous pouvez également utiliser `Update-Help` sur des ordinateurs qui ne sont pas connectés à Internet.</span><span class="sxs-lookup"><span data-stu-id="16652-121">You can also use `Update-Help` on computers that are not connected to the internet.</span></span> <span data-ttu-id="16652-122">Tout d’abord, utilisez la `Save-Help` cmdlet pour télécharger les fichiers d’aide à partir d’Internet et enregistrez-les dans un dossier partagé accessible au système qui n’est pas connecté à Internet.</span><span class="sxs-lookup"><span data-stu-id="16652-122">First, use the `Save-Help`cmdlet to download help files from the internet and save them in a shared folder that is accessible to the system not connected to the internet.</span></span> <span data-ttu-id="16652-123">Utilisez ensuite le paramètre **SourcePath** de `Update-Help` pour télécharger les fichiers d’aide mis à jour à partir du partagé et les installer sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16652-123">Then use the **SourcePath** parameter of `Update-Help` to download the updated help files from the shared and install them on the computer.</span></span>

<span data-ttu-id="16652-124">Vous pouvez automatiser les mises à jour de l’aide en ajoutant l' `Update-Help` applet de commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16652-124">You can automate help updates by adding the `Update-Help` cmdlet to your PowerShell profile.</span></span> <span data-ttu-id="16652-125">Par défaut, `Update-Help` s’exécute une seule fois par jour sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16652-125">By default, `Update-Help` runs only one time per day on each computer.</span></span> <span data-ttu-id="16652-126">Pour remplacer la limite d'une fois par jour, utilisez le paramètre **Force**.</span><span class="sxs-lookup"><span data-stu-id="16652-126">To override the once-per-day limit, use the **Force** parameter.</span></span>

<span data-ttu-id="16652-127">L' `Update-Help` applet de commande a été introduite dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="16652-127">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16652-128">`Update-Help` requiert des privilèges d’administrateur dans PowerShell 6,0 et versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="16652-128">`Update-Help` requires administrative privileges in PowerShell 6.0 and below.</span></span>
> <span data-ttu-id="16652-129">PowerShell 6,1 et versions ultérieures définissent l' **étendue** par défaut sur `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="16652-129">PowerShell 6.1 and above set the default **Scope** to `CurrentUser`.</span></span>
> <span data-ttu-id="16652-130">Avant PowerShell 6,1, le paramètre d' **étendue** n’était pas disponible.</span><span class="sxs-lookup"><span data-stu-id="16652-130">Prior to PowerShell 6.1, the **Scope** parameter was not available.</span></span>
>
> <span data-ttu-id="16652-131">Vous devez être membre du groupe Administrateurs sur l’ordinateur pour mettre à jour les fichiers d’aide pour les modules PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="16652-131">You must be a member of the Administrators group on the computer to update the help files for the PowerShell Core modules.</span></span>
>
> <span data-ttu-id="16652-132">Pour télécharger ou mettre à jour les fichiers d’aide pour les modules dans le répertoire d’installation de PowerShell ( `$PSHOME\Modules` ), y compris les modules PowerShell Core, démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="16652-132">To download or update the help files for modules in the PowerShell installation directory (`$PSHOME\Modules`), including the PowerShell Core modules, start PowerShell by using the **Run as administrator** option.</span></span>
> <span data-ttu-id="16652-133">Par exemple, `Start-Process pwsh.exe -Verb RunAs`.</span><span class="sxs-lookup"><span data-stu-id="16652-133">For example: `Start-Process pwsh.exe -Verb RunAs`.</span></span>

## <span data-ttu-id="16652-134">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="16652-134">EXAMPLES</span></span>

### <span data-ttu-id="16652-135">Exemple 1 : mettre à jour les fichiers d’aide de tous les modules</span><span class="sxs-lookup"><span data-stu-id="16652-135">Example 1: Update help files for all modules</span></span>

<span data-ttu-id="16652-136">L' `Update-Help` applet de commande met à jour les fichiers d’aide pour les modules installés qui prennent en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="16652-136">The `Update-Help` cmdlet updates help files for installed modules that support Updatable Help.</span></span> <span data-ttu-id="16652-137">La langue de la culture de l’interface utilisateur (IU) est définie dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="16652-137">The user-interface (UI) culture language is set in the operating system.</span></span>

```powershell
Update-Help
```

### <span data-ttu-id="16652-138">Exemple 2 : mettre à jour les fichiers d’aide pour les modules spécifiés</span><span class="sxs-lookup"><span data-stu-id="16652-138">Example 2: Update help files for specified modules</span></span>

<span data-ttu-id="16652-139">L' `Update-Help` applet de commande met à jour les fichiers d’aide uniquement pour les noms de modules qui commencent par **Microsoft. PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="16652-139">The `Update-Help` cmdlet updates help files only for module names that begin with **Microsoft.PowerShell**.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### <span data-ttu-id="16652-140">Exemple 3 : mettre à jour les fichiers d’aide pour différentes langues</span><span class="sxs-lookup"><span data-stu-id="16652-140">Example 3: Update help files for different languages</span></span>

<span data-ttu-id="16652-141">L' `Update-Help` applet de commande met à jour les fichiers d’aide japonais (ja-JP) et anglais (en-US) pour tous les modules.</span><span class="sxs-lookup"><span data-stu-id="16652-141">The `Update-Help` cmdlet updates the Japanese (ja-JP) and English (en-US) help files for all modules.</span></span>

<span data-ttu-id="16652-142">Si un module ne fournit pas de fichiers d’aide pour une culture d’interface utilisateur spécifiée, un message d’erreur s’affiche pour le module et la culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="16652-142">If a module doesn't provide help files for a specified UI culture, an error message is displayed for the module and UI culture.</span></span> <span data-ttu-id="16652-143">Dans cet exemple, le message d’erreur indique que les fichiers d’aide **ja-JP** sont introuvables pour le module **Microsoft. PowerShell. Utility**.</span><span class="sxs-lookup"><span data-stu-id="16652-143">In this example, the error message indicates that the **ja-JP** help files were not found for module **Microsoft.PowerShell.Utility**.</span></span>

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### <span data-ttu-id="16652-144">Exemple 4 : mettre à jour les fichiers d’aide sur plusieurs ordinateurs à partir d’un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="16652-144">Example 4: Update help files on multiple computers from a file share</span></span>

<span data-ttu-id="16652-145">Dans cet exemple, les fichiers d’aide mis à jour sont téléchargés à partir d’Internet et enregistrés dans un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="16652-145">In this example, updated help files are downloaded from the internet and saved in a file share.</span></span> <span data-ttu-id="16652-146">Des informations d’identification de l’utilisateur sont nécessaires pour accéder au partage de fichiers et installer les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="16652-146">User credentials are needed that have permissions to access the file share and install updates.</span></span> <span data-ttu-id="16652-147">Lorsqu’un partage de fichiers est utilisé, il est possible de mettre à jour les ordinateurs qui se trouvent derrière des pare-feu ou qui ne sont pas connectés à Internet.</span><span class="sxs-lookup"><span data-stu-id="16652-147">When a file share is used, it's possible to update computers that are behind firewalls or aren't connected to the internet.</span></span>

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

<span data-ttu-id="16652-148">La `Save-Help` commande télécharge les fichiers d’aide les plus récents pour tous les modules qui prennent en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="16652-148">The `Save-Help` command downloads the newest help files for all modules that support Updatable Help.</span></span>
<span data-ttu-id="16652-149">Le paramètre **DestinationPath** enregistre les fichiers dans le `\\Server01\Share\PSHelp` partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="16652-149">The **DestinationPath** parameter saves the files in the `\\Server01\Share\PSHelp` file share.</span></span> <span data-ttu-id="16652-150">Le paramètre **Credential** spécifie un utilisateur qui a l’autorisation d’accéder au partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="16652-150">The **Credential** parameter specifies a user who has permission to access the file share.</span></span>

<span data-ttu-id="16652-151">L' `Invoke-Command` applet `Update-Help` de commande exécute des commandes à distance sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="16652-151">The `Invoke-Command` cmdlet runs remote `Update-Help` commands on multiple computers.</span></span> <span data-ttu-id="16652-152">Le paramètre **ComputerName** obtient une liste d’ordinateurs distants à partir du fichier **Servers.txt** .</span><span class="sxs-lookup"><span data-stu-id="16652-152">The **ComputerName** parameter gets a list of remote computers from the **Servers.txt** file.</span></span> <span data-ttu-id="16652-153">Le paramètre **scriptblock** exécute la `Update-Help` commande et utilise le paramètre **SourcePath** pour spécifier le partage de fichiers qui contient les fichiers d’aide mis à jour.</span><span class="sxs-lookup"><span data-stu-id="16652-153">The **ScriptBlock** parameter runs the `Update-Help` command and uses the **SourcePath** parameter to specify the file share that contains the updated help files.</span></span> <span data-ttu-id="16652-154">Le paramètre **Credential** spécifie un utilisateur qui peut accéder au partage de fichiers et exécuter la commande distante `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="16652-154">The **Credential** parameter specifies a user who can access the file share and run the remote `Update-Help` command.</span></span>

### <span data-ttu-id="16652-155">Exemple 5 : obtenir la liste des fichiers d’aide mis à jour</span><span class="sxs-lookup"><span data-stu-id="16652-155">Example 5: Get a list of updated help files</span></span>

<span data-ttu-id="16652-156">L' `Update-Help` applet de commande met à jour l’aide pour un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="16652-156">The `Update-Help` cmdlet updates help for a specified module.</span></span> <span data-ttu-id="16652-157">L’applet de commande utilise le paramètre commun **Verbose** pour afficher la liste des fichiers d’aide qui ont été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="16652-157">The cmdlet uses the **Verbose** common parameter to display the list of help files that were updated.</span></span> <span data-ttu-id="16652-158">Vous pouvez utiliser **Verbose** pour afficher la sortie de tous les fichiers d’aide ou fichiers d’aide pour un module spécifique.</span><span class="sxs-lookup"><span data-stu-id="16652-158">You can use **Verbose** to view output for all help files or help files for a specific module.</span></span>

<span data-ttu-id="16652-159">Sans le paramètre **Verbose** , `Update-Help` n’affiche pas les résultats de la commande.</span><span class="sxs-lookup"><span data-stu-id="16652-159">Without the **Verbose** parameter, `Update-Help` doesn't display the results of the command.</span></span> <span data-ttu-id="16652-160">La sortie des paramètres **détaillés** est utile pour vérifier que les fichiers d’aide ont été mis à jour ou si la version la plus récente est installée.</span><span class="sxs-lookup"><span data-stu-id="16652-160">The **Verbose** parameter output is useful to verify that the help files were updated or if the latest version is installed.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### <span data-ttu-id="16652-161">Exemple 6 : Rechercher les modules qui prennent en charge l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="16652-161">Example 6: Find modules that support Updatable Help</span></span>

<span data-ttu-id="16652-162">Cet exemple répertorie les modules qui prennent en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="16652-162">This example lists modules that support Updatable Help.</span></span> <span data-ttu-id="16652-163">La commande utilise la propriété **HelpInfoUri** du module pour identifier les modules qui prennent en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="16652-163">The command uses the module's **HelpInfoUri** property to identify modules that support Updatable Help.</span></span> <span data-ttu-id="16652-164">La propriété **HelpInfoUri** contient une adresse qui est redirigée lorsque l' `Update-Help` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="16652-164">The **HelpInfoUri** property contains an address that is redirected when the `Update-Help` cmdlet is run.</span></span>

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### <span data-ttu-id="16652-165">Exemple 7 : inventaire des fichiers d’aide mis à jour</span><span class="sxs-lookup"><span data-stu-id="16652-165">Example 7: Inventory updated help files</span></span>

<span data-ttu-id="16652-166">Dans cet exemple, le script `Get-UpdateHelpVersion.ps1` crée un inventaire des fichiers d’aide pouvant être mis à jour pour chaque module et de leurs numéros de version.</span><span class="sxs-lookup"><span data-stu-id="16652-166">In this example, the script `Get-UpdateHelpVersion.ps1` creates an inventory of the Updatable Help files for each module and their version numbers.</span></span>

<span data-ttu-id="16652-167">Le script identifie les modules qui prennent en charge l’aide actualisable à l’aide de la propriété **HelpInfoUri** des modules.</span><span class="sxs-lookup"><span data-stu-id="16652-167">The script identifies modules that support Updatable Help by using the **HelpInfoUri** property of modules.</span></span> <span data-ttu-id="16652-168">Pour les modules qui prennent en charge l’aide actualisable, le script recherche et analyse le fichier d’informations d’aide (\* helpinfo.xml) pour rechercher le numéro de version le plus récent.</span><span class="sxs-lookup"><span data-stu-id="16652-168">For modules that support Updatable Help, the script looks for and parses the help information file (\*helpinfo.xml) to find the latest version number.</span></span>

<span data-ttu-id="16652-169">Le script utilise la classe **PSCustomObject** et une table de hachage pour créer un objet de sortie personnalisé.</span><span class="sxs-lookup"><span data-stu-id="16652-169">The script uses the **PSCustomObject** class and a hash table to create a custom output object.</span></span>

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## <span data-ttu-id="16652-170">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="16652-170">PARAMETERS</span></span>

### <span data-ttu-id="16652-171">-Credential</span><span class="sxs-lookup"><span data-stu-id="16652-171">-Credential</span></span>

<span data-ttu-id="16652-172">Spécifie les informations d’identification d’un utilisateur qui a l’autorisation d’accéder à l’emplacement du système de fichiers spécifié par **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="16652-172">Specifies credentials of a user who has permission to access the file system location specified by **SourcePath**.</span></span> <span data-ttu-id="16652-173">Ce paramètre est valide uniquement quand le paramètre **SourcePath** ou **LiteralPath** est utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="16652-173">This parameter is valid only when the **SourcePath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="16652-174">Le paramètre **Credential** vous permet d’exécuter `Update-Help` des commandes avec le paramètre **SourcePath** sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="16652-174">The **Credential** parameter enables you to run `Update-Help` commands with the **SourcePath** parameter on remote computers.</span></span> <span data-ttu-id="16652-175">En fournissant des informations d’identification explicites, vous pouvez exécuter la commande sur un ordinateur distant et accéder à un partage de fichiers sur un troisième ordinateur sans rencontrer une erreur d’accès refusé ou en utilisant l’authentification CredSSP pour déléguer les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="16652-175">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="16652-176">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="16652-176">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="16652-177">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="16652-177">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="16652-178">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="16652-178">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="16652-179">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="16652-179">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16652-180">-Force</span><span class="sxs-lookup"><span data-stu-id="16652-180">-Force</span></span>

<span data-ttu-id="16652-181">Indique que cette applet de commande ne suit pas la limite d’une fois par jour, ignore la vérification de version et télécharge les fichiers qui dépassent la limite de 1 Go.</span><span class="sxs-lookup"><span data-stu-id="16652-181">Indicates that this cmdlet doesn't follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="16652-182">Sans ce paramètre, `Update-Help` s’exécute une seule fois par période de 24 heures.</span><span class="sxs-lookup"><span data-stu-id="16652-182">Without this parameter, `Update-Help` runs only once in each 24-hour period.</span></span> <span data-ttu-id="16652-183">Les téléchargements sont limités à 1 Go de contenu non compressé par module et les fichiers d’aide ne sont installés que s’ils sont plus récents que les fichiers existants sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16652-183">Downloads are limited to 1 GB of uncompressed content per module and help files are only installed when they're newer than the existing files on the computer.</span></span>

<span data-ttu-id="16652-184">La limite d’une fois par jour protège les serveurs qui hébergent les fichiers d’aide et vous permet d’ajouter une `Update-Help` commande à votre profil PowerShell sans impliquer le coût des ressources des connexions ou des téléchargements répétés.</span><span class="sxs-lookup"><span data-stu-id="16652-184">The once-per-day limit protects the servers that host the help files and makes it practical for you to add an `Update-Help` command to your PowerShell profile without incurring the resource cost of repeated connections or downloads.</span></span>

<span data-ttu-id="16652-185">Pour mettre à jour l'aide d'un module dans plusieurs cultures d'interface utilisateur sans le paramètre **Force**, incluez toutes les cultures d'interface utilisateur dans la même commande, par exemple, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="16652-185">To update help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as:</span></span>

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

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

### <span data-ttu-id="16652-186">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="16652-186">-FullyQualifiedModule</span></span>

<span data-ttu-id="16652-187">Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** .</span><span class="sxs-lookup"><span data-stu-id="16652-187">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="16652-188">Ces modules sont décrits dans la section Notes du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="16652-188">These modules are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="16652-189">Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié au format :</span><span class="sxs-lookup"><span data-stu-id="16652-189">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

<span data-ttu-id="16652-190">ou</span><span class="sxs-lookup"><span data-stu-id="16652-190">or</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

<span data-ttu-id="16652-191">**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="16652-191">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="16652-192">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** .</span><span class="sxs-lookup"><span data-stu-id="16652-192">You can't specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span>

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

### <span data-ttu-id="16652-193">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="16652-193">-LiteralPath</span></span>

<span data-ttu-id="16652-194">Spécifie le dossier pour les fichiers d’aide mis à jour au lieu de les télécharger à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="16652-194">Specifies the folder for updated help files instead of downloading them from the internet.</span></span> <span data-ttu-id="16652-195">Utilisez ce paramètre ou **SourcePath** si vous avez utilisé l' `Save-Help` applet de commande pour télécharger les fichiers d’aide dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="16652-195">Use this parameter or **SourcePath** if you've used the `Save-Help` cmdlet to download help files to a directory.</span></span>

<span data-ttu-id="16652-196">Vous pouvez effectuer un pipeline d’un objet d’annuaire, tel que des `Get-Item` applets de commande ou `Get-ChildItem` , à `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="16652-196">You can pipeline a directory object, such as from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="16652-197">Contrairement à la valeur de **SourcePath**, la valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="16652-197">Unlike the value of **SourcePath**, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="16652-198">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="16652-198">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="16652-199">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="16652-199">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="16652-200">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="16652-200">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="16652-201">-Module</span><span class="sxs-lookup"><span data-stu-id="16652-201">-Module</span></span>

<span data-ttu-id="16652-202">Met à jour l'aide pour les modules spécifiés.</span><span class="sxs-lookup"><span data-stu-id="16652-202">Updates help for the specified modules.</span></span> <span data-ttu-id="16652-203">Entrez un ou plusieurs noms de module ou modèles de nom dans une liste séparée par des virgules, ou spécifiez un fichier qui répertorie un nom de module sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="16652-203">Enter one or more module names or name patterns in a comma-separated list, or specify a file that lists one module name on each line.</span></span> <span data-ttu-id="16652-204">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="16652-204">Wildcard characters are permitted.</span></span> <span data-ttu-id="16652-205">Vous pouvez effectuer le pipeline des modules de l' `Get-Module` applet de commande vers l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="16652-205">You can pipeline modules from the `Get-Module` cmdlet to the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="16652-206">Les modules que vous spécifiez doivent être installés sur l’ordinateur, mais ils n’ont pas besoin d’être importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="16652-206">The modules that you specify must be installed on the computer, but they don't have to be imported into the current session.</span></span> <span data-ttu-id="16652-207">Vous pouvez spécifier n’importe quel module de la session ou tout module installé dans un emplacement figurant dans la `$env:PSModulePath` variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="16652-207">You can specify any module in the session or any module that is installed in a location listed in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="16652-208">La valeur `*` (All) tente de mettre à jour l’aide de tous les modules installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16652-208">A value of `*` (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="16652-209">Les modules qui ne prennent pas en charge l’aide actualisable sont inclus.</span><span class="sxs-lookup"><span data-stu-id="16652-209">Modules that don't support Updatable Help are included.</span></span> <span data-ttu-id="16652-210">Cette valeur peut générer des erreurs quand la commande rencontre des modules qui ne prennent pas en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="16652-210">This value might generate errors when the command encounters modules that don't support Updatable Help.</span></span> <span data-ttu-id="16652-211">Au lieu de cela, exécutez `Update-Help` sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="16652-211">Instead, run `Update-Help` without parameters.</span></span>

<span data-ttu-id="16652-212">Le paramètre **module** de l' `Update-Help` applet de commande n’accepte pas le chemin d’accès complet d’un fichier de module ou d’un fichier manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="16652-212">The **Module** parameter of the `Update-Help` cmdlet doesn't accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="16652-213">Pour mettre à jour l’aide d’un module qui ne se trouve pas dans un `$env:PSModulePath` emplacement, importez le module dans la session active avant d’exécuter la `Update-Help` commande.</span><span class="sxs-lookup"><span data-stu-id="16652-213">To update help for a module that isn't in a `$env:PSModulePath` location, import the module into the current session before you run the `Update-Help` command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="16652-214">-Recurse</span><span class="sxs-lookup"><span data-stu-id="16652-214">-Recurse</span></span>

<span data-ttu-id="16652-215">Effectue une recherche récursive des fichiers d’aide dans le répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="16652-215">Performs a recursive search for help files in the specified directory.</span></span> <span data-ttu-id="16652-216">Ce paramètre est valide uniquement lorsque la commande utilise le paramètre **SourcePath** .</span><span class="sxs-lookup"><span data-stu-id="16652-216">This parameter is valid only when the command uses the **SourcePath** parameter.</span></span>

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

### <span data-ttu-id="16652-217">-Étendue</span><span class="sxs-lookup"><span data-stu-id="16652-217">-Scope</span></span>

<span data-ttu-id="16652-218">Spécifie l’étendue du système dans laquelle l’aide est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="16652-218">Specifies the system scope where help is updated.</span></span> <span data-ttu-id="16652-219">Les mises à jour au niveau de l’étendue **ALLUSERS** requièrent des privilèges d’administrateur sur les systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="16652-219">Updates at the **AllUsers** scope require administrative privileges on Windows systems.</span></span> <span data-ttu-id="16652-220">Le `-Scope` paramètre a été introduit dans PowerShell Core version 6,1.</span><span class="sxs-lookup"><span data-stu-id="16652-220">The `-Scope` parameter was introduced in PowerShell Core version 6.1.</span></span>

<span data-ttu-id="16652-221">**CurrentUser** est l’étendue par défaut pour les fichiers d’aide dans PowerShell 6,1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="16652-221">**CurrentUser** is the default scope for help files in PowerShell 6.1 and above.</span></span> <span data-ttu-id="16652-222">**ALLUSERS** peut être spécifié pour installer ou mettre à jour l’aide pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="16652-222">**AllUsers** can be specified to install or update help for all users.</span></span> <span data-ttu-id="16652-223">Sur les systèmes UNIX `sudo` , des privilèges sont requis pour mettre à jour l’aide pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="16652-223">On Unix systems `sudo` privileges are required to update help for all users.</span></span> <span data-ttu-id="16652-224">Par exemple : `sudo pwsh -c Update-Help`</span><span class="sxs-lookup"><span data-stu-id="16652-224">For example: `sudo pwsh -c Update-Help`</span></span>

<span data-ttu-id="16652-225">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="16652-225">The acceptable values are:</span></span>

- <span data-ttu-id="16652-226">Utilisateur en cours</span><span class="sxs-lookup"><span data-stu-id="16652-226">CurrentUser</span></span>
- <span data-ttu-id="16652-227">AllUsers</span><span class="sxs-lookup"><span data-stu-id="16652-227">AllUsers</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="16652-228">-SourcePath</span><span class="sxs-lookup"><span data-stu-id="16652-228">-SourcePath</span></span>

<span data-ttu-id="16652-229">Spécifie un dossier de système de fichiers dans lequel `Update-Help` les fichiers d’aide mis à jour, au lieu de les télécharger à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="16652-229">Specifies a file system folder where `Update-Help` gets updated help files, instead of downloading them from the internet.</span></span> <span data-ttu-id="16652-230">Entrez le chemin d’accès à un dossier.</span><span class="sxs-lookup"><span data-stu-id="16652-230">Enter the path of a folder.</span></span> <span data-ttu-id="16652-231">Ne spécifiez pas un nom de fichier ou une extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="16652-231">Don't specify a file name or file name extension.</span></span> <span data-ttu-id="16652-232">Vous pouvez canaliser un dossier, tel que celui des `Get-Item` applets de commande ou `Get-ChildItem` , vers `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="16652-232">You can pipeline a folder, such as one from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="16652-233">Par défaut, `Update-Help` télécharge les fichiers d’aide mis à jour à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="16652-233">By default, `Update-Help` downloads updated help files from the internet.</span></span> <span data-ttu-id="16652-234">Utilisez **SourcePath** lorsque vous avez utilisé l' `Save-Help` applet de commande pour télécharger les fichiers d’aide mis à jour dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="16652-234">Use **SourcePath** when you've used the `Save-Help` cmdlet to download updated help files to a directory.</span></span>

<span data-ttu-id="16652-235">Pour spécifier une valeur par défaut pour **SourcePath**, accédez à **stratégie de groupe**, **Configuration ordinateur**, puis **Définissez le chemin source par défaut pour Update-Help**.</span><span class="sxs-lookup"><span data-stu-id="16652-235">To specify a default value for **SourcePath**, go to **Group Policy**, **Computer Configuration**, and **Set the default source path for Update-Help**.</span></span> <span data-ttu-id="16652-236">Ce paramètre stratégie de groupe empêche les utilisateurs d’utiliser `Update-Help` pour télécharger des fichiers d’aide à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="16652-236">This Group Policy setting prevents users from using `Update-Help` to download help files from the internet.</span></span>
<span data-ttu-id="16652-237">Pour plus d’informations, consultez [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="16652-237">For more information, see [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16652-238">-UICulture</span><span class="sxs-lookup"><span data-stu-id="16652-238">-UICulture</span></span>

<span data-ttu-id="16652-239">Spécifie les valeurs de culture d’interface utilisateur `Update-Help` utilisées par pour obtenir les fichiers d’aide mis à jour.</span><span class="sxs-lookup"><span data-stu-id="16652-239">Specifies UI culture values that `Update-Help` uses to get updated help files.</span></span> <span data-ttu-id="16652-240">Entrez un ou plusieurs codes de langue, tels que **es-es**, une variable qui contient des objets de culture ou une commande qui obtient des objets de culture, tels qu’une `Get-Culture` `Get-UICulture` commande ou.</span><span class="sxs-lookup"><span data-stu-id="16652-240">Enter one or more language codes, such as **es-ES**, a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span> <span data-ttu-id="16652-241">Les caractères génériques ne sont pas autorisés et vous ne pouvez pas envoyer un code de langue partielle, tel que **de**.</span><span class="sxs-lookup"><span data-stu-id="16652-241">Wildcard characters aren't permitted and you can't submit a partial language code, such as **de**.</span></span>

<span data-ttu-id="16652-242">Par défaut, `Update-Help` obtient les fichiers d’aide dans la culture d’interface utilisateur définie pour le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="16652-242">By default, `Update-Help` gets help files in the UI culture set for the operating system.</span></span> <span data-ttu-id="16652-243">Si vous spécifiez le paramètre **UICulture** , `Update-Help` recherche uniquement de l’aide pour la culture d’interface utilisateur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16652-243">If you specify the **UICulture** parameter, `Update-Help` looks for help only for the specified UI culture.</span></span>

> [!NOTE]
> <span data-ttu-id="16652-244">Ubuntu 18,04 a modifié les paramètres régionaux par défaut en `C.UTF.8` , qui n’est pas une culture d’interface utilisateur reconnue.</span><span class="sxs-lookup"><span data-stu-id="16652-244">Ubuntu 18.04 changed the default locale setting to `C.UTF.8`, which is not a recognized UI culture.</span></span> <span data-ttu-id="16652-245">`Update-Help` ne parvient pas à télécharger l’aide en mode silencieux, sauf si vous utilisez ce paramètre avec des paramètres régionaux pris en charge, comme `en-US` .</span><span class="sxs-lookup"><span data-stu-id="16652-245">`Update-Help` silently fails to download help unless you use this parameter with a supported locale like `en-US`.</span></span> <span data-ttu-id="16652-246">Cela peut se produire sur n’importe quelle plateforme qui utilise une valeur non prise en charge.</span><span class="sxs-lookup"><span data-stu-id="16652-246">This could occur on any platform that uses an unsupported value.</span></span>

<span data-ttu-id="16652-247">Les commandes qui utilisent le paramètre **UICulture** ne réussissent que si le module fournit les fichiers d'aide pour la culture d'interface utilisateur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16652-247">Commands that use the **UICulture** parameter succeed only when the module provides help files for the specified UI culture.</span></span> <span data-ttu-id="16652-248">Si la commande échoue car la culture d’interface utilisateur spécifiée n’est pas prise en charge, un message d’erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="16652-248">If the command fails because the specified UI culture isn't supported, an error message is displayed.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16652-249">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="16652-249">-UseDefaultCredentials</span></span>

<span data-ttu-id="16652-250">Indique que `Update-Help` exécute la commande, y compris le téléchargement Internet, à l’aide des informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="16652-250">Indicates that `Update-Help` runs the command, including the internet download, by using the credentials of the current user.</span></span> <span data-ttu-id="16652-251">Par défaut, la commande s'exécute sans informations d'identification explicites.</span><span class="sxs-lookup"><span data-stu-id="16652-251">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="16652-252">Ce paramètre est effectif uniquement quand le téléchargement Web utilise l’authentification NTLM (NT LAN Manager), Negotiate ou Kerberos.</span><span class="sxs-lookup"><span data-stu-id="16652-252">This parameter is effective only when the web download uses NT LAN Manager (NTLM), negotiate, or Kerberos-based authentication.</span></span>

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

### <span data-ttu-id="16652-253">-Confirm</span><span class="sxs-lookup"><span data-stu-id="16652-253">-Confirm</span></span>

<span data-ttu-id="16652-254">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="16652-254">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16652-255">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="16652-255">-WhatIf</span></span>

<span data-ttu-id="16652-256">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="16652-256">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="16652-257">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="16652-257">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16652-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="16652-258">CommonParameters</span></span>

<span data-ttu-id="16652-259">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="16652-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="16652-260">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="16652-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="16652-261">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="16652-261">INPUTS</span></span>

### <span data-ttu-id="16652-262">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="16652-262">System.IO.DirectoryInfo</span></span>

<span data-ttu-id="16652-263">Vous pouvez diriger un chemin d’accès de répertoire vers `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="16652-263">You can pipe a directory path to `Update-Help`.</span></span>

### <span data-ttu-id="16652-264">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="16652-264">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="16652-265">Vous pouvez diriger un objet de module de l’applet de commande `Get-Module` vers `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="16652-265">You can pipe a module object from the `Get-Module` cmdlet to `Update-Help`.</span></span>

## <span data-ttu-id="16652-266">SORTIES</span><span class="sxs-lookup"><span data-stu-id="16652-266">OUTPUTS</span></span>

### <span data-ttu-id="16652-267">None</span><span class="sxs-lookup"><span data-stu-id="16652-267">None</span></span>

<span data-ttu-id="16652-268">`Update-Help` ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="16652-268">`Update-Help` doesn't generate any output.</span></span>

## <span data-ttu-id="16652-269">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="16652-269">NOTES</span></span>

<span data-ttu-id="16652-270">Pour mettre à jour l’aide pour les modules PowerShell Core, qui contiennent les commandes installées avec PowerShell, ou tout module dans l' `$PSHOME\Modules` annuaire, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="16652-270">To update help for the PowerShell Core modules, that contain the commands that are installed with PowerShell, or any module in the `$PSHOME\Modules` directory, start PowerShell with the option to **Run as administrator**.</span></span>

<span data-ttu-id="16652-271">Seuls les membres du groupe Administrateurs sur l’ordinateur peuvent mettre à jour l’aide pour les modules PowerShell Core, les commandes qui sont installées avec PowerShell et les modules dans le `$PSHOME\Modules` dossier.</span><span class="sxs-lookup"><span data-stu-id="16652-271">Only members of the Administrators group on the computer can update help for the PowerShell Core modules, the commands that are installed together with PowerShell, and for modules in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="16652-272">Si vous n’avez pas l’autorisation de mettre à jour les fichiers d’aide, vous pouvez lire les fichiers d’aide en ligne.</span><span class="sxs-lookup"><span data-stu-id="16652-272">If you don't have permission to update help files, you can read the help files online.</span></span> <span data-ttu-id="16652-273">Par exemple, `Get-Help Update-Help -Online`.</span><span class="sxs-lookup"><span data-stu-id="16652-273">For example, `Get-Help Update-Help -Online`.</span></span>

<span data-ttu-id="16652-274">Les modules sont la plus petite unité d'aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="16652-274">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="16652-275">Vous ne pouvez pas mettre à jour l’aide d’une applet de commande particulière.</span><span class="sxs-lookup"><span data-stu-id="16652-275">You can't update help for a particular cmdlet.</span></span> <span data-ttu-id="16652-276">Pour rechercher le module qui contient une applet de commande particulière, utilisez la propriété **modulename** de l’applet de commande `Get-Command` , par exemple, `(Get-Command Update-Help).ModuleName` .</span><span class="sxs-lookup"><span data-stu-id="16652-276">To find the module that contains a particular cmdlet, use the **ModuleName** property of the `Get-Command` cmdlet, for example, `(Get-Command Update-Help).ModuleName`.</span></span>

<span data-ttu-id="16652-277">Étant donné que les fichiers d’aide sont installés dans le répertoire du module, l’applet de commande `Update-Help` peut installer le fichier d’aide mis à jour uniquement pour les modules qui sont installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16652-277">Because help files are installed in the module directory, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span> <span data-ttu-id="16652-278">Toutefois, l' `Save-Help` applet de commande peut enregistrer l’aide pour les modules qui ne sont pas installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16652-278">However, the `Save-Help` cmdlet can save help for modules that aren't installed on the computer.</span></span>

<span data-ttu-id="16652-279">Si `Update-Help` ne peut pas trouver les fichiers d’aide mis à jour pour un module ou si l’aide mise à jour est introuvable dans la langue spécifiée, elle se poursuit en mode silencieux sans afficher de message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="16652-279">If `Update-Help` can't find updated help files for a module, or can't find updated help in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="16652-280">Pour afficher l'état et les détails de la progression, utilisez le paramètre **Verbose**.</span><span class="sxs-lookup"><span data-stu-id="16652-280">To see status and progress details, use the **Verbose** parameter.</span></span>

<span data-ttu-id="16652-281">L' `Update-Help` applet de commande a été introduite dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="16652-281">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="16652-282">Il ne fonctionne pas dans les versions antérieures de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16652-282">It doesn't work in earlier versions of PowerShell.</span></span> <span data-ttu-id="16652-283">Sur les ordinateurs qui ont à la fois Windows PowerShell 2,0 et Windows PowerShell 3,0, utilisez l' `Update-Help` applet de commande dans une session Windows powershell 3,0 pour télécharger et mettre à jour les fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="16652-283">On computers that have both Windows PowerShell 2.0 and Windows PowerShell 3.0, use the `Update-Help` cmdlet in a Windows PowerShell 3.0 session to download and update help files.</span></span> <span data-ttu-id="16652-284">Les fichiers d’aide sont disponibles pour Windows PowerShell 2,0 et Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="16652-284">The help files are available to both Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span>

<span data-ttu-id="16652-285">Les `Update-Help` `Save-Help` applets de commande et utilisent les ports suivants pour télécharger les fichiers d’aide : le port 80 pour http et le port 443 pour HTTPS.</span><span class="sxs-lookup"><span data-stu-id="16652-285">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>

<span data-ttu-id="16652-286">`Update-Help` prend en charge tous les modules et les composants logiciels enfichables PowerShell Core. Elle ne prend en charge aucun autre composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="16652-286">`Update-Help` supports all modules and the PowerShell Core snap-ins. It doesn't support any other snap-ins.</span></span>

<span data-ttu-id="16652-287">Pour mettre à jour l’aide d’un module dans un emplacement qui n’est pas listé dans la `$env:PSModulePath` variable d’environnement, importez le module dans la session active, puis exécutez une `Update-Help` commande.</span><span class="sxs-lookup"><span data-stu-id="16652-287">To update help for a module in a location that isn't listed in the `$env:PSModulePath` environment variable, import the module into the current session and then run an `Update-Help` command.</span></span> <span data-ttu-id="16652-288">Exécutez `Update-Help` sans paramètres ou utilisez le paramètre **module** pour spécifier le nom du module.</span><span class="sxs-lookup"><span data-stu-id="16652-288">Run `Update-Help` without parameters or use the **Module** parameter to specify the module name.</span></span> <span data-ttu-id="16652-289">Le paramètre **module** des `Update-Help` applets de commande et `Save-Help` n’accepte pas le chemin d’accès complet d’un fichier de module ou d’un fichier manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="16652-289">The **Module** parameter of the `Update-Help` and `Save-Help` cmdlets doesn't accept the full path of a module file or module manifest file.</span></span>

<span data-ttu-id="16652-290">Tout module prend en charge de l'aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="16652-290">Any module can support Updatable Help.</span></span> <span data-ttu-id="16652-291">Pour obtenir des instructions sur la prise en charge de l’aide actualisable dans les modules que vous créez, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="16652-291">For instructions for supporting Updatable Help in the modules that you author, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="16652-292">Les `Update-Help` applets de commande et ne `Save-Help` sont pas prises en charge sur environnement de préinstallation Windows (WinPE) (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="16652-292">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="16652-293">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="16652-293">RELATED LINKS</span></span>

[<span data-ttu-id="16652-294">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="16652-294">Get-Culture</span></span>](../Microsoft.PowerShell.Utility/Get-Culture.md)

[<span data-ttu-id="16652-295">Get-Help</span><span class="sxs-lookup"><span data-stu-id="16652-295">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="16652-296">Get-Module</span><span class="sxs-lookup"><span data-stu-id="16652-296">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="16652-297">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="16652-297">Get-UICulture</span></span>](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[<span data-ttu-id="16652-298">Start-Job</span><span class="sxs-lookup"><span data-stu-id="16652-298">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="16652-299">Save-Help</span><span class="sxs-lookup"><span data-stu-id="16652-299">Save-Help</span></span>](Save-Help.md)
