---
title: Installation de PowerShell Core sous Linux
description: Informations sur l’installation de PowerShell Core sur diverses distributions Linux
ms.date: 08/06/2018
ms.openlocfilehash: 0a1f30ef75a0feeb97df9a35a08d6b0d3edaeccf
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133144"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="cb566-103">Installation de PowerShell Core sous Linux</span><span class="sxs-lookup"><span data-stu-id="cb566-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="cb566-104">Prend en charge [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] et [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="cb566-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="cb566-105">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’utiliser [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="cb566-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="cb566-106">Vous pouvez également essayer de déployer des fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires selon le système d’exploitation dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="cb566-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="cb566-107">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="cb566-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="cb566-108">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="cb566-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="cb566-109">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="cb566-109">Installing Preview Releases</span></span>

<span data-ttu-id="cb566-110">Lorsque vous installez une préversion de PowerShell Core pour Linux via un dépôt de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="cb566-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="cb566-111">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="cb566-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="cb566-112">Voici un tableau des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="cb566-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="cb566-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="cb566-113">Distribution(s)</span></span>|<span data-ttu-id="cb566-114">Commande stable</span><span class="sxs-lookup"><span data-stu-id="cb566-114">Stable Command</span></span> | <span data-ttu-id="cb566-115">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="cb566-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="cb566-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="cb566-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="cb566-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="cb566-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="cb566-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="cb566-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="cb566-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="cb566-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="cb566-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb566-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="cb566-121">Installation via un dépôt de packages - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb566-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="cb566-122">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb566-123">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="cb566-123">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cb566-124">En tant que super utilisateur, inscrivez le référentiel Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cb566-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="cb566-125">Dès lors, il vous suffit d’utiliser `sudo apt-get upgrade powershell` pour mettre à jour l’installation.</span><span class="sxs-lookup"><span data-stu-id="cb566-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="cb566-126">Installation par téléchargement direct - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb566-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="cb566-127">Téléchargez le package Debian `powershell_6.0.3-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cb566-127">Download the Debian package `powershell_6.0.3-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="cb566-128">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cb566-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cb566-129">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="cb566-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cb566-130">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="cb566-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="cb566-131">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb566-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="cb566-132">Désinstallation - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb566-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="cb566-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb566-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="cb566-134">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb566-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="cb566-135">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb566-136">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="cb566-136">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cb566-137">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="cb566-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="cb566-138">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb566-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="cb566-139">Téléchargez le package Debian `powershell_6.0.3-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cb566-139">Download the Debian package `powershell_6.0.3-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="cb566-140">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cb566-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cb566-141">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="cb566-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cb566-142">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="cb566-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="cb566-143">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb566-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="cb566-144">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb566-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="cb566-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cb566-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="cb566-146">Ajout de la prise en charge d’Ubuntu 18.04 après `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="cb566-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="cb566-147">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cb566-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="cb566-148">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb566-149">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="cb566-149">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="cb566-150">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="cb566-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="cb566-151">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cb566-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="cb566-152">Téléchargez le package Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cb566-152">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="cb566-153">à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cb566-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cb566-154">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="cb566-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cb566-155">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="cb566-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="cb566-156">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb566-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="cb566-157">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cb566-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="cb566-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="cb566-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="cb566-159">Ajout de la prise en charge d’Ubuntu 18.10 après `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="cb566-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="cb566-160">18.10 étant une build quotidienne, elle est uniquement prise en charge par la communauté.</span><span class="sxs-lookup"><span data-stu-id="cb566-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="cb566-161">L’installation de 18.10 est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="cb566-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="cb566-162">Consultez [Snap Package][snap] pour des instructions complètes.</span><span class="sxs-lookup"><span data-stu-id="cb566-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="cb566-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="cb566-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="cb566-164">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="cb566-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="cb566-165">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb566-166">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="cb566-166">This is the preferred method.</span></span>

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

<span data-ttu-id="cb566-167">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="cb566-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="cb566-168">Installation par téléchargement direct - Debian 8</span><span class="sxs-lookup"><span data-stu-id="cb566-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="cb566-169">Téléchargez le package Debian `powershell_6.0.3-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cb566-169">Download the Debian package `powershell_6.0.3-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="cb566-170">à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="cb566-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cb566-171">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="cb566-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cb566-172">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="cb566-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="cb566-173">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb566-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="cb566-174">Désinstallation - Debian 8</span><span class="sxs-lookup"><span data-stu-id="cb566-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="cb566-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="cb566-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="cb566-176">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="cb566-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="cb566-177">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cb566-178">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="cb566-178">This is the preferred method.</span></span>

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

<span data-ttu-id="cb566-179">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="cb566-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="cb566-180">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="cb566-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="cb566-181">Téléchargez le package Debian `powershell_6.0.3-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cb566-181">Download the Debian package `powershell_6.0.3-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="cb566-182">à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="cb566-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cb566-183">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="cb566-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="cb566-184">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="cb566-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="cb566-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb566-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="cb566-186">Ce package fonctionne également sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="cb566-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="cb566-187">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb566-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="cb566-188">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cb566-189">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb566-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="cb566-190">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb566-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="cb566-191">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="cb566-191">Using [CentOS 7][], download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="cb566-192">à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="cb566-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="cb566-193">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="cb566-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cb566-194">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="cb566-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="cb566-195">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb566-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cb566-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cb566-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cb566-198">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cb566-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cb566-199">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cb566-200">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb566-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cb566-201">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cb566-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cb566-202">Téléchargez le package RPM `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="cb566-202">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="cb566-203">à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="cb566-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="cb566-204">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="cb566-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cb566-205">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="cb566-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cb566-206">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cb566-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="cb566-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="cb566-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="cb566-208">Lors de l’installation de PowerShell Core, `zypper` peut signaler l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="cb566-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="cb566-209">Dans ce cas, vérifiez qu’une bibliothèque `libcurl` compatible est présente en contrôlant que la commande suivante indique que le package `libcurl4` est installé :</span><span class="sxs-lookup"><span data-stu-id="cb566-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="cb566-210">Ensuite, choisissez la solution `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` quand vous installez le package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb566-210">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="cb566-211">Installation via un dépôt de packages (par défaut) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="cb566-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="cb566-212">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="cb566-213">Installation par téléchargement direct - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="cb566-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="cb566-214">Téléchargez le package RPM `powershell-6.0.3-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="cb566-214">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cb566-215">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="cb566-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="cb566-216">Désinstallation - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="cb566-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="cb566-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="cb566-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="cb566-218">Fedora 28 est pris en charge dans PowerShell Core 6.1 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="cb566-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="cb566-219">Installation au moyen d’un référentiel de packages (par défaut) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cb566-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="cb566-220">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="cb566-221">Installation par téléchargement direct – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cb566-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="cb566-222">Téléchargez le package RPM `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="cb566-222">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="cb566-223">à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="cb566-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="cb566-224">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="cb566-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cb566-225">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="cb566-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="cb566-226">Désinstallation – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cb566-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="cb566-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="cb566-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="cb566-228">La prise en charge d’arch est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="cb566-228">Arch support is experimental.</span></span>

<span data-ttu-id="cb566-229">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="cb566-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="cb566-230">Il peut être compilé avec la [dernière version identifiée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="cb566-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="cb566-231">Il peut être compilé à partir de la [dernière validation sur le maître][arch-git]</span><span class="sxs-lookup"><span data-stu-id="cb566-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="cb566-232">Il peut être installé à l’aide de la [dernière ressource binaire de version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="cb566-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="cb566-233">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="cb566-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="cb566-234">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou le [fichier Dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la communauté.</span><span class="sxs-lookup"><span data-stu-id="cb566-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="cb566-236">Snap Package</span><span class="sxs-lookup"><span data-stu-id="cb566-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="cb566-237">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="cb566-237">Getting snapd</span></span>

<span data-ttu-id="cb566-238">`snapd` est obligatoire pour exécuter des snaps.</span><span class="sxs-lookup"><span data-stu-id="cb566-238">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="cb566-239">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="cb566-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="cb566-240">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="cb566-240">Installation via Snap</span></span>

<span data-ttu-id="cb566-241">PowerShell Core pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="cb566-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="cb566-242">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="cb566-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="cb566-243">Une fois Snap installé, la mise à niveau est automatique, mais vous pouvez déclencher une mise à niveau à l’aide de `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="cb566-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="cb566-244">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="cb566-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="cb566-245">AppImage Linux</span><span class="sxs-lookup"><span data-stu-id="cb566-245">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="cb566-246">La prise en charge d’AppImage est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="cb566-246">AppImage support is experimental</span></span>

<span data-ttu-id="cb566-247">En utilisant une distribution Linux récente, téléchargez AppImage `powershell-6.0.1-x86_64.AppImage` à partir de la page de [versions][] sur l’ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="cb566-247">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="cb566-248">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="cb566-248">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="cb566-249">[AppImage][] vous permet d’exécuter PowerShell sans l’installer.</span><span class="sxs-lookup"><span data-stu-id="cb566-249">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="cb566-250">Il s’agit d’une application portable qui regroupe PowerShell et ses dépendances (dont les dépendances système de .NET Core) en un package cohérent.</span><span class="sxs-lookup"><span data-stu-id="cb566-250">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="cb566-251">Ce package est un fichier binaire unique qui fonctionne indépendamment de la distribution Linux de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cb566-251">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="cb566-253">Kali</span><span class="sxs-lookup"><span data-stu-id="cb566-253">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="cb566-254">La prise en charge de Kali est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="cb566-254">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="cb566-255">Installation</span><span class="sxs-lookup"><span data-stu-id="cb566-255">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.3-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="cb566-256">Exécuter PowerShell dans la dernière version de Kali (publication en continu Kali GNU/Linux) sans l’installer</span><span class="sxs-lookup"><span data-stu-id="cb566-256">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="cb566-257">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="cb566-257">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="cb566-258">Raspbian</span><span class="sxs-lookup"><span data-stu-id="cb566-258">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="cb566-259">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="cb566-259">Raspbian support is experimental.</span></span>

<span data-ttu-id="cb566-260">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="cb566-260">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="cb566-261">De plus, CoreCLR (et donc PowerShell Core) fonctionne uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cb566-261">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="cb566-262">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="cb566-262">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="cb566-263">Installation</span><span class="sxs-lookup"><span data-stu-id="cb566-263">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.3-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="cb566-264">Si vous le souhaitez, vous pouvez créer un lien symbolique pour être en mesure de démarrer PowerShell sans spécifier de chemin d’accès au binaire « pwsh »</span><span class="sxs-lookup"><span data-stu-id="cb566-264">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="cb566-265">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="cb566-265">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="cb566-266">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="cb566-266">Binary Archives</span></span>

<span data-ttu-id="cb566-267">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="cb566-267">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="cb566-268">Dépendances</span><span class="sxs-lookup"><span data-stu-id="cb566-268">Dependencies</span></span>

<span data-ttu-id="cb566-269">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="cb566-269">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="cb566-270">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte par conséquent de la même manière.</span><span class="sxs-lookup"><span data-stu-id="cb566-270">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="cb566-271">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="cb566-271">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="cb566-272">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="cb566-272">OS</span></span>                 | <span data-ttu-id="cb566-273">Dépendances</span><span class="sxs-lookup"><span data-stu-id="cb566-273">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="cb566-274">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cb566-274">Ubuntu 14.04</span></span>       | <span data-ttu-id="cb566-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb566-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb566-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="cb566-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="cb566-277">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cb566-277">Ubuntu 16.04</span></span>       | <span data-ttu-id="cb566-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb566-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb566-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="cb566-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="cb566-280">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="cb566-280">Ubuntu 17.10</span></span>       | <span data-ttu-id="cb566-281">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb566-281">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb566-282">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="cb566-282">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="cb566-283">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cb566-283">Ubuntu 18.04</span></span>       | <span data-ttu-id="cb566-284">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb566-284">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb566-285">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="cb566-285">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="cb566-286">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="cb566-286">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="cb566-287">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb566-287">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb566-288">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="cb566-288">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="cb566-289">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="cb566-289">Debian 9 (Stretch)</span></span> | <span data-ttu-id="cb566-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cb566-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cb566-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="cb566-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="cb566-292">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb566-292">CentOS 7</span></span> <br> <span data-ttu-id="cb566-293">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="cb566-293">Oracle Linux 7</span></span> <br> <span data-ttu-id="cb566-294">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="cb566-294">RHEL 7</span></span> <br> <span data-ttu-id="cb566-295">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="cb566-295">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="cb566-296">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="cb566-296">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="cb566-297">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="cb566-297">Fedora 27</span></span> <br> <span data-ttu-id="cb566-298">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cb566-298">Fedora 28</span></span> | <span data-ttu-id="cb566-299">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="cb566-299">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="cb566-300">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="cb566-300">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="cb566-301">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe tout d’abord les dépendances, puis extrait l’archive `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="cb566-301">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="cb566-302">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="cb566-302">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="cb566-303">Linux</span><span class="sxs-lookup"><span data-stu-id="cb566-303">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="cb566-304">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="cb566-304">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="cb566-305">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="cb566-305">Paths</span></span>

* <span data-ttu-id="cb566-306">`$PSHOME` est `/opt/microsoft/powershell/6.0.3/`</span><span class="sxs-lookup"><span data-stu-id="cb566-306">`$PSHOME` is `/opt/microsoft/powershell/6.0.3/`</span></span>
* <span data-ttu-id="cb566-307">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="cb566-307">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="cb566-308">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="cb566-308">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="cb566-309">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="cb566-309">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cb566-310">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="cb566-310">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cb566-311">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="cb566-311">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="cb566-312">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="cb566-312">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="cb566-313">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="cb566-313">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="cb566-314">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="cb566-314">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
