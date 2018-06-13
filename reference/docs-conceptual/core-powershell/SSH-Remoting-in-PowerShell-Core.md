# <a name="powershell-remoting-over-ssh"></a>Accès distant à PowerShell via SSH

## <a name="overview"></a>Vue d’ensemble

L’accès distant PowerShell utilise normalement WinRM pour la négociation de la connexion et le transport des données.
SSH a été choisi pour cette implémentation de l’accès distant, car il est maintenant disponible pour les plateformes Linux et Windows, et permet un véritable accès distant PowerShell multiplateforme.
Cependant, WinRM fournit également un modèle d’hébergement robuste pour les sessions à distance PowerShell, ce que cette implémentation ne fait pas encore.
Cela signifie aussi que la configuration de point de terminaison distant PowerShell et JEA (Just Enough Administration) ne sont pas encore pris en charge dans cette implémentation.

L’accès distant SSH PowerShell vous permet un accès distant pour une session PowerShell de base entre des ordinateurs Windows et Linux.
Pour cela, vous devez créer un processus hébergeant PowerShell sur l’ordinateur cible en tant que sous-système SSH.
Au final, ce sera remplacé en un modèle d’hébergement plus général, similaire au mode de fonctionnement de WinRM pour prendre en charge la configuration de point de terminaison et JEA.

Les applets de commande New-PSSession, Enter-PSSession et Invoke-Command ont maintenant un nouvel ensemble de paramètres pour faciliter cette nouvelle connexion d’accès distant

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Ce nouvel ensemble de paramètres changera probablement mais pour l’instant, il vous permet de créer des sessions PowerShell SSH, avec lesquelles vous pouvez interagir depuis la ligne de commande, ou sur lesquelles vous pouvez appeler des commandes et des scripts.
Vous spécifiez l’ordinateur cible avec le paramètre HostName et vous fournissez le nom d’utilisateur avec UserName.
Lors de l’exécution interactive des applets de commande sur la ligne de commande PowerShell, un mot de passe vous est demandé.
Vous pouvez cependant aussi utiliser l’authentification par clé SSH et fournir un chemin de fichier de clé privée avec le paramètre KeyFilePath.

## <a name="general-setup-information"></a>Informations générales sur l’installation

SSH doit être installé sur tous les ordinateurs.
Vous devez installer le client (ssh.exe) et le serveur (sshd.exe) pour pouvoir tester l’accès distant vers et depuis les ordinateurs.
Pour Windows, vous devez installer [OpenSSH Win32 à partir de GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Pour Linux, vous devrez installer SSH (y compris le serveur sshd) approprié pour votre plateforme.
Il vous faut également une version ou un package récent de PowerShell, provenant de GitHub et ayant la fonctionnalité d’accès distant SSH.
Les sous-systèmes SSH sont utilisés pour établir un processus PowerShell sur l’ordinateur distant ; le serveur SSH doit être configuré pour cela.
De plus, vous devez activer l’authentification par mot de passe et éventuellement l’authentification basée sur une clé.

## <a name="setup-on-windows-machine"></a>Configuration sur un ordinateur Windows

1. Installez la dernière version de [PowerShell Core pour Windows]
    - Vous pouvez savoir si elle dispose de la prise en charge de l’accès distant SSH en examinant les ensembles de paramètres pour New-PSSession

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. Installez la dernière version de [OpenSSH Win32] depuis GitHub en utilisant les instructions d’[Installation]
1. Ouvrez le fichier sshd_config à l’emplacement où vous avez installé OpenSSH Win32
    - Vérifiez que l’authentification par mot de passe est activée

    ```
    PasswordAuthentication yes
    ```

    - Ajoutez une entrée de sous-système PowerShell et remplacez `c:/program files/powershell/6.0.0/pwsh.exe` par le chemin correct vers la version que vous voulez utiliser

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - Vous pouvez éventuellement activer l’authentification par clé

    ```
    PubkeyAuthentication yes
    ```

1. Redémarrez le service sshd

    ```powershell
    Restart-Service sshd
    ```

1. Ajoutez le chemin où OpenSSH est installé à votre variable d’environnement PATH
    - Il devrait s’agir de `C:\Program Files\OpenSSH\`
    - Ceci permet au système de trouver ssh.exe

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Configuration sur un ordinateur Linux (Ubuntu 14.04)

1. Installez la dernière version [PowerShell Core pour Linux] à partir de GitHub
1. Installez [Ubuntu SSH] si nécessaire

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. Ouvrez le fichier sshd_config à l’emplacement /etc/ssh
    - Vérifiez que l’authentification par mot de passe est activée

    ```
    PasswordAuthentication yes
    ```

    - Ajoutez une entrée de sous-système PowerShell

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - Vous pouvez éventuellement activer l’authentification par clé

    ```
    PubkeyAuthentication yes
    ```

1. Redémarrez le service sshd

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a>Configuration sur un ordinateur MacOS

1. Installez la dernière version de [PowerShell Core pour MacOS]
    - Vérifiez que l’accès distant SSH est activé en suivant ces étapes :
      - Ouvrez `System Preferences`
      - Cliquez sur `Sharing`
      - Vérifiez `Remote Login`, qui doit être `Remote Login: On`
      - Autorisez l’accès aux utilisateurs appropriés
1. Ouvrez le fichier `sshd_config` à l’emplacement `/private/etc/ssh/sshd_config`
    - Utiliser votre éditeur préféré ou

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - Vérifiez que l’authentification par mot de passe est activée

    ```
    PasswordAuthentication yes
    ```

    - Ajoutez une entrée de sous-système PowerShell

    ```
    Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - Vous pouvez éventuellement activer l’authentification par clé

    ```
    PubkeyAuthentication yes
    ```

1. Redémarrez le service sshd

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a>Exemple d’accès distant PowerShell

Le moyen le plus simple de tester l’accès distant est simplement de l’essayer sur un seul ordinateur.
Je vais créer ici une session à distance avec le même ordinateur sur une zone Linux.
Notez que j’utilise des applets de commande PowerShell à partir d’une invite de commandes : nous voyons donc des invites SSH demandant de vérifier l’ordinateur hôte ainsi que des demandes de mot de passe.
Vous pouvez faire de même sur un ordinateur Windows pour vérifier que l’accès distant fonctionne, puis établir un accès distant entre des ordinateurs en changeant simplement le nom d’hôte.

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
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

### <a name="known-issues"></a>Problèmes connus

1. La commande sudo ne fonctionne pas dans la session à distance sur un ordinateur Linux.

[PowerShell Core pour Windows]: ../setup/installing-powershell-core-on-windows.md#msi
[PowerShell Core pour Linux]: ../setup/installing-powershell-core-on-linux.md#ubuntu-1404
[PowerShell Core pour MacOS]: ../setup/installing-powershell-core-on-macos.md
[OpenSSH Win32]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
