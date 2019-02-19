---
title: Installation de PowerShell Core sous Linux
description: Informations sur l’installation de PowerShell Core sur diverses distributions Linux
ms.date: 08/06/2018
ms.openlocfilehash: 2ab9beb19e5f90b392413eee31e3fed317e267b0
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265533"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="ec1e7-103">Installation de PowerShell Core sous Linux</span><span class="sxs-lookup"><span data-stu-id="ec1e7-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="ec1e7-104">Prend en charge [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] et [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="ec1e7-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="ec1e7-105">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’utiliser [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="ec1e7-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="ec1e7-106">Vous pouvez également essayer de déployer des fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires selon le système d’exploitation dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="ec1e7-107">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="ec1e7-108">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="ec1e7-109">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="ec1e7-109">Installing Preview Releases</span></span>

<span data-ttu-id="ec1e7-110">Lorsque vous installez une préversion de PowerShell Core pour Linux via un dépôt de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="ec1e7-111">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="ec1e7-112">Voici un tableau des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="ec1e7-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="ec1e7-113">Distribution(s)</span></span>|<span data-ttu-id="ec1e7-114">Commande stable</span><span class="sxs-lookup"><span data-stu-id="ec1e7-114">Stable Command</span></span> | <span data-ttu-id="ec1e7-115">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="ec1e7-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="ec1e7-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="ec1e7-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="ec1e7-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="ec1e7-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="ec1e7-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="ec1e7-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="ec1e7-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="ec1e7-120">Installation via un dépôt de packages - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="ec1e7-121">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec1e7-122">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec1e7-123">En tant que super utilisateur, inscrivez le référentiel Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="ec1e7-124">Dès lors, il vous suffit d’utiliser `sudo apt-get upgrade powershell` pour mettre à jour l’installation.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="ec1e7-125">Installation par téléchargement direct - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="ec1e7-126">Téléchargez le package Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="ec1e7-127">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ec1e7-128">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ec1e7-129">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ec1e7-130">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="ec1e7-131">Désinstallation - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="ec1e7-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="ec1e7-133">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="ec1e7-134">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec1e7-135">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-135">This is the preferred method.</span></span>

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

<span data-ttu-id="ec1e7-136">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="ec1e7-137">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="ec1e7-138">Téléchargez le package Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="ec1e7-139">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ec1e7-140">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ec1e7-141">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ec1e7-142">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="ec1e7-143">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="ec1e7-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="ec1e7-145">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="ec1e7-146">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec1e7-147">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-147">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec1e7-148">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="ec1e7-149">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="ec1e7-150">Téléchargez le package Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-150">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="ec1e7-151">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ec1e7-152">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ec1e7-153">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ec1e7-154">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="ec1e7-155">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="ec1e7-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="ec1e7-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="ec1e7-157">Comme 18.10 est un [version intermédiaire](https://www.ubuntu.com/about/release-cycle), il est uniquement [Communauté pris en charge](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="ec1e7-158">L’installation de 18.10 est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="ec1e7-159">Consultez [Snap Package][snap] pour des instructions complètes.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="ec1e7-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="ec1e7-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="ec1e7-161">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="ec1e7-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="ec1e7-162">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec1e7-163">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-163">This is the preferred method.</span></span>

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

<span data-ttu-id="ec1e7-164">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="ec1e7-165">Installation par téléchargement direct - Debian 8</span><span class="sxs-lookup"><span data-stu-id="ec1e7-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="ec1e7-166">Téléchargez le package Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-166">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="ec1e7-167">à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-167">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ec1e7-168">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-168">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ec1e7-169">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-169">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ec1e7-170">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-170">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="ec1e7-171">Désinstallation - Debian 8</span><span class="sxs-lookup"><span data-stu-id="ec1e7-171">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="ec1e7-172">Debian 9</span><span class="sxs-lookup"><span data-stu-id="ec1e7-172">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="ec1e7-173">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ec1e7-173">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="ec1e7-174">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-174">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ec1e7-175">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-175">This is the preferred method.</span></span>

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

<span data-ttu-id="ec1e7-176">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-176">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="ec1e7-177">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ec1e7-177">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="ec1e7-178">Téléchargez le package Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-178">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="ec1e7-179">à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-179">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ec1e7-180">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-180">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="ec1e7-181">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ec1e7-181">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="ec1e7-182">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-182">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="ec1e7-183">Ce package fonctionne également sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-183">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="ec1e7-184">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-184">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="ec1e7-185">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec1e7-186">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-186">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="ec1e7-187">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-187">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="ec1e7-188">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-188">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="ec1e7-189">à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-189">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="ec1e7-190">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-190">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec1e7-191">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-191">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="ec1e7-192">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-192">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec1e7-194">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-194">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec1e7-195">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-195">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ec1e7-196">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ec1e7-197">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-197">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec1e7-198">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-198">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ec1e7-199">Téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-199">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="ec1e7-200">à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-200">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="ec1e7-201">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-201">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec1e7-202">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-202">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ec1e7-203">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-203">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="ec1e7-204">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="ec1e7-204">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="ec1e7-205">Installation – openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ec1e7-205">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="ec1e7-206">Installation – openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ec1e7-206">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="ec1e7-207">Désinstallation – openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ec1e7-207">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="ec1e7-208">Fedora</span><span class="sxs-lookup"><span data-stu-id="ec1e7-208">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="ec1e7-209">Fedora 28 est pris en charge dans PowerShell Core 6.1 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-209">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="ec1e7-210">Installation au moyen d’un référentiel de packages (par défaut) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec1e7-210">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ec1e7-211">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-211">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="ec1e7-212">Installation par téléchargement direct – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec1e7-212">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ec1e7-213">Téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-213">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="ec1e7-214">à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-214">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="ec1e7-215">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-215">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ec1e7-216">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="ec1e7-216">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="ec1e7-217">Désinstallation – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec1e7-217">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="ec1e7-218">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="ec1e7-218">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="ec1e7-219">La prise en charge d’arch est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-219">Arch support is experimental.</span></span>

<span data-ttu-id="ec1e7-220">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="ec1e7-220">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="ec1e7-221">Il peut être compilé avec la [dernière version identifiée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="ec1e7-221">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="ec1e7-222">Il peut être compilé à partir de la [dernière validation sur le maître][arch-git]</span><span class="sxs-lookup"><span data-stu-id="ec1e7-222">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="ec1e7-223">Il peut être installé à l’aide de la [dernière ressource binaire de version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="ec1e7-223">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="ec1e7-224">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-224">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="ec1e7-225">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou le [fichier Dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la communauté.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-225">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="ec1e7-227">Snap Package</span><span class="sxs-lookup"><span data-stu-id="ec1e7-227">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="ec1e7-228">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="ec1e7-228">Getting snapd</span></span>

<span data-ttu-id="ec1e7-229">`snapd` est obligatoire pour exécuter des snaps.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-229">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="ec1e7-230">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-230">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="ec1e7-231">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="ec1e7-231">Installation via Snap</span></span>

<span data-ttu-id="ec1e7-232">PowerShell Core pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="ec1e7-232">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="ec1e7-233">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-233">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="ec1e7-234">Si vous souhaitez installer la préversion, utilisez la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-234">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="ec1e7-235">La mise à niveau de Snap est automatique après l’installation, mais vous pouvez déclencher une mise à niveau avec `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="ec1e7-236">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="ec1e7-236">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="ec1e7-237">ou</span><span class="sxs-lookup"><span data-stu-id="ec1e7-237">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="ec1e7-238">Kali</span><span class="sxs-lookup"><span data-stu-id="ec1e7-238">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="ec1e7-239">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="ec1e7-239">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
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

### <a name="uninstallation---kali"></a><span data-ttu-id="ec1e7-240">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="ec1e7-240">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="ec1e7-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="ec1e7-241">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="ec1e7-242">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-242">Raspbian support is experimental.</span></span>

<span data-ttu-id="ec1e7-243">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-243">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="ec1e7-244">De plus, CoreCLR (et donc PowerShell Core) fonctionne uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-244">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="ec1e7-245">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-245">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="ec1e7-246">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="ec1e7-246">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="ec1e7-247">Si vous le souhaitez, vous pouvez créer un lien symbolique pour être en mesure de démarrer PowerShell sans spécifier de chemin d’accès au binaire « pwsh »</span><span class="sxs-lookup"><span data-stu-id="ec1e7-247">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="ec1e7-248">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="ec1e7-248">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="ec1e7-249">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="ec1e7-249">Binary Archives</span></span>

<span data-ttu-id="ec1e7-250">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-250">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="ec1e7-251">Dépendances</span><span class="sxs-lookup"><span data-stu-id="ec1e7-251">Dependencies</span></span>

<span data-ttu-id="ec1e7-252">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-252">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="ec1e7-253">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte par conséquent de la même manière.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-253">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="ec1e7-254">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-254">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="ec1e7-255">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="ec1e7-255">OS</span></span>                 | <span data-ttu-id="ec1e7-256">Dépendances</span><span class="sxs-lookup"><span data-stu-id="ec1e7-256">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="ec1e7-257">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-257">Ubuntu 14.04</span></span>       | <span data-ttu-id="ec1e7-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ec1e7-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec1e7-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="ec1e7-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ec1e7-260">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-260">Ubuntu 16.04</span></span>       | <span data-ttu-id="ec1e7-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ec1e7-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec1e7-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="ec1e7-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="ec1e7-263">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="ec1e7-263">Ubuntu 17.10</span></span>       | <span data-ttu-id="ec1e7-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ec1e7-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec1e7-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="ec1e7-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="ec1e7-266">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ec1e7-266">Ubuntu 18.04</span></span>       | <span data-ttu-id="ec1e7-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ec1e7-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec1e7-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="ec1e7-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="ec1e7-269">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="ec1e7-269">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="ec1e7-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ec1e7-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec1e7-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="ec1e7-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ec1e7-272">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="ec1e7-272">Debian 9 (Stretch)</span></span> | <span data-ttu-id="ec1e7-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ec1e7-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ec1e7-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="ec1e7-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="ec1e7-275">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-275">CentOS 7</span></span> <br> <span data-ttu-id="ec1e7-276">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-276">Oracle Linux 7</span></span> <br> <span data-ttu-id="ec1e7-277">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="ec1e7-277">RHEL 7</span></span> | <span data-ttu-id="ec1e7-278">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="ec1e7-278">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="ec1e7-279">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ec1e7-279">openSUSE 42.3</span></span> | <span data-ttu-id="ec1e7-280">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="ec1e7-280">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="ec1e7-281">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ec1e7-281">openSUSE Leap 15</span></span> | <span data-ttu-id="ec1e7-282">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="ec1e7-282">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="ec1e7-283">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="ec1e7-283">Fedora 27</span></span> <br> <span data-ttu-id="ec1e7-284">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ec1e7-284">Fedora 28</span></span> | <span data-ttu-id="ec1e7-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="ec1e7-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="ec1e7-286">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-286">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="ec1e7-287">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe tout d’abord les dépendances, puis extrait l’archive `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-287">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="ec1e7-288">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="ec1e7-288">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="ec1e7-289">Linux</span><span class="sxs-lookup"><span data-stu-id="ec1e7-289">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="ec1e7-290">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="ec1e7-290">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="ec1e7-291">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="ec1e7-291">Paths</span></span>

* <span data-ttu-id="ec1e7-292">`$PSHOME` est `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-292">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="ec1e7-293">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-293">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="ec1e7-294">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-294">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="ec1e7-295">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-295">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ec1e7-296">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-296">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ec1e7-297">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-297">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="ec1e7-298">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="ec1e7-298">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="ec1e7-299">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-299">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ec1e7-300">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="ec1e7-300">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
