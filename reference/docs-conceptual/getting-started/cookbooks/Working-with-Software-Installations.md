---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation des installations de logiciels
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952815"
---
# <a name="working-with-software-installations"></a>Utilisation des installations de logiciels

Les applications conçues pour utiliser Windows Installer sont accessibles via la classe WMI **Win32_Product**. Toutefois, certaines applications ne font pas appel à Windows Installer. Étant donné que Windows Installer offre la plus vaste palette de techniques standard associées aux applications installables, nous allons examiner principalement ces applications. En général, les applications qui utilisent d'autres routines d'installation ne sont pas gérées par Windows Installer. Les techniques spécifiques à employer avec ces applications dépendent du programme d'installation et des décisions prises par le développeur de l'application.

> [!NOTE]
> Dans la plupart des cas, les applications installées par copie des fichiers de l'application sur l'ordinateur ne peuvent pas être gérées au moyen des techniques présentées ici. Vous pouvez gérer ces applications en tant que fichiers et dossiers en utilisant les techniques présentées dans la section « Utilisation des fichiers et dossiers ».

### <a name="listing-windows-installer-applications"></a>Affichage de la liste des applications Windows Installer

Pour répertorier les applications installées avec Windows Installer sur un système local ou distant, utilisez la requête WMI simple suivante :

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Pour afficher toutes les propriétés de l’objet Win32_Product, utilisez le paramètre Property des applets de commande de mise en forme, telle l’applet de commande Format-List, avec la valeur \* (all).

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

Vous pouvez également utiliser le paramètre **Get-WmiObject Filter** pour sélectionner uniquement Microsoft .NET Framework 2.0. Le filtre utilisé dans cette commande étant un filtre WMI, il utilise la syntaxe du langage de requêtes WMI (WQL), et non la syntaxe Windows PowerShell. À la place :

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Notez que les requêtes WQL utilisent fréquemment des caractères, tels que des espaces ou des signes d'égalité, qui ont une signification spéciale dans Windows PowerShell. Pour cette raison, il est préférable de toujours mettre la valeur du paramètre Filter entre guillemets. Vous pouvez également utiliser le caractère d’échappement de Windows PowerShell, à savoir l’accent grave (\`), bien que cela n’améliore pas nécessairement la lisibilité. La commande suivante est équivalente à la précédente et retourne les mêmes résultats. Toutefois, des accents graves sont utilisés pour échapper les caractères spéciaux, ce qui évite de mettre la chaîne de filtre entre guillemets.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Pour répertorier uniquement les propriétés qui vous intéressent, utilisez le paramètre Property des applets de commande de mise en forme pour répertorier les propriétés désirées.

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

Enfin, pour obtenir uniquement les noms des applications installées, une instruction **Format-Wide** simplifie la sortie :

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Si nous disposons de plusieurs méthodes pour examiner les applications faisant appel à Windows Installer pour l'installation, notre analyse ne tient pas compte des autres applications pour le moment. Étant donné que la plupart des applications standard inscrivent leur programme de désinstallation auprès de Windows, nous pouvons les rechercher dans le Registre Windows pour les utiliser localement.

### <a name="listing-all-uninstallable-applications"></a>Affichage de la liste de toutes les applications non installables

Bien qu'aucune méthode ne garantisse l'identification de toutes les applications présentes sur un système, il est possible de trouver tous les programmes répertoriés dans la boîte de dialogue Ajout/Suppression de programmes. Cette dernière recherche les applications dans la clé de Registre suivante :

**HKEY_LOCAL_MACHINE\\Logiciel\\Microsoft\\Windows\\CurrentVersion\\Désinstaller**.

Nous pouvons également examiner cette clé pour trouver des applications. Pour faciliter l'affichage de la clé Uninstall, nous pouvons mapper un lecteur Windows PowerShell à cet emplacement de Registre :

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> Le lecteur **HKLM:** étant mappé à la racine de **HKEY_LOCAL_MACHINE**, nous utilisons ce lecteur dans le chemin d’accès à la clé Uninstall. Au lieu d’utiliser **HKLM:**, nous pourrions recourir à **HKLM** ou à  **HKEY_LOCAL_MACHINE** pour spécifier le chemin d’accès au Registre. L'avantage d'utiliser un lecteur de Registre existant, c'est que nous pouvons utiliser la saisie semi-automatique par tabulation pour remplir les noms des clés, ce qui nous évite de les taper.

