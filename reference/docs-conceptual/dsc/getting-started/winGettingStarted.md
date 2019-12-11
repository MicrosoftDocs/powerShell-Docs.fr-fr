---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Prendre en main la fonctionnalité DSC (Desired State Configuration) pour Windows
ms.openlocfilehash: a9346b96693acdbad9bacbd4b6ca85971e17a3d1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417766"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Prendre en main la fonctionnalité DSC (Desired State Configuration) pour Windows

Cette rubrique explique comment prendre en main la fonctionnalité DSC (Desired State Configuration) PowerShell pour Windows.
Pour obtenir des informations générales sur DSC, consultez [Prendre en main la fonctionnalité DSC (Desired State Configuration) Windows PowerShell](../overview/overview.md).

## <a name="supported-windows-operation-system-versions"></a>Versions du système d’exploitation Windows prises en charge

Les versions suivantes sont prises en charge :

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

La référence SKU de produit autonome [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) ne contient pas d’implémentation de l’état de configuration souhaité, de sorte qu’elle ne peut pas être gérée par PowerShell DSC ni par la configuration de l’état Azure Automation.

## <a name="installing-dsc"></a>Installation de DSC

La fonctionnalité Desired State Configuration de PowerShell est incluse dans Windows et mise à jour par le biais de Windows Management Framework.
La version la plus récente est [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

> [!NOTE]
> Vous n’avez pas besoin d’activer la fonctionnalité « DSC-Service » de Windows Server pour gérer un ordinateur à l’aide de DSC.
> Cette fonctionnalité est uniquement nécessaire lors de la création d’une instance de serveur Pull Windows.

## <a name="using-dsc-for-windows"></a>Utilisation de DSC pour Windows

Les sections suivantes expliquent comment créer et exécuter des configurations DSC sur les ordinateurs Windows.

### <a name="creating-a-configuration-mof-document"></a>Création d’un document MOF de configuration

Le mot clé Windows PowerShell « Configuration » permet de créer une configuration.
Suivez les étapes décrites ci-dessous pour créer un document de configuration à l’aide de Windows PowerShell.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Définissez une configuration et créez le document de configuration :

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a>Installer un module contenant des ressources DSC

La fonctionnalité Desired State Configuration de Windows PowerShell inclut des modules intégrés contenant des ressources DSC.
Vous pouvez également charger des modules à partir de sources externes, telles que PowerShell Gallery, à l’aide des cmdlets PowerShellGet.

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a>Appliquer la configuration à l’ordinateur

La configuration de documents (fichiers MOF) peut être appliquée à l’ordinateur à l’aide de la cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a>Obtient l’état actuel de la configuration

La cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) interroge l’état actuel de l’ordinateur et retourne les valeurs actuelles de la configuration.

`Get-DscConfiguration`

La cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) retourne la méta-configuration actuelle appliquée à l’ordinateur.

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a>Supprimer la configuration actuelle d’un ordinateur

[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a>Configurer les paramètres dans le Configuration Manager Manager local

Appliquez un fichier MOF de méta-configuration à l’ordinateur à l’aide de la cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).
Doit spécifier le chemin du fichier MOF de métaconfiguration.

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Fichiers journaux de la fonctionnalité Desired State Configuration de Windows PowerShell

Les journaux pour DSC sont écrits dans le journal des événements Windows dans le chemin d’accès `Microsoft-Windows-Dsc/Operational`.
Des journaux supplémentaires à des fins de débogage peuvent être activés en suivant les étapes décrites dans [Où se trouvent les journaux des événements DSC](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).
