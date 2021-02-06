---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: 6996decc6b2f8b99ab9c04d96c487c37f2609c9e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596918"
---
# <span data-ttu-id="a0378-102">Save-Help</span><span class="sxs-lookup"><span data-stu-id="a0378-102">Save-Help</span></span>

## <span data-ttu-id="a0378-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a0378-103">SYNOPSIS</span></span>
<span data-ttu-id="a0378-104">Télécharge et enregistre les derniers fichiers d'aide dans un répertoire du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a0378-104">Downloads and saves the newest help files to a file system directory.</span></span>

## <span data-ttu-id="a0378-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a0378-105">SYNTAX</span></span>

### <span data-ttu-id="a0378-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a0378-106">Path (Default)</span></span>

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

### <span data-ttu-id="a0378-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0378-107">LiteralPath</span></span>

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

## <span data-ttu-id="a0378-108">Description</span><span class="sxs-lookup"><span data-stu-id="a0378-108">DESCRIPTION</span></span>

<span data-ttu-id="a0378-109">L' `Save-Help` applet de commande télécharge les fichiers d’aide les plus récents pour les modules PowerShell et les enregistre dans un répertoire que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="a0378-109">The `Save-Help` cmdlet downloads the newest help files for PowerShell modules and saves them to a directory that you specify.</span></span> <span data-ttu-id="a0378-110">Cette fonctionnalité vous permet de mettre à jour les fichiers d'aide sur les ordinateurs qui n'ont pas accès à Internet et facilite la mise à jour des fichiers d'aide sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a0378-110">This feature lets you update the help files on computers that do not have access to the Internet, and makes it easier to update the help files on multiple computers.</span></span>

<span data-ttu-id="a0378-111">Dans Windows PowerShell 3,0, `Save-Help` fonctionnait uniquement pour les modules qui sont installés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a0378-111">In Windows PowerShell 3.0, `Save-Help` worked only for modules that are installed on the local computer.</span></span> <span data-ttu-id="a0378-112">Bien qu’il soit possible d’importer un module à partir d’un ordinateur distant ou d’obtenir une référence à un objet **PSModuleInfo** à partir d’un ordinateur distant à l’aide de la communication à distance PowerShell, la propriété **HelpInfoUri** n’a pas été conservée et `Save-Help` ne fonctionnerait pas pour l’aide des modules distants.</span><span class="sxs-lookup"><span data-stu-id="a0378-112">Although it was possible to import a module from a remote computer, or obtain a reference to a **PSModuleInfo** object from a remote computer by using PowerShell remoting, the **HelpInfoUri** property was not preserved, and `Save-Help` would not work for remote module Help.</span></span>

<span data-ttu-id="a0378-113">Dans Windows PowerShell 4,0, la propriété **HelpInfoUri** est conservée via la communication à distance PowerShell, ce qui permet `Save-Help` à de fonctionner pour les modules qui sont installés sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="a0378-113">In Windows PowerShell 4.0, the **HelpInfoUri** property is preserved over PowerShell remoting, which enables `Save-Help` to work for modules that are installed on remote computers.</span></span> <span data-ttu-id="a0378-114">Il est également possible d’enregistrer un objet **PSModuleInfo** sur un disque ou sur un support amovible en exécutant `Export-Clixml` sur un ordinateur qui n’a pas accès à Internet, d’importer l’objet sur un ordinateur qui a accès à Internet, puis `Save-Help` d’exécuter sur l’objet **PSModuleInfo** .</span><span class="sxs-lookup"><span data-stu-id="a0378-114">It is also possible to save a **PSModuleInfo** object to disk or removable media by running `Export-Clixml` on a computer that does not have Internet access, import the object on a computer that does have Internet access, and then run `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="a0378-115">L’aide enregistrée peut être transportée vers l’ordinateur distant à l’aide d’un support de stockage amovible, tel qu’un lecteur USB.</span><span class="sxs-lookup"><span data-stu-id="a0378-115">The saved help can be transported to the remote computer by using removable storage media, such as a USB drive.</span></span> <span data-ttu-id="a0378-116">L’aide peut être installée sur l’ordinateur distant en exécutant `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="a0378-116">The help can be installed on the remote computer by running `Update-Help`.</span></span> <span data-ttu-id="a0378-117">Ce processus peut être utilisé pour installer l'aide sur les ordinateurs qui ne disposent d'aucun accès réseau.</span><span class="sxs-lookup"><span data-stu-id="a0378-117">This process can be used to install help on computers that do not have any kind of network access.</span></span>

