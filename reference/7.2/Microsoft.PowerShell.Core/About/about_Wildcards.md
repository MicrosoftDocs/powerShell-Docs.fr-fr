---
description: Décrit comment utiliser des caractères génériques dans PowerShell.
Locale: en-US
ms.date: 02/13/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 40620e54bb889d683192b346f3ba1c139895e4d0
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529972"
---
# <a name="about-wildcards"></a><span data-ttu-id="4c5c9-103">À propos des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="4c5c9-103">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="4c5c9-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="4c5c9-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="4c5c9-105">Décrit comment utiliser des caractères génériques dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-105">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4c5c9-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="4c5c9-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="4c5c9-107">Les caractères génériques représentent un ou plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-107">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="4c5c9-108">Vous pouvez les utiliser pour créer des séquences de mots dans des commandes.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-108">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="4c5c9-109">Les expressions génériques sont utilisées avec l' `-like` opérateur ou avec n’importe quel paramètre qui accepte les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-109">Wildcard expressions are used with the `-like` operator or with any parameter that accepts wildcards.</span></span>

<span data-ttu-id="4c5c9-110">Par exemple, pour faire correspondre tous les fichiers du `C:\Techdocs` répertoire avec une `.ppt` extension de nom de fichier, tapez :</span><span class="sxs-lookup"><span data-stu-id="4c5c9-110">For example, to match all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="4c5c9-111">Dans ce cas, le `*` caractère générique astérisque () représente tous les caractères qui apparaissent avant l' `.ppt` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="4c5c9-112">Les expressions génériques sont plus simples que les expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-112">Wildcard expressions are simpler than regular expressions.</span></span> <span data-ttu-id="4c5c9-113">Pour plus d’informations, consultez [about_regular_expressions](./about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4c5c9-113">For more information, see [about_Regular_Expressions](./about_Regular_Expressions.md).</span></span>

<span data-ttu-id="4c5c9-114">PowerShell prend en charge les caractères génériques suivants :</span><span class="sxs-lookup"><span data-stu-id="4c5c9-114">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="4c5c9-115">Caractère générique</span><span class="sxs-lookup"><span data-stu-id="4c5c9-115">Wildcard</span></span>|<span data-ttu-id="4c5c9-116">Description</span><span class="sxs-lookup"><span data-stu-id="4c5c9-116">Description</span></span>               |<span data-ttu-id="4c5c9-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="4c5c9-117">Example</span></span> |<span data-ttu-id="4c5c9-118">Faire correspondre</span><span class="sxs-lookup"><span data-stu-id="4c5c9-118">Match</span></span>        |<span data-ttu-id="4c5c9-119">Aucune correspondance</span><span class="sxs-lookup"><span data-stu-id="4c5c9-119">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="4c5c9-120">Correspond à zéro ou plusieurs caractères</span><span class="sxs-lookup"><span data-stu-id="4c5c9-120">Match zero or more characters</span></span> | <span data-ttu-id="4c5c9-121">un\*</span><span class="sxs-lookup"><span data-stu-id="4c5c9-121">a\*</span></span>  | <span data-ttu-id="4c5c9-122">aA, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="4c5c9-122">aA, ag, Apple</span></span> | <span data-ttu-id="4c5c9-123">Banana</span><span class="sxs-lookup"><span data-stu-id="4c5c9-123">banana</span></span> |
|<span data-ttu-id="4c5c9-124">?</span><span class="sxs-lookup"><span data-stu-id="4c5c9-124">?</span></span>       |<span data-ttu-id="4c5c9-125">Correspond à un caractère de cette position</span><span class="sxs-lookup"><span data-stu-id="4c5c9-125">Match one character in that position</span></span> | <span data-ttu-id="4c5c9-126">? n</span><span class="sxs-lookup"><span data-stu-id="4c5c9-126">?n</span></span> | <span data-ttu-id="4c5c9-127">, dans, sur</span><span class="sxs-lookup"><span data-stu-id="4c5c9-127">an, in, on</span></span> | <span data-ttu-id="4c5c9-128">antécédent</span><span class="sxs-lookup"><span data-stu-id="4c5c9-128">ran</span></span> |
|<span data-ttu-id="4c5c9-129">\[ \]</span><span class="sxs-lookup"><span data-stu-id="4c5c9-129">\[ \]</span></span>   |<span data-ttu-id="4c5c9-130">Correspond à une plage de caractères</span><span class="sxs-lookup"><span data-stu-id="4c5c9-130">Match a range of characters</span></span> | <span data-ttu-id="4c5c9-131">\[ook a-l \]</span><span class="sxs-lookup"><span data-stu-id="4c5c9-131">\[a-l\]ook</span></span> | <span data-ttu-id="4c5c9-132">livre, Cook, look</span><span class="sxs-lookup"><span data-stu-id="4c5c9-132">book, cook, look</span></span> | <span data-ttu-id="4c5c9-133">prit</span><span class="sxs-lookup"><span data-stu-id="4c5c9-133">took</span></span> |
|<span data-ttu-id="4c5c9-134">\[ \]</span><span class="sxs-lookup"><span data-stu-id="4c5c9-134">\[ \]</span></span>   |<span data-ttu-id="4c5c9-135">Rechercher des caractères spécifiques</span><span class="sxs-lookup"><span data-stu-id="4c5c9-135">Match specific characters</span></span> | <span data-ttu-id="4c5c9-136">\[\]ook BC</span><span class="sxs-lookup"><span data-stu-id="4c5c9-136">\[bc\]ook</span></span> | <span data-ttu-id="4c5c9-137">livre, Cook</span><span class="sxs-lookup"><span data-stu-id="4c5c9-137">book, cook</span></span> | <span data-ttu-id="4c5c9-138">rester</span><span class="sxs-lookup"><span data-stu-id="4c5c9-138">hook</span></span> |

