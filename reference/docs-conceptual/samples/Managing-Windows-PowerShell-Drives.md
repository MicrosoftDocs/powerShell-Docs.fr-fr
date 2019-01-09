---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Gestion des lecteurs Windows PowerShell
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: cfc5418e9d2efb1a786817e1b941d75e22291742
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401917"
---
# <a name="managing-windows-powershell-drives"></a>Gestion des lecteurs Windows PowerShell

Un *lecteur Windows PowerShell* est un emplacement de magasin de données auquel vous pouvez accéder, au même titre qu’un lecteur du système de fichiers dans Windows PowerShell. Les fournisseurs Windows PowerShell créent pour vous certains lecteurs, comme les lecteurs du système de fichiers (y compris C: et D:), les lecteurs de Registre (HKCU: et HKLM:) et le lecteur de certificat (Cert:). Vous pouvez également créer vos propres lecteurs Windows PowerShell. Ces lecteurs sont très utiles, mais ils ne sont disponibles que dans Windows PowerShell. Vous ne pouvez pas y accéder à l'aide d'autres outils Windows, tels que l'Explorateur de fichiers ou Cmd.exe.

Les commandes associées aux lecteurs Windows PowerShell comportent le mot **PSDrive** dans leur intitulé. Pour obtenir la liste des lecteurs Windows PowerShell dans votre session Windows PowerShell, utilisez l’applet de commande **Get-PSDrive**.

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

Bien que les lecteurs répertoriés varient en fonction des lecteurs de votre système, leur liste est similaire à la sortie de la commande **Get-PSDrive** ci-dessus.

Les lecteurs du système de fichiers sont un sous-ensemble des lecteurs Windows PowerShell. Les lecteurs du système de fichiers sont identifiés par l'entrée FileSystem dans la colonne Provider. (Les lecteurs du système de fichiers dans Windows PowerShell sont pris en charge par le fournisseur FileSystem de Windows PowerShell.)

Pour afficher la syntaxe de l’applet de commande **Get-PSDrive**, tapez une commande **Get-Command** avec le paramètre **Syntax** :

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

Le paramètre **PSProvider** permet d’afficher uniquement les lecteurs Windows PowerShell pris en charge par un fournisseur particulier. Par exemple, pour afficher uniquement les lecteurs pris en charge par le fournisseur FileSystem de Windows PowerShell, tapez une commande **Get-PSDrive** avec le paramètre **PSProvider** et la valeur **FileSystem** :

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Pour afficher les lecteurs Windows PowerShell qui représentent les ruches du Registre, utilisez le paramètre **PSProvider** pour afficher uniquement les lecteurs Windows PowerShell pris en charge par le fournisseur de Registre de Windows PowerShell :

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Vous pouvez également utiliser les applets de commande Location standard avec les lecteurs Windows PowerShell :

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Ajout de nouveaux lecteurs Windows PowerShell (New-PSDrive)

Vous pouvez ajouter vos propres lecteurs Windows PowerShell à l’aide de la commande **New-PSDrive**. Pour obtenir la syntaxe de l’applet de commande **New-PSDrive**, entrez la commande **Get-Command** avec le paramètre **Syntax** :

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Pour créer un lecteur Windows PowerShell, vous devez spécifier trois paramètres :

- le nom du lecteur (vous pouvez utiliser n'importe quel nom Windows PowerShell valide) ;

- le fournisseur PSProvider (utilisez « FileSystem » pour les emplacements du système de fichiers et « Registry » pour les emplacements du Registre) ;

- la racine, c'est-à-dire le chemin d'accès à la racine du nouveau lecteur.

Par exemple, vous pouvez créer un lecteur nommé « Office » qui est mappé au dossier contenant les applications Microsoft Office sur votre ordinateur, par exemple **C:\\Program Files\\Microsoft Office\\OFFICE11**. Pour créer le lecteur, tapez la commande suivante :

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> En général, les chemins d'accès ne respectent pas la casse.

Vous pouvez référencer le nouveau lecteur Windows PowerShell comme tout autre lecteur Windows PowerShell, c’est-à-dire en tapant son nom suivi du signe deux-points (**:**).

Un lecteur Windows PowerShell peut simplifier de nombreuses tâches. Par exemple, certaines clés importantes dans le Registre Windows ont des chemins d'accès tellement longs qu'il est difficile d'y accéder et de s'en souvenir. Les informations de configuration critiques se trouvent sous **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**. Pour afficher et modifier des éléments dans la clé de Registre CurrentVersion, vous pouvez créer un lecteur Windows PowerShell ayant pour racine cette clé en tapant :

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Vous pouvez ensuite modifier l’emplacement du lecteur **cvkey:** comme vous le feriez pour tout autre lecteur :

`PS> cd cvkey:`

ou :

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

L'applet de commande New-PsDrive ajoute le nouveau lecteur uniquement à la session Windows PowerShell active. Si vous fermez la fenêtre Windows PowerShell, le nouveau lecteur est perdu. Pour enregistrer un lecteur Windows PowerShell, utilisez l’applet de commande Export-Console pour exporter la session Windows PowerShell active, puis utilisez le paramètre **PSConsoleFile** de PowerShell.exe pour l’importer. Vous pouvez aussi ajouter le nouveau lecteur à votre profil Windows PowerShell.

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Suppression de lecteurs Windows PowerShell (Remove-PSDrive)

Pour supprimer des lecteurs de Windows PowerShell, utilisez l’applet de commande **Remove-PSDrive**. L’applet de commande **Remove-PSDrive** est facile à utiliser. Pour supprimer un lecteur Windows PowerShell, vous devez simplement spécifier son nom.

Par exemple, si vous avez ajouté le lecteur Windows PowerShell **Office :** qui apparaît dans la rubrique **New-PSDrive**, vous pouvez le supprimer en saisissant :

```powershell
Remove-PSDrive -Name Office
```

Pour supprimer la **cvkey :** Windows PowerShell de lecteur, également illustré dans le **New-PSDrive** rubrique, utilisez la commande suivante :

```powershell
Remove-PSDrive -Name cvkey
```

S'il est facile de supprimer un lecteur Windows PowerShell, vous devez toutefois vous assurer de ne pas vous trouver à l'emplacement du lecteur pour que l'opération réussisse. Par exemple :

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a>Ajout et suppression de lecteurs en dehors de Windows PowerShell

Windows PowerShell détecte les lecteurs du système de fichiers qui sont ajoutés ou supprimés dans Windows, y compris les lecteurs réseau mappés, les lecteurs USB attachés, ainsi que les lecteurs supprimés à l’aide de la commande **net use** ou des méthodes **WScript.NetworkMapNetworkDrive** et **RemoveNetworkDrive** à partir d’un script WSH (Windows Script Host).