---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Obtention d’objets WMI - Get-CimInstance
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "77002649"
---
# <a name="getting-wmi-objects-get-ciminstance"></a>Obtention d’objets WMI (Get-CimInstance)

## <a name="getting-wmi-objects-get-ciminstance"></a>Obtention d’objets WMI (Get-CimInstance)

WMI (Windows Management Instrumentation) est une technologie majeure pour l’administration du système Windows, car elle expose un vaste éventail d’informations de manière uniforme. Compte tenu de tout ce que WMI permet de réaliser, la cmdlet Windows PowerShell pour l’accès aux objets WMI, `Get-CimInstance`, est l’une des plus utiles pour travailler réellement. Nous allons aborder l’utilisation des CimCmdlets pour accéder aux objets WMI, puis expliquer comment utiliser des objets WMI pour réaliser des opérations spécifiques.

### <a name="listing-wmi-classes"></a>Affichage de la liste des classes WMI

Le premier problème que rencontrent la plupart des utilisateurs de WMI est de comprendre ce que WMI permet de faire. Les classes WMI décrivent les ressources qui peuvent être gérées. Il existe des centaines de classes WMI, dont certaines contiennent des dizaines de propriétés.

`Get-CimClass` résout ce problème en rendant WMI détectable. Vous pouvez obtenir la liste des classes WMI disponibles sur l’ordinateur local en tapant ce qui suit :

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

Vous pouvez récupérer les mêmes informations à partir d’un ordinateur distant à l’aide du paramètre **ComputerName**, en spécifiant une adresse IP ou un nom d’ordinateur :

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

La liste de classes retournée par des ordinateurs distants peut varier selon le système d’exploitation que l’ordinateur exécute et les extensions WMI ajoutées par les applications installées.

> [!NOTE]
> Lorsque vous utilisez des cmdlets CIM pour vous connecter à un ordinateur distant, celui-ci doit exécuter WMI et le compte que vous utilisez doit figurer dans le groupe Administrateurs local sur l’ordinateur distant.
> PowerShell ne doit pas nécessairement être installé sur le système distant. Cela permet d’administrer des systèmes d’exploitation qui n’exécutent pas PowerShell, mais disposent de WMI.

### <a name="displaying-wmi-class-details"></a>Affichage des détails de classe WMI

Si vous connaissez déjà le nom d’une classe WMI, vous pouvez l’utiliser pour obtenir des informations immédiatement. Par exemple, une des classes WMI couramment utilisées pour récupérer des informations sur un ordinateur est **Win32_OperatingSystem**.

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

Bien que nous montrions tous les paramètres, la commande peut être exprimée de façon plus concise.
Le paramètre **ComputerName** n’est pas nécessaire lors de la connexion au système local. Nous le montrons pour illustrer le cas le plus général, et vous rappeler la disponibilité de ce paramètre. Par défaut, l’**espace de noms** passe à `root/CIMV2`. Vous pouvez également l’omettre. Enfin, la plupart des applets de commande permettent l’omission du nom de paramètres communs. Avec `Get-CimInstance`, si aucun nom n’est spécifié pour le premier paramètre, PowerShell traite celui-ci en tant que paramètre **Classe**. Cela signifie que la dernière commande pourrait avoir été émise en tapant ce qui suit :

```powershell
Get-CimInstance Win32_OperatingSystem
```

La classe **Win32_OperatingSystem** a beaucoup plus de propriétés que celles affichées ici. Vous pouvez utiliser l’applet de commande Get-Member pour voir toutes les propriétés. Les propriétés d’une classe WMI sont automatiquement disponibles, comme d’autres propriétés de l’objet :

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Affichage de propriétés autres que par défaut avec les applets de commande Format

Si vous souhaitez des informations contenues dans la classe **Win32_OperatingSystem** qui ne sont pas affichées par défaut, vous pouvez les afficher à l’aide des applets de commande **Format**. Par exemple, si vous souhaitez afficher les données de la mémoire disponible, tapez :

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> Les caractères génériques fonctionnant avec les noms de propriété dans `Format-Table`, l’élément final du pipeline peut être réduit à `Format-Table -Property Total*Memory*, Free*`

Les données de la mémoire peuvent être plus lisibles si vous les affichez sous forme de liste en tapant ce qui suit :

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
