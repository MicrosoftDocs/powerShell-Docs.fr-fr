---
ms.date: 1/17/2019
keywords: dsc,powershell,configuration,setup
title: Redémarrez un nœud
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678353"
---
# <a name="reboot-a-node"></a>Redémarrez un nœud

> [!NOTE]
> Cette rubrique explique comment redémarrer un nœud. Dans l’ordre du redémarrage réussir le **ActionAfterReboot** et **RebootNodeIfNeeded** paramètres LCM doivent être configurés correctement.
> Pour en savoir plus sur les paramètres de gestionnaire de Configuration Local, consultez [configurer le Gestionnaire de Configuration Local](../managing-nodes/metaConfig.md), ou [configurer le Gestionnaire de Configuration Local (v4)](../managing-nodes/metaConfig4.md).

Nœuds peuvent être redémarrées à partir d’au sein d’une ressource, à l’aide de la `$global:DSCMachineStatus` indicateur. Définition de cet indicateur `1` dans le `Set-TargetResource` fonction force le LCM pour redémarrer le nœud directement après le **définir** méthode de la ressource actuelle. À l’aide de cet indicateur, la **xPendingReboot** ressources détecte si un redémarrage est en attente en dehors de DSC.

Votre [configurations](configurations.md) peut effectuer des étapes qui requièrent le nœud à redémarrer. Cela peut inclure des éléments tels que :

- Windows : Mises à jour
- Installation du logiciel
- Fichier renomme
- Changement de nom ordinateur

Le **xPendingReboot** ressource vérifie les emplacements des ordinateurs spécifiques pour déterminer si un redémarrage est en attente. Si le nœud nécessite un redémarrage en dehors de DSC, le **xPendingReboot** ensembles de ressources le `$global:DSCMachineStatus` indicateur `1` forcer un redémarrage et la résolution de la condition en attente.

> [!NOTE]
> N’importe quelle ressource DSC peut indiquer le LCM pour redémarrer le nœud en définissant cet indicateur dans le `Set-TargetResource` (fonction). Pour plus d’informations, consultez [écriture d’une ressource DSC personnalisée avec MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Syntaxe

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>Propriétés

| Propriété | Description |
| --- | --- |
| Name| Paramètre obligatoire qui doit être unique pour chaque instance de la ressource au sein d’une configuration.|
| SkipComponentBasedServicing | Redémarrages de Skip déclenchées par le composant Component Based Servicing. |
| SkipWindowsUpdate | Redémarrages de Skip déclenchées par la mise à jour de Windows.|
| SkipPendingFileRename | Ignorer les redémarrages de changement de nom de fichier en attente. |
| SkipCcmClientSDK | Redémarrages de Skip déclenchées par le client ConfigMgr. |
| SkipComputerRename | Skip redémarre déclenchées par les affectations de l’ordinateur. |
| PSDSCRunAsCredential | Prise en charge dans v5. Exécute la ressource en tant que l’utilisateur spécifié. |
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`. Pour plus d’informations, consultez [à l’aide de DependsOn](resource-depends-on.md)|

## <a name="example"></a>Exemple

L’exemple suivant installe à l’aide de Microsoft Exchange le [xExchange](https://github.com/PowerShell/xExchange) ressource.
Tout au long de l’installation, le **xPendingReboot** ressource est utilisée pour redémarrer le nœud.

> [!NOTE]
> Cet exemple nécessite les informations d’identification d’un compte disposant des droits nécessaires pour ajouter un serveur Exchange à la forêt. Pour plus d’informations sur l’utilisation des informations d’identification dans DSC, consultez [gère les informations d’identification dans DSC](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> Cet exemple suppose que vous avez configuré votre gestionnaire de Configuration Local pour autoriser les redémarrages et poursuivre la configuration après un redémarrage.

## <a name="where-to-download"></a>Emplacement de téléchargement

Vous pouvez télécharger les ressources utilisées dans cette rubrique aux emplacements suivants, ou à l’aide de PowerShell gallery.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
