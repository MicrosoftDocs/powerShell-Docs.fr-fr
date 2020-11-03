---
description: Décrit comment utiliser des caractères génériques dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 3/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 4778de5022f35f354e7783cedc5019198d11604b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208266"
---
# <a name="about-wildcards"></a><span data-ttu-id="dff19-104">À propos des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="dff19-104">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="dff19-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="dff19-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="dff19-106">Décrit comment utiliser des caractères génériques dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dff19-106">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="dff19-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="dff19-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="dff19-108">Les caractères génériques représentent un ou plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="dff19-108">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="dff19-109">Vous pouvez les utiliser pour créer des séquences de mots dans des commandes.</span><span class="sxs-lookup"><span data-stu-id="dff19-109">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="dff19-110">Par exemple, pour obtenir tous les fichiers du `C:\Techdocs` répertoire avec une `.ppt` extension de nom de fichier, tapez :</span><span class="sxs-lookup"><span data-stu-id="dff19-110">For example, to get all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="dff19-111">Dans ce cas, le `*` caractère générique astérisque () représente tous les caractères qui apparaissent avant l' `.ppt` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="dff19-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="dff19-112">PowerShell prend en charge les caractères génériques suivants :</span><span class="sxs-lookup"><span data-stu-id="dff19-112">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="dff19-113">Caractère générique</span><span class="sxs-lookup"><span data-stu-id="dff19-113">Wildcard</span></span>|<span data-ttu-id="dff19-114">Description</span><span class="sxs-lookup"><span data-stu-id="dff19-114">Description</span></span>               |<span data-ttu-id="dff19-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="dff19-115">Example</span></span> |<span data-ttu-id="dff19-116">Correspond</span><span class="sxs-lookup"><span data-stu-id="dff19-116">Match</span></span>        |<span data-ttu-id="dff19-117">Aucune correspondance</span><span class="sxs-lookup"><span data-stu-id="dff19-117">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="dff19-118">Correspond à zéro ou plusieurs caractères</span><span class="sxs-lookup"><span data-stu-id="dff19-118">Match zero or more characters</span></span> | <span data-ttu-id="dff19-119">un\*</span><span class="sxs-lookup"><span data-stu-id="dff19-119">a\*</span></span>  | <span data-ttu-id="dff19-120">aA, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="dff19-120">aA, ag, Apple</span></span> | <span data-ttu-id="dff19-121">Banana</span><span class="sxs-lookup"><span data-stu-id="dff19-121">banana</span></span> |
|<span data-ttu-id="dff19-122">?</span><span class="sxs-lookup"><span data-stu-id="dff19-122">?</span></span>       |<span data-ttu-id="dff19-123">Correspond à un caractère de cette position</span><span class="sxs-lookup"><span data-stu-id="dff19-123">Match one character in that position</span></span> | <span data-ttu-id="dff19-124">? n</span><span class="sxs-lookup"><span data-stu-id="dff19-124">?n</span></span> | <span data-ttu-id="dff19-125">, dans, sur</span><span class="sxs-lookup"><span data-stu-id="dff19-125">an, in, on</span></span> | <span data-ttu-id="dff19-126">antécédent</span><span class="sxs-lookup"><span data-stu-id="dff19-126">ran</span></span> |
|<span data-ttu-id="dff19-127">\[ \]</span><span class="sxs-lookup"><span data-stu-id="dff19-127">\[ \]</span></span>   |<span data-ttu-id="dff19-128">Correspond à une plage de caractères</span><span class="sxs-lookup"><span data-stu-id="dff19-128">Match a range of characters</span></span> | <span data-ttu-id="dff19-129">\[ook a-l \]</span><span class="sxs-lookup"><span data-stu-id="dff19-129">\[a-l\]ook</span></span> | <span data-ttu-id="dff19-130">livre, Cook, look</span><span class="sxs-lookup"><span data-stu-id="dff19-130">book, cook, look</span></span> | <span data-ttu-id="dff19-131">prit</span><span class="sxs-lookup"><span data-stu-id="dff19-131">took</span></span> |
|<span data-ttu-id="dff19-132">\[ \]</span><span class="sxs-lookup"><span data-stu-id="dff19-132">\[ \]</span></span>   |<span data-ttu-id="dff19-133">Rechercher des caractères spécifiques</span><span class="sxs-lookup"><span data-stu-id="dff19-133">Match specific characters</span></span> | <span data-ttu-id="dff19-134">\[\]ook BC</span><span class="sxs-lookup"><span data-stu-id="dff19-134">\[bc\]ook</span></span> | <span data-ttu-id="dff19-135">livre, Cook</span><span class="sxs-lookup"><span data-stu-id="dff19-135">book, cook</span></span> | <span data-ttu-id="dff19-136">rester</span><span class="sxs-lookup"><span data-stu-id="dff19-136">hook</span></span> |

<span data-ttu-id="dff19-137">Vous pouvez inclure plusieurs caractères génériques dans le même modèle de mot.</span><span class="sxs-lookup"><span data-stu-id="dff19-137">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="dff19-138">Par exemple, pour rechercher des fichiers texte dont les noms commencent par les lettres **a** à **l** , tapez :</span><span class="sxs-lookup"><span data-stu-id="dff19-138">For example, to find text files with names that begin with the letters **a** through **l** , type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="dff19-139">De nombreuses cmdlets acceptent les caractères génériques dans les valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="dff19-139">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="dff19-140">La rubrique d’aide de chaque applet de commande décrit les paramètres qui acceptent des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="dff19-140">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="dff19-141">Pour les paramètres qui acceptent des caractères génériques, leur utilisation ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="dff19-141">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="dff19-142">Vous pouvez utiliser des caractères génériques dans les commandes et les blocs de script, par exemple pour créer un modèle Word qui représente des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="dff19-142">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="dff19-143">Par exemple, la commande suivante obtient les services dans lesquels la valeur de la propriété **serviceType** comprend **interactive** .</span><span class="sxs-lookup"><span data-stu-id="dff19-143">For example, the following command gets services in which the **ServiceType** property value includes **Interactive** .</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="dff19-144">Dans l’exemple suivant, l' `If` instruction comprend une condition qui utilise des caractères génériques pour rechercher des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="dff19-144">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="dff19-145">Si la **Description** du point de restauration inclut **PowerShell** , la commande ajoute la valeur de la propriété **CreationTime** du point de restauration dans un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="dff19-145">If the restore point's **Description** includes **PowerShell** , the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="dff19-146">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="dff19-146">SEE ALSO</span></span>

[<span data-ttu-id="dff19-147">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="dff19-147">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="dff19-148">about_If</span><span class="sxs-lookup"><span data-stu-id="dff19-148">about_If</span></span>](about_If.md)

[<span data-ttu-id="dff19-149">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="dff19-149">about_Script_Blocks</span></span>](about_Script_Blocks.md)
