---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: eac42af069b5d1276105c16dd6e280c7c72cf558
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204578"
---
# <span data-ttu-id="eb403-103">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="eb403-103">Get-Variable</span></span>

## <span data-ttu-id="eb403-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="eb403-104">SYNOPSIS</span></span>
<span data-ttu-id="eb403-105">Obtient les variables dans la console active.</span><span class="sxs-lookup"><span data-stu-id="eb403-105">Gets the variables in the current console.</span></span>

## <span data-ttu-id="eb403-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eb403-106">SYNTAX</span></span>

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="eb403-107">Description</span><span class="sxs-lookup"><span data-stu-id="eb403-107">DESCRIPTION</span></span>

<span data-ttu-id="eb403-108">L' `Get-Variable` applet de commande obtient les variables PowerShell dans la console active.</span><span class="sxs-lookup"><span data-stu-id="eb403-108">The `Get-Variable` cmdlet gets the PowerShell variables in the current console.</span></span>
<span data-ttu-id="eb403-109">Vous pouvez récupérer seulement les valeurs des variables en spécifiant le paramètre **ValueOnly** , et vous pouvez filtrer les variables retournées par nom.</span><span class="sxs-lookup"><span data-stu-id="eb403-109">You can retrieve just the values of the variables by specifying the **ValueOnly** parameter, and you can filter the variables returned by name.</span></span>

## <span data-ttu-id="eb403-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="eb403-110">EXAMPLES</span></span>

### <span data-ttu-id="eb403-111">Exemple 1 : récupérer les variables par lettre</span><span class="sxs-lookup"><span data-stu-id="eb403-111">Example 1: Get variables by letter</span></span>

<span data-ttu-id="eb403-112">Cette commande obtient les variables dont le nom commence par la lettre m.</span><span class="sxs-lookup"><span data-stu-id="eb403-112">This command gets variables with names that begin with the letter m.</span></span>
<span data-ttu-id="eb403-113">La commande obtient également la valeur des variables.</span><span class="sxs-lookup"><span data-stu-id="eb403-113">The command also gets the value of the variables.</span></span>

```powershell
Get-Variable m*
```

### <span data-ttu-id="eb403-114">Exemple 2 : récupérer des valeurs de variables par lettre</span><span class="sxs-lookup"><span data-stu-id="eb403-114">Example 2: Get variable values by letter</span></span>

<span data-ttu-id="eb403-115">Cette commande obtient uniquement les valeurs des variables dont le nom commence par m.</span><span class="sxs-lookup"><span data-stu-id="eb403-115">This command gets only the values of the variables that have names that begin with m.</span></span>

```powershell
Get-Variable m* -ValueOnly
```

### <span data-ttu-id="eb403-116">Exemple 3 : récupération de variables à l’aide de deux lettres</span><span class="sxs-lookup"><span data-stu-id="eb403-116">Example 3: Get variables by two letters</span></span>

<span data-ttu-id="eb403-117">Cette commande obtient des informations sur les variables qui commencent par la lettre M ou par la lettre P.</span><span class="sxs-lookup"><span data-stu-id="eb403-117">This command gets information about the variables that begin with either the letter M or the letter P.</span></span>

```powershell
Get-Variable -Include M*,P*
```

### <span data-ttu-id="eb403-118">Exemple 4 : récupération des variables par étendue</span><span class="sxs-lookup"><span data-stu-id="eb403-118">Example 4: Get variables by scope</span></span>

<span data-ttu-id="eb403-119">La première commande obtient seulement les variables définies dans l'étendue locale.</span><span class="sxs-lookup"><span data-stu-id="eb403-119">The first command gets only the variables that are defined in the local scope.</span></span>
<span data-ttu-id="eb403-120">Elle est équivalente à `Get-Variable -Scope Local` et peut être abrégée en `gv -s 0` .</span><span class="sxs-lookup"><span data-stu-id="eb403-120">It is equivalent to `Get-Variable -Scope Local` and can be abbreviated as `gv -s 0`.</span></span>

<span data-ttu-id="eb403-121">La deuxième commande utilise l' `Compare-Object` applet de commande pour rechercher les variables définies dans l’étendue parente (étendue 1), mais uniquement dans l’étendue locale (étendue 0).</span><span class="sxs-lookup"><span data-stu-id="eb403-121">The second command uses the `Compare-Object` cmdlet to find the variables that are defined in the parent scope (Scope 1) but are visible only in the local scope (Scope 0).</span></span>

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## <span data-ttu-id="eb403-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eb403-122">PARAMETERS</span></span>

### <span data-ttu-id="eb403-123">-Exclude</span><span class="sxs-lookup"><span data-stu-id="eb403-123">-Exclude</span></span>

<span data-ttu-id="eb403-124">Spécifie un tableau d’éléments que cette applet de commande exclut de l’opération.</span><span class="sxs-lookup"><span data-stu-id="eb403-124">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="eb403-125">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eb403-125">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="eb403-126">-Include</span><span class="sxs-lookup"><span data-stu-id="eb403-126">-Include</span></span>

