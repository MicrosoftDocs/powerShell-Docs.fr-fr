---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: 487fd85bdcc918b7fb360f9c9d23388a06b35f86
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603679"
---
# <span data-ttu-id="4cb3e-102">New-Module</span><span class="sxs-lookup"><span data-stu-id="4cb3e-102">New-Module</span></span>

## <span data-ttu-id="4cb3e-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4cb3e-103">SYNOPSIS</span></span>
<span data-ttu-id="4cb3e-104">Crée un module dynamique qui existe uniquement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-104">Creates a new dynamic module that exists only in memory.</span></span>

## <span data-ttu-id="4cb3e-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="4cb3e-105">SYNTAX</span></span>

### <span data-ttu-id="4cb3e-106">ScriptBlock (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="4cb3e-106">ScriptBlock (Default)</span></span>

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="4cb3e-107">Nom</span><span class="sxs-lookup"><span data-stu-id="4cb3e-107">Name</span></span>

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="4cb3e-108">Description</span><span class="sxs-lookup"><span data-stu-id="4cb3e-108">DESCRIPTION</span></span>

<span data-ttu-id="4cb3e-109">L' `New-Module` applet de commande crée un module dynamique à partir d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-109">The `New-Module` cmdlet creates a dynamic module from a script block.</span></span> <span data-ttu-id="4cb3e-110">Les membres du module dynamique, tels des fonctions et des variables, sont immédiatement disponibles dans la session et restent disponibles jusqu'à la fermeture de la session.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-110">The members of the dynamic module, such as functions and variables, are immediately available in the session and remain available until you close the session.</span></span>

<span data-ttu-id="4cb3e-111">Comme des modules statiques, les applets de commande et les fonctions figurant dans un module dynamique sont exportées par défaut, alors que les variables et les alias ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-111">Like static modules, by default, the cmdlets and functions in a dynamic module are exported and the variables and aliases are not.</span></span> <span data-ttu-id="4cb3e-112">Toutefois, vous pouvez utiliser l’applet de commande Export-ModuleMember et les paramètres de `New-Module` pour remplacer les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-112">However, you can use the Export-ModuleMember cmdlet and the parameters of `New-Module` to override the defaults.</span></span>

<span data-ttu-id="4cb3e-113">Vous pouvez également utiliser le paramètre **AsCustomObject** de `New-Module` pour retourner le module dynamique en tant qu’objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-113">You can also use the **AsCustomObject** parameter of `New-Module` to return the dynamic module as a custom object.</span></span> <span data-ttu-id="4cb3e-114">Les membres des modules, tels que les fonctions, sont implémentés en tant que méthodes de script de l'objet personnalisé au lieu d'être importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-114">The members of the modules, such as functions, are implemented as script methods of the custom object instead of being imported into the session.</span></span>

<span data-ttu-id="4cb3e-115">Les modules dynamiques existent uniquement en mémoire, pas sur le disque.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-115">Dynamic modules exist only in memory, not on disk.</span></span> <span data-ttu-id="4cb3e-116">Comme tous les modules, les membres des modules dynamiques s'exécutent dans une étendue de module privée qui est un enfant de l'étendue globale.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-116">Like all modules, the members of dynamic modules run in a private module scope that is a child of the global scope.</span></span> <span data-ttu-id="4cb3e-117">Get-Module ne peut pas obtenir un module dynamique, mais Get-Command peut obtenir les membres exportés.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-117">Get-Module cannot get a dynamic module, but Get-Command can get the exported members.</span></span>

<span data-ttu-id="4cb3e-118">Pour mettre un module dynamique à la disposition de `Get-Module` , dirigez une `New-Module` commande vers Import-Module, ou dirigez l’objet de module qui `New-Module` retourne à `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-118">To make a dynamic module available to `Get-Module`, pipe a `New-Module` command to Import-Module, or pipe the module object that `New-Module` returns to `Import-Module`.</span></span> <span data-ttu-id="4cb3e-119">Cette action ajoute le module dynamique à la `Get-Module` liste, mais il n’enregistre pas le module sur le disque ou le rend persistant.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-119">This action adds the dynamic module to the `Get-Module` list, but it does not save the module to disk or make it persistent.</span></span>

## <span data-ttu-id="4cb3e-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4cb3e-120">EXAMPLES</span></span>

### <span data-ttu-id="4cb3e-121">Exemple 1 : créer un module dynamique</span><span class="sxs-lookup"><span data-stu-id="4cb3e-121">Example 1: Create a dynamic module</span></span>

<span data-ttu-id="4cb3e-122">Cet exemple crée un nouveau module dynamique avec une fonction appelée `Hello` .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-122">This example creates a new dynamic module with a function called `Hello`.</span></span> <span data-ttu-id="4cb3e-123">La commande retourne un objet de module qui représente le nouveau module dynamique.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-123">The command returns a module object that represents the new dynamic module.</span></span>

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

### <span data-ttu-id="4cb3e-124">Exemple 2 : utilisation des modules dynamiques et des Get-Module et des Get-Command</span><span class="sxs-lookup"><span data-stu-id="4cb3e-124">Example 2: Working with dynamic modules and Get-Module and Get-Command</span></span>

<span data-ttu-id="4cb3e-125">Cet exemple montre que les modules dynamiques ne sont pas retournés par l’applet de commande `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-125">This example demonstrates that dynamic modules are not returned by the `Get-Module` cmdlet.</span></span> <span data-ttu-id="4cb3e-126">Les membres qu’ils exportent sont retournés par l’applet de commande `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-126">The members that they export are returned by the `Get-Command` cmdlet.</span></span>

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

