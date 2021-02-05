---
title: Accès distant à PowerShell via SSH
ms.date: 10/19/2020
description: Explique comment configurer le protocole SSH pour l’accès distant à PowerShell.
ms.openlocfilehash: c3373ac30fd915d42e8c9fb7f1eae348a2aee7f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501335"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="78a6b-103">Accès distant à PowerShell via SSH</span><span class="sxs-lookup"><span data-stu-id="78a6b-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="78a6b-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="78a6b-104">Overview</span></span>

<span data-ttu-id="78a6b-105">L’accès distant PowerShell utilise normalement WinRM pour la négociation de la connexion et le transport des données.</span><span class="sxs-lookup"><span data-stu-id="78a6b-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="78a6b-106">SSH est désormais disponible pour les plateformes Linux et Windows, et permet une réelle communication à distance PowerShell multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="78a6b-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="78a6b-107">WinRM fournit un modèle d’hébergement robuste pour les sessions distantes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a6b-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="78a6b-108">La communication à distance SSH ne prend actuellement en charge ni la configuration de points de terminaison distants ni l’administration JEA (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="78a6b-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="78a6b-109">La communication à distance SSH vous permet d’établir la communication à distance pour une session PowerShell de base entre des ordinateurs Windows et Linux.</span><span class="sxs-lookup"><span data-stu-id="78a6b-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="78a6b-110">La communication à distance SSH crée un processus hôte PowerShell sur l’ordinateur cible en tant que sous-système SSH.</span><span class="sxs-lookup"><span data-stu-id="78a6b-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="78a6b-111">Nous implémenterons prochainement un modèle d’hébergement général, similaire à WinRM, pour prendre en charge la configuration de point de terminaison et JEA.</span><span class="sxs-lookup"><span data-stu-id="78a6b-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="78a6b-112">Les cmdlets `New-PSSession``Enter-PSSession` et `Invoke-Command` ont maintenant un nouvel ensemble de paramètres pour prendre en charge cette nouvelle connexion de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="78a6b-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="78a6b-113">Pour créer une session distante, vous devez spécifier l’ordinateur cible avec le paramètre **HostName**, et indiquer le nom d’utilisateur avec **UserName**.</span><span class="sxs-lookup"><span data-stu-id="78a6b-113">To create a remote session, you specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="78a6b-114">Lors de l’exécution des cmdlets de manière interactive, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="78a6b-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="78a6b-115">Vous pouvez également utiliser l’authentification par clé SSH à l’aide d’un fichier de clé privée avec le paramètre **KeyFilePath**.</span><span class="sxs-lookup"><span data-stu-id="78a6b-115">You can also use SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span> <span data-ttu-id="78a6b-116">La création de clés pour l’authentification SSH varie selon la plateforme.</span><span class="sxs-lookup"><span data-stu-id="78a6b-116">Creating keys for SSH authentication varies by platform.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="78a6b-117">Informations générales sur l’installation</span><span class="sxs-lookup"><span data-stu-id="78a6b-117">General setup information</span></span>

<span data-ttu-id="78a6b-118">PowerShell 6 ou version ultérieure et SSH doivent être installés sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="78a6b-118">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="78a6b-119">Installez le client SSH (`ssh.exe`) et le serveur (`sshd.exe`) pour pouvoir communiquer à distance vers et à partir des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="78a6b-119">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="78a6b-120">OpenSSH pour Windows est désormais disponible dans Windows 10 build 1809 et Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="78a6b-120">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="78a6b-121">Pour plus d’informations, consultez [Gérer Windows avec OpenSSH](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="78a6b-121">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="78a6b-122">Pour Linux, installez la version de SSH (avec le serveur sshd) qui correspond à votre plateforme.</span><span class="sxs-lookup"><span data-stu-id="78a6b-122">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="78a6b-123">Vous devez aussi installer PowerShell à partir de GitHub pour obtenir la fonctionnalité de communication à distance SSH.</span><span class="sxs-lookup"><span data-stu-id="78a6b-123">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="78a6b-124">Le serveur SSH doit être configuré pour créer un sous-système SSH destiné à héberger un processus PowerShell sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="78a6b-124">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="78a6b-125">Par ailleurs, vous devez activer l’authentification par **mot de passe** ou **clé**.</span><span class="sxs-lookup"><span data-stu-id="78a6b-125">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="78a6b-126">Installation sur un ordinateur Windows</span><span class="sxs-lookup"><span data-stu-id="78a6b-126">Set up on a Windows computer</span></span>

1. <span data-ttu-id="78a6b-127">Installez la version la plus récente de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a6b-127">Install the latest version of PowerShell.</span></span> <span data-ttu-id="78a6b-128">Pour plus d’informations, consultez [Installation de PowerShell Core sur Windows](../../install/installing-powershell-core-on-windows.md#msi).</span><span class="sxs-lookup"><span data-stu-id="78a6b-128">For more information, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="78a6b-129">Vous pouvez vérifier que PowerShell prend bien en charge la communication à distance SSH en listant les jeux de paramètres `New-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-129">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="78a6b-130">Vous noterez la présence de noms de jeux de paramètres commençant par **SSH**.</span><span class="sxs-lookup"><span data-stu-id="78a6b-130">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="78a6b-131">Ces jeux de paramètres comportent des paramètres **SSH**.</span><span class="sxs-lookup"><span data-stu-id="78a6b-131">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="78a6b-132">Installez la dernière version d’OpenSSH Win32.</span><span class="sxs-lookup"><span data-stu-id="78a6b-132">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="78a6b-133">Pour obtenir des instructions d’installation, consultez [Bien démarrer avec OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="78a6b-133">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="78a6b-134">Si vous voulez définir PowerShell en tant qu’interpréteur de commandes par défaut pour OpenSSH, consultez [Configuration de Windows pour OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span><span class="sxs-lookup"><span data-stu-id="78a6b-134">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="78a6b-135">Modifiez le fichier `sshd_config` situé dans `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-135">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="78a6b-136">Vérifiez que l’authentification par mot de passe est activée :</span><span class="sxs-lookup"><span data-stu-id="78a6b-136">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="78a6b-137">Créez le sous-système SSH destiné à héberger un processus PowerShell sur l’ordinateur distant :</span><span class="sxs-lookup"><span data-stu-id="78a6b-137">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/7/pwsh.exe -sshs -NoLogo
   ```

   > [!NOTE]
   > <span data-ttu-id="78a6b-138">L’emplacement par défaut de l’exécutable PowerShell est `c:/progra~1/powershell/7/pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-138">The default location of the PowerShell executable is `c:/progra~1/powershell/7/pwsh.exe`.</span></span> <span data-ttu-id="78a6b-139">L’emplacement peut varier en fonction de la façon dont vous avez installé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a6b-139">The location can vary depending on how you installed PowerShell.</span></span>
   >
   > <span data-ttu-id="78a6b-140">Vous devez utiliser le nom abrégé 8.3 pour les chemins de fichiers qui contiennent des espaces.</span><span class="sxs-lookup"><span data-stu-id="78a6b-140">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="78a6b-141">OpenSSH pour Windows présente un bogue qui empêche les espaces de fonctionner dans les chemins exécutables du sous-système.</span><span class="sxs-lookup"><span data-stu-id="78a6b-141">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="78a6b-142">Pour plus d’informations, consultez ce [problème GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="78a6b-142">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="78a6b-143">Le nom abrégé 8.3 du dossier `Program Files` dans Windows est généralement `Progra~1`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-143">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="78a6b-144">Cependant, vous pouvez utiliser la commande suivante pour vous en assurer :</span><span class="sxs-lookup"><span data-stu-id="78a6b-144">However, you can use the following command to make sure:</span></span>
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   <span data-ttu-id="78a6b-145">Vous pouvez éventuellement activer l’authentification par clé :</span><span class="sxs-lookup"><span data-stu-id="78a6b-145">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="78a6b-146">Pour plus d’informations, consultez [Gestion des clés OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="78a6b-146">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="78a6b-147">Redémarrez le service **sshd**.</span><span class="sxs-lookup"><span data-stu-id="78a6b-147">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="78a6b-148">Ajoutez le chemin où OpenSSH est installé à votre variable d’environnement Path.</span><span class="sxs-lookup"><span data-stu-id="78a6b-148">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="78a6b-149">Par exemple : `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-149">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="78a6b-150">Cette entrée permet au système de trouver `ssh.exe`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-150">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="78a6b-151">Installation sur un ordinateur Linux Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="78a6b-151">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="78a6b-152">Installez la dernière version de PowerShell (voir [Installation de PowerShell Core sur Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)).</span><span class="sxs-lookup"><span data-stu-id="78a6b-152">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="78a6b-153">Installez [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span><span class="sxs-lookup"><span data-stu-id="78a6b-153">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="78a6b-154">Modifiez le fichier `sshd_config` à l’emplacement `/etc/ssh`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-154">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="78a6b-155">Vérifiez que l’authentification par mot de passe est activée :</span><span class="sxs-lookup"><span data-stu-id="78a6b-155">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="78a6b-156">Vous pouvez éventuellement activer l’authentification par clé :</span><span class="sxs-lookup"><span data-stu-id="78a6b-156">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="78a6b-157">Pour plus d’informations sur la création de clés SSH sur Ubuntu, consultez la Manpage concernant [ssh-keygen](http://manpages.ubuntu.com/manpages/xenial/man1/ssh-keygen.1.html).</span><span class="sxs-lookup"><span data-stu-id="78a6b-157">For more information about creating SSH keys on Ubuntu, see the manpage for [ssh-keygen](http://manpages.ubuntu.com/manpages/xenial/man1/ssh-keygen.1.html).</span></span>

   <span data-ttu-id="78a6b-158">Ajoutez une entrée de sous-système PowerShell :</span><span class="sxs-lookup"><span data-stu-id="78a6b-158">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > <span data-ttu-id="78a6b-159">L’emplacement par défaut de l’exécutable PowerShell est `/usr/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-159">The default location of the PowerShell executable is `/usr/bin/pwsh`.</span></span> <span data-ttu-id="78a6b-160">L’emplacement peut varier en fonction de la façon dont vous avez installé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a6b-160">The location can vary depending on how you installed PowerShell.</span></span>

   <span data-ttu-id="78a6b-161">Vous pouvez éventuellement activer l’authentification par clé :</span><span class="sxs-lookup"><span data-stu-id="78a6b-161">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="78a6b-162">Redémarrez le service **ssh**.</span><span class="sxs-lookup"><span data-stu-id="78a6b-162">Restart the **ssh** service.</span></span>

   ```bash
   sudo service ssh restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="78a6b-163">Installation sur un ordinateur macOS</span><span class="sxs-lookup"><span data-stu-id="78a6b-163">Set up on a macOS computer</span></span>

1. <span data-ttu-id="78a6b-164">Installez la version la plus récente de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a6b-164">Install the latest version of PowerShell.</span></span> <span data-ttu-id="78a6b-165">Pour plus d’informations, consultez [Installation de PowerShell Core sur macOS](../../install/installing-powershell-core-on-macos.md).</span><span class="sxs-lookup"><span data-stu-id="78a6b-165">For more information, [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="78a6b-166">Vérifiez que l’accès distant SSH est activé en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="78a6b-166">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="78a6b-167">Ouvrez `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-167">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="78a6b-168">Cliquez sur `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-168">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="78a6b-169">Vérifiez `Remote Login` pour définir `Remote Login: On`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-169">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="78a6b-170">Autorisez l’accès aux utilisateurs appropriés.</span><span class="sxs-lookup"><span data-stu-id="78a6b-170">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="78a6b-171">Modifiez le fichier `sshd_config` à l’emplacement `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-171">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="78a6b-172">Utilisez un éditeur de texte tel que **nano** :</span><span class="sxs-lookup"><span data-stu-id="78a6b-172">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="78a6b-173">Vérifiez que l’authentification par mot de passe est activée :</span><span class="sxs-lookup"><span data-stu-id="78a6b-173">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="78a6b-174">Ajoutez une entrée de sous-système PowerShell :</span><span class="sxs-lookup"><span data-stu-id="78a6b-174">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > <span data-ttu-id="78a6b-175">L’emplacement par défaut de l’exécutable PowerShell est `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-175">The default location of the PowerShell executable is `/usr/local/bin/pwsh`.</span></span> <span data-ttu-id="78a6b-176">L’emplacement peut varier en fonction de la façon dont vous avez installé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a6b-176">The location can vary depending on how you installed PowerShell.</span></span>

   <span data-ttu-id="78a6b-177">Vous pouvez éventuellement activer l’authentification par clé :</span><span class="sxs-lookup"><span data-stu-id="78a6b-177">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="78a6b-178">Redémarrez le service **sshd**.</span><span class="sxs-lookup"><span data-stu-id="78a6b-178">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="78a6b-179">Authentification</span><span class="sxs-lookup"><span data-stu-id="78a6b-179">Authentication</span></span>

<span data-ttu-id="78a6b-180">L’accès distant PowerShell via SSH repose sur l’échange d’authentification entre le client SSH et le service SSH et n’implémente aucun schéma d’authentification par lui-même.</span><span class="sxs-lookup"><span data-stu-id="78a6b-180">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="78a6b-181">Résultat : les schémas d’authentification éventuellement configurés, comme l’authentification multifacteur, sont gérés par SSH et sont indépendants de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a6b-181">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="78a6b-182">Par exemple, vous pouvez configurer le service SSH pour exiger une authentification par clé publique et un mot de passe à usage unique pour une sécurité renforcée.</span><span class="sxs-lookup"><span data-stu-id="78a6b-182">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="78a6b-183">La configuration de l’authentification multifacteur sort du cadre de cette documentation.</span><span class="sxs-lookup"><span data-stu-id="78a6b-183">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="78a6b-184">Reportez-vous à la documentation SSH pour savoir comment configurer correctement l’authentification multifacteur et vérifier qu’elle fonctionne en dehors de PowerShell avant d’essayer de l’utiliser avec l’accès distant PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a6b-184">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="78a6b-185">Les utilisateurs conservent les mêmes privilèges dans les sessions à distance.</span><span class="sxs-lookup"><span data-stu-id="78a6b-185">Users retain the same privileges in remote sessions.</span></span> <span data-ttu-id="78a6b-186">Cela signifie que les administrateurs ont accès à un interpréteur de commandes avec élévation de privilèges, contrairement aux utilisateurs normaux.</span><span class="sxs-lookup"><span data-stu-id="78a6b-186">Meaning, Administrators have access to an elevated shell, and normal users will not.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="78a6b-187">Exemple d’accès distant PowerShell</span><span class="sxs-lookup"><span data-stu-id="78a6b-187">PowerShell remoting example</span></span>

<span data-ttu-id="78a6b-188">Le moyen le plus simple de tester l’accès distant est de l’essayer sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="78a6b-188">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="78a6b-189">Dans cet exemple, nous créons une session distante avec le même ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="78a6b-189">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="78a6b-190">Comme nous utilisons des applets de commande PowerShell de manière interactive, des invites SSH s’affichent pour demander de vérifier l’ordinateur hôte et de fournir un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="78a6b-190">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="78a6b-191">Vous pouvez faire la même chose sur un ordinateur Windows pour vérifier que l’accès distant fonctionne.</span><span class="sxs-lookup"><span data-stu-id="78a6b-191">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="78a6b-192">Ensuite, établissez une communication à distance entre les ordinateurs en changeant le nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="78a6b-192">Then, remote between computers by changing the host name.</span></span>

```powershell
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
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

```
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
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

### <a name="limitations"></a><span data-ttu-id="78a6b-193">Limites</span><span class="sxs-lookup"><span data-stu-id="78a6b-193">Limitations</span></span>

- <span data-ttu-id="78a6b-194">La commande **sudo** ne fonctionne pas dans une session distante sur un ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="78a6b-194">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

- <span data-ttu-id="78a6b-195">PSRemoting sur SSH ne prend pas en charge les profils et n’a pas accès à `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="78a6b-195">PSRemoting over SSH does not support Profiles and does not have access to `$PROFILE`.</span></span> <span data-ttu-id="78a6b-196">Une fois que vous avez ouvert une session, vous pouvez charger un profil en le « dot sourçant » avec le chemin de fichier complet.</span><span class="sxs-lookup"><span data-stu-id="78a6b-196">Once in a session, you can load a profile by dot sourcing the profile with the full filepath.</span></span> <span data-ttu-id="78a6b-197">Cela n’a pas de rapports avec les profils SSH.</span><span class="sxs-lookup"><span data-stu-id="78a6b-197">This is not related to SSH profiles.</span></span> <span data-ttu-id="78a6b-198">Vous pouvez configurer le serveur SSH pour utiliser PowerShell comme interpréteur de commandes par défaut et charger un profil par le biais du SSH.</span><span class="sxs-lookup"><span data-stu-id="78a6b-198">You can configure the SSH server to use PowerShell as the default shell and to load a profile through SSH.</span></span> <span data-ttu-id="78a6b-199">Pour plus d’informations, consultez la documentation SSH.</span><span class="sxs-lookup"><span data-stu-id="78a6b-199">See the SSH documentation for more information.</span></span>

- <span data-ttu-id="78a6b-200">Avant PowerShell 7.1, la communication à distance via SSH ne prenait pas en charge les sessions à distance de deuxième saut.</span><span class="sxs-lookup"><span data-stu-id="78a6b-200">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="78a6b-201">Cette fonctionnalité était limitée aux sessions qui utilisaient WinRM.</span><span class="sxs-lookup"><span data-stu-id="78a6b-201">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="78a6b-202">PowerShell 7.1 permet à `Enter-PSSession` et `Enter-PSHostProcess` de fonctionner dans n’importe quelle session à distance interactive.</span><span class="sxs-lookup"><span data-stu-id="78a6b-202">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <a name="see-also"></a><span data-ttu-id="78a6b-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78a6b-203">See also</span></span>

[<span data-ttu-id="78a6b-204">Installation de PowerShell Core sur Linux</span><span class="sxs-lookup"><span data-stu-id="78a6b-204">Installing PowerShell Core on Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="78a6b-205">Installation de PowerShell Core sur macOS</span><span class="sxs-lookup"><span data-stu-id="78a6b-205">Installing PowerShell Core on macOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="78a6b-206">Installation de PowerShell Core sur Windows</span><span class="sxs-lookup"><span data-stu-id="78a6b-206">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="78a6b-207">Gérer Windows avec OpenSSH</span><span class="sxs-lookup"><span data-stu-id="78a6b-207">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="78a6b-208">Gestion des clés OpenSSH</span><span class="sxs-lookup"><span data-stu-id="78a6b-208">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="78a6b-209">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="78a6b-209">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
