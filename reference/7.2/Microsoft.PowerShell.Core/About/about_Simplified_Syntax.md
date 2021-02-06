---
description: Décrit des méthodes plus simples et plus naturelles pour les filtres de script pour les collections d’objets.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: dbd30d566414f784e7d5eca04af716c2bf1642b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597358"
---
# <a name="about_simplified_syntax"></a><span data-ttu-id="fd21c-103">about_Simplified_Syntax</span><span class="sxs-lookup"><span data-stu-id="fd21c-103">about_Simplified_Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="fd21c-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="fd21c-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="fd21c-105">Décrit des méthodes plus simples et plus naturelles pour les filtres de script pour les collections d’objets.</span><span class="sxs-lookup"><span data-stu-id="fd21c-105">Describes easier, more natural-language ways of scripting filters for collections of objects.</span></span>

## <a name="long-description"></a><span data-ttu-id="fd21c-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="fd21c-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="fd21c-107">La syntaxe simplifiée, introduite dans Windows PowerShell 3,0, vous permet de créer des commandes de filtre sans utiliser de blocs de script.</span><span class="sxs-lookup"><span data-stu-id="fd21c-107">Simplified syntax, introduced in Windows PowerShell 3.0, lets you build some filter commands without using script blocks.</span></span> <span data-ttu-id="fd21c-108">La syntaxe simplifiée est plus proche du langage naturel et est principalement utile avec les collections d’objets qui sont dirigés vers des commandes `Where-Object` et `ForEach-Object` leurs alias `where` et `foreach` .</span><span class="sxs-lookup"><span data-stu-id="fd21c-108">The simplified syntax more closely resembles natural language, and is primarily useful with collections of objects that get piped into commands `Where-Object` and `ForEach-Object` and their corresponding aliases `where` and `foreach`.</span></span>

<span data-ttu-id="fd21c-109">Vous pouvez utiliser une méthode sur les membres d’une collection (le plus souvent, un tableau) sans faire référence à la variable automatique `$_` à l’intérieur d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="fd21c-109">You can use a method on the members of a collection (most commonly, an array) without referring to the automatic variable `$_` inside a script block.</span></span>

<span data-ttu-id="fd21c-110">Considérez les deux appels suivants :</span><span class="sxs-lookup"><span data-stu-id="fd21c-110">Consider the following two invocations:</span></span>

### <a name="standard-syntax"></a><span data-ttu-id="fd21c-111">Syntaxe standard</span><span class="sxs-lookup"><span data-stu-id="fd21c-111">Standard Syntax</span></span>

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a><span data-ttu-id="fd21c-112">Syntaxe simplifiée</span><span class="sxs-lookup"><span data-stu-id="fd21c-112">Simplified syntax</span></span>

<span data-ttu-id="fd21c-113">Dans la syntaxe simplifiée, les opérateurs de comparaison qui fonctionnent sur les membres des objets d’une collection sont traités comme des paramètres.</span><span class="sxs-lookup"><span data-stu-id="fd21c-113">Under the simplified syntax, comparison operators that work on members of objects in a collection are treated as parameters.</span></span> <span data-ttu-id="fd21c-114">Vous pouvez appeler une méthode sur des objets dans une collection sans faire référence à la variable automatique `$_` à l’intérieur d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="fd21c-114">You can invoke a method on objects in a collection without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="fd21c-115">Comparez les deux appels suivants à ceux de l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="fd21c-115">Compare the following two invocations to those of the previous example:</span></span>

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

<span data-ttu-id="fd21c-116">Tandis que les deux syntaxes fonctionnent, la syntaxe simplifiée retourne les résultats sans faire référence à la variable automatique `$_` à l’intérieur d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="fd21c-116">While both syntaxes work, the simplified syntax returns results without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="fd21c-117">Le nom de la méthode `GetKeyAlgorithm` est traité comme un paramètre de `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="fd21c-117">The method name `GetKeyAlgorithm` is treated as a parameter of `ForEach-Object`.</span></span>
<span data-ttu-id="fd21c-118">La deuxième commande retourne les mêmes résultats, mais sans erreur, car la syntaxe simplifiée ne tente pas de retourner des résultats pour les éléments pour lesquels l’argument spécifié ne s’est pas appliqué.</span><span class="sxs-lookup"><span data-stu-id="fd21c-118">The second command returns the same results, but without errors, because the simplified syntax does not attempt to return results for items for which the specified argument did not apply.</span></span>

<span data-ttu-id="fd21c-119">Dans cet exemple, la `Process` propriété `Description` est passée en tant que paramètre de nom de membre à la `ForEach-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="fd21c-119">In this example, the `Process` property `Description` is passed as the member name parameter to the `ForEach-Object` command.</span></span> <span data-ttu-id="fd21c-120">Les résultats sont des descriptions des processus actifs.</span><span class="sxs-lookup"><span data-stu-id="fd21c-120">The results are descriptions of active processes.</span></span>

```powershell
Get-Process | foreach Description
```

<span data-ttu-id="fd21c-121">Dans cet exemple, la `DirectoryInfo` méthode `GetFiles` est passée en tant que paramètre de nom de membre de la `ForEach-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="fd21c-121">In this example, the `DirectoryInfo` method `GetFiles` is passed as the member name parameter of the `ForEach-Object` command.</span></span>  
<span data-ttu-id="fd21c-122">La méthode est appelée avec le paramètre de modèle de recherche `.*` .</span><span class="sxs-lookup"><span data-stu-id="fd21c-122">The method is called with the search pattern parameter `.*`.</span></span>  
<span data-ttu-id="fd21c-123">Les résultats sont `FileInfo` des enregistrements pour tous les fichiers masqués de type UNIX dans les répertoires de démarrage de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fd21c-123">The results are `FileInfo` records for all Unix-style hidden files in user home directories.</span></span> 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a><span data-ttu-id="fd21c-124">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="fd21c-124">SEE ALSO</span></span>

- [<span data-ttu-id="fd21c-125">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="fd21c-125">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="fd21c-126">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="fd21c-126">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="fd21c-127">Where-Object</span><span class="sxs-lookup"><span data-stu-id="fd21c-127">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
- [<span data-ttu-id="fd21c-128">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="fd21c-128">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

