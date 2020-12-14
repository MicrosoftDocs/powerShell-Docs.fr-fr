---
description: Explique comment installer, importer et utiliser des modules PowerShell.
Locale: en-US
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: aebebc3f41a091151fbbecd9925a4ebc063e678e
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564600"
---
# <a name="about-modules"></a><span data-ttu-id="ecd99-103">À propos des modules</span><span class="sxs-lookup"><span data-stu-id="ecd99-103">About Modules</span></span>

## <a name="short-description"></a><span data-ttu-id="ecd99-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="ecd99-104">Short Description</span></span>
<span data-ttu-id="ecd99-105">Explique comment installer, importer et utiliser des modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-105">Explains how to install, import, and use PowerShell modules.</span></span>

## <a name="long-description"></a><span data-ttu-id="ecd99-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="ecd99-106">Long Description</span></span>

<span data-ttu-id="ecd99-107">Un module est un package qui contient des membres PowerShell, tels que des applets de commande, des fournisseurs, des fonctions, des workflows, des variables et des alias.</span><span class="sxs-lookup"><span data-stu-id="ecd99-107">A module is a package that contains PowerShell members, such as cmdlets, providers, functions, workflows, variables, and aliases.</span></span>

<span data-ttu-id="ecd99-108">Les personnes qui écrivent des commandes peuvent utiliser des modules pour organiser leurs commandes et les partager avec d'autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ecd99-108">People who write commands can use modules to organize their commands and share them with others.</span></span> <span data-ttu-id="ecd99-109">Les personnes qui reçoivent des modules peuvent ajouter les commandes dans les modules à leurs sessions PowerShell et les utiliser comme les commandes intégrées.</span><span class="sxs-lookup"><span data-stu-id="ecd99-109">People who receive modules can add the commands in the modules to their PowerShell sessions and use them just like the built-in commands.</span></span>

<span data-ttu-id="ecd99-110">Cette rubrique explique comment utiliser les modules PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-110">This topic explains how to use PowerShell modules.</span></span> <span data-ttu-id="ecd99-111">Pour plus d’informations sur l’écriture de modules PowerShell, consultez [écriture d’un module PowerShell](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span><span class="sxs-lookup"><span data-stu-id="ecd99-111">For information about how to write PowerShell modules, see [Writing a PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="what-is-a-module"></a><span data-ttu-id="ecd99-112">Qu’est-ce qu’un module ?</span><span class="sxs-lookup"><span data-stu-id="ecd99-112">What Is a Module?</span></span>

<span data-ttu-id="ecd99-113">Un module est un package qui contient des membres PowerShell, tels que des applets de commande, des fournisseurs, des fonctions, des workflows, des variables et des alias.</span><span class="sxs-lookup"><span data-stu-id="ecd99-113">A module is a package that contains PowerShell members, such as cmdlets, providers, functions, workflows, variables, and aliases.</span></span> <span data-ttu-id="ecd99-114">Les membres de ce package peuvent être implémentés dans un script PowerShell, une DLL compilée ou une combinaison des deux.</span><span class="sxs-lookup"><span data-stu-id="ecd99-114">The members of this package can be implemented in a PowerShell script, a compiled DLL, or a combination of both.</span></span> <span data-ttu-id="ecd99-115">Ces fichiers sont généralement regroupés dans un seul répertoire.</span><span class="sxs-lookup"><span data-stu-id="ecd99-115">These files are usually grouped together in a single directory.</span></span> <span data-ttu-id="ecd99-116">Pour plus d’informations, consultez [comprendre un module Windows PowerShell](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) dans la documentation du kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="ecd99-116">For more information, see [Understanding a Windows PowerShell Module](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) in the SDK documentation.</span></span>

## <a name="module-auto-loading"></a><span data-ttu-id="ecd99-117">Chargement automatique des modules</span><span class="sxs-lookup"><span data-stu-id="ecd99-117">Module Auto-Loading</span></span>

<span data-ttu-id="ecd99-118">À compter de PowerShell 3,0, PowerShell importe automatiquement les modules la première fois que vous exécutez une commande dans un module installé.</span><span class="sxs-lookup"><span data-stu-id="ecd99-118">Beginning in PowerShell 3.0, PowerShell imports modules automatically the first time that you run any command in an installed module.</span></span> <span data-ttu-id="ecd99-119">Vous pouvez désormais utiliser les commandes d'un module sans même le configurer ni définir de profil. Une fois vos modules installés sur votre ordinateur, vous n'avez pas à vous en occuper.</span><span class="sxs-lookup"><span data-stu-id="ecd99-119">You can now use the commands in a module without any set-up or profile configuration, so there's no need to manage modules after you install them on your computer.</span></span>

<span data-ttu-id="ecd99-120">Vous pouvez aussi trouver plus facilement les commandes contenues dans un module.</span><span class="sxs-lookup"><span data-stu-id="ecd99-120">The commands in a module are also easier to find.</span></span> <span data-ttu-id="ecd99-121">L' `Get-Command` applet de commande obtient désormais toutes les commandes de tous les modules installés, même si elles n’ont pas encore été dans la session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-121">The `Get-Command` cmdlet now gets all commands in all installed modules, even if they are not yet in the session.</span></span> <span data-ttu-id="ecd99-122">Vous pouvez rechercher une commande et l’utiliser sans importer en premier lieu.</span><span class="sxs-lookup"><span data-stu-id="ecd99-122">You can find a command and use it without importing needing to import the module first.</span></span>

<span data-ttu-id="ecd99-123">Chacun des exemples suivants provoque l’importation du module CimCmdlets, qui contient `Get-CimInstance` , dans votre session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-123">Each of the following examples cause the CimCmdlets module, which contains `Get-CimInstance`, to be imported into your session.</span></span>

- <span data-ttu-id="ecd99-124">Exécutez la commande</span><span class="sxs-lookup"><span data-stu-id="ecd99-124">Run the Command</span></span>

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- <span data-ttu-id="ecd99-125">Obtient la commande</span><span class="sxs-lookup"><span data-stu-id="ecd99-125">Get the Command</span></span>

  ```powershell
  Get-Command Get-CimInstance
  ```

