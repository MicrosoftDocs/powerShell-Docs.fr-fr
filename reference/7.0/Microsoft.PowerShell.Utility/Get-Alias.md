---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 98f68cff8501fec375e3a2b8ac446e41d5721fc7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201642"
---
# <span data-ttu-id="fa402-103">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="fa402-103">Get-Alias</span></span>

## <span data-ttu-id="fa402-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fa402-104">SYNOPSIS</span></span>
<span data-ttu-id="fa402-105">Obtient l'alias pour la session active.</span><span class="sxs-lookup"><span data-stu-id="fa402-105">Gets the aliases for the current session.</span></span>

## <span data-ttu-id="fa402-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fa402-106">SYNTAX</span></span>

### <span data-ttu-id="fa402-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="fa402-107">Default (Default)</span></span>

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="fa402-108">Définition</span><span class="sxs-lookup"><span data-stu-id="fa402-108">Definition</span></span>

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="fa402-109">Description</span><span class="sxs-lookup"><span data-stu-id="fa402-109">DESCRIPTION</span></span>

<span data-ttu-id="fa402-110">L’applet de commande **obtenir-alias** obtient les alias de la session active.</span><span class="sxs-lookup"><span data-stu-id="fa402-110">The **Get-Alias** cmdlet gets the aliases in the current session.</span></span>
<span data-ttu-id="fa402-111">Cela comprend les alias intégrés, les alias que vous avez définis ou importés, et les alias que vous avez ajoutés à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa402-111">This includes built-in aliases, aliases that you have set or imported, and aliases that you have added to your PowerShell profile.</span></span>

<span data-ttu-id="fa402-112">Par **défaut, l’alias d'** accès prend un alias et retourne le nom de la commande.</span><span class="sxs-lookup"><span data-stu-id="fa402-112">By default, **Get-Alias** takes an alias and returns the command name.</span></span>
<span data-ttu-id="fa402-113">Quand vous utilisez le paramètre de *définition* , la commande **obtenir un alias** prend un nom de commande et retourne ses alias.</span><span class="sxs-lookup"><span data-stu-id="fa402-113">When you use the *Definition* parameter, **Get-Alias** takes a command name and returns its aliases.</span></span>

<span data-ttu-id="fa402-114">À compter de Windows PowerShell 3,0, la tâche **obtenir un alias** affiche les noms d’alias sans trait d’Union dans un `<alias> -> <definition>` format pour faciliter encore la recherche des informations dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="fa402-114">Beginning in Windows PowerShell 3.0, **Get-Alias** displays non-hyphenated alias names in an `<alias> -> <definition>` format to make it even easier to find the information that you need.</span></span>

## <span data-ttu-id="fa402-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fa402-115">EXAMPLES</span></span>

### <span data-ttu-id="fa402-116">Exemple 1 : récupérer tous les alias dans la session active</span><span class="sxs-lookup"><span data-stu-id="fa402-116">Example 1: Get all aliases in the current session</span></span>

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

<span data-ttu-id="fa402-117">Cette commande obtient tous les alias dans la session active.</span><span class="sxs-lookup"><span data-stu-id="fa402-117">This command gets all aliases in the current session.</span></span>

<span data-ttu-id="fa402-118">La sortie indique le `<alias> -> <definition>` format qui a été introduit dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fa402-118">The output shows the `<alias> -> <definition>` format that was introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="fa402-119">Ce format est utilisé uniquement pour les alias qui n'incluent pas de traits d'union, étant donné que les alias avec des traits d'union sont des noms généralement préférés aux surnoms pour les applets de commande et les fonctions.</span><span class="sxs-lookup"><span data-stu-id="fa402-119">This format is used only for aliases that do not include hyphens, because aliases with hyphens are typically preferred names for cmdlets and functions, rather than nicknames.</span></span>

### <span data-ttu-id="fa402-120">Exemple 2 : récupérer des alias par nom</span><span class="sxs-lookup"><span data-stu-id="fa402-120">Example 2: Get aliases by name</span></span>

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

<span data-ttu-id="fa402-121">Cette commande obtient tous les alias qui commencent par GP ou SP, à l’exception des alias qui se terminent par PS.</span><span class="sxs-lookup"><span data-stu-id="fa402-121">This command gets all aliases that begin with gp or sp, except for aliases that end with ps.</span></span>

### <span data-ttu-id="fa402-122">Exemple 3 : obtenir des alias pour une applet de commande</span><span class="sxs-lookup"><span data-stu-id="fa402-122">Example 3: Get aliases for a cmdlet</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