<span data-ttu-id="a0378-118">Pour installer les fichiers d’aide enregistrés, exécutez l’applet de commande `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="a0378-118">To install saved help files, run the `Update-Help` cmdlet.</span></span> <span data-ttu-id="a0378-119">Ajoutez son paramètre **SourcePath** pour spécifier le dossier dans lequel vous avez enregistré les fichiers d’aide.</span><span class="sxs-lookup"><span data-stu-id="a0378-119">Add its **SourcePath** parameter to specify the folder in which you saved the Help files.</span></span>

<span data-ttu-id="a0378-120">Sans paramètres, une `Save-Help` commande télécharge l’aide la plus récente pour tous les modules de la session et les modules installés sur l’ordinateur à un emplacement répertorié dans la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="a0378-120">Without parameters, a `Save-Help` command downloads the newest help for all modules in the session and for modules that are installed on the computer in a location listed in the **PSModulePath** environment variable.</span></span> <span data-ttu-id="a0378-121">Cette action ignore les modules qui ne prennent pas en charge l’aide actualisable sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="a0378-121">This action skips modules that do not support Updatable Help without warning.</span></span>

<span data-ttu-id="a0378-122">L' `Save-Help` applet de commande vérifie la version des fichiers d’aide dans le dossier de destination.</span><span class="sxs-lookup"><span data-stu-id="a0378-122">The `Save-Help` cmdlet checks the version of any help files in the destination folder.</span></span> <span data-ttu-id="a0378-123">Si des fichiers d’aide plus récents sont disponibles, cette applet de commande télécharge les fichiers d’aide les plus récents à partir d’Internet, puis les enregistre dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="a0378-123">If newer help files are available, this cmdlet downloads the newest help files from the Internet, and then saves them in the folder.</span></span> <span data-ttu-id="a0378-124">L' `Save-Help` applet de commande fonctionne comme la `Update-Help` cmdlet, sauf qu’elle enregistre les fichiers CAB (. cab) téléchargés, au lieu d’extraire les fichiers d’aide des fichiers CAB et de les installer sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-124">The `Save-Help` cmdlet works just like the `Update-Help` cmdlet, except that it saves the downloaded cabinet (.cab) files, instead of extracting the help files from the cabinet files and installing them on the computer.</span></span>

<span data-ttu-id="a0378-125">L'aide enregistrée pour chaque module se compose d'un fichier d'informations d'aide (HelpInfo XML) et d'un fichier CAB pour les fichiers d'aide dans chaque culture d'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-125">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="a0378-126">Vous n’avez pas besoin d’extraire les fichiers d’aide du fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="a0378-126">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="a0378-127">L' `Update-Help` applet de commande extrait les fichiers d’aide, valide le code XML à des fins de sécurité, puis installe les fichiers d’aide et le fichier d’informations d’aide dans un sous-dossier spécifique à la langue du dossier du module.</span><span class="sxs-lookup"><span data-stu-id="a0378-127">The `Update-Help` cmdlet extracts the help files, validates the XML for safety, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>

<span data-ttu-id="a0378-128">Pour enregistrer les fichiers d’aide pour les modules dans le dossier d’installation de PowerShell ( `$pshome\Modules` ), démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-128">To save the help files for modules in the PowerShell installation folder (`$pshome\Modules`), start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="a0378-129">Vous devez être membre du groupe Administrateurs sur l'ordinateur pour télécharger les fichiers d'aide pour ces modules.</span><span class="sxs-lookup"><span data-stu-id="a0378-129">You must be a member of the Administrators group on the computer to download the help files for these modules.</span></span>

<span data-ttu-id="a0378-130">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="a0378-130">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="a0378-131">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a0378-131">EXAMPLES</span></span>

### <span data-ttu-id="a0378-132">Exemple 1 : enregistrer l’aide du module DhcpServer</span><span class="sxs-lookup"><span data-stu-id="a0378-132">Example 1: Save the help for the DhcpServer module</span></span>

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module,
# save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

<span data-ttu-id="a0378-133">Cet exemple montre trois façons différentes d’utiliser `Save-Help` pour enregistrer l’aide du module **dhcpserver** à partir d’un ordinateur client connecté à Internet, sans installer le module **dhcpserver** ou le rôle serveur DHCP sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a0378-133">This example shows three different ways to use `Save-Help` to save the help for the **DhcpServer** module from an Internet-connected client computer, without installing the **DhcpServer** module or the DHCP Server role on the local computer.</span></span>

### <span data-ttu-id="a0378-134">Exemple 2 : installer l’aide pour le module DhcpServer</span><span class="sxs-lookup"><span data-stu-id="a0378-134">Example 2: Install help for the DhcpServer module</span></span>

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the
# PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer
# module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and
# then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

<span data-ttu-id="a0378-135">Cet exemple montre comment installer l’aide que vous avez enregistrée dans l’exemple 1 pour le module **DhcpServer** sur un ordinateur qui n’a pas accès à Internet.</span><span class="sxs-lookup"><span data-stu-id="a0378-135">This example shows how to install help that you saved in Example 1 for the **DhcpServer** module on a computer that does not have Internet access.</span></span>

### <span data-ttu-id="a0378-136">Exemple 3 : enregistrer l’aide pour tous les modules</span><span class="sxs-lookup"><span data-stu-id="a0378-136">Example 3: Save help for all modules</span></span>

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

<span data-ttu-id="a0378-137">Cette commande télécharge les fichiers d'aide les plus récents pour tous les modules dans la culture d'interface utilisateur définie pour Windows sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a0378-137">This command downloads the newest help files for all modules in the UI culture set for Windows on the local computer.</span></span> <span data-ttu-id="a0378-138">Elle enregistre les fichiers d’aide dans le `\\Server01\Fileshare01` dossier.</span><span class="sxs-lookup"><span data-stu-id="a0378-138">It saves the help files in the `\\Server01\Fileshare01` folder.</span></span>

### <span data-ttu-id="a0378-139">Exemple 4 : enregistrer l’aide pour un module sur l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="a0378-139">Example 4: Save help for a module on the computer</span></span>

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

<span data-ttu-id="a0378-140">Cette commande télécharge les fichiers d’aide les plus récents pour le module **ServerManager** , puis les enregistre dans le `\\Server01\Fileshare01` dossier.</span><span class="sxs-lookup"><span data-stu-id="a0378-140">This command downloads the newest help files for the **ServerManager** module, and then saves them in the `\\Server01\Fileshare01` folder.</span></span>

<span data-ttu-id="a0378-141">Quand un module est installé sur l'ordinateur, vous pouvez taper le nom du module comme valeur du paramètre **Module**, même si le module n'est pas importé dans la session active.</span><span class="sxs-lookup"><span data-stu-id="a0378-141">When a module is installed on the computer, you can type the module name as the value of the **Module** parameter, even if the module is not imported into the current session.</span></span>

<span data-ttu-id="a0378-142">La commande utilise le paramètre **Credential** pour fournir les informations d'identification d'un utilisateur qui a l'autorisation d'écrire dans le partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a0378-142">The command uses the **Credential** parameter to supply the credentials of a user who has permission to write to the file share.</span></span>

### <span data-ttu-id="a0378-143">Exemple 5 : enregistrer l’aide pour un module sur un autre ordinateur</span><span class="sxs-lookup"><span data-stu-id="a0378-143">Example 5: Save help for a module on a different computer</span></span>

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

<span data-ttu-id="a0378-144">Ces commandes téléchargent les fichiers d’aide les plus récents pour le module **CustomSQL** et les enregistrent dans le `\\Server01\Fileshare01` dossier.</span><span class="sxs-lookup"><span data-stu-id="a0378-144">These commands download the newest help files for the **CustomSQL** module and save them in the `\\Server01\Fileshare01` folder.</span></span>

<span data-ttu-id="a0378-145">Étant donné que le module **CustomSQL** n’est pas installé sur l’ordinateur, la séquence comprend une `Invoke-Command` commande qui obtient l’objet module pour le module CustomSQL à partir de l’ordinateur Server02, puis dirige l’objet module vers l’applet de commande `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="a0378-145">Because the **CustomSQL** module is not installed on the computer, the sequence includes an `Invoke-Command` command that gets the module object for the CustomSQL module from the Server02 computer and then pipes the module object to the `Save-Help` cmdlet.</span></span>

