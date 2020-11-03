---
description: Décrit comment accéder aux éléments à partir de l’emplacement de travail dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: ed8d17b7f217c86ba3161f017e2794524d5da829
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207629"
---
# <a name="about_locations"></a><span data-ttu-id="eb286-104">about_Locations</span><span class="sxs-lookup"><span data-stu-id="eb286-104">about_Locations</span></span>

## <a name="short-description"></a><span data-ttu-id="eb286-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="eb286-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="eb286-106">Décrit comment accéder aux éléments à partir de l’emplacement de travail dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb286-106">Describes how to access items from the working location in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="eb286-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="eb286-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="eb286-108">L’emplacement de travail actuel est l’emplacement par défaut dans lequel les commandes pointent.</span><span class="sxs-lookup"><span data-stu-id="eb286-108">The current working location is the default location to which commands point.</span></span>
<span data-ttu-id="eb286-109">En d’autres termes, il s’agit de l’emplacement que PowerShell utilise si vous ne fournissez pas de chemin d’accès explicite à l’élément ou à l’emplacement affecté par la commande.</span><span class="sxs-lookup"><span data-stu-id="eb286-109">In other words, this is the location that PowerShell uses if you do not supply an explicit path to the item or location that is affected by the command.</span></span> <span data-ttu-id="eb286-110">Dans la plupart des cas, l’emplacement de travail actuel est un lecteur accessible via le fournisseur FileSystem PowerShell et, dans certains cas, un répertoire sur ce lecteur.</span><span class="sxs-lookup"><span data-stu-id="eb286-110">In most cases, the current working location is a drive accessed through the PowerShell FileSystem provider and, in some cases, a directory on that drive.</span></span>
<span data-ttu-id="eb286-111">Par exemple, vous pouvez définir l’emplacement de travail actuel à l’emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="eb286-111">For example, you might set your current working location to the following location:</span></span>

```powershell
C:\Program Files\Windows PowerShell
```

<span data-ttu-id="eb286-112">Par conséquent, toutes les commandes sont traitées à partir de cet emplacement, sauf si un autre chemin d’accès est explicitement fourni.</span><span class="sxs-lookup"><span data-stu-id="eb286-112">As a result, all commands are processed from this location unless another path is explicitly provided.</span></span>

<span data-ttu-id="eb286-113">PowerShell conserve l’emplacement de travail actuel de chaque lecteur, même si le lecteur n’est pas le lecteur actif.</span><span class="sxs-lookup"><span data-stu-id="eb286-113">PowerShell maintains the current working location for each drive even when the drive is not the current drive.</span></span> <span data-ttu-id="eb286-114">Cela vous permet d’accéder aux éléments à partir de l’emplacement de travail actuel en faisant référence uniquement au lecteur d’un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="eb286-114">This allows you to access items from the current working location by referring only to the drive of another location.</span></span>
<span data-ttu-id="eb286-115">Par exemple, supposons que votre emplacement de travail actuel est C : \\ Windows.</span><span class="sxs-lookup"><span data-stu-id="eb286-115">For example, suppose that your current working location is C:\\Windows.</span></span> <span data-ttu-id="eb286-116">Supposons à présent que vous utilisez la commande suivante pour modifier l’emplacement de travail actuel sur le lecteur HKLM :</span><span class="sxs-lookup"><span data-stu-id="eb286-116">Now, suppose you use the following command to change your current working location to the HKLM: drive:</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="eb286-117">Bien que votre emplacement actuel soit maintenant le lecteur de Registre, vous pouvez toujours accéder aux éléments dans le répertoire C : \\ Windows en utilisant simplement le lecteur c :, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eb286-117">Although your current location is now the registry drive, you can still access items in the C:\\Windows directory simply by using the C: drive, as shown in the following example:</span></span>

```powershell
Get-ChildItem C:
```

<span data-ttu-id="eb286-118">PowerShell se souvient que votre emplacement de travail actuel pour ce lecteur est le répertoire Windows. il récupère donc les éléments de ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="eb286-118">PowerShell remembers that your current working location for that drive is the Windows directory, so it retrieves items from that directory.</span></span> <span data-ttu-id="eb286-119">Les résultats seraient les mêmes si vous avez exécuté la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="eb286-119">The results would be the same if you ran the following command:</span></span>

```powershell
Get-ChildItem C:\Windows
```

<span data-ttu-id="eb286-120">Dans PowerShell, vous pouvez utiliser la commande Get-Location pour déterminer l’emplacement de travail actuel, et vous pouvez utiliser la commande Set-Location pour définir l’emplacement de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="eb286-120">In PowerShell, you can use the Get-Location command to determine the current working location, and you can use the Set-Location command to set the current working location.</span></span> <span data-ttu-id="eb286-121">Par exemple, la commande suivante définit l’emplacement de travail actuel sur le répertoire Windows du lecteur C ::</span><span class="sxs-lookup"><span data-stu-id="eb286-121">For example, the following command sets the current working location to the Windows directory of the C: drive:</span></span>

```powershell
Set-Location c:\windows
```

<span data-ttu-id="eb286-122">Une fois que vous avez défini l’emplacement de travail actuel, vous pouvez toujours accéder aux éléments à partir d’autres lecteurs en incluant simplement le nom du lecteur (suivi d’un signe deux-points) dans la commande, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eb286-122">After you set the current working location, you can still access items from other drives simply by including the drive name (followed by a colon) in the command, as shown in the following example:</span></span>