<span data-ttu-id="fa402-123">Cette commande obtient les alias de l'applet de commande Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="fa402-123">This command gets the aliases for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="fa402-124">Par défaut, l’applet de commande **obtenir-alias** obtient le nom de l’élément lorsque vous connaissez l’alias.</span><span class="sxs-lookup"><span data-stu-id="fa402-124">By default, the **Get-Alias** cmdlet gets the item name when you know the alias.</span></span>
<span data-ttu-id="fa402-125">Le paramètre de *définition* obtient l’alias quand vous connaissez le nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="fa402-125">The *Definition* parameter gets the alias when you know the item name.</span></span>

### <span data-ttu-id="fa402-126">Exemple 4 : récupérer des alias par propriété</span><span class="sxs-lookup"><span data-stu-id="fa402-126">Example 4: Get aliases by property</span></span>

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

<span data-ttu-id="fa402-127">Cette commande obtient tous les alias dans lesquels la valeur de la propriété Options est ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="fa402-127">This command gets all aliases in which the value of the Options property is ReadOnly.</span></span>
<span data-ttu-id="fa402-128">Cette commande offre un moyen rapide de rechercher les alias intégrés à PowerShell, car ils possèdent l’option ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="fa402-128">This command provides a quick way to find the aliases that are built into PowerShell, because they have the ReadOnly option.</span></span>

<span data-ttu-id="fa402-129">Options n’est qu’une des propriétés des objets AliasInfo que obtient **-alias** .</span><span class="sxs-lookup"><span data-stu-id="fa402-129">Options is just one property of the AliasInfo objects that **Get-Alias** gets.</span></span>
<span data-ttu-id="fa402-130">Pour rechercher toutes les propriétés et méthodes des objets AliasInfo, tapez `Get-Alias | get-member` .</span><span class="sxs-lookup"><span data-stu-id="fa402-130">To find all properties and methods of AliasInfo objects, type `Get-Alias | get-member`.</span></span>

### <span data-ttu-id="fa402-131">Exemple 5 : récupérer des alias par nom et filtrer par lettre initiale</span><span class="sxs-lookup"><span data-stu-id="fa402-131">Example 5: Get aliases by name and filter by beginning letter</span></span>

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

<span data-ttu-id="fa402-132">Cet exemple obtient les alias des commandes qui ont des noms se terminant par « -PSSession », à l'exception de ceux qui commencent par « e ».</span><span class="sxs-lookup"><span data-stu-id="fa402-132">This example gets aliases for commands that have names that end in "-PSSession", except for those that begin with "e".</span></span>

<span data-ttu-id="fa402-133">La commande utilise le paramètre *scope* pour appliquer la commande dans l’étendue globale.</span><span class="sxs-lookup"><span data-stu-id="fa402-133">The command uses the *Scope* parameter to apply the command in the global scope.</span></span>
<span data-ttu-id="fa402-134">Cela est utile dans les scripts quand vous souhaitez obtenir les alias figurant dans la session.</span><span class="sxs-lookup"><span data-stu-id="fa402-134">This is useful in scripts when you want to get the aliases in the session.</span></span>

## <span data-ttu-id="fa402-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fa402-135">PARAMETERS</span></span>

### <span data-ttu-id="fa402-136">-Definition</span><span class="sxs-lookup"><span data-stu-id="fa402-136">-Definition</span></span>

<span data-ttu-id="fa402-137">Obtient les alias pour l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="fa402-137">Gets the aliases for the specified item.</span></span>
<span data-ttu-id="fa402-138">Entrez le nom d'une applet de commande, d'une fonction, d'un script, d'un fichier ou d'un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="fa402-138">Enter the name of a cmdlet, function, script, file, or executable file.</span></span>

<span data-ttu-id="fa402-139">Ce paramètre est appelé *définition* , car il recherche le nom de l’élément dans la propriété de définition de l’objet alias.</span><span class="sxs-lookup"><span data-stu-id="fa402-139">This parameter is called *Definition* , because it searches for the item name in the Definition property of the alias object.</span></span>

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

### <span data-ttu-id="fa402-140">-Exclude</span><span class="sxs-lookup"><span data-stu-id="fa402-140">-Exclude</span></span>

<span data-ttu-id="fa402-141">Omet les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="fa402-141">Omits the specified items.</span></span>
<span data-ttu-id="fa402-142">La valeur de ce paramètre qualifie les paramètres Name et Definition.</span><span class="sxs-lookup"><span data-stu-id="fa402-142">The value of this parameter qualifies the Name and Definition parameters.</span></span>
<span data-ttu-id="fa402-143">Entrez un nom, une définition ou un modèle, tel que « s\* ».</span><span class="sxs-lookup"><span data-stu-id="fa402-143">Enter a name, a definition, or a pattern, such as "s\*".</span></span>
<span data-ttu-id="fa402-144">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fa402-144">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="fa402-145">-Name</span><span class="sxs-lookup"><span data-stu-id="fa402-145">-Name</span></span>

