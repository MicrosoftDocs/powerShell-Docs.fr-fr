---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: 1314d388bff5a46bcf335f3da7908a65233aa46e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595490"
---
# <span data-ttu-id="1c205-102">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="1c205-102">Update-TypeData</span></span>

## <span data-ttu-id="1c205-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="1c205-103">Synopsis</span></span>
<span data-ttu-id="1c205-104">Met à jour les données de type étendu dans la session.</span><span class="sxs-lookup"><span data-stu-id="1c205-104">Updates the extended type data in the session.</span></span>

## <span data-ttu-id="1c205-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c205-105">Syntax</span></span>

### <span data-ttu-id="1c205-106">(Par défaut)</span><span class="sxs-lookup"><span data-stu-id="1c205-106">FileSet (Default)</span></span>

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1c205-107">DynamicTypeSet</span><span class="sxs-lookup"><span data-stu-id="1c205-107">DynamicTypeSet</span></span>

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1c205-108">TypeDataSet</span><span class="sxs-lookup"><span data-stu-id="1c205-108">TypeDataSet</span></span>

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1c205-109">Description</span><span class="sxs-lookup"><span data-stu-id="1c205-109">Description</span></span>

<span data-ttu-id="1c205-110">L' `Update-TypeData` applet de commande met à jour les données de type étendu dans la session en rechargeant les `Types.ps1xml` fichiers en mémoire et en ajoutant de nouvelles données de type étendu.</span><span class="sxs-lookup"><span data-stu-id="1c205-110">The `Update-TypeData` cmdlet updates the extended type data in the session by reloading the `Types.ps1xml` files into memory and adding new extended type data.</span></span>

<span data-ttu-id="1c205-111">Par défaut, PowerShell charge les données de type étendu en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="1c205-111">By default, PowerShell loads extended type data as it is needed.</span></span> <span data-ttu-id="1c205-112">Sans paramètres, `Update-TypeData` recharge tous les `Types.ps1xml` fichiers qu’il a chargés dans la session, y compris tous les fichiers de type que vous avez ajoutés.</span><span class="sxs-lookup"><span data-stu-id="1c205-112">Without parameters, `Update-TypeData` reloads all of the `Types.ps1xml` files that it has loaded in the session, including any type files that you added.</span></span> <span data-ttu-id="1c205-113">Vous pouvez utiliser les paramètres de `Update-TypeData` pour ajouter de nouveaux fichiers de type et ajouter et remplacer des données de type étendu.</span><span class="sxs-lookup"><span data-stu-id="1c205-113">You can use the parameters of `Update-TypeData` to add new type files and add and replace extended type data.</span></span>

<span data-ttu-id="1c205-114">L' `Update-TypeData` applet de commande peut être utilisée pour précharger toutes les données de type.</span><span class="sxs-lookup"><span data-stu-id="1c205-114">The `Update-TypeData` cmdlet can be used to preload all type data.</span></span> <span data-ttu-id="1c205-115">Cette fonctionnalité est particulièrement utile quand vous développez des types et que vous souhaitez charger ces nouveaux types à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="1c205-115">This feature is particularly useful when you are developing types and want to load those new types for testing purposes.</span></span>

<span data-ttu-id="1c205-116">À compter de Windows PowerShell 3,0, vous pouvez utiliser `Update-TypeData` pour ajouter et remplacer des données de type étendu dans la session sans utiliser de `Types.ps1xml` fichier.</span><span class="sxs-lookup"><span data-stu-id="1c205-116">Beginning in Windows PowerShell 3.0, you can use `Update-TypeData` to add and replace extended type data in the session without using a `Types.ps1xml` file.</span></span> <span data-ttu-id="1c205-117">Les données de type ajoutées de manière dynamique, c'est-à-dire sans fichier, sont ajoutées uniquement à la session active.</span><span class="sxs-lookup"><span data-stu-id="1c205-117">Type data that is added dynamically, that is, without a file, is added only to the current session.</span></span> <span data-ttu-id="1c205-118">Pour ajouter les données de type à toutes les sessions, ajoutez une `Update-TypeData` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c205-118">To add the type data to all sessions, add an `Update-TypeData` command to your PowerShell profile.</span></span> <span data-ttu-id="1c205-119">Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1c205-119">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="1c205-120">En outre, à compter de Windows PowerShell 3,0, vous pouvez utiliser l' `Get-TypeData` applet de commande pour récupérer les types étendus dans la session active et l' `Remove-TypeData` applet de commande pour supprimer les types étendus de la session active.</span><span class="sxs-lookup"><span data-stu-id="1c205-120">Also, beginning in Windows PowerShell 3.0, you can use the `Get-TypeData` cmdlet to get the extended types in the current session and the `Remove-TypeData` cmdlet to delete extended types from the current session.</span></span>

<span data-ttu-id="1c205-121">Les exceptions qui se produisent dans les propriétés, ou l’ajout de propriétés à une `Update-TypeData` commande, ne signalent pas d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="1c205-121">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors.</span></span> <span data-ttu-id="1c205-122">Cela permet de supprimer des exceptions qui se produisent dans de nombreux types courants durant la mise en forme et la sortie.</span><span class="sxs-lookup"><span data-stu-id="1c205-122">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="1c205-123">Si vous obtenez des propriétés .NET, vous pouvez contourner la suppression des exceptions en utilisant la syntaxe de méthode à la place, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1c205-123">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

`"hello".get_Length()`

