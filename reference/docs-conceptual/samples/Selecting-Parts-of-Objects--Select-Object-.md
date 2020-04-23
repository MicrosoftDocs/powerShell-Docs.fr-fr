---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Sélection de parties d’objets Select Object
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737166"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="bd144-103">Sélection de parties d’objets (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="bd144-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="bd144-104">Vous pouvez utiliser la cmdlet `Select-Object` pour créer des objets PowerShell personnalisés qui contiennent des propriétés sélectionnées à partir des objets que vous utilisez pour les créer.</span><span class="sxs-lookup"><span data-stu-id="bd144-104">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="bd144-105">Pour créer un nouvel objet qui inclut uniquement les propriétés **Nom** et **FreeSpace** de la classe WMI **Win32_LogicalDisk**, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="bd144-105">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="bd144-106">Avec `Select-Object` vous pouvez créer des propriétés calculées.</span><span class="sxs-lookup"><span data-stu-id="bd144-106">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="bd144-107">Vous pouvez ainsi afficher **FreeSpace** en gigaoctets plutôt qu’en octets.</span><span class="sxs-lookup"><span data-stu-id="bd144-107">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  Select-Object -Property Name, @{
    label='FreeSpace'
    expression={($_.FreeSpace/1GB).ToString('F2')}
  }
```

```Output
Name    FreeSpace
----    ---------
C:      47.18
```
