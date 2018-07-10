# <a name="installing-powershell-core-on-macos"></a>Installation de PowerShell Core sous macOS

PowerShell Core prend en charge macOS 10.12 et versions ultérieures.
Tous les packages sont disponibles dans notre page de [versions][] GitHub.
Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.

### <a name="installation-via-homebrew-on-macos-1012"></a>Installation via Homebrew sous macOS 10.12

[Homebrew][brew] est le gestionnaire de package préféré pour macOS.
Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].

Une fois que vous avez installé Homebrew, l’installation de PowerShell est facile.
Pour commencer, installez [Homebrew-Cask][cask] afin de pouvoir installer d’autres packages :

```sh
brew tap caskroom/cask
```

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
[cask]: https://caskroom.github.io/

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

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
