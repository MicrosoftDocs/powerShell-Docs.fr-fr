---
ms.date: 02/28/2020
keywords: dsc,powershell,configuration,installation
title: Ressources DSC
ms.openlocfilehash: 863898d910cc3c75c3e5977a5b6b0657ba7ed512
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278242"
---
# <a name="dsc-resources"></a>Ressources DSC

> S’applique à la version 4.0 de Windows PowerShell et aux versions ultérieures.

## <a name="overview"></a>Vue d’ensemble

Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC. Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.

Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS. Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.

Chaque ressource comporte un *schéma qui détermine la syntaxe nécessaire pour utiliser la ressource dans une [configuration](../configurations/configurations.md).
Le schéma d’une ressource peut être défini comme suit :

- Fichier **'Schema.Mof'**  : La plupart des ressources définissent leur _schéma_ dans un fichier « Schema.MOF » à l’aide de [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- Fichier **'\<Nom de la ressource\>.schema.psm1'**  : Les [ressources composites](../configurations/compositeConfigs.md) définissent leur *schéma* dans un fichier '<ResourceName>.schema.psm1' à l’aide d’un [bloc de paramètres](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- Fichier **'\<Nom de la ressource\>.psm1'**  : Les ressources DSC basées sur la classe définissent leur _schéma_ dans la définition de classe. Les éléments de syntaxe sont signalés en tant que propriétés de classe. Pour plus d’informations, consultez [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Pour récupérer la syntaxe d’une ressource DSC, utilisez l’applet de commande [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) avec le paramètre `-Syntax`. Cette méthode est similaire à l’utilisation de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) avec le paramètre `-Syntax` pour obtenir la syntaxe de l’applet de commande. Le résultat affichera le modèle utilisé pour un bloc de ressources correspondant à la ressource que vous spécifiez.

```powershell
Get-DscResource -Syntax Service
```

Le résultat devrait être similaire à ce qui suit, même si la syntaxe de la ressource risque de change à l’avenir. Comme dans la syntaxe de l’applet de commande, les _clés_ affichées entre crochets sont facultatives. Les types spécifient le type de données attendu par chaque clé.

> [!NOTE]
> La clé **Ensure** (garantir) est facultative car les valeurs par défaut sont définies sur « Present ».

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

Dans une configuration, un bloc de ressources **Service** peut ressembler à ceci pour **garantir** que le service Spooler est en cours d’exécution.

> [!NOTE]
> Avant d’utiliser une ressource dans une configuration, vous devez l’importer à l’aide d’[Import-DSCResource](../configurations/import-dscresource.md).

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

Les configurations peuvent contenir plusieurs instances du même type de ressource. Chaque instance doit afficher un nom unique. Dans l’exemple suivant, un second bloc de ressources **Service** est ajouté pour configurer le service « DHCP ».

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
> À compter de PowerShell 5.0, IntelliSense a été ajouté pour DSC. Cette nouvelle fonctionnalité permet d’utiliser les touches <kbd>Tab</kbd> et <kbd>Ctrl</kbd>+<kbd>Espace</kbd> pour l’autocomplétion des noms de clés.

![Saisie semi-automatique des ressources via la touche Tab](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a>Types de ressources

Windows est fourni avec des ressources intégrées et Linux possède des ressources propres au système d’exploitation. Il existe des ressources pour les [dépendances entre les nœuds](../configurations/crossNodeDependencies.md), des ressources de gestion des packages, ainsi que des ressources [appartenant à la communauté et gérées par la communauté](https://github.com/dsccommunity). Vous pouvez suivre les étapes ci-dessus pour déterminer la syntaxe de ces ressources et savoir comment les utiliser. Les pages qui utilisent ces ressources ont été archivées sous **Référence**.

### <a name="windows-built-in-resources"></a>Ressources intégrées Windows

- [Ressource Archive](../reference/resources/windows/archiveResource.md)
- [Ressource Environment](../reference/resources/windows/environmentResource.md)
- [Ressource File](../reference/resources/windows/fileResource.md)
- [Ressource Group](../reference/resources/windows/groupResource.md)
- [Ressource GroupSet](../reference/resources/windows/groupSetResource.md)
- [Ressource Log](../reference/resources/windows/logResource.md)
- [Ressource Package](../reference/resources/windows/packageResource.md)
- [Ressource ProcessSet](../reference/resources/windows/ProcessSetResource.md)
- [Ressources Registry](../reference/resources/windows/registryResource.md)
- [Ressource Script](../reference/resources/windows/scriptResource.md)
- [Ressource Service](../reference/resources/windows/serviceResource.md)
- [Ressource ServiceSet](../reference/resources/windows/serviceSetResource.md)
- [Ressource User](../reference/resources/windows/userResource.md)
- [Ressource WindowsFeature](../reference/resources/windows/windowsFeatureResource.md)
- [Ressource WindowsFeatureSet](../reference/resources/windows/windowsFeatureSetResource.md)
- [Ressource WindowsOptionalFeature](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [Ressource WindowsOptionalFeatureSet](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [Ressource WindowsPackageCabResource](../reference/resources/windows/windowsPackageCabResource.md)
- [Ressource WindowsProcess](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a>Ressources de dépendance entre les nœuds

- [Ressource WaitForAll](../reference/resources/windows/waitForAllResource.md)
- [Ressource WaitForSome](../reference/resources/windows/waitForSomeResource.md)
- [Ressource WaitForAny](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a>Ressources Package Management

- [Ressource PackageManagement](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [Ressource PackageManagementSource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a>Ressources Linux

- [Ressource Archive Linux](../reference/resources/linux/lnxArchiveResource.md)
- [Ressource Environment Linux](../reference/resources/linux/lnxEnvironmentResource.md)
- [Ressources FileLine Linux](../reference/resources/linux/lnxFileLineResource.md)
- [Ressource File Linux](../reference/resources/linux/lnxFileResource.md)
- [Ressource Group Linux](../reference/resources/linux/lnxGroupResource.md)
- [Ressource Package Linux](../reference/resources/linux/lnxPackageResource.md)
- [Ressource Script Linux](../reference/resources/linux/lnxScriptResource.md)
- [Ressource Service Linux](../reference/resources/linux/lnxServiceResource.md)
- [Ressource SshAuthorizedKeys Linux](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [Ressource User Linux](../reference/resources/linux/lnxUserResource.md)
