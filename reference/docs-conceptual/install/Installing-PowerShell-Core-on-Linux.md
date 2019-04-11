---
title: Installation de PowerShell Core sous Linux
description: Informations sur l’installation de PowerShell Core sur diverses distributions Linux
ms.date: 08/06/2018
ms.openlocfilehash: 06194550f4e73f9dd38f8cdc25f6c7f698cafce2
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293331"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="595e3-103">Installation de PowerShell Core sous Linux</span><span class="sxs-lookup"><span data-stu-id="595e3-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="595e3-104">Prend en charge [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], et [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="595e3-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="595e3-105">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’utiliser [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="595e3-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="595e3-106">Vous pouvez également essayer de déployer des fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires selon le système d’exploitation dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="595e3-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="595e3-107">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="595e3-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="595e3-108">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="595e3-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="595e3-109">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="595e3-109">Installing Preview Releases</span></span>

<span data-ttu-id="595e3-110">Lorsque vous installez une préversion de PowerShell Core pour Linux via un dépôt de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="595e3-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="595e3-111">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="595e3-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="595e3-112">Voici un tableau des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="595e3-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="595e3-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="595e3-113">Distribution(s)</span></span>|<span data-ttu-id="595e3-114">Commande stable</span><span class="sxs-lookup"><span data-stu-id="595e3-114">Stable Command</span></span> | <span data-ttu-id="595e3-115">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="595e3-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="595e3-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="595e3-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="595e3-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="595e3-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="595e3-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="595e3-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="595e3-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="595e3-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="595e3-120">Installation via un dépôt de packages - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="595e3-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="595e3-121">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="595e3-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="595e3-122">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="595e3-122">This is the preferred method.</span></span>

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

<span data-ttu-id="595e3-123">En tant que super utilisateur, inscrivez le référentiel Microsoft.</span><span class="sxs-lookup"><span data-stu-id="595e3-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="595e3-124">Dès lors, il vous suffit d’utiliser `sudo apt-get upgrade powershell` pour mettre à jour l’installation.</span><span class="sxs-lookup"><span data-stu-id="595e3-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="595e3-125">Installation par téléchargement direct - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="595e3-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="595e3-126">Téléchargez le package Debian</span><span class="sxs-lookup"><span data-stu-id="595e3-126">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.14.04_amd64.deb`
<span data-ttu-id="595e3-127">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="595e3-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="595e3-128">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="595e3-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="595e3-129">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="595e3-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="595e3-130">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="595e3-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="595e3-131">Désinstallation - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="595e3-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="595e3-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="595e3-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="595e3-133">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="595e3-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="595e3-134">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="595e3-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="595e3-135">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="595e3-135">This is the preferred method.</span></span>

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

<span data-ttu-id="595e3-136">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="595e3-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="595e3-137">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="595e3-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="595e3-138">Téléchargez le package Debian</span><span class="sxs-lookup"><span data-stu-id="595e3-138">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.16.04_amd64.deb`
<span data-ttu-id="595e3-139">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="595e3-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="595e3-140">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="595e3-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="595e3-141">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="595e3-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="595e3-142">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="595e3-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="595e3-143">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="595e3-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="595e3-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="595e3-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="595e3-145">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="595e3-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="595e3-146">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="595e3-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="595e3-147">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="595e3-147">This is the preferred method.</span></span>

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

<span data-ttu-id="595e3-148">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="595e3-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="595e3-149">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="595e3-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="595e3-150">Téléchargez le package Debian</span><span class="sxs-lookup"><span data-stu-id="595e3-150">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.18.04_amd64.deb`
<span data-ttu-id="595e3-151">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="595e3-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="595e3-152">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="595e3-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="595e3-153">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="595e3-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="595e3-154">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="595e3-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="595e3-155">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="595e3-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="595e3-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="595e3-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="595e3-157">La version 18.10 étant une [version intermédiaire](https://www.ubuntu.com/about/release-cycle), elle est uniquement [prise en charge par la communauté](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="595e3-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="595e3-158">L’installation de 18.10 est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="595e3-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="595e3-159">Consultez [Snap Package][snap] pour des instructions complètes.</span><span class="sxs-lookup"><span data-stu-id="595e3-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="595e3-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="595e3-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="595e3-161">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="595e3-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="595e3-162">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="595e3-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="595e3-163">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="595e3-163">This is the preferred method.</span></span>

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

<span data-ttu-id="595e3-164">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="595e3-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="595e3-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="595e3-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="595e3-166">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="595e3-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="595e3-167">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="595e3-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="595e3-168">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="595e3-168">This is the preferred method.</span></span>

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

<span data-ttu-id="595e3-169">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="595e3-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="595e3-170">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="595e3-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="595e3-171">Téléchargez le package Debian</span><span class="sxs-lookup"><span data-stu-id="595e3-171">Download the Debian package</span></span>
`powershell_6.2.0-1.debian.9_amd64.deb`
<span data-ttu-id="595e3-172">à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="595e3-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="595e3-173">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="595e3-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="595e3-174">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="595e3-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="595e3-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="595e3-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="595e3-176">Ce package fonctionne également sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="595e3-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="595e3-177">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="595e3-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="595e3-178">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="595e3-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="595e3-179">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="595e3-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="595e3-180">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="595e3-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="595e3-181">À l’aide de [CentOS 7][], téléchargez le package RPM</span><span class="sxs-lookup"><span data-stu-id="595e3-181">Using [CentOS 7][], download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="595e3-182">à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="595e3-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="595e3-183">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="595e3-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="595e3-184">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="595e3-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="595e3-185">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="595e3-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[<span data-ttu-id="595e3-186">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="595e3-186">CentOS 7</span></span>]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="595e3-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="595e3-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="595e3-188">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="595e3-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="595e3-189">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="595e3-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="595e3-190">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="595e3-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="595e3-191">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="595e3-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="595e3-192">Téléchargez le package RPM</span><span class="sxs-lookup"><span data-stu-id="595e3-192">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="595e3-193">à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="595e3-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="595e3-194">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="595e3-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="595e3-195">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="595e3-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="595e3-196">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="595e3-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="595e3-197">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="595e3-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="595e3-198">Installation – openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="595e3-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="595e3-199">Installation – openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="595e3-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="595e3-200">Désinstallation – openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="595e3-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="595e3-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="595e3-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="595e3-202">Fedora 28 est pris en charge dans PowerShell Core 6.1 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="595e3-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="595e3-203">Installation au moyen d’un référentiel de packages (par défaut) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="595e3-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="595e3-204">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="595e3-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="595e3-205">Installation par téléchargement direct – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="595e3-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="595e3-206">Téléchargez le package RPM</span><span class="sxs-lookup"><span data-stu-id="595e3-206">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="595e3-207">à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="595e3-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="595e3-208">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="595e3-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="595e3-209">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="595e3-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="595e3-210">Désinstallation – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="595e3-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="595e3-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="595e3-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="595e3-212">La prise en charge d’arch est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="595e3-212">Arch support is experimental.</span></span>

<span data-ttu-id="595e3-213">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="595e3-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="595e3-214">Il peut être compilé avec la [dernière version identifiée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="595e3-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="595e3-215">Il peut être compilé à partir de la [dernière validation sur le maître][arch-git]</span><span class="sxs-lookup"><span data-stu-id="595e3-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="595e3-216">Il peut être installé à l’aide de la [dernière ressource binaire de version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="595e3-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="595e3-217">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="595e3-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="595e3-218">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou le [fichier Dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la communauté.</span><span class="sxs-lookup"><span data-stu-id="595e3-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[<span data-ttu-id="595e3-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="595e3-219">Arch Linux</span></span>]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="595e3-220">Snap Package</span><span class="sxs-lookup"><span data-stu-id="595e3-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="595e3-221">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="595e3-221">Getting snapd</span></span>

`snapd` <span data-ttu-id="595e3-222">est obligatoire pour exécuter des instantanés.</span><span class="sxs-lookup"><span data-stu-id="595e3-222">is required to run snaps.</span></span>
<span data-ttu-id="595e3-223">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="595e3-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="595e3-224">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="595e3-224">Installation via Snap</span></span>

<span data-ttu-id="595e3-225">PowerShell Core pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="595e3-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="595e3-226">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="595e3-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="595e3-227">Si vous souhaitez installer la préversion, utilisez la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="595e3-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="595e3-228">La mise à niveau de Snap est automatique après l’installation, mais vous pouvez déclencher une mise à niveau avec `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="595e3-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="595e3-229">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="595e3-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="595e3-230">ou</span><span class="sxs-lookup"><span data-stu-id="595e3-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="595e3-231">Kali</span><span class="sxs-lookup"><span data-stu-id="595e3-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="595e3-232">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="595e3-232">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="595e3-233">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="595e3-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="595e3-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="595e3-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="595e3-235">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="595e3-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="595e3-236">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="595e3-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="595e3-237">De plus, CoreCLR (et donc PowerShell Core) fonctionne uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="595e3-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="595e3-238">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="595e3-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="595e3-239">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="595e3-239">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="595e3-240">Si vous le souhaitez, vous pouvez créer un lien symbolique pour être en mesure de démarrer PowerShell sans spécifier de chemin d’accès au binaire « pwsh »</span><span class="sxs-lookup"><span data-stu-id="595e3-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="595e3-241">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="595e3-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="595e3-242">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="595e3-242">Binary Archives</span></span>

<span data-ttu-id="595e3-243">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="595e3-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="595e3-244">Dépendances</span><span class="sxs-lookup"><span data-stu-id="595e3-244">Dependencies</span></span>

<span data-ttu-id="595e3-245">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="595e3-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="595e3-246">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte par conséquent de la même manière.</span><span class="sxs-lookup"><span data-stu-id="595e3-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="595e3-247">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="595e3-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="595e3-248">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="595e3-248">OS</span></span>                 | <span data-ttu-id="595e3-249">Dépendances</span><span class="sxs-lookup"><span data-stu-id="595e3-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="595e3-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="595e3-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="595e3-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="595e3-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="595e3-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="595e3-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="595e3-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="595e3-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="595e3-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="595e3-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="595e3-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="595e3-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="595e3-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="595e3-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="595e3-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="595e3-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="595e3-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="595e3-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="595e3-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="595e3-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="595e3-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="595e3-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="595e3-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="595e3-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="595e3-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="595e3-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="595e3-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="595e3-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="595e3-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="595e3-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="595e3-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="595e3-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="595e3-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="595e3-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="595e3-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="595e3-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="595e3-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="595e3-268">CentOS 7</span></span> <br> <span data-ttu-id="595e3-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="595e3-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="595e3-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="595e3-270">RHEL 7</span></span> | <span data-ttu-id="595e3-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="595e3-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="595e3-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="595e3-272">openSUSE 42.3</span></span> | <span data-ttu-id="595e3-273">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="595e3-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="595e3-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="595e3-274">openSUSE Leap 15</span></span> | <span data-ttu-id="595e3-275">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="595e3-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="595e3-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="595e3-276">Fedora 27</span></span> <br> <span data-ttu-id="595e3-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="595e3-277">Fedora 28</span></span> | <span data-ttu-id="595e3-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="595e3-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="595e3-279">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="595e3-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="595e3-280">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe tout d’abord les dépendances, puis extrait l’archive `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="595e3-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="595e3-281">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="595e3-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="595e3-282">Linux</span><span class="sxs-lookup"><span data-stu-id="595e3-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="595e3-283">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="595e3-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="595e3-284">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="595e3-284">Paths</span></span>

* `$PSHOME` <span data-ttu-id="595e3-285">est</span><span class="sxs-lookup"><span data-stu-id="595e3-285">is</span></span> `/opt/microsoft/powershell/6.2.0/`
* <span data-ttu-id="595e3-286">Les profils utilisateur sont lus à partir de</span><span class="sxs-lookup"><span data-stu-id="595e3-286">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="595e3-287">Les profils par défaut sont lus à partir de</span><span class="sxs-lookup"><span data-stu-id="595e3-287">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="595e3-288">Les modules utilisateur sont lus à partir de</span><span class="sxs-lookup"><span data-stu-id="595e3-288">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="595e3-289">Les modules partagés sont lus à partir de</span><span class="sxs-lookup"><span data-stu-id="595e3-289">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="595e3-290">Les modules par défaut sont lus à partir de</span><span class="sxs-lookup"><span data-stu-id="595e3-290">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="595e3-291">L’historique PSReadline est enregistré dans</span><span class="sxs-lookup"><span data-stu-id="595e3-291">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="595e3-292">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="595e3-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="595e3-293">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="595e3-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[<span data-ttu-id="595e3-294">versions</span><span class="sxs-lookup"><span data-stu-id="595e3-294">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