<span data-ttu-id="a0378-146">Lorsqu’un module n’est pas installé sur l’ordinateur, `Save-Help` il a besoin de l’objet de module, qui comprend des informations sur l’emplacement des fichiers d’aide les plus récents.</span><span class="sxs-lookup"><span data-stu-id="a0378-146">When a module is not installed on the computer, `Save-Help` needs the module object, which includes information about the location of the newest help files.</span></span>

### <span data-ttu-id="a0378-147">Exemple 6 : enregistrer l’aide d’un module dans plusieurs langues</span><span class="sxs-lookup"><span data-stu-id="a0378-147">Example 6: Save help for a module in multiple languages</span></span>

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

<span data-ttu-id="a0378-148">Cette commande enregistre l’aide pour les modules PowerShell Core dans quatre cultures d’interface utilisateur différentes.</span><span class="sxs-lookup"><span data-stu-id="a0378-148">This command saves help for the PowerShell Core modules in four different UI cultures.</span></span> <span data-ttu-id="a0378-149">Il n’est pas nécessaire d’installer les modules linguistiques de ces paramètres régionaux sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-149">The language packs for these locales do not have to be installed on the computer.</span></span>

<span data-ttu-id="a0378-150">`Save-Help` peut télécharger des fichiers d’aide pour les modules dans des cultures d’interface utilisateur différentes uniquement lorsque le propriétaire du module rend les fichiers traduits disponibles sur Internet.</span><span class="sxs-lookup"><span data-stu-id="a0378-150">`Save-Help` can download help files for modules in different UI cultures only when the module owner makes the translated files available on the Internet.</span></span>

