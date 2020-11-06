---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,installation
title: Écriture d’une ressource DSC personnalisée avec MOF
description: Cet article définit le schéma d’une ressource DSC personnalisée dans un fichier MOF et implémente la ressource dans un fichier de script PowerShell.
ms.openlocfilehash: e79a37699c468b2c55c307c96f1c193a2c1595b3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667179"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Écriture d’une ressource DSC personnalisée avec MOF

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Dans cet article, nous allons définir le schéma d’une ressource DSC Windows PowerShell personnalisée dans un fichier MOF et implémenter cette ressource dans un fichier de script Windows PowerShell.
Cette ressource personnalisée permet de créer et de gérer un site web.

## <a name="creating-the-mof-schema"></a>Création du schéma MOF

Le schéma définit les propriétés de votre ressource qui peuvent être configurées par un script de configuration DSC.

### <a name="folder-structure-for-a-mof-resource"></a>Structure de dossiers pour une ressource MOF

Pour implémenter une ressource personnalisée DSC avec un schéma MOF, créez la structure de dossiers suivante. Le schéma MOF est défini dans le fichier `Demo_IISWebsite.schema.mof` et le script de la ressource dans `Demo_IISWebsite.psm1`. Si vous le voulez, vous pouvez créer un fichier de manifeste de module (psd1).

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

> [!NOTE]
> Il est nécessaire de créer un dossier nommé DSCResources sous le dossier de niveau supérieur, et que le dossier de chaque ressource doit porter le même nom que la ressource.

### <a name="the-contents-of-the-mof-file"></a>Le contenu du fichier MOF

Voici un exemple de fichier MOF qui peut être utilisé pour une ressource de site web personnalisée. Pour suivre cet exemple, enregistrez ce schéma dans un fichier et appelez le fichier `Demo_IISWebsite.schema.mof`.

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Notez les éléments suivants concernant le code ci-dessus :

- `FriendlyName` définit le nom que vous pouvez utiliser pour faire référence à cette ressource personnalisée dans les scripts de configuration DSC. Dans cet exemple, `Website` équivaut au nom convivial `Archive` de la ressource Archive intégrée.
- La classe que vous définissez pour la ressource personnalisée doit dériver de `OMI_BaseResource`.
- Le qualificateur de type (`[Key]`) d’une propriété indique que cette propriété identifie de manière unique l’instance de ressource. Au moins une propriété `[Key]` est requise.
- Le qualificateur `[Required]` indique que la propriété est obligatoire (une valeur doit être spécifiée dans un script de configuration qui utilise cette ressource).
- Le qualificateur `[write]` indique que cette propriété est facultative quand vous utilisez la ressource personnalisée dans un script de configuration. Le qualificateur `[read]` indique qu’une propriété ne peut pas être définie par une configuration et qu’elle ne peut être utilisée qu’à des fins de création de rapports.
- `Values` limite les valeurs pouvant être affectées à la propriété à la liste des valeurs définies dans `ValueMap`. Pour plus d’informations, consultez [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).
- Il est recommandé d’utiliser une propriété appelée `Ensure` avec les valeurs `Present` et `Absent` dans votre ressource pour maintenir un style cohérent entre les ressources DSC intégrées.
- Nommez le fichier de schéma de la ressource personnalisée comme suit : `classname.schema.mof`, où `classname` est l’identificateur qui suit le mot clé `class` dans votre définition de schéma.

### <a name="writing-the-resource-script"></a>Écriture du script de la ressource

Le script de la ressource implémente la logique de la ressource. Dans ce module, vous devez inclure les trois fonctions `Get-TargetResource`, `Set-TargetResource` et `Test-TargetResource`. Les trois fonctions doivent accepter un jeu de paramètres identique à l’ensemble de propriétés définies dans le schéma MOF que vous avez créé pour votre ressource. Dans ce document, nous appelons cet ensemble de propriétés « propriétés de ressource ». Stockez ces trois fonctions dans un fichier appelé `<ResourceName>.psm1`. Dans l’exemple suivant, les fonctions sont stockées dans un fichier appelé `Demo_IISWebsite.psm1`.

> [!NOTE]
> Quand vous exécutez le même script de configuration plusieurs fois sur votre ressource, vous ne devez pas obtenir d’erreur et la ressource doit avoir le même état que lorsque le script n’est exécuté qu’une seule fois. Pour cela, assurez-vous que vos fonctions `Get-TargetResource` et `Test-TargetResource` ne modifient pas la ressource, et que le fait d’appeler la fonction `Set-TargetResource` plusieurs fois de suite avec les mêmes valeurs de paramètres équivaut toujours à un appel unique.

