---
ms.date: 05/22/2020
keywords: powershell,applet de commande
title: Qu’est-ce que PowerShell ?
description: Cet article présente l’environnement de script PowerShell et ses fonctionnalités.
ms.openlocfilehash: 91fc580af9a3adf43a24c40b4aaf3f1843882705
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500774"
---
# <a name="what-is-powershell"></a>Qu’est-ce que PowerShell ?

PowerShell est une infrastructure multiplateforme pour la gestion de la configuration et de l’automatisation des tâches, composée d’un interpréteur de commandes (shell) de ligne de commande et d’un langage de script. Contrairement à la plupart des interpréteurs de commandes qui acceptent et retournent du texte, PowerShell est construit sur le .NET Common Language Runtime (CLR), et accepte et retourne des objets .NET Framework. Ce changement fondamental apporte de nouveaux outils et méthodes pour l’automatisation.

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a>La sortie est basée sur les objets

Contrairement aux interfaces de ligne de commande traditionnelles, les applets de commande PowerShell sont conçues pour traiter des objets.
Un objet est une information structurée qui va au-delà de la seule chaîne de caractères s’affichant à l’écran. Une sortie de commande comporte toujours des informations supplémentaires que vous pouvez utiliser si nécessaire.

Si vous avez utilisé des outils de traitement de texte pour traiter des données dans le passé, vous constaterez qu’ils se comportent différemment lorsqu’ils sont utilisés dans PowerShell. Dans la plupart des cas, vous n’avez pas besoin d’outils de traitement texte pour extraire des informations spécifiques. Vous accédez directement à des portions de données à l’aide de la syntaxe d’objet PowerShell standard.

## <a name="the-command-family-is-extensible"></a>La famille de commandes est extensible

Les interfaces comme `cmd.exe` n’offrent aucun moyen d’étendre directement le jeu de commandes intégré. Vous pouvez créer des outils en ligne de commande externes qui s’exécutent dans `cmd.exe`. Mais ces outils externes ne proposent pas de services comme l’intégration de l’aide. `cmd.exe` ne sait pas automatiquement que ces outils externes sont des commandes valides.

Dans PowerShell, les commandes sont appelées des _cmdlets_ . Vous pouvez utiliser chaque cmdlet séparément, mais leur puissance s’exprime pleinement quand vous les combinez pour effectuer des tâches complexes. Comme de nombreux interpréteurs de commandes, PowerShell permet d’accéder au système de fichiers sur l’ordinateur. Les _fournisseurs_ PowerShell permettent d’accéder à d’autres magasins de données, tels que le Registre et les magasins de certificats, aussi facilement qu’au système de fichiers.

Vous pouvez créer vos propres modules de fonction et de cmdlet à l’aide de code ou de scripts compilés. Les modules peuvent ajouter des cmdlets et des fournisseurs à l’interpréteur de commandes. PowerShell prend également en charge des scripts analogues à ceux de l’interpréteur de commande UNIX et aux fichiers de traitement `cmd.exe`.

## <a name="support-for-command-aliases"></a>Prise en charge des alias de commande

PowerShell prend en charge les alias pour faire référence aux commandes avec d’autres noms. Les alias permettent aux utilisateurs ayant l’expérience d’autres interpréteurs de commande d’utiliser des noms de commandes courants qu’ils connaissent déjà pour des opérations similaires dans PowerShell.

Créer un alias associe un nouveau nom à une autre commande. Par exemple, PowerShell dispose d’une fonction interne nommée `Clear-Host` qui efface la fenêtre de sortie. Vous pouvez taper l’alias `cls` ou `clear` dans une invite de commandes. PowerShell interprète ces alias et exécute la fonction `Clear-Host`.

Cette fonctionnalité aide les utilisateurs à apprendre à utiliser PowerShell. Tout d’abord, la plupart des utilisateurs de `cmd.exe` et d’Unix ont un répertoire de commandes qu’ils connaissent déjà par leur nom. Les équivalents PowerShell ne donneront peut-être pas des résultats identiques. Toutefois, les résultats sont assez proches pour que les utilisateurs puissent travailler sans connaître le nom de la commande PowerShell. La « mémoire musculaire » est une autre source principale de frustration lors de l’apprentissage d’un nouvel interpréteur de commande. Si vous avez utilisé `cmd.exe` pendant des années, vous risquez de taper instinctivement la commande `cls` pour effacer l’écran. Sans l’alias de `Clear-Host`, vous recevez un message d’erreur et ne savez pas quoi faire pour effacer la sortie.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell gère l’entrée et l’affichage sur la console

