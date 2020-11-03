---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 7406b2cac771ae7a741af92cd362cce834c59a50
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203665"
---
# <span data-ttu-id="426f8-103">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="426f8-103">Remove-Alias</span></span>

## <span data-ttu-id="426f8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="426f8-104">SYNOPSIS</span></span>
<span data-ttu-id="426f8-105">Supprimer un alias de la session active.</span><span class="sxs-lookup"><span data-stu-id="426f8-105">Remove an alias from the current session.</span></span>

## <span data-ttu-id="426f8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="426f8-106">SYNTAX</span></span>

### <span data-ttu-id="426f8-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="426f8-107">Default (Default)</span></span>

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="426f8-108">Description</span><span class="sxs-lookup"><span data-stu-id="426f8-108">DESCRIPTION</span></span>

<span data-ttu-id="426f8-109">L' `Remove-Alias` applet de commande supprime un alias de la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="426f8-109">The `Remove-Alias` cmdlet removes an alias from the current PowerShell session.</span></span> <span data-ttu-id="426f8-110">Pour supprimer un alias avec la propriété **option** définie sur **ReadOnly** , utilisez le paramètre **force** .</span><span class="sxs-lookup"><span data-stu-id="426f8-110">To remove an alias with the **Option** property set to **ReadOnly** , use the **Force** parameter.</span></span>

<span data-ttu-id="426f8-111">L' `Remove-Alias` applet de commande a été introduite dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="426f8-111">The `Remove-Alias` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="426f8-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="426f8-112">EXAMPLES</span></span>

### <span data-ttu-id="426f8-113">Exemple 1 : supprimer un alias</span><span class="sxs-lookup"><span data-stu-id="426f8-113">Example 1 - Remove an alias</span></span>

<span data-ttu-id="426f8-114">Cet exemple supprime un alias nommé `del` qui représente l' `Remove-Item` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="426f8-114">This example removes an alias named `del` that represents the `Remove-Item` cmdlet.</span></span>

```powershell
Remove-Alias -Name del
```

### <span data-ttu-id="426f8-115">Exemple 2 : supprimer tous les alias non constants</span><span class="sxs-lookup"><span data-stu-id="426f8-115">Example 2 - Remove all non-Constant aliases</span></span>

<span data-ttu-id="426f8-116">Cet exemple supprime tous les alias de la session PowerShell active, à l’exception des alias dont la propriété **options** a la valeur **constant** .</span><span class="sxs-lookup"><span data-stu-id="426f8-116">This example removes all aliases from the current PowerShell session, except for aliases with the **Options** property set to **Constant** .</span></span> <span data-ttu-id="426f8-117">Une fois la commande exécutée, les alias sont disponibles dans d’autres sessions PowerShell ou dans de nouvelles sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="426f8-117">After the command is run, the aliases are available in other PowerShell sessions or new PowerShell sessions.</span></span>

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

<span data-ttu-id="426f8-118">`Get-Alias` Obtient tous les alias dans la session PowerShell et envoie les objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="426f8-118">`Get-Alias` gets all the aliases in the PowerShell session and sends the objects down the pipeline.</span></span>
<span data-ttu-id="426f8-119">`Where-Object` utilise un bloc de script, et la propriété automatique variable ( `$_` ) et **options** représente l’objet de pipeline actuel.</span><span class="sxs-lookup"><span data-stu-id="426f8-119">`Where-Object` uses a script block, and the automatic variable (`$_`) and **Options** property represent the current pipeline object.</span></span> <span data-ttu-id="426f8-120">Le paramètre **ne** (pas égal à), sélectionne les objets qui n’ont pas de valeur d' **option** définie sur **constant** .</span><span class="sxs-lookup"><span data-stu-id="426f8-120">The parameter **NE** (not equal), selects objects that don't have an **Options** value set to **Constant** .</span></span> <span data-ttu-id="426f8-121">`Remove-Alias` utilise le paramètre **force** pour supprimer des alias, y compris des alias en lecture seule, à partir de la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="426f8-121">`Remove-Alias` uses the **Force** parameter to remove aliases, including read-only aliases, from the PowerShell session.</span></span>

## <span data-ttu-id="426f8-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="426f8-122">PARAMETERS</span></span>

### <span data-ttu-id="426f8-123">-Force</span><span class="sxs-lookup"><span data-stu-id="426f8-123">-Force</span></span>

