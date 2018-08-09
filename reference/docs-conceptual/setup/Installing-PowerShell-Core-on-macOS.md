---
title: Installation de PowerShell Core sur macOS
description: Informations sur l’installation de PowerShell Core sur macOS
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587463"
---
# <a name="installing-powershell-core-on-macos"></a>Installation de PowerShell Core sur macOS

PowerShell Core prend en charge macOS 10.12 et versions ultérieures.
Tous les packages sont disponibles dans notre page de [versions][] GitHub.
Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.

### <a name="installation-via-homebrew-on-macos-1012"></a>Installation via Homebrew sur macOS 10.12+

[Homebrew][brew] est le gestionnaire de package préféré pour macOS.
Dans une fenêtre de terminal, tapez `brew` pour exécuter Homebrew.  Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].

> [!NOTE]
> Si vous avez déjà installé Homebrew, il est toujours judicieux d’exécuter « brew update-reset » et « brew update ».
```sh
brew update-reset
brew update
```

> Les anciennes versions d’Homebrew utilisaient le tap « caskroom/cask », qui a été déprécié et migré vers « homebrew/cask ».  Pour plus d’informations, consultez [Homebrew-cask][cask]. Utilisez la commande « brew tap » pour lister vos taps actuels.  Si vous voyez « caskroom/cask », vous pouvez utiliser « brew update » pour qu’Homebrew fasse migrer les taps.

```sh
brew tap
brew update
```

Une fois que vous avez installé/mis à jour Homebrew, l’installation de PowerShell est simple.

Pour installer PowerShell :

```sh
brew cask install powershell
```

Enfin, vérifiez que votre installation fonctionne correctement :

```sh
pwsh
```

Pour quitter PowerShell et retourner à bash, utilisez la commande « exit ».
```sh
exit
```

Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans $PSVersionTable.

### <a name="installing-preview-via-homebrew-on-macos-1012"></a>Installation de la préversion via Homebrew sur macOS 10.12+

[Homebrew][brew] est le gestionnaire de package préféré pour macOS.
Dans une fenêtre de terminal, tapez `brew` pour exécuter Homebrew.  Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].

> [!NOTE]
> Si vous avez déjà installé Homebrew, il est toujours judicieux d’exécuter « brew update-reset » et « brew update ».
```sh
brew update-reset
brew update
```

Vous devez ensuite effectuer un tap du dépôt `versions` casks pour obtenir le package de préversion :

```sh
brew tap homebrew/cask-versions
```

Pour installer la préversion de PowerShell :

```sh
brew cask install powershell-preview
```

Enfin, vérifiez que votre installation fonctionne correctement :

```sh
pwsh-preview
```

Quand de nouvelles versions de PowerShell sont disponibles, il vous suffit de mettre à jour les formules de Homebrew et de mettre à niveau la préversion de PowerShell :

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans $PSVersionTable.

### <a name="installation-via-direct-download"></a>Installation par téléchargement direct

Téléchargez le package PKG `powershell-6.0.2-osx.10.12-x64.pkg` à partir de la page de [versions][] sur votre ordinateur macOS.

Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Archives binaires

Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes macOS et Linux afin de permettre des scénarios de déploiement avancés.

### <a name="installing-binary-archives-on-macos"></a>Installation des archives binaires sur macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a>Désinstallation de PowerShell Core

Si vous avez installé PowerShell avec Homebrew, la désinstallation est simple :

```sh
brew cask uninstall powershell
```

Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Pour supprimer les chemins PowerShell supplémentaires, consultez la section sur les [chemin d’accès][] dans ce document et supprimez les chemins souhaités avec `sudo rm`.

> [!NOTE]
> Cela est inutile si vous avez installé PowerShell avec Homebrew.

[chemin d’accès]:#paths

## <a name="paths"></a>Chemins d’accès

* `$PSHOME` est `/usr/local/microsoft/powershell/6.0.2/`
* Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`
* Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`
* Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`
* Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`
* Les modules par défaut sont lus à partir de `$PSHOME/Modules`
* L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Les profils respectent la configuration par hôte de PowerShell.
Donc, les profils spécifiques à l’hôte par défaut existent dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.

PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.

Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.
Par conséquent, `$PSHOME` est `/usr/local/microsoft/powershell/6.0.2/`, et le lien symbolique est placé sur `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ressources supplémentaires

* [Site web d’Homebrew][brew]
* [Dépôt GitHub d’Homebrew][GitHub]
* [Homebrew-Cask][cask]


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
