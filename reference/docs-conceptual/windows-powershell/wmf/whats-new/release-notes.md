---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Notes de publication de WMF 5.x
ms.openlocfilehash: 3fc712dbcbe184c60ae248b260c8f6800f111fdd
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809875"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Notes de publication de Windows Management Framework (WMF) 5.x

## <a name="wmf-50-changes"></a>Modifications de WMF 5.0

- Ajout d’un nouveau flux **d’informations** structuré dans PowerShell 5.0
- Amélioration de DSC, notamment quatre nouvelles ressources DSC :
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Ajout de Just Enough Administration pour permettre une administration basée sur des rôles par la communication à distance PowerShell
- Extension du langage aux énumérations et aux classes définies par l’utilisateur dans PowerShell 5.0
- Amélioration des fonctionnalités de débogage dans PowerShell ISE et ajout du débogage à distance
- Ajout des modules PowerShellGet et PackageManagement
- Amélioration de la transcription et de la journalisation des scripts PowerShell
- Ajout des cmdlets CMS (Cryptographic Message Syntax)
- Ajout du module NetworkSwitchManager pour Windows dans WMF 5.0
- Ajout du module Microsoft.PowerShell.ODataUtils
- Ajout de la prise en charge de la Journalisation de l’inventaire logiciel (SIL)
- Plusieurs ajouts ou mises à jour de cmdlets en réponse aux problèmes et demandes des utilisateurs

## <a name="wmf-51-changes"></a>Modifications de WMF 5.1

WMF 5.1 comprend les composants PowerShell, WMI, WinRM et SIL (Journalisation de l’inventaire logiciel) qui ont été publiés avec Windows Server 2016. WMF 5.1, qui peut être installé sur Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 et 2012 R2, comporte plusieurs améliorations par rapport à WMF 5.0 :

- Nouvelles applets de commande
- Améliorations de PowerShellGet avec l’utilisation imposée de modules signés et l’installation de modules JEA
- Ajout de la prise en charge de PackageManagement pour les conteneurs, l’installation de CBS, l’installation basée sur des fichiers .exe et les packages CAB
- Améliorations du débogage pour les classes DSC et PowerShell
- Améliorations de la sécurité, notamment l’utilisation imposée de modules signés par le catalogue provenant du serveur collecteur et lors de l’utilisation des applets de commande PowerShellGet
- Réponses à plusieurs demandes et problèmes des utilisateurs

> [!IMPORTANT]
> Avant d’installer WMF 5.1 sur Windows Server 2008 ou Windows 7, confirmez que WMF 3.0 n’est pas installé. Pour plus d’informations, consultez [Prérequis de WMF 5.1 pour Windows Server 2008 R2 SP1 et Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).

## <a name="powershell-editions"></a>Éditions de PowerShell

À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui affichent une compatibilité distincte avec les plateformes et des ensembles de fonctionnalités variables.

- **Édition Desktop :** repose sur le .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et Bureau Windows.
- **Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>En savoir plus sur l’utilisation des éditions de PowerShell

- [Déterminer la version en cours d’exécution de PowerShell à l’aide de $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrer les résultats de Get-Module par CompatiblePSEditions à l’aide du paramètre PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Empêcher l’exécution des scripts, sauf en cas d’exécution sur une édition compatible de PowerShell](/powershell/scripting/gallery/concepts/script-psedition-support)
- [Déclarer la compatibilité d’un module avec des versions spécifiques de PowerShell](/powershell/scripting/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Cache d’analyse de module

À compter de la version 5.1, PowerShell fournit le contrôle suivant sur le fichier utilisé pour mettre en cache les données relatives à un module, comme les commandes qu’il exporte.

Par défaut, ce cache est stocké dans le fichier `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Le cache est normalement lu au démarrage lors de la recherche d’une commande, et les données y sont écrites sur un thread d’arrière-plan après l’importation d’un module.

Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement `$env:PSModuleAnalysisCachePath` avant de démarrer PowerShell. Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants. La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers. Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple :

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Cela définit un appareil non valide comme chemin. Si PowerShell ne peut pas écrire dans le chemin, aucune erreur n’est retournée, mais vous pouvez observer la présence d’une erreur signalée à l’aide d’un suivi :

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Lors de l’écriture du cache, PowerShell recherche les modules qui n’existent plus pour éviter que le cache ne devienne volumineux inutilement. Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant ce qui suit :

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Cette variable d’environnement prend effet immédiatement dans le processus actif.

## <a name="specifying-module-version"></a>Spécification de la version de module

Dans WMF 5.1, `using module` se comporte de la même façon que les autres constructions liées aux modules dans PowerShell.
Auparavant, vous n’aviez aucun moyen de spécifier une version de module particulière. Si plusieurs versions étaient présentes, une erreur se produisait.

Dans WMF 5.1 :

- Vous pouvez utiliser [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

  Cette table de hachage a le même format que `Get-Module -FullyQualifiedName`.

  **Exemple :** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- S’il existe plusieurs versions du module, PowerShell utilise la **même logique de résolution** que `Import-Module` et ne retourne pas d’erreur (même comportement que `Import-Module` et `Import-DscResource`).

## <a name="improvements-to-pester"></a>Améliorations apportées à Pester

Dans WMF 5.1, la version de Pester fournie avec PowerShell a été mise à jour de la version 3.3.5 à la version 3.4.0.
Cette mise à jour améliore le comportement de Pester sur Nano Server.

Pour voir les modifications apportées à Pester, consultez le [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) dans le référentiel GitHub.
