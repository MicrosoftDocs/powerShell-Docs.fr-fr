---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 7b6f639d1c5685e341260c056a1dd0a17fe9f46d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596108"
---
# <span data-ttu-id="859ea-102">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="859ea-102">Get-Alias</span></span>

## <span data-ttu-id="859ea-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="859ea-103">SYNOPSIS</span></span>
<span data-ttu-id="859ea-104">Obtient l'alias pour la session active.</span><span class="sxs-lookup"><span data-stu-id="859ea-104">Gets the aliases for the current session.</span></span>

## <span data-ttu-id="859ea-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="859ea-105">SYNTAX</span></span>

### <span data-ttu-id="859ea-106">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="859ea-106">Default (Default)</span></span>

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="859ea-107">Définition</span><span class="sxs-lookup"><span data-stu-id="859ea-107">Definition</span></span>

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="859ea-108">Description</span><span class="sxs-lookup"><span data-stu-id="859ea-108">DESCRIPTION</span></span>

<span data-ttu-id="859ea-109">L’applet de commande **obtenir-alias** obtient les alias de la session active.</span><span class="sxs-lookup"><span data-stu-id="859ea-109">The **Get-Alias** cmdlet gets the aliases in the current session.</span></span>
<span data-ttu-id="859ea-110">Cela comprend les alias intégrés, les alias que vous avez définis ou importés, et les alias que vous avez ajoutés à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="859ea-110">This includes built-in aliases, aliases that you have set or imported, and aliases that you have added to your PowerShell profile.</span></span>

<span data-ttu-id="859ea-111">Par **défaut, l’alias d'** accès prend un alias et retourne le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="859ea-111">By default, **Get-Alias** takes an alias and returns the command name.</span></span>
<span data-ttu-id="859ea-112">Quand vous utilisez le paramètre de *définition* , la commande **obtenir un alias** prend un nom de commande et retourne ses alias.</span><span class="sxs-lookup"><span data-stu-id="859ea-112">When you use the *Definition* parameter, **Get-Alias** takes a command name and returns its aliases.</span></span>

<span data-ttu-id="859ea-113">À compter de Windows PowerShell 3,0, la tâche **obtenir un alias** affiche les noms d’alias sans trait d’Union dans un `<alias> -> <definition>` format pour faciliter encore la recherche des informations dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="859ea-113">Beginning in Windows PowerShell 3.0, **Get-Alias** displays non-hyphenated alias names in an `<alias> -> <definition>` format to make it even easier to find the information that you need.</span></span>

## <span data-ttu-id="859ea-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="859ea-114">EXAMPLES</span></span>

### <span data-ttu-id="859ea-115">Exemple 1 : récupérer tous les alias dans la session active</span><span class="sxs-lookup"><span data-stu-id="859ea-115">Example 1: Get all aliases in the current session</span></span>

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

<span data-ttu-id="859ea-116">Cette commande obtient tous les alias dans la session active.</span><span class="sxs-lookup"><span data-stu-id="859ea-116">This command gets all aliases in the current session.</span></span>

<span data-ttu-id="859ea-117">La sortie indique le `<alias> -> <definition>` format qui a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="859ea-117">The output shows the `<alias> -> <definition>` format that was introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="859ea-118">Ce format est utilisé uniquement pour les alias qui n'incluent pas de traits d'union, étant donné que les alias avec des traits d'union sont des noms généralement préférés aux surnoms pour les applets de commande et les fonctions.</span><span class="sxs-lookup"><span data-stu-id="859ea-118">This format is used only for aliases that do not include hyphens, because aliases with hyphens are typically preferred names for cmdlets and functions, rather than nicknames.</span></span>

### <span data-ttu-id="859ea-119">Exemple 2 : récupérer des alias par nom</span><span class="sxs-lookup"><span data-stu-id="859ea-119">Example 2: Get aliases by name</span></span>

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

<span data-ttu-id="859ea-120">Cette commande obtient tous les alias qui commencent par GP ou SP, à l’exception des alias qui se terminent par PS.</span><span class="sxs-lookup"><span data-stu-id="859ea-120">This command gets all aliases that begin with gp or sp, except for aliases that end with ps.</span></span>

### <span data-ttu-id="859ea-121">Exemple 3 : obtenir des alias pour une applet de commande</span><span class="sxs-lookup"><span data-stu-id="859ea-121">Example 3: Get aliases for a cmdlet</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

<span data-ttu-id="859ea-122">Cette commande obtient les alias de l'applet de commande Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="859ea-122">This command gets the aliases for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="859ea-123">Par défaut, l’applet de commande **obtenir-alias** obtient le nom de l’élément lorsque vous connaissez l’alias.</span><span class="sxs-lookup"><span data-stu-id="859ea-123">By default, the **Get-Alias** cmdlet gets the item name when you know the alias.</span></span>
<span data-ttu-id="859ea-124">Le paramètre de *définition* obtient l’alias quand vous connaissez le nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="859ea-124">The *Definition* parameter gets the alias when you know the item name.</span></span>

