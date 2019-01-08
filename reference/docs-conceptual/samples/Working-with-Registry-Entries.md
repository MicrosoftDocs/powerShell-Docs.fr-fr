---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation des entrées de Registre
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401852"
---
# <a name="working-with-registry-entries"></a>Utilisation des entrées de Registre

Les entrées de Registre étant des propriétés de clés, il est impossible de les parcourir directement. Il est donc nécessaire d'adopter une approche légèrement différente pour pouvoir les utiliser.

### <a name="listing-registry-entries"></a>Affichage de la liste des entrées de Registre

Vous pouvez examiner les entrées de Registre de plusieurs manières. La façon la plus simple consiste à obtenir les noms des propriétés associées à une clé. Par exemple, pour afficher les noms des entrées dans la clé de Registre **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, utilisez **Get-Item**. Les clés de Registre possèdent une propriété avec le nom générique « Property » qui contient la liste des entrées de Registre dans la clé. La commande suivante sélectionne la propriété Property et développe les éléments pour les afficher dans une liste :

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Pour afficher les entrées de Registre dans un format plus lisible, utilisez l’applet de commande **Get-ItemProperty** :

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

Les propriétés liées à Windows PowerShell pour la clé possèdent toutes le préfixe « PS », comme **PSPath**, **PSParentPath**, **PSChildName** et **PSProvider**.

Pour faire référence à l’emplacement actuel, vous pouvez utiliser la notation «  **.**  ». Pour passer d’abord au conteneur de Registre **CurrentVersion**, vous pouvez utiliser l’applet de commande **Set-Location** :

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Vous pouvez également utiliser le PSDrive HKLM intégré avec l’applet de commande **Set-Location** :

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Vous pouvez ensuite utiliser la notation «  **.**  » pour l’emplacement actuel pour répertorier les propriétés sans spécifier de chemin d’accès complet :

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

L’expansion de chemin fonctionne de la même façon que dans le système de fichiers. Ainsi, à partir de cet emplacement, vous pouvez obtenir la liste **ItemProperty** pour **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** en utilisant l’applet de commande **Get-ItemProperty -Path ..\\Help**.

### <a name="getting-a-single-registry-entry"></a>Obtention d'une entrée de Registre unique

Si vous souhaitez récupérer une entrée spécifique d'une clé de Registre, plusieurs options s'offrent à vous. Cet exemple recherche la valeur de **DevicePath** dans **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.

Utilisez l’applet de commande **Get-ItemProperty** avec le paramètre **Path** pour spécifier le nom de la clé, et avec le paramètre **Name** pour spécifier le nom de l’entrée **DevicePath**.

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

Cette commande retourne les propriétés Windows PowerShell standard, ainsi que la propriété **DevicePath**.

> [!NOTE]
> Bien que l’applet de commande **Get-ItemProperty** dispose des paramètres **Filter**, **Include** et **Exclude**, vous ne pouvez pas les utiliser pour filtrer sur le nom de propriété. Ces paramètres font référence aux clés de Registre (qui sont des chemins d'accès à des éléments) et non à des entrées de Registre (qui sont des propriétés d'éléments).

Une autre option consiste à utiliser l'outil en ligne de commande Reg.exe. Pour obtenir de l’aide sur reg.exe, tapez **reg.exe /?** à une invite de commandes. Pour rechercher l'entrée DevicePath, utilisez reg.exe comme indiqué dans la commande suivante :

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Vous pouvez aussi utiliser l’objet **COM WshShell** pour rechercher des entrées de Registre. Toutefois, cette méthode ne fonctionne ni avec des données binaires volumineuses, ni avec des noms d’entrées de Registre contenant des caractères tels que « \\ ». Ajoutez le nom de la propriété au chemin de l’élément avec un séparateur \\ :

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Création d'entrées de Registre

Pour ajouter une nouvelle entrée nommée « PowerShellPath » à la clé **CurrentVersion**, utilisez l’applet de commande **New-ItemProperty** avec le chemin d’accès à la clé, le nom de l’entrée et la valeur de l’entrée. Pour cet exemple, nous allons prendre la valeur de la variable Windows PowerShell **$PSHome**, qui stocke le chemin d’accès au répertoire d’installation de Windows PowerShell.

Vous pouvez ajouter la nouvelle entrée à la clé à l'aide de la commande suivante. La commande retourne également des informations sur la nouvelle entrée :

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

**PropertyType** doit être le nom d’un membre d’énumération **Microsoft.Win32.RegistryValueKind** figurant dans le tableau suivant :

|Valeur PropertyType|Signification|
|----------------------|-----------|
|Binary|Données binaires|
|DWord|Nombre UInt32 valide|
|ExpandString|Chaîne pouvant contenir des variables d'environnement qui sont développées de manière dynamique|
|MultiString|Chaîne multiligne|
|String|Valeur de chaîne quelconque|
|QWord|8 octets de données binaires|

> [!NOTE]
> Vous pouvez ajouter une entrée de Registre à plusieurs emplacements en spécifiant un tableau de valeurs pour le paramètre **Path** :

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Vous pouvez aussi remplacer une valeur d’entrée de Registre préexistante en ajoutant le paramètre **Force** à toute commande **New-ItemProperty**.

### <a name="renaming-registry-entries"></a>Affectation d'un nouveau nom à des entrées de Registre

Pour affecter à l’entrée **PowerShellPath** le nom « PSHome », utilisez **Rename-ItemProperty** :

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Pour afficher la valeur renommée, ajoutez le paramètre **PassThru** à la commande.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Suppression d'entrées de Registre

Pour supprimer les entrées de Registre PSHome et PowerShellPath, utilisez l’applet de commande **Remove-ItemProperty** :

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```