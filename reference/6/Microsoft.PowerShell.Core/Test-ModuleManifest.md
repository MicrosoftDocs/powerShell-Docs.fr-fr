---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: 03f32d798a9e7ec1e58cdeb4ddf5d30edccd2490
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204866"
---
# <span data-ttu-id="81725-103">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="81725-103">Test-ModuleManifest</span></span>

## <span data-ttu-id="81725-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="81725-104">SYNOPSIS</span></span>
<span data-ttu-id="81725-105">Vérifie qu'un fichier manifeste de module décrit précisément le contenu d'un module.</span><span class="sxs-lookup"><span data-stu-id="81725-105">Verifies that a module manifest file accurately describes the contents of a module.</span></span>

## <span data-ttu-id="81725-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="81725-106">SYNTAX</span></span>

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="81725-107">Description</span><span class="sxs-lookup"><span data-stu-id="81725-107">DESCRIPTION</span></span>

<span data-ttu-id="81725-108">L’applet de commande **Test-ModuleManifest** vérifie que les fichiers qui sont répertoriés dans le fichier manifeste du module (. psd1) se trouvent dans les chemins d’accès spécifiés.</span><span class="sxs-lookup"><span data-stu-id="81725-108">The **Test-ModuleManifest** cmdlet verifies that the files that are listed in the module manifest (.psd1) file are actually in the specified paths.</span></span>

<span data-ttu-id="81725-109">Cette applet de commande est conçue pour aider les auteurs du module à tester leurs fichiers manifeste.</span><span class="sxs-lookup"><span data-stu-id="81725-109">This cmdlet is designed to help module authors test their manifest files.</span></span>
<span data-ttu-id="81725-110">Les utilisateurs du module peuvent également utiliser cette applet de commande dans des scripts et des commandes pour détecter les erreurs avant d’exécuter des scripts qui dépendent du module.</span><span class="sxs-lookup"><span data-stu-id="81725-110">Module users can also use this cmdlet in scripts and commands to detect errors before they run scripts that depend on the module.</span></span>

<span data-ttu-id="81725-111">**Test-ModuleManifest** retourne un objet qui représente le module.</span><span class="sxs-lookup"><span data-stu-id="81725-111">**Test-ModuleManifest** returns an object that represents the module.</span></span>
<span data-ttu-id="81725-112">Il s’agit du même type d’objet que Get-Module retourne.</span><span class="sxs-lookup"><span data-stu-id="81725-112">This is the same type of object that Get-Module returns.</span></span>
<span data-ttu-id="81725-113">Si des fichiers ne figurent pas aux emplacements spécifiés dans le manifeste, l'applet de commande génère également une erreur pour chaque fichier manquant.</span><span class="sxs-lookup"><span data-stu-id="81725-113">If any files are not in the locations specified in the manifest, the cmdlet also generates an error for each missing file.</span></span>

## <span data-ttu-id="81725-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="81725-114">EXAMPLES</span></span>

### <span data-ttu-id="81725-115">Exemple 1 : tester un manifeste</span><span class="sxs-lookup"><span data-stu-id="81725-115">Example 1: Test a manifest</span></span>

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

<span data-ttu-id="81725-116">Cette commande teste le manifeste de module TestModule.psd1.</span><span class="sxs-lookup"><span data-stu-id="81725-116">This command tests the TestModule.psd1 module manifest.</span></span>

### <span data-ttu-id="81725-117">Exemple 2 : tester un manifeste à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="81725-117">Example 2: Test a manifest by using the pipeline</span></span>

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="81725-118">Cette commande utilise un opérateur de pipeline (|) pour envoyer une chaîne de chemin d’accès à **Test-ModuleManifest** .</span><span class="sxs-lookup"><span data-stu-id="81725-118">This command uses a pipeline operator (|) to send a path string to **Test-ModuleManifest** .</span></span>

<span data-ttu-id="81725-119">La sortie de la commande indique que le test a échoué, car le fichier TestTypes.ps1xml, indiqué dans le manifeste, est introuvable.</span><span class="sxs-lookup"><span data-stu-id="81725-119">The command output shows that the test failed, because the TestTypes.ps1xml file, which was listed in the manifest, was not found.</span></span>

### <span data-ttu-id="81725-120">Exemple 3 : écrire une fonction pour tester un manifeste de module</span><span class="sxs-lookup"><span data-stu-id="81725-120">Example 3: Write a function to test a module manifest</span></span>

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

<span data-ttu-id="81725-121">Cette fonction est similaire **à Test-ModuleManifest** , mais retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="81725-121">This function is like **Test-ModuleManifest** , but it returns a Boolean value.</span></span>
<span data-ttu-id="81725-122">La fonction retourne $True si le manifeste a réussi le test et $False dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="81725-122">The function returns $True if the manifest passed the test and $False otherwise.</span></span>

<span data-ttu-id="81725-123">La fonction utilise l’applet de commande Get-ChildItem, alias = dir, pour récupérer le manifeste de module spécifié par la variable $path.</span><span class="sxs-lookup"><span data-stu-id="81725-123">The function uses the Get-ChildItem cmdlet, alias = dir, to get the module manifest specified by the $path variable.</span></span>
<span data-ttu-id="81725-124">La commande utilise un opérateur de pipeline (|) pour passer l’objet fichier à **Test-ModuleManifest** .</span><span class="sxs-lookup"><span data-stu-id="81725-124">The command uses a pipeline operator (|) to pass the file object to **Test-ModuleManifest** .</span></span>

