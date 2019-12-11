---
ms.date: 01/17/2019
keywords: dsc,powershell,configuration,setup
title: Redémarrer un nœud
ms.openlocfilehash: 22c63fab9b6646f522f8531b46a43a94ff883552
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954026"
---
# <a name="reboot-a-node"></a>Redémarrer un nœud

> [!NOTE]
> Cette rubrique explique comment redémarrer un nœud. Pour que le redémarrage réussisse, les paramètres **ActionAfterReboot** et **RebootNodeIfNeeded** du Gestionnaire de configuration local doivent être configurés correctement.
> Pour en savoir plus sur les paramètres du Gestionnaire de configuration local, consultez [Configurer le Gestionnaire de configuration local](../managing-nodes/metaConfig.md) ou [Configurer le Gestionnaire de configuration local (v4)](../managing-nodes/metaConfig4.md).

Les nœuds peuvent être redémarrés à partir d’une ressource, à l’aide de l’indicateur `$global:DSCMachineStatus`. L’affectation de la valeur `1` à cet indicateur dans la fonction `Set-TargetResource` force le Gestionnaire de configuration local à redémarrer le nœud juste après la méthode **Set** de la ressource actuelle. Grâce à cet indicateur, la ressource **PendingReboot** dans le module de la ressource DSC [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) détecte si un redémarrage est en attente en dehors de DSC.

Vos [configurations](configurations.md) peuvent effectuer des étapes qui nécessitent un redémarrage du nœud, par exemple :

- Mises à jour Windows
- Installation de logiciel
- Renommages de fichiers
- Renommage d’ordinateur

La ressource **PendingReboot** vérifie des emplacements d’ordinateurs spécifiques pour déterminer si un redémarrage est en attente. Si le nœud nécessite un redémarrage en dehors de DSC, la ressource **PendingReboot** affecte la valeur `1` à l’indicateur `$global:DSCMachineStatus` pour forcer un redémarrage et résoudre la condition en attente.

> [!NOTE]
> Toute ressource DSC peut forcer le Gestionnaire de configuration local à redémarrer le nœud en définissant cet indicateur dans la fonction `Set-TargetResource`. Pour plus d’informations, consultez [Écriture d’une ressource DSC personnalisée avec MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Syntaxe

```
PendingReboot [String] #ResourceName
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
| SkipComponentBasedServicing | Ignorer les redémarrages déclenchés par le composant des services à base de composants. |
| SkipWindowsUpdate | Ignorer les redémarrages déclenchés par Windows Update.|
| SkipPendingFileRename | Ignorer les redémarrages en attente dus à un renommage de fichiers. |
| SkipCcmClientSDK | Ignorer les redémarrages déclenchés par le client ConfigMgr. |
| SkipComputerRename | Ignorer les redémarrages déclenchés par un renommage d’ordinateur. |
| PSDSCRunAsCredential | Prise en charge dans v5. Exécute la ressource en tant que l’utilisateur spécifié. |
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`. Pour plus d’informations, consultez [Utilisation de DependsOn](resource-depends-on.md).|

## <a name="example"></a>Exemple

L’exemple suivant installe Microsoft Exchange à l’aide de la ressource [xExchange](https://github.com/PowerShell/xExchange).
Tout au long de l’installation, la ressource **PendingReboot** est utilisée pour redémarrer le nœud.

> [!NOTE]
> Cet exemple nécessite les informations d’identification d’un compte disposant des droits nécessaires pour ajouter un serveur Exchange à la forêt. Pour plus d’informations sur l’utilisation des informations d’identification dans DSC, consultez [Gestion des informations d’identification dans DSC](../configurations/configDataCredentials.md).

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
    Import-DscResource -Module ComputerManagementDsc

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
        PendingReboot BeforeExchangeInstall
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
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> Cet exemple part du principe que vous avez configuré votre Gestionnaire de configuration local de façon à autoriser les redémarrages et à poursuivre la configuration après un redémarrage.

## <a name="where-to-download"></a>Emplacement de téléchargement

Vous pouvez télécharger les ressources utilisées dans cette rubrique aux emplacements suivants, ou à l’aide de PowerShell Gallery.

- [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc)
- [xExchange](https://github.com/PowerShell/xExchange)
