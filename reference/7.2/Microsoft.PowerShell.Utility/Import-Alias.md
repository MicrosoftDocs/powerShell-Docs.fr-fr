---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 20bc5d141b68cab19374afbe44b3472c72bf69bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595474"
---
# <span data-ttu-id="912bd-102">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="912bd-102">Import-Alias</span></span>

## <span data-ttu-id="912bd-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="912bd-103">SYNOPSIS</span></span>
<span data-ttu-id="912bd-104">Importe une liste d'alias à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="912bd-104">Imports an alias list from a file.</span></span>

## <span data-ttu-id="912bd-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="912bd-105">SYNTAX</span></span>

### <span data-ttu-id="912bd-106">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="912bd-106">ByPath (Default)</span></span>

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="912bd-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="912bd-107">ByLiteralPath</span></span>

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="912bd-108">Description</span><span class="sxs-lookup"><span data-stu-id="912bd-108">DESCRIPTION</span></span>

<span data-ttu-id="912bd-109">L' `Import-Alias` applet de commande importe une liste d’alias à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="912bd-109">The `Import-Alias` cmdlet imports an alias list from a file.</span></span>

<span data-ttu-id="912bd-110">À compter de Windows PowerShell 3,0, en tant que fonctionnalité de sécurité, `Import-Alias` ne remplace pas les alias existants par défaut.</span><span class="sxs-lookup"><span data-stu-id="912bd-110">Beginning in Windows PowerShell 3.0, as a security feature, `Import-Alias` does not overwrite existing aliases by default.</span></span>
<span data-ttu-id="912bd-111">Pour remplacer un alias existant, après avoir garanti la sécurité du contenu du fichier alias, utilisez le paramètre **Force**.</span><span class="sxs-lookup"><span data-stu-id="912bd-111">To overwrite an existing alias, after assuring that the contents of the alias file is safe, use the **Force** parameter.</span></span>

## <span data-ttu-id="912bd-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="912bd-112">EXAMPLES</span></span>

### <span data-ttu-id="912bd-113">Exemple 1 : importer des alias à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="912bd-113">Example 1: Import aliases from a file</span></span>

```powershell
Import-Alias test.txt
```

<span data-ttu-id="912bd-114">Cette commande importe les informations d'alias à partir d'un fichier nommé test.txt.</span><span class="sxs-lookup"><span data-stu-id="912bd-114">This command imports alias information from a file named test.txt.</span></span>

## <span data-ttu-id="912bd-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="912bd-115">PARAMETERS</span></span>

### <span data-ttu-id="912bd-116">-Force</span><span class="sxs-lookup"><span data-stu-id="912bd-116">-Force</span></span>

<span data-ttu-id="912bd-117">Permet à l'applet de commande d'importer un alias qui est déjà défini ou en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="912bd-117">Allows the cmdlet to import an alias that is already defined or is read only.</span></span>
<span data-ttu-id="912bd-118">Vous pouvez utiliser la commande suivante pour afficher des informations sur les alias actuellement définis :</span><span class="sxs-lookup"><span data-stu-id="912bd-118">You can use the following command to display information about the currently-defined aliases:</span></span>

`Get-Alias | Select-Object Name, Options`

<span data-ttu-id="912bd-119">Si l'alias correspondant est en lecture seule, il s'affichera dans la valeur de la propriété **Options**.</span><span class="sxs-lookup"><span data-stu-id="912bd-119">If the corresponding alias is read-only, it will be displayed in the value of the **Options** property.</span></span>

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

### <span data-ttu-id="912bd-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="912bd-120">-LiteralPath</span></span>

<span data-ttu-id="912bd-121">Spécifie le chemin d'accès à un fichier qui inclut des informations sur les alias exportés.</span><span class="sxs-lookup"><span data-stu-id="912bd-121">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="912bd-122">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="912bd-122">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="912bd-123">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="912bd-123">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="912bd-124">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="912bd-124">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="912bd-125">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="912bd-125">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="912bd-126">-PassThru</span><span class="sxs-lookup"><span data-stu-id="912bd-126">-PassThru</span></span>

<span data-ttu-id="912bd-127">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="912bd-127">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="912bd-128">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="912bd-128">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="912bd-129">-Path</span><span class="sxs-lookup"><span data-stu-id="912bd-129">-Path</span></span>

<span data-ttu-id="912bd-130">Spécifie le chemin d'accès à un fichier qui inclut des informations sur les alias exportés.</span><span class="sxs-lookup"><span data-stu-id="912bd-130">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="912bd-131">Les caractères génériques sont autorisés, mais ils doivent correspondre à un nom unique.</span><span class="sxs-lookup"><span data-stu-id="912bd-131">Wildcards are allowed but they must resolve to a single name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="912bd-132">-Étendue</span><span class="sxs-lookup"><span data-stu-id="912bd-132">-Scope</span></span>

<span data-ttu-id="912bd-133">Spécifie l'étendue dans laquelle les alias sont importés.</span><span class="sxs-lookup"><span data-stu-id="912bd-133">Specifies the scope into which the aliases are imported.</span></span>
<span data-ttu-id="912bd-134">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="912bd-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="912bd-135">Global</span><span class="sxs-lookup"><span data-stu-id="912bd-135">Global</span></span>
- <span data-ttu-id="912bd-136">Local</span><span class="sxs-lookup"><span data-stu-id="912bd-136">Local</span></span>
- <span data-ttu-id="912bd-137">Script</span><span class="sxs-lookup"><span data-stu-id="912bd-137">Script</span></span>
- <span data-ttu-id="912bd-138">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)</span><span class="sxs-lookup"><span data-stu-id="912bd-138">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="912bd-139">La valeur par défaut est local.</span><span class="sxs-lookup"><span data-stu-id="912bd-139">The default is Local.</span></span>
<span data-ttu-id="912bd-140">Pour plus d'informations, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="912bd-140">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="912bd-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="912bd-141">-Confirm</span></span>

<span data-ttu-id="912bd-142">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="912bd-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="912bd-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="912bd-143">-WhatIf</span></span>

<span data-ttu-id="912bd-144">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="912bd-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="912bd-145">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="912bd-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="912bd-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="912bd-146">CommonParameters</span></span>

<span data-ttu-id="912bd-147">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="912bd-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="912bd-148">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="912bd-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="912bd-149">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="912bd-149">INPUTS</span></span>

### <span data-ttu-id="912bd-150">System.String</span><span class="sxs-lookup"><span data-stu-id="912bd-150">System.String</span></span>

<span data-ttu-id="912bd-151">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="912bd-151">You can pipe a string that contains a path to `Import-Alias`.</span></span>

## <span data-ttu-id="912bd-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="912bd-152">OUTPUTS</span></span>

### <span data-ttu-id="912bd-153">None ou System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="912bd-153">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="912bd-154">Quand vous utilisez le paramètre **PassThru** , `Import-Alias` retourne un objet **System. Management. Automation. AliasInfo** qui représente l’alias.</span><span class="sxs-lookup"><span data-stu-id="912bd-154">When you use the **Passthru** parameter, `Import-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="912bd-155">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="912bd-155">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="912bd-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="912bd-156">NOTES</span></span>

## <span data-ttu-id="912bd-157">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="912bd-157">RELATED LINKS</span></span>

[<span data-ttu-id="912bd-158">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="912bd-158">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="912bd-159">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="912bd-159">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="912bd-160">New-Alias</span><span class="sxs-lookup"><span data-stu-id="912bd-160">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="912bd-161">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="912bd-161">Set-Alias</span></span>](Set-Alias.md)

