---
ms.topic: reference
keywords: powershell,applet de commande
ms.date: 12/12/2016
title: Get-PswaAuthorizationRule
ms.openlocfilehash: d61dce18e87311d7d815a689ba675db44aaec3cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="31184-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="31184-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="31184-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="31184-104">SYNOPSIS</span></span>

<span data-ttu-id="31184-105">Retourne un ensemble des règles d’autorisation d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="31184-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="31184-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31184-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="31184-107">ID</span><span class="sxs-lookup"><span data-stu-id="31184-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="31184-108">Name</span><span class="sxs-lookup"><span data-stu-id="31184-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="31184-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="31184-109">DESCRIPTION</span></span>

<span data-ttu-id="31184-110">L’applet de commande **Get-PswaAuthorizationRule** retourne un ensemble de règles d’autorisation d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="31184-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="31184-111">Si ni le paramètre **Id** ni le paramètre **RuleName** n’est spécifié, cette applet de commande répertorie toutes les règles.</span><span class="sxs-lookup"><span data-stu-id="31184-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="31184-112">Le paramètre **Id** peut être utilisé pour filtrer les résultats.</span><span class="sxs-lookup"><span data-stu-id="31184-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="31184-113">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="31184-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="31184-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="31184-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="31184-115">Spécifie les identificateurs (ID) des règles que cette applet de commande doit obtenir.</span><span class="sxs-lookup"><span data-stu-id="31184-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="31184-116">Si aucun ID n’est spécifié, cette applet de commande retourne toutes les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="31184-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="31184-117">Alias</span><span class="sxs-lookup"><span data-stu-id="31184-117">Aliases</span></span>                              | <span data-ttu-id="31184-118">none</span><span class="sxs-lookup"><span data-stu-id="31184-118">none</span></span>                                 |
| <span data-ttu-id="31184-119">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="31184-119">Required?</span></span>                            | <span data-ttu-id="31184-120">false</span><span class="sxs-lookup"><span data-stu-id="31184-120">false</span></span>                                |
| <span data-ttu-id="31184-121">Position ?</span><span class="sxs-lookup"><span data-stu-id="31184-121">Position?</span></span>                            | <span data-ttu-id="31184-122">2</span><span class="sxs-lookup"><span data-stu-id="31184-122">2</span></span>                                    |
| <span data-ttu-id="31184-123">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="31184-123">Default Value</span></span>                        | <span data-ttu-id="31184-124">none</span><span class="sxs-lookup"><span data-stu-id="31184-124">none</span></span>                                 |
| <span data-ttu-id="31184-125">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="31184-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="31184-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="31184-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="31184-127">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="31184-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="31184-128">false</span><span class="sxs-lookup"><span data-stu-id="31184-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="31184-129">-RuleName&lt;Chaîne\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="31184-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="31184-130">Spécifie les noms des règles d’autorisation à récupérer.</span><span class="sxs-lookup"><span data-stu-id="31184-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="31184-131">Ce paramètre retourne les règles qui correspondent exactement aux noms de règle des chaînes de ce tableau.</span><span class="sxs-lookup"><span data-stu-id="31184-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="31184-132">Alias</span><span class="sxs-lookup"><span data-stu-id="31184-132">Aliases</span></span>                              | <span data-ttu-id="31184-133">none</span><span class="sxs-lookup"><span data-stu-id="31184-133">none</span></span>                                 |
| <span data-ttu-id="31184-134">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="31184-134">Required?</span></span>                            | <span data-ttu-id="31184-135">true</span><span class="sxs-lookup"><span data-stu-id="31184-135">true</span></span>                                 |
| <span data-ttu-id="31184-136">Position ?</span><span class="sxs-lookup"><span data-stu-id="31184-136">Position?</span></span>                            | <span data-ttu-id="31184-137">2</span><span class="sxs-lookup"><span data-stu-id="31184-137">2</span></span>                                    |
| <span data-ttu-id="31184-138">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="31184-138">Default Value</span></span>                        | <span data-ttu-id="31184-139">none</span><span class="sxs-lookup"><span data-stu-id="31184-139">none</span></span>                                 |
| <span data-ttu-id="31184-140">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="31184-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="31184-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="31184-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="31184-142">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="31184-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="31184-143">false</span><span class="sxs-lookup"><span data-stu-id="31184-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="31184-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="31184-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="31184-145">Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="31184-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="31184-146">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="31184-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="31184-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="31184-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="31184-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="31184-148">int\[\]</span></span>

<span data-ttu-id="31184-149">Cette applet de commande accepte un tableau d’entiers ou un tableau de valeurs de chaîne en entrée.</span><span class="sxs-lookup"><span data-stu-id="31184-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="31184-150">Chaîne\[\]</span><span class="sxs-lookup"><span data-stu-id="31184-150">String\[\]</span></span>

<span data-ttu-id="31184-151">Cette applet de commande accepte un tableau d’entiers ou un tableau de valeurs de chaîne en entrée.</span><span class="sxs-lookup"><span data-stu-id="31184-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="31184-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="31184-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="31184-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="31184-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="31184-154">Cette applet de commande produit un objet PswaAuthorizationRule en sortie.</span><span class="sxs-lookup"><span data-stu-id="31184-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="31184-155">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="31184-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="31184-156">EXEMPLE 1</span><span class="sxs-lookup"><span data-stu-id="31184-156">EXAMPLE 1</span></span>

<span data-ttu-id="31184-157">Cet exemple obtient toutes les règles.</span><span class="sxs-lookup"><span data-stu-id="31184-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="31184-158">EXAMPLE 2</span><span class="sxs-lookup"><span data-stu-id="31184-158">EXAMPLE 2</span></span>

<span data-ttu-id="31184-159">Cet exemple obtient une règle avec l’ID *2*.</span><span class="sxs-lookup"><span data-stu-id="31184-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="31184-160">EXEMPLE 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="31184-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="31184-161">Cet exemple montre comment l’applet de commande accepte une valeur du pipeline.</span><span class="sxs-lookup"><span data-stu-id="31184-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="31184-162">Un ID de règle et un nom de règle sont passés à cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="31184-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="31184-163">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="31184-163">Related topics</span></span>

- [<span data-ttu-id="31184-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="31184-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="31184-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="31184-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="31184-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="31184-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="31184-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="31184-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)