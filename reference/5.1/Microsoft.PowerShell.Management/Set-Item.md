---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: c49cc60ec6ebf3f62a94f5511b55d578337be804
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203517"
---
# <span data-ttu-id="1a984-103">Set-Item</span><span class="sxs-lookup"><span data-stu-id="1a984-103">Set-Item</span></span>

## <span data-ttu-id="1a984-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1a984-104">SYNOPSIS</span></span>
<span data-ttu-id="1a984-105">Remplace la valeur d'un élément par la valeur spécifiée dans la commande.</span><span class="sxs-lookup"><span data-stu-id="1a984-105">Changes the value of an item to the value specified in the command.</span></span>

## <span data-ttu-id="1a984-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1a984-106">SYNTAX</span></span>

### <span data-ttu-id="1a984-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="1a984-107">Path (Default)</span></span>

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="1a984-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1a984-108">LiteralPath</span></span>

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="1a984-109">Description</span><span class="sxs-lookup"><span data-stu-id="1a984-109">DESCRIPTION</span></span>

<span data-ttu-id="1a984-110">L' `Set-Item` applet de commande modifie la valeur d’un élément, telle qu’une variable ou une clé de Registre, en fonction de la valeur spécifiée dans la commande.</span><span class="sxs-lookup"><span data-stu-id="1a984-110">The `Set-Item` cmdlet changes the value of an item, such as a variable or registry key, to the value specified in the command.</span></span>

## <span data-ttu-id="1a984-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1a984-111">EXAMPLES</span></span>

### <span data-ttu-id="1a984-112">Exemple 1 : créer un alias</span><span class="sxs-lookup"><span data-stu-id="1a984-112">Example 1: Create an alias</span></span>

<span data-ttu-id="1a984-113">Cette commande crée un alias de NP pour le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="1a984-113">This command creates an alias of np for Notepad.</span></span>

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### <span data-ttu-id="1a984-114">Exemple 2 : modifier la valeur d’une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="1a984-114">Example 2: Change the value of an environment variable</span></span>

<span data-ttu-id="1a984-115">Cette commande modifie la valeur de la variable d’environnement UserRole en Administrator.</span><span class="sxs-lookup"><span data-stu-id="1a984-115">This command changes the value of the UserRole environment variable to Administrator.</span></span>

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### <span data-ttu-id="1a984-116">Exemple 3 : modifier votre fonction d’invite</span><span class="sxs-lookup"><span data-stu-id="1a984-116">Example 3: Modify your prompt function</span></span>

<span data-ttu-id="1a984-117">Cette commande modifie la fonction d’invite afin qu’elle affiche l’heure avant le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="1a984-117">This command changes the prompt function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### <span data-ttu-id="1a984-118">Exemple 4 : définir les options de votre fonction d’invite</span><span class="sxs-lookup"><span data-stu-id="1a984-118">Example 4: Set options for your prompt function</span></span>

<span data-ttu-id="1a984-119">Cette commande définit les options **options AllScope** et **ReadOnly** pour la fonction prompt.</span><span class="sxs-lookup"><span data-stu-id="1a984-119">This command sets the **AllScope** and **ReadOnly** options for the prompt function.</span></span>
<span data-ttu-id="1a984-120">Cette commande utilise le paramètre dynamique **options** de `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="1a984-120">This command uses the **Options** dynamic parameter of `Set-Item`.</span></span>
<span data-ttu-id="1a984-121">Le paramètre **options** est disponible dans `Set-Item` uniquement lorsque vous l’utilisez avec l' **alias** ou le fournisseur de **fonctions** .</span><span class="sxs-lookup"><span data-stu-id="1a984-121">The **Options** parameter is available in `Set-Item` only when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

## <span data-ttu-id="1a984-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1a984-122">PARAMETERS</span></span>

### <span data-ttu-id="1a984-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="1a984-123">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="1a984-124">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a984-124">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="1a984-125">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="1a984-125">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="1a984-126">-Exclude</span><span class="sxs-lookup"><span data-stu-id="1a984-126">-Exclude</span></span>

<span data-ttu-id="1a984-127">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="1a984-127">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="1a984-128">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="1a984-128">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1a984-129">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="1a984-129">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1a984-130">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1a984-130">Wildcard characters are permitted.</span></span> <span data-ttu-id="1a984-131">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="1a984-131">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1a984-132">-Filter</span><span class="sxs-lookup"><span data-stu-id="1a984-132">-Filter</span></span>

<span data-ttu-id="1a984-133">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="1a984-133">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="1a984-134">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="1a984-134">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="1a984-135">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="1a984-135">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="1a984-136">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="1a984-136">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1a984-137">-Force</span><span class="sxs-lookup"><span data-stu-id="1a984-137">-Force</span></span>

<span data-ttu-id="1a984-138">Force l’applet de commande à définir des éléments qui ne peuvent pas être modifiés autrement, tels que des alias ou des variables en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="1a984-138">Forces the cmdlet to set items that cannot otherwise be changed, such as read-only alias or variables.</span></span> <span data-ttu-id="1a984-139">L’applet de commande ne peut pas modifier des alias ou variables constants.</span><span class="sxs-lookup"><span data-stu-id="1a984-139">The cmdlet cannot change constant aliases or variables.</span></span>
<span data-ttu-id="1a984-140">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="1a984-140">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="1a984-141">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="1a984-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="1a984-142">Même en utilisant le paramètre *force* , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1a984-142">Even using the *Force* parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="1a984-143">-Include</span><span class="sxs-lookup"><span data-stu-id="1a984-143">-Include</span></span>

<span data-ttu-id="1a984-144">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="1a984-144">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="1a984-145">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="1a984-145">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1a984-146">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="1a984-146">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="1a984-147">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1a984-147">Wildcard characters are permitted.</span></span> <span data-ttu-id="1a984-148">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="1a984-148">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1a984-149">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1a984-149">-LiteralPath</span></span>

<span data-ttu-id="1a984-150">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="1a984-150">Specifies a path to one or more locations.</span></span> <span data-ttu-id="1a984-151">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="1a984-151">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="1a984-152">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="1a984-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1a984-153">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="1a984-153">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1a984-154">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="1a984-154">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="1a984-155">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="1a984-155">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1a984-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1a984-156">-PassThru</span></span>

<span data-ttu-id="1a984-157">Passe un objet qui représente l’élément au pipeline.</span><span class="sxs-lookup"><span data-stu-id="1a984-157">Passes an object that represents the item to the pipeline.</span></span>
<span data-ttu-id="1a984-158">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="1a984-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1a984-159">-Path</span><span class="sxs-lookup"><span data-stu-id="1a984-159">-Path</span></span>

<span data-ttu-id="1a984-160">Spécifie le chemin d’accès de l’emplacement des éléments.</span><span class="sxs-lookup"><span data-stu-id="1a984-160">Specifies a path of the location of the items.</span></span>
<span data-ttu-id="1a984-161">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1a984-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="1a984-162">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="1a984-162">-UseTransaction</span></span>

<span data-ttu-id="1a984-163">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="1a984-163">Includes the command in the active transaction.</span></span>
<span data-ttu-id="1a984-164">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="1a984-164">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="1a984-165">Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="1a984-165">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a984-166">-Value</span><span class="sxs-lookup"><span data-stu-id="1a984-166">-Value</span></span>

<span data-ttu-id="1a984-167">Spécifie une nouvelle valeur pour l’élément.</span><span class="sxs-lookup"><span data-stu-id="1a984-167">Specifies a new value for the item.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1a984-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1a984-168">-Confirm</span></span>

<span data-ttu-id="1a984-169">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1a984-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1a984-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1a984-170">-WhatIf</span></span>

<span data-ttu-id="1a984-171">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1a984-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1a984-172">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="1a984-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1a984-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a984-173">CommonParameters</span></span>

<span data-ttu-id="1a984-174">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="1a984-174">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="1a984-175">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="1a984-175">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1a984-176">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1a984-176">INPUTS</span></span>

### <span data-ttu-id="1a984-177">System.Object</span><span class="sxs-lookup"><span data-stu-id="1a984-177">System.Object</span></span>

<span data-ttu-id="1a984-178">Vous pouvez diriger un objet qui représente la nouvelle valeur de l’élément vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1a984-178">You can pipe an object that represents the new value of the item to this cmdlet.</span></span>

## <span data-ttu-id="1a984-179">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1a984-179">OUTPUTS</span></span>

### <span data-ttu-id="1a984-180">Aucun ou un objet représentant l’élément nouveau ou modifié.</span><span class="sxs-lookup"><span data-stu-id="1a984-180">None or an object representing the new or changed item.</span></span>

<span data-ttu-id="1a984-181">Cette applet de commande génère un objet qui représente l’élément, si vous spécifiez le paramètre *PassThru* .</span><span class="sxs-lookup"><span data-stu-id="1a984-181">This cmdlet generates an object that represent the item, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="1a984-182">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1a984-182">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1a984-183">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1a984-183">NOTES</span></span>

- <span data-ttu-id="1a984-184">`Set-Item` n’est pas pris en charge par le fournisseur FileSystem PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a984-184">`Set-Item` is not supported by the PowerShell FileSystem provider.</span></span> <span data-ttu-id="1a984-185">Pour modifier les valeurs des éléments dans le système de fichiers, utilisez l’applet de commande `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="1a984-185">To change the values of items in the file system, use the `Set-Content` cmdlet.</span></span>
- <span data-ttu-id="1a984-186">Dans les lecteurs de Registre, `HKLM:` et `HKCU:` , `Set-Item` modifie les données dans la valeur (par défaut) d’une clé de registre.</span><span class="sxs-lookup"><span data-stu-id="1a984-186">In the Registry drives, `HKLM:` and `HKCU:`, `Set-Item` changes the data in the (Default) value of a registry key.</span></span>
  - <span data-ttu-id="1a984-187">Pour créer et modifier les noms des clés de Registre, utilisez l' `New-Item` applet de commande et `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="1a984-187">To create and change the names of registry keys, use the `New-Item` and `Rename-Item` cmdlet.</span></span>
  - <span data-ttu-id="1a984-188">Pour modifier les noms et les données dans les valeurs de Registre, utilisez les `New-ItemProperty` applets de commande, `Set-ItemProperty` et `Rename-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="1a984-188">To change the names and data in registry values, use the `New-ItemProperty`, `Set-ItemProperty`, and `Rename-ItemProperty` cmdlets.</span></span>
- <span data-ttu-id="1a984-189">`Set-Item` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1a984-189">`Set-Item` is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="1a984-190">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="1a984-190">To list the providers available in your session, type `Get-PsProvider`.</span></span>
  <span data-ttu-id="1a984-191">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="1a984-191">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="1a984-192">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1a984-192">RELATED LINKS</span></span>

[<span data-ttu-id="1a984-193">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="1a984-193">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="1a984-194">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="1a984-194">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="1a984-195">Get-Item</span><span class="sxs-lookup"><span data-stu-id="1a984-195">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="1a984-196">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="1a984-196">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="1a984-197">Move-Item</span><span class="sxs-lookup"><span data-stu-id="1a984-197">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="1a984-198">New-Item</span><span class="sxs-lookup"><span data-stu-id="1a984-198">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="1a984-199">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="1a984-199">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="1a984-200">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="1a984-200">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="1a984-201">about_Providers</span><span class="sxs-lookup"><span data-stu-id="1a984-201">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
