---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: 7f226af3cb221543cdae88930f661e2343d954b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599165"
---
# <span data-ttu-id="3e006-102">New-Alias</span><span class="sxs-lookup"><span data-stu-id="3e006-102">New-Alias</span></span>

## <span data-ttu-id="3e006-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3e006-103">SYNOPSIS</span></span>
<span data-ttu-id="3e006-104">Crée un alias.</span><span class="sxs-lookup"><span data-stu-id="3e006-104">Creates a new alias.</span></span>

## <span data-ttu-id="3e006-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="3e006-105">SYNTAX</span></span>

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3e006-106">Description</span><span class="sxs-lookup"><span data-stu-id="3e006-106">DESCRIPTION</span></span>

<span data-ttu-id="3e006-107">L’applet de commande **New-alias** crée un alias dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="3e006-107">The **New-Alias** cmdlet creates a new alias in the current PowerShell session.</span></span>
<span data-ttu-id="3e006-108">Les alias créés à l’aide de **New-alias** ne sont pas enregistrés quand vous quittez la session ou fermez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e006-108">Aliases created by using **New-Alias** are not saved after you exit the session or close PowerShell.</span></span>
<span data-ttu-id="3e006-109">Vous pouvez utiliser l'applet de commande Export-Alias pour enregistrer vos informations d'alias dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="3e006-109">You can use the Export-Alias cmdlet to save your alias information to a file.</span></span>
<span data-ttu-id="3e006-110">Vous pouvez par la suite utiliser **Import-alias** pour récupérer les informations d’alias enregistrées.</span><span class="sxs-lookup"><span data-stu-id="3e006-110">You can later use **Import-Alias** to retrieve that saved alias information.</span></span>

## <span data-ttu-id="3e006-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3e006-111">EXAMPLES</span></span>

### <span data-ttu-id="3e006-112">Exemple 1 : créer un alias pour une applet de commande</span><span class="sxs-lookup"><span data-stu-id="3e006-112">Example 1: Create an alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

<span data-ttu-id="3e006-113">Cette commande crée un alias nommé List pour représenter l’applet de commande Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="3e006-113">This command creates an alias named List to represent the Get-ChildItem cmdlet.</span></span>

### <span data-ttu-id="3e006-114">Exemple 2 : créer un alias en lecture seule pour une applet de commande</span><span class="sxs-lookup"><span data-stu-id="3e006-114">Example 2: Create a read-only alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

<span data-ttu-id="3e006-115">Cette commande crée un alias nommé W pour représenter l’applet de commande Get-WmiObject.</span><span class="sxs-lookup"><span data-stu-id="3e006-115">This command creates an alias named W to represent the Get-WmiObject cmdlet.</span></span>
<span data-ttu-id="3e006-116">Il crée une description, un alias WMI rapide, pour l’alias et le rend accessible en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="3e006-116">It creates a description, quick wmi alias, for the alias and makes it read-only.</span></span>
<span data-ttu-id="3e006-117">La dernière ligne de la commande utilise Get-Alias pour obtenir le nouvel alias et le dirige vers Format-List pour afficher toutes les informations le concernant.</span><span class="sxs-lookup"><span data-stu-id="3e006-117">The last line of the command uses Get-Alias to get the new alias and pipes it to Format-List to display all of the information about it.</span></span>

## <span data-ttu-id="3e006-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e006-118">PARAMETERS</span></span>

### <span data-ttu-id="3e006-119">Description</span><span class="sxs-lookup"><span data-stu-id="3e006-119">-Description</span></span>

<span data-ttu-id="3e006-120">Spécifie une description de l'alias.</span><span class="sxs-lookup"><span data-stu-id="3e006-120">Specifies a description of the alias.</span></span>
<span data-ttu-id="3e006-121">Vous pouvez entrer n'importe quelle chaîne.</span><span class="sxs-lookup"><span data-stu-id="3e006-121">You can type any string.</span></span>
<span data-ttu-id="3e006-122">Si la description inclut des espaces, mettez-la entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="3e006-122">If the description includes spaces, enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="3e006-123">-Force</span><span class="sxs-lookup"><span data-stu-id="3e006-123">-Force</span></span>

<span data-ttu-id="3e006-124">Indique que l’applet de commande agit comme Set-Alias si l’alias nommé existe déjà.</span><span class="sxs-lookup"><span data-stu-id="3e006-124">Indicates that the cmdlet acts like Set-Alias if the alias named already exists.</span></span>

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

### <span data-ttu-id="3e006-125">-Name</span><span class="sxs-lookup"><span data-stu-id="3e006-125">-Name</span></span>

<span data-ttu-id="3e006-126">Spécifie le nouvel alias.</span><span class="sxs-lookup"><span data-stu-id="3e006-126">Specifies the new alias.</span></span>
<span data-ttu-id="3e006-127">Vous pouvez utiliser des caractères alphanumériques dans un alias, mais le premier caractère ne peut pas être un nombre.</span><span class="sxs-lookup"><span data-stu-id="3e006-127">You can use any alphanumeric characters in an alias, but the first character cannot be a number.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e006-128">-Option</span><span class="sxs-lookup"><span data-stu-id="3e006-128">-Option</span></span>

<span data-ttu-id="3e006-129">Spécifie la valeur de la propriété **options** de l’alias.</span><span class="sxs-lookup"><span data-stu-id="3e006-129">Specifies the value of the **Options** property of the alias.</span></span>
<span data-ttu-id="3e006-130">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="3e006-130">Valid values are:</span></span>

