---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: 66a7b82b56028a4801a3aa8c93cd46460a5353ce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203782"
---
# <span data-ttu-id="a3d36-103">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="a3d36-103">Rename-Item</span></span>

## <span data-ttu-id="a3d36-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a3d36-104">SYNOPSIS</span></span>
<span data-ttu-id="a3d36-105">Renomme un élément dans un espace de noms de fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3d36-105">Renames an item in a PowerShell provider namespace.</span></span>

## <span data-ttu-id="a3d36-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a3d36-106">SYNTAX</span></span>

### <span data-ttu-id="a3d36-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a3d36-107">ByPath (Default)</span></span>

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="a3d36-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="a3d36-108">ByLiteralPath</span></span>

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="a3d36-109">Description</span><span class="sxs-lookup"><span data-stu-id="a3d36-109">DESCRIPTION</span></span>

<span data-ttu-id="a3d36-110">L' `Rename-Item` applet de commande modifie le nom d’un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="a3d36-110">The `Rename-Item` cmdlet changes the name of a specified item.</span></span> <span data-ttu-id="a3d36-111">Cette applet de commande n’affecte pas le contenu de l’élément qui est renommé.</span><span class="sxs-lookup"><span data-stu-id="a3d36-111">This cmdlet does not affect the content of the item being renamed.</span></span>

<span data-ttu-id="a3d36-112">Vous ne pouvez pas utiliser `Rename-Item` pour déplacer un élément, par exemple en spécifiant un chemin d’accès avec le nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="a3d36-112">You can't use `Rename-Item` to move an item, such as by specifying a path together with the new name.</span></span> <span data-ttu-id="a3d36-113">Pour déplacer et renommer un élément, utilisez l' `Move-Item` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a3d36-113">To move and rename an item, use the `Move-Item` cmdlet.</span></span>

## <span data-ttu-id="a3d36-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a3d36-114">EXAMPLES</span></span>

### <span data-ttu-id="a3d36-115">Exemple 1 : renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="a3d36-115">Example 1: Rename a file</span></span>

<span data-ttu-id="a3d36-116">Cette commande renomme le fichier `daily_file.txt` `monday_file.txt` .</span><span class="sxs-lookup"><span data-stu-id="a3d36-116">This command renames the file `daily_file.txt` to `monday_file.txt`.</span></span>

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### <span data-ttu-id="a3d36-117">Exemple 2 : renommer et déplacer un élément</span><span class="sxs-lookup"><span data-stu-id="a3d36-117">Example 2: Rename and move an item</span></span>

<span data-ttu-id="a3d36-118">Vous ne pouvez pas utiliser `Rename-Item` à la fois pour renommer et déplacer un élément.</span><span class="sxs-lookup"><span data-stu-id="a3d36-118">You can't use `Rename-Item` to both rename and move an item.</span></span> <span data-ttu-id="a3d36-119">Plus précisément, vous ne pouvez pas fournir de chemin d’accès pour la valeur du paramètre **NewName** , sauf si le chemin d’accès est identique au chemin d’accès spécifié dans le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="a3d36-119">Specifically, you can't supply a path for the value of the **NewName** parameter, unless the path is identical to the path specified in the **Path** parameter.</span></span> <span data-ttu-id="a3d36-120">Sinon, seul un nouveau nom est autorisé.</span><span class="sxs-lookup"><span data-stu-id="a3d36-120">Otherwise, only a new name is permitted.</span></span>

<span data-ttu-id="a3d36-121">Cet exemple tente de renommer le `project.txt` fichier du répertoire actif dans `old-project.txt` le `D:\Archive` répertoire.</span><span class="sxs-lookup"><span data-stu-id="a3d36-121">This example attempts to rename the `project.txt` file in the current directory to `old-project.txt` in the `D:\Archive` directory.</span></span> <span data-ttu-id="a3d36-122">Il en résulte l’erreur indiquée dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="a3d36-122">The result is the error shown in the output.</span></span>

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### <span data-ttu-id="a3d36-123">Exemple 3 : renommer une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="a3d36-123">Example 3: Rename a registry key</span></span>

