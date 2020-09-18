---
title: Installation de PowerShell sur Windows
description: Informations sur l’installation de PowerShell sur Windows
ms.date: 09/14/2020
ms.openlocfilehash: 8f1b60ef6bfef5c2434b0affabb5e0e7af392b96
ms.sourcegitcommit: 30c0c1563f8e840f24b65297e907f3583d90e677
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90574451"
---
# <a name="installing-powershell-on-windows"></a>Installation de PowerShell sur Windows

Il existe plusieurs façons d’installer PowerShell Core sur Windows.

## <a name="prerequisites"></a>Prérequis

La dernière version de PowerShell est prise en charge sur Windows 7 SP1, Server 2008 R2 et versions ultérieures.

Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :

- Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10. Il est disponible par téléchargement direct ou sur Windows Update. Ce package est déjà installé sur les systèmes où tous les correctifs sont installés.
- Installer WMF (Windows Management Framework) 4.0 ou une version ultérieure sur Windows 7 et Windows Server 2008 R2. Pour plus d’informations sur WMF, voir [Vue d’ensemble de WMF](/powershell/scripting/wmf/overview).

## <a name="download-the-installer-package"></a>Télécharger le package du programme d’installation

Pour installer PowerShell sur Windows, téléchargez le package d’installation à partir de notre page de [versions][releases] GitHub. Faites défiler jusqu'à la section **Ressources** de la page de versions. Il est possible que la section **Ressources** soit réduite et que vous deviez cliquer dessus pour la développer.

## <a name="installing-the-msi-package"></a><a id="msi" />Installation du package MSI

Le fichier MSI ressemble à `PowerShell-<version>-win-<os-arch>.msi`. Par exemple :

- `PowerShell-7.0.3-win-x64.msi`
- `PowerShell-7.0.3-win-x86.msi`

Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.

Le programme d’installation crée un raccourci dans le menu Démarrer de Windows.

- Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\<version>`
- Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

> [!NOTE]
> PowerShell 7 s’installe dans un nouveau répertoire et s’exécute côte à côte avec Windows PowerShell 5.1. Pour PowerShell Core 6.x, PowerShell 7 est une mise à niveau sur place qui supprime PowerShell Core 6.x.
>
> - PowerShell 7 est installé sur `$env:ProgramFiles\PowerShell\7`
> - Le dossier `$env:ProgramFiles\PowerShell\7` est ajouté à `$env:PATH`
> - Le dossier `$env:ProgramFiles\PowerShell\6` est supprimé
>
> Si vous devez exécuter PowerShell 6 côte à côte avec PowerShell 7, réinstallez PowerShell 6 suivant la méthode [d’installation ZIP](#zip).

### <a name="administrative-install-from-the-command-line"></a>Installation administrative à partir de la ligne de commande

Les packages MSI peuvent être installés à partir de la ligne de commande, ce qui permet aux administrateurs de déployer des packages sans interaction de l’utilisateur. Le package MSI inclut les propriétés suivantes pour contrôler les options d’installation :

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : cette propriété contrôle l’option permettant d’ajouter l’élément **Ouvrir PowerShell** au menu contextuel dans l’Explorateur Windows.
- **ENABLE_PSREMOTING** : cette propriété contrôle l’option permettant d’activer la communication à distance PowerShell pendant l’installation.
- **REGISTER_MANIFEST** : cette propriété contrôle l’option permettant d’enregistrer le manifeste de journalisation des événements Windows.

L’exemple suivant montre comment installer PowerShell sans assistance avec toutes les options d’installation activées.

```powershell
msiexec.exe /package PowerShell-7.0.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Pour obtenir une liste complète des options de ligne de commande pour `Msiexec.exe`, consultez [Options de ligne de commande](/windows/desktop/Msi/command-line-options).

### <a name="registry-keys-created-during-installation"></a>Clés de Registre créées pendant l'installation

À compter de PowerShell 7.1, le package MSI crée des clés de Registre qui stockent l’emplacement d’installation et la version de PowerShell. Ces valeurs se trouvent sous `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`. La valeur de `<GUID>` est unique pour chaque type de build (version ou préversion), version principale et architecture.

|    Libérer    | Architecture |                                          Clé de Registre                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| Version 7.1 |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| Version 7.1 |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| Préversion 7.1 |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| Préversion 7.1 |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

Cela peut être utilisé par les administrateurs et les développeurs pour trouver le chemin de PowerShell. Les valeurs de `<GUID>` sont les mêmes pour toutes les mises en production de préversions et de versions mineures. Les valeurs de `<GUID>` sont modifiées pour chaque version majeure.

## <a name="installing-the-msix-package"></a><a id="msix" />Installation du package MSIX

> [!NOTE]
> Le package MSIX n’est pas officiellement pris en charge pour le moment. Nous continuons à créer le package à des fins de test interne uniquement.

Pour installer manuellement le package MSIX sur un client Windows 10, téléchargez le package MSIX à partir de notre page des [versions][releases] de GitHub. Faites défiler jusqu'à la section **Ressources** de la version que vous souhaitez installer. Il est possible que la section Ressources soit réduite et que vous deviez cliquer dessus pour la développer.

Le fichier MSIX se présente ainsi : `PowerShell-<version>-win-<os-arch>.msix`.

