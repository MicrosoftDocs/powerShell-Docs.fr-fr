---
description: Décrit comment créer et utiliser une variable de type référence. Vous pouvez utiliser des variables de type référence pour permettre à une fonction de modifier la valeur d’une variable qui lui est transmise.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: 3d1ae1fd53e7b4e845c8df76e1826c45b32c9c72
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207589"
---
# <a name="about-ref"></a><span data-ttu-id="709a4-105">À propos de Ref</span><span class="sxs-lookup"><span data-stu-id="709a4-105">About Ref</span></span>

## <a name="short-description"></a><span data-ttu-id="709a4-106">Description courte</span><span class="sxs-lookup"><span data-stu-id="709a4-106">Short description</span></span>

<span data-ttu-id="709a4-107">Décrit comment créer et utiliser une variable de type référence.</span><span class="sxs-lookup"><span data-stu-id="709a4-107">Describes how to create and use a reference type variable.</span></span> <span data-ttu-id="709a4-108">Vous pouvez utiliser des variables de type référence pour permettre à une fonction de modifier la valeur d’une variable qui lui est transmise.</span><span class="sxs-lookup"><span data-stu-id="709a4-108">You can use reference type variables to permit a function to change the value of a variable that is passed to it.</span></span>

## <a name="long-description"></a><span data-ttu-id="709a4-109">Description longue</span><span class="sxs-lookup"><span data-stu-id="709a4-109">Long description</span></span>

<span data-ttu-id="709a4-110">Vous pouvez passer des variables aux fonctions *par référence* ou *par valeur* .</span><span class="sxs-lookup"><span data-stu-id="709a4-110">You can pass variables to functions *by reference* or *by value* .</span></span>

<span data-ttu-id="709a4-111">Lorsque vous passez une variable *par valeur* , vous passez une copie des données.</span><span class="sxs-lookup"><span data-stu-id="709a4-111">When you pass a variable *by value* , you are passing a copy of the data.</span></span>

<span data-ttu-id="709a4-112">Dans l’exemple suivant, la fonction modifie la valeur de la variable qui lui est transmise.</span><span class="sxs-lookup"><span data-stu-id="709a4-112">In the following example, the function changes the value of the variable passed to it.</span></span> <span data-ttu-id="709a4-113">Dans PowerShell, les entiers sont des types valeur afin qu’ils soient passés par valeur.</span><span class="sxs-lookup"><span data-stu-id="709a4-113">In PowerShell, integers are value types so they are passed by value.</span></span>
<span data-ttu-id="709a4-114">Par conséquent, la valeur de `$var` est inchangée en dehors de la portée de la fonction.</span><span class="sxs-lookup"><span data-stu-id="709a4-114">Therefore, the value of `$var` is unchanged outside the scope of the function.</span></span>

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

<span data-ttu-id="709a4-115">Dans l’exemple suivant, une variable contenant un `Hashtable` est passée à une fonction.</span><span class="sxs-lookup"><span data-stu-id="709a4-115">In the following example, a variable containing a `Hashtable` is passed to a function.</span></span> <span data-ttu-id="709a4-116">`Hashtable` est un type d’objet, par défaut, il est passé à la fonction *par référence* .</span><span class="sxs-lookup"><span data-stu-id="709a4-116">`Hashtable` is an object type so by default it is passed to the function *by reference* .</span></span>

<span data-ttu-id="709a4-117">Lors du passage d’une variable *par référence* , la fonction peut modifier les données et cette modification persiste après l’exécution de la fonction.</span><span class="sxs-lookup"><span data-stu-id="709a4-117">When passing a variable *by reference* , the function can change the data and that change persists after the function executes.</span></span>

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

<span data-ttu-id="709a4-118">La fonction ajoute une nouvelle paire clé-valeur qui persiste en dehors de la portée de la fonction.</span><span class="sxs-lookup"><span data-stu-id="709a4-118">The function adds a new key-value pair that persists outside of the function's scope.</span></span>

### <a name="writing-functions-to-accept-reference-parameters"></a><span data-ttu-id="709a4-119">Écriture de fonctions pour accepter des paramètres de référence</span><span class="sxs-lookup"><span data-stu-id="709a4-119">Writing functions to accept reference parameters</span></span>

