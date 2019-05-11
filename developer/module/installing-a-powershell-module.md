---
title: Installation d’un Module PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229455"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="f5f82-102">Installation d’un module PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5f82-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="f5f82-103">Une fois que vous avez créé votre module PowerShell, vous pouvez installer le module sur un système, afin que vous ou autres utilisateurs peuvent l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="f5f82-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="f5f82-104">En règle générale, cela consiste à copier les fichiers de module (Internet Explorer, le .psm1, ou l’assembly binaire, le manifeste de module et tous les autres fichiers associés) sur un répertoire sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f5f82-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="f5f82-105">Pour un très petit projet, cela peut être aussi simple que de copier et coller les fichiers avec l’Explorateur Windows sur un seul ordinateur distant ; Toutefois, pour les solutions plus volumineuses, vous souhaiterez utiliser un processus d’installation plus sophistiqué.</span><span class="sxs-lookup"><span data-stu-id="f5f82-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="f5f82-106">Quelle que soit la façon dont vous obtenez votre module sur le système, PowerShell peut utiliser un certain nombre de techniques qui permettent aux utilisateurs de trouver et utiliser vos modules.</span><span class="sxs-lookup"><span data-stu-id="f5f82-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="f5f82-107">Par conséquent, le problème principal pour l’installation consiste à s’assurer que PowerShell sera en mesure de trouver votre module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="f5f82-108">Pour plus d’informations, consultez [importation d’un PowerShell Module](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="f5f82-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="f5f82-109">Règles pour l’installation de Modules</span><span class="sxs-lookup"><span data-stu-id="f5f82-109">Rules for Installing Modules</span></span>

<span data-ttu-id="f5f82-110">Les informations suivantes se rapportent à tous les modules, y compris les modules que vous créez pour votre propre utilisation, les modules que vous obtenez d’autres parties et les modules que vous distribuez à d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="f5f82-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="f5f82-111">Installer des Modules de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="f5f82-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="f5f82-112">Si possible, installez tous les modules dans un chemin d’accès qui est répertorié dans le **PSModulePath** variable d’environnement ou ajouter le chemin d’accès de module pour le **PSModulePath** valeur de variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f5f82-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="f5f82-113">Le **PSModulePath** variable d’environnement ($Env : PSModulePath) contient les emplacements des modules Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5f82-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="f5f82-114">Applets de commande s’appuient sur la valeur de cette variable d’environnement pour rechercher des modules.</span><span class="sxs-lookup"><span data-stu-id="f5f82-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="f5f82-115">Par défaut, le **PSModulePath** valeur de la variable contient le système suivantes et les répertoires de module d’utilisateur, mais vous pouvez ajouter à et modifier la valeur.</span><span class="sxs-lookup"><span data-stu-id="f5f82-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="f5f82-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="f5f82-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="f5f82-117">Cet emplacement est réservé pour les modules fournis avec Windows.</span><span class="sxs-lookup"><span data-stu-id="f5f82-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="f5f82-118">N’installez pas de modules à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="f5f82-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="f5f82-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="f5f82-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="f5f82-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="f5f82-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="f5f82-121">Pour obtenir la valeur de la **PSModulePath** variable d’environnement, utilisez une des commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f5f82-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="f5f82-122">Pour ajouter un chemin d’accès du module à la valeur de la **PSModulePath** variable d’environnement, utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="f5f82-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="f5f82-123">Ce format utilise le **SetEnvironmentVariable ne contient pas** méthode de la **System.Environment** classe pour apporter une modification de session indépendante au **PSModulePath** environnement variable.</span><span class="sxs-lookup"><span data-stu-id="f5f82-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="f5f82-124">Une fois que vous avez ajouté le chemin d’accès à **PSModulePath**, vous devez diffuser un message d’environnement sur la modification.</span><span class="sxs-lookup"><span data-stu-id="f5f82-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="f5f82-125">Diffusion de la modification permet aux autres applications, telles que l’interpréteur de commandes, la modification.</span><span class="sxs-lookup"><span data-stu-id="f5f82-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="f5f82-126">Pour diffuser la modification, que votre code d’installation de produit envoie un **WM_SETTINGCHANGE** message avec `lParam` défini sur la chaîne « Environnement ».</span><span class="sxs-lookup"><span data-stu-id="f5f82-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="f5f82-127">Veillez à envoyer le message une fois que votre code d’installation de module a mis à jour **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="f5f82-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="f5f82-128">Utilisez le nom de répertoire de Module approprié</span><span class="sxs-lookup"><span data-stu-id="f5f82-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="f5f82-129">Un module correct est un module qui est stocké dans un répertoire portant le même nom que le nom de base d’au moins un fichier dans le répertoire de module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="f5f82-130">Si un module n’est pas bien formé, Windows PowerShell ne le reconnaît pas en tant que module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="f5f82-131">Le nom « base » d’un fichier est le nom sans l’extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="f5f82-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="f5f82-132">Dans un module bien formé, le nom du répertoire qui contient les fichiers de module doit correspondre au nom de base d’au moins un fichier dans le module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="f5f82-133">Par exemple, dans l’exemple de module de Fabrikam, le répertoire qui contient les fichiers de module est nommé « Fabrikam » et au moins un fichier a le nom de base « Fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="f5f82-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="f5f82-134">Dans ce cas, Fabrikam.psd1 et Fabrikam.dll ont le nom de base « Fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="f5f82-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="f5f82-135">Effet de l’Installation incorrecte</span><span class="sxs-lookup"><span data-stu-id="f5f82-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="f5f82-136">Si le module n’est pas bien formé et son emplacement n’est pas inclus dans la valeur de la **PSModulePath** variable d’environnement, fonctionnalités élémentaires de découverte de Windows PowerShell, comme celle ci-dessous, ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="f5f82-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="f5f82-137">La fonctionnalité de chargement automatique de Module ne peut pas importer le module automatiquement.</span><span class="sxs-lookup"><span data-stu-id="f5f82-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="f5f82-138">Le `ListAvailable` paramètre de la [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) applet de commande ne peut pas trouver le module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="f5f82-139">Le [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande ne peut pas trouver le module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="f5f82-140">Pour importer le module, vous devez fournir le chemin d’accès complet au fichier de module racine ou au fichier manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="f5f82-141">Des fonctionnalités supplémentaires, telles que la commande suivante, ne fonctionnent pas, sauf si le module est importé dans la session.</span><span class="sxs-lookup"><span data-stu-id="f5f82-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="f5f82-142">Dans les modules bien formés dans le **PSModulePath** variable d’environnement, ces fonctionnalités fonctionnent même lorsque le module n’est pas importé dans la session.</span><span class="sxs-lookup"><span data-stu-id="f5f82-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="f5f82-143">Le [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) applet de commande ne peut pas trouver les commandes dans le module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="f5f82-144">Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) applets de commande ne peut pas mettre à jour ou enregistrer l’aide du module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="f5f82-145">Le [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) applet de commande ne peut pas rechercher et afficher les commandes dans le module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="f5f82-146">Les commandes du module sont manquants dans le `Show-Command` fenêtre dans Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f5f82-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="f5f82-147">Où installer les Modules</span><span class="sxs-lookup"><span data-stu-id="f5f82-147">Where to Install Modules</span></span>

<span data-ttu-id="f5f82-148">Cette section explique où dans le système de fichiers pour installer les modules Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5f82-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="f5f82-149">L’emplacement dépend de la façon dont le module est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f5f82-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="f5f82-150">Installation de Modules pour un utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="f5f82-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="f5f82-151">Si vous créez votre propre module ou obtenez un module à partir d’une autre partie, par exemple un site Web communautaire de Windows PowerShell, et que le module soit disponible pour votre compte d’utilisateur, installer le module dans votre répertoire de Modules spécifiques à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f5f82-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="f5f82-152">Le répertoire de Modules spécifiques à l’utilisateur est ajouté à la valeur de la **PSModulePath** variable d’environnement par défaut.</span><span class="sxs-lookup"><span data-stu-id="f5f82-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="f5f82-153">Installation de Modules pour tous les utilisateurs dans les fichiers programme</span><span class="sxs-lookup"><span data-stu-id="f5f82-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="f5f82-154">Si vous souhaitez un module soit disponible pour tous les comptes d’utilisateur sur l’ordinateur, installez le module dans l’emplacement des fichiers de programme.</span><span class="sxs-lookup"><span data-stu-id="f5f82-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="f5f82-155">L’emplacement des fichiers de programme est ajouté à la valeur de la variable d’environnement PSModulePath par défaut dans Windows PowerShell 4.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f5f82-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="f5f82-156">Pour les versions antérieures de Windows PowerShell, vous pouvez manuellement créer la ((%ProgramFiles%\WindowsPowerShell\Modules) emplacement Program Files et ajouter ce chemin d’accès à votre variable d’environnement PSModulePath, comme décrit ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="f5f82-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="f5f82-157">Installation de Modules dans un répertoire de produit</span><span class="sxs-lookup"><span data-stu-id="f5f82-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="f5f82-158">Si vous voulez distribuer le module à d’autres parties, utiliser l’emplacement des fichiers de programme par défaut décrit ci-dessus, ou créez votre propre sous-répertoire spécifique à la société ou spécifiques au produit du répertoire % ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="f5f82-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="f5f82-159">Par exemple, Fabrikam Technologies, une société fictive, est prévu pour fonctionner un module Windows PowerShell pour leur produit Manager de Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="f5f82-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="f5f82-160">Leur programme d’installation du module crée également un sous-répertoire de Modules dans le sous-répertoire de product Manager de Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="f5f82-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="f5f82-161">Pour activer les fonctionnalités de découverte de module Windows PowerShell rechercher le module de Fabrikam, le programme d’installation du module de Fabrikam ajoute l’emplacement de module à la valeur de la **PSModulePath** variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f5f82-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="f5f82-162">Installation de Modules dans le répertoire des fichiers communs</span><span class="sxs-lookup"><span data-stu-id="f5f82-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="f5f82-163">Si un module est utilisé par plusieurs composants d’un produit ou par plusieurs versions d’un produit, installez le module dans un sous-répertoire spécifique au module du sous-répertoire Files\Modules %ProgramFiles%\Common.</span><span class="sxs-lookup"><span data-stu-id="f5f82-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="f5f82-164">Dans l’exemple suivant, le module de Fabrikam est installé dans un sous-répertoire de Fabrikam de la `%ProgramFiles%\Common Files\Modules` sous-répertoire.</span><span class="sxs-lookup"><span data-stu-id="f5f82-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="f5f82-165">Notez que chaque module réside dans son propre sous-répertoire dans le sous-répertoire de Modules.</span><span class="sxs-lookup"><span data-stu-id="f5f82-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="f5f82-166">Ensuite, le programme d’installation garantit la valeur de la **PSModulePath** variable d’environnement inclut le chemin d’accès du sous-répertoire de modules de fichiers courants.</span><span class="sxs-lookup"><span data-stu-id="f5f82-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="f5f82-167">Installation de plusieurs Versions d’un Module</span><span class="sxs-lookup"><span data-stu-id="f5f82-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="f5f82-168">Pour installer plusieurs versions du même module, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="f5f82-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="f5f82-169">Créez un répertoire pour chaque version du module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="f5f82-170">Inclure le numéro de version dans le nom du répertoire.</span><span class="sxs-lookup"><span data-stu-id="f5f82-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="f5f82-171">Créez un manifeste de module pour chaque version du module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="f5f82-172">Dans la valeur de la **ModuleVersion** dans le manifeste de clé, entrez le numéro de version du module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="f5f82-173">Enregistrez le fichier manifest (.psd1) dans le répertoire spécifique à la version du module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="f5f82-174">Ajouter le chemin de dossier de module racine à la valeur de la **PSModulePath** variable d’environnement, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="f5f82-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="f5f82-175">Pour importer une version particulière du module, l’utilisateur final peut utiliser le `MinimumVersion` ou `RequiredVersion` paramètres de le [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f5f82-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="f5f82-176">Par exemple, si le module de Fabrikam est disponible dans les versions 8.0 et 9.0, la structure de répertoire de module de Fabrikam peut se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="f5f82-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="f5f82-177">Le programme d’installation ajoute les deux les chemins d’accès de module pour le **PSModulePath** valeur de variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="f5f82-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="f5f82-178">Une fois ces étapes terminées, le **ListAvailable** paramètre de la [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) applet de commande Obtient les deux modules de Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="f5f82-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="f5f82-179">Pour importer un module particulier, utilisez le `MinimumVersion` ou `RequiredVersion` paramètres de le [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f5f82-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="f5f82-180">Si les deux modules sont importés dans la même session, et les modules contiennent des applets de commande avec les mêmes noms, les applets de commande sont importés en dernier sont efficaces dans la session.</span><span class="sxs-lookup"><span data-stu-id="f5f82-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="f5f82-181">Gestion des conflits de nom de commande</span><span class="sxs-lookup"><span data-stu-id="f5f82-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="f5f82-182">Conflits de noms de commande peuvent se produire lorsque les commandes exportées par un module possèdent le même nom que les commandes dans la session utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f5f82-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="f5f82-183">Lorsqu’une session contient deux commandes qui ont le même nom, Windows PowerShell s’exécute le type de commande qui est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="f5f82-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="f5f82-184">Lorsqu’une session contient deux commandes qui ont le même nom et le même type, Windows PowerShell exécute la commande qui a été ajoutée à la session la plus récemment.</span><span class="sxs-lookup"><span data-stu-id="f5f82-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="f5f82-185">Pour exécuter une commande qui n’est pas exécutée par défaut, les utilisateurs peuvent qualifier le nom de commande avec le nom du module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="f5f82-186">Par exemple, si la session contient un `Get-Date` (fonction) et le `Get-Date` applet de commande Windows PowerShell exécute la fonction par défaut.</span><span class="sxs-lookup"><span data-stu-id="f5f82-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="f5f82-187">Pour exécuter l’applet de commande, la faire précéder le nom du module, tel que :</span><span class="sxs-lookup"><span data-stu-id="f5f82-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="f5f82-188">Pour éviter les conflits de noms, les auteurs de modules peuvent utiliser le **DefaultCommandPrefix** clé dans le manifeste de module pour spécifier un préfixe pour toutes les commandes exportées à partir du module.</span><span class="sxs-lookup"><span data-stu-id="f5f82-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="f5f82-189">Les utilisateurs peuvent utiliser le **préfixe** paramètre de la `Import-Module` applet de commande à utiliser un autre préfixe.</span><span class="sxs-lookup"><span data-stu-id="f5f82-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="f5f82-190">La valeur de la **préfixe** paramètre est prioritaire sur la valeur de la **DefaultCommandPrefix** clé.</span><span class="sxs-lookup"><span data-stu-id="f5f82-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5f82-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5f82-191">See Also</span></span>

[<span data-ttu-id="f5f82-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="f5f82-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="f5f82-193">Écrire un Module PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="f5f82-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
