---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Ressources DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046689"
---
# <a name="dsc-resources"></a>Ressources DSC

>S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC. Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.

Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.  Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.

Chaque ressource a un * schéma qui détermine la syntaxe nécessaire pour utiliser la ressource dans un [Configuration](../configurations/configurations.md). Un schéma d’une ressource peut être défini comme suit :

- **« Schema.MOF »** fichier : La plupart des ressources définir leurs *schéma* dans un « Schema.MOF' fichier, à l’aide [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- **«\<Nom de la ressource\>. schema.psm1'** fichier : [Ressources composites](../configurations/compositeConfigs.md) définir leurs *schéma* dans un «<ResourceName>. schema.psm1' à l’aide de fichiers un [bloc de paramètres de](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **«\<Nom de la ressource\>.psm1'** fichier : Classe les ressources DSC en définissent leurs *schéma* dans la définition de classe. Éléments de syntaxe sont signalées en tant que propriétés de classe. Pour plus d’informations, consultez [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Pour récupérer la syntaxe pour une ressource DSC, utilisez le [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) applet de commande avec le `-Syntax` paramètre. Cette utilisation est similaire à l’utilisation de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) avec le `-Syntax` pour obtenir la syntaxe de l’applet de commande. La sortie que vous voyez affiche le modèle utilisé pour un bloc de ressources pour la ressource que vous spécifiez.

```powershell
Get-DscResource -Syntax Service
```

La sortie que vous voyez doit être similaire à la sortie ci-dessous, bien que la syntaxe de la ressource pourrait changer à l’avenir. Comme la syntaxe de l’applet de commande, le *clés* vu dans les crochets, sont facultatifs. Les types de spécifient le type de données qu'attend de chaque clé.

> [!NOTE]
> Le **Vérifiez** clé est facultative, car les valeurs par défaut sur « Present ».

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

À l’intérieur d’une Configuration, un **Service** bloc de ressources peut ressembler à ceci pour **Vérifiez** que le service spouleur est en cours d’exécution.

> [!NOTE]
> Avant d’utiliser une ressource dans une Configuration, vous devez l’importer à l’aide de [Import-DSCResource](../configurations/import-dscresource.md).

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

Les configurations peuvent contenir plusieurs instances du même type de ressource. Chaque instance doit être nommé de manière unique. Dans l’exemple suivant, une seconde **Service** bloc de ressources est ajouté pour configurer le service « DHCP ».

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> À compter de PowerShell 5.0, intellisense a été ajoutée pour DSC. Cette nouvelle fonctionnalité vous permet d’utiliser \<onglet\> et \<Ctrl + espace\> à compléter automatiquement les noms de clé.

![Saisie semi-automatique par tabulation ressource](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>Ressources intégrées

En plus de ressources de la Communauté, il existe des ressources intégrées pour Windows, les ressources pour Linux et les ressources pour les dépendances entre nœuds. Vous pouvez utiliser les étapes ci-dessus pour déterminer la syntaxe de ces ressources et comment les utiliser. Les pages qui utilise ces ressources ont été archivés sous **référence**.

Ressources intégrées Windows

* [Ressource Archive](../reference/resources/windows/archiveResource.md)
* [Ressource Environment](../reference/resources/windows/environmentResource.md)
* [Ressource File](../reference/resources/windows/fileResource.md)
* [Ressource Group](../reference/resources/windows/groupResource.md)
* [Ressource GroupSet](../reference/resources/windows/groupSetResource.md)
* [Ressource Log](../reference/resources/windows/logResource.md)
* [Ressource Package](../reference/resources/windows/packageResource.md)
* [Ressource ProcessSet](../reference/resources/windows/ProcessSetResource.md)
* [Ressources Registry](../reference/resources/windows/registryResource.md)
* [Ressource Script](../reference/resources/windows/scriptResource.md)
* [Ressource Service](../reference/resources/windows/serviceResource.md)
* [Ressource ServiceSet](../reference/resources/windows/serviceSetResource.md)
* [Ressource User](../reference/resources/windows/userResource.md)
* [Ressource WindowsFeature](../reference/resources/windows/windowsFeatureResource.md)
* [Ressource WindowsFeatureSet](../reference/resources/windows/windowsFeatureSetResource.md)
* [Ressource WindowsOptionalFeature](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [Ressource WindowsOptionalFeatureSet](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [Ressources de WindowsPackageCabResource](../reference/resources/windows/windowsPackageCabResource.md)
* [Ressource WindowsProcess](../reference/resources/windows/windowsProcessResource.md)

[Les dépendances entre nœuds](../configurations/crossNodeDependencies.md) ressources

* [WaitForAll ressource](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome ressource](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny ressource](../reference/resources/windows/waitForAnyResource.md)

Ressources de gestion de package

* [Ressources de PackageManagement](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [Ressources de PackageManagementSource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Ressources de Linux

* [Ressource Archive de Linux](../reference/resources/linux/lnxArchiveResource.md)
* [Ressource de l’environnement Linux](../reference/resources/linux/lnxEnvironmentResource.md)
* [Ressources de FileLine Linux](../reference/resources/linux/lnxFileLineResource.md)
* [Ressources de fichier Linux](../reference/resources/linux/lnxFileResource.md)
* [Ressource de groupe Linux](../reference/resources/linux/lnxGroupResource.md)
* [Ressource de Package Linux](../reference/resources/linux/lnxPackageResource.md)
* [Ressource de Script de Linux](../reference/resources/linux/lnxScriptResource.md)
* [Ressource de Service de Linux](../reference/resources/linux/lnxServiceResource.md)
* [Ressources de SshAuthorizedKeys Linux](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Ressources d’utilisateur Linux](../reference/resources/linux/lnxUserResource.md)
