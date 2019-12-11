---
title: Installation de PowerShell Core sous Windows
description: Informations sur l’installation de PowerShell Core sur Windows
ms.date: 08/06/2018
ms.openlocfilehash: 00a1d8064a3c1ec6608a46415bbabb8d98d880f0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416788"
---
# <a name="installing-powershell-core-on-windows"></a>Installation de PowerShell Core sous Windows

Il existe plusieurs façons d’installer PowerShell Core dans Windows.

> [!TIP]
> Si vous avez déjà installé le kit [SDK .NET Core](/dotnet/core/sdk), il est facile d’installer PowerShell en tant qu’[outil global .NET](/dotnet/core/tools/global-tools).
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a>Conditions préalables

Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :

- Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10. Il est disponible par téléchargement direct ou sur Windows Update. Il est déjà installé sur les systèmes pris en charge où tous les correctifs sont installés (dont les packages facultatifs).
- Installer WMF (Windows Management Framework) 4.0 ou une version ultérieure sur Windows 7 et Windows Server 2008 R2. Pour plus d’informations sur WMF, voir [Vue d’ensemble de WMF](/powershell/scripting/wmf/overview).

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />Installation du package MSI

Pour installer PowerShell sur un client Windows ou Windows Server (fonctionne sur Windows 7 SP1, Server 2008 R2, et versions ultérieures), téléchargez le package MSI à partir de notre page de [versions][releases] GitHub. Faites défiler jusqu'à la section **Ressources** de la version que vous souhaitez installer. Il est possible que la section Ressources soit réduite et que vous deviez cliquer dessus pour la développer.

Le fichier MSI ressemble à ceci : `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.

Le programme d’installation crée un raccourci dans le menu Démarrer de Windows.

- Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\<version>`
- Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="administrative-install-from-the-command-line"></a>Installation administrative à partir de la ligne de commande

Les packages MSI peuvent être installés à partir de la ligne de commande. Cela permet aux administrateurs de déployer des packages sans l’intervention de l’utilisateur. Le package MSI pour PowerShell inclut les propriétés suivantes pour contrôler les options d’installation :

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : cette propriété contrôle l’option permettant d’ajouter l’élément **Ouvrir PowerShell** au menu contextuel dans l’Explorateur Windows.
- **ENABLE_PSREMOTING** : cette propriété contrôle l’option permettant d’activer la communication à distance PowerShell pendant l’installation.
- **REGISTER_MANIFEST** : cette propriété contrôle l’option permettant d’enregistrer le manifeste de journalisation des événements Windows.

Les exemples suivants montrent comment installer PowerShell Core sans assistance avec toutes les options d’installation activées.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Pour obtenir une liste complète des options de ligne de commande pour Msiexec.exe, consultez [Options de ligne de commande](/windows/desktop/Msi/command-line-options).

## <a name="a-idmsix-installing-the-msix-package"></a><a id="msix" />Installation du package MSIX

Pour installer manuellement le package MSIX sur un client Windows 10, téléchargez le package MSIX à partir de notre page des [versions][releases] de GitHub. Faites défiler jusqu'à la section **Ressources** de la version que vous souhaitez installer. Il est possible que la section Ressources soit réduite et que vous deviez cliquer dessus pour la développer.

Le fichier MSI ressemble à ceci : `PowerShell-<version>-win-<os-arch>.msix`

Une fois téléchargé, vous ne pouvez pas simplement double-cliquer sur le programme d’installation, car ce package requiert l’utilisation de ressources non virtualisées.  Pour installer, vous devez utiliser la cmdlet `Add-AppxPackage` :

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />Installation du package ZIP

Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés. Notez que, lors de l’utilisation de l’archive ZIP, les conditions préalables ne sont pas vérifiées comme pour le package MSI. Pour que la communication à distance via WSMan fonctionne correctement, vérifiez que vous respectez bien les [prérequis](#prerequisites).

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
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Connectez-vous à l’appareil et développez l’archive

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. Configurez la communication à distance avec PowerShell Core 6

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Connectez-vous au point de terminaison PowerShell Core 6 sur l’appareil

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
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
4. Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

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

- Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [« technique d’une autre instance »](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="how-to-create-a-remoting-endpoint"></a>Comment créer un point de terminaison de communication à distance

PowerShell Core prend en charge le protocole de communication à distance PowerShell sur WSMan et SSH. Pour plus d’informations, voir :

- [Communication à distance SSH dans PowerShell Core][ssh-remoting]
- [Communication à distance WSMan dans PowerShell Core][wsman-remoting]

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
