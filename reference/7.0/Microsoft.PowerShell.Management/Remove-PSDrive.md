---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: 2b5508899b61ac5460c5ce06aa7521be50c0f2d4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201165"
---
# <span data-ttu-id="32875-103">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="32875-103">Remove-PSDrive</span></span>

## <span data-ttu-id="32875-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="32875-104">SYNOPSIS</span></span>
<span data-ttu-id="32875-105">Supprime les lecteurs PowerShell temporaires et déconnecte les lecteurs réseau mappés.</span><span class="sxs-lookup"><span data-stu-id="32875-105">Deletes temporary PowerShell drives and disconnects mapped network drives.</span></span>

## <span data-ttu-id="32875-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="32875-106">SYNTAX</span></span>

### <span data-ttu-id="32875-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="32875-107">Name (Default)</span></span>

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="32875-108">LiteralName</span><span class="sxs-lookup"><span data-stu-id="32875-108">LiteralName</span></span>

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="32875-109">Description</span><span class="sxs-lookup"><span data-stu-id="32875-109">DESCRIPTION</span></span>

<span data-ttu-id="32875-110">L' `Remove-PSDrive` applet de commande supprime les lecteurs PowerShell temporaires qui ont été créés à l’aide de l’applet de commande `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="32875-110">The `Remove-PSDrive` cmdlet deletes temporary PowerShell drives that were created by using the `New-PSDrive` cmdlet.</span></span>

