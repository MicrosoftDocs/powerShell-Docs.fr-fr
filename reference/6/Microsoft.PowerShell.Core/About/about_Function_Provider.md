---
description: Fonction
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Function
ms.openlocfilehash: 0323433d5ab9114dd1bb21afc47b7fa7db3d6f8f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207094"
---
# <a name="function-provider"></a>Fournisseur de fonctions

## <a name="provider-name"></a>Nom du fournisseur
Fonction

## <a name="drives"></a>Lecteurs

`Function:`

## <a name="capabilities"></a>Fonctionnalités

**ShouldProcess**

## <a name="short-description"></a>Description courte

Fournit l’accès aux fonctions définies dans PowerShell.

## <a name="detailed-description"></a>Description détaillée

Le fournisseur de **fonctions** PowerShell vous permet d’accéder, d’ajouter, de modifier, d’effacer et de supprimer les fonctions et les filtres dans PowerShell.

Une fonction est un bloc de code nommé qui effectue une action. Quand vous tapez le nom de la fonction, le code de la fonction s'exécute. Un filtre est un bloc de code nommé qui établit les conditions d'une action. Vous pouvez taper le nom du filtre à la place de la condition, par exemple dans une `Where-Object` commande.

La **fonction** Drive est un espace de noms plat qui contient uniquement les objets Function et Filter. Ni les fonctions ni les filtres n'ont des éléments enfants.

Le fournisseur de **fonctions** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>Types exposés par ce fournisseur

Chaque fonction est une instance de la classe [System. Management. Automation. FunctionInfo](/dotnet/api/system.management.automation.functioninfo) . Chaque filtre est une instance de la classe [System. Management. Automation. FilterInfo](/dotnet/api/system.management.automation.filterinfo) .

## <a name="navigating-the-function-drive"></a>Navigation dans le lecteur de fonction

Le fournisseur de **fonctions** expose son magasin de données dans le `Function:` lecteur. Pour utiliser des fonctions, vous pouvez modifier votre emplacement sur le `Function:` lecteur ( `Set-Location Function:` ). Vous pouvez également travailler à partir d’un autre lecteur PowerShell. Pour faire référence à une fonction à partir d’un autre emplacement, utilisez le nom du lecteur ( `Function:` ) dans le chemin d’accès.

```powershell
Set-Location Function:
```

Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur. Par exemple, entrez :

```powershell
Set-Location C:
```

Vous pouvez également utiliser le fournisseur de **fonctions** à partir de n’importe quel autre lecteur PowerShell. Pour faire référence à une fonction à partir d’un autre emplacement, utilisez le nom du lecteur `Function:` dans le chemin d’accès.

> [!NOTE]
> PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs. Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location). et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="getting-functions"></a>Obtention de fonctions

Cette commande obtient la liste de toutes les fonctions dans la session active. Vous pouvez utiliser cette commande à partir de n’importe quel lecteur PowerShell.

```powershell
Get-ChildItem -Path Function:
```

Le fournisseur de fonctions n’a pas de conteneur, donc la commande ci-dessus a le même effet lorsqu’elle est utilisée avec `Get-ChildItem` .

```powershell
Get-ChildItem -Path Function:
```

Vous pouvez récupérer la définition d’une fonction en accédant à la propriété de **définition** , comme indiqué ci-dessous.

```powershell
(Get-Item -Path function:more).Definition
```

Vous pouvez également récupérer la définition d’une fonction à l’aide de son chemin d’accès de fournisseur préfixé par le signe dollar ( `$` ).

```powershell
$function:more
```

### <a name="getting-selected-functions"></a>Obtention des fonctions sélectionnées

Cette commande obtient la `man` fonction à partir du `Function:` lecteur. Elle utilise l' `Get-Item` applet de commande pour récupérer la fonction. L’opérateur de pipeline ( `|` ) envoie le résultat à `Format-Table` . Le `-Wrap` paramètre dirige le texte qui ne tient pas sur la ligne sur la ligne suivante. Le `-Autosize` paramètre redimensionne les colonnes de la table pour s’adapter au texte.

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a>Utilisation des chemins d’accès des fournisseurs de fonctions

Ces commandes obtiennent toutes les deux la fonction nommée `c:` . La première commande peut être utilisée dans n'importe quel lecteur. La deuxième commande est utilisée dans le `Function:` lecteur. Comme le nom se termine par un signe deux-points, qui est la syntaxe pour un lecteur, vous devez qualifier le chemin d'accès avec le nom du lecteur. Dans le `Function:` lecteur, vous pouvez utiliser l’un ou l’autre format. Dans la deuxième commande, le point ( `.` ) représente l’emplacement actuel.

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a>Création d’une fonction

Cette commande utilise l' `New-Item` applet de commande pour créer une fonction appelée `Win32:` .
L'expression entre accolades est le bloc de script qui est représenté par le nom de la fonction.

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

Vous pouvez également créer une fonction en la tapant à la ligne de commande PowerShell. Par exemple, éditeur `Function:Win32: {Set-Location C:\Windows\System32}` . Si vous êtes dans le `Function:` lecteur, vous pouvez omettre le nom du lecteur.

## <a name="deleting-a-function"></a>Suppression d’une fonction

Cette commande supprime la `more:` fonction de la session active.

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a>Modification d’une fonction

Cette commande utilise l' `Set-Item` applet de commande pour modifier la `prompt` fonction afin qu’elle affiche l’heure avant le chemin d’accès.

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a>Renommer une fonction

Cette commande utilise l' `Rename-Item` applet de commande pour modifier le nom de la `help` fonction en `gh` .

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a>Copie d’une fonction

Cette commande copie la `prompt` fonction dans `oldPrompt` , en créant en fait un nouveau nom pour le bloc de script associé à la fonction prompt.
Vous pouvez utiliser ceci pour enregistrer la fonction prompt d'origine si vous projetez de la changer.
La propriété **options** de la nouvelle fonction a la valeur `None` . Pour modifier la valeur de la propriété **options** , utilisez `Set-Item` .

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.

### <a name="options-systemmanagementautomationscopeditemoptions"></a>Options < [System. Management. Automation. ScopedItemOptions] >

Détermine la valeur de la propriété **options** d’une fonction.

- `None`: Aucune option. `None` est la valeur par défaut.
- `Constant`: La fonction ne peut pas être supprimée et ses propriétés ne peuvent pas être modifiées. `Constant` est disponible uniquement lorsque vous créez une fonction.
  Vous ne pouvez pas modifier l’option d’une fonction existante en `Constant` .
- `Private`: La fonction est visible uniquement dans la portée actuelle
- (pas dans les portées enfants).
- `ReadOnly`: Les propriétés de la fonction ne peuvent pas être modifiées, sauf en utilisant le `-Force` paramètre. Vous pouvez utiliser `Remove-Item` pour supprimer la fonction.
- `AllScope`: La fonction est copiée vers toutes les nouvelles étendues créées.

### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)

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
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a>Voir aussi

[about_Functions](../About/about_Functions.md)

[about_Providers](../About/about_Providers.md)