### <span data-ttu-id="a0378-151">Exemple 7 : enregistrer l’aide plusieurs fois par jour</span><span class="sxs-lookup"><span data-stu-id="a0378-151">Example 7: Save help more than one time each day</span></span>

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

<span data-ttu-id="a0378-152">Cette commande enregistre l'aide de tous les modules qui sont installés sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-152">This command saves help for all modules that are installed on the computer.</span></span> <span data-ttu-id="a0378-153">La commande spécifie le paramètre **force** pour remplacer la règle qui empêche l' `Save-Help` applet de commande de télécharger l’aide plusieurs fois par période de 24 heures.</span><span class="sxs-lookup"><span data-stu-id="a0378-153">The command specifies the **Force** parameter to override the rule that prevents the `Save-Help` cmdlet from downloading help more than once in each 24-hour period.</span></span>

<span data-ttu-id="a0378-154">Le paramètre **force** remplace également la restriction de 1 Go et contourne la vérification de version.</span><span class="sxs-lookup"><span data-stu-id="a0378-154">The **Force** parameter also overrides the 1 GB restriction and circumvents version checking.</span></span>
<span data-ttu-id="a0378-155">Par conséquent, vous pouvez télécharger des fichiers même si la version n’est pas ultérieure à la version dans le dossier de destination.</span><span class="sxs-lookup"><span data-stu-id="a0378-155">Therefore, you can download files even if the version is not later than the version in the destination folder.</span></span>

<span data-ttu-id="a0378-156">La commande utilise l' `Save-Help` applet de commande pour télécharger et enregistrer les fichiers d’aide dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="a0378-156">The command uses the `Save-Help` cmdlet to download and save the help files to the specified folder.</span></span>
<span data-ttu-id="a0378-157">Le paramètre **force** est obligatoire lorsque vous devez exécuter une `Save-Help` commande plusieurs fois par jour.</span><span class="sxs-lookup"><span data-stu-id="a0378-157">The **Force** parameter is required when you have to run a `Save-Help` command more than one time each day.</span></span>

## <span data-ttu-id="a0378-158">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a0378-158">PARAMETERS</span></span>

### <span data-ttu-id="a0378-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="a0378-159">-Credential</span></span>

