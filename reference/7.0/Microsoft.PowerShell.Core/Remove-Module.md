---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: b8577db1d44f0e7bd4571a080133fecaa282770b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201482"
---
# <span data-ttu-id="d8da4-103">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="d8da4-103">Remove-Module</span></span>

## <span data-ttu-id="d8da4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d8da4-104">SYNOPSIS</span></span>
<span data-ttu-id="d8da4-105">Supprime des modules de la session active.</span><span class="sxs-lookup"><span data-stu-id="d8da4-105">Removes modules from the current session.</span></span>

## <span data-ttu-id="d8da4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8da4-106">SYNTAX</span></span>

### <span data-ttu-id="d8da4-107">name</span><span class="sxs-lookup"><span data-stu-id="d8da4-107">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d8da4-108">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="d8da4-108">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d8da4-109">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="d8da4-109">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d8da4-110">Description</span><span class="sxs-lookup"><span data-stu-id="d8da4-110">DESCRIPTION</span></span>

<span data-ttu-id="d8da4-111">L'applet de commande **Remove-Module** supprime les membres d'un module, tels que les applets de commande et les fonctions, dans la session active.</span><span class="sxs-lookup"><span data-stu-id="d8da4-111">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="d8da4-112">Si le module inclut un assembly (.dll), tous les membres implémentés par l'assembly sont supprimés, mais l'assembly n'est pas déchargé.</span><span class="sxs-lookup"><span data-stu-id="d8da4-112">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="d8da4-113">Cette applet de commande ne désinstalle pas le module et ne le supprime pas non plus de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d8da4-113">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="d8da4-114">Elle affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="d8da4-114">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="d8da4-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d8da4-115">EXAMPLES</span></span>

### <span data-ttu-id="d8da4-116">Exemple 1 : supprimer un module</span><span class="sxs-lookup"><span data-stu-id="d8da4-116">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="d8da4-117">Cette commande supprime le module BitsTransfer de la session active.</span><span class="sxs-lookup"><span data-stu-id="d8da4-117">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="d8da4-118">Exemple 2 : supprimer tous les modules</span><span class="sxs-lookup"><span data-stu-id="d8da4-118">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="d8da4-119">Cette commande supprime tous les modules de la session active.</span><span class="sxs-lookup"><span data-stu-id="d8da4-119">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="d8da4-120">Exemple 3 : supprimer des modules à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="d8da4-120">Example 3: Remove modules by using the pipeline</span></span>

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

<span data-ttu-id="d8da4-121">Cette commande supprime les modules BitsTransfer et PSDiagnostics de la session active.</span><span class="sxs-lookup"><span data-stu-id="d8da4-121">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="d8da4-122">La commande utilise un opérateur de pipeline (|) pour envoyer les noms de module à **Remove-Module** .</span><span class="sxs-lookup"><span data-stu-id="d8da4-122">The command uses a pipeline operator (|) to send the module names to **Remove-Module** .</span></span>
<span data-ttu-id="d8da4-123">Elle utilise le paramètre commun *Verbose* pour obtenir des informations détaillées sur les membres qui sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="d8da4-123">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="d8da4-124">Les messages *détaillés* affichent les éléments qui sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="d8da4-124">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="d8da4-125">Les messages diffèrent car le module BitsTransfer inclut un assembly qui implémente ses applets de commande et un module imbriqué avec son propre assembly.</span><span class="sxs-lookup"><span data-stu-id="d8da4-125">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="d8da4-126">Le module PSDiagnostics inclut un fichier de script de module (.psm1) qui exporte des fonctions.</span><span class="sxs-lookup"><span data-stu-id="d8da4-126">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="d8da4-127">Exemple 4 : supprimer un module à l’aide de ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="d8da4-127">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="d8da4-128">Cette commande utilise le paramètre *ModuleInfo* pour supprimer le module BitsTransfer.</span><span class="sxs-lookup"><span data-stu-id="d8da4-128">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="d8da4-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8da4-129">PARAMETERS</span></span>

### <span data-ttu-id="d8da4-130">-Force</span><span class="sxs-lookup"><span data-stu-id="d8da4-130">-Force</span></span>

<span data-ttu-id="d8da4-131">Indique que cette applet de commande supprime les modules en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="d8da4-131">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="d8da4-132">Par défaut, **Remove-Module** supprime uniquement les modules en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="d8da4-132">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="d8da4-133">Les valeurs **ReadOnly** et **ReadWrite** sont stockées dans la propriété **AccessMode** d'un module.</span><span class="sxs-lookup"><span data-stu-id="d8da4-133">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="d8da4-134">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="d8da4-134">-FullyQualifiedName</span></span>

<span data-ttu-id="d8da4-135">Spécifie les noms complets des modules à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d8da4-135">Specifies the fully qualified names of modules to remove.</span></span>

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

### <span data-ttu-id="d8da4-136">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="d8da4-136">-ModuleInfo</span></span>

