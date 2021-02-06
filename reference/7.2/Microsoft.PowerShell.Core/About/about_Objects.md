---
description: Fournit des informations essentielles sur les objets dans PowerShell.
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: bfb66e72a74d20379123558b85047097dc801e9d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598795"
---
# <a name="about-objects"></a><span data-ttu-id="c205c-103">À propos des objets</span><span class="sxs-lookup"><span data-stu-id="c205c-103">About Objects</span></span>

## <a name="short-description"></a><span data-ttu-id="c205c-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="c205c-104">Short Description</span></span>
<span data-ttu-id="c205c-105">Fournit des informations essentielles sur les objets dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c205c-105">Provides essential information about objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="c205c-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="c205c-106">Long Description</span></span>

<span data-ttu-id="c205c-107">Toutes les actions que vous effectuez dans PowerShell se produisent dans le contexte d’objets.</span><span class="sxs-lookup"><span data-stu-id="c205c-107">Every action you take in PowerShell occurs within the context of objects.</span></span> <span data-ttu-id="c205c-108">À mesure que les données se déplacent d’une commande à l’autre, elles se déplacent sous la forme d’un ou plusieurs objets identifiables.</span><span class="sxs-lookup"><span data-stu-id="c205c-108">As data moves from one command to the next, it moves as one or more identifiable objects.</span></span> <span data-ttu-id="c205c-109">Un objet est une collection de données qui représente un élément.</span><span class="sxs-lookup"><span data-stu-id="c205c-109">An object, then, is a collection of data that represents an item.</span></span> <span data-ttu-id="c205c-110">Un objet est constitué de trois types de données : le type d’objets, ses méthodes et ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="c205c-110">An object is made up of three types of data: the objects type, its methods, and its properties.</span></span>

## <a name="types-methods-and-properties"></a><span data-ttu-id="c205c-111">Types, méthodes et propriétés</span><span class="sxs-lookup"><span data-stu-id="c205c-111">Types, Methods, and Properties</span></span>

<span data-ttu-id="c205c-112">Le type d’objet indique le type d’objet dont il s’agit.</span><span class="sxs-lookup"><span data-stu-id="c205c-112">The object type tells what kind of object it is.</span></span> <span data-ttu-id="c205c-113">Par exemple, un objet qui représente un fichier est un objet FileInfo.</span><span class="sxs-lookup"><span data-stu-id="c205c-113">For example, an object that represents a file is a FileInfo object.</span></span>

<span data-ttu-id="c205c-114">Les méthodes d’objet sont des actions que vous pouvez effectuer sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="c205c-114">The object methods are actions that you can perform on the object.</span></span>
<span data-ttu-id="c205c-115">Par exemple, les objets FileInfo ont une méthode CopyTo que vous pouvez utiliser pour copier le fichier.</span><span class="sxs-lookup"><span data-stu-id="c205c-115">For example, FileInfo objects have a CopyTo method that you can use to copy the file.</span></span>

<span data-ttu-id="c205c-116">Les propriétés d’objet stockent des informations sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="c205c-116">Object properties store information about the object.</span></span> <span data-ttu-id="c205c-117">Par exemple, les objets FileInfo ont une propriété LastWriteTime qui stocke la date et l’heure auxquelles le fichier a été accédé le plus récemment.</span><span class="sxs-lookup"><span data-stu-id="c205c-117">For example, FileInfo objects have a LastWriteTime property that stores the date and time that the file was most recently accessed.</span></span>

<span data-ttu-id="c205c-118">Lorsque vous travaillez avec des objets, vous pouvez utiliser leurs méthodes et propriétés dans les commandes pour effectuer une action et gérer des données.</span><span class="sxs-lookup"><span data-stu-id="c205c-118">When working with objects, you can use their methods and properties in commands to take action and manage data.</span></span>

## <a name="objects-in-pipelines"></a><span data-ttu-id="c205c-119">Objets dans les pipelines</span><span class="sxs-lookup"><span data-stu-id="c205c-119">Objects in Pipelines</span></span>

<span data-ttu-id="c205c-120">Lorsque les commandes sont combinées dans un pipeline, elles passent des informations les unes aux autres sous forme d’objets.</span><span class="sxs-lookup"><span data-stu-id="c205c-120">When commands are combined in a pipeline, they pass information to each other as objects.</span></span> <span data-ttu-id="c205c-121">Lorsque la première commande s’exécute, elle envoie un ou plusieurs objets dans le pipeline vers la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="c205c-121">When the first command runs, it sends one or more objects down the pipeline to the second command.</span></span> <span data-ttu-id="c205c-122">La deuxième commande reçoit les objets de la première commande, traite les objets, puis passe les objets nouveaux ou modifiés à la commande suivante dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="c205c-122">The second command receives the objects from the first command, processes the objects, and then passes new or revised objects to the next command in the pipeline.</span></span>
<span data-ttu-id="c205c-123">Cela se poursuit jusqu’à ce que toutes les commandes dans le pipeline s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="c205c-123">This continues until all commands in the pipeline run.</span></span>

<span data-ttu-id="c205c-124">L’exemple suivant montre comment les objets sont passés d’une commande à l’autre :</span><span class="sxs-lookup"><span data-stu-id="c205c-124">The following example demonstrates how objects are passed from one command to the next:</span></span>

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

<span data-ttu-id="c205c-125">La première commande `Get-ChildItem C:` retourne un objet de fichier ou de répertoire pour chaque élément dans le répertoire racine du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="c205c-125">The first command `Get-ChildItem C:` returns a file or directory object for each item in the root directory of the file system.</span></span> <span data-ttu-id="c205c-126">Les objets de fichiers et de répertoires sont passés dans le pipeline à la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="c205c-126">The file and directory objects are passed down the pipeline to the second command.</span></span>

<span data-ttu-id="c205c-127">La deuxième commande `where { $_.PsIsContainer -eq $false }` utilise la propriété PSIsContainer de tous les objets de système de fichiers pour sélectionner uniquement les fichiers qui ont la valeur false ( \$ false) dans leur propriété PSIsContainer.</span><span class="sxs-lookup"><span data-stu-id="c205c-127">The second command `where { $_.PsIsContainer -eq $false }` uses the PsIsContainer property of all file system objects to select only files, which have a value of False (\$false) in their PsIsContainer property.</span></span> <span data-ttu-id="c205c-128">Les dossiers, qui sont des conteneurs et, par conséquent, ont la valeur true ( \$ vrai) dans leur propriété PSIsContainer, ils ne sont pas sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="c205c-128">Folders, which are containers and, thus, have a value of True (\$true) in their PsIsContainer property, are not selected.</span></span>

<span data-ttu-id="c205c-129">La deuxième commande transmet uniquement les objets de fichier à la troisième commande `Format-List` , qui affiche les objets de fichier dans une liste.</span><span class="sxs-lookup"><span data-stu-id="c205c-129">The second command passes only the file objects to the third command `Format-List`, which displays the file objects in a list.</span></span>

## <a name="see-also"></a><span data-ttu-id="c205c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c205c-130">See Also</span></span>

[<span data-ttu-id="c205c-131">about_Methods</span><span class="sxs-lookup"><span data-stu-id="c205c-131">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="c205c-132">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="c205c-132">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="c205c-133">about_Properties</span><span class="sxs-lookup"><span data-stu-id="c205c-133">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="c205c-134">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="c205c-134">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="c205c-135">Get-Member</span><span class="sxs-lookup"><span data-stu-id="c205c-135">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

