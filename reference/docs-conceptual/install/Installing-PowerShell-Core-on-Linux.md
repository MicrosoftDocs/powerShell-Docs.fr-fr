---
title: Installation de PowerShell sur Linux
description: Informations sur l’installation de PowerShell sur différentes distributions Linux
ms.date: 03/09/2020
ms.openlocfilehash: e04d8a91999cd6e9b2d669230c7a1b412f11eeb8
ms.sourcegitcommit: 4eda0bc902658d4a188159bd7310e64399f6e178
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83271897"
---
# <a name="installing-powershell-on-linux"></a>Installation de PowerShell sur Linux

Tous les packages sont disponibles dans notre page de [versions][] GitHub. Une fois le package installé, exécutez `pwsh` à partir d’un terminal. Exécutez `pwsh-preview` si vous avez installé une [préversion](#installing-preview-releases).

> [!NOTE]
> PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.
>
> Le dossier `/usr/local/microsoft/powershell/6` est remplacé par `/usr/local/microsoft/powershell/7`.
>
> Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [Archive binaire](#binary-archives).

Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’installer PowerShell avec [PowerShell Snap Package][snap]. Vous pouvez également essayer de déployer les fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires en fonction du système d’exploitation dans des étapes distinctes.

[snap]: #snap-package
[tar]: #binary-archives

Mises en production officiellement prises en charge

- Ubuntu 16.04
- Ubuntu 18.04
- Debian 8
- Debian 9
- Debian 10
- Alpine 3.9 et 3.10
- CentOS 7
- Red Hat Enterprise Linux (RHEL) 7
- Fedora 28
- Fedora 29
- Fedora 30
- openSUSE 42.3
- openSUSE Leap 15

Mises en production prises en charge par la communauté

- Ubuntu 18.10
- Ubuntu 19.04
- Arch Linux
- Kali
- Raspbian (expérimental)

Autres méthodes d’installation

- Snap Package
- Archives binaires
- Outil .NET Global

Non prise en charge pour le moment 

- Ubuntu 20.04

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Installation via un dépôt de packages - Ubuntu 16.04

PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.

La méthode recommandée est la suivante :

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

En tant que super utilisateur, inscrivez le référentiel Microsoft une fois. Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installation par téléchargement direct - Ubuntu 16.04

Téléchargez le package Debian `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.

Exécutez ensuite les commandes suivantes dans le terminal :

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> La commande `dpkg -i` échoue avec les dépendances unmet. La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Désinstallation - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>Installation via un dépôt de packages - Ubuntu 18.04

PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.

La méthode recommandée est la suivante :

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

En tant que super utilisateur, inscrivez le référentiel Microsoft une fois. Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Installation par téléchargement direct - Ubuntu 18.04

Téléchargez le package Debian `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.

Exécutez ensuite les commandes suivantes dans le terminal :

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> La commande `dpkg -i` échoue avec les dépendances unmet. La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.

### <a name="uninstallation---ubuntu-1804"></a>Désinstallation - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

L’installation est prise en charge via `snapd`. Pour obtenir des instructions, consultez [Package Snap][snap].

> [!NOTE]
> Ubuntu 18.10 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle)[prise en charge par la communauté](../powershell-support-lifecycle.md).

## <a name="ubuntu-1904"></a>Ubuntu 19.04

L’installation est prise en charge via `snapd`. Pour obtenir des instructions, consultez [Package Snap][snap].

> [!NOTE]
> Ubuntu 19.04 est une [version intermédiaire](https://www.ubuntu.com/about/release-cycle)[prise en charge par la communauté](../powershell-support-lifecycle.md).

## <a name="ubuntu-2004"></a>Ubuntu 20.04

Ubuntu 20.04 est une version LTS. PowerShell ne prend pas en charge cette version pour l’instant. La prise en charge de cette version est actuellement envisagée pour la version PowerShell 7.1. Veuillez voter pour cette [demande](https://github.com/PowerShell/PowerShell/issues/12626) si vous souhaitez la prise en charge pour Ubuntu 20.04.

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Installation via un dépôt de packages - Debian 8

PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.

La méthode recommandée est la suivante :

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

En tant que super utilisateur, inscrivez le référentiel Microsoft une fois. Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Installation via un dépôt de packages - Debian 9

PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.

La méthode recommandée est la suivante :

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

En tant que super utilisateur, inscrivez le référentiel Microsoft une fois. Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---debian-9"></a>Installation par téléchargement direct - Debian 9

Téléchargez le package Debian `powershell-lts_7.0.0-1.debian.9_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.

Exécutez ensuite les commandes suivantes dans le terminal :

```sh
sudo dpkg -i powershell-lts_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Désinstallation - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a>Debian 10

> [!NOTE]
> Debian 10 est pris en charge dans PowerShell 7.0 et ultérieur uniquement.

### <a name="installation-via-package-repository---debian-10"></a>Installation via un dépôt de packages - Debian 10

PowerShell pour Linux est publié dans les référentiels de packages pour faciliter l’installation et les mises à jour.

La méthode recommandée est la suivante :

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

### <a name="installation-via-direct-download---debian-10"></a>Installation par téléchargement direct - Debian 10

Téléchargez le package tar.gz `powershell_7.0.0-linux-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Debian.

Exécutez ensuite les commandes suivantes dans le terminal :

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

## <a name="alpine-39-and-310"></a>Alpine 3.9 et 3.10

> [!NOTE]
> Alpine 3.9 et 3.10 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.

### <a name="installation-via-direct-download---alpine-39-and-310"></a>Installation par téléchargement direct - Alpine 3.9 et 3.10

Téléchargez le package tar.gz `powershell-7.0.0-linux-alpine-x64.tar.gz` à partir de la page de [versions][] sur l’ordinateur Alpine.

Exécutez ensuite les commandes suivantes dans le terminal :

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

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Ce package fonctionne sur Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Installation via un dépôt de packages (par défaut) - CentOS 7

PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

En tant que super utilisateur, inscrivez le référentiel Microsoft une fois. Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.

### <a name="installation-via-direct-download---centos-7"></a>Installation par téléchargement direct - CentOS 7

À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur CentOS.

Exécutez ensuite les commandes suivantes dans le terminal :

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Désinstallation - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7

PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

En tant que super utilisateur, inscrivez le référentiel Microsoft une fois. Après l’inscription, vous pouvez mettre à jour PowerShell avec `sudo yum update powershell`.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7

Téléchargez le package RPM `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.

Exécutez ensuite les commandes suivantes dans le terminal :

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Désinstallation - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>OpenSUSE

### <a name="installation---opensuse-423"></a>Installation – openSUSE 42.3

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

### <a name="installation---opensuse-leap-15"></a>Installation – openSUSE Leap 15

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Désinstallation – openSUSE 42.3, openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 n’est pris en charge que dans la version 6.1 et les versions plus récentes de PowerShell.

> [!NOTE]
> Fedora 29 et 30 sont pris en charge dans PowerShell 7.0 et ultérieur uniquement.

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a>Installation via un dépôt de packages (par défaut) - Fedora 28, 29 et 30

PowerShell pour Linux est publié dans les référentiels Microsoft officiels pour faciliter l’installation et les mises à jour.

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a>Installation par téléchargement direct - Fedora 28, 29 et 30

Téléchargez le package RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.

Exécutez ensuite les commandes suivantes dans le terminal :

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

Vous pouvez installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a>Désinstallation - Fedora 28, 29 et 30

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> La prise en charge d’Arch n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.

PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].

- Il peut être compilé avec la [dernière version étiquetée][arch-release]
- Il peut être compilé à partir de la [dernière validation sur le master][arch-git]
- Il peut être installé en utilisant la [dernière ressource binaire de la version][arch-bin]

Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.

Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou [Utilisation de PowerShell](powershell-in-docker.md).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Snap Package

### <a name="getting-snapd"></a>Obtention de snapd

`snapd` est obligatoire pour exécuter des snaps. Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.

### <a name="installation-via-snap"></a>Installation via Snap

PowerShell pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation et les mises à jour.

La méthode recommandée est la suivante :

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Pour installer une préversion, utilisez la méthode suivante :

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Après l’installation, Snap est automatiquement mis à niveau. Vous pouvez déclencher une mise à niveau avec `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Désinstallation

```sh
sudo snap remove powershell
```

or

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

> [!NOTE]
> La prise en charge de Kali n’est pas officiellement reconnue par Microsoft et est gérée par la communauté.

### <a name="installation---kali"></a>Installation – Kali

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>Désinstallation - Kali

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> La prise en charge de Raspbian est expérimentale.

Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.

CoreCLR et PowerShell fonctionnent uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.

Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.

### <a name="installation---raspbian"></a>Installation – Raspbian

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

Si vous le souhaitez, vous pouvez créer un lien symbolique pour démarrer PowerShell sans spécifier de chemin d’accès au binaire `pwsh`.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Désinstallation - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a>Installation de préversions

Lorsque vous installez une préversion de PowerShell pour Linux au moyen d’un référentiel de packages, le nom de package passe de `powershell` à `powershell-preview`.

Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.

Le tableau suivant contient des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :

| Distribution(s) |            Commande stable            |               Commande de préversion                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| Ubuntu, Debian  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| CentOS, RedHat  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| Fedora          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a>Installation en tant qu’outil global .NET

Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Le programme d’installation de l’outil dotnet ajoute `~/.dotnet/tools` à votre variable d’environnement `PATH`. Toutefois, le `PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour. Vous devez pouvoir démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.

## <a name="binary-archives"></a>Archives binaires

Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.

### <a name="dependencies"></a>Les dépendances

PowerShell génère des binaires portables pour toutes les distributions Linux. Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte de la même manière.

Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.

| Système d''exploitation                 | Les dépendances |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, openssl-libs, libicu |
| openSUSE 42.3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE Leap 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte. Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe d’abord les dépendances, puis extrait l’archive Linux `tar.gz`.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>Installation - Archives binaires

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>Désinstallation des archives binaires

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Chemins

- `$PSHOME` est `/opt/microsoft/powershell/7/`
- Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`
- Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`
- Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`
- Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`
- Les modules par défaut sont lus à partir de `$PSHOME/Modules`
- L’historique PSReadLine est enregistré dans`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.

PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
