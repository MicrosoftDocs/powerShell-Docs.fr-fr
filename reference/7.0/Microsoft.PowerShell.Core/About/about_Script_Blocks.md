---
description: Définit ce qu’est un bloc de script et explique comment utiliser des blocs de script dans le langage de programmation PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: 1793deded63669399246d18132bbc5b6d6c4810b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206593"
---
# <a name="about-script-blocks"></a>À propos des blocs de script

## <a name="short-description"></a>Description courte

Définit ce qu’est un bloc de script et explique comment utiliser des blocs de script dans le langage de programmation PowerShell.

## <a name="long-description"></a>Description longue

Dans le langage de programmation PowerShell, un bloc de script est une collection d’instructions ou d’expressions qui peuvent être utilisées comme une seule unité.
Un bloc de script peut accepter des arguments et retourner des valeurs.

Syntaxiquement, un bloc de script est une liste d’instructions entre accolades, comme illustré dans la syntaxe suivante :

```
{<statement list>}
```

Un bloc de script retourne la sortie de toutes les commandes dans le bloc de script, sous la forme d’un objet unique ou d’un tableau.

Vous pouvez également spécifier une valeur de retour à l’aide du `return` mot clé. Le `return` mot clé n’affecte pas ou ne supprime pas la sortie retournée par votre bloc de script. Toutefois, le `return` mot clé quitte le bloc de script à cette ligne. Pour plus d’informations, consultez [about_Return](about_Return.md).

Comme les fonctions, un bloc de script peut inclure des paramètres. Utilisez le mot clé param pour assigner des paramètres nommés, comme indiqué dans la syntaxe suivante :

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> Dans un bloc de script, contrairement à une fonction, vous ne pouvez pas spécifier de paramètres en dehors des accolades.

Comme les fonctions, les blocs de script peuvent inclure les `DynamicParam` `Begin` Mots clés,, `Process` et `End` . Pour plus d’informations, consultez [about_Functions](about_Functions.md) et [about_Functions_Advanced](about_Functions_Advanced.md).

## <a name="using-script-blocks"></a>Utilisation des blocs de script

Un bloc de script est une instance d’un type Microsoft .NET Framework `System.Management.Automation.ScriptBlock` . Les commandes peuvent avoir des valeurs de paramètre de bloc de script. Par exemple, l' `Invoke-Command` applet de commande a un `ScriptBlock` paramètre qui prend une valeur de bloc de script, comme illustré dans cet exemple :

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

`Invoke-Command` peut également exécuter des blocs de script qui ont des blocs de paramètres.
Les paramètres sont assignés par position à l’aide du paramètre **argumentlist** .

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

Le bloc de script dans l’exemple précédent utilise le `param` mot clé pour créer `$p1` des paramètres et `$p2` . La chaîne « First » est liée au premier paramètre ( `$p1` ) et « second » est lié à ( `$p2` ).

Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about_Splatting.md#splatting-with-arrays).

Vous pouvez utiliser des variables pour stocker et exécuter des blocs de script. L’exemple ci-dessous stocke un bloc de script dans une variable et le passe à `Invoke-Command` .

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

L’opérateur d’appel est une autre façon d’exécuter des blocs de script stockés dans une variable.
Comme `Invoke-Command` , l’opérateur d’appel exécute le bloc de script dans une étendue enfant. L’opérateur d’appel peut faciliter l’utilisation de paramètres avec vos blocs de script.

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

Vous pouvez stocker la sortie de vos blocs de script dans une variable à l’aide de l’assignation.

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

Pour plus d’informations sur l’opérateur d’appel, consultez [about_Operators](about_Operators.md).

## <a name="using-delay-bind-script-blocks-with-parameters"></a>Utilisation de blocs de script de liaison différée avec des paramètres

Un paramètre typé qui accepte l’entrée de pipeline ( `by Value` ) ou ( `by PropertyName` ) permet d’utiliser des blocs de script de **liaison différée** sur le paramètre.
Dans le bloc de script de **liaison différée** , vous pouvez référencer l’objet dirigé dans à l’aide de la variable de pipeline `$_` .

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

Dans les cmdlets plus complexes, les blocs de script de liaison différée permettent la réutilisation d’un objet dirigé dans pour remplir d’autres paramètres.

Remarques sur les blocs de script de **liaison différée** comme paramètres :

- Vous devez spécifier explicitement les noms de paramètres que vous utilisez avec des blocs de script de **liaison différée** .
- Le paramètre ne doit pas être non typé et le type du paramètre ne peut pas être `[scriptblock]` ou `[object]` .
- Vous recevez une erreur si vous utilisez un bloc de script **de liaison différée** sans fournir d’entrée de pipeline.

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a>Voir aussi

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Operators](about_Operators.md)
