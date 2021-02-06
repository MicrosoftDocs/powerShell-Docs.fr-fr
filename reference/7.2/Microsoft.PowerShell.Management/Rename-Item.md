---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: dec5c2c905486110e4885f29d236ab41d945fb96
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596119"
---
# <span data-ttu-id="dbd74-102">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="dbd74-102">Rename-Item</span></span>

## <span data-ttu-id="dbd74-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="dbd74-103">SYNOPSIS</span></span>
<span data-ttu-id="dbd74-104">Renomme un élément dans un espace de noms de fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbd74-104">Renames an item in a PowerShell provider namespace.</span></span>

## <span data-ttu-id="dbd74-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="dbd74-105">SYNTAX</span></span>

### <span data-ttu-id="dbd74-106">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="dbd74-106">ByPath (Default)</span></span>

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="dbd74-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="dbd74-107">ByLiteralPath</span></span>

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="dbd74-108">Description</span><span class="sxs-lookup"><span data-stu-id="dbd74-108">DESCRIPTION</span></span>

<span data-ttu-id="dbd74-109">L' `Rename-Item` applet de commande modifie le nom d’un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="dbd74-109">The `Rename-Item` cmdlet changes the name of a specified item.</span></span> <span data-ttu-id="dbd74-110">Cette applet de commande n’affecte pas le contenu de l’élément qui est renommé.</span><span class="sxs-lookup"><span data-stu-id="dbd74-110">This cmdlet does not affect the content of the item being renamed.</span></span>

<span data-ttu-id="dbd74-111">Vous ne pouvez pas utiliser `Rename-Item` pour déplacer un élément, par exemple en spécifiant un chemin d’accès avec le nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="dbd74-111">You can't use `Rename-Item` to move an item, such as by specifying a path together with the new name.</span></span> <span data-ttu-id="dbd74-112">Pour déplacer et renommer un élément, utilisez l' `Move-Item` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dbd74-112">To move and rename an item, use the `Move-Item` cmdlet.</span></span>

## <span data-ttu-id="dbd74-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="dbd74-113">EXAMPLES</span></span>

### <span data-ttu-id="dbd74-114">Exemple 1 : renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="dbd74-114">Example 1: Rename a file</span></span>

<span data-ttu-id="dbd74-115">Cette commande renomme le fichier `daily_file.txt` `monday_file.txt` .</span><span class="sxs-lookup"><span data-stu-id="dbd74-115">This command renames the file `daily_file.txt` to `monday_file.txt`.</span></span>

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### <span data-ttu-id="dbd74-116">Exemple 2 : renommer et déplacer un élément</span><span class="sxs-lookup"><span data-stu-id="dbd74-116">Example 2: Rename and move an item</span></span>

<span data-ttu-id="dbd74-117">Vous ne pouvez pas utiliser `Rename-Item` à la fois pour renommer et déplacer un élément.</span><span class="sxs-lookup"><span data-stu-id="dbd74-117">You can't use `Rename-Item` to both rename and move an item.</span></span> <span data-ttu-id="dbd74-118">Plus précisément, vous ne pouvez pas fournir de chemin d’accès pour la valeur du paramètre **NewName** , sauf si le chemin d’accès est identique au chemin d’accès spécifié dans le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="dbd74-118">Specifically, you can't supply a path for the value of the **NewName** parameter, unless the path is identical to the path specified in the **Path** parameter.</span></span> <span data-ttu-id="dbd74-119">Sinon, seul un nouveau nom est autorisé.</span><span class="sxs-lookup"><span data-stu-id="dbd74-119">Otherwise, only a new name is permitted.</span></span>

<span data-ttu-id="dbd74-120">Cet exemple tente de renommer le `project.txt` fichier du répertoire actif dans `old-project.txt` le `D:\Archive` répertoire.</span><span class="sxs-lookup"><span data-stu-id="dbd74-120">This example attempts to rename the `project.txt` file in the current directory to `old-project.txt` in the `D:\Archive` directory.</span></span> <span data-ttu-id="dbd74-121">Il en résulte l’erreur indiquée dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="dbd74-121">The result is the error shown in the output.</span></span>

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

### <span data-ttu-id="dbd74-122">Exemple 3 : renommer une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="dbd74-122">Example 3: Rename a registry key</span></span>

