---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: 26d53ab633f5f73495a8d66012ae55dc10c5d629
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205734"
---
# <span data-ttu-id="8cd4d-103">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="8cd4d-103">Remove-Variable</span></span>

## <span data-ttu-id="8cd4d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8cd4d-104">SYNOPSIS</span></span>
<span data-ttu-id="8cd4d-105">Supprime une variable et sa valeur.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-105">Deletes a variable and its value.</span></span>

## <span data-ttu-id="8cd4d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8cd4d-106">SYNTAX</span></span>

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8cd4d-107">Description</span><span class="sxs-lookup"><span data-stu-id="8cd4d-107">DESCRIPTION</span></span>

<span data-ttu-id="8cd4d-108">L' `Remove-Variable` applet de commande supprime une variable et sa valeur de l’étendue dans laquelle elle est définie, telle que la session active.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-108">The `Remove-Variable` cmdlet deletes a variable and its value from the scope in which it is defined, such as the current session.</span></span> <span data-ttu-id="8cd4d-109">Vous ne pouvez pas utiliser cette applet de commande pour supprimer des variables qui sont définies en tant que constantes ou celles qui sont détenues par le système.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-109">You cannot use this cmdlet to delete variables that are set as constants or those that are owned by the system.</span></span>

## <span data-ttu-id="8cd4d-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8cd4d-110">EXAMPLES</span></span>

### <span data-ttu-id="8cd4d-111">Exemple 1 : supprimer une variable</span><span class="sxs-lookup"><span data-stu-id="8cd4d-111">Example 1: Remove a variable</span></span>

```powershell
Remove-Variable Smp
```

<span data-ttu-id="8cd4d-112">Cette commande supprime la `$Smp` variable.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-112">This command deletes the `$Smp` variable.</span></span>

## <span data-ttu-id="8cd4d-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8cd4d-113">PARAMETERS</span></span>

### <span data-ttu-id="8cd4d-114">-Exclude</span><span class="sxs-lookup"><span data-stu-id="8cd4d-114">-Exclude</span></span>

<span data-ttu-id="8cd4d-115">Spécifie un tableau d’éléments que cette applet de commande omet de l’opération.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-115">Specifies an array of items that this cmdlet omits from the operation.</span></span> <span data-ttu-id="8cd4d-116">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="8cd4d-116">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="8cd4d-117">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="8cd4d-117">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="8cd4d-118">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-118">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="8cd4d-119">-Force</span><span class="sxs-lookup"><span data-stu-id="8cd4d-119">-Force</span></span>

<span data-ttu-id="8cd4d-120">Indique que l’applet de commande supprime une variable, même si elle est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-120">Indicates that the cmdlet removes a variable even if it is read-only.</span></span> <span data-ttu-id="8cd4d-121">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas supprimer une constante.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-121">Even using the **Force** parameter, the cmdlet cannot remove a constant.</span></span>

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

### <span data-ttu-id="8cd4d-122">-Include</span><span class="sxs-lookup"><span data-stu-id="8cd4d-122">-Include</span></span>

<span data-ttu-id="8cd4d-123">Spécifie un tableau d’éléments que cette applet de commande supprime dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-123">Specifies an array of items that this cmdlet deletes in the operation.</span></span> <span data-ttu-id="8cd4d-124">La valeur de ce paramètre qualifie le paramètre **Name** .</span><span class="sxs-lookup"><span data-stu-id="8cd4d-124">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="8cd4d-125">Entrez un élément ou un modèle de nom, tel que s \*.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-125">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="8cd4d-126">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-126">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="8cd4d-127">-Name</span><span class="sxs-lookup"><span data-stu-id="8cd4d-127">-Name</span></span>

<span data-ttu-id="8cd4d-128">Spécifie le nom de la variable à supprimer.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-128">Specifies the name of the variable to be removed.</span></span> <span data-ttu-id="8cd4d-129">Le nom du paramètre ( **Name** ) est facultatif.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-129">The parameter name ( **Name** ) is optional.</span></span>
<span data-ttu-id="8cd4d-130">Les caractères génériques sont autorisés</span><span class="sxs-lookup"><span data-stu-id="8cd4d-130">Wildcards are permitted</span></span>

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

### <span data-ttu-id="8cd4d-131">-Étendue</span><span class="sxs-lookup"><span data-stu-id="8cd4d-131">-Scope</span></span>

<span data-ttu-id="8cd4d-132">Obtient seulement les variables de l'étendue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-132">Gets only the variables in the specified scope.</span></span> <span data-ttu-id="8cd4d-133">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="8cd4d-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8cd4d-134">Global</span><span class="sxs-lookup"><span data-stu-id="8cd4d-134">Global</span></span>
- <span data-ttu-id="8cd4d-135">Local</span><span class="sxs-lookup"><span data-stu-id="8cd4d-135">Local</span></span>
- <span data-ttu-id="8cd4d-136">Script</span><span class="sxs-lookup"><span data-stu-id="8cd4d-136">Script</span></span>
- <span data-ttu-id="8cd4d-137">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)</span><span class="sxs-lookup"><span data-stu-id="8cd4d-137">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="8cd4d-138">Local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-138">Local is the default.</span></span> <span data-ttu-id="8cd4d-139">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="8cd4d-139">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="8cd4d-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8cd4d-140">-Confirm</span></span>

<span data-ttu-id="8cd4d-141">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8cd4d-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8cd4d-142">-WhatIf</span></span>

<span data-ttu-id="8cd4d-143">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8cd4d-144">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8cd4d-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8cd4d-145">CommonParameters</span></span>

<span data-ttu-id="8cd4d-146">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8cd4d-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8cd4d-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8cd4d-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8cd4d-148">INPUTS</span></span>

### <span data-ttu-id="8cd4d-149">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="8cd4d-149">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="8cd4d-150">Vous pouvez diriger un objet de variable vers `Remove-Variable` .</span><span class="sxs-lookup"><span data-stu-id="8cd4d-150">You can pipe a variable object to `Remove-Variable`.</span></span>

## <span data-ttu-id="8cd4d-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8cd4d-151">OUTPUTS</span></span>

### <span data-ttu-id="8cd4d-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="8cd4d-152">None</span></span>

<span data-ttu-id="8cd4d-153">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="8cd4d-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8cd4d-154">NOTES</span></span>

- <span data-ttu-id="8cd4d-155">Les modifications affectent uniquement l'étendue actuelle, par exemple une session.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-155">Changes affect only the current scope, such as a session.</span></span> <span data-ttu-id="8cd4d-156">Pour supprimer une variable de toutes les sessions, ajoutez une `Remove-Variable` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8cd4d-156">To delete a variable from all sessions, add a `Remove-Variable` command to your PowerShell profile.</span></span>

- <span data-ttu-id="8cd4d-157">Vous pouvez également faire référence à `Remove-Variable` par son alias intégré, `rv` .</span><span class="sxs-lookup"><span data-stu-id="8cd4d-157">You can also refer to `Remove-Variable` by its built-in alias, `rv`.</span></span> <span data-ttu-id="8cd4d-158">Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="8cd4d-158">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

## <span data-ttu-id="8cd4d-159">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8cd4d-159">RELATED LINKS</span></span>

[<span data-ttu-id="8cd4d-160">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="8cd4d-160">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="8cd4d-161">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="8cd4d-161">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="8cd4d-162">New-Variable</span><span class="sxs-lookup"><span data-stu-id="8cd4d-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="8cd4d-163">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="8cd4d-163">Set-Variable</span></span>](Set-Variable.md)
