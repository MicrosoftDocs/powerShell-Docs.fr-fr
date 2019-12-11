---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Sélection de parties d’objets Select Object
ms.openlocfilehash: 4d4c89f0b5103e4701a3af3cd07fcd7c8f1c697f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030108"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="e51e2-103">Sélection de parties d’objets (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="e51e2-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="e51e2-104">L’applet de commande **Select-Object** permet de créer des objets Windows PowerShell personnalisés qui contiennent des propriétés sélectionnées à partir des objets que vous utilisez pour les créer.</span><span class="sxs-lookup"><span data-stu-id="e51e2-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="e51e2-105">Pour créer un objet qui inclut uniquement les propriétés Name et FreeSpace de la classe WMI de Win32_LogicalDisk, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e51e2-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="e51e2-106">Après avoir émis cette commande, vous ne pouvez pas voir le type des données mais, si vous canalisez le résultat de l’applet de commande Select-Object vers l’applet de commande Get-Member, vous pouvez constater que vous disposez d’un nouveau type d’objet, PSCustomObject :</span><span class="sxs-lookup"><span data-stu-id="e51e2-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

<span data-ttu-id="e51e2-107">L’applet de commande Select-Object a de nombreuses usages.</span><span class="sxs-lookup"><span data-stu-id="e51e2-107">Select-Object has many uses.</span></span> <span data-ttu-id="e51e2-108">L’un d’eux consiste à répliquer des données que vous pouvez ensuite modifier.</span><span class="sxs-lookup"><span data-stu-id="e51e2-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="e51e2-109">Nous pouvons désormais gérer le problème que nous avons rencontré dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="e51e2-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="e51e2-110">Nous pouvons mettre à jour la valeur de FreeSpace dans nos objets nouvellement créés, et la sortie inclut l’étiquette descriptive :</span><span class="sxs-lookup"><span data-stu-id="e51e2-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
