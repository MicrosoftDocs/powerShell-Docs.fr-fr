---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: d404f0fdc82e3730f1f6a04d7f39d5988a3de7d6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201385"
---
# Get-PSDrive

## SYNOPSIS
Obtient les lecteurs dans la session active.

## SYNTAX

### Nom (par défaut)

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

### LiteralName

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

## Description

L' `Get-PSDrive` applet de commande obtient les lecteurs dans la session active. Vous pouvez obtenir un lecteur particulier ou tous les lecteurs présents dans la session.

Cette applet de commande obtient les types de lecteurs suivants :

- Lecteurs logiques Windows sur l’ordinateur, y compris les lecteurs mappés à des partages réseau.
- Lecteurs exposés par les fournisseurs PowerShell (tels que le certificat :, Function : et alias : Drives) et les lecteurs HKLM : et HKCU : qui sont exposés par le fournisseur de Registre Windows PowerShell.
- Lecteurs temporaires spécifiés par session et lecteurs réseau mappés persistants que vous créez à l’aide de l’applet de commande New-PSDrive.

À compter de Windows PowerShell 3,0, le paramètre **Persist** de l’applet de commande `New-PSDrive` peut créer des lecteurs réseau mappés qui sont enregistrés sur l’ordinateur local et qui sont disponibles dans d’autres sessions. Pour plus d’informations, consultez New-PSDrive.

De plus, depuis Windows PowerShell 3.0, lorsqu’un lecteur externe est connecté à l’ordinateur, Windows PowerShell ajoute automatiquement un lecteur PSDrive au système de fichiers qui représente le nouveau lecteur.
Il n'est pas nécessaire de redémarrer Windows PowerShell. De même, lorsqu'un lecteur externe est déconnecté de l'ordinateur, Windows PowerShell supprime automatiquement le PSDrive qui représente le lecteur supprimé.

## EXEMPLES

### Exemple 1 : récupérer des lecteurs dans la session active

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

Cette commande obtient les lecteurs dans la session active.

La sortie indique le disque dur (C :), le lecteur de CD-ROM (D :) et les lecteurs exposés par les fournisseurs Windows PowerShell (alias :, CERT :, env :, Function :, HKCU :, HKLM : et variable :).

### Exemple 2 : obtenir un lecteur sur l’ordinateur

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

Cette commande obtient le lecteur D: sur l’ordinateur. Notez que la lettre de lecteur dans la commande n’est pas suivie d’un signe deux-points.

### Exemple 3 : récupération de tous les lecteurs pris en charge par le fournisseur de système de fichiers Windows PowerShell

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

Cette commande obtient tous les lecteurs qui sont pris en charge par le fournisseur de système de fichiers de Windows PowerShell. Cela comprend les lecteurs fixes, les partitions logiques, les lecteurs réseau mappés et les lecteurs temporaires que vous créez à l’aide de l’applet de commande New-PSDrive.

### Exemple 4 : vérifier si un lecteur est en cours d’utilisation en tant que nom de lecteur Windows PowerShell

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

Cette commande vérifie si le lecteur X est déjà utilisé en tant que nom de lecteur Windows PowerShell.
Si ce n’est pas le cas, la commande utilise l' `New-PSDrive` applet de commande pour créer un lecteur temporaire mappé à la clé de Registre HKLM : \ Software.

### Exemple 5 : comparer les types de lecteurs système de fichiers

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

Cet exemple compare les types de lecteurs de système de fichiers affichés par `Get-PSDrive` à ceux affichés à l’aide d’autres méthodes. Cet exemple illustre différentes façons d’afficher des lecteurs dans Windows PowerShell et il montre que les lecteurs spécifiques à la session créés à l’aide de l’applet de commande New-PSDrive sont accessibles uniquement dans Windows PowerShell.

La première commande utilise `Get-PSDrive` pour récupérer tous les lecteurs du système de fichiers dans la session. Cela comprend les lecteurs fixes (C : et D :), un lecteur réseau mappé (G :) qui a été créé à l’aide du paramètre **Persist** de `New-PSDrive` et d’un lecteur PowerShell (T :) qui a été créé à l’aide de `New-PSDrive` sans le paramètre **Persist** .

La commande **net use** affiche les lecteurs réseau mappés Windows. dans ce cas, elle affiche uniquement le lecteur G. Elle n’affiche pas le lecteur X : qui a été créé par `New-PSDrive` . Elle indique que le lecteur G : est également mappé à \\ \\ Music \\ GratefulDead.

La troisième commande utilise la méthode **GetDrives** de la classe Microsoft .NET Framework **System.IO.DriveInfo** . Cette commande obtient les lecteurs du système de fichiers Windows, y compris le lecteur G :, mais il n’obtient pas les lecteurs créés par `New-PSDrive` .

La quatrième commande utilise l’applet de commande `Get-CimInstance` pour obtenir les instances de la classe **Win32_LogicalDisk** . Elle retourne les lecteurs A :, C :, D :, E : et G :, mais pas les lecteurs créés par `New-PSDrive` .

La dernière commande utilise l’applet de commande `Get-CimInstance` pour afficher les instances de la classe **Win32_NetworkConnection** . Tout comme **net use** , elle retourne uniquement le lecteur G : persistant créé par `New-PSDrive` .

## PARAMETERS

### -LiteralName

Spécifie le nom du lecteur.

La valeur de **LiteralName**  est utilisée exactement telle que vous la tapez. Aucun caractère n’est interprété en tant que caractère générique. Si le nom inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie, sous forme de tableau de chaînes, le nom ou le nom des lecteurs que cette applet de commande obtient dans l’opération.
Tapez la lettre ou le nom du lecteur sans le signe deux-points (:).

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Spécifie, sous la forme d’un tableau de chaînes, le fournisseur Windows PowerShell. Cette applet de commande obtient uniquement les lecteurs pris en charge par ce fournisseur. Tapez le nom d’un fournisseur (FileSystem, Registry ou Certificate, par exemple).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Étendue

Spécifie l’étendue dans laquelle cette applet de commande obtient les lecteurs.

Les valeurs valides pour ce paramètre sont :

- Global
- Local
- Script
- nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent). « Local » est la valeur par défaut.

Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### System.Management.Automation.PSDriveInfo

Cette applet de commande retourne des objets qui représentent les lecteurs dans la session.

## REMARQUES

* Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, utilisez l'applet de commande `Get-PSProvider`. Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).
* Les lecteurs réseau mappés qui sont créés à l’aide du paramètre **Persist** de l’applet de commande New-PSDrive sont spécifiques à un compte d’utilisateur. Les lecteurs réseau mappés que vous créez dans les sessions démarrées avec l’option Exécuter en tant qu’administrateur ou avec les informations d’identification d’un autre utilisateur ne sont pas visibles dans les sessions démarrées sans informations d’identification explicites ou avec les informations d’identification de l’utilisateur actuel.

## LIENS CONNEXES

[New-PSDrive](New-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)

[Get-PSProvider](Get-PSProvider.md)