<span data-ttu-id="709a4-120">Vous pouvez coder vos fonctions pour prendre un paramètre en tant que référence, quel que soit le type de données passé.</span><span class="sxs-lookup"><span data-stu-id="709a4-120">You can code your functions to take a parameter as a reference, regardless of the type of data passed.</span></span> <span data-ttu-id="709a4-121">Pour cela, vous devez spécifier le type de paramètres en tant que `System.Management.Automation.PSReference` , ou `[ref]` .</span><span class="sxs-lookup"><span data-stu-id="709a4-121">This requires that you specify the parameters type as `System.Management.Automation.PSReference`, or `[ref]`.</span></span>

<span data-ttu-id="709a4-122">Lorsque vous utilisez des références, vous devez utiliser la `Value` propriété du `System.Management.Automation.PSReference` type pour accéder à vos données.</span><span class="sxs-lookup"><span data-stu-id="709a4-122">When using references, you must use the `Value` property of the `System.Management.Automation.PSReference` type to access your data.</span></span>

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

<span data-ttu-id="709a4-123">Pour passer une variable à un paramètre qui attend une référence, vous devez taper cast de la variable en tant que référence.</span><span class="sxs-lookup"><span data-stu-id="709a4-123">To pass a variable to a parameter that expects a reference, you must type cast your variable as a reference.</span></span>

> [!NOTE]
> <span data-ttu-id="709a4-124">Les crochets et les parenthèses sont tous deux requis.</span><span class="sxs-lookup"><span data-stu-id="709a4-124">The brackets and parenthesis are BOTH required.</span></span>

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a><span data-ttu-id="709a4-125">Passage de références à des méthodes .NET</span><span class="sxs-lookup"><span data-stu-id="709a4-125">Passing references to .NET methods</span></span>

<span data-ttu-id="709a4-126">Certaines méthodes .NET peuvent vous obliger à passer une variable en tant que référence.</span><span class="sxs-lookup"><span data-stu-id="709a4-126">Some .NET methods may require you to pass a variable as a reference.</span></span> <span data-ttu-id="709a4-127">Lorsque la définition de la méthode utilise les mots clés `in` , `out` ou `ref` sur un paramètre, elle attend une référence.</span><span class="sxs-lookup"><span data-stu-id="709a4-127">When the method's definition uses the keywords `in`, `out`, or `ref` on a parameter, it expects a reference.</span></span>

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

<span data-ttu-id="709a4-128">La `TryParse` méthode tente d’analyser une chaîne comme un entier.</span><span class="sxs-lookup"><span data-stu-id="709a4-128">The `TryParse` method attempts to parse a string as an integer.</span></span> <span data-ttu-id="709a4-129">Si la méthode réussit, elle retourne `$true` et le résultat est stocké dans la variable que vous avez passée **par référence** .</span><span class="sxs-lookup"><span data-stu-id="709a4-129">If the method succeeds, it returns `$true`, and the result is stored in the variable you passed **by reference** .</span></span>

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a><span data-ttu-id="709a4-130">Références et étendues</span><span class="sxs-lookup"><span data-stu-id="709a4-130">References and scopes</span></span>

<span data-ttu-id="709a4-131">Les références permettent de modifier la valeur d’une variable dans l’étendue parente dans une étendue enfant.</span><span class="sxs-lookup"><span data-stu-id="709a4-131">References allow the value of a variable in the parent scope to be changed within a child scope.</span></span>

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

<span data-ttu-id="709a4-132">Seule la variable du type de référence a été modifiée.</span><span class="sxs-lookup"><span data-stu-id="709a4-132">Only the reference type's variable was changed.</span></span>

## <a name="see-also"></a><span data-ttu-id="709a4-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="709a4-133">See also</span></span>

[<span data-ttu-id="709a4-134">about_Variables</span><span class="sxs-lookup"><span data-stu-id="709a4-134">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="709a4-135">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="709a4-135">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="709a4-136">about_Functions</span><span class="sxs-lookup"><span data-stu-id="709a4-136">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="709a4-137">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="709a4-137">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="709a4-138">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="709a4-138">about_Scopes</span></span>](about_scopes.md)
