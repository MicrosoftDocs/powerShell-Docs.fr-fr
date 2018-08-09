---
title: Accès distant à PowerShell via SSH
description: Accès distant dans PowerShell Core à l’aide de SSH
ms.date: 08/06/2018
ms.openlocfilehash: 27a8fc5623796a270a2ea67aa550c9a0998e766b
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587497"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="8ece4-103">Accès distant à PowerShell via SSH</span><span class="sxs-lookup"><span data-stu-id="8ece4-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="8ece4-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="8ece4-104">Overview</span></span>

<span data-ttu-id="8ece4-105">L’accès distant PowerShell utilise normalement WinRM pour la négociation de la connexion et le transport des données.</span><span class="sxs-lookup"><span data-stu-id="8ece4-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="8ece4-106">SSH a été choisi pour cette implémentation de l’accès distant, car il est maintenant disponible pour les plateformes Linux et Windows, et permet un véritable accès distant PowerShell multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="8ece4-106">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span> <span data-ttu-id="8ece4-107">Cependant, WinRM fournit également un modèle d’hébergement robuste pour les sessions à distance PowerShell, ce que cette implémentation ne fait pas encore.</span><span class="sxs-lookup"><span data-stu-id="8ece4-107">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span> <span data-ttu-id="8ece4-108">Cela signifie aussi que la configuration de point de terminaison distant PowerShell et JEA (Just Enough Administration) ne sont pas encore pris en charge dans cette implémentation.</span><span class="sxs-lookup"><span data-stu-id="8ece4-108">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="8ece4-109">L’accès distant SSH PowerShell vous permet un accès distant pour une session PowerShell de base entre des ordinateurs Windows et Linux.</span><span class="sxs-lookup"><span data-stu-id="8ece4-109">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="8ece4-110">Pour cela, vous devez créer un processus hébergeant PowerShell sur l’ordinateur cible en tant que sous-système SSH.</span><span class="sxs-lookup"><span data-stu-id="8ece4-110">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span> <span data-ttu-id="8ece4-111">Au final, ce sera remplacé en un modèle d’hébergement plus général, similaire au mode de fonctionnement de WinRM pour prendre en charge la configuration de point de terminaison et JEA.</span><span class="sxs-lookup"><span data-stu-id="8ece4-111">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="8ece4-112">Les applets de commande `New-PSSession` `Enter-PSSession` et `Invoke-Command` ont maintenant un nouvel ensemble de paramètres pour faciliter cette nouvelle connexion d’accès distant.</span><span class="sxs-lookup"><span data-stu-id="8ece4-112">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="8ece4-113">Ce nouvel ensemble de paramètres changera probablement mais pour l’instant, il vous permet de créer des sessions PowerShell SSH, avec lesquelles vous pouvez interagir depuis la ligne de commande, ou sur lesquelles vous pouvez appeler des commandes et des scripts.</span><span class="sxs-lookup"><span data-stu-id="8ece4-113">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span> <span data-ttu-id="8ece4-114">Vous spécifiez l’ordinateur cible avec le paramètre HostName et vous fournissez le nom d’utilisateur avec UserName.</span><span class="sxs-lookup"><span data-stu-id="8ece4-114">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span> <span data-ttu-id="8ece4-115">Lors de l’exécution interactive des applets de commande sur la ligne de commande PowerShell, un mot de passe vous est demandé.</span><span class="sxs-lookup"><span data-stu-id="8ece4-115">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span> <span data-ttu-id="8ece4-116">Vous pouvez cependant aussi utiliser l’authentification par clé SSH et fournir un chemin de fichier de clé privée avec le paramètre KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="8ece4-116">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="8ece4-117">Informations générales sur l’installation</span><span class="sxs-lookup"><span data-stu-id="8ece4-117">General setup information</span></span>

