---
title: Installation de PowerShell Core sous macOS
description: Informations sur l’installation de PowerShell Core sur macOS
ms.date: 12/12/2018
ms.openlocfilehash: 70f5d64aa8a697a9011d07fbcb2bb821463827e1
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229740"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="c0038-103">Installation de PowerShell Core sous macOS</span><span class="sxs-lookup"><span data-stu-id="c0038-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="c0038-104">PowerShell Core prend en charge macOS 10.12 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c0038-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="c0038-105">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="c0038-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c0038-106">Une fois le package installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="c0038-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="c0038-107">À propos de Brew</span><span class="sxs-lookup"><span data-stu-id="c0038-107">About Brew</span></span>

<span data-ttu-id="c0038-108">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="c0038-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="c0038-109">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="c0038-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="c0038-110">Sinon, vous pouvez installer PowerShell par [Téléchargement direct](#installation-via-direct-download) ou à partir des [Archives binaires](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="c0038-110">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="c0038-111">Installation de la dernière version stable via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="c0038-111">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="c0038-112">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="c0038-112">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="c0038-113">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c0038-113">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="c0038-114">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="c0038-114">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="c0038-115">Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c0038-115">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="c0038-116">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="c0038-116">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="c0038-117">Installation de la dernière version préliminaire via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="c0038-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="c0038-118">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="c0038-118">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="c0038-119">Une fois Homebrew installé, vous pouvez installer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0038-119">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="c0038-120">Tout d’abord, installez le package [Cask-Versions][cask-versions], ce qui va vous permettre d’installer d’autres versions de packages cask :</span><span class="sxs-lookup"><span data-stu-id="c0038-120">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="c0038-121">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c0038-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="c0038-122">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="c0038-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="c0038-123">Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c0038-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="c0038-124">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="c0038-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="c0038-125">et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="c0038-125">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="c0038-126">Installation par téléchargement direct</span><span class="sxs-lookup"><span data-stu-id="c0038-126">Installation via Direct Download</span></span>

<span data-ttu-id="c0038-127">Téléchargez le package PKG `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="c0038-127">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="c0038-128">de la page [versions][] sur votre ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="c0038-128">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="c0038-129">Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="c0038-129">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="c0038-130">Installez [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="c0038-130">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="c0038-131">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0038-131">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="c0038-132">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="c0038-132">Binary Archives</span></span>

<span data-ttu-id="c0038-133">Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="c0038-133">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="c0038-134">Installation des archives binaires sur macOS</span><span class="sxs-lookup"><span data-stu-id="c0038-134">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="c0038-135">Installez [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="c0038-135">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="c0038-136">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0038-136">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="c0038-137">Installer les dépendances</span><span class="sxs-lookup"><span data-stu-id="c0038-137">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="c0038-138">Installer les outils en ligne de commande XCode</span><span class="sxs-lookup"><span data-stu-id="c0038-138">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="c0038-139">Installer OpenSSL</span><span class="sxs-lookup"><span data-stu-id="c0038-139">Install OpenSSL</span></span>

<span data-ttu-id="c0038-140">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0038-140">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="c0038-141">Vous pouvez l’installer avec MacPorts ou Brew.</span><span class="sxs-lookup"><span data-stu-id="c0038-141">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="c0038-142">Installer OpenSSL avec Brew</span><span class="sxs-lookup"><span data-stu-id="c0038-142">Install OpenSSL via Brew</span></span>

<span data-ttu-id="c0038-143">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="c0038-143">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="c0038-144">Exécutez `brew install openssl` pour installer OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="c0038-144">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="c0038-145">Installer OpenSSL avec MacPorts</span><span class="sxs-lookup"><span data-stu-id="c0038-145">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="c0038-146">Installez les [outils en ligne de commande XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="c0038-146">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="c0038-147">Installez MacPorts.</span><span class="sxs-lookup"><span data-stu-id="c0038-147">Install MacPorts.</span></span>
   <span data-ttu-id="c0038-148">Pour connaître les instructions à suivre, reportez-vous au [guide d’installation](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="c0038-148">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="c0038-149">Mettez à jour MacPorts en exécutant `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="c0038-149">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="c0038-150">Mettez à niveau les packages MacPorts en exécutant `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="c0038-150">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="c0038-151">Installez OpenSSL en exécutant `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="c0038-151">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="c0038-152">Liez les bibliothèques pour les mettre à la disposition de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c0038-152">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="c0038-153">Désinstallation de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c0038-153">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="c0038-154">Si vous avez installé PowerShell avec Homebrew, utilisez la commande suivante pour le désinstaller :</span><span class="sxs-lookup"><span data-stu-id="c0038-154">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="c0038-155">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="c0038-155">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="c0038-156">Pour supprimer les chemins d’accès PowerShell supplémentaires, reportez-vous à la section sur les [chemins d’accès](#paths) dans ce document et supprimez les chemins d’accès avec `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="c0038-156">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="c0038-157">Cela est inutile si vous avez installé PowerShell avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="c0038-157">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="c0038-158">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="c0038-158">Paths</span></span>

* <span data-ttu-id="c0038-159">`$PSHOME` est `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="c0038-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="c0038-160">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c0038-160">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c0038-161">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c0038-161">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c0038-162">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c0038-162">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c0038-163">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c0038-163">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c0038-164">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="c0038-164">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c0038-165">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c0038-165">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c0038-166">Les profils respectent la configuration par hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0038-166">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="c0038-167">Donc, le profil spécifique à l’hôte par défaut existe dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="c0038-167">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c0038-168">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.</span><span class="sxs-lookup"><span data-stu-id="c0038-168">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="c0038-169">Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="c0038-169">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="c0038-170">`$PSHOME` est donc `/usr/local/microsoft/powershell/6.2.0/` ; le lien symbolique se trouve à l’emplacement `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="c0038-170">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c0038-171">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c0038-171">Additional Resources</span></span>

* <span data-ttu-id="c0038-172">[Site web d’Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="c0038-172">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="c0038-173">[Dépôt GitHub d’Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="c0038-173">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="c0038-174">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="c0038-174">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