### <span data-ttu-id="4cb3e-127">Exemple 3 : exporter une variable dans la session active</span><span class="sxs-lookup"><span data-stu-id="4cb3e-127">Example 3: Export a variable into the current session</span></span>

<span data-ttu-id="4cb3e-128">Cet exemple utilise l' `Export-ModuleMember` applet de commande pour exporter une variable dans la session active.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-128">This example uses the `Export-ModuleMember` cmdlet to export a variable into the current session.</span></span>
<span data-ttu-id="4cb3e-129">Sans la `Export-ModuleMember` commande, seule la fonction est exportée.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-129">Without the `Export-ModuleMember` command, only the function is exported.</span></span>

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

<span data-ttu-id="4cb3e-130">La sortie indique que la variable et la fonction ont été exportées dans la session.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-130">The output shows that both the variable and the function were exported into the session.</span></span>

### <span data-ttu-id="4cb3e-131">Exemple 4 : mettre un module dynamique à la disposition d' Get-Module</span><span class="sxs-lookup"><span data-stu-id="4cb3e-131">Example 4: Make a dynamic module available to Get-Module</span></span>

<span data-ttu-id="4cb3e-132">Cet exemple montre que vous pouvez mettre un module dynamique à la disposition de `Get-Module` en canalisant le module dynamique vers `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-132">This example demonstrates that you can make a dynamic module available to `Get-Module` by piping the dynamic module to `Import-Module`.</span></span>

<span data-ttu-id="4cb3e-133">`New-Module` crée un objet de module qui est dirigé vers l’applet de commande `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-133">`New-Module` creates a module object that is piped to the `Import-Module` cmdlet.</span></span> <span data-ttu-id="4cb3e-134">Le paramètre **Name** de `New-Module` affecte un nom convivial au module.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-134">The **Name** parameter of `New-Module` assigns a friendly name to the module.</span></span> <span data-ttu-id="4cb3e-135">Étant donné que `Import-Module` ne retourne pas d’objets par défaut, il n’y a aucune sortie de cette commande.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-135">Because `Import-Module` does not return any objects by default, there is no output from this command.</span></span> <span data-ttu-id="4cb3e-136">`Get-Module` que le **GreetingModule** a été importé dans la session active.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-136">`Get-Module` that the **GreetingModule** has been imported into the current session.</span></span>

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

<span data-ttu-id="4cb3e-137">L' `Get-Command` applet de commande affiche la `Hello` fonction exportée par le module dynamique.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-137">The `Get-Command` cmdlet shows the `Hello` function that the dynamic module exports.</span></span>

### <span data-ttu-id="4cb3e-138">Exemple 5 : générer un objet personnalisé qui a des fonctions exportées</span><span class="sxs-lookup"><span data-stu-id="4cb3e-138">Example 5: Generate a custom object that has exported functions</span></span>

<span data-ttu-id="4cb3e-139">Cet exemple montre comment utiliser le paramètre **AsCustomObject** de `New-Module` pour générer un objet personnalisé qui a des méthodes de script qui représentent les fonctions exportées.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-139">This example shows how to use the **AsCustomObject** parameter of `New-Module` to generate a custom object that has script methods that represent the exported functions.</span></span>

<span data-ttu-id="4cb3e-140">L' `New-Module` applet de commande crée un module dynamique avec deux fonctions, `Hello` et `Goodbye` .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-140">The `New-Module` cmdlet creates a dynamic module with two functions, `Hello` and `Goodbye`.</span></span> <span data-ttu-id="4cb3e-141">Le paramètre **AsCustomObject** crée un objet personnalisé à la place de l’objet **PSModuleInfo** `New-Module` généré par défaut par.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-141">The **AsCustomObject** parameter creates a custom object instead of the **PSModuleInfo** object that `New-Module` generates by default.</span></span> <span data-ttu-id="4cb3e-142">Cet objet personnalisé est enregistré dans la `$m` variable.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-142">This custom object is saved in the `$m` variable.</span></span>
<span data-ttu-id="4cb3e-143">La `$m` variable semble n’avoir aucune valeur assignée.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-143">The `$m` variable appears to have no assigned value.</span></span>

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

