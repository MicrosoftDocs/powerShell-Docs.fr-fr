---
title: Installation de PowerShell sur Linux
description: Informations sur l’installation de PowerShell sur différentes distributions Linux
ms.date: 07/30/2020
ms.openlocfilehash: ce69f75416eb326e38d42991a4ae85a3a7298c5d
ms.sourcegitcommit: 79d430fe48ad77a058f42b6bc9955d21b657987e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87441769"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="ceb08-103">Installation de PowerShell sur Linux</span><span class="sxs-lookup"><span data-stu-id="ceb08-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="ceb08-104">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="ceb08-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="ceb08-105">Une fois le package installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="ceb08-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="ceb08-106">Exécutez `pwsh-preview` si vous avez installé une [préversion](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="ceb08-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-107">PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="ceb08-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="ceb08-108">Le dossier `/usr/local/microsoft/powershell/6` est remplacé par `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="ceb08-109">Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [Archive binaire](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="ceb08-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="ceb08-110">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’installer PowerShell avec [PowerShell Snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="ceb08-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="ceb08-111">Vous pouvez également essayer de déployer les fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires en fonction du système d’exploitation dans des étapes distinctes.</span><span class="sxs-lookup"><span data-stu-id="ceb08-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="ceb08-112">Mises en production officiellement prises en charge</span><span class="sxs-lookup"><span data-stu-id="ceb08-112">Officially supported releases</span></span>

- <span data-ttu-id="ceb08-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="ceb08-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="ceb08-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="ceb08-115">Debian 8</span></span>
- <span data-ttu-id="ceb08-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="ceb08-116">Debian 9</span></span>
- <span data-ttu-id="ceb08-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="ceb08-117">Debian 10</span></span>
- <span data-ttu-id="ceb08-118">Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="ceb08-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="ceb08-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-119">CentOS 7</span></span>
- <span data-ttu-id="ceb08-120">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="ceb08-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ceb08-121">Fedora 28</span></span>
- <span data-ttu-id="ceb08-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="ceb08-122">Fedora 29</span></span>
- <span data-ttu-id="ceb08-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="ceb08-123">Fedora 30</span></span>
- <span data-ttu-id="ceb08-124">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ceb08-124">openSUSE 42.3</span></span>
- <span data-ttu-id="ceb08-125">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ceb08-125">openSUSE Leap 15</span></span>

<span data-ttu-id="ceb08-126">Mises en production prises en charge par la communauté</span><span class="sxs-lookup"><span data-stu-id="ceb08-126">Community supported releases</span></span>

- <span data-ttu-id="ceb08-127">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="ceb08-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="ceb08-128">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="ceb08-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="ceb08-129">Arch Linux</span></span>
- <span data-ttu-id="ceb08-130">Kali</span><span class="sxs-lookup"><span data-stu-id="ceb08-130">Kali</span></span>
- <span data-ttu-id="ceb08-131">Raspbian (expérimental)</span><span class="sxs-lookup"><span data-stu-id="ceb08-131">Raspbian (experimental)</span></span>

<span data-ttu-id="ceb08-132">Autres méthodes d’installation</span><span class="sxs-lookup"><span data-stu-id="ceb08-132">Alternate install methods</span></span>

- <span data-ttu-id="ceb08-133">Snap Package</span><span class="sxs-lookup"><span data-stu-id="ceb08-133">Snap Package</span></span>
- <span data-ttu-id="ceb08-134">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="ceb08-134">Binary Archives</span></span>
- <span data-ttu-id="ceb08-135">Outil .NET Global</span><span class="sxs-lookup"><span data-stu-id="ceb08-135">.NET Global tool</span></span>

<span data-ttu-id="ceb08-136">Non prise en charge pour le moment</span><span class="sxs-lookup"><span data-stu-id="ceb08-136">Not currently supported</span></span>

- <span data-ttu-id="ceb08-137">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-137">Ubuntu 20.04</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-138">PowerShell peut uniquement prendre en charge les distributions prises en charge par .NET.</span><span class="sxs-lookup"><span data-stu-id="ceb08-138">PowerShell can only support the distributions that are supported by .NET.</span></span> <span data-ttu-id="ceb08-139">Pour obtenir la liste des distributions prises en charge, consultez les [notes de publication de .NET Core][distros].</span><span class="sxs-lookup"><span data-stu-id="ceb08-139">See the [.NET Core release notes][distros] for a list of supported distributions.</span></span> <span data-ttu-id="ceb08-140">Si une distribution prise en charge par .NET n’y est pas listée, vous pouvez demander à ce qu’elle soit ajoutée.</span><span class="sxs-lookup"><span data-stu-id="ceb08-140">If there is a distrbution supported by .NET that is not listed here, you can request that support for the distribution be added.</span></span> <span data-ttu-id="ceb08-141">Renseignez une demande à l’aide du modèle [Demande de support de distribution][].</span><span class="sxs-lookup"><span data-stu-id="ceb08-141">Please file a request using the [Distribution Support Request][] template.</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="ceb08-142">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-142">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="ceb08-143">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-143">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="ceb08-144">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-144">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ceb08-145">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ceb08-145">The preferred method is as follows:</span></span>

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

<span data-ttu-id="ceb08-146">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="ceb08-146">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ceb08-147">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get install powershell`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-147">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="ceb08-148">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-148">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="ceb08-149">Téléchargez le package Debian `powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="ceb08-149">Download the Debian package `powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ceb08-150">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ceb08-150">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ceb08-151">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="ceb08-151">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="ceb08-152">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceb08-152">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="ceb08-153">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-153">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="ceb08-154">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-154">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="ceb08-155">Installation via un dépôt de packages - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="ceb08-156">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-156">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ceb08-157">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ceb08-157">The preferred method is as follows:</span></span>

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

<span data-ttu-id="ceb08-158">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="ceb08-158">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ceb08-159">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get install powershell`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-159">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="ceb08-160">Installation par téléchargement direct - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-160">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="ceb08-161">Téléchargez le package Debian `powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="ceb08-161">Download the Debian package `powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ceb08-162">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ceb08-162">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ceb08-163">La commande `dpkg -i` échoue avec les dépendances unmet.</span><span class="sxs-lookup"><span data-stu-id="ceb08-163">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="ceb08-164">La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceb08-164">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="ceb08-165">Désinstallation - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-165">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="ceb08-166">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="ceb08-166">Ubuntu 18.10</span></span>

<span data-ttu-id="ceb08-167">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-167">Installation is supported via `snapd`.</span></span> <span data-ttu-id="ceb08-168">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="ceb08-168">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-169">Ubuntu 18.10 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle)[prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="ceb08-169">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="ceb08-170">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-170">Ubuntu 19.04</span></span>

<span data-ttu-id="ceb08-171">L’installation est prise en charge via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-171">Installation is supported via `snapd`.</span></span> <span data-ttu-id="ceb08-172">Pour obtenir des instructions, consultez [Package Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="ceb08-172">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-173">Ubuntu 19.04 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle)[prise en charge par la communauté](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="ceb08-173">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-2004"></a><span data-ttu-id="ceb08-174">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-174">Ubuntu 20.04</span></span>

<span data-ttu-id="ceb08-175">Ubuntu 20.04 est une version LTS.</span><span class="sxs-lookup"><span data-stu-id="ceb08-175">Ubuntu 20.04 is an LTS release.</span></span> <span data-ttu-id="ceb08-176">PowerShell ne prend pas en charge cette version pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="ceb08-176">PowerShell does not currently support this version.</span></span> <span data-ttu-id="ceb08-177">La prise en charge de cette version est actuellement envisagée pour la version PowerShell 7.1.</span><span class="sxs-lookup"><span data-stu-id="ceb08-177">Support for this version is being considered for the PowerShell 7.1 release.</span></span> <span data-ttu-id="ceb08-178">Veuillez voter pour cette [demande](https://github.com/PowerShell/PowerShell/issues/12626) si vous souhaitez la prise en charge pour Ubuntu 20.04.</span><span class="sxs-lookup"><span data-stu-id="ceb08-178">Please upvote this [request](https://github.com/PowerShell/PowerShell/issues/12626) if you would like support for Ubuntu 20.04.</span></span>

## <a name="debian-8"></a><span data-ttu-id="ceb08-179">Debian 8</span><span class="sxs-lookup"><span data-stu-id="ceb08-179">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="ceb08-180">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="ceb08-180">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="ceb08-181">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-181">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ceb08-182">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ceb08-182">The preferred method is as follows:</span></span>

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

<span data-ttu-id="ceb08-183">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="ceb08-183">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ceb08-184">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get install powershell`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-184">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="ceb08-185">Debian 9</span><span class="sxs-lookup"><span data-stu-id="ceb08-185">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="ceb08-186">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ceb08-186">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="ceb08-187">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-187">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ceb08-188">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ceb08-188">The preferred method is as follows:</span></span>

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

<span data-ttu-id="ceb08-189">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="ceb08-189">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ceb08-190">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get install powershell`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-190">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="ceb08-191">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ceb08-191">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="ceb08-192">Téléchargez le package Debian `powershell-lts_7.0.3-1.debian.9_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="ceb08-192">Download the Debian package `powershell-lts_7.0.3-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ceb08-193">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ceb08-193">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.3-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="ceb08-194">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ceb08-194">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="ceb08-195">Debian 10</span><span class="sxs-lookup"><span data-stu-id="ceb08-195">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-196">Debian 10 est pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="ceb08-196">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="ceb08-197">Installation via un dépôt de packages - Debian 10</span><span class="sxs-lookup"><span data-stu-id="ceb08-197">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="ceb08-198">PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-198">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="ceb08-199">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ceb08-199">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="ceb08-200">Installation par téléchargement direct - Debian 10</span><span class="sxs-lookup"><span data-stu-id="ceb08-200">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="ceb08-201">Téléchargez le package tar.gz `powershell-7.0.3-linux-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="ceb08-201">Download the tar.gz package `powershell-7.0.3-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ceb08-202">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ceb08-202">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="ceb08-203">Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="ceb08-203">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-204">Alpine 3.9 et 3.10 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="ceb08-204">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="ceb08-205">Installation par téléchargement direct - Alpine 3.9 et 3.10</span><span class="sxs-lookup"><span data-stu-id="ceb08-205">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="ceb08-206">Téléchargez le package tar.gz `powershell-7.0.3-linux-alpine-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Alpine.</span><span class="sxs-lookup"><span data-stu-id="ceb08-206">Download the tar.gz package `powershell-7.0.3-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="ceb08-207">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ceb08-207">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="ceb08-208">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-208">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-209">Ce package fonctionne sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="ceb08-209">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="ceb08-210">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-210">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="ceb08-211">PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ceb08-212">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="ceb08-212">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ceb08-213">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-213">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="ceb08-214">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-214">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="ceb08-215">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="ceb08-215">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="ceb08-216">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ceb08-216">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ceb08-217">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="ceb08-217">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="ceb08-218">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-218">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ceb08-220">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-220">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ceb08-221">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-221">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ceb08-222">PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-222">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ceb08-223">En tant que super utilisateur, inscrivez le référentiel Microsoft une fois.</span><span class="sxs-lookup"><span data-stu-id="ceb08-223">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="ceb08-224">Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-224">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ceb08-225">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-225">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ceb08-226">Téléchargez le package RPM `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="ceb08-226">Download the RPM package `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="ceb08-227">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ceb08-227">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ceb08-228">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="ceb08-228">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ceb08-229">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-229">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="ceb08-230">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="ceb08-230">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="ceb08-231">Installation – openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ceb08-231">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="ceb08-232">Installation – openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ceb08-232">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="ceb08-233">Désinstallation – openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ceb08-233">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="ceb08-234">Fedora</span><span class="sxs-lookup"><span data-stu-id="ceb08-234">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-235">Fedora 28 n’est pris en charge que dans la version 6.1 et les versions plus récentes de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceb08-235">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-236">Fedora 29 et 30 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.</span><span class="sxs-lookup"><span data-stu-id="ceb08-236">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="ceb08-237">Installation via un dépôt de packages (par défaut) - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="ceb08-237">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="ceb08-238">PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-238">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="ceb08-239">Installation par téléchargement direct - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="ceb08-239">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="ceb08-240">Téléchargez le package RPM `powershell-7.0.3-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="ceb08-240">Download the RPM package `powershell-7.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="ceb08-241">Exécutez ensuite les commandes suivantes dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="ceb08-241">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ceb08-242">Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="ceb08-242">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="ceb08-243">Désinstallation - Fedora 28, 29 et 30</span><span class="sxs-lookup"><span data-stu-id="ceb08-243">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="ceb08-244">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="ceb08-244">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-245">La prise en charge d’Arch n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.</span><span class="sxs-lookup"><span data-stu-id="ceb08-245">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="ceb08-246">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="ceb08-246">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="ceb08-247">Il peut être compilé avec la [dernière version étiquetée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="ceb08-247">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="ceb08-248">Il peut être compilé à partir de la [dernière validation sur le master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="ceb08-248">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="ceb08-249">Il peut être installé en utilisant la [dernière ressource binaire de la version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="ceb08-249">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="ceb08-250">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="ceb08-250">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="ceb08-251">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou [Utilisation de PowerShell](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="ceb08-251">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="ceb08-253">Snap Package</span><span class="sxs-lookup"><span data-stu-id="ceb08-253">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="ceb08-254">Obtention de snapd</span><span class="sxs-lookup"><span data-stu-id="ceb08-254">Getting snapd</span></span>

<span data-ttu-id="ceb08-255">`snapd` est obligatoire pour exécuter des snaps.</span><span class="sxs-lookup"><span data-stu-id="ceb08-255">`snapd` is required to run snaps.</span></span> <span data-ttu-id="ceb08-256">Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-256">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="ceb08-257">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="ceb08-257">Installation via Snap</span></span>

<span data-ttu-id="ceb08-258">PowerShell pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation et les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-258">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="ceb08-259">La méthode recommandée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ceb08-259">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="ceb08-260">Pour installer une préversion, utilisez la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="ceb08-260">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="ceb08-261">Après l’installation, Snap est automatiquement mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="ceb08-261">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="ceb08-262">Vous pouvez déclencher une mise à niveau avec `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-262">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="ceb08-263">Désinstallation</span><span class="sxs-lookup"><span data-stu-id="ceb08-263">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="ceb08-264">or</span><span class="sxs-lookup"><span data-stu-id="ceb08-264">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="ceb08-265">Kali</span><span class="sxs-lookup"><span data-stu-id="ceb08-265">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-266">La prise en charge de Kali n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.</span><span class="sxs-lookup"><span data-stu-id="ceb08-266">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="ceb08-267">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="ceb08-267">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="ceb08-268">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="ceb08-268">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="ceb08-269">Raspbian</span><span class="sxs-lookup"><span data-stu-id="ceb08-269">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="ceb08-270">La prise en charge de Raspbian est expérimentale.</span><span class="sxs-lookup"><span data-stu-id="ceb08-270">Raspbian support is experimental.</span></span>

<span data-ttu-id="ceb08-271">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="ceb08-271">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="ceb08-272">CoreCLR et PowerShell fonctionnent uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ceb08-272">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="ceb08-273">Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.</span><span class="sxs-lookup"><span data-stu-id="ceb08-273">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="ceb08-274">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="ceb08-274">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.3-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="ceb08-275">Si vous le souhaitez, vous pouvez créer un lien symbolique pour démarrer PowerShell sans spécifier de chemin d’accès au binaire `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-275">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="ceb08-276">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="ceb08-276">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="ceb08-277">Installation de préversions</span><span class="sxs-lookup"><span data-stu-id="ceb08-277">Installing Preview Releases</span></span>

<span data-ttu-id="ceb08-278">Lorsque vous installez une préversion de PowerShell pour Linux au moyen d’un référentiel de packages, le nom de package passe de `powershell` à `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-278">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="ceb08-279">Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="ceb08-279">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="ceb08-280">Le tableau suivant contient des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :</span><span class="sxs-lookup"><span data-stu-id="ceb08-280">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="ceb08-281">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="ceb08-281">Distribution(s)</span></span> |            <span data-ttu-id="ceb08-282">Commande stable</span><span class="sxs-lookup"><span data-stu-id="ceb08-282">Stable Command</span></span>            |               <span data-ttu-id="ceb08-283">Commande de préversion</span><span class="sxs-lookup"><span data-stu-id="ceb08-283">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="ceb08-284">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="ceb08-284">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="ceb08-285">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="ceb08-285">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="ceb08-286">Fedora</span><span class="sxs-lookup"><span data-stu-id="ceb08-286">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="ceb08-287">Installation en tant qu’outil global .NET</span><span class="sxs-lookup"><span data-stu-id="ceb08-287">Install as a .NET Global tool</span></span>

<span data-ttu-id="ceb08-288">Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="ceb08-288">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="ceb08-289">Le programme d’installation de l’outil dotnet ajoute `~/.dotnet/tools` à votre variable d’environnement `PATH`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-289">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="ceb08-290">Toutefois, le `PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="ceb08-290">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="ceb08-291">Vous devez pouvoir démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-291">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="ceb08-292">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="ceb08-292">Binary Archives</span></span>

<span data-ttu-id="ceb08-293">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="ceb08-293">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="ceb08-294">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="ceb08-294">Dependencies</span></span>

<span data-ttu-id="ceb08-295">PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="ceb08-295">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="ceb08-296">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte de la même manière.</span><span class="sxs-lookup"><span data-stu-id="ceb08-296">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="ceb08-297">Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="ceb08-297">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="ceb08-298">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="ceb08-298">OS</span></span>                 | <span data-ttu-id="ceb08-299">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="ceb08-299">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="ceb08-300">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-300">Ubuntu 16.04</span></span>       | <span data-ttu-id="ceb08-301">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ceb08-301">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ceb08-302">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="ceb08-302">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="ceb08-303">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="ceb08-303">Ubuntu 17.10</span></span>       | <span data-ttu-id="ceb08-304">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ceb08-304">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ceb08-305">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="ceb08-305">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="ceb08-306">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ceb08-306">Ubuntu 18.04</span></span>       | <span data-ttu-id="ceb08-307">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ceb08-307">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ceb08-308">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="ceb08-308">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="ceb08-309">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="ceb08-309">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="ceb08-310">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ceb08-310">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ceb08-311">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="ceb08-311">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ceb08-312">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="ceb08-312">Debian 9 (Stretch)</span></span> | <span data-ttu-id="ceb08-313">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ceb08-313">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ceb08-314">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="ceb08-314">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="ceb08-315">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-315">CentOS 7</span></span> <br> <span data-ttu-id="ceb08-316">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-316">Oracle Linux 7</span></span> <br> <span data-ttu-id="ceb08-317">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="ceb08-317">RHEL 7</span></span> | <span data-ttu-id="ceb08-318">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="ceb08-318">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="ceb08-319">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ceb08-319">openSUSE 42.3</span></span> | <span data-ttu-id="ceb08-320">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="ceb08-320">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="ceb08-321">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ceb08-321">openSUSE Leap 15</span></span> | <span data-ttu-id="ceb08-322">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="ceb08-322">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="ceb08-323">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="ceb08-323">Fedora 27</span></span> <br> <span data-ttu-id="ceb08-324">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ceb08-324">Fedora 28</span></span> | <span data-ttu-id="ceb08-325">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="ceb08-325">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="ceb08-326">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="ceb08-326">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="ceb08-327">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe d’abord les dépendances, puis extrait l’archive Linux `tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="ceb08-327">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="ceb08-328">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="ceb08-328">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="ceb08-329">Linux</span><span class="sxs-lookup"><span data-stu-id="ceb08-329">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="ceb08-330">Désinstallation des archives binaires</span><span class="sxs-lookup"><span data-stu-id="ceb08-330">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="ceb08-331">Chemins</span><span class="sxs-lookup"><span data-stu-id="ceb08-331">Paths</span></span>

- <span data-ttu-id="ceb08-332">`$PSHOME` est `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="ceb08-332">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="ceb08-333">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ceb08-333">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="ceb08-334">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ceb08-334">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="ceb08-335">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ceb08-335">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="ceb08-336">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ceb08-336">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="ceb08-337">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="ceb08-337">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="ceb08-338">L’historique PSReadLine est enregistré dans`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="ceb08-338">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="ceb08-339">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="ceb08-339">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ceb08-340">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.</span><span class="sxs-lookup"><span data-stu-id="ceb08-340">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="ceb08-341">Prise en charge de l’installation</span><span class="sxs-lookup"><span data-stu-id="ceb08-341">Installation support</span></span>

<span data-ttu-id="ceb08-342">Microsoft prend en charge les méthodes d’installation mentionnées dans ce document.</span><span class="sxs-lookup"><span data-stu-id="ceb08-342">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="ceb08-343">D’autres méthodes d’installation peuvent être disponibles à partir d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="ceb08-343">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="ceb08-344">Même s’il est possible que ces outils et méthodes fonctionnent, Microsoft ne peut pas prendre en charge ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="ceb08-344">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Demande de support de distribution]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
