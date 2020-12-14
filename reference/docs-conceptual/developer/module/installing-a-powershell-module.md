---
ms.date: 09/13/2016
ms.topic: reference
title: Installation d’un module PowerShell
description: Installation d’un module PowerShell
ms.openlocfilehash: 3c7a4413168934ca4de1912c9615a6ae0fc45788
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645334"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="87dc0-103">Installation d’un module PowerShell</span><span class="sxs-lookup"><span data-stu-id="87dc0-103">Installing a PowerShell Module</span></span>

<span data-ttu-id="87dc0-104">Après avoir créé votre module PowerShell, vous souhaitez probablement l’installer sur un système, afin que vous ou d’autres utilisateurs puissiez l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="87dc0-104">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="87dc0-105">En règle générale, l’opération consiste à copier les fichiers de module (soit le fichier .psm1 ou l’assembly binaire, le manifeste du module et tous les fichiers associés) dans un répertoire sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="87dc0-105">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="87dc0-106">Pour un très petit projet, il peut suffire de copier et de coller les fichiers avec l’Explorateur Windows sur un seul ordinateur distant. Pour les plus grosses solutions toutefois, il peut être préférable de suivre un processus d’installation plus élaboré.</span><span class="sxs-lookup"><span data-stu-id="87dc0-106">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="87dc0-107">Quelle que soit la façon dont le module est ajouté sur le système, PowerShell peut utiliser un certain nombre de techniques qui permettront aux utilisateurs de le trouver et de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="87dc0-107">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="87dc0-108">Par conséquent, le problème principal de l’installation consiste à faire en sorte que PowerShell soit en mesure de le localiser.</span><span class="sxs-lookup"><span data-stu-id="87dc0-108">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="87dc0-109">Pour plus d’informations, consultez [Importation d’un module PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="87dc0-109">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="87dc0-110">Règles d’installation des modules</span><span class="sxs-lookup"><span data-stu-id="87dc0-110">Rules for Installing Modules</span></span>

<span data-ttu-id="87dc0-111">Les informations suivantes se rapportent à tous les modules, y compris ceux que vous créez pour votre propre usage, ceux que vous recevez d’autres parties et ceux que vous distribuez à des tiers.</span><span class="sxs-lookup"><span data-stu-id="87dc0-111">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="87dc0-112">Installation de modules dans PSModulePath</span><span class="sxs-lookup"><span data-stu-id="87dc0-112">Install Modules in PSModulePath</span></span>

<span data-ttu-id="87dc0-113">Dans la mesure du possible, installez tous les modules dans un chemin qui figure dans la variable d’environnement **PSModulePath** ou ajoutez le chemin du module à la valeur de cette variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="87dc0-113">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="87dc0-114">La variable d’environnement **PSModulePath** ($Env:PSModulePath) contient les emplacements des modules Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87dc0-114">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="87dc0-115">Les cmdlets s’appuient sur la valeur de cette variable d’environnement pour rechercher des modules.</span><span class="sxs-lookup"><span data-stu-id="87dc0-115">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="87dc0-116">Par défaut, la valeur de la variable d’environnement **PSModulePath** contient les répertoires de modules système et utilisateur suivants. Vous pouvez toutefois les modifier et en ajouter d’autres.</span><span class="sxs-lookup"><span data-stu-id="87dc0-116">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="87dc0-117">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="87dc0-117">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="87dc0-118">Cet emplacement est réservé aux modules fournis avec Windows.</span><span class="sxs-lookup"><span data-stu-id="87dc0-118">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="87dc0-119">N’installez pas de modules à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="87dc0-119">Do not install modules to this location.</span></span>

- <span data-ttu-id="87dc0-120">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="87dc0-120">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="87dc0-121">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="87dc0-121">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="87dc0-122">Pour récupérer la valeur de la variable d’environnement **PSModulePath**, utilisez l’une des commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="87dc0-122">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="87dc0-123">Pour ajouter un chemin de module à la valeur de la variable d’environnement **PSModulePath**, suivez le format de commande ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="87dc0-123">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="87dc0-124">Ce format utilise la méthode **SetEnvironmentVariable** de la classe **System.Environment** pour appliquer une modification indépendante de la session à la variable d’environnement **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="87dc0-124">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="87dc0-125">Une fois que vous avez ajouté le chemin à **PSModulePath**, diffusez un message d’environnement au sujet de cette modification</span><span class="sxs-lookup"><span data-stu-id="87dc0-125">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="87dc0-126">pour permettre à d’autres applications (notamment l’interpréteur de commandes) de la récupérer.</span><span class="sxs-lookup"><span data-stu-id="87dc0-126">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="87dc0-127">Pour diffuser la modification, faites en sorte que le code d’installation de votre produit envoie un message **WM_SETTINGCHANGE** avec `lParam` défini sur la chaîne « Environment ».</span><span class="sxs-lookup"><span data-stu-id="87dc0-127">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="87dc0-128">Veillez à envoyer le message une fois que le code d’installation de votre module a mis à jour **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="87dc0-128">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="87dc0-129">Choix du nom de répertoire du module</span><span class="sxs-lookup"><span data-stu-id="87dc0-129">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="87dc0-130">Un module bien formé est un module stocké dans un répertoire portant le même nom que le nom de base d’au moins un des fichiers du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-130">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="87dc0-131">Windows PowerShell ne reconnaît pas comme modules les modules qui ne sont pas bien formés.</span><span class="sxs-lookup"><span data-stu-id="87dc0-131">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="87dc0-132">Le « nom de base » d’un fichier correspond au nom sans l’extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="87dc0-132">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="87dc0-133">Dans un module bien formé, le nom du répertoire contenant les fichiers du module doit correspondre au nom de base d’au moins un des fichiers du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-133">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="87dc0-134">Dans l’exemple de module Fabrikam, le répertoire qui contient les fichiers du module est nommé « Fabrikam » et au moins un fichier possède le nom de base « Fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="87dc0-134">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="87dc0-135">Dans ce cas, Fabrikam.psd1 et Fabrikam.dll présentent tous les deux le nom de base « Fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="87dc0-135">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="87dc0-136">Effet d’une installation incorrecte</span><span class="sxs-lookup"><span data-stu-id="87dc0-136">Effect of Incorrect Installation</span></span>

<span data-ttu-id="87dc0-137">Si le module n’est pas bien formé et que son emplacement n’est pas inclus dans la valeur de la variable d’environnement **PSModulePath**, les fonctionnalités de découverte de base de Windows PowerShell, et notamment les suivantes, ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="87dc0-137">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="87dc0-138">La fonctionnalité de chargement automatique de module ne peut pas importer le module automatiquement.</span><span class="sxs-lookup"><span data-stu-id="87dc0-138">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="87dc0-139">Le paramètre `ListAvailable` de la cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) ne trouve pas le module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-139">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="87dc0-140">La cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ne trouve pas le module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-140">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="87dc0-141">Pour importer le module, vous devez indique le chemin complet du fichier de module racine ou du fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-141">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="87dc0-142">Les fonctionnalités supplémentaires, et notamment les suivantes, ne fonctionnent pas tant que le module n’est pas importé dans la session.</span><span class="sxs-lookup"><span data-stu-id="87dc0-142">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="87dc0-143">Dans les modules bien formés présents dans la variable d’environnement **PSModulePath**, elles fonctionnent même si le module n’est pas importé dans la session.</span><span class="sxs-lookup"><span data-stu-id="87dc0-143">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="87dc0-144">La cmdlet [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) ne trouve pas de commandes dans le module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-144">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="87dc0-145">Les cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) ne parviennent pas à mettre à jour/enregistrer l’aide du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-145">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="87dc0-146">La cmdlet [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) ne parvient pas à localiser ni à afficher les commandes du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-146">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="87dc0-147">Les commandes du module sont absentes de la fenêtre `Show-Command` dans l’Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="87dc0-147">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="87dc0-148">Emplacement d’installation des modules</span><span class="sxs-lookup"><span data-stu-id="87dc0-148">Where to Install Modules</span></span>