- <span data-ttu-id="ecd99-126">Obtenir de l’aide pour la commande</span><span class="sxs-lookup"><span data-stu-id="ecd99-126">Get Help for the Command</span></span>

  ```powershell
  Get-Help Get-CimInstance
  ```

<span data-ttu-id="ecd99-127">`Get-Command` les commandes qui incluent un caractère générique ( `*` ) sont considérées comme étant destinées à être découvertes, ne sont pas utilisées et n’importent pas de modules.</span><span class="sxs-lookup"><span data-stu-id="ecd99-127">`Get-Command` commands that include a wildcard character (`*`) are considered to be for discovery, not use, and do not import any modules.</span></span>

<span data-ttu-id="ecd99-128">Seuls les modules stockés à l’emplacement spécifié par la variable d’environnement PSModulePath sont importés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ecd99-128">Only modules that are stored in the location specified by the PSModulePath environment variable are automatically imported.</span></span> <span data-ttu-id="ecd99-129">Les modules dans d’autres emplacements doivent être importés en exécutant l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-129">Modules in other locations must be imported by running the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="ecd99-130">En outre, les commandes qui utilisent des fournisseurs PowerShell n’importent pas automatiquement un module.</span><span class="sxs-lookup"><span data-stu-id="ecd99-130">Also, commands that use PowerShell providers do not automatically import a module.</span></span> <span data-ttu-id="ecd99-131">Par exemple, si vous utilisez une commande qui requiert le lecteur WSMan :, tel que l' `Get-PSSessionConfiguration` applet de commande, vous devrez peut-être exécuter l' `Import-Module` applet de commande pour importer le module **Microsoft. WSMan. Management** qui comprend le `WSMan:` lecteur.</span><span class="sxs-lookup"><span data-stu-id="ecd99-131">For example, if you use a command that requires the WSMan: drive, such as the `Get-PSSessionConfiguration` cmdlet, you might need to run the `Import-Module` cmdlet to import the **Microsoft.WSMan.Management** module that includes the `WSMan:` drive.</span></span>

<span data-ttu-id="ecd99-132">Vous pouvez toujours exécuter la `Import-Module` commande pour importer un module et utiliser la `$PSModuleAutoloadingPreference` variable pour activer, désactiver et configurer l’importation automatique de modules.</span><span class="sxs-lookup"><span data-stu-id="ecd99-132">You can still run the `Import-Module` command to import a module and use the `$PSModuleAutoloadingPreference` variable to enable, disable and configure automatic importing of modules.</span></span> <span data-ttu-id="ecd99-133">Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ecd99-133">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="how-to-use-a-module"></a><span data-ttu-id="ecd99-134">Comment utiliser un module</span><span class="sxs-lookup"><span data-stu-id="ecd99-134">How to Use a Module</span></span>

<span data-ttu-id="ecd99-135">Pour utiliser un module, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ecd99-135">To use a module, perform the following tasks:</span></span>

1. <span data-ttu-id="ecd99-136">Installez le module.</span><span class="sxs-lookup"><span data-stu-id="ecd99-136">Install the module.</span></span> <span data-ttu-id="ecd99-137">(Bien souvent, cette tâche ne vous incombe pas.)</span><span class="sxs-lookup"><span data-stu-id="ecd99-137">(This is often done for you.)</span></span>
1. <span data-ttu-id="ecd99-138">Recherchez les commandes ajoutées par le module.</span><span class="sxs-lookup"><span data-stu-id="ecd99-138">Find the commands that the module added.</span></span>
1. <span data-ttu-id="ecd99-139">Utilisez les commandes ajoutées par le module.</span><span class="sxs-lookup"><span data-stu-id="ecd99-139">Use the commands that the module added.</span></span>

<span data-ttu-id="ecd99-140">Cette rubrique explique comment effectuer ces tâches.</span><span class="sxs-lookup"><span data-stu-id="ecd99-140">This topic explains how to perform these tasks.</span></span> <span data-ttu-id="ecd99-141">Elle contient également d'autres informations utiles sur la gestion des modules.</span><span class="sxs-lookup"><span data-stu-id="ecd99-141">It also includes other useful information about managing modules.</span></span>

## <a name="how-to-install-a-module"></a><span data-ttu-id="ecd99-142">Comment installer un module</span><span class="sxs-lookup"><span data-stu-id="ecd99-142">How to Install a Module</span></span>

<span data-ttu-id="ecd99-143">Si vous recevez un module sous la forme d’un dossier contenant des fichiers, vous devez l’installer sur votre ordinateur avant de pouvoir l’utiliser dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-143">If you receive a module as a folder with files in it, you need to install it on your computer before you can use it in PowerShell.</span></span>

<span data-ttu-id="ecd99-144">La plupart des modules sont installés pour vous.</span><span class="sxs-lookup"><span data-stu-id="ecd99-144">Most modules are installed for you.</span></span> <span data-ttu-id="ecd99-145">PowerShell est fourni avec plusieurs modules préinstallés, parfois appelés modules _principaux_ .</span><span class="sxs-lookup"><span data-stu-id="ecd99-145">PowerShell comes with several preinstalled modules, sometimes called the _core_ modules.</span></span> <span data-ttu-id="ecd99-146">Sur les ordinateurs Windows, si des fonctionnalités incluses avec le système d’exploitation possèdent des applets de commande pour les gérer, ces modules sont préinstallés.</span><span class="sxs-lookup"><span data-stu-id="ecd99-146">On Windows-based computers, if features that are included with the operating system have cmdlets to manage them, those modules are preinstalled.</span></span> <span data-ttu-id="ecd99-147">Quand vous installez une fonctionnalité Windows, en utilisant, par exemple, l’Assistant Ajout de rôles et de fonctionnalités dans Gestionnaire de serveur, ou la boîte de dialogue Activer ou désactiver des fonctionnalités Windows dans le panneau de configuration, tous les modules PowerShell qui font partie de la fonctionnalité sont installés.</span><span class="sxs-lookup"><span data-stu-id="ecd99-147">When you install a Windows feature, by using, for example, the Add Roles and Features Wizard in Server Manager, or the Turn Windows features on or off dialog box in Control Panel, any PowerShell modules that are part of the feature are installed.</span></span> <span data-ttu-id="ecd99-148">D'autres modules sont fournis avec un programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="ecd99-148">Many other modules come in an installer or Setup program that installs the module.</span></span>

