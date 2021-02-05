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
# <a name="powershell-remoting-over-ssh"></a>Accès distant à PowerShell via SSH

## <a name="overview"></a>Vue d’ensemble

L’accès distant PowerShell utilise normalement WinRM pour la négociation de la connexion et le transport des données. SSH est désormais disponible pour les plateformes Linux et Windows, et permet une réelle communication à distance PowerShell multiplateforme.

WinRM fournit un modèle d’hébergement robuste pour les sessions distantes PowerShell. La communication à distance SSH ne prend actuellement en charge ni la configuration de points de terminaison distants ni l’administration JEA (Just Enough Administration).

La communication à distance SSH vous permet d’établir la communication à distance pour une session PowerShell de base entre des ordinateurs Windows et Linux. La communication à distance SSH crée un processus hôte PowerShell sur l’ordinateur cible en tant que sous-système SSH. Nous implémenterons prochainement un modèle d’hébergement général, similaire à WinRM, pour prendre en charge la configuration de point de terminaison et JEA.

Les cmdlets `New-PSSession``Enter-PSSession` et `Invoke-Command` ont maintenant un nouvel ensemble de paramètres pour prendre en charge cette nouvelle connexion de communication à distance.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Pour créer une session distante, vous devez spécifier l’ordinateur cible avec le paramètre **HostName**, et indiquer le nom d’utilisateur avec **UserName**. Lors de l’exécution des cmdlets de manière interactive, vous êtes invité à entrer un mot de passe. Vous pouvez également utiliser l’authentification par clé SSH à l’aide d’un fichier de clé privée avec le paramètre **KeyFilePath**. La création de clés pour l’authentification SSH varie selon la plateforme.

## <a name="general-setup-information"></a>Informations générales sur l’installation

PowerShell 6 ou version ultérieure et SSH doivent être installés sur tous les ordinateurs. Installez le client SSH (`ssh.exe`) et le serveur (`sshd.exe`) pour pouvoir communiquer à distance vers et à partir des ordinateurs. OpenSSH pour Windows est désormais disponible dans Windows 10 build 1809 et Windows Server 2019. Pour plus d’informations, consultez [Gérer Windows avec OpenSSH](/windows-server/administration/openssh/openssh_overview). Pour Linux, installez la version de SSH (avec le serveur sshd) qui correspond à votre plateforme. Vous devez aussi installer PowerShell à partir de GitHub pour obtenir la fonctionnalité de communication à distance SSH. Le serveur SSH doit être configuré pour créer un sous-système SSH destiné à héberger un processus PowerShell sur l’ordinateur distant. Par ailleurs, vous devez activer l’authentification par **mot de passe** ou **clé**.

## <a name="set-up-on-a-windows-computer"></a>Installation sur un ordinateur Windows

