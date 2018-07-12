---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Prendre en main la fonctionnalité DSC (Desired State Configuration) pour Linux
ms.openlocfilehash: d5a4a17fbcffbbbd6df3dd902dbd104769b7d17e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893594"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Prendre en main la fonctionnalité DSC (Desired State Configuration) pour Linux

Cette rubrique explique comment prendre en main la fonctionnalité DSC (Desired State Configuration) PowerShell pour Linux. Pour obtenir des informations générales sur DSC, consultez [Prendre en main la fonctionnalité DSC (Desired State Configuration) Windows PowerShell](overview.md).

## <a name="supported-linux-operation-system-versions"></a>Versions du système d’exploitation Linux prises en charge

Les versions suivantes du système d’exploitation Linux prennent en charge DSC pour Linux.

- CentOS 5, 6 et 7 (x86/x64)
- Debian GNU/Linux 6, 7 et 8 (x86/x64)
- Oracle Linux 5, 6 et 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 et 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 et 12 (x86/x64)
- Ubuntu Server 12.04 LTS, 14.04 LTS et 16.04 LTS (x86/x64)

Le tableau suivant décrit les dépendances de package nécessaires pour utiliser DSC pour Linux.

|  Package nécessaire |  Description |  Version minimale |
|---|---|---|
| glibc| Bibliothèque GNU| 2…4 – 31.30|
| python| Python| 2.4 – 3.4|
| omiserver| Infrastructure de gestion ouverte| 1.0.8.1|
| openssl| Bibliothèques OpenSSL| 0.9.8 ou 1.0|
| ctypes| Bibliothèque CTypes Python| Identique à la version Python|
| libcurl| Bibliothèque client http cURL| 7.15.1|

## <a name="installing-dsc-for-linux"></a>Installation de DSC pour Linux

Vous devez installer [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) avant d’installer DSC pour Linux.

### <a name="installing-omi"></a>Installation d’OMI

