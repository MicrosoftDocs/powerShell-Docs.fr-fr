---
description: La variable d’environnement PSModulePath contient une liste d’emplacements de dossiers dans lesquels rechercher les modules et les ressources.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: 5d87f550b3aa8774ae81f68848d5aa252b2e5851
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524652"
---
# <a name="about-psmodulepath"></a>À propos de PSModulePath

La `$env:PSModulePath` variable d’environnement contient une liste d’emplacements de dossiers dans lesquels rechercher des modules et des ressources. PowerShell recherche de manière récursive chaque dossier pour les fichiers de module ( `.psd1` ou `.psm1` ).

Par défaut, les emplacements effectifs affectés à `$env:PSModulePath` sont les suivants :

- Emplacements à l’ensemble du système : ces dossiers contiennent des modules fournis avec PowerShell. Ces modules sont stockés dans le `$PSHOME\Modules` dossier. Il s’agit également de l’emplacement d’installation des modules de gestion Windows.

- Modules installés par l’utilisateur : il s’agit de modules installés par l’utilisateur.
  `Install-Module` possède un paramètre d' **étendue** qui vous permet de spécifier si le module est installé pour l’utilisateur actuel ou pour tous les utilisateurs. Pour plus d’informations, consultez [install-module](xref:PowerShellGet.Install-Module).

  - Sur Windows, l’emplacement de l’étendue **CurrentUser** propre à l’utilisateur est le `$HOME\Documents\PowerShell\Modules` dossier. L’emplacement de l’étendue **ALLUSERS** est `$env:ProgramFiles\PowerShell\Modules` .
  - Sur les systèmes non-Windows, l’emplacement de l’étendue **CurrentUser** propre à l’utilisateur est le `$HOME/.local/share/powershell/Modules` dossier. L’emplacement de l’étendue **ALLUSERS** est `/usr/local/share/powershell/Modules` .

En outre, les programmes d’installation qui installent des modules dans d’autres répertoires, tels que le répertoire Program Files, peuvent ajouter leurs emplacements à la valeur de `$env:PSModulePath` .

> [!NOTE]
> Sur Windows, l’emplacement spécifique à l’utilisateur est le `PowerShell\Modules` dossier situé dans le dossier **documents** de votre profil utilisateur. Le chemin d’accès spécifique de cet emplacement varie selon la version de Windows et si vous utilisez la redirection de dossiers ou non. Microsoft OneDrive peut également modifier l’emplacement de votre dossier **documents** . Vous pouvez vérifier l’emplacement de votre dossier **documents** à l’aide de la commande suivante : `[Environment]::GetFolderPath('MyDocuments')` .

## <a name="modifying-psmodulepath"></a>Modification de PSModulePath

Pour modifier les répertoires de module par défaut de la session active, utilisez le format de commande suivant pour modifier la valeur de la `PSModulePath` variable d’environnement.

Par exemple, pour ajouter le `C:\Program Files\Fabrikam\Modules` répertoire à la valeur de la variable d’environnement PSModulePath, tapez :

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

Le point-virgule ( `;` ) dans la commande sépare le nouveau chemin d’accès du chemin d’accès qui le précède dans la liste. Sur les plateformes non-Windows, le signe deux-points ( `:` ) sépare les emplacements de chemin d’accès dans la variable d’environnement.

Pour modifier la valeur de `PSModulePath` dans chaque session, ajoutez la commande précédente à votre profil PowerShell ou utilisez la méthode **SetEnvironmentVariable ne contient** de la classe d' **environnement** .

La commande suivante utilise la méthode **GetEnvironmentVariable** pour récupérer le paramètre de l’ordinateur de `PSModulePath` et la méthode **SetEnvironmentVariable ne contient** pour ajouter le `C:\Program Files\Fabrikam\Modules` chemin d’accès à la valeur.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

Pour ajouter un chemin d’accès au paramètre utilisateur, remplacez la valeur cible par **utilisateur**.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

Pour plus d’informations sur les méthodes de la classe **System. Environment** , consultez [méthodes d’environnement](/dotnet/api/system.environment).

## <a name="powershell-psmodulepath-construction"></a>Construction de PSModulePath PowerShell

La valeur de `$env:PSModulePath` est construite à chaque démarrage de PowerShell.
La valeur varie en fonction de la version de PowerShell et de son mode de lancement.

### <a name="windows-powershell-startup"></a>Démarrage de Windows PowerShell

Windows PowerShell utilise la logique suivante pour construire au `PSModulePath` démarrage :

- Si `PSModulePath` n’existe pas, combinez **CurrentUser** , **ALLUSERS** et les `$PSHOME` chemins des modules
- Si `PSModulePath` existe :
  - Si `PSModulePath` contient le `$PSHOME` chemin des modules :
    - Le chemin des modules **ALLUSERS** est inséré avant le `$PSHOME` chemin des modules
  - tierce
    - Utilisez simplement `PSModulePath` comme défini, car l’utilisateur a délibérément supprimé l' `$PSHOME` emplacement

