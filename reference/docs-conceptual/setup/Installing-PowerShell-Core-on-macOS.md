# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="0c5f1-101">Installation de PowerShell Core sous macOS</span><span class="sxs-lookup"><span data-stu-id="0c5f1-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="0c5f1-102">PowerShell Core prend en charge macOS 10.12 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="0c5f1-103">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="0c5f1-104">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="0c5f1-105">Installation via Homebrew sur macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="0c5f1-105">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="0c5f1-106">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="0c5f1-107">Dans une fenêtre de terminal, tapez `brew` pour exécuter Homebrew.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-107">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="0c5f1-108">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="0c5f1-108">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="0c5f1-109">Si vous avez déjà installé Homebrew, il est toujours judicieux d’exécuter « brew update-reset » et « brew update ».</span><span class="sxs-lookup"><span data-stu-id="0c5f1-109">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="0c5f1-110">Les anciennes versions d’Homebrew utilisaient le tap « caskroom/cask », qui a été déprécié et migré vers « homebrew/cask ».</span><span class="sxs-lookup"><span data-stu-id="0c5f1-110">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="0c5f1-111">Pour plus d’informations, consultez [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="0c5f1-111">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="0c5f1-112">Utilisez la commande « brew tap » pour lister vos taps actuels.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-112">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="0c5f1-113">Si vous voyez « caskroom/cask », vous pouvez utiliser « brew update » pour qu’Homebrew fasse migrer les taps.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-113">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="0c5f1-114">Une fois que vous avez installé/mis à jour Homebrew, l’installation de PowerShell est simple.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-114">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="0c5f1-115">Pour installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-115">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="0c5f1-116">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-116">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="0c5f1-117">Pour quitter PowerShell et retourner à bash, utilisez la commande « exit ».</span><span class="sxs-lookup"><span data-stu-id="0c5f1-117">To exit PowerShell, and return to bash, use the 'exit' command.</span></span> 
```sh
exit
```

<span data-ttu-id="0c5f1-118">Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-118">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="0c5f1-119">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="0c5f1-120">Installation de la préversion via Homebrew sur macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="0c5f1-120">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="0c5f1-121">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-121">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="0c5f1-122">Dans une fenêtre de terminal, tapez `brew` pour exécuter Homebrew.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-122">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="0c5f1-123">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="0c5f1-123">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="0c5f1-124">Si vous avez déjà installé Homebrew, il est toujours judicieux d’exécuter « brew update-reset » et « brew update ».</span><span class="sxs-lookup"><span data-stu-id="0c5f1-124">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="0c5f1-125">Vous devez ensuite effectuer un tap du dépôt `versions` casks pour obtenir le package de préversion :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-125">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="0c5f1-126">Pour installer la préversion de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-126">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="0c5f1-127">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-127">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="0c5f1-128">Quand de nouvelles versions de PowerShell sont disponibles, il vous suffit de mettre à jour les formules de Homebrew et de mettre à niveau la préversion de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-128">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="0c5f1-129">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-129">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="0c5f1-130">Installation par téléchargement direct</span><span class="sxs-lookup"><span data-stu-id="0c5f1-130">Installation via Direct Download</span></span>

<span data-ttu-id="0c5f1-131">Téléchargez le package PKG `powershell-6.0.2-osx.10.12-x64.pkg` à partir de la page de [versions][] sur votre ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-131">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="0c5f1-132">Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="0c5f1-133">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="0c5f1-133">Binary Archives</span></span>

<span data-ttu-id="0c5f1-134">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes macOS et Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-134">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="0c5f1-135">Installation des archives binaires sur macOS</span><span class="sxs-lookup"><span data-stu-id="0c5f1-135">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="0c5f1-136">Désinstallation de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="0c5f1-136">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="0c5f1-137">Si vous avez installé PowerShell avec Homebrew, la désinstallation est simple :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-137">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="0c5f1-138">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="0c5f1-138">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="0c5f1-139">Pour supprimer les chemins PowerShell supplémentaires, consultez la section sur les [chemin d’accès][] dans ce document et supprimez les chemins souhaités avec `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-139">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="0c5f1-140">Cela est inutile si vous avez installé PowerShell avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-140">This is not necessary if you installed with Homebrew.</span></span>

[chemin d’accès]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="0c5f1-142">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="0c5f1-142">Paths</span></span>

* <span data-ttu-id="0c5f1-143">`$PSHOME` est `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="0c5f1-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="0c5f1-144">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0c5f1-144">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="0c5f1-145">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0c5f1-145">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="0c5f1-146">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0c5f1-146">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0c5f1-147">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0c5f1-147">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0c5f1-148">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="0c5f1-148">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="0c5f1-149">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="0c5f1-149">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="0c5f1-150">Les profils respectent la configuration par hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-150">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="0c5f1-151">Donc, les profils spécifiques à l’hôte par défaut existent dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-151">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0c5f1-152">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-152">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="0c5f1-153">Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-153">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="0c5f1-154">Par conséquent, `$PSHOME` est `/usr/local/microsoft/powershell/6.0.2/`, et le lien symbolique est placé sur `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="0c5f1-154">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0c5f1-155">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="0c5f1-155">Additional Resources</span></span>

* <span data-ttu-id="0c5f1-156">[Site web d’Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="0c5f1-156">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="0c5f1-157">[Dépôt GitHub d’Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="0c5f1-157">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="0c5f1-158">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="0c5f1-158">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
