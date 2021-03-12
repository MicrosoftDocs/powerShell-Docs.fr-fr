---
description: Décrit comment créer et utiliser un profil PowerShell.
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 7604b8058a731939524769b6e1469b072a7eb2fe
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196178"
---
# <a name="about-profiles"></a>À propos des profils

## <a name="short-description"></a>Description courte
Décrit comment créer et utiliser un profil PowerShell.

## <a name="long-description"></a>Description longue

Vous pouvez créer un profil PowerShell pour personnaliser votre environnement et ajouter des éléments spécifiques à la session à chaque session PowerShell que vous démarrez.

Un profil PowerShell est un script qui s’exécute au démarrage de PowerShell. Vous pouvez utiliser le profil comme script d’ouverture de session pour personnaliser l’environnement. Vous pouvez ajouter des commandes, des alias, des fonctions, des variables, des composants logiciels enfichables, des modules et des lecteurs PowerShell. Vous pouvez également ajouter d’autres éléments spécifiques à la session à votre profil afin qu’ils soient disponibles dans chaque session sans avoir à les importer ou à les recréer.

PowerShell prend en charge plusieurs profils pour les utilisateurs et les programmes hôtes. Toutefois, il ne crée pas les profils pour vous. Cette rubrique décrit les profils et décrit comment créer et gérer des profils sur votre ordinateur.

Il explique comment utiliser le paramètre **noprofile** de la console powershell (PowerShell.exe) pour démarrer PowerShell sans aucun profil. Et explique l’effet de la stratégie d’exécution de PowerShell sur les profils.

## <a name="the-profile-files"></a>Fichiers de profil

PowerShell prend en charge plusieurs fichiers de profil. En outre, les programmes hôtes PowerShell peuvent prendre en charge leurs propres profils propres à l’hôte.

Par exemple, la console PowerShell prend en charge les fichiers de profil de base suivants. Les profils sont répertoriés par ordre de priorité. Le premier profil a la priorité la plus élevée.

|Description               | Path                                          |
|--------------------------|-----------------------------------------------|
|Tous les utilisateurs, tous les ordinateurs hôtes      |$PSHOME \\Profile.ps1                           |
|Tous les utilisateurs, hôte actuel   |$PSHOME \\Microsoft.PowerShell_profile.ps1      |
|Utilisateur actuel, tous les ordinateurs hôtes   |$Home \\ [My] Documents \\ \\Profile.ps1 PowerShell |
|Utilisateur actuel, hôte actuel|$Home \\ [My] documents \\ PowerShell\\<br>Microsoft.PowerShell_profile.ps1 |

Les chemins d’accès aux profils incluent les variables suivantes :

- La `$PSHOME` variable, qui stocke le répertoire d’installation de PowerShell
- La `$Home` variable, qui stocke le répertoire de démarrage de l’utilisateur actuel

En outre, d’autres programmes qui hébergent PowerShell peuvent prendre en charge leurs propres profils. Par exemple, Visual Studio Code prend en charge les profils spécifiques à l’hôte suivants.

|Description               | Path                                     |
|--------------------------|------------------------------------------|
|Tous les utilisateurs, hôte actuel   |$PSHOME \\Microsoft.VSCode_profile.ps1|
|Utilisateur actuel, hôte actuel|$Home \\ [My] documents \\ PowerShell\\<br>Microsoft.VSCode_profile.ps1|

Dans l’aide PowerShell, le profil « CurrentUser, hôte actuel » est le profil le plus souvent appelé « votre profil PowerShell ».

## <a name="the-profile-variable"></a>La variable $PROFILE

La `$PROFILE` variable automatique stocke les chemins d’accès aux profils PowerShell qui sont disponibles dans la session active.

Pour afficher un chemin de profil, affichez la valeur de la `$PROFILE` variable. Vous pouvez également utiliser la `$PROFILE` variable dans une commande pour représenter un chemin d’accès.

La `$PROFILE` variable stocke le chemin d’accès au profil « utilisateur actuel, hôte actuel ». Les autres profils sont enregistrés dans les propriétés de note de la `$PROFILE` variable.

