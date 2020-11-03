---
description: Décrit les nouvelles fonctionnalités incluses dans Windows PowerShell 5,1.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/17/2018
online version: https://docs.microsoft.com/powershell/module/?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_5.1
ms.openlocfilehash: 567af048dd137c0287c6eba4ccc42a77055c0c92
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208741"
---
# <a name="about_windows_powershell_51"></a>about_Windows_PowerShell_5.1

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit les nouvelles fonctionnalités incluses dans Windows PowerShell 5,1.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Windows PowerShell 5,1 comprend de nouvelles fonctionnalités importantes qui étendent son utilisation, améliorent sa convivialité et vous permettent de contrôler et de gérer des environnements Windows plus facilement et de manière plus complète.

Windows PowerShell 5,1 est à compatibilité descendante. Les applets de commande, fournisseurs, modules, composants logiciels enfichables, scripts, fonctions et profils conçus pour Windows PowerShell 4,0, Windows PowerShell 3,0 et Windows PowerShell 2,0 fonctionnent généralement dans Windows PowerShell 5,1 sans aucune modification.

- Nouvelles applets de commande : groupes et utilisateurs locaux ; Get-ComputerInfo
- Améliorations de PowerShellGet avec l’utilisation imposée de modules signés et l’installation de modules JEA
- Ajout de la prise en charge de PackageManagement pour les conteneurs, l’installation de CBS, l’installation basée sur des fichiers .exe et les packages CAB
- Améliorations du débogage pour les classes DSC et PowerShell
- Améliorations de la sécurité, notamment l’utilisation imposée de modules signés par le catalogue provenant du serveur collecteur et lors de l’utilisation des applets de commande PowerShellGet
- Réponses à plusieurs demandes et problèmes des utilisateurs

Windows PowerShell 5,1 est installé par défaut sur Windows Server 2016 et Windows 10. Pour installer Windows PowerShell 5,1 sur Windows Server 2012 R2, Windows 8.1 Enterprise ou Windows 8.1 Pro, consultez [installer et configurer WMF 5,1](/powershell/scripting/wmf/setup/install-configure).
Veillez à lire les détails du téléchargement et à respecter la configuration requise avant d’installer Windows Management Framework 5,1.

Vous pouvez également en savoir plus sur les modifications apportées à Windows PowerShell 5,1 dans [Nouveautés de Windows PowerShell](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50).

## <a name="new-scenarios-and-features-in-wmf-51"></a>Nouveaux scénarios et fonctionnalités dans WMF 5.1

> Remarque : Ces informations sont préliminaires et susceptibles d’être modifiées.

### <a name="powershell-editions"></a>Éditions de PowerShell
À compter de la version 5.1, PowerShell est disponible dans plusieurs éditions, dont les ensembles de fonctionnalités et la compatibilité de plateforme diffèrent.

- **Édition Desktop :** repose sur le .NET Framework et offre une compatibilité avec les scripts et les modules ciblant les versions de PowerShell exécutées sur les éditions complètes de Windows, telles que Server Core et le Bureau Windows.
- **Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.

**En savoir plus sur l’utilisation des éditions de PowerShell**

- [Déterminer la version en cours d’exécution de PowerShell à l’aide de $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrer les résultats de Get-Module par CompatiblePSEditions à l’aide du paramètre PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Empêcher l’exécution des scripts, sauf en cas d’exécution sur une édition compatible de PowerShell](/powershell/scripting/gallery/concepts/script-psedition-support)
- [Déclarer la compatibilité d’un module avec des versions spécifiques de PowerShell](/powershell/scripting/gallery/concepts/module-psedition-support)

### <a name="catalog-cmdlets"></a>Applets de commande de catalogue

Deux nouvelles applets de commande ont été ajoutées au module [Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) pour générer et valider des fichiers catalogue Windows.

#### <a name="new-filecatalog"></a>New-FileCatalog

New-FileCatalog crée un fichier catalogue Windows pour un ensemble de dossiers et de fichiers.
Ce fichier catalogue contient des hachages pour tous les fichiers dans les chemins spécifiés. Les utilisateurs peuvent distribuer l’ensemble des dossiers ainsi que le fichier catalogue correspondant représentant ces dossiers. Ces informations sont utiles pour vérifier si des modifications ont été apportées aux dossiers depuis l’heure de création du catalogue.

