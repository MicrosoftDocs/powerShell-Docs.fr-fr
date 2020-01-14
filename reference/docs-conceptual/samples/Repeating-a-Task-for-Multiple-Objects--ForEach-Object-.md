---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Répétition d’une tâche pour plusieurs objets ForEach Object
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736877"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="d85f2-103">Répétition d’une tâche pour plusieurs objets (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="d85f2-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="d85f2-104">La cmdlet `ForEach-Object` utilise des blocs de script et le descripteur `$_` pour l’objet de pipeline actuel, afin de vous permettre d’exécuter une commande sur chaque objet figurant dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d85f2-104">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="d85f2-105">Vous pouvez l’utiliser pour effectuer des tâches complexes.</span><span class="sxs-lookup"><span data-stu-id="d85f2-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="d85f2-106">Une situation où elle peut être utile est la manipulation de données pour les rendre plus exploitables.</span><span class="sxs-lookup"><span data-stu-id="d85f2-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="d85f2-107">Par exemple, la classe **Win32_LogicalDisk** de VMI peut être utilisée pour renvoyer des informations sur l’espace libre pour chaque disque local.</span><span class="sxs-lookup"><span data-stu-id="d85f2-107">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="d85f2-108">Toutefois, les données retournées sont exprimées en octets, ce qui rend leur lecture difficile :</span><span class="sxs-lookup"><span data-stu-id="d85f2-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="d85f2-109">Nous pouvons convertir la valeur **FreeSpace** en mégaoctets en divisant chaque valeur par 1 Mo.</span><span class="sxs-lookup"><span data-stu-id="d85f2-109">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="d85f2-110">Vous pouvez faire cela dans un bloc de script `ForEach-Object` en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d85f2-110">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="d85f2-111">Malheureusement, la sortie est désormais constituée de données sans étiquette associée.</span><span class="sxs-lookup"><span data-stu-id="d85f2-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="d85f2-112">De telles propriétés WMI étant en lecture seule, vous ne pouvez pas convertir **FreeSpace** directement.</span><span class="sxs-lookup"><span data-stu-id="d85f2-112">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="d85f2-113">Si vous tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d85f2-113">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="d85f2-114">Vous obtenez un message d’erreur :</span><span class="sxs-lookup"><span data-stu-id="d85f2-114">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="d85f2-115">Vous pouvez réorganiser les données à l’aide de techniques avancées, mais une approche plus simple consiste à créer un nouvel objet à l’aide de `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="d85f2-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