<span data-ttu-id="fa402-146">Spécifie les alias que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="fa402-146">Specifies the aliases that this cmdlet gets.</span></span>
<span data-ttu-id="fa402-147">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fa402-147">Wildcards are permitted.</span></span>
<span data-ttu-id="fa402-148">Par défaut, `Get-Alias` récupère tous les alias définis pour la session active.</span><span class="sxs-lookup"><span data-stu-id="fa402-148">By default, `Get-Alias` retrieves all aliases defined for the current session.</span></span>
<span data-ttu-id="fa402-149">Le **nom du paramètre est facultatif** .</span><span class="sxs-lookup"><span data-stu-id="fa402-149">The parameter name **Name** is optional.</span></span>
<span data-ttu-id="fa402-150">Vous pouvez également diriger les noms d’alias vers `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="fa402-150">You can also pipe alias names to `Get-Alias`.</span></span>

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

### <span data-ttu-id="fa402-151">-Étendue</span><span class="sxs-lookup"><span data-stu-id="fa402-151">-Scope</span></span>

<span data-ttu-id="fa402-152">Spécifie l’étendue pour laquelle cette applet de commande obtient des alias.</span><span class="sxs-lookup"><span data-stu-id="fa402-152">Specifies the scope for which this cmdlet gets aliases.</span></span>
<span data-ttu-id="fa402-153">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="fa402-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fa402-154">Global</span><span class="sxs-lookup"><span data-stu-id="fa402-154">Global</span></span>
- <span data-ttu-id="fa402-155">Local</span><span class="sxs-lookup"><span data-stu-id="fa402-155">Local</span></span>
- <span data-ttu-id="fa402-156">Script</span><span class="sxs-lookup"><span data-stu-id="fa402-156">Script</span></span>
- <span data-ttu-id="fa402-157">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)</span><span class="sxs-lookup"><span data-stu-id="fa402-157">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="fa402-158">Local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="fa402-158">Local is the default.</span></span>
<span data-ttu-id="fa402-159">Pour plus d'informations, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="fa402-159">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="fa402-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fa402-160">CommonParameters</span></span>

<span data-ttu-id="fa402-161">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fa402-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fa402-162">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fa402-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fa402-163">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fa402-163">INPUTS</span></span>

### <span data-ttu-id="fa402-164">System.String</span><span class="sxs-lookup"><span data-stu-id="fa402-164">System.String</span></span>

<span data-ttu-id="fa402-165">Vous pouvez diriger les noms d’alias vers la valeur de l' **alias** .</span><span class="sxs-lookup"><span data-stu-id="fa402-165">You can pipe alias names to **Get-Alias** .</span></span>

## <span data-ttu-id="fa402-166">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fa402-166">OUTPUTS</span></span>

### <span data-ttu-id="fa402-167">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="fa402-167">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="fa402-168">La **fonction de récupération d’alias** retourne un objet qui représente chaque alias.</span><span class="sxs-lookup"><span data-stu-id="fa402-168">**Get-Alias** returns an object that represents each alias.</span></span>
<span data-ttu-id="fa402-169">L' **alias « obtenir »** retourne le même objet pour chaque alias, mais PowerShell utilise un format basé sur les flèches pour afficher les noms des alias sans trait d’Union.</span><span class="sxs-lookup"><span data-stu-id="fa402-169">**Get-Alias** returns the same object for every alias, but PowerShell uses an arrow-based format to display the names of non-hyphenated aliases.</span></span>

## <span data-ttu-id="fa402-170">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fa402-170">NOTES</span></span>

- <span data-ttu-id="fa402-171">Pour créer un alias, utilisez Set-Alias ou New-Alias.</span><span class="sxs-lookup"><span data-stu-id="fa402-171">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="fa402-172">Pour supprimer un alias, utilisez Remove-Item.</span><span class="sxs-lookup"><span data-stu-id="fa402-172">To delete an alias, use Remove-Item.</span></span>
- <span data-ttu-id="fa402-173">Le format de nom d'alias basé sur les flèches n'est pas utilisé pour les alias qui comportent un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="fa402-173">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="fa402-174">Ceux-ci sont susceptibles d'être des noms de remplacement par défaut pour les applets de commande et les fonctions, au lieu d'être des abréviations ou des surnoms standard.</span><span class="sxs-lookup"><span data-stu-id="fa402-174">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames.</span></span>

## <span data-ttu-id="fa402-175">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fa402-175">RELATED LINKS</span></span>

[<span data-ttu-id="fa402-176">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="fa402-176">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="fa402-177">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="fa402-177">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="fa402-178">New-Alias</span><span class="sxs-lookup"><span data-stu-id="fa402-178">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="fa402-179">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="fa402-179">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="fa402-180">Fournisseur Alias</span><span class="sxs-lookup"><span data-stu-id="fa402-180">Alias Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[<span data-ttu-id="fa402-181">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="fa402-181">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)