<span data-ttu-id="87dc0-149">Cette section explique où installer les modules Windows PowerShell dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="87dc0-149">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="87dc0-150">L’emplacement dépend de l’utilisation du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-150">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="87dc0-151">Installation de modules pour un utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="87dc0-151">Installing Modules for a Specific User</span></span>

<span data-ttu-id="87dc0-152">Si vous créez votre propre module ou que vous en recevez un d’un tiers (par exemple, un site web de la communauté Windows PowerShell) et que vous souhaitez qu’il ne soit accessible qu’à votre compte d’utilisateur, installez-le dans votre répertoire Modules propre à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="87dc0-152">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="87dc0-153">Le répertoire Modules propre à l’utilisateur est ajouté à la valeur de la variable d’environnement **PSModulePath** par défaut.</span><span class="sxs-lookup"><span data-stu-id="87dc0-153">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="87dc0-154">Installation de modules pour tous les utilisateurs dans Program Files</span><span class="sxs-lookup"><span data-stu-id="87dc0-154">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="87dc0-155">Si vous souhaitez qu’un module soit accessible à tous les comptes d’utilisateur de l’ordinateur, installez-le à l’emplacement Program Files.</span><span class="sxs-lookup"><span data-stu-id="87dc0-155">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="87dc0-156">L’emplacement Program Files est ajouté à la valeur de la variable d’environnement PSModulePath par défaut dans la version 4.0 et les versions ultérieures de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87dc0-156">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="87dc0-157">Dans les versions antérieures de Windows PowerShell, vous pouvez créer manuellement l’emplacement Program Files (%ProgramFiles%\WindowsPowerShell\Modules) et ajouter ce chemin à votre variable d’environnement PSModulePath (cf. plus haut).</span><span class="sxs-lookup"><span data-stu-id="87dc0-157">For earlier versions of Windows PowerShell, you can manually create the Program Files location (%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="87dc0-158">Installation de modules dans un répertoire de produit</span><span class="sxs-lookup"><span data-stu-id="87dc0-158">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="87dc0-159">Si vous distribuez le module à des tiers, choisissez l’emplacement Program Files par défaut décrit ci-dessus ou créez votre propre sous-répertoire propre à la société ou au produit du répertoire %ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="87dc0-159">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="87dc0-160">Par exemple, Fabrikam Technologies, une société fictive, livre un module Windows PowerShell pour son produit Fabrikam Manager.</span><span class="sxs-lookup"><span data-stu-id="87dc0-160">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="87dc0-161">Le programme d’installation du module crée un sous-répertoire Modules dans le sous-répertoire du produit Fabrikam Manager.</span><span class="sxs-lookup"><span data-stu-id="87dc0-161">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="87dc0-162">Pour permettre aux fonctionnalités de découverte de modules Windows PowerShell de trouver le module Fabrikam, le programme d’installation de ce dernier ajoute l’emplacement du module à la valeur de la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="87dc0-162">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="87dc0-163">Installation de modules dans le répertoire Common Files</span><span class="sxs-lookup"><span data-stu-id="87dc0-163">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="87dc0-164">Si un module est utilisé par plusieurs composants ou plusieurs versions d’un produit, installez-le dans un sous-répertoire propre au module du sous-répertoire %ProgramFiles%\Common Files\Modules.</span><span class="sxs-lookup"><span data-stu-id="87dc0-164">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="87dc0-165">Dans l’exemple suivant, le module Fabrikam est installé dans un sous-répertoire Fabrikam du sous-répertoire `%ProgramFiles%\Common Files\Modules`.</span><span class="sxs-lookup"><span data-stu-id="87dc0-165">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="87dc0-166">À savoir : chaque module se trouve dans son propre sous-répertoire au sein du sous-répertoire Modules.</span><span class="sxs-lookup"><span data-stu-id="87dc0-166">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="87dc0-167">Le programme d’installation fait alors en sorte que la valeur de la variable d’environnement **PSModulePath** comprenne le chemin du sous-répertoire Common Files\Modules.</span><span class="sxs-lookup"><span data-stu-id="87dc0-167">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="87dc0-168">Installation de plusieurs versions d’un module</span><span class="sxs-lookup"><span data-stu-id="87dc0-168">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="87dc0-169">Pour installer plusieurs versions du même module, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="87dc0-169">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="87dc0-170">Créez un répertoire pour chaque version du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-170">Create a directory for each version of the module.</span></span> <span data-ttu-id="87dc0-171">Ajoutez le numéro de version dans le nom du répertoire.</span><span class="sxs-lookup"><span data-stu-id="87dc0-171">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="87dc0-172">Créez un manifeste de module pour chaque version du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-172">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="87dc0-173">Dans la valeur de la clé **ModuleVersion** qui se trouve dans le manifeste, entrez le numéro de version du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-173">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="87dc0-174">Enregistrez le fichier manifeste (.psd1) dans le répertoire propre à la version du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-174">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="87dc0-175">Ajoutez le chemin du dossier racine du module à la valeur de la variable d’environnement **PSModulePath** (cf. exemples suivants).</span><span class="sxs-lookup"><span data-stu-id="87dc0-175">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="87dc0-176">Pour importer une version particulière du module, l’utilisateur final peut utiliser le paramètre `MinimumVersion` ou le paramètre `RequiredVersion` de la cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="87dc0-176">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="87dc0-177">Par exemple, si le module Fabrikam est disponible dans les versions 8.0 et 9.0, la structure de répertoires du module Fabrikam peut se présenter ainsi :</span><span class="sxs-lookup"><span data-stu-id="87dc0-177">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="87dc0-178">Le programme d’installation ajoute les deux chemins de module à la valeur de la variable d’environnement **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="87dc0-178">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="87dc0-179">À l’issue de cette procédure, le paramètre **ListAvailable** de la cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) récupère les deux modules Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="87dc0-179">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="87dc0-180">Pour importer un module en particulier, utilisez le paramètre `MinimumVersion` ou le paramètre `RequiredVersion` de la cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="87dc0-180">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="87dc0-181">Si les deux modules sont importés dans la même session et qu’ils contiennent des cmdlets portant le même nom, sont effectives dans la session les cmdlets importées en dernier.</span><span class="sxs-lookup"><span data-stu-id="87dc0-181">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="87dc0-182">Gestion des conflits de noms de commandes</span><span class="sxs-lookup"><span data-stu-id="87dc0-182">Handling Command Name Conflicts</span></span>

<span data-ttu-id="87dc0-183">Des conflits de noms de commandes peuvent se produire lorsque les commandes exportées par un module portent le même nom que les commandes de la session de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="87dc0-183">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="87dc0-184">Si une session contient deux commandes du même nom, Windows PowerShell exécute le type de commande prioritaire.</span><span class="sxs-lookup"><span data-stu-id="87dc0-184">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="87dc0-185">Si une session contient deux commandes du même nom et du même type, Windows PowerShell exécute la dernière commande ajoutée à la session.</span><span class="sxs-lookup"><span data-stu-id="87dc0-185">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="87dc0-186">Pour exécuter une commande qui n’est pas exécutée par défaut, les utilisateurs peuvent qualifier le nom de la commande avec celui du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-186">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="87dc0-187">Par exemple, si la session comprend une fonction `Get-Date` et la cmdlet `Get-Date`, Windows PowerShell exécute par défaut la fonction.</span><span class="sxs-lookup"><span data-stu-id="87dc0-187">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="87dc0-188">Pour exécuter la cmdlet, faites précéder la commande du nom du module :</span><span class="sxs-lookup"><span data-stu-id="87dc0-188">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="87dc0-189">Pour éviter les conflits de noms, les auteurs de modules peuvent utiliser la clé **DefaultCommandPrefix** dans le manifeste de module afin de spécifier un préfixe substantif pour toutes les commandes exportées à partir du module.</span><span class="sxs-lookup"><span data-stu-id="87dc0-189">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="87dc0-190">Les utilisateurs peuvent se servir du paramètre **Prefix** de la cmdlet `Import-Module` pour utiliser un autre préfixe.</span><span class="sxs-lookup"><span data-stu-id="87dc0-190">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="87dc0-191">La valeur du paramètre **Prefix** est prioritaire sur la valeur de la clé **DefaultCommandPrefix**.</span><span class="sxs-lookup"><span data-stu-id="87dc0-191">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="87dc0-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87dc0-192">See Also</span></span>

[<span data-ttu-id="87dc0-193">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="87dc0-193">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="87dc0-194">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="87dc0-194">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
