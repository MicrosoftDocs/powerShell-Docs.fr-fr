---
description: Explique comment utiliser des variables locales et distantes dans des commandes distantes.
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 1cd6d0c4562fcd63fc56f103ec41aa6f0bb4c01c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595921"
---
# <a name="about-remote-variables"></a>À propos des variables distantes

## <a name="short-description"></a>Description courte

Explique comment utiliser des variables locales et distantes dans des commandes distantes.

## <a name="long-description"></a>Description longue

Vous pouvez utiliser des variables dans les commandes que vous exécutez sur des ordinateurs distants. Assignez une valeur à la variable, puis utilisez la variable à la place de la valeur.

Par défaut, les variables des commandes distantes sont supposées être définies dans la session qui exécute la commande. Les variables définies dans une session locale doivent être identifiées en tant que variables locales dans la commande.

## <a name="using-remote-variables"></a>Utilisation de variables distantes

PowerShell suppose que les variables utilisées dans les commandes distantes sont définies dans la session dans laquelle la commande s’exécute.

Dans cet exemple, la `$ps` variable est définie dans la session temporaire dans laquelle la `Get-WinEvent` commande s’exécute.

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

Lorsque la commande s’exécute dans une session persistante, **PSSession**, la variable distante doit être définie dans cette session.

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a>Utilisation de variables locales

Vous pouvez utiliser des variables locales dans des commandes distantes, mais la variable doit être définie dans la session locale.

À compter de PowerShell 3,0, vous pouvez utiliser le `Using` modificateur de portée pour identifier une variable locale dans une commande à distance.

La syntaxe de `Using` est la suivante :

```
$Using:<VariableName>
```

Dans l’exemple suivant, la `$ps` variable est créée dans la session locale, mais elle est utilisée dans la session dans laquelle la commande s’exécute. Le `Using` modificateur de portée identifie `$ps` en tant que variable locale.

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

Le `Using` modificateur de portée peut être utilisé dans une **session PSSession**.

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

Une référence de variable telle que `$using:var` s’étend à la valeur de la variable `$var` à partir du contexte de l’appelant. Vous n’accédez pas à l’objet variable de l’appelant.
Le `Using` modificateur de portée ne peut pas être utilisé pour modifier une variable locale au sein de la **session PSSession**. Par exemple, le code suivant ne fonctionne pas :

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

Pour plus d’informations sur `Using` , consultez [about_Scopes](./about_Scopes.md)

### <a name="using-splatting"></a>Utilisation de la projection

La projection PowerShell passe une collection de noms et de valeurs de paramètres à une commande. Pour plus d’informations, consultez [about_Splatting](about_Splatting.md).

Dans cet exemple, la variable de projection `$Splat` est une table de hachage configurée sur l’ordinateur local. Le `Invoke-Command` se connecte à une session de l’ordinateur distant. Le **scriptblock** utilise le `Using` modificateur de portée avec le symbole at ( `@` ) pour représenter la variable dans le volet.

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a>Autres situations où le modificateur de portée’Using’est nécessaire

Pour tout script ou commande qui s’exécute hors session, vous avez besoin du `Using` modificateur de portée pour incorporer les valeurs de variable de l’étendue de la session appelante, afin que le code hors session puisse y accéder. Le `Using` modificateur de portée est pris en charge dans les contextes suivants :

- Exécuter des commandes à distance, démarré avec `Invoke-Command` à l’aide des paramètres **ComputerName**, **hostname**, **SSHConnection** ou **session** (session à distance)
- Travaux en arrière-plan, démarrés avec `Start-Job` (session hors processus)
- Travaux de thread, démarrés via `Start-ThreadJob` ou `ForEach-Object -Parallel` (session de threads distincte)

Selon le contexte, les valeurs des variables incorporées sont soit des copies indépendantes des données dans la portée de l’appelant, soit des références à celles-ci. Dans les sessions à distance et hors processus, il s’agit toujours de copies indépendantes. Dans les sessions de thread, elles sont passées par référence.

## <a name="serialization-of-variable-values"></a>Sérialisation de valeurs de variables

Les commandes exécutées à distance et les travaux en arrière-plan s’exécutent hors processus.
Les sessions hors processus utilisent la sérialisation et la désérialisation basées sur XML pour rendre les valeurs des variables disponibles dans les limites du processus. Le processus de sérialisation convertit des objets en **PSObject** qui contient les propriétés des objets d’origine, mais pas ses méthodes.

Pour un ensemble limité de types, la désérialisation réalimente les objets dans le type d’origine. L’objet réalimenté est une copie de l’instance d’objet d’origine.
Il a les propriétés et les méthodes de type. Pour les types simples, tels que **System. version**, la copie est exacte. Pour les types complexes, la copie n’est pas parfaite. Par exemple, les objets de certificat réalimentés n’incluent pas la clé privée.

Les instances de tous les autres types sont des instances **PSObject** . La propriété **PSTypeNames** contient le nom du type d’origine préfixé avec **désérialisé**, par exemple, **Deserialized.SysTEM. Data. DataTable**

## <a name="using-local-variables-with-argumentlist-parameter"></a>Utilisation de variables locales avec le paramètre **argumentlist**

Vous pouvez utiliser des variables locales dans une commande à distance en définissant les paramètres de la commande distante et en utilisant le paramètre **argumentlist** de l' `Invoke-Command` applet de commande pour spécifier la variable locale comme valeur de paramètre.

- Utilisez le `param` mot clé pour définir les paramètres de la commande distante. Les noms de paramètres sont des espaces réservés qui n’ont pas besoin de correspondre au nom de la variable locale.

- Utilisez les paramètres définis par le `param` mot clé dans la commande.

- Utilisez le paramètre **argumentlist** de l' `Invoke-Command` applet de commande pour spécifier la variable locale comme valeur de paramètre.

Par exemple, les commandes suivantes définissent la `$ps` variable dans la session locale, puis l’utilisent dans une commande à distance. La commande utilise `$log` comme nom de paramètre et la variable locale, `$ps` , comme valeur.

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a>Voir aussi

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)

@Microsoft.PowerShell.Core.ForEach-Object