<span data-ttu-id="81725-125">**Test-ModuleManifest** utilise le paramètre commun *ErrorAction* avec la valeur SilentlyContinue pour supprimer l’affichage des erreurs générées par la commande.</span><span class="sxs-lookup"><span data-stu-id="81725-125">**Test-ModuleManifest** uses the *ErrorAction* common parameter with a value of SilentlyContinue to suppress the display of any errors that the command generates.</span></span>
<span data-ttu-id="81725-126">Elle enregistre également l’objet **PSModuleInfo** que **Test-ModuleManifest** renvoie dans la variable $a.</span><span class="sxs-lookup"><span data-stu-id="81725-126">It also saves the **PSModuleInfo** object that **Test-ModuleManifest** returns in the $a variable.</span></span>
<span data-ttu-id="81725-127">Par conséquent, l’objet n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="81725-127">Therefore, the object is not displayed.</span></span>

<span data-ttu-id="81725-128">Ensuite, dans une commande distincte, la fonction affiche la valeur de $ ?</span><span class="sxs-lookup"><span data-stu-id="81725-128">Then, in a separate command, the function displays the value of the $?</span></span>
<span data-ttu-id="81725-129">variable automatique.</span><span class="sxs-lookup"><span data-stu-id="81725-129">automatic variable.</span></span>
<span data-ttu-id="81725-130">Si la commande précédente ne génère pas d’erreur, la commande affiche $True et $False dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="81725-130">If the previous command generates no error, the command displays $True, and $False otherwise.</span></span>

<span data-ttu-id="81725-131">Vous pouvez utiliser cette fonction dans des instructions conditionnelles, telles que celles qui peuvent précéder une commande **import-module** ou une commande qui utilise le module.</span><span class="sxs-lookup"><span data-stu-id="81725-131">You can use this function in conditional statements, such as those that might precede an **Import-Module** command or a command that uses the module.</span></span>

## <span data-ttu-id="81725-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="81725-132">PARAMETERS</span></span>

### <span data-ttu-id="81725-133">-Path</span><span class="sxs-lookup"><span data-stu-id="81725-133">-Path</span></span>

<span data-ttu-id="81725-134">Spécifie un chemin d’accès et un nom de fichier pour le fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="81725-134">Specifies a path and file name for the manifest file.</span></span>
<span data-ttu-id="81725-135">Entrez un chemin d’accès et un nom facultatifs pour le fichier manifeste de module avec l’extension de nom de fichier. psd1.</span><span class="sxs-lookup"><span data-stu-id="81725-135">Enter an optional path and name of the module manifest file that has the .psd1 file name extension.</span></span>
<span data-ttu-id="81725-136">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="81725-136">The default location is the current directory.</span></span>
<span data-ttu-id="81725-137">Les caractères génériques sont pris en charge, mais ils doivent être résolus en un seul fichier manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="81725-137">Wildcard characters are supported, but must resolve to a single module manifest file.</span></span>
<span data-ttu-id="81725-138">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="81725-138">This parameter is required.</span></span>
<span data-ttu-id="81725-139">Vous pouvez également diriger un chemin vers **Test-ModuleManifest** .</span><span class="sxs-lookup"><span data-stu-id="81725-139">You can also pipe a path to **Test-ModuleManifest** .</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="81725-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="81725-140">CommonParameters</span></span>

<span data-ttu-id="81725-141">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="81725-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="81725-142">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="81725-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="81725-143">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="81725-143">INPUTS</span></span>

### <span data-ttu-id="81725-144">System.String</span><span class="sxs-lookup"><span data-stu-id="81725-144">System.String</span></span>

<span data-ttu-id="81725-145">Vous pouvez diriger le chemin d’accès vers un manifeste de module vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="81725-145">You can pipe the path to a module manifest to this cmdlet.</span></span>

## <span data-ttu-id="81725-146">SORTIES</span><span class="sxs-lookup"><span data-stu-id="81725-146">OUTPUTS</span></span>

### <span data-ttu-id="81725-147">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="81725-147">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="81725-148">Cette applet de commande retourne un objet **PSModuleInfo** qui représente le module.</span><span class="sxs-lookup"><span data-stu-id="81725-148">This cmdlet returns a **PSModuleInfo** object that represents the module.</span></span>
<span data-ttu-id="81725-149">Il retourne cet objet même si le manifeste comporte des erreurs.</span><span class="sxs-lookup"><span data-stu-id="81725-149">It returns this object even if the manifest has errors.</span></span>

## <span data-ttu-id="81725-150">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="81725-150">NOTES</span></span>

## <span data-ttu-id="81725-151">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="81725-151">RELATED LINKS</span></span>

[<span data-ttu-id="81725-152">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="81725-152">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="81725-153">Get-Module</span><span class="sxs-lookup"><span data-stu-id="81725-153">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="81725-154">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="81725-154">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="81725-155">New-Module</span><span class="sxs-lookup"><span data-stu-id="81725-155">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="81725-156">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="81725-156">New-ModuleManifest</span></span>](New-ModuleManifest.md)

[<span data-ttu-id="81725-157">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="81725-157">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="81725-158">about_Modules</span><span class="sxs-lookup"><span data-stu-id="81725-158">about_Modules</span></span>](About/about_Modules.md)
