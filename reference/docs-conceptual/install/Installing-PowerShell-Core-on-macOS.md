---
title: Installation de PowerShell sur macOS
description: Informations sur l’installation de PowerShell sur macOS
ms.date: 12/12/2018
ms.openlocfilehash: 2233bc01ee8c53087f79d83ca936c5a3800cfdba
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082771"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="7854f-103">Installation de PowerShell sur macOS</span><span class="sxs-lookup"><span data-stu-id="7854f-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="7854f-104">PowerShell Core prend en charge la version 10.12 et les versions ultérieures de macOS.</span><span class="sxs-lookup"><span data-stu-id="7854f-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="7854f-105">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="7854f-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="7854f-106">Une fois le package installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="7854f-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="7854f-107">PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="7854f-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="7854f-108">Le dossier `/usr/local/microsoft/powershell/6` est remplacé par `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="7854f-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="7854f-109">Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [Archive binaire](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="7854f-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="7854f-110">À propos de Brew</span><span class="sxs-lookup"><span data-stu-id="7854f-110">About Brew</span></span>

<span data-ttu-id="7854f-111">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="7854f-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="7854f-112">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [ces instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="7854f-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="7854f-113">Sinon, vous pouvez installer PowerShell par [Téléchargement direct](#installation-via-direct-download) ou à partir des [Archives binaires](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="7854f-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="7854f-114">Installation de la dernière version stable via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="7854f-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="7854f-115">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="7854f-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="7854f-116">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="7854f-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="7854f-117">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="7854f-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="7854f-118">Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="7854f-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="7854f-119">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="7854f-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="7854f-120">Installation de la dernière version préliminaire via Homebrew sur macOS 10.12 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="7854f-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="7854f-121">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="7854f-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="7854f-122">Une fois Homebrew installé, vous pouvez installer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7854f-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="7854f-123">Tout d’abord, installez le package [Cask-Versions][cask-versions] qui vous permettre d’installer d’autres versions de packages cask :</span><span class="sxs-lookup"><span data-stu-id="7854f-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="7854f-124">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="7854f-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="7854f-125">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="7854f-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="7854f-126">Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="7854f-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="7854f-127">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="7854f-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="7854f-128">et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="7854f-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="7854f-129">Installation par téléchargement direct</span><span class="sxs-lookup"><span data-stu-id="7854f-129">Installation via Direct Download</span></span>

<span data-ttu-id="7854f-130">Téléchargez le package PKG `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="7854f-130">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="7854f-131">de la page [versions][] sur votre ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="7854f-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="7854f-132">Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="7854f-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="7854f-133">Installez [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="7854f-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="7854f-134">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7854f-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="7854f-135">Installation en tant qu’outil global .NET</span><span class="sxs-lookup"><span data-stu-id="7854f-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="7854f-136">Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="7854f-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="7854f-137">Le programme d’installation de l’outil dotnet ajoute `~/.dotnet/tools` à votre variable d’environnement `PATH`.</span><span class="sxs-lookup"><span data-stu-id="7854f-137">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="7854f-138">Toutefois, le `PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="7854f-138">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="7854f-139">Vous devez pouvoir démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="7854f-139">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="7854f-140">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="7854f-140">Binary Archives</span></span>

<span data-ttu-id="7854f-141">Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="7854f-141">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="7854f-142">Installation des archives binaires sur macOS</span><span class="sxs-lookup"><span data-stu-id="7854f-142">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="7854f-143">Installez [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="7854f-143">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="7854f-144">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7854f-144">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="7854f-145">Installer les dépendances</span><span class="sxs-lookup"><span data-stu-id="7854f-145">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="7854f-146">Installer les outils en ligne de commande XCode</span><span class="sxs-lookup"><span data-stu-id="7854f-146">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="7854f-147">Installer OpenSSL</span><span class="sxs-lookup"><span data-stu-id="7854f-147">Install OpenSSL</span></span>

<span data-ttu-id="7854f-148">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7854f-148">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="7854f-149">Vous pouvez l’installer avec MacPorts ou Brew.</span><span class="sxs-lookup"><span data-stu-id="7854f-149">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="7854f-150">Installer OpenSSL avec Brew</span><span class="sxs-lookup"><span data-stu-id="7854f-150">Install OpenSSL via Brew</span></span>

<span data-ttu-id="7854f-151">Pour plus d'informations sur Brew, voir [À propos de Brew](#about-brew).</span><span class="sxs-lookup"><span data-stu-id="7854f-151">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="7854f-152">Exécutez `brew install openssl` pour installer OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="7854f-152">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="7854f-153">Installer OpenSSL avec MacPorts</span><span class="sxs-lookup"><span data-stu-id="7854f-153">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="7854f-154">Installez les [outils en ligne de commande XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="7854f-154">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="7854f-155">Installez MacPorts.</span><span class="sxs-lookup"><span data-stu-id="7854f-155">Install MacPorts.</span></span>
   <span data-ttu-id="7854f-156">Pour connaître les instructions à suivre, reportez-vous au [guide d’installation](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="7854f-156">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="7854f-157">Mettez à jour MacPorts en exécutant `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="7854f-157">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="7854f-158">Mettez à niveau les packages MacPorts en exécutant `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="7854f-158">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="7854f-159">Installez OpenSSL en exécutant `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="7854f-159">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="7854f-160">Liez les bibliothèques pour les mettre à la disposition de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="7854f-160">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="7854f-161">Désinstallation de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7854f-161">Uninstalling PowerShell</span></span>

<span data-ttu-id="7854f-162">Si vous avez installé PowerShell avec Homebrew, utilisez la commande suivante pour le désinstaller :</span><span class="sxs-lookup"><span data-stu-id="7854f-162">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="7854f-163">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="7854f-163">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="7854f-164">Pour supprimer les chemins d’accès PowerShell supplémentaires, reportez-vous à la section sur les [chemins d’accès](#paths) dans ce document et supprimez les chemins d’accès avec `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="7854f-164">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="7854f-165">Cela est inutile si vous avez installé PowerShell avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="7854f-165">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="7854f-166">Chemins</span><span class="sxs-lookup"><span data-stu-id="7854f-166">Paths</span></span>

* <span data-ttu-id="7854f-167">`$PSHOME` est `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="7854f-167">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="7854f-168">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7854f-168">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="7854f-169">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7854f-169">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="7854f-170">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7854f-170">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7854f-171">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7854f-171">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7854f-172">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="7854f-172">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="7854f-173">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="7854f-173">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="7854f-174">Les profils respectent la configuration par hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7854f-174">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="7854f-175">Donc, le profil spécifique à l’hôte par défaut existe dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="7854f-175">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="7854f-176">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.</span><span class="sxs-lookup"><span data-stu-id="7854f-176">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="7854f-177">Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="7854f-177">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="7854f-178">`$PSHOME` est donc `/usr/local/microsoft/powershell/6.2.0/` ; le lien symbolique se trouve à l’emplacement `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="7854f-178">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7854f-179">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="7854f-179">Additional Resources</span></span>

* <span data-ttu-id="7854f-180">[Site web Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="7854f-180">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="7854f-181">[Dépôt Homebrew sur GitHub][GitHub]</span><span class="sxs-lookup"><span data-stu-id="7854f-181">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="7854f-182">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="7854f-182">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
