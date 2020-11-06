---
ms.date: 08/11/2020
keywords: dsc,powershell,configuration,installation
title: Appel direct de méthodes de ressources DSC
description: L’applet de commande Invoke-DscResource peut être utilisée pour appeler les fonctions ou méthodes d’une ressource DSC. Elle peut être utilisée par des tiers qui veulent utiliser des ressources DSC, ou comme un outil très utile lors du développement de ressources.
ms.openlocfilehash: 5ccf0f589b60cef4ec197d1e0a583af9ed60d5e7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650997"
---
# <a name="calling-dsc-resource-methods-directly"></a>Appel direct de méthodes de ressources DSC

> S’applique à : Windows PowerShell 5.0

Vous pouvez utiliser l’applet de commande [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) pour appeler directement les fonctions ou méthodes d’une ressource DSC (les fonctions `Get-TargetResource`, `Set-TargetResource` et `Test-TargetResource` d’une ressource basée sur MOF ou les méthodes **Get** , **Set** et **Test** d’une ressource basée sur la classe). Elle peut être utilisée par des tiers qui veulent utiliser des ressources DSC, ou comme un outil très utile lors du développement de ressources.

> [!NOTE]
> Dans PowerShell 7.0+, `Invoke-DscResource` ne prend plus en charge l’appel des ressources DSC WMI. Sont incluses les ressources **File** et **Log** dans **PSDesiredStateConfiguration**.

Cette applet de commande est généralement utilisée avec une propriété de métaconfiguration `refreshMode = 'Disabled'`, mais vous pouvez l’utiliser quelle que soit la valeur de **refreshMode**.

Lors de l’appel de l’applet de commande `Invoke-DscResource`, vous spécifiez la méthode ou fonction à appeler à l’aide du paramètre **Method**. Vous spécifiez les propriétés de la ressource en passant une table de hachage comme valeur du paramètre **Property**.

Voici quelques exemples d’appels directs de méthodes de ressources :

## <a name="ensure-a-file-is-present"></a>S’assurer de la présence d’un fichier

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Tester la présence d’un fichier

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>Obtenir le contenu du fichier

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

> [!NOTE]
> l’appel direct de méthodes de ressources composites n’est pas pris en charge. Appelez plutôt les ressources sous-jacentes qui forment la ressource composite.

## <a name="see-also"></a>Voir aussi

- [Écriture d’une ressource DSC personnalisée avec MOF](../resources/authoringResourceMOF.md)
- [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](../resources/authoringResourceClass.md)
- [Débogage des ressources DSC](../troubleshooting/debugResource.md)
