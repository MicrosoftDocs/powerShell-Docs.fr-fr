---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Nouveaux scénarios et fonctionnalités dans WMF 5.1
ms.openlocfilehash: 77b439e61c5802f8ddbc4a0f39923cc8c0c36fe9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190313"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Nouveaux scénarios et fonctionnalités dans WMF 5.1

> Remarque : Ces informations sont préliminaires et susceptibles d’être modifiées.

## <a name="powershell-editions"></a>Éditions de PowerShell

À compter de la version 5.1, PowerShell est disponible dans plusieurs éditions, dont les ensembles de fonctionnalités et la compatibilité de plateforme diffèrent.

- **Desktop Edition :** basée sur le .NET Framework, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions complètes de Windows telles que Server Core et Windows Desktop.
- **Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.

**En savoir plus sur l’utilisation des éditions de PowerShell**

- [Déterminer la version en cours d’exécution de PowerShell à l’aide de $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrer les résultats de Get-Module par CompatiblePSEditions à l’aide du paramètre PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Empêcher l’exécution des scripts, sauf en cas d’exécution sur une édition compatible de PowerShell](/powershell/gallery/psget/script/scriptwithpseditionsupport)
- [Déclarer la compatibilité d’un module avec des versions spécifiques de PowerShell](/powershell/gallery/psget/module/modulewithpseditionsupport)

## <a name="catalog-cmdlets"></a>Applets de commande de catalogue

Deux nouvelles applets de commande ont été ajoutées au module [Microsoft.PowerShell.Security](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security) pour générer et valider des fichiers catalogue Windows.

### <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

New-FileCatalog crée un fichier catalogue Windows pour un ensemble de dossiers et de fichiers.
Ce fichier catalogue contient des hachages pour tous les fichiers dans les chemins spécifiés.
Les utilisateurs peuvent distribuer l’ensemble des dossiers ainsi que le fichier catalogue correspondant représentant ces dossiers.
Ces informations sont utiles pour vérifier si des modifications ont été apportées aux dossiers depuis l’heure de création du catalogue.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Les versions de catalogues 1 et 2 sont prises en charge.
La version 1 utilise l’algorithme de hachage SHA1 pour créer des fichiers à hacher et la version 2 utilise SHA256.
La version de catalogue 2 n’est pas prise en charge sur *Windows Server 2008 R2* ni *Windows 7*.
Vous devez utiliser la version de catalogue 2 sur *Windows 8*, *Windows Server 2012* et les systèmes d’exploitation ultérieurs.

![](../images/NewFileCatalog.jpg)

Le fichier catalogue est ainsi créé.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Pour vérifier l’intégrité du fichier catalogue (Pester.cat dans l’exemple ci-dessus), signez-le à l’aide de l’applet de commande [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Test-FileCatalog valide le catalogue qui représente un ensemble de dossiers.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Cette applet de commande compare tous les fichiers à hacher et leurs chemins relatifs qui figurent dans le *catalogue* à ceux sur le *disque*.
Si elle détecte une incompatibilité entre les fichiers à hacher et les chemins, elle retourne le statut *ValidationFailed*.
Les utilisateurs peuvent récupérer toutes ces informations à l’aide du paramètre *-Detailed*.
Elle affiche également le statut de signature du catalogue dans la propriété *Signature*, ce qui revient à appeler l’applet de commande [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) sur le fichier catalogue.
Les utilisateurs peuvent également ignorer des fichiers lors de la validation à l’aide du paramètre *-FilesToSkip*.

## <a name="module-analysis-cache"></a>Cache d’analyse de module

À compter de la version 5.1, PowerShell fournit le contrôle suivant sur le fichier utilisé pour mettre en cache les données relatives à un module, comme les commandes qu’il exporte.

Par défaut, ce cache est stocké dans le fichier `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Le cache est normalement lu au démarrage lors de la recherche d’une commande, et les données y sont écrites sur un thread d’arrière-plan après l’importation d’un module.

Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement `$env:PSModuleAnalysisCachePath` avant de démarrer PowerShell.
Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants.
La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers.
Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple :

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Cela définit un appareil non valide comme chemin.
Si PowerShell ne peut pas écrire dans le chemin, aucune erreur n’est retournée, mais vous pouvez observer la présence d’une erreur signalée à l’aide d’un suivi :

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Lors de l’écriture du cache, PowerShell recherche les modules qui n’existent plus pour éviter que le cache ne devienne volumineux inutilement.
Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant ce qui suit :

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Cette variable d’environnement prend effet immédiatement dans le processus actif.

## <a name="specifying-module-version"></a>Spécification de la version de module

Dans WMF 5.1, `using module` se comporte de la même façon que les autres constructions liées aux modules dans PowerShell.
Auparavant, vous n’aviez aucun moyen de spécifier une version de module particulière. Si plusieurs versions étaient présentes, une erreur se produisait.

Dans WMF 5.1 :

- Vous pouvez utiliser [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290).
Cette table de hachage a le même format que `Get-Module -FullyQualifiedName`.

**Exemple :** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- S’il existe plusieurs versions du module, PowerShell utilise la **même logique de résolution** que `Import-Module` et ne retourne pas d’erreur (même comportement que `Import-Module` et `Import-DscResource`).

## <a name="improvements-to-pester"></a>Améliorations apportées à Pester

Dans WMF 5.1, la version de Pester qui est fournie avec PowerShell a été mise à jour de la version 3.3.5 vers 3.4.0, avec l’ajout de la validation https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, ce qui permet à Pester de mieux fonctionner sur Nano Server.

Vous pouvez examiner les modifications des versions 3.3.5 à 3.4.0 dans le fichier ChangeLog.md qui se trouve ici : https://github.com/pester/Pester/blob/master/CHANGELOG.md