<span data-ttu-id="1c205-124">Notez que la syntaxe de méthode peut uniquement être utilisée avec des propriétés .NET.</span><span class="sxs-lookup"><span data-stu-id="1c205-124">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="1c205-125">Les propriétés ajoutées en exécutant l’applet de commande `Update-TypeData` ne peuvent pas utiliser la syntaxe de méthode.</span><span class="sxs-lookup"><span data-stu-id="1c205-125">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

<span data-ttu-id="1c205-126">Pour plus d’informations sur les `Types.ps1xml` fichiers dans PowerShell, consultez [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="1c205-126">For more information about the `Types.ps1xml` files in PowerShell, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

## <span data-ttu-id="1c205-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="1c205-127">Examples</span></span>

### <span data-ttu-id="1c205-128">Exemple 1 : mettre à jour les types étendus</span><span class="sxs-lookup"><span data-stu-id="1c205-128">Example 1: Update extended types</span></span>

```powershell
Update-TypeData
```

<span data-ttu-id="1c205-129">Cette commande met à jour la configuration de type étendu à partir des `Types.ps1xml` fichiers qui ont déjà été utilisés dans la session.</span><span class="sxs-lookup"><span data-stu-id="1c205-129">This command updates the extended type configuration from the `Types.ps1xml` files that have already been used in the session.</span></span>

### <span data-ttu-id="1c205-130">Exemple 2 : mettre à jour les types plusieurs fois</span><span class="sxs-lookup"><span data-stu-id="1c205-130">Example 2: Update types multiple times</span></span>

<span data-ttu-id="1c205-131">Cet exemple montre comment mettre à jour les types dans un fichier de type plusieurs fois dans la même session.</span><span class="sxs-lookup"><span data-stu-id="1c205-131">This example shows how to update the types in a type file multiple times in the same session.</span></span>

<span data-ttu-id="1c205-132">La première commande met à jour la configuration de type étendu à partir des `Types.ps1xml` fichiers, en traitant les `TypesA.types.ps1xml` fichiers et en `TypesB.types.ps1xml` premier.</span><span class="sxs-lookup"><span data-stu-id="1c205-132">The first command updates the extended type configuration from the `Types.ps1xml` files, processing the `TypesA.types.ps1xml` and `TypesB.types.ps1xml` files first.</span></span>

<span data-ttu-id="1c205-133">La deuxième commande montre comment mettre à jour le `TypesA.types.ps1xml` , comme vous pouvez le faire si vous avez ajouté ou modifié un type dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="1c205-133">The second command shows how to update the `TypesA.types.ps1xml` again, such as you might do if you added or changed a type in the file.</span></span> <span data-ttu-id="1c205-134">Vous pouvez répéter la commande précédente pour le `TypesA.types.ps1xml` fichier ou exécuter une `Update-TypeData` commande sans paramètres, car `TypesA.types.ps1xml` figure déjà dans la liste des fichiers de type pour la session active.</span><span class="sxs-lookup"><span data-stu-id="1c205-134">You can either repeat the previous command for the `TypesA.types.ps1xml` file, or run an `Update-TypeData` command without parameters, because `TypesA.types.ps1xml` is already in the type file list for the current session.</span></span>

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### <span data-ttu-id="1c205-135">Exemple 3 : ajouter une propriété de script aux objets DateTime</span><span class="sxs-lookup"><span data-stu-id="1c205-135">Example 3: Add a script property to DateTime objects</span></span>

<span data-ttu-id="1c205-136">Cet exemple utilise `Update-TypeData` pour ajouter la propriété de script **Quarter** aux objets **System. DateTime** dans la session active, tels que ceux retournés par l’applet de commande `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="1c205-136">This example uses `Update-TypeData` to add the **Quarter** script property to **System.DateTime** objects in the current session, such as those returned by the `Get-Date` cmdlet.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

<span data-ttu-id="1c205-137">La `Update-TypeData` commande utilise le paramètre **TypeName** pour spécifier **le type System. DateTime** , le paramètre **MemberName** pour spécifier un nom pour la nouvelle propriété, la propriété **MemberType** pour spécifier le type **ScriptProperty** et le paramètre **value** pour spécifier le script qui détermine le trimestre annuel.</span><span class="sxs-lookup"><span data-stu-id="1c205-137">The `Update-TypeData` command uses the **TypeName** parameter to specify **the System.DateTime** type, the **MemberName** parameter to specify a name for the new property, the **MemberType** property to specify the **ScriptProperty** type, and the **Value** parameter to specify the script that determines the annual quarter.</span></span>

<span data-ttu-id="1c205-138">La valeur de la propriété **Value** est un script qui calcule le trimestre annuel actif.</span><span class="sxs-lookup"><span data-stu-id="1c205-138">The value of the **Value** property is a script that calculates the current annual quarter.</span></span> <span data-ttu-id="1c205-139">Le bloc de script utilise la `$this` variable automatique pour représenter l’instance actuelle de l’objet et l’opérateur in pour déterminer si la valeur de mois apparaît dans chaque tableau d’entiers.</span><span class="sxs-lookup"><span data-stu-id="1c205-139">The script block uses the `$this` automatic variable to represent the current instance of the object and the In operator to determine whether the month value appears in each integer array.</span></span> <span data-ttu-id="1c205-140">Pour plus d’informations sur l' `-in` opérateur, consultez [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="1c205-140">For more information about the `-in` operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).</span></span>

<span data-ttu-id="1c205-141">La deuxième commande obtient la nouvelle propriété Quarter de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="1c205-141">The second command gets the new Quarter property of the current date.</span></span>

### <span data-ttu-id="1c205-142">Exemple 4 : mettre à jour un type qui s’affiche dans des listes par défaut</span><span class="sxs-lookup"><span data-stu-id="1c205-142">Example 4: Update a type that displays in lists by default</span></span>

<span data-ttu-id="1c205-143">Cet exemple montre comment définir les propriétés d’un type qui s’affiche dans des listes par défaut, autrement dit, quand aucune propriété n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1c205-143">This example shows how to set the properties of a type that displays in lists by default, that is, when no properties are specified.</span></span> <span data-ttu-id="1c205-144">Étant donné que les données de type ne sont pas spécifiées dans un `Types.ps1xml` fichier, elles sont effectives uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="1c205-144">Because the type data is not specified in a `Types.ps1xml` file, it is effective only in the current session.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

<span data-ttu-id="1c205-145">La première commande utilise l' `Update-TypeData` applet de commande pour définir les propriétés de liste par défaut pour le type **System. DateTime** .</span><span class="sxs-lookup"><span data-stu-id="1c205-145">The first command uses the `Update-TypeData` cmdlet to set the default list properties for the **System.DateTime** type.</span></span> <span data-ttu-id="1c205-146">La commande utilise le paramètre **TypeName** pour spécifier le type et le paramètre **DefaultDisplayPropertySet** pour spécifier les propriétés par défaut d'une liste.</span><span class="sxs-lookup"><span data-stu-id="1c205-146">The command uses the **TypeName** parameter to specify the type and the **DefaultDisplayPropertySet** parameter to specify the default properties for a list.</span></span> <span data-ttu-id="1c205-147">Les propriétés sélectionnées incluent la nouvelle propriété de script **Quarter** qui a été ajoutée dans un exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="1c205-147">The selected properties include the new **Quarter** script property that was added in a previous example.</span></span>

<span data-ttu-id="1c205-148">La deuxième commande utilise l' `Get-Date` applet de commande pour obtenir un objet **System. DateTime** qui représente la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="1c205-148">The second command uses the `Get-Date` cmdlet to get a **System.DateTime** object that represents the current date.</span></span> <span data-ttu-id="1c205-149">La commande utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet **DateTime** à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="1c205-149">The command uses a pipeline operator (`|`) to send the **DateTime** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="1c205-150">Étant donné que la `Format-List` commande ne spécifie pas les propriétés à afficher dans la liste, PowerShell utilise les valeurs par défaut qui ont été établies par la `Update-TypeData` commande.</span><span class="sxs-lookup"><span data-stu-id="1c205-150">Because the `Format-List` command does not specify the properties to display in the list, PowerShell uses the default values that were established by the `Update-TypeData` command.</span></span>

### <span data-ttu-id="1c205-151">Exemple 5 : mettre à jour les données de type pour un objet dirigé</span><span class="sxs-lookup"><span data-stu-id="1c205-151">Example 5: Update type data for a piped object</span></span>

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

<span data-ttu-id="1c205-152">Cet exemple montre que lorsque vous dirigez un objet vers `Update-TypeData` , `Update-TypeData` ajoute des données de type étendu pour le type d’objet.</span><span class="sxs-lookup"><span data-stu-id="1c205-152">This example demonstrates that when you pipe an object to `Update-TypeData`, `Update-TypeData` adds extended type data for the object type.</span></span>

<span data-ttu-id="1c205-153">Cette technique est plus rapide que l’utilisation de l' `Get-Member` applet `Get-Type` de commande ou de la méthode pour accéder au type d’objet.</span><span class="sxs-lookup"><span data-stu-id="1c205-153">This technique is quicker than using the `Get-Member` cmdlet or the `Get-Type` method to get the object type.</span></span> <span data-ttu-id="1c205-154">Toutefois, si vous dirigez une collection d’objets vers `Update-TypeData` , elle met à jour les données de type du premier type d’objet, puis retourne une erreur pour tous les autres objets de la collection, car le membre est déjà défini sur le type.</span><span class="sxs-lookup"><span data-stu-id="1c205-154">However, if you pipe a collection of objects to `Update-TypeData`, it updates the type data of the first object type and then returns an error for all other objects in the collection because the member is already defined on the type.</span></span>

<span data-ttu-id="1c205-155">La première commande utilise l' `Get-Module` applet de commande pour récupérer le module PSScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="1c205-155">The first command uses the `Get-Module` cmdlet to get the PSScheduledJob module.</span></span> <span data-ttu-id="1c205-156">La commande dirige l’objet module vers l' `Update-TypeData` applet de commande, qui met à jour les données de type pour le type **System. Management. Automation. PSModuleInfo** et les types dérivés, tels que le type ModuleInfoGrouping qui `Get-Module` retourne quand vous utilisez le paramètre **listAvailable** dans la commande.</span><span class="sxs-lookup"><span data-stu-id="1c205-156">The command pipes the module object to the `Update-TypeData` cmdlet, which updates the type data for the **System.Management.Automation.PSModuleInfo** type and the types derived from it, such as the ModuleInfoGrouping type that `Get-Module` returns when you use the **ListAvailable** parameter in the command.</span></span>

<span data-ttu-id="1c205-157">La `Update-TypeData` commande ajoute la propriété de script **SupportsUpdatableHelp** à tous les modules importés.</span><span class="sxs-lookup"><span data-stu-id="1c205-157">The `Update-TypeData` commands adds the **SupportsUpdatableHelp** script property to all imported modules.</span></span> <span data-ttu-id="1c205-158">La valeur du paramètre **value** est un script qui retourne `$True` si la propriété **HelpInfoUri** du module est remplie et dans le `$False` cas contraire.</span><span class="sxs-lookup"><span data-stu-id="1c205-158">The value of the **Value** parameter is a script that returns `$True` if the **HelpInfoUri** property of the module is populated and `$False` otherwise.</span></span>

<span data-ttu-id="1c205-159">La deuxième commande transmet les objets de module de `Get-Module` à l’applet de commande `Format-Table` , qui affiche les propriétés **Name** et **SupportsUpdatableHelp** de tous les modules d’une liste.</span><span class="sxs-lookup"><span data-stu-id="1c205-159">The second command pipes the module objects from `Get-Module` to the `Format-Table` cmdlet, which displays the **Name** and **SupportsUpdatableHelp** properties of all modules in a list.</span></span>

## <span data-ttu-id="1c205-160">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c205-160">Parameters</span></span>

### <span data-ttu-id="1c205-161">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="1c205-161">-AppendPath</span></span>

<span data-ttu-id="1c205-162">Spécifie le chemin d’accès aux fichiers facultatifs `.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="1c205-162">Specifies the path to optional `.ps1xml` files.</span></span> <span data-ttu-id="1c205-163">Les fichiers spécifiés sont chargés dans l'ordre dans lequel ils sont répertoriés après le chargement des fichiers intégrés.</span><span class="sxs-lookup"><span data-stu-id="1c205-163">The specified files are loaded in the order that they are listed after the built-in files are loaded.</span></span> <span data-ttu-id="1c205-164">Vous pouvez également diriger une valeur **AppendPath** vers `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="1c205-164">You can also pipe an **AppendPath** value to `Update-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-165">-DefaultDisplayProperty</span><span class="sxs-lookup"><span data-stu-id="1c205-165">-DefaultDisplayProperty</span></span>

<span data-ttu-id="1c205-166">Spécifie la propriété du type qui est affiché par l' `Format-Wide` applet de commande quand aucune autre propriété n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1c205-166">Specifies the property of the type that is displayed by the `Format-Wide` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="1c205-167">Tapez le nom d'une propriété standard ou étendue du type.</span><span class="sxs-lookup"><span data-stu-id="1c205-167">Type the name of a standard or extended property of the type.</span></span> <span data-ttu-id="1c205-168">La valeur de ce paramètre peut correspondre au nom d'un type ajouté dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="1c205-168">The value of this parameter can be the name of a type that is added in the same command.</span></span>

<span data-ttu-id="1c205-169">Cette valeur est effective uniquement lorsqu’il n’existe aucune vue étendue définie pour le type dans un `Format.ps1xml` fichier.</span><span class="sxs-lookup"><span data-stu-id="1c205-169">This value is effective only when there are no wide views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="1c205-170">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-170">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-171">-DefaultDisplayPropertySet</span><span class="sxs-lookup"><span data-stu-id="1c205-171">-DefaultDisplayPropertySet</span></span>

<span data-ttu-id="1c205-172">Spécifie une ou plusieurs propriétés du type.</span><span class="sxs-lookup"><span data-stu-id="1c205-172">Specifies one or more properties of the type.</span></span> <span data-ttu-id="1c205-173">Ces propriétés sont affichées par l' `Format-List` applet de commande quand aucune autre propriété n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1c205-173">These properties are displayed by the `Format-List` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="1c205-174">Tapez les noms des propriétés standard ou étendues du type.</span><span class="sxs-lookup"><span data-stu-id="1c205-174">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="1c205-175">La valeur de ce paramètre peut correspondre aux noms des types ajoutés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="1c205-175">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="1c205-176">Cette valeur est effective uniquement quand il n’existe aucun affichage de liste défini pour le type dans un `Format.ps1xml` fichier.</span><span class="sxs-lookup"><span data-stu-id="1c205-176">This value is effective only when there are no list views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="1c205-177">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-177">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-178">-DefaultKeyPropertySet</span><span class="sxs-lookup"><span data-stu-id="1c205-178">-DefaultKeyPropertySet</span></span>

<span data-ttu-id="1c205-179">Spécifie une ou plusieurs propriétés du type.</span><span class="sxs-lookup"><span data-stu-id="1c205-179">Specifies one or more properties of the type.</span></span> <span data-ttu-id="1c205-180">Ces propriétés sont utilisées par les `Group-Object` applets de commande et `Sort-Object` quand aucune autre propriété n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1c205-180">These properties are used by the `Group-Object` and `Sort-Object` cmdlets when no other properties are specified.</span></span>

<span data-ttu-id="1c205-181">Tapez les noms des propriétés standard ou étendues du type.</span><span class="sxs-lookup"><span data-stu-id="1c205-181">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="1c205-182">La valeur de ce paramètre peut correspondre aux noms des types ajoutés dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="1c205-182">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="1c205-183">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-183">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-184">-Force</span><span class="sxs-lookup"><span data-stu-id="1c205-184">-Force</span></span>

<span data-ttu-id="1c205-185">Indique que l’applet de commande utilise les données de type spécifiées, même si des données de type ont déjà été spécifiées pour ce type.</span><span class="sxs-lookup"><span data-stu-id="1c205-185">Indicates that the cmdlet uses the specified type data, even if type data has already been specified for that type.</span></span>

<span data-ttu-id="1c205-186">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-186">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-187">-InheritPropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="1c205-187">-InheritPropertySerializationSet</span></span>

<span data-ttu-id="1c205-188">Indique si le jeu des propriétés sérialisées est hérité.</span><span class="sxs-lookup"><span data-stu-id="1c205-188">Indicates whether the set of properties that are serialized is inherited.</span></span> <span data-ttu-id="1c205-189">La valeur par défaut est `$Null`.</span><span class="sxs-lookup"><span data-stu-id="1c205-189">The default value is `$Null`.</span></span> <span data-ttu-id="1c205-190">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="1c205-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1c205-191">`$True`.</span><span class="sxs-lookup"><span data-stu-id="1c205-191">`$True`.</span></span> <span data-ttu-id="1c205-192">Le jeu de propriétés est hérité.</span><span class="sxs-lookup"><span data-stu-id="1c205-192">The property set is inherited.</span></span>
- <span data-ttu-id="1c205-193">`$False`.</span><span class="sxs-lookup"><span data-stu-id="1c205-193">`$False`.</span></span> <span data-ttu-id="1c205-194">Le jeu de propriétés n'est pas hérité.</span><span class="sxs-lookup"><span data-stu-id="1c205-194">The property set is not inherited.</span></span>
- <span data-ttu-id="1c205-195">`$Null`.</span><span class="sxs-lookup"><span data-stu-id="1c205-195">`$Null`.</span></span> <span data-ttu-id="1c205-196">L'héritage n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="1c205-196">Inheritance is not defined.</span></span>

<span data-ttu-id="1c205-197">Ce paramètre est valide uniquement lorsque la valeur du paramètre **SerializationMethod** est `SpecificProperties` .</span><span class="sxs-lookup"><span data-stu-id="1c205-197">This parameter is valid only when the value of the **SerializationMethod** parameter is `SpecificProperties`.</span></span> <span data-ttu-id="1c205-198">Lorsque la valeur de ce paramètre est `$False` , le paramètre **PropertySerializationSet** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1c205-198">When the value of this parameter is `$False`, the **PropertySerializationSet** parameter is required.</span></span>

<span data-ttu-id="1c205-199">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-199">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-200">-MemberName</span><span class="sxs-lookup"><span data-stu-id="1c205-200">-MemberName</span></span>

<span data-ttu-id="1c205-201">Spécifie le nom d'une propriété ou d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="1c205-201">Specifies the name of a property or method.</span></span>

<span data-ttu-id="1c205-202">Utilisez ce paramètre avec les paramètres **TypeName**, **MemberType**, **Value** et **SecondValue** pour ajouter ou modifier une propriété ou méthode d'un type.</span><span class="sxs-lookup"><span data-stu-id="1c205-202">Use this parameter with the **TypeName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="1c205-203">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-204">-MemberType</span><span class="sxs-lookup"><span data-stu-id="1c205-204">-MemberType</span></span>

<span data-ttu-id="1c205-205">Spécifie le type du membre à ajouter ou changer.</span><span class="sxs-lookup"><span data-stu-id="1c205-205">Specifies the type of the member to add or change.</span></span>

<span data-ttu-id="1c205-206">Utilisez ce paramètre avec les paramètres **TypeName**, **MemberType**, **Value** et **SecondValue** pour ajouter ou modifier une propriété ou méthode d'un type.</span><span class="sxs-lookup"><span data-stu-id="1c205-206">Use this parameter with the **TypeName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span> <span data-ttu-id="1c205-207">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="1c205-207">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1c205-208">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="1c205-208">AliasProperty</span></span>
- <span data-ttu-id="1c205-209">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="1c205-209">CodeMethod</span></span>
- <span data-ttu-id="1c205-210">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="1c205-210">CodeProperty</span></span>
- <span data-ttu-id="1c205-211">NoteProperty</span><span class="sxs-lookup"><span data-stu-id="1c205-211">Noteproperty</span></span>
- <span data-ttu-id="1c205-212">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="1c205-212">ScriptMethod</span></span>
- <span data-ttu-id="1c205-213">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="1c205-213">ScriptProperty</span></span>

<span data-ttu-id="1c205-214">Pour plus d’informations sur ces valeurs, consultez [énumération PSMemberTypes](/dotnet/api/system.management.automation.psmembertypes).</span><span class="sxs-lookup"><span data-stu-id="1c205-214">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes).</span></span>

