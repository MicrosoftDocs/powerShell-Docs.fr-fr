---
description: Explique comment rediriger la sortie de PowerShell vers des fichiers texte.
keywords: PowerShell, applet de commande
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 7e6dcadc3bcabd4dc0521a158db87ca2bba41af8
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208406"
---
# <a name="about-redirection"></a>À propos de la redirection

## <a name="short-description"></a>Description courte
Explique comment rediriger la sortie de PowerShell vers des fichiers texte.

## <a name="long-description"></a>Description longue

Par défaut, PowerShell envoie la sortie à l’hôte PowerShell. Il s’agit généralement de l’application console. Toutefois, vous pouvez diriger la sortie vers un fichier texte et vous pouvez rediriger la sortie d’erreur vers le flux de sortie normal.

Vous pouvez utiliser les méthodes suivantes pour rediriger la sortie :

- Utilisez l' `Out-File` applet de commande, qui envoie une sortie de commande à un fichier texte.
  En général, vous utilisez l’applet de commande `Out-File` lorsque vous avez besoin d’utiliser ses paramètres, tels que les `Encoding` paramètres,, `Force` `Width` ou `NoClobber` .

- Utilisez l' `Tee-Object` applet de commande, qui envoie une sortie de commande à un fichier texte, puis l’envoie au pipeline.

- Utilisez les opérateurs de redirection PowerShell. L’utilisation de l’opérateur de redirection avec une cible de fichier est fonctionnellement équivalente à la fonctionnalité de canalisation `Out-File` sans aucun paramètre supplémentaire.

Pour plus d’informations sur les flux, consultez [about_Output_Streams](about_Output_Streams.md).

### <a name="redirectable-output-streams"></a>Flux de sortie redirigés

PowerShell prend en charge la redirection des flux de sortie suivants.

| Train # |      Description       | Introduite dans  |    Écrire l’applet de commande     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **Opération réussie** Train     | PowerShell 2.0 | `Write-Output`      |
| 2        | **Erreur** Train       | PowerShell 2.0 | `Write-Error`       |
| 3        | **Avertissement** Train     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **Commentaires** Train     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **Débogage** Train       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **Informations** Train | PowerShell 5.0 | `Write-Information` |
| *        | Tous les flux            | PowerShell 3.0 |                     |

> [!NOTE]
> Il y a également un flux de **progression** dans PowerShell, mais il ne prend pas en charge la redirection.

### <a name="powershell-redirection-operators"></a>Opérateurs de redirection PowerShell

Les opérateurs de redirection PowerShell sont les suivants, où `n` représente le numéro de flux. Le flux de **réussite** ( `1` ) est la valeur par défaut si aucun flux n’est spécifié.

| Opérateur |                         Description                         | Syntaxe |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | Envoie le flux spécifié à un fichier.                            | `n>`   |
| `>>`     | **Ajoute** le flux spécifié à un fichier.                      | `n>>`  |
| `>&1`    | _Redirige_ le flux spécifié vers le flux de **réussite** . | `n>&1` |

> [!NOTE]
> Contrairement à certains shells UNIX, vous pouvez rediriger uniquement les autres flux vers le flux de **réussite** .

## <a name="examples"></a>Exemples

### <a name="example-1-redirect-errors-and-output-to-a-file"></a>Exemple 1 : rediriger les erreurs et la sortie vers un fichier

Cet exemple s’exécute `dir` sur un élément qui sera correctement exécuté, et sur un élément qui génère une erreur.

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

Il utilise `2>&1` pour rediriger le flux d' **Erreurs** vers le flux de **réussite** , et `>` pour envoyer le flux de **réussite** obtenu à un fichier appelé `dir.log`

### <a name="example-2-send-all-success-stream-data-to-a-file"></a>Exemple 2 : envoyer toutes les données de flux de réussite à un fichier

Cet exemple envoie toutes les données de flux de **réussite** à un fichier appelé `script.log` .

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a>Exemple 3 : envoyer des flux de réussite, d’avertissement et d’erreur à un fichier

