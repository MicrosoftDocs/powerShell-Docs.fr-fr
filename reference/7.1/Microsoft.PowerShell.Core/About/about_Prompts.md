---
description: Décrit la `Prompt` fonction et montre comment créer une fonction personnalisée `Prompt` .
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: c21c51a58beeb454e785e57989d3b4a75d575d0e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208309"
---
# <a name="about-prompts"></a>À propos des invites

## <a name="short-description"></a>Description courte
Décrit la `Prompt` fonction et montre comment créer une fonction personnalisée `Prompt` .

## <a name="long-description"></a>Description longue

L’invite de commandes PowerShell indique que PowerShell est prêt à exécuter une commande :

```
PS C:\>
```

L’invite PowerShell est déterminée par la `Prompt` fonction intégrée. Vous pouvez personnaliser l’invite en créant votre propre `Prompt` fonction et en l’enregistrant dans votre profil PowerShell.

## <a name="about-the-prompt-function"></a>À propos de la fonction prompt

La `Prompt` fonction détermine l’apparence de l’invite PowerShell.
PowerShell est fourni avec une fonction intégrée `Prompt` , mais vous pouvez la remplacer en définissant votre propre `Prompt` fonction.

La `Prompt` fonction a la syntaxe suivante :

```powershell
function Prompt { <function-body> }
```

La `Prompt` fonction doit retourner un objet. Il est recommandé de retourner une chaîne ou un objet mis en forme en tant que chaîne. La longueur maximale recommandée est de 80 caractères.

Par exemple, la `Prompt` fonction suivante retourne une chaîne « Hello, World » suivie d’un chevron droit ( `>` ).

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a>Obtention de la fonction prompt

Pour accéder à la `Prompt` fonction, utilisez l' `Get-Command` applet de commande ou utilisez l' `Get-Item` applet de commande dans le lecteur de la fonction.

Par exemple :

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

Pour récupérer le script qui définit la valeur de l’invite, utilisez la méthode point pour récupérer la propriété **scriptblock** de la `Prompt` fonction.

Par exemple :

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

Comme toutes les fonctions, la `Prompt` fonction est stockée dans le `Function:` lecteur.
Pour afficher le script qui crée la `Prompt` fonction active, tapez :

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a>Invite par défaut

L’invite par défaut s’affiche uniquement lorsque la `Prompt` fonction génère une erreur ou ne retourne pas d’objet.

L’invite PowerShell par défaut est :

```
PS>
```

Par exemple, la commande suivante affecte `Prompt` à la fonction la valeur `$null` , qui n’est pas valide. Par conséquent, l’invite par défaut s’affiche.

```powershell
PS C:\> function prompt {$null}
PS>
```

Étant donné que PowerShell est fourni avec une invite intégrée, vous ne voyez généralement pas l’invite par défaut.

### <a name="built-in-prompt"></a>Invite intégrée

PowerShell intègre une `Prompt` fonction intégrée.

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

La fonction utilise l' `Test-Path` applet de commande pour déterminer si la `$PSDebugContext` variable automatique est remplie. Si `$PSDebugContext` est rempli, vous êtes en mode de débogage, et `[DBG]:` est ajouté à l’invite, comme suit :

```Output
[DBG]: PS C:\ps-test>
```

Si `$PSDebugContext` n’est pas rempli, la fonction ajoute `PS` à l’invite.
Et, la fonction utilise l' `Get-Location` applet de commande pour récupérer l’emplacement du répertoire du système de fichiers actuel. Ensuite, elle ajoute un chevron droit ( `>` ).

Par exemple :

```Output
PS C:\ps-test>
```

Si vous êtes dans une invite imbriquée, la fonction ajoute deux chevrons ( `>>` ) à l’invite. (Vous êtes dans une invite imbriquée si la valeur de la `$NestedPromptLevel` variable automatique est supérieure à 1.)

Par exemple, lorsque vous effectuez un débogage dans une invite imbriquée, l’invite ressemble à l’invite suivante :

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a>Modifications apportées à l’invite

L' `Enter-PSSession` applet de commande ajoute le nom de l’ordinateur distant à la `Prompt` fonction active. Lorsque vous utilisez l' `Enter-PSSession` applet de commande pour démarrer une session avec un ordinateur distant, l’invite de commandes change pour inclure le nom de l’ordinateur distant. Par exemple :

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

D’autres applications hôtes PowerShell et autres shells peuvent avoir leurs propres invites de commandes personnalisées.

Pour plus d’informations sur `$PSDebugContext` les `$NestedPromptLevel` variables automatiques et, consultez [about_Automatic_Variables](about_Automatic_Variables.md).

### <a name="how-to-customize-the-prompt"></a>Comment personnaliser l’invite

Pour personnaliser l’invite, écrivez une nouvelle `Prompt` fonction. La fonction n’étant pas protégée, vous pouvez la remplacer.

Pour écrire une `Prompt` fonction, tapez ce qui suit :

```powershell
function prompt { }
```

Puis, entre les accolades, entrez les commandes ou la chaîne qui crée votre invite.

Par exemple, l’invite suivante comprend le nom de votre ordinateur :

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

Sur l’ordinateur Serveur01, l’invite de commandes ressemble à l’invite suivante :

```Output
PS [Server01] >
```

La `Prompt` fonction suivante contient la date et l’heure actuelles :

```powershell
function prompt {"$(Get-Date)> "}
```

L’invite ressemble à l’invite suivante :

```Output
03/15/2012 17:49:47>
```

Vous pouvez également modifier la fonction par défaut `Prompt` :

Par exemple, la fonction modifiée suivante `Prompt` ajoute `[ADMIN]:` à l’invite PowerShell intégrée lorsque PowerShell est ouvert à l’aide de l’option **exécuter en tant qu’administrateur** :

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

Lorsque vous démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** , une invite semblable à la suivante s’affiche :

```Output
[ADMIN]: PS C:\ps-test>
```

La `Prompt` fonction suivante affiche l’ID d’historique de la commande suivante. Pour afficher l’historique des commandes, utilisez l’applet de commande `Get-History` .

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

L’invite suivante utilise les `Write-Host` applets de commande et `Get-Random` pour créer une invite qui modifie la couleur de façon aléatoire. Étant donné que `Write-Host` écrit dans l’application hôte actuelle, mais ne retourne pas d’objet, cette fonction comprend une `Return` instruction. Sans lui, PowerShell utilise l’invite par défaut, `PS>` .

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a>Enregistrement de la fonction prompt

Comme toute fonction, la `Prompt` fonction existe uniquement dans la session active. Pour enregistrer la `Prompt` fonction pour des sessions ultérieures, ajoutez-la à vos profils PowerShell. Pour plus d'informations sur les profils, consultez [about_Profiles](about_Profiles.md).

## <a name="see-also"></a>Voir aussi

[Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Get-History](xref:Microsoft.PowerShell.Core.Get-History)

[Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random)

[Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)

[about_Profiles](about_Profiles.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Debuggers](about_Debuggers.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

