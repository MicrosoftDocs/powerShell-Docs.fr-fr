---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configurations DSC
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401449"
---
# <a name="dsc-configurations"></a>Configurations DSC

> S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Les configurations DSC sont des scripts PowerShell qui définissent un type spécial de fonction.
Pour définir une configuration, utilisez le mot clé PowerShell **Configuration**.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Enregistrez le script sous un `.ps1` fichier.

## <a name="configuration-syntax"></a>Syntaxe de configuration

Un script de configuration comprend les éléments suivants :

- Le bloc **Configuration**. Il s’agit du bloc de script le plus externe. Pour le définir, utilisez le mot clé **Configuration**, puis attribuez-lui un nom. Ici, le nom de la configuration est « MyDscConfiguration ».
- Un ou plusieurs blocs **Node**. Ils définissent les nœuds (ordinateurs ou machines virtuelles) que vous configurez. Dans la configuration ci-dessus, un bloc **Node** cible un ordinateur nommé « TEST-PC1 ». Le bloc de nœud peut accepter plusieurs noms d’ordinateurs.
- Un ou plusieurs blocs de ressources. C’est là que la configuration définit les propriétés pour les ressources qu’elle configure. Ici, nous avons deux blocs de ressources qui appellent tous les deux la ressource « WindowsFeature ».

Dans un bloc **Configuration**, vous pouvez faire tout ce qu’il est possible de faire dans une fonction PowerShell. Par exemple, dans l’exemple précédent, si vous ne vouliez pas coder en dur le nom de l’ordinateur cible dans la configuration, vous auriez pu ajouter un paramètre pour le nom du nœud :

Dans cet exemple, vous spécifiez le nom du nœud en le passant comme paramètre **ComputerName** quand vous compilez la configuration. Par défaut, le nom est « localhost ».

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

Le **nœud** bloc peut également accepter plusieurs noms d’ordinateurs. Dans l’exemple ci-dessus, vous pouvez utiliser la `-ComputerName` paramètre ou une liste de pass séparées par des virgules d’ordinateurs directement à la **nœud** bloc.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

Lorsque vous spécifiez une liste d’ordinateurs à la **nœud** bloc, au sein d’une Configuration, vous devez utiliser la notation de tableau.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>Compilation de la configuration.

Avant de pouvoir promulguer une configuration, vous devez la compiler dans un document MOF.
Pour cela, appelez la configuration comme pour une fonction PowerShell.
La dernière ligne de l’exemple, qui contient uniquement le nom de la configuration, appelle la configuration.

> [!NOTE]
> Pour appeler une configuration, la fonction doit se trouver dans la portée globale (comme pour toutes les fonctions PowerShell).
> Vous avez le choix entre « dot sourcer » le script, exécuter le script de configuration avec la touche F5 ou cliquer sur le bouton **Exécuter le script** dans l’environnement ISE.
> Pour « dot sourcer » le script, exécutez la commande `. .\myConfig.ps1`, où `myConfig.ps1` correspond au nom du fichier de script qui contient votre configuration.

Quand vous appelez la configuration, elle :

- Résout toutes les variables.
- Crée un dossier dans le répertoire actif portant le même nom que la configuration.
- Crée un fichier nommé _nom_nœud_.mof dans le nouveau répertoire, où _nom_nœud_ correspond au nom du nœud cible de la configuration.
  S’il existe plusieurs nœuds, un fichier MOF est créé pour chaque nœud.

> [!NOTE]
> Le fichier MOF contient toutes les informations de configuration du nœud cible. Il est donc important de le sécuriser.
> Pour plus d’informations, consultez [Sécurisation du fichier MOF](../pull-server/secureMOF.md).

Après la compilation de la première configuration, vous obtenez la structure de dossiers suivante :

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Si la configuration prend un paramètre, comme dans le deuxième exemple, le paramètre doit être fourni au moment de la compilation. Voici à quoi cela ressemble :

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>Utilisation de nouvelles ressources dans la configuration

Si vous avez exécuté les exemples précédents, vous avez peut-être remarqué un avertissement disant que vous utilisez une ressource sans l’avoir importée explicitement.
Actuellement, DSC est fourni avec 12 ressources contenues dans le module PSDesiredStateConfiguration.

Une nouvelle cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), peut être utilisée pour déterminer quelles ressources sont installées sur le système et lesquelles peuvent être utilisées par le gestionnaire de configuration local.
Une fois ces modules placés dans `$env:PSModulePath` et correctement reconnus par [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ils doivent encore être chargés dans votre configuration.

**Import-DscResource** est un mot clé dynamique qui peut être reconnu uniquement au sein d’un **Configuration** bloc, il n’est pas une applet de commande.
**Import-DscResource** accepte deux paramètres :

- **ModuleName** est recommandé pour l’utilisation d’**Import-DscResource**. Il accepte le nom du module qui contient les ressources à importer (ainsi qu’un tableau de chaînes comprenant des noms de modules).
- **Name** correspond au nom de la ressource à importer. Il ne s’agit pas du nom convivial retourné comme « Name » par [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), mais du nom de classe utilisé lors de la définition du schéma de la ressource (retourné comme **ResourceType** par [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).

Pour plus d’informations sur l’utilisation de `Import-DSCResource`, consultez [Import-DSCResource à l’aide de](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>Différences de v4 et v5 PowerShell

Il existe des différences dans où les ressources DSC besoin d’être stocké dans PowerShell 4.0. Pour plus d’informations, consultez [emplacement de la ressource](import-dscresource.md#resource-location).

## <a name="see-also"></a>Voir aussi

- [Présentation de la configuration de l’état souhaité de Windows PowerShell](../overview/overview.md)
- [Ressources DSC](../resources/resources.md)
- [Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md)
