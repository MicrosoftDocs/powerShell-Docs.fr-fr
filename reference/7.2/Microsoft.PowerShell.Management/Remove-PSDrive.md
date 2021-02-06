---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: d20a348f3f5ba193eb85e0f9d0e2cc11ad083b47
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597551"
---
# <span data-ttu-id="1086f-102">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="1086f-102">Remove-PSDrive</span></span>

## <span data-ttu-id="1086f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1086f-103">SYNOPSIS</span></span>
<span data-ttu-id="1086f-104">Supprime les lecteurs PowerShell temporaires et déconnecte les lecteurs réseau mappés.</span><span class="sxs-lookup"><span data-stu-id="1086f-104">Deletes temporary PowerShell drives and disconnects mapped network drives.</span></span>

## <span data-ttu-id="1086f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="1086f-105">SYNTAX</span></span>

### <span data-ttu-id="1086f-106">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="1086f-106">Name (Default)</span></span>

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1086f-107">LiteralName</span><span class="sxs-lookup"><span data-stu-id="1086f-107">LiteralName</span></span>

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1086f-108">Description</span><span class="sxs-lookup"><span data-stu-id="1086f-108">DESCRIPTION</span></span>

<span data-ttu-id="1086f-109">L' `Remove-PSDrive` applet de commande supprime les lecteurs PowerShell temporaires qui ont été créés à l’aide de l’applet de commande `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="1086f-109">The `Remove-PSDrive` cmdlet deletes temporary PowerShell drives that were created by using the `New-PSDrive` cmdlet.</span></span>

