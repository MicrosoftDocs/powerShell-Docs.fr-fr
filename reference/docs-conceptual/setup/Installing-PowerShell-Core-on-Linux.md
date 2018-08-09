---
title: Installation de PowerShell Core sous Linux
description: Informations sur l’installation de PowerShell Core sur diverses distributions Linux
ms.date: 08/06/2018
ms.openlocfilehash: a6b0e3003f84ea6dc99cffcc7edf1b5b6963aa21
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587446"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="4e99b-103">Installation de PowerShell Core sous Linux</span><span class="sxs-lookup"><span data-stu-id="4e99b-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="4e99b-104">Prend en charge [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] et [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="4e99b-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="4e99b-105">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’utiliser [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="4e99b-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="4e99b-106">Vous pouvez également essayer de déployer des fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires selon le système d’exploitation dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="4e99b-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="4e99b-107">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="4e99b-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="4e99b-108">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="4e99b-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="4e99b-109">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="4e99b-109">Installing Preview Releases</span></span>

<span data-ttu-id="4e99b-110">Lorsque vous installez une préversion de PowerShell Core pour Linux via un dépôt de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="4e99b-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="4e99b-111">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="4e99b-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="4e99b-112">Voici un tableau des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="4e99b-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="4e99b-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="4e99b-113">Distribution(s)</span></span>|<span data-ttu-id="4e99b-114">Commande stable</span><span class="sxs-lookup"><span data-stu-id="4e99b-114">Stable Command</span></span> | <span data-ttu-id="4e99b-115">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="4e99b-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="4e99b-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="4e99b-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="4e99b-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="4e99b-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="4e99b-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="4e99b-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="4e99b-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="4e99b-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="4e99b-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="4e99b-121">Installation via un dépôt de packages - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="4e99b-122">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4e99b-123">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="4e99b-123">This is the preferred method.</span></span>

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

<span data-ttu-id="4e99b-124">En tant que super utilisateur, inscrivez le référentiel Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4e99b-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="4e99b-125">Dès lors, il vous suffit d’utiliser `sudo apt-get upgrade powershell` pour mettre à jour l’installation.</span><span class="sxs-lookup"><span data-stu-id="4e99b-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="4e99b-126">Installation par téléchargement direct - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="4e99b-127">Téléchargez le package Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4e99b-127">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4e99b-128">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4e99b-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4e99b-129">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="4e99b-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="4e99b-130">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e99b-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="4e99b-131">Désinstallation - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="4e99b-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="4e99b-133">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="4e99b-134">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4e99b-135">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="4e99b-135">This is the preferred method.</span></span>

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

<span data-ttu-id="4e99b-136">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="4e99b-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="4e99b-137">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="4e99b-138">Téléchargez le package Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4e99b-138">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4e99b-139">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4e99b-139">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4e99b-140">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="4e99b-140">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="4e99b-141">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e99b-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="4e99b-142">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-142">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="4e99b-143">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-143">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="4e99b-144">Ajout de la prise en charge d’Ubuntu 18.04 après `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="4e99b-144">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="4e99b-145">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="4e99b-146">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4e99b-147">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="4e99b-147">This is the preferred method.</span></span>

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

<span data-ttu-id="4e99b-148">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="4e99b-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="4e99b-149">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="4e99b-150">Téléchargez le package Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4e99b-150">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4e99b-151">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4e99b-151">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4e99b-152">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="4e99b-152">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="4e99b-153">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e99b-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="4e99b-154">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-154">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="4e99b-155">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="4e99b-155">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="4e99b-156">Ajout de la prise en charge d’Ubuntu 18.10 après `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="4e99b-156">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="4e99b-157">18.10 étant une build quotidienne, elle est uniquement prise en charge par la communauté.</span><span class="sxs-lookup"><span data-stu-id="4e99b-157">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="4e99b-158">L’installation de 18.10 est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="4e99b-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="4e99b-159">Consultez [Snap Package][snap] pour des instructions complètes.</span><span class="sxs-lookup"><span data-stu-id="4e99b-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="4e99b-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="4e99b-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="4e99b-161">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="4e99b-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="4e99b-162">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4e99b-163">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="4e99b-163">This is the preferred method.</span></span>

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

<span data-ttu-id="4e99b-164">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="4e99b-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="4e99b-165">Installation par téléchargement direct - Debian 8</span><span class="sxs-lookup"><span data-stu-id="4e99b-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="4e99b-166">Téléchargez le package Debian `powershell_6.0.2-1.debian.8_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="4e99b-166">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="4e99b-167">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4e99b-167">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4e99b-168">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="4e99b-168">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="4e99b-169">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e99b-169">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="4e99b-170">Désinstallation - Debian 8</span><span class="sxs-lookup"><span data-stu-id="4e99b-170">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="4e99b-171">Debian 9</span><span class="sxs-lookup"><span data-stu-id="4e99b-171">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="4e99b-172">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="4e99b-172">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="4e99b-173">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-173">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4e99b-174">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="4e99b-174">This is the preferred method.</span></span>

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

<span data-ttu-id="4e99b-175">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="4e99b-175">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="4e99b-176">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="4e99b-176">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="4e99b-177">Téléchargez le package Debian `powershell_6.0.2-1.debian.9_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="4e99b-177">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="4e99b-178">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4e99b-178">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="4e99b-179">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="4e99b-179">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="4e99b-180">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-180">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="4e99b-181">Ce package fonctionne également sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="4e99b-181">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="4e99b-182">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-182">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="4e99b-183">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-183">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="4e99b-184">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e99b-184">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="4e99b-185">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="4e99b-186">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="4e99b-186">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="4e99b-187">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4e99b-187">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4e99b-188">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="4e99b-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="4e99b-189">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4e99b-191">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4e99b-192">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="4e99b-193">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="4e99b-194">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e99b-194">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4e99b-195">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="4e99b-196">Téléchargez le package RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="4e99b-196">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="4e99b-197">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4e99b-197">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4e99b-198">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="4e99b-198">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4e99b-199">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="4e99b-200">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="4e99b-200">OpenSUSE 42.3</span></span>

<span data-ttu-id="4e99b-201">Lors de l’installation de PowerShell Core, `zypper` peut signaler l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="4e99b-201">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="4e99b-202">Dans ce cas, vérifiez qu’une bibliothèque `libcurl` compatible est présente en contrôlant que la commande suivante indique que le package `libcurl4` est installé :</span><span class="sxs-lookup"><span data-stu-id="4e99b-202">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="4e99b-203">Ensuite, choisissez la solution `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` quand vous installez le package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e99b-203">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="4e99b-204">Installation via un dépôt de packages (par défaut) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="4e99b-204">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="4e99b-205">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-205">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="4e99b-206">Installation par téléchargement direct - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="4e99b-206">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="4e99b-207">Téléchargez le package RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="4e99b-207">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4e99b-208">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="4e99b-208">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="4e99b-209">Désinstallation - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="4e99b-209">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="4e99b-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="4e99b-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="4e99b-211">Fedora 28 est pris en charge dans PowerShell Core 6.1 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="4e99b-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="4e99b-212">Installation au moyen d’un référentiel de packages (par défaut) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="4e99b-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="4e99b-213">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="4e99b-214">Installation par téléchargement direct – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="4e99b-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="4e99b-215">Téléchargez le package RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="4e99b-215">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="4e99b-216">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4e99b-216">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4e99b-217">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="4e99b-217">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="4e99b-218">Désinstallation – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="4e99b-218">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="4e99b-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="4e99b-219">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="4e99b-220">La prise en charge d’arch est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="4e99b-220">Arch support is experimental.</span></span>

<span data-ttu-id="4e99b-221">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="4e99b-221">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="4e99b-222">Il peut être compilé avec la [dernière version identifiée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="4e99b-222">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="4e99b-223">Il peut être compilé à partir de la [dernière validation sur le maître][arch-git]</span><span class="sxs-lookup"><span data-stu-id="4e99b-223">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="4e99b-224">Il peut être installé à l’aide de la [dernière ressource binaire de version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="4e99b-224">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="4e99b-225">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="4e99b-225">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="4e99b-226">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou le [fichier Dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la communauté.</span><span class="sxs-lookup"><span data-stu-id="4e99b-226">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="4e99b-228">Snap Package</span><span class="sxs-lookup"><span data-stu-id="4e99b-228">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="4e99b-229">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="4e99b-229">Getting snapd</span></span>

<span data-ttu-id="4e99b-230">`snapd` est obligatoire pour exécuter des snaps.</span><span class="sxs-lookup"><span data-stu-id="4e99b-230">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="4e99b-231">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="4e99b-231">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="4e99b-232">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="4e99b-232">Installation via Snap</span></span>

<span data-ttu-id="4e99b-233">PowerShell Core pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="4e99b-233">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="4e99b-234">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="4e99b-234">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="4e99b-235">Une fois Snap installé, la mise à niveau est automatique, mais vous pouvez déclencher une mise à niveau à l’aide de `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="4e99b-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="4e99b-236">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="4e99b-236">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="4e99b-237">AppImage Linux</span><span class="sxs-lookup"><span data-stu-id="4e99b-237">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="4e99b-238">La prise en charge d’AppImage est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="4e99b-238">AppImage support is experimental</span></span>

<span data-ttu-id="4e99b-239">En utilisant une distribution Linux récente, téléchargez AppImage `powershell-6.0.1-x86_64.AppImage` à partir de la page de [versions][] sur l’ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="4e99b-239">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="4e99b-240">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="4e99b-240">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="4e99b-241">[AppImage][] vous permet d’exécuter PowerShell sans l’installer.</span><span class="sxs-lookup"><span data-stu-id="4e99b-241">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="4e99b-242">Il s’agit d’une application portable qui regroupe PowerShell et ses dépendances (dont les dépendances système de .NET Core) en un package cohérent.</span><span class="sxs-lookup"><span data-stu-id="4e99b-242">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="4e99b-243">Ce package est un fichier binaire unique qui fonctionne indépendamment de la distribution Linux de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4e99b-243">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="4e99b-245">Kali</span><span class="sxs-lookup"><span data-stu-id="4e99b-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="4e99b-246">La prise en charge de Kali est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="4e99b-246">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="4e99b-247">Installation</span><span class="sxs-lookup"><span data-stu-id="4e99b-247">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="4e99b-248">Exécuter PowerShell dans la dernière version de Kali (publication en continu Kali GNU/Linux) sans l’installer</span><span class="sxs-lookup"><span data-stu-id="4e99b-248">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="4e99b-249">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="4e99b-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="4e99b-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="4e99b-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="4e99b-251">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="4e99b-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="4e99b-252">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="4e99b-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="4e99b-253">De plus, CoreCLR (et donc PowerShell Core) fonctionne uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4e99b-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="4e99b-254">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="4e99b-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="4e99b-255">Installation</span><span class="sxs-lookup"><span data-stu-id="4e99b-255">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="4e99b-256">Si vous le souhaitez, vous pouvez créer un lien symbolique pour être en mesure de démarrer PowerShell sans spécifier de chemin d’accès au binaire « pwsh »</span><span class="sxs-lookup"><span data-stu-id="4e99b-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="4e99b-257">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="4e99b-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="4e99b-258">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="4e99b-258">Binary Archives</span></span>

<span data-ttu-id="4e99b-259">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="4e99b-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="4e99b-260">Dépendances</span><span class="sxs-lookup"><span data-stu-id="4e99b-260">Dependencies</span></span>

<span data-ttu-id="4e99b-261">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="4e99b-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="4e99b-262">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte par conséquent de la même manière.</span><span class="sxs-lookup"><span data-stu-id="4e99b-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="4e99b-263">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="4e99b-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="4e99b-264">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="4e99b-264">OS</span></span>                 | <span data-ttu-id="4e99b-265">Dépendances</span><span class="sxs-lookup"><span data-stu-id="4e99b-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="4e99b-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="4e99b-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="4e99b-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4e99b-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="4e99b-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="4e99b-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="4e99b-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="4e99b-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4e99b-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="4e99b-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="4e99b-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="4e99b-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="4e99b-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="4e99b-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4e99b-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="4e99b-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="4e99b-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="4e99b-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="4e99b-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="4e99b-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4e99b-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="4e99b-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="4e99b-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="4e99b-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="4e99b-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="4e99b-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4e99b-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="4e99b-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="4e99b-281">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="4e99b-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="4e99b-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="4e99b-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4e99b-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="4e99b-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="4e99b-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-284">CentOS 7</span></span> <br> <span data-ttu-id="4e99b-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="4e99b-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="4e99b-286">RHEL 7</span></span> <br> <span data-ttu-id="4e99b-287">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="4e99b-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="4e99b-288">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="4e99b-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="4e99b-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="4e99b-289">Fedora 27</span></span> <br> <span data-ttu-id="4e99b-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="4e99b-290">Fedora 28</span></span> | <span data-ttu-id="4e99b-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="4e99b-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="4e99b-292">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="4e99b-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="4e99b-293">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe tout d’abord les dépendances, puis extrait l’archive `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="4e99b-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="4e99b-294">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="4e99b-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="4e99b-295">Linux</span><span class="sxs-lookup"><span data-stu-id="4e99b-295">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="4e99b-296">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="4e99b-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="4e99b-297">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="4e99b-297">Paths</span></span>

* <span data-ttu-id="4e99b-298">`$PSHOME` est `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="4e99b-298">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="4e99b-299">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4e99b-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="4e99b-300">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4e99b-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="4e99b-301">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4e99b-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4e99b-302">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4e99b-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4e99b-303">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="4e99b-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="4e99b-304">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="4e99b-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="4e99b-305">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="4e99b-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="4e99b-306">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="4e99b-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
