---
description: Décrit des méthodes plus simples et plus naturelles pour les filtres de script pour les collections d’objets.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: 0a5d0059c6fd318fc9ddf2f49489fc2ae8aee291
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207810"
---
# <a name="about_simplified_syntax"></a>about_Simplified_Syntax

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit des méthodes plus simples et plus naturelles pour les filtres de script pour les collections d’objets.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

La syntaxe simplifiée, introduite dans Windows PowerShell 3,0, vous permet de créer des commandes de filtre sans utiliser de blocs de script. La syntaxe simplifiée est plus proche du langage naturel et est principalement utile avec les collections d’objets qui sont dirigés vers des commandes `Where-Object` et `ForEach-Object` leurs alias `where` et `foreach` .

Vous pouvez utiliser une méthode sur les membres d’une collection (le plus souvent, un tableau) sans faire référence à la variable automatique `$_` à l’intérieur d’un bloc de script.

Considérez les deux appels suivants :

### <a name="standard-syntax"></a>Syntaxe standard

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a>Syntaxe simplifiée

Dans la syntaxe simplifiée, les opérateurs de comparaison qui fonctionnent sur les membres des objets d’une collection sont traités comme des paramètres. Vous pouvez appeler une méthode sur des objets dans une collection sans faire référence à la variable automatique `$_` à l’intérieur d’un bloc de script.
Comparez les deux appels suivants à ceux de l’exemple précédent :

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

Tandis que les deux syntaxes fonctionnent, la syntaxe simplifiée retourne les résultats sans faire référence à la variable automatique `$_` à l’intérieur d’un bloc de script.
Le nom de la méthode `GetKeyAlgorithm` est traité comme un paramètre de `ForEach-Object` .
La deuxième commande retourne les mêmes résultats, mais sans erreur, car la syntaxe simplifiée ne tente pas de retourner des résultats pour les éléments pour lesquels l’argument spécifié ne s’est pas appliqué.

Dans cet exemple, la `Process` propriété `Description` est passée en tant que paramètre de nom de membre à la `ForEach-Object` commande. Les résultats sont des descriptions des processus actifs.

```powershell
Get-Process | foreach Description
```

Dans cet exemple, la `DirectoryInfo` méthode `GetFiles` est passée en tant que paramètre de nom de membre de la `ForEach-Object` commande.  
La méthode est appelée avec le paramètre de modèle de recherche `.*` .  
Les résultats sont `FileInfo` des enregistrements pour tous les fichiers masqués de type UNIX dans les répertoires de démarrage de l’utilisateur. 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a>VOIR AUSSI

- [about_Comparison_Operators](about_Comparison_Operators.md)
- [about_Foreach](about_Foreach.md)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)
- [ForEach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)