### <span data-ttu-id="859ea-125">Exemple 4 : récupérer des alias par propriété</span><span class="sxs-lookup"><span data-stu-id="859ea-125">Example 4: Get aliases by property</span></span>

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

<span data-ttu-id="859ea-126">Cette commande obtient tous les alias dans lesquels la valeur de la propriété Options est ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="859ea-126">This command gets all aliases in which the value of the Options property is ReadOnly.</span></span>
<span data-ttu-id="859ea-127">Cette commande offre un moyen rapide de rechercher les alias intégrés à PowerShell, car ils possèdent l’option ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="859ea-127">This command provides a quick way to find the aliases that are built into PowerShell, because they have the ReadOnly option.</span></span>

<span data-ttu-id="859ea-128">Options n’est qu’une des propriétés des objets AliasInfo que obtient **-alias** .</span><span class="sxs-lookup"><span data-stu-id="859ea-128">Options is just one property of the AliasInfo objects that **Get-Alias** gets.</span></span>
<span data-ttu-id="859ea-129">Pour rechercher toutes les propriétés et méthodes des objets AliasInfo, tapez `Get-Alias | get-member` .</span><span class="sxs-lookup"><span data-stu-id="859ea-129">To find all properties and methods of AliasInfo objects, type `Get-Alias | get-member`.</span></span>

### <span data-ttu-id="859ea-130">Exemple 5 : récupérer des alias par nom et filtrer par lettre initiale</span><span class="sxs-lookup"><span data-stu-id="859ea-130">Example 5: Get aliases by name and filter by beginning letter</span></span>

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

<span data-ttu-id="859ea-131">Cet exemple obtient les alias des commandes qui ont des noms se terminant par « -PSSession », à l'exception de ceux qui commencent par « e ».</span><span class="sxs-lookup"><span data-stu-id="859ea-131">This example gets aliases for commands that have names that end in "-PSSession", except for those that begin with "e".</span></span>

<span data-ttu-id="859ea-132">La commande utilise le paramètre *scope* pour appliquer la commande dans l’étendue globale.</span><span class="sxs-lookup"><span data-stu-id="859ea-132">The command uses the *Scope* parameter to apply the command in the global scope.</span></span>
<span data-ttu-id="859ea-133">Cela est utile dans les scripts quand vous souhaitez obtenir les alias figurant dans la session.</span><span class="sxs-lookup"><span data-stu-id="859ea-133">This is useful in scripts when you want to get the aliases in the session.</span></span>

## <span data-ttu-id="859ea-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="859ea-134">PARAMETERS</span></span>

### <span data-ttu-id="859ea-135">-Definition</span><span class="sxs-lookup"><span data-stu-id="859ea-135">-Definition</span></span>

<span data-ttu-id="859ea-136">Obtient les alias pour l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="859ea-136">Gets the aliases for the specified item.</span></span>
<span data-ttu-id="859ea-137">Entrez le nom d'une applet de commande, d'une fonction, d'un script, d'un fichier ou d'un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="859ea-137">Enter the name of a cmdlet, function, script, file, or executable file.</span></span>

<span data-ttu-id="859ea-138">Ce paramètre est appelé *définition*, car il recherche le nom de l’élément dans la propriété de définition de l’objet alias.</span><span class="sxs-lookup"><span data-stu-id="859ea-138">This parameter is called *Definition*, because it searches for the item name in the Definition property of the alias object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="859ea-139">-Exclude</span><span class="sxs-lookup"><span data-stu-id="859ea-139">-Exclude</span></span>

<span data-ttu-id="859ea-140">Omet les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="859ea-140">Omits the specified items.</span></span>
<span data-ttu-id="859ea-141">La valeur de ce paramètre qualifie les paramètres Name et Definition.</span><span class="sxs-lookup"><span data-stu-id="859ea-141">The value of this parameter qualifies the Name and Definition parameters.</span></span>
<span data-ttu-id="859ea-142">Entrez un nom, une définition ou un modèle, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="859ea-142">Enter a name, a definition, or a pattern, such as "s\*".</span></span>
<span data-ttu-id="859ea-143">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="859ea-143">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="859ea-144">-Name</span><span class="sxs-lookup"><span data-stu-id="859ea-144">-Name</span></span>