<span data-ttu-id="32875-111">À compter de Windows PowerShell 3,0, `Remove-PSDrive` déconnecte également les lecteurs réseau mappés, y compris, mais sans s’y limiter, les lecteurs créés à l’aide du `Persist` paramètre de `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="32875-111">Beginning in Windows PowerShell 3.0, `Remove-PSDrive` also disconnects mapped network drives, including, but not limited to, drives created by using the `Persist` parameter of `New-PSDrive`.</span></span>

<span data-ttu-id="32875-112">`Remove-PSDrive` Impossible de supprimer les lecteurs physiques ou logiques Windows.</span><span class="sxs-lookup"><span data-stu-id="32875-112">`Remove-PSDrive` cannot delete Windows physical or logical drives.</span></span>

<span data-ttu-id="32875-113">À compter de Windows PowerShell 3,0, lorsqu’un lecteur externe est connecté à l’ordinateur, PowerShell ajoute automatiquement un PSDrive au système de fichiers qui représente le nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="32875-113">Beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="32875-114">Vous n’avez pas besoin de redémarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32875-114">You do not need to restart PowerShell.</span></span>
<span data-ttu-id="32875-115">De même, lorsqu’un lecteur externe est déconnecté de l’ordinateur, PowerShell supprime automatiquement le PSDrive qui représente le lecteur supprimé.</span><span class="sxs-lookup"><span data-stu-id="32875-115">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="32875-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="32875-116">EXAMPLES</span></span>

### <span data-ttu-id="32875-117">Exemple 1 : supprimer un lecteur du système de fichiers</span><span class="sxs-lookup"><span data-stu-id="32875-117">Example 1: Remove a file system drive</span></span>

<span data-ttu-id="32875-118">Cette commande supprime un lecteur de système de fichiers temporaire nommé « smp ».</span><span class="sxs-lookup"><span data-stu-id="32875-118">This command removes a temporary file system drive named "smp".</span></span>

```powershell
Remove-PSDrive -Name smp
```

### <span data-ttu-id="32875-119">Exemple 2 : supprimer les lecteurs réseau mappés</span><span class="sxs-lookup"><span data-stu-id="32875-119">Example 2: Remove mapped network drives</span></span>

<span data-ttu-id="32875-120">Cette commande utilise `Remove-PSDrive` pour déconnecter les lecteurs réseau mappés X : et S :.</span><span class="sxs-lookup"><span data-stu-id="32875-120">This command uses `Remove-PSDrive` to disconnect the X: and S: mapped network drives.</span></span>

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## <span data-ttu-id="32875-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32875-121">PARAMETERS</span></span>

### <span data-ttu-id="32875-122">-Force</span><span class="sxs-lookup"><span data-stu-id="32875-122">-Force</span></span>

<span data-ttu-id="32875-123">Supprime le lecteur PowerShell actuel.</span><span class="sxs-lookup"><span data-stu-id="32875-123">Removes the current PowerShell drive.</span></span>

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

### <span data-ttu-id="32875-124">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="32875-124">-LiteralName</span></span>

<span data-ttu-id="32875-125">Spécifie le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="32875-125">Specifies the name of the drive.</span></span>

<span data-ttu-id="32875-126">La valeur de **LiteralName** est utilisée exactement comme elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="32875-126">The value of **LiteralName** is used exactly as typed.</span></span>
<span data-ttu-id="32875-127">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="32875-127">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="32875-128">Si le nom inclut des caractères d’échappement, entourez-le de guillemets simples (’).</span><span class="sxs-lookup"><span data-stu-id="32875-128">If the name includes escape characters, enclose it in single quotation marks (').</span></span>
<span data-ttu-id="32875-129">Les guillemets simples indiquent à PowerShell qu’aucun caractère n’est interprété comme séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="32875-129">Single quotation marks instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32875-130">-Name</span><span class="sxs-lookup"><span data-stu-id="32875-130">-Name</span></span>

<span data-ttu-id="32875-131">Spécifie les noms des lecteurs à supprimer.</span><span class="sxs-lookup"><span data-stu-id="32875-131">Specifies the names of the drives to remove.</span></span>
<span data-ttu-id="32875-132">Ne tapez pas le signe deux-points (:) après le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="32875-132">Do not type a colon (:) after the drive name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="32875-133">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="32875-133">-PSProvider</span></span>

<span data-ttu-id="32875-134">Spécifie un tableau d’objets **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="32875-134">Specifies an array of **PSProvider** objects.</span></span>
<span data-ttu-id="32875-135">Cette applet de commande supprime et déconnecte tous les lecteurs associés au fournisseur PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="32875-135">This cmdlet removes and disconnects all of the drives associated with the specified PowerShell provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32875-136">-Étendue</span><span class="sxs-lookup"><span data-stu-id="32875-136">-Scope</span></span>

<span data-ttu-id="32875-137">Spécifie une portée pour le lecteur.</span><span class="sxs-lookup"><span data-stu-id="32875-137">Specifies a scope for the drive.</span></span>
<span data-ttu-id="32875-138">Les valeurs acceptables pour ce paramètre sont : global, local et script, ou un nombre relatif à l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="32875-138">The acceptable values for this parameter are: Global, Local, and Script, or a number relative to the current scope.</span></span> <span data-ttu-id="32875-139">Les étendues numéro 0 à travers le nombre d’étendues.</span><span class="sxs-lookup"><span data-stu-id="32875-139">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="32875-140">Le numéro d’étendue actuel est 0 et son parent est 1.</span><span class="sxs-lookup"><span data-stu-id="32875-140">The current scope number is 0 and its parent is 1.</span></span>
<span data-ttu-id="32875-141">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="32875-141">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32875-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="32875-142">-Confirm</span></span>

<span data-ttu-id="32875-143">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="32875-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="32875-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="32875-144">-WhatIf</span></span>

<span data-ttu-id="32875-145">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="32875-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="32875-146">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="32875-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="32875-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32875-147">CommonParameters</span></span>

<span data-ttu-id="32875-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32875-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32875-149">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="32875-149">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="32875-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="32875-150">INPUTS</span></span>

### <span data-ttu-id="32875-151">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="32875-151">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="32875-152">Vous pouvez diriger un objet lecteur, tel que celui de l' `Get-PSDrive` applet de commande, vers l’applet de commande `Remove-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="32875-152">You can pipe a drive object, such as one from the `Get-PSDrive` cmdlet, to the `Remove-PSDrive` cmdlet.</span></span>

## <span data-ttu-id="32875-153">SORTIES</span><span class="sxs-lookup"><span data-stu-id="32875-153">OUTPUTS</span></span>

### <span data-ttu-id="32875-154">Aucun</span><span class="sxs-lookup"><span data-stu-id="32875-154">None</span></span>

<span data-ttu-id="32875-155">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="32875-155">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="32875-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="32875-156">NOTES</span></span>

- <span data-ttu-id="32875-157">L' `Remove-PSDrive` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32875-157">The `Remove-PSDrive` cmdlet is designed to work with the data exposed by any PowerShell provider.</span></span> <span data-ttu-id="32875-158">Pour répertorier les fournisseurs disponibles dans votre session, utilisez l’applet de commande `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="32875-158">To list the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="32875-159">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="32875-159">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="32875-160">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="32875-160">RELATED LINKS</span></span>

[<span data-ttu-id="32875-161">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="32875-161">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="32875-162">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="32875-162">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="32875-163">about_Providers</span><span class="sxs-lookup"><span data-stu-id="32875-163">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
