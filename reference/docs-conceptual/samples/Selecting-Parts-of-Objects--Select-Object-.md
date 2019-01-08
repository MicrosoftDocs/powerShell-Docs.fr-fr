---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Sélection de parties d’objets Select Object
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402036"
---
# <a name="selecting-parts-of-objects-select-object"></a>Sélection de parties d’objets (Select-Object)

L’applet de commande **Select-Object** permet de créer des objets Windows PowerShell personnalisés qui contiennent des propriétés sélectionnées à partir des objets que vous utilisez pour les créer. Pour créer un objet qui inclut uniquement les propriétés Name et FreeSpace de la classe WMI de Win32_LogicalDisk, tapez la commande suivante :

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Après avoir émis cette commande, vous ne pouvez pas voir le type des données mais, si vous canalisez le résultat de l’applet de commande Select-Object vers l’applet de commande Get-Member, vous pouvez constater que vous disposez d’un nouveau type d’objet, PSCustomObject :

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

L’applet de commande Select-Object a de nombreuses usages. L’un d’eux consiste à répliquer des données que vous pouvez ensuite modifier. Nous pouvons désormais gérer le problème que nous avons rencontré dans la section précédente. Nous pouvons mettre à jour la valeur de FreeSpace dans nos objets nouvellement créés, et la sortie inclut l’étiquette descriptive :

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```