<span data-ttu-id="426f8-124">Indique que l’applet de commande supprime un alias, y compris les alias avec la propriété **option** définie sur **ReadOnly** .</span><span class="sxs-lookup"><span data-stu-id="426f8-124">Indicates that the cmdlet removes an alias, including aliases with the **Option** property set to **ReadOnly** .</span></span> <span data-ttu-id="426f8-125">Le paramètre **force** ne peut pas supprimer un alias avec une propriété **option** définie sur **constant** .</span><span class="sxs-lookup"><span data-stu-id="426f8-125">The **Force** parameter can't remove an alias with an **Option** property set to **Constant** .</span></span>

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

### <span data-ttu-id="426f8-126">-Name</span><span class="sxs-lookup"><span data-stu-id="426f8-126">-Name</span></span>

<span data-ttu-id="426f8-127">Spécifie le nom de l’alias à supprimer.</span><span class="sxs-lookup"><span data-stu-id="426f8-127">Specifies the name of the alias to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="426f8-128">-Étendue</span><span class="sxs-lookup"><span data-stu-id="426f8-128">-Scope</span></span>

<span data-ttu-id="426f8-129">Affecte uniquement les alias dans l’étendue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="426f8-129">Affects only the aliases in the specified scope.</span></span> <span data-ttu-id="426f8-130">La portée par défaut est **local** .</span><span class="sxs-lookup"><span data-stu-id="426f8-130">The default scope is **Local** .</span></span> <span data-ttu-id="426f8-131">Pour plus d’informations, consultez [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span><span class="sxs-lookup"><span data-stu-id="426f8-131">For more information, see [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span></span>

<span data-ttu-id="426f8-132">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="426f8-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="426f8-133">Global</span><span class="sxs-lookup"><span data-stu-id="426f8-133">Global</span></span>
- <span data-ttu-id="426f8-134">Local</span><span class="sxs-lookup"><span data-stu-id="426f8-134">Local</span></span>
- <span data-ttu-id="426f8-135">Script</span><span class="sxs-lookup"><span data-stu-id="426f8-135">Script</span></span>
- <span data-ttu-id="426f8-136">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)</span><span class="sxs-lookup"><span data-stu-id="426f8-136">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="426f8-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="426f8-137">CommonParameters</span></span>

<span data-ttu-id="426f8-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="426f8-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="426f8-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="426f8-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="426f8-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="426f8-140">INPUTS</span></span>

### <span data-ttu-id="426f8-141">System.String[]</span><span class="sxs-lookup"><span data-stu-id="426f8-141">System.String[]</span></span>

<span data-ttu-id="426f8-142">Vous pouvez diriger un objet alias vers **Remove-alias** .</span><span class="sxs-lookup"><span data-stu-id="426f8-142">You can pipe an alias object to **Remove-Alias** .</span></span>

## <span data-ttu-id="426f8-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="426f8-143">OUTPUTS</span></span>

### <span data-ttu-id="426f8-144">Aucun</span><span class="sxs-lookup"><span data-stu-id="426f8-144">None</span></span>

<span data-ttu-id="426f8-145">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="426f8-145">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="426f8-146">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="426f8-146">NOTES</span></span>

<span data-ttu-id="426f8-147">Les modifications affectent uniquement l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="426f8-147">Changes only affect the current scope.</span></span> <span data-ttu-id="426f8-148">Pour supprimer un alias de toutes les sessions, ajoutez une commande **Remove-alias** à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="426f8-148">To remove an alias from all sessions, add a **Remove-Alias** command to your PowerShell profile.</span></span>

<span data-ttu-id="426f8-149">Pour plus d’informations, consultez [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span><span class="sxs-lookup"><span data-stu-id="426f8-149">For more information, see [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span></span>

## <span data-ttu-id="426f8-150">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="426f8-150">RELATED LINKS</span></span>

[<span data-ttu-id="426f8-151">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="426f8-151">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="426f8-152">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="426f8-152">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="426f8-153">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="426f8-153">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="426f8-154">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="426f8-154">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="426f8-155">New-Alias</span><span class="sxs-lookup"><span data-stu-id="426f8-155">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="426f8-156">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="426f8-156">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="426f8-157">Where-Object</span><span class="sxs-lookup"><span data-stu-id="426f8-157">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