<span data-ttu-id="eb403-127">Spécifie un tableau d’éléments sur lesquels l’applet de commande agira, en excluant tous les autres.</span><span class="sxs-lookup"><span data-stu-id="eb403-127">Specifies an array of items upon which the cmdlet will act, excluding all others.</span></span>
<span data-ttu-id="eb403-128">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eb403-128">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="eb403-129">-Name</span><span class="sxs-lookup"><span data-stu-id="eb403-129">-Name</span></span>

<span data-ttu-id="eb403-130">Spécifie le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="eb403-130">Specifies the name of the variable.</span></span>
<span data-ttu-id="eb403-131">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="eb403-131">Wildcards are permitted.</span></span>
<span data-ttu-id="eb403-132">Vous pouvez également diriger un nom de variable vers `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="eb403-132">You can also pipe a variable name to `Get-Variable`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="eb403-133">-Étendue</span><span class="sxs-lookup"><span data-stu-id="eb403-133">-Scope</span></span>

<span data-ttu-id="eb403-134">Spécifie les variables dans l’étendue. Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb403-134">Specifies the variables in the scope.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="eb403-135">**Global**</span><span class="sxs-lookup"><span data-stu-id="eb403-135">**Global**</span></span>
- <span data-ttu-id="eb403-136">**Local**</span><span class="sxs-lookup"><span data-stu-id="eb403-136">**Local**</span></span>
- <span data-ttu-id="eb403-137">**Script**</span><span class="sxs-lookup"><span data-stu-id="eb403-137">**Script**</span></span>
- <span data-ttu-id="eb403-138">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)</span><span class="sxs-lookup"><span data-stu-id="eb403-138">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="eb403-139">**Local** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="eb403-139">**Local** is the default.</span></span>
<span data-ttu-id="eb403-140">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="eb403-140">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="eb403-141">-ValueOnly</span><span class="sxs-lookup"><span data-stu-id="eb403-141">-ValueOnly</span></span>

<span data-ttu-id="eb403-142">Indique que cette applet de commande obtient uniquement la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="eb403-142">Indicates that this cmdlet gets only the value of the variable.</span></span>

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

### <span data-ttu-id="eb403-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eb403-143">CommonParameters</span></span>

<span data-ttu-id="eb403-144">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eb403-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eb403-145">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="eb403-145">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="eb403-146">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="eb403-146">INPUTS</span></span>

### <span data-ttu-id="eb403-147">System.String</span><span class="sxs-lookup"><span data-stu-id="eb403-147">System.String</span></span>

<span data-ttu-id="eb403-148">Vous pouvez diriger une chaîne qui contient le nom de la variable vers `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="eb403-148">You can pipe a string that contains the variable name to `Get-Variable`.</span></span>

## <span data-ttu-id="eb403-149">SORTIES</span><span class="sxs-lookup"><span data-stu-id="eb403-149">OUTPUTS</span></span>

### <span data-ttu-id="eb403-150">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="eb403-150">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="eb403-151">Cette applet de commande retourne un objet **System. Management. AutomationPSVariable** pour chaque variable qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="eb403-151">This cmdlet returns a **System.Management.AutomationPSVariable** object for each variable that it gets.</span></span> <span data-ttu-id="eb403-152">Le type d'objet dépend de la variable.</span><span class="sxs-lookup"><span data-stu-id="eb403-152">The object type depends on the variable.</span></span>

### <span data-ttu-id="eb403-153">System. Object []</span><span class="sxs-lookup"><span data-stu-id="eb403-153">System.Object[]</span></span>

<span data-ttu-id="eb403-154">Lorsque vous spécifiez le paramètre **ValueOnly** , si la valeur de la variable spécifiée est une collection, `Get-Variable` retourne un `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="eb403-154">When you specify the **ValueOnly** parameter, if the specified variable's value is a collection, `Get-Variable` returns a `[System.Object[]]`.</span></span> <span data-ttu-id="eb403-155">Ce comportement empêche l’opération de pipeline normale de traiter les valeurs de la variable une à la fois.</span><span class="sxs-lookup"><span data-stu-id="eb403-155">This behavior prevents normal pipeline operation from processing the variable's values one at a time.</span></span> <span data-ttu-id="eb403-156">Une solution de contournement pour forcer l’énumération de collections consiste à placer la `Get-Variable` commande entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="eb403-156">A workaround to force collection enumeration is to enclose the `Get-Variable` command in parenthesis.</span></span>

## <span data-ttu-id="eb403-157">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="eb403-157">NOTES</span></span>

- <span data-ttu-id="eb403-158">Cette applet de commande ne gère pas les variables d'environnement.</span><span class="sxs-lookup"><span data-stu-id="eb403-158">This cmdlet does not manage environment variables.</span></span> <span data-ttu-id="eb403-159">Pour gérer les variables d'environnement, vous pouvez utiliser le fournisseur de variables d'environnement.</span><span class="sxs-lookup"><span data-stu-id="eb403-159">To manage environment variables, you can use the environment variable provider.</span></span>

## <span data-ttu-id="eb403-160">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="eb403-160">RELATED LINKS</span></span>

[<span data-ttu-id="eb403-161">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="eb403-161">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="eb403-162">New-Variable</span><span class="sxs-lookup"><span data-stu-id="eb403-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="eb403-163">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="eb403-163">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="eb403-164">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="eb403-164">Set-Variable</span></span>](Set-Variable.md)
