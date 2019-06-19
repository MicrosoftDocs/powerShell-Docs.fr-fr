---
ms.date: 08/27/2018
keywords: powershell,applet de commande
title: Utilisation de noms de commande familiers
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030895"
---
# <a name="using-familiar-command-names"></a>Utilisation de noms de commande familiers

PowerShell prend en charge les alias pour faire référence aux commandes avec d’autres noms. Les alias permettent aux utilisateurs ayant l’expérience d’autres interpréteurs de commande d’utiliser des noms de commandes courants qu’ils connaissent déjà pour des opérations similaires dans PowerShell.

Créer un alias associe un nouveau nom à une autre commande. Par exemple, PowerShell dispose d’une fonction interne nommée `Clear-Host` qui efface la fenêtre de sortie. Vous pouvez taper l’alias `cls` ou `clear` dans une invite de commandes. PowerShell interprète ces alias et exécute la fonction `Clear-Host`.

Cette fonctionnalité aide les utilisateurs à apprendre à utiliser PowerShell. Tout d’abord, la plupart des utilisateurs de **cmd.exe** et d’Unix ont un répertoire de commandes qu’ils connaissent déjà par leur nom. Les équivalents PowerShell ne donneront peut-être pas des résultats identiques. Toutefois, les résultats sont assez proches pour que les utilisateurs puissent travailler sans connaître le nom de la commande PowerShell. La « mémoire des doigts » est une autre source principale de frustration lors de l’apprentissage d’un nouvel interpréteur de commande. Si vous avez utilisé **cmd.exe** pendant des années, vous risquez de taper instinctivement la commande `cls` pour effacer l’écran. Sans l’alias de `Clear-Host`, vous recevez un message d’erreur et ne savez pas quoi faire pour effacer la sortie.

La liste ci-dessous contient quelques-unes des commandes **Cmd.exe** et Unix courantes que vous pouvez utiliser dans PowerShell :

|||||
|-|-|-|-|
|cat|dir|mount|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|type|
|del|lp|r|write|
|diff|ls|ren||

L’applet de commande `Get-Alias` affiche le nom réel de la commande PowerShell native associée à un alias.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Interprétation des alias standard

Les alias décrits plus haut ont été conçus pour que leurs noms soient compatibles avec d’autres interpréteurs de commande.
La plupart des alias intégrés dans PowerShell sont conçues par souci de concision. Des noms plus courts sont plus faciles à taper, mais ils sont difficiles à lire si vous ne savez pas à quoi ils font référence.

Les alias PowerShell sont une tentative de compromis entre la clarté et la concision. PowerShell utilise un ensemble standard d’alias pour les verbes et les noms courants.

Exemples d’abréviations :

| Nom ou verbe | Abréviation |
|--------------|--------------|
| Get          | g            |
| Set          | s            |
| Élément         | i            |
| Emplacement     | l            |
| Commande      | cm           |
| Alias        | al           |

Ces alias sont compréhensibles lorsque vous connaissez les noms abrégés.

| Nom de l’applet de commande    | Alias |
|----------------|-------|
| `Get-Item`     | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | gal   |

Une fois que vous êtes familiarisé avec les alias de PowerShell, il est facile de deviner à quoi l’alias **sal** fait référence`Set-Alias`.

## <a name="creating-new-aliases"></a>Création d’alias

Vous pouvez créer vos propres alias à l’aide de l’applet de commande `Set-Alias`. Par exemple, les instructions suivantes créent les alias d’applet de commande standard décrits précédemment :

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

En interne, PowerShell utilise des commandes similaires pendant le démarrage, mais ces alias ne sont pas modifiables.
Si vous tentez d’exécuter l’une de ces commandes, vous obtenez un message d’erreur expliquant que l’alias ne peut pas être modifié. Par exemple :

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