Nous disposons désormais d'un lecteur nommé « Uninstall » qui peut servir à rechercher rapidement et facilement des installations d'applications. Nous pouvons trouver le nombre d’applications installées en comptant le nombre de clés de Registre dans le lecteur Windows PowerShell Uninstall :

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Nous pouvons affiner cette liste d’applications à l’aide de diverses techniques, la première d’entre elles étant **Get-ChildItem**. Pour obtenir la liste des applications et les enregistrer dans la variable **$UninstallableApplications**, utilisez la commande suivante :

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Nous utilisons ici un nom de variable long par souci de clarté. Dans la réalité, il est inutile d'utiliser des noms longs. Bien que vous puissiez utiliser la saisie semi-automatique via la touche Tab pour les noms de variable, vous pouvez également utiliser des noms contenant 1 ou 2 caractères pour aller plus vite. Des noms descriptifs plus longs sont particulièrement utiles quand vous développez du code destiné à être réutilisé.

Pour afficher les valeurs des entrées de Registre dans les clés de Registre sous Uninstall, utilisez la méthode GetValue des clés de Registre. La valeur de la méthode est le nom de l'entrée de Registre.

Par exemple, pour rechercher les noms d'affichage des applications dans la clé Uninstall, utilisez la commande suivante :

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Rien ne garantit que ces valeurs sont uniques. Dans l'exemple suivant, deux éléments installés apparaissent sous le nom « Windows Media Encoder 9 Series » :

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a>Installation d'applications

Vous pouvez utiliser la classe **Win32_Product** pour installer, localement ou à distance, des packages Windows Installer.

> [!NOTE]
> Dans Windows Vista, Windows Server 2008 et versions ultérieures de Windows, vous devez démarrer Windows PowerShell avec l'option « Exécuter en tant qu'administrateur » pour installer une application.

Pour effectuer une installation à distance, utilisez un chemin d'accès réseau UNC (Universal Naming Convention) pour spécifier le chemin d'accès au package .msi, car le sous-système WMI ne prend pas en charge les chemins d'accès Windows PowerShell. Par exemple, pour installer le package NewPackage.msi situé dans le partage réseau \\\\AppServ\\dsp sur l’ordinateur distant PC01, tapez la commande suivante à l’invite Windows PowerShell :

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Les applications qui n'utilisent pas la technologie Windows Installer peuvent faire appel à leurs propres méthodes de déploiement automatisé. Pour déterminer s'il existe ou non une méthode d'automatisation du déploiement, examinez la documentation de l'application ou consultez le système d'aide du fournisseur de l'application. Dans certains cas, même si le fournisseur d'une application n'a pas spécifiquement prévu d'automatiser l'installation, le fabricant du logiciel d'installation peut proposer certaines techniques d'automatisation.

### <a name="removing-applications"></a>Suppression d'applications

La procédure de suppression d'un package Windows Installer à l'aide de Windows PowerShell est semblable à la procédure d'installation. Voici un exemple qui sélectionne le package à désinstaller d’après son nom. Dans certains cas, il peut être plus facile d’utiliser un filtre avec **IdentifyingNumber** :

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

La suppression d'autres applications n'est pas aussi simple, même si vous travaillez localement. Pour obtenir les chaînes de désinstallation pour ces applications à partir de la ligne de commande, extrayez la propriété **UninstallString**. Cette méthode fonctionne pour les applications Windows Installer et les programmes plus anciens qui apparaissent sous la clé de Uninstall :

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Si vous le souhaitez, vous pouvez filtrer la sortie en fonction du nom d'affichage :

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Toutefois, pour exploiter ces chaînes provenant directement de l'invite Windows PowerShell, vous devrez peut-être les modifier.

### <a name="upgrading-windows-installer-applications"></a>Mise à niveau d'applications Windows Installer

Pour mettre à niveau une application, vous devez connaître son nom et le chemin d'accès au package de mise à niveau de l'application. Muni de ces informations, vous pouvez mettre à niveau une application avec une seule commande Windows PowerShell :

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```