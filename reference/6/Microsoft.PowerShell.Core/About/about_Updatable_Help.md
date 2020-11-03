---
description: Décrit le système d’aide pouvant être mis à jour dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: 9f946fa1ef0f11efc3e0d964cf9ea8a55e01ff8f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206826"
---
# <a name="about-updatable-help"></a><span data-ttu-id="fa300-104">À propos de l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="fa300-104">About Updatable Help</span></span>

## <a name="short-description"></a><span data-ttu-id="fa300-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="fa300-105">Short description</span></span>
<span data-ttu-id="fa300-106">Décrit le système d’aide pouvant être mis à jour dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa300-106">Describes the updatable help system in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="fa300-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="fa300-107">Long description</span></span>

<span data-ttu-id="fa300-108">PowerShell offre différentes façons d’accéder aux rubriques d’aide les plus récentes pour les applets de commande et les concepts PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa300-108">PowerShell provides several different ways to access the most up-to-date help topics for PowerShell cmdlets and concepts.</span></span>

<span data-ttu-id="fa300-109">Le système d’aide actualisable, introduit dans PowerShell 3,0, est conçu pour vous assurer que vous disposez toujours des dernières rubriques d’aide sur votre ordinateur local afin de pouvoir les lire sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="fa300-109">The Updatable Help system, introduced in PowerShell 3.0, is designed to assure that you always have the newest help topics on your local computer so that you can read them at the command line.</span></span> <span data-ttu-id="fa300-110">Il facilite le téléchargement et l’installation des fichiers d’aide et leur mise à jour chaque fois que des fichiers d’aide plus récents sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="fa300-110">It makes it easy to download and install help files and to update them whenever newer help files become available.</span></span>

<span data-ttu-id="fa300-111">Pour fournir une aide mise à jour pour plusieurs ordinateurs dans une entreprise et pour les ordinateurs qui n’ont pas accès à Internet, l’aide actualisable vous permet de télécharger les fichiers d’aide dans un répertoire de système de fichiers ou un partage de fichiers, puis d’installer les fichiers d’aide à partir du partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="fa300-111">To provide updated help for multiple computers in an enterprise and for computers that do not have access to the internet, Updatable Help lets you download help files to a filesystem directory or file share, and then install the help files from the file share.</span></span>

