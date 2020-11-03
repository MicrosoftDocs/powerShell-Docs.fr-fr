---
description: Alias
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Alias
ms.openlocfilehash: 994bd183f047123502f7e152c59b0d8aeb32a1b9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208082"
---
# <a name="alias-provider"></a>Fournisseur alias

## <a name="provider-name"></a>Nom du fournisseur

Alias

## <a name="drives"></a>Lecteurs

`Alias:`

## <a name="capabilities"></a>Fonctionnalités

**ShouldProcess**

## <a name="short-description"></a>Description courte

Fournit l’accès aux alias PowerShell et aux valeurs qu’ils représentent.

## <a name="detailed-description"></a>Description détaillée

Le fournisseur d' **alias** PowerShell vous permet d’accéder, d’ajouter, de modifier, d’effacer et de supprimer des alias dans PowerShell.

Un alias est un autre nom pour une applet de commande, une fonction ou un fichier exécutable, y compris des scripts. PowerShell comprend un ensemble d’alias intégrés. Vous pouvez ajouter vos propres alias à la session active et à votre profil PowerShell.

Le lecteur d' **alias** est un espace de noms plat qui contient uniquement les objets d’alias.
Les alias n'ont pas d'éléments enfants.

Le fournisseur **alias** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

PowerShell comprend un ensemble d’applets de commande conçues pour afficher et modifier des alias. Lorsque vous utilisez des applets de commande d' **alias** , vous n’avez pas besoin de spécifier le `Alias:` lecteur dans le nom. Cet article ne traite pas de l’utilisation des applets de commande d' **alias** .