<span data-ttu-id="a0378-160">Spécifie les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-160">Specifies a user credential.</span></span> <span data-ttu-id="a0378-161">Cette applet de commande exécute la commande à l’aide des informations d’identification d’un utilisateur qui a l’autorisation d’accéder à l’emplacement du système de fichiers spécifié par le paramètre **DestinationPath** .</span><span class="sxs-lookup"><span data-stu-id="a0378-161">This cmdlet runs the command by using credentials of a user who has permission to access the file system location specified by the **DestinationPath** parameter.</span></span> <span data-ttu-id="a0378-162">Ce paramètre est valide uniquement lorsque le paramètre **DestinationPath** ou **LiteralPath** est utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="a0378-162">This parameter is valid only when the **DestinationPath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="a0378-163">Ce paramètre vous permet d’exécuter `Save-Help` des commandes qui utilisent le paramètre **DestinationPath** sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="a0378-163">This parameter enables you to run `Save-Help` commands that use the **DestinationPath** parameter on remote computers.</span></span> <span data-ttu-id="a0378-164">En fournissant des informations d’identification explicites, vous pouvez exécuter la commande sur un ordinateur distant et accéder à un partage de fichiers sur un troisième ordinateur sans rencontrer une erreur d’accès refusé ou en utilisant l’authentification CredSSP pour déléguer les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a0378-164">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="a0378-165">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="a0378-165">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a0378-166">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="a0378-166">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="a0378-167">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="a0378-167">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="a0378-168">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="a0378-168">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0378-169">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="a0378-169">-DestinationPath</span></span>

<span data-ttu-id="a0378-170">Spécifie le chemin d’accès du dossier dans lequel les fichiers d’aide sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="a0378-170">Specifies the path of the folder in which the help files are saved.</span></span> <span data-ttu-id="a0378-171">Ne spécifiez pas un nom de fichier ou une extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="a0378-171">Do not specify a file name or file name extension.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0378-172">-Force</span><span class="sxs-lookup"><span data-stu-id="a0378-172">-Force</span></span>

<span data-ttu-id="a0378-173">Indique que cette applet de commande ne suit pas la limite d’une fois par jour, ignore la vérification de version et télécharge les fichiers qui dépassent la limite de 1 Go.</span><span class="sxs-lookup"><span data-stu-id="a0378-173">Indicates that this cmdlet does not follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="a0378-174">Sans ce paramètre, une seule `Save-Help` commande est autorisée pour chaque module au cours de chaque période de 24 heures, les téléchargements sont limités à 1 Go de contenu non compressé par module et les fichiers d’aide d’un module sont installés uniquement lorsqu’ils sont plus récents que les fichiers de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-174">Without this parameter, only one `Save-Help` command for each module is permitted in each 24-hour period, downloads are limited to 1 GB of uncompressed content per module, and help files for a module are installed only when they are newer than the files on the computer.</span></span>

<span data-ttu-id="a0378-175">La limite d’une fois par jour protège les serveurs qui hébergent les fichiers d’aide et vous permet d’ajouter une `Save-Help` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0378-175">The once-per-day limit protects the servers that host the help files, and makes it practical for you to add a `Save-Help` command to your PowerShell profile.</span></span>