DSC pour Linux nécessite le serveur CIM d’Open Management Infrastructure (OMI), version 1.0.8.1 ou ultérieure. Vous pouvez télécharger OMI à partir de The Open Group : [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Pour installer OMI, installez le package approprié pour le système Linux (.rpm ou .deb), la version d’OpenSSL (ssl_098 ou ssl_100) et l’architecture (x64/x86) que vous utilisez. Les packages RPM sont conçus pour les systèmes CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server et Oracle Linux. Les packages DEB sont conçus pour les systèmes Debian GNU/Linux et Ubuntu Server. Les packages ssl_098 et les packages ssl_100 sont conçus pour les ordinateurs avec OpenSSL 0.9.8 et les ordinateurs avec OpenSSL 1.0, respectivement.

> [!NOTE]
> Pour connaître la version d’OpenSSL installée, exécutez la commande `openssl version`.

Exécutez la commande suivante pour installer OMI sur un système CentOS 7 x64.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Installation de DSC

DSC pour Linux est disponible en téléchargement [ici](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).

Pour installer DSC, installez le package approprié pour le système Linux (.rpm ou .deb), la version d’OpenSSL (ssl_098 ou ssl_100) et l’architecture (x64/x86) que vous utilisez. Les packages RPM sont conçus pour les systèmes CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server et Oracle Linux. Les packages DEB sont conçus pour les systèmes Debian GNU/Linux et Ubuntu Server. Les packages ssl_098 et les packages ssl_100 sont conçus pour les ordinateurs avec OpenSSL 0.9.8 et les ordinateurs avec OpenSSL 1.0, respectivement.

> [!NOTE]
> Pour connaître la version d’OpenSSL installée, exécutez la commande « openssl version ».

Exécutez la commande suivante pour installer DSC sur un système CentOS 7 x64.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>Utilisation de DSC pour Linux

Les sections suivantes expliquent comment créer et exécuter des configurations DSC sur les ordinateurs Linux.

### <a name="creating-a-configuration-mof-document"></a>Création d’un document MOF de configuration

Le mot clé Windows PowerShell « Configuration » permet de créer une configuration pour les ordinateurs Linux, tout comme pour les ordinateurs Windows. Suivez les étapes décrites ci-dessous pour créer un document de configuration pour un ordinateur Linux à l’aide de Windows PowerShell.

1. Importez le module nx. Le module nx de Windows PowerShell contient le schéma des ressources intégrées pour DSC pour Linux. Il doit être installé sur votre ordinateur local et importé dans la configuration.

   - Pour installer le module nx, copiez le répertoire du module nx vers `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` ou `$PSHOME\Modules`. Le module nx est inclus dans le package d’installation (MSI) de DSC pour Linux. Pour importer le module nx dans votre configuration, utilisez la commande `Import-DSCResource` :

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. Définissez une configuration et créez le document de configuration :

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a>Transmission de la configuration en mode Push à l’ordinateur Linux.

Vous pouvez effectuer une transmission Push des documents de configuration (fichiers MOF) vers l’ordinateur Linux à l’aide de l’applet de commande [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration). Pour utiliser cette applet de commande avec les applets de commande [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) ou [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) à distance sur un ordinateur Linux, vous devez utiliser une session CIMSession. L’applet de commande [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) permet de créer une session CIMSession sur l’ordinateur Linux.

Le code suivant crée une session CIMSession pour DSC pour Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> [!NOTE]
> En mode « Push », les informations d’identification de l’utilisateur doivent correspondre à l’utilisateur racine sur l’ordinateur Linux.
> Seules les connexions SSL/TLS sont prises en charge pour DSC pour Linux. L’applet de commande `New-CimSession` doit être utilisée avec le paramètre –UseSSL défini sur $true.
> Le certificat SSL utilisé par OMI (pour DSC) est spécifié dans le fichier `/opt/omi/etc/omiserver.conf` avec les propriétés pemfile et keyfile.
> Si ce certificat n’est pas approuvé par l’ordinateur Windows où l’applet de commande [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) est exécutée, vous pouvez choisir d’ignorer la validation des certificats en spécifiant les options CIMSession suivantes : `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Exécutez la commande suivante pour transmettre en mode Push la configuration DSC vers le nœud Linux.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Distribution de la configuration à l’aide d’un serveur collecteur

Vous pouvez utiliser un serveur collecteur pour distribuer des configurations sur un ordinateur Linux, de la même manière que sur un ordinateur Windows. Pour obtenir des conseils d’utilisation d’un serveur collecteur, consultez [Serveurs collecteurs dans DSC Windows PowerShell](pullServer.md). Pour obtenir plus d’informations et connaître les limitations relatives à l’utilisation d’ordinateurs Linux avec un serveur collecteur, consultez les notes de publication concernant DSC pour Linux.

### <a name="working-with-configurations-locally"></a>Utilisation de configurations locales

DSC pour Linux fournit des scripts qui peuvent être utilisés avec une configuration de l’ordinateur Linux local. Ces scripts se trouvent dans le répertoire `/opt/microsoft/dsc/Scripts` et contiennent les éléments suivants :

- GetDscConfiguration.py

Retourne la configuration actuellement appliquée à l’ordinateur. Semblable à l’applet de commande `Get-DscConfiguration` Windows PowerShell.

`# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

Retourne la métaconfiguration actuellement appliquée à l’ordinateur. Similaire à l’applet de commande [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

`# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

Installe un module de ressources DSC personnalisé. Doit spécifier le chemin d’un fichier .zip contenant la bibliothèque d’objets partagés et les fichiers MOF de schéma du module.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

Supprime un module de ressources DSC personnalisé. Doit spécifier le nom du module à supprimer.

`# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

Applique un fichier MOF de configuration sur l’ordinateur. Similaire à l’applet de commande [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration). Doit spécifier le chemin du fichier MOF de configuration à appliquer.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

Applique un fichier MOF de métaconfiguration sur l’ordinateur. Similaire à l’applet de commande [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager). Doit spécifier le chemin du fichier MOF de métaconfiguration à appliquer.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>Fichiers journaux de DSC PowerShell pour Linux

Les messages concernant DSC pour Linux sont écrits dans les fichiers journaux suivants.

|Fichier journal|Répertoire|Description|
|---|---|---|
|**omiserver.log**|`/var/opt/omi/log`|Messages relatifs au fonctionnement du serveur CIM d’OMI.|
|**dsc.log**|`/var/opt/omi/log`|Messages relatifs au fonctionnement de LCM (Local Configuration Manager) et à l’utilisation des ressources DSC.|