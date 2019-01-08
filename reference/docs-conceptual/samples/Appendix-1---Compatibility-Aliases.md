---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: 'Annexe 1 : Alias de compatibilité'
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402035"
---
# <a name="appendix-1---compatibility-aliases"></a>Annexe 1 - Alias de compatibilité

Windows PowerShell dispose de plusieurs alias de transition qui permettent aux utilisateurs d’UNIX et de Cmd d’utiliser des noms de commande familiers dans Windows PowerShell. Les alias courants sont répertoriés dans le tableau ci-dessous, ainsi que la commande Windows PowerShell sous-jacente, et l’alias Windows PowerShell standard, s’il en existe.

Pour trouver la commande Windows PowerShell vers laquelle pointe un alias, dans Windows PowerShell utilisez l’applet de commande Get-Alias. Par exemple, tapez **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Commande CMD|Commande UNIX|Commande PS|Alias PS|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host** (fonction)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|