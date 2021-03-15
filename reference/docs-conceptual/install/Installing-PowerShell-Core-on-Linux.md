---
title: Installation de PowerShell sur Linux
description: Informations sur l’installation de PowerShell sur différentes distributions Linux
ms.date: 02/02/2021
ms.openlocfilehash: ab075a3570695f5a58b7e7fbf968243a4ff45929
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195264"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="d500e-103">Installation de PowerShell sur Linux</span><span class="sxs-lookup"><span data-stu-id="d500e-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="d500e-104">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="d500e-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="d500e-105">Une fois le package installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="d500e-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="d500e-106">Exécutez `pwsh-preview` si vous avez installé une [préversion](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="d500e-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-107">PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="d500e-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="d500e-108">Le dossier `/usr/local/microsoft/powershell/6` est remplacé par `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="d500e-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="d500e-109">Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [Archive binaire](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="d500e-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="d500e-110">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’installer PowerShell avec [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="d500e-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="d500e-111">Vous pouvez également essayer de déployer les fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires en fonction du système d’exploitation dans des étapes distinctes.</span><span class="sxs-lookup"><span data-stu-id="d500e-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<!-- TODO: Update for supported releases v7.0 & v7.1 -->

<span data-ttu-id="d500e-112">Versions de plateforme officiellement prises en charge pour PowerShell 7.1</span><span class="sxs-lookup"><span data-stu-id="d500e-112">Officially supported platform releases for PowerShell 7.1</span></span>

- <span data-ttu-id="d500e-113">Ubuntu 16.04/18.04/20.04 (y compris ARM64)</span><span class="sxs-lookup"><span data-stu-id="d500e-113">Ubuntu 16.04/18.04/20.04 (including ARM64)</span></span>
- <span data-ttu-id="d500e-114">Ubuntu 19.10 (via Snap Package)</span><span class="sxs-lookup"><span data-stu-id="d500e-114">Ubuntu 19.10 (via Snap package)</span></span>
- <span data-ttu-id="d500e-115">Debian 9/10</span><span class="sxs-lookup"><span data-stu-id="d500e-115">Debian 9/10</span></span>
- <span data-ttu-id="d500e-116">CentOS et RHEL 7/8</span><span class="sxs-lookup"><span data-stu-id="d500e-116">CentOS and RHEL 7/8</span></span>
- <span data-ttu-id="d500e-117">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="d500e-117">Fedora 30</span></span>
- <span data-ttu-id="d500e-118">Alpine 3.11+ (y compris ARM64)</span><span class="sxs-lookup"><span data-stu-id="d500e-118">Alpine 3.11+ (including ARM64)</span></span>

<span data-ttu-id="d500e-119">Versions de plateforme officiellement prises en charge pour PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="d500e-119">Officially supported platform releases for PowerShell 7.0</span></span>

- <span data-ttu-id="d500e-120">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d500e-120">Ubuntu 16.04</span></span>
- <span data-ttu-id="d500e-121">Ubuntu 18.04 et 20.04</span><span class="sxs-lookup"><span data-stu-id="d500e-121">Ubuntu 18.04 and 20.04</span></span>
- <span data-ttu-id="d500e-122">Debian 8</span><span class="sxs-lookup"><span data-stu-id="d500e-122">Debian 8</span></span>
- <span data-ttu-id="d500e-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d500e-123">Debian 9</span></span>
- <span data-ttu-id="d500e-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="d500e-124">Debian 10</span></span>
- <span data-ttu-id="d500e-125">Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="d500e-125">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="d500e-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d500e-126">CentOS 7</span></span>
- <span data-ttu-id="d500e-127">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d500e-127">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="d500e-128">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d500e-128">Fedora 28</span></span>
- <span data-ttu-id="d500e-129">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="d500e-129">Fedora 29</span></span>
- <span data-ttu-id="d500e-130">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="d500e-130">Fedora 30</span></span>
- <span data-ttu-id="d500e-131">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d500e-131">openSUSE 42.3</span></span>
- <span data-ttu-id="d500e-132">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d500e-132">openSUSE Leap 15</span></span>

<span data-ttu-id="d500e-133">Mises en production prises en charge par la communauté</span><span class="sxs-lookup"><span data-stu-id="d500e-133">Community supported releases</span></span>

- <span data-ttu-id="d500e-134">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="d500e-134">Ubuntu 18.10</span></span>
- <span data-ttu-id="d500e-135">Ubuntu 19.10 et 20.10</span><span class="sxs-lookup"><span data-stu-id="d500e-135">Ubuntu 19.10 and 20.10</span></span>
- <span data-ttu-id="d500e-136">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="d500e-136">Arch Linux</span></span>
- <span data-ttu-id="d500e-137">Kali</span><span class="sxs-lookup"><span data-stu-id="d500e-137">Kali</span></span>
- <span data-ttu-id="d500e-138">Raspbian (expérimental)</span><span class="sxs-lookup"><span data-stu-id="d500e-138">Raspbian (experimental)</span></span>

<span data-ttu-id="d500e-139">Autres méthodes d’installation</span><span class="sxs-lookup"><span data-stu-id="d500e-139">Alternate install methods</span></span>

- <span data-ttu-id="d500e-140">Snap Package</span><span class="sxs-lookup"><span data-stu-id="d500e-140">Snap Package</span></span>
- <span data-ttu-id="d500e-141">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="d500e-141">Binary Archives</span></span>
- <span data-ttu-id="d500e-142">Outil .NET Global</span><span class="sxs-lookup"><span data-stu-id="d500e-142">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="d500e-143">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d500e-143">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="d500e-144">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d500e-144">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="d500e-145">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-145">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d500e-146">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d500e-146">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of packages after we added packages.microsoft.com
sudo apt-get update
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="d500e-147">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="d500e-147">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d500e-148">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get install powershell`.</span><span class="sxs-lookup"><span data-stu-id="d500e-148">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="d500e-149">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d500e-149">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="d500e-150">Téléchargez le package Debian `powershell_7.1.2-1.ubuntu.16.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d500e-150">Download the Debian package `powershell_7.1.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d500e-151">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d500e-151">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d500e-152">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="d500e-152">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="d500e-153">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d500e-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="d500e-154">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d500e-154">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="d500e-155">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d500e-155">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="d500e-156">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d500e-156">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="d500e-157">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d500e-158">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d500e-158">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of products
sudo apt-get update
# Enable the "universe" repositories
sudo add-apt-repository universe
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="d500e-159">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="d500e-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d500e-160">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get install powershell`.</span><span class="sxs-lookup"><span data-stu-id="d500e-160">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="d500e-161">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d500e-161">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="d500e-162">Téléchargez le package Debian `powershell_7.1.2-1.ubuntu.18.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d500e-162">Download the Debian package `powershell_7.1.2-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d500e-163">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d500e-163">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d500e-164">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="d500e-164">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="d500e-165">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d500e-165">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="d500e-166">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d500e-166">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-2004"></a><span data-ttu-id="d500e-167">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="d500e-167">Ubuntu 20.04</span></span>

### <a name="installation-via-package-repository---ubuntu-2004"></a><span data-ttu-id="d500e-168">Installation via un dépôt de packages - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="d500e-168">Installation via Package Repository - Ubuntu 20.04</span></span>

<span data-ttu-id="d500e-169">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-169">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d500e-170">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d500e-170">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of products
sudo apt-get update
# Enable the "universe" repositories
sudo add-apt-repository universe
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="d500e-171">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="d500e-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d500e-172">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get install powershell`.</span><span class="sxs-lookup"><span data-stu-id="d500e-172">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-2004"></a><span data-ttu-id="d500e-173">Installation par téléchargement direct - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="d500e-173">Installation via Direct Download - Ubuntu 20.04</span></span>

<span data-ttu-id="d500e-174">Téléchargez le package Debian `powershell_7.1.2-1.ubuntu.20.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d500e-174">Download the Debian package `powershell_7.1.2-1.ubuntu.20.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d500e-175">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d500e-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.ubuntu.20.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d500e-176">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="d500e-176">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="d500e-177">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d500e-177">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-2004"></a><span data-ttu-id="d500e-178">Désinstallation - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="d500e-178">Uninstallation - Ubuntu 20.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="d500e-179">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="d500e-179">Ubuntu 18.10</span></span>

<span data-ttu-id="d500e-180">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="d500e-180">Installation is supported via `snapd`.</span></span> <span data-ttu-id="d500e-181">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="d500e-181">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-182">Ubuntu 18.10 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle)[prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="d500e-182">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1910-and-2010"></a><span data-ttu-id="d500e-183">Ubuntu 19.10 et 20.10</span><span class="sxs-lookup"><span data-stu-id="d500e-183">Ubuntu 19.10 and 20.10</span></span>

<span data-ttu-id="d500e-184">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="d500e-184">Installation is supported via `snapd`.</span></span> <span data-ttu-id="d500e-185">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="d500e-185">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-186">Ubuntu 19.10 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle) [prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="d500e-186">Ubuntu 19.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="d500e-187">Debian 8</span><span class="sxs-lookup"><span data-stu-id="d500e-187">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="d500e-188">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="d500e-188">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="d500e-189">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-189">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d500e-190">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d500e-190">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d500e-191">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="d500e-191">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d500e-192">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get install powershell`.</span><span class="sxs-lookup"><span data-stu-id="d500e-192">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="d500e-193">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d500e-193">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="d500e-194">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="d500e-194">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="d500e-195">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-195">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d500e-196">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d500e-196">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d500e-197">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="d500e-197">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d500e-198">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get install powershell`.</span><span class="sxs-lookup"><span data-stu-id="d500e-198">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="d500e-199">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="d500e-199">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="d500e-200">Téléchargez le package Debian `powershell_7.1.2-1.debian.9_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="d500e-200">Download the Debian package `powershell_7.1.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="d500e-201">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d500e-201">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="d500e-202">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="d500e-202">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="d500e-203">Debian 10</span><span class="sxs-lookup"><span data-stu-id="d500e-203">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-204">Debian 10 est pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="d500e-204">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="d500e-205">Installation via un dépôt de packages - Debian 10</span><span class="sxs-lookup"><span data-stu-id="d500e-205">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="d500e-206">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-206">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d500e-207">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d500e-207">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="d500e-208">Installation par téléchargement direct - Debian 10</span><span class="sxs-lookup"><span data-stu-id="d500e-208">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="d500e-209">Téléchargez le package tar.gz `powershell-7.1.2-linux-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="d500e-209">Download the tar.gz package `powershell-7.1.2-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="d500e-210">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d500e-210">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="d500e-211">Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="d500e-211">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-212">Alpine 3.9 et 3.10 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="d500e-212">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="d500e-213">Installation par téléchargement direct - Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="d500e-213">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="d500e-214">Téléchargez le package tar.gz `powershell-7.1.2-linux-alpine-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Alpine.</span><span class="sxs-lookup"><span data-stu-id="d500e-214">Download the tar.gz package `powershell-7.1.2-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="d500e-215">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d500e-215">Then, in the terminal, execute the following commands:</span></span>

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="centos-7"></a><span data-ttu-id="d500e-216">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d500e-216">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-217">Ce package fonctionne sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="d500e-217">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="d500e-218">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d500e-218">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="d500e-219">PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-219">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d500e-220">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="d500e-220">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d500e-221">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="d500e-221">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="d500e-222">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d500e-222">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="d500e-223">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-7.1.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="d500e-223">Using [CentOS 7][], download the RPM package `powershell-7.1.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="d500e-224">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d500e-224">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d500e-225">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="d500e-225">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="d500e-226">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d500e-226">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d500e-228">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d500e-228">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d500e-229">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d500e-229">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d500e-230">PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-230">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d500e-231">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="d500e-231">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d500e-232">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="d500e-232">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d500e-233">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d500e-233">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d500e-234">Téléchargez le package RPM `powershell-7.1.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="d500e-234">Download the RPM package `powershell-7.1.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="d500e-235">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d500e-235">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d500e-236">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="d500e-236">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d500e-237">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d500e-237">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="d500e-238">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="d500e-238">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="d500e-239">Installation – openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d500e-239">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="d500e-240">Installation – openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d500e-240">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="d500e-241">Désinstallation – openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d500e-241">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="d500e-242">Fedora</span><span class="sxs-lookup"><span data-stu-id="d500e-242">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-243">Fedora 28 n’est pris en charge que dans la version 6.1 et les versions plus récentes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d500e-243">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-244">Fedora 29 et 30 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="d500e-244">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="d500e-245">Installation via un dépôt de packages (par défaut) - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="d500e-245">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="d500e-246">PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-246">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf check-update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="d500e-247">Installation par téléchargement direct - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="d500e-247">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="d500e-248">Téléchargez le package RPM `powershell-7.1.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="d500e-248">Download the RPM package `powershell-7.1.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="d500e-249">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d500e-249">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.1.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d500e-250">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="d500e-250">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="d500e-251">Désinstallation - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="d500e-251">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="d500e-252">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="d500e-252">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-253">La prise en charge d’Arch n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.</span><span class="sxs-lookup"><span data-stu-id="d500e-253">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="d500e-254">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="d500e-254">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="d500e-255">Il peut être compilé avec la [dernière version étiquetée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="d500e-255">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="d500e-256">Il peut être compilé à partir de la [dernière validation sur le master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="d500e-256">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="d500e-257">Il peut être installé en utilisant la [dernière ressource binaire de la version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="d500e-257">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="d500e-258">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="d500e-258">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="d500e-259">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou [Utilisation de PowerShell](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="d500e-259">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="d500e-261">Snap Package</span><span class="sxs-lookup"><span data-stu-id="d500e-261">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="d500e-262">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="d500e-262">Getting snapd</span></span>

<span data-ttu-id="d500e-263">`snapd` est obligatoire pour exécuter des snaps.</span><span class="sxs-lookup"><span data-stu-id="d500e-263">`snapd` is required to run snaps.</span></span> <span data-ttu-id="d500e-264">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="d500e-264">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="d500e-265">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="d500e-265">Installation via Snap</span></span>

<span data-ttu-id="d500e-266">PowerShell pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-266">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="d500e-267">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d500e-267">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="d500e-268">Pour installer une préversion, utilisez la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="d500e-268">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="d500e-269">Après l’installation, Snap est automatiquement mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="d500e-269">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="d500e-270">Vous pouvez déclencher une mise à niveau avec `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="d500e-270">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="d500e-271">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="d500e-271">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="d500e-272">or</span><span class="sxs-lookup"><span data-stu-id="d500e-272">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="d500e-273">Kali</span><span class="sxs-lookup"><span data-stu-id="d500e-273">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-274">La prise en charge de Kali n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.</span><span class="sxs-lookup"><span data-stu-id="d500e-274">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="d500e-275">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="d500e-275">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="d500e-276">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="d500e-276">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="support-for-arm-processors"></a><span data-ttu-id="d500e-277">Prise en charge des processeurs ARM</span><span class="sxs-lookup"><span data-stu-id="d500e-277">Support for Arm processors</span></span>

<span data-ttu-id="d500e-278">PowerShell peut être installé sur certaines distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="d500e-278">PowerShell can be installed on some Linux distributions.</span></span> <span data-ttu-id="d500e-279">Il dépend de la prise en charge .NET d’ARM.</span><span class="sxs-lookup"><span data-stu-id="d500e-279">PowerShell is dependent on .NET support of Arm.</span></span> <span data-ttu-id="d500e-280">Il est pris en charge sur les distributions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d500e-280">PowerShell is supported on the following distributions:</span></span>

- <span data-ttu-id="d500e-281">Alpine Linux v3.11 et versions ultérieures : .NET prend en charge ARM64, mais il n’existe pour l’instant aucun package installable pour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d500e-281">Alpine Linux v3.11+ - .NET supports Arm64 but there is no installable package for PowerShell at this time</span></span>
- <span data-ttu-id="d500e-282">Raspbian : consultez ci-dessous les instructions d’installation.</span><span class="sxs-lookup"><span data-stu-id="d500e-282">Raspbian - see the installation instructions below</span></span>
- <span data-ttu-id="d500e-283">Debian v9 et versions ultérieures : prend en charge ARM32 et ARM64 suivant la méthode d’installation [Archive binaire](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="d500e-283">Debian v9+ - supports Arm32 and Arm64 using the [Binary Archive](#binary-archives) installation method</span></span>
- <span data-ttu-id="d500e-284">Ubuntu 20,10, 20,04, 18,04, 16,04 : prend en charge ARM32 et ARM64 suivant la méthode d’installation [Archive binaire](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="d500e-284">Ubuntu 20.10, 20.04, 18.04, 16.04 - supports Arm32 and Arm64 using the [Binary Archive](#binary-archives) installation method</span></span>

## <a name="raspbian"></a><span data-ttu-id="d500e-285">Raspbian</span><span class="sxs-lookup"><span data-stu-id="d500e-285">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="d500e-286">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="d500e-286">Raspbian support is experimental.</span></span>

<span data-ttu-id="d500e-287">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="d500e-287">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="d500e-288">CoreCLR et PowerShell fonctionnent uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d500e-288">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="d500e-289">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="d500e-289">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="d500e-290">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="d500e-290">Installation - Raspbian</span></span>

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.1.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="d500e-291">Si vous le souhaitez, vous pouvez créer un lien symbolique pour démarrer PowerShell sans spécifier de chemin d’accès au binaire `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="d500e-291">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="d500e-292">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="d500e-292">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="d500e-293">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="d500e-293">Installing Preview Releases</span></span>

<span data-ttu-id="d500e-294">Lorsque vous installez une préversion de PowerShell pour Linux au moyen d’un référentiel de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="d500e-294">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="d500e-295">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="d500e-295">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="d500e-296">Le tableau suivant contient des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="d500e-296">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="d500e-297">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="d500e-297">Distribution(s)</span></span> |            <span data-ttu-id="d500e-298">Commande stable</span><span class="sxs-lookup"><span data-stu-id="d500e-298">Stable Command</span></span>            |               <span data-ttu-id="d500e-299">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="d500e-299">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="d500e-300">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="d500e-300">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="d500e-301">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="d500e-301">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="d500e-302">Fedora</span><span class="sxs-lookup"><span data-stu-id="d500e-302">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="d500e-303">Installation en tant qu’outil global .NET</span><span class="sxs-lookup"><span data-stu-id="d500e-303">Install as a .NET Global tool</span></span>

<span data-ttu-id="d500e-304">Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="d500e-304">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="d500e-305">Le programme d’installation de l’outil dotnet ajoute `~/.dotnet/tools` à votre variable d’environnement `PATH`.</span><span class="sxs-lookup"><span data-stu-id="d500e-305">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="d500e-306">Toutefois, le `PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="d500e-306">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="d500e-307">Vous devez pouvoir démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="d500e-307">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="d500e-308">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="d500e-308">Binary Archives</span></span>

<span data-ttu-id="d500e-309">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="d500e-309">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="d500e-310">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="d500e-310">Dependencies</span></span>

<span data-ttu-id="d500e-311">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="d500e-311">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="d500e-312">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte de la même manière.</span><span class="sxs-lookup"><span data-stu-id="d500e-312">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="d500e-313">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="d500e-313">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="d500e-314">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="d500e-314">OS</span></span>                 | <span data-ttu-id="d500e-315">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="d500e-315">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="d500e-316">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d500e-316">Ubuntu 16.04</span></span>       | <span data-ttu-id="d500e-317">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d500e-317">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d500e-318">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="d500e-318">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="d500e-319">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="d500e-319">Ubuntu 17.10</span></span>       | <span data-ttu-id="d500e-320">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d500e-320">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d500e-321">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="d500e-321">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="d500e-322">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d500e-322">Ubuntu 18.04</span></span>       | <span data-ttu-id="d500e-323">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d500e-323">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d500e-324">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="d500e-324">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="d500e-325">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="d500e-325">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="d500e-326">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d500e-326">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d500e-327">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="d500e-327">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="d500e-328">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="d500e-328">Debian 9 (Stretch)</span></span> | <span data-ttu-id="d500e-329">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d500e-329">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d500e-330">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="d500e-330">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="d500e-331">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d500e-331">CentOS 7</span></span> <br> <span data-ttu-id="d500e-332">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="d500e-332">Oracle Linux 7</span></span> <br> <span data-ttu-id="d500e-333">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="d500e-333">RHEL 7</span></span> | <span data-ttu-id="d500e-334">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="d500e-334">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="d500e-335">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d500e-335">openSUSE 42.3</span></span> | <span data-ttu-id="d500e-336">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="d500e-336">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="d500e-337">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d500e-337">openSUSE Leap 15</span></span> | <span data-ttu-id="d500e-338">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="d500e-338">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="d500e-339">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="d500e-339">Fedora 27</span></span> <br> <span data-ttu-id="d500e-340">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d500e-340">Fedora 28</span></span> | <span data-ttu-id="d500e-341">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="d500e-341">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="d500e-342">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="d500e-342">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="d500e-343">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe d’abord les dépendances, puis extrait l’archive Linux `tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="d500e-343">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="d500e-344">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="d500e-344">Installation - Binary Archives</span></span>

<span data-ttu-id="d500e-345">L’exemple suivant illustre les étapes d’installation de l’archive binaire x64.</span><span class="sxs-lookup"><span data-stu-id="d500e-345">The following example shows the steps for installing the x64 binary archive.</span></span> <span data-ttu-id="d500e-346">Vous devez choisir l’archive binaire correspondant au type de processeur de votre plateforme.</span><span class="sxs-lookup"><span data-stu-id="d500e-346">You must choose the correct binary archive that matches the processor type for your platform.</span></span>

- <span data-ttu-id="d500e-347">powershell-7.1.2-linux-arm32.tar.gz</span><span class="sxs-lookup"><span data-stu-id="d500e-347">powershell-7.1.2-linux-arm32.tar.gz</span></span>
- <span data-ttu-id="d500e-348">powershell-7.1.2-linux-arm64.tar.gz</span><span class="sxs-lookup"><span data-stu-id="d500e-348">powershell-7.1.2-linux-arm64.tar.gz</span></span>
- <span data-ttu-id="d500e-349">powershell-7.1.2-linux-x64.tar.gz</span><span class="sxs-lookup"><span data-stu-id="d500e-349">powershell-7.1.2-linux-x64.tar.gz</span></span>

#### <a name="linux"></a><span data-ttu-id="d500e-350">Linux</span><span class="sxs-lookup"><span data-stu-id="d500e-350">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="d500e-351">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="d500e-351">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="d500e-352">Chemins</span><span class="sxs-lookup"><span data-stu-id="d500e-352">Paths</span></span>

- <span data-ttu-id="d500e-353">`$PSHOME` est `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="d500e-353">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="d500e-354">Les profils utilisateur sont lus dans `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d500e-354">User profiles are read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="d500e-355">Les profils par défaut sont lus dans `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d500e-355">Default profiles are read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="d500e-356">Les modules utilisateur sont lus dans `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d500e-356">User modules are read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="d500e-357">Les modules partagés sont lus dans `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d500e-357">Shared modules are read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="d500e-358">Les modules par défaut sont lus dans `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="d500e-358">Default modules are read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="d500e-359">L’historique PSReadLine est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="d500e-359">PSReadLine history is recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="d500e-360">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="d500e-360">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="d500e-361">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="d500e-361">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="d500e-362">Prise en charge de l’installation</span><span class="sxs-lookup"><span data-stu-id="d500e-362">Installation support</span></span>

<span data-ttu-id="d500e-363">Microsoft prend en charge les méthodes d’installation mentionnées dans ce document.</span><span class="sxs-lookup"><span data-stu-id="d500e-363">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="d500e-364">D’autres méthodes d’installation peuvent être disponibles à partir d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="d500e-364">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="d500e-365">Même s’il est possible que ces outils et méthodes fonctionnent, Microsoft ne peut pas prendre en charge ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="d500e-365">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[versions]: https://aka.ms/PowerShell-Release?tag=stable
[releases]: https://aka.ms/PowerShell-Release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
