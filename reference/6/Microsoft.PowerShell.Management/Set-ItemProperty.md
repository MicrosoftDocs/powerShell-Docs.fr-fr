---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: b12ca6bda03c1eb3834916bf9bfce43ecc3a70fb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202430"
---
# <span data-ttu-id="fb976-103">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fb976-103">Set-ItemProperty</span></span>

## <span data-ttu-id="fb976-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fb976-104">SYNOPSIS</span></span>
<span data-ttu-id="fb976-105">Crée ou modifie la valeur d'une propriété d'un élément.</span><span class="sxs-lookup"><span data-stu-id="fb976-105">Creates or changes the value of a property of an item.</span></span>

## <span data-ttu-id="fb976-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fb976-106">SYNTAX</span></span>

### <span data-ttu-id="fb976-107">propertyValuePathSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="fb976-107">propertyValuePathSet (Default)</span></span>

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fb976-108">propertyPSObjectPathSet</span><span class="sxs-lookup"><span data-stu-id="fb976-108">propertyPSObjectPathSet</span></span>

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fb976-109">propertyValueLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="fb976-109">propertyValueLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fb976-110">propertyPSObjectLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="fb976-110">propertyPSObjectLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fb976-111">Description</span><span class="sxs-lookup"><span data-stu-id="fb976-111">DESCRIPTION</span></span>

<span data-ttu-id="fb976-112">L' `Set-ItemProperty` applet de commande modifie la valeur de la propriété de l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="fb976-112">The `Set-ItemProperty` cmdlet changes the value of the property of the specified item.</span></span>
<span data-ttu-id="fb976-113">Vous pouvez utiliser cette applet de commande pour définir ou modifier les propriétés d'éléments.</span><span class="sxs-lookup"><span data-stu-id="fb976-113">You can use the cmdlet to establish or change the properties of items.</span></span>
<span data-ttu-id="fb976-114">Par exemple, vous pouvez utiliser `Set-ItemProperty` pour définir la valeur de la propriété **IsReadOnly** d’un objet fichier sur `$True` .</span><span class="sxs-lookup"><span data-stu-id="fb976-114">For example, you can use `Set-ItemProperty` to set the value of the **IsReadOnly** property of a file object to `$True`.</span></span>

<span data-ttu-id="fb976-115">Vous pouvez également utiliser `Set-ItemProperty` pour créer et modifier les valeurs de Registre et les données.</span><span class="sxs-lookup"><span data-stu-id="fb976-115">You also use `Set-ItemProperty` to create and change registry values and data.</span></span>
<span data-ttu-id="fb976-116">Par exemple, vous pouvez ajouter une nouvelle entrée de Registre à une clé, puis définir ou modifier sa valeur.</span><span class="sxs-lookup"><span data-stu-id="fb976-116">For example, you can add a new registry entry to a key and establish or change its value.</span></span>

## <span data-ttu-id="fb976-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fb976-117">EXAMPLES</span></span>

### <span data-ttu-id="fb976-118">Exemple 1 : définir une propriété d’un fichier</span><span class="sxs-lookup"><span data-stu-id="fb976-118">Example 1: Set a property of a file</span></span>

<span data-ttu-id="fb976-119">Cette commande affecte la valeur « true » à la propriété **IsReadOnly** du fichier « final.doc ».</span><span class="sxs-lookup"><span data-stu-id="fb976-119">This command sets the value of the **IsReadOnly** property of the "final.doc" file to "true".</span></span>
<span data-ttu-id="fb976-120">Elle utilise **path** pour spécifier le fichier, **Name** pour spécifier le nom de la propriété et le paramètre **value** pour spécifier la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="fb976-120">It uses **Path** to specify the file, **Name** to specify the name of the property, and the **Value** parameter to specify the new value.</span></span>

<span data-ttu-id="fb976-121">Le fichier est un objet **System. IO. FileInfo** et **IsReadOnly** est simplement l’une de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="fb976-121">The file is a **System.IO.FileInfo** object and **IsReadOnly** is just one of its properties.</span></span>
<span data-ttu-id="fb976-122">Pour afficher toutes les propriétés, tapez `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property` .</span><span class="sxs-lookup"><span data-stu-id="fb976-122">To see all of the properties, type `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property`.</span></span>

<span data-ttu-id="fb976-123">La `$true` variable automatique représente une valeur « true ».</span><span class="sxs-lookup"><span data-stu-id="fb976-123">The `$true` automatic variable represents a value of "TRUE".</span></span>
<span data-ttu-id="fb976-124">Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="fb976-124">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### <span data-ttu-id="fb976-125">Exemple 2 : créer une entrée et une valeur de Registre</span><span class="sxs-lookup"><span data-stu-id="fb976-125">Example 2: Create a registry entry and value</span></span>

