---
title: Installation de PowerShell sur macOS
description: Informations sur l’installation de PowerShell sur macOS
ms.date: 05/21/2020
ms.openlocfilehash: 32b3ebf3eb4017af41fc1a062f2f0a2e08629a58
ms.sourcegitcommit: fd6a33b9fac973b3554fecfea7f51475e650a606
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83791476"
---
# <a name="installing-powershell-on-macos"></a>Installation de PowerShell sur macOS

PowerShell Core prend en charge la version 10.12 et les versions ultérieures de macOS.
Tous les packages sont disponibles dans notre page de [versions][] GitHub.
Une fois le package installé, exécutez `pwsh` à partir d’un terminal.

> [!NOTE]
> PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.
>
> Le dossier `/usr/local/microsoft/powershell/6` est remplacé par `/usr/local/microsoft/powershell/7`.
>
> Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [Archive binaire](#binary-archives).

## <a name="about-brew"></a>À propos de Brew

[Homebrew][brew] est le gestionnaire de package préféré pour macOS. Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [ces instructions][brew]. Sinon, vous pouvez installer PowerShell par [Téléchargement direct](#installation-via-direct-download) ou à partir des [Archives binaires](#binary-archives).

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

Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans `$PSVersionTable`.

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installation de la dernière version préliminaire via Homebrew sur macOS 10.12 ou version ultérieure

Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).

Une fois Homebrew installé, vous pouvez installer PowerShell.
Tout d’abord, installez le package [Cask-Versions][cask-versions] qui vous permettre d’installer d’autres versions de packages cask :

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

Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau
> et actualiser les valeurs indiquées dans `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Installation par téléchargement direct

Téléchargez le package PKG `powershell-lts-7.0.1-osx-x64.pkg`
de la page [versions][] sur votre ordinateur macOS.

Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :

```sh
sudo installer -pkg powershell-lts-7.0.1-osx-x64.pkg -target /
```

Installez [OpenSSL](#install-openssl). OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.

## <a name="install-as-a-net-global-tool"></a>Installation en tant qu’outil global .NET

Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Le programme d’installation de l’outil dotnet ajoute `~/.dotnet/tools` à votre variable d’environnement `PATH`. Toutefois, le `PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour. Vous devez pouvoir démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.

## <a name="binary-archives"></a>Archives binaires

Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés.

### <a name="installing-binary-archives-on-macos"></a>Installation des archives binaires sur macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.1

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.1

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.1/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.1/pwsh /usr/local/bin/pwsh
```

Installez [OpenSSL](#install-openssl). OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.

## <a name="installing-dependencies"></a>Installer les dépendances

### <a name="install-xcode-command-line-tools"></a>Installer les outils en ligne de commande XCode

```sh
xcode-select --install
```

### <a name="install-openssl"></a>Installer OpenSSL

OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell. Vous pouvez l’installer avec MacPorts.

#### <a name="install-openssl-via-macports"></a>Installer OpenSSL avec MacPorts

1. Installez les [outils en ligne de commande XCode](#install-xcode-command-line-tools).
1. Installez MacPorts.
   Pour connaître les instructions à suivre, reportez-vous au [guide d’installation](https://guide.macports.org/chunked/installing.macports.html).
1. Mettez à jour MacPorts en exécutant `sudo port selfupdate`.
1. Mettez à niveau les packages MacPorts en exécutant `sudo port upgrade outdated`.
1. Installez OpenSSL en exécutant `sudo port install openssl10`.
1. Liez les bibliothèques pour les mettre à la disposition de PowerShell :

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a>Désinstallation de PowerShell

Si vous avez installé PowerShell avec Homebrew, utilisez la commande suivante pour le désinstaller :

```sh
brew cask uninstall powershell
```

Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Pour supprimer les chemins d’accès PowerShell supplémentaires, reportez-vous à la section sur les [chemins d’accès](#paths) dans ce document et supprimez les chemins d’accès avec `sudo rm`.

> [!NOTE]
> Cela est inutile si vous avez installé PowerShell avec Homebrew.

## <a name="paths"></a>Chemins

* `$PSHOME` est `/usr/local/microsoft/powershell/7.0.1/`
* Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`
* Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`
* Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`
* Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`
* Les modules par défaut sont lus à partir de `$PSHOME/Modules`
* L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Les profils respectent la configuration par hôte de PowerShell.
Donc, le profil spécifique à l’hôte par défaut existe dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.

PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.

Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.
`$PSHOME` est donc `/usr/local/microsoft/powershell/7.0.1/` ; le lien symbolique se trouve à l’emplacement `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ressources supplémentaires

* [Site web Homebrew][brew]
* [Dépôt Homebrew sur GitHub][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