<span data-ttu-id="d8da4-137">Spécifie les objets de module à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d8da4-137">Specifies the module objects to remove.</span></span>
<span data-ttu-id="d8da4-138">Entrez une variable qui contient un objet de module ( **PSModuleInfo** ) ou une commande qui obtient un objet de module, tel qu’une commande Get-Module.</span><span class="sxs-lookup"><span data-stu-id="d8da4-138">Enter a variable that contains a module object ( **PSModuleInfo** ) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="d8da4-139">Vous pouvez également diriger les objets vers **Remove-Module** .</span><span class="sxs-lookup"><span data-stu-id="d8da4-139">You can also pipe module objects to **Remove-Module** .</span></span>

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

### <span data-ttu-id="d8da4-140">-Name</span><span class="sxs-lookup"><span data-stu-id="d8da4-140">-Name</span></span>

<span data-ttu-id="d8da4-141">Spécifie les noms des modules à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d8da4-141">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="d8da4-142">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d8da4-142">Wildcard characters are permitted.</span></span>
<span data-ttu-id="d8da4-143">Vous pouvez également diriger les chaînes de nom vers **Remove-Module** .</span><span class="sxs-lookup"><span data-stu-id="d8da4-143">You can also pipe name strings to **Remove-Module** .</span></span>

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

### <span data-ttu-id="d8da4-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d8da4-144">-Confirm</span></span>

<span data-ttu-id="d8da4-145">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8da4-145">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d8da4-146">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d8da4-146">-WhatIf</span></span>

<span data-ttu-id="d8da4-147">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8da4-147">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d8da4-148">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d8da4-148">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d8da4-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8da4-149">CommonParameters</span></span>

<span data-ttu-id="d8da4-150">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d8da4-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8da4-151">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d8da4-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8da4-152">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d8da4-152">INPUTS</span></span>

### <span data-ttu-id="d8da4-153">System. String, System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="d8da4-153">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="d8da4-154">Vous pouvez diriger les noms de module et les objets de module vers **Remove-Module** .</span><span class="sxs-lookup"><span data-stu-id="d8da4-154">You can pipe module names and module objects to **Remove-Module** .</span></span>

## <span data-ttu-id="d8da4-155">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d8da4-155">OUTPUTS</span></span>

### <span data-ttu-id="d8da4-156">Aucun</span><span class="sxs-lookup"><span data-stu-id="d8da4-156">None</span></span>

<span data-ttu-id="d8da4-157">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d8da4-157">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d8da4-158">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d8da4-158">NOTES</span></span>

<span data-ttu-id="d8da4-159">Lors de la suppression d’un module, il existe un événement sur le module qui s’exécutera.</span><span class="sxs-lookup"><span data-stu-id="d8da4-159">When removing a module, there is an event on the module that will execute.</span></span>
<span data-ttu-id="d8da4-160">Cet événement permet à un module de réagir en cours de suppression et d’effectuer un nettoyage, par exemple la libération de ressources.</span><span class="sxs-lookup"><span data-stu-id="d8da4-160">This event allows a module to react to being removed and perform some cleanup such as freeing up resources.</span></span> <span data-ttu-id="d8da4-161">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d8da4-161">Example:</span></span>

<span data-ttu-id="d8da4-162">$OnRemoveScript = {</span><span class="sxs-lookup"><span data-stu-id="d8da4-162">$OnRemoveScript = {</span></span>

  <span data-ttu-id="d8da4-163">\# effectuer un nettoyage</span><span class="sxs-lookup"><span data-stu-id="d8da4-163">\# perform cleanup</span></span>

  <span data-ttu-id="d8da4-164">$cachedSessions | Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="d8da4-164">$cachedSessions | Remove-PSSession</span></span>

<span data-ttu-id="d8da4-165">}</span><span class="sxs-lookup"><span data-stu-id="d8da4-165">}</span></span>

<span data-ttu-id="d8da4-166">$ExecutionContext. SessionState. module. OnRemove + = $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="d8da4-166">$ExecutionContext.SessionState.Module.OnRemove += $OnRemoveScript</span></span>

<span data-ttu-id="d8da4-167">Pour une cohérence totale, il peut être également utile de réagir à la fermeture du processus PowerShell :</span><span class="sxs-lookup"><span data-stu-id="d8da4-167">For full consistency, it might be also useful to react to the closing of the PowerShell process:</span></span>

<span data-ttu-id="d8da4-168">Register-EngineEvent-SourceIdentifier ([System. Management. Automation. PsEngineEvent] :: sortie)-action $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="d8da4-168">Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Action $OnRemoveScript</span></span>

## <span data-ttu-id="d8da4-169">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d8da4-169">RELATED LINKS</span></span>

[<span data-ttu-id="d8da4-170">Get-Module</span><span class="sxs-lookup"><span data-stu-id="d8da4-170">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="d8da4-171">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="d8da4-171">Import-Module</span></span>](Import-Module.md)