1. Installez la version la plus récente de PowerShell. Pour plus d’informations, consultez [Installation de PowerShell Core sur Windows](../../install/installing-powershell-core-on-windows.md#msi).

   Vous pouvez vérifier que PowerShell prend bien en charge la communication à distance SSH en listant les jeux de paramètres `New-PSSession`. Vous noterez la présence de noms de jeux de paramètres commençant par **SSH**. Ces jeux de paramètres comportent des paramètres **SSH**.

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. Installez la dernière version d’OpenSSH Win32. Pour obtenir des instructions d’installation, consultez [Bien démarrer avec OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).

   > [!NOTE]
   > Si vous voulez définir PowerShell en tant qu’interpréteur de commandes par défaut pour OpenSSH, consultez [Configuration de Windows pour OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).

1. Modifiez le fichier `sshd_config` situé dans `$env:ProgramData\ssh`.

   Vérifiez que l’authentification par mot de passe est activée :

   ```
   PasswordAuthentication yes
   ```

   Créez le sous-système SSH destiné à héberger un processus PowerShell sur l’ordinateur distant :

   ```
   Subsystem powershell c:/progra~1/powershell/7/pwsh.exe -sshs -NoLogo
   ```

   > [!NOTE]
   > L’emplacement par défaut de l’exécutable PowerShell est `c:/progra~1/powershell/7/pwsh.exe`. L’emplacement peut varier en fonction de la façon dont vous avez installé PowerShell.
   >
   > Vous devez utiliser le nom abrégé 8.3 pour les chemins de fichiers qui contiennent des espaces. OpenSSH pour Windows présente un bogue qui empêche les espaces de fonctionner dans les chemins exécutables du sous-système. Pour plus d’informations, consultez ce [problème GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).
   >
   > Le nom abrégé 8.3 du dossier `Program Files` dans Windows est généralement `Progra~1`. Cependant, vous pouvez utiliser la commande suivante pour vous en assurer :
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

   Vous pouvez éventuellement activer l’authentification par clé :

   ```
   PubkeyAuthentication yes
   ```

   Pour plus d’informations, consultez [Gestion des clés OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).

1. Redémarrez le service **sshd**.

   ```powershell
   Restart-Service sshd
   ```

1. Ajoutez le chemin où OpenSSH est installé à votre variable d’environnement Path. Par exemple : `C:\Program Files\OpenSSH\`. Cette entrée permet au système de trouver `ssh.exe`.

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a>Installation sur un ordinateur Linux Ubuntu 16.04

1. Installez la dernière version de PowerShell (voir [Installation de PowerShell Core sur Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)).
1. Installez [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. Modifiez le fichier `sshd_config` à l’emplacement `/etc/ssh`.

   Vérifiez que l’authentification par mot de passe est activée :

   ```
   PasswordAuthentication yes
   ```

   Vous pouvez éventuellement activer l’authentification par clé :

   ```
   PubkeyAuthentication yes
   ```

   Pour plus d’informations sur la création de clés SSH sur Ubuntu, consultez la Manpage concernant [ssh-keygen](http://manpages.ubuntu.com/manpages/xenial/man1/ssh-keygen.1.html).

   Ajoutez une entrée de sous-système PowerShell :

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > L’emplacement par défaut de l’exécutable PowerShell est `/usr/bin/pwsh`. L’emplacement peut varier en fonction de la façon dont vous avez installé PowerShell.

   Vous pouvez éventuellement activer l’authentification par clé :

   ```
   PubkeyAuthentication yes
   ```

1. Redémarrez le service **ssh**.

   ```bash
   sudo service ssh restart
   ```

## <a name="set-up-on-a-macos-computer"></a>Installation sur un ordinateur macOS

1. Installez la version la plus récente de PowerShell. Pour plus d’informations, consultez [Installation de PowerShell Core sur macOS](../../install/installing-powershell-core-on-macos.md).

   Vérifiez que l’accès distant SSH est activé en suivant ces étapes :

   1. Ouvrez `System Preferences`.
   1. Cliquez sur `Sharing`.
   1. Vérifiez `Remote Login` pour définir `Remote Login: On`.
   1. Autorisez l’accès aux utilisateurs appropriés.

1. Modifiez le fichier `sshd_config` à l’emplacement `/private/etc/ssh/sshd_config`.

   Utilisez un éditeur de texte tel que **nano** :

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   Vérifiez que l’authentification par mot de passe est activée :

   ```
   PasswordAuthentication yes
   ```

   Ajoutez une entrée de sous-système PowerShell :

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > L’emplacement par défaut de l’exécutable PowerShell est `/usr/local/bin/pwsh`. L’emplacement peut varier en fonction de la façon dont vous avez installé PowerShell.

   Vous pouvez éventuellement activer l’authentification par clé :

   ```
   PubkeyAuthentication yes
   ```

1. Redémarrez le service **sshd**.

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Authentification

L’accès distant PowerShell via SSH repose sur l’échange d’authentification entre le client SSH et le service SSH et n’implémente aucun schéma d’authentification par lui-même. Résultat : les schémas d’authentification éventuellement configurés, comme l’authentification multifacteur, sont gérés par SSH et sont indépendants de PowerShell. Par exemple, vous pouvez configurer le service SSH pour exiger une authentification par clé publique et un mot de passe à usage unique pour une sécurité renforcée. La configuration de l’authentification multifacteur sort du cadre de cette documentation. Reportez-vous à la documentation SSH pour savoir comment configurer correctement l’authentification multifacteur et vérifier qu’elle fonctionne en dehors de PowerShell avant d’essayer de l’utiliser avec l’accès distant PowerShell.

> [!NOTE]
> Les utilisateurs conservent les mêmes privilèges dans les sessions à distance. Cela signifie que les administrateurs ont accès à un interpréteur de commandes avec élévation de privilèges, contrairement aux utilisateurs normaux.

## <a name="powershell-remoting-example"></a>Exemple d’accès distant PowerShell

Le moyen le plus simple de tester l’accès distant est de l’essayer sur un seul ordinateur. Dans cet exemple, nous créons une session distante avec le même ordinateur Linux. Comme nous utilisons des applets de commande PowerShell de manière interactive, des invites SSH s’affichent pour demander de vérifier l’ordinateur hôte et de fournir un mot de passe. Vous pouvez faire la même chose sur un ordinateur Windows pour vérifier que l’accès distant fonctionne. Ensuite, établissez une communication à distance entre les ordinateurs en changeant le nom d’hôte.

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

### <a name="limitations"></a>Limites

- La commande **sudo** ne fonctionne pas dans une session distante sur un ordinateur Linux.

- PSRemoting sur SSH ne prend pas en charge les profils et n’a pas accès à `$PROFILE`. Une fois que vous avez ouvert une session, vous pouvez charger un profil en le « dot sourçant » avec le chemin de fichier complet. Cela n’a pas de rapports avec les profils SSH. Vous pouvez configurer le serveur SSH pour utiliser PowerShell comme interpréteur de commandes par défaut et charger un profil par le biais du SSH. Pour plus d’informations, consultez la documentation SSH.

- Avant PowerShell 7.1, la communication à distance via SSH ne prenait pas en charge les sessions à distance de deuxième saut. Cette fonctionnalité était limitée aux sessions qui utilisaient WinRM. PowerShell 7.1 permet à `Enter-PSSession` et `Enter-PSHostProcess` de fonctionner dans n’importe quelle session à distance interactive.

## <a name="see-also"></a>Voir aussi

[Installation de PowerShell Core sur Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[Installation de PowerShell Core sur macOS](../../install/installing-powershell-core-on-macos.md)

[Installation de PowerShell Core sur Windows](../../install/installing-powershell-core-on-windows.md#msi)

[Gérer Windows avec OpenSSH](/windows-server/administration/openssh/openssh_overview)

[Gestion des clés OpenSSH](/windows-server/administration/openssh/openssh_keymanagement)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
