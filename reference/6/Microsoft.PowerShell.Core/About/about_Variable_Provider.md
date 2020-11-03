---
description: Variable
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Variable
ms.openlocfilehash: c58ec641db0902088bf931d8bf4a48f5f7fa2ab8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206814"
---
# <a name="variable-provider"></a>Fournisseur de variables

## <a name="provider-name"></a>Nom du fournisseur
Variable

## <a name="drives"></a>Lecteurs

`Variable:`

## <a name="capabilities"></a>Fonctionnalités

**ShouldProcess**

## <a name="short-description"></a>Description courte

Fournit l’accès aux variables PowerShell et à leurs valeurs.

## <a name="detailed-description"></a>Description détaillée

Le fournisseur de **variables** PowerShell vous permet d’afficher, d’ajouter, de modifier, d’effacer et de supprimer des variables PowerShell dans la console active.

Le fournisseur **de variables PowerShell** prend en charge les variables créées par PowerShell, y compris les variables automatiques, les variables de préférence et les variables que vous créez.

La **variable** Drive est un espace de noms plat qui contient uniquement les objets variables. Les variables n'ont pas d'éléments enfants.

Le fournisseur **variable** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

PowerShell comprend également un ensemble d’applets de commande spécialement conçues pour afficher et modifier des variables. Lorsque vous utilisez des applets de commande de **variables** , vous n’avez pas besoin de spécifier le `Variable:` lecteur dans le nom. Cet article ne traite pas de l’utilisation des applets de commande **variables** .

- [Get-Variable](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [New-Variable](xref:Microsoft.PowerShell.Utility.New-Variable)
- [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> Vous pouvez également utiliser l’analyseur d’expression PowerShell pour créer, afficher et modifier les valeurs des variables sans utiliser les applets de commande. Lorsque vous travaillez avec des variables directement, utilisez un signe dollar ( `$` ) pour identifier le nom en tant que variable et l’opérateur d’assignation ( `=` ) pour établir et modifier sa valeur. Par exemple, `$p = Get-Process` crée la `p` variable et stocke les résultats d’une `Get-Process` commande dans celle-ci.

## <a name="types-exposed-by-this-provider"></a>Types exposés par ce fournisseur

Les variables peuvent être de plusieurs types différents. La plupart des variables sont des instances de la `PSVariable` classe. D’autres variables et leurs types sont répertoriés ci-dessous.

- La `?` variable est une instance de la `QuestionMarkVariable` classe.
- La `null` variable est une instance de la `NullVariable` classe.
- Les variables de nombre maximal sont des instances de la `SessionStateCapacityVariable` classe.
- `LocalVariable` les instances de contiennent des informations sur l’exécution actuelle, telles que :
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a>Navigation dans les lecteurs de variables

Le fournisseur **variable** expose son magasin de données dans le `Variable:` lecteur. Pour utiliser des variables, vous pouvez modifier votre emplacement sur le `Variable:` lecteur ( `Set-Location Variable:` ) ou vous pouvez utiliser n’importe quel autre lecteur PowerShell. Pour faire référence à une variable à partir d’un autre emplacement, utilisez le nom du lecteur ( `Variable:` ) dans le chemin d’accès.

```powershell
Set-Location Variable:
```

Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur. Par exemple, entrez :

```powershell
Set-Location C:
```

Vous pouvez également utiliser le fournisseur de **variables** à partir de n’importe quel autre lecteur PowerShell. Pour faire référence à une variable à partir d’un autre emplacement, utilisez le nom du lecteur `Variable:` dans le chemin d’accès.

> [!NOTE]
> PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs. Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location). et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="displaying-the-value-of-variables"></a>Affichage de la valeur des variables

### <a name="get-all-variables-in-the-current-session"></a>Obtient toutes les variables dans la session active

Cette commande obtient la liste de toutes les variables et de leur valeur dans la session active. Vous pouvez utiliser cette commande à partir de n’importe quel lecteur PowerShell.

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a>Obtenir une variable à l’aide du chemin d’accès au fournisseur

Cette commande récupère une valeur de variables en utilisant son chemin d’accès de fournisseur préfixé par le signe dollar ( `$` ). Cela a le même effet que le préfixe du nom des variables avec le signe dollar ( `$` ).

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a>Récupérer des variables à l’aide de caractères génériques

Cette commande obtient les variables dont le nom commence par « max ». Vous pouvez utiliser cette commande à partir de n’importe quel lecteur PowerShell.

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a>Obtient la valeur de l' ? variable

Cette commande utilise le `-LiteralPath` paramètre de la commande [« obtient-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem) pour récupérer la valeur de la `?` variable dans le `Variable:` lecteur. `?`Est un caractère générique dans les chemins d’accès, mais `Get-ChildItem` ne tente pas de résoudre les caractères génériques dans les valeurs du `-LiteralPath` paramètre.

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a>Obtient les variables ReadOnly et constantes

Cette commande obtient les variables qui ont les valeurs de `ReadOnly` ou `Constant` pour leur propriété **options** .

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a>Création de variables

### <a name="create-a-new-variable"></a>Créer une variable

Cette commande crée la `services` variable et stocke les résultats d’une `Get-Service` commande dans celle-ci. Étant donné que l’emplacement actuel se trouve dans le `Variable:` lecteur, la valeur du `-Path` paramètre est un point ( `.` ), qui représente l’emplacement actuel.

Les parenthèses entourant la `Get-Service` commande vérifient que la commande est exécutée avant la création de la variable. Sans les parenthèses, la valeur de la nouvelle variable serait une chaîne « Get-Service ».

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a>Créer une variable à l’aide d’un chemin d’accès absolu

Cette commande crée une `services` variable et stocke le résultat d’une `Get-Service` commande dans celle-ci.

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 Pour créer une variable sans valeur, omettez l'opérateur d'affectation.

## <a name="changing-variables"></a>Modification de variables

### <a name="rename-a-variable"></a>Renommer une variable

Cette commande utilise l' `Rename-Item` applet de commande pour modifier le nom de la `a` variable en `processes` .

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a>Modifier la valeur d’une variable

Cette commande utilise l' `Set-Item` applet de commande pour modifier la valeur de la `ErrorActionPreference` variable en « stop ».

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a>Copier une variable

Cette commande utilise la `Copy-Item` cmdlet pour copier la `processes` variable dans `old_processes` . Cela crée une variable nommée `old_processes` qui a la même valeur que la `processes` variable.

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a>Supprimer une variable

Cette commande supprime la `serv` variable de la session active. Vous pouvez utiliser cette commande dans n’importe quel lecteur PowerShell.

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a>Supprimer des variables à l’aide du paramètre-force

Cette commande supprime toutes les variables de la session active, à l’exception des variables dont la propriété **options** a la valeur `Constant` . Sans le `-Force` paramètre, la commande ne supprime pas les variables dont la propriété **options** a la valeur `ReadOnly` .

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a>Définition de la valeur d’une variable sur NULL

Cette commande utilise l' `Clear-Item` applet de commande pour remplacer la valeur de la `processes` variable par null.

```powershell
Clear-Item -Path Variable:processes
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
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a>Voir aussi

[about_Variables](../About/about_Variables.md)

[about_Automatic_Variables](../About/about_Automatic_Variables.md)

[about_Providers](../About/about_Providers.md)
