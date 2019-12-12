---
title: Installation d’un module PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367068"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="c2921-102">Installation d’un module PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2921-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="c2921-103">Une fois que vous avez créé votre module PowerShell, vous souhaiterez probablement installer le module sur un système, afin que vous ou d’autres utilisateurs puissent l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="c2921-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="c2921-104">En règle générale, cela consiste à copier les fichiers de module (IE, le fichier. psm1 ou l’assembly binaire, le manifeste de module et tous les autres fichiers associés) sur un répertoire sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c2921-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="c2921-105">Pour un très petit projet, cela peut être aussi simple que la copie et le collage des fichiers avec l’Explorateur Windows sur un ordinateur distant unique. Toutefois, pour les solutions plus grandes, vous souhaiterez peut-être utiliser un processus d’installation plus sophistiqué.</span><span class="sxs-lookup"><span data-stu-id="c2921-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="c2921-106">Quelle que soit la façon dont vous obtenez votre module sur le système, PowerShell peut utiliser un certain nombre de techniques qui permettront aux utilisateurs de trouver et d’utiliser vos modules.</span><span class="sxs-lookup"><span data-stu-id="c2921-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="c2921-107">Par conséquent, le problème principal d’installation consiste à s’assurer que PowerShell sera en mesure de trouver votre module.</span><span class="sxs-lookup"><span data-stu-id="c2921-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="c2921-108">Pour plus d’informations, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="c2921-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="c2921-109">Règles d’installation des modules</span><span class="sxs-lookup"><span data-stu-id="c2921-109">Rules for Installing Modules</span></span>

<span data-ttu-id="c2921-110">Les informations suivantes se rapportent à tous les modules, y compris les modules que vous créez pour votre propre usage, les modules que vous recevez d’autres parties et les modules que vous distribuez à d’autres tiers.</span><span class="sxs-lookup"><span data-stu-id="c2921-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="c2921-111">Installer les modules dans PSModulePath</span><span class="sxs-lookup"><span data-stu-id="c2921-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="c2921-112">Dans la mesure du possible, installez tous les modules dans un chemin d’accès qui est listé dans la variable d’environnement **PSModulePath** ou ajoutez le chemin d’accès du module à la valeur de la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="c2921-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="c2921-113">La variable d’environnement **PSModulePath** ($env :P smodulepath) contient les emplacements des modules Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2921-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="c2921-114">Les applets de commande s’appuient sur la valeur de cette variable d’environnement pour rechercher des modules.</span><span class="sxs-lookup"><span data-stu-id="c2921-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="c2921-115">Par défaut, la valeur de la variable d’environnement **PSModulePath** contient les répertoires du module système et utilisateur suivants, mais vous pouvez ajouter et modifier la valeur.</span><span class="sxs-lookup"><span data-stu-id="c2921-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="c2921-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="c2921-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="c2921-117">Cet emplacement est réservé aux modules fournis avec Windows.</span><span class="sxs-lookup"><span data-stu-id="c2921-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="c2921-118">N’installez pas les modules à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="c2921-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="c2921-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="c2921-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="c2921-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="c2921-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="c2921-121">Pour récupérer la valeur de la variable d’environnement **PSModulePath** , utilisez l’une des commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c2921-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="c2921-122">Pour ajouter un chemin de module à la valeur de la variable d’environnement **PSModulePath** , utilisez le format de commande suivant.</span><span class="sxs-lookup"><span data-stu-id="c2921-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="c2921-123">Ce format utilise la méthode **SetEnvironmentVariable ne contient** de la classe **System. Environment** pour apporter une modification indépendante de la session à la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="c2921-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="c2921-124">Une fois que vous avez ajouté le chemin d’accès à **PSModulePath**, vous devez diffuser un message d’environnement sur la modification.</span><span class="sxs-lookup"><span data-stu-id="c2921-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="c2921-125">La diffusion de la modification permet à d’autres applications, telles que l’interpréteur de commandes, de récupérer la modification.</span><span class="sxs-lookup"><span data-stu-id="c2921-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="c2921-126">Pour diffuser la modification, faire en sorte que le code d’installation de votre produit envoie un message de **WM_SETTINGCHANGE** avec `lParam` défini sur la chaîne « environnement ».</span><span class="sxs-lookup"><span data-stu-id="c2921-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="c2921-127">Veillez à envoyer le message une fois que le code d’installation de votre module a mis à jour **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="c2921-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="c2921-128">Utiliser le nom de répertoire du module correct</span><span class="sxs-lookup"><span data-stu-id="c2921-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="c2921-129">Un module bien formé est un module qui est stocké dans un répertoire portant le même nom que le nom de base d’au moins un fichier dans le répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="c2921-130">Si un module n’est pas bien formé, Windows PowerShell ne le reconnaît pas comme un module.</span><span class="sxs-lookup"><span data-stu-id="c2921-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="c2921-131">Le « nom de base » d’un fichier est le nom sans l’extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="c2921-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="c2921-132">Dans un module bien formé, le nom du répertoire qui contient les fichiers de module doit correspondre au nom de base d’au moins un fichier dans le module.</span><span class="sxs-lookup"><span data-stu-id="c2921-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="c2921-133">Par exemple, dans l’exemple de module Fabrikam, le répertoire qui contient les fichiers de module est nommé « Fabrikam » et au moins un fichier a le nom de base « fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="c2921-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="c2921-134">Dans ce cas, fabrikam. psd1 et fabrikam. dll ont tous les deux le nom de base « fabrikam ».</span><span class="sxs-lookup"><span data-stu-id="c2921-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="c2921-135">Effet d’une installation incorrecte</span><span class="sxs-lookup"><span data-stu-id="c2921-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="c2921-136">Si le module n’est pas bien formé et que son emplacement n’est pas inclus dans la valeur de la variable d’environnement **PSModulePath** , les fonctionnalités de découverte de base de Windows PowerShell, comme ci-dessous, ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="c2921-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="c2921-137">La fonctionnalité de chargement automatique de module ne peut pas importer le module automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c2921-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="c2921-138">Le paramètre `ListAvailable` de l’applet de commande [obtenir-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) ne trouve pas le module.</span><span class="sxs-lookup"><span data-stu-id="c2921-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="c2921-139">L’applet [de commande Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ne trouve pas le module.</span><span class="sxs-lookup"><span data-stu-id="c2921-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="c2921-140">Pour importer le module, vous devez fournir le chemin d’accès complet au fichier de module racine ou au fichier manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="c2921-141">Les fonctionnalités supplémentaires, telles que les suivantes, ne fonctionnent pas, sauf si le module est importé dans la session.</span><span class="sxs-lookup"><span data-stu-id="c2921-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="c2921-142">Dans les modules bien formés de la variable d’environnement **PSModulePath** , ces fonctionnalités fonctionnent même si le module n’est pas importé dans la session.</span><span class="sxs-lookup"><span data-stu-id="c2921-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="c2921-143">L’applet de [commande obtenir-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) ne peut pas trouver de commandes dans le module.</span><span class="sxs-lookup"><span data-stu-id="c2921-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="c2921-144">Les applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) ne peuvent pas mettre à jour ou enregistrer l’aide du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="c2921-145">L’applet de [commande show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) ne peut pas trouver et afficher les commandes du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="c2921-146">Les commandes du module sont absentes de la fenêtre `Show-Command` dans Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="c2921-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="c2921-147">Emplacement d’installation des modules</span><span class="sxs-lookup"><span data-stu-id="c2921-147">Where to Install Modules</span></span>

