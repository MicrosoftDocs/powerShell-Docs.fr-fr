---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: cbd1229721650823d9780517934c40a2287f4227
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692661"
---
# <span data-ttu-id="d49d6-103">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d49d6-103">Set-ItemProperty</span></span>

## <span data-ttu-id="d49d6-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d49d6-104">SYNOPSIS</span></span>
<span data-ttu-id="d49d6-105">Crée ou modifie la valeur d'une propriété d'un élément.</span><span class="sxs-lookup"><span data-stu-id="d49d6-105">Creates or changes the value of a property of an item.</span></span>

## <span data-ttu-id="d49d6-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d49d6-106">SYNTAX</span></span>

### <span data-ttu-id="d49d6-107">propertyValuePathSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d49d6-107">propertyValuePathSet (Default)</span></span>

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="d49d6-108">propertyPSObjectPathSet</span><span class="sxs-lookup"><span data-stu-id="d49d6-108">propertyPSObjectPathSet</span></span>

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="d49d6-109">propertyValueLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="d49d6-109">propertyValueLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="d49d6-110">propertyPSObjectLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="d49d6-110">propertyPSObjectLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="d49d6-111">Description</span><span class="sxs-lookup"><span data-stu-id="d49d6-111">DESCRIPTION</span></span>

<span data-ttu-id="d49d6-112">L' `Set-ItemProperty` applet de commande modifie la valeur de la propriété de l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="d49d6-112">The `Set-ItemProperty` cmdlet changes the value of the property of the specified item.</span></span> <span data-ttu-id="d49d6-113">Vous pouvez utiliser cette applet de commande pour définir ou modifier les propriétés d'éléments.</span><span class="sxs-lookup"><span data-stu-id="d49d6-113">You can use the cmdlet to establish or change the properties of items.</span></span> <span data-ttu-id="d49d6-114">Par exemple, vous pouvez utiliser `Set-ItemProperty` pour définir la valeur de la propriété **IsReadOnly** d’un objet fichier sur `$True` .</span><span class="sxs-lookup"><span data-stu-id="d49d6-114">For example, you can use `Set-ItemProperty` to set the value of the **IsReadOnly** property of a file object to `$True`.</span></span>

<span data-ttu-id="d49d6-115">Vous pouvez également utiliser `Set-ItemProperty` pour créer et modifier les valeurs de Registre et les données.</span><span class="sxs-lookup"><span data-stu-id="d49d6-115">You also use `Set-ItemProperty` to create and change registry values and data.</span></span>
<span data-ttu-id="d49d6-116">Par exemple, vous pouvez ajouter une nouvelle entrée de Registre à une clé, puis définir ou modifier sa valeur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-116">For example, you can add a new registry entry to a key and establish or change its value.</span></span>

## <span data-ttu-id="d49d6-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d49d6-117">EXAMPLES</span></span>

### <span data-ttu-id="d49d6-118">Exemple 1 : définir une propriété d’un fichier</span><span class="sxs-lookup"><span data-stu-id="d49d6-118">Example 1: Set a property of a file</span></span>

<span data-ttu-id="d49d6-119">Cette commande affecte la valeur « true » à la propriété **IsReadOnly** du fichier « final.doc ».</span><span class="sxs-lookup"><span data-stu-id="d49d6-119">This command sets the value of the **IsReadOnly** property of the "final.doc" file to "true".</span></span> <span data-ttu-id="d49d6-120">Elle utilise **path** pour spécifier le fichier, **Name** pour spécifier le nom de la propriété et le paramètre **value** pour spécifier la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-120">It uses **Path** to specify the file, **Name** to specify the name of the property, and the **Value** parameter to specify the new value.</span></span>

<span data-ttu-id="d49d6-121">Le fichier est un objet **System. IO. FileInfo** et **IsReadOnly** est simplement l’une de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="d49d6-121">The file is a **System.IO.FileInfo** object and **IsReadOnly** is just one of its properties.</span></span>
<span data-ttu-id="d49d6-122">Pour afficher toutes les propriétés, tapez `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property` .</span><span class="sxs-lookup"><span data-stu-id="d49d6-122">To see all of the properties, type `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property`.</span></span>

