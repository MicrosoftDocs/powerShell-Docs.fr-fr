---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: d28ff57c864847658072c9b7a1979b2b513c04b3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204870"
---
# <span data-ttu-id="1a3b7-103">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="1a3b7-103">Set-StrictMode</span></span>

## <span data-ttu-id="1a3b7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1a3b7-104">SYNOPSIS</span></span>
<span data-ttu-id="1a3b7-105">Établit et applique des règles de codage dans les expressions, les scripts et les blocs de script.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-105">Establishes and enforces coding rules in expressions, scripts, and script blocks.</span></span>

## <span data-ttu-id="1a3b7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1a3b7-106">SYNTAX</span></span>

### <span data-ttu-id="1a3b7-107">Version (par défaut)</span><span class="sxs-lookup"><span data-stu-id="1a3b7-107">Version (Default)</span></span>

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### <span data-ttu-id="1a3b7-108">Désactivé</span><span class="sxs-lookup"><span data-stu-id="1a3b7-108">Off</span></span>

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## <span data-ttu-id="1a3b7-109">Description</span><span class="sxs-lookup"><span data-stu-id="1a3b7-109">DESCRIPTION</span></span>

<span data-ttu-id="1a3b7-110">L' `Set-StrictMode` applet de commande configure le mode strict pour l’étendue actuelle et toutes les étendues enfants, puis l’active et la désactive.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-110">The `Set-StrictMode` cmdlet configures strict mode for the current scope and all child scopes, and turns it on and off.</span></span> <span data-ttu-id="1a3b7-111">Lorsque le mode strict est activé, PowerShell génère une erreur de fin lorsque le contenu d’une expression, d’un script ou d’un bloc de script enfreint les règles de codage de base recommandées.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-111">When strict mode is on, PowerShell generates a terminating error when the content of an expression, script, or script block violates basic best-practice coding rules.</span></span>

<span data-ttu-id="1a3b7-112">Utilisez le paramètre **version** pour déterminer les règles de codage appliquées.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-112">Use the **Version** parameter to determine which coding rules are enforced.</span></span>

<span data-ttu-id="1a3b7-113">`Set-PSDebug -Strict` active le mode strict pour l’étendue globale.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-113">`Set-PSDebug -Strict` cmdlet turns on strict mode for the global scope.</span></span> <span data-ttu-id="1a3b7-114">`Set-StrictMode` affecte uniquement l’étendue actuelle et ses portées enfants.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-114">`Set-StrictMode` affects only the current scope and its child scopes.</span></span> <span data-ttu-id="1a3b7-115">Par conséquent, vous pouvez l’utiliser dans un script ou une fonction pour remplacer le paramètre hérité de la portée globale.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-115">Therefore, you can use it in a script or function to override the setting inherited from the global scope.</span></span>

<span data-ttu-id="1a3b7-116">Lorsque `Set-StrictMode` est désactivé, PowerShell présente les comportements suivants :</span><span class="sxs-lookup"><span data-stu-id="1a3b7-116">When `Set-StrictMode` is off, PowerShell has the following behaviors:</span></span>

- <span data-ttu-id="1a3b7-117">Les variables non initialisées sont supposées avoir la valeur 0 (zéro) ou `$Null` , selon le type</span><span class="sxs-lookup"><span data-stu-id="1a3b7-117">Uninitialized variables are assumed to have a value of 0 (zero) or `$Null`, depending on type</span></span>
- <span data-ttu-id="1a3b7-118">Les références aux propriétés inexistantes retournent `$Null`</span><span class="sxs-lookup"><span data-stu-id="1a3b7-118">References to non-existent properties return `$Null`</span></span>
- <span data-ttu-id="1a3b7-119">Les résultats d’une syntaxe de fonction incorrecte varient selon les conditions d’erreur</span><span class="sxs-lookup"><span data-stu-id="1a3b7-119">Results of improper function syntax vary with the error conditions</span></span>
- <span data-ttu-id="1a3b7-120">La tentative de récupération d’une valeur à l’aide d’un index non valide dans un tableau retourne `$Null`</span><span class="sxs-lookup"><span data-stu-id="1a3b7-120">Attempting to retrieve a value using an invalid index in an array returns `$Null`</span></span>

## <span data-ttu-id="1a3b7-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1a3b7-121">EXAMPLES</span></span>

### <span data-ttu-id="1a3b7-122">Exemple 1 : activer le mode strict en tant que version 1,0</span><span class="sxs-lookup"><span data-stu-id="1a3b7-122">Example 1: Turn on strict mode as version 1.0</span></span>

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
The variable $a cannot be retrieved because it has not been set yet.

