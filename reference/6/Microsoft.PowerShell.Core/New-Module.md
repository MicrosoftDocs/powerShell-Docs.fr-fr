---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: d0c0388142092034b06a2185dadcaed2f19d9865
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204514"
---
# <span data-ttu-id="cff42-103">New-Module</span><span class="sxs-lookup"><span data-stu-id="cff42-103">New-Module</span></span>

## <span data-ttu-id="cff42-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="cff42-104">SYNOPSIS</span></span>
<span data-ttu-id="cff42-105">Crée un module dynamique qui existe uniquement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="cff42-105">Creates a new dynamic module that exists only in memory.</span></span>

## <span data-ttu-id="cff42-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cff42-106">SYNTAX</span></span>

### <span data-ttu-id="cff42-107">ScriptBlock (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="cff42-107">ScriptBlock (Default)</span></span>

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="cff42-108">Nom</span><span class="sxs-lookup"><span data-stu-id="cff42-108">Name</span></span>

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="cff42-109">Description</span><span class="sxs-lookup"><span data-stu-id="cff42-109">DESCRIPTION</span></span>

<span data-ttu-id="cff42-110">L' `New-Module` applet de commande crée un module dynamique à partir d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="cff42-110">The `New-Module` cmdlet creates a dynamic module from a script block.</span></span> <span data-ttu-id="cff42-111">Les membres du module dynamique, tels des fonctions et des variables, sont immédiatement disponibles dans la session et restent disponibles jusqu'à la fermeture de la session.</span><span class="sxs-lookup"><span data-stu-id="cff42-111">The members of the dynamic module, such as functions and variables, are immediately available in the session and remain available until you close the session.</span></span>

<span data-ttu-id="cff42-112">Comme des modules statiques, les applets de commande et les fonctions figurant dans un module dynamique sont exportées par défaut, alors que les variables et les alias ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="cff42-112">Like static modules, by default, the cmdlets and functions in a dynamic module are exported and the variables and aliases are not.</span></span> <span data-ttu-id="cff42-113">Toutefois, vous pouvez utiliser l’applet de commande Export-ModuleMember et les paramètres de `New-Module` pour remplacer les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="cff42-113">However, you can use the Export-ModuleMember cmdlet and the parameters of `New-Module` to override the defaults.</span></span>

<span data-ttu-id="cff42-114">Vous pouvez également utiliser le paramètre **AsCustomObject** de `New-Module` pour retourner le module dynamique en tant qu’objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="cff42-114">You can also use the **AsCustomObject** parameter of `New-Module` to return the dynamic module as a custom object.</span></span> <span data-ttu-id="cff42-115">Les membres des modules, tels que les fonctions, sont implémentés en tant que méthodes de script de l'objet personnalisé au lieu d'être importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="cff42-115">The members of the modules, such as functions, are implemented as script methods of the custom object instead of being imported into the session.</span></span>

<span data-ttu-id="cff42-116">Les modules dynamiques existent uniquement en mémoire, pas sur le disque.</span><span class="sxs-lookup"><span data-stu-id="cff42-116">Dynamic modules exist only in memory, not on disk.</span></span> <span data-ttu-id="cff42-117">Comme tous les modules, les membres des modules dynamiques s'exécutent dans une étendue de module privée qui est un enfant de l'étendue globale.</span><span class="sxs-lookup"><span data-stu-id="cff42-117">Like all modules, the members of dynamic modules run in a private module scope that is a child of the global scope.</span></span> <span data-ttu-id="cff42-118">Get-Module ne peut pas obtenir un module dynamique, mais Get-Command peut obtenir les membres exportés.</span><span class="sxs-lookup"><span data-stu-id="cff42-118">Get-Module cannot get a dynamic module, but Get-Command can get the exported members.</span></span>