Par exemple, la `$PROFILE` variable a les valeurs suivantes dans la console Windows PowerShell.

|Description                |Nom                              |
|---------------------------|----------------------------------|
|Utilisateur actuel, hôte actuel |`$PROFILE`                        |
|Utilisateur actuel, hôte actuel |`$PROFILE.CurrentUserCurrentHost` |
|Utilisateur actuel, tous les ordinateurs hôtes    |`$PROFILE.CurrentUserAllHosts`    |
|Tous les utilisateurs, hôte actuel    |`$PROFILE.AllUsersCurrentHost`    |
|Tous les utilisateurs, tous les ordinateurs hôtes       |`$PROFILE.AllUsersAllHosts`       |

Étant donné que les valeurs de la `$PROFILE` variable changent pour chaque utilisateur et dans chaque application hôte, assurez-vous d’afficher les valeurs des variables de profil dans chaque application hôte PowerShell que vous utilisez.

Pour afficher les valeurs actuelles de la `$PROFILE` variable, tapez :

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

Vous pouvez utiliser la `$PROFILE` variable dans de nombreuses commandes. Par exemple, la commande suivante ouvre le profil « utilisateur actuel, hôte actuel » dans le bloc-notes :

```powershell
notepad $PROFILE
```

La commande suivante détermine si un profil « tous les utilisateurs, tous les ordinateurs hôtes » a été créé sur l’ordinateur local :

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a>Comment créer un profil

Pour créer un profil PowerShell, utilisez le format de commande suivant :

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

Par exemple, pour créer un profil pour l’utilisateur actuel dans l’application hôte PowerShell actuelle, utilisez la commande suivante :

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

Dans cette commande, l' `If` instruction vous empêche de remplacer un profil existant. Remplacez la valeur de l' \<profile-path\> espace réservé par le chemin d’accès au fichier de profil que vous souhaitez créer.

> [!NOTE]
> Pour créer des profils « tous les utilisateurs » dans Windows Vista et les versions ultérieures de Windows, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

## <a name="how-to-edit-a-profile"></a>Comment modifier un profil

Vous pouvez ouvrir n’importe quel profil PowerShell dans un éditeur de texte, tel que le bloc-notes.

Pour ouvrir le profil de l’utilisateur actuel dans l’application hôte PowerShell actuelle dans le bloc-notes, tapez :

```powershell
notepad $PROFILE
```

Pour ouvrir d’autres profils, spécifiez le nom du profil. Par exemple, pour ouvrir le profil pour tous les utilisateurs de toutes les applications hôtes, tapez :

```powershell
notepad $PROFILE.AllUsersAllHosts
```

Pour appliquer les modifications, enregistrez le fichier de profil, puis redémarrez PowerShell.

## <a name="how-to-choose-a-profile"></a>Comment choisir un profil

Si vous utilisez plusieurs applications hôtes, placez les éléments que vous utilisez dans toutes les applications hôtes dans votre `$PROFILE.CurrentUserAllHosts` profil. Placez les éléments spécifiques à une application hôte, par exemple une commande qui définit la couleur d’arrière-plan d’une application hôte, dans un profil spécifique à cette application hôte.

Si vous êtes un administrateur qui personnalise PowerShell pour de nombreux utilisateurs, suivez ces instructions :

- Stocker les éléments communs dans le `$PROFILE.AllUsersAllHosts` profil
- Stocker des éléments spécifiques à une application hôte dans des `$PROFILE.AllUsersCurrentHost` profils spécifiques à l’application hôte
- Stocker des éléments pour des utilisateurs particuliers dans les profils spécifiques à l’utilisateur

Veillez à consulter la documentation de l’application hôte pour connaître toute implémentation spéciale des profils PowerShell.

## <a name="how-to-use-a-profile"></a>Comment utiliser un profil

La plupart des éléments que vous créez dans PowerShell et la plupart des commandes que vous exécutez affectent uniquement la session active. Lorsque vous terminez la session, les éléments sont supprimés.

