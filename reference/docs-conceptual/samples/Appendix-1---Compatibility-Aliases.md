---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: 'Annexe 1 : Alias de compatibilité'
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030332"
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
