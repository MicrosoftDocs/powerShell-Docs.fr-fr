---
description: Décrit comment PowerShell détermine la commande à exécuter.
keywords: powershell,applet de commande
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: 288c01af2d66aca786cf1b97ad844dd91cac45ca
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207690"
---
# <a name="about-command-precedence"></a>À propos de la priorité des commandes

## <a name="short-description"></a>Description courte
Décrit comment PowerShell détermine la commande à exécuter.

## <a name="long-description"></a>Description longue

La priorité des commandes décrit la façon dont PowerShell détermine la commande à exécuter lorsqu’une session contient plusieurs commandes portant le même nom. Les commandes d’une session peuvent être masquées ou remplacées par des commandes portant le même nom. Cet article explique comment exécuter des commandes masquées et comment éviter les conflits de noms de commandes.

## <a name="command-precedence"></a>Priorité des commandes

Lorsqu’une session PowerShell inclut plusieurs commandes portant le même nom, PowerShell détermine la commande à exécuter à l’aide des règles suivantes.

Si vous spécifiez le chemin d’accès à une commande, PowerShell exécute la commande à l’emplacement spécifié par le chemin d’accès.

Par exemple, la commande suivante exécute le script FindDocs.ps1 dans le répertoire « C : \\ TechDocs » :

```
C:\TechDocs\FindDocs.ps1
```

En tant que fonctionnalité de sécurité, PowerShell n’exécute pas les commandes exécutables (natives), y compris les scripts PowerShell, sauf si la commande se trouve dans un chemin d’accès qui est listé dans la variable d’environnement PATH `$env:path` ou si vous spécifiez le chemin d’accès au fichier de script.

