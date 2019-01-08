---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Obtention d’objets WMI Get WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401179"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Obtention d’objets WMI (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Obtention d’objets WMI (Get-WmiObject)

WMI (Windows Management Instrumentation) est une technologie majeure pour l’administration du système Windows, car elle expose un vaste éventail d’informations de manière uniforme. Compte tenu de tout ce que WMI permet de réaliser, l’applet de commande Windows PowerShell pour l’accès aux objets WMI, **Get-WmiObject**, est l’une des plus utiles pour travailler réellement. Nous allons aborder l’utilisation de l’applet de commande Get-WmiObject pour accéder aux objets WMI, puis expliquer comment utiliser des objets WMI pour réaliser des opérations spécifiques.

### <a name="listing-wmi-classes"></a>Affichage de la liste des classes WMI

Le premier problème que rencontrent la plupart des utilisateurs de WMI est de comprendre ce que WMI permet de faire. Les classes WMI décrivent les ressources qui peuvent être gérées. Il existe des centaines de classes WMI, dont certaines contiennent des dizaines de propriétés.

L’applet de commande **Get-WmiObject** résout ce problème en rendant WMI détectable. Vous pouvez obtenir la liste des classes WMI disponibles sur l’ordinateur local en tapant ce qui suit :

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Vous pouvez récupérer les mêmes informations à partir d’un ordinateur distant à l’aide du paramètre ComputerName, en spécifiant une adresse IP ou un nom d’ordinateur :

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

La liste de classes retournée par des ordinateurs distants peut varier selon le système d’exploitation que l’ordinateur exécute et les extensions WMI ajoutées par les applications installées.

> [!NOTE]
> Lorsque vous utilisez l’applet de commande Get-WmiObject pour vous connecter à un ordinateur distant, celui-ci doit exécuter WMI et, dans la configuration par défaut, le compte que vous utilisez doit figurer dans le groupe Administrateurs local sur l’ordinateur distant. Windows PowerShell ne doit pas nécessairement être installé sur le système distant. Cela permet d’administrer des systèmes d’exploitation qui n’exécutent pas Windows PowerShell, mais disposent de WMI.

Lors de la connexion au système local, vous pouvez même inclure le nom d’ordinateur à l’aide du paramètre ComputerName. Vous pouvez utiliser le nom de l’ordinateur local, son adresse IP (ou l’adresse de bouclage 127.0.0.1), ou le style de WMI « . » comme nom d’ordinateur. Si vous exécutez Windows PowerShell sur un ordinateur nommé Admin01 dont l’adresse IP est 192.168.1.90, les commandes suivantes retournent toutes la classe WMI pour cet ordinateur :

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Par défaut, l’applet de commande Get-WmiObject utilise l’espace de noms root/cimv2. Si vous souhaitez spécifier un autre espace de noms WMI, utilisez le paramètre **Namespace** en spécifiant le chemin d’accès à l’espace de noms correspondant :

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Affichage des détails de classe WMI

Si vous connaissez déjà le nom d’une classe WMI, vous pouvez l’utiliser pour obtenir des informations immédiatement. Par exemple, une des classes WMI couramment utilisées pour récupérer des informations sur un ordinateur est **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Bien que nous montrions tous les paramètres, la commande peut être exprimée de façon plus concise. Le paramètre **ComputerName** n’est pas nécessaire lors de la connexion au système local. Nous le montrons pour illustrer le cas le plus général, et vous rappeler la disponibilité de ce paramètre. Par défaut, l’**espace de noms** est root/cimv2. Vous pouvez également l’omettre. Enfin, la plupart des applets de commande permettent l’omission du nom de paramètres communs. Avec l’applet de commande Get-WmiObject, si aucun nom n’est spécifié pour le premier paramètre, Windows PowerShell traite celui-ci en tant que paramètre **Class**. Cela signifie que la dernière commande pourrait avoir été émise en tapant ce qui suit :

```powershell
Get-WmiObject Win32_OperatingSystem
```

La classe **Win32_OperatingSystem** a beaucoup plus de propriétés que celles affichées ici. Vous pouvez utiliser l’applet de commande Get-Member pour voir toutes les propriétés. Les propriétés d’une classe WMI sont automatiquement disponibles, comme d’autres propriétés de l’objet :

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Affichage de propriétés autres que par défaut avec les applets de commande Format

Si vous souhaitez des informations contenues dans la classe **Win32_OperatingSystem** qui ne sont pas affichées par défaut, vous pouvez les afficher à l’aide des applets de commande **Format**. Par exemple, si vous souhaitez afficher les données de la mémoire disponible, tapez :

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Les caractères génériques fonctionnant avec les noms de propriété dans **Format-Table**, l’élément final du pipeline peut être réduit à `Format-Table -Property Total,Free`

Les données de la mémoire peuvent être plus lisibles si vous les affichez sous forme de liste en tapant ce qui suit :

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