<span data-ttu-id="1c205-215">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-216">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="1c205-216">-PrependPath</span></span>

<span data-ttu-id="1c205-217">Spécifie le chemin d’accès aux fichiers facultatifs `.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="1c205-217">Specifies the path to the optional `.ps1xml` files.</span></span> <span data-ttu-id="1c205-218">Les fichiers spécifiés sont chargés dans l'ordre dans lequel ils sont répertoriés avant le chargement des fichiers intégrés.</span><span class="sxs-lookup"><span data-stu-id="1c205-218">The specified files are loaded in the order that they are listed before the built-in files are loaded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-219">-PropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="1c205-219">-PropertySerializationSet</span></span>

<span data-ttu-id="1c205-220">Spécifie les noms des propriétés qui sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="1c205-220">Specifies the names of properties that are serialized.</span></span> <span data-ttu-id="1c205-221">Utilisez ce paramètre quand la valeur du paramètre **SerializationMethod** est **SpecificProperties**.</span><span class="sxs-lookup"><span data-stu-id="1c205-221">Use this parameter when the value of the **SerializationMethod** parameter is **SpecificProperties**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-222">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="1c205-222">-SecondValue</span></span>

<span data-ttu-id="1c205-223">Spécifie des valeurs supplémentaires pour les membres **AliasProperty**, **ScriptProperty**, **CodeProperty** ou **CodeMethod**.</span><span class="sxs-lookup"><span data-stu-id="1c205-223">Specifies additional values for **AliasProperty**, **ScriptProperty**, **CodeProperty**, or **CodeMethod** members.</span></span>

<span data-ttu-id="1c205-224">Utilisez ce paramètre avec les paramètres **TypeName**, **MemberType**, **value** et **SecondValue** pour ajouter ou modifier une propriété ou une méthode d’un type.</span><span class="sxs-lookup"><span data-stu-id="1c205-224">Use this parameter with the **TypeName**, **MemberType**, **Value**, and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="1c205-225">Quand la valeur du paramètre **MemberType** est `AliasProperty` , la valeur du paramètre **SecondValue** doit être un type de données.</span><span class="sxs-lookup"><span data-stu-id="1c205-225">When the value of the **MemberType** parameter is `AliasProperty`, the value of the **SecondValue** parameter must be a data type.</span></span> <span data-ttu-id="1c205-226">PowerShell convertit (autrement dit, effectue un cast) la valeur de la propriété d’alias vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="1c205-226">PowerShell converts (that is, casts) the value of the alias property to the specified type.</span></span> <span data-ttu-id="1c205-227">Par exemple, si vous ajoutez une propriété d’alias qui fournit un autre nom pour une propriété de type chaîne, vous pouvez également spécifier un **SecondValue** de **System. Int32** pour convertir la valeur de chaîne avec alias en entier.</span><span class="sxs-lookup"><span data-stu-id="1c205-227">For example, if you add an alias property that provides an alternate name for a string property, you can also specify a **SecondValue** of **System.Int32** to convert the aliased string value to an integer.</span></span>

<span data-ttu-id="1c205-228">Quand la valeur du paramètre **MemberType** est `ScriptProperty` , vous pouvez utiliser le paramètre **SecondValue** pour spécifier un bloc de script supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="1c205-228">When the value of the **MemberType** parameter is `ScriptProperty`, you can use the **SecondValue** parameter to specify an additional script block.</span></span> <span data-ttu-id="1c205-229">Le bloc de script dans la valeur du paramètre **Value** obtient la valeur d'une variable.</span><span class="sxs-lookup"><span data-stu-id="1c205-229">The script block in the value of the **Value** parameter gets the value of a variable.</span></span> <span data-ttu-id="1c205-230">Le bloc de script dans la valeur du paramètre **SecondValue** définit la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="1c205-230">The script block in the value of the **SecondValue** parameter set the value of the variable.</span></span>

<span data-ttu-id="1c205-231">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-231">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-232">-SerializationDepth</span><span class="sxs-lookup"><span data-stu-id="1c205-232">-SerializationDepth</span></span>

<span data-ttu-id="1c205-233">Spécifie le nombre de niveaux d'objets de type sérialisés en tant que chaînes.</span><span class="sxs-lookup"><span data-stu-id="1c205-233">Specifies how many levels of type objects are serialized as strings.</span></span> <span data-ttu-id="1c205-234">La valeur par défaut `1` sérialise l’objet et ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="1c205-234">The default value `1` serializes the object and its properties.</span></span> <span data-ttu-id="1c205-235">`0`La valeur sérialise l’objet, mais pas ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="1c205-235">A value of `0` serializes the object, but not its properties.</span></span> <span data-ttu-id="1c205-236">`2`La valeur sérialise l’objet, ses propriétés et tous les objets des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="1c205-236">A value of `2` serializes the object, its properties, and any objects in property values.</span></span>

<span data-ttu-id="1c205-237">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-237">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-238">-SerializationMethod</span><span class="sxs-lookup"><span data-stu-id="1c205-238">-SerializationMethod</span></span>

<span data-ttu-id="1c205-239">Spécifie une méthode de sérialisation pour le type.</span><span class="sxs-lookup"><span data-stu-id="1c205-239">Specifies a serialization method for the type.</span></span> <span data-ttu-id="1c205-240">Une méthode de sérialisation détermine quelles sont les propriétés du type qui sont sérialisées, ainsi que la technique de sérialisation utilisée.</span><span class="sxs-lookup"><span data-stu-id="1c205-240">A serialization method determines which properties of the type are serialized and the technique that is used to serialize them.</span></span> <span data-ttu-id="1c205-241">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="1c205-241">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1c205-242">`AllPublicProperties`.</span><span class="sxs-lookup"><span data-stu-id="1c205-242">`AllPublicProperties`.</span></span> <span data-ttu-id="1c205-243">sérialisez toutes les propriétés publiques du type.</span><span class="sxs-lookup"><span data-stu-id="1c205-243">Serialize all public properties of the type.</span></span> <span data-ttu-id="1c205-244">Vous pouvez utiliser le paramètre **SerializationDepth** pour déterminer si les propriétés enfants sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="1c205-244">You can use the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>
- <span data-ttu-id="1c205-245">`String`.</span><span class="sxs-lookup"><span data-stu-id="1c205-245">`String`.</span></span> <span data-ttu-id="1c205-246">sérialisez le type en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="1c205-246">Serialize the type as a string.</span></span> <span data-ttu-id="1c205-247">Vous pouvez utiliser **StringSerializationSource** pour spécifier une propriété du type à utiliser comme résultat de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1c205-247">You can use the **StringSerializationSource** to specify a property of the type to use as the serialization result.</span></span> <span data-ttu-id="1c205-248">Sinon, le type est sérialisé à l'aide de la méthode **ToString** de l'objet.</span><span class="sxs-lookup"><span data-stu-id="1c205-248">Otherwise, the type is serialized by using the **ToString** method of the object.</span></span>
- <span data-ttu-id="1c205-249">`SpecificProperties`.</span><span class="sxs-lookup"><span data-stu-id="1c205-249">`SpecificProperties`.</span></span> <span data-ttu-id="1c205-250">Sérialise uniquement les propriétés spécifiées de ce type.</span><span class="sxs-lookup"><span data-stu-id="1c205-250">Serialize only the specified properties of this type.</span></span> <span data-ttu-id="1c205-251">Utilisez le paramètre **PropertySerializationSet** pour spécifier les propriétés du type qui sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="1c205-251">Use the **PropertySerializationSet** parameter to specify the properties of the type that are serialized.</span></span>
  <span data-ttu-id="1c205-252">Vous pouvez également utiliser le paramètre **InheritPropertySerializationSet** pour déterminer si le jeu de propriétés est hérité, ainsi que le paramètre **SerializationDepth** pour déterminer si les propriétés enfants sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="1c205-252">You can also use the **InheritPropertySerializationSet** parameter to determine whether the property set is inherited and the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>

<span data-ttu-id="1c205-253">Dans PowerShell, les méthodes de sérialisation sont stockées dans des objets internes **PSStandardMembers** .</span><span class="sxs-lookup"><span data-stu-id="1c205-253">In PowerShell, serialization methods are stored in **PSStandardMembers** internal objects.</span></span>

<span data-ttu-id="1c205-254">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-254">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-255">-StringSerializationSource</span><span class="sxs-lookup"><span data-stu-id="1c205-255">-StringSerializationSource</span></span>

<span data-ttu-id="1c205-256">Spécifie le nom d'une propriété du type.</span><span class="sxs-lookup"><span data-stu-id="1c205-256">Specifies the name of a property of the type.</span></span> <span data-ttu-id="1c205-257">La valeur de la propriété spécifiée est utilisée comme résultat de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1c205-257">The value of specified property is used as the serialization result.</span></span> <span data-ttu-id="1c205-258">Ce paramètre est valide uniquement lorsque la valeur du paramètre **SerializationMethod** est String.</span><span class="sxs-lookup"><span data-stu-id="1c205-258">This parameter is valid only when the value of the **SerializationMethod** parameter is String.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-259">-TargetTypeForDeserialization</span><span class="sxs-lookup"><span data-stu-id="1c205-259">-TargetTypeForDeserialization</span></span>

<span data-ttu-id="1c205-260">Spécifie le type vers lequel les objets de ce type sont convertis quand ils sont désérialisés.</span><span class="sxs-lookup"><span data-stu-id="1c205-260">Specifies the type to which object of this type are converted when they are deserialized.</span></span>

<span data-ttu-id="1c205-261">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-262">-TypeAdapter</span><span class="sxs-lookup"><span data-stu-id="1c205-262">-TypeAdapter</span></span>

<span data-ttu-id="1c205-263">Spécifie le type d’un adaptateur de type, tel que **Microsoft. PowerShell. CIM. CimInstanceAdapter**.</span><span class="sxs-lookup"><span data-stu-id="1c205-263">Specifies the type of a type adapter, such as **Microsoft.PowerShell.Cim.CimInstanceAdapter**.</span></span> <span data-ttu-id="1c205-264">Un adaptateur de type permet à PowerShell d’obtenir les membres d’un type.</span><span class="sxs-lookup"><span data-stu-id="1c205-264">A type adapter enables PowerShell to get the members of a type.</span></span>

<span data-ttu-id="1c205-265">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-265">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-266">-TypeConverter</span><span class="sxs-lookup"><span data-stu-id="1c205-266">-TypeConverter</span></span>

<span data-ttu-id="1c205-267">Spécifie un convertisseur de type pour convertir des valeurs entre différents types.</span><span class="sxs-lookup"><span data-stu-id="1c205-267">Specifies a type converter to convert values between different types.</span></span> <span data-ttu-id="1c205-268">Si un convertisseur de type est défini pour un type, une instance du convertisseur de type est utilisée pour la conversion.</span><span class="sxs-lookup"><span data-stu-id="1c205-268">If a type converter is defined for a type, an instance of the type converter is used for the conversion.</span></span>

<span data-ttu-id="1c205-269">Entrez une valeur **System.Type** dérivée des classes **System.ComponentModel.TypeConverter** ou **System.Management.Automation.PSTypeConverter**.</span><span class="sxs-lookup"><span data-stu-id="1c205-269">Enter a **System.Type** value that is derived from the **System.ComponentModel.TypeConverter** or **System.Management.Automation.PSTypeConverter** classes.</span></span>

<span data-ttu-id="1c205-270">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-270">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-271">-TypeData</span><span class="sxs-lookup"><span data-stu-id="1c205-271">-TypeData</span></span>

<span data-ttu-id="1c205-272">Spécifie un tableau de données de type que cette applet de commande ajoute à la session.</span><span class="sxs-lookup"><span data-stu-id="1c205-272">Specifies an array of type data that this cmdlet adds to the session.</span></span> <span data-ttu-id="1c205-273">Entrez une variable qui contient un objet **TypeData** ou une commande qui obtient un objet **TypeData** , tel qu’une `Get-TypeData` commande.</span><span class="sxs-lookup"><span data-stu-id="1c205-273">Enter a variable that contains a **TypeData** object or a command that gets a **TypeData** object, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="1c205-274">Vous pouvez également diriger un objet **TypeData** vers `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="1c205-274">You can also pipe a **TypeData** object to `Update-TypeData`.</span></span>