<span data-ttu-id="a0378-176">Pour enregistrer l’aide d’un module dans plusieurs cultures d’interface utilisateur sans le paramètre **force** , incluez toutes les cultures d’interface utilisateur dans la même commande, par exemple : `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span><span class="sxs-lookup"><span data-stu-id="a0378-176">To save help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span></span>

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

### <span data-ttu-id="a0378-177">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="a0378-177">-FullyQualifiedModule</span></span>

<span data-ttu-id="a0378-178">Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** .</span><span class="sxs-lookup"><span data-stu-id="a0378-178">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="a0378-179">Consultez la section Notes du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="a0378-179">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="a0378-180">Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié dans l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="a0378-180">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="a0378-181">**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a0378-181">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="a0378-182">Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** .</span><span class="sxs-lookup"><span data-stu-id="a0378-182">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="a0378-183">les deux paramètres s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="a0378-183">the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="a0378-184">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0378-184">-LiteralPath</span></span>

<span data-ttu-id="a0378-185">Spécifie le chemin d’accès du dossier de destination.</span><span class="sxs-lookup"><span data-stu-id="a0378-185">Specifies a path of the destination folder.</span></span> <span data-ttu-id="a0378-186">Contrairement à la valeur du paramètre **DestinationPath** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="a0378-186">Unlike the value of the **DestinationPath** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="a0378-187">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="a0378-187">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="a0378-188">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a0378-188">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a0378-189">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="a0378-189">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0378-190">-Module</span><span class="sxs-lookup"><span data-stu-id="a0378-190">-Module</span></span>

<span data-ttu-id="a0378-191">Spécifie les modules pour lesquels cette applet de commande télécharge l’aide.</span><span class="sxs-lookup"><span data-stu-id="a0378-191">Specifies modules for which this cmdlet downloads help.</span></span> <span data-ttu-id="a0378-192">Entrez un ou plusieurs noms de module ou modèles de nom dans une liste séparée par des virgules ou dans un fichier qui a un nom de module sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="a0378-192">Enter one or more module names or name patters in a comma-separated list or in a file that has one module name on each line.</span></span> <span data-ttu-id="a0378-193">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a0378-193">Wildcard characters are permitted.</span></span> <span data-ttu-id="a0378-194">Vous pouvez également diriger les objets de module de l’applet de commande `Get-Module` vers `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="a0378-194">You can also pipe module objects from the `Get-Module` cmdlet to `Save-Help`.</span></span>

<span data-ttu-id="a0378-195">Par défaut, `Save-Help` télécharge l’aide pour tous les modules qui prennent en charge l’aide actualisable et sont installés sur l’ordinateur local à un emplacement répertorié dans la variable d’environnement **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="a0378-195">By default, `Save-Help` downloads help for all modules that support Updatable Help and are installed on the local computer in a location listed in the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="a0378-196">Pour enregistrer l’aide pour les modules qui ne sont pas installés sur l’ordinateur, exécutez une `Get-Module` commande sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a0378-196">To save help for modules that are not installed on the computer, run a `Get-Module` command on a remote computer.</span></span> <span data-ttu-id="a0378-197">Ensuite, dirigez les objets de module résultants vers l’applet de commande `Save-Help` ou envoyez les objets de module en tant que valeur des paramètres **module** ou **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="a0378-197">Then pipe the resulting module objects to the `Save-Help` cmdlet or submit the module objects as the value of the **Module** or **InputObject** parameters.</span></span>

<span data-ttu-id="a0378-198">Si le module que vous spécifiez est installé sur l'ordinateur, vous pouvez entrer le nom du module ou un objet de module.</span><span class="sxs-lookup"><span data-stu-id="a0378-198">If the module that you specify is installed on the computer, you can enter the module name or a module object.</span></span> <span data-ttu-id="a0378-199">Si le module n’est pas installé sur l’ordinateur, vous devez entrer un objet de module, tel que celui retourné par l’applet de commande `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="a0378-199">If the module is not installed on the computer, you must enter a module object, such as one returned by the `Get-Module` cmdlet.</span></span>

<span data-ttu-id="a0378-200">Le paramètre **module** de l' `Save-Help` applet de commande n’accepte pas le chemin d’accès complet d’un fichier de module ou d’un fichier manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="a0378-200">The **Module** parameter of the `Save-Help` cmdlet does not accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="a0378-201">Pour enregistrer l’aide d’un module qui ne se trouve pas dans un emplacement **PSModulePath** , importez le module dans la session active avant d’exécuter la `Save-Help` commande.</span><span class="sxs-lookup"><span data-stu-id="a0378-201">To save help for a module that is not in a **PSModulePath** location, import the module into the current session before you run the `Save-Help` command.</span></span>

<span data-ttu-id="a0378-202">La valeur « \* » (tous) tente de mettre à jour l’aide de tous les modules installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-202">A value of "\*" (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="a0378-203">Cela comprend les modules qui ne prennent pas en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="a0378-203">This includes modules that do not support Updatable Help.</span></span> <span data-ttu-id="a0378-204">Cette valeur peut générer des erreurs quand la commande rencontre des modules qui ne prennent pas en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="a0378-204">This value might generate errors when the command encounters modules that do not support Updatable Help.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="a0378-205">-UICulture</span><span class="sxs-lookup"><span data-stu-id="a0378-205">-UICulture</span></span>