<span data-ttu-id="ecd99-149">Utilisez la commande suivante pour créer un répertoire **modules** pour l’utilisateur actuel :</span><span class="sxs-lookup"><span data-stu-id="ecd99-149">Use the following command to create a **Modules** directory for the current user:</span></span>

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="ecd99-150">Copiez le dossier du module en totalité dans le répertoire Modules.</span><span class="sxs-lookup"><span data-stu-id="ecd99-150">Copy the entire module folder into the Modules directory.</span></span> <span data-ttu-id="ecd99-151">Vous pouvez utiliser n’importe quelle méthode pour copier le dossier, y compris l’Explorateur Windows et Cmd.exe, ainsi que PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-151">You can use any method to copy the folder, including Windows Explorer and Cmd.exe, as well as PowerShell.</span></span> <span data-ttu-id="ecd99-152">Dans PowerShell, utilisez l’applet de commande `Copy-Item` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-152">In PowerShell use the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="ecd99-153">Par exemple, pour copier le dossier MyModule de dans `C:\ps-test\MyModule` le répertoire Modules, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-153">For example, to copy the MyModule folder from `C:\ps-test\MyModule` to the Modules directory, type:</span></span>

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="ecd99-154">Vous pouvez installer vos modules n'importe où, mais nous vous recommandons de les installer dans un emplacement de module par défaut pour faciliter leur gestion.</span><span class="sxs-lookup"><span data-stu-id="ecd99-154">You can install a module in any location, but installing your modules in a default module location makes them easier to manage.</span></span> <span data-ttu-id="ecd99-155">Pour plus d’informations sur les emplacements par défaut des modules, consultez les sections [module et emplacements des ressources DSC et PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) .</span><span class="sxs-lookup"><span data-stu-id="ecd99-155">For more information about the default module locations, see the [Module and DSC Resource Locations, and PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) section.</span></span>

## <a name="how-to-find-installed-modules"></a><span data-ttu-id="ecd99-156">Comment rechercher des modules installés</span><span class="sxs-lookup"><span data-stu-id="ecd99-156">How to Find Installed Modules</span></span>

<span data-ttu-id="ecd99-157">Pour trouver les modules qui sont installés dans un emplacement par défaut, mais qui ne sont pas encore dans votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-157">To find modules that are installed in a default module location, but not yet imported into your session, type:</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="ecd99-158">Pour rechercher les modules qui ont déjà été importés dans votre session, à l’invite de PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-158">To find the modules that have already been imported into your session, at the PowerShell prompt, type:</span></span>

```powershell
Get-Module
```

<span data-ttu-id="ecd99-159">Pour plus d’informations sur l’applet de commande `Get-Module` , consultez la rubrique [obtenir-module](xref:Microsoft.PowerShell.Core.Get-Module).</span><span class="sxs-lookup"><span data-stu-id="ecd99-159">For more information about the `Get-Module` cmdlet, see [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

## <a name="how-to-find-the-commands-in-a-module"></a><span data-ttu-id="ecd99-160">Comment rechercher les commandes dans un module</span><span class="sxs-lookup"><span data-stu-id="ecd99-160">How to Find the Commands in a Module</span></span>

<span data-ttu-id="ecd99-161">Utilisez l' `Get-Command` applet de commande pour rechercher toutes les commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="ecd99-161">Use the `Get-Command` cmdlet to find all available commands.</span></span> <span data-ttu-id="ecd99-162">Vous pouvez utiliser les paramètres de l' `Get-Command` applet de commande pour filtrer les commandes, par exemple par module, nom et substantif.</span><span class="sxs-lookup"><span data-stu-id="ecd99-162">You can use the parameters of the `Get-Command` cmdlet to filter commands such as by module, name, and noun.</span></span>

<span data-ttu-id="ecd99-163">Pour trouver toutes les commandes dans un module, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-163">To find all commands in a module, type:</span></span>

```powershell
Get-Command -Module <module-name>
```

<span data-ttu-id="ecd99-164">Par exemple, pour rechercher les commandes dans le module BitsTransfer, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-164">For example, to find the commands in the BitsTransfer module, type:</span></span>

```powershell
Get-Command -Module BitsTransfer
```

<span data-ttu-id="ecd99-165">Pour plus d’informations sur l' `Get-Command` applet de commande, consultez la rubrique [obtenir-Command](xref:Microsoft.PowerShell.Core.Get-Command).</span><span class="sxs-lookup"><span data-stu-id="ecd99-165">For more information about the `Get-Command` cmdlet, see [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command).</span></span>

## <a name="how-to-get-help-for-the-commands-in-a-module"></a><span data-ttu-id="ecd99-166">Comment obtenir de l’aide pour les commandes d’un module</span><span class="sxs-lookup"><span data-stu-id="ecd99-166">How to Get Help for the Commands in a Module</span></span>

<span data-ttu-id="ecd99-167">Si le module contient des fichiers d’aide pour les commandes qu’il exporte, l’applet de commande `Get-Help` affiche les rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="ecd99-167">If the module contains Help files for the commands that it exports, the `Get-Help` cmdlet will display the Help topics.</span></span> <span data-ttu-id="ecd99-168">Utilisez le même `Get-Help` format de commande que celui que vous utiliseriez pour obtenir de l’aide pour n’importe quelle commande dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-168">Use the same `Get-Help` command format that you would use to get help for any command in PowerShell.</span></span>

<span data-ttu-id="ecd99-169">À compter de PowerShell 3,0, vous pouvez télécharger les fichiers d’aide d’un module et télécharger les mises à jour des fichiers d’aide afin qu’elles ne soient jamais obsolètes.</span><span class="sxs-lookup"><span data-stu-id="ecd99-169">Beginning in PowerShell 3.0, you can download Help files for a module and download updates to the Help files so they are never obsolete.</span></span>

<span data-ttu-id="ecd99-170">Pour obtenir de l'aide sur une commande d'un module, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-170">To get help for a commands in a module, type:</span></span>

```powershell
Get-Help <command-name>
```

<span data-ttu-id="ecd99-171">Pour obtenir de l’aide en ligne pour la commande dans un module, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-171">To get help online for command in a module, type:</span></span>

```powershell
Get-Help <command-name> -Online
```

<span data-ttu-id="ecd99-172">Pour télécharger et installer les fichiers d’aide pour les commandes d’un module, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-172">To download and install the help files for the commands in a module, type:</span></span>

```powershell
Update-Help -Module <module-name>
```

<span data-ttu-id="ecd99-173">Pour plus d’informations, consultez la rubrique [obtenir-aide](xref:Microsoft.PowerShell.Core.Get-Help) et [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help).</span><span class="sxs-lookup"><span data-stu-id="ecd99-173">For more information, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help).</span></span>

