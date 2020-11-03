---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: a1052c357f19fd8f06eb39a14f8e8eded0c881a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202681"
---
# <span data-ttu-id="c0479-103">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="c0479-103">Remove-Module</span></span>

## <span data-ttu-id="c0479-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c0479-104">SYNOPSIS</span></span>
<span data-ttu-id="c0479-105">Supprime des modules de la session active.</span><span class="sxs-lookup"><span data-stu-id="c0479-105">Removes modules from the current session.</span></span>

## <span data-ttu-id="c0479-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c0479-106">SYNTAX</span></span>

### <span data-ttu-id="c0479-107">name</span><span class="sxs-lookup"><span data-stu-id="c0479-107">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c0479-108">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c0479-108">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c0479-109">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="c0479-109">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c0479-110">Description</span><span class="sxs-lookup"><span data-stu-id="c0479-110">DESCRIPTION</span></span>

<span data-ttu-id="c0479-111">L'applet de commande **Remove-Module** supprime les membres d'un module, tels que les applets de commande et les fonctions, dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c0479-111">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="c0479-112">Si le module inclut un assembly (.dll), tous les membres implémentés par l'assembly sont supprimés, mais l'assembly n'est pas déchargé.</span><span class="sxs-lookup"><span data-stu-id="c0479-112">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="c0479-113">Cette applet de commande ne désinstalle pas le module et ne le supprime pas non plus de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c0479-113">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="c0479-114">Elle affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="c0479-114">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="c0479-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c0479-115">EXAMPLES</span></span>

### <span data-ttu-id="c0479-116">Exemple 1 : supprimer un module</span><span class="sxs-lookup"><span data-stu-id="c0479-116">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="c0479-117">Cette commande supprime le module BitsTransfer de la session active.</span><span class="sxs-lookup"><span data-stu-id="c0479-117">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="c0479-118">Exemple 2 : supprimer tous les modules</span><span class="sxs-lookup"><span data-stu-id="c0479-118">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="c0479-119">Cette commande supprime tous les modules de la session active.</span><span class="sxs-lookup"><span data-stu-id="c0479-119">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="c0479-120">Exemple 3 : supprimer des modules à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="c0479-120">Example 3: Remove modules by using the pipeline</span></span>

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

<span data-ttu-id="c0479-121">Cette commande supprime les modules BitsTransfer et PSDiagnostics de la session active.</span><span class="sxs-lookup"><span data-stu-id="c0479-121">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="c0479-122">La commande utilise un opérateur de pipeline (|) pour envoyer les noms de module à **Remove-Module** .</span><span class="sxs-lookup"><span data-stu-id="c0479-122">The command uses a pipeline operator (|) to send the module names to **Remove-Module** .</span></span>
<span data-ttu-id="c0479-123">Elle utilise le paramètre commun *Verbose* pour obtenir des informations détaillées sur les membres qui sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="c0479-123">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="c0479-124">Les messages *détaillés* affichent les éléments qui sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="c0479-124">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="c0479-125">Les messages diffèrent car le module BitsTransfer inclut un assembly qui implémente ses applets de commande et un module imbriqué avec son propre assembly.</span><span class="sxs-lookup"><span data-stu-id="c0479-125">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="c0479-126">Le module PSDiagnostics inclut un fichier de script de module (.psm1) qui exporte des fonctions.</span><span class="sxs-lookup"><span data-stu-id="c0479-126">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="c0479-127">Exemple 4 : supprimer un module à l’aide de ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="c0479-127">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="c0479-128">Cette commande utilise le paramètre *ModuleInfo* pour supprimer le module BitsTransfer.</span><span class="sxs-lookup"><span data-stu-id="c0479-128">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="c0479-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c0479-129">PARAMETERS</span></span>

### <span data-ttu-id="c0479-130">-Force</span><span class="sxs-lookup"><span data-stu-id="c0479-130">-Force</span></span>

<span data-ttu-id="c0479-131">Indique que cette applet de commande supprime les modules en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="c0479-131">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="c0479-132">Par défaut, **Remove-Module** supprime uniquement les modules en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="c0479-132">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="c0479-133">Les valeurs **ReadOnly** et **ReadWrite** sont stockées dans la propriété **AccessMode** d'un module.</span><span class="sxs-lookup"><span data-stu-id="c0479-133">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="c0479-134">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c0479-134">-FullyQualifiedName</span></span>

<span data-ttu-id="c0479-135">Spécifie les noms complets des modules à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c0479-135">Specifies the fully qualified names of modules to remove.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c0479-136">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="c0479-136">-ModuleInfo</span></span>

<span data-ttu-id="c0479-137">Spécifie les objets de module à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c0479-137">Specifies the module objects to remove.</span></span>
<span data-ttu-id="c0479-138">Entrez une variable qui contient un objet de module ( **PSModuleInfo** ) ou une commande qui obtient un objet de module, tel qu’une commande Get-Module.</span><span class="sxs-lookup"><span data-stu-id="c0479-138">Enter a variable that contains a module object ( **PSModuleInfo** ) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="c0479-139">Vous pouvez également diriger les objets vers **Remove-Module** .</span><span class="sxs-lookup"><span data-stu-id="c0479-139">You can also pipe module objects to **Remove-Module** .</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c0479-140">-Name</span><span class="sxs-lookup"><span data-stu-id="c0479-140">-Name</span></span>

<span data-ttu-id="c0479-141">Spécifie les noms des modules à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c0479-141">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="c0479-142">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c0479-142">Wildcard characters are permitted.</span></span>
<span data-ttu-id="c0479-143">Vous pouvez également diriger les chaînes de nom vers **Remove-Module** .</span><span class="sxs-lookup"><span data-stu-id="c0479-143">You can also pipe name strings to **Remove-Module** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="c0479-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c0479-144">-Confirm</span></span>

<span data-ttu-id="c0479-145">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c0479-145">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c0479-146">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c0479-146">-WhatIf</span></span>

<span data-ttu-id="c0479-147">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c0479-147">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c0479-148">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="c0479-148">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c0479-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0479-149">CommonParameters</span></span>

<span data-ttu-id="c0479-150">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c0479-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0479-151">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c0479-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0479-152">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c0479-152">INPUTS</span></span>

### <span data-ttu-id="c0479-153">System. String, System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="c0479-153">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="c0479-154">Vous pouvez diriger les noms de module et les objets de module vers **Remove-Module** .</span><span class="sxs-lookup"><span data-stu-id="c0479-154">You can pipe module names and module objects to **Remove-Module** .</span></span>

## <span data-ttu-id="c0479-155">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c0479-155">OUTPUTS</span></span>

### <span data-ttu-id="c0479-156">Aucun</span><span class="sxs-lookup"><span data-stu-id="c0479-156">None</span></span>

<span data-ttu-id="c0479-157">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="c0479-157">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c0479-158">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c0479-158">NOTES</span></span>

## <span data-ttu-id="c0479-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c0479-159">RELATED LINKS</span></span>

[<span data-ttu-id="c0479-160">Get-Module</span><span class="sxs-lookup"><span data-stu-id="c0479-160">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="c0479-161">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="c0479-161">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="c0479-162">about_Modules</span><span class="sxs-lookup"><span data-stu-id="c0479-162">about_Modules</span></span>](About/about_Modules.md)
