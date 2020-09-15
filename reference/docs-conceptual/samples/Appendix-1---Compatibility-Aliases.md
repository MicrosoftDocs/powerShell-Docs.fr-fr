---
ms.date: 08/03/2020
keywords: powershell,applet de commande
title: 'Annexe 1 : Alias de compatibilité'
ms.openlocfilehash: e5bd170fea6b6109d2ef4fd58863d6cc8a0e3ae1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758497"
---
# <a name="appendix-1---compatibility-aliases"></a>Annexe 1 - Alias de compatibilité

PowerShell a plusieurs alias qui permettent aux utilisateurs **UNIX** et **cmd.exe** d’utiliser des commandes familières.
Les commandes, ainsi que leurs applets de commande PowerShell et alias PowerShell associés, sont indiqués dans le tableau suivant :

|            commande cmd.exe            | Commande UNIX | Applet de commande PowerShell | Alias PowerShell |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| **cd**, **chdir**                     | **cd**       | `Set-Location`    | `sl`             |
| **cls**                               | **clear**    | `Clear-Host`      | `cls`            |
| **copy**                              | **cp**       | `Copy-Item`       | `cpi`            |
| **del**, **erase**, **rd**, **rmdir** | **rm**       | `Remove-Item`     | `ri`             |
| **dir**                               | **ls**       | `Get-ChildItem`   | `gci`            |
| **echo**                              | **echo**     | `Write-Output`    | `write`          |
| **md**                                | **mkdir**    | `New-Item`        | `ni`             |
| **move**                              | **mv**       | `Move-Item`       | `mi`             |
| **popd**                              | **popd**     | `Pop-Location`    | `popd`           |
| **pushd**                             | **pushd**    | `Push-Location`   | `pushd`          |
| **ren**                               | **mv**       | `Rename-Item`     | `rni`            |
| **type**                              | **cat**      | `Get-Content`     | `gc`             |

Pour trouver les alias PowerShell, utilisez l’applet de commande [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias). Pour afficher les alias d’une applet de commande, utilisez le paramètre **Definition** et spécifiez le nom de l’applet de commande.
Ou, pour trouver le nom d’applet de commande d’un alias, utilisez le paramètre **Name** et spécifiez l’alias.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