Lorsque vous tapez une commande, PowerShell traite toujours directement la saisie de la ligne de commande. PowerShell met également en forme la sortie sur écran. Cette différence est importante, car elle réduit le travail requis de chaque cmdlet. Elle garantit que vous pouvez toujours procéder de la même façon avec chaque cmdlet. Les développeurs de cmdlet n’ont besoin ni d’écrire du code pour analyser les arguments de ligne de commande, ni de mettre en forme la sortie.

Les outils en ligne de commande traditionnels ont leurs propres modes de demande et d’affichage de l’aide. Certains outils en ligne de commande utilisent `/?` pour lancer l’affichage de l’aide. D’autres utilisent `-?`, `/H`, voire `//`. Certains affichent l’aide dans une fenêtre d’interface graphique utilisateur, plutôt que dans l’affichage de la console. Si vous utilisez un paramètre incorrect, l’outil peut ignorer ce que vous avez tapé et commencer à exécuter une tâche automatiquement.
Étant donné que PowerShell analyse et traite automatiquement la ligne de commande, le paramètre `-?` signifie toujours « afficher l’aide de cette commande ».

> [!NOTE]
> Si vous exécutez une application graphique dans PowerShell, la fenêtre de l’application s’ouvre.
> PowerShell intervient uniquement lors du traitement de l’entrée de ligne de commande que vous saisissez ou lors du renvoi de la sortie de l’application à la fenêtre de la console. Cela n’affecte en rien le fonctionnement interne de l’application.

## <a name="powershell-has-a-pipeline"></a>PowerShell a un pipeline

Les pipelines constituent indubitablement le concept plus important utilisé dans les interfaces de ligne de commande. Lorsqu’ils sont utilisés correctement, les pipelines réduisent l’effort lié à l’utilisation de commandes complexes et facilitent la visualisation du flux de travail. Chaque commande dans un pipeline passe sa sortie, élément par élément, à la commande suivante. Les commandes n’ont pas à gérer plusieurs éléments à la fois. Il en résulte une consommation réduite des ressources et la possibilité de recevoir la sortie immédiatement.

La notation utilisée pour les pipelines est similaire celle utilisée dans d’autres interpréteurs de commandes. À première vue, les différences des pipelines dans PowerShell peuvent ne pas être évidentes. Même si vous voyez du texte à l’écran, PowerShell canalise des objets, pas du texte, entre les commandes.

Par exemple, si vous utilisez la cmdlet `Out-Host` pour forcer un affichage page par page de la sortie d’une autre commande, la sortie ressemble exactement au texte normal affiché à l’écran, mais divisé en pages :

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

La pagination réduit également l’utilisation du processeur, car le traitement transfère à la cmdlet `Out-Host` lorsqu’il a une page complète prête à afficher. L’exécution des cmdlets qui la précèdent dans le pipeline est interrompue jusqu’à ce que la page suivante de la sortie soit disponible.

### <a name="objects-in-the-pipeline"></a>Objets dans le pipeline

Lorsque vous exécutez une cmdlet dans PowerShell, vous voyez une sortie texte, car il est de nécessaire de représenter les objets sous forme de texte dans une fenêtre de console. La sortie texte peut ne pas afficher toutes les propriétés de l’objet en cours de sortie.

Prenez, par exemple, la cmdlet `Get-Location`. La sortie texte est un résumé des informations, non une représentation complète de l’objet retourné par `Get-Location`. Le titre dans la sortie est ajouté par le processus qui met en forme les données pour l’affichage à l’écran.

```powershell
Get-Location
```

```Output
Path
----
C:\
```

Lorsque vous dirigez la sortie vers la cmdlet `Get-Member`, vous obtenez des informations sur l’objet retourné par `Get-Location`.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` retourne un objet **PathInfo** qui contient le chemin d’accès actuel et d’autres informations.

## <a name="built-in-help-system"></a>Système d’aide intégré

À l’instar des pages `man` Unix, PowerShell inclut des articles d’aide détaillés qui expliquent les concepts et la syntaxe de commande de PowerShell. Utilisez la cmdlet [Get-Help][] pour afficher ces articles à l’invite de commandes ou affichez les versions les plus récemment mises à jour de ces articles dans la documentation PowerShell en ligne.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur PowerShell, consultez la section **Découvrir PowerShell** de ce site.

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
