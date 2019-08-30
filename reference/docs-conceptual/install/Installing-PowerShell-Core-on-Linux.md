---
title: Installation de PowerShell Core sous Linux
description: Informations sur l’installation de PowerShell Core sur diverses distributions Linux
ms.date: 07/19/2019
ms.openlocfilehash: be11a2a873af71c193730d0a9e723da2dc70a62d
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986724"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e23e7-103">Installation de PowerShell Core sous Linux</span><span class="sxs-lookup"><span data-stu-id="e23e7-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e23e7-104">Prend en charge [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] et [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="e23e7-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e23e7-105">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’installer PowerShell avec [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="e23e7-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="e23e7-106">Vous pouvez également essayer de déployer les fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires en fonction du système d’exploitation dans des étapes distinctes.</span><span class="sxs-lookup"><span data-stu-id="e23e7-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e23e7-107">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="e23e7-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="e23e7-108">Une fois le package installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="e23e7-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="e23e7-109">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="e23e7-109">Installing Preview Releases</span></span>

<span data-ttu-id="e23e7-110">Lorsque vous installez une préversion de PowerShell Core pour Linux via un dépôt de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e23e7-111">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e23e7-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="e23e7-112">Le tableau suivant contient des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="e23e7-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="e23e7-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="e23e7-113">Distribution(s)</span></span>|<span data-ttu-id="e23e7-114">Commande stable</span><span class="sxs-lookup"><span data-stu-id="e23e7-114">Stable Command</span></span> | <span data-ttu-id="e23e7-115">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="e23e7-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="e23e7-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="e23e7-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="e23e7-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="e23e7-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="e23e7-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="e23e7-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="e23e7-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e23e7-120">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e23e7-121">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="e23e7-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e23e7-122">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e23e7-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="e23e7-123">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="e23e7-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e23e7-124">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e23e7-125">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e23e7-126">Téléchargez le package Debian `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e23e7-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e23e7-127">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="e23e7-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e23e7-128">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="e23e7-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="e23e7-129">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e23e7-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e23e7-130">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e23e7-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e23e7-132">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e23e7-133">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="e23e7-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e23e7-134">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e23e7-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="e23e7-135">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="e23e7-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e23e7-136">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e23e7-137">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e23e7-138">Téléchargez le package Debian `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e23e7-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e23e7-139">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="e23e7-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e23e7-140">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="e23e7-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="e23e7-141">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e23e7-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="e23e7-142">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="e23e7-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="e23e7-143">Ubuntu 18.10</span></span>

<span data-ttu-id="e23e7-144">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-144">Installation is supported via `snapd`.</span></span> <span data-ttu-id="e23e7-145">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="e23e7-145">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="e23e7-146">Ubuntu 18.10 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle) [prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="e23e7-146">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="e23e7-147">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-147">Ubuntu 19.04</span></span>

<span data-ttu-id="e23e7-148">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="e23e7-149">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="e23e7-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="e23e7-150">Ubuntu 19.04 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle) [prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="e23e7-150">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="e23e7-151">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e23e7-151">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e23e7-152">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e23e7-152">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e23e7-153">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="e23e7-153">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e23e7-154">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e23e7-154">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

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

<span data-ttu-id="e23e7-155">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="e23e7-155">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e23e7-156">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-156">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="e23e7-157">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e23e7-157">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e23e7-158">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e23e7-158">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e23e7-159">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="e23e7-159">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e23e7-160">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e23e7-160">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

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

<span data-ttu-id="e23e7-161">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="e23e7-161">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e23e7-162">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-162">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e23e7-163">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e23e7-163">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e23e7-164">Téléchargez le package Debian `powershell_6.2.0-1.debian.9_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="e23e7-164">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e23e7-165">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="e23e7-165">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e23e7-166">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e23e7-166">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e23e7-167">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-167">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e23e7-168">Ce package fonctionne sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e23e7-168">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e23e7-169">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-169">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e23e7-170">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="e23e7-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e23e7-171">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="e23e7-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e23e7-172">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-172">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e23e7-173">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-173">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e23e7-174">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="e23e7-174">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e23e7-175">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="e23e7-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e23e7-176">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="e23e7-176">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e23e7-177">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-177">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e23e7-179">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-179">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e23e7-180">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-180">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e23e7-181">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="e23e7-181">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e23e7-182">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="e23e7-182">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e23e7-183">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-183">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e23e7-184">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-184">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e23e7-185">Téléchargez le package RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="e23e7-185">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e23e7-186">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="e23e7-186">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e23e7-187">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="e23e7-187">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e23e7-188">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-188">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="e23e7-189">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="e23e7-189">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="e23e7-190">Installation – openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e23e7-190">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="e23e7-191">Installation – openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e23e7-191">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="e23e7-192">Désinstallation – openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e23e7-192">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="e23e7-193">Fedora</span><span class="sxs-lookup"><span data-stu-id="e23e7-193">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e23e7-194">Fedora 28 est pris en charge dans PowerShell Core 6.1 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="e23e7-194">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e23e7-195">Installation au moyen d’un référentiel de packages (par défaut) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e23e7-195">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e23e7-196">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="e23e7-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e23e7-197">Installation par téléchargement direct – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e23e7-197">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e23e7-198">Téléchargez le package RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="e23e7-198">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e23e7-199">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="e23e7-199">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e23e7-200">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="e23e7-200">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e23e7-201">Désinstallation – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e23e7-201">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e23e7-202">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e23e7-202">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e23e7-203">La prise en charge d’arch est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="e23e7-203">Arch support is experimental.</span></span>

<span data-ttu-id="e23e7-204">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="e23e7-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e23e7-205">Il peut être compilé avec la [dernière version étiquetée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e23e7-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e23e7-206">Il peut être compilé à partir de la [dernière validation sur le master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e23e7-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e23e7-207">Il peut être installé en utilisant la [dernière ressource binaire de la version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e23e7-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e23e7-208">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="e23e7-208">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="e23e7-209">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou le [fichier Dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la communauté.</span><span class="sxs-lookup"><span data-stu-id="e23e7-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="e23e7-211">Snap Package</span><span class="sxs-lookup"><span data-stu-id="e23e7-211">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="e23e7-212">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="e23e7-212">Getting snapd</span></span>

<span data-ttu-id="e23e7-213">`snapd` est obligatoire pour exécuter des snaps.</span><span class="sxs-lookup"><span data-stu-id="e23e7-213">`snapd` is required to run snaps.</span></span> <span data-ttu-id="e23e7-214">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-214">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="e23e7-215">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="e23e7-215">Installation via Snap</span></span>

<span data-ttu-id="e23e7-216">PowerShell Core pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="e23e7-216">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="e23e7-217">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e23e7-217">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="e23e7-218">Pour installer une préversion, utilisez la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="e23e7-218">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="e23e7-219">Après l’installation, Snap est automatiquement mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="e23e7-219">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="e23e7-220">Vous pouvez déclencher une mise à niveau avec `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-220">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="e23e7-221">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="e23e7-221">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="e23e7-222">ou</span><span class="sxs-lookup"><span data-stu-id="e23e7-222">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="e23e7-223">Kali</span><span class="sxs-lookup"><span data-stu-id="e23e7-223">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="e23e7-224">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="e23e7-224">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="e23e7-225">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="e23e7-225">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="e23e7-226">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e23e7-226">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e23e7-227">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="e23e7-227">Raspbian support is experimental.</span></span>

<span data-ttu-id="e23e7-228">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="e23e7-228">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e23e7-229">CoreCLR et PowerShell Core fonctionnent uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e23e7-229">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e23e7-230">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="e23e7-230">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="e23e7-231">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="e23e7-231">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="e23e7-232">Si vous le souhaitez, vous pouvez créer un lien symbolique pour démarrer PowerShell sans spécifier de chemin d’accès au binaire `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-232">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e23e7-233">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e23e7-233">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e23e7-234">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="e23e7-234">Binary Archives</span></span>

<span data-ttu-id="e23e7-235">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="e23e7-235">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e23e7-236">Dépendances</span><span class="sxs-lookup"><span data-stu-id="e23e7-236">Dependencies</span></span>

<span data-ttu-id="e23e7-237">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="e23e7-237">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="e23e7-238">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte de la même manière.</span><span class="sxs-lookup"><span data-stu-id="e23e7-238">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="e23e7-239">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="e23e7-239">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e23e7-240">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="e23e7-240">OS</span></span>                 | <span data-ttu-id="e23e7-241">Dépendances</span><span class="sxs-lookup"><span data-stu-id="e23e7-241">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e23e7-242">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-242">Ubuntu 16.04</span></span>       | <span data-ttu-id="e23e7-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e23e7-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e23e7-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e23e7-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e23e7-245">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e23e7-245">Ubuntu 17.10</span></span>       | <span data-ttu-id="e23e7-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e23e7-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e23e7-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e23e7-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e23e7-248">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e23e7-248">Ubuntu 18.04</span></span>       | <span data-ttu-id="e23e7-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e23e7-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e23e7-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e23e7-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e23e7-251">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e23e7-251">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e23e7-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e23e7-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e23e7-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e23e7-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e23e7-254">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e23e7-254">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e23e7-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e23e7-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e23e7-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e23e7-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e23e7-257">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-257">CentOS 7</span></span> <br> <span data-ttu-id="e23e7-258">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-258">Oracle Linux 7</span></span> <br> <span data-ttu-id="e23e7-259">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e23e7-259">RHEL 7</span></span> | <span data-ttu-id="e23e7-260">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="e23e7-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e23e7-261">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e23e7-261">openSUSE 42.3</span></span> | <span data-ttu-id="e23e7-262">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="e23e7-262">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="e23e7-263">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e23e7-263">openSUSE Leap 15</span></span> | <span data-ttu-id="e23e7-264">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="e23e7-264">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="e23e7-265">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e23e7-265">Fedora 27</span></span> <br> <span data-ttu-id="e23e7-266">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e23e7-266">Fedora 28</span></span> | <span data-ttu-id="e23e7-267">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="e23e7-267">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e23e7-268">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="e23e7-268">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="e23e7-269">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe d’abord les dépendances, puis extrait l’archive Linux `tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="e23e7-269">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e23e7-270">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="e23e7-270">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e23e7-271">Linux</span><span class="sxs-lookup"><span data-stu-id="e23e7-271">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e23e7-272">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="e23e7-272">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e23e7-273">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="e23e7-273">Paths</span></span>

* <span data-ttu-id="e23e7-274">`$PSHOME` est `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="e23e7-274">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="e23e7-275">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e23e7-275">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e23e7-276">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e23e7-276">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e23e7-277">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e23e7-277">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e23e7-278">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e23e7-278">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e23e7-279">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e23e7-279">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e23e7-280">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e23e7-280">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e23e7-281">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="e23e7-281">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e23e7-282">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="e23e7-282">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
