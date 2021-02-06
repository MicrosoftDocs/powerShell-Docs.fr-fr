---
description: Décrit comment utiliser des caractères génériques dans PowerShell.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: b5f13fdbfbc24e19e5ad0b1cd6ecc1b99f68914f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598777"
---
# <a name="about-wildcards"></a><span data-ttu-id="e8c55-103">À propos des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="e8c55-103">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="e8c55-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="e8c55-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="e8c55-105">Décrit comment utiliser des caractères génériques dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8c55-105">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e8c55-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="e8c55-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="e8c55-107">Les caractères génériques représentent un ou plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="e8c55-107">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="e8c55-108">Vous pouvez les utiliser pour créer des séquences de mots dans des commandes.</span><span class="sxs-lookup"><span data-stu-id="e8c55-108">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="e8c55-109">Par exemple, pour obtenir tous les fichiers du `C:\Techdocs` répertoire avec une `.ppt` extension de nom de fichier, tapez :</span><span class="sxs-lookup"><span data-stu-id="e8c55-109">For example, to get all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="e8c55-110">Dans ce cas, le `*` caractère générique astérisque () représente tous les caractères qui apparaissent avant l' `.ppt` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e8c55-110">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="e8c55-111">PowerShell prend en charge les caractères génériques suivants :</span><span class="sxs-lookup"><span data-stu-id="e8c55-111">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="e8c55-112">Caractère générique</span><span class="sxs-lookup"><span data-stu-id="e8c55-112">Wildcard</span></span>|<span data-ttu-id="e8c55-113">Description</span><span class="sxs-lookup"><span data-stu-id="e8c55-113">Description</span></span>               |<span data-ttu-id="e8c55-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8c55-114">Example</span></span> |<span data-ttu-id="e8c55-115">Faire correspondre</span><span class="sxs-lookup"><span data-stu-id="e8c55-115">Match</span></span>        |<span data-ttu-id="e8c55-116">Aucune correspondance</span><span class="sxs-lookup"><span data-stu-id="e8c55-116">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="e8c55-117">Correspond à zéro ou plusieurs caractères</span><span class="sxs-lookup"><span data-stu-id="e8c55-117">Match zero or more characters</span></span> | <span data-ttu-id="e8c55-118">un\*</span><span class="sxs-lookup"><span data-stu-id="e8c55-118">a\*</span></span>  | <span data-ttu-id="e8c55-119">aA, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="e8c55-119">aA, ag, Apple</span></span> | <span data-ttu-id="e8c55-120">Banana</span><span class="sxs-lookup"><span data-stu-id="e8c55-120">banana</span></span> |
|<span data-ttu-id="e8c55-121">?</span><span class="sxs-lookup"><span data-stu-id="e8c55-121">?</span></span>       |<span data-ttu-id="e8c55-122">Correspond à un caractère de cette position</span><span class="sxs-lookup"><span data-stu-id="e8c55-122">Match one character in that position</span></span> | <span data-ttu-id="e8c55-123">? n</span><span class="sxs-lookup"><span data-stu-id="e8c55-123">?n</span></span> | <span data-ttu-id="e8c55-124">, dans, sur</span><span class="sxs-lookup"><span data-stu-id="e8c55-124">an, in, on</span></span> | <span data-ttu-id="e8c55-125">antécédent</span><span class="sxs-lookup"><span data-stu-id="e8c55-125">ran</span></span> |
|<span data-ttu-id="e8c55-126">\[ \]</span><span class="sxs-lookup"><span data-stu-id="e8c55-126">\[ \]</span></span>   |<span data-ttu-id="e8c55-127">Correspond à une plage de caractères</span><span class="sxs-lookup"><span data-stu-id="e8c55-127">Match a range of characters</span></span> | <span data-ttu-id="e8c55-128">\[ook a-l \]</span><span class="sxs-lookup"><span data-stu-id="e8c55-128">\[a-l\]ook</span></span> | <span data-ttu-id="e8c55-129">livre, Cook, look</span><span class="sxs-lookup"><span data-stu-id="e8c55-129">book, cook, look</span></span> | <span data-ttu-id="e8c55-130">prit</span><span class="sxs-lookup"><span data-stu-id="e8c55-130">took</span></span> |
|<span data-ttu-id="e8c55-131">\[ \]</span><span class="sxs-lookup"><span data-stu-id="e8c55-131">\[ \]</span></span>   |<span data-ttu-id="e8c55-132">Rechercher des caractères spécifiques</span><span class="sxs-lookup"><span data-stu-id="e8c55-132">Match specific characters</span></span> | <span data-ttu-id="e8c55-133">\[\]ook BC</span><span class="sxs-lookup"><span data-stu-id="e8c55-133">\[bc\]ook</span></span> | <span data-ttu-id="e8c55-134">livre, Cook</span><span class="sxs-lookup"><span data-stu-id="e8c55-134">book, cook</span></span> | <span data-ttu-id="e8c55-135">rester</span><span class="sxs-lookup"><span data-stu-id="e8c55-135">hook</span></span> |

<span data-ttu-id="e8c55-136">Vous pouvez inclure plusieurs caractères génériques dans le même modèle de mot.</span><span class="sxs-lookup"><span data-stu-id="e8c55-136">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="e8c55-137">Par exemple, pour rechercher des fichiers texte dont les noms commencent par les lettres **a** à **l**, tapez :</span><span class="sxs-lookup"><span data-stu-id="e8c55-137">For example, to find text files with names that begin with the letters **a** through **l**, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="e8c55-138">De nombreuses cmdlets acceptent les caractères génériques dans les valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="e8c55-138">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="e8c55-139">La rubrique d’aide de chaque applet de commande décrit les paramètres qui acceptent des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="e8c55-139">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="e8c55-140">Pour les paramètres qui acceptent des caractères génériques, leur utilisation ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="e8c55-140">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="e8c55-141">Vous pouvez utiliser des caractères génériques dans les commandes et les blocs de script, par exemple pour créer un modèle Word qui représente des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="e8c55-141">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="e8c55-142">Par exemple, la commande suivante obtient les services dans lesquels la valeur de la propriété **serviceType** comprend **interactive**.</span><span class="sxs-lookup"><span data-stu-id="e8c55-142">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="e8c55-143">Dans l’exemple suivant, l' `If` instruction comprend une condition qui utilise des caractères génériques pour rechercher des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="e8c55-143">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="e8c55-144">Si la **Description** du point de restauration inclut **PowerShell**, la commande ajoute la valeur de la propriété **CreationTime** du point de restauration dans un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="e8c55-144">If the restore point's **Description** includes **PowerShell**, the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e8c55-145">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="e8c55-145">SEE ALSO</span></span>

[<span data-ttu-id="e8c55-146">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="e8c55-146">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="e8c55-147">about_If</span><span class="sxs-lookup"><span data-stu-id="e8c55-147">about_If</span></span>](about_If.md)

[<span data-ttu-id="e8c55-148">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="e8c55-148">about_Script_Blocks</span></span>](about_Script_Blocks.md)

