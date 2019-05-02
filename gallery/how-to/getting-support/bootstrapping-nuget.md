---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Amorcer NuGet
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084383"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Amorcer le fournisseur NuGet et NuGet.exe

NuGet.exe n’est pas inclus dans le dernier fournisseur NuGet. Pour les opérations de publication d’un module ou d’un script, PowerShellGet nécessite la version binaire exécutable, NuGet.exe. Le fournisseur NuGet est requis pour toutes les autres opérations, y compris *trouver*, *installer*, *enregistrer* et *désinstaller*.
PowerShellGet inclut une logique pour gérer soit un démarrage combiné du fournisseur NuGet et de NuGet.exe soit un démarrage du fournisseur NuGet uniquement. Dans les deux cas, une seule invite doit s’afficher. Si l’ordinateur n’est pas connecté à Internet, l’utilisateur ou administrateur doit copier une instance approuvée du fournisseur NuGet et/ou du fichier NuGet.exe sur l’ordinateur déconnecté.

> [!NOTE]
> À compter de la version 6, le fournisseur NuGet est inclus dans l’installation de PowerShell.

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Résolution des erreurs lorsque le fournisseur NuGet n’a pas été installé sur un ordinateur qui est connecté à Internet

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Résolution des erreurs lorsque le fournisseur NuGet est disponible et que NuGet.exe n’est pas disponible lors de l’opération de publication sur une machine connectée à Internet

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Résolution des erreurs lorsque ni le fournisseur NuGet ni NuGet.exe ne sont disponibles lors de l’opération de publication sur une machine connectée à Internet

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Démarrage manuel du fournisseur NuGet sur un ordinateur qui n’est pas connecté à Internet

Les processus détaillés ci-dessus supposent que l’ordinateur est connecté à Internet et peut télécharger des fichiers à partir d’un emplacement public. Si cela n’est pas possible, la seule option est de démarrer une machine en utilisant les processus ci-dessus et de copier manuellement le fournisseur sur le nœud isolé via un processus approuvé en mode hors connexion. Le cas d’utilisation le plus courant pour ce scénario est lorsqu’une galerie privée est disponible pour prendre en charge un environnement isolé.

Après avoir suivi le processus ci-dessus pour démarrer une machine connectée à Internet, vous trouverez des fichiers du fournisseur à l’emplacement :

`C:\Program Files\PackageManagement\ProviderAssemblies\`

La structure de dossiers et fichiers du fournisseur NuGet sera (éventuellement avec un autre numéro de version) :

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

Copiez ces dossiers et fichiers avec un processus approuvé sur les machines en mode hors connexion.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Démarrage manuel de NuGet.exe pour prendre en charge les opérations de publication sur un ordinateur qui n’est pas connecté à Internet

Outre le processus de démarrage manuel du fournisseur NuGet, si la machine doit être utilisée pour publier des modules ou des scripts dans une galerie privée à l’aide de l’applet de commande `Publish-Module` ou `Publish-Script`, le fichier exécutable binaire NuGet.exe sera nécessaire.

Le cas d’utilisation le plus courant pour ce scénario est lorsqu’une galerie privée est disponible pour prendre en charge un environnement isolé. Il existe deux options pour obtenir le fichier de NuGet.exe.

Une option consiste à démarrer une machine connectée à Internet et de copier les fichiers sur les machines en mode hors connexion à l’aide d’un processus approuvé. Après le démarrage de la machine connectée à Internet, le fichier binaire exécutable NuGet.exe se trouve dans un de ces deux dossiers :

Si l’applet de commande `Publish-Module` ou `Publish-Script` a été exécutée avec des autorisations élevées (en tant qu’administrateur) :

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Si les applets de commande ont été exécutées en tant qu’utilisateur sans autorisations élevées :

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

L’autre possibilité consiste à télécharger NuGet.exe sur le site web NuGet.Org : [https://dist.nuget.org/index.html](https://www.nuget.org/downloads). Pour les ordinateurs de production, veillez à sélectionner une version de NuGet ultérieure à 2.8.5.208 et étiquetée comme étant « recommandée ». N’oubliez pas de débloquer le fichier s’il a été téléchargé à l’aide d’un navigateur. Vous pouvez pour cela exécuter l’applet de commande `Unblock-File`.

Dans les deux cas, le fichier NuGet.exe peut être copié vers un emplacement quelconque dans `$env:path`, mais les emplacements standard sont :

Pour rendre l’exécutable disponible afin que tous les utilisateurs puissent utiliser les applets de commande `Publish-Module` et `Publish-Script` :

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Pour rendre l’exécutable disponible pour seulement un utilisateur spécifique, copiez vers l’emplacement dans le profil de cet utilisateur uniquement :

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
