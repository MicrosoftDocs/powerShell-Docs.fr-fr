---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Utilisation d’Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080099"
---
# <a name="using-import-dscresource"></a>Utilisation d’Import-DSCResource

`Import-DScResource` est un mot clé dynamique, qui peut être utilisé uniquement dans un bloc de script de configuration. Le mot clé `Import-DSCResource` pour importer toutes les ressources nécessaires dans votre configuration. Les ressources sous `$pshome` sont importées automatiquement, mais il est toujours préférable d’importer explicitement toutes les ressources utilisées dans votre [configuration](Configurations.md).

La syntaxe pour `Import-DSCResource` est indiquée ci-dessous.  Lorsque vous spécifiez des modules par nom, il est nécessaire de répertorier chacun de ces modules sur une nouvelle ligne.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Paramètre  |Description  |
|---------|---------|
|`-Name`|Les noms des ressources DSC que vous devez importer. Si le nom du module est spécifié, la commande recherche ces ressources DSC dans ce module ; sinon, la commande recherche les ressources DSC dans tous leurs chemins d’accès. Les caractères génériques sont pris en charge.|
|`-ModuleName`|Le nom du module, ou une spécification de module.  Si vous spécifiez les ressources à importer à partir d’un module, la commande tente d’importer uniquement ces ressources. Si vous spécifiez uniquement le module, la commande importe toutes les ressources DSC dans le module.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Exemple : Utiliser Import-DSCResource au sein d’une configuration

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
> La spécification de plusieurs valeurs pour les noms de ressources et les noms de modules dans la même commande n’est pas prise en charge. Un comportement non déterminant permet de choisir quelle ressource charger à partir de quel module, au cas où une même ressource existe dans plusieurs modules. La commande ci-dessous génère une erreur pendant la compilation.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Éléments à prendre en compte lorsque vous utilisez uniquement le paramètre Name :

- Cette opération nécessite beaucoup de ressources, en fonction du nombre de modules installés sur l’ordinateur.
- Elle charge la première ressource trouvée avec le nom donné. Si plusieurs ressources installées portent le même nom, elle risque de charger la mauvaise ressource.

Il est recommandé de spécifier `–ModuleName` avec le paramètre `-Name`, comme décrit ci-dessous.

Cette méthode offre les avantages suivants :

- Elle réduit l’impact sur les performances en limitant l’étendue de la recherche pour la ressource spécifiée.
- Elle précise explicitement le module qui définit la ressource, en garantissant le chargement de la ressource adéquate.

> [!NOTE]
> Dans PowerShell 5.0, les ressources DSC peuvent avoir plusieurs versions et celles-ci peuvent être installées sur un ordinateur côte à côte. L’implémentation inclut plusieurs versions d’un module de ressource qui sont contenues dans le même dossier de module.
> Pour plus d’informations, consultez [Utilisation de ressources avec plusieurs versions](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense avec Import-DSCResource

Lorsque vous créez la configuration DSC dans ISE, PowerShell fournit à IntelliSence les ressources et les propriétés des ressources. Les définitions de ressources dans le chemin d’accès du module `$pshome` sont automatiquement chargées. Lorsque vous importez des ressources à l’aide du mot clé `Import-DSCResource`, les définitions de ressources spécifiées sont ajoutées, et IntelliSense est développé pour inclure le schéma de la ressource importée.

![Ressource Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> À compter de PowerShell 5.0, la saisie semi-automatique via la touche Tab a été ajoutée à ISE pour les ressources DSC et leurs propriétés. Pour plus d’informations, consultez [Ressources](../resources/resources.md).

Lors de la compilation de la configuration, PowerShell utilise les définitions de ressources importées pour valider tous les blocs de ressources dans la configuration.
Chaque bloc de ressources est validé à l’aide de la définition de schéma de la ressource, selon les règles suivantes.

- Seules les propriétés définies dans le schéma sont utilisées.
- Les types de données pour chaque propriété sont corrects.
- Les propriétés de clés sont spécifiées.
- Aucune propriété en lecture seule n’est utilisée.
- La validation des valeurs est mappée à des types.

Considérez la configuration suivante :

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

La compilation de cette configuration entraîne une erreur.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense et le schéma de validation vous permettent de détecter plus d’erreurs lors de l’analyse et de la compilation, évitant des complications au moment de l’exécution.

> [!NOTE]
> Chaque ressource DSC peut avoir un nom et une propriété **FriendlyName** définie par le schéma de la ressource. Voici les deux premières lignes du fichier « MSFT_ServiceResource.shema.mof ».
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Lorsque vous utilisez cette ressource dans une configuration, vous pouvez spécifier **MSFT_ServiceResource** ou **Service**.

## <a name="powershell-v4-and-v5-differences"></a>Différences entre PowerShell v4 et PowerShell v5

Plusieurs différences apparaissent lors de la création de configurations dans Visual Studio PowerShell 4.0. PowerShell 5.0 et ultérieur. Cette section met en évidence les différences pertinentes pour cet article.

### <a name="multiple-resource-versions"></a>Plusieurs versions de ressources

L’installation et l’utilisation de plusieurs versions de ressources côte à côte n’étaient pas prises en charge dans PowerShell 4.0. Si vous rencontrez des problèmes d’importation de ressources dans votre configuration, assurez-vous d’utiliser uniquement une version de la ressource installée.

Dans l’image ci-dessous, deux versions du module **xPSDesiredStateConfiguration** sont installées.

![Correction de plusieurs versions de ressources](/media/multiple-resource-versions-broken.md)

Copiez le contenu de votre version de module souhaitée dans le niveau supérieur du répertoire du module.

![Correction de plusieurs versions de ressources](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Emplacement de la ressource

Lorsque vous créez et compilez des configurations, vos ressources peuvent être stockées dans un répertoire spécifié par [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). Dans PowerShell 4.0, le LCM nécessite le stockage de tous les modules de ressources DSC sous "Program Files\WindowsPowerShell\Modules" ou `$pshome\Modules`. À compter de PowerShell 5.0, cette exigence a été supprimée, et les modules de ressources peuvent être stockés dans un répertoire spécifié par `PSModulePath`.

## <a name="see-also"></a>Voir aussi

- [Ressources](../resources/resources.md)
