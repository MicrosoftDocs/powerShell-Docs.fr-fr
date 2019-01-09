---
ms.date: 12/12/2018
keywords: DSC, powershell, ressource, galerie, le programme d’installation
title: Ajouter des paramètres à une configuration
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401431"
---
# <a name="add-parameters-to-a-configuration"></a>Ajouter des paramètres à une configuration

Comme les fonctions, [Configurations](configurations.md) peut être paramétré pour permettre aux configurations plus dynamiques en fonction de l’entrée d’utilisateur. Les étapes sont similaires à ceux décrits dans [fonctions munies de paramètres](/powershell/module/microsoft.powershell.core/about/about_functions).

Cet exemple démarre avec une Configuration de base qui configure le service « Spooler » à « Exécution ».

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Paramètres de Configuration intégrés

Contrairement à une fonction, le [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribut n’ajoute aucune fonctionnalité. En plus de [paramètres communs](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations peuvent également utiliser les intégrées dans les paramètres sans avoir à les définir suivantes.

|Paramètre  |Description  |
|---------|---------|
|`-InstanceName`|Utilisé dans la définition [Configurations Composite](compositeconfigs.md)|
|`-DependsOn`|Utilisé dans la définition [Configurations Composite](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Utilisé dans la définition [Configurations Composite](compositeconfigs.md)|
|`-ConfigurationData`|Utilisé pour passer dans structuré [les données de Configuration](configData.md) pour une utilisation dans la Configuration.|
|`-OutputPath`|Utilisé pour spécifier l’emplacement où votre «\<computername\>.mof « fichier sera compilé|

## <a name="adding-your-own-parameters-to-configurations"></a>Ajout de vos propres paramètres aux Configurations

Outre les paramètres intégrés, vous pouvez également ajouter vos propres paramètres pour vos Configurations. Le bloc de paramètres est placé directement dans la déclaration de la Configuration, comme une fonction. Un bloc de paramètres de Configuration doit être en dehors des **nœud** déclarations et avant tout autre *importer* instructions. En ajoutant des paramètres, vous pouvez appliquer vos Configurations plus robuste et dynamique.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Ajouter un paramètre ComputerName

Est le premier paramètre que vous pouvez ajouter un `-Computername` paramètre afin de compiler dynamiquement un fichier « .mof » pour tout `-Computername` vous passez à votre configuration. Comme les fonctions, vous pouvez également définir une valeur par défaut, au cas où l’utilisateur ne passe pas une valeur pour `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Au sein de votre configuration, vous pouvez ensuite spécifier votre `-ComputerName` paramètre lors de la définition de votre bloc de nœud.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Appelez votre Configuration avec des paramètres

Une fois que vous avez ajouté des paramètres à votre Configuration, vous pouvez les utiliser comme vous le feriez avec une applet de commande.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Compilation de plusieurs fichiers .mof

Le bloc de nœud peut également accepter une liste séparée par des virgules de noms d’ordinateur et génère des fichiers « .mof » pour chaque. Vous pouvez exécuter l’exemple suivant pour générer des fichiers « .mof » pour tous les ordinateurs passés à la `-ComputerName` paramètre.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Paramètres avancés dans les Configurations

Outre un `-ComputerName` paramètre, nous pouvons ajouter des paramètres pour le nom du service et l’état. L’exemple suivant ajoute un bloc de paramètres avec un `-ServiceName` paramètre et l’utilise pour définir dynamiquement le **Service** bloc de ressources. Il ajoute également un `-State` paramètre pour définir dynamiquement le **état** dans le **Service** bloc de ressources.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> Dans d’autres scénarios advacned, il peut être plus judicieux de déplacer vos données dynamiques dans un texte structuré [les données de Configuration](configData.md).

L’exemple de Configuration maintenant prend un dynamique `$ServiceName`, mais s’il n’est pas spécifié, génère une erreur de compilation. Vous pouvez ajouter une valeur par défaut, comme dans cet exemple.

```powershell
[String]
$ServiceName="Spooler"
```

Dans cette instance, il est plus judicieux de simplement forcer l’utilisateur de spécifier une valeur pour le `$ServiceName` paramètre. Le `parameter` attribut vous permet d’ajouter la prise en charge supplémentaire de validation et de pipeline pour les paramètres de Configuration de votre.

Au-dessus de toute déclaration de paramètre, ajoutez le `parameter` bloc d’attributs comme dans l’exemple ci-dessous.

```powershell
[parameter()]
[String]
$ServiceName
```

Vous pouvez spécifier des arguments à chaque `parameter` attribut, de contrôler divers aspects du paramètre défini. L’exemple suivant effectue la `$ServiceName` un **obligatoire** paramètre.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Pour le `$State` paramètre, nous aimerions empêcher l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini (comme en cours d’exécution, arrêté) le `ValidationSet*`attribut empêche l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini (par exemple, en cours d’exécution, Arrêté). L’exemple suivant ajoute le `ValidationSet` attribut le `$State` paramètre. Étant donné que nous ne souhaitez pas rendre le `$State` paramètre **obligatoire**, nous devrons ajouter une valeur par défaut pour celle-ci.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Vous n’avez pas besoin de spécifier un `parameter` attribut lorsque vous utilisez un `validation` attribut.

Vous pouvez en savoir plus sur la `parameter` et attributs de validation dans [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Configuration entièrement paramétrable

Nous disposons désormais d’une Configuration paramétrable qui oblige l’utilisateur à spécifier un `-InstanceName`, `-ServiceName`et valide les `-State` paramètre.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Écrire une aide pour les configurations DSC](configHelp.md)
- [Configuration dynamique](flow-control-in-configurations.md)
- [Utiliser les données de Configuration dans vos Configurations](configData.md)
- [Données de configuration et d’environnement distinct](separatingEnvData.md)
