---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: abf6a5ef365a606b6ca501e9cb924528763a8754
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204453"
---
# Get-ItemProperty

## SYNOPSIS
Obtient les propriétés de l'élément spécifié.

## SYNTAX

### Chemin d’accès (par défaut)

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## Description

L' `Get-ItemProperty` applet de commande obtient les propriétés des éléments spécifiés.
Par exemple, vous pouvez utiliser cette applet de commande pour obtenir la valeur de la propriété LastAccessTime d’un objet fichier. Vous pouvez également utiliser cette applet de commande pour afficher les entrées de Registre et leurs valeurs.

## EXEMPLES

### Exemple 1 : obtenir des informations sur un répertoire spécifique

Cette commande obtient des informations sur le `C:\Windows` répertoire.

```powershell
Get-ItemProperty C:\Windows
```

### Exemple 2 : obtenir les propriétés d’un fichier spécifique

Cette commande obtient les propriétés du `C:\Test\Weather.xls` fichier.
Le résultat est dirigé vers l' `Format-List` applet de commande pour afficher la sortie sous forme de liste.

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### Exemple 3 : afficher le nom de la valeur et les données des entrées de Registre dans une sous-clé de Registre

Cette commande affiche le nom de la valeur et les données de chacune des entrées de Registre contenues dans la sous-clé de Registre « CurrentVersion ».

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

> [!NOTE]
> Cette commande requiert l’existence d’un lecteur PowerShell nommé `HKLM:` qui est mappé à la ruche « HKEY_LOCAL_MACHINE » du Registre.
>
> Un lecteur avec ce nom et ce mappage est disponible dans PowerShell par défaut.
> Le chemin d'accès à cette sous-clé de Registre peut également être spécifié à l'aide du chemin d'accès suivant, commençant par le nom du fournisseur suivi de deux deux-points :
>
> `Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

### Exemple 4 : obtenir le nom de la valeur et les données d’une entrée de Registre dans une sous-clé de Registre

Cette commande obtient le nom et les données de la valeur de l’entrée de Registre « ProgramFilesDir figurant » dans la sous-clé de Registre « CurrentVersion ».
Le **chemin d’accès** spécifie la sous-clé et le paramètre **Name** spécifie le nom de la valeur de l’entrée.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### Exemple 5 : obtenir les noms de valeur et les données des entrées de Registre dans une clé de Registre

Cette commande obtient les noms de valeur et les données des entrées de Registre dans la clé de Registre « PowerShellEngine ». Les résultats sont présentés dans l'exemple de sortie suivant.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
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
Default value: Current user
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

Required: False
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

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-ItemProperty` .

## SORTIES

### System. Boolean, System. String, System. DateTime

`Get-ItemProperty` retourne un objet pour chaque propriété d’élément qu’il obtient. Le type d'objet dépend de l'objet récupéré. Par exemple, dans un lecteur du système de fichiers, un fichier ou un dossier peut être retourné.

## REMARQUES

L' `Get-ItemProperty` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
