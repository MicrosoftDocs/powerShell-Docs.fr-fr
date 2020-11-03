---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 335f1f5b3e40eaf39cee7213b7bb02dbfa69ee3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202054"
---
# Remove-ItemProperty

## SYNOPSIS
Supprime la propriété et sa valeur d'un élément.

## SYNTAX

### Chemin d’accès (par défaut)

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Remove-ItemProperty` applet de commande supprime une propriété et sa valeur d’un élément.
Vous pouvez l’utiliser pour supprimer des valeurs de Registre et les données qu’elles contiennent.

## EXEMPLES

### Exemple 1 : supprimer une valeur de Registre

Cette commande supprime la valeur de Registre « SmpProperty » et ses données de la sous-clé « SmpApplication » de la `HKEY_LOCAL_MACHINE\Software` clé de registre.

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

Étant donné que la commande est émise à partir d’un lecteur du système de fichiers ( `PS C:\>` ), elle inclut le chemin d’accès complet de la sous-clé « SmpApplication », y compris le lecteur, `HKLM:` et la clé « logiciel ».

### Exemple 2 : supprimer une valeur de registre de l’emplacement HKCU

Ces commandes suppriment la valeur de Registre « Options », ainsi que ses données, de la sous-clé « MyApp » de « HKEY_CURRENT_USER\Software\MyCompany ».

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

La première commande utilise l' `Set-Location` applet de commande pour modifier l’emplacement actuel sur le lecteur **HKEY_CURRENT_USER** ( `HKCU:` ) et la `Software\MyCompany\MyApp` sous-clé.

La deuxième commande utilise `Remove-ItemProperty` pour supprimer la valeur de Registre « Options » et ses données de la sous-clé « MyApp ». Étant donné que **path** est requis, la commande utilise un point ( `.` ) pour indiquer l’emplacement actuel. Le paramètre **Confirm** demande une invite utilisateur avant de supprimer la valeur.

### Exemple 3 : supprimer une valeur de Registre à l’aide du pipeline

Cette commande supprime la valeur de Registre « NoOfEmployees » et ses données de la clé de `HKLM\Software\MyCompany` Registre.

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

La commande utilise l' `Get-Item` applet de commande pour récupérer un élément qui représente la clé de registre.
Elle utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet à `Remove-ItemProperty` .
Ensuite, elle utilise le paramètre **Name** de `Remove-ItemProperty` pour spécifier le nom de la valeur de registre.

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

### -Force

Force l’applet de commande à supprimer une propriété d’un objet qui, sinon, n’est pas accessible par l’utilisateur.
L'implémentation est différente d'un fournisseur à l'autre.
Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
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

Spécifie les noms des propriétés à supprimer.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Path

Spécifie le chemin d’accès de l’élément dont les propriétés sont supprimées.
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

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

- Dans le fournisseur de Registre PowerShell, les valeurs de Registre sont considérées comme des propriétés d’une clé de registre ou d’une sous-clé. Vous pouvez utiliser les applets de commande **ItemProperty** pour gérer ces valeurs.
- `Remove-ItemProperty` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Get-Item](Get-Item.md)

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-Item](Remove-Item.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[Set-Location](Set-Location.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

