---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Mettre à jour des nœuds à partir d’un serveur Pull
ms.openlocfilehash: 516e50b0c39e4747a123307cb3f5e25259ac7ce5
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417719"
---
# <a name="update-nodes-from-a-pull-server"></a>Mettre à jour des nœuds à partir d’un serveur Pull

Les sections ci-dessous supposent que vous avez déjà configuré un serveur Pull. Si vous n’avez pas configuré votre serveur Pull, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état. Cet article montre comment charger des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources. Lorsque le nœud reçoit une configuration attribuée, via un serveur **Pull** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la configuration depuis l’emplacement spécifié dans le gestionnaire de configuration local (LCM).

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Utilisation de l’applet de commande Update-DSCConfiguration

À compter de PowerShell 5.0, l’applet de commande [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) force un nœud à mettre à jour sa configuration à partir du serveur Pull configuré dans le gestionnaire de configuration local.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Utilisation d’Invoke-CIMMethod

Dans PowerShell 4.0, vous pouvez forcer manuellement un client Pull à mettre à jour sa configuration à l’aide d’[Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). L’exemple suivant crée une session CIM avec les informations d’identification spécifiées, appelle la méthode CIM appropriée, puis supprime la session.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Voir aussi

[PerformRequiredConfigurationChecks](/powershell/scripting/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