<span data-ttu-id="859ea-145">Spécifie les alias que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="859ea-145">Specifies the aliases that this cmdlet gets.</span></span>
<span data-ttu-id="859ea-146">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="859ea-146">Wildcards are permitted.</span></span>
<span data-ttu-id="859ea-147">Par défaut, `Get-Alias` récupère tous les alias définis pour la session active.</span><span class="sxs-lookup"><span data-stu-id="859ea-147">By default, `Get-Alias` retrieves all aliases defined for the current session.</span></span>
<span data-ttu-id="859ea-148">Le **nom du paramètre est facultatif** .</span><span class="sxs-lookup"><span data-stu-id="859ea-148">The parameter name **Name** is optional.</span></span>
<span data-ttu-id="859ea-149">Vous pouvez également diriger les noms d’alias vers `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="859ea-149">You can also pipe alias names to `Get-Alias`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="859ea-150">-Étendue</span><span class="sxs-lookup"><span data-stu-id="859ea-150">-Scope</span></span>

<span data-ttu-id="859ea-151">Spécifie l’étendue pour laquelle cette applet de commande obtient des alias.</span><span class="sxs-lookup"><span data-stu-id="859ea-151">Specifies the scope for which this cmdlet gets aliases.</span></span>
<span data-ttu-id="859ea-152">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="859ea-152">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="859ea-153">Global</span><span class="sxs-lookup"><span data-stu-id="859ea-153">Global</span></span>
- <span data-ttu-id="859ea-154">Local</span><span class="sxs-lookup"><span data-stu-id="859ea-154">Local</span></span>
- <span data-ttu-id="859ea-155">Script</span><span class="sxs-lookup"><span data-stu-id="859ea-155">Script</span></span>
- <span data-ttu-id="859ea-156">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)</span><span class="sxs-lookup"><span data-stu-id="859ea-156">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="859ea-157">Local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="859ea-157">Local is the default.</span></span>
<span data-ttu-id="859ea-158">Pour plus d'informations, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="859ea-158">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="859ea-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="859ea-159">CommonParameters</span></span>

<span data-ttu-id="859ea-160">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="859ea-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="859ea-161">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="859ea-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="859ea-162">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="859ea-162">INPUTS</span></span>

### <span data-ttu-id="859ea-163">System.String</span><span class="sxs-lookup"><span data-stu-id="859ea-163">System.String</span></span>

<span data-ttu-id="859ea-164">Vous pouvez diriger les noms d’alias vers la valeur de l' **alias**.</span><span class="sxs-lookup"><span data-stu-id="859ea-164">You can pipe alias names to **Get-Alias**.</span></span>

## <span data-ttu-id="859ea-165">SORTIES</span><span class="sxs-lookup"><span data-stu-id="859ea-165">OUTPUTS</span></span>

### <span data-ttu-id="859ea-166">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="859ea-166">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="859ea-167">La **fonction de récupération d’alias** retourne un objet qui représente chaque alias.</span><span class="sxs-lookup"><span data-stu-id="859ea-167">**Get-Alias** returns an object that represents each alias.</span></span>
<span data-ttu-id="859ea-168">L' **alias « obtenir »** retourne le même objet pour chaque alias, mais PowerShell utilise un format basé sur les flèches pour afficher les noms des alias sans trait d’Union.</span><span class="sxs-lookup"><span data-stu-id="859ea-168">**Get-Alias** returns the same object for every alias, but PowerShell uses an arrow-based format to display the names of non-hyphenated aliases.</span></span>

## <span data-ttu-id="859ea-169">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="859ea-169">NOTES</span></span>

- <span data-ttu-id="859ea-170">Pour créer un alias, utilisez Set-Alias ou New-Alias.</span><span class="sxs-lookup"><span data-stu-id="859ea-170">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="859ea-171">Pour supprimer un alias, utilisez Remove-Item.</span><span class="sxs-lookup"><span data-stu-id="859ea-171">To delete an alias, use Remove-Item.</span></span>
- <span data-ttu-id="859ea-172">Le format de nom d'alias basé sur les flèches n'est pas utilisé pour les alias qui comportent un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="859ea-172">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="859ea-173">Ceux-ci sont susceptibles d'être des noms de remplacement par défaut pour les applets de commande et les fonctions, au lieu d'être des abréviations ou des surnoms standard.</span><span class="sxs-lookup"><span data-stu-id="859ea-173">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames.</span></span>

## <span data-ttu-id="859ea-174">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="859ea-174">RELATED LINKS</span></span>

[<span data-ttu-id="859ea-175">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="859ea-175">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="859ea-176">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="859ea-176">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="859ea-177">New-Alias</span><span class="sxs-lookup"><span data-stu-id="859ea-177">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="859ea-178">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="859ea-178">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="859ea-179">Fournisseur Alias</span><span class="sxs-lookup"><span data-stu-id="859ea-179">Alias Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[<span data-ttu-id="859ea-180">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="859ea-180">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