<span data-ttu-id="a3d36-124">Cet exemple renomme une clé de registre de la **publication** en **marketing** .</span><span class="sxs-lookup"><span data-stu-id="a3d36-124">This example renames a registry key from **Advertising** to **Marketing** .</span></span> <span data-ttu-id="a3d36-125">Une fois la commande exécutée, la clé est renommée, mais les entrées de Registre qui figurent dans la clé demeurent inchangées.</span><span class="sxs-lookup"><span data-stu-id="a3d36-125">When the command is complete, the key is renamed, but the registry entries in the key are unchanged.</span></span>

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### <span data-ttu-id="a3d36-126">Exemple 4 : renommer plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="a3d36-126">Example 4: Rename multiple files</span></span>

<span data-ttu-id="a3d36-127">Cet exemple renomme tous les `*.txt` fichiers du répertoire actif `*.log` .</span><span class="sxs-lookup"><span data-stu-id="a3d36-127">This example renames all the `*.txt` files in the current directory to `*.log`.</span></span>

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

<span data-ttu-id="a3d36-128">L' `Get-ChildItem` applet de commande obtient tous les fichiers du dossier actif qui ont une `.txt` extension de fichier, puis les dirige vers `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="a3d36-128">The `Get-ChildItem` cmdlet gets all the files in the current folder that have a `.txt` file extension then pipes them to `Rename-Item`.</span></span> <span data-ttu-id="a3d36-129">La valeur de **NewName** est un bloc de script qui s’exécute avant que la valeur ne soit soumise au paramètre **NewName** .</span><span class="sxs-lookup"><span data-stu-id="a3d36-129">The value of **NewName** is a script block that runs before the value is submitted to the **NewName** parameter.</span></span>

<span data-ttu-id="a3d36-130">Dans le bloc de script, la `$_` variable automatique représente chaque objet fichier tel qu’il arrive à la commande via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="a3d36-130">In the script block, the `$_` automatic variable represents each file object as it comes to the command through the pipeline.</span></span> <span data-ttu-id="a3d36-131">Le bloc de script utilise l' `-replace` opérateur pour remplacer l’extension de fichier de chaque fichier par `.log` .</span><span class="sxs-lookup"><span data-stu-id="a3d36-131">The script block uses the `-replace` operator to replace the file extension of each file with `.log`.</span></span> <span data-ttu-id="a3d36-132">Notez que la correspondance à l’aide de l’opérateur ne respecte `-replace` pas la casse.</span><span class="sxs-lookup"><span data-stu-id="a3d36-132">Notice that matching using the `-replace` operator is not case sensitive.</span></span>

## <span data-ttu-id="a3d36-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a3d36-133">PARAMETERS</span></span>

### <span data-ttu-id="a3d36-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="a3d36-134">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a3d36-135">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3d36-135">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="a3d36-136">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="a3d36-136">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a3d36-137">-Force</span><span class="sxs-lookup"><span data-stu-id="a3d36-137">-Force</span></span>

<span data-ttu-id="a3d36-138">Force l’applet de commande à renommer des éléments qui ne peuvent pas être modifiés autrement, tels que des fichiers cachés ou en lecture seule ou des alias ou des variables en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="a3d36-138">Forces the cmdlet to rename items that can't otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="a3d36-139">L’applet de commande ne peut pas modifier les alias ou variables constants.</span><span class="sxs-lookup"><span data-stu-id="a3d36-139">The cmdlet can't change constant aliases or variables.</span></span>
<span data-ttu-id="a3d36-140">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="a3d36-140">Implementation varies from provider to provider.</span></span> <span data-ttu-id="a3d36-141">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a3d36-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="a3d36-142">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a3d36-142">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="a3d36-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a3d36-143">-LiteralPath</span></span>

<span data-ttu-id="a3d36-144">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="a3d36-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a3d36-145">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="a3d36-145">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a3d36-146">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="a3d36-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a3d36-147">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a3d36-147">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a3d36-148">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="a3d36-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a3d36-149">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="a3d36-149">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a3d36-150">-NewName</span><span class="sxs-lookup"><span data-stu-id="a3d36-150">-NewName</span></span>