- [Export-Alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Import-Alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Set-Alias](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a>Types exposés par ce fournisseur

Chaque alias est une instance de la classe [System. Management. Automation. AliasInfo](/dotnet/api/system.management.automation.aliasinfo) .

## <a name="navigating-the-alias-drive"></a>Navigation dans le lecteur d’alias

Le fournisseur **alias** expose son magasin de données dans le `Alias:` lecteur. Pour utiliser des alias, vous pouvez modifier votre emplacement sur le lecteur à l' `Alias:` aide de la commande suivante :

```powershell
Set-Location Alias:
```

Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur. Par exemple, entrez :

```powershell
Set-Location C:
```

Vous pouvez également utiliser le fournisseur alias à partir de n’importe quel autre lecteur PowerShell. Pour référencer un alias à partir d’un autre emplacement, utilisez le `Alias:` nom du lecteur dans le chemin d’accès.

> [!NOTE]
> PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs. Les commandes telles que `dir` et `ls` sont maintenant des alias pour l’expression [« obtenir-ChildItem »](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location). et `pwd` est un alias pour la récupération de l' [emplacement](xref:Microsoft.PowerShell.Management.Get-Location).

### <a name="displaying-the-contents-of-the-alias-drive"></a>Affichage du contenu du lecteur Alias :

Cette commande obtient la liste de tous les alias lorsque l’emplacement actuel est le `Alias:` lecteur. Elle utilise un caractère générique `*` pour indiquer tout le contenu de l’emplacement actuel.

```powershell
PS Alias:\> Get-Item -Path *
```

Dans le `Alias:` lecteur, un point `.` , qui représente l’emplacement actuel, et un caractère générique `*` , qui représente tous les éléments de l’emplacement actuel, ont le même effet. Par exemple, `Get-Item -Path .` ou `Get-Item \*` produisent le même résultat.

Le fournisseur alias n’a pas de conteneurs, donc la commande ci-dessus a le même effet lorsqu’elle est utilisée avec `Get-ChildItem` .

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a>Obtenir un alias sélectionné

Cette commande obtient l' `ls` alias.
Étant donné qu’il comprend le chemin d’accès, vous pouvez l’utiliser dans n’importe quel lecteur PowerShell.

```powershell
Get-Item -Path Alias:ls
```

Si vous êtes dans le `Alias:` lecteur, vous pouvez omettre le nom du lecteur dans le chemin d’accès.

Vous pouvez également récupérer la définition d’un alias en préfixant le chemin d’accès du fournisseur avec le signe dollar ( `$` ).

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a>Obtenir tous les alias pour une applet de commande spécifique

Cette commande obtient une liste des alias associés à l’applet de commande `Get-ChildItem` . Elle utilise la propriété de **définition** , qui stocke le nom de l’applet de commande.

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a>Création d’alias

### <a name="create-an-alias-from-the-alias-drive"></a>Créer un alias à partir du lecteur Alias :

Cette commande crée l' `serv` alias pour l' `Get-Service` applet de commande. Étant donné que l’emplacement actuel se trouve dans le `Alias:` lecteur, le `-Path` paramètre n’est pas nécessaire.

Cette commande utilise également le `-Options` paramètre Dynamic pour définir l’option **options AllScope** sur l’alias. Le `-Options` paramètre est disponible dans l' `New-Item` applet de commande uniquement lorsque vous êtes dans le `Alias:` lecteur. Le point ( `.` ) indique le répertoire actif, qui est le lecteur d’alias.

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a>Créer un alias avec un chemin d’accès absolu

Vous pouvez créer un alias pour tout élément qui appelle une commande.
Cette commande crée l' `np` alias pour `Notepad.exe` .

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a>Créer un alias pour une nouvelle fonction

Vous pouvez créer un alias pour n'importe quelle fonction. Vous pouvez utiliser cette fonctionnalité pour créer un alias qui inclut à la fois une applet de commande et ses paramètres.

La première commande crée la `CD32` fonction, qui remplace le répertoire actif par le `System32` répertoire. La deuxième commande crée l' `go` alias pour la `CD32` fonction.

Une fois la commande terminée, vous pouvez utiliser `CD32` ou `go` pour appeler la fonction.

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a>Modification des alias

### <a name="change-the-options-of-an-alias"></a>Modifier les options d’un alias

Vous pouvez utiliser l' `Set-Item` applet de commande avec le `-Options` paramètre Dynamic pour modifier la valeur de la `-Options` propriété d’un alias.

Cette commande définit les options **options AllScope** et **ReadOnly** pour l' `dir` alias. La commande utilise le `-Options` paramètre dynamique de l' `Set-Item` applet de commande. Le `-Options` paramètre est disponible dans `Set-Item` lorsque vous l’utilisez avec l' **alias** ou le fournisseur de **fonctions** .

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a>Modifier une commande référencée d’alias

Cette commande utilise la `Set-Item` cmdlet pour modifier l' `gp` alias afin qu’il représente l' `Get-Process` applet de commande au lieu de l’applet de commande `Get-ItemProperty` .
Le `-Force` paramètre est obligatoire, car la valeur de la propriété **options** de l' `gp` alias est définie sur `ReadOnly` . Étant donné que la commande est envoyée à partir du `Alias:` lecteur, le lecteur n’est pas spécifié dans le chemin d’accès.

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

La modification affecte les quatre propriétés qui définissent l'association entre l'alias et la commande. Pour afficher l’effet de la modification, tapez la commande suivante :

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a>Renommer un alias

Cette commande utilise l' `Rename-Item` applet de commande pour remplacer l' `popd` alias par `pop` .

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a>Copie d’un alias

Cette commande copie l' `pushd` alias afin qu’un nouvel `push` alias soit créé pour l' `Push-Location` applet de commande.

Lorsque le nouvel alias est créé, sa propriété **Description** a une valeur null.
Et, sa propriété **option** a la valeur `None` . Si la commande est émise à partir du `Alias:` lecteur, vous pouvez omettre le nom du lecteur de la valeur du `-Path` paramètre.

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a>Suppression d’un alias

Cette commande supprime l' `serv` alias de la session active.
Vous pouvez utiliser cette commande dans n’importe quel lecteur PowerShell.

```powershell
Remove-Item -Path Alias:serv
```

Cette commande supprime les alias qui commencent par « s ».
Elle ne supprime pas les alias en lecture seule.

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a>Supprimer les alias en lecture seule

Cette commande supprime tous les alias de la session active, à l’exception de ceux dont la `Constant` propriété **options** a la valeur. Le `-Force` paramètre permet à la commande de supprimer des alias dont la propriété **options** a la valeur `ReadOnly` .

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.

### <a name="options-systemmanagementautomationscopeditemoptions"></a>Options [System. Management. Automation. ScopedItemOptions]

Détermine la valeur de la propriété **options** d’un alias.

- **None** : aucune option. Cette valeur est la valeur par défaut.
- **Constante** : l’alias ne peut pas être supprimé et ses propriétés ne peuvent pas être modifiées.
  La **constante** n’est disponible que lorsque vous créez un alias. Vous ne pouvez pas modifier l’option d’un alias existant en **constant** .
- **Privé** : l’alias est visible uniquement dans l’étendue actuelle, et non dans les étendues enfants.
- **ReadOnly** : les propriétés de l’alias ne peuvent pas être modifiées, sauf en utilisant le `-Force` paramètre. Vous pouvez utiliser `Remove-Item` pour supprimer l’alias.
- **Options AllScope** : l’alias est copié vers toutes les nouvelles étendues créées.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

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
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a>Voir aussi

[about_Aliases](../About/about_Aliases.md)

[about_Providers](../About/about_Providers.md)
