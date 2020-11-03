---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 5b12e91ab5562dcce9fa4441ecd27f575f6e07a7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201126"
---
# Get-ItemPropertyValue

## SYNOPSIS
Obtient la valeur d’une ou plusieurs propriétés d’un élément spécifié.

## SYNTAX

### Chemin d’accès (par défaut)

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## Description

`Get-ItemPropertyValue`Obtient la valeur actuelle d’une propriété que vous spécifiez quand vous utilisez le paramètre *Name* , situé dans un chemin d’accès que vous spécifiez avec les paramètres *path* ou *LiteralPath* .

## EXEMPLES

### Exemple 1 : récupérer la valeur de la propriété ProductID

Cette commande obtient la valeur de la propriété **ProductID** de l’objet « \Software\Microsoft\Windows NT\CurrentVersion » dans le fournisseur de Registre Windows.

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### Exemple 2 : obtenir l’heure de la dernière écriture d’un fichier ou d’un dossier

Cette commande obtient la valeur de la propriété **LastWriteTime** , ou la dernière heure de modification d’un fichier ou d’un dossier, à partir du dossier « C:\Users\Test\Documents\ModuleToAssembly », en travaillant dans le fournisseur FileSystem.

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### Exemple 3 : obtenir plusieurs valeurs de propriété d’un fichier ou d’un dossier

Cette commande obtient les valeurs des propriétés **LastWriteTime** , **CreationTime** et **root** d’un dossier. Les valeurs de propriété sont retournées dans l’ordre dans lequel vous avez spécifié les noms de propriété.

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## PARAMETERS

### -Credential

> [!NOTE]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.
> Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés. Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Spécifie un filtre pour qualifier le paramètre **path** . Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres. Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).
Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` . Les caractères génériques sont autorisés. Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

Spécifie un chemin d’accès à un ou plusieurs emplacements. La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie le nom des propriétés à récupérer.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

Spécifie le chemin d'accès aux éléments.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.

## SORTIES

### System. Boolean, System. String, System. DateTime

Cette applet de commande retourne un objet pour chaque valeur de propriété d’élément qu’il obtient.
Le type d’objet dépend de la valeur de propriété récupérée.
Par exemple, dans un lecteur du système de fichiers, l’applet de commande peut retourner un fichier ou un dossier.

## REMARQUES

Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, exécutez l’applet de commande `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Get-ItemProperty](Get-ItemProperty.md)

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