Les commandes et éléments spécifiques à la session incluent les variables, les variables de préférence, les alias, les fonctions, les commandes (à l’exception de [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) et les modules PowerShell que vous ajoutez à la session.

Pour enregistrer ces éléments et les rendre disponibles dans toutes les sessions ultérieures, ajoutez-les à un profil PowerShell.

Une autre utilisation courante des profils consiste à enregistrer les fonctions, alias et variables fréquemment utilisés. Lorsque vous enregistrez les éléments dans un profil, vous pouvez les utiliser dans n’importe quelle session applicable sans les recréer.

## <a name="how-to-start-a-profile"></a>Comment démarrer un profil

Lorsque vous ouvrez le fichier de profil, il est vide. Toutefois, vous pouvez le remplir avec les variables, les alias et les commandes que vous utilisez fréquemment.

Voici quelques suggestions pour vous aider à démarrer.

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a>Ajoutez des commandes qui facilitent l’ouverture de votre profil

Cela s’avère particulièrement utile si vous utilisez un profil autre que le profil « utilisateur actuel, hôte actuel ». Par exemple, ajoutez la commande suivante :

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a>Ajouter une fonction qui répertorie les alias de toute applet de commande

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a>Personnaliser votre console

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a>Ajouter une invite PowerShell personnalisée

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

Pour plus d’informations sur l’invite de PowerShell, consultez [about_Prompts](about_Prompts.md).

## <a name="the-noprofile-parameter"></a>Paramètre noprofile

Pour démarrer PowerShell sans profils, utilisez le paramètre **noprofile** de **PowerShell.exe**, le programme qui démarre PowerShell.

Pour commencer, ouvrez un programme capable de Démarrer PowerShell, tel que Cmd.exe ou PowerShell lui-même. Vous pouvez également utiliser la boîte de dialogue Exécuter dans Windows.

Tapez :

```
PowerShell -NoProfile
```

Pour obtenir la liste complète des paramètres de PowerShell.exe, tapez :

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a>Profils et stratégie d’exécution

La stratégie d’exécution de PowerShell détermine, en partie, si vous pouvez exécuter des scripts et charger des fichiers de configuration, y compris les profils. La stratégie d’exécution **restreinte** est la stratégie par défaut. Il empêche l’exécution de tous les scripts, y compris les profils. Si vous utilisez la stratégie « Restricted », le profil ne s’exécute pas et son contenu n’est pas appliqué.

Une `Set-ExecutionPolicy` commande définit et modifie votre stratégie d’exécution. Il s’agit de l’une des quelques commandes qui s’appliquent à toutes les sessions PowerShell, car la valeur est enregistrée dans le registre. Vous n’avez pas besoin de la définir lorsque vous ouvrez la console, et vous n’avez pas besoin de stocker une `Set-ExecutionPolicy` commande dans votre profil.

## <a name="profiles-and-remote-sessions"></a>Profils et sessions à distance

Les profils PowerShell ne sont pas exécutés automatiquement dans les sessions à distance. par conséquent, les commandes ajoutées par les profils ne sont pas présentes dans la session à distance. En outre, la `$PROFILE` variable automatique n’est pas remplie dans les sessions à distance.

Pour exécuter un profil dans une session, utilisez l’applet de [commande Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .

Par exemple, la commande suivante exécute le profil « utilisateur actuel, hôte actuel » à partir de l’ordinateur local dans la session dans `$s` .

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

La commande suivante exécute le profil « utilisateur actuel, hôte actuel » à partir de l’ordinateur distant dans la session dans `$s` . Étant donné que la `$PROFILE` variable n’est pas remplie, la commande utilise le chemin d’accès explicite au profil. Nous utilisons un opérateur d’approvisionnement en points pour que le profil s’exécute dans l’étendue actuelle sur l’ordinateur distant et non dans sa propre étendue.

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

Après l’exécution de cette commande, les commandes ajoutées par le profil à la session sont disponibles dans `$s` .

## <a name="see-also"></a>Voir aussi

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Prompts](about_Prompts.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Signing](about_Signing.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

