---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Utilisation d’Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803410"
---
# <a name="using-import-dscresource"></a>Utilisation d’Import-DSCResource

`Import-DScResource` est un mot clé dynamique, ce qui peut être utilisé uniquement dans un bloc de script de Configuration. Le `Import-DSCResource` mot clé pour importer toutes les ressources nécessaires dans votre Configuration. Ressources sous `$pshome` sont importés automatiquement, mais il est toujours considéré comme bonne pratique consiste à importer explicitement toutes les ressources utilisées dans votre [Configuration](Configurations.md).

La syntaxe pour `Import-DSCResource` est indiqué ci-dessous.  Lorsque vous spécifiez les modules par nom, il est nécessaire pour répertorier chacun sur une nouvelle ligne.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Paramètre  |Description  |
|---------|---------|
|`-Name`|Les noms des ressources DSC que vous devez importer. Si le nom du module est spécifié, la commande recherche ces ressources DSC dans ce module ; Sinon, la commande recherche les ressources DSC dans tous les chemins d’accès de ressource DSC. Les caractères génériques sont pris en charge.|
|`-ModuleName`|Le nom du module, ou une spécification de module.  Si vous spécifiez les ressources à importer à partir d’un module, la commande tente d’importer uniquement les ressources. Si vous spécifiez uniquement le module, la commande importe toutes les ressources DSC dans le module.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Exemple : Utilisez Import-DSCResource au sein d’une configuration

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> Spécification de plusieurs valeurs pour les noms de ressources et les noms de modules dans la même commande ne sont pas pris en charge. Il peut avoir un comportement non déterminant sur quelle ressource à charger à partir de quel module au cas où même ressource existe dans plusieurs modules. Commande ci-dessous entraîne erreur pendant la compilation.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Éléments à prendre en compte lorsque vous utilisez uniquement le paramètre Name :

- C’est une opération gourmande en ressources en fonction du nombre de modules installés sur l’ordinateur.
- Il charge la première ressource trouvée avec le nom donné. Dans le cas où il existe plusieurs ressources avec le même nom installé, il peut charger la ressource incorrecte.

L’utilisation recommandée consiste à spécifier `–ModuleName` avec la `-Name` paramètre, comme décrit ci-dessous.

Cette utilisation présente les avantages suivants :

- Elle réduit l’impact sur les performances en limitant l’étendue de recherche pour la ressource spécifiée.
- Elle définit explicitement le module de définition de la ressource, en garantissant que la ressource correcte est chargée.

> [!NOTE]
> Dans PowerShell 5.0, les ressources DSC peuvent avoir plusieurs versions et celles-ci peuvent être installées sur un ordinateur côte à côte. L’implémentation inclut plusieurs versions d’un module de ressource qui sont contenues dans le même dossier de module.
> Pour plus d’informations, consultez [Utilisation de ressources avec plusieurs versions](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense avec Import-DSCResource

Lorsque vous créez la configuration DSC dans ISE, PowerShell fournit IntelliSence pour les ressources et les propriétés de ressource. Définitions de ressource sous la `$pshome` chemin d’accès du module sont chargés automatiquement. Lorsque vous importez des ressources à l’aide de la `Import-DSCResource` mot clé, les définitions de ressources spécifié sont ajoutées et Intellisense est développé pour inclure le schéma de la ressource importée.

![Intellisense de ressources](/media/resource-intellisense.png)

> [!NOTE]
> À compter de PowerShell 5.0, la saisie semi-automatique par tabulation a été ajoutée à l’environnement ISE pour les ressources DSC et leurs propriétés. Pour plus d’informations, consultez [ressources](../resources/resources.md).

Lors de la compilation de la Configuration, PowerShell utilise les définitions de ressource importée pour valider tous les blocs de ressources dans la configuration.
Chaque bloc de ressources est validé, à l’aide de la définition de schéma de la ressource pour les règles suivantes.

- Seules les propriétés définies dans le schéma sont utilisées.
- Les types de données pour chaque propriété sont corrects.
- Propriétés de clés sont spécifiées.
- Aucune propriété en lecture seule n’est utilisée.
- Mappe les types de validation de valeur.

Prenez en compte la configuration suivante :

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Résultats de cette Configuration dans une erreur de compilation.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense et le schéma de validation permettent d’intercepter les erreurs plus au moment de l’analyse et de compilation, éviter les complications au moment de l’exécution.

> [!NOTE]
> Chaque ressource DSC peut avoir un nom et un **FriendlyName** défini par le schéma de la ressource. Voici les deux premières lignes de « MSFT_ServiceResource.shema.mof ».
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Lorsque vous utilisez cette ressource dans une Configuration, vous pouvez spécifier **MSFT_ServiceResource** ou **Service**.

## <a name="powershell-v4-and-v5-differences"></a>Différences de v4 et v5 PowerShell

Il existe plusieurs différences que vous voyez lors de la création de Configurations dans Visual Studio PowerShell 4.0. PowerShell 5.0 et versions ultérieur. Cette section met en évidence les différences que vous consultez pertinents pour cet article.

### <a name="multiple-resource-versions"></a>Plusieurs Versions de ressources

Installation et l’utilisation de plusieurs versions de ressources côte à côte n’était pas pris en charge dans PowerShell 4.0. Si vous remarquez des problèmes d’importation de ressources dans votre Configuration, assurez-vous que vous avez uniquement une version de la ressource installée.

Dans l’image ci-dessous, deux versions de la **xPSDesiredStateConfiguration** module sont installés.

![Plusieurs Versions des ressources fixées](/media/multiple-resource-versions-broken.md)

Copiez le contenu de votre version du module souhaité dans le niveau supérieur du répertoire du module.

![Plusieurs Versions des ressources fixées](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Emplacement de la ressource

Lorsque vous créez et compilation de Configurations, vos ressources peuvent être stockées dans un répertoire spécifié par votre [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). Dans PowerShell 4.0, le LCM nécessite tous les modules de ressources DSC soient stockées sous « Programme Files\WindowsPowerShell\Modules » ou `$pshome\Modules`. À compter de PowerShell 5.0, cette exigence a été supprimée, et les modules de ressources peuvent être stockées dans un répertoire spécifié par `PSModulePath`.

## <a name="see-also"></a>Voir aussi

- [Ressources](../resources/resources.md)