<span data-ttu-id="dbd74-123">Cet exemple renomme une clé de registre de la **publication** en **marketing**.</span><span class="sxs-lookup"><span data-stu-id="dbd74-123">This example renames a registry key from **Advertising** to **Marketing**.</span></span> <span data-ttu-id="dbd74-124">Une fois la commande exécutée, la clé est renommée, mais les entrées de Registre qui figurent dans la clé demeurent inchangées.</span><span class="sxs-lookup"><span data-stu-id="dbd74-124">When the command is complete, the key is renamed, but the registry entries in the key are unchanged.</span></span>

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### <span data-ttu-id="dbd74-125">Exemple 4 : renommer plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="dbd74-125">Example 4: Rename multiple files</span></span>

<span data-ttu-id="dbd74-126">Cet exemple renomme tous les `*.txt` fichiers du répertoire actif `*.log` .</span><span class="sxs-lookup"><span data-stu-id="dbd74-126">This example renames all the `*.txt` files in the current directory to `*.log`.</span></span>

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

<span data-ttu-id="dbd74-127">L' `Get-ChildItem` applet de commande obtient tous les fichiers du dossier actif qui ont une `.txt` extension de fichier, puis les dirige vers `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="dbd74-127">The `Get-ChildItem` cmdlet gets all the files in the current folder that have a `.txt` file extension then pipes them to `Rename-Item`.</span></span> <span data-ttu-id="dbd74-128">La valeur de **NewName** est un bloc de script qui s’exécute avant que la valeur ne soit soumise au paramètre **NewName** .</span><span class="sxs-lookup"><span data-stu-id="dbd74-128">The value of **NewName** is a script block that runs before the value is submitted to the **NewName** parameter.</span></span>

<span data-ttu-id="dbd74-129">Dans le bloc de script, la `$_` variable automatique représente chaque objet fichier tel qu’il arrive à la commande via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="dbd74-129">In the script block, the `$_` automatic variable represents each file object as it comes to the command through the pipeline.</span></span> <span data-ttu-id="dbd74-130">Le bloc de script utilise l' `-replace` opérateur pour remplacer l’extension de fichier de chaque fichier par `.log` .</span><span class="sxs-lookup"><span data-stu-id="dbd74-130">The script block uses the `-replace` operator to replace the file extension of each file with `.log`.</span></span> <span data-ttu-id="dbd74-131">Notez que la correspondance à l’aide de l’opérateur ne respecte `-replace` pas la casse.</span><span class="sxs-lookup"><span data-stu-id="dbd74-131">Notice that matching using the `-replace` operator is not case sensitive.</span></span>

## <span data-ttu-id="dbd74-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dbd74-132">PARAMETERS</span></span>

### <span data-ttu-id="dbd74-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="dbd74-133">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="dbd74-134">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbd74-134">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="dbd74-135">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="dbd74-135">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="dbd74-136">-Force</span><span class="sxs-lookup"><span data-stu-id="dbd74-136">-Force</span></span>

<span data-ttu-id="dbd74-137">Force l’applet de commande à renommer des éléments qui ne peuvent pas être modifiés autrement, tels que des fichiers cachés ou en lecture seule ou des alias ou des variables en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="dbd74-137">Forces the cmdlet to rename items that can't otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="dbd74-138">L’applet de commande ne peut pas modifier les alias ou variables constants.</span><span class="sxs-lookup"><span data-stu-id="dbd74-138">The cmdlet can't change constant aliases or variables.</span></span>
<span data-ttu-id="dbd74-139">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="dbd74-139">Implementation varies from provider to provider.</span></span> <span data-ttu-id="dbd74-140">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="dbd74-140">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="dbd74-141">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="dbd74-141">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="dbd74-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dbd74-142">-LiteralPath</span></span>

<span data-ttu-id="dbd74-143">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="dbd74-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="dbd74-144">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="dbd74-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="dbd74-145">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="dbd74-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="dbd74-146">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="dbd74-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="dbd74-147">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="dbd74-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="dbd74-148">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="dbd74-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="dbd74-149">-NewName</span><span class="sxs-lookup"><span data-stu-id="dbd74-149">-NewName</span></span>

<span data-ttu-id="dbd74-150">Spécifie le nouveau nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="dbd74-150">Specifies the new name of the item.</span></span> <span data-ttu-id="dbd74-151">Entrez uniquement un nom, et non un chemin d’accès et un nom.</span><span class="sxs-lookup"><span data-stu-id="dbd74-151">Enter only a name, not a path and name.</span></span> <span data-ttu-id="dbd74-152">Si vous entrez un chemin d’accès différent du chemin d’accès spécifié dans le paramètre **path** , `Rename-Item` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="dbd74-152">If you enter a path that differs from the path that is specified in the **Path** parameter, `Rename-Item` generates an error.</span></span>
<span data-ttu-id="dbd74-153">Pour renommer et déplacer un élément, utilisez `Move-Item` .</span><span class="sxs-lookup"><span data-stu-id="dbd74-153">To rename and move an item, use `Move-Item`.</span></span>

<span data-ttu-id="dbd74-154">Vous ne pouvez pas utiliser de caractères génériques dans la valeur du paramètre **NewName** .</span><span class="sxs-lookup"><span data-stu-id="dbd74-154">You can't use wildcard characters in the value of the **NewName** parameter.</span></span> <span data-ttu-id="dbd74-155">Pour spécifier un nom pour plusieurs fichiers, utilisez l’opérateur **Replace** dans une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="dbd74-155">To specify a name for multiple files, use the **Replace** operator in a regular expression.</span></span> <span data-ttu-id="dbd74-156">Pour plus d’informations sur l’opérateur Replace, consultez [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dbd74-156">For more information about the Replace operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span></span>

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

### <span data-ttu-id="dbd74-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="dbd74-157">-PassThru</span></span>

<span data-ttu-id="dbd74-158">Retourne un objet qui représente l’élément dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="dbd74-158">Returns an object that represents the item to the pipeline.</span></span> <span data-ttu-id="dbd74-159">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="dbd74-159">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="dbd74-160">-Path</span><span class="sxs-lookup"><span data-stu-id="dbd74-160">-Path</span></span>

<span data-ttu-id="dbd74-161">Spécifie le chemin d’accès de l’élément à renommer.</span><span class="sxs-lookup"><span data-stu-id="dbd74-161">Specifies the path of the item to rename.</span></span>

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

### <span data-ttu-id="dbd74-162">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dbd74-162">-Confirm</span></span>

<span data-ttu-id="dbd74-163">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dbd74-163">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dbd74-164">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dbd74-164">-WhatIf</span></span>

<span data-ttu-id="dbd74-165">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dbd74-165">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="dbd74-166">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="dbd74-166">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="dbd74-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dbd74-167">CommonParameters</span></span>

<span data-ttu-id="dbd74-168">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dbd74-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dbd74-169">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="dbd74-169">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="dbd74-170">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="dbd74-170">INPUTS</span></span>

### <span data-ttu-id="dbd74-171">System.String</span><span class="sxs-lookup"><span data-stu-id="dbd74-171">System.String</span></span>

<span data-ttu-id="dbd74-172">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dbd74-172">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="dbd74-173">SORTIES</span><span class="sxs-lookup"><span data-stu-id="dbd74-173">OUTPUTS</span></span>

### <span data-ttu-id="dbd74-174">Aucun ou un objet qui représente l’élément renommé.</span><span class="sxs-lookup"><span data-stu-id="dbd74-174">None or an object that represents the renamed item.</span></span>

<span data-ttu-id="dbd74-175">Cette applet de commande génère un objet qui représente l’élément renommé, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="dbd74-175">This cmdlet generates an object that represents the renamed item, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="dbd74-176">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="dbd74-176">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="dbd74-177">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="dbd74-177">NOTES</span></span>

<span data-ttu-id="dbd74-178">`Rename-Item` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="dbd74-178">`Rename-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="dbd74-179">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="dbd74-179">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="dbd74-180">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="dbd74-180">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="dbd74-181">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="dbd74-181">RELATED LINKS</span></span>

[<span data-ttu-id="dbd74-182">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="dbd74-182">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="dbd74-183">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="dbd74-183">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="dbd74-184">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="dbd74-184">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="dbd74-185">Get-Item</span><span class="sxs-lookup"><span data-stu-id="dbd74-185">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="dbd74-186">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="dbd74-186">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="dbd74-187">Move-Item</span><span class="sxs-lookup"><span data-stu-id="dbd74-187">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="dbd74-188">New-Item</span><span class="sxs-lookup"><span data-stu-id="dbd74-188">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="dbd74-189">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="dbd74-189">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="dbd74-190">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="dbd74-190">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="dbd74-191">Set-Item</span><span class="sxs-lookup"><span data-stu-id="dbd74-191">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="dbd74-192">about_Providers</span><span class="sxs-lookup"><span data-stu-id="dbd74-192">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