Cet exemple montre comment combiner des opérateurs de redirection pour obtenir le résultat souhaité.

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > P:\Temp\redirection.log
```

- `3>&1` redirige le flux d' **Avertissement** vers le flux de **réussite** .
- `2>&1` redirige le flux d' **Erreurs** vers le flux de **réussite** (qui contient également toutes les données de flux d' **Avertissement** )
- `>` redirige le flux de **réussite** (qui contient désormais à la fois des flux d' **avertissements** et d' **Erreurs** ) vers un fichier appelé `C:\temp\redirection.log` )

### <a name="example-4-redirect-all-streams-to-a-file"></a>Exemple 4 : rediriger tous les flux vers un fichier

Cet exemple envoie tous les flux de sortie à partir d’un script appelé `script.ps1` dans un fichier appelé `script.log`

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a>Exemple 5 : supprimer toutes les données de flux de Write-Host et d’informations

Cet exemple supprime toutes les données de flux d’informations. Pour en savoir plus sur les applets de commande de flux d' **informations** , consultez [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) et [Write-information](xref:Microsoft.PowerShell.Utility.Write-Information) .

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a>Exemple 6 : afficher l’effet des préférences d’action

Les paramètres et les variables de préférence d’action peuvent modifier ce qui est écrit dans un flux de données particulier. Le script de cet exemple montre comment la valeur de `$ErrorActionPreference` affecte ce qui est écrit dans le flux d' **Erreurs** .

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

Lorsque nous exécutons ce script, nous recevons une invite quand `$ErrorActionPreference` a la valeur `Inquire` .

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

Lorsque nous examinons le fichier journal, nous voyons ce qui suit :

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a>Notes

Les opérateurs de redirection qui n’ajoutent pas de données ( `>` et `n>` ) remplacent le contenu actuel du fichier spécifié sans avertissement.

Toutefois, si le fichier est un fichier système, masqué et en lecture seule, la redirection **échoue** . Les opérateurs de redirection d’ajout ( `>>` et `n>>` ) n’écrivent pas dans un fichier en lecture seule, mais ils ajoutent du contenu à un fichier système ou masqué.

Pour forcer la redirection du contenu vers un fichier système, masqué ou en lecture seule, utilisez l' `Out-File` applet de commande avec son `Force` paramètre.

Lorsque vous écrivez dans des fichiers, les opérateurs de redirection utilisent l' `UTF8NoBOM` encodage. Si le fichier a un encodage différent, il est possible que la sortie ne soit pas correctement mise en forme. Pour écrire dans des fichiers avec un encodage différent, utilisez l' `Out-File` applet de commande avec son `Encoding` paramètre.

### <a name="potential-confusion-with-comparison-operators"></a>Confusion potentielle avec les opérateurs de comparaison

L' `>` opérateur ne doit pas être confondu avec l’opérateur de comparaison [supérieur](about_Comparison_Operators.md#-gt) à (souvent désigné comme `>` dans d’autres langages de programmation).

Selon les objets comparés, la sortie à l’aide de `>` peut sembler correcte (car 36 n’est pas supérieur à 42).

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

Toutefois, une vérification du système de fichiers local peut voir qu’un fichier appelé `42` a été écrit avec le contenu `36` .

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

Toute tentative d’utilisation de la comparaison inverse `<` (inférieure à) génère une erreur système :

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : RedirectionNotSupported
```

Si la comparaison numérique est l’opération requise, elle `-lt` `-gt` doit être utilisée. Voir : [ `-gt` opérateur de comparaison](about_Comparison_Operators.md#-gt)

## <a name="see-also"></a>Voir aussi

- [Out-File](xref:Microsoft.PowerShell.Utility.Out-File)
- [Tee-Object](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Écriture-erreur](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-Output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_Output_Streams](about_Output_Streams.md)
- [about_Operators](about_Operators.md)
- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Path_Syntax](about_Path_Syntax.md)