<span data-ttu-id="d49d6-123">La `$true` variable automatique représente une valeur « true ».</span><span class="sxs-lookup"><span data-stu-id="d49d6-123">The `$true` automatic variable represents a value of "TRUE".</span></span>
<span data-ttu-id="d49d6-124">Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="d49d6-124">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### <span data-ttu-id="d49d6-125">Exemple 2 : créer une entrée et une valeur de Registre</span><span class="sxs-lookup"><span data-stu-id="d49d6-125">Example 2: Create a registry entry and value</span></span>

<span data-ttu-id="d49d6-126">Cet exemple montre comment utiliser `Set-ItemProperty` pour créer une nouvelle entrée de Registre et affecter une valeur à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="d49d6-126">This example shows how to use `Set-ItemProperty` to create a new registry entry and to assign a value to the entry.</span></span> <span data-ttu-id="d49d6-127">Il crée l’entrée « NoOfEmployees » dans la clé « ContosoCompany » de la clé « HKLM\Software » et définit sa valeur sur 823.</span><span class="sxs-lookup"><span data-stu-id="d49d6-127">It creates the "NoOfEmployees" entry in the "ContosoCompany" key in "HKLM\Software" key and sets its value to 823.</span></span>

<span data-ttu-id="d49d6-128">Étant donné que les entrées de Registre sont considérées comme des propriétés des clés de Registre, qui sont des éléments, vous utilisez `Set-ItemProperty` pour créer des entrées de Registre et pour définir et modifier leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="d49d6-128">Because registry entries are considered to be properties of the registry keys, which are items, you use `Set-ItemProperty` to create registry entries, and to establish and change their values.</span></span>

<span data-ttu-id="d49d6-129">La première commande crée l’entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="d49d6-129">The first command creates the registry entry.</span></span>
<span data-ttu-id="d49d6-130">Elle utilise **path** pour spécifier le chemin d’accès du `HKLM:` lecteur et la clé « Software\MyCompany. ».</span><span class="sxs-lookup"><span data-stu-id="d49d6-130">It uses **Path** to specify the path of the `HKLM:` drive and the "Software\MyCompany" key.</span></span>
<span data-ttu-id="d49d6-131">La commande utilise **Name** pour spécifier le nom et la **valeur** de l’entrée pour spécifier une valeur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-131">The command uses **Name** to specify the entry name and **Value** to specify a value.</span></span>

<span data-ttu-id="d49d6-132">La deuxième commande utilise l' `Get-ItemProperty` applet de commande pour afficher la nouvelle entrée de registre.</span><span class="sxs-lookup"><span data-stu-id="d49d6-132">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span> <span data-ttu-id="d49d6-133">Si vous utilisez les `Get-Item` applets de commande ou `Get-ChildItem` , les entrées ne s’affichent pas, car il s’agit des propriétés d’une clé, et non des éléments ou des éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="d49d6-133">If you use the `Get-Item` or `Get-ChildItem` cmdlets, the entries do not appear because they are properties of a key, not items or child items.</span></span>

<span data-ttu-id="d49d6-134">La troisième commande modifie la valeur de l’entrée **NoOfEmployees** en 824.</span><span class="sxs-lookup"><span data-stu-id="d49d6-134">The third command changes the value of the **NoOfEmployees** entry to 824.</span></span>

<span data-ttu-id="d49d6-135">Vous pouvez également utiliser l' `New-ItemProperty` applet de commande pour créer l’entrée de Registre et sa valeur, puis utiliser `Set-ItemProperty` pour modifier la valeur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-135">You can also use the `New-ItemProperty` cmdlet to create the registry entry and its value and then use `Set-ItemProperty` to change the value.</span></span>