## <a name="how-to-import-a-module"></a><span data-ttu-id="ecd99-174">Comment importer un module</span><span class="sxs-lookup"><span data-stu-id="ecd99-174">How to Import a Module</span></span>

<span data-ttu-id="ecd99-175">Vous pouvez être amené à importer un module ou un fichier de module.</span><span class="sxs-lookup"><span data-stu-id="ecd99-175">You might have to import a module or import a module file.</span></span> <span data-ttu-id="ecd99-176">L’importation est requise lorsqu’un module n’est pas installé dans les emplacements spécifiés par la variable d’environnement **PSModulePath** , `$env:PSModulePath` ou le module se compose d’un fichier, tel qu’un fichier. dll ou. psm1, au lieu d’un module standard fourni sous forme de dossier.</span><span class="sxs-lookup"><span data-stu-id="ecd99-176">Importing is required when a module is not installed in the locations specified by the **PSModulePath** environment variable, `$env:PSModulePath`, or the module consists of file, such as a .dll or .psm1 file, instead of typical module that is delivered as a folder.</span></span>

<span data-ttu-id="ecd99-177">Vous pouvez également choisir d’importer un module pour pouvoir utiliser les paramètres de la `Import-Module` commande, tels que le paramètre prefix, qui ajoute un préfixe unique aux noms de toutes les commandes importées, ou le paramètre **NoClobber** , qui empêche le module d’ajouter des commandes qui masquent ou remplacent des commandes existantes dans la session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-177">You might also choose to import a module so that you can use the parameters of the `Import-Module` command, such as the Prefix parameter, which adds a distinctive prefix to the noun names of all imported commands, or the **NoClobber** parameter, which prevents the module from adding commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="ecd99-178">Pour importer des modules, utilisez l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-178">To import modules, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="ecd99-179">Pour importer des modules dans un emplacement PSModulePath de la session active, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="ecd99-179">To import modules in a PSModulePath location into the current session, use the following command format.</span></span>

```powershell
Import-Module <module-name>
```

<span data-ttu-id="ecd99-180">Par exemple, la commande suivante importe le module BitsTransfer dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ecd99-180">For example, the following command imports the BitsTransfer module into the current session.</span></span>

```powershell
Import-Module BitsTransfer
```

<span data-ttu-id="ecd99-181">Pour importer un module qui ne figure pas dans un emplacement de module par défaut, utilisez le chemin d'accès complet au dossier du module dans la commande.</span><span class="sxs-lookup"><span data-stu-id="ecd99-181">To import a module that is not in a default module location, use the fully qualified path to the module folder in the command.</span></span>

