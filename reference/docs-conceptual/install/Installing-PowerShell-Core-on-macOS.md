---
title: Installation de PowerShell sur macOS
description: Informations sur l’installation de PowerShell sur macOS
ms.date: 12/12/2018
ms.openlocfilehash: 7f0d6a1aa275deb39a7d670546ee7e833b8ef315
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404829"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="cae5b-103">Installation de PowerShell sur macOS</span><span class="sxs-lookup"><span data-stu-id="cae5b-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="cae5b-104">PowerShell Core prend en charge la version 10.12 et les versions ultérieures de macOS.</span><span class="sxs-lookup"><span data-stu-id="cae5b-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="cae5b-105">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="cae5b-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="cae5b-106">Une fois le package installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="cae5b-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="cae5b-107">PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="cae5b-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="cae5b-108">Le dossier `/usr/local/microsoft/powershell/6` est remplacé par `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="cae5b-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="cae5b-109">Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [Archive binaire](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="cae5b-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="cae5b-110">À propos de Brew</span><span class="sxs-lookup"><span data-stu-id="cae5b-110">About Brew</span></span>

<span data-ttu-id="cae5b-111">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="cae5b-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="cae5b-112">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [ces instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="cae5b-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="cae5b-113">Sinon, vous pouvez installer PowerShell par [Téléchargement direct](#installation-via-direct-download) ou à partir des [Archives binaires](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="cae5b-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="cae5b-114">Installation de la dernière version stable via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="cae5b-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="cae5b-115">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="cae5b-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cae5b-116">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="cae5b-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="cae5b-117">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="cae5b-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="cae5b-118">Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="cae5b-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="cae5b-119">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="cae5b-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="cae5b-120">Installation de la dernière version préliminaire via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="cae5b-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="cae5b-121">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="cae5b-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cae5b-122">Une fois Homebrew installé, vous pouvez installer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cae5b-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="cae5b-123">Tout d’abord, installez le package [Cask-Versions][cask-versions] qui vous permettre d’installer d’autres versions de packages cask :</span><span class="sxs-lookup"><span data-stu-id="cae5b-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="cae5b-124">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="cae5b-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="cae5b-125">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="cae5b-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="cae5b-126">Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="cae5b-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="cae5b-127">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="cae5b-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="cae5b-128">et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="cae5b-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="cae5b-129">Installation par téléchargement direct</span><span class="sxs-lookup"><span data-stu-id="cae5b-129">Installation via Direct Download</span></span>

<span data-ttu-id="cae5b-130">Téléchargez le package PKG `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="cae5b-130">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="cae5b-131">de la page [versions][] sur votre ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="cae5b-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="cae5b-132">Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="cae5b-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="cae5b-133">Installez [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="cae5b-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="cae5b-134">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cae5b-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="cae5b-135">Installation en tant qu’outil global .NET</span><span class="sxs-lookup"><span data-stu-id="cae5b-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="cae5b-136">Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="cae5b-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

## <a name="binary-archives"></a><span data-ttu-id="cae5b-137">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="cae5b-137">Binary Archives</span></span>

<span data-ttu-id="cae5b-138">Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="cae5b-138">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="cae5b-139">Installation des archives binaires sur macOS</span><span class="sxs-lookup"><span data-stu-id="cae5b-139">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="cae5b-140">Installez [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="cae5b-140">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="cae5b-141">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cae5b-141">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="cae5b-142">Installer les dépendances</span><span class="sxs-lookup"><span data-stu-id="cae5b-142">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="cae5b-143">Installer les outils en ligne de commande XCode</span><span class="sxs-lookup"><span data-stu-id="cae5b-143">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="cae5b-144">Installer OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cae5b-144">Install OpenSSL</span></span>

<span data-ttu-id="cae5b-145">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cae5b-145">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="cae5b-146">Vous pouvez l’installer avec MacPorts ou Brew.</span><span class="sxs-lookup"><span data-stu-id="cae5b-146">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="cae5b-147">Installer OpenSSL avec Brew</span><span class="sxs-lookup"><span data-stu-id="cae5b-147">Install OpenSSL via Brew</span></span>

<span data-ttu-id="cae5b-148">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="cae5b-148">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="cae5b-149">Exécutez `brew install openssl` pour installer OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="cae5b-149">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="cae5b-150">Installer OpenSSL avec MacPorts</span><span class="sxs-lookup"><span data-stu-id="cae5b-150">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="cae5b-151">Installez les [outils en ligne de commande XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="cae5b-151">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="cae5b-152">Installez MacPorts.</span><span class="sxs-lookup"><span data-stu-id="cae5b-152">Install MacPorts.</span></span>
   <span data-ttu-id="cae5b-153">Pour connaître les instructions à suivre, reportez-vous au [guide d’installation](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="cae5b-153">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="cae5b-154">Mettez à jour MacPorts en exécutant `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="cae5b-154">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="cae5b-155">Mettez à niveau les packages MacPorts en exécutant `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="cae5b-155">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="cae5b-156">Installez OpenSSL en exécutant `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="cae5b-156">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="cae5b-157">Liez les bibliothèques pour les mettre à la disposition de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="cae5b-157">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="cae5b-158">Désinstallation de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cae5b-158">Uninstalling PowerShell</span></span>

<span data-ttu-id="cae5b-159">Si vous avez installé PowerShell avec Homebrew, utilisez la commande suivante pour le désinstaller :</span><span class="sxs-lookup"><span data-stu-id="cae5b-159">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="cae5b-160">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="cae5b-160">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="cae5b-161">Pour supprimer les chemins d’accès PowerShell supplémentaires, reportez-vous à la section sur les [chemins d’accès](#paths) dans ce document et supprimez les chemins d’accès avec `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="cae5b-161">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="cae5b-162">Cela est inutile si vous avez installé PowerShell avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="cae5b-162">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="cae5b-163">Chemins</span><span class="sxs-lookup"><span data-stu-id="cae5b-163">Paths</span></span>

* <span data-ttu-id="cae5b-164">`$PSHOME` est `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="cae5b-164">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="cae5b-165">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="cae5b-165">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="cae5b-166">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="cae5b-166">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="cae5b-167">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="cae5b-167">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cae5b-168">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="cae5b-168">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cae5b-169">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="cae5b-169">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="cae5b-170">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="cae5b-170">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="cae5b-171">Les profils respectent la configuration par hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cae5b-171">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="cae5b-172">Donc, le profil spécifique à l’hôte par défaut existe dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="cae5b-172">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="cae5b-173">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.</span><span class="sxs-lookup"><span data-stu-id="cae5b-173">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="cae5b-174">Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="cae5b-174">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="cae5b-175">`$PSHOME` est donc `/usr/local/microsoft/powershell/6.2.0/` ; le lien symbolique se trouve à l’emplacement `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="cae5b-175">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cae5b-176">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="cae5b-176">Additional Resources</span></span>

* <span data-ttu-id="cae5b-177">[Site web Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="cae5b-177">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="cae5b-178">[Dépôt Homebrew sur GitHub][GitHub]</span><span class="sxs-lookup"><span data-stu-id="cae5b-178">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="cae5b-179">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="cae5b-179">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
