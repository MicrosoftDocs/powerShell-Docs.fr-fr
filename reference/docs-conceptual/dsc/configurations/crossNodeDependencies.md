---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Spécification de dépendances entre nœuds
description: DSC fournit des ressources spéciales, utilisées dans les configurations pour spécifier les dépendances sur les configurations sur d’autres nœuds.
ms.openlocfilehash: a9fc09af922839b37db476c24c113efc5e3e8cb1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658495"
---
# <a name="specifying-cross-node-dependencies"></a>Spécification de dépendances entre nœuds

> S’applique à : Windows PowerShell 5.0

DSC fournit des ressources spéciales, **WaitForAll** , **WaitForAny** et **WaitForSome** , qui peuvent être utilisées dans les configurations pour spécifier les dépendances sur les configurations sur d’autres nœuds. Le comportement de ces ressources est le suivant :

- **WaitForAll**  : réussit si la ressource spécifiée est dans l’état souhaité sur tous les nœuds cibles définis dans la propriété **NodeName**.
- **WaitForAny**  : réussit si la ressource spécifiée est dans l’état souhaité sur au moins l’un des nœuds cibles définis dans la propriété **NodeName**.
- **WaitForSome**  : spécifie une propriété **NodeCount** en plus d’une propriété **NodeName**. La ressource réussit si elle est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount** ) défini par la propriété **NodeName**.

## <a name="syntax"></a>Syntax

Les ressources **WaitForAll** et **WaitForAny** partagent la même syntaxe. Dans l’exemple ci-dessous, remplacez `<ResourceType>` par **WaitForAny** ou **WaitForAll**. Comme pour le mot clé **DependsOn** , vous devrez appliquer au nom le format `[ResourceType]ResourceName`. Si la ressource appartient à une [configuration](configurations.md) distincte, incluez **ConfigurationName** dans la chaîne mise en forme `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`. **NodeName** représente l’ordinateur ou le nœud sur lequel la ressource actuelle doit attendre.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

La ressource **WaitForSome** affiche une syntaxe similaire à l’exemple ci-dessus, mais ajoute la clé **NodeCount**. **NodeCount** indique le nombre de nœuds sur lesquels la ressource actuelle doit attendre.

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

Toutes les ressources **WaitForXXXX** partagent les clés de syntaxe suivantes.

|       Property       |                                                                           Description                                                                           |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RetryIntervalSec     | Le nombre de secondes avant la nouvelle tentative. Le minimum est 1.                                                                                                            |
| RetryCount           | Le nombre maximum de nouvelles tentatives.                                                                                                                           |
| ThrottleLimit        | Le nombre de machines à connecter simultanément. La valeur par défaut est `New-CimSession` par défaut.                                                                              |
| DependsOn            | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Pour plus d’informations, consultez [DependsOn](resource-depends-on.md). |
| PsDscRunAsCredential | Voir [Exécution de DSC avec les informations d’identification de l’utilisateur](./runAsUser.md)                                                                                                           |

## <a name="using-waitforxxxx-resources"></a>Utilisation de ressources WaitForXXXX

Chaque ressource **WaitForXXXX** attend que les ressources spécifiées soient terminées sur le nœud spécifié.
Les autres ressources dans la même configuration peuvent ensuite *dépendre* de la ressource **WaitForXXXX** à l’aide de la clé **DependsOn**.

Par exemple, dans la configuration suivante, le nœud cible attend que la ressource **xADDomain** se termine sur le nœud **MyDC** avec un nombre maximal de 30 tentatives, à des intervalles de 15 secondes, avant que le nœud cible ne puisse joindre le domaine.

Par défaut, les ressources **WaitForXXX** effectuent une tentative, puis échouent. Même si ce n’est pas obligatoire, vous spécifiez généralement les valeurs **RetryCount** et **RetryIntervalSec**.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

Lorsque vous compilez la configuration, deux fichiers « .mof » sont générés. Appliquez ces deux fichiers « .mof » aux nœuds cibles à l’aide de l’applet de commande [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)

> [!NOTE]
> Les ressources **WaitForXXX** utilisent Windows Remote Management pour vérifier l’état d’autres nœuds. Pour plus d’informations sur la configuration requise des ports et de la sécurité pour WinRM, consultez [Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell](/powershell/scripting/learn/remoting/winrmsecurity).

## <a name="see-also"></a>Voir aussi

- [Configurations DSC](configurations.md)
- [Utiliser des dépendances de ressources](resource-depends-on.md)
- [Ressources DSC](../resources/resources.md)
- [Configuration de Local Configuration Manager](../managing-nodes/metaConfig.md)
