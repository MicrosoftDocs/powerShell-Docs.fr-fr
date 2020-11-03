---
description: Environnement
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Environment
ms.openlocfilehash: 354d6b0d07ac93a0b1a40543ca1e301a785ca934
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207133"
---
# <a name="environment-provider"></a>Fournisseur d’environnement

## <a name="provider-name"></a>Nom du fournisseur
Environnement

## <a name="drives"></a>Lecteurs

`Env:`

## <a name="capabilities"></a>Fonctionnalités

**ShouldProcess**

## <a name="short-description"></a>Description courte

Fournit l'accès aux variables d'environnement Windows.

## <a name="detailed-description"></a>Description détaillée

Le fournisseur d' **environnement** PowerShell vous permet d’extraire, d’ajouter, de modifier, d’effacer et de supprimer des variables d’environnement et des valeurs dans PowerShell.

Les variables d' **environnement** sont des variables nommées dynamiquement qui décrivent l’environnement dans lequel vos programmes s’exécutent. Windows et PowerShell utilisent des variables d’environnement pour stocker des informations persistantes qui affectent l’exécution du système et des processus. Contrairement aux variables PowerShell, les variables d’environnement ne sont pas soumises aux contraintes de portée.

Le lecteur d' **environnement** est un espace de noms plat contenant les variables d’environnement spécifiques à la session de l’utilisateur actuel. Les variables d’environnement n’ont pas d’éléments enfants.

Le fournisseur d' **environnement** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>Types exposés par ce fournisseur

Chaque variable d’environnement est une instance de la classe [System. Collections. DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) . Le nom de la variable est la clé du dictionnaire. La valeur de la variable d'environnement est la valeur du dictionnaire.

## <a name="navigating-the-environment-drive"></a>Navigation dans le lecteur de l’environnement

Le fournisseur d' **environnement** expose son magasin de données dans le `Env:` lecteur. Pour utiliser des variables d’environnement, modifiez votre emplacement sur le `Env:` lecteur ( `Set-Location Env:` ) ou utilisez un autre lecteur PowerShell. Pour référencer une variable d’environnement à partir d’un autre emplacement, utilisez le `Env:` nom du lecteur dans le chemin d’accès.

```powershell
Set-Location Env:
```

Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur. Par exemple, entrez :

```powershell
Set-Location C:
```

Vous pouvez également utiliser le fournisseur de l' **environnement** à partir de n’importe quel autre lecteur PowerShell. Pour référencer une variable d’environnement à partir d’un autre emplacement, utilisez le nom du lecteur `Env:` dans le chemin d’accès.

Le fournisseur d' **environnement** expose également les variables d’environnement à l’aide d’un préfixe variable de `$env:` .  La commande suivante affiche le contenu de la variable d’environnement **ProgramFiles** . Le `$env:` préfixe de variable peut être utilisé à partir de n’importe quel lecteur PowerShell.

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

Vous pouvez également modifier la valeur d’une variable d’environnement à l’aide du `$env:` préfixe de variable.  Toutes les modifications apportées se rapportent uniquement à la session PowerShell active tant qu’elle est active.

> [!NOTE]
> PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs. Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location). et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="getting-environment-variables"></a>Obtention de variables d’environnement

Cette commande répertorie toutes les variables d’environnement dans la session active.

```powershell
Get-Item -Path Env:
```

Vous pouvez utiliser cette commande à partir de n’importe quel lecteur PowerShell.

Le fournisseur d’environnement n’a pas de conteneurs, donc la commande ci-dessus a le même effet lorsqu’elle est utilisée avec `Get-ChildItem` .

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a>Obtenir une variable d’environnement sélectionnée

Cette commande obtient la `WINDIR` variable d’environnement.

```powershell
Get-ChildItem -Path Env:windir
```

Vous pouvez également utiliser le format de préfixe de variable.

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a>Créer une variable d’environnement

Cette commande crée la `USERMODE` variable d’environnement avec la valeur « non-admin ». La `-Path` valeur du paramètre crée le nouvel élément dans le `Env:` lecteur. La nouvelle variable d’environnement est utilisable uniquement dans la session PowerShell active tant qu’elle est active.

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a>Modification d’une variable d’environnement

### <a name="rename-an-environment-variable"></a>Renommer une variable d’environnement

Cette commande utilise l' `Rename-Item` applet de commande pour modifier le nom de la `USERMODE` variable d’environnement que vous avez créée `USERROLE` . Ne changez pas le nom d'une variable d'environnement utilisée par le système. Bien que ces modifications affectent uniquement la session active, elles peuvent provoquer un fonctionnement incorrect du système ou d'un programme.

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a>Modifier une variable d’environnement

Cette commande utilise l' `Set-Item` applet de commande pour modifier la valeur de la `USERROLE` variable d’environnement en « Administrator ».

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a>Copier une variable d’environnement

Cette commande copie la valeur de la `USERROLE` variable d’environnement dans la `USERROLE2` variable d’environnement.

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a>Supprimer une variable d’environnement

Cette commande supprime la `USERROLE2` variable d’environnement de la session active.

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a>Supprimer une variable d’environnement avec Clear-Item

Cette commande supprime la `USERROLE` variable d’environnement en effaçant sa valeur.

```powershell
Clear-Item -Path Env:USERROLE
```

## <a name="using-the-pipeline"></a>Utilisation du pipeline

Les applets de commande du fournisseur acceptent l’entrée du pipeline. Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.
Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.

## <a name="getting-help"></a>Obtenir de l’aide

Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.

Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a>Voir aussi

[about_Providers](../About/about_Providers.md)
