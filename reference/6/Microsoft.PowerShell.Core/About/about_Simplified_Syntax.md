---
description: Décrit des méthodes plus simples et plus naturelles pour les filtres de script pour les collections d’objets.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: d2e603b4d2092d4ba4ed9c1d7253991cc34ddca8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206862"
---
# <a name="about_simplified_syntax"></a><span data-ttu-id="94d25-104">about_Simplified_Syntax</span><span class="sxs-lookup"><span data-stu-id="94d25-104">about_Simplified_Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="94d25-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="94d25-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="94d25-106">Décrit des méthodes plus simples et plus naturelles pour les filtres de script pour les collections d’objets.</span><span class="sxs-lookup"><span data-stu-id="94d25-106">Describes easier, more natural-language ways of scripting filters for collections of objects.</span></span>

## <a name="long-description"></a><span data-ttu-id="94d25-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="94d25-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="94d25-108">La syntaxe simplifiée, introduite dans Windows PowerShell 3,0, vous permet de créer des commandes de filtre sans utiliser de blocs de script.</span><span class="sxs-lookup"><span data-stu-id="94d25-108">Simplified syntax, introduced in Windows PowerShell 3.0, lets you build some filter commands without using script blocks.</span></span> <span data-ttu-id="94d25-109">La syntaxe simplifiée est plus proche du langage naturel et est principalement utile avec les collections d’objets qui sont dirigés vers des commandes `Where-Object` et `ForEach-Object` leurs alias `where` et `foreach` .</span><span class="sxs-lookup"><span data-stu-id="94d25-109">The simplified syntax more closely resembles natural language, and is primarily useful with collections of objects that get piped into commands `Where-Object` and `ForEach-Object` and their corresponding aliases `where` and `foreach`.</span></span>

<span data-ttu-id="94d25-110">Vous pouvez utiliser une méthode sur les membres d’une collection (le plus souvent, un tableau) sans faire référence à la variable automatique `$_` à l’intérieur d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="94d25-110">You can use a method on the members of a collection (most commonly, an array) without referring to the automatic variable `$_` inside a script block.</span></span>

<span data-ttu-id="94d25-111">Considérez les deux appels suivants :</span><span class="sxs-lookup"><span data-stu-id="94d25-111">Consider the following two invocations:</span></span>

### <a name="standard-syntax"></a><span data-ttu-id="94d25-112">Syntaxe standard</span><span class="sxs-lookup"><span data-stu-id="94d25-112">Standard Syntax</span></span>

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a><span data-ttu-id="94d25-113">Syntaxe simplifiée</span><span class="sxs-lookup"><span data-stu-id="94d25-113">Simplified syntax</span></span>

<span data-ttu-id="94d25-114">Dans la syntaxe simplifiée, les opérateurs de comparaison qui fonctionnent sur les membres des objets d’une collection sont traités comme des paramètres.</span><span class="sxs-lookup"><span data-stu-id="94d25-114">Under the simplified syntax, comparison operators that work on members of objects in a collection are treated as parameters.</span></span> <span data-ttu-id="94d25-115">Vous pouvez appeler une méthode sur des objets dans une collection sans faire référence à la variable automatique `$_` à l’intérieur d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="94d25-115">You can invoke a method on objects in a collection without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="94d25-116">Comparez les deux appels suivants à ceux de l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="94d25-116">Compare the following two invocations to those of the previous example:</span></span>
```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

<span data-ttu-id="94d25-117">Tandis que les deux syntaxes fonctionnent, la syntaxe simplifiée retourne les résultats sans faire référence à la variable automatique `$_` à l’intérieur d’un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="94d25-117">While both syntaxes work, the simplified syntax returns results without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="94d25-118">Le nom de la méthode `GetKeyAlgorithm` est traité comme un paramètre de `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="94d25-118">The method name `GetKeyAlgorithm` is treated as a parameter of `ForEach-Object`.</span></span>
<span data-ttu-id="94d25-119">La deuxième commande retourne les mêmes résultats, mais sans erreur, car la syntaxe simplifiée ne tente pas de retourner des résultats pour les éléments pour lesquels l’argument spécifié ne s’est pas appliqué.</span><span class="sxs-lookup"><span data-stu-id="94d25-119">The second command returns the same results, but without errors, because the simplified syntax does not attempt to return results for items for which the specified argument did not apply.</span></span>

<span data-ttu-id="94d25-120">Dans cet exemple, la `Process` propriété `Description` est passée en tant que paramètre de nom de membre à la `ForEach-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="94d25-120">In this example, the `Process` property `Description` is passed as the member name parameter to the `ForEach-Object` command.</span></span> <span data-ttu-id="94d25-121">Les résultats sont des descriptions des processus actifs.</span><span class="sxs-lookup"><span data-stu-id="94d25-121">The results are descriptions of active processes.</span></span>

```powershell
Get-Process | foreach Description
```

<span data-ttu-id="94d25-122">Dans cet exemple, la `DirectoryInfo` méthode `GetFiles` est passée en tant que paramètre de nom de membre de la `ForEach-Object` commande.</span><span class="sxs-lookup"><span data-stu-id="94d25-122">In this example, the `DirectoryInfo` method `GetFiles` is passed as the member name parameter of the `ForEach-Object` command.</span></span>  
<span data-ttu-id="94d25-123">La méthode est appelée avec le paramètre de modèle de recherche `.*` .</span><span class="sxs-lookup"><span data-stu-id="94d25-123">The method is called with the search pattern parameter `.*`.</span></span>  
<span data-ttu-id="94d25-124">Les résultats sont `FileInfo` des enregistrements pour tous les fichiers masqués de type UNIX dans les répertoires de démarrage de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="94d25-124">The results are `FileInfo` records for all Unix-style hidden files in user home directories.</span></span> 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a><span data-ttu-id="94d25-125">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="94d25-125">SEE ALSO</span></span>

- [<span data-ttu-id="94d25-126">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="94d25-126">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="94d25-127">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="94d25-127">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="94d25-128">Where-Object</span><span class="sxs-lookup"><span data-stu-id="94d25-128">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
- [<span data-ttu-id="94d25-129">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="94d25-129">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
