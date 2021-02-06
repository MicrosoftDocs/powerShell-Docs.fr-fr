---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: c617f4554c8e61ed6cf54b0faf0cd7d79be84595
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597773"
---
# <span data-ttu-id="de840-102">Set-Item</span><span class="sxs-lookup"><span data-stu-id="de840-102">Set-Item</span></span>

## <span data-ttu-id="de840-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="de840-103">SYNOPSIS</span></span>
<span data-ttu-id="de840-104">Remplace la valeur d'un élément par la valeur spécifiée dans la commande.</span><span class="sxs-lookup"><span data-stu-id="de840-104">Changes the value of an item to the value specified in the command.</span></span>

## <span data-ttu-id="de840-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="de840-105">SYNTAX</span></span>

### <span data-ttu-id="de840-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="de840-106">Path (Default)</span></span>

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="de840-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="de840-107">LiteralPath</span></span>

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="de840-108">Description</span><span class="sxs-lookup"><span data-stu-id="de840-108">DESCRIPTION</span></span>

<span data-ttu-id="de840-109">L' `Set-Item` applet de commande modifie la valeur d’un élément, telle qu’une variable ou une clé de Registre, en fonction de la valeur spécifiée dans la commande.</span><span class="sxs-lookup"><span data-stu-id="de840-109">The `Set-Item` cmdlet changes the value of an item, such as a variable or registry key, to the value specified in the command.</span></span>

## <span data-ttu-id="de840-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="de840-110">EXAMPLES</span></span>

### <span data-ttu-id="de840-111">Exemple 1 : créer un alias</span><span class="sxs-lookup"><span data-stu-id="de840-111">Example 1: Create an alias</span></span>

<span data-ttu-id="de840-112">Cette commande crée un alias de NP pour le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="de840-112">This command creates an alias of np for Notepad.</span></span>

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### <span data-ttu-id="de840-113">Exemple 2 : modifier la valeur d’une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="de840-113">Example 2: Change the value of an environment variable</span></span>

<span data-ttu-id="de840-114">Cette commande modifie la valeur de la variable d’environnement UserRole en Administrator.</span><span class="sxs-lookup"><span data-stu-id="de840-114">This command changes the value of the UserRole environment variable to Administrator.</span></span>

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### <span data-ttu-id="de840-115">Exemple 3 : modifier votre fonction d’invite</span><span class="sxs-lookup"><span data-stu-id="de840-115">Example 3: Modify your prompt function</span></span>

<span data-ttu-id="de840-116">Cette commande modifie la fonction d’invite afin qu’elle affiche l’heure avant le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="de840-116">This command changes the prompt function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### <span data-ttu-id="de840-117">Exemple 4 : définir les options de votre fonction d’invite</span><span class="sxs-lookup"><span data-stu-id="de840-117">Example 4: Set options for your prompt function</span></span>

<span data-ttu-id="de840-118">Cette commande définit les options **options AllScope** et **ReadOnly** pour la fonction prompt.</span><span class="sxs-lookup"><span data-stu-id="de840-118">This command sets the **AllScope** and **ReadOnly** options for the prompt function.</span></span>
<span data-ttu-id="de840-119">Cette commande utilise le paramètre dynamique **options** de `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="de840-119">This command uses the **Options** dynamic parameter of `Set-Item`.</span></span>
<span data-ttu-id="de840-120">Le paramètre **options** est disponible dans `Set-Item` uniquement lorsque vous l’utilisez avec l' **alias** ou le fournisseur de **fonctions** .</span><span class="sxs-lookup"><span data-stu-id="de840-120">The **Options** parameter is available in `Set-Item` only when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

## <span data-ttu-id="de840-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="de840-121">PARAMETERS</span></span>

### <span data-ttu-id="de840-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="de840-122">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="de840-123">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de840-123">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="de840-124">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="de840-124">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="de840-125">-Exclude</span><span class="sxs-lookup"><span data-stu-id="de840-125">-Exclude</span></span>

<span data-ttu-id="de840-126">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="de840-126">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="de840-127">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="de840-127">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="de840-128">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="de840-128">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="de840-129">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="de840-129">Wildcard characters are permitted.</span></span> <span data-ttu-id="de840-130">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="de840-130">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="de840-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="de840-131">-Filter</span></span>

<span data-ttu-id="de840-132">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="de840-132">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="de840-133">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="de840-133">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="de840-134">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="de840-134">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="de840-135">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="de840-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="de840-136">-Force</span><span class="sxs-lookup"><span data-stu-id="de840-136">-Force</span></span>

<span data-ttu-id="de840-137">Force l’applet de commande à définir des éléments qui ne peuvent pas être modifiés autrement, tels que des alias ou des variables en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="de840-137">Forces the cmdlet to set items that cannot otherwise be changed, such as read-only alias or variables.</span></span> <span data-ttu-id="de840-138">L’applet de commande ne peut pas modifier des alias ou variables constants.</span><span class="sxs-lookup"><span data-stu-id="de840-138">The cmdlet cannot change constant aliases or variables.</span></span>
<span data-ttu-id="de840-139">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="de840-139">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="de840-140">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="de840-140">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="de840-141">Même en utilisant le paramètre *force* , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="de840-141">Even using the *Force* parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="de840-142">-Include</span><span class="sxs-lookup"><span data-stu-id="de840-142">-Include</span></span>

<span data-ttu-id="de840-143">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="de840-143">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="de840-144">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="de840-144">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="de840-145">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="de840-145">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="de840-146">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="de840-146">Wildcard characters are permitted.</span></span> <span data-ttu-id="de840-147">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="de840-147">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="de840-148">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="de840-148">-LiteralPath</span></span>

<span data-ttu-id="de840-149">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="de840-149">Specifies a path to one or more locations.</span></span> <span data-ttu-id="de840-150">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="de840-150">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="de840-151">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="de840-151">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="de840-152">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="de840-152">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="de840-153">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="de840-153">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="de840-154">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="de840-154">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="de840-155">-PassThru</span><span class="sxs-lookup"><span data-stu-id="de840-155">-PassThru</span></span>

<span data-ttu-id="de840-156">Passe un objet qui représente l’élément au pipeline.</span><span class="sxs-lookup"><span data-stu-id="de840-156">Passes an object that represents the item to the pipeline.</span></span>
<span data-ttu-id="de840-157">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="de840-157">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="de840-158">-Path</span><span class="sxs-lookup"><span data-stu-id="de840-158">-Path</span></span>

<span data-ttu-id="de840-159">Spécifie le chemin d’accès de l’emplacement des éléments.</span><span class="sxs-lookup"><span data-stu-id="de840-159">Specifies a path of the location of the items.</span></span>
<span data-ttu-id="de840-160">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="de840-160">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="de840-161">-Value</span><span class="sxs-lookup"><span data-stu-id="de840-161">-Value</span></span>

<span data-ttu-id="de840-162">Spécifie une nouvelle valeur pour l’élément.</span><span class="sxs-lookup"><span data-stu-id="de840-162">Specifies a new value for the item.</span></span>

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

### <span data-ttu-id="de840-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="de840-163">-Confirm</span></span>

<span data-ttu-id="de840-164">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="de840-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="de840-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="de840-165">-WhatIf</span></span>

<span data-ttu-id="de840-166">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="de840-166">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="de840-167">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="de840-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="de840-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="de840-168">CommonParameters</span></span>

<span data-ttu-id="de840-169">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="de840-169">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="de840-170">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="de840-170">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="de840-171">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="de840-171">INPUTS</span></span>

### <span data-ttu-id="de840-172">System.Object</span><span class="sxs-lookup"><span data-stu-id="de840-172">System.Object</span></span>

<span data-ttu-id="de840-173">Vous pouvez diriger un objet qui représente la nouvelle valeur de l’élément vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="de840-173">You can pipe an object that represents the new value of the item to this cmdlet.</span></span>

## <span data-ttu-id="de840-174">SORTIES</span><span class="sxs-lookup"><span data-stu-id="de840-174">OUTPUTS</span></span>

### <span data-ttu-id="de840-175">Aucun ou un objet représentant l’élément nouveau ou modifié.</span><span class="sxs-lookup"><span data-stu-id="de840-175">None or an object representing the new or changed item.</span></span>

<span data-ttu-id="de840-176">Cette applet de commande génère un objet qui représente l’élément, si vous spécifiez le paramètre *PassThru* .</span><span class="sxs-lookup"><span data-stu-id="de840-176">This cmdlet generates an object that represent the item, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="de840-177">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="de840-177">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="de840-178">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="de840-178">NOTES</span></span>

- <span data-ttu-id="de840-179">`Set-Item` n’est pas pris en charge par le fournisseur FileSystem PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de840-179">`Set-Item` is not supported by the PowerShell FileSystem provider.</span></span> <span data-ttu-id="de840-180">Pour modifier les valeurs des éléments dans le système de fichiers, utilisez l’applet de commande `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="de840-180">To change the values of items in the file system, use the `Set-Content` cmdlet.</span></span>
- <span data-ttu-id="de840-181">Dans les lecteurs de Registre, `HKLM:` et `HKCU:` , `Set-Item` modifie les données dans la valeur (par défaut) d’une clé de registre.</span><span class="sxs-lookup"><span data-stu-id="de840-181">In the Registry drives, `HKLM:` and `HKCU:`, `Set-Item` changes the data in the (Default) value of a registry key.</span></span>
  - <span data-ttu-id="de840-182">Pour créer et modifier les noms des clés de Registre, utilisez l' `New-Item` applet de commande et `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="de840-182">To create and change the names of registry keys, use the `New-Item` and `Rename-Item` cmdlet.</span></span>
  - <span data-ttu-id="de840-183">Pour modifier les noms et les données dans les valeurs de Registre, utilisez les `New-ItemProperty` applets de commande, `Set-ItemProperty` et `Rename-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="de840-183">To change the names and data in registry values, use the `New-ItemProperty`, `Set-ItemProperty`, and `Rename-ItemProperty` cmdlets.</span></span>
- <span data-ttu-id="de840-184">`Set-Item` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="de840-184">`Set-Item` is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="de840-185">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="de840-185">To list the providers available in your session, type `Get-PsProvider`.</span></span>
  <span data-ttu-id="de840-186">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="de840-186">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="de840-187">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="de840-187">RELATED LINKS</span></span>

[<span data-ttu-id="de840-188">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="de840-188">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="de840-189">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="de840-189">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="de840-190">Get-Item</span><span class="sxs-lookup"><span data-stu-id="de840-190">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="de840-191">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="de840-191">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="de840-192">Move-Item</span><span class="sxs-lookup"><span data-stu-id="de840-192">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="de840-193">New-Item</span><span class="sxs-lookup"><span data-stu-id="de840-193">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="de840-194">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="de840-194">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="de840-195">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="de840-195">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="de840-196">about_Providers</span><span class="sxs-lookup"><span data-stu-id="de840-196">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