<span data-ttu-id="a3d36-151">Spécifie le nouveau nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="a3d36-151">Specifies the new name of the item.</span></span> <span data-ttu-id="a3d36-152">Entrez uniquement un nom, et non un chemin d’accès et un nom.</span><span class="sxs-lookup"><span data-stu-id="a3d36-152">Enter only a name, not a path and name.</span></span> <span data-ttu-id="a3d36-153">Si vous entrez un chemin d’accès différent du chemin d’accès spécifié dans le paramètre **path** , `Rename-Item` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="a3d36-153">If you enter a path that differs from the path that is specified in the **Path** parameter, `Rename-Item` generates an error.</span></span>
<span data-ttu-id="a3d36-154">Pour renommer et déplacer un élément, utilisez `Move-Item` .</span><span class="sxs-lookup"><span data-stu-id="a3d36-154">To rename and move an item, use `Move-Item`.</span></span>

<span data-ttu-id="a3d36-155">Vous ne pouvez pas utiliser de caractères génériques dans la valeur du paramètre **NewName** .</span><span class="sxs-lookup"><span data-stu-id="a3d36-155">You can't use wildcard characters in the value of the **NewName** parameter.</span></span> <span data-ttu-id="a3d36-156">Pour spécifier un nom pour plusieurs fichiers, utilisez l’opérateur **Replace** dans une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="a3d36-156">To specify a name for multiple files, use the **Replace** operator in a regular expression.</span></span> <span data-ttu-id="a3d36-157">Pour plus d’informations sur l’opérateur Replace, consultez [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="a3d36-157">For more information about the Replace operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span></span>

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

### <span data-ttu-id="a3d36-158">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a3d36-158">-PassThru</span></span>

<span data-ttu-id="a3d36-159">Retourne un objet qui représente l’élément dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="a3d36-159">Returns an object that represents the item to the pipeline.</span></span> <span data-ttu-id="a3d36-160">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="a3d36-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a3d36-161">-Path</span><span class="sxs-lookup"><span data-stu-id="a3d36-161">-Path</span></span>

<span data-ttu-id="a3d36-162">Spécifie le chemin d’accès de l’élément à renommer.</span><span class="sxs-lookup"><span data-stu-id="a3d36-162">Specifies the path of the item to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a3d36-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a3d36-163">-Confirm</span></span>

<span data-ttu-id="a3d36-164">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a3d36-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a3d36-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a3d36-165">-WhatIf</span></span>

<span data-ttu-id="a3d36-166">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a3d36-166">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a3d36-167">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a3d36-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a3d36-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a3d36-168">CommonParameters</span></span>

<span data-ttu-id="a3d36-169">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a3d36-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a3d36-170">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a3d36-170">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a3d36-171">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a3d36-171">INPUTS</span></span>

### <span data-ttu-id="a3d36-172">System.String</span><span class="sxs-lookup"><span data-stu-id="a3d36-172">System.String</span></span>

<span data-ttu-id="a3d36-173">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a3d36-173">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="a3d36-174">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a3d36-174">OUTPUTS</span></span>

### <span data-ttu-id="a3d36-175">Aucun ou un objet qui représente l’élément renommé.</span><span class="sxs-lookup"><span data-stu-id="a3d36-175">None or an object that represents the renamed item.</span></span>

<span data-ttu-id="a3d36-176">Cette applet de commande génère un objet qui représente l’élément renommé, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="a3d36-176">This cmdlet generates an object that represents the renamed item, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="a3d36-177">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="a3d36-177">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a3d36-178">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a3d36-178">NOTES</span></span>

<span data-ttu-id="a3d36-179">`Rename-Item` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a3d36-179">`Rename-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a3d36-180">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="a3d36-180">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="a3d36-181">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a3d36-181">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a3d36-182">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a3d36-182">RELATED LINKS</span></span>

[<span data-ttu-id="a3d36-183">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="a3d36-183">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="a3d36-184">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="a3d36-184">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="a3d36-185">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a3d36-185">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="a3d36-186">Get-Item</span><span class="sxs-lookup"><span data-stu-id="a3d36-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="a3d36-187">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="a3d36-187">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="a3d36-188">Move-Item</span><span class="sxs-lookup"><span data-stu-id="a3d36-188">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="a3d36-189">New-Item</span><span class="sxs-lookup"><span data-stu-id="a3d36-189">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="a3d36-190">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="a3d36-190">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="a3d36-191">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a3d36-191">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="a3d36-192">Set-Item</span><span class="sxs-lookup"><span data-stu-id="a3d36-192">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="a3d36-193">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a3d36-193">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
