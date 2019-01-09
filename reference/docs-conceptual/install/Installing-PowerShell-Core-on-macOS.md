---
title: Installation de PowerShell Core sous macOS
description: Informations sur l’installation de PowerShell Core sur macOS
ms.date: 12/12/2018
ms.openlocfilehash: 91e64cace7d4ed988da56109dde9bf2a80528eb4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401432"
---
# <a name="installing-powershell-core-on-macos"></a>Installation de PowerShell Core sous macOS

PowerShell Core prend en charge macOS 10.12 et versions ultérieures.
Tous les packages sont disponibles dans notre page de [versions][] GitHub.
Une fois le package est installé, exécutez `pwsh` à partir d’un terminal.

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

Quand de nouvelles versions de PowerShell sont publiées, mettre à jour les formules de Homebrew et mettez à niveau PowerShell :

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh), mais l’interpréteur de commandes PowerShell doit être s’est arrêté puis redémarré pour terminer la mise à niveau et actualiser les valeurs indiquées dans `$PSVersionTable`.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installation de la dernière version préliminaire via Homebrew sur macOS 10.12 ou version ultérieure

Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).

Une fois que vous avez installé Homebrew, vous pouvez installer PowerShell.
Tout d’abord, installez le [Cask-Versions] [ cask-versions] package qui vous permet d’installer d’autres versions des packages de cask :

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

Quand de nouvelles versions de PowerShell sont publiées, mettre à jour les formules de Homebrew et mettez à niveau PowerShell :

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau
> et actualiser les valeurs indiquées dans `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Installation par téléchargement direct

Téléchargez le package PKG `powershell-6.1.0-osx-x64.pkg`
de la page [versions][] sur votre ordinateur macOS.

Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

Installez [OpenSSL](#install-openssl). OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.

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

Installez [OpenSSL](#install-openssl). OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.

## <a name="installing-dependencies"></a>Installer les dépendances

### <a name="install-xcode-command-line-tools"></a>Installer les outils en ligne de commande XCode

```sh
xcode-select --install
```

### <a name="install-openssl"></a>Installer OpenSSL

OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell. Vous pouvez l’installer avec MacPorts ou Brew.

#### <a name="install-openssl-via-brew"></a>Installer OpenSSL avec Brew

Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).

Pour installer OpenSSL, exécutez `brew install openssl`.

#### <a name="install-openssl-via-macports"></a>Installer OpenSSL avec MacPorts

1. Installer le [outils de ligne de commande XCode](#install-xcode-command-line-tools).
1. Installez MacPorts.
   Si vous avez besoin d’instructions, reportez-vous à la [guide d’installation](https://guide.macports.org/chunked/installing.macports.html).
1. Mettez à jour MacPorts en exécutant `sudo port selfupdate`.
1. Mettez à niveau les packages MacPorts en exécutant `sudo port upgrade outdated`.
1. Installez OpenSSL en exécutant `sudo port install openssl`.
1. Lier les bibliothèques pour les rendre disponibles à PowerShell :

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>Désinstallation de PowerShell Core

Si vous avez installé PowerShell avec Homebrew, utilisez la commande suivante pour désinstaller :

```sh
brew cask uninstall powershell
```

Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Pour supprimer les chemins PowerShell supplémentaires, reportez-vous à la [chemins](#paths) section de ce document et de supprimer les chemins d’accès à l’aide de `sudo rm`.

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
Pour le profil de spécifique à l’hôte par défaut existe à `Microsoft.PowerShell_profile.ps1` dans les mêmes emplacements.

PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.

Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.
Par conséquent, `$PSHOME` est `/usr/local/microsoft/powershell/6.1.0/`, et le lien symbolique est placé au niveau `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ressources supplémentaires

* [Site web d’Homebrew][brew]
* [Dépôt GitHub d’Homebrew][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
