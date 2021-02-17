---
title: Installation de PowerShell sur macOS
description: Informations sur l’installation de PowerShell sur macOS
ms.date: 02/02/2021
ms.openlocfilehash: 3ae1fe0eb29b4d826221a2c11db19bc18c3efba7
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563213"
---
# <a name="installing-powershell-on-macos"></a>Installation de PowerShell sur macOS

PowerShell 7.0 ou version ultérieure nécessite macOS 10.13 et versions ultérieures. Tous les packages sont disponibles dans notre page de [versions][] GitHub. Une fois le package installé, exécutez `pwsh` à partir d’un terminal.

> [!NOTE]
> PowerShell 7.1 est une mise à niveau sur place qui supprime PowerShell Core 6.x et 7.0.
>
> Le dossier `/usr/local/microsoft/powershell/6` est remplacé par `/usr/local/microsoft/powershell/7`.
>
> Si vous devez exécuter une ancienne version de PowerShell Core côte à côte avec PowerShell 7.1, installez la version de votre choix à l’aide de la méthode [Archive binaire](#binary-archives).

Il existe plusieurs façons d’installer PowerShell sur macOS. Choisissez l’une des méthodes suivantes :

- Installation avec Homebrew. Homebrew est le gestionnaire de package préféré pour macOS.
- Installation de PowerShell par [téléchargement direct](#installation-via-direct-download).
- Installation à partir d’[archives binaires](#binary-archives).

Après avoir installé PowerShell, vous devez installer [OpenSSL](#installing-dependencies). OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a>Installation de la dernière version stable par le biais de Homebrew sur macOS 10.13 ou ultérieur

Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [ces instructions][brew].

Maintenant, vous pouvez installer PowerShell :

```sh
brew install --cask powershell
```

Enfin, vérifiez que votre installation fonctionne correctement :

```sh
pwsh
```

Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans `$PSVersionTable`.

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a>Installation de la dernière préversion par le biais de Homebrew sur macOS 10.13 ou ultérieur

Une fois Homebrew installé, vous pouvez installer PowerShell. Tout d’abord, installez le package [Cask-Versions][cask-versions], ce qui va vous permettre d’installer d’autres versions de packages cask :

```sh
brew tap homebrew/cask-versions
```

Maintenant, vous pouvez installer PowerShell :

```sh
brew install --cask powershell-preview
```

Enfin, vérifiez que votre installation fonctionne correctement :

```sh
pwsh-preview
```

Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau
> et actualiser les valeurs indiquées dans `$PSVersionTable`.

L’installation de PowerShell avec la méthode tap Homebrew est également prise en charge pour les versions stables et LTS.

```sh
brew install powershell/tap/powershell
```

Vous pouvez maintenant vérifier votre installation.

```sh
pwsh
```

Quand de nouvelles versions de PowerShell sont publiées, exécutez simplement la commande suivante.

```sh
brew upgrade powershell
```

> [!NOTE]
> Que vous utilisiez la méthode cask ou tap, lors de la mise à jour vers une version plus récente de PowerShell, utilisez la même méthode que celle utilisée pour l’installation initiale de PowerShell. Si vous utilisez une autre méthode, l’ouverture d’une nouvelle session pwsh continuera à utiliser l’ancienne version de PowerShell.
>
> Si vous décidez d’utiliser d’autres méthodes, vous pouvez corriger le problème à l’aide de la [méthode link Homebrew](https://docs.brew.sh/Manpage#link-ln-options-formula).

## <a name="installation-via-direct-download"></a>Installation par téléchargement direct

Téléchargez le package PKG `powershell-7.1.2-osx-x64.pkg` à partir de la page de [versions][] sur votre ordinateur macOS.

Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :

```sh
sudo installer -pkg powershell-7.1.2-osx-x64.pkg -target /
```

Installez [OpenSSL](#installing-dependencies). OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.

## <a name="install-as-a-net-global-tool"></a>Installation en tant qu’outil global .NET

Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Le programme d’installation de l’outil dotnet ajoute `~/.dotnet/tools` à votre variable d’environnement `PATH`. Toutefois, le `PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour. Vous devez pouvoir démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.

Installez [OpenSSL](#installing-dependencies). OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.

## <a name="binary-archives"></a>Archives binaires

Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés. Quand vous installez avec cette méthode, vous devez également installer manuellement toutes les dépendances.

Installez [OpenSSL](#installing-dependencies). OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.

### <a name="installing-binary-archives-on-macos"></a>Installation des archives binaires sur macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.2/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a>Installer les dépendances

OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell. Vous pouvez installer OpenSSL par le biais de MacPorts si nécessaire.

> [!NOTE]
> Utilisés ensemble sur le même système, MacPorts et Homebrew peuvent rencontrer des problèmes. En revanche, Homebrew n’a pas de package pour OpenSSL 1.0. Pour plus d’informations, consultez les [questions fréquentes (FAQ) sur MacPorts](https://trac.macports.org/wiki/FAQ).

1. Installez les outils en ligne de commande Xcode. Les outils Xcode sont une exigence de MacPorts.

   ```sh
   xcode-select --install
   ```

1. Installez MacPorts. Pour connaître les instructions à suivre, reportez-vous au [guide d’installation](https://www.macports.org/install.php).
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

- `$PSHOME` est `/usr/local/microsoft/powershell/7.1.2/`
- Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`
- Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`
- Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`
- Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`
- Les modules par défaut sont lus à partir de `$PSHOME/Modules`
- L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Les profils respectent la configuration par hôte de PowerShell. Donc, le profil spécifique à l’hôte par défaut existe dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.

PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.

Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`. `$PSHOME` est donc `/usr/local/microsoft/powershell/7.1.2/` ; le lien symbolique se trouve à l’emplacement `/usr/local/bin/pwsh`.

## <a name="installation-support"></a>Prise en charge de l’installation

Microsoft prend en charge les méthodes d’installation mentionnées dans ce document. D’autres méthodes d’installation peuvent être disponibles à partir d’autres sources. Même s’il est possible que ces outils et méthodes fonctionnent, Microsoft ne peut pas prendre en charge ces méthodes.

## <a name="additional-resources"></a>Ressources supplémentaires

- [Site web d’Homebrew][brew]
- [Dépôt GitHub d’Homebrew][GitHub]
- [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versions]: https://aka.ms/powershell-release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