<span data-ttu-id="d49d6-136">Pour plus d’informations sur le `HKLM:` lecteur, tapez `Get-Help Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="d49d6-136">For more information about the `HKLM:` drive, type `Get-Help Get-PSDrive`.</span></span>
<span data-ttu-id="d49d6-137">Pour plus d’informations sur l’utilisation de PowerShell pour gérer le registre, tapez `Get-Help Registry` .</span><span class="sxs-lookup"><span data-stu-id="d49d6-137">For more information about how to use PowerShell to manage the registry, type `Get-Help Registry`.</span></span>

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
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

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

### <span data-ttu-id="d49d6-138">Exemple 3 : modifier un élément à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="d49d6-138">Example 3: Modify an item by using the pipeline</span></span>

<span data-ttu-id="d49d6-139">Ces commandes montrent comment utiliser un opérateur de pipeline ( `|` ) pour envoyer un élément à `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="d49d6-139">These commands show how to use a pipeline operator (`|`) to send an item to `Set-ItemProperty`.</span></span>

<span data-ttu-id="d49d6-140">La première partie de la commande utilise `Get-ChildItem` pour récupérer un objet qui représente le fichier « Weekly.txt ».</span><span class="sxs-lookup"><span data-stu-id="d49d6-140">The first part of the command uses `Get-ChildItem` to get an object that represents the "Weekly.txt" file.</span></span>
<span data-ttu-id="d49d6-141">La commande utilise un opérateur de pipeline auquel envoyer l’objet fichier `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="d49d6-141">The command uses a pipeline operator to send the file object to `Set-ItemProperty`.</span></span>
<span data-ttu-id="d49d6-142">La `Set-ItemProperty` commande utilise les paramètres **Name** et **value** pour spécifier la propriété et sa nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-142">The `Set-ItemProperty` command uses the **Name** and **Value** parameters to specify the property and its new value.</span></span>

<span data-ttu-id="d49d6-143">Cette commande revient à utiliser le paramètre **InputObject** pour spécifier l’objet qui `Get-ChildItem` obtient.</span><span class="sxs-lookup"><span data-stu-id="d49d6-143">This command is equivalent to using the **InputObject** parameter to specify the object that `Get-ChildItem` gets.</span></span>

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## <span data-ttu-id="d49d6-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d49d6-144">PARAMETERS</span></span>

### <span data-ttu-id="d49d6-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="d49d6-145">-Credential</span></span>

<span data-ttu-id="d49d6-146">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="d49d6-146">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="d49d6-147">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="d49d6-147">The default is the current user.</span></span>

<span data-ttu-id="d49d6-148">Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential**, tel que celui généré par l’applet de commande `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="d49d6-148">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="d49d6-149">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="d49d6-149">If you type a user name, you are prompted for a password.</span></span>

> [!NOTE]
> <span data-ttu-id="d49d6-150">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d49d6-150">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="d49d6-151">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="d49d6-151">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="d49d6-152">-Exclude</span><span class="sxs-lookup"><span data-stu-id="d49d6-152">-Exclude</span></span>

<span data-ttu-id="d49d6-153">Spécifie les éléments sur lesquels l’applet de commande n’agit pas, et comprend tous les autres.</span><span class="sxs-lookup"><span data-stu-id="d49d6-153">Specifies those items upon which the cmdlet does not act, and includes all others.</span></span>
<span data-ttu-id="d49d6-154">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-154">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="d49d6-155">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="d49d6-155">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="d49d6-156">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d49d6-156">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d49d6-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="d49d6-157">-Filter</span></span>

<span data-ttu-id="d49d6-158">Spécifie un filtre dans le format ou la langue du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-158">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="d49d6-159">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-159">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="d49d6-160">La syntaxe du filtre, notamment l’utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-160">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="d49d6-161">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="d49d6-161">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="d49d6-162">-Force</span><span class="sxs-lookup"><span data-stu-id="d49d6-162">-Force</span></span>

<span data-ttu-id="d49d6-163">Force l’applet de commande à définir une propriété sur des éléments qui, sinon, ne sont pas accessibles par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-163">Forces the cmdlet to set a property on items that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="d49d6-164">L'implémentation est différente d'un fournisseur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="d49d6-164">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="d49d6-165">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="d49d6-165">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="d49d6-166">-Include</span><span class="sxs-lookup"><span data-stu-id="d49d6-166">-Include</span></span>

<span data-ttu-id="d49d6-167">Spécifie uniquement les éléments sur lesquels l’applet de commande agit, ce qui exclut tous les autres.</span><span class="sxs-lookup"><span data-stu-id="d49d6-167">Specifies only those items upon which the cmdlet acts, which excludes all others.</span></span>
<span data-ttu-id="d49d6-168">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-168">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="d49d6-169">Entrez un élément ou un modèle de chemin d'accès, tel que « \*.txt ».</span><span class="sxs-lookup"><span data-stu-id="d49d6-169">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="d49d6-170">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="d49d6-170">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d49d6-171">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d49d6-171">-InputObject</span></span>

<span data-ttu-id="d49d6-172">Spécifie l’objet qui a les propriétés modifiées par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d49d6-172">Specifies the object that has the properties that this cmdlet changes.</span></span>
<span data-ttu-id="d49d6-173">Entrez une variable qui contient l'objet ou tapez une commande permettant d'obtenir cet objet.</span><span class="sxs-lookup"><span data-stu-id="d49d6-173">Enter a variable that contains the object or a command that gets the object.</span></span>

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

### <span data-ttu-id="d49d6-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d49d6-174">-LiteralPath</span></span>

<span data-ttu-id="d49d6-175">Spécifie le chemin d’accès de la propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="d49d6-175">Specifies a path of the item property.</span></span>
<span data-ttu-id="d49d6-176">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="d49d6-176">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="d49d6-177">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="d49d6-177">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="d49d6-178">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="d49d6-178">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="d49d6-179">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="d49d6-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d49d6-180">-Name</span><span class="sxs-lookup"><span data-stu-id="d49d6-180">-Name</span></span>

<span data-ttu-id="d49d6-181">Spécifie le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d49d6-181">Specifies the name of the property.</span></span>

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

### <span data-ttu-id="d49d6-182">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d49d6-182">-PassThru</span></span>

<span data-ttu-id="d49d6-183">Retourne un objet qui représente la propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="d49d6-183">Returns an object that represents the item property.</span></span>
<span data-ttu-id="d49d6-184">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="d49d6-184">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d49d6-185">-Path</span><span class="sxs-lookup"><span data-stu-id="d49d6-185">-Path</span></span>

<span data-ttu-id="d49d6-186">Spécifie le chemin d’accès des éléments avec la propriété à modifier.</span><span class="sxs-lookup"><span data-stu-id="d49d6-186">Specifies the path of the items with the property to modify.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d49d6-187">-Type</span><span class="sxs-lookup"><span data-stu-id="d49d6-187">-Type</span></span>

<span data-ttu-id="d49d6-188">Le **type** est un paramètre dynamique que le fournisseur du Registre ajoute à l’applet de commande `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="d49d6-188">**Type** is a dynamic parameter that the Registry provider adds to the `Set-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="d49d6-189">Ce paramètre fonctionne uniquement dans les lecteurs de registre.</span><span class="sxs-lookup"><span data-stu-id="d49d6-189">This parameter only works in the registry drives.</span></span>

