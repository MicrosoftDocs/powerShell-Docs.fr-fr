---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: 6b9d351b5092d96d7698a28d3de63a493d566c6d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596335"
---
# <span data-ttu-id="c8f16-102">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="c8f16-102">Remove-Variable</span></span>

## <span data-ttu-id="c8f16-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c8f16-103">SYNOPSIS</span></span>
<span data-ttu-id="c8f16-104">Supprime une variable et sa valeur.</span><span class="sxs-lookup"><span data-stu-id="c8f16-104">Deletes a variable and its value.</span></span>

## <span data-ttu-id="c8f16-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c8f16-105">SYNTAX</span></span>

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c8f16-106">Description</span><span class="sxs-lookup"><span data-stu-id="c8f16-106">DESCRIPTION</span></span>

<span data-ttu-id="c8f16-107">L' `Remove-Variable` applet de commande supprime une variable et sa valeur de l’étendue dans laquelle elle est définie, telle que la session active.</span><span class="sxs-lookup"><span data-stu-id="c8f16-107">The `Remove-Variable` cmdlet deletes a variable and its value from the scope in which it is defined, such as the current session.</span></span> <span data-ttu-id="c8f16-108">Vous ne pouvez pas utiliser cette applet de commande pour supprimer des variables qui sont définies en tant que constantes ou celles qui sont détenues par le système.</span><span class="sxs-lookup"><span data-stu-id="c8f16-108">You cannot use this cmdlet to delete variables that are set as constants or those that are owned by the system.</span></span>

## <span data-ttu-id="c8f16-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c8f16-109">EXAMPLES</span></span>

### <span data-ttu-id="c8f16-110">Exemple 1 : supprimer une variable</span><span class="sxs-lookup"><span data-stu-id="c8f16-110">Example 1: Remove a variable</span></span>

```powershell
Remove-Variable Smp
```

<span data-ttu-id="c8f16-111">Cette commande supprime la `$Smp` variable.</span><span class="sxs-lookup"><span data-stu-id="c8f16-111">This command deletes the `$Smp` variable.</span></span>

## <span data-ttu-id="c8f16-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c8f16-112">PARAMETERS</span></span>

### <span data-ttu-id="c8f16-113">-Exclude</span><span class="sxs-lookup"><span data-stu-id="c8f16-113">-Exclude</span></span>

<span data-ttu-id="c8f16-114">Spécifie un tableau d’éléments que cette applet de commande omet de l’opération.</span><span class="sxs-lookup"><span data-stu-id="c8f16-114">Specifies an array of items that this cmdlet omits from the operation.</span></span> <span data-ttu-id="c8f16-115">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="c8f16-115">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="c8f16-116">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="c8f16-116">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="c8f16-117">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c8f16-117">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c8f16-118">-Force</span><span class="sxs-lookup"><span data-stu-id="c8f16-118">-Force</span></span>

<span data-ttu-id="c8f16-119">Indique que l’applet de commande supprime une variable, même si elle est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="c8f16-119">Indicates that the cmdlet removes a variable even if it is read-only.</span></span> <span data-ttu-id="c8f16-120">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas supprimer une constante.</span><span class="sxs-lookup"><span data-stu-id="c8f16-120">Even using the **Force** parameter, the cmdlet cannot remove a constant.</span></span>

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

### <span data-ttu-id="c8f16-121">-Include</span><span class="sxs-lookup"><span data-stu-id="c8f16-121">-Include</span></span>

<span data-ttu-id="c8f16-122">Spécifie un tableau d’éléments que cette applet de commande supprime dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="c8f16-122">Specifies an array of items that this cmdlet deletes in the operation.</span></span> <span data-ttu-id="c8f16-123">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="c8f16-123">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="c8f16-124">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="c8f16-124">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="c8f16-125">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="c8f16-125">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c8f16-126">-Name</span><span class="sxs-lookup"><span data-stu-id="c8f16-126">-Name</span></span>

