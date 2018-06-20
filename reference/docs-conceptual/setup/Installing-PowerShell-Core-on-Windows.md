# <a name="installing-powershell-core-on-windows"></a>Installation de PowerShell Core sous Windows

## <a name="msi"></a>MSI

Pour installer PowerShell sur un client Windows ou Windows Server (fonctionne sur Windows 7 SP1, Server 2008 R2 et les versions ultérieures), téléchargez le package MSI sur notre page de [versions][] GitHub.

Le fichier MSI se présente ainsi : `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->.

Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.

Un raccourci est placé dans le menu Démarrer lors de l’installation.

- Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\<version>`
- Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Conditions préalables

Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :

- Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10.
  Il est disponible par téléchargement direct ou sur Windows Update.
  Il est déjà installé sur les systèmes pris en charge où tous les correctifs sont installés (dont les packages facultatifs).
- Installer WMF (Windows Management Framework) 4.0 ou une version ultérieure sur Windows 7 et Windows Server 2008 R2.

## <a name="zip"></a>ZIP

Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés.
Notez que, lors de l’utilisation de l’archive ZIP, les conditions préalables ne sont pas vérifiées comme pour le package MSI.
Ainsi, pour que la communication à distance via WSMan puisse fonctionner correctement sur les versions de Windows antérieures à Windows 10, vous devez vérifier que ces [conditions préalables](#prerequisites) sont remplies.

## <a name="deploying-on-windows-iot"></a>Déploiement sur Windows IoT

Windows IoT est déjà équipé de Windows PowerShell que nous utiliserons pour déployer PowerShell Core 6.

1. Créez `PSSession` sur l’appareil cible

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Copiez le fichier ZIP sur l’appareil

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Connectez-vous à l’appareil et développez l’archive

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. Configurez la communication à distance avec PowerShell Core 6

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Connectez-vous au point de terminaison PowerShell Core 6 sur l’appareil

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a>Déploiement sur Nano Server

Ces instructions supposent qu’une version de PowerShell est déjà en cours d’exécution sur l’image Nano Server et qu’elle a été générée par le [Générateur d’images Nano Server](/windows-server/get-started/deploy-nano-server).
Nano Server est un système d’exploitation « administré à distance ». Les binaires Core peuvent être déployés à l’aide de deux méthodes différentes.

1. Hors connexion : montez le disque dur virtuel Nano Server et décompressez le contenu du fichier zip à l’emplacement que vous avez choisi dans l’image montée.
2. En ligne : transférez le fichier zip sur une session PowerShell et décompressez-le à l’emplacement que vous avez choisi.

Dans les deux cas, vous avez besoin du package de la version ZIP Windows 10 x64 et devez exécuter les commandes dans une instance de PowerShell « Administrateur ».

### <a name="offline-deployment-of-powershell-core"></a>Déploiement hors connexion de PowerShell Core

1. Utilisez votre utilitaire zip favori pour décompresser le package dans un répertoire au sein de l’image Nano Server montée.
2. Démontez l’image et démarrez-la.
3. Connectez-vous à l’instance de boîte de réception de Windows PowerShell.
4. Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Déploiement en ligne de PowerShell Core

La procédure suivante vous guide tout au long du déploiement de PowerShell Core sur une instance en cours d’exécution de Nano Server et la configuration de son point de terminaison distant.

- Connectez-vous à l’instance de boîte de réception de Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Copiez le fichier sur l’instance de Nano Server

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Entrez dans la session

  ```powershell
  Enter-PSSession $session
  ```

- Extrayez le fichier ZIP

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instructions pour créer un point de terminaison de communication à distance

PowerShell Core prend en charge le protocole de communication à distance PowerShell sur WSMan et SSH.
Pour plus d’informations, voir :

- [Accès distant SSH dans PowerShell Core] [ssh-remoting]
- [Communication à distance WSMan dans PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Instructions d’installation des artefacts

Nous publions une archive avec des bits CoreCLR sur chaque build CI avec [AppVeyor][].

Pour installer PowerShell Core à partir de l’artefact CoreCLR :

1. Téléchargez le package ZIP à partir de l’onglet des **artefacts** de la build spécifique.
2. Débloquez le fichier ZIP : cliquez avec le bouton droit dans l’Explorateur de fichiers -> Propriétés -> cochez la case Débloquer -> Appliquer
3. Extrayez le fichier zip dans le répertoire `bin`
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO --> [versions] : https://github.com/PowerShell/PowerShell/releases [ssh-remoting] : ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting] : ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor] : https://ci.appveyor.com/project/PowerShell/powershell