<span data-ttu-id="ecd99-182">Par exemple, pour ajouter le module TestCmdlets dans le `C:\ps-test` répertoire à votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-182">For example, to add the TestCmdlets module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets
```

<span data-ttu-id="ecd99-183">Pour importer un fichier de module qui ne figure pas dans un dossier de module, utilisez le chemin d'accès complet au fichier du module dans la commande.</span><span class="sxs-lookup"><span data-stu-id="ecd99-183">To import a module file that is not contained in a module folder, use the fully qualified path to the module file in the command.</span></span>

<span data-ttu-id="ecd99-184">Par exemple, pour ajouter le module TestCmdlets.dll dans le `C:\ps-test` répertoire à votre session, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-184">For example, to add the TestCmdlets.dll module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

<span data-ttu-id="ecd99-185">Pour plus d’informations sur l’ajout de modules à votre session, consultez [import-module](xref:Microsoft.PowerShell.Core.Import-Module).</span><span class="sxs-lookup"><span data-stu-id="ecd99-185">For more information about adding modules to your session, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="how-to-import-a-module-into-every-session"></a><span data-ttu-id="ecd99-186">Comment importer un module dans chaque session</span><span class="sxs-lookup"><span data-stu-id="ecd99-186">How to Import a Module into Every Session</span></span>

<span data-ttu-id="ecd99-187">La `Import-Module` commande importe les modules dans votre session PowerShell actuelle.</span><span class="sxs-lookup"><span data-stu-id="ecd99-187">The `Import-Module` command imports modules into your current PowerShell session.</span></span> <span data-ttu-id="ecd99-188">Pour importer un module dans chaque session PowerShell que vous démarrez, ajoutez la `Import-Module` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-188">To import a module into every PowerShell session that you start, add the `Import-Module` command to your PowerShell profile.</span></span>

<span data-ttu-id="ecd99-189">Pour plus d'informations sur les profils, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ecd99-189">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="how-to-remove-a-module"></a><span data-ttu-id="ecd99-190">Comment supprimer un module</span><span class="sxs-lookup"><span data-stu-id="ecd99-190">How to Remove a Module</span></span>

<span data-ttu-id="ecd99-191">Quand vous supprimez un module, les commandes ajoutées par le module sont supprimées de la session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-191">When you remove a module, the commands that the module added are deleted from the session.</span></span>

<span data-ttu-id="ecd99-192">Pour supprimer un module de votre session, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="ecd99-192">To remove a module from your session, use the following command format.</span></span>

```powershell
Remove-Module <module-name>
```

<span data-ttu-id="ecd99-193">Par exemple, la commande suivante supprime le module BitsTransfer de la session active.</span><span class="sxs-lookup"><span data-stu-id="ecd99-193">For example, the following command removes the BitsTransfer module from the current session.</span></span>

```powershell
Remove-Module BitsTransfer
```

<span data-ttu-id="ecd99-194">Le fait de supprimer un module annule l'opération d'importation d'un module.</span><span class="sxs-lookup"><span data-stu-id="ecd99-194">Removing a module reverses the operation of importing a module.</span></span> <span data-ttu-id="ecd99-195">Toutefois, le module supprimé n'est pas désinstallé.</span><span class="sxs-lookup"><span data-stu-id="ecd99-195">Removing a module does not uninstall the module.</span></span> <span data-ttu-id="ecd99-196">Pour plus d’informations, consultez [Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="ecd99-196">For more information, see [Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module).</span></span>

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a><span data-ttu-id="ecd99-197">Emplacements des ressources de module et DSC, et PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ecd99-197">Module and DSC Resource Locations, and PSModulePath</span></span>

<span data-ttu-id="ecd99-198">La `$env:PSModulePath` variable d’environnement contient une liste d’emplacements de dossiers dans lesquels rechercher des modules et des ressources.</span><span class="sxs-lookup"><span data-stu-id="ecd99-198">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="ecd99-199">Par défaut, les emplacements effectifs affectés à `$env:PSModulePath` sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="ecd99-199">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="ecd99-200">Emplacements à l’ensemble du système : `$PSHOME\Modules`</span><span class="sxs-lookup"><span data-stu-id="ecd99-200">System-wide locations: `$PSHOME\Modules`</span></span>

  <span data-ttu-id="ecd99-201">Ces dossiers contiennent des modules fournis avec Windows et PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-201">These folders contain modules that ship with Windows and PowerShell.</span></span>

  <span data-ttu-id="ecd99-202">Les ressources DSC incluses avec PowerShell sont stockées dans le `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` dossier.</span><span class="sxs-lookup"><span data-stu-id="ecd99-202">DSC resources that are included with PowerShell are stored in the `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` folder.</span></span>

- <span data-ttu-id="ecd99-203">Modules spécifiques à l’utilisateur : il s’agit de modules installés par l’utilisateur dans l’étendue de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ecd99-203">User-specific modules: These are modules installed by the user in the user's scope.</span></span> <span data-ttu-id="ecd99-204">`Install-Module` possède un paramètre d' **étendue** qui vous permet de spécifier si le module est installé pour l’utilisateur actuel ou pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ecd99-204">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="ecd99-205">Pour plus d’informations, consultez [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="ecd99-205">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  <span data-ttu-id="ecd99-206">L’emplacement **CurrentUser** spécifique à l’utilisateur sur Windows est le `PowerShell\Modules` dossier situé à l’emplacement **documents** dans votre profil utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ecd99-206">The user-specific **CurrentUser** location on Windows is the `PowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="ecd99-207">Le chemin d’accès spécifique de cet emplacement varie selon la version de Windows et si vous utilisez la redirection de dossiers ou non.</span><span class="sxs-lookup"><span data-stu-id="ecd99-207">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="ecd99-208">Microsoft OneDrive peut également modifier l’emplacement de votre dossier **documents** .</span><span class="sxs-lookup"><span data-stu-id="ecd99-208">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span>

  <span data-ttu-id="ecd99-209">Par défaut, sur Windows 10, cet emplacement est `$HOME\Documents\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-209">By default, on Windows 10, that location is `$HOME\Documents\PowerShell\Modules`.</span></span> <span data-ttu-id="ecd99-210">Sur Linux ou Mac, l’emplacement **CurrentUser** est `$HOME/.local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-210">On Linux or Mac, the **CurrentUser** location is `$HOME/.local/share/powershell/Modules`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ecd99-211">Vous pouvez vérifier l’emplacement de votre dossier **documents** à l’aide de la commande suivante : `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-211">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

- <span data-ttu-id="ecd99-212">L’emplacement de **ALLUSERS** est `$env:PROGRAMFILES\PowerShell\Modules` sur Windows.</span><span class="sxs-lookup"><span data-stu-id="ecd99-212">The **AllUsers** location is `$env:PROGRAMFILES\PowerShell\Modules` on Windows.</span></span> <span data-ttu-id="ecd99-213">Sur Linux ou Mac, les modules sont stockés à l’adresse `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-213">On Linux or Mac the modules are stored at `/usr/local/share/powershell/Modules`.</span></span>

> [!NOTE]
> <span data-ttu-id="ecd99-214">Pour ajouter ou modifier des fichiers dans le `$env:Windir\System32` répertoire, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="ecd99-214">To add or change files in the `$env:Windir\System32` directory, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="ecd99-215">Vous pouvez modifier les emplacements par défaut des modules sur votre système en modifiant la valeur de la variable d’environnement **PSModulePath** , `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-215">You can change the default module locations on your system by changing the value of the **PSModulePath** environment variable, `$Env:PSModulePath`.</span></span> <span data-ttu-id="ecd99-216">La variable d’environnement **PSModulePath** est modélisée sur la variable d’environnement PATH et a le même format.</span><span class="sxs-lookup"><span data-stu-id="ecd99-216">The **PSModulePath** environment variable is modeled on the Path environment variable and has the same format.</span></span>

<span data-ttu-id="ecd99-217">Pour afficher les emplacements par défaut des modules, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-217">To view the default module locations, type:</span></span>

```powershell
$Env:PSModulePath
```

<span data-ttu-id="ecd99-218">Pour ajouter un emplacement de module par défaut, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="ecd99-218">To add a default module location, use the following command format.</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

<span data-ttu-id="ecd99-219">Le point-virgule ( `;` ) dans la commande sépare le nouveau chemin d’accès du chemin d’accès qui le précède dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ecd99-219">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="ecd99-220">Par exemple, pour ajouter le `C:\ps-test\Modules` répertoire, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-220">For example, to add the `C:\ps-test\Modules` directory, type:</span></span>

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

<span data-ttu-id="ecd99-221">Pour ajouter un emplacement de module par défaut sur Linux ou MacOS, utilisez le format de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="ecd99-221">To add a default module location on Linux or MacOS, use the following command format:</span></span>

```powershell
$Env:PSModulePath += ":<path>"
```

<span data-ttu-id="ecd99-222">Par exemple, pour ajouter le `/usr/local/Fabrikam/Modules` répertoire à la valeur de la variable d’environnement **PSModulePath** , tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-222">For example, to add the `/usr/local/Fabrikam/Modules` directory to the value of the **PSModulePath** environment variable, type:</span></span>

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

<span data-ttu-id="ecd99-223">Sur Linux ou MacOS, le signe deux-points ( `:` ) dans la commande sépare le nouveau chemin d’accès du chemin d’accès qui le précède dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ecd99-223">On Linux or MacOS, the colon (`:`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="ecd99-224">Lorsque vous ajoutez un chemin d’accès à **PSModulePath**, `Get-Module` les `Import-Module` commandes incluent des modules dans ce chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ecd99-224">When you add a path to **PSModulePath**, `Get-Module` and `Import-Module` commands include modules in that path.</span></span>

<span data-ttu-id="ecd99-225">La valeur que vous définissez affecte uniquement la session active.</span><span class="sxs-lookup"><span data-stu-id="ecd99-225">The value that you set affects only the current session.</span></span> <span data-ttu-id="ecd99-226">Pour rendre le changement persistant, ajoutez la commande à votre profil PowerShell ou utilisez l’option système du panneau de configuration pour modifier la valeur de la variable d’environnement **PSModulePath** dans le registre.</span><span class="sxs-lookup"><span data-stu-id="ecd99-226">To make the change persistent, add the command to your PowerShell profile or use System in Control Panel to change the value of the **PSModulePath** environment variable in the registry.</span></span>

<span data-ttu-id="ecd99-227">En outre, pour rendre le changement persistant, vous pouvez également utiliser la méthode **SetEnvironmentVariable ne contient** de la classe **System. Environment** pour ajouter un chemin d’accès à la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="ecd99-227">Also, to make the change persistent, you can also use the **SetEnvironmentVariable** method of the **System.Environment** class to add a Path to the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="ecd99-228">Pour plus d’informations sur la variable **PSModulePath** , consultez [about_Environment_Variables](about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ecd99-228">For more information about the **PSModulePath** variable, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

## <a name="modules-and-name-conflicts"></a><span data-ttu-id="ecd99-229">Modules et conflits de noms</span><span class="sxs-lookup"><span data-stu-id="ecd99-229">Modules and Name Conflicts</span></span>

<span data-ttu-id="ecd99-230">Des conflits de noms se produisent quand plusieurs commandes portent le même nom dans la session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-230">Name conflicts occur when more than one command in the session has the same name.</span></span> <span data-ttu-id="ecd99-231">Quand vous importez un module, un conflit survient si les noms des commandes de ce module sont identiques à ceux de commandes ou d'éléments présents dans la session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-231">Importing a module causes a name conflict when commands in the module have the same names as commands or items in the session.</span></span>

<span data-ttu-id="ecd99-232">Les conflits de noms peuvent entraîner le masquage ou le remplacement de commandes.</span><span class="sxs-lookup"><span data-stu-id="ecd99-232">Name conflicts can result in commands being hidden or replaced.</span></span>

### <a name="hidden"></a><span data-ttu-id="ecd99-233">Hidden</span><span class="sxs-lookup"><span data-stu-id="ecd99-233">Hidden</span></span>

<span data-ttu-id="ecd99-234">Une commande est masquée si elle ne s'exécute pas quand vous tapez son nom. Vous pouvez toutefois l'exécuter en utilisant une autre méthode, par exemple en qualifiant le nom de la commande avec le nom du module ou du composant logiciel enfichable d'où elle provient.</span><span class="sxs-lookup"><span data-stu-id="ecd99-234">A command is hidden when it is not the command that runs when you type the command name, but you can run it by using another method, such as by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

### <a name="replaced"></a><span data-ttu-id="ecd99-235">Remplacé</span><span class="sxs-lookup"><span data-stu-id="ecd99-235">Replaced</span></span>

<span data-ttu-id="ecd99-236">Une commande est remplacée quand vous ne pouvez pas l'exécuter parce qu'elle a été remplacée par une commande du même nom.</span><span class="sxs-lookup"><span data-stu-id="ecd99-236">A command is replaced when you cannot run it because it has been overwritten by a command with the same name.</span></span> <span data-ttu-id="ecd99-237">Même quand vous supprimez le module à l'origine du conflit, vous ne pouvez pas exécuter une commande remplacée, à moins de redémarrer la session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-237">Even when you remove the module that caused the conflict, you cannot run a replaced command unless you restart the session.</span></span>

<span data-ttu-id="ecd99-238">`Import-Module` peut ajouter des commandes qui masquent et remplacent des commandes dans la session active.</span><span class="sxs-lookup"><span data-stu-id="ecd99-238">`Import-Module` might add commands that hide and replace commands in the current session.</span></span> <span data-ttu-id="ecd99-239">Par ailleurs, les commandes dans votre session peuvent masquer les commandes ajoutées par le module.</span><span class="sxs-lookup"><span data-stu-id="ecd99-239">Also, commands in your session can hide commands that the module added.</span></span>

<span data-ttu-id="ecd99-240">Pour détecter les conflits de noms, utilisez le paramètre **All** de l’applet de commande `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-240">To detect name conflicts, use the **All** parameter of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="ecd99-241">À compter de PowerShell 3,0, `Get-Command` obtient uniquement les commandes qui s’exécutent lorsque vous tapez le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="ecd99-241">Beginning in PowerShell 3.0, `Get-Command` gets only that commands that run when you type the command name.</span></span> <span data-ttu-id="ecd99-242">Le paramètre **All** obtient toutes les commandes portant le nom spécifique dans la session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-242">The **All** parameter gets all commands with the specific name in the session.</span></span>

<span data-ttu-id="ecd99-243">Pour éviter les conflits de noms, utilisez les paramètres **NoClobber** ou **prefix** de l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-243">To prevent name conflicts, use the **NoClobber** or **Prefix** parameters of the `Import-Module` cmdlet.</span></span> <span data-ttu-id="ecd99-244">Le paramètre **prefix** ajoute un préfixe aux noms des commandes importées afin qu’elles soient uniques dans la session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-244">The **Prefix** parameter adds a prefix to the names of imported commands so that they are unique in the session.</span></span> <span data-ttu-id="ecd99-245">Le paramètre **NoClobber** n’importe aucune commande susceptible de masquer ou de remplacer des commandes existantes dans la session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-245">The **NoClobber** parameter does not import any commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="ecd99-246">Vous pouvez également utiliser les paramètres **alias**, **cmdlet**, **Function** et **variable** de `Import-Module` pour sélectionner uniquement les commandes que vous souhaitez importer, et vous pouvez exclure les commandes qui provoquent des conflits de noms dans votre session.</span><span class="sxs-lookup"><span data-stu-id="ecd99-246">You can also use the **Alias**, **Cmdlet**, **Function**, and **Variable** parameters of `Import-Module` to select only the commands that you want to import, and you can exclude commands that cause name conflicts in your session.</span></span>

