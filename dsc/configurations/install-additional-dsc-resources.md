---
ms.date: 12/12/2018
keywords: DSC, powershell, ressource, galerie, le programme d’installation
title: Installer des ressources DSC supplémentaires
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401695"
---
# <a name="install-additional-dsc-resources"></a>Installer des ressources DSC supplémentaires

PowerShell inclut plusieurs ressources Out-of-the-box pour Desired State Configuration (DSC). Le **PSDesiredStateConfiguration** module contient toutes les ressources OOB DSC disponibles sur votre instance spécifique de PowerShell.

Il s’agit d’une liste des ressources OOB incluses dans PowerShell 4.0 et une description des fonctionnalités de la ressource.

> [!NOTE]
> Il s’agit d’une liste incomplète, comme le nombre de ressources OOB a augmenté avec chaque version de PowerShell.

|Resource  |Description  |
|---------|---------|
|**File**|Contrôle l’état des fichiers et répertoires. Copie les fichiers à partir d’un **Source** à un **Destination** et les met à jour lorsque le **Source** modifications en comparant les dates, les sommes de contrôle et les hachages.|
|**Archive**|Décompresse les archives et un emplacement spécifié. Valide les archives avec un **somme de contrôle**.|
|**Environment**|Gère les variables d’environnement.|
|**Groupe**|Gère les groupes locaux et contrôle l’appartenance au groupe.|
|**Log**|Écrit des messages à la `Microsoft-Windows-Desired State Configuration/Analytic` journal des événements.|
|**Package**|Installe ou désinstalle des packages à l’aide **Arguments**, **LogPath**, **ReturnCode**, autres paramètres.|
|**Registry**|Gère les valeurs et clés de Registre.|
|**Script**|Vous pouvez ainsi concevoir votre propre [get-test-set](../resources/get-test-set.md) blocs de script.|
|**Service**|Configure les services Windows.|
|**User** |Gère les attributs et les utilisateurs locaux.|
|**WindowsFeature**|Gère les rôles et fonctionnalités.|
|**WindowsProcess**|Configure les processus Windows.|

Les ressources OOB autorisent un bon point de départ pour les opérations courantes. Si les ressources prêtes à l’emploi ne répondent pas à vos besoins, vous pouvez écrire votre propre [ressource personnalisée](../resources/authoringResource.md). Avant d’écrire une ressource personnalisée pour résoudre votre problème, vous devriez rechercher via la multitude de ressources DSC qui ont déjà été créés par Microsoft et la Communauté PowerShell.

Vous pouvez trouver les ressources DSC dans les deux le [PowerShell Gallery](https://www.powershellgallery.com/) et [GitHub](https://github.com/). Vous pouvez également installer les ressources DSC directement à partir de la console PowerShell à l’aide [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Installation de PowerShellGet

Pour déterminer si vous avez déjà **PowerShell** obtenir, ou pour obtenir de l’aide de l’installer, consultez le guide suivant : [Installation de PowerShellGet](/powershell/gallery/installing-psget)

## <a name="finding-dsc-resources-using-powershellget"></a>Recherche de ressources DSC à l’aide de PowerShellGet

Une fois **PowerShellGet** est installé sur votre système, vous pouvez rechercher et installer des ressources DSC hébergées dans le [PowerShell Gallery](https://www.powershellgallery.com/).

Tout d’abord, utilisez le [Find-DSCResource](/powershell/module/powershellget/find-dscresource) applet de commande pour rechercher des ressources DSC. Lorsque vous exécutez `Find-DSCResource` pour la première fois, vous voyez l’invite suivante pour installer le fournisseur « NuGet ».

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

Après en appuyant sur « y », le fournisseur « NuGet » est installé, vous voyez une liste de ressources DSC que vous pouvez installer à partir de PowerShell Gallery.

> [!NOTE]
> Liste n’est pas affichée, car il est très volumineux.

Vous pouvez également spécifier le `-Name` paramètre à l’aide des caractères génériques, ou `-Filter` paramètre sans caractères génériques pour limiter votre recherche. Cet exemple tente de trouver une ressource de « Fuseau horaire » DSC en utilisant les caractères génériques.

> [!IMPORTANT]
> Actuellement, il existe un bogue dans le `Find-DSCResource` applet de commande qui empêche l’utilisation des caractères génériques dans les deux le `-Name` et `-Filter` paramètres. Le deuxième exemple ci-dessous montre un à l’aide de la solution de contournement `Where-Object`.

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

Vous pouvez également utiliser `Where-Object` pour rechercher des ressources DSC avec un filtrage plus précis. Cette approche sera plus lente que la base de paramètres de filtrage.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Pour plus d’informations sur le filtrage, consultez [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Installation des ressources DSC à l’aide de PowerShellGet

Pour installer une ressource DSC, utilisez le [Install-Module](/powershell/module/PowershellGet/Install-Module) applet de commande, en spécifiant le nom du module figurant sous **Module** nom dans vos résultats de recherche.

La ressource « Fuseau horaire » existe dans le module « ComputerManagementDSC », de sorte qu’il que le module de cet exemple installe.

> [!NOTE]
> Si vous n’avez pas approuvé la PowerShell gallery, vous voyez l’avertissement ci-dessous demander de confirmation, et qui vous indiquent comment éviter les invites suivantes sur installe.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Appuyez sur « y » pour continuer l’installation du module. Après l’installation, vous pouvez vérifier que votre nouvelle ressource est installé à l’aide de [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

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

Vous pouvez également afficher les autres ressources dans votre module nouvellement installé, en spécifiant le `-ModuleName` paramètre.

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