<span data-ttu-id="d49d6-190">Spécifie le type de propriété que cette applet de commande ajoute.</span><span class="sxs-lookup"><span data-stu-id="d49d6-190">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="d49d6-191">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="d49d6-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d49d6-192">**String**: spécifie une chaîne terminée par le caractère null.</span><span class="sxs-lookup"><span data-stu-id="d49d6-192">**String**: Specifies a null-terminated string.</span></span> <span data-ttu-id="d49d6-193">Équivalent à **REG_SZ**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-193">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="d49d6-194">**ExpandString**: spécifie une chaîne terminée par le caractère null qui contient des références non développées à des variables d’environnement qui sont développées lorsque la valeur est récupérée.</span><span class="sxs-lookup"><span data-stu-id="d49d6-194">**ExpandString**: Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="d49d6-195">Équivalent à **REG_EXPAND_SZ**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-195">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="d49d6-196">**Binary**: spécifie des données binaires sous n’importe quelle forme.</span><span class="sxs-lookup"><span data-stu-id="d49d6-196">**Binary**: Specifies binary data in any form.</span></span> <span data-ttu-id="d49d6-197">Équivalent à **REG_BINARY**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-197">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="d49d6-198">**DWORD**: spécifie un nombre binaire de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d49d6-198">**DWord**: Specifies a 32-bit binary number.</span></span> <span data-ttu-id="d49d6-199">Équivalent à **REG_DWORD**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-199">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="d49d6-200">**MultiString**: spécifie un tableau de chaînes terminées par le caractère null qui se sont terminées par deux caractères null.</span><span class="sxs-lookup"><span data-stu-id="d49d6-200">**MultiString**: Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="d49d6-201">Équivalent à **REG_MULTI_SZ**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-201">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="d49d6-202">**QWord**: spécifie un nombre binaire de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d49d6-202">**Qword**: Specifies a 64-bit binary number.</span></span> <span data-ttu-id="d49d6-203">Équivalent à **REG_QWORD**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-203">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="d49d6-204">**Inconnu**: indique un type de données de Registre non pris en charge, tel que **REG_RESOURCE_LIST**.</span><span class="sxs-lookup"><span data-stu-id="d49d6-204">**Unknown**: Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d49d6-205">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="d49d6-205">-UseTransaction</span></span>

<span data-ttu-id="d49d6-206">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="d49d6-206">Includes the command in the active transaction.</span></span>
<span data-ttu-id="d49d6-207">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="d49d6-207">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="d49d6-208">Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="d49d6-208">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d49d6-209">-Value</span><span class="sxs-lookup"><span data-stu-id="d49d6-209">-Value</span></span>

<span data-ttu-id="d49d6-210">Spécifie la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d49d6-210">Specifies the value of the property.</span></span>

```yaml
Type: Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d49d6-211">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d49d6-211">-Confirm</span></span>

<span data-ttu-id="d49d6-212">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d49d6-212">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d49d6-213">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d49d6-213">-WhatIf</span></span>

<span data-ttu-id="d49d6-214">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d49d6-214">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d49d6-215">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d49d6-215">The cmdlet is not run.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d49d6-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d49d6-216">CommonParameters</span></span>

<span data-ttu-id="d49d6-217">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="d49d6-217">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="d49d6-218">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="d49d6-218">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d49d6-219">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d49d6-219">INPUTS</span></span>

### <span data-ttu-id="d49d6-220">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="d49d6-220">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="d49d6-221">Vous pouvez diriger les objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d49d6-221">You can pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="d49d6-222">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d49d6-222">OUTPUTS</span></span>

### <span data-ttu-id="d49d6-223">Aucun, System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="d49d6-223">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="d49d6-224">Cette applet de commande génère un objet **PSCustomObject** qui représente l’élément qui a été modifié et sa nouvelle valeur de propriété, si vous spécifiez le paramètre **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="d49d6-224">This cmdlet generates a **PSCustomObject** object that represents the item that was changed and its new property value, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="d49d6-225">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="d49d6-225">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d49d6-226">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d49d6-226">NOTES</span></span>

<span data-ttu-id="d49d6-227">`Set-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="d49d6-227">`Set-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d49d6-228">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="d49d6-228">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="d49d6-229">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="d49d6-229">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="d49d6-230">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d49d6-230">RELATED LINKS</span></span>

[<span data-ttu-id="d49d6-231">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d49d6-231">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="d49d6-232">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d49d6-232">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="d49d6-233">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d49d6-233">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="d49d6-234">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d49d6-234">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="d49d6-235">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d49d6-235">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="d49d6-236">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d49d6-236">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="d49d6-237">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d49d6-237">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)