<span data-ttu-id="fa300-112">Dans PowerShell 4,0, la propriété **HelpInfoUri** est conservée sur la communication à distance Windows PowerShell, ce qui permet `Save-Help` à de fonctionner pour les modules qui sont installés sur un ordinateur distant, mais qui ne sont pas nécessairement installés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fa300-112">In PowerShell 4.0, the **HelpInfoUri** property is preserved over Windows PowerShell remoting, which allows `Save-Help` to work for modules that are installed on a remote computer, but are not necessarily installed on the local computer.</span></span> <span data-ttu-id="fa300-113">Vous pouvez enregistrer un objet **PSModuleInfo** sur un disque ou sur un support amovible (tel qu’un lecteur USB) en exécutant `Export-Clixml` sur un ordinateur qui n’a pas accès à Internet, en important l’objet **PSModuleInfo** sur un ordinateur qui a accès à Internet, puis en cours `Save-Help` d’exécution sur l’objet **PSModuleInfo** .</span><span class="sxs-lookup"><span data-stu-id="fa300-113">You can save a **PSModuleInfo** object to disk or removable media (such as a USB drive) by running `Export-Clixml` on a computer that does not have internet access, importing the **PSModuleInfo** object on a computer that does have internet access, and then running `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="fa300-114">L’aide enregistrée peut être copiée sur l’ordinateur distant, déconnecté à l’aide d’un support amovible, puis installé en exécutant `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-114">The saved help can be copied to the remote, disconnected computer by using removable media, and then installed by running `Update-Help`.</span></span> <span data-ttu-id="fa300-115">Ces améliorations de la `Save-Help` fonctionnalité vous permettent d’installer l’aide sur les ordinateurs qui ne disposent d’aucun accès réseau.</span><span class="sxs-lookup"><span data-stu-id="fa300-115">These improvements in `Save-Help` functionality let you install help on computers that are without any kind of network access.</span></span> <span data-ttu-id="fa300-116">Pour obtenir un exemple d’utilisation de la nouvelle `Save-Help` fonctionnalité, consultez [Comment mettre à jour l’aide d’un partage de fichiers](#how-to-update-help-from-a-file-share) dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fa300-116">For an example of how to use the new `Save-Help` functionality, see [How to update help from a file share](#how-to-update-help-from-a-file-share) in this topic.</span></span>

<span data-ttu-id="fa300-117">L’aide actualisable prend également en charge l’accès en ligne aux dernières rubriques d’aide et à l’aide de base pour les applets de commande, même lorsqu’il n’y a aucun fichier d’aide sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fa300-117">Updatable Help also supports online access to the newest help topics and basic help for cmdlets, even when there are no help files on the computer.</span></span>

<span data-ttu-id="fa300-118">PowerShell 3,0 n’est pas fourni avec les fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="fa300-118">PowerShell 3.0 does not come with Help files.</span></span> <span data-ttu-id="fa300-119">Vous pouvez utiliser la fonctionnalité d’aide actualisable pour installer les fichiers d’aide de toutes les commandes incluses par défaut dans PowerShell et pour tous les modules Windows.</span><span class="sxs-lookup"><span data-stu-id="fa300-119">You can use the Updatable Help feature to install the help files for all of the commands that are included by default in PowerShell and for all Windows modules.</span></span>

## <a name="updatable-help-cmdlets"></a><span data-ttu-id="fa300-120">Applets de commande d’aide actualisables</span><span class="sxs-lookup"><span data-stu-id="fa300-120">Updatable help cmdlets</span></span>

- <span data-ttu-id="fa300-121">`Update-Help`: Télécharge les fichiers d’aide les plus récents à partir d’Internet ou d’un partage de fichiers, puis les installe sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fa300-121">`Update-Help`: Downloads the newest help files from the internet or a file share, and installs them on the local computer.</span></span>

- <span data-ttu-id="fa300-122">`Save-Help`: Télécharge les fichiers d’aide les plus récents à partir d’Internet et les enregistre dans un répertoire de système de fichiers ou un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="fa300-122">`Save-Help`: Downloads the newest help files from the internet and saves them in a filesystem directory or file share.</span></span> <span data-ttu-id="fa300-123">Pour installer les fichiers d’aide sur les ordinateurs, utilisez `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-123">To install the help files on computers, use `Update-Help`.</span></span>

- <span data-ttu-id="fa300-124">`Get-Help`: Affiche les rubriques d’aide sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="fa300-124">`Get-Help`: Displays help topics at the command line.</span></span> <span data-ttu-id="fa300-125">Obtient de l’aide à partir des fichiers d’aide sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fa300-125">Gets help from the help files on the computer.</span></span> <span data-ttu-id="fa300-126">Affiche l’aide générée automatiquement pour les applets de commande et les fonctions qui n’ont pas de fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="fa300-126">Displays auto-generated help for cmdlets and functions that do not have help files.</span></span> <span data-ttu-id="fa300-127">Ouvre les rubriques d’aide en ligne pour les applets de commande, les fonctions, les scripts et les flux de travail dans votre navigateur Internet par défaut.</span><span class="sxs-lookup"><span data-stu-id="fa300-127">Opens online help topics for cmdlets, functions, scripts, and workflows in your default internet browser.</span></span>

## <a name="auto-generated-help-help-without-help-files"></a><span data-ttu-id="fa300-128">Aide générée automatiquement : aide sans fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="fa300-128">Auto-generated help: help without help files</span></span>

<span data-ttu-id="fa300-129">Si vous ne disposez pas du fichier d’aide d’une applet de commande, d’une fonction ou d’un flux de travail sur l’ordinateur, l’applet de commande `Get-Help` affiche l’aide générée automatiquement et vous invite à télécharger les fichiers d’aide ou à les lire en ligne.</span><span class="sxs-lookup"><span data-stu-id="fa300-129">If you do not have the help file for a cmdlet, function, or workflow on the computer, the `Get-Help` cmdlet displays auto-generated help and prompts you to download the help files or read them online.</span></span>

<span data-ttu-id="fa300-130">L’aide générée automatiquement comprend la syntaxe et les alias, ainsi que des remarques qui expliquent comment utiliser les applets de commande de l’aide actualisable et accéder aux rubriques d’aide en ligne.</span><span class="sxs-lookup"><span data-stu-id="fa300-130">Auto-generated help includes syntax and aliases, and remarks that explain how to use the Updatable Help cmdlets and to access the online help topics.</span></span>

<span data-ttu-id="fa300-131">Par exemple, la commande suivante obtient l’aide de base pour l’applet de commande `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="fa300-131">For example, the following command gets basic help for the `Get-Culture` cmdlet.</span></span> <span data-ttu-id="fa300-132">La sortie indique l' `Get-Help` affichage lorsqu’il n’y a aucun fichier d’aide sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fa300-132">The output shows the `Get-Help` display when there are no help files on the computer.</span></span>

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a><span data-ttu-id="fa300-133">Fichiers d’aide pour les modules</span><span class="sxs-lookup"><span data-stu-id="fa300-133">Help files for modules</span></span>

<span data-ttu-id="fa300-134">La plus petite unité d’aide actualisable est l’aide d’un module.</span><span class="sxs-lookup"><span data-stu-id="fa300-134">The smallest unit of Updatable Help is help for a module.</span></span> <span data-ttu-id="fa300-135">L’aide du module comprend de l’aide sur toutes les applets de commande, fonctions, flux de travail, fournisseurs, scripts et concepts d’un module.</span><span class="sxs-lookup"><span data-stu-id="fa300-135">Module help includes help for all of the cmdlets, functions, workflows, providers, scripts, and concepts in a module.</span></span> <span data-ttu-id="fa300-136">Vous pouvez mettre à jour l’aide de tous les modules installés sur l’ordinateur, même s’ils ne sont pas importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fa300-136">You can update help for all modules that are installed on the computer, even if they are not imported into the current session.</span></span>

<span data-ttu-id="fa300-137">Vous pouvez mettre à jour l’aide pour l’ensemble du module, mais vous ne pouvez pas mettre à jour l’aide pour les applets de commande individuelles.</span><span class="sxs-lookup"><span data-stu-id="fa300-137">You can update help for the entire module, but you cannot update help for individual cmdlets.</span></span>

<span data-ttu-id="fa300-138">Pour rechercher le module qui contient une applet de commande particulière, utilisez le format de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="fa300-138">To find the module that contains a particular cmdlet, use the following command format:</span></span>

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

<span data-ttu-id="fa300-139">Par exemple, pour rechercher le module qui contient l' `Set-ExecutionPolicy` applet de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="fa300-139">For example, to find the module that contains the `Set-ExecutionPolicy` cmdlet, type:</span></span>

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

<span data-ttu-id="fa300-140">Pour mettre à jour l’aide d’un module particulier, tapez :</span><span class="sxs-lookup"><span data-stu-id="fa300-140">To update help for a particular module, type:</span></span>

```powershell
Update-Help -Module <ModuleName>
```

<span data-ttu-id="fa300-141">Par exemple, pour mettre à jour l’aide pour le module qui contient l’applet de commande Set-ExecutionPolicy, tapez :</span><span class="sxs-lookup"><span data-stu-id="fa300-141">For example, to update help for the module that contains the Set-ExecutionPolicy cmdlet, type:</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a><span data-ttu-id="fa300-142">Autorisations pour l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="fa300-142">Permissions for updatable help</span></span>

<span data-ttu-id="fa300-143">Pour mettre à jour l’aide pour les modules de l’annuaire `$pshome/Modules` , vous devez être membre du groupe Administrateurs sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fa300-143">To update help for the modules in the directory `$pshome/Modules`, you must be member of the Administrators group on the computer.</span></span>

<span data-ttu-id="fa300-144">Si vous n’êtes pas membre du groupe administrateurs, vous ne pouvez pas mettre à jour l’aide pour ces modules. Toutefois, si vous avez accès à Internet, vous pouvez afficher l’aide en ligne.</span><span class="sxs-lookup"><span data-stu-id="fa300-144">If you are not a member of the Administrators group, you cannot update help for these modules; but if you have internet access, you can view help online.</span></span>

<span data-ttu-id="fa300-145">La mise à jour de l’aide pour les modules dans le `$home/Documents/PowerShell/Modules` ou les modules dans d’autres sous-répertoires du `$home` Répertoire ne nécessite pas d’autorisations spéciales.</span><span class="sxs-lookup"><span data-stu-id="fa300-145">Updating help for modules in the directory `$home/Documents/PowerShell/Modules` or modules in other subdirectories of the `$home` directory does not require special permissions.</span></span>

<span data-ttu-id="fa300-146">Les `Update-Help` applets de commande et `Save-Help` ont un paramètre **UseDefaultCredentials** qui fournit les informations d’identification explicites de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="fa300-146">The `Update-Help` and `Save-Help` cmdlets have a **UseDefaultCredentials** parameter that provides the explicit credentials of the current user.</span></span> <span data-ttu-id="fa300-147">Ce paramètre est conçu pour accéder à des emplacements Internet sécurisés.</span><span class="sxs-lookup"><span data-stu-id="fa300-147">This parameter is designed for accessing secure internet locations.</span></span>

<span data-ttu-id="fa300-148">Les `Update-Help` `Save-Help` applets de commande et possèdent également un paramètre **Credential** qui vous permet d’exécuter la commande sur un ordinateur distant et d’accéder à un partage de fichiers sur un troisième ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fa300-148">The `Update-Help` and `Save-Help` cmdlets also have a **Credential** parameter that allows you to run the command on a remote computer and access a file share on a third computer.</span></span> <span data-ttu-id="fa300-149">Le paramètre **Credential** est valide uniquement lorsque vous utilisez les paramètres SourcePath ou **LiteralPath** de `Update-Help` et les paramètres **DestinationPath** ou **LiteralPath** de `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-149">The **Credential** parameter is valid only when you use the SourcePath or **LiteralPath** parameters of `Update-Help` and the **DestinationPath** or **LiteralPath** parameters of `Save-Help`.</span></span>

## <a name="how-to-install-and-update-help-files"></a><span data-ttu-id="fa300-150">Procédure d’installation et de mise à jour des fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="fa300-150">How to install and update help files</span></span>

<span data-ttu-id="fa300-151">Pour télécharger et installer les fichiers d’aide pour la première fois, ou pour mettre à jour les fichiers d’aide sur votre ordinateur, utilisez l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-151">To download and install help files for the first time, or to update the help files on your computer, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="fa300-152">L' `Update-Help` applet de commande effectue tout le travail pour vous, y compris les tâches suivantes.</span><span class="sxs-lookup"><span data-stu-id="fa300-152">The `Update-Help` cmdlet does all of the hard work for you, including the following tasks.</span></span>

- <span data-ttu-id="fa300-153">Détermine les modules qui prennent en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="fa300-153">Determines which modules support Updatable Help.</span></span>
- <span data-ttu-id="fa300-154">Recherche l’emplacement Internet où chaque module stocke ses fichiers d’aide pouvant être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="fa300-154">Finds the internet location where each module stores its Updatable Help files.</span></span>
- <span data-ttu-id="fa300-155">Compare les fichiers d’aide pour chaque module de votre ordinateur avec les derniers fichiers d’aide disponibles pour chaque module.</span><span class="sxs-lookup"><span data-stu-id="fa300-155">Compares the help files for each module on your computer to the newest help files that are available for each module.</span></span>
- <span data-ttu-id="fa300-156">Télécharge les nouveaux fichiers à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="fa300-156">Downloads the new files from the internet.</span></span>
- <span data-ttu-id="fa300-157">Désencapsule le package du fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="fa300-157">Unwraps the help file package.</span></span>
- <span data-ttu-id="fa300-158">Vérifie que les fichiers sont des fichiers d’aide valides.</span><span class="sxs-lookup"><span data-stu-id="fa300-158">Verifies that the files are valid help files.</span></span>
- <span data-ttu-id="fa300-159">Installe les fichiers d’aide dans le sous-répertoire spécifique à la langue du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="fa300-159">Installs the help files in the language-specific subdirectory of the module directory.</span></span>

<span data-ttu-id="fa300-160">Pour accéder aux nouvelles rubriques d’aide, utilisez l’applet de commande `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-160">To access the new help topics, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="fa300-161">Vous n’avez pas besoin de redémarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa300-161">You do not need to restart PowerShell.</span></span>

<span data-ttu-id="fa300-162">Pour installer ou mettre à jour l’aide de tous les modules sur l’ordinateur qui prend en charge l’aide actualisable, tapez :</span><span class="sxs-lookup"><span data-stu-id="fa300-162">To install or update help for all modules on the computer that supports Updatable Help, type:</span></span>

```powershell
Update-Help
```

<span data-ttu-id="fa300-163">Pour mettre à jour l’aide pour des modules particuliers, ajoutez le paramètre **module** de `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-163">To update help for particular modules, add the **Module** parameter of `Update-Help`.</span></span> <span data-ttu-id="fa300-164">Les caractères génériques sont autorisés dans le nom du module.</span><span class="sxs-lookup"><span data-stu-id="fa300-164">Wildcard characters are permitted in the module name.</span></span>

<span data-ttu-id="fa300-165">Par exemple, pour mettre à jour l’aide du module ServerManager, tapez :</span><span class="sxs-lookup"><span data-stu-id="fa300-165">For example, to update help for the ServerManager module, type:</span></span>

```powershell
Update-Help -Module ServerManager
```

<span data-ttu-id="fa300-166">Sans paramètres, `Update-Help` met à jour l’aide de tous les modules de la session et de tous les modules installés qui prennent en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="fa300-166">Without parameters, `Update-Help` updates help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="fa300-167">Pour être inclus, les modules doivent être installés dans les répertoires qui sont répertoriés dans la valeur de la variable d’environnement PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="fa300-167">To be included, modules must be installed in directories that are listed in the value of the PSModulePath environment variable.</span></span> <span data-ttu-id="fa300-168">Il s’agit également de modules qui sont retournés par une commande « obtenir-Help-ListAvailable ».</span><span class="sxs-lookup"><span data-stu-id="fa300-168">These are also modules that are returned by a "Get-Help -ListAvailable" command.</span></span>

<span data-ttu-id="fa300-169">Si la valeur du paramètre **module** est `*` (All), `Update-Help` tente de mettre à jour l’aide de tous les modules installés, y compris les modules qui ne prennent pas en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="fa300-169">If the value of the **Module** parameter is `*` (all), `Update-Help` attempts to update help for all installed modules, including modules that do not support Updatable Help.</span></span> <span data-ttu-id="fa300-170">Cette commande génère généralement de nombreuses Erreurs lorsque l’applet de commande rencontre des modules qui ne prennent pas en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="fa300-170">This command typically generates many errors as the cmdlet encounters modules that do not support Updatable Help.</span></span>

## <a name="how-to-update-help-from-a-file-share"></a><span data-ttu-id="fa300-171">Comment mettre à jour l’aide d’un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="fa300-171">How to update help from a file share</span></span>

<span data-ttu-id="fa300-172">Pour prendre en charge les ordinateurs qui ne sont pas connectés à Internet, ou pour contrôler ou simplifier la mise à jour de l’aide dans une entreprise, utilisez l’applet de commande `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-172">To support computers that are not connected to the internet, or to control or streamline help updating in an enterprise, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="fa300-173">L' `Save-Help` applet de commande télécharge les fichiers d’aide à partir d’Internet et les enregistre dans un répertoire de système de fichiers que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="fa300-173">The `Save-Help` cmdlet downloads help files from the internet and saves them in a filesystem directory that you specify.</span></span>

<span data-ttu-id="fa300-174">`Save-Help` compare les fichiers d’aide dans le répertoire spécifié aux fichiers d’aide les plus récents qui sont disponibles pour chaque module.</span><span class="sxs-lookup"><span data-stu-id="fa300-174">`Save-Help` compares the help files in the specified directory to the newest help files that are available for each module.</span></span> <span data-ttu-id="fa300-175">Si le répertoire n’a pas de fichiers d’aide ou si des fichiers d’aide plus récents sont disponibles pour le module, l’applet de commande `Save-Help` télécharge les nouveaux fichiers à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="fa300-175">If the directory has no help files or newer help files are available for the module, the `Save-Help` cmdlet downloads the new files from the internet.</span></span> <span data-ttu-id="fa300-176">Toutefois, il ne désencapsule pas ou n’installe pas les fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="fa300-176">However, it does not unwrap or install the help files.</span></span>

<span data-ttu-id="fa300-177">Pour installer ou mettre à jour les fichiers d’aide sur un ordinateur à partir de fichiers d’aide enregistrés dans un répertoire FileSystem, utilisez le paramètre **SourcePath** de l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-177">To install or update the help files on a computer from help files that were saved to a filesystem directory, use the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="fa300-178">L' `Update-Help` applet de commande identifie les fichiers d’aide les plus récents, les désencapsule et les valide et les installe dans les sous-répertoires spécifiques au langage des répertoires du module.</span><span class="sxs-lookup"><span data-stu-id="fa300-178">The `Update-Help` cmdlet identifies the newest help files, unwraps and validates them, and installs them in the language-specific subdirectories of the module directories.</span></span>

<span data-ttu-id="fa300-179">Par exemple, pour enregistrer l’aide de tous les modules installés dans le `\\Server\Share` répertoire, tapez :</span><span class="sxs-lookup"><span data-stu-id="fa300-179">For example, to save help for all installed modules to the `\\Server\Share` directory, type:</span></span>

```powershell
Save-Help -DestinationPath \\Server\Share
```

<span data-ttu-id="fa300-180">Ensuite, pour mettre à jour l’aide à partir de l' `\\Server\Share` annuaire, tapez :</span><span class="sxs-lookup"><span data-stu-id="fa300-180">Then, to update help from the `\\Server\Share` directory, type:</span></span>

```powershell
Update-Help -SourcePath \\Server\Share
```

<span data-ttu-id="fa300-181">Les exemples suivants illustrent l’utilisation de `Save-Help` pour enregistrer l’aide des modules qui ne sont pas installés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fa300-181">The following examples show the use of `Save-Help` to save help for modules that are not installed on the local computer.</span></span> <span data-ttu-id="fa300-182">Dans cet exemple, l’administrateur s’exécute `Save-Help` pour enregistrer l’aide du module dhcpserver à partir d’un ordinateur client connecté à Internet, sans installer le module dhcpserver ou le rôle serveur DHCP sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fa300-182">In this example, the administrator runs `Save-Help` to save the help for the DhcpServer module from an internet-connected client computer, without installing the DhcpServer module or DHCP Server role on the local computer.</span></span>

<span data-ttu-id="fa300-183">Option 1 : exécutez `Invoke-Command` pour obtenir l’objet **PSModuleInfo** pour le module distant, enregistrez-le dans une variable `$m` ,, puis exécutez `Save-Help` sur l’objet **PSModuleInfo** en spécifiant la variable `$m` comme nom de module.</span><span class="sxs-lookup"><span data-stu-id="fa300-183">Option 1: Run `Invoke-Command` to get the **PSModuleInfo** object for the remote module, save it in a variable, `$m`, and then run `Save-Help` on the **PSModuleInfo** object by specifying the variable `$m` as the module name.</span></span>

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="fa300-184">Option 2 : Ouvrez une session PSSession ciblée sur l’ordinateur qui exécute le module de serveur DHCP, pour obtenir l’objet **PSModuleInfo** pour le module, enregistrez-le dans une variable `$m` , puis exécutez `Save-Help` sur l’objet qui est enregistré dans la `$m` variable.</span><span class="sxs-lookup"><span data-stu-id="fa300-184">Option 2: Open a PSSession targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="fa300-185">Option 3 : Ouvrez une session CIM, ciblée sur l’ordinateur qui exécute le module de serveur DHCP, pour obtenir l’objet **PSModuleInfo** pour le module, enregistrez-la dans une variable `$m` , puis exécutez `Save-Help` sur l’objet qui est enregistré dans la `$m` variable.</span><span class="sxs-lookup"><span data-stu-id="fa300-185">Option 3: Open a CIM session, targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="fa300-186">Dans l’exemple suivant, l’administrateur installe l’aide pour le module serveur DHCP sur un ordinateur qui ne dispose pas d’un accès réseau.</span><span class="sxs-lookup"><span data-stu-id="fa300-186">In the following example, the administrator installs help for the DHCP Server module on a computer that does not have network access.</span></span>

<span data-ttu-id="fa300-187">Tout d’abord, exécutez `Export-Clixml` pour exporter l’objet **PSModuleInfo** dans un dossier partagé ou sur un support amovible.</span><span class="sxs-lookup"><span data-stu-id="fa300-187">First, run `Export-Clixml` to export the **PSModuleInfo** object to a shared folder or to removable media.</span></span>

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

<span data-ttu-id="fa300-188">Ensuite, transférez le support amovible vers un ordinateur qui a accès à Internet, puis importez l’objet **PSModuleInfo** avec `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="fa300-188">Next, transport the removable media to a computer that has internet access, and then import the **PSModuleInfo** object with `Import-Clixml`.</span></span> <span data-ttu-id="fa300-189">Exécutez `Save-Help` pour enregistrer l’aide de l’objet **PSModuleInfo** du module DhcpServer importé.</span><span class="sxs-lookup"><span data-stu-id="fa300-189">Run `Save-Help` to save the Help for the imported DhcpServer module **PSModuleInfo** object.</span></span>

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="fa300-190">Enfin, transférez le support amovible sur l’ordinateur qui ne dispose pas d’un accès réseau, puis installez l’aide en exécutant `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-190">Finally, transport the removable media back to the computer that does not have network access, and then install the help by running `Update-Help`.</span></span>

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="fa300-191">Sans paramètres, `Save-Help` télécharge l’aide pour tous les modules de la session et pour tous les modules installés qui prennent en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="fa300-191">Without parameters, `Save-Help` downloads help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="fa300-192">Pour être inclus, les modules doivent être installés dans des répertoires qui sont répertoriés dans la valeur de la `$env:PSModulePath` variable d’environnement, sur l’ordinateur local ou sur un ordinateur distant pour lequel vous souhaitez enregistrer l’aide.</span><span class="sxs-lookup"><span data-stu-id="fa300-192">To be included, modules must be installed in directories that are listed in the value of the `$env:PSModulePath` environment variable, on either the local computer or on a remote computer for which you want to save help.</span></span> <span data-ttu-id="fa300-193">Il s’agit également de modules qui sont retournés par l’exécution d’une `Get-Help -ListAvailable` commande.</span><span class="sxs-lookup"><span data-stu-id="fa300-193">These are also modules that are returned by running a `Get-Help -ListAvailable` command.</span></span>

## <a name="how-to-update-help-files-in-different-languages"></a><span data-ttu-id="fa300-194">Comment mettre à jour les fichiers d’aide dans différentes langues</span><span class="sxs-lookup"><span data-stu-id="fa300-194">How to update help files in different languages</span></span>

<span data-ttu-id="fa300-195">Par défaut, les `Update-Help` applets de commande et `Save-Help` téléchargent l’aide dans la culture et la langue de l’interface utilisateur définies pour Windows sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="fa300-195">By default, the `Update-Help` and `Save-Help` cmdlets download help in the UI culture and language that is set for Windows on the local computer.</span></span> <span data-ttu-id="fa300-196">Si les fichiers d’aide pour les modules spécifiés ne sont pas disponibles dans la culture d’interface utilisateur locale, `Update-Help` et `Save-Help` utilisent les règles de secours de la langue Windows pour rechercher le meilleur langage pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fa300-196">If help files for the specified modules are not available in the local UI culture, `Update-Help` and `Save-Help` use the Windows language fallback rules to find the best supported language.</span></span>

<span data-ttu-id="fa300-197">Toutefois, vous pouvez utiliser les paramètres **UICulture** des `Update-Help` applets de commande et `Save-Help` pour télécharger et installer les fichiers d’aide dans toutes les cultures d’interface utilisateur dans lesquelles ils sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="fa300-197">However, you can use the **UICulture** parameters of the `Update-Help` and `Save-Help` cmdlets to download and install help files in any UI cultures in which they are available.</span></span>

<span data-ttu-id="fa300-198">Par exemple, pour enregistrer les fichiers d’aide les plus récents pour tous les modules de la session en japonais (ja-JP) et français (fr-FR), tapez :</span><span class="sxs-lookup"><span data-stu-id="fa300-198">For example, to save the newest help files for all modules on the session in Japanese (Ja-jp) and French (fr-FR), type:</span></span>

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

<span data-ttu-id="fa300-199">Si les fichiers d’aide pour les modules ne sont pas disponibles dans les langues que vous avez spécifiées, les `Update-Help` applets de commande et `Save-Help` retournent un message d’erreur qui répertorie les langues dans lesquelles l’aide pour chaque module est disponible pour vous permettre de choisir celle qui répond le mieux à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="fa300-199">If help files for the modules are not available in the languages that you specified, the `Update-Help` and `Save-Help` cmdlets return an error message that lists the languages in which help for each module is available so you can choose the alternative that best meets your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="fa300-200">Actuellement, le contenu de l’aide actualisable est publié uniquement en anglais (en-US).</span><span class="sxs-lookup"><span data-stu-id="fa300-200">Currently, Updateable Help content is only published in English (en-US).</span></span> <span data-ttu-id="fa300-201">Sur certains systèmes non-Windows, vous devez utiliser le paramètre **UICulture** pour demander explicitement le `en-US` contenu.</span><span class="sxs-lookup"><span data-stu-id="fa300-201">On some non-Windows systems you must use the **UICulture** parameter to explicitly request the `en-US` content.</span></span>

## <a name="how-to-use-online-help"></a><span data-ttu-id="fa300-202">Comment utiliser l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="fa300-202">How to use online help</span></span>

<span data-ttu-id="fa300-203">Si vous ne pouvez pas ou choisissez de ne pas mettre à jour les fichiers d’aide sur votre ordinateur local, vous pouvez toujours obtenir les fichiers d’aide les plus récents en ligne.</span><span class="sxs-lookup"><span data-stu-id="fa300-203">If you cannot or choose not to update the help files on your local computer, you can still get the newest help files online.</span></span>

<span data-ttu-id="fa300-204">Pour ouvrir la rubrique d’aide en ligne pour une applet de commande ou une fonction, utilisez le paramètre **Online** de l’applet de commande `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-204">To open the online help topic for any cmdlet or function, use the **Online** parameter of the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="fa300-205">Par exemple, la commande suivante ouvre la rubrique d’aide en ligne de l' `Get-Job` applet de commande dans votre navigateur Internet par défaut :</span><span class="sxs-lookup"><span data-stu-id="fa300-205">For example, the following command opens the online help topic for the `Get-Job` cmdlet in your default internet browser:</span></span>

```powershell
Get-Help Get-Job -Online
```

<span data-ttu-id="fa300-206">Pour obtenir de l’aide en ligne sur un script, utilisez le paramètre **Online** et le chemin d’accès complet au script.</span><span class="sxs-lookup"><span data-stu-id="fa300-206">To get online help for a script, use the **Online** parameter and the full path to the script.</span></span>

<span data-ttu-id="fa300-207">Le paramètre **Online** ne fonctionne pas avec à propos des rubriques.</span><span class="sxs-lookup"><span data-stu-id="fa300-207">The **Online** parameter does not work with About topics.</span></span> <span data-ttu-id="fa300-208">Pour voir les rubriques about pour PowerShell, y compris les rubriques d’aide sur le langage PowerShell, consultez les [rubriques relatives à PowerShell](about.md).</span><span class="sxs-lookup"><span data-stu-id="fa300-208">To see the about topics for PowerShell, including help topics about the PowerShell language, see [PowerShell About Topics](about.md).</span></span>

## <a name="how-to-minimize-or-prevent-internet-downloads"></a><span data-ttu-id="fa300-209">Comment réduire ou empêcher les téléchargements Internet</span><span class="sxs-lookup"><span data-stu-id="fa300-209">How to minimize or prevent internet downloads</span></span>

<span data-ttu-id="fa300-210">Pour réduire les téléchargements Internet et fournir une aide actualisable aux utilisateurs qui ne sont pas connectés à Internet, utilisez l’applet de commande `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="fa300-210">To minimize internet downloads and provide Updatable Help to users who are not connected to the internet, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="fa300-211">Téléchargez l’aide à partir d’Internet et enregistrez-la sur un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="fa300-211">Download help from the internet and save it to a network share.</span></span> <span data-ttu-id="fa300-212">Ensuite, créez un paramètre de stratégie de groupe ou une tâche planifiée qui exécute une `Update-Help` commande sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="fa300-212">Then, create a Group Policy setting or scheduled job that runs an `Update-Help` command on all computers.</span></span> <span data-ttu-id="fa300-213">Définissez la valeur du paramètre **SourcePath** de l’applet de commande `Update-Help` sur le partage réseau.</span><span class="sxs-lookup"><span data-stu-id="fa300-213">Set the value of the **SourcePath** parameter of the `Update-Help` cmdlet to the network share.</span></span>

<span data-ttu-id="fa300-214">Pour empêcher les utilisateurs qui disposent d’un accès à Internet de télécharger l’aide pouvant être mise à jour à partir d’Internet, utilisez le paramètre **définir le chemin source par défaut pour Update-help** stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="fa300-214">To prevent users who have internet access from downloading Updatable Help from the internet, use the **Set the default source path for Update-Help** Group Policy setting.</span></span>

<span data-ttu-id="fa300-215">Cette stratégie de groupe paramètre ajoute implicitement le paramètre **SourcePath** , avec l’emplacement du système de fichiers que vous spécifiez, à chaque `Update-Help` commande sur chaque ordinateur affecté.</span><span class="sxs-lookup"><span data-stu-id="fa300-215">This Group Policy setting implicitly adds the **SourcePath** parameter, with the filesystem location that you specify, to every `Update-Help` command on every affected computer.</span></span> <span data-ttu-id="fa300-216">Les utilisateurs peuvent utiliser le paramètre **SourcePath** explicitement pour spécifier un emplacement de système de fichiers différent, mais ils ne peuvent pas exclure le paramètre **SourcePath** et télécharger l’aide à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="fa300-216">Users can use the **SourcePath** parameter explicitly to specify a different filesystem location, but they cannot exclude the **SourcePath** parameter and download help from the internet.</span></span>

> [!NOTE]
> <span data-ttu-id="fa300-217">Le paramètre **définir le chemin d’accès source par défaut pour la stratégie de groupe mise à jour-aide** apparaît sous **Configuration ordinateur** et **Configuration utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="fa300-217">The **Set the default source path for Update-Help** group policy setting appears under **Computer Configuration** and **User Configuration** .</span></span> <span data-ttu-id="fa300-218">Toutefois, seul le paramètre de stratégie sous **Configuration ordinateur** est effectif.</span><span class="sxs-lookup"><span data-stu-id="fa300-218">However, only the policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="fa300-219">Le paramètre de stratégie sous **Configuration utilisateur** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="fa300-219">The policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="fa300-220">Pour plus d’informations, consultez [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="fa300-220">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="how-to-update-help-for-non-standard-modules"></a><span data-ttu-id="fa300-221">Comment mettre à jour l’aide pour les modules non standard</span><span class="sxs-lookup"><span data-stu-id="fa300-221">How to update help for non-standard modules</span></span>

<span data-ttu-id="fa300-222">Pour mettre à jour ou enregistrer l’aide d’un module qui n’est pas retourné par le paramètre **listAvailable** de l' `Get-Module` applet de commande, importez le module dans la session active avant d’exécuter une `Update-Help` `Save-Help` commande ou.</span><span class="sxs-lookup"><span data-stu-id="fa300-222">To update or save help for a module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, import the module into the current session before running an `Update-Help` or `Save-Help` command.</span></span> <span data-ttu-id="fa300-223">Sur un ordinateur distant, avant d’exécuter la `Save-Help` commande, importez le module dans la session active, ou le `Invoke-Command` bloc de script, qui est connecté à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fa300-223">On a remote computer, before running the `Save-Help` command, import the module into the current Session, or `Invoke-Command` script block, that is connected to the remote computer.</span></span>

<span data-ttu-id="fa300-224">Quand le module est dans la session active, exécutez les `Update-Help` applets de commande ou `Save-Help` sans paramètres, ou utilisez le paramètre **module** pour spécifier le nom du module.</span><span class="sxs-lookup"><span data-stu-id="fa300-224">When the module is in the current session, run the `Update-Help` or `Save-Help` cmdlets without parameters, or use the **Module** parameter to specify the module name.</span></span>

<span data-ttu-id="fa300-225">Les paramètres de **module** des `Update-Help` applets de commande et `Save-Help` acceptent uniquement un nom de module.</span><span class="sxs-lookup"><span data-stu-id="fa300-225">The **Module** parameters of the `Update-Help` and `Save-Help` cmdlets accept only a module name.</span></span> <span data-ttu-id="fa300-226">Ils n’acceptent pas le chemin d’accès à un fichier de module.</span><span class="sxs-lookup"><span data-stu-id="fa300-226">They do not accept the path to a module file.</span></span>

<span data-ttu-id="fa300-227">Utilisez cette technique pour mettre à jour ou enregistrer l’aide des modules qui ne sont pas retournés par le paramètre **listAvailable** de l’applet de commande `Get-Module` , par exemple un module installé dans un emplacement qui n’est pas listé dans la `$env:PSModulePath` variable d’environnement, ou un module qui n’est pas correctement construit (le répertoire du module ne contient pas au moins un fichier dont le nom de la valeur est identique</span><span class="sxs-lookup"><span data-stu-id="fa300-227">Use this technique to update or save help for any module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, such as a module that is installed in a location that is not listed in the `$env:PSModulePath` environment variable, or a module that is not well-formed (the module directory does not contain at least one file whose basename is the same as the directory name).</span></span>

## <a name="how-to-support-updatable-help"></a><span data-ttu-id="fa300-228">Comment prendre en charge l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="fa300-228">How to support updatable help</span></span>

<span data-ttu-id="fa300-229">Si vous créez un module, vous pouvez prendre en charge l’aide en ligne et l’aide actualisable pour vos modules.</span><span class="sxs-lookup"><span data-stu-id="fa300-229">If you author a module, you can support online help and Updatable Help for your modules.</span></span> <span data-ttu-id="fa300-230">Pour plus d’informations, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/help/supporting-updatable-help) et prise en charge de l' [aide en ligne](/powershell/scripting/developer/module/supporting-online-help) dans le Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="fa300-230">For more information, see [Supporting Updatable Help](/powershell/scripting/developer/help/supporting-updatable-help) and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help) in the Microsoft Docs.</span></span>

<span data-ttu-id="fa300-231">Aide actualisable non disponible pour les composants logiciels enfichables PowerShell ou l’aide basée sur des commentaires.</span><span class="sxs-lookup"><span data-stu-id="fa300-231">Updatable help not available for PowerShell snap-ins or comment-based help.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa300-232">Notes</span><span class="sxs-lookup"><span data-stu-id="fa300-232">Remarks</span></span>

<span data-ttu-id="fa300-233">Les `Update-Help` applets de commande et ne `Save-Help` sont pas prises en charge sur environnement de préinstallation Windows (WinPE) (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="fa300-233">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa300-234">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa300-234">See also</span></span>

[<span data-ttu-id="fa300-235">Get-Help</span><span class="sxs-lookup"><span data-stu-id="fa300-235">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="fa300-236">Save-Help</span><span class="sxs-lookup"><span data-stu-id="fa300-236">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

[<span data-ttu-id="fa300-237">Update-Help</span><span class="sxs-lookup"><span data-stu-id="fa300-237">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)
