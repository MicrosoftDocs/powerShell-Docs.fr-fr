---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 54b65a636fe05ed82d4f022b5bb8cbf8acaf7bab
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597950"
---
# New-PSDrive

## SYNOPSIS
Crée des lecteurs réseau mappés temporaires et persistants.

## SYNTAXE

### Tous

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `New-PSDrive` applet de commande crée des lecteurs temporaires et persistants mappés à ou associés à un emplacement dans un magasin de données, tel qu’un lecteur réseau, un répertoire sur l’ordinateur local ou une clé de Registre, et des lecteurs réseau mappés Windows persistants associés à un emplacement de système de fichiers sur un ordinateur distant.

Les lecteurs temporaires existent uniquement dans la session PowerShell active et dans les sessions que vous créez dans la session active. Ils peuvent avoir n’importe quel nom valide dans PowerShell et peuvent être mappés à n’importe quelle ressource locale ou distante. Vous pouvez utiliser des lecteurs PowerShell temporaires pour accéder aux données dans le magasin de données associé, comme vous le feriez avec n’importe quel lecteur réseau mappé. Vous pouvez modifier les emplacements dans le lecteur, à l’aide de `Set-Location` , et accéder au contenu du lecteur à l’aide de `Get-Item` ou de `Get-ChildItem` .

Étant donné que les lecteurs temporaires sont connus uniquement de PowerShell, vous ne pouvez pas y accéder à l’aide de l’Explorateur de fichiers, Windows Management Instrumentation (WMI), COM (Component Object Model), Microsoft .NET Framework ou avec des outils tels que **net use**.

Les fonctionnalités suivantes ont été ajoutées à `New-PSDrive` dans PowerShell 3,0 :

- Lecteurs réseau mappés. Vous pouvez utiliser le paramètre **Persist** de `New-PSDrive` pour créer des lecteurs réseau mappés Windows. Contrairement aux lecteurs PowerShell temporaires, les lecteurs réseau mappés Windows ne sont pas spécifiques à la session. Ils sont enregistrés dans Windows et peuvent être gérés à l’aide d’outils Windows standard, tels que l’Explorateur de fichiers et **net use**. Les lecteurs réseau mappés doivent avoir un nom de lettre de lecteur et être connectés à un emplacement du système de fichiers distant. Lorsque votre commande est limitée localement, sans point, le paramètre **persiste** ne conserve pas la création d’un **PSDrive** au-delà de l’étendue dans laquelle la commande s’exécute. Si vous exécutez `New-PSDrive` à l’intérieur d’un script et que vous souhaitez que le lecteur persiste indéfiniment, vous devez effectuer un point-source du script. Pour de meilleurs résultats, pour forcer un nouveau lecteur à rester indéfiniment, ajoutez le paramètre **scope** à votre commande et définissez sa valeur sur **Global**. Pour plus d’informations sur la source de points, consultez [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).
- Lecteurs externes. Lorsqu’un lecteur externe est connecté à l’ordinateur, PowerShell ajoute automatiquement un **PSDrive** au système de fichiers qui représente le nouveau lecteur. Vous n’avez pas besoin de redémarrer PowerShell. De même, lorsqu’un lecteur externe est déconnecté de l’ordinateur, PowerShell supprime automatiquement le **PSDrive** qui représente le lecteur supprimé.
- Informations d’identification pour les chemins d’accès UNC (Universal Naming Convention).

Lorsque la valeur du paramètre **root** est un chemin d’accès UNC, tel que `\\Server\Share` , les informations d’identification spécifiées dans la valeur du paramètre **Credential** sont utilisées pour créer le **PSDrive**. Dans le cas contraire, les **informations d’identification** ne sont pas effectives lorsque vous créez de nouveaux lecteurs de système de fichiers.

Certains exemples de code utilisent la projection pour réduire la longueur de ligne et améliorer la lisibilité. Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

## EXEMPLES

### Exemple 1 : créer un lecteur temporaire mappé à un partage réseau

Cet exemple crée un lecteur PowerShell temporaire qui est mappé à un partage réseau.

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