<span data-ttu-id="ecd99-247">Les auteurs de modules peuvent éviter les conflits de noms à l’aide de la propriété **DefaultCommandPrefix** du manifeste de module pour ajouter un préfixe par défaut à tous les noms de commandes.</span><span class="sxs-lookup"><span data-stu-id="ecd99-247">Module authors can prevent name conflicts by using the **DefaultCommandPrefix** property of the module manifest to add a default prefix to all command names.</span></span>
<span data-ttu-id="ecd99-248">La valeur du paramètre **prefix** est prioritaire sur la valeur de **DefaultCommandPrefix**.</span><span class="sxs-lookup"><span data-stu-id="ecd99-248">The value of the **Prefix** parameter takes precedence over the value of **DefaultCommandPrefix**.</span></span>

<span data-ttu-id="ecd99-249">Même si une commande est masquée, vous pouvez l'exécuter en qualifiant le nom de la commande avec le nom du module ou du composant logiciel enfichable d'où elle provient.</span><span class="sxs-lookup"><span data-stu-id="ecd99-249">Even if a command is hidden, you can run it by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

<span data-ttu-id="ecd99-250">Les règles de priorité des commandes PowerShell déterminent la commande qui est exécutée lorsque la session comprend des commandes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="ecd99-250">The PowerShell command precedence rules determine which command runs when the session includes commands with the same name.</span></span>

<span data-ttu-id="ecd99-251">Par exemple, lorsqu’une session comprend une fonction et une applet de commande portant le même nom, PowerShell exécute la fonction par défaut.</span><span class="sxs-lookup"><span data-stu-id="ecd99-251">For example, when a session includes a function and a cmdlet with the same name, PowerShell runs the function by default.</span></span> <span data-ttu-id="ecd99-252">Quand la session inclut des commandes du même type avec le même nom, par exemple deux applets de commande avec le même nom, la commande la plus récemment ajoutée est exécutée par défaut.</span><span class="sxs-lookup"><span data-stu-id="ecd99-252">When the session includes commands of the same type with the same name, such as two cmdlets with the same name, by default, it runs the most recently added command.</span></span>