<span data-ttu-id="a0378-206">Spécifie les valeurs de culture d’interface utilisateur pour lesquelles cette applet de commande obtient les fichiers d’aide mis à jour.</span><span class="sxs-lookup"><span data-stu-id="a0378-206">Specifies UI culture values for which this cmdlet gets updated help files.</span></span> <span data-ttu-id="a0378-207">Entrez un ou plusieurs codes de langue, par exemple `es-ES` , une variable qui contient des objets de culture ou une commande qui obtient des objets de culture, telle qu’une `Get-Culture` `Get-UICulture` commande ou.</span><span class="sxs-lookup"><span data-stu-id="a0378-207">Enter one or more language codes, such as `es-ES`, a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span>

<span data-ttu-id="a0378-208">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="a0378-208">Wildcard characters are not permitted.</span></span> <span data-ttu-id="a0378-209">Ne spécifiez pas de code de langue partielle, tel que « de ».</span><span class="sxs-lookup"><span data-stu-id="a0378-209">Do not specify a partial language code, such as "de".</span></span>

<span data-ttu-id="a0378-210">Par défaut, `Save-Help` obtient les fichiers d’aide dans la culture d’interface utilisateur définie pour Windows ou sa culture de secours.</span><span class="sxs-lookup"><span data-stu-id="a0378-210">By default, `Save-Help` gets help files in the UI culture set for Windows or its fallback culture.</span></span>
<span data-ttu-id="a0378-211">Si vous spécifiez le paramètre **UICulture** , `Save-Help` recherche uniquement de l’aide pour la culture d’interface utilisateur spécifiée, et non dans une culture de secours.</span><span class="sxs-lookup"><span data-stu-id="a0378-211">If you specify the **UICulture** parameter, `Save-Help` looks for help only for the specified UI culture, not in any fallback culture.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0378-212">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="a0378-212">-UseDefaultCredentials</span></span>

<span data-ttu-id="a0378-213">Indique que cette applet de commande exécute la commande, y compris le téléchargement Web, avec les informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="a0378-213">Indicates that this cmdlet runs the command, including the web download, with the credentials of the current user.</span></span> <span data-ttu-id="a0378-214">Par défaut, la commande s'exécute sans informations d'identification explicites.</span><span class="sxs-lookup"><span data-stu-id="a0378-214">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="a0378-215">Ce paramètre est effectif uniquement quand le téléchargement web utilise NTLM, la négociation ou l'authentification Kerberos.</span><span class="sxs-lookup"><span data-stu-id="a0378-215">This parameter is effective only when the web download uses NTLM, negotiate, or Kerberos-based authentication.</span></span>

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

### <span data-ttu-id="a0378-216">-Étendue</span><span class="sxs-lookup"><span data-stu-id="a0378-216">-Scope</span></span>

<span data-ttu-id="a0378-217">Ce paramètre ne fait rien dans cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a0378-217">This paramater does nothing in this cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0378-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0378-218">CommonParameters</span></span>

<span data-ttu-id="a0378-219">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0378-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0378-220">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a0378-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0378-221">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a0378-221">INPUTS</span></span>

### <span data-ttu-id="a0378-222">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="a0378-222">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="a0378-223">Vous pouvez diriger un objet de module de l’applet de commande `Get-Module` vers le paramètre de **module** de `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="a0378-223">You can pipe a module object from the `Get-Module` cmdlet to the **Module** parameter of `Save-Help`.</span></span>

## <span data-ttu-id="a0378-224">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a0378-224">OUTPUTS</span></span>

### <span data-ttu-id="a0378-225">None</span><span class="sxs-lookup"><span data-stu-id="a0378-225">None</span></span>

<span data-ttu-id="a0378-226">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="a0378-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a0378-227">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a0378-227">NOTES</span></span>

