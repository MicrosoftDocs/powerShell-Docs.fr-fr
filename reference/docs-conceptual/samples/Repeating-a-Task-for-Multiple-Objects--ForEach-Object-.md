---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Répétition d’une tâche pour plusieurs objets ForEach Object
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086168"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="f227e-103">Répétition d’une tâche pour plusieurs objets (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="f227e-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="f227e-104">La cmdlet **ForEach-Object** utilise des blocs de script et le descripteur `$_` pour l’objet de pipeline actuel, afin de vous permettre d’exécuter une commande sur chaque objet figurant dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="f227e-104">The **ForEach-Object** cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="f227e-105">Vous pouvez l’utiliser pour effectuer des tâches complexes.</span><span class="sxs-lookup"><span data-stu-id="f227e-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="f227e-106">Une situation où elle peut être utile est la manipulation de données pour les rendre plus exploitables.</span><span class="sxs-lookup"><span data-stu-id="f227e-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="f227e-107">Par exemple, la classe Win32_LogicalDisk de WMI permet de retourner des informations d’espace libre sur chaque disque local.</span><span class="sxs-lookup"><span data-stu-id="f227e-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="f227e-108">Toutefois, les données retournées sont exprimées en octets, ce qui rend leur lecture difficile :</span><span class="sxs-lookup"><span data-stu-id="f227e-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="f227e-109">Il est possible de convertir la valeur FreeSpace en mégaoctets, en divisant chaque valeur par 1024 à deux reprises. Après la première division, les données sont exprimées en kilo-octets (Ko) et, après la seconde division, en mégaoctets (Mo).</span><span class="sxs-lookup"><span data-stu-id="f227e-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="f227e-110">Vous pouvez faire cela dans un bloc de script ForEach-Object en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f227e-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="f227e-111">Malheureusement, la sortie est désormais constituée de données sans étiquette associée.</span><span class="sxs-lookup"><span data-stu-id="f227e-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="f227e-112">De telles propriétés WMI étant en lecture seule, vous ne pouvez pas convertir FreeSpace directement.</span><span class="sxs-lookup"><span data-stu-id="f227e-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="f227e-113">Si vous tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f227e-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="f227e-114">Vous obtenez un message d’erreur :</span><span class="sxs-lookup"><span data-stu-id="f227e-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="f227e-115">Vous pouvez réorganiser les données à l’aide de techniques avancées, mais une approche plus simple consiste à créer un nouvel objet à l’aide de l’applet de commande **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="f227e-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>