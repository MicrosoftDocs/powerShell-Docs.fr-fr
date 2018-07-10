# <a name="installing-powershell-core-on-linux"></a>Installation de PowerShell Core sous Linux

Prend en charge [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] et [Arch Linux][arch].

Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’utiliser [AppImage PowerShell][lai].
Vous pouvez également essayer de déployer des fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires selon le système d’exploitation dans une procédure distincte.

Tous les packages sont disponibles dans notre page de [versions][] GitHub.
Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Installation de préversions

Lorsque vous installez une préversion de PowerShell Core pour Linux via un dépôt de packages, le nom de package passe de `powershell` à `powershell-preview`.

Les installations par téléchargement direct ne changent rien, sinon le nom de fichier.

Voici un tableau des commandes permettant d’installer les packages stables et en préversion à l’aide des divers gestionnaires de package :

|Distribution(s)|Commande stable | Commande de préversion |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| OpenSUSE |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Installation via un dépôt de packages - Ubuntu 14.04

PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).
Il s’agit de la méthode recommandée.

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

En tant que super utilisateur, inscrivez le référentiel Microsoft.
Dès lors, il vous suffit d’utiliser `sudo apt-get upgrade powershell` pour mettre à jour l’installation.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Installation par téléchargement direct - Ubuntu 14.04

Téléchargez le package Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
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

Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installation par téléchargement direct - Ubuntu 16.04

Téléchargez le package Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> La commande `dpkg -i` échoue avec les dépendances unmet.
> La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Désinstallation - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a>Ubuntu 17.10

> [!NOTE]
> Ajout de la prise en charge d’Ubuntu 17.04 après `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1710"></a>Installation via un dépôt de packages - Ubuntu 17.10

PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).
Il s’agit de la méthode recommandée.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.

### <a name="installation-via-direct-download---ubuntu-1710"></a>Installation par téléchargement direct - Ubuntu 17.10

Téléchargez le package Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> La commande `dpkg -i` échoue avec les dépendances unmet.
> La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.

### <a name="uninstallation---ubuntu-1710"></a>Désinstallation - Ubuntu 17.10

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
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh
```

Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Installation par téléchargement direct - Ubuntu 18.04

Téléchargez le package Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> La commande `dpkg -i` échoue avec les dépendances unmet.
> La commande suivante, `apt-get install -f`, résout ces problèmes et termine la configuration du package PowerShell.

### <a name="uninstallation---ubuntu-1710"></a>Désinstallation - Ubuntu 17.10

```sh
sudo apt-get remove powershell
```

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

Téléchargez le package Debian `powershell_6.0.2-1.debian.8_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
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

Téléchargez le package Debian `powershell_6.0.2-1.debian.9_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
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

À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur CentOS.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Téléchargez le package RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Désinstallation - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

Lors de l’installation de PowerShell Core, `zypper` peut signaler l’erreur suivante :

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

Dans ce cas, vérifiez qu’une bibliothèque `libcurl` compatible est présente en contrôlant que la commande suivante indique que le package `libcurl4` est installé :

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

Ensuite, choisissez la solution `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` quand vous installez le package PowerShell.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Installation via un dépôt de packages (par défaut) - OpenSUSE 42.2

PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Installation par téléchargement direct - OpenSUSE 42.2

Téléchargez le package RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur OpenSUSE.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Désinstallation - OpenSUSE 42.2

```sh
sudo zypper remove powershell
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

Téléchargez le package RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.

Exécutez ensuite le code suivant dans le terminal :

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

## <a name="linux-appimage"></a>AppImage Linux

> [!NOTE]
> La prise en charge d’AppImage est expérimentale.

En utilisant une distribution Linux récente, téléchargez AppImage `powershell-6.0.1-x86_64.AppImage` à partir de la page de [versions][] sur l’ordinateur Linux.

Exécutez ensuite le code suivant dans le terminal :

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

[AppImage][] vous permet d’exécuter PowerShell sans l’installer.
Il s’agit d’une application portable qui regroupe PowerShell et ses dépendances (dont les dépendances système de .NET Core) en un package cohérent.
Ce package est un fichier binaire unique qui fonctionne indépendamment de la distribution Linux de l’utilisateur.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

> [!NOTE]
> La prise en charge de Kali est expérimentale.

### <a name="installation"></a>Installation

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Exécuter PowerShell dans la dernière version de Kali (publication en continu Kali GNU/Linux) sans l’installer

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Désinstallation - Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> La prise en charge de Raspbian est expérimentale.

Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.

De plus, CoreCLR (et donc PowerShell Core) fonctionne uniquement sur les appareils Pi 2 et Pi 3, car les autres appareils, comme [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ont un processeur non pris en charge.

Téléchargez [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) et suivez les [instructions d’installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) pour l’obtenir sur votre Pi.

### <a name="installation"></a>Installation

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
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 | libunwind, libcurl, openssl-libs, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.
Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe tout d’abord les dépendances, puis extrait l’archive `tar.gz` Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Installation - Archives binaires

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>Désinstallation des archives binaires

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Chemins d’accès

* `$PSHOME` est `/opt/microsoft/powershell/6.0.2/`
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