<span data-ttu-id="1c205-275">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-275">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-276">-TypeName</span><span class="sxs-lookup"><span data-stu-id="1c205-276">-TypeName</span></span>

<span data-ttu-id="1c205-277">Spécifie le nom du type à étendre.</span><span class="sxs-lookup"><span data-stu-id="1c205-277">Specifies the name of the type to extend.</span></span>

<span data-ttu-id="1c205-278">Pour les types de l'espace de noms **System**, entrez le nom court.</span><span class="sxs-lookup"><span data-stu-id="1c205-278">For types in the **System** namespace, enter the short name.</span></span> <span data-ttu-id="1c205-279">Sinon, le nom de type complet est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1c205-279">Otherwise, the full type name is required.</span></span> <span data-ttu-id="1c205-280">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1c205-280">Wildcards are not supported.</span></span>

<span data-ttu-id="1c205-281">Vous pouvez diriger les noms de types vers `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="1c205-281">You can pipe type names to `Update-TypeData`.</span></span> <span data-ttu-id="1c205-282">Quand vous dirigez un objet vers `Update-TypeData` , `Update-TypeData` obtient le nom de type de l’objet et les données de type vers le type d’objet.</span><span class="sxs-lookup"><span data-stu-id="1c205-282">When you pipe an object to `Update-TypeData`, `Update-TypeData` gets the type name of the object and type data to the object type.</span></span>

<span data-ttu-id="1c205-283">Utilisez ce paramètre avec les paramètres **MemberName**, **MemberType**, **value** et **SecondValue** pour ajouter ou modifier une propriété ou une méthode d’un type.</span><span class="sxs-lookup"><span data-stu-id="1c205-283">Use this parameter with the **MemberName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="1c205-284">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-284">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-285">-Value</span><span class="sxs-lookup"><span data-stu-id="1c205-285">-Value</span></span>

<span data-ttu-id="1c205-286">Spécifie la valeur de la propriété ou de la méthode.</span><span class="sxs-lookup"><span data-stu-id="1c205-286">Specifies the value of the property or method.</span></span>

<span data-ttu-id="1c205-287">Si vous ajoutez un `AliasProperty` `CodeProperty` membre,, `ScriptProperty` ou `CodeMethod` , vous pouvez utiliser le paramètre **SecondValue** pour ajouter des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1c205-287">If you add an `AliasProperty`, `CodeProperty`, `ScriptProperty`, or `CodeMethod` member, you can use the **SecondValue** parameter to add additional information.</span></span>

<span data-ttu-id="1c205-288">Utilisez ce paramètre avec les paramètres **MemberName**, **MemberType**, **value** et **SecondValue** pour ajouter ou modifier une propriété ou une méthode d’un type.</span><span class="sxs-lookup"><span data-stu-id="1c205-288">Use this parameter with the **MemberName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="1c205-289">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1c205-289">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c205-290">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1c205-290">-Confirm</span></span>

<span data-ttu-id="1c205-291">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1c205-291">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1c205-292">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1c205-292">-WhatIf</span></span>

<span data-ttu-id="1c205-293">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1c205-293">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1c205-294">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="1c205-294">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1c205-295">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1c205-295">CommonParameters</span></span>

<span data-ttu-id="1c205-296">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1c205-296">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1c205-297">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1c205-297">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1c205-298">Entrées</span><span class="sxs-lookup"><span data-stu-id="1c205-298">Inputs</span></span>

### <span data-ttu-id="1c205-299">System.String</span><span class="sxs-lookup"><span data-stu-id="1c205-299">System.String</span></span>

<span data-ttu-id="1c205-300">Vous pouvez diriger une chaîne qui contient les valeurs des paramètres **AppendPath**, **TypeName** ou **TypeData** vers `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="1c205-300">You can pipe a string that contains the values of the **AppendPath**, **TypeName**, or **TypeData** parameters to `Update-TypeData`.</span></span>

## <span data-ttu-id="1c205-301">Sorties</span><span class="sxs-lookup"><span data-stu-id="1c205-301">Outputs</span></span>

### <span data-ttu-id="1c205-302">None</span><span class="sxs-lookup"><span data-stu-id="1c205-302">None</span></span>

<span data-ttu-id="1c205-303">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1c205-303">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="1c205-304">Notes</span><span class="sxs-lookup"><span data-stu-id="1c205-304">Notes</span></span>

## <span data-ttu-id="1c205-305">Liens connexes</span><span class="sxs-lookup"><span data-stu-id="1c205-305">Related links</span></span>

[<span data-ttu-id="1c205-306">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="1c205-306">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="1c205-307">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="1c205-307">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="1c205-308">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="1c205-308">Remove-TypeData</span></span>](Remove-TypeData.md)