`New-PSDrive` utilise le paramètre **Name** pour spécifier le lecteur PowerShell nommé `Public` et le paramètre **PSProvider** pour spécifier le `FileSystem` fournisseur PowerShell. Le paramètre **root** spécifie le chemin d’accès UNC du partage réseau.

Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path Public:`

### Exemple 2 : créer un lecteur temporaire mappé à un répertoire local

Cet exemple crée un lecteur PowerShell temporaire qui fournit l’accès à un répertoire sur l’ordinateur local.

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

La projection crée les clés et valeurs de paramètre. Le paramètre **Name** spécifie le nom du lecteur, **mydocs**. Le paramètre **PSProvider** spécifie le `FileSystem` fournisseur PowerShell. **Root** spécifie le répertoire de l’ordinateur local. Le paramètre **Description** décrit l’objectif du lecteur. `New-PSDrive` utilise les paramètres de projection pour créer le `MyDocs` lecteur.

Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path MyDocs:`

### Exemple 3 : créer un lecteur temporaire pour une clé de Registre

Cet exemple crée un lecteur PowerShell temporaire qui fournit l’accès à une clé de registre. Il crée un lecteur nommé MyCompany qui est mappé à la `HKLM:\Software\MyCompany` clé de registre.

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

`New-PSDrive` utilise le paramètre **Name** pour spécifier le lecteur PowerShell nommé `MyCompany` et le paramètre **PSProvider** pour spécifier le `Registry` fournisseur PowerShell. Le paramètre **root** spécifie l’emplacement du Registre.

Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path MyCompany:`

### Exemple 4 : créer un lecteur réseau mappé persistant à l’aide des informations d’identification

Cet exemple mappe un lecteur réseau authentifié avec les informations d’identification d’un compte de service de domaine.
Pour plus d’informations sur l’objet **PSCredential** qui stocke les informations d’identification et sur la manière dont les mots de passe sont stockés sous forme de **SecureString**, consultez la description du paramètre **Credential** .

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> N’oubliez pas que si vous utilisez l’extrait de code ci-dessus dans un script, définissez la valeur du paramètre d' **étendue** sur « global » pour vous assurer que le lecteur persiste en dehors de l’étendue actuelle.

La `$cred` variable stocke un objet **PSCredential** qui contient les informations d’identification du compte de service. `Get-Credential` vous invite à entrer le mot de passe qui est stocké dans une **SecureString**.

`New-PSDrive` crée le lecteur réseau mappé à l’aide de plusieurs paramètres. **Nom** spécifie la `S` lettre de lecteur que Windows accepte. et la **racine** définit `\\Server01\Scripts` comme emplacement sur un ordinateur distant. **Persist** crée un lecteur réseau mappé Windows qui est enregistré sur l’ordinateur local. **PSProvider** spécifie le `FileSystem` fournisseur. **Credential** utilise la `$cred` variable pour obtenir les informations d’identification du compte de service pour l’authentification.

Le lecteur mappé peut être affiché sur l’ordinateur local dans les sessions PowerShell, l’Explorateur de fichiers et avec des outils tels que **net use**. Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path S:`

### Exemple 5 : créer des lecteurs permanents et temporaires

Cet exemple montre la différence entre un lecteur réseau mappé persistant et un lecteur PowerShell temporaire qui est mappé au même partage réseau.

Si vous fermez la session PowerShell et que vous ouvrez une nouvelle session, le temporaire `PSDrive:` n’est pas disponible, mais le `X:` lecteur persistant est disponible. Lorsque vous décidez de la méthode à utiliser pour mapper les lecteurs réseau, réfléchissez à la façon dont vous allez utiliser le lecteur. Par exemple, s’il doit être persistant et si le lecteur doit être visible par d’autres fonctionnalités de Windows.

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## PARAMETERS

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action. La valeur par défaut est l’utilisateur actuel.

Depuis PowerShell 3,0, lorsque la valeur du paramètre **root** est un chemin UNC, vous pouvez utiliser les informations d’identification pour créer des lecteurs de système de fichiers.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### Description

Spécifie une courte description du lecteur. Tapez une chaîne.

Pour afficher les descriptions de tous les lecteurs de la session, `Get-PSDrive | Format-Table Name, Description` .

Pour afficher la description d’un lecteur particulier, tapez `(Get-PSDrive <DriveName>).Description` .

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