<span data-ttu-id="c8f16-127">Spécifie le nom de la variable à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c8f16-127">Specifies the name of the variable to be removed.</span></span> <span data-ttu-id="c8f16-128">Le nom du paramètre (**Name**) est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c8f16-128">The parameter name (**Name**) is optional.</span></span>
<span data-ttu-id="c8f16-129">Les caractères génériques sont autorisés</span><span class="sxs-lookup"><span data-stu-id="c8f16-129">Wildcards are permitted</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c8f16-130">-Étendue</span><span class="sxs-lookup"><span data-stu-id="c8f16-130">-Scope</span></span>

<span data-ttu-id="c8f16-131">Obtient seulement les variables de l'étendue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c8f16-131">Gets only the variables in the specified scope.</span></span> <span data-ttu-id="c8f16-132">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c8f16-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c8f16-133">Global</span><span class="sxs-lookup"><span data-stu-id="c8f16-133">Global</span></span>
- <span data-ttu-id="c8f16-134">Local</span><span class="sxs-lookup"><span data-stu-id="c8f16-134">Local</span></span>
- <span data-ttu-id="c8f16-135">Script</span><span class="sxs-lookup"><span data-stu-id="c8f16-135">Script</span></span>
- <span data-ttu-id="c8f16-136">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)</span><span class="sxs-lookup"><span data-stu-id="c8f16-136">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="c8f16-137">Local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c8f16-137">Local is the default.</span></span> <span data-ttu-id="c8f16-138">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="c8f16-138">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8f16-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c8f16-139">-Confirm</span></span>

<span data-ttu-id="c8f16-140">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c8f16-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c8f16-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c8f16-141">-WhatIf</span></span>

<span data-ttu-id="c8f16-142">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c8f16-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="c8f16-143">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="c8f16-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c8f16-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8f16-144">CommonParameters</span></span>

<span data-ttu-id="c8f16-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c8f16-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c8f16-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c8f16-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c8f16-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c8f16-147">INPUTS</span></span>

### <span data-ttu-id="c8f16-148">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="c8f16-148">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="c8f16-149">Vous pouvez diriger un objet de variable vers `Remove-Variable` .</span><span class="sxs-lookup"><span data-stu-id="c8f16-149">You can pipe a variable object to `Remove-Variable`.</span></span>

## <span data-ttu-id="c8f16-150">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c8f16-150">OUTPUTS</span></span>

### <span data-ttu-id="c8f16-151">None</span><span class="sxs-lookup"><span data-stu-id="c8f16-151">None</span></span>

<span data-ttu-id="c8f16-152">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="c8f16-152">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="c8f16-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c8f16-153">NOTES</span></span>

- <span data-ttu-id="c8f16-154">Les modifications affectent uniquement l'étendue actuelle, par exemple une session.</span><span class="sxs-lookup"><span data-stu-id="c8f16-154">Changes affect only the current scope, such as a session.</span></span> <span data-ttu-id="c8f16-155">Pour supprimer une variable de toutes les sessions, ajoutez une `Remove-Variable` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8f16-155">To delete a variable from all sessions, add a `Remove-Variable` command to your PowerShell profile.</span></span>

- <span data-ttu-id="c8f16-156">Vous pouvez également faire référence à `Remove-Variable` par son alias intégré, `rv` .</span><span class="sxs-lookup"><span data-stu-id="c8f16-156">You can also refer to `Remove-Variable` by its built-in alias, `rv`.</span></span> <span data-ttu-id="c8f16-157">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="c8f16-157">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

## <span data-ttu-id="c8f16-158">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c8f16-158">RELATED LINKS</span></span>

[<span data-ttu-id="c8f16-159">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="c8f16-159">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="c8f16-160">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="c8f16-160">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="c8f16-161">New-Variable</span><span class="sxs-lookup"><span data-stu-id="c8f16-161">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="c8f16-162">Set-variable</span><span class="sxs-lookup"><span data-stu-id="c8f16-162">Set-Variable</span></span>](Set-Variable.md)