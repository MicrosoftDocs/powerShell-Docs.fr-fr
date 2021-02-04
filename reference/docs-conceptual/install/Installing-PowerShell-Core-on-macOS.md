---
title: Installation de PowerShell sur macOS
description: Informations sur l’installation de PowerShell sur macOS
ms.date: 02/02/2021
ms.openlocfilehash: 8132d88f4104696c5580a44b26247a24643f1b5b
ms.sourcegitcommit: 40b6d8e9b6d791ac69e2ff85224e900b21552bc1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99536540"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="50369-103">Installation de PowerShell sur macOS</span><span class="sxs-lookup"><span data-stu-id="50369-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="50369-104">PowerShell 7.0 ou version ultérieure nécessite macOS 10.13 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="50369-104">PowerShell 7.0 or higher require macOS 10.13 and higher.</span></span> <span data-ttu-id="50369-105">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="50369-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="50369-106">Une fois le package installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="50369-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="50369-107">PowerShell 7.1 est une mise à niveau sur place qui supprime PowerShell Core 6.x et 7.0.</span><span class="sxs-lookup"><span data-stu-id="50369-107">PowerShell 7.1 is an in-place upgrade that removes PowerShell Core 6.x and 7.0.</span></span>
>
> <span data-ttu-id="50369-108">Le dossier `/usr/local/microsoft/powershell/6` est remplacé par `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="50369-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="50369-109">Si vous devez exécuter une ancienne version de PowerShell Core côte à côte avec PowerShell 7.1, installez la version de votre choix à l’aide de la méthode [Archive binaire](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="50369-109">If you need to run and older version of PowerShell core side-by-side with PowerShell 7.1, install the version you want using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="50369-110">Il existe plusieurs façons d’installer PowerShell sur macOS.</span><span class="sxs-lookup"><span data-stu-id="50369-110">There are several ways to install PowerShell on macOS.</span></span> <span data-ttu-id="50369-111">Choisissez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="50369-111">Choose one of the following methods:</span></span>

- <span data-ttu-id="50369-112">Installation avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="50369-112">Install using Homebrew.</span></span> <span data-ttu-id="50369-113">Homebrew est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="50369-113">Homebrew is the preferred package manager for macOS.</span></span>
- <span data-ttu-id="50369-114">Installation de PowerShell par [téléchargement direct](#installation-via-direct-download).</span><span class="sxs-lookup"><span data-stu-id="50369-114">Install PowerShell via [Direct Download](#installation-via-direct-download)</span></span>
- <span data-ttu-id="50369-115">Installation à partir d’[archives binaires](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="50369-115">Install from [binary archives](#binary-archives).</span></span>

<span data-ttu-id="50369-116">Après avoir installé PowerShell, vous devez installer [OpenSSL](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="50369-116">After installing PowerShell, you should install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="50369-117">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50369-117">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="50369-118">Installation de la dernière version stable par le biais de Homebrew sur macOS 10.13 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="50369-118">Installation of latest stable release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="50369-119">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [ces instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="50369-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="50369-120">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="50369-120">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell
```

<span data-ttu-id="50369-121">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="50369-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="50369-122">Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="50369-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> <span data-ttu-id="50369-123">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter et redémarrer l’interpréteur de commandes PowerShell pour terminer la mise à niveau et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="50369-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="50369-124">Installation de la dernière préversion par le biais de Homebrew sur macOS 10.13 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="50369-124">Installation of latest preview release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="50369-125">Une fois Homebrew installé, vous pouvez installer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50369-125">After you've installed Homebrew, you can install PowerShell.</span></span> <span data-ttu-id="50369-126">Tout d’abord, installez le package [Cask-Versions][cask-versions], ce qui va vous permettre d’installer d’autres versions de packages cask :</span><span class="sxs-lookup"><span data-stu-id="50369-126">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="50369-127">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="50369-127">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell-preview
```

<span data-ttu-id="50369-128">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="50369-128">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="50369-129">Quand de nouvelles versions de PowerShell sont publiées, mettez à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="50369-129">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> <span data-ttu-id="50369-130">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="50369-130">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="50369-131">et actualiser les valeurs indiquées dans `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="50369-131">and refresh the values shown in `$PSVersionTable`.</span></span>

<span data-ttu-id="50369-132">L’installation de PowerShell avec la méthode tap Homebrew est également prise en charge pour les versions stables et LTS.</span><span class="sxs-lookup"><span data-stu-id="50369-132">Installing PowerShell using the Homebrew tap method is also supported for stable and LTS versions.</span></span>

```sh
brew install powershell/tap/powershell
```

