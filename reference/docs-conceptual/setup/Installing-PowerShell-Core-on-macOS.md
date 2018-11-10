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
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="9251d-103">Installation de PowerShell Core sous macOS</span><span class="sxs-lookup"><span data-stu-id="9251d-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="9251d-104">PowerShell Core prend en charge macOS 10.12 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="9251d-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="9251d-105">Tous les packages sont disponibles dans notre page de [releases][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="9251d-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="9251d-106">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="9251d-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="9251d-107">À propos de Brew</span><span class="sxs-lookup"><span data-stu-id="9251d-107">About Brew</span></span>

<span data-ttu-id="9251d-108">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="9251d-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="9251d-109">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="9251d-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="9251d-110">Installation de la dernière version stable via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="9251d-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="9251d-111">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="9251d-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9251d-112">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="9251d-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="9251d-113">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="9251d-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="9251d-114">Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="9251d-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="9251d-115">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="9251d-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="9251d-116">Installation de la dernière version préliminaire via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="9251d-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="9251d-117">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="9251d-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9251d-118">Une fois que vous avez installé Homebrew, l’installation de PowerShell est facile.</span><span class="sxs-lookup"><span data-stu-id="9251d-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="9251d-119">Tout d’abord, installez [Cask-Versions][cask-versions], ce qui va vous permettre d’installer d’autres versions de packages cask :</span><span class="sxs-lookup"><span data-stu-id="9251d-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="9251d-120">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="9251d-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="9251d-121">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="9251d-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="9251d-122">Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="9251d-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="9251d-123">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="9251d-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="9251d-124">et actualiser les valeurs indiquées dans $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="9251d-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="9251d-125">Installation par téléchargement direct</span><span class="sxs-lookup"><span data-stu-id="9251d-125">Installation via Direct Download</span></span>

<span data-ttu-id="9251d-126">Téléchargez le package PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="9251d-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="9251d-127">de la page [releases][] (versions) sur votre ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="9251d-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="9251d-128">Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="9251d-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="9251d-129">Installez [OpenSSL](#install-openssl) (nécessaire pour les opérations de CIM et de communication à distance PowerShell).</span><span class="sxs-lookup"><span data-stu-id="9251d-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="9251d-130">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="9251d-130">Binary Archives</span></span>

<span data-ttu-id="9251d-131">Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="9251d-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="9251d-132">Installation des archives binaires sur macOS</span><span class="sxs-lookup"><span data-stu-id="9251d-132">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="9251d-133">Installez [OpenSSL](#install-openssl) (nécessaire pour les opérations de CIM et de communication à distance PowerShell).</span><span class="sxs-lookup"><span data-stu-id="9251d-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="9251d-134">Installer les dépendances</span><span class="sxs-lookup"><span data-stu-id="9251d-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="9251d-135">Installer les outils en ligne de commande XCode</span><span class="sxs-lookup"><span data-stu-id="9251d-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="9251d-136">Installer OpenSSL</span><span class="sxs-lookup"><span data-stu-id="9251d-136">Install OpenSSL</span></span>

<span data-ttu-id="9251d-137">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9251d-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="9251d-138">Vous pouvez l’installer avec MacPorts ou Brew.</span><span class="sxs-lookup"><span data-stu-id="9251d-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="9251d-139">Installer OpenSSL avec Brew</span><span class="sxs-lookup"><span data-stu-id="9251d-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="9251d-140">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="9251d-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9251d-141">Exécutez `brew install openssl` pour installer OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="9251d-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="9251d-142">Installer OpenSSL avec MacPorts</span><span class="sxs-lookup"><span data-stu-id="9251d-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="9251d-143">Installez les [outils en ligne de commande XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="9251d-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="9251d-144">Installez MacPorts.</span><span class="sxs-lookup"><span data-stu-id="9251d-144">Install MacPorts.</span></span>
   <span data-ttu-id="9251d-145">Pour connaître les instructions à suivre, consultez le [guide d’installation](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="9251d-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="9251d-146">Mettez à jour MacPorts en exécutant `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="9251d-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="9251d-147">Mettez à niveau les packages MacPorts en exécutant `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="9251d-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="9251d-148">Installez OpenSSL en exécutant `sudo port instal openssl`.</span><span class="sxs-lookup"><span data-stu-id="9251d-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="9251d-149">Liez les bibliothèques pour que PowerShell puisse les utiliser.</span><span class="sxs-lookup"><span data-stu-id="9251d-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="9251d-150">Désinstallation de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9251d-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="9251d-151">Si vous avez installé PowerShell avec Homebrew, la désinstallation est simple :</span><span class="sxs-lookup"><span data-stu-id="9251d-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="9251d-152">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="9251d-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="9251d-153">Pour supprimer les chemins PowerShell supplémentaires, consultez la section sur les [chemin d’accès](#paths) dans ce document et supprimez les chemins souhaités avec `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="9251d-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="9251d-154">Cela est inutile si vous avez installé PowerShell avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="9251d-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="9251d-155">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="9251d-155">Paths</span></span>

* <span data-ttu-id="9251d-156">`$PSHOME` est `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="9251d-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="9251d-157">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9251d-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="9251d-158">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9251d-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="9251d-159">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9251d-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9251d-160">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9251d-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9251d-161">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="9251d-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="9251d-162">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="9251d-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="9251d-163">Les profils respectent la configuration par hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9251d-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="9251d-164">Donc, les profils spécifiques à l’hôte par défaut existent dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="9251d-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="9251d-165">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.</span><span class="sxs-lookup"><span data-stu-id="9251d-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="9251d-166">Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="9251d-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="9251d-167">`$PSHOME` est donc `/usr/local/microsoft/powershell/6.1.0/` ; le lien symbolique se trouve à l’emplacement `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="9251d-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9251d-168">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="9251d-168">Additional Resources</span></span>

* <span data-ttu-id="9251d-169">[Site web d’Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="9251d-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="9251d-170">[Dépôt GitHub d’Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="9251d-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="9251d-171">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="9251d-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
