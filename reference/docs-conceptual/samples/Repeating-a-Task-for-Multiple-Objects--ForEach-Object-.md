---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Répétition d’une tâche pour plusieurs objets ForEach Object
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736877"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Répétition d’une tâche pour plusieurs objets (ForEach-Object)

La cmdlet `ForEach-Object` utilise des blocs de script et le descripteur `$_` pour l’objet de pipeline actuel, afin de vous permettre d’exécuter une commande sur chaque objet figurant dans le pipeline. Vous pouvez l’utiliser pour effectuer des tâches complexes.

Une situation où elle peut être utile est la manipulation de données pour les rendre plus exploitables. Par exemple, la classe **Win32_LogicalDisk** de VMI peut être utilisée pour renvoyer des informations sur l’espace libre pour chaque disque local. Toutefois, les données retournées sont exprimées en octets, ce qui rend leur lecture difficile :

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

Nous pouvons convertir la valeur **FreeSpace** en mégaoctets en divisant chaque valeur par 1 Mo. Vous pouvez faire cela dans un bloc de script `ForEach-Object` en tapant ce qui suit :

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

Malheureusement, la sortie est désormais constituée de données sans étiquette associée. De telles propriétés WMI étant en lecture seule, vous ne pouvez pas convertir **FreeSpace** directement. Si vous tapez ce qui suit :

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

Vous obtenez un message d’erreur :

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

Vous pouvez réorganiser les données à l’aide de techniques avancées, mais une approche plus simple consiste à créer un nouvel objet à l’aide de `Select-Object`.