<span data-ttu-id="50369-133">Vous pouvez maintenant vérifier votre installation.</span><span class="sxs-lookup"><span data-stu-id="50369-133">You can now verify your install</span></span>

```sh
pwsh
```

<span data-ttu-id="50369-134">Quand de nouvelles versions de PowerShell sont publiées, exécutez simplement la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="50369-134">When new versions of PowerShell are released, simply run the following command.</span></span>

```sh
brew upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="50369-135">Que vous utilisiez la méthode cask ou tap, lors de la mise à jour vers une version plus récente de PowerShell, utilisez la même méthode que celle utilisée pour l’installation initiale de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50369-135">Whether you use the cask or the tap method, when updating to a newer version of PowerShell, use the same method you used to initially install PowerShell.</span></span> <span data-ttu-id="50369-136">Si vous utilisez une autre méthode, l’ouverture d’une nouvelle session pwsh continuera à utiliser l’ancienne version de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50369-136">If you use a different method, opening a new pwsh session will continue to use the older version of PowerShell.</span></span>
>
> <span data-ttu-id="50369-137">Si vous décidez d’utiliser d’autres méthodes, vous pouvez corriger le problème à l’aide de la [méthode link Homebrew](https://docs.brew.sh/Manpage#link-ln-options-formula).</span><span class="sxs-lookup"><span data-stu-id="50369-137">If you do decide to use different methods, there are ways to correct the issue using the [Homebrew link method](https://docs.brew.sh/Manpage#link-ln-options-formula).</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="50369-138">Installation par téléchargement direct</span><span class="sxs-lookup"><span data-stu-id="50369-138">Installation via Direct Download</span></span>

<span data-ttu-id="50369-139">Téléchargez le package PKG `powershell-7.1.1-osx-x64.pkg` à partir de la page de [versions][] sur votre ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="50369-139">Download the PKG package `powershell-7.1.1-osx-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="50369-140">Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="50369-140">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-7.1.1-osx-x64.pkg -target /
```

<span data-ttu-id="50369-141">Installez [OpenSSL](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="50369-141">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="50369-142">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50369-142">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="50369-143">Installation en tant qu’outil global .NET</span><span class="sxs-lookup"><span data-stu-id="50369-143">Install as a .NET Global tool</span></span>

<span data-ttu-id="50369-144">Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="50369-144">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="50369-145">Le programme d’installation de l’outil dotnet ajoute `~/.dotnet/tools` à votre variable d’environnement `PATH`.</span><span class="sxs-lookup"><span data-stu-id="50369-145">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="50369-146">Toutefois, le `PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="50369-146">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="50369-147">Vous devez pouvoir démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="50369-147">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

