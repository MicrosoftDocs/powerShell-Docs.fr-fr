---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: 6208e9c1b7124c8faec1e3e87a6e815540d2b962
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201994"
---
# <span data-ttu-id="b04f2-103">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="b04f2-103">Clear-Variable</span></span>

## <span data-ttu-id="b04f2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b04f2-104">SYNOPSIS</span></span>
<span data-ttu-id="b04f2-105">Supprime la valeur d'une variable.</span><span class="sxs-lookup"><span data-stu-id="b04f2-105">Deletes the value of a variable.</span></span>

## <span data-ttu-id="b04f2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b04f2-106">SYNTAX</span></span>

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b04f2-107">Description</span><span class="sxs-lookup"><span data-stu-id="b04f2-107">DESCRIPTION</span></span>

<span data-ttu-id="b04f2-108">L’applet **de commande Clear-variable** supprime les données stockées dans une variable, mais elle ne supprime pas la variable.</span><span class="sxs-lookup"><span data-stu-id="b04f2-108">The **Clear-Variable** cmdlet deletes the data stored in a variable, but it does not delete the variable.</span></span>
<span data-ttu-id="b04f2-109">Par conséquent, la valeur de la variable est NULL (vide).</span><span class="sxs-lookup"><span data-stu-id="b04f2-109">As a result, the value of the variable is NULL (empty).</span></span>
<span data-ttu-id="b04f2-110">Si la variable a un type de données ou d’objet spécifié, cette applet de commande conserve le type de l’objet stocké dans la variable.</span><span class="sxs-lookup"><span data-stu-id="b04f2-110">If the variable has a specified data or object type, this cmdlet preserves the type of the object stored in the variable.</span></span>

## <span data-ttu-id="b04f2-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b04f2-111">EXAMPLES</span></span>

### <span data-ttu-id="b04f2-112">Exemple 1 : supprimer la valeur des variables globales qui commencent par une chaîne de recherche</span><span class="sxs-lookup"><span data-stu-id="b04f2-112">Example 1: Remove the value of global variables that begin with a search string</span></span>

```
PS C:\> Clear-Variable my* -Scope Global
```

<span data-ttu-id="b04f2-113">Cette commande supprime la valeur des variables globales dont le nom commence par My.</span><span class="sxs-lookup"><span data-stu-id="b04f2-113">This command removes the value of global variables that have names that begin with my.</span></span>

### <span data-ttu-id="b04f2-114">Exemple 2 : effacer une variable dans une étendue enfant, mais pas à l’étendue parente</span><span class="sxs-lookup"><span data-stu-id="b04f2-114">Example 2: Clear a variable in a child scope but not the parent scope</span></span>

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

<span data-ttu-id="b04f2-115">Ces commandes montrent qu'effacer une variable dans une étendue enfant n'efface pas la valeur dans l'étendue parente.</span><span class="sxs-lookup"><span data-stu-id="b04f2-115">These commands demonstrate that clearing a variable in a child scope does not clear the value in the parent scope.</span></span>
<span data-ttu-id="b04f2-116">La première commande définit la valeur de la variable $A sur 3.</span><span class="sxs-lookup"><span data-stu-id="b04f2-116">The first command sets the value of the variable $A to 3.</span></span>
<span data-ttu-id="b04f2-117">La deuxième commande utilise l’opérateur d’appel (&) pour exécuter la commande **Clear-variable** dans une nouvelle étendue.</span><span class="sxs-lookup"><span data-stu-id="b04f2-117">The second command uses the invoke operator (&) to run the **Clear-Variable** command in a new scope.</span></span>
<span data-ttu-id="b04f2-118">La variable est effacée dans l'étendue enfant (même si elle n'existait pas), mais elle n'est pas effacée dans l'étendue locale.</span><span class="sxs-lookup"><span data-stu-id="b04f2-118">The variable is cleared in the child scope (although it did not exist), but it is not cleared in the local scope.</span></span>
<span data-ttu-id="b04f2-119">La troisième commande, qui obtient la valeur de $A, indique que la valeur 3 n’est pas affectée.</span><span class="sxs-lookup"><span data-stu-id="b04f2-119">The third command, which gets the value of $A, shows that the value 3 is unaffected.</span></span>

