---
title: Installation de PowerShell Core sous Linux
description: Informations sur l’installation de PowerShell Core sur diverses distributions Linux
ms.date: 08/06/2018
ms.openlocfilehash: d60e1d5a89b6907b67c19b8cfcde969be156bd60
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851287"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="d4fa9-103">Installation de PowerShell Core sous Linux</span><span class="sxs-lookup"><span data-stu-id="d4fa9-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="d4fa9-104">Prend en charge [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] et [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="d4fa9-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="d4fa9-105">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’utiliser [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="d4fa9-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="d4fa9-106">Vous pouvez également essayer de déployer des fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires selon le système d’exploitation dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="d4fa9-107">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="d4fa9-108">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="d4fa9-109">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="d4fa9-109">Installing Preview Releases</span></span>

<span data-ttu-id="d4fa9-110">Lorsque vous installez une préversion de PowerShell Core pour Linux via un dépôt de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="d4fa9-111">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="d4fa9-112">Voici un tableau des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="d4fa9-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="d4fa9-113">Distribution(s)</span></span>|<span data-ttu-id="d4fa9-114">Commande stable</span><span class="sxs-lookup"><span data-stu-id="d4fa9-114">Stable Command</span></span> | <span data-ttu-id="d4fa9-115">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="d4fa9-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="d4fa9-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="d4fa9-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="d4fa9-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="d4fa9-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="d4fa9-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="d4fa9-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="d4fa9-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="d4fa9-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="d4fa9-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="d4fa9-121">Installation via un dépôt de packages - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="d4fa9-122">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="d4fa9-123">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-123">This is the preferred method.</span></span>

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

<span data-ttu-id="d4fa9-124">En tant que super utilisateur, inscrivez le référentiel Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="d4fa9-125">Dès lors, il vous suffit d’utiliser `sudo apt-get upgrade powershell` pour mettre à jour l’installation.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="d4fa9-126">Installation par téléchargement direct - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="d4fa9-127">Téléchargez le package Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-127">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="d4fa9-128">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d4fa9-129">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d4fa9-130">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="d4fa9-131">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="d4fa9-132">Désinstallation - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="d4fa9-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="d4fa9-134">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="d4fa9-135">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="d4fa9-136">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-136">This is the preferred method.</span></span>

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

<span data-ttu-id="d4fa9-137">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="d4fa9-138">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="d4fa9-139">Téléchargez le package Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-139">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="d4fa9-140">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d4fa9-141">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d4fa9-142">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="d4fa9-143">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="d4fa9-144">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="d4fa9-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="d4fa9-146">Ajout de la prise en charge d’Ubuntu 18.04 après `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="d4fa9-147">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="d4fa9-148">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="d4fa9-149">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-149">This is the preferred method.</span></span>

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

<span data-ttu-id="d4fa9-150">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="d4fa9-151">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="d4fa9-152">Téléchargez le package Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-152">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="d4fa9-153">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d4fa9-154">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d4fa9-155">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="d4fa9-156">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="d4fa9-157">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="d4fa9-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="d4fa9-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="d4fa9-159">Ajout de la prise en charge d’Ubuntu 18.10 après `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="d4fa9-160">18.10 étant une build quotidienne, elle est uniquement prise en charge par la communauté.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="d4fa9-161">L’installation de 18.10 est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="d4fa9-162">Consultez [Snap Package][snap] pour des instructions complètes.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="d4fa9-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="d4fa9-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="d4fa9-164">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="d4fa9-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="d4fa9-165">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="d4fa9-166">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-166">This is the preferred method.</span></span>

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

<span data-ttu-id="d4fa9-167">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="d4fa9-168">Installation par téléchargement direct - Debian 8</span><span class="sxs-lookup"><span data-stu-id="d4fa9-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="d4fa9-169">Téléchargez le package Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-169">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="d4fa9-170">à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="d4fa9-171">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d4fa9-172">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="d4fa9-173">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="d4fa9-174">Désinstallation - Debian 8</span><span class="sxs-lookup"><span data-stu-id="d4fa9-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="d4fa9-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d4fa9-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="d4fa9-176">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="d4fa9-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="d4fa9-177">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="d4fa9-178">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-178">This is the preferred method.</span></span>

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

<span data-ttu-id="d4fa9-179">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="d4fa9-180">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="d4fa9-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="d4fa9-181">Téléchargez le package Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-181">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="d4fa9-182">à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="d4fa9-183">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="d4fa9-184">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="d4fa9-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="d4fa9-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="d4fa9-186">Ce package fonctionne également sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="d4fa9-187">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="d4fa9-188">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d4fa9-189">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="d4fa9-190">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="d4fa9-191">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-191">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="d4fa9-192">à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="d4fa9-193">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d4fa9-194">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="d4fa9-195">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d4fa9-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d4fa9-198">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d4fa9-199">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d4fa9-200">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d4fa9-201">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d4fa9-202">Téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-202">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="d4fa9-203">à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="d4fa9-204">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d4fa9-205">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d4fa9-206">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="d4fa9-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d4fa9-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="d4fa9-208">Lors de l’installation de PowerShell Core, `zypper` peut signaler l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="d4fa9-209">Dans ce cas, vérifiez qu’une bibliothèque `libcurl` compatible est présente en contrôlant que la commande suivante indique que le package `libcurl4` est installé :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="d4fa9-210">Ensuite, choisissez la solution `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` quand vous installez le package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-210">Then choose the `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="d4fa9-211">Installation via un dépôt de packages (par défaut) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d4fa9-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="d4fa9-212">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="d4fa9-213">Installation par téléchargement direct - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d4fa9-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="d4fa9-214">Téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-214">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d4fa9-215">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="d4fa9-216">Désinstallation - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d4fa9-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="d4fa9-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="d4fa9-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="d4fa9-218">Fedora 28 est pris en charge dans PowerShell Core 6.1 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="d4fa9-219">Installation au moyen d’un référentiel de packages (par défaut) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d4fa9-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="d4fa9-220">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="d4fa9-221">Installation par téléchargement direct – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d4fa9-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="d4fa9-222">Téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-222">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="d4fa9-223">à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="d4fa9-224">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d4fa9-225">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="d4fa9-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="d4fa9-226">Désinstallation – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d4fa9-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="d4fa9-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="d4fa9-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="d4fa9-228">La prise en charge d’arch est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-228">Arch support is experimental.</span></span>

<span data-ttu-id="d4fa9-229">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="d4fa9-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="d4fa9-230">Il peut être compilé avec la [dernière version identifiée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="d4fa9-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="d4fa9-231">Il peut être compilé à partir de la [dernière validation sur le maître][arch-git]</span><span class="sxs-lookup"><span data-stu-id="d4fa9-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="d4fa9-232">Il peut être installé à l’aide de la [dernière ressource binaire de version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="d4fa9-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="d4fa9-233">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="d4fa9-234">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou le [fichier Dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la communauté.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="d4fa9-236">Snap Package</span><span class="sxs-lookup"><span data-stu-id="d4fa9-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="d4fa9-237">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="d4fa9-237">Getting snapd</span></span>

<span data-ttu-id="d4fa9-238">`snapd` est obligatoire pour exécuter des snaps.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-238">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="d4fa9-239">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="d4fa9-240">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="d4fa9-240">Installation via Snap</span></span>

<span data-ttu-id="d4fa9-241">PowerShell Core pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="d4fa9-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="d4fa9-242">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="d4fa9-243">Une fois Snap installé, la mise à niveau est automatique, mais vous pouvez déclencher une mise à niveau à l’aide de `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="d4fa9-244">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="d4fa9-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="d4fa9-245">Kali</span><span class="sxs-lookup"><span data-stu-id="d4fa9-245">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="d4fa9-246">Installation</span><span class="sxs-lookup"><span data-stu-id="d4fa9-246">Installation</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="d4fa9-247">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="d4fa9-247">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="d4fa9-248">Raspbian</span><span class="sxs-lookup"><span data-stu-id="d4fa9-248">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="d4fa9-249">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-249">Raspbian support is experimental.</span></span>

<span data-ttu-id="d4fa9-250">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-250">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="d4fa9-251">De plus, CoreCLR (et donc PowerShell Core) fonctionne uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-251">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="d4fa9-252">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-252">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="d4fa9-253">Installation</span><span class="sxs-lookup"><span data-stu-id="d4fa9-253">Installation</span></span>

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

<span data-ttu-id="d4fa9-254">Si vous le souhaitez, vous pouvez créer un lien symbolique pour être en mesure de démarrer PowerShell sans spécifier de chemin d’accès au binaire « pwsh »</span><span class="sxs-lookup"><span data-stu-id="d4fa9-254">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="d4fa9-255">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="d4fa9-255">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="d4fa9-256">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="d4fa9-256">Binary Archives</span></span>

<span data-ttu-id="d4fa9-257">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-257">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="d4fa9-258">Dépendances</span><span class="sxs-lookup"><span data-stu-id="d4fa9-258">Dependencies</span></span>

<span data-ttu-id="d4fa9-259">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-259">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="d4fa9-260">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte par conséquent de la même manière.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-260">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="d4fa9-261">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-261">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="d4fa9-262">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="d4fa9-262">OS</span></span>                 | <span data-ttu-id="d4fa9-263">Dépendances</span><span class="sxs-lookup"><span data-stu-id="d4fa9-263">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="d4fa9-264">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-264">Ubuntu 14.04</span></span>       | <span data-ttu-id="d4fa9-265">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d4fa9-265">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d4fa9-266">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="d4fa9-266">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="d4fa9-267">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-267">Ubuntu 16.04</span></span>       | <span data-ttu-id="d4fa9-268">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d4fa9-268">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d4fa9-269">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="d4fa9-269">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="d4fa9-270">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="d4fa9-270">Ubuntu 17.10</span></span>       | <span data-ttu-id="d4fa9-271">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d4fa9-271">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d4fa9-272">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="d4fa9-272">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="d4fa9-273">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d4fa9-273">Ubuntu 18.04</span></span>       | <span data-ttu-id="d4fa9-274">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d4fa9-274">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d4fa9-275">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="d4fa9-275">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="d4fa9-276">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="d4fa9-276">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="d4fa9-277">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d4fa9-277">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d4fa9-278">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="d4fa9-278">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="d4fa9-279">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="d4fa9-279">Debian 9 (Stretch)</span></span> | <span data-ttu-id="d4fa9-280">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="d4fa9-280">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d4fa9-281">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="d4fa9-281">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="d4fa9-282">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-282">CentOS 7</span></span> <br> <span data-ttu-id="d4fa9-283">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-283">Oracle Linux 7</span></span> <br> <span data-ttu-id="d4fa9-284">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="d4fa9-284">RHEL 7</span></span> <br> <span data-ttu-id="d4fa9-285">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d4fa9-285">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="d4fa9-286">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="d4fa9-286">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="d4fa9-287">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="d4fa9-287">Fedora 27</span></span> <br> <span data-ttu-id="d4fa9-288">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d4fa9-288">Fedora 28</span></span> | <span data-ttu-id="d4fa9-289">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="d4fa9-289">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="d4fa9-290">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-290">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="d4fa9-291">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe tout d’abord les dépendances, puis extrait l’archive `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-291">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="d4fa9-292">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="d4fa9-292">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="d4fa9-293">Linux</span><span class="sxs-lookup"><span data-stu-id="d4fa9-293">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="d4fa9-294">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="d4fa9-294">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="d4fa9-295">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="d4fa9-295">Paths</span></span>

* <span data-ttu-id="d4fa9-296">`$PSHOME` est `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-296">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="d4fa9-297">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-297">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="d4fa9-298">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-298">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="d4fa9-299">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-299">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="d4fa9-300">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-300">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="d4fa9-301">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-301">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="d4fa9-302">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="d4fa9-302">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="d4fa9-303">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-303">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="d4fa9-304">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="d4fa9-304">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
