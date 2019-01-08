---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Appel direct de méthodes de ressources DSC
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401233"
---
# <a name="calling-dsc-resource-methods-directly"></a>Appel direct de méthodes de ressources DSC

>S'applique à : Windows PowerShell 5.0

Vous pouvez utiliser l’applet de commande [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) pour appeler directement les fonctions ou méthodes d’une ressource DSC (les fonctions **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource** d’une ressource basée sur MOF, ou les méthodes **Get**, **Set** et **Test** d’une ressource basée sur la classe).
Elle peut être utilisée par des tiers qui veulent utiliser des ressources DSC, ou comme un outil très utile lors du développement de ressources.

Cette applet de commande est généralement utilisée avec une propriété de métaconfiguration `refreshMode = 'Disabled'`, mais vous pouvez l’utiliser quelle que soit la valeur de **refreshMode**.

Lors de l’appel de l’applet de commande **Invoke-DscResource**, vous spécifiez la méthode ou fonction à appeler à l’aide du paramètre **Method**. Vous spécifiez les propriétés de la ressource en passant une table de hachage comme valeur du paramètre **Property**.

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

>**Remarque :** Appeler directement les méthodes de ressources composites n’est pas pris en charge. Appelez plutôt les ressources sous-jacentes qui forment la ressource composite.

## <a name="see-also"></a>Voir aussi
- [Écriture d’une ressource DSC personnalisée avec MOF](../resources/authoringResourceMOF.md)
- [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](../resources/authoringResourceClass.md)
- [Débogage des ressources DSC](../troubleshooting/debugResource.md)