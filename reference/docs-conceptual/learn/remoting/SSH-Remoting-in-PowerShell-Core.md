---
title: Accès distant à PowerShell via SSH
description: Accès distant dans PowerShell Core à l’aide de SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1d7bcb69c7e784bf745cb5c2633106ea53f6226a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58056530"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="5d769-103">Accès distant à PowerShell via SSH</span><span class="sxs-lookup"><span data-stu-id="5d769-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="5d769-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="5d769-104">Overview</span></span>

<span data-ttu-id="5d769-105">L’accès distant PowerShell utilise normalement WinRM pour la négociation de la connexion et le transport des données.</span><span class="sxs-lookup"><span data-stu-id="5d769-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="5d769-106">SSH est désormais disponible pour les plateformes Linux et Windows, et permet une réelle communication à distance PowerShell multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="5d769-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="5d769-107">WinRM fournit un modèle d’hébergement robuste pour les sessions distantes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d769-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="5d769-108">La communication à distance SSH ne prend actuellement en charge ni la configuration de points de terminaison distants ni l’administration JEA (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="5d769-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="5d769-109">La communication à distance SSH vous permet d’établir la communication à distance pour une session PowerShell de base entre des ordinateurs Windows et Linux.</span><span class="sxs-lookup"><span data-stu-id="5d769-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="5d769-110">La communication à distance SSH crée un processus hôte PowerShell sur l’ordinateur cible en tant que sous-système SSH.</span><span class="sxs-lookup"><span data-stu-id="5d769-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="5d769-111">Nous implémenterons prochainement un modèle d’hébergement général, similaire à WinRM, pour prendre en charge la configuration de point de terminaison et JEA.</span><span class="sxs-lookup"><span data-stu-id="5d769-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="5d769-112">Les cmdlets `New-PSSession` `Enter-PSSession` et `Invoke-Command` ont maintenant un nouvel ensemble de paramètres pour prendre en charge cette nouvelle connexion de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="5d769-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="5d769-113">Pour créer une session distante, vous spécifiez l’ordinateur cible avec le paramètre `HostName` et vous fournissez le nom d’utilisateur avec `UserName`.</span><span class="sxs-lookup"><span data-stu-id="5d769-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="5d769-114">Lors de l’exécution des cmdlets de manière interactive, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="5d769-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="5d769-115">Vous pouvez également utiliser l’authentification par clé SSH à l’aide d’un fichier de clé privée avec le paramètre `KeyFilePath`.</span><span class="sxs-lookup"><span data-stu-id="5d769-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="5d769-116">Informations générales sur l’installation</span><span class="sxs-lookup"><span data-stu-id="5d769-116">General setup information</span></span>

<span data-ttu-id="5d769-117">SSH doit être installé sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="5d769-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="5d769-118">Installez le client SSH (`ssh.exe`) et le serveur (`sshd.exe`) pour pouvoir communiquer à distance vers et depuis les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="5d769-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="5d769-119">OpenSSH pour Windows est désormais disponible dans Windows 10 build 1809 et Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="5d769-119">OpenSSH for Windows is now availabe in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="5d769-120">Pour plus d’informations, consultez [OpenSSH pour Windows](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="5d769-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="5d769-121">Pour Linux, installez SSH (y compris le serveur sshd) approprié pour votre plateforme.</span><span class="sxs-lookup"><span data-stu-id="5d769-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="5d769-122">Vous devez également installer PowerShell Core à partir de GitHub pour obtenir la fonctionnalité de communication à distance SSH.</span><span class="sxs-lookup"><span data-stu-id="5d769-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="5d769-123">Le serveur SSH doit être configuré pour créer un sous-système SSH afin d’héberger un processus PowerShell sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5d769-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="5d769-124">Vous devez également configurer l’activation de l’authentification par mot de passe ou clé.</span><span class="sxs-lookup"><span data-stu-id="5d769-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="5d769-125">Configuration sur un ordinateur Windows</span><span class="sxs-lookup"><span data-stu-id="5d769-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="5d769-126">Installez la dernière version de [PowerShell Core pour Windows](../../install/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="5d769-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="5d769-127">Vous pouvez savoir si elle dispose de la prise en charge de l’accès distant SSH en examinant les ensembles de paramètres pour `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="5d769-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="5d769-128">Installez la dernière version d’OpenSSH Win32.</span><span class="sxs-lookup"><span data-stu-id="5d769-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="5d769-129">Pour obtenir des instructions d’installation, consultez [Installation d’OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="5d769-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="5d769-130">Modifiez le fichier `sshd_config` situé dans `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="5d769-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="5d769-131">Vérifiez que l’authentification par mot de passe est activée</span><span class="sxs-lookup"><span data-stu-id="5d769-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="5d769-132">OpenSSH pour Windows présente un bogue qui empêche les espaces de fonctionner dans les chemins exécutables du sous-système.</span><span class="sxs-lookup"><span data-stu-id="5d769-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="5d769-133">Pour plus d’informations, consultez [ce problème GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="5d769-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="5d769-134">Une solution consiste à créer un lien symbolique vers le répertoire d’installation de PowerShell sans espaces :</span><span class="sxs-lookup"><span data-stu-id="5d769-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="5d769-135">puis de l’entrer dans le sous-système :</span><span class="sxs-lookup"><span data-stu-id="5d769-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="5d769-136">Vous pouvez éventuellement activer l’authentification par clé</span><span class="sxs-lookup"><span data-stu-id="5d769-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="5d769-137">Redémarrez le service sshd</span><span class="sxs-lookup"><span data-stu-id="5d769-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="5d769-138">Ajoutez le chemin où OpenSSH est installé à votre variable d’environnement Path.</span><span class="sxs-lookup"><span data-stu-id="5d769-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="5d769-139">Par exemple, `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="5d769-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="5d769-140">Cette entrée permet au système de trouver ssh.exe.</span><span class="sxs-lookup"><span data-stu-id="5d769-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="5d769-141">Configuration sur un ordinateur Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="5d769-141">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="5d769-142">Installez la dernière version [PowerShell Core pour Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) à partir de GitHub</span><span class="sxs-lookup"><span data-stu-id="5d769-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="5d769-143">Installez [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) si nécessaire</span><span class="sxs-lookup"><span data-stu-id="5d769-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="5d769-144">Ouvrez le fichier sshd_config à l’emplacement /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="5d769-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="5d769-145">Vérifiez que l’authentification par mot de passe est activée</span><span class="sxs-lookup"><span data-stu-id="5d769-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="5d769-146">Ajoutez une entrée de sous-système PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d769-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="5d769-147">Vous pouvez éventuellement activer l’authentification par clé</span><span class="sxs-lookup"><span data-stu-id="5d769-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="5d769-148">Redémarrez le service sshd</span><span class="sxs-lookup"><span data-stu-id="5d769-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="5d769-149">Configuration sur un ordinateur MacOS</span><span class="sxs-lookup"><span data-stu-id="5d769-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="5d769-150">Installez la dernière version de [PowerShell Core pour MacOS](../../install/installing-powershell-core-on-macos.md)</span><span class="sxs-lookup"><span data-stu-id="5d769-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="5d769-151">Vérifiez que l’accès distant SSH est activé en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="5d769-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="5d769-152">Ouvrez `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="5d769-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="5d769-153">Cliquez sur `Sharing`</span><span class="sxs-lookup"><span data-stu-id="5d769-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="5d769-154">Vérifiez `Remote Login`, qui doit être `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="5d769-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="5d769-155">Autorisez l’accès aux utilisateurs appropriés</span><span class="sxs-lookup"><span data-stu-id="5d769-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="5d769-156">Ouvrez le fichier `sshd_config` à l’emplacement `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="5d769-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="5d769-157">Utiliser votre éditeur préféré ou</span><span class="sxs-lookup"><span data-stu-id="5d769-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="5d769-158">Vérifiez que l’authentification par mot de passe est activée</span><span class="sxs-lookup"><span data-stu-id="5d769-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="5d769-159">Ajoutez une entrée de sous-système PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d769-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="5d769-160">Vous pouvez éventuellement activer l’authentification par clé</span><span class="sxs-lookup"><span data-stu-id="5d769-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="5d769-161">Redémarrez le service sshd</span><span class="sxs-lookup"><span data-stu-id="5d769-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="5d769-162">Authentification</span><span class="sxs-lookup"><span data-stu-id="5d769-162">Authentication</span></span>

<span data-ttu-id="5d769-163">L’accès distant PowerShell via SSH repose sur l’échange d’authentification entre le client SSH et le service SSH et n’implémente aucun schéma d’authentification par lui-même.</span><span class="sxs-lookup"><span data-stu-id="5d769-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="5d769-164">Cela signifie que les schémas d’authentification éventuellement configurés, comme l’authentification multifacteur, sont gérés par SSH et sont indépendants de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d769-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="5d769-165">Par exemple, vous pouvez configurer le service SSH pour exiger une authentification par clé publique, doublée d’un mot de passe à usage unique pour une sécurité renforcée.</span><span class="sxs-lookup"><span data-stu-id="5d769-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="5d769-166">La configuration de l’authentification multifacteur sort du cadre de cette documentation.</span><span class="sxs-lookup"><span data-stu-id="5d769-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="5d769-167">Reportez-vous à la documentation SSH pour savoir comment configurer correctement l’authentification multifacteur et vérifier qu’elle fonctionne en dehors de PowerShell avant d’essayer de l’utiliser avec l’accès distant PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d769-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="5d769-168">Exemple d’accès distant PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d769-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="5d769-169">Le moyen le plus simple de tester la communication à distance est de l’essayer sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5d769-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="5d769-170">Dans cet exemple, nous créons une session distante avec le même ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="5d769-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="5d769-171">Nous utilisons des cmdlets PowerShell de manière interactive, afin de voir les invites SSH demandant de vérifier l’ordinateur hôte ainsi que des demandes de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="5d769-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="5d769-172">Vous pouvez faire la même chose sur un ordinateur Windows pour vérifier que la communication à distance fonctionne.</span><span class="sxs-lookup"><span data-stu-id="5d769-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="5d769-173">Puis, établissez la communication à distance entre les ordinateurs en modifiant le nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="5d769-173">Then remote between machines by changing the host name.</span></span>

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
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
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

### <a name="known-issues"></a><span data-ttu-id="5d769-174">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="5d769-174">Known Issues</span></span>

<span data-ttu-id="5d769-175">La commande sudo ne fonctionne pas dans une session distante sur un ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="5d769-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d769-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d769-176">See Also</span></span>

[<span data-ttu-id="5d769-177">PowerShell Core pour Windows</span><span class="sxs-lookup"><span data-stu-id="5d769-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="5d769-178">PowerShell Core pour Linux</span><span class="sxs-lookup"><span data-stu-id="5d769-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="5d769-179">PowerShell Core pour MacOS</span><span class="sxs-lookup"><span data-stu-id="5d769-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="5d769-180">OpenSSH pour Windows</span><span class="sxs-lookup"><span data-stu-id="5d769-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="5d769-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="5d769-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