- <span data-ttu-id="3e006-131">None : l’alias n’a pas de contraintes (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="3e006-131">None: The alias has no constraints (default value)</span></span>
- <span data-ttu-id="3e006-132">ReadOnly : l’alias peut être supprimé, mais il ne peut pas être modifié, sauf en utilisant le paramètre **force**</span><span class="sxs-lookup"><span data-stu-id="3e006-132">ReadOnly: The alias can be deleted but cannot be changed except by using the **Force** parameter</span></span>
- <span data-ttu-id="3e006-133">Constante : l’alias ne peut pas être supprimé ou modifié</span><span class="sxs-lookup"><span data-stu-id="3e006-133">Constant: The alias cannot be deleted or changed</span></span>
- <span data-ttu-id="3e006-134">Privé : l’alias est uniquement disponible dans l’étendue actuelle</span><span class="sxs-lookup"><span data-stu-id="3e006-134">Private: The alias is available only in the current scope</span></span>
- <span data-ttu-id="3e006-135">Options AllScope : l’alias est copié vers toutes les nouvelles étendues créées</span><span class="sxs-lookup"><span data-stu-id="3e006-135">AllScope: The alias is copied to any new scopes that are created</span></span>
- <span data-ttu-id="3e006-136">Non spécifié : l’option n’est pas spécifiée</span><span class="sxs-lookup"><span data-stu-id="3e006-136">Unspecified: The option is not specified</span></span>

<span data-ttu-id="3e006-137">Pour afficher la propriété **options** de tous les alias dans la session, tapez `Get-Alias | Format-Table -Property Name, Options -AutoSize` .</span><span class="sxs-lookup"><span data-stu-id="3e006-137">To see the **Options** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -AutoSize`.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e006-138">-PassThru</span><span class="sxs-lookup"><span data-stu-id="3e006-138">-PassThru</span></span>

<span data-ttu-id="3e006-139">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="3e006-139">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="3e006-140">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="3e006-140">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="3e006-141">-Étendue</span><span class="sxs-lookup"><span data-stu-id="3e006-141">-Scope</span></span>

<span data-ttu-id="3e006-142">Spécifie l'étendue du nouvel alias.</span><span class="sxs-lookup"><span data-stu-id="3e006-142">Specifies the scope of the new alias.</span></span>
<span data-ttu-id="3e006-143">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="3e006-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3e006-144">Global</span><span class="sxs-lookup"><span data-stu-id="3e006-144">Global</span></span>
- <span data-ttu-id="3e006-145">Local</span><span class="sxs-lookup"><span data-stu-id="3e006-145">Local</span></span>
- <span data-ttu-id="3e006-146">Script</span><span class="sxs-lookup"><span data-stu-id="3e006-146">Script</span></span>
- <span data-ttu-id="3e006-147">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent).</span><span class="sxs-lookup"><span data-stu-id="3e006-147">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="3e006-148">Local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3e006-148">Local is the default.</span></span>
<span data-ttu-id="3e006-149">Pour plus d'informations, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="3e006-149">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="3e006-150">-Value</span><span class="sxs-lookup"><span data-stu-id="3e006-150">-Value</span></span>

<span data-ttu-id="3e006-151">Spécifie le nom de l'élément d'applet de commande ou de commande auquel est associé un alias.</span><span class="sxs-lookup"><span data-stu-id="3e006-151">Specifies the name of the cmdlet or command element that is being aliased.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e006-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3e006-152">-Confirm</span></span>

<span data-ttu-id="3e006-153">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3e006-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3e006-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3e006-154">-WhatIf</span></span>

<span data-ttu-id="3e006-155">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3e006-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3e006-156">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="3e006-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3e006-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e006-157">CommonParameters</span></span>

<span data-ttu-id="3e006-158">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e006-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e006-159">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3e006-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e006-160">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3e006-160">INPUTS</span></span>

### <span data-ttu-id="3e006-161">None</span><span class="sxs-lookup"><span data-stu-id="3e006-161">None</span></span>

<span data-ttu-id="3e006-162">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3e006-162">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3e006-163">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3e006-163">OUTPUTS</span></span>

### <span data-ttu-id="3e006-164">None ou System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="3e006-164">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="3e006-165">Quand vous utilisez le paramètre *PassThru* , **New-alias** génère un objet **System. Management. Automation. AliasInfo** qui représente le nouvel alias.</span><span class="sxs-lookup"><span data-stu-id="3e006-165">When you use the *Passthru* parameter, **New-Alias** generates a **System.Management.Automation.AliasInfo** object representing the new alias.</span></span>
<span data-ttu-id="3e006-166">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="3e006-166">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3e006-167">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3e006-167">NOTES</span></span>

* <span data-ttu-id="3e006-168">Pour créer un alias, utilisez `Set-Alias` ou `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="3e006-168">To create a new alias, use `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="3e006-169">Pour modifier un alias, utilisez `Set-Alias` .</span><span class="sxs-lookup"><span data-stu-id="3e006-169">To change an alias, use `Set-Alias`.</span></span> <span data-ttu-id="3e006-170">Pour supprimer un alias, utilisez `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="3e006-170">To delete an alias, use `Remove-Item`.</span></span>

## <span data-ttu-id="3e006-171">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3e006-171">RELATED LINKS</span></span>

[<span data-ttu-id="3e006-172">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="3e006-172">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="3e006-173">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="3e006-173">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="3e006-174">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="3e006-174">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="3e006-175">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="3e006-175">Set-Alias</span></span>](Set-Alias.md)

