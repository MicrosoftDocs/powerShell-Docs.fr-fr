---
title: Installation de PowerShell Core sous Linux
description: Informations sur l’installation de PowerShell Core sur diverses distributions Linux
ms.date: 07/19/2019
ms.openlocfilehash: 3b0b9b1520247fa49760e631c837196fb7107b5f
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022269"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="a3aaf-103">Installation de PowerShell Core sous Linux</span><span class="sxs-lookup"><span data-stu-id="a3aaf-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="a3aaf-104">Prend en charge [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] et [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="a3aaf-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="a3aaf-105">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’installer PowerShell avec [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="a3aaf-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="a3aaf-106">Vous pouvez également essayer de déployer les fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires en fonction du système d’exploitation dans des étapes distinctes.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="a3aaf-107">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="a3aaf-108">Une fois le package installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="a3aaf-109">Exécutez `pwsh-preview` si vous avez installé une [préversion](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="a3aaf-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[deb10]: #debian-10
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

> [!TIP]
> <span data-ttu-id="a3aaf-110">Si vous avez déjà installé le kit [SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant qu’[outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="a3aaf-110">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="installing-preview-releases"></a><span data-ttu-id="a3aaf-111">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="a3aaf-111">Installing Preview Releases</span></span>

<span data-ttu-id="a3aaf-112">Lorsque vous installez une préversion de PowerShell Core pour Linux via un dépôt de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-112">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="a3aaf-113">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-113">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="a3aaf-114">Le tableau suivant contient des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-114">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="a3aaf-115">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="a3aaf-115">Distribution(s)</span></span>|<span data-ttu-id="a3aaf-116">Commande stable</span><span class="sxs-lookup"><span data-stu-id="a3aaf-116">Stable Command</span></span> | <span data-ttu-id="a3aaf-117">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="a3aaf-117">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="a3aaf-118">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="a3aaf-118">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="a3aaf-119">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="a3aaf-119">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="a3aaf-120">Fedora</span><span class="sxs-lookup"><span data-stu-id="a3aaf-120">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="a3aaf-121">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-121">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="a3aaf-122">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-122">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="a3aaf-123">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-123">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="a3aaf-124">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-124">The preferred method is as follows:</span></span>

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

<span data-ttu-id="a3aaf-125">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-125">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="a3aaf-126">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-126">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="a3aaf-127">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-127">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="a3aaf-128">Téléchargez le package Debian `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-128">Download the Debian package `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="a3aaf-129">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-129">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a3aaf-130">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-130">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="a3aaf-131">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="a3aaf-132">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-132">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="a3aaf-133">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-133">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="a3aaf-134">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-134">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="a3aaf-135">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-135">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="a3aaf-136">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-136">The preferred method is as follows:</span></span>

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

<span data-ttu-id="a3aaf-137">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-137">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="a3aaf-138">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-138">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="a3aaf-139">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-139">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="a3aaf-140">Téléchargez le package Debian `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-140">Download the Debian package `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="a3aaf-141">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-141">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a3aaf-142">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-142">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="a3aaf-143">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="a3aaf-144">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-144">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="a3aaf-145">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="a3aaf-145">Ubuntu 18.10</span></span>

<span data-ttu-id="a3aaf-146">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-146">Installation is supported via `snapd`.</span></span> <span data-ttu-id="a3aaf-147">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="a3aaf-147">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-148">Ubuntu 18.10 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle)[prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="a3aaf-148">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="a3aaf-149">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-149">Ubuntu 19.04</span></span>

<span data-ttu-id="a3aaf-150">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-150">Installation is supported via `snapd`.</span></span> <span data-ttu-id="a3aaf-151">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="a3aaf-151">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-152">Ubuntu 19.04 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle)[prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="a3aaf-152">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="a3aaf-153">Debian 8</span><span class="sxs-lookup"><span data-stu-id="a3aaf-153">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="a3aaf-154">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a3aaf-154">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="a3aaf-155">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="a3aaf-156">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="a3aaf-157">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="a3aaf-158">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="a3aaf-159">Debian 9</span><span class="sxs-lookup"><span data-stu-id="a3aaf-159">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="a3aaf-160">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a3aaf-160">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="a3aaf-161">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-161">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="a3aaf-162">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-162">The preferred method is as follows:</span></span>

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

<span data-ttu-id="a3aaf-163">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-163">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="a3aaf-164">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-164">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="a3aaf-165">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a3aaf-165">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="a3aaf-166">Téléchargez le package Debian `powershell_7.0.0-1.debian.9_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-166">Download the Debian package `powershell_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="a3aaf-167">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-167">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="a3aaf-168">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a3aaf-168">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="a3aaf-169">Debian 10</span><span class="sxs-lookup"><span data-stu-id="a3aaf-169">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-170">Debian 10 est pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-170">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="a3aaf-171">Installation par téléchargement direct - Debian 10</span><span class="sxs-lookup"><span data-stu-id="a3aaf-171">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="a3aaf-172">Téléchargez le package tar.gz `powershell_7.0.0-preview-7-linux-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-172">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="a3aaf-173">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-173">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="a3aaf-174">Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="a3aaf-174">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-175">Alpine 3.9 et 3.10 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-175">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="a3aaf-176">Installation par téléchargement direct - Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="a3aaf-176">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="a3aaf-177">Téléchargez le package tar.gz `powershell_7.0.0-preview-7-linux-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Alpine.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-177">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="a3aaf-178">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-178">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="centos-7"></a><span data-ttu-id="a3aaf-179">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-179">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-180">Ce package fonctionne sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-180">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="a3aaf-181">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-181">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="a3aaf-182">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-182">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a3aaf-183">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-183">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="a3aaf-184">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-184">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="a3aaf-185">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="a3aaf-186">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-186">Using [CentOS 7][], download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="a3aaf-187">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-187">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a3aaf-188">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-188">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="a3aaf-189">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a3aaf-191">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a3aaf-192">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="a3aaf-193">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a3aaf-194">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-194">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="a3aaf-195">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-195">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a3aaf-196">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-196">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="a3aaf-197">Téléchargez le package RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-197">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="a3aaf-198">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-198">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a3aaf-199">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-199">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a3aaf-200">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-200">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="a3aaf-201">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="a3aaf-201">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="a3aaf-202">Installation – openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="a3aaf-202">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="a3aaf-203">Installation – openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="a3aaf-203">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="a3aaf-204">Désinstallation – openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="a3aaf-204">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="a3aaf-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="a3aaf-205">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-206">Fedora 28 est pris en charge dans PowerShell Core 6.1 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-206">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-207">Fedora 29 et 30 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-207">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="a3aaf-208">Installation via un dépôt de packages (par défaut) - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="a3aaf-208">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="a3aaf-209">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-209">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="a3aaf-210">Installation par téléchargement direct - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="a3aaf-210">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="a3aaf-211">Téléchargez le package RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-211">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="a3aaf-212">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-212">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a3aaf-213">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-213">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="a3aaf-214">Désinstallation - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="a3aaf-214">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="a3aaf-215">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="a3aaf-215">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-216">La prise en charge d’Arch n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-216">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="a3aaf-217">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="a3aaf-217">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="a3aaf-218">Il peut être compilé avec la [dernière version étiquetée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="a3aaf-218">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="a3aaf-219">Il peut être compilé à partir de la [dernière validation sur le master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="a3aaf-219">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="a3aaf-220">Il peut être installé en utilisant la [dernière ressource binaire de la version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="a3aaf-220">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="a3aaf-221">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-221">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="a3aaf-222">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou le [fichier Dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la communauté.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-222">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="a3aaf-224">Snap Package</span><span class="sxs-lookup"><span data-stu-id="a3aaf-224">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="a3aaf-225">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="a3aaf-225">Getting snapd</span></span>

<span data-ttu-id="a3aaf-226">`snapd` est obligatoire pour exécuter des snaps.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-226">`snapd` is required to run snaps.</span></span> <span data-ttu-id="a3aaf-227">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-227">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="a3aaf-228">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="a3aaf-228">Installation via Snap</span></span>

<span data-ttu-id="a3aaf-229">PowerShell Core pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-229">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="a3aaf-230">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-230">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="a3aaf-231">Pour installer une préversion, utilisez la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="a3aaf-231">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="a3aaf-232">Après l’installation, Snap est automatiquement mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-232">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="a3aaf-233">Vous pouvez déclencher une mise à niveau avec `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-233">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="a3aaf-234">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="a3aaf-234">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="a3aaf-235">or</span><span class="sxs-lookup"><span data-stu-id="a3aaf-235">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="a3aaf-236">Kali</span><span class="sxs-lookup"><span data-stu-id="a3aaf-236">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-237">La prise en charge de Kali n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-237">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="a3aaf-238">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="a3aaf-238">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="a3aaf-239">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="a3aaf-239">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="a3aaf-240">Raspbian</span><span class="sxs-lookup"><span data-stu-id="a3aaf-240">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="a3aaf-241">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-241">Raspbian support is experimental.</span></span>

<span data-ttu-id="a3aaf-242">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="a3aaf-243">CoreCLR et PowerShell Core fonctionnent uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-243">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="a3aaf-244">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-244">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="a3aaf-245">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="a3aaf-245">Installation - Raspbian</span></span>

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

<span data-ttu-id="a3aaf-246">Si vous le souhaitez, vous pouvez créer un lien symbolique pour démarrer PowerShell sans spécifier de chemin d’accès au binaire `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-246">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="a3aaf-247">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="a3aaf-247">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="a3aaf-248">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="a3aaf-248">Binary Archives</span></span>

<span data-ttu-id="a3aaf-249">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-249">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="a3aaf-250">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="a3aaf-250">Dependencies</span></span>

<span data-ttu-id="a3aaf-251">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-251">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="a3aaf-252">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte de la même manière.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-252">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="a3aaf-253">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-253">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="a3aaf-254">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="a3aaf-254">OS</span></span>                 | <span data-ttu-id="a3aaf-255">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="a3aaf-255">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="a3aaf-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="a3aaf-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="a3aaf-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a3aaf-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="a3aaf-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="a3aaf-259">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="a3aaf-259">Ubuntu 17.10</span></span>       | <span data-ttu-id="a3aaf-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="a3aaf-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a3aaf-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="a3aaf-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="a3aaf-262">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a3aaf-262">Ubuntu 18.04</span></span>       | <span data-ttu-id="a3aaf-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="a3aaf-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a3aaf-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="a3aaf-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="a3aaf-265">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="a3aaf-265">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="a3aaf-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="a3aaf-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a3aaf-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="a3aaf-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="a3aaf-268">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="a3aaf-268">Debian 9 (Stretch)</span></span> | <span data-ttu-id="a3aaf-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="a3aaf-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a3aaf-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="a3aaf-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="a3aaf-271">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-271">CentOS 7</span></span> <br> <span data-ttu-id="a3aaf-272">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-272">Oracle Linux 7</span></span> <br> <span data-ttu-id="a3aaf-273">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="a3aaf-273">RHEL 7</span></span> | <span data-ttu-id="a3aaf-274">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="a3aaf-274">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="a3aaf-275">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="a3aaf-275">openSUSE 42.3</span></span> | <span data-ttu-id="a3aaf-276">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="a3aaf-276">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="a3aaf-277">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="a3aaf-277">openSUSE Leap 15</span></span> | <span data-ttu-id="a3aaf-278">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="a3aaf-278">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="a3aaf-279">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="a3aaf-279">Fedora 27</span></span> <br> <span data-ttu-id="a3aaf-280">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a3aaf-280">Fedora 28</span></span> | <span data-ttu-id="a3aaf-281">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="a3aaf-281">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="a3aaf-282">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-282">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="a3aaf-283">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe d’abord les dépendances, puis extrait l’archive Linux `tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-283">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="a3aaf-284">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="a3aaf-284">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="a3aaf-285">Linux</span><span class="sxs-lookup"><span data-stu-id="a3aaf-285">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="a3aaf-286">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="a3aaf-286">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="a3aaf-287">Chemins</span><span class="sxs-lookup"><span data-stu-id="a3aaf-287">Paths</span></span>

* <span data-ttu-id="a3aaf-288">`$PSHOME` est `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="a3aaf-288">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
* <span data-ttu-id="a3aaf-289">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a3aaf-289">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="a3aaf-290">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a3aaf-290">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="a3aaf-291">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a3aaf-291">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a3aaf-292">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a3aaf-292">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a3aaf-293">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="a3aaf-293">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="a3aaf-294">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="a3aaf-294">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="a3aaf-295">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-295">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="a3aaf-296">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-296">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
