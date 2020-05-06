---
title: Installation de PowerShell sur Linux
description: Informations sur l’installation de PowerShell sur différentes distributions Linux
ms.date: 03/09/2020
ms.openlocfilehash: 6ad637bd30e5e40ccc9532bae6f1171ecf79734a
ms.sourcegitcommit: e0a737961280026832cff9c658ed1468dc904e80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82605847"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="18dcc-103">Installation de PowerShell sur Linux</span><span class="sxs-lookup"><span data-stu-id="18dcc-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="18dcc-104">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="18dcc-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="18dcc-105">Une fois le package installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="18dcc-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="18dcc-106">Exécutez `pwsh-preview` si vous avez installé une [préversion](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="18dcc-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-107">PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="18dcc-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="18dcc-108">Le dossier `/usr/local/microsoft/powershell/6` est remplacé par `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="18dcc-109">Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [Archive binaire](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="18dcc-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="18dcc-110">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’installer PowerShell avec [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="18dcc-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="18dcc-111">Vous pouvez également essayer de déployer les fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires en fonction du système d’exploitation dans des étapes distinctes.</span><span class="sxs-lookup"><span data-stu-id="18dcc-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="18dcc-112">Mises en production officiellement prises en charge</span><span class="sxs-lookup"><span data-stu-id="18dcc-112">Officially supported releases</span></span>

- <span data-ttu-id="18dcc-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="18dcc-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="18dcc-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="18dcc-115">Debian 8</span></span>
- <span data-ttu-id="18dcc-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="18dcc-116">Debian 9</span></span>
- <span data-ttu-id="18dcc-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="18dcc-117">Debian 10</span></span>
- <span data-ttu-id="18dcc-118">Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="18dcc-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="18dcc-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-119">CentOS 7</span></span>
- <span data-ttu-id="18dcc-120">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="18dcc-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="18dcc-121">Fedora 28</span></span>
- <span data-ttu-id="18dcc-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="18dcc-122">Fedora 29</span></span>
- <span data-ttu-id="18dcc-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="18dcc-123">Fedora 30</span></span>
- <span data-ttu-id="18dcc-124">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="18dcc-124">openSUSE 42.3</span></span>
- <span data-ttu-id="18dcc-125">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="18dcc-125">openSUSE Leap 15</span></span>

<span data-ttu-id="18dcc-126">Mises en production prises en charge par la communauté</span><span class="sxs-lookup"><span data-stu-id="18dcc-126">Community supported releases</span></span>

- <span data-ttu-id="18dcc-127">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="18dcc-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="18dcc-128">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="18dcc-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="18dcc-129">Arch Linux</span></span>
- <span data-ttu-id="18dcc-130">Kali</span><span class="sxs-lookup"><span data-stu-id="18dcc-130">Kali</span></span>
- <span data-ttu-id="18dcc-131">Raspbian (expérimental)</span><span class="sxs-lookup"><span data-stu-id="18dcc-131">Raspbian (experimental)</span></span>

<span data-ttu-id="18dcc-132">Autres méthodes d’installation</span><span class="sxs-lookup"><span data-stu-id="18dcc-132">Alternate install methods</span></span>

- <span data-ttu-id="18dcc-133">Snap Package</span><span class="sxs-lookup"><span data-stu-id="18dcc-133">Snap Package</span></span>
- <span data-ttu-id="18dcc-134">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="18dcc-134">Binary Archives</span></span>
- <span data-ttu-id="18dcc-135">Outil .NET Global</span><span class="sxs-lookup"><span data-stu-id="18dcc-135">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="18dcc-136">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-136">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="18dcc-137">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-137">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="18dcc-138">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-138">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="18dcc-139">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="18dcc-139">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="18dcc-140">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="18dcc-140">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="18dcc-141">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-141">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="18dcc-142">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-142">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="18dcc-143">Téléchargez le package Debian `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="18dcc-143">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="18dcc-144">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="18dcc-144">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="18dcc-145">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="18dcc-145">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="18dcc-146">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="18dcc-146">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="18dcc-147">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-147">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="18dcc-148">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-148">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="18dcc-149">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-149">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="18dcc-150">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-150">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="18dcc-151">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="18dcc-151">The preferred method is as follows:</span></span>

```sh
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

<span data-ttu-id="18dcc-152">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="18dcc-152">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="18dcc-153">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-153">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="18dcc-154">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-154">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="18dcc-155">Téléchargez le package Debian `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="18dcc-155">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="18dcc-156">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="18dcc-156">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="18dcc-157">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="18dcc-157">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="18dcc-158">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="18dcc-158">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="18dcc-159">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-159">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="18dcc-160">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="18dcc-160">Ubuntu 18.10</span></span>

<span data-ttu-id="18dcc-161">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-161">Installation is supported via `snapd`.</span></span> <span data-ttu-id="18dcc-162">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="18dcc-162">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-163">Ubuntu 18.10 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle)[prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="18dcc-163">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="18dcc-164">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-164">Ubuntu 19.04</span></span>

<span data-ttu-id="18dcc-165">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-165">Installation is supported via `snapd`.</span></span> <span data-ttu-id="18dcc-166">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="18dcc-166">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-167">Ubuntu 19.04 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle)[prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="18dcc-167">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="18dcc-168">Debian 8</span><span class="sxs-lookup"><span data-stu-id="18dcc-168">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="18dcc-169">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="18dcc-169">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="18dcc-170">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-170">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="18dcc-171">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="18dcc-171">The preferred method is as follows:</span></span>

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

<span data-ttu-id="18dcc-172">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="18dcc-172">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="18dcc-173">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-173">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="18dcc-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="18dcc-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="18dcc-175">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="18dcc-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="18dcc-176">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-176">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="18dcc-177">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="18dcc-177">The preferred method is as follows:</span></span>

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

<span data-ttu-id="18dcc-178">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="18dcc-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="18dcc-179">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-179">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="18dcc-180">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="18dcc-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="18dcc-181">Téléchargez le package Debian `powershell-lts_7.0.0-1.debian.9_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="18dcc-181">Download the Debian package `powershell-lts_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="18dcc-182">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="18dcc-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="18dcc-183">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="18dcc-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="18dcc-184">Debian 10</span><span class="sxs-lookup"><span data-stu-id="18dcc-184">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-185">Debian 10 est pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="18dcc-185">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="18dcc-186">Installation via un dépôt de packages - Debian 10</span><span class="sxs-lookup"><span data-stu-id="18dcc-186">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="18dcc-187">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-187">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="18dcc-188">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="18dcc-188">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="18dcc-189">Installation par téléchargement direct - Debian 10</span><span class="sxs-lookup"><span data-stu-id="18dcc-189">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="18dcc-190">Téléchargez le package tar.gz `powershell_7.0.0-linux-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="18dcc-190">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="18dcc-191">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="18dcc-191">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="18dcc-192">Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="18dcc-192">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-193">Alpine 3.9 et 3.10 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="18dcc-193">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="18dcc-194">Installation par téléchargement direct - Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="18dcc-194">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="18dcc-195">Téléchargez le package tar.gz `powershell-7.0.0-linux-alpine-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Alpine.</span><span class="sxs-lookup"><span data-stu-id="18dcc-195">Download the tar.gz package `powershell-7.0.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="18dcc-196">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="18dcc-196">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="18dcc-197">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-197">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-198">Ce package fonctionne sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="18dcc-198">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="18dcc-199">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-199">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="18dcc-200">PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-200">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="18dcc-201">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="18dcc-201">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="18dcc-202">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-202">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="18dcc-203">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-203">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="18dcc-204">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="18dcc-204">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="18dcc-205">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="18dcc-205">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="18dcc-206">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="18dcc-206">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="18dcc-207">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-207">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="18dcc-209">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-209">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="18dcc-210">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-210">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="18dcc-211">PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="18dcc-212">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="18dcc-212">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="18dcc-213">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-213">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="18dcc-214">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-214">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="18dcc-215">Téléchargez le package RPM `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="18dcc-215">Download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="18dcc-216">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="18dcc-216">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="18dcc-217">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="18dcc-217">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="18dcc-218">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-218">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="18dcc-219">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="18dcc-219">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="18dcc-220">Installation – openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="18dcc-220">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="18dcc-221">Installation – openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="18dcc-221">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="18dcc-222">Désinstallation – openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="18dcc-222">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="18dcc-223">Fedora</span><span class="sxs-lookup"><span data-stu-id="18dcc-223">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-224">Fedora 28 n’est pris en charge que dans la version 6.1 et les versions plus récentes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="18dcc-224">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-225">Fedora 29 et 30 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="18dcc-225">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="18dcc-226">Installation via un dépôt de packages (par défaut) - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="18dcc-226">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="18dcc-227">PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-227">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="18dcc-228">Installation par téléchargement direct - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="18dcc-228">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="18dcc-229">Téléchargez le package RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="18dcc-229">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="18dcc-230">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="18dcc-230">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="18dcc-231">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="18dcc-231">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="18dcc-232">Désinstallation - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="18dcc-232">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="18dcc-233">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="18dcc-233">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-234">La prise en charge d’Arch n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.</span><span class="sxs-lookup"><span data-stu-id="18dcc-234">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="18dcc-235">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="18dcc-235">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="18dcc-236">Il peut être compilé avec la [dernière version étiquetée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="18dcc-236">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="18dcc-237">Il peut être compilé à partir de la [dernière validation sur le master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="18dcc-237">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="18dcc-238">Il peut être installé en utilisant la [dernière ressource binaire de la version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="18dcc-238">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="18dcc-239">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="18dcc-239">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="18dcc-240">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou [Utilisation de PowerShell](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="18dcc-240">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="18dcc-242">Snap Package</span><span class="sxs-lookup"><span data-stu-id="18dcc-242">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="18dcc-243">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="18dcc-243">Getting snapd</span></span>

<span data-ttu-id="18dcc-244">`snapd` est obligatoire pour exécuter des snaps.</span><span class="sxs-lookup"><span data-stu-id="18dcc-244">`snapd` is required to run snaps.</span></span> <span data-ttu-id="18dcc-245">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-245">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="18dcc-246">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="18dcc-246">Installation via Snap</span></span>

<span data-ttu-id="18dcc-247">PowerShell pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-247">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="18dcc-248">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="18dcc-248">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="18dcc-249">Pour installer une préversion, utilisez la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="18dcc-249">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="18dcc-250">Après l’installation, Snap est automatiquement mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="18dcc-250">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="18dcc-251">Vous pouvez déclencher une mise à niveau avec `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-251">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="18dcc-252">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="18dcc-252">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="18dcc-253">or</span><span class="sxs-lookup"><span data-stu-id="18dcc-253">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="18dcc-254">Kali</span><span class="sxs-lookup"><span data-stu-id="18dcc-254">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-255">La prise en charge de Kali n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.</span><span class="sxs-lookup"><span data-stu-id="18dcc-255">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="18dcc-256">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="18dcc-256">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="18dcc-257">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="18dcc-257">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="18dcc-258">Raspbian</span><span class="sxs-lookup"><span data-stu-id="18dcc-258">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="18dcc-259">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="18dcc-259">Raspbian support is experimental.</span></span>

<span data-ttu-id="18dcc-260">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="18dcc-260">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="18dcc-261">CoreCLR et PowerShell fonctionnent uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="18dcc-261">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="18dcc-262">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="18dcc-262">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="18dcc-263">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="18dcc-263">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="18dcc-264">Si vous le souhaitez, vous pouvez créer un lien symbolique pour démarrer PowerShell sans spécifier de chemin d’accès au binaire `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-264">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="18dcc-265">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="18dcc-265">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="18dcc-266">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="18dcc-266">Installing Preview Releases</span></span>

<span data-ttu-id="18dcc-267">Lorsque vous installez une préversion de PowerShell pour Linux au moyen d’un référentiel de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-267">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="18dcc-268">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="18dcc-268">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="18dcc-269">Le tableau suivant contient des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="18dcc-269">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="18dcc-270">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="18dcc-270">Distribution(s)</span></span> |            <span data-ttu-id="18dcc-271">Commande stable</span><span class="sxs-lookup"><span data-stu-id="18dcc-271">Stable Command</span></span>            |               <span data-ttu-id="18dcc-272">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="18dcc-272">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="18dcc-273">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="18dcc-273">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="18dcc-274">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="18dcc-274">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="18dcc-275">Fedora</span><span class="sxs-lookup"><span data-stu-id="18dcc-275">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="18dcc-276">Installation en tant qu’outil global .NET</span><span class="sxs-lookup"><span data-stu-id="18dcc-276">Install as a .NET Global tool</span></span>

<span data-ttu-id="18dcc-277">Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="18dcc-277">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="18dcc-278">Le programme d’installation de l’outil dotnet ajoute `~/.dotnet/tools` à votre variable d’environnement `PATH`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-278">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="18dcc-279">Toutefois, le `PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="18dcc-279">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="18dcc-280">Vous devez pouvoir démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-280">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="18dcc-281">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="18dcc-281">Binary Archives</span></span>

<span data-ttu-id="18dcc-282">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="18dcc-282">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="18dcc-283">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="18dcc-283">Dependencies</span></span>

<span data-ttu-id="18dcc-284">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="18dcc-284">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="18dcc-285">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte de la même manière.</span><span class="sxs-lookup"><span data-stu-id="18dcc-285">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="18dcc-286">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="18dcc-286">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="18dcc-287">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="18dcc-287">OS</span></span>                 | <span data-ttu-id="18dcc-288">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="18dcc-288">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="18dcc-289">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-289">Ubuntu 16.04</span></span>       | <span data-ttu-id="18dcc-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="18dcc-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="18dcc-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="18dcc-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="18dcc-292">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="18dcc-292">Ubuntu 17.10</span></span>       | <span data-ttu-id="18dcc-293">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="18dcc-293">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="18dcc-294">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="18dcc-294">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="18dcc-295">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="18dcc-295">Ubuntu 18.04</span></span>       | <span data-ttu-id="18dcc-296">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="18dcc-296">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="18dcc-297">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="18dcc-297">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="18dcc-298">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="18dcc-298">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="18dcc-299">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="18dcc-299">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="18dcc-300">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="18dcc-300">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="18dcc-301">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="18dcc-301">Debian 9 (Stretch)</span></span> | <span data-ttu-id="18dcc-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="18dcc-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="18dcc-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="18dcc-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="18dcc-304">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-304">CentOS 7</span></span> <br> <span data-ttu-id="18dcc-305">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-305">Oracle Linux 7</span></span> <br> <span data-ttu-id="18dcc-306">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="18dcc-306">RHEL 7</span></span> | <span data-ttu-id="18dcc-307">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="18dcc-307">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="18dcc-308">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="18dcc-308">openSUSE 42.3</span></span> | <span data-ttu-id="18dcc-309">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="18dcc-309">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="18dcc-310">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="18dcc-310">openSUSE Leap 15</span></span> | <span data-ttu-id="18dcc-311">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="18dcc-311">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="18dcc-312">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="18dcc-312">Fedora 27</span></span> <br> <span data-ttu-id="18dcc-313">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="18dcc-313">Fedora 28</span></span> | <span data-ttu-id="18dcc-314">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="18dcc-314">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="18dcc-315">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="18dcc-315">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="18dcc-316">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe d’abord les dépendances, puis extrait l’archive Linux `tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="18dcc-316">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="18dcc-317">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="18dcc-317">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="18dcc-318">Linux</span><span class="sxs-lookup"><span data-stu-id="18dcc-318">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="18dcc-319">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="18dcc-319">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="18dcc-320">Chemins</span><span class="sxs-lookup"><span data-stu-id="18dcc-320">Paths</span></span>

- <span data-ttu-id="18dcc-321">`$PSHOME` est `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="18dcc-321">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="18dcc-322">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="18dcc-322">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="18dcc-323">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="18dcc-323">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="18dcc-324">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="18dcc-324">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="18dcc-325">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="18dcc-325">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="18dcc-326">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="18dcc-326">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="18dcc-327">L’historique PSReadLine est enregistré dans`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="18dcc-327">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="18dcc-328">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="18dcc-328">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="18dcc-329">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="18dcc-329">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