### -Name

Spécifie le nom du nouveau lecteur. Pour les lecteurs réseau mappés persistants, utilisez une lettre de lecteur. Pour les lecteurs PowerShell temporaires, vous n’êtes pas limité aux lettres de lecteur, utilisez une chaîne valide.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Persist

Indique que cette applet de commande crée un lecteur réseau mappé Windows. Le paramètre **Persist** est uniquement disponible sur Windows.

Les lecteurs réseau mappés sont enregistrés dans Windows sur l'ordinateur local. Ils sont persistants, non spécifiques à la session et peuvent être affichés et gérés dans l’Explorateur de fichiers et d’autres outils.

Lorsque vous étendez la commande en local, sans la source de points, le paramètre **persiste** ne conserve pas la création d’un **PSDrive** au-delà de la portée dans laquelle vous exécutez la commande. Si vous exécutez `New-PSDrive` à l’intérieur d’un script et que vous souhaitez que le nouveau lecteur persiste indéfiniment, vous devez effectuer un point-source du script. Pour de meilleurs résultats, pour forcer la conservation d’un nouveau lecteur, spécifiez **Global** comme valeur du paramètre d' **étendue** et include **persiste** dans votre commande.

Le nom du lecteur doit être une lettre, telle que `D` ou `E` . La valeur du paramètre **root** doit être un chemin d’accès UNC d’un autre ordinateur. La valeur du paramètre **PSProvider** doit être `FileSystem` .

Pour déconnecter un lecteur réseau mappé Windows, utilisez l'applet de commande `Remove-PSDrive`. Lorsque vous déconnectez un lecteur réseau Windows mappé, le mappage est définitivement supprimé de l'ordinateur (et pas simplement de la session active).

les lecteurs réseau mappés sont spécifiques à un compte d'utilisateur. Les lecteurs mappés créés dans les sessions ou sessions élevées à l’aide des informations d’identification d’un autre utilisateur ne sont pas visibles dans les sessions démarrées à l’aide d’autres informations d’identification.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Spécifie le fournisseur PowerShell qui prend en charge les lecteurs de ce type.

Par exemple, si le lecteur est associé à un répertoire de partage réseau ou de système de fichiers, le fournisseur PowerShell est `FileSystem` . Si le lecteur est associé à une clé de Registre, le fournisseur est `Registry` .

Les lecteurs PowerShell temporaires peuvent être associés à n’importe quel fournisseur PowerShell. Les lecteurs réseau mappés ne peuvent être associés qu’au `FileSystem` fournisseur.

Pour afficher la liste des fournisseurs dans votre session PowerShell, utilisez l’applet de commande `Get-PSProvider` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Racine

Spécifie l’emplacement du magasin de données auquel un lecteur PowerShell est mappé.

Par exemple, spécifiez un partage réseau, tel que `\\Server01\Public` , un répertoire local, tel que `C:\Program Files` , ou une clé de Registre, telle que `HKLM:\Software\Microsoft` .

Les lecteurs PowerShell temporaires peuvent être associés à un emplacement local ou distant sur n’importe quel lecteur de fournisseur pris en charge. Les lecteurs réseau mappés ne peuvent être associés qu'à un emplacement du système de fichiers sur un ordinateur distant.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Étendue

Spécifie une portée pour le lecteur. Les valeurs acceptables pour ce paramètre sont : **Global**, **local** et **script**, ou un nombre relatif à l’étendue actuelle. Les étendues numéro 0 à travers le nombre d’étendues. Le numéro d’étendue actuel est 0 et son parent est 1. Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### None

Vous ne pouvez pas effectuer de pipeline d’entrée pour cette applet de commande.

## SORTIES

### System.Management.Automation.PSDriveInfo

## REMARQUES

`New-PSDrive` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, utilisez `Get-PSProvider` . Pour plus d’informations sur les fournisseurs, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

les lecteurs réseau mappés sont spécifiques à un compte d'utilisateur. Les lecteurs mappés créés dans les sessions ou sessions élevées à l’aide des informations d’identification d’un autre utilisateur ne sont pas visibles dans les sessions démarrées à l’aide d’autres informations d’identification.

## LIENS CONNEXES

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PSDrive](Get-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)

