---
description: Fournit des informations essentielles sur les objets dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: 152234de5e4f55f63b70ee9775bba0c5c9977f84
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207021"
---
# <a name="about-objects"></a><span data-ttu-id="00d2c-104">À propos des objets</span><span class="sxs-lookup"><span data-stu-id="00d2c-104">About Objects</span></span>

## <a name="short-description"></a><span data-ttu-id="00d2c-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="00d2c-105">Short Description</span></span>
<span data-ttu-id="00d2c-106">Fournit des informations essentielles sur les objets dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00d2c-106">Provides essential information about objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="00d2c-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="00d2c-107">Long Description</span></span>

<span data-ttu-id="00d2c-108">Toutes les actions que vous effectuez dans PowerShell se produisent dans le contexte d’objets.</span><span class="sxs-lookup"><span data-stu-id="00d2c-108">Every action you take in PowerShell occurs within the context of objects.</span></span> <span data-ttu-id="00d2c-109">À mesure que les données se déplacent d’une commande à l’autre, elles se déplacent sous la forme d’un ou plusieurs objets identifiables.</span><span class="sxs-lookup"><span data-stu-id="00d2c-109">As data moves from one command to the next, it moves as one or more identifiable objects.</span></span> <span data-ttu-id="00d2c-110">Un objet est une collection de données qui représente un élément.</span><span class="sxs-lookup"><span data-stu-id="00d2c-110">An object, then, is a collection of data that represents an item.</span></span> <span data-ttu-id="00d2c-111">Un objet est constitué de trois types de données : le type d’objets, ses méthodes et ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="00d2c-111">An object is made up of three types of data: the objects type, its methods, and its properties.</span></span>

## <a name="types-methods-and-properties"></a><span data-ttu-id="00d2c-112">Types, méthodes et propriétés</span><span class="sxs-lookup"><span data-stu-id="00d2c-112">Types, Methods, and Properties</span></span>

<span data-ttu-id="00d2c-113">Le type d’objet indique le type d’objet dont il s’agit.</span><span class="sxs-lookup"><span data-stu-id="00d2c-113">The object type tells what kind of object it is.</span></span> <span data-ttu-id="00d2c-114">Par exemple, un objet qui représente un fichier est un objet FileInfo.</span><span class="sxs-lookup"><span data-stu-id="00d2c-114">For example, an object that represents a file is a FileInfo object.</span></span>

<span data-ttu-id="00d2c-115">Les méthodes d’objet sont des actions que vous pouvez effectuer sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="00d2c-115">The object methods are actions that you can perform on the object.</span></span>
<span data-ttu-id="00d2c-116">Par exemple, les objets FileInfo ont une méthode CopyTo que vous pouvez utiliser pour copier le fichier.</span><span class="sxs-lookup"><span data-stu-id="00d2c-116">For example, FileInfo objects have a CopyTo method that you can use to copy the file.</span></span>

<span data-ttu-id="00d2c-117">Les propriétés d’objet stockent des informations sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="00d2c-117">Object properties store information about the object.</span></span> <span data-ttu-id="00d2c-118">Par exemple, les objets FileInfo ont une propriété LastWriteTime qui stocke la date et l’heure auxquelles le fichier a été accédé le plus récemment.</span><span class="sxs-lookup"><span data-stu-id="00d2c-118">For example, FileInfo objects have a LastWriteTime property that stores the date and time that the file was most recently accessed.</span></span>

<span data-ttu-id="00d2c-119">Lorsque vous travaillez avec des objets, vous pouvez utiliser leurs méthodes et propriétés dans les commandes pour effectuer une action et gérer des données.</span><span class="sxs-lookup"><span data-stu-id="00d2c-119">When working with objects, you can use their methods and properties in commands to take action and manage data.</span></span>

## <a name="objects-in-pipelines"></a><span data-ttu-id="00d2c-120">Objets dans les pipelines</span><span class="sxs-lookup"><span data-stu-id="00d2c-120">Objects in Pipelines</span></span>

<span data-ttu-id="00d2c-121">Lorsque les commandes sont combinées dans un pipeline, elles passent des informations les unes aux autres sous forme d’objets.</span><span class="sxs-lookup"><span data-stu-id="00d2c-121">When commands are combined in a pipeline, they pass information to each other as objects.</span></span> <span data-ttu-id="00d2c-122">Lorsque la première commande s’exécute, elle envoie un ou plusieurs objets dans le pipeline vers la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="00d2c-122">When the first command runs, it sends one or more objects down the pipeline to the second command.</span></span> <span data-ttu-id="00d2c-123">La deuxième commande reçoit les objets de la première commande, traite les objets, puis passe les objets nouveaux ou modifiés à la commande suivante dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="00d2c-123">The second command receives the objects from the first command, processes the objects, and then passes new or revised objects to the next command in the pipeline.</span></span>
<span data-ttu-id="00d2c-124">Cela se poursuit jusqu’à ce que toutes les commandes dans le pipeline s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="00d2c-124">This continues until all commands in the pipeline run.</span></span>

<span data-ttu-id="00d2c-125">L’exemple suivant montre comment les objets sont passés d’une commande à l’autre :</span><span class="sxs-lookup"><span data-stu-id="00d2c-125">The following example demonstrates how objects are passed from one command to the next:</span></span>

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

<span data-ttu-id="00d2c-126">La première commande `Get-ChildItem C:` retourne un objet de fichier ou de répertoire pour chaque élément dans le répertoire racine du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="00d2c-126">The first command `Get-ChildItem C:` returns a file or directory object for each item in the root directory of the file system.</span></span> <span data-ttu-id="00d2c-127">Les objets de fichiers et de répertoires sont passés dans le pipeline à la deuxième commande.</span><span class="sxs-lookup"><span data-stu-id="00d2c-127">The file and directory objects are passed down the pipeline to the second command.</span></span>

<span data-ttu-id="00d2c-128">La deuxième commande `where { $_.PsIsContainer -eq $false }` utilise la propriété PSIsContainer de tous les objets de système de fichiers pour sélectionner uniquement les fichiers qui ont la valeur false ( \$ false) dans leur propriété PSIsContainer.</span><span class="sxs-lookup"><span data-stu-id="00d2c-128">The second command `where { $_.PsIsContainer -eq $false }` uses the PsIsContainer property of all file system objects to select only files, which have a value of False (\$false) in their PsIsContainer property.</span></span> <span data-ttu-id="00d2c-129">Les dossiers, qui sont des conteneurs et, par conséquent, ont la valeur true ( \$ vrai) dans leur propriété PSIsContainer, ils ne sont pas sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="00d2c-129">Folders, which are containers and, thus, have a value of True (\$true) in their PsIsContainer property, are not selected.</span></span>

<span data-ttu-id="00d2c-130">La deuxième commande transmet uniquement les objets de fichier à la troisième commande `Format-List` , qui affiche les objets de fichier dans une liste.</span><span class="sxs-lookup"><span data-stu-id="00d2c-130">The second command passes only the file objects to the third command `Format-List`, which displays the file objects in a list.</span></span>

## <a name="see-also"></a><span data-ttu-id="00d2c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00d2c-131">See Also</span></span>

[<span data-ttu-id="00d2c-132">about_Methods</span><span class="sxs-lookup"><span data-stu-id="00d2c-132">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="00d2c-133">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="00d2c-133">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="00d2c-134">about_Properties</span><span class="sxs-lookup"><span data-stu-id="00d2c-134">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="00d2c-135">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="00d2c-135">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="00d2c-136">Get-Member</span><span class="sxs-lookup"><span data-stu-id="00d2c-136">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
