---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Collecte d’informations sur les ordinateurs
ms.openlocfilehash: 5dc8fcc5f12fdf9e3fc8151d3e50b8b660262c62
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030837"
---
# <a name="collecting-information-about-computers"></a>Collecte d’informations sur les ordinateurs

Les applets de commande du module **CimCmdlets** sont les applets de commande les plus importants pour les tâches générales de gestion du système.
Tous les paramètres critiques du sous-système sont exposés via WMI.
En outre, WMI traite les données en tant qu’objets figurant dans des collections d’un ou plusieurs éléments.
Étant donné que Windows PowerShell fonctionne également avec des objets et dispose d’un pipeline permettant de traiter un ou plusieurs objets de la même façon, l’accès générique à WMI permet d’effectuer des tâches avancées sans grand effort.

Les exemples suivants montrent comment collecter des informations spécifiques en appliquant l’applet de commande `Get-CimInstance` à un ordinateur arbitraire.
Nous spécifions le paramètre **ComputerName** avec la valeur de point ( **.** ) qui représente l’ordinateur local.
Vous pouvez spécifier un nom ou une adresse IP associés à tout ordinateur accessible via WMI.
Pour récupérer des informations sur l’ordinateur local, vous pouvez omettre le paramètre **ComputerName**.

## <a name="listing-desktop-settings"></a>Affichage de la liste des paramètres de bureau

Nous allons commencer par une commande qui collecte des informations concernant les postes de travail sur l’ordinateur local.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Cette commande retourne des informations sur tous les postes de travail, qu’ils soient en cours d’utilisation ou non.

> [!NOTE]
> Les informations retournées par certaines classes WMI peuvent être très détaillées, et incluent souvent des métadonnées sur la classe WMI.
Étant donné que la plupart de ces propriétés de métadonnées portent des noms commençant par **Cim**, vous pouvez filtrer les propriétés à l’aide de `Select-Object`.
Spécifiez le paramètre **-ExcludeProperty** avec "Cim*" comme valeur.
Par exemple :

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Pour exclure les métadonnées, utilisez un opérateur de pipeline (|) pour envoyer les résultats de la commande `Get-CimInstance` à `Select-Object -ExcludeProperty "CIM*"`.

## <a name="listing-bios-information"></a>Affichage d’informations sur le BIOS

La classe WMI **Win32_BIOS** retourne des informations relativement compactes et complètes sur le BIOS de l’ordinateur local :

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a>Affichage d’informations sur le processeur

Vous pouvez récupérer des informations générales sur le processeur à l’aide de la classe **Win32_Processor** de WMI, même si vous pouvez filtrer les informations :

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Pour une chaîne de description générique de la famille de processeurs, vous pouvez simplement retourner la propriété **SystemType** :

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>Affichage du modèle et du fabricant de l’ordinateur

Des informations sur le modèle d’ordinateur sont également accessibles par le biais de l’applet de commande **Win32_ComputerSystem**.
La sortie standard affichée ne nécessite pas de filtrage pour fournir des données OEM :

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

La qualité de la sortie de telles commandes, qui retournent des informations directement à partir de certains composants matériels, dépend des données dont vous disposez.
Il se peut que des informations mal configurées par certains fabricants de matériel ne soient pas être disponibles.

## <a name="listing-installed-hotfixes"></a>Affichage de la liste des correctifs installés

Vous pouvez afficher la liste de tous les correctifs à l’aide de la classe **Win32_QuickFixEngineering** :

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Cette classe retourne une liste des correctifs ressemblant à ceci :

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Pour une sortie plus concise, vous pouvez exclure certaines propriétés.
Vous pouvez utiliser le paramètre **Property** de `Get-CimInstance` pour choisir uniquement le **HotFixID**. Cela permet d’obtenir plus d’informations, car toutes les métadonnées sont affichées par défaut :

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Les données supplémentaires sont retournées, car le paramètre Property dans l’applet de commande `Get-CimInstance` restreint les propriétés retournées par les instances de classe WMI, pas l’objet retourné à Windows PowerShell.
Pour réduire la sortie, utilisez `Select-Object` :

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>Affichage d’informations sur la version du système d’exploitation

Les propriétés de la classe **Win32_OperatingSystem** incluent des informations sur la version et le Service Pack.
Vous ne pouvez sélectionner explicitement que ces propriétés pour obtenir un résumé d’informations sur la version à partir de la classe **Win32_OperatingSystem** :

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Vous pouvez également utiliser des caractères génériques avec le paramètre **Property** de `Select-Object`.
Étant donné que l’utilisation de toutes les propriétés commençant par **Build** ou **ServicePack** est importante ici, nous pouvons raccourcir cela en utilisant la forme suivante :

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a>Affichage des utilisateurs locaux et du propriétaire

Vous pouvez trouver des informations générales sur l’utilisateur local (nombre d’utilisateurs sous licence, nombre actuel d’utilisateurs et nom du propriétaire) avec une sélection de propriétés de la classe **Win32_OperatingSystem**.
Vous pouvez sélectionner explicitement les propriétés à afficher comme suit :

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Une version plus concise utilisant des caractères génériques est la suivante :

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Obtention de l’espace disque disponible

Pour afficher l’espace disque et l’espace libre sur les lecteurs locaux, vous pouvez utiliser la classe WMI Win32_LogicalDisk.
Vous ne devez voir que les instances dont DriveType a la valeur 3 (valeur que WMI utilise pour les disques durs fixes).

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a>Obtention d’informations sur l’ouverture de session

Vous pouvez obtenir des informations générales sur les ouvertures de session associées aux utilisateurs par le biais de la classe WMI **Win32_LogonSession** :

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>Obtention de l’utilisateur connecté à un ordinateur

Vous pouvez afficher l’utilisateur connecté à un système informatique particulier à l’aide de la commande Win32_ComputerSystem.
Cette commande retourne uniquement l’utilisateur connecté au bureau du système :

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a>Obtention de l’heure locale d’un ordinateur

Vous pouvez récupérer l’heure locale actuelle sur un ordinateur spécifique à l’aide de la classe WMI **Win32_LocalTime**.

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

## <a name="displaying-service-status"></a>Affichage de l’état du service

Pour afficher l’état de tous les services sur un ordinateur spécifique, vous pouvez utiliser localement l’applet de commande `Get-Service`.
Pour des systèmes distants, vous pouvez utiliser la classe WMI **Win32_Service**.
Si vous utilisez également `Select-Object` pour filtrer les résultats pour **Status**, **Name** et **DisplayName**, le format de sortie est quasiment identique à celui de `Get-Service` :

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Pour permettre l’affichage complet des noms des services occasionnels portant des noms très longs, vous pouvez utiliser l’applet de commande `Format-Table` avec les paramètres **AutoSize** et **Wrap**, pour optimiser la largeur des colonnes et permettre le retour à la ligne plutôt que la troncation des noms longs :

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
