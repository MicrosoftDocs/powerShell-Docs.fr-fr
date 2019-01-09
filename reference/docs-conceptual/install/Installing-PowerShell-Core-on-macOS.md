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
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="07af4-103">Installation de PowerShell Core sous macOS</span><span class="sxs-lookup"><span data-stu-id="07af4-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="07af4-104">PowerShell Core prend en charge macOS 10.12 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="07af4-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="07af4-105">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="07af4-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="07af4-106">Une fois le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="07af4-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="07af4-107">À propos de Brew</span><span class="sxs-lookup"><span data-stu-id="07af4-107">About Brew</span></span>

<span data-ttu-id="07af4-108">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="07af4-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="07af4-109">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="07af4-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="07af4-110">Installation de la dernière version stable via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="07af4-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="07af4-111">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="07af4-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="07af4-112">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="07af4-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="07af4-113">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="07af4-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="07af4-114">Quand de nouvelles versions de PowerShell sont publiées, mettre à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="07af4-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="07af4-115">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh), mais l’interpréteur de commandes PowerShell doit être s’est arrêté puis redémarré pour terminer la mise à niveau et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="07af4-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="07af4-116">Installation de la dernière version préliminaire via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="07af4-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="07af4-117">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="07af4-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="07af4-118">Une fois que vous avez installé Homebrew, vous pouvez installer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07af4-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="07af4-119">Tout d’abord, installez le [Cask-Versions] [ cask-versions] package qui vous permet d’installer d’autres versions des packages de cask :</span><span class="sxs-lookup"><span data-stu-id="07af4-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="07af4-120">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="07af4-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="07af4-121">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="07af4-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="07af4-122">Quand de nouvelles versions de PowerShell sont publiées, mettre à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="07af4-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="07af4-123">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="07af4-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="07af4-124">et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="07af4-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="07af4-125">Installation par téléchargement direct</span><span class="sxs-lookup"><span data-stu-id="07af4-125">Installation via Direct Download</span></span>

<span data-ttu-id="07af4-126">Téléchargez le package PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="07af4-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="07af4-127">de la page [versions][] sur votre ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="07af4-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="07af4-128">Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="07af4-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="07af4-129">Installez [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="07af4-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="07af4-130">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07af4-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="07af4-131">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="07af4-131">Binary Archives</span></span>

<span data-ttu-id="07af4-132">Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="07af4-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="07af4-133">Installation des archives binaires sur macOS</span><span class="sxs-lookup"><span data-stu-id="07af4-133">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="07af4-134">Installez [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="07af4-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="07af4-135">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07af4-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="07af4-136">Installer les dépendances</span><span class="sxs-lookup"><span data-stu-id="07af4-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="07af4-137">Installer les outils en ligne de commande XCode</span><span class="sxs-lookup"><span data-stu-id="07af4-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="07af4-138">Installer OpenSSL</span><span class="sxs-lookup"><span data-stu-id="07af4-138">Install OpenSSL</span></span>

<span data-ttu-id="07af4-139">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07af4-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="07af4-140">Vous pouvez l’installer avec MacPorts ou Brew.</span><span class="sxs-lookup"><span data-stu-id="07af4-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="07af4-141">Installer OpenSSL avec Brew</span><span class="sxs-lookup"><span data-stu-id="07af4-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="07af4-142">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="07af4-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="07af4-143">Pour installer OpenSSL, exécutez `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="07af4-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="07af4-144">Installer OpenSSL avec MacPorts</span><span class="sxs-lookup"><span data-stu-id="07af4-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="07af4-145">Installer le [outils de ligne de commande XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="07af4-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="07af4-146">Installez MacPorts.</span><span class="sxs-lookup"><span data-stu-id="07af4-146">Install MacPorts.</span></span>
   <span data-ttu-id="07af4-147">Si vous avez besoin d’instructions, reportez-vous à la [guide d’installation](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="07af4-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="07af4-148">Mettez à jour MacPorts en exécutant `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="07af4-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="07af4-149">Mettez à niveau les packages MacPorts en exécutant `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="07af4-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="07af4-150">Installez OpenSSL en exécutant `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="07af4-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="07af4-151">Lier les bibliothèques pour les rendre disponibles à PowerShell :</span><span class="sxs-lookup"><span data-stu-id="07af4-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="07af4-152">Désinstallation de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="07af4-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="07af4-153">Si vous avez installé PowerShell avec Homebrew, utilisez la commande suivante pour désinstaller :</span><span class="sxs-lookup"><span data-stu-id="07af4-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="07af4-154">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="07af4-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="07af4-155">Pour supprimer les chemins PowerShell supplémentaires, reportez-vous à la [chemins](#paths) section de ce document et de supprimer les chemins d’accès à l’aide de `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="07af4-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="07af4-156">Cela est inutile si vous avez installé PowerShell avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="07af4-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="07af4-157">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="07af4-157">Paths</span></span>

* <span data-ttu-id="07af4-158">`$PSHOME` est `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="07af4-158">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="07af4-159">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="07af4-159">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="07af4-160">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="07af4-160">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="07af4-161">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="07af4-161">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="07af4-162">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="07af4-162">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="07af4-163">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="07af4-163">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="07af4-164">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="07af4-164">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="07af4-165">Les profils respectent la configuration par hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07af4-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="07af4-166">Pour le profil de spécifique à l’hôte par défaut existe à `Microsoft.PowerShell_profile.ps1` dans les mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="07af4-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="07af4-167">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.</span><span class="sxs-lookup"><span data-stu-id="07af4-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="07af4-168">Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="07af4-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="07af4-169">Par conséquent, `$PSHOME` est `/usr/local/microsoft/powershell/6.1.0/`, et le lien symbolique est placé au niveau `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="07af4-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="07af4-170">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="07af4-170">Additional Resources</span></span>

* <span data-ttu-id="07af4-171">[Site web d’Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="07af4-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="07af4-172">[Dépôt GitHub d’Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="07af4-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="07af4-173">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="07af4-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
