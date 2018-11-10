---
title: Installation de PowerShell Core sous macOS
description: Informations sur l’installation de PowerShell Core sur macOS
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998501"
---
# <a name="installing-powershell-core-on-macos"></a>Installation de PowerShell Core sous macOS

PowerShell Core prend en charge macOS 10.12 et versions ultérieures.
Tous les packages sont disponibles dans notre page de [releases][] GitHub.
Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.

## <a name="about-brew"></a>À propos de Brew

[Homebrew][brew] est le gestionnaire de package préféré pour macOS.
Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installation de la dernière version stable via Homebrew sur macOS 10.12 ou version ultérieure

Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).

Maintenant, vous pouvez installer PowerShell :

```sh
brew cask install powershell
```

Enfin, vérifiez que votre installation fonctionne correctement :

```sh
pwsh
```

Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans $PSVersionTable.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installation de la dernière version préliminaire via Homebrew sur macOS 10.12 ou version ultérieure

Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).

Une fois que vous avez installé Homebrew, l’installation de PowerShell est facile.
Tout d’abord, installez [Cask-Versions][cask-versions], ce qui va vous permettre d’installer d’autres versions de packages cask :

```sh
brew tap homebrew/cask-versions
```

Maintenant, vous pouvez installer PowerShell :

```sh
brew cask install powershell-preview
```

Enfin, vérifiez que votre installation fonctionne correctement :

```sh
pwsh-preview
```

Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau
> et actualiser les valeurs indiquées dans $PSVersionTable.

## <a name="installation-via-direct-download"></a>Installation par téléchargement direct

Téléchargez le package PKG `powershell-6.1.0-osx-x64.pkg`
de la page [releases][] (versions) sur votre ordinateur macOS.

Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

Installez [OpenSSL](#install-openssl) (nécessaire pour les opérations de CIM et de communication à distance PowerShell).

## <a name="binary-archives"></a>Archives binaires

Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés.

### <a name="installing-binary-archives-on-macos"></a>Installation des archives binaires sur macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

Installez [OpenSSL](#install-openssl) (nécessaire pour les opérations de CIM et de communication à distance PowerShell).

## <a name="installing-dependencies"></a>Installer les dépendances

### <a name="install-xcode-command-line-tools"></a>Installer les outils en ligne de commande XCode

```shell
xcode-select -install
```

### <a name="install-openssl"></a>Installer OpenSSL

OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.  Vous pouvez l’installer avec MacPorts ou Brew.

#### <a name="install-openssl-via-brew"></a>Installer OpenSSL avec Brew

Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).

Exécutez `brew install openssl` pour installer OpenSSL.

#### <a name="install-openssl-via-macports"></a>Installer OpenSSL avec MacPorts

1. Installez les [outils en ligne de commande XCode](#install-xcode-command-line-tools).
1. Installez MacPorts.
   Pour connaître les instructions à suivre, consultez le [guide d’installation](https://guide.macports.org/chunked/installing.macports.html).
1. Mettez à jour MacPorts en exécutant `sudo port selfupdate`.
1. Mettez à niveau les packages MacPorts en exécutant `sudo port upgrade outdated`.
1. Installez OpenSSL en exécutant `sudo port instal openssl`.
1. Liez les bibliothèques pour que PowerShell puisse les utiliser.

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
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

Pour supprimer les chemins PowerShell supplémentaires, consultez la section sur les [chemin d’accès](#paths) dans ce document et supprimez les chemins souhaités avec `sudo rm`.

> [!NOTE]
> Cela est inutile si vous avez installé PowerShell avec Homebrew.

## <a name="paths"></a>Chemins d’accès

* `$PSHOME` est `/usr/local/microsoft/powershell/6.1.0/`
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
`$PSHOME` est donc `/usr/local/microsoft/powershell/6.1.0/` ; le lien symbolique se trouve à l’emplacement `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ressources supplémentaires

* [Site web d’Homebrew][brew]
* [Dépôt GitHub d’Homebrew][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
