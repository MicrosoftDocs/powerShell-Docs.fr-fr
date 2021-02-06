---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: 2954bbec68b837a73e5365ab6a1e8ecb501d4898
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599011"
---
# <span data-ttu-id="1d8c2-102">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="1d8c2-102">Remove-Module</span></span>

## <span data-ttu-id="1d8c2-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1d8c2-103">SYNOPSIS</span></span>
<span data-ttu-id="1d8c2-104">Supprime des modules de la session active.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-104">Removes modules from the current session.</span></span>

## <span data-ttu-id="1d8c2-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="1d8c2-105">SYNTAX</span></span>

### <span data-ttu-id="1d8c2-106">name</span><span class="sxs-lookup"><span data-stu-id="1d8c2-106">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1d8c2-107">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="1d8c2-107">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1d8c2-108">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="1d8c2-108">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1d8c2-109">Description</span><span class="sxs-lookup"><span data-stu-id="1d8c2-109">DESCRIPTION</span></span>

<span data-ttu-id="1d8c2-110">L'applet de commande **Remove-Module** supprime les membres d'un module, tels que les applets de commande et les fonctions, dans la session active.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-110">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="1d8c2-111">Si le module inclut un assembly (.dll), tous les membres implémentés par l'assembly sont supprimés, mais l'assembly n'est pas déchargé.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-111">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="1d8c2-112">Cette applet de commande ne désinstalle pas le module et ne le supprime pas non plus de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-112">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="1d8c2-113">Elle affecte uniquement la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-113">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="1d8c2-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1d8c2-114">EXAMPLES</span></span>

### <span data-ttu-id="1d8c2-115">Exemple 1 : supprimer un module</span><span class="sxs-lookup"><span data-stu-id="1d8c2-115">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="1d8c2-116">Cette commande supprime le module BitsTransfer de la session active.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-116">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="1d8c2-117">Exemple 2 : supprimer tous les modules</span><span class="sxs-lookup"><span data-stu-id="1d8c2-117">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="1d8c2-118">Cette commande supprime tous les modules de la session active.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-118">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="1d8c2-119">Exemple 3 : supprimer des modules à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="1d8c2-119">Example 3: Remove modules by using the pipeline</span></span>

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

<span data-ttu-id="1d8c2-120">Cette commande supprime les modules BitsTransfer et PSDiagnostics de la session active.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-120">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="1d8c2-121">La commande utilise un opérateur de pipeline (|) pour envoyer les noms de module à **Remove-Module**.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-121">The command uses a pipeline operator (|) to send the module names to **Remove-Module**.</span></span>
<span data-ttu-id="1d8c2-122">Elle utilise le paramètre commun *Verbose* pour obtenir des informations détaillées sur les membres qui sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-122">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="1d8c2-123">Les messages *détaillés* affichent les éléments qui sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-123">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="1d8c2-124">Les messages diffèrent car le module BitsTransfer inclut un assembly qui implémente ses applets de commande et un module imbriqué avec son propre assembly.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-124">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="1d8c2-125">Le module PSDiagnostics inclut un fichier de script de module (.psm1) qui exporte des fonctions.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-125">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="1d8c2-126">Exemple 4 : supprimer un module à l’aide de ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="1d8c2-126">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="1d8c2-127">Cette commande utilise le paramètre *ModuleInfo* pour supprimer le module BitsTransfer.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-127">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="1d8c2-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1d8c2-128">PARAMETERS</span></span>

### <span data-ttu-id="1d8c2-129">-Force</span><span class="sxs-lookup"><span data-stu-id="1d8c2-129">-Force</span></span>

<span data-ttu-id="1d8c2-130">Indique que cette applet de commande supprime les modules en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-130">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="1d8c2-131">Par défaut, **Remove-Module** supprime uniquement les modules en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-131">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="1d8c2-132">Les valeurs **ReadOnly** et **ReadWrite** sont stockées dans la propriété **AccessMode** d'un module.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-132">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="1d8c2-133">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="1d8c2-133">-FullyQualifiedName</span></span>

<span data-ttu-id="1d8c2-134">Spécifie les noms complets des modules à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-134">Specifies the fully qualified names of modules to remove.</span></span>

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

### <span data-ttu-id="1d8c2-135">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="1d8c2-135">-ModuleInfo</span></span>