Pour exécuter un script qui se trouve dans le répertoire actif, spécifiez le chemin d’accès complet ou tapez un point `.\` pour représenter le répertoire actif.

Par exemple, pour exécuter le fichier FindDocs.ps1 dans le répertoire actif, tapez :

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a>Utilisation de caractères génériques dans l’exécution

Vous pouvez utiliser des caractères génériques dans l’exécution de la commande. L’utilisation de caractères génériques est également appelée *globbing* .

PowerShell exécute un fichier avec une correspondance de caractère générique, avant qu’un littéral ne corresponde.

Prenons l’exemple d’un répertoire contenant les fichiers suivants :

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

Les deux fichiers de script ont le même contenu : `$MyInvocation.MyCommand.Path` .
Cette commande affiche le nom du script qui est appelé.

Lorsque vous exécutez `[a1].ps1` , le fichier `a.ps1` est exécuté même si le fichier `[a1].ps1` est une correspondance littérale.

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

À présent, nous allons supprimer le `a.ps1` fichier et tenter de l’exécuter à nouveau.

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

Vous pouvez voir à partir de la sortie qui `[a1].ps1` s’exécute cette fois, car la correspondance littérale est la seule correspondance de fichier pour ce modèle de caractère générique.

Pour plus d’informations sur la façon dont PowerShell utilise les caractères génériques, consultez [about_Wildcards](about_Wildcards.md).

> [!NOTE]
> Pour limiter la recherche à un chemin d’accès relatif, vous devez faire précéder le nom du script du `.\` chemin d’accès. Cela limite la recherche de commandes aux fichiers dans ce chemin d’accès relatif. Sans ce préfixe, d’autres syntaxes PowerShell peuvent entrer en conflit et il existe peu de garantie que le fichier sera trouvé.

Si vous ne spécifiez pas de chemin d’accès, PowerShell utilise l’ordre de priorité suivant lorsqu’il exécute des commandes pour tous les éléments chargés dans la session active :

  1. Alias
  2. Fonction
  3. Applet de commande
  4. Fichiers exécutables externes (programmes et scripts non-PowerShell)

Par conséquent, si vous tapez « help », PowerShell recherche d’abord un alias nommé `help` , puis une fonction nommée `Help` et enfin une applet de commande nommée `Help` . Elle exécute le premier `help` élément qu’elle trouve.

Par exemple, si votre session contient une applet de commande et une fonction, toutes deux nommées `Get-Map` , lorsque vous tapez `Get-Map` , PowerShell exécute la fonction.

> [!NOTE]
> Cela s’applique uniquement aux commandes chargées. S’il existe un `build` exécutable et un alias `build` pour une fonction avec le nom de `Invoke-Build` à l’intérieur d’un module qui n’est pas chargé dans la session active, PowerShell exécute le `build` fichier exécutable à la place. Il ne charge pas les modules automatiquement s’il trouve l’exécutable externe dans ce cas. C’est uniquement lorsqu’aucun exécutable externe n’est trouvé qu’un alias, une fonction ou une applet de commande avec le nom donné est appelé, ce qui déclenche le chargement automatique de son module.

Lorsque la session contient des éléments du même type qui ont le même nom, PowerShell exécute l’élément le plus récent.

Par exemple, si vous importez une autre `Get-Date` applet de commande à partir d’un module, lorsque vous tapez `Get-Date` , PowerShell exécute la version importée sur le natif.

## <a name="hidden-and-replaced-items"></a>Éléments masqués et remplacés

À la suite de ces règles, les éléments peuvent être remplacés ou masqués par des éléments portant le même nom.

Les éléments sont « masqués » ou « occultés » si vous pouvez toujours accéder à l’élément d’origine, par exemple en qualifiant le nom de l’élément avec un nom de module ou de composant logiciel enfichable.

Par exemple, si vous importez une fonction qui porte le même nom qu’une applet de commande dans la session, l’applet de commande est masquée (mais pas remplacée), car elle a été importée à partir d’un composant logiciel enfichable ou d’un module.

Les éléments sont « remplacés » ou « remplacés » si vous ne pouvez plus accéder à l’élément d’origine.

Par exemple, si vous importez une variable qui porte le même nom qu’une variable de la session, la variable d’origine est remplacée et n’est plus accessible.
Vous ne pouvez pas qualifier une variable avec un nom de module.

De même, si vous tapez une fonction sur la ligne de commande, puis que vous importez une fonction portant le même nom, la fonction d’origine est remplacée et n’est plus accessible.

### <a name="finding-hidden-commands"></a>Recherche de commandes masquées

Le paramètre **All** de l’applet de [commande obtenir-Command](xref:Microsoft.PowerShell.Core.Get-Command) obtient toutes les commandes portant le nom spécifié, même si elles sont masquées ou remplacées. À compter de PowerShell 3,0, par défaut, `Get-Command` obtient uniquement les commandes qui s’exécutent lorsque vous tapez le nom de la commande.

Dans les exemples suivants, la session comprend une `Get-Date` fonction et une applet de commande [« obtenir-date »](xref:Microsoft.PowerShell.Utility.Get-Date) .

La commande suivante obtient la `Get-Date` commande qui s’exécute lorsque vous tapez `Get-Date` .

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

La commande suivante utilise le paramètre **All** pour récupérer toutes les `Get-Date` commandes.

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a>Exécution de commandes masquées

Vous pouvez exécuter des commandes particulières en spécifiant des propriétés d’élément qui distinguent la commande des autres commandes qui peuvent avoir le même nom. Vous pouvez utiliser cette méthode pour exécuter une commande, mais elle est particulièrement utile pour exécuter des commandes masquées.

#### <a name="qualified-names"></a>Noms qualifiés

L’utilisation du nom qualifié du module d’une applet de commande vous permet d’exécuter des commandes masquées par un élément portant le même nom. Par exemple, vous pouvez exécuter l' `Get-Date` applet de commande en la qualifiant avec son nom de module **Microsoft. PowerShell. Utility** .

Utilisez cette méthode préférée lorsque vous écrivez des scripts que vous envisagez de distribuer. Vous ne pouvez pas prédire les commandes qui peuvent être présentes dans la session dans laquelle le script s’exécute.

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

Pour exécuter une `New-Map` commande qui a été ajoutée par le `MapFunctions` module, utilisez son nom qualifié de module :

```powershell
MapFunctions\New-Map
```

Pour rechercher le module à partir duquel une commande a été importée, utilisez la propriété **modulename** des commandes.

```
(Get-Command <command-name>).ModuleName
```

Par exemple, pour trouver la source de l' `Get-Date` applet de commande, tapez :

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> Vous ne pouvez pas qualifier de variables ou d’alias.

#### <a name="call-operator"></a>Opérateur d’appel

Vous pouvez également utiliser l' `Call` opérateur `&` pour exécuter des commandes masquées en les associant à un appel à la commande [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (l’alias est « dir ») ou à l’opération « `Get-Command` [obtenir-module](xref:Microsoft.PowerShell.Core.Get-Module)».

L’opérateur d’appel exécute des chaînes et des blocs de script dans une étendue enfant. Pour plus d’informations, consultez [about_Operators](about_Operators.md).

Par exemple, si vous avez une fonction nommée `Map` qui est masquée par un alias nommé `Map` , utilisez la commande suivante pour exécuter la fonction.

```powershell
&(Get-Command -Name Map -CommandType Function)
```

ou

```powershell
&(dir Function:\map)
```

Vous pouvez également enregistrer votre commande masquée dans une variable pour faciliter son exécution.

Par exemple, la commande suivante enregistre la `Map` fonction dans la `$myMap` variable, puis utilise l' `Call` opérateur pour l’exécuter.

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a>Éléments remplacés

Un élément « remplacé » est un élément auquel vous ne pouvez plus accéder. Vous pouvez remplacer des éléments en important des éléments portant le même nom à partir d’un module ou d’un composant logiciel enfichable.

Par exemple, si vous tapez une `Get-Map` fonction dans votre session et que vous importez une fonction appelée `Get-Map` , elle remplace la fonction d’origine. Vous ne pouvez pas le récupérer dans la session active.

Les variables et les alias ne peuvent pas être masqués, car vous ne pouvez pas utiliser un opérateur d’appel ou un nom qualifié pour les exécuter. Lorsque vous importez des variables et des alias à partir d’un module ou d’un composant logiciel enfichable, ils remplacent les variables dans la session portant le même nom.

### <a name="avoiding-name-conflicts"></a>Éviter les conflits de noms

La meilleure façon de gérer les conflits de noms de commande consiste à les empêcher. Lorsque vous nommez vos commandes, utilisez un nom unique. Par exemple, ajoutez vos initiales ou acronyme de nom de société aux noms de vos commandes.

En outre, lorsque vous importez des commandes dans votre session à partir d’un module PowerShell ou d’une autre session, utilisez le `Prefix` paramètre de la commande [import-module](xref:Microsoft.PowerShell.Core.Import-Module) ou

Applet de commande [Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) pour ajouter un préfixe aux noms des commandes.

Par exemple, la commande suivante évite tout conflit avec les `Get-Date` applets de commande et `Set-Date` fournies avec PowerShell lorsque vous importez le `DateFunctions` module.

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

Pour plus d’informations, consultez `Import-Module` et `Import-PSSession` ci-dessous.

## <a name="see-also"></a>Voir aussi

- [about_Path_Syntax](about_Path_Syntax.md)
- [about_Aliases](about_Aliases.md)
- [about_Functions](about_Functions.md)
- [Alias-Provider](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [Function-Provider](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Module d’importation](xref:Microsoft.PowerShell.Core.Import-Module)
- [Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)
