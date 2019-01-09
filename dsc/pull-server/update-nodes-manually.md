---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Mettre à jour des nœuds à partir d’un serveur Pull
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401126"
---
# <a name="update-nodes-from-a-pull-server"></a>Mettre à jour des nœuds à partir d’un serveur Pull

Les sections ci-dessous supposent que vous avez déjà configuré un serveur collecteur. Si vous n’avez pas configuré votre serveur collecteur, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations, ressources et même signaler son état. Cet article montre comment charger des ressources afin qu’ils soient disponibles pour être téléchargé et configurer les clients pour télécharger automatiquement les ressources. Lorsque le nœud reçoit une Configuration attribuée, via **extraire** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la Configuration à partir de l’emplacement spécifié dans le Gestionnaire de configuration local.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>À l’aide de l’applet de commande Update-DSCConfiguration

À compter de PowerShell 5.0, le [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) applet de commande force un nœud pour mettre à jour sa configuration à partir du serveur collecteur configuré dans le Gestionnaire de configuration local.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>À l’aide de Invoke-CIMMethod

Dans PowerShell 4.0, vous pouvez forcer manuellement d’un Client collecteur à mettre à jour sa Configuration à l’aide [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). L’exemple suivant crée une session CIM avec les informations d’identification spécifiées, appelle la méthode CIM appropriée et supprime la session.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Voir aussi

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