<span data-ttu-id="4cb3e-144">Le canalisation `$m` vers l’applet de commande `Get-Member` affiche les propriétés et les méthodes de l’objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-144">Piping `$m` to the `Get-Member` cmdlet displays the properties and methods of the custom object.</span></span> <span data-ttu-id="4cb3e-145">La sortie indique que l’objet possède des méthodes de script qui représentent les `Hello` `Goodbye` fonctions et.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-145">The output shows that the object has script methods that represent the `Hello` and `Goodbye` functions.</span></span>
<span data-ttu-id="4cb3e-146">Enfin, nous appelons ces méthodes de script et affichons les résultats.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-146">Finally, we call these script methods and display the results.</span></span>

### <span data-ttu-id="4cb3e-147">Exemple 6 : obtenir les résultats du bloc de script</span><span class="sxs-lookup"><span data-stu-id="4cb3e-147">Example 6: Get the results of the script block</span></span>

<span data-ttu-id="4cb3e-148">Cet exemple utilise le paramètre **ReturnResult** pour demander les résultats de l’exécution du bloc de script au lieu de demander un objet de module.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-148">This example uses the **ReturnResult** parameter to request the results of running the script block instead of requesting a module object.</span></span> <span data-ttu-id="4cb3e-149">Le bloc de script dans le nouveau module définit la `SayHello` fonction, puis appelle la fonction.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-149">The script block in the new module defines the `SayHello` function and then calls the function.</span></span>

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## <span data-ttu-id="4cb3e-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4cb3e-150">PARAMETERS</span></span>

### <span data-ttu-id="4cb3e-151">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="4cb3e-151">-ArgumentList</span></span>

<span data-ttu-id="4cb3e-152">Spécifie un tableau d’arguments qui sont des valeurs de paramètre passées au bloc de script.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-152">Specifies an array of arguments which are parameter values that are passed to the script block.</span></span> <span data-ttu-id="4cb3e-153">Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="4cb3e-153">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="4cb3e-154">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="4cb3e-154">-AsCustomObject</span></span>

<span data-ttu-id="4cb3e-155">Indique que cette applet de commande retourne un objet personnalisé qui représente le module dynamique.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-155">Indicates that this cmdlet returns a custom object that represents the dynamic module.</span></span> <span data-ttu-id="4cb3e-156">Les membres de module sont implémentés en tant que méthodes de script de l'objet personnalisé, mais ils ne sont pas importés dans la session.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-156">The module members are implemented as script methods of the custom object, but they are not imported into the session.</span></span> <span data-ttu-id="4cb3e-157">Vous pouvez enregistrer l'objet personnalisé dans une variable et utiliser la notation par points pour appeler les membres.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-157">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

<span data-ttu-id="4cb3e-158">Si le module possède plusieurs membres portant le même nom, tels qu’une fonction et une variable qui sont tous deux nommés A, un seul membre avec chaque nom est accessible à partir de l’objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-158">If the module has multiple members with the same name, such as a function and a variable that are both named A, only one member with each name can be accessed from the custom object.</span></span>

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

### <span data-ttu-id="4cb3e-159">-Applet de commande</span><span class="sxs-lookup"><span data-stu-id="4cb3e-159">-Cmdlet</span></span>

<span data-ttu-id="4cb3e-160">Spécifie un tableau d’applets de commande que cette applet de commande exporte à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-160">Specifies an array of cmdlets that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="4cb3e-161">Entrez la liste des applets de commandes, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-161">Enter a comma-separated list of cmdlets.</span></span> <span data-ttu-id="4cb3e-162">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-162">Wildcard characters are permitted.</span></span> <span data-ttu-id="4cb3e-163">Par défaut, toutes les applets de commande du module sont exportées.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-163">By default, all cmdlets in the module are exported.</span></span>

<span data-ttu-id="4cb3e-164">Vous ne pouvez pas définir des applets de commande dans un bloc de script, mais un module dynamique peut inclure des applets de commande s'il importe les applets de commande à partir d'un module binaire.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-164">You cannot define cmdlets in a script block, but a dynamic module can include cmdlets if it imports the cmdlets from a binary module.</span></span>

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

### <span data-ttu-id="4cb3e-165">-Fonction</span><span class="sxs-lookup"><span data-stu-id="4cb3e-165">-Function</span></span>

<span data-ttu-id="4cb3e-166">Spécifie un tableau de fonctions que cette applet de commande exporte à partir du module dans la session active.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-166">Specifies an array of functions that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="4cb3e-167">Entrez la liste des fonctions, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-167">Enter a comma-separated list of functions.</span></span> <span data-ttu-id="4cb3e-168">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-168">Wildcard characters are permitted.</span></span> <span data-ttu-id="4cb3e-169">Par défaut, toutes les fonctions définies dans un module sont exportées.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-169">By default, all functions defined in a module are exported.</span></span>

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

### <span data-ttu-id="4cb3e-170">-Name</span><span class="sxs-lookup"><span data-stu-id="4cb3e-170">-Name</span></span>

<span data-ttu-id="4cb3e-171">Spécifie un nom pour le nouveau module.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-171">Specifies a name for the new module.</span></span> <span data-ttu-id="4cb3e-172">Vous pouvez également diriger un nom de module vers New-Module.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-172">You can also pipe a module name to New-Module.</span></span>

<span data-ttu-id="4cb3e-173">La valeur par défaut est un nom généré automatiquement qui commence par `__DynamicModule_` et est suivi d’un GUID qui spécifie le chemin d’accès du module dynamique.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-173">The default value is an autogenerated name that starts with `__DynamicModule_` and is followed by a GUID that specifies the path of the dynamic module.</span></span>

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

### <span data-ttu-id="4cb3e-174">-ReturnResult</span><span class="sxs-lookup"><span data-stu-id="4cb3e-174">-ReturnResult</span></span>

<span data-ttu-id="4cb3e-175">Indique que cette applet de commande exécute le bloc de script et retourne les résultats du bloc de script au lieu de retourner un objet de module.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-175">Indicates that this cmdlet runs the script block and returns the script block results instead of returning a module object.</span></span>

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

### <span data-ttu-id="4cb3e-176">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="4cb3e-176">-ScriptBlock</span></span>

<span data-ttu-id="4cb3e-177">Spécifie le contenu du module dynamique.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-177">Specifies the contents of the dynamic module.</span></span> <span data-ttu-id="4cb3e-178">Placez le contenu entre accolades ( `{}` ) pour créer un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-178">Enclose the contents in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="4cb3e-179">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-179">This parameter is required.</span></span>

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

### <span data-ttu-id="4cb3e-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4cb3e-180">CommonParameters</span></span>

<span data-ttu-id="4cb3e-181">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4cb3e-182">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4cb3e-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4cb3e-183">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4cb3e-183">INPUTS</span></span>

### <span data-ttu-id="4cb3e-184">System.String</span><span class="sxs-lookup"><span data-stu-id="4cb3e-184">System.String</span></span>

<span data-ttu-id="4cb3e-185">Vous pouvez diriger un nom de module vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-185">You can pipe a module name to this cmdlet.</span></span>

## <span data-ttu-id="4cb3e-186">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4cb3e-186">OUTPUTS</span></span>

### <span data-ttu-id="4cb3e-187">System. Management. Automation. PSModuleInfo, System. Management. Automation. PSCustomObject ou aucun</span><span class="sxs-lookup"><span data-stu-id="4cb3e-187">System.Management.Automation.PSModuleInfo, System.Management.Automation.PSCustomObject, or None</span></span>

<span data-ttu-id="4cb3e-188">Par défaut, cette applet de commande génère un objet **PSModuleInfo** .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-188">This cmdlet generates a **PSModuleInfo** object, by default.</span></span> <span data-ttu-id="4cb3e-189">Si vous utilisez le paramètre **AsCustomObject** , il génère un objet **PSCustomObject** .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-189">If you use the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span> <span data-ttu-id="4cb3e-190">Si vous utilisez le paramètre **ReturnResult** , il retourne le résultat de l’évaluation du bloc de script dans le module dynamique.</span><span class="sxs-lookup"><span data-stu-id="4cb3e-190">If you use the **ReturnResult** parameter, it returns the result of evaluating the script block in the dynamic module.</span></span>

## <span data-ttu-id="4cb3e-191">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4cb3e-191">NOTES</span></span>

<span data-ttu-id="4cb3e-192">Vous pouvez également faire référence à `New-Module` par son alias, `nmo` .</span><span class="sxs-lookup"><span data-stu-id="4cb3e-192">You can also refer to `New-Module` by its alias, `nmo`.</span></span> <span data-ttu-id="4cb3e-193">Pour plus d’informations, consultez [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="4cb3e-193">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="4cb3e-194">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4cb3e-194">RELATED LINKS</span></span>

[<span data-ttu-id="4cb3e-195">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="4cb3e-195">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="4cb3e-196">Get-Module</span><span class="sxs-lookup"><span data-stu-id="4cb3e-196">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="4cb3e-197">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="4cb3e-197">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="4cb3e-198">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="4cb3e-198">Remove-Module</span></span>](Remove-Module.md)