```
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>]
 [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Les versions de catalogues 1 et 2 sont prises en charge. La version 1 utilise l’algorithme de hachage SHA1 pour créer des fichiers à hacher et la version 2 utilise SHA256. La version de catalogue 2 n’est pas prise en charge sur *Windows Server 2008 R2* ni *Windows 7* . Vous devez utiliser la version de catalogue 2 sur *Windows 8* , *Windows Server 2012* et les systèmes d’exploitation ultérieurs.

Pour vérifier l’intégrité du fichier catalogue (Pester.cat dans l’exemple ci-dessus), signez-le à l’aide de l’applet de commande [Set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature).

#### <a name="test-filecatalog"></a>Test-FileCatalog

Test-FileCatalog valide le catalogue qui représente un ensemble de dossiers.

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>]
 [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

Cette applet de commande compare tous les fichiers à hacher et leurs chemins relatifs qui figurent dans le *catalogue* à ceux sur le *disque* . Si elle détecte une incompatibilité entre les fichiers à hacher et les chemins, elle retourne le statut *ValidationFailed* . Les utilisateurs peuvent récupérer toutes ces informations à l’aide du paramètre *-Detailed* . Elle affiche également le statut de signature du catalogue dans la propriété *Signature* , ce qui revient à appeler l’applet de commande [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) sur le fichier catalogue. Les utilisateurs peuvent également ignorer des fichiers lors de la validation à l’aide du paramètre *-FilesToSkip* .

### <a name="module-analysis-cache"></a>Cache d’analyse de module

À compter de la version 5.1, PowerShell fournit le contrôle suivant sur le fichier utilisé pour mettre en cache les données relatives à un module, comme les commandes qu’il exporte.

Par défaut, ce cache est stocké dans le fichier `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Le cache est normalement lu au démarrage lors de la recherche d’une commande, et les données y sont écrites sur un thread d’arrière-plan après l’importation d’un module.

Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement `$env:PSModuleAnalysisCachePath` avant de démarrer PowerShell. Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants. La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers. Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple :

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Cela définit un appareil non valide comme chemin. Si PowerShell ne peut pas écrire dans le chemin, aucune erreur n’est retournée, mais vous pouvez observer la présence d’une erreur signalée à l’aide d’un suivi :

```powershell
Trace-Command -PSHost -Name Modules -Expression {
  Import-Module Microsoft.PowerShell.Management -Force
}
```

Lors de l’écriture du cache, PowerShell recherche les modules qui n’existent plus pour éviter que le cache ne devienne volumineux inutilement. Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant ce qui suit :

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Cette variable d’environnement prend effet immédiatement dans le processus actif.

### <a name="specifying-module-version"></a>Spécification de la version de module

Dans WMF 5.1, `using module` se comporte de la même façon que les autres constructions liées aux modules dans PowerShell. Auparavant, vous n’aviez aucun moyen de spécifier une version de module particulière. Si plusieurs versions étaient présentes, une erreur se produisait.

Dans WMF 5.1 :

* Vous pouvez utiliser [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor).
  Cette table de hachage a le même format que `Get-Module -FullyQualifiedName`.

  **Exemple :** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* S’il existe plusieurs versions du module, PowerShell utilise la **même logique de résolution** que `Import-Module` et ne retourne pas d’erreur (même comportement que `Import-Module` et `Import-DscResource`).

### <a name="improvements-to-pester"></a>Améliorations apportées à Pester

Dans WMF 5,1, la version de pester fournie avec PowerShell a été mise à jour de 3.3.5 à 3.4.0, avec l’ajout de GitHub [PR # 484](https://github.com/pester/Pester/pull/484), ce qui permet un meilleur comportement pour pester sur nano Server.

Vous pouvez examiner les modifications des versions 3.3.5 à 3.4.0 dans le fichier ChangeLog.md qui se trouve ici : https://github.com/pester/Pester/blob/master/CHANGELOG.md

## <a name="keywords"></a>MOT

Nouveautés de Windows PowerShell 5,1
