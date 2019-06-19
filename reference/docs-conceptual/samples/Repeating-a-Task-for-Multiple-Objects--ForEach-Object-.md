---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Répétition d’une tâche pour plusieurs objets ForEach Object
ms.openlocfilehash: 1442507c4213476f65df3401c1021f8d0fc31956
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030802"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Répétition d’une tâche pour plusieurs objets (ForEach-Object)

La cmdlet **ForEach-Object** utilise des blocs de script et le descripteur `$_` pour l’objet de pipeline actuel, afin de vous permettre d’exécuter une commande sur chaque objet figurant dans le pipeline. Vous pouvez l’utiliser pour effectuer des tâches complexes.

Une situation où elle peut être utile est la manipulation de données pour les rendre plus exploitables. Par exemple, la classe Win32_LogicalDisk de WMI permet de retourner des informations d’espace libre sur chaque disque local. Toutefois, les données retournées sont exprimées en octets, ce qui rend leur lecture difficile :

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Il est possible de convertir la valeur FreeSpace en mégaoctets, en divisant chaque valeur par 1024 à deux reprises. Après la première division, les données sont exprimées en kilo-octets (Ko) et, après la seconde division, en mégaoctets (Mo). Vous pouvez faire cela dans un bloc de script ForEach-Object en tapant ce qui suit :

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Malheureusement, la sortie est désormais constituée de données sans étiquette associée. De telles propriétés WMI étant en lecture seule, vous ne pouvez pas convertir FreeSpace directement. Si vous tapez ce qui suit :

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Vous obtenez un message d’erreur :

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Vous pouvez réorganiser les données à l’aide de techniques avancées, mais une approche plus simple consiste à créer un nouvel objet à l’aide de l’applet de commande **Select-Object**.
