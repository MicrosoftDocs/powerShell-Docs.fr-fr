---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Utilisation des données de configuration
description: Cette rubrique décrit la structure de la table de hachage ConfigurationData. Cela vous permet de créer une configuration unique utilisée pour plusieurs nœuds ou différents environnements.
ms.openlocfilehash: aa4a0545aec529dbc923908612d2e1f9e60b3c9c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647103"
---
# <a name="using-configuration-data-in-dsc"></a>Utilisation des données de configuration dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

À l’aide du paramètre DSC intégré **ConfigurationData** , vous pouvez définir les données qui peuvent être utilisées dans une configuration. Cela vous permet de créer une configuration unique utilisée pour plusieurs nœuds ou différents environnements. Par exemple, si vous développez une application, vous pouvez utiliser une seule configuration pour les environnements de développement et de production et utiliser les données de configuration pour spécifier les données de chaque environnement.

Cette rubrique décrit la structure de la table de hachage **ConfigurationData** . Pour des exemples d’utilisation des données de configuration, consultez [Séparation des données de configuration et d’environnement](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>Le paramètre commun ConfigurationData

Une configuration DSC prend un paramètre commun, **ConfigurationData** , que vous spécifiez lorsque vous compilez la configuration. Pour obtenir des informations sur la compilation des configurations, consultez [Configurations DSC](configurations.md).

Le paramètre **ConfigurationData** est une table de hachage qui doit contenir au moins une clé nommée **AllNodes** . Il peut également avoir une ou plusieurs autres clés.

> [!NOTE]
> Les exemples de cette rubrique utilisent une seule clé supplémentaire (autres que la clé nommée **AllNodes** ) appelée `NonNodeData`, mais vous pouvez inclure n’importe quel nombre de clés supplémentaires et les nommer comme vous le souhaitez.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

La valeur de la clé **AllNodes** est un tableau. Chaque élément de ce tableau est également une table de hachage qui doit contenir au moins une clé nommée **NodeName**  :

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

Vous pouvez ajouter d’autres clés à chaque table de hachage :

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

Pour appliquer une propriété à tous les nœuds, vous pouvez créer un membre du tableau **AllNodes** dont un **NodeName** a la valeur `*`. Par exemple, pour attribuer la propriété `LogPath` à tous les nœuds, vous pouvez procéder ainsi :

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Ceci équivaut à ajouter une propriété portant le nom `LogPath` avec la valeur `"C:\Logs"` à chacun des autres blocs (`VM-1`, `VM-2` et `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Définition de la table de hachage ConfigurationData

Vous pouvez définir **ConfigurationData** soit comme variable dans le même fichier de script qu’une configuration (comme dans nos exemples précédents), soit dans un fichier `.psd1` distinct. Pour définir **ConfigurationData** dans un fichier `.psd1`, créez un fichier contenant uniquement la table de hachage qui représente les données de configuration.

Par exemple, vous pouvez créer un fichier nommé `MyData.psd1` avec le contenu suivant :

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Compilation d’une configuration avec des données de configuration

Pour compiler une configuration pour laquelle vous avez défini des données de configuration, vous passez les données de configuration en tant que valeur du paramètre **ConfigurationData** .

Cela crée un fichier MOF pour chaque entrée dans le tableau **AllNodes** . Chaque fichier MOF est nommé avec la propriété `NodeName` de l’entrée correspondante du tableau.

Par exemple, si vous définissez des données de configuration comme dans le fichier `MyData.psd1` ci-dessus, la compilation d’une configuration créerait à la fois des fichiers `VM-1.mof` et `VM-2.mof`.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Compilation d’une configuration avec des données de configuration à l’aide d’une variable

Pour utiliser les données de configuration qui sont définies comme une variable dans le même fichier `.ps1` que la configuration, vous passez le nom de la variable comme valeur du paramètre **ConfigurationData** lors de la compilation de la configuration :

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Compilation d’une configuration avec des données de configuration à l’aide d’un fichier de données

Pour utiliser les données de configuration qui sont définies dans un fichier .psd1, vous passez le chemin et le nom de ce fichier comme valeur du paramètre **ConfigurationData** lors de la compilation de la configuration :

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Utilisation de variables ConfigurationData dans une configuration

DSC fournit les variables spéciales suivantes, qui peuvent être utilisées dans un script de configuration :

- **$AllNodes** fait référence à l’ensemble de la collection de nœuds définis dans **ConfigurationData** . Vous pouvez filtrer la collection **AllNodes** à l’aide de **.Where()** et **.ForEach()** .
- **ConfigurationData** fait référence à la table de hachage entière qui est passée comme paramètre lors de la compilation d’une configuration.
- **MyTypeName** contient le nom de la [configuration](configurations.md) dans laquelle la variable est utilisée. Par exemple, dans la configuration `MyDscConfiguration`, `$MyTypeName` aura la valeur `MyDscConfiguration`.
- **Node** fait référence à une entrée particulière dans la collection **AllNodes** une fois qu’elle a été filtrée à l’aide de **.Where()** ou **.ForEach()** .
  - Vous pouvez en savoir plus sur ces méthodes dans [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)

## <a name="using-non-node-data"></a>Utilisation des données n’appartenant pas à un nœud

Comme nous l’avons vu dans les exemples précédents, la table de hachage **ConfigurationData** peut avoir une ou plusieurs clés en plus de la clé **AllNodes** requise. Dans les exemples de cette rubrique, nous avons utilisé un seul nœud supplémentaire et l’avons nommé `NonNodeData`. Toutefois, vous pouvez définir n’importe quel nombre de clés supplémentaires et les nommer comme vous le souhaitez.

Pour obtenir un exemple d’utilisation des données n’appartenant pas à un nœud, consultez [Séparation des données de configuration et d’environnement](separatingEnvData.md).

## <a name="see-also"></a>Voir aussi

- [Options relatives aux informations d’identification dans les données de configuration](configDataCredentials.md)
- [Configurations DSC](configurations.md)
