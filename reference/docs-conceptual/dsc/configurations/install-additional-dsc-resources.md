---
ms.date: 12/12/2018
keywords: dsc,powershell,ressource,galerie,configuration
title: Installer des ressources DSC supplémentaires
ms.openlocfilehash: 7a6a935349358e11a77d2f00c0bf88e0ad18c097
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "74417795"
---
# <a name="install-additional-dsc-resources"></a>Installer des ressources DSC supplémentaires

PowerShell inclut plusieurs ressources prêtes à l’emploi (OOB) pour Desired State Configuration (DSC). Le module **PSDesiredStateConfiguration** contient toutes les ressources OOB DSC disponibles sur votre instance spécifique de PowerShell.

Il s’agit d’une liste des ressources OOB incluses dans PowerShell 4.0 et d’une description des fonctionnalités de chaque ressource.

> [!NOTE]
> Cette liste est incomplète car le nombre de ressources OOB a augmenté avec chaque version de PowerShell.

|Ressource  |Description  |
|---------|---------|
|**File**|Contrôle l’état des fichiers et des répertoires. Copie les fichiers d’une **source** vers une **destination** et les met à jour à chaque modification de la **source** en comparant les dates, les sommes de contrôle et les hachages.|
|**Archive**|Décompresse les archives et un emplacement spécifié. Valide les archives avec une **somme de contrôle** spécifiée.|
|**Environment**|Gère les variables d’environnement.|
|**Groupe**|Gère les groupes locaux et contrôle l’appartenance au groupe.|
|**Journal**|Consigne des messages dans le journal des événements `Microsoft-Windows-Desired State Configuration/Analytic`.|
|**Package**|Installe ou désinstalle des packages à l’aide des paramètres **Arguments**, **LogPath**, **ReturnCode**, entre autres.|
|**Registre**|Gère les valeurs et clés de Registre.|
|**Script**|Vous permet de concevoir vos propres blocs de script [get-test-set](../resources/get-test-set.md).|
|**Service**|Configure les services Windows.|
|**Utilisateur** |Gère les attributs et les utilisateurs locaux.|
|**WindowsFeature**|Supprime des rôles et des fonctionnalités.|
|**WindowsProcess**|Configure les processus Windows.|

Les ressources OOB constituent un bon point de départ pour les opérations courantes. Si les ressources OOB ne répondent pas à vos besoins, vous pouvez écrire votre propre [ressource personnalisée](../resources/authoringResource.md). Avant d’écrire une ressource personnalisée pour résoudre votre problème, vous devriez consulter les nombreuses ressources DSC déjà créées par Microsoft et la Communauté PowerShell.

Vous trouverez des ressources DSC dans [PowerShell Gallery](https://www.powershellgallery.com/) et [GitHub](https://github.com/). Vous pouvez également installer des ressources DSC directement à partir de la console PowerShell à l’aide de [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Installation de PowerShellGet

Pour déterminer si vous disposez déjà de **PowerShellGet**, ou pour obtenir de l’aide sur son installation, consultez le guide suivant : [Installation de PowerShellGet](/powershell/scripting/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Recherche de ressources DSC à l’aide de PowerShellGet

Une fois **PowerShellGet** installé sur votre système, vous pouvez rechercher et installer des ressources DSC hébergées dans [PowerShell Gallery](https://www.powershellgallery.com/).

Tout d’abord, utilisez l’applet de commande [Find-DSCResource](/powershell/module/powershellget/find-dscresource) pour rechercher des ressources DSC. Lorsque vous exécutez `Find-DSCResource` pour la première fois, le message suivant vous invite à installer le « fournisseur NuGet ».

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

Appuyez sur « y » pour installer le fournisseur NuGet et afficher la liste des ressources DSC que vous pouvez installer à partir de PowerShell Gallery.

> [!NOTE]
> Cette liste n’est pas visible car elle est très longue.

Vous pouvez également spécifier le paramètre `-Name` à l’aide de caractères génériques, ou le paramètre `-Filter` sans caractères génériques pour affiner votre recherche. Cet exemple tente de trouver une ressource DSC « TimeZone » (fuseau horaire) en utilisant les caractères génériques.

> [!IMPORTANT]
> Actuellement, un bogue dans l’applet de commande `Find-DSCResource` empêche l’utilisation des caractères génériques dans les paramètres `-Name` et `-Filter`. Le second exemple ci-dessous montre une solution de contournement qui utilise `Where-Object`.

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

Vous pouvez également utiliser `Where-Object` pour rechercher des ressources DSC avec un filtrage plus précis. Cette approche sera plus lente que l’utilisation des paramètres de filtrage intégrés.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Pour plus d’informations sur le filtrage, consultez [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Installation de ressources DSC à l’aide de PowerShellGet

Pour installer une ressource DSC, utilisez l’applet de commande [Install-Module](/powershell/module/PowershellGet/Install-Module), en spécifiant le nom du module figurant sous **Module** dans vos résultats de recherche.

La ressource « TimeZone » existe dans le module « ComputerManagementDSC », et c’est donc ce module que l’exemple installe.

> [!NOTE]
> Si vous n’avez pas approuvé PowerShell Gallery, l’avertissement ci-dessous vous demande de confirmer et vous explique comment éviter ces invites lors des prochaines installations.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Appuyez sur « y » pour continuer l’installation du module. Après l’installation, vous pouvez vérifier que votre nouvelle ressource est installée à l’aide de [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Vous pouvez également afficher d’autres ressources de votre module nouvellement installé en spécifiant le paramètre `-ModuleName`.

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>Voir aussi

- [Présentation des ressources](../resources/resources.md)
