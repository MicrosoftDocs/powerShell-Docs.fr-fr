---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configurer une machine virtuelle au démarrage initial à l’aide de DSC
ms.openlocfilehash: 7b9ebc6c818aa39365759945667426c8976997e5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401750"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Configurer une machine virtuelle au démarrage initial à l’aide de DSC

> [!IMPORTANT]
> S'applique à : Windows PowerShell 5.0

## <a name="requirements"></a>Spécifications

> [!NOTE]
> La clé de Registre **DSCAutomationHostEnabled** décrite dans cette rubrique n’est pas disponible dans PowerShell 4.0.
> Pour plus d’informations sur la configuration de nouvelles machines virtuelles au démarrage initial dans PowerShell 4.0, consultez [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Pour exécuter ces exemples, vous avez besoin des éléments suivants :

- Un disque dur virtuel démarrable avec lequel travailler. Vous pouvez télécharger une image ISO avec une copie d’évaluation de Windows Server 2016 auprès du [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). Vous trouverez des instructions sur la création d’un disque dur virtuel à partir d’une image ISO dans [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- Un ordinateur hôte où Hyper-V est activé. Pour plus d’informations, consultez [Vue d’ensemble d’Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  À l’aide de DSC, vous pouvez automatiser l’installation et la configuration de logiciels d’un ordinateur au démarrage initial.
  Pour cela, vous injectez un document MOF de configuration ou une métaconfiguration dans un média démarrable (comme un disque dur virtuel) afin qu’ils soient exécutés lors du processus de démarrage initial.
  Ce comportement est spécifié par la [clé de Registre DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) sous `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.
  Par défaut, la valeur de cette clé est 2, ce qui permet à DSC de s’exécuter au moment du démarrage.

  Si vous ne voulez pas que DSC s’exécute au démarrage, définissez la valeur de la [clé de Registre DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) sur 0.

- Injecter un document MOF de configuration dans un disque dur virtuel
- Injecter une métaconfiguration DSC dans un disque dur virtuel
- Désactiver DSC au démarrage

> [!NOTE]
> Vous pouvez injecter à la fois `Pending.mof` et `MetaConfig.mof` dans un ordinateur en même temps.
> Si les deux fichiers sont présents, les paramètres spécifiés dans `MetaConfig.mof` sont prioritaires.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Injecter un document MOF de configuration dans un disque dur virtuel

Pour promulguer une configuration au démarrage initial, vous pouvez injecter un document MOF de configuration compilé dans le disque dur virtuel sous la forme de son fichier `Pending.mof`.
Si la clé de Registre **DSCAutomationHostEnabled** est définie sur 2 (la valeur par défaut), DSC applique la configuration définie par `Pending.mof` quand l’ordinateur démarre pour la première fois.

Pour cet exemple, nous utilisons la configuration suivante, qui installe IIS sur le nouvel ordinateur :

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Pour injecter le document MOF de configuration sur le disque dur virtuel

1. Montez le disque dur virtuel dans lequel vous voulez injecter la configuration en appelant l’applet de commande [Mount-VHD](/powershell/module/hyper-v/mount-vhd). Par exemple :

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Sur un ordinateur exécutant PowerShell 5.0 ou ultérieur, enregistrez la configuration ci-dessus (**SampleIISInstall**) dans un fichier de script PowerShell (.ps1).

3. Dans une console PowerShell, accédez au dossier où vous avez enregistré le fichier .ps1.

4. Exécutez les commandes PowerShell suivantes pour compiler le document MOF. Pour plus d’informations sur la compilation des configurations DSC, consultez [Configurations DSC](../configurations/configurations.md) :

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. Cette opération crée un fichier `localhost.mof` dans un nouveau dossier nommé `SampleIISInstall`.
   Renommez le fichier en `Pending.mof` et déplacez-le à l’emplacement approprié sur le disque dur virtuel en utilisant l’applet de commande [Move-Item](/powershell/module/microsoft.powershell.management/move-item). Par exemple :

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. Démontez le disque dur virtuel en appelant l’applet de commande [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd). Par exemple :

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. Créez une machine virtuelle en utilisant le disque dur virtuel où vous avez installé le document MOF DSC.

Après le démarrage initial et l’installation du système d’exploitation, IIS est installé.
Vous pouvez le vérifier en appelant l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Injecter une métaconfiguration DSC dans un disque dur virtuel

Vous pouvez également configurer un ordinateur pour extraire une configuration au démarrage initial en injectant une métaconfiguration (consultez [Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig.md)) dans le disque dur virtuel sous la forme de son fichier `MetaConfig.mof`.
Si la clé de Registre **DSCAutomationHostEnabled** est définie sur 2 (la valeur par défaut), DSC applique la métaconfiguration définie par `MetaConfig.mof` au gestionnaire de configuration local quand l’ordinateur démarre pour la première fois.
Si la métaconfiguration spécifie que le gestionnaire de configuration local doit extraire les configurations à partir d’un serveur collecteur, l’ordinateur tente d’extraire une configuration auprès de ce serveur collecteur au démarrage initial.
Pour plus d’informations sur la configuration d’un serveur collecteur DSC, consultez [Configuration d’un serveur collecteur web DSC](../pull-server/pullServer.md).

Pour cet exemple, nous utilisons la configuration décrite dans la section précédente (**SampleIISInstall**) et la métaconfiguration suivante :

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Pour injecter le document MOF de métaconfiguration sur le disque dur virtuel

1. Montez le disque dur virtuel dans lequel vous voulez injecter la métaconfiguration en appelant l’applet de commande [Mount-VHD](/powershell/module/hyper-v/mount-vhd). Par exemple :

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [Configurez un serveur collecteur web DSC](../pull-server/pullServer.md), puis enregistrez la configuration **SampleIISInistall** dans le dossier approprié.

3. Sur un ordinateur exécutant PowerShell 5.0 ou ultérieur, enregistrez la métaconfiguration ci-dessus (**PullClientBootstrap**) dans un fichier de script PowerShell (.ps1).

4. Dans une console PowerShell, accédez au dossier où vous avez enregistré le fichier .ps1.

5. Exécutez les commandes PowerShell suivantes pour compiler le document MOF de métaconfiguration (pour plus d’informations sur la compilation des configurations DSC, consultez [Configurations DSC](../configurations/configurations.md) :

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. Cette opération crée un fichier `localhost.meta.mof` dans un nouveau dossier nommé `PullClientBootstrap`.
   Renommez le fichier en `MetaConfig.mof` et déplacez-le à l’emplacement approprié sur le disque dur virtuel en utilisant l’applet de commande [Move-Item](/powershell/module/microsoft.powershell.management/move-item).

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. Démontez le disque dur virtuel en appelant l’applet de commande [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd). Par exemple :

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. Créez une machine virtuelle en utilisant le disque dur virtuel où vous avez installé le document MOF DSC.

Après le démarrage initial et l’installation du système d’exploitation, DSC extrait la configuration auprès du serveur collecteur et IIS est installé.
Vous pouvez le vérifier en appelant l’applet de commande [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).

## <a name="disable-dsc-at-boot-time"></a>Désactiver DSC au démarrage

Par défaut, la valeur de la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` est définie sur 2, ce qui permet à une configuration DSC de exécuter si l’ordinateur est en état d’attente ou actif. Si vous ne voulez pas qu’une configuration s’exécute au démarrage initial, vous devez définir la valeur de cette clé sur 0 :

1. Montez le disque dur virtuel en appelant l’applet de commande [Mount-VHD](/powershell/module/hyper-v/mount-vhd). Par exemple :

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Chargez la sous-clé `HKLM\Software` du Registre à partir du disque dur virtuel en appelant `reg load`.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. Accédez à `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` à l’aide du fournisseur de Registre de PowerShell.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. Remplacez la valeur de `DSCAutomationHostEnabled` par 0.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. Déchargez le Registre en exécutant les commandes suivantes :

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Voir aussi

[Configurations DSC](../configurations/configurations.md)

[Clé de Registre DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

[Configuration du gestionnaire de configuration local](../managing-nodes/metaConfig.md)

[Configuration d’un serveur collecteur web DSC](../pull-server/pullServer.md)