<span data-ttu-id="8ece4-118">SSH doit être installé sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="8ece4-118">SSH is required to be installed on all machines.</span></span> <span data-ttu-id="8ece4-119">Vous devez installer le client (`ssh.exe`) et le serveur (`sshd.exe`) pour pouvoir tester l’accès distant vers et depuis les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="8ece4-119">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span> <span data-ttu-id="8ece4-120">Pour Windows, vous devez installer [OpenSSH Win32 à partir de GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="8ece4-120">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="8ece4-121">Pour Linux, vous devrez installer SSH (y compris le serveur sshd) approprié pour votre plateforme.</span><span class="sxs-lookup"><span data-stu-id="8ece4-121">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="8ece4-122">Il vous faut également une version ou un package récent de PowerShell, provenant de GitHub et ayant la fonctionnalité d’accès distant SSH.</span><span class="sxs-lookup"><span data-stu-id="8ece4-122">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="8ece4-123">Les sous-systèmes SSH sont utilisés pour établir un processus PowerShell sur l’ordinateur distant ; le serveur SSH doit être configuré pour cela.</span><span class="sxs-lookup"><span data-stu-id="8ece4-123">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span> <span data-ttu-id="8ece4-124">De plus, vous devez activer l’authentification par mot de passe et éventuellement l’authentification basée sur une clé.</span><span class="sxs-lookup"><span data-stu-id="8ece4-124">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="8ece4-125">Configuration sur un ordinateur Windows</span><span class="sxs-lookup"><span data-stu-id="8ece4-125">Setup on Windows Machine</span></span>

1. <span data-ttu-id="8ece4-126">Installez la dernière version de [PowerShell Core pour Windows]</span><span class="sxs-lookup"><span data-stu-id="8ece4-126">Install the latest version of [PowerShell Core for Windows]</span></span>

   - <span data-ttu-id="8ece4-127">Vous pouvez savoir si elle dispose de la prise en charge de l’accès distant SSH en examinant les ensembles de paramètres pour `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="8ece4-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="8ece4-128">Installez la dernière version de [OpenSSH Win32] depuis GitHub en utilisant les instructions [d’installation]</span><span class="sxs-lookup"><span data-stu-id="8ece4-128">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
3. <span data-ttu-id="8ece4-129">Ouvrez le fichier sshd_config à l’emplacement où vous avez installé OpenSSH Win32</span><span class="sxs-lookup"><span data-stu-id="8ece4-129">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>

   - <span data-ttu-id="8ece4-130">Vérifiez que l’authentification par mot de passe est activée</span><span class="sxs-lookup"><span data-stu-id="8ece4-130">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="8ece4-131">OpenSSH pour Windows présente un bogue qui empêche les espaces de fonctionner dans les chemins exécutables du sous-système.</span><span class="sxs-lookup"><span data-stu-id="8ece4-131">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
     > <span data-ttu-id="8ece4-132">Consultez [ce problème sur GitHub pour plus d’informations](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="8ece4-132">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="8ece4-133">Une solution consiste à créer un lien symbolique vers le répertoire d’installation de Powershell sans espaces :</span><span class="sxs-lookup"><span data-stu-id="8ece4-133">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
     ```

     <span data-ttu-id="8ece4-134">puis de l’entrer dans le sous-système :</span><span class="sxs-lookup"><span data-stu-id="8ece4-134">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="8ece4-135">Vous pouvez éventuellement activer l’authentification par clé</span><span class="sxs-lookup"><span data-stu-id="8ece4-135">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="8ece4-136">Redémarrez le service sshd</span><span class="sxs-lookup"><span data-stu-id="8ece4-136">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="8ece4-137">Ajoutez le chemin où OpenSSH est installé à votre variable d’environnement PATH</span><span class="sxs-lookup"><span data-stu-id="8ece4-137">Add the path where OpenSSH is installed to your Path Env Variable</span></span>

   - <span data-ttu-id="8ece4-138">Il devrait s’agir de `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="8ece4-138">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="8ece4-139">Ceci permet au système de trouver ssh.exe</span><span class="sxs-lookup"><span data-stu-id="8ece4-139">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="8ece4-140">Configuration sur un ordinateur Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="8ece4-140">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="8ece4-141">Installez la dernière version [PowerShell Core pour Linux] à partir de GitHub</span><span class="sxs-lookup"><span data-stu-id="8ece4-141">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
2. <span data-ttu-id="8ece4-142">Installez [Ubuntu SSH] si nécessaire</span><span class="sxs-lookup"><span data-stu-id="8ece4-142">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="8ece4-143">Ouvrez le fichier sshd_config à l’emplacement /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="8ece4-143">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="8ece4-144">Vérifiez que l’authentification par mot de passe est activée</span><span class="sxs-lookup"><span data-stu-id="8ece4-144">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="8ece4-145">Ajoutez une entrée de sous-système PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ece4-145">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="8ece4-146">Vous pouvez éventuellement activer l’authentification par clé</span><span class="sxs-lookup"><span data-stu-id="8ece4-146">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="8ece4-147">Redémarrez le service sshd</span><span class="sxs-lookup"><span data-stu-id="8ece4-147">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="8ece4-148">Configuration sur un ordinateur MacOS</span><span class="sxs-lookup"><span data-stu-id="8ece4-148">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="8ece4-149">Installez la dernière version de [PowerShell Core pour MacOS]</span><span class="sxs-lookup"><span data-stu-id="8ece4-149">Install the latest [PowerShell Core for MacOS] build</span></span>

   - <span data-ttu-id="8ece4-150">Vérifiez que l’accès distant SSH est activé en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="8ece4-150">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="8ece4-151">Ouvrez `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="8ece4-151">Open `System Preferences`</span></span>
     - <span data-ttu-id="8ece4-152">Cliquez sur `Sharing`</span><span class="sxs-lookup"><span data-stu-id="8ece4-152">Click on `Sharing`</span></span>
     - <span data-ttu-id="8ece4-153">Vérifiez `Remote Login`, qui doit être `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="8ece4-153">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="8ece4-154">Autorisez l’accès aux utilisateurs appropriés</span><span class="sxs-lookup"><span data-stu-id="8ece4-154">Allow access to appropriate users</span></span>

2. <span data-ttu-id="8ece4-155">Ouvrez le fichier `sshd_config` à l’emplacement `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="8ece4-155">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="8ece4-156">Utiliser votre éditeur préféré ou</span><span class="sxs-lookup"><span data-stu-id="8ece4-156">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="8ece4-157">Vérifiez que l’authentification par mot de passe est activée</span><span class="sxs-lookup"><span data-stu-id="8ece4-157">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="8ece4-158">Ajoutez une entrée de sous-système PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ece4-158">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="8ece4-159">Vous pouvez éventuellement activer l’authentification par clé</span><span class="sxs-lookup"><span data-stu-id="8ece4-159">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="8ece4-160">Redémarrez le service sshd</span><span class="sxs-lookup"><span data-stu-id="8ece4-160">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="8ece4-161">Exemple d’accès distant PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ece4-161">PowerShell Remoting Example</span></span>

<span data-ttu-id="8ece4-162">Le moyen le plus simple de tester l’accès distant est simplement de l’essayer sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8ece4-162">The easiest way to test remoting is to just try it on a single machine.</span></span> <span data-ttu-id="8ece4-163">Je vais créer ici une session à distance avec le même ordinateur sur une zone Linux.</span><span class="sxs-lookup"><span data-stu-id="8ece4-163">Here I will create a remote session back to the same machine on a Linux box.</span></span> <span data-ttu-id="8ece4-164">Notez que j’utilise des applets de commande PowerShell à partir d’une invite de commandes : nous voyons donc des invites SSH demandant de vérifier l’ordinateur hôte ainsi que des demandes de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8ece4-164">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span> <span data-ttu-id="8ece4-165">Vous pouvez faire de même sur un ordinateur Windows pour vérifier que l’accès distant fonctionne, puis établir un accès distant entre des ordinateurs en changeant simplement le nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="8ece4-165">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="8ece4-166">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="8ece4-166">Known Issues</span></span>

<span data-ttu-id="8ece4-167">La commande sudo ne fonctionne pas dans une session à distance sur une machine Linux.</span><span class="sxs-lookup"><span data-stu-id="8ece4-167">The sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ece4-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ece4-168">See Also</span></span>

[<span data-ttu-id="8ece4-169">PowerShell Core pour Windows</span><span class="sxs-lookup"><span data-stu-id="8ece4-169">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="8ece4-170">PowerShell Core pour Linux</span><span class="sxs-lookup"><span data-stu-id="8ece4-170">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="8ece4-171">PowerShell Core pour MacOS</span><span class="sxs-lookup"><span data-stu-id="8ece4-171">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="8ece4-172">OpenSSH Win32</span><span class="sxs-lookup"><span data-stu-id="8ece4-172">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="8ece4-173">Installation</span><span class="sxs-lookup"><span data-stu-id="8ece4-173">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="8ece4-174">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="8ece4-174">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)