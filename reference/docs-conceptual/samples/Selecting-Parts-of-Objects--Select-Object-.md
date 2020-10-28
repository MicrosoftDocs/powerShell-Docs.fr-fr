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
# <a name="selecting-parts-of-objects-select-object"></a>Sélection de parties d’objets (Select-Object)

Vous pouvez utiliser la cmdlet `Select-Object` pour créer des objets PowerShell personnalisés qui contiennent des propriétés sélectionnées à partir des objets que vous utilisez pour les créer. Pour créer un nouvel objet qui inclut uniquement les propriétés **Nom** et **FreeSpace** de la classe WMI **Win32_LogicalDisk** , tapez la commande suivante :

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

Avec `Select-Object` vous pouvez créer des propriétés calculées. Vous pouvez ainsi afficher **FreeSpace** en gigaoctets plutôt qu’en octets.

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