<span data-ttu-id="4c5c9-139">Vous pouvez inclure plusieurs caractères génériques dans le même modèle de mot.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-139">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="4c5c9-140">Par exemple, pour rechercher des fichiers texte dont les noms commencent par les lettres **a** à **l**, tapez :</span><span class="sxs-lookup"><span data-stu-id="4c5c9-140">For example, to find text files with names that begin with the letters **a** through **l**, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="4c5c9-141">De nombreuses cmdlets acceptent les caractères génériques dans les valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-141">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="4c5c9-142">La rubrique d’aide de chaque applet de commande décrit les paramètres qui acceptent des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-142">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="4c5c9-143">Pour les paramètres qui acceptent des caractères génériques, leur utilisation ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-143">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="4c5c9-144">Vous pouvez utiliser des caractères génériques dans les commandes et les blocs de script, par exemple pour créer un modèle Word qui représente des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-144">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="4c5c9-145">Par exemple, la commande suivante obtient les services dans lesquels la valeur de la propriété **serviceType** comprend **interactive**.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-145">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="4c5c9-146">Dans l’exemple suivant, l' `If` instruction comprend une condition qui utilise des caractères génériques pour rechercher des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-146">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="4c5c9-147">Si la **Description** du point de restauration inclut **PowerShell**, la commande ajoute la valeur de la propriété **CreationTime** du point de restauration dans un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="4c5c9-147">If the restore point's **Description** includes **PowerShell**, the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="4c5c9-148">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="4c5c9-148">SEE ALSO</span></span>

[<span data-ttu-id="4c5c9-149">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="4c5c9-149">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="4c5c9-150">about_If</span><span class="sxs-lookup"><span data-stu-id="4c5c9-150">about_If</span></span>](about_If.md)

[<span data-ttu-id="4c5c9-151">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="4c5c9-151">about_Script_Blocks</span></span>](about_Script_Blocks.md)