### <span data-ttu-id="b04f2-120">Exemple 3 : supprimer la valeur de la variable spécifiée</span><span class="sxs-lookup"><span data-stu-id="b04f2-120">Example 3: Delete the value of the specified variable</span></span>

```
PS C:\> Clear-Variable -Name "Processes"
```

<span data-ttu-id="b04f2-121">Cette commande supprime la valeur de la variable named Processes.</span><span class="sxs-lookup"><span data-stu-id="b04f2-121">This command deletes the value of the variable named Processes.</span></span>
<span data-ttu-id="b04f2-122">Une fois que l’applet de commande a terminé l’opération, la variable nommée Processes existe toujours, mais la valeur est null.</span><span class="sxs-lookup"><span data-stu-id="b04f2-122">After the cmdlet completes the operation, the variable named Processes still exists, but the value is null.</span></span>

## <span data-ttu-id="b04f2-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b04f2-123">PARAMETERS</span></span>

### <span data-ttu-id="b04f2-124">-Exclude</span><span class="sxs-lookup"><span data-stu-id="b04f2-124">-Exclude</span></span>

<span data-ttu-id="b04f2-125">Spécifie un tableau d’éléments que cette applet de commande omet dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="b04f2-125">Specifies an array of items that this cmdlet omits in the operation.</span></span>
<span data-ttu-id="b04f2-126">La valeur de ce paramètre qualifie le paramètre *Name* .</span><span class="sxs-lookup"><span data-stu-id="b04f2-126">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="b04f2-127">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="b04f2-127">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="b04f2-128">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="b04f2-128">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="b04f2-129">-Force</span><span class="sxs-lookup"><span data-stu-id="b04f2-129">-Force</span></span>

<span data-ttu-id="b04f2-130">Permet à l'applet de commande d'effacer une variable, même si elle est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="b04f2-130">Allows the cmdlet to clear a variable even if it is read-only.</span></span>
<span data-ttu-id="b04f2-131">Même en utilisant le paramètre Force, l'applet de commande ne peut pas effacer des constantes.</span><span class="sxs-lookup"><span data-stu-id="b04f2-131">Even using the Force parameter, the cmdlet cannot clear constants.</span></span>

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

### <span data-ttu-id="b04f2-132">-Include</span><span class="sxs-lookup"><span data-stu-id="b04f2-132">-Include</span></span>

<span data-ttu-id="b04f2-133">Spécifie un tableau d’éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="b04f2-133">Specifies an array of items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="b04f2-134">La valeur de ce paramètre qualifie le paramètre *Name* .</span><span class="sxs-lookup"><span data-stu-id="b04f2-134">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="b04f2-135">Entrez un élément ou un modèle de nom, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="b04f2-135">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="b04f2-136">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="b04f2-136">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="b04f2-137">-Name</span><span class="sxs-lookup"><span data-stu-id="b04f2-137">-Name</span></span>

<span data-ttu-id="b04f2-138">Spécifie le nom de la variable à effacer.</span><span class="sxs-lookup"><span data-stu-id="b04f2-138">Specifies the name of the variable to be cleared.</span></span>
<span data-ttu-id="b04f2-139">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="b04f2-139">Wildcards are permitted.</span></span>
<span data-ttu-id="b04f2-140">Ce paramètre est requis, mais le nom du paramètre (« Name ») est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b04f2-140">This parameter is required, but the parameter name ("Name") is optional.</span></span>

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

### <span data-ttu-id="b04f2-141">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b04f2-141">-PassThru</span></span>

<span data-ttu-id="b04f2-142">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="b04f2-142">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="b04f2-143">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="b04f2-143">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b04f2-144">-Étendue</span><span class="sxs-lookup"><span data-stu-id="b04f2-144">-Scope</span></span>

<span data-ttu-id="b04f2-145">Spécifie l'étendue dans laquelle cet alias est valide.</span><span class="sxs-lookup"><span data-stu-id="b04f2-145">Specifies the scope in which this alias is valid.</span></span>

<span data-ttu-id="b04f2-146">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="b04f2-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b04f2-147">Global</span><span class="sxs-lookup"><span data-stu-id="b04f2-147">Global</span></span>
- <span data-ttu-id="b04f2-148">Local</span><span class="sxs-lookup"><span data-stu-id="b04f2-148">Local</span></span>
- <span data-ttu-id="b04f2-149">Script</span><span class="sxs-lookup"><span data-stu-id="b04f2-149">Script</span></span>

<span data-ttu-id="b04f2-150">Vous pouvez également utiliser un nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est l’étendue actuelle et 1 est son parent).</span><span class="sxs-lookup"><span data-stu-id="b04f2-150">You can also use a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>
<span data-ttu-id="b04f2-151">Local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b04f2-151">Local is the default.</span></span>
<span data-ttu-id="b04f2-152">Pour plus d'informations, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="b04f2-152">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="b04f2-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b04f2-153">-Confirm</span></span>

<span data-ttu-id="b04f2-154">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b04f2-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b04f2-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b04f2-155">-WhatIf</span></span>

<span data-ttu-id="b04f2-156">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b04f2-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b04f2-157">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b04f2-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b04f2-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b04f2-158">CommonParameters</span></span>

<span data-ttu-id="b04f2-159">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b04f2-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b04f2-160">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b04f2-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b04f2-161">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b04f2-161">INPUTS</span></span>

### <span data-ttu-id="b04f2-162">Aucun</span><span class="sxs-lookup"><span data-stu-id="b04f2-162">None</span></span>

<span data-ttu-id="b04f2-163">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b04f2-163">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="b04f2-164">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b04f2-164">OUTPUTS</span></span>

### <span data-ttu-id="b04f2-165">None ou System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="b04f2-165">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="b04f2-166">Quand vous utilisez le paramètre *PassThru* , cette applet de commande génère un objet **System. Management. Automation. PSVariable** représentant la variable effacée.</span><span class="sxs-lookup"><span data-stu-id="b04f2-166">When you use the *PassThru* parameter, this cmdlet generates a **System.Management.Automation.PSVariable** object representing the cleared variable.</span></span>
<span data-ttu-id="b04f2-167">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="b04f2-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b04f2-168">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b04f2-168">NOTES</span></span>

* <span data-ttu-id="b04f2-169">Pour supprimer une variable, ainsi que sa valeur, utilisez Remove-Variable ou Remove-Item.</span><span class="sxs-lookup"><span data-stu-id="b04f2-169">To delete a variable, along with its value, use Remove-Variable or Remove-Item.</span></span>

  <span data-ttu-id="b04f2-170">Cette applet de commande ne supprime pas les valeurs des variables qui sont définies en tant que constantes ou détenues par le système, même si vous utilisez le paramètre *force* .</span><span class="sxs-lookup"><span data-stu-id="b04f2-170">This cmdlet does not delete the values of variables that are set as constants or owned by the system, even if you use the *Force* parameter.</span></span>

  <span data-ttu-id="b04f2-171">Si la variable que vous effacez n'existe pas, l'applet de commande n'a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="b04f2-171">If the variable that you are clearing does not exist, the cmdlet has no effect.</span></span>
<span data-ttu-id="b04f2-172">Elle ne crée pas de variable avec une valeur null.</span><span class="sxs-lookup"><span data-stu-id="b04f2-172">It does not create a variable with a null value.</span></span>

  <span data-ttu-id="b04f2-173">Vous pouvez également faire référence à **Clear-variable** par son alias intégré, CLV.</span><span class="sxs-lookup"><span data-stu-id="b04f2-173">You can also refer to **Clear-Variable** by its built-in alias, clv.</span></span>
<span data-ttu-id="b04f2-174">Pour plus d'informations, consultez about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="b04f2-174">For more information, see about_Aliases.</span></span>

*

## <span data-ttu-id="b04f2-175">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b04f2-175">RELATED LINKS</span></span>

[<span data-ttu-id="b04f2-176">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="b04f2-176">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="b04f2-177">New-Variable</span><span class="sxs-lookup"><span data-stu-id="b04f2-177">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="b04f2-178">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="b04f2-178">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="b04f2-179">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="b04f2-179">Set-Variable</span></span>](Set-Variable.md)