<span data-ttu-id="cff42-119">Pour mettre un module dynamique à la disposition de `Get-Module` , dirigez une `New-Module` commande vers Import-Module, ou dirigez l’objet de module qui `New-Module` retourne à `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="cff42-119">To make a dynamic module available to `Get-Module`, pipe a `New-Module` command to Import-Module, or pipe the module object that `New-Module` returns to `Import-Module`.</span></span> <span data-ttu-id="cff42-120">Cette action ajoute le module dynamique à la `Get-Module` liste, mais il n’enregistre pas le module sur le disque ou le rend persistant.</span><span class="sxs-lookup"><span data-stu-id="cff42-120">This action adds the dynamic module to the `Get-Module` list, but it does not save the module to disk or make it persistent.</span></span>

## <span data-ttu-id="cff42-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="cff42-121">EXAMPLES</span></span>

### <span data-ttu-id="cff42-122">Exemple 1 : créer un module dynamique</span><span class="sxs-lookup"><span data-stu-id="cff42-122">Example 1: Create a dynamic module</span></span>

<span data-ttu-id="cff42-123">Cet exemple crée un nouveau module dynamique avec une fonction appelée `Hello` .</span><span class="sxs-lookup"><span data-stu-id="cff42-123">This example creates a new dynamic module with a function called `Hello`.</span></span> <span data-ttu-id="cff42-124">La commande retourne un objet de module qui représente le nouveau module dynamique.</span><span class="sxs-lookup"><span data-stu-id="cff42-124">The command returns a module object that represents the new dynamic module.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### <span data-ttu-id="cff42-125">Exemple 2 : utilisation des modules dynamiques et des Get-Module et des Get-Command</span><span class="sxs-lookup"><span data-stu-id="cff42-125">Example 2: Working with dynamic modules and Get-Module and Get-Command</span></span>

<span data-ttu-id="cff42-126">Cet exemple montre que les modules dynamiques ne sont pas retournés par l’applet de commande `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="cff42-126">This example demonstrates that dynamic modules are not returned by the `Get-Module` cmdlet.</span></span> <span data-ttu-id="cff42-127">Les membres qu’ils exportent sont retournés par l’applet de commande `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="cff42-127">The members that they export are returned by the `Get-Command` cmdlet.</span></span>

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### <span data-ttu-id="cff42-128">Exemple 3 : exporter une variable dans la session active</span><span class="sxs-lookup"><span data-stu-id="cff42-128">Example 3: Export a variable into the current session</span></span>

<span data-ttu-id="cff42-129">Cet exemple utilise l' `Export-ModuleMember` applet de commande pour exporter une variable dans la session active.</span><span class="sxs-lookup"><span data-stu-id="cff42-129">This example uses the `Export-ModuleMember` cmdlet to export a variable into the current session.</span></span>
<span data-ttu-id="cff42-130">Sans la `Export-ModuleMember` commande, seule la fonction est exportée.</span><span class="sxs-lookup"><span data-stu-id="cff42-130">Without the `Export-ModuleMember` command, only the function is exported.</span></span>

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

<span data-ttu-id="cff42-131">La sortie indique que la variable et la fonction ont été exportées dans la session.</span><span class="sxs-lookup"><span data-stu-id="cff42-131">The output shows that both the variable and the function were exported into the session.</span></span>

### <span data-ttu-id="cff42-132">Exemple 4 : mettre un module dynamique à la disposition d' Get-Module</span><span class="sxs-lookup"><span data-stu-id="cff42-132">Example 4: Make a dynamic module available to Get-Module</span></span>

<span data-ttu-id="cff42-133">Cet exemple montre que vous pouvez mettre un module dynamique à la disposition de `Get-Module` en canalisant le module dynamique vers `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="cff42-133">This example demonstrates that you can make a dynamic module available to `Get-Module` by piping the dynamic module to `Import-Module`.</span></span>

<span data-ttu-id="cff42-134">`New-Module` crée un objet de module qui est dirigé vers l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="cff42-134">`New-Module` creates a module object that is piped to the `Import-Module` cmdlet.</span></span> <span data-ttu-id="cff42-135">Le paramètre **Name** de `New-Module` affecte un nom convivial au module.</span><span class="sxs-lookup"><span data-stu-id="cff42-135">The **Name** parameter of `New-Module` assigns a friendly name to the module.</span></span> <span data-ttu-id="cff42-136">Étant donné que `Import-Module` ne retourne pas d’objets par défaut, il n’y a aucune sortie de cette commande.</span><span class="sxs-lookup"><span data-stu-id="cff42-136">Because `Import-Module` does not return any objects by default, there is no output from this command.</span></span> <span data-ttu-id="cff42-137">`Get-Module` que le **GreetingModule** a été importé dans la session active.</span><span class="sxs-lookup"><span data-stu-id="cff42-137">`Get-Module` that the **GreetingModule** has been imported into the current session.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