<span data-ttu-id="ecd99-253">Pour plus d’informations, y compris une explication des règles de précédence et des instructions pour l’exécution de commandes masquées, consultez [about_Command_Precedence](about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ecd99-253">For more information, including an explanation of the precedence rules and instructions for running hidden commands, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

## <a name="modules-and-snap-ins"></a><span data-ttu-id="ecd99-254">Modules et composants logiciels enfichables</span><span class="sxs-lookup"><span data-stu-id="ecd99-254">Modules and Snap-ins</span></span>

<span data-ttu-id="ecd99-255">Vous pouvez ajouter des commandes à votre session à partir de modules et de composants logiciels enfichables. Les modules peuvent ajouter tous les types de commandes, y compris les applets de commande, les fournisseurs, les fonctions et les éléments, tels que les variables, les alias et les lecteurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-255">You can add commands to your session from modules and snap-ins. Modules can add all types of commands, including cmdlets, providers, and functions, and items, such as variables, aliases, and PowerShell drives.</span></span> <span data-ttu-id="ecd99-256">Les composants logiciels enfichables peuvent uniquement ajouter des applets de commande et des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="ecd99-256">Snap-ins can add only cmdlets and providers.</span></span>

<span data-ttu-id="ecd99-257">Avant de supprimer un module ou un composant logiciel enfichable de votre session, utilisez les commandes suivantes pour déterminer les commandes qui seront supprimées.</span><span class="sxs-lookup"><span data-stu-id="ecd99-257">Before removing a module or snap-in from your session, use the following commands to determine which commands will be removed.</span></span>

<span data-ttu-id="ecd99-258">Pour rechercher la source d’une applet de commande dans votre session, utilisez le format de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="ecd99-258">To find the source of a cmdlet in your session, use the following command format:</span></span>

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

<span data-ttu-id="ecd99-259">Par exemple, pour trouver la source de l' `Get-Date` applet de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="ecd99-259">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a><span data-ttu-id="ecd99-260">Avertissements et erreurs liés au module</span><span class="sxs-lookup"><span data-stu-id="ecd99-260">Module-related Warnings and Errors</span></span>

<span data-ttu-id="ecd99-261">Les commandes exportées par un module doivent respecter les règles d’affectation des noms de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-261">The commands that a module exports should follow the PowerShell command naming rules.</span></span> <span data-ttu-id="ecd99-262">Si le module que vous importez exporte des applets de commande ou des fonctions dont les noms comportent des verbes non approuvés, l' `Import-Module` applet de commande affiche le message d’avertissement suivant.</span><span class="sxs-lookup"><span data-stu-id="ecd99-262">If the module that you import exports cmdlets or functions that have unapproved verbs in their names, the `Import-Module` cmdlet displays the following warning message.</span></span>

> <span data-ttu-id="ecd99-263">AVERTISSEMENT : certains noms de commandes importés incluent des verbes non approuvés qui peuvent les rendre moins détectables.</span><span class="sxs-lookup"><span data-stu-id="ecd99-263">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="ecd99-264">Utilisez le paramètre Verbose pour obtenir plus d'informations ou tapez Get-Verb pour afficher la liste des verbes approuvés.</span><span class="sxs-lookup"><span data-stu-id="ecd99-264">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="ecd99-265">Ce message n'est qu'un avertissement.</span><span class="sxs-lookup"><span data-stu-id="ecd99-265">This message is only a warning.</span></span> <span data-ttu-id="ecd99-266">Le module entier est toujours importé, y compris les commandes non conformes.</span><span class="sxs-lookup"><span data-stu-id="ecd99-266">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="ecd99-267">Bien que le message soit affiché aux utilisateurs du module, le problème d'affectation de noms doit être corrigé par l'auteur du module.</span><span class="sxs-lookup"><span data-stu-id="ecd99-267">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

<span data-ttu-id="ecd99-268">Pour supprimer le message d’avertissement, utilisez le paramètre **DisableNameChecking** de l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-268">To suppress the warning message, use the **DisableNameChecking** parameter of the `Import-Module` cmdlet.</span></span>

## <a name="built-in-modules-and-snap-ins"></a><span data-ttu-id="ecd99-269">Modules intégrés et composants logiciels enfichables</span><span class="sxs-lookup"><span data-stu-id="ecd99-269">Built-in Modules and Snap-ins</span></span>

<span data-ttu-id="ecd99-270">Dans PowerShell 2,0 et dans les anciens programmes hôtes de PowerShell 3,0 et versions ultérieures, les commandes de base qui sont installées avec PowerShell sont empaquetées dans des composants logiciels enfichables qui sont ajoutés automatiquement à chaque session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-270">In PowerShell 2.0 and in older-style host programs in PowerShell 3.0 and later, the core commands that are installed with PowerShell are packaged in snap-ins that are added automatically to every PowerShell session.</span></span>

<span data-ttu-id="ecd99-271">À compter de PowerShell 3,0, pour les programmes hôtes qui implémentent l' `InitialSessionState.CreateDefault2` API d’état de session initiale, le composant logiciel enfichable Microsoft. PowerShell. Core est ajouté à chaque session par défaut.</span><span class="sxs-lookup"><span data-stu-id="ecd99-271">Beginning in PowerShell 3.0, for host programs that implement the `InitialSessionState.CreateDefault2` initial session state API the Microsoft.PowerShell.Core snap-in is added to every session by default.</span></span> <span data-ttu-id="ecd99-272">Les modules sont chargés automatiquement lors de la première utilisation.</span><span class="sxs-lookup"><span data-stu-id="ecd99-272">Modules are loaded automatically on first-use.</span></span>

> [!NOTE]
> <span data-ttu-id="ecd99-273">Les sessions à distance, y compris les sessions démarrées à l’aide de l' `New-PSSession` applet de commande, sont des sessions de style plus ancienne dans lesquelles les commandes intégrées sont empaquetées dans des composants logiciels enfichables.</span><span class="sxs-lookup"><span data-stu-id="ecd99-273">Remote sessions, including sessions that are started by using the `New-PSSession` cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="ecd99-274">Les modules (ou composants logiciels enfichables) suivants sont installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-274">The following modules (or snap-ins) are installed with PowerShell.</span></span>

- <span data-ttu-id="ecd99-275">CimCmdlets</span><span class="sxs-lookup"><span data-stu-id="ecd99-275">CimCmdlets</span></span>
- <span data-ttu-id="ecd99-276">Microsoft.PowerShell.Archive</span><span class="sxs-lookup"><span data-stu-id="ecd99-276">Microsoft.PowerShell.Archive</span></span>
- <span data-ttu-id="ecd99-277">Microsoft.PowerShell.Core</span><span class="sxs-lookup"><span data-stu-id="ecd99-277">Microsoft.PowerShell.Core</span></span>
- <span data-ttu-id="ecd99-278">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="ecd99-278">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="ecd99-279">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="ecd99-279">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="ecd99-280">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="ecd99-280">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="ecd99-281">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="ecd99-281">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="ecd99-282">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="ecd99-282">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="ecd99-283">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="ecd99-283">Microsoft.WSMan.Management</span></span>
- <span data-ttu-id="ecd99-284">PackageManagement</span><span class="sxs-lookup"><span data-stu-id="ecd99-284">PackageManagement</span></span>
- <span data-ttu-id="ecd99-285">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="ecd99-285">PowerShellGet</span></span>
- <span data-ttu-id="ecd99-286">PSDesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ecd99-286">PSDesiredStateConfiguration</span></span>
- <span data-ttu-id="ecd99-287">PSDiagnostics</span><span class="sxs-lookup"><span data-stu-id="ecd99-287">PSDiagnostics</span></span>
- <span data-ttu-id="ecd99-288">PSReadline</span><span class="sxs-lookup"><span data-stu-id="ecd99-288">PSReadline</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="ecd99-289">Journalisation des événements du module</span><span class="sxs-lookup"><span data-stu-id="ecd99-289">Logging Module Events</span></span>

<span data-ttu-id="ecd99-290">À compter de PowerShell 3,0, vous pouvez enregistrer les événements d’exécution des applets de commande et des fonctions dans les modules et les composants logiciels enfichables PowerShell en affectant à la propriété **LogPipelineExecutionDetails** des modules et des composants logiciels enfichables `$True` .</span><span class="sxs-lookup"><span data-stu-id="ecd99-290">Beginning in PowerShell 3.0, you can record execution events for the cmdlets and functions in PowerShell modules and snap-ins by setting the **LogPipelineExecutionDetails** property of modules and snap-ins to `$True`.</span></span>
<span data-ttu-id="ecd99-291">Vous pouvez également utiliser un paramètre stratégie de groupe, activer la journalisation des modules, pour activer la journalisation des modules dans toutes les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecd99-291">You can also use a Group Policy setting, Turn on Module Logging, to enable module logging in all PowerShell sessions.</span></span> <span data-ttu-id="ecd99-292">Pour plus d’informations, consultez les articles sur la journalisation et la stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="ecd99-292">For more information, see the logging and group policy articles.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecd99-293">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecd99-293">See Also</span></span>

[<span data-ttu-id="ecd99-294">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="ecd99-294">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="ecd99-295">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="ecd99-295">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="ecd99-296">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="ecd99-296">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="ecd99-297">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="ecd99-297">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="ecd99-298">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="ecd99-298">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="ecd99-299">Get-Command</span><span class="sxs-lookup"><span data-stu-id="ecd99-299">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="ecd99-300">Get-Help</span><span class="sxs-lookup"><span data-stu-id="ecd99-300">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="ecd99-301">Get-Module</span><span class="sxs-lookup"><span data-stu-id="ecd99-301">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="ecd99-302">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="ecd99-302">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="ecd99-303">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="ecd99-303">Remove-Module</span></span>](xref:Microsoft.PowerShell.Core.Remove-Module)
