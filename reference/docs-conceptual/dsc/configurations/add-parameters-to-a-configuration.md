---
ms.date: 12/12/2018
keywords: dsc,powershell,ressource,galerie,configuration
title: Ajouter des paramètres à une configuration
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954196"
---
# <a name="add-parameters-to-a-configuration"></a>Ajouter des paramètres à une configuration

Comme les fonctions, les [configurations](configurations.md) peuvent être paramétrées pour offrir des configurations plus dynamiques selon les données entrées par l’utilisateur. Les étapes sont similaires à celles décrites dans la section [Fonctions avec paramètres](/powershell/module/microsoft.powershell.core/about/about_functions).

Cet exemple commence avec une configuration de base qui définit le service « Spooler » sur « Running » (En cours d’exécution).

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a>Paramètres de configuration intégrés

Mais contrairement à une fonction, l’attribut [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) n’ajoute aucune fonctionnalité. Outre les [paramètres communs](/powershell/module/microsoft.powershell.core/about/about_commonparameters), les configurations peuvent également utiliser les paramètres intégrés suivants, sans que vous ayez à les définir.

|Paramètre  |Description  |
|---------|---------|
|`-InstanceName`|Permet de définir des [configurations composites](compositeconfigs.md)|
|`-DependsOn`|Permet de définir des [configurations composites](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Permet de définir des [configurations composites](compositeconfigs.md)|
|`-ConfigurationData`|Permet de transmettre des [données de configuration](configData.md) structurées à utiliser dans la configuration.|
|`-OutputPath`|Permet de spécifier l’emplacement où votre fichier « \<computername\>.mof » sera compilé|

## <a name="adding-your-own-parameters-to-configurations"></a>Ajout de vos propres paramètres à des configurations

Outre les paramètres intégrés, vous pouvez également ajouter vos propres paramètres à vos configurations. Le bloc de paramètres est placé directement dans la déclaration de la configuration, exactement comme une fonction. Un bloc de paramètres de configuration doit être placé en dehors de toute déclaration de **nœud** et avant toute instruction *import*. En ajoutant des paramètres, vous pouvez rendre vos configurations plus robustes et dynamiques.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Ajouter un paramètre ComputerName

Le premier paramètre que vous pouvez ajouter est un paramètre `-Computername` afin de compiler dynamiquement un fichier « .mof » pour tout paramètre `-Computername` que vous transmettez à votre configuration. Comme pour les fonctions, vous pouvez également définir une valeur par défaut, au cas où l’utilisateur ne transmet aucune valeur pour `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Au sein de votre configuration, vous pouvez alors spécifier votre paramètre `-ComputerName` lors de la définition de votre bloc de nœud.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Appel de votre configuration avec des paramètres

Après avoir ajouté des paramètres à votre configuration, vous pouvez les utiliser comme s’il s’agissait d’une applet de commande.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Compilation de plusieurs fichiers .mof

Le bloc de nœud peut également accepter une liste séparée par des virgules de noms d’ordinateurs, et générer des fichiers « .mof » pour chacun de ces ordinateurs. Vous pouvez exécuter l’exemple suivant afin de générer des fichiers « .mof » pour tous les ordinateurs transmis au paramètre `-ComputerName`.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a>Paramètres avancés dans les configurations

Outre un paramètre `-ComputerName`, nous pouvons ajouter des paramètres pour le nom du service et l’état. L’exemple suivant ajoute un bloc de paramètres avec un paramètre `-ServiceName` et l’utilise pour définir dynamiquement le bloc de ressources **Service**. Il ajoute également un paramètre `-State` pour définir dynamiquement l’**état** dans le bloc de ressources **Service**.

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

    # It is best practice to explicitly import any required resources or modules.
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
> Dans des scénarios plus complexes, il peut être plus judicieux de déplacer vos données dynamiques vers des [données de configuration](configData.md) structurées.

L’exemple de configuration utilise désormais un paramètre `$ServiceName` dynamique, mais si aucune valeur n’est spécifiée, la compilation génère une erreur. Vous pouvez ajouter une valeur par défaut, comme dans cet exemple.

```powershell
[String]
$ServiceName="Spooler"
```

Mais dans cette instance, il est plus judicieux de forcer simplement l’utilisateur à spécifier une valeur pour le paramètre `$ServiceName`. L’attribut `parameter` vous permet d’ajouter une prise en charge de validation et de pipeline pour les paramètres de votre configuration.

Au-dessus de toute déclaration de paramètre, ajoutez le bloc d’attributs `parameter`, comme dans l’exemple ci-dessous.

```powershell
[parameter()]
[String]
$ServiceName
```

Vous pouvez spécifier des arguments pour chaque attribut `parameter` afin de contrôler divers aspects du paramètre défini. L’exemple suivant fait du paramètre `$ServiceName` un paramètre **obligatoire**.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Pour le paramètre `$State`, nous aimerions empêcher l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini, par exemple Running (en cours d’exécution) ou Stopped (arrêté). L’attribut `ValidationSet*` empêche l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini, par exemple Running (en cours d’exécution) ou Stopped (arrêté). L’exemple suivant ajoute l’attribut `ValidationSet` au paramètre `$State`. Comme nous ne souhaitons pas rendre le paramètre `$State` **obligatoire**, nous devrons lui ajouter une valeur par défaut.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Vous n’avez pas besoin de spécifier un attribut `parameter` lorsque vous utilisez un attribut `validation`.

Pour en savoir plus sur les `parameter` et les attributs de validation, consultez [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).

## <a name="fully-parameterized-configuration"></a>Configuration entièrement paramétrable

Nous disposons désormais d’une configuration paramétrable qui oblige l’utilisateur à spécifier des valeurs `-InstanceName`, `-ServiceName`, et qui valide le paramètre `-State`.

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

    # It is best practice to explicitly import any required resources or modules.
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
- [Configurations dynamiques](flow-control-in-configurations.md)
- [Utiliser des données de configuration dans vos configurations](configData.md)
- [Séparer des données de configuration et d’environnement](separatingEnvData.md)