<span data-ttu-id="cff42-138">L' `Get-Command` applet de commande affiche la `Hello` fonction exportée par le module dynamique.</span><span class="sxs-lookup"><span data-stu-id="cff42-138">The `Get-Command` cmdlet shows the `Hello` function that the dynamic module exports.</span></span>

### <span data-ttu-id="cff42-139">Exemple 5 : générer un objet personnalisé qui a des fonctions exportées</span><span class="sxs-lookup"><span data-stu-id="cff42-139">Example 5: Generate a custom object that has exported functions</span></span>

<span data-ttu-id="cff42-140">Cet exemple montre comment utiliser le paramètre **AsCustomObject** de `New-Module` pour générer un objet personnalisé qui a des méthodes de script qui représentent les fonctions exportées.</span><span class="sxs-lookup"><span data-stu-id="cff42-140">This example shows how to use the **AsCustomObject** parameter of `New-Module` to generate a custom object that has script methods that represent the exported functions.</span></span>

<span data-ttu-id="cff42-141">L' `New-Module` applet de commande crée un module dynamique avec deux fonctions, `Hello` et `Goodbye` .</span><span class="sxs-lookup"><span data-stu-id="cff42-141">The `New-Module` cmdlet creates a dynamic module with two functions, `Hello` and `Goodbye`.</span></span> <span data-ttu-id="cff42-142">Le paramètre **AsCustomObject** crée un objet personnalisé à la place de l’objet **PSModuleInfo** `New-Module` généré par défaut par.</span><span class="sxs-lookup"><span data-stu-id="cff42-142">The **AsCustomObject** parameter creates a custom object instead of the **PSModuleInfo** object that `New-Module` generates by default.</span></span> <span data-ttu-id="cff42-143">Cet objet personnalisé est enregistré dans la `$m` variable.</span><span class="sxs-lookup"><span data-stu-id="cff42-143">This custom object is saved in the `$m` variable.</span></span>
<span data-ttu-id="cff42-144">La `$m` variable semble n’avoir aucune valeur assignée.</span><span class="sxs-lookup"><span data-stu-id="cff42-144">The `$m` variable appears to have no assigned value.</span></span>

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

<span data-ttu-id="cff42-145">Le canalisation `$m` vers l’applet de commande `Get-Member` affiche les propriétés et les méthodes de l’objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="cff42-145">Piping `$m` to the `Get-Member` cmdlet displays the properties and methods of the custom object.</span></span> <span data-ttu-id="cff42-146">La sortie indique que l’objet possède des méthodes de script qui représentent les `Hello` `Goodbye` fonctions et.</span><span class="sxs-lookup"><span data-stu-id="cff42-146">The output shows that the object has script methods that represent the `Hello` and `Goodbye` functions.</span></span>
<span data-ttu-id="cff42-147">Enfin, nous appelons ces méthodes de script et affichons les résultats.</span><span class="sxs-lookup"><span data-stu-id="cff42-147">Finally, we call these script methods and display the results.</span></span>

### <span data-ttu-id="cff42-148">Exemple 6 : obtenir les résultats du bloc de script</span><span class="sxs-lookup"><span data-stu-id="cff42-148">Example 6: Get the results of the script block</span></span>

<span data-ttu-id="cff42-149">Cet exemple utilise le paramètre **ReturnResult** pour demander les résultats de l’exécution du bloc de script au lieu de demander un objet de module.</span><span class="sxs-lookup"><span data-stu-id="cff42-149">This example uses the **ReturnResult** parameter to request the results of running the script block instead of requesting a module object.</span></span> <span data-ttu-id="cff42-150">Le bloc de script dans le nouveau module définit la `SayHello` fonction, puis appelle la fonction.</span><span class="sxs-lookup"><span data-stu-id="cff42-150">The script block in the new module defines the `SayHello` function and then calls the function.</span></span>

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## <span data-ttu-id="cff42-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cff42-151">PARAMETERS</span></span>

### <span data-ttu-id="cff42-152">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="cff42-152">-ArgumentList</span></span>

<span data-ttu-id="cff42-153">Spécifie un tableau d’arguments qui sont des valeurs de paramètre passées au bloc de script.</span><span class="sxs-lookup"><span data-stu-id="cff42-153">Specifies an array of arguments which are parameter values that are passed to the script block.</span></span> <span data-ttu-id="cff42-154">Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="cff42-154">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cff42-155">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="cff42-155">-AsCustomObject</span></span>

<span data-ttu-id="cff42-156">Indique que cette applet de commande retourne un objet personnalisé qui représente le module dynamique.</span><span class="sxs-lookup"><span data-stu-id="cff42-156">Indicates that this cmdlet returns a custom object that represents the dynamic module.</span></span> <span data-ttu-id="cff42-157">Les membres de module sont implémentés en tant que méthodes de script de l'objet personnalisé, mais ils ne sont pas importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="cff42-157">The module members are implemented as script methods of the custom object, but they are not imported into the session.</span></span> <span data-ttu-id="cff42-158">Vous pouvez enregistrer l'objet personnalisé dans une variable et utiliser la notation par points pour appeler les membres.</span><span class="sxs-lookup"><span data-stu-id="cff42-158">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

<span data-ttu-id="cff42-159">Si le module possède plusieurs membres portant le même nom, tels qu’une fonction et une variable qui sont tous deux nommés A, un seul membre avec chaque nom est accessible à partir de l’objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="cff42-159">If the module has multiple members with the same name, such as a function and a variable that are both named A, only one member with each name can be accessed from the custom object.</span></span>

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

### <span data-ttu-id="cff42-160">-Applet de commande</span><span class="sxs-lookup"><span data-stu-id="cff42-160">-Cmdlet</span></span>

<span data-ttu-id="cff42-161">Spécifie un tableau d’applets de commande que cette applet de commande exporte à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="cff42-161">Specifies an array of cmdlets that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="cff42-162">Entrez la liste des applets de commandes, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="cff42-162">Enter a comma-separated list of cmdlets.</span></span> <span data-ttu-id="cff42-163">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="cff42-163">Wildcard characters are permitted.</span></span> <span data-ttu-id="cff42-164">Par défaut, toutes les applets de commande du module sont exportées.</span><span class="sxs-lookup"><span data-stu-id="cff42-164">By default, all cmdlets in the module are exported.</span></span>

<span data-ttu-id="cff42-165">Vous ne pouvez pas définir des applets de commande dans un bloc de script, mais un module dynamique peut inclure des applets de commande s'il importe les applets de commande à partir d'un module binaire.</span><span class="sxs-lookup"><span data-stu-id="cff42-165">You cannot define cmdlets in a script block, but a dynamic module can include cmdlets if it imports the cmdlets from a binary module.</span></span>

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

### <span data-ttu-id="cff42-166">-Fonction</span><span class="sxs-lookup"><span data-stu-id="cff42-166">-Function</span></span>

<span data-ttu-id="cff42-167">Spécifie un tableau de fonctions que cette applet de commande exporte à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="cff42-167">Specifies an array of functions that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="cff42-168">Entrez la liste des fonctions, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="cff42-168">Enter a comma-separated list of functions.</span></span> <span data-ttu-id="cff42-169">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="cff42-169">Wildcard characters are permitted.</span></span> <span data-ttu-id="cff42-170">Par défaut, toutes les fonctions définies dans un module sont exportées.</span><span class="sxs-lookup"><span data-stu-id="cff42-170">By default, all functions defined in a module are exported.</span></span>

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

### <span data-ttu-id="cff42-171">-Name</span><span class="sxs-lookup"><span data-stu-id="cff42-171">-Name</span></span>

<span data-ttu-id="cff42-172">Spécifie un nom pour le nouveau module.</span><span class="sxs-lookup"><span data-stu-id="cff42-172">Specifies a name for the new module.</span></span> <span data-ttu-id="cff42-173">Vous pouvez également diriger un nom de module vers New-Module.</span><span class="sxs-lookup"><span data-stu-id="cff42-173">You can also pipe a module name to New-Module.</span></span>