<span data-ttu-id="1d8c2-136">Spécifie les objets de module à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-136">Specifies the module objects to remove.</span></span>
<span data-ttu-id="1d8c2-137">Entrez une variable qui contient un objet de module (**PSModuleInfo**) ou une commande qui obtient un objet de module, tel qu’une commande Get-Module.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-137">Enter a variable that contains a module object (**PSModuleInfo**) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="1d8c2-138">Vous pouvez également diriger les objets vers **Remove-Module**.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-138">You can also pipe module objects to **Remove-Module**.</span></span>

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

### <span data-ttu-id="1d8c2-139">-Name</span><span class="sxs-lookup"><span data-stu-id="1d8c2-139">-Name</span></span>

<span data-ttu-id="1d8c2-140">Spécifie les noms des modules à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-140">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="1d8c2-141">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-141">Wildcard characters are permitted.</span></span>
<span data-ttu-id="1d8c2-142">Vous pouvez également diriger les chaînes de nom vers **Remove-Module**.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-142">You can also pipe name strings to **Remove-Module**.</span></span>

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

### <span data-ttu-id="1d8c2-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1d8c2-143">-Confirm</span></span>

<span data-ttu-id="1d8c2-144">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1d8c2-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1d8c2-145">-WhatIf</span></span>

<span data-ttu-id="1d8c2-146">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-146">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1d8c2-147">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1d8c2-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1d8c2-148">CommonParameters</span></span>

<span data-ttu-id="1d8c2-149">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1d8c2-150">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1d8c2-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1d8c2-151">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1d8c2-151">INPUTS</span></span>

### <span data-ttu-id="1d8c2-152">System. String, System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="1d8c2-152">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="1d8c2-153">Vous pouvez diriger les noms de module et les objets de module vers **Remove-Module**.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-153">You can pipe module names and module objects to **Remove-Module**.</span></span>

## <span data-ttu-id="1d8c2-154">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1d8c2-154">OUTPUTS</span></span>

### <span data-ttu-id="1d8c2-155">None</span><span class="sxs-lookup"><span data-stu-id="1d8c2-155">None</span></span>

<span data-ttu-id="1d8c2-156">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-156">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1d8c2-157">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1d8c2-157">NOTES</span></span>

<span data-ttu-id="1d8c2-158">Lors de la suppression d’un module, il existe un événement sur le module qui s’exécutera.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-158">When removing a module, there is an event on the module that will execute.</span></span>
<span data-ttu-id="1d8c2-159">Cet événement permet à un module de réagir en cours de suppression et d’effectuer un nettoyage, par exemple la libération de ressources.</span><span class="sxs-lookup"><span data-stu-id="1d8c2-159">This event allows a module to react to being removed and perform some cleanup such as freeing up resources.</span></span> <span data-ttu-id="1d8c2-160">Exemple :</span><span class="sxs-lookup"><span data-stu-id="1d8c2-160">Example:</span></span>

<span data-ttu-id="1d8c2-161">$OnRemoveScript = {</span><span class="sxs-lookup"><span data-stu-id="1d8c2-161">$OnRemoveScript = {</span></span>

  <span data-ttu-id="1d8c2-162">\# effectuer un nettoyage</span><span class="sxs-lookup"><span data-stu-id="1d8c2-162">\# perform cleanup</span></span>

  <span data-ttu-id="1d8c2-163">$cachedSessions | Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="1d8c2-163">$cachedSessions | Remove-PSSession</span></span>

<span data-ttu-id="1d8c2-164">}</span><span class="sxs-lookup"><span data-stu-id="1d8c2-164">}</span></span>

<span data-ttu-id="1d8c2-165">$ExecutionContext. SessionState. module. OnRemove + = $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="1d8c2-165">$ExecutionContext.SessionState.Module.OnRemove += $OnRemoveScript</span></span>

<span data-ttu-id="1d8c2-166">Pour une cohérence totale, il peut être également utile de réagir à la fermeture du processus PowerShell :</span><span class="sxs-lookup"><span data-stu-id="1d8c2-166">For full consistency, it might be also useful to react to the closing of the PowerShell process:</span></span>

<span data-ttu-id="1d8c2-167">Register-EngineEvent-SourceIdentifier ([System. Management. Automation. PsEngineEvent] :: sortie)-action $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="1d8c2-167">Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Action $OnRemoveScript</span></span>

## <span data-ttu-id="1d8c2-168">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1d8c2-168">RELATED LINKS</span></span>

[<span data-ttu-id="1d8c2-169">Get-Module</span><span class="sxs-lookup"><span data-stu-id="1d8c2-169">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="1d8c2-170">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="1d8c2-170">Import-Module</span></span>](Import-Module.md)