<span data-ttu-id="50369-148">Installez [OpenSSL](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="50369-148">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="50369-149">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50369-149">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="50369-150">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="50369-150">Binary Archives</span></span>

<span data-ttu-id="50369-151">Les archives `tar.gz` binaires PowerShell sont fournies pour la plateforme macOS pour permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="50369-151">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span> <span data-ttu-id="50369-152">Quand vous installez avec cette méthode, vous devez également installer manuellement toutes les dépendances.</span><span class="sxs-lookup"><span data-stu-id="50369-152">When you install using this method you must also manually install any dependencies.</span></span>

<span data-ttu-id="50369-153">Installez [OpenSSL](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="50369-153">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="50369-154">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50369-154">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="50369-155">Installation des archives binaires sur macOS</span><span class="sxs-lookup"><span data-stu-id="50369-155">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.1/powershell-7.1.1-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.1

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.1

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.1/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.1/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a><span data-ttu-id="50369-156">Installer les dépendances</span><span class="sxs-lookup"><span data-stu-id="50369-156">Installing dependencies</span></span>

<span data-ttu-id="50369-157">OpenSSL est nécessaire pour les opérations de CIM et de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50369-157">OpenSSL is required for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="50369-158">Vous pouvez installer OpenSSL par le biais de MacPorts si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="50369-158">You can install OpenSSL via MacPorts if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="50369-159">Utilisés ensemble sur le même système, MacPorts et Homebrew peuvent rencontrer des problèmes.</span><span class="sxs-lookup"><span data-stu-id="50369-159">MacPorts and Homebrew can have problems when used to together on the same system.</span></span> <span data-ttu-id="50369-160">En revanche, Homebrew n’a pas de package pour OpenSSL 1.0.</span><span class="sxs-lookup"><span data-stu-id="50369-160">However, Homebrew does not have a package for OpenSSL 1.0.</span></span> <span data-ttu-id="50369-161">Pour plus d’informations, consultez les [questions fréquentes (FAQ) sur MacPorts](https://trac.macports.org/wiki/FAQ).</span><span class="sxs-lookup"><span data-stu-id="50369-161">For more information, see the [MacPorts FAQ](https://trac.macports.org/wiki/FAQ).</span></span>

1. <span data-ttu-id="50369-162">Installez les outils en ligne de commande Xcode.</span><span class="sxs-lookup"><span data-stu-id="50369-162">Install the Xcode command-line tools.</span></span> <span data-ttu-id="50369-163">Les outils Xcode sont une exigence de MacPorts.</span><span class="sxs-lookup"><span data-stu-id="50369-163">The Xcode tools are required by MacPorts.</span></span>

   ```sh
   xcode-select --install
   ```

1. <span data-ttu-id="50369-164">Installez MacPorts.</span><span class="sxs-lookup"><span data-stu-id="50369-164">Install MacPorts.</span></span> <span data-ttu-id="50369-165">Pour connaître les instructions à suivre, reportez-vous au [guide d’installation](https://www.macports.org/install.php).</span><span class="sxs-lookup"><span data-stu-id="50369-165">If you need instructions, refer to the [installation guide](https://www.macports.org/install.php).</span></span>
1. <span data-ttu-id="50369-166">Mettez à jour MacPorts en exécutant `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="50369-166">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="50369-167">Mettez à niveau les packages MacPorts en exécutant `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="50369-167">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="50369-168">Installez OpenSSL en exécutant `sudo port install openssl10`.</span><span class="sxs-lookup"><span data-stu-id="50369-168">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="50369-169">Liez les bibliothèques pour les mettre à la disposition de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="50369-169">Link the libraries to make them available to PowerShell:</span></span>

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a><span data-ttu-id="50369-170">Désinstallation de PowerShell</span><span class="sxs-lookup"><span data-stu-id="50369-170">Uninstalling PowerShell</span></span>

<span data-ttu-id="50369-171">Si vous avez installé PowerShell avec Homebrew, utilisez la commande suivante pour le désinstaller :</span><span class="sxs-lookup"><span data-stu-id="50369-171">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="50369-172">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="50369-172">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="50369-173">Pour supprimer les chemins d’accès PowerShell supplémentaires, reportez-vous à la section sur les [chemins d’accès](#paths) dans ce document et supprimez les chemins d’accès avec `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="50369-173">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="50369-174">Cela est inutile si vous avez installé PowerShell avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="50369-174">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="50369-175">Chemins</span><span class="sxs-lookup"><span data-stu-id="50369-175">Paths</span></span>

- <span data-ttu-id="50369-176">`$PSHOME` est `/usr/local/microsoft/powershell/7.1.1/`</span><span class="sxs-lookup"><span data-stu-id="50369-176">`$PSHOME` is `/usr/local/microsoft/powershell/7.1.1/`</span></span>
- <span data-ttu-id="50369-177">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="50369-177">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="50369-178">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="50369-178">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="50369-179">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="50369-179">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="50369-180">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="50369-180">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="50369-181">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="50369-181">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="50369-182">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="50369-182">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="50369-183">Les profils respectent la configuration par hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50369-183">The profiles respect PowerShell's per-host configuration.</span></span> <span data-ttu-id="50369-184">Donc, le profil spécifique à l’hôte par défaut existe dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="50369-184">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="50369-185">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.</span><span class="sxs-lookup"><span data-stu-id="50369-185">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="50369-186">Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="50369-186">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span> <span data-ttu-id="50369-187">`$PSHOME` est donc `/usr/local/microsoft/powershell/7.1.1/` ; le lien symbolique se trouve à l’emplacement `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="50369-187">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.1.1/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="installation-support"></a><span data-ttu-id="50369-188">Prise en charge de l’installation</span><span class="sxs-lookup"><span data-stu-id="50369-188">Installation support</span></span>

<span data-ttu-id="50369-189">Microsoft prend en charge les méthodes d’installation mentionnées dans ce document.</span><span class="sxs-lookup"><span data-stu-id="50369-189">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="50369-190">D’autres méthodes d’installation peuvent être disponibles à partir d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="50369-190">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="50369-191">Même s’il est possible que ces outils et méthodes fonctionnent, Microsoft ne peut pas prendre en charge ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="50369-191">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="50369-192">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="50369-192">Additional Resources</span></span>

- <span data-ttu-id="50369-193">[Site web d’Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="50369-193">[Homebrew Web][brew]</span></span>
- <span data-ttu-id="50369-194">[Dépôt GitHub d’Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="50369-194">[Homebrew Github Repository][GitHub]</span></span>
- <span data-ttu-id="50369-195">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="50369-195">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versions]: https://aka.ms/powershell-release?tag=stable
[releases]: https://aka.ms/powershell-release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