```powershell
Get-ChildItem HKLM:\software
```

<span data-ttu-id="eb286-123">L’exemple de commande récupère une liste d’éléments dans le conteneur logiciel de la ruche HKEY local machine dans le registre.</span><span class="sxs-lookup"><span data-stu-id="eb286-123">The example command retrieves a list of items in the Software container of the HKEY Local Machine hive in the registry.</span></span>

<span data-ttu-id="eb286-124">PowerShell vous permet également d’utiliser des caractères spéciaux pour représenter l’emplacement de travail actuel et son emplacement parent.</span><span class="sxs-lookup"><span data-stu-id="eb286-124">PowerShell also allows you to use special characters to represent the current working location and its parent location.</span></span> <span data-ttu-id="eb286-125">Pour représenter l’emplacement de travail actuel, utilisez un seul point.</span><span class="sxs-lookup"><span data-stu-id="eb286-125">To represent the current working location, use a single period.</span></span> <span data-ttu-id="eb286-126">Pour représenter le parent de l’emplacement de travail actuel, utilisez deux points.</span><span class="sxs-lookup"><span data-stu-id="eb286-126">To represent the parent of the current working location, use two periods.</span></span> <span data-ttu-id="eb286-127">Par exemple, le code suivant spécifie le sous-répertoire système à l’emplacement de travail actuel :</span><span class="sxs-lookup"><span data-stu-id="eb286-127">For example, the following specifies the System subdirectory in the current working location:</span></span>

```powershell
Get-ChildItem .\system
```

<span data-ttu-id="eb286-128">Si l’emplacement de travail actuel est C : \\ Windows, cette commande retourne une liste de tous les éléments dans le \\ système c : Windows \\ .</span><span class="sxs-lookup"><span data-stu-id="eb286-128">If the current working location is C:\\Windows, this command returns a list of all the items in C:\\Windows\\System.</span></span> <span data-ttu-id="eb286-129">Toutefois, si vous utilisez deux périodes, le répertoire parent du répertoire de travail actuel est utilisé, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eb286-129">However, if you use two periods, the parent directory of the current working directory is used, as shown in the following example:</span></span>

```powershell
Get-ChildItem ..\"program files"
```

<span data-ttu-id="eb286-130">Dans ce cas, PowerShell traite les deux points comme le lecteur C :, de sorte que la commande récupère tous les éléments dans le répertoire C : \\ Program Files.</span><span class="sxs-lookup"><span data-stu-id="eb286-130">In this case, PowerShell treats the two periods as the C: drive, so the command retrieves all the items in the C:\\Program Files directory.</span></span>

<span data-ttu-id="eb286-131">Un chemin d’accès commençant par une barre oblique identifie un chemin d’accès à la racine du lecteur actif.</span><span class="sxs-lookup"><span data-stu-id="eb286-131">A path beginning with a slash identifies a path from the root of the current drive.</span></span> <span data-ttu-id="eb286-132">Par exemple, si votre emplacement de travail actuel est C : \\ Program Files \\ PowerShell, la racine de votre lecteur est c. Par conséquent, la commande suivante répertorie tous les éléments dans le répertoire C : \\ Windows :</span><span class="sxs-lookup"><span data-stu-id="eb286-132">For example, if your current working location is C:\\Program Files\\PowerShell, the root of your drive is C. Therefore, the following command lists all items in the C:\\Windows directory:</span></span>

```powershell
Get-ChildItem \windows
```

<span data-ttu-id="eb286-133">Si vous ne spécifiez pas de chemin d’accès commençant par un nom de lecteur, une barre oblique ou une période lorsque vous fournissez le nom d’un conteneur ou d’un élément, le conteneur ou l’élément est supposé être situé à l’emplacement de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="eb286-133">If you do not specify a path beginning with a drive name, slash, or period when supplying the name of a container or item, the container or item is assumed to be located in the current working location.</span></span> <span data-ttu-id="eb286-134">Par exemple, si votre emplacement de travail actuel est C : \\ Windows, la commande suivante retourne tous les éléments du \\ répertoire système c : Windows \\ :</span><span class="sxs-lookup"><span data-stu-id="eb286-134">For example, if your current working location is C:\\Windows, the following command returns all the items in the C:\\Windows\\System directory:</span></span>

```powershell
Get-ChildItem system
```

<span data-ttu-id="eb286-135">Si vous spécifiez un nom de fichier plutôt qu’un nom de répertoire, PowerShell retourne des détails sur ce fichier (en supposant que ce fichier se trouve à l’emplacement de travail actuel).</span><span class="sxs-lookup"><span data-stu-id="eb286-135">If you specify a file name rather than a directory name, PowerShell returns details about that file (assuming that file is located in the current working location).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb286-136">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="eb286-136">SEE ALSO</span></span>

[<span data-ttu-id="eb286-137">Set-Location</span><span class="sxs-lookup"><span data-stu-id="eb286-137">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

[<span data-ttu-id="eb286-138">about_Providers</span><span class="sxs-lookup"><span data-stu-id="eb286-138">about_Providers</span></span>](about_Providers.md)

[<span data-ttu-id="eb286-139">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="eb286-139">about_Path_Syntax</span></span>](about_Path_Syntax.md)