Dans l’implémentation de la fonction `Get-TargetResource`, utilisez les valeurs de propriétés de ressource de clé qui sont fournies comme paramètres pour vérifier l’état de l’instance de la ressource spécifiée. Cette fonction doit retourner une table de hachage comprenant toutes les propriétés de ressource comme clés, ainsi que les valeurs réelles de ces propriétés comme valeurs correspondantes. Le code suivant montre un exemple.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance
# specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <#
          Insert logic that uses the mandatory parameter values to get the website and
          assign it to a variable called $Website
          Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise
        #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
            Name = $Website.Name
            Ensure = $ensureResult
            PhysicalPath = $Website.physicalPath
            State = $Website.state
            ID = $Website.id
            ApplicationPool = $Website.applicationPool
            Protocol = $Website.bindings.Collection.protocol
            Binding = $Website.bindings.Collection.bindingInformation
        }

        $getTargetResourceResult
}
```

Selon les valeurs qui sont spécifiées pour les propriétés de ressource dans le script de configuration, la fonction `Set-TargetResource` doit effectuer l’une des opérations suivantes :

- Créer un site web
- Mettre à jour un site web existant
- Supprimer un site web existant

L'exemple suivant illustre ce comportement.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <#
        If Ensure is set to "Present" and the website specified in the mandatory input parameters
          does not exist, then create it using the specified parameter values
        Else, if Ensure is set to "Present" and the website does exist, then update its properties
          to match the values provided in the non-mandatory parameter values
        Else, if Ensure is set to "Absent" and the website does not exist, then do nothing
        Else, if Ensure is set to "Absent" and the website does exist, then delete the website
    #>
}
```

Enfin, la fonction `Test-TargetResource` doit prendre le même jeu de paramètres que `Get-TargetResource` et `Set-TargetResource`. Dans votre implémentation de `Test-TargetResource`, vérifiez l’état de l’instance de ressource qui est spécifié dans les paramètres de clé. Si l’état réel de l’instance de ressource ne correspond pas aux valeurs spécifiées dans le jeu de paramètres, retournez `$false`. Sinon, retournez `$true`.

Le code suivant implémente la fonction `Test-TargetResource`.

```powershell
function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([System.Boolean])]
    param
    (
        [ValidateSet("Present","Absent")]
        [System.String]
        $Ensure,

        [parameter(Mandatory = $true)]
        [System.String]
        $Name,

        [parameter(Mandatory = $true)]
        [System.String]
        $PhysicalPath,

        [ValidateSet("Started","Stopped")]
        [System.String]
        $State,

        [System.String[]]
        $Protocol,

        [System.String[]]
        $BindingData,

        [System.String]
        $ApplicationPool
    )

    # Get the current state
    $currentState = Get-TargetResource -Ensure $Ensure -Name $Name -PhysicalPath $PhysicalPath -State $State -ApplicationPool $ApplicationPool -BindingInfo $BindingInfo -Protocol $Protocol

    # Write-Verbose "Use this cmdlet to deliver information about command processing."

    # Write-Debug "Use this cmdlet to write debug information while troubleshooting."

    # Include logic to
    $result = [System.Boolean]
    # Add logic to test whether the website is present and its status matches the supplied
    # parameter values. If it does, return true. If it does not, return false.
    $result
}
```

> [!NOTE]
> Pour faciliter le débogage, utilisez l’applet de commande `Write-Verbose` dans l’implémentation des trois fonctions précédentes. Cette applet de commande écrit du texte dans le flux de message détaillé. Par défaut, le flux de message détaillé n’est pas affiché, mais vous pouvez l’afficher en modifiant la valeur de la variable **$VerbosePreference** ou en utilisant le paramètre **Verbose** dans DSC cmdlets = new.

### <a name="creating-the-module-manifest"></a>Création du manifeste de module

Enfin, utilisez la cmdlet `New-ModuleManifest` pour définir un fichier `<ResourceName>.psd1` pour votre module de ressource personnalisé. Quand vous appelez cette applet de commande, référencez le fichier de module de script (.psm1) décrit dans la section précédente. Ajoutez `Get-TargetResource`, `Set-TargetResource` et `Test-TargetResource` à la liste des fonctions à exporter. Voici un exemple de fichier de manifeste.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a>Prise en charge de PsDscRunAsCredential

> [!Note]
> **PsDscRunAsCredential** est pris en charge dans PowerShell 5.0 et versions ultérieures.

La propriété **PsDscRunAsCredential** peut être utilisée dans le bloc de ressources [Configurations DSC](../configurations/configurations.md) pour spécifier que la ressource doit être exécutée sous un jeu d’informations d’identification spécifié. Pour plus d’informations, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](../configurations/runAsUser.md).

Pour accéder au contexte utilisateur dans une ressource personnalisée, vous pouvez utiliser la variable automatique `$PsDscContext`.

Par exemple, le code suivant écrit le contexte de l’utilisateur sous lequel la ressource s’exécute dans le flux de sortie des messages :

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a>Redémarrage du nœud

Si les actions effectuées dans votre fonction `Set-TargetResource` nécessitent un redémarrage, vous pouvez utiliser un indicateur global pour signaler au Gestionnaire de configuration local qu’il faut redémarrer le nœud. Ce redémarrage se produit juste après l’exécution de la fonction `Set-TargetResource`.

À l’intérieur de votre fonction `Set-TargetResource`, ajoutez la ligne de code suivante.

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

Pour que le Gestionnaire de configuration local redémarre le nœud, il faut que l’indicateur **RebootNodeIfNeeded** ait la valeur `$true`.
Le paramètre **ActionAfterReboot** doit également être défini sur **ContinueConfiguration** , qui est la valeur par défaut. Pour plus d’informations sur la configuration du Gestionnaire de configuration local, consultez [Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md) ou [Configuration du Gestionnaire de configuration local (v4)](../managing-nodes/metaConfig4.md).
