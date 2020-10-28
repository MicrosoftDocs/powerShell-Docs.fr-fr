---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Sélection de parties d’objets Select Object
description: Vous pouvez utiliser l’applet de commande `Select-Object` pour créer des objets PowerShell personnalisés qui contiennent des propriétés sélectionnées à partir des objets du pipeline.
ms.openlocfilehash: 92635ac54ea1469739bcb228c5e9a0a8dbfc648b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501029"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="332f7-104">Sélection de parties d’objets (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="332f7-104">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="332f7-105">Vous pouvez utiliser la cmdlet `Select-Object` pour créer des objets PowerShell personnalisés qui contiennent des propriétés sélectionnées à partir des objets que vous utilisez pour les créer.</span><span class="sxs-lookup"><span data-stu-id="332f7-105">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="332f7-106">Pour créer un nouvel objet qui inclut uniquement les propriétés **Nom** et **FreeSpace** de la classe WMI **Win32_LogicalDisk** , tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="332f7-106">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="332f7-107">Avec `Select-Object` vous pouvez créer des propriétés calculées.</span><span class="sxs-lookup"><span data-stu-id="332f7-107">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="332f7-108">Vous pouvez ainsi afficher **FreeSpace** en gigaoctets plutôt qu’en octets.</span><span class="sxs-lookup"><span data-stu-id="332f7-108">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

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
