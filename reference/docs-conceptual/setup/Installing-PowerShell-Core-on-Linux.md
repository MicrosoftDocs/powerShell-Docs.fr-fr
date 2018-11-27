---
title: Installation de PowerShell Core sous Linux
description: Informations sur l’installation de PowerShell Core sur diverses distributions Linux
ms.date: 08/06/2018
ms.openlocfilehash: afb11f053517af592fe42754d543f9f4a9966c5b
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321109"
---
# <a name="installing-powershell-core-on-linux"></a>Installation de PowerShell Core sous Linux

Prend en charge [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] et [Arch Linux][arch].

Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’utiliser [PowerShell Snap Package][snap].
Vous pouvez également essayer de déployer des fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires selon le système d’exploitation dans une procédure distincte.

Tous les packages sont disponibles dans notre page de [versions][] GitHub.
Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.

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

## <a name="installing-preview-releases"></a>Installation de préversions

Lorsque vous installez une préversion de PowerShell Core pour Linux via un dépôt de packages, le nom de package passe de `powershell` à `powershell-preview`.

Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.

Voici un tableau des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :

|Distribution(s)|Commande stable | Commande de préversion |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Installation via un dépôt de packages - Ubuntu 14.04

PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).
Il s’agit de la méthode recommandée.

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

En tant que super utilisateur, inscrivez le référentiel Microsoft.
Dès lors, il vous suffit d’utiliser `sudo apt-get upgrade powershell` pour mettre à jour l’installation.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Installation par téléchargement direct - Ubuntu 14.04

Téléchargez le package Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`
à partir de la page de [versions][] sur l’ordinateur Ubuntu.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> La commande `dpkg -i` échoue avec les dépendances unmet.
> La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.

### <a name="uninstallation---ubuntu-1404"></a>Désinstallation - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Installation via un dépôt de packages - Ubuntu 16.04

PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).
Il s’agit de la méthode recommandée.

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

Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installation par téléchargement direct - Ubuntu 16.04

Téléchargez le package Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`
à partir de la page de [versions][] sur l’ordinateur Ubuntu.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> La commande `dpkg -i` échoue avec les dépendances unmet.
> La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Désinstallation - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Ajout de la prise en charge d’Ubuntu 18.04 après `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1804"></a>Installation via un dépôt de packages - Ubuntu 18.04

PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).
Il s’agit de la méthode recommandée.

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

Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Installation par téléchargement direct - Ubuntu 18.04

Téléchargez le package Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`
à partir de la page de [versions][] sur l’ordinateur Ubuntu.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> La commande `dpkg -i` échoue avec les dépendances unmet.
> La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.

### <a name="uninstallation---ubuntu-1804"></a>Désinstallation - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

> [!NOTE]
> Ajout de la prise en charge d’Ubuntu 18.10 après `6.1.0-preview.3`.
> 18.10 étant une build quotidienne, elle est uniquement prise en charge par la communauté.

L’installation de 18.10 est prise en charge via `snapd`. Consultez [Snap Package][snap] pour des instructions complètes.

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Installation via un dépôt de packages - Debian 8

PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).
Il s’agit de la méthode recommandée.

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

Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.

### <a name="installation-via-direct-download---debian-8"></a>Installation par téléchargement direct - Debian 8

Téléchargez le package Debian `powershell_6.1.0-1.debian.8_amd64.deb`
à partir de la page de [versions][] sur l’ordinateur Debian.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> La commande `dpkg -i` échoue avec les dépendances unmet.
> La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.

### <a name="uninstallation---debian-8"></a>Désinstallation - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Installation via un dépôt de packages - Debian 9

PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).
Il s’agit de la méthode recommandée.

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

Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.

### <a name="installation-via-direct-download---debian-9"></a>Installation par téléchargement direct - Debian 9

Téléchargez le package Debian `powershell_6.1.0-1.debian.9_amd64.deb`
à partir de la page de [versions][] sur l’ordinateur Debian.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Désinstallation - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Ce package fonctionne également sur Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Installation via un dépôt de packages (par défaut) - CentOS 7

PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Installation par téléchargement direct - CentOS 7

À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`
à partir de la page de [versions][] sur l’ordinateur CentOS.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Désinstallation - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7

PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7

Téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`
à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
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

### <a name="installation---opensuse-leap-15"></a>Installation – openSUSE Leap 15

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Désinstallation – openSUSE 42.3, openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 est pris en charge dans PowerShell Core 6.1 et ultérieur uniquement.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Installation au moyen d’un référentiel de packages (par défaut) – Fedora 27, Fedora 28

PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Installation par téléchargement direct – Fedora 27, Fedora 28

Téléchargez le package RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`
à partir de la page de [versions][] sur l’ordinateur Fedora.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Désinstallation – Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> La prise en charge d’arch est expérimentale.

PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].

* Il peut être compilé avec la [dernière version identifiée][arch-release]
* Il peut être compilé à partir de la [dernière validation sur le maître][arch-git]
* Il peut être installé à l’aide de la [dernière ressource binaire de version][arch-bin]

Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.

Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou le [fichier Dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la communauté.

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Snap Package

### <a name="getting-snapd"></a>Obtention de snapd

`snapd` est obligatoire pour exécuter des snaps.
Utilisez [ces instructions](https://docs.snapcraft.io/core/install) pour vérifier que vous avez bien installé `snapd`.

### <a name="installation-via-snap"></a>Installation via Snap

PowerShell Core pour Linux est publié dans le [Snap Store](https://snapcraft.io/store) pour faciliter l’installation (et les mises à jour).
Il s’agit de la méthode recommandée.

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Si vous souhaitez installer la préversion, utilisez la méthode suivante.

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

La mise à niveau de Snap est automatique après l’installation, mais vous pouvez déclencher une mise à niveau avec `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Désinstallation

```sh
sudo snap remove powershell
```

ou

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation---kali"></a>Installation – Kali

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

### <a name="uninstallation---kali"></a>Désinstallation - Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> La prise en charge de Raspbian est expérimentale.

Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.

De plus, CoreCLR (et donc PowerShell Core) fonctionne uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.

Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.

### <a name="installation---raspbian"></a>Installation – Raspbian

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

Si vous le souhaitez, vous pouvez créer un lien symbolique pour être en mesure de démarrer PowerShell sans spécifier de chemin d’accès au binaire « pwsh »

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Désinstallation - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Archives binaires

Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes Linux afin de permettre des scénarios de déploiement avancés.

### <a name="dependencies"></a>Dépendances

PowerShell génère des binaires portables pour toutes les distributions Linux.
Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte par conséquent de la même manière.

Le graphique suivant montre les dépendances .NET Core 2.0 prises en charge officiellement sur différentes distributions Linux.

| Système d’exploitation                 | Dépendances |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, openssl-libs, libicu |
| openSUSE 42.3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE Leap 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.
Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe tout d’abord les dépendances, puis extrait l’archive `tar.gz` Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Installation - Archives binaires

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>Désinstallation des archives binaires

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Chemins d’accès

* `$PSHOME` est `/opt/microsoft/powershell/6.1.0/`
* Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`
* Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`
* Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`
* Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`
* Les modules par défaut sont lus à partir de `$PSHOME/Modules`
* L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.

PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur Linux.

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
