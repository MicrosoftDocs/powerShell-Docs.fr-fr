---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Utilisation des installations de logiciels
ms.openlocfilehash: f3023d8819d6cdcc9f55befcfedb21e6ff9d282c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "76996120"
---
# <a name="working-with-software-installations"></a>Utilisation des installations de logiciels

Les applications conçues pour utiliser Windows Installer sont accessibles via la classe WMI **Win32_Product**. Toutefois, certaines applications ne font pas appel à Windows Installer.
En général, les applications qui utilisent d'autres routines d'installation ne sont pas gérées par Windows Installer.
Les techniques spécifiques à employer avec ces applications dépendent du programme d'installation et des décisions prises par le développeur de l'application. Par exemple, les applications installées par copie des fichiers dans un dossier sur l'ordinateur ne peuvent généralement pas être gérées au moyen des techniques présentées ici. Vous pouvez gérer ces applications en tant que fichiers et dossiers en utilisant les techniques présentées dans la section [Utilisation des fichiers et dossiers](Working-with-Files-and-Folders.md).

> [!CAUTION]
> La classe **Win32_Product** n’est pas optimisée pour les requêtes. Les requêtes basées sur des filtres génériques forcent WMI à utiliser le fournisseur MSI pour énumérer tous les produits installés avant d’analyser de façon séquentielle la liste complète pour gérer le filtre. Ce processus lance également une vérification de cohérence des packages installés, en vérifiant et en réparant l’installation. La validation est un processus assez lent qui peut entraîner des erreurs dans les journaux des événements. Pour plus d’informations, consultez l’[article 974524 de la Base de connaissances](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>Affichage de la liste des applications Windows Installer

Pour répertorier les applications installées avec Windows Installer sur un système local ou distant, utilisez la requête WMI simple suivante :

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

Pour afficher toutes les propriétés de l’objet **Win32_Product**, utilisez le paramètre **Property** des applets de commande de mise en forme, telle l’applet de commande `Format-List`, avec la valeur `*` (all).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Vous pouvez également utiliser le paramètre `Get-CimInstance` **Filtre** pour sélectionner uniquement le Runtime Microsoft .NET 2.0. La valeur du paramètre **Filter** utilise la syntaxe du langage de requêtes WMI (WQL), et non la syntaxe Windows PowerShell. Par exemple :

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

Pour répertorier uniquement les propriétés qui vous intéressent, utilisez le paramètre **Property** des applets de commande de mise en forme pour répertorier les propriétés désirées.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Affichage de la liste de toutes les applications non installables

Étant donné que la plupart des applications standard inscrivent un programme de désinstallation auprès de Windows, nous pouvons les rechercher dans le Registre Windows pour les utiliser localement. Aucune méthode ne garantit l'identification de toutes les applications présentes sur un système. Il est toutefois possible de rechercher tous les programmes avec des listes affichées dans **Ajouter ou supprimer des programmes** dans la clé de registre suivante :

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

Nous pouvons examiner cette clé pour trouver des applications. Pour faciliter l'affichage de la clé Uninstall, nous pouvons mapper un lecteur PowerShell à cet emplacement de Registre :

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

Nous disposons désormais d'un lecteur nommé « Uninstall » qui peut servir à rechercher rapidement et facilement des installations d'applications. Nous pouvons trouver le nombre d’applications installées en comptant le nombre de clés de Registre dans le lecteur PowerShell Uninstall :

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

Nous pouvons affiner cette liste d’applications à l’aide de diverses techniques, la première d’entre elles étant `Get-ChildItem`. Pour obtenir la liste des applications et les enregistrer dans la variable `$UninstallableApplications`, utilisez la commande suivante :

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Pour afficher les valeurs des entrées de Registre dans les clés de Registre sous Uninstall, utilisez la méthode GetValue des clés de Registre. La valeur de la méthode est le nom de l'entrée de Registre.

Par exemple, pour rechercher les noms d'affichage des applications dans la clé Uninstall, utilisez la commande suivante :

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Rien ne garantit que ces valeurs sont uniques. Dans l'exemple suivant, deux éléments installés apparaissent sous le nom « Windows Media Encoder 9 Series » :

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : https://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a>Installation d'applications

Vous pouvez utiliser la classe **Win32_Product** pour installer, localement ou à distance, des packages Windows Installer.

> [!NOTE]
> Pour installer une application, vous devez démarrer PowerShell avec l'option « Exécuter en tant qu'administrateur ».

Pour effectuer une installation à distance, utilisez un chemin d'accès réseau UNC (Universal Naming Convention) pour spécifier le chemin d'accès au package .msi, car le sous-système WMI ne prend pas en charge les chemins d'accès PowerShell. Par exemple, pour installer le package NewPackage.msi situé dans le partage réseau `\\AppServ\dsp` sur l’ordinateur distant PC01, tapez la commande suivante à l’invite PowerShell :

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Les applications qui n'utilisent pas la technologie Windows Installer peuvent faire appel à leurs propres méthodes de déploiement automatisé. Examinez la documentation de l'application ou consultez le système d'aide du fournisseur de l'application.

## <a name="removing-applications"></a>Suppression d'applications

La procédure de suppression d'un package Installer à l'aide de Windows PowerShell est semblable à la procédure d'installation. Voici un exemple qui sélectionne le package à désinstaller d’après son nom. Dans certains cas, il peut être plus facile d’utiliser un filtre avec **IdentifyingNumber** :

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

La suppression d'autres applications n'est pas aussi simple, même si vous travaillez localement. Pour obtenir les chaînes de désinstallation pour ces applications à partir de la ligne de commande, extrayez la propriété **UninstallString**.
Cette méthode fonctionne pour les applications Windows Installer et les programmes plus anciens qui apparaissent sous la clé de Uninstall :

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Si vous le souhaitez, vous pouvez filtrer la sortie en fonction du nom d'affichage :

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Toutefois, pour exploiter ces chaînes provenant directement de l'invite PowerShell, vous devrez peut-être les modifier.

## <a name="upgrading-windows-installer-applications"></a>Mise à niveau d'applications Windows Installer

Pour mettre à niveau une application, vous devez connaître son nom et le chemin d'accès au package de mise à niveau de l'application. Muni de ces informations, vous pouvez mettre à niveau une application avec une seule commande PowerShell :

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