<span data-ttu-id="fb976-126">Cet exemple montre comment utiliser `Set-ItemProperty` pour créer une nouvelle entrée de Registre et affecter une valeur à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="fb976-126">This example shows how to use `Set-ItemProperty` to create a new registry entry and to assign a value to the entry.</span></span> <span data-ttu-id="fb976-127">Il crée l’entrée « NoOfEmployees » dans la clé « ContosoCompany » dans la `HKLM\Software` clé et définit sa valeur sur 823.</span><span class="sxs-lookup"><span data-stu-id="fb976-127">It creates the "NoOfEmployees" entry in the "ContosoCompany" key in `HKLM\Software` key and sets its value to 823.</span></span>

<span data-ttu-id="fb976-128">Étant donné que les entrées de Registre sont considérées comme des propriétés des clés de Registre, qui sont des éléments, vous utilisez `Set-ItemProperty` pour créer des entrées de Registre et pour définir et modifier leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="fb976-128">Because registry entries are considered to be properties of the registry keys, which are items, you use `Set-ItemProperty` to create registry entries, and to establish and change their values.</span></span>

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823
```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

<span data-ttu-id="fb976-129">La première commande crée l’entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="fb976-129">The first command creates the registry entry.</span></span>
<span data-ttu-id="fb976-130">Elle utilise **path** pour spécifier le chemin d’accès du `HKLM:` lecteur et la clé « Software\MyCompany. ».</span><span class="sxs-lookup"><span data-stu-id="fb976-130">It uses **Path** to specify the path of the `HKLM:` drive and the "Software\MyCompany" key.</span></span>
<span data-ttu-id="fb976-131">La commande utilise **Name** pour spécifier le nom et la **valeur** de l’entrée pour spécifier une valeur.</span><span class="sxs-lookup"><span data-stu-id="fb976-131">The command uses **Name** to specify the entry name and **Value** to specify a value.</span></span>

<span data-ttu-id="fb976-132">La deuxième commande utilise l' `Get-ItemProperty` applet de commande pour afficher la nouvelle entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="fb976-132">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>
<span data-ttu-id="fb976-133">Si vous utilisez les `Get-Item` applets de commande ou `Get-ChildItem` , les entrées ne s’affichent pas, car il s’agit des propriétés d’une clé, et non des éléments ou des éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="fb976-133">If you use the `Get-Item` or `Get-ChildItem` cmdlets, the entries do not appear because they are properties of a key, not items or child items.</span></span>

<span data-ttu-id="fb976-134">La troisième commande modifie la valeur de l’entrée **NoOfEmployees** en 824.</span><span class="sxs-lookup"><span data-stu-id="fb976-134">The third command changes the value of the **NoOfEmployees** entry to 824.</span></span>

<span data-ttu-id="fb976-135">Vous pouvez également utiliser l' `New-ItemProperty` applet de commande pour créer l’entrée de Registre et sa valeur, puis utiliser `Set-ItemProperty` pour modifier la valeur.</span><span class="sxs-lookup"><span data-stu-id="fb976-135">You can also use the `New-ItemProperty` cmdlet to create the registry entry and its value and then use `Set-ItemProperty` to change the value.</span></span>

<span data-ttu-id="fb976-136">Pour plus d’informations sur le `HKLM:` lecteur, tapez `Get-Help Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="fb976-136">For more information about the `HKLM:` drive, type `Get-Help Get-PSDrive`.</span></span>
<span data-ttu-id="fb976-137">Pour plus d’informations sur l’utilisation de PowerShell pour gérer le registre, tapez `Get-Help Registry` .</span><span class="sxs-lookup"><span data-stu-id="fb976-137">For more information about how to use PowerShell to manage the registry, type `Get-Help Registry`.</span></span>

### <span data-ttu-id="fb976-138">Exemple 3 : modifier un élément à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="fb976-138">Example 3: Modify an item by using the pipeline</span></span>

<span data-ttu-id="fb976-139">Ces commandes montrent comment utiliser un opérateur de pipeline ( `|` ) pour envoyer un élément à `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="fb976-139">These commands show how to use a pipeline operator (`|`) to send an item to `Set-ItemProperty`.</span></span>

<span data-ttu-id="fb976-140">La première partie de la commande utilise `Get-ChildItem` pour récupérer un objet qui représente le fichier « Weekly.txt ».</span><span class="sxs-lookup"><span data-stu-id="fb976-140">The first part of the command uses `Get-ChildItem` to get an object that represents the "Weekly.txt" file.</span></span> <span data-ttu-id="fb976-141">La commande utilise un opérateur de pipeline auquel envoyer l’objet fichier `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="fb976-141">The command uses a pipeline operator to send the file object to `Set-ItemProperty`.</span></span>
<span data-ttu-id="fb976-142">La `Set-ItemProperty` commande utilise les paramètres **Name** et **value** pour spécifier la propriété et sa nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="fb976-142">The `Set-ItemProperty` command uses the **Name** and **Value** parameters to specify the property and its new value.</span></span>