<span data-ttu-id="c2921-148">Cette section explique où dans le système de fichiers pour installer les modules Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2921-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="c2921-149">L’emplacement dépend de la façon dont le module est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c2921-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="c2921-150">Installation de modules pour un utilisateur spécifique</span><span class="sxs-lookup"><span data-stu-id="c2921-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="c2921-151">Si vous créez votre propre module ou si vous recevez un module d’un autre tiers, tel qu’un site Web de la communauté Windows PowerShell, et que vous souhaitez que le module soit disponible uniquement pour votre compte d’utilisateur, installez le module dans votre répertoire de modules spécifiques à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c2921-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="c2921-152">Le répertoire modules spécifiques à l’utilisateur est ajouté à la valeur de la variable d’environnement **PSModulePath** par défaut.</span><span class="sxs-lookup"><span data-stu-id="c2921-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="c2921-153">Installation de modules pour tous les utilisateurs dans Program Files</span><span class="sxs-lookup"><span data-stu-id="c2921-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="c2921-154">Si vous souhaitez qu’un module soit disponible pour tous les comptes d’utilisateur sur l’ordinateur, installez le module à l’emplacement Program Files.</span><span class="sxs-lookup"><span data-stu-id="c2921-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="c2921-155">L’emplacement des fichiers programme est ajouté à la valeur de la variable d’environnement PSModulePath par défaut dans Windows PowerShell 4,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c2921-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="c2921-156">Pour les versions antérieures de Windows PowerShell, vous pouvez créer manuellement l’emplacement des fichiers programme ((%ProgramFiles%\WindowsPowerShell\Modules) et ajouter ce chemin d’accès à votre variable d’environnement PSModulePath comme décrit ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="c2921-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="c2921-157">Installation de modules dans un répertoire de produit</span><span class="sxs-lookup"><span data-stu-id="c2921-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="c2921-158">Si vous distribuez le module à d’autres tiers, utilisez l’emplacement par défaut des fichiers programme décrit ci-dessus, ou créez votre propre sous-répertoire spécifique à la société ou au produit du répertoire% ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="c2921-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="c2921-159">Par exemple, Fabrikam technologies, une société fictive, expédie un module Windows PowerShell pour son produit Fabrikam Manager.</span><span class="sxs-lookup"><span data-stu-id="c2921-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="c2921-160">Le programme d’installation de leur module crée un sous-répertoire Modules dans le sous-répertoire du produit de Fabrikam Manager.</span><span class="sxs-lookup"><span data-stu-id="c2921-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="c2921-161">Pour activer les fonctionnalités de détection des modules Windows PowerShell afin de rechercher le module Fabrikam, le programme d’installation du module Fabrikam ajoute l’emplacement du module à la valeur de la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="c2921-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="c2921-162">Installation des modules dans le répertoire des fichiers communs</span><span class="sxs-lookup"><span data-stu-id="c2921-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="c2921-163">Si un module est utilisé par plusieurs composants d’un produit ou par plusieurs versions d’un produit, installez le module dans un sous-répertoire spécifique au module du sous-répertoire%ProgramFiles%\Common Files\Modules.</span><span class="sxs-lookup"><span data-stu-id="c2921-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="c2921-164">Dans l’exemple suivant, le module Fabrikam est installé dans un sous-répertoire Fabrikam du sous-répertoire `%ProgramFiles%\Common Files\Modules`.</span><span class="sxs-lookup"><span data-stu-id="c2921-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="c2921-165">Notez que chaque module réside dans son propre sous-répertoire dans le sous-répertoire Modules.</span><span class="sxs-lookup"><span data-stu-id="c2921-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="c2921-166">Ensuite, le programme d’installation vérifie que la valeur de la variable d’environnement **PSModulePath** comprend le chemin d’accès du sous-répertoire des modules de fichiers communs.</span><span class="sxs-lookup"><span data-stu-id="c2921-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="c2921-167">Installation de plusieurs versions d’un module</span><span class="sxs-lookup"><span data-stu-id="c2921-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="c2921-168">Pour installer plusieurs versions du même module, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="c2921-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="c2921-169">Créez un répertoire pour chaque version du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="c2921-170">Incluez le numéro de version dans le nom du répertoire.</span><span class="sxs-lookup"><span data-stu-id="c2921-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="c2921-171">Créez un manifeste de module pour chaque version du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="c2921-172">Dans la valeur de la clé **ModuleVersion** dans le manifeste, entrez le numéro de version du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="c2921-173">Enregistrez le fichier manifeste (. psd1) dans le répertoire spécifique à la version du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="c2921-174">Ajoutez le chemin d’accès au dossier racine du module à la valeur de la variable d’environnement **PSModulePath** , comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="c2921-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="c2921-175">Pour importer une version particulière du module, l’utilisateur final peut utiliser les paramètres `MinimumVersion` ou `RequiredVersion` de l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="c2921-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="c2921-176">Par exemple, si le module Fabrikam est disponible dans les versions 8,0 et 9,0, la structure de répertoires du module Fabrikam peut ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="c2921-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="c2921-177">Le programme d’installation ajoute les deux chemins d’accès au module à la valeur de la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="c2921-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="c2921-178">Une fois ces étapes terminées, le paramètre **listAvailable** de l’applet de commande [obtenir-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) obtient les deux modules fabrikam.</span><span class="sxs-lookup"><span data-stu-id="c2921-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="c2921-179">Pour importer un module particulier, utilisez les paramètres `MinimumVersion` ou `RequiredVersion` de l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="c2921-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="c2921-180">Si les deux modules sont importés dans la même session et que les modules contiennent des applets de commande portant le même nom, les applets de commande importées en dernier sont effectives dans la session.</span><span class="sxs-lookup"><span data-stu-id="c2921-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="c2921-181">Gestion des conflits de noms de commande</span><span class="sxs-lookup"><span data-stu-id="c2921-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="c2921-182">Les conflits de noms de commande peuvent se produire lorsque les commandes exportées par un module ont le même nom que les commandes dans la session de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c2921-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="c2921-183">Quand une session contient deux commandes qui portent le même nom, Windows PowerShell exécute le type de commande qui est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="c2921-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="c2921-184">Quand une session contient deux commandes qui ont le même nom et le même type, Windows PowerShell exécute la commande qui a été ajoutée à la session la plus récente.</span><span class="sxs-lookup"><span data-stu-id="c2921-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="c2921-185">Pour exécuter une commande qui n’est pas exécutée par défaut, les utilisateurs peuvent qualifier le nom de la commande avec le nom du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="c2921-186">Par exemple, si la session contient une fonction `Get-Date` et l’applet de commande `Get-Date`, Windows PowerShell exécute la fonction par défaut.</span><span class="sxs-lookup"><span data-stu-id="c2921-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="c2921-187">Pour exécuter l’applet de commande, faites précéder la commande du nom du module, par exemple :</span><span class="sxs-lookup"><span data-stu-id="c2921-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="c2921-188">Pour éviter les conflits de noms, les auteurs de modules peuvent utiliser la clé **DefaultCommandPrefix** dans le manifeste de module pour spécifier un préfixe substantif pour toutes les commandes exportées à partir du module.</span><span class="sxs-lookup"><span data-stu-id="c2921-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="c2921-189">Les utilisateurs peuvent utiliser le paramètre **prefix** de l’applet de commande `Import-Module` pour utiliser un autre préfixe.</span><span class="sxs-lookup"><span data-stu-id="c2921-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="c2921-190">La valeur du paramètre **prefix** est prioritaire sur la valeur de la clé **DefaultCommandPrefix** .</span><span class="sxs-lookup"><span data-stu-id="c2921-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2921-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2921-191">See Also</span></span>

[<span data-ttu-id="c2921-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="c2921-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="c2921-193">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2921-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