Pour installer le package, vous devez utiliser la cmdlet `Add-AppxPackage`.

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="installing-the-zip-package"></a><a id="zip" />Installation du package ZIP

Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés. Contrairement aux packages MSI, l’installation de l’archive ZIP ne vérifie pas les prérequis. Téléchargez l’archive ZIP à partir de la page des [mises en production][releases]. Selon la façon dont vous téléchargez le fichier, vous devrez peut-être débloquer le fichier avec l’applet de commande `Unblock-File`. Décompressez le contenu à l’emplacement de votre choix et exécutez `pwsh.exe` à partir de celui-ci. Pour que la communication à distance via WSMan fonctionne correctement, vérifiez que vous respectez bien les [prérequis](#prerequisites).

## <a name="deploying-on-windows-10-iot-enterprise"></a>Déploiement sur Windows 10 IoT Entreprise

Windows 10 IoT Entreprise contient Windows PowerShell, que l’on peut utiliser pour déployer PowerShell 7.

1. Créez `PSSession` sur l’appareil cible

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. Copiez le fichier ZIP sur l’appareil

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. Connectez-vous à l’appareil et développez l’archive

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. Configurez la communication à distance avec PowerShell 7

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

1. Connectez-vous au point de terminaison PowerShell 7 sur l’appareil

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a>Déploiement sur Windows 10 IoT Core

Windows 10 IoT Core ajoute Windows PowerShell lorsque vous incluez la fonctionnalité *IOT_POWERSHELL*, que nous pouvons utiliser pour déployer PowerShell 7.
Les étapes définies ci-dessus pour Windows 10 IoT Entreprise peuvent également être suivies pour IoT Core.

Pour ajouter la dernière version de PowerShell dans l’image d’expédition, utilisez la commande [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) pour inclure le package dans la zone de travail et ajouter la fonctionnalité *OPENSRC_POWERSHELL* à votre image.

> [!NOTE]
> Pour l’architecture ARM64, Windows PowerShell n’est pas ajouté lorsque vous incluez *IOT_POWERSHELL*. L’installation basée sur zip ne fonctionne donc pas.
> Vous devrez utiliser la commande Import-PSCoreRelease pour l’ajouter dans l’image.

## <a name="deploying-on-nano-server"></a>Déploiement sur Nano Server

Ces instructions partent du principe que Nano Server est un système d’exploitation sans périphériques de contrôle (« headless ») sur lequel une version de PowerShell est déjà en cours d’exécution. Pour plus d’informations, consultez la documentation [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).

Il existe deux façons différentes de déployer des binaires PowerShell.

1. Hors connexion : montez le disque dur virtuel Nano Server et décompressez le contenu du fichier zip à l’emplacement que vous avez choisi dans l’image montée.
1. En ligne : transférez le fichier zip sur une session PowerShell et décompressez-le à l’emplacement que vous avez choisi.

Dans les deux cas, vous avez besoin du package ZIP de la version de Windows 10 x64. Exécutez les commandes dans une instance « Administrateur » de PowerShell.

### <a name="offline-deployment-of-powershell"></a>Déploiement hors connexion de PowerShell

1. Utilisez votre utilitaire zip favori pour décompresser le package dans un répertoire au sein de l’image Nano Server montée.
1. Démontez l’image et démarrez-la.
1. Connectez-vous à l’instance intégrée de Windows PowerShell.
1. Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell"></a>Déploiement en ligne de PowerShell

Déployez PowerShell sur Nano Server en procédant comme suit.

- Connectez-vous à l’instance intégrée de Windows PowerShell

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

- Extrayez le fichier zip.

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="install-as-a-net-global-tool"></a>Installation en tant qu’outil global .NET

Si vous avez déjà installé le [kit SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant [qu’outil global .NET](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Le programme d’installation de l’outil dotnet ajoute `$env:USERPROFILE\dotnet\tools` à votre variable d’environnement `$env:PATH`. Toutefois, le `$env:PATH` de l’interpréteur de commandes en cours d’exécution n’a pas été mis à jour. Vous pouvez démarrer PowerShell à partir d’un nouvel interpréteur de commandes en tapant `pwsh`.

## <a name="install-powershell-via-winget"></a>Installer PowerShell via Winget

L’outil de ligne de commande `winget` permet aux développeurs de découvrir, d’installer, de mettre à niveau, de supprimer et de configurer des applications sur des ordinateurs Windows 10. Cet outil est l’interface cliente du service Gestionnaire de package Windows.

> [!NOTE]
> L’outil `winget` est actuellement une préversion. Toutes les fonctionnalités planifiées ne sont pas disponibles pour l’instant.
> Les options et les fonctionnalités de l’outil sont sujettes à modification. Vous ne devriez pas utiliser cette méthode dans un scénario de déploiement de production. Pour obtenir la liste des configurations requises et des instructions d’installation, consultez la documentation [winget].

Les commandes suivantes peuvent être utilisées pour installer PowerShell à l’aide des packages `winget` publiés :

1. Rechercher la version la plus récente de PowerShell

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.0.3
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.0-preview.5
   ```

1. Installer une version de PowerShell à l’aide du paramètre `--exact`

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="how-to-create-a-remoting-endpoint"></a>Comment créer un point de terminaison de communication à distance

PowerShell prend en charge le protocole de communication à distance PowerShell (PSRP) sur WSMan et SSH. Pour plus d'informations, consultez les pages suivantes :

- [Communication à distance SSH dans PowerShell Core][ssh-remoting]
- [Communication à distance WSMan dans PowerShell Core][wsman-remoting]

## <a name="installation-support"></a>Prise en charge de l’installation

Microsoft prend en charge les méthodes d’installation mentionnées dans ce document. D’autres méthodes d’installation peuvent être disponibles à partir d’autres sources. Même s’il est possible que ces outils et méthodes fonctionnent, Microsoft ne peut pas prendre en charge ces méthodes.

<!-- link references -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
