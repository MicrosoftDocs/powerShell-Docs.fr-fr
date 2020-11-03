---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 8378534715bfcfa8fffc08be17cb4bef9de6c60e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202085"
---
# <span data-ttu-id="03ad6-103">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="03ad6-103">New-ItemProperty</span></span>

## <span data-ttu-id="03ad6-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="03ad6-104">SYNOPSIS</span></span>
<span data-ttu-id="03ad6-105">Crée une propriété pour un élément et définit sa valeur.</span><span class="sxs-lookup"><span data-stu-id="03ad6-105">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="03ad6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="03ad6-106">SYNTAX</span></span>

### <span data-ttu-id="03ad6-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="03ad6-107">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="03ad6-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="03ad6-108">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="03ad6-109">Description</span><span class="sxs-lookup"><span data-stu-id="03ad6-109">DESCRIPTION</span></span>

<span data-ttu-id="03ad6-110">L' `New-ItemProperty` applet de commande crée une nouvelle propriété pour un élément spécifié et définit sa valeur.</span><span class="sxs-lookup"><span data-stu-id="03ad6-110">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="03ad6-111">En général, cette applet de commande permet de créer des valeurs de Registre, car les valeurs de Registre sont les propriétés d’un élément de clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="03ad6-111">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="03ad6-112">Cette applet de commande n’ajoute pas de propriétés à un objet.</span><span class="sxs-lookup"><span data-stu-id="03ad6-112">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="03ad6-113">Pour ajouter une propriété à une instance d’un objet, utilisez l' `Add-Member` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="03ad6-113">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="03ad6-114">Pour ajouter une propriété à tous les objets d’un type particulier, modifiez le fichier XML Types.ps1.</span><span class="sxs-lookup"><span data-stu-id="03ad6-114">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="03ad6-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="03ad6-115">EXAMPLES</span></span>

### <span data-ttu-id="03ad6-116">Exemple 1 : ajouter une entrée de Registre</span><span class="sxs-lookup"><span data-stu-id="03ad6-116">Example 1: Add a registry entry</span></span>

<span data-ttu-id="03ad6-117">Cette commande ajoute une nouvelle entrée de Registre, « NoOfEmployees », à la clé « MyCompany » de la « HKLM : \ Software Hive ».</span><span class="sxs-lookup"><span data-stu-id="03ad6-117">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="03ad6-118">La première commande utilise le paramètre **path** pour spécifier le chemin d’accès de la clé de Registre « MyCompany ».</span><span class="sxs-lookup"><span data-stu-id="03ad6-118">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="03ad6-119">Elle utilise le paramètre **Name** pour spécifier le nom de l’entrée et le paramètre **value** pour spécifier sa valeur.</span><span class="sxs-lookup"><span data-stu-id="03ad6-119">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="03ad6-120">La deuxième commande utilise l' `Get-ItemProperty` applet de commande pour afficher la nouvelle entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="03ad6-120">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### <span data-ttu-id="03ad6-121">Exemple 2 : ajouter une entrée de Registre à une clé</span><span class="sxs-lookup"><span data-stu-id="03ad6-121">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="03ad6-122">Cette commande ajoute une nouvelle entrée de Registre à une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="03ad6-122">This command adds a new registry entry to a registry key.</span></span>
<span data-ttu-id="03ad6-123">Pour spécifier la clé, elle utilise un opérateur de pipeline ( `|` ) pour envoyer un objet qui représente la clé à `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="03ad6-123">To specify the key, it uses a pipeline operator (`|`) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="03ad6-124">La première partie de la commande utilise l' `Get-Item` applet de commande pour récupérer la clé de Registre « MyCompany ».</span><span class="sxs-lookup"><span data-stu-id="03ad6-124">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span>
<span data-ttu-id="03ad6-125">L’opérateur de pipeline envoie les résultats de la commande à `New-ItemProperty` , qui ajoute la nouvelle entrée de Registre (« (NoOfLocations) ») et sa valeur (3) à la clé « MyCompany ».</span><span class="sxs-lookup"><span data-stu-id="03ad6-125">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="03ad6-126">Cette commande fonctionne, car la fonctionnalité de liaison de paramètre de PowerShell associe le chemin d’accès de l' `RegistryKey` objet `Get-Item` retourné par le paramètre **LiteralPath** de `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="03ad6-126">This command works because the parameter-binding feature of PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="03ad6-127">Pour plus d’informations, consultez [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span><span class="sxs-lookup"><span data-stu-id="03ad6-127">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="03ad6-128">Exemple 3 : créer une valeur de chaînes multiples dans le registre à l’aide d’un Here-String</span><span class="sxs-lookup"><span data-stu-id="03ad6-128">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="03ad6-129">Cet exemple crée une valeur multichaîne à l’aide d’une chaîne ici.</span><span class="sxs-lookup"><span data-stu-id="03ad6-129">This example creates a MultiString value using a Here-String.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### <span data-ttu-id="03ad6-130">Exemple 4 : créer une valeur de chaînes multiples dans le registre à l’aide d’un tableau</span><span class="sxs-lookup"><span data-stu-id="03ad6-130">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="03ad6-131">L’exemple montre comment utiliser un tableau de valeurs pour créer la `MultiString` valeur.</span><span class="sxs-lookup"><span data-stu-id="03ad6-131">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="03ad6-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="03ad6-132">PARAMETERS</span></span>

### <span data-ttu-id="03ad6-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="03ad6-133">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="03ad6-134">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03ad6-134">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="03ad6-135">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="03ad6-135">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="03ad6-136">-Exclude</span><span class="sxs-lookup"><span data-stu-id="03ad6-136">-Exclude</span></span>

<span data-ttu-id="03ad6-137">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="03ad6-137">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="03ad6-138">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="03ad6-139">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="03ad6-139">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="03ad6-140">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="03ad6-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="03ad6-141">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="03ad6-141">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="03ad6-142">-Filter</span><span class="sxs-lookup"><span data-stu-id="03ad6-142">-Filter</span></span>

<span data-ttu-id="03ad6-143">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-143">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="03ad6-144">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="03ad6-144">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="03ad6-145">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="03ad6-145">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="03ad6-146">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="03ad6-146">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="03ad6-147">-Force</span><span class="sxs-lookup"><span data-stu-id="03ad6-147">-Force</span></span>

<span data-ttu-id="03ad6-148">Force l’applet de commande à créer une propriété sur un objet qui, sinon, n’est pas accessible par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="03ad6-148">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="03ad6-149">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="03ad6-149">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="03ad6-150">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="03ad6-150">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="03ad6-151">-Include</span><span class="sxs-lookup"><span data-stu-id="03ad6-151">-Include</span></span>

<span data-ttu-id="03ad6-152">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="03ad6-152">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="03ad6-153">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-153">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="03ad6-154">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="03ad6-154">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="03ad6-155">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="03ad6-155">Wildcard characters are permitted.</span></span> <span data-ttu-id="03ad6-156">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="03ad6-156">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="03ad6-157">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="03ad6-157">-LiteralPath</span></span>

<span data-ttu-id="03ad6-158">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="03ad6-158">Specifies a path to one or more locations.</span></span> <span data-ttu-id="03ad6-159">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="03ad6-159">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="03ad6-160">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="03ad6-160">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="03ad6-161">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="03ad6-161">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="03ad6-162">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="03ad6-162">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="03ad6-163">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="03ad6-163">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="03ad6-164">-Name</span><span class="sxs-lookup"><span data-stu-id="03ad6-164">-Name</span></span>

<span data-ttu-id="03ad6-165">Spécifie le nom de la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="03ad6-165">Specifies a name for the new property.</span></span>
<span data-ttu-id="03ad6-166">Si la propriété est une entrée de Registre, ce paramètre spécifie le nom de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="03ad6-166">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="03ad6-167">-Path</span><span class="sxs-lookup"><span data-stu-id="03ad6-167">-Path</span></span>

<span data-ttu-id="03ad6-168">Spécifie le chemin d’accès de l’élément.</span><span class="sxs-lookup"><span data-stu-id="03ad6-168">Specifies the path of the item.</span></span>
<span data-ttu-id="03ad6-169">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="03ad6-169">Wildcard characters are permitted.</span></span>
<span data-ttu-id="03ad6-170">Ce paramètre identifie l’élément auquel cette applet de commande ajoute la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="03ad6-170">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="03ad6-171">-PropertyType</span><span class="sxs-lookup"><span data-stu-id="03ad6-171">-PropertyType</span></span>

<span data-ttu-id="03ad6-172">Spécifie le type de propriété que cette applet de commande ajoute.</span><span class="sxs-lookup"><span data-stu-id="03ad6-172">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="03ad6-173">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="03ad6-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="03ad6-174">**String** : spécifie une chaîne terminée par le caractère null.</span><span class="sxs-lookup"><span data-stu-id="03ad6-174">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="03ad6-175">Équivalent à **REG_SZ** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-175">Equivalent to **REG_SZ** .</span></span>
- <span data-ttu-id="03ad6-176">**ExpandString** : spécifie une chaîne terminée par le caractère null qui contient des références non développées à des variables d’environnement qui sont développées lorsque la valeur est récupérée.</span><span class="sxs-lookup"><span data-stu-id="03ad6-176">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="03ad6-177">Équivalent à **REG_EXPAND_SZ** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-177">Equivalent to **REG_EXPAND_SZ** .</span></span>
- <span data-ttu-id="03ad6-178">**Binary** : spécifie des données binaires sous n’importe quelle forme.</span><span class="sxs-lookup"><span data-stu-id="03ad6-178">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="03ad6-179">Équivalent à **REG_BINARY** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-179">Equivalent to **REG_BINARY** .</span></span>
- <span data-ttu-id="03ad6-180">**DWORD** : spécifie un nombre binaire de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="03ad6-180">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="03ad6-181">Équivalent à **REG_DWORD** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-181">Equivalent to **REG_DWORD** .</span></span>
- <span data-ttu-id="03ad6-182">**MultiString** : spécifie un tableau de chaînes terminées par le caractère null qui se sont terminées par deux caractères null.</span><span class="sxs-lookup"><span data-stu-id="03ad6-182">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="03ad6-183">Équivalent à **REG_MULTI_SZ** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-183">Equivalent to **REG_MULTI_SZ** .</span></span>
- <span data-ttu-id="03ad6-184">**QWord** : spécifie un nombre binaire de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="03ad6-184">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="03ad6-185">Équivalent à **REG_QWORD** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-185">Equivalent to **REG_QWORD** .</span></span>
- <span data-ttu-id="03ad6-186">**Inconnu** : indique un type de données de Registre non pris en charge, tel que **REG_RESOURCE_LIST** .</span><span class="sxs-lookup"><span data-stu-id="03ad6-186">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST** .</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="03ad6-187">-Value</span><span class="sxs-lookup"><span data-stu-id="03ad6-187">-Value</span></span>

<span data-ttu-id="03ad6-188">Spécifie la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="03ad6-188">Specifies the property value.</span></span>
<span data-ttu-id="03ad6-189">Si la propriété est une entrée de Registre, ce paramètre spécifie la valeur de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="03ad6-189">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="03ad6-190">-Confirm</span><span class="sxs-lookup"><span data-stu-id="03ad6-190">-Confirm</span></span>

<span data-ttu-id="03ad6-191">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="03ad6-191">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="03ad6-192">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="03ad6-192">-WhatIf</span></span>

<span data-ttu-id="03ad6-193">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="03ad6-193">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="03ad6-194">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="03ad6-194">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="03ad6-195">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="03ad6-195">CommonParameters</span></span>

<span data-ttu-id="03ad6-196">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="03ad6-196">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="03ad6-197">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="03ad6-197">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="03ad6-198">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="03ad6-198">INPUTS</span></span>

### <span data-ttu-id="03ad6-199">Aucun</span><span class="sxs-lookup"><span data-stu-id="03ad6-199">None</span></span>

<span data-ttu-id="03ad6-200">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="03ad6-200">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="03ad6-201">SORTIES</span><span class="sxs-lookup"><span data-stu-id="03ad6-201">OUTPUTS</span></span>

### <span data-ttu-id="03ad6-202">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="03ad6-202">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="03ad6-203">`New-ItemProperty` retourne un objet personnalisé qui contient la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="03ad6-203">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="03ad6-204">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="03ad6-204">NOTES</span></span>

<span data-ttu-id="03ad6-205">`New-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="03ad6-205">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="03ad6-206">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="03ad6-206">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="03ad6-207">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="03ad6-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="03ad6-208">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="03ad6-208">RELATED LINKS</span></span>

[<span data-ttu-id="03ad6-209">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="03ad6-209">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="03ad6-210">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="03ad6-210">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="03ad6-211">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="03ad6-211">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="03ad6-212">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="03ad6-212">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="03ad6-213">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="03ad6-213">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="03ad6-214">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="03ad6-214">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="03ad6-215">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="03ad6-215">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="03ad6-216">about_Providers</span><span class="sxs-lookup"><span data-stu-id="03ad6-216">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