- <span data-ttu-id="a0378-228">Pour enregistrer l’aide des modules dans le dossier $pshome nouvelle \modules., démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-228">To save help for modules in the $pshome\Modules folder, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="a0378-229">Seuls les membres du groupe Administrateurs sur l’ordinateur peuvent télécharger l’aide pour les modules dans le dossier $pshome nouvelle \modules..</span><span class="sxs-lookup"><span data-stu-id="a0378-229">Only members of the Administrators group on the computer can download help for modules in the $pshome\Modules folder.</span></span>
- <span data-ttu-id="a0378-230">L'aide enregistrée pour chaque module se compose d'un fichier d'informations d'aide (HelpInfo XML) et d'un fichier CAB pour les fichiers d'aide dans chaque culture d'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-230">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="a0378-231">Vous n’avez pas besoin d’extraire les fichiers d’aide du fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="a0378-231">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="a0378-232">L' `Update-Help` applet de commande extrait les fichiers d’aide, valide le XML, puis installe les fichiers d’aide et le fichier d’informations d’aide dans un sous-dossier spécifique à la langue du dossier du module.</span><span class="sxs-lookup"><span data-stu-id="a0378-232">The `Update-Help` cmdlet extracts the help files, validates the XML, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>
- <span data-ttu-id="a0378-233">L' `Save-Help` applet de commande peut enregistrer l’aide pour les modules qui ne sont pas installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-233">The `Save-Help` cmdlet can save help for modules that are not installed on the computer.</span></span> <span data-ttu-id="a0378-234">Toutefois, étant donné que les fichiers d’aide sont installés dans le dossier de module, l’applet de commande `Update-Help` peut installer le fichier d’aide mis à jour uniquement pour les modules qui sont installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0378-234">However, because help files are installed in the module folder, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span>
- <span data-ttu-id="a0378-235">Si `Save-Help` ne parvient pas à trouver les fichiers d’aide mis à jour pour un module ou ne peut pas trouver les fichiers d’aide mis à jour dans la langue spécifiée, il se poursuit en mode silencieux sans afficher de message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a0378-235">If `Save-Help` cannot find updated help files for a module, or cannot find updated help files in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="a0378-236">Pour voir quels fichiers ont été enregistrés par la commande, spécifiez le paramètre **Verbose** .</span><span class="sxs-lookup"><span data-stu-id="a0378-236">To see which files were saved by the command, specify the **Verbose** parameter.</span></span>
- <span data-ttu-id="a0378-237">Les modules sont la plus petite unité d'aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="a0378-237">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="a0378-238">Vous ne pouvez pas enregistrer l’aide d’une applet de commande particulière, uniquement pour toutes les applets de commande du module.</span><span class="sxs-lookup"><span data-stu-id="a0378-238">You cannot save help for a particular cmdlet, only for all cmdlets in module.</span></span> <span data-ttu-id="a0378-239">Pour rechercher le module qui contient une applet de commande particulière, utilisez la propriété **modulename** avec l' `Get-Command` applet de commande, par exemple, `(Get-Command \<cmdlet-name\>).ModuleName`</span><span class="sxs-lookup"><span data-stu-id="a0378-239">To find the module that contains a particular cmdlet, use the **ModuleName** property together with the `Get-Command` cmdlet, for example, `(Get-Command \<cmdlet-name\>).ModuleName`</span></span>
- <span data-ttu-id="a0378-240">`Save-Help` prend en charge tous les modules et les composants logiciels enfichables PowerShell Core. Elle ne prend en charge aucun autre composant logiciel enfichable.</span><span class="sxs-lookup"><span data-stu-id="a0378-240">`Save-Help` supports all modules and the PowerShell Core snap-ins. It does not support any other snap-ins.</span></span>
- <span data-ttu-id="a0378-241">Les `Update-Help` `Save-Help` applets de commande et utilisent les ports suivants pour télécharger les fichiers d’aide : le port 80 pour http et le port 443 pour HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a0378-241">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>
- <span data-ttu-id="a0378-242">Les `Update-Help` applets de commande et ne `Save-Help` sont pas prises en charge sur environnement de préinstallation Windows (WinPE) (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="a0378-242">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="a0378-243">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a0378-243">RELATED LINKS</span></span>

[<span data-ttu-id="a0378-244">Get-Help</span><span class="sxs-lookup"><span data-stu-id="a0378-244">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="a0378-245">Get-Module</span><span class="sxs-lookup"><span data-stu-id="a0378-245">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="a0378-246">Update-Help</span><span class="sxs-lookup"><span data-stu-id="a0378-246">Update-Help</span></span>](Update-Help.md)