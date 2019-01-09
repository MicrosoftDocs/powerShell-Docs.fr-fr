---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Importer une version spécifique d’une ressource installée
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401168"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importer une version spécifique d’une ressource installée

> S'applique à : Windows PowerShell 5.0

Dans PowerShell 5.0, des versions distinctes des ressources de DSC peuvent être installées sur un ordinateur côte à côte. Un module de ressources peut stocker des versions distinctes d’une ressource dans la version dossiers nommée.

## <a name="installing-separate-resource-versions-side-by-side"></a>Installation des versions de ressources distinct côte à côte

Vous pouvez utiliser les paramètres **MinimumVersion**, **MaximumVersion** et **RequiredVersion** de l’applet de commande [Install-Module](/powershell/module/PowershellGet/Install-Module) pour indiquer la version d’un module à installer. L’appel de l’applet de commande **Install-Module** sans spécifier de version installe la version la plus récente.

Par exemple, il existe plusieurs versions du module **xFailOverCluster**, chacun contenant une ressource **xCluster**. Appel **Install-Module** sans spécifier la version numéro installe la version la plus récente du module.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Pour installer une version spécifique d’un module, vous devez spécifier un **RequiredVersion** de 1.1.0.0. Cette opération installe la version spécifiée côte à côte avec la version installée.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

À présent, vous voyez à la fois la version du module répertorié lorsque vous utilisez `Get-DSCResource`.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Spécification d’une version de ressource dans une configuration

Si vous disposez des versions de ressources distinct installées sur un ordinateur, vous devez spécifier la version de la ressource lorsque vous l’utilisez dans une configuration. Pour cela, vous devez spécifier le paramètre **ModuleVersion** du mot-clé **Import-DscResource**. Si vous ne parvenez pas à spécifier la version d’un module d’une ressource dont plusieurs versions sont installées, la configuration génère une erreur.

La configuration suivante montre comment spécifier la version de la ressource à appeler :

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>Remarque : Le paramètre ModuleVersion d’Import-DscResource n’est pas disponible dans PowerShell 4.0. Dans PowerShell 4.0, vous pouvez spécifier une version du module en passant un objet de spécification de module au paramètre ModuleName d’Import-DscResource. Un objet de spécification de module est une table de hachage qui contient les clés ModuleName et RequiredVersion. Par exemple :

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

Cela fonctionne également dans PowerShell 5.0, mais il est recommandé d’utiliser le paramètre **ModuleVersion**.

## <a name="see-also"></a>Voir aussi

- [Configurations DSC](configurations.md)
- [Ressources DSC](../resources/resources.md)
