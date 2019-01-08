---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Spécification de dépendances entre nœuds
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401162"
---
# <a name="specifying-cross-node-dependencies"></a>Spécification de dépendances entre nœuds

> S'applique à : Windows PowerShell 5.0

DSC fournit des ressources spéciales, **WaitForAll**, **WaitForAny** et **WaitForSome**, qui peuvent être utilisées dans les configurations pour spécifier les dépendances sur les configurations sur d’autres nœuds. Le comportement de ces ressources est le suivant :

- **WaitForAll**: Réussit si la ressource spécifiée est dans l’état souhaité sur tous les nœuds cibles définis dans le **NodeName** propriété.
- **WaitForAny**: Réussit si la ressource spécifiée est dans l’état souhaité sur au moins un des nœuds cibles définis dans le **NodeName** propriété.
- **WaitForSome**: Spécifie un **NodeCount** propriété outre un **NodeName** propriété. La ressource réussit si elle est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**.

## <a name="syntax"></a>Syntaxe

Le **WaitForAll** et **WaitForAny** ressources partagent la même syntaxe. Remplacez \<ResourceType\> dans l’exemple ci-dessous, avec soit **WaitForAny** ou **WaitForAll**.
Comme le **DependsOn** mot clé, vous devez mettre en forme le nom en tant que « [ResourceType] ResourceName ». Si la ressource appartient à un distinct [Configuration](configurations.md), incluent le **ConfigurationName** dans la chaîne mise en forme « [ResourceType] ResourceName :: [ConfigurationName] :: [ConfigurationName] ». Le **NodeName** est l’ordinateur ou le nœud, sur lequel la ressource actuelle doit attendre.

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

Le **WaitForSome** ressource a une syntaxe similaire à l’exemple ci-dessus, mais ajoute le **NodeCount** clé. Le **NodeCount** indique le nombre de nœuds doit attendre la ressource actuelle.

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

Tous les **WaitForXXXX** partager les clés de syntaxe suivantes.

|  Propriété |  Description || RetryIntervalSec | Le nombre de secondes avant de réessayer. Valeur minimale est 1. | | RetryCount | Le nombre maximal de tentatives. | | ThrottleLimit | Nombre d’ordinateurs à se connecter simultanément. Valeur par défaut est `New-CimSession` par défaut. | | DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Pour plus d’informations, consultez [DependsOn](resource-depends-on.md)|| PsDscRunAsCredential | Consultez [à l’aide de DSC avec les informations d’identification utilisateur](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>Utilisation de ressources WaitForXXXX

Chaque **WaitForXXXX** attentes de ressources pour les ressources spécifiées à effectuer sur le nœud spécifié. Autres ressources dans la même Configuration peuvent ensuite *dépendent* le **WaitForXXXX** à l’aide de la ressource le **DependsOn** clé.

Par exemple, dans la configuration suivante, le nœud cible attend que la ressource **xADDomain** se termine sur le nœud **MyDC** avec un nombre maximal de 30 tentatives, à des intervalles de 15 secondes, avant que le nœud cible ne puisse joindre le domaine.

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

Lorsque vous compilez la Configuration, deux fichiers « .mof » sont générés. Appliquer les deux fichiers « .mof » aux nœuds cibles à l’aide de la [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) applet de commande

>**Remarque :** Par défaut la waitforxxx effectuent une tentative ressources essaient une seule fois, puis échouent. Il n’est pas obligatoire, vous devez généralement spécifier un **RetryCount** et **RetryIntervalSec**.

## <a name="see-also"></a>Voir aussi

- [Configurations DSC](configurations.md)
- [Utiliser les dépendances de ressource](resource-depends-on.md)
- [Ressources DSC](../resources/resources.md)
- [Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md)