<span data-ttu-id="fb976-143">Cette commande revient à utiliser le paramètre **InputObject** pour spécifier l’objet qui `Get-ChildItem` obtient.</span><span class="sxs-lookup"><span data-stu-id="fb976-143">This command is equivalent to using the **InputObject** parameter to specify the object that `Get-ChildItem` gets.</span></span>

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## <span data-ttu-id="fb976-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fb976-144">PARAMETERS</span></span>

### <span data-ttu-id="fb976-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="fb976-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="fb976-146">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb976-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="fb976-147">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="fb976-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="fb976-148">-Exclude</span><span class="sxs-lookup"><span data-stu-id="fb976-148">-Exclude</span></span>

<span data-ttu-id="fb976-149">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="fb976-149">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="fb976-150">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="fb976-150">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fb976-151">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="fb976-151">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="fb976-152">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fb976-152">Wildcard characters are permitted.</span></span> <span data-ttu-id="fb976-153">Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="fb976-153">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fb976-154">-Filter</span><span class="sxs-lookup"><span data-stu-id="fb976-154">-Filter</span></span>

<span data-ttu-id="fb976-155">Spécifie un filtre pour qualifier le paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="fb976-155">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="fb976-156">Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres.</span><span class="sxs-lookup"><span data-stu-id="fb976-156">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="fb976-157">Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="fb976-157">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="fb976-158">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="fb976-158">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="fb976-159">-Force</span><span class="sxs-lookup"><span data-stu-id="fb976-159">-Force</span></span>

<span data-ttu-id="fb976-160">Force l’applet de commande à définir une propriété sur des éléments qui, sinon, ne sont pas accessibles par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fb976-160">Forces the cmdlet to set a property on items that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="fb976-161">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="fb976-161">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="fb976-162">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="fb976-162">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="fb976-163">-Include</span><span class="sxs-lookup"><span data-stu-id="fb976-163">-Include</span></span>

<span data-ttu-id="fb976-164">Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="fb976-164">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="fb976-165">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="fb976-165">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="fb976-166">Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="fb976-166">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="fb976-167">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fb976-167">Wildcard characters are permitted.</span></span> <span data-ttu-id="fb976-168">Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="fb976-168">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="fb976-169">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fb976-169">-InputObject</span></span>

<span data-ttu-id="fb976-170">Spécifie l’objet qui a les propriétés modifiées par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fb976-170">Specifies the object that has the properties that this cmdlet changes.</span></span>
<span data-ttu-id="fb976-171">Entrez une variable qui contient l'objet ou tapez une commande permettant d'obtenir cet objet.</span><span class="sxs-lookup"><span data-stu-id="fb976-171">Enter a variable that contains the object or a command that gets the object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fb976-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fb976-172">-LiteralPath</span></span>

<span data-ttu-id="fb976-173">Spécifie un chemin d’accès à un ou plusieurs emplacements.</span><span class="sxs-lookup"><span data-stu-id="fb976-173">Specifies a path to one or more locations.</span></span> <span data-ttu-id="fb976-174">La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="fb976-174">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="fb976-175">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="fb976-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="fb976-176">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="fb976-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="fb976-177">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="fb976-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="fb976-178">Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="fb976-178">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyPSObjectLiteralPathSet, propertyValueLiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb976-179">-Name</span><span class="sxs-lookup"><span data-stu-id="fb976-179">-Name</span></span>

<span data-ttu-id="fb976-180">Spécifie le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="fb976-180">Specifies the name of the property.</span></span>

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb976-181">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fb976-181">-PassThru</span></span>

<span data-ttu-id="fb976-182">Retourne un objet qui représente la propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="fb976-182">Returns an object that represents the item property.</span></span>
<span data-ttu-id="fb976-183">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="fb976-183">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="fb976-184">-Path</span><span class="sxs-lookup"><span data-stu-id="fb976-184">-Path</span></span>

<span data-ttu-id="fb976-185">Spécifie le chemin d’accès des éléments avec la propriété à modifier.</span><span class="sxs-lookup"><span data-stu-id="fb976-185">Specifies the path of the items with the property to modify.</span></span>
<span data-ttu-id="fb976-186">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="fb976-186">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="fb976-187">-Type</span><span class="sxs-lookup"><span data-stu-id="fb976-187">-Type</span></span>

<span data-ttu-id="fb976-188">Le **type** est un paramètre dynamique que le fournisseur du Registre ajoute à l’applet de commande `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="fb976-188">**Type** is a dynamic parameter that the Registry provider adds to the `Set-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="fb976-189">Ce paramètre fonctionne uniquement dans les lecteurs de registre.</span><span class="sxs-lookup"><span data-stu-id="fb976-189">This parameter only works in the registry drives.</span></span>

<span data-ttu-id="fb976-190">Spécifie le type de propriété que cette applet de commande ajoute.</span><span class="sxs-lookup"><span data-stu-id="fb976-190">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="fb976-191">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="fb976-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fb976-192">**String** : spécifie une chaîne terminée par le caractère null.</span><span class="sxs-lookup"><span data-stu-id="fb976-192">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="fb976-193">Équivalent à **REG_SZ** .</span><span class="sxs-lookup"><span data-stu-id="fb976-193">Equivalent to **REG_SZ** .</span></span>
- <span data-ttu-id="fb976-194">**ExpandString** : spécifie une chaîne terminée par le caractère null qui contient des références non développées à des variables d’environnement qui sont développées lorsque la valeur est récupérée.</span><span class="sxs-lookup"><span data-stu-id="fb976-194">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="fb976-195">Équivalent à **REG_EXPAND_SZ** .</span><span class="sxs-lookup"><span data-stu-id="fb976-195">Equivalent to **REG_EXPAND_SZ** .</span></span>
- <span data-ttu-id="fb976-196">**Binary** : spécifie des données binaires sous n’importe quelle forme.</span><span class="sxs-lookup"><span data-stu-id="fb976-196">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="fb976-197">Équivalent à **REG_BINARY** .</span><span class="sxs-lookup"><span data-stu-id="fb976-197">Equivalent to **REG_BINARY** .</span></span>
- <span data-ttu-id="fb976-198">**DWORD** : spécifie un nombre binaire de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="fb976-198">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="fb976-199">Équivalent à **REG_DWORD** .</span><span class="sxs-lookup"><span data-stu-id="fb976-199">Equivalent to **REG_DWORD** .</span></span>
- <span data-ttu-id="fb976-200">**MultiString** : spécifie un tableau de chaînes terminées par le caractère null qui se sont terminées par deux caractères null.</span><span class="sxs-lookup"><span data-stu-id="fb976-200">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="fb976-201">Équivalent à **REG_MULTI_SZ** .</span><span class="sxs-lookup"><span data-stu-id="fb976-201">Equivalent to **REG_MULTI_SZ** .</span></span>
- <span data-ttu-id="fb976-202">**QWord** : spécifie un nombre binaire de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="fb976-202">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="fb976-203">Équivalent à **REG_QWORD** .</span><span class="sxs-lookup"><span data-stu-id="fb976-203">Equivalent to **REG_QWORD** .</span></span>
- <span data-ttu-id="fb976-204">**Inconnu** : indique un type de données de Registre non pris en charge, tel que **REG_RESOURCE_LIST** .</span><span class="sxs-lookup"><span data-stu-id="fb976-204">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST** .</span></span>

```yaml
Type: Microsoft.Win32.RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb976-205">-Value</span><span class="sxs-lookup"><span data-stu-id="fb976-205">-Value</span></span>

<span data-ttu-id="fb976-206">Spécifie la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="fb976-206">Specifies the value of the property.</span></span>

```yaml
Type: System.Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb976-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fb976-207">-Confirm</span></span>

<span data-ttu-id="fb976-208">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fb976-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fb976-209">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fb976-209">-WhatIf</span></span>

<span data-ttu-id="fb976-210">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fb976-210">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fb976-211">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="fb976-211">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fb976-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb976-212">CommonParameters</span></span>

<span data-ttu-id="fb976-213">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="fb976-213">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="fb976-214">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="fb976-214">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fb976-215">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fb976-215">INPUTS</span></span>

### <span data-ttu-id="fb976-216">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="fb976-216">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="fb976-217">Vous pouvez diriger les objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fb976-217">You can pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="fb976-218">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fb976-218">OUTPUTS</span></span>

### <span data-ttu-id="fb976-219">Aucun, System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="fb976-219">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="fb976-220">Cette applet de commande génère un objet **PSCustomObject** qui représente l’élément qui a été modifié et sa nouvelle valeur de propriété, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="fb976-220">This cmdlet generates a **PSCustomObject** object that represents the item that was changed and its new property value, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="fb976-221">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="fb976-221">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fb976-222">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fb976-222">NOTES</span></span>

<span data-ttu-id="fb976-223">`Set-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="fb976-223">`Set-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="fb976-224">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="fb976-224">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="fb976-225">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="fb976-225">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="fb976-226">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fb976-226">RELATED LINKS</span></span>

[<span data-ttu-id="fb976-227">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fb976-227">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="fb976-228">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fb976-228">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="fb976-229">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fb976-229">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="fb976-230">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fb976-230">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="fb976-231">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fb976-231">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="fb976-232">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fb976-232">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="fb976-233">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="fb976-233">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="fb976-234">about_Providers</span><span class="sxs-lookup"><span data-stu-id="fb976-234">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