At line:1 char:3
+ $a <<<<  -gt 5
+ CategoryInfo          : InvalidOperation: (a:Token) [], RuntimeException
+ FullyQualifiedErrorId : VariableIsUndefined
```

<span data-ttu-id="1a3b7-123">Si le mode strict est défini sur la version 1,0, les tentatives de référencement des variables qui ne sont pas initialisées échouent.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-123">With strict mode set to version 1.0, attempts to reference variables that are not initialized fail.</span></span>

### <span data-ttu-id="1a3b7-124">Exemple 2 : activer le mode strict en tant que version 2,0</span><span class="sxs-lookup"><span data-stu-id="1a3b7-124">Example 2: Turn on strict mode as version 2.0</span></span>

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
The function or command was called like a method. Parameters should be separated by spaces,
as described in 'Get-Help about_Parameter.'
At line:1 char:4
+ add <<<< (3,4)
+ CategoryInfo          : InvalidOperation: (:) [], RuntimeException
+ FullyQualifiedErrorId : StrictModeFunctionCallWithParens
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$string.Month -eq $null
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$string.Month -eq $null
```

```Output
Property 'Month' cannot be found on this object; make sure it exists.
At line:1 char:9
+ $string. <<<< month
+ CategoryInfo          : InvalidOperation: (.:OperatorToken) [], RuntimeException
+ FullyQualifiedErrorId : PropertyNotFoundStrict
```

<span data-ttu-id="1a3b7-125">Cette commande active le mode strict sur et lui affecte la version 2,0.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-125">This command turns strict mode on and sets it to version 2.0.</span></span> <span data-ttu-id="1a3b7-126">Par conséquent, PowerShell retourne une erreur si vous utilisez la syntaxe de méthode, qui utilise des parenthèses et des virgules pour un appel de fonction ou référence des variables non initialisées ou des propriétés inexistantes.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-126">As a result, PowerShell returns an error if you use method syntax, which uses parentheses and commas, for a function call or reference uninitialized variables or non-existent properties.</span></span>

<span data-ttu-id="1a3b7-127">L’exemple de sortie montre l’effet de la version 2,0 du mode strict.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-127">The sample output shows the effect of version 2.0 strict mode.</span></span>

<span data-ttu-id="1a3b7-128">Sans le mode strict version 2.0, la valeur « (3,4) » est interprétée comme un objet tableau unique auquel rien n'est ajouté.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-128">Without version 2.0 strict mode, the "(3,4)" value is interpreted as a single array object to which nothing is added.</span></span> <span data-ttu-id="1a3b7-129">En utilisant le mode strict version 2,0, il est correctement interprété comme une syntaxe défectueuse pour l’envoi de deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-129">By using version 2.0 strict mode, it is correctly interpreted as faulty syntax for submitting two values.</span></span>

<span data-ttu-id="1a3b7-130">Sans la version 2,0, la référence à la propriété **Month** inexistante d’une chaîne retourne uniquement `$Null` .</span><span class="sxs-lookup"><span data-stu-id="1a3b7-130">Without version 2.0, the reference to the non-existent **Month** property of a string returns only `$Null`.</span></span> <span data-ttu-id="1a3b7-131">En utilisant la version 2,0, elle est interprétée correctement comme une erreur de référence.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-131">By using version 2.0, it is interpreted correctly as a reference error.</span></span>

### <span data-ttu-id="1a3b7-132">Exemple 3 : activer le mode strict en tant que version 3,0</span><span class="sxs-lookup"><span data-stu-id="1a3b7-132">Example 3: Turn on strict mode as version 3.0</span></span>

<span data-ttu-id="1a3b7-133">Si le mode strict est défini sur **off** , les index non valides ou hors limites renvoient des valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-133">With strict mode set to **Off** , invalid or out of bounds indexes result return null values.</span></span>

```powershell
# Strict mode is off by default.
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
Index was outside the bounds of the array.
At line:1 char:1
+ $a[2] -eq $null
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
    + FullyQualifiedErrorId : System.IndexOutOfRangeException

Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
At line:1 char:1
+ $a['abc'] -eq $null
+ ~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvalidCastFromStringToInteger
```

<span data-ttu-id="1a3b7-134">Si le mode strict est défini sur la version 3 ou une version ultérieure, les index non valides ou hors limites génèrent des erreurs.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-134">With strict mode set to version 3 or higher, invalid or out of bounds indexes result in errors.</span></span>

## <span data-ttu-id="1a3b7-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1a3b7-135">PARAMETERS</span></span>

### <span data-ttu-id="1a3b7-136">-Désactivé</span><span class="sxs-lookup"><span data-stu-id="1a3b7-136">-Off</span></span>

<span data-ttu-id="1a3b7-137">Indique que cette applet de commande désactive le mode strict pour l’étendue actuelle et toutes les étendues enfants.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-137">Indicates that this cmdlet turns strict mode off for the current scope and all child scopes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a3b7-138">-Version</span><span class="sxs-lookup"><span data-stu-id="1a3b7-138">-Version</span></span>

<span data-ttu-id="1a3b7-139">Spécifie les conditions qui provoquent une erreur en mode strict.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-139">Specifies the conditions that cause an error in strict mode.</span></span> <span data-ttu-id="1a3b7-140">Ce paramètre accepte tout numéro de version PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-140">This parameter accepts any valid PowerShell version number.</span></span> <span data-ttu-id="1a3b7-141">Toute valeur supérieure à 3 est traitée comme la **dernière version** .</span><span class="sxs-lookup"><span data-stu-id="1a3b7-141">Any number higher than 3 is treated as **Latest** .</span></span>

<span data-ttu-id="1a3b7-142">Les valeurs effectives pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1a3b7-142">The effective values for this parameter are:</span></span>

- <span data-ttu-id="1a3b7-143">1.0</span><span class="sxs-lookup"><span data-stu-id="1a3b7-143">1.0</span></span>
  - <span data-ttu-id="1a3b7-144">Interdit les références à des variables non initialisées, à l’exception des variables non initialisées dans les chaînes.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-144">Prohibits references to uninitialized variables, except for uninitialized variables in strings.</span></span>
- <span data-ttu-id="1a3b7-145">2.0</span><span class="sxs-lookup"><span data-stu-id="1a3b7-145">2.0</span></span>
  - <span data-ttu-id="1a3b7-146">Interdit les références à des variables non initialisées.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-146">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="1a3b7-147">Cela comprend les variables non initialisées dans les chaînes.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-147">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="1a3b7-148">Interdit les références aux propriétés inexistantes d’un objet.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-148">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="1a3b7-149">Interdit les appels de fonction qui utilisent la syntaxe pour appeler des méthodes.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-149">Prohibits function calls that use the syntax for calling methods.</span></span>
- <span data-ttu-id="1a3b7-150">3.0</span><span class="sxs-lookup"><span data-stu-id="1a3b7-150">3.0</span></span>
  - <span data-ttu-id="1a3b7-151">Interdit les références à des variables non initialisées.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-151">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="1a3b7-152">Cela comprend les variables non initialisées dans les chaînes.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-152">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="1a3b7-153">Interdit les références aux propriétés inexistantes d’un objet.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-153">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="1a3b7-154">Interdit les appels de fonction qui utilisent la syntaxe pour appeler des méthodes.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-154">Prohibits function calls that use the syntax for calling methods.</span></span>
  - <span data-ttu-id="1a3b7-155">Interdit les index hors limites ou les index de tableau insolubles.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-155">Prohibit out of bounds or unresolvable array indexes.</span></span>
- <span data-ttu-id="1a3b7-156">Latest</span><span class="sxs-lookup"><span data-stu-id="1a3b7-156">Latest</span></span>
  - <span data-ttu-id="1a3b7-157">Sélectionne la dernière version disponible.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-157">Selects the latest version available.</span></span> <span data-ttu-id="1a3b7-158">La dernière version est la plus stricte.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-158">The latest version is the most strict.</span></span> <span data-ttu-id="1a3b7-159">Utilisez cette valeur pour vous assurer que les scripts utilisent la version disponible la plus stricte, même quand de nouvelles versions sont ajoutées à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-159">Use this value to make sure that scripts use the strictest available version, even when new versions are added to PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="1a3b7-160">Utilisation d’une **version** des **derniers** scripts dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-160">Using a **Version** of **Latest** in scripts.</span></span> <span data-ttu-id="1a3b7-161">La signification du **dernier** peut changer dans les nouvelles versions de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-161">The meaning of **Latest** can change in new releases of PowerShell.</span></span> <span data-ttu-id="1a3b7-162">Par conséquent, un script écrit pour une version antérieure de PowerShell qui utilise `Set-StrictMode -Version Latest` est soumis à des règles plus restrictives lorsqu’il est exécuté dans une version plus récente de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-162">Therefore, a script written for an older version of PowerShell that uses `Set-StrictMode -Version Latest` is subject to more restrictive rules when run in a newer version of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a3b7-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a3b7-163">CommonParameters</span></span>

<span data-ttu-id="1a3b7-164">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a3b7-165">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1a3b7-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a3b7-166">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1a3b7-166">INPUTS</span></span>

### <span data-ttu-id="1a3b7-167">Aucun</span><span class="sxs-lookup"><span data-stu-id="1a3b7-167">None</span></span>

<span data-ttu-id="1a3b7-168">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1a3b7-169">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1a3b7-169">OUTPUTS</span></span>

### <span data-ttu-id="1a3b7-170">Aucun</span><span class="sxs-lookup"><span data-stu-id="1a3b7-170">None</span></span>

<span data-ttu-id="1a3b7-171">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-171">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="1a3b7-172">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1a3b7-172">NOTES</span></span>

<span data-ttu-id="1a3b7-173">`Set-StrictMode` est effectif uniquement dans l’étendue dans laquelle il est défini et dans ses étendues enfants.</span><span class="sxs-lookup"><span data-stu-id="1a3b7-173">`Set-StrictMode` is effective only in the scope in which it is set and in its child scopes.</span></span> <span data-ttu-id="1a3b7-174">Pour plus d’informations sur les étendues dans PowerShell, consultez [about_Scopes](about/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="1a3b7-174">For more information about scopes in PowerShell, see [about_Scopes](about/about_Scopes.md).</span></span>

## <span data-ttu-id="1a3b7-175">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1a3b7-175">RELATED LINKS</span></span>

[<span data-ttu-id="1a3b7-176">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="1a3b7-176">Set-PSDebug</span></span>](Set-PSDebug.md)