Le chemin d’accès du module **CurrentUser** est préfixé uniquement si l’étendue de l’utilisateur `$env:PSModulePath` n’existe pas. Dans le cas contraire, l’étendue de l’utilisateur `$env:PSModulePath` est utilisée comme définie.

### <a name="powershell-core-6-startup"></a>Démarrage de PowerShell Core 6

PowerShell Core 6 n’utilise pas le contenu de `$env:PSModulePath` s’il détecte qu’il a été démarré à partir de PowerShell. Il le remplace par :

- **CurrentUser** modules chemin + **ALLUSERS** modules chemin + `$PSHOME` modules chemin + modules Windows PowerShell `$PSHOME` chemin d’accès.

### <a name="powershell-7-startup"></a>Démarrage de PowerShell 7

Dans Windows, pour la plupart des variables d’environnement, si la variable de portée utilisateur existe, un nouveau processus utilise cette valeur uniquement s’il existe une variable de portée ordinateur portant le même nom.

Dans PowerShell 7, `PSModulePath` est traité de façon similaire à la façon dont la `Path` variable d’environnement est traitée sur Windows. Sur Windows, `Path` est traité différemment des autres variables d’environnement. Quand un processus est démarré, Windows combine l’étendue de l’utilisateur `Path` avec l’étendue de l’ordinateur `Path` .

- Récupérer l’étendue de l’utilisateur `PSModulePath`
- Comparer pour traiter la `PSModulePath` variable d’environnement héritée
  - Si le même :
    - Ajoutez le **ALLUSERS** `PSModulePath` à la fin suivant la sémantique de la `Path` variable d’environnement.
    - Le `System32` chemin d’accès Windows provient de l’ordinateur défini `PSModulePath` , il n’est donc pas nécessaire de l’ajouter explicitement
  - Si différent, Treat comme si l’utilisateur l’avait explicitement modifié et n’ajoute pas **ALLUSERS**`PSModulePath`
- Préfixe avec utilisateur, système et `$PSHOME` chemins d’accès PS7 dans cet ordre
  - Si `powershell.config.json` contient une étendue d’utilisateur `PSModulePath` , utilisez-le à la place de la valeur par défaut pour l’utilisateur
  - Si `powershell.config.json` contient une portée système `PSModulePath` , utilisez-le à la place de la valeur par défaut pour le système.

Les systèmes UNIX n’ont pas de séparation entre les variables d’environnement utilisateur et système.
`PSModulePath` est hérité et les chemins d’accès spécifiques à PS7 sont préfixés s’ils ne sont pas déjà définis.

### <a name="starting-windows-powershell-from-powershell-7"></a>Démarrage de Windows PowerShell à partir de PowerShell 7

Pour cette discussion, _Windows PowerShell_ signifie à la fois `powershell.exe` et `powershell_ise.exe` .

La valeur de `$env:PSModulePath` est copiée vers `WinPSModulePath` avec les modifications suivantes :

- Supprimer PS7 le chemin d’accès au module utilisateur
- Supprimer PS7 le chemin d’accès au module système
- Supprimer PS7 le `$PSHOME` chemin d’accès au module

Les chemins d’accès PS7 sont supprimés afin que les modules PS7 ne soient pas chargés dans Windows PowerShell. La `WinPSModulePath` valeur est utilisée lors du démarrage de Windows PowerShell.

### <a name="starting-powershell-7-from-windows-powershell"></a>Démarrage de PowerShell 7 à partir de Windows PowerShell

Le démarrage de PowerShell 7 se poursuit comme avec l’ajout de chemins d’accès hérités ajoutés par Windows PowerShell. Étant donné que les chemins d’accès spécifiques à PS7 sont préfixés, il n’y a aucun problème fonctionnel.

### <a name="starting-powershell-6-from-powershell-7"></a>Démarrage de PowerShell 6 à partir de PowerShell 7

PowerShell Core 6 remplace `$env:PSModulePath` . Aucune modification n’est apportée.

### <a name="starting-powershell-7-from-powershell-6"></a>Démarrage de PowerShell 7 à partir de PowerShell 6

Le démarrage de PowerShell 7 se poursuit comme avec l’ajout de chemins d’accès hérités que PowerShell Core 6 a ajoutés. Étant donné que les chemins d’accès spécifiques à PS7 sont préfixés, il n’y a aucun problème fonctionnel.

## <a name="module-search-behavior"></a>Comportement de recherche de module

PowerShell effectue une recherche récursive dans chaque dossier du **PSModulePath** pour les fichiers de module ( `.psd1` ou `.psm1` ). Ce modèle de recherche permet d’installer plusieurs versions du même module dans des dossiers différents. Par exemple :

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules\PowerShellGet

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           8/14/2020  5:56 PM                1.0.0.1
d----           9/13/2019  3:53 PM                2.1.2
```

Par défaut, PowerShell charge le numéro de version le plus élevé d’un module lorsque plusieurs versions sont trouvées. Pour charger une version spécifique, utilisez `Import-Module` avec le paramètre **FullyQualifiedName** . Pour plus d’informations, voir [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).

## <a name="see-also"></a>Voir aussi

- [about_Modules](about_Modules.md)
- [Méthodes d’environnement](/dotnet/api/system.environment)