<span data-ttu-id="1086f-110">À compter de Windows PowerShell 3,0, `Remove-PSDrive` déconnecte également les lecteurs réseau mappés, y compris, mais sans s’y limiter, les lecteurs créés à l’aide du `Persist` paramètre de `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="1086f-110">Beginning in Windows PowerShell 3.0, `Remove-PSDrive` also disconnects mapped network drives, including, but not limited to, drives created by using the `Persist` parameter of `New-PSDrive`.</span></span>

<span data-ttu-id="1086f-111">`Remove-PSDrive` Impossible de supprimer les lecteurs physiques ou logiques Windows.</span><span class="sxs-lookup"><span data-stu-id="1086f-111">`Remove-PSDrive` cannot delete Windows physical or logical drives.</span></span>

<span data-ttu-id="1086f-112">À compter de Windows PowerShell 3,0, lorsqu’un lecteur externe est connecté à l’ordinateur, PowerShell ajoute automatiquement un PSDrive au système de fichiers qui représente le nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="1086f-112">Beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="1086f-113">Vous n’avez pas besoin de redémarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1086f-113">You do not need to restart PowerShell.</span></span>
<span data-ttu-id="1086f-114">De même, lorsqu’un lecteur externe est déconnecté de l’ordinateur, PowerShell supprime automatiquement le PSDrive qui représente le lecteur supprimé.</span><span class="sxs-lookup"><span data-stu-id="1086f-114">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="1086f-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1086f-115">EXAMPLES</span></span>

### <span data-ttu-id="1086f-116">Exemple 1 : supprimer un lecteur du système de fichiers</span><span class="sxs-lookup"><span data-stu-id="1086f-116">Example 1: Remove a file system drive</span></span>

<span data-ttu-id="1086f-117">Cette commande supprime un lecteur de système de fichiers temporaire nommé « smp ».</span><span class="sxs-lookup"><span data-stu-id="1086f-117">This command removes a temporary file system drive named "smp".</span></span>

```powershell
Remove-PSDrive -Name smp
```

### <span data-ttu-id="1086f-118">Exemple 2 : supprimer les lecteurs réseau mappés</span><span class="sxs-lookup"><span data-stu-id="1086f-118">Example 2: Remove mapped network drives</span></span>

<span data-ttu-id="1086f-119">Cette commande utilise `Remove-PSDrive` pour déconnecter les lecteurs réseau mappés X : et S :.</span><span class="sxs-lookup"><span data-stu-id="1086f-119">This command uses `Remove-PSDrive` to disconnect the X: and S: mapped network drives.</span></span>

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## <span data-ttu-id="1086f-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1086f-120">PARAMETERS</span></span>

### <span data-ttu-id="1086f-121">-Force</span><span class="sxs-lookup"><span data-stu-id="1086f-121">-Force</span></span>

<span data-ttu-id="1086f-122">Supprime le lecteur PowerShell actuel.</span><span class="sxs-lookup"><span data-stu-id="1086f-122">Removes the current PowerShell drive.</span></span>

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

### <span data-ttu-id="1086f-123">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="1086f-123">-LiteralName</span></span>

<span data-ttu-id="1086f-124">Spécifie le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="1086f-124">Specifies the name of the drive.</span></span>

<span data-ttu-id="1086f-125">La valeur de **LiteralName** est utilisée exactement comme elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="1086f-125">The value of **LiteralName** is used exactly as typed.</span></span>
<span data-ttu-id="1086f-126">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="1086f-126">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="1086f-127">Si le nom inclut des caractères d’échappement, entourez-le de guillemets simples (’).</span><span class="sxs-lookup"><span data-stu-id="1086f-127">If the name includes escape characters, enclose it in single quotation marks (').</span></span>
<span data-ttu-id="1086f-128">Les guillemets simples indiquent à PowerShell qu’aucun caractère n’est interprété comme séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="1086f-128">Single quotation marks instruct PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="1086f-129">-Name</span><span class="sxs-lookup"><span data-stu-id="1086f-129">-Name</span></span>

<span data-ttu-id="1086f-130">Spécifie les noms des lecteurs à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1086f-130">Specifies the names of the drives to remove.</span></span>
<span data-ttu-id="1086f-131">Ne tapez pas le signe deux-points (:) après le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="1086f-131">Do not type a colon (:) after the drive name.</span></span>

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

### <span data-ttu-id="1086f-132">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="1086f-132">-PSProvider</span></span>

<span data-ttu-id="1086f-133">Spécifie un tableau d’objets **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="1086f-133">Specifies an array of **PSProvider** objects.</span></span>
<span data-ttu-id="1086f-134">Cette applet de commande supprime et déconnecte tous les lecteurs associés au fournisseur PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="1086f-134">This cmdlet removes and disconnects all of the drives associated with the specified PowerShell provider.</span></span>

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

### <span data-ttu-id="1086f-135">-Étendue</span><span class="sxs-lookup"><span data-stu-id="1086f-135">-Scope</span></span>

<span data-ttu-id="1086f-136">Spécifie une portée pour le lecteur.</span><span class="sxs-lookup"><span data-stu-id="1086f-136">Specifies a scope for the drive.</span></span>
<span data-ttu-id="1086f-137">Les valeurs acceptables pour ce paramètre sont : global, local et script, ou un nombre relatif à l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="1086f-137">The acceptable values for this parameter are: Global, Local, and Script, or a number relative to the current scope.</span></span> <span data-ttu-id="1086f-138">Les étendues numéro 0 à travers le nombre d’étendues.</span><span class="sxs-lookup"><span data-stu-id="1086f-138">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="1086f-139">Le numéro d’étendue actuel est 0 et son parent est 1.</span><span class="sxs-lookup"><span data-stu-id="1086f-139">The current scope number is 0 and its parent is 1.</span></span>
<span data-ttu-id="1086f-140">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="1086f-140">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="1086f-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1086f-141">-Confirm</span></span>

<span data-ttu-id="1086f-142">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1086f-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1086f-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1086f-143">-WhatIf</span></span>

<span data-ttu-id="1086f-144">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1086f-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1086f-145">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="1086f-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1086f-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1086f-146">CommonParameters</span></span>

<span data-ttu-id="1086f-147">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1086f-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1086f-148">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="1086f-148">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1086f-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1086f-149">INPUTS</span></span>

### <span data-ttu-id="1086f-150">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="1086f-150">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="1086f-151">Vous pouvez diriger un objet lecteur, tel que celui de l' `Get-PSDrive` applet de commande, vers l’applet de commande `Remove-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="1086f-151">You can pipe a drive object, such as one from the `Get-PSDrive` cmdlet, to the `Remove-PSDrive` cmdlet.</span></span>

## <span data-ttu-id="1086f-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1086f-152">OUTPUTS</span></span>

### <span data-ttu-id="1086f-153">None</span><span class="sxs-lookup"><span data-stu-id="1086f-153">None</span></span>

<span data-ttu-id="1086f-154">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1086f-154">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="1086f-155">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1086f-155">NOTES</span></span>

- <span data-ttu-id="1086f-156">L' `Remove-PSDrive` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1086f-156">The `Remove-PSDrive` cmdlet is designed to work with the data exposed by any PowerShell provider.</span></span> <span data-ttu-id="1086f-157">Pour répertorier les fournisseurs disponibles dans votre session, utilisez l’applet de commande `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="1086f-157">To list the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="1086f-158">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="1086f-158">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="1086f-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1086f-159">RELATED LINKS</span></span>

[<span data-ttu-id="1086f-160">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="1086f-160">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="1086f-161">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="1086f-161">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="1086f-162">about_Providers</span><span class="sxs-lookup"><span data-stu-id="1086f-162">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