<span data-ttu-id="cff42-174">La valeur par défaut est un nom généré automatiquement qui commence par `__DynamicModule_` et est suivi d’un GUID qui spécifie le chemin d’accès du module dynamique.</span><span class="sxs-lookup"><span data-stu-id="cff42-174">The default value is an autogenerated name that starts with `__DynamicModule_` and is followed by a GUID that specifies the path of the dynamic module.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cff42-175">-ReturnResult</span><span class="sxs-lookup"><span data-stu-id="cff42-175">-ReturnResult</span></span>

<span data-ttu-id="cff42-176">Indique que cette applet de commande exécute le bloc de script et retourne les résultats du bloc de script au lieu de retourner un objet de module.</span><span class="sxs-lookup"><span data-stu-id="cff42-176">Indicates that this cmdlet runs the script block and returns the script block results instead of returning a module object.</span></span>

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

### <span data-ttu-id="cff42-177">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="cff42-177">-ScriptBlock</span></span>

<span data-ttu-id="cff42-178">Spécifie le contenu du module dynamique.</span><span class="sxs-lookup"><span data-stu-id="cff42-178">Specifies the contents of the dynamic module.</span></span> <span data-ttu-id="cff42-179">Placez le contenu entre accolades ( `{}` ) pour créer un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="cff42-179">Enclose the contents in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="cff42-180">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cff42-180">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cff42-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cff42-181">CommonParameters</span></span>

<span data-ttu-id="cff42-182">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cff42-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cff42-183">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cff42-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cff42-184">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="cff42-184">INPUTS</span></span>

### <span data-ttu-id="cff42-185">System.String</span><span class="sxs-lookup"><span data-stu-id="cff42-185">System.String</span></span>

<span data-ttu-id="cff42-186">Vous pouvez diriger un nom de module vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cff42-186">You can pipe a module name to this cmdlet.</span></span>

## <span data-ttu-id="cff42-187">SORTIES</span><span class="sxs-lookup"><span data-stu-id="cff42-187">OUTPUTS</span></span>

### <span data-ttu-id="cff42-188">System. Management. Automation. PSModuleInfo, System. Management. Automation. PSCustomObject ou aucun</span><span class="sxs-lookup"><span data-stu-id="cff42-188">System.Management.Automation.PSModuleInfo, System.Management.Automation.PSCustomObject, or None</span></span>

<span data-ttu-id="cff42-189">Par défaut, cette applet de commande génère un objet **PSModuleInfo** .</span><span class="sxs-lookup"><span data-stu-id="cff42-189">This cmdlet generates a **PSModuleInfo** object, by default.</span></span> <span data-ttu-id="cff42-190">Si vous utilisez le paramètre **AsCustomObject** , il génère un objet **PSCustomObject** .</span><span class="sxs-lookup"><span data-stu-id="cff42-190">If you use the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span> <span data-ttu-id="cff42-191">Si vous utilisez le paramètre **ReturnResult** , il retourne le résultat de l’évaluation du bloc de script dans le module dynamique.</span><span class="sxs-lookup"><span data-stu-id="cff42-191">If you use the **ReturnResult** parameter, it returns the result of evaluating the script block in the dynamic module.</span></span>

## <span data-ttu-id="cff42-192">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="cff42-192">NOTES</span></span>

<span data-ttu-id="cff42-193">Vous pouvez également faire référence à `New-Module` par son alias, `nmo` .</span><span class="sxs-lookup"><span data-stu-id="cff42-193">You can also refer to `New-Module` by its alias, `nmo`.</span></span> <span data-ttu-id="cff42-194">Pour plus d’informations, consultez [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="cff42-194">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="cff42-195">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="cff42-195">RELATED LINKS</span></span>

[<span data-ttu-id="cff42-196">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="cff42-196">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="cff42-197">Get-Module</span><span class="sxs-lookup"><span data-stu-id="cff42-197">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="cff42-198">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="cff42-198">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="cff42-199">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="cff42-199">Remove-Module</span></span>](Remove-Module.md)
