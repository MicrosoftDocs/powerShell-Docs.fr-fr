---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 67bcb45ec9e23ba9d4f4ae38d378d2c48180666b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93202006"
---
# <span data-ttu-id="07389-103">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="07389-103">Import-Alias</span></span>

## <span data-ttu-id="07389-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="07389-104">SYNOPSIS</span></span>
<span data-ttu-id="07389-105">Importe une liste d'alias à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="07389-105">Imports an alias list from a file.</span></span>

## <span data-ttu-id="07389-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="07389-106">SYNTAX</span></span>

### <span data-ttu-id="07389-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="07389-107">ByPath (Default)</span></span>

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="07389-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="07389-108">ByLiteralPath</span></span>

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="07389-109">Description</span><span class="sxs-lookup"><span data-stu-id="07389-109">DESCRIPTION</span></span>

<span data-ttu-id="07389-110">L' `Import-Alias` applet de commande importe une liste d’alias à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="07389-110">The `Import-Alias` cmdlet imports an alias list from a file.</span></span>

<span data-ttu-id="07389-111">À compter de Windows PowerShell 3,0, en tant que fonctionnalité de sécurité, `Import-Alias` ne remplace pas les alias existants par défaut.</span><span class="sxs-lookup"><span data-stu-id="07389-111">Beginning in Windows PowerShell 3.0, as a security feature, `Import-Alias` does not overwrite existing aliases by default.</span></span>
<span data-ttu-id="07389-112">Pour remplacer un alias existant, après avoir garanti la sécurité du contenu du fichier alias, utilisez le paramètre **Force** .</span><span class="sxs-lookup"><span data-stu-id="07389-112">To overwrite an existing alias, after assuring that the contents of the alias file is safe, use the **Force** parameter.</span></span>

## <span data-ttu-id="07389-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="07389-113">EXAMPLES</span></span>

### <span data-ttu-id="07389-114">Exemple 1 : importer des alias à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="07389-114">Example 1: Import aliases from a file</span></span>

```powershell
Import-Alias test.txt
```

<span data-ttu-id="07389-115">Cette commande importe les informations d'alias à partir d'un fichier nommé test.txt.</span><span class="sxs-lookup"><span data-stu-id="07389-115">This command imports alias information from a file named test.txt.</span></span>

## <span data-ttu-id="07389-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="07389-116">PARAMETERS</span></span>

### <span data-ttu-id="07389-117">-Force</span><span class="sxs-lookup"><span data-stu-id="07389-117">-Force</span></span>

<span data-ttu-id="07389-118">Permet à l'applet de commande d'importer un alias qui est déjà défini ou en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="07389-118">Allows the cmdlet to import an alias that is already defined or is read only.</span></span>
<span data-ttu-id="07389-119">Vous pouvez utiliser la commande suivante pour afficher des informations sur les alias actuellement définis :</span><span class="sxs-lookup"><span data-stu-id="07389-119">You can use the following command to display information about the currently-defined aliases:</span></span>

`Get-Alias | Select-Object Name, Options`

<span data-ttu-id="07389-120">Si l'alias correspondant est en lecture seule, il s'affichera dans la valeur de la propriété **Options** .</span><span class="sxs-lookup"><span data-stu-id="07389-120">If the corresponding alias is read-only, it will be displayed in the value of the **Options** property.</span></span>

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

### <span data-ttu-id="07389-121">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="07389-121">-LiteralPath</span></span>

<span data-ttu-id="07389-122">Spécifie le chemin d'accès à un fichier qui inclut des informations sur les alias exportés.</span><span class="sxs-lookup"><span data-stu-id="07389-122">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="07389-123">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="07389-123">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="07389-124">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="07389-124">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="07389-125">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="07389-125">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="07389-126">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="07389-126">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="07389-127">-PassThru</span><span class="sxs-lookup"><span data-stu-id="07389-127">-PassThru</span></span>

<span data-ttu-id="07389-128">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="07389-128">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="07389-129">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="07389-129">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="07389-130">-Path</span><span class="sxs-lookup"><span data-stu-id="07389-130">-Path</span></span>

<span data-ttu-id="07389-131">Spécifie le chemin d'accès à un fichier qui inclut des informations sur les alias exportés.</span><span class="sxs-lookup"><span data-stu-id="07389-131">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="07389-132">Les caractères génériques sont autorisés, mais ils doivent correspondre à un nom unique.</span><span class="sxs-lookup"><span data-stu-id="07389-132">Wildcards are allowed but they must resolve to a single name.</span></span>

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

### <span data-ttu-id="07389-133">-Étendue</span><span class="sxs-lookup"><span data-stu-id="07389-133">-Scope</span></span>

<span data-ttu-id="07389-134">Spécifie l'étendue dans laquelle les alias sont importés.</span><span class="sxs-lookup"><span data-stu-id="07389-134">Specifies the scope into which the aliases are imported.</span></span>
<span data-ttu-id="07389-135">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="07389-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="07389-136">Global</span><span class="sxs-lookup"><span data-stu-id="07389-136">Global</span></span>
- <span data-ttu-id="07389-137">Local</span><span class="sxs-lookup"><span data-stu-id="07389-137">Local</span></span>
- <span data-ttu-id="07389-138">Script</span><span class="sxs-lookup"><span data-stu-id="07389-138">Script</span></span>
- <span data-ttu-id="07389-139">Nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent)</span><span class="sxs-lookup"><span data-stu-id="07389-139">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="07389-140">La valeur par défaut est local.</span><span class="sxs-lookup"><span data-stu-id="07389-140">The default is Local.</span></span>
<span data-ttu-id="07389-141">Pour plus d'informations, consultez about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="07389-141">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="07389-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="07389-142">-Confirm</span></span>

<span data-ttu-id="07389-143">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="07389-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="07389-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="07389-144">-WhatIf</span></span>

<span data-ttu-id="07389-145">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="07389-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="07389-146">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="07389-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="07389-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07389-147">CommonParameters</span></span>

<span data-ttu-id="07389-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07389-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07389-149">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="07389-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07389-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="07389-150">INPUTS</span></span>

### <span data-ttu-id="07389-151">System.String</span><span class="sxs-lookup"><span data-stu-id="07389-151">System.String</span></span>

<span data-ttu-id="07389-152">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="07389-152">You can pipe a string that contains a path to `Import-Alias`.</span></span>

## <span data-ttu-id="07389-153">SORTIES</span><span class="sxs-lookup"><span data-stu-id="07389-153">OUTPUTS</span></span>

### <span data-ttu-id="07389-154">None ou System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="07389-154">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="07389-155">Quand vous utilisez le paramètre **PassThru** , `Import-Alias` retourne un objet **System. Management. Automation. AliasInfo** qui représente l’alias.</span><span class="sxs-lookup"><span data-stu-id="07389-155">When you use the **Passthru** parameter, `Import-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="07389-156">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="07389-156">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="07389-157">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="07389-157">NOTES</span></span>

## <span data-ttu-id="07389-158">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="07389-158">RELATED LINKS</span></span>

[<span data-ttu-id="07389-159">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="07389-159">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="07389-160">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="07389-160">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="07389-161">New-Alias</span><span class="sxs-lookup"><span data-stu-id="07389-161">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="07389-162">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="07389-162">Set-Alias</span></span>](Set-Alias.md)
