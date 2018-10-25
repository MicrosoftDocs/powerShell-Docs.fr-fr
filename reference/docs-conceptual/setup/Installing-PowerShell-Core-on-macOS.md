---
title: Installation de PowerShell Core sous macOS
description: Informations sur l’installation de PowerShell Core sur macOS
ms.date: 08/06/2018
ms.openlocfilehash: 042c933dfa83f3ab52e315036e4f817145116d00
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611485"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="26af8-103">Installation de PowerShell Core sous macOS</span><span class="sxs-lookup"><span data-stu-id="26af8-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="26af8-104">PowerShell Core prend en charge macOS 10.12 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="26af8-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="26af8-105">Tous les packages sont disponibles dans notre page de [releases][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="26af8-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="26af8-106">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="26af8-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="26af8-107">Installation de la dernière version stable via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="26af8-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="26af8-108">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="26af8-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="26af8-109">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="26af8-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="26af8-110">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="26af8-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="26af8-111">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="26af8-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="26af8-112">Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="26af8-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="26af8-113">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="26af8-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="26af8-114">et actualiser les valeurs indiquées dans $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="26af8-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="26af8-115">Installation de la dernière version préliminaire via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="26af8-115">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="26af8-116">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="26af8-116">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="26af8-117">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="26af8-117">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="26af8-118">Une fois que vous avez installé Homebrew, l’installation de PowerShell est facile.</span><span class="sxs-lookup"><span data-stu-id="26af8-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="26af8-119">Tout d’abord, installez [Cask-Versions][cask-versions], ce qui va vous permettre d’installer d’autres versions de packages cask :</span><span class="sxs-lookup"><span data-stu-id="26af8-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="26af8-120">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="26af8-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="26af8-121">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="26af8-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="26af8-122">Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="26af8-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="26af8-123">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="26af8-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="26af8-124">et actualiser les valeurs indiquées dans $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="26af8-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="26af8-125">Installation par téléchargement direct</span><span class="sxs-lookup"><span data-stu-id="26af8-125">Installation via Direct Download</span></span>

<span data-ttu-id="26af8-126">Téléchargez le package PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="26af8-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="26af8-127">de la page [releases][] (versions) sur votre ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="26af8-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="26af8-128">Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="26af8-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="26af8-129">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="26af8-129">Binary Archives</span></span>

<span data-ttu-id="26af8-130">Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="26af8-130">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="26af8-131">Installation des archives binaires sur macOS</span><span class="sxs-lookup"><span data-stu-id="26af8-131">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="26af8-132">Désinstallation de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="26af8-132">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="26af8-133">Si vous avez installé PowerShell avec Homebrew, la désinstallation est simple :</span><span class="sxs-lookup"><span data-stu-id="26af8-133">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="26af8-134">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="26af8-134">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="26af8-135">Pour supprimer les chemins PowerShell supplémentaires, consultez la section sur les [chemin d’accès](#paths) dans ce document et supprimez les chemins souhaités avec `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="26af8-135">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="26af8-136">Cela est inutile si vous avez installé PowerShell avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="26af8-136">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="26af8-137">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="26af8-137">Paths</span></span>

* <span data-ttu-id="26af8-138">`$PSHOME` est `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="26af8-138">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="26af8-139">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="26af8-139">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="26af8-140">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="26af8-140">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="26af8-141">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="26af8-141">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="26af8-142">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="26af8-142">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="26af8-143">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="26af8-143">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="26af8-144">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="26af8-144">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="26af8-145">Les profils respectent la configuration par hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26af8-145">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="26af8-146">Donc, les profils spécifiques à l’hôte par défaut existent dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="26af8-146">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="26af8-147">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.</span><span class="sxs-lookup"><span data-stu-id="26af8-147">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="26af8-148">Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="26af8-148">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="26af8-149">Par conséquent, `$PSHOME` est `/usr/local/microsoft/powershell/6.1.0/`, et le lien symbolique est placé sur `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="26af8-149">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="26af8-150">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="26af8-150">Additional Resources</span></span>

* <span data-ttu-id="26af8-151">[Site web d’Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="26af8-151">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="26af8-152">[Dépôt GitHub d’Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="26af8-152">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="26af8-153">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="26af8-153">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
