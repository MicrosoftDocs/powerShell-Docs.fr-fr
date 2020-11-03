---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: b5dfd3e55ceadf4141e977f0fb879ba5d05538f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202046"
---
# Rename-Item

## SYNOPSIS
Renomme un élément dans un espace de noms de fournisseur PowerShell.

## SYNTAX

### ByPath (par défaut)

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## Description

L' `Rename-Item` applet de commande modifie le nom d’un élément spécifié. Cette applet de commande n’affecte pas le contenu de l’élément qui est renommé.

Vous ne pouvez pas utiliser `Rename-Item` pour déplacer un élément, par exemple en spécifiant un chemin d’accès avec le nouveau nom. Pour déplacer et renommer un élément, utilisez l' `Move-Item` applet de commande.

## EXEMPLES

### Exemple 1 : renommer un fichier

Cette commande renomme le fichier `daily_file.txt` `monday_file.txt` .

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### Exemple 2 : renommer et déplacer un élément

Vous ne pouvez pas utiliser `Rename-Item` à la fois pour renommer et déplacer un élément. Plus précisément, vous ne pouvez pas fournir de chemin d’accès pour la valeur du paramètre **NewName** , sauf si le chemin d’accès est identique au chemin d’accès spécifié dans le paramètre **path** . Sinon, seul un nouveau nom est autorisé.

Cet exemple tente de renommer le `project.txt` fichier du répertoire actif dans `old-project.txt` le `D:\Archive` répertoire. Il en résulte l’erreur indiquée dans la sortie.

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### Exemple 3 : renommer une clé de Registre

Cet exemple renomme une clé de registre de la **publication** en **marketing** . Une fois la commande exécutée, la clé est renommée, mais les entrées de Registre qui figurent dans la clé demeurent inchangées.

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### Exemple 4 : renommer plusieurs fichiers

Cet exemple renomme tous les `*.txt` fichiers du répertoire actif `*.log` .

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

L' `Get-ChildItem` applet de commande obtient tous les fichiers du dossier actif qui ont une `.txt` extension de fichier, puis les dirige vers `Rename-Item` . La valeur de **NewName** est un bloc de script qui s’exécute avant que la valeur ne soit soumise au paramètre **NewName** .

Dans le bloc de script, la `$_` variable automatique représente chaque objet fichier tel qu’il arrive à la commande via le pipeline. Le bloc de script utilise l' `-replace` opérateur pour remplacer l’extension de fichier de chaque fichier par `.log` . Notez que la correspondance à l’aide de l’opérateur ne respecte `-replace` pas la casse.

## PARAMETERS

### -Credential

> [!NOTE]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell. Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

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

### -Force

Force l’applet de commande à renommer des éléments qui ne peuvent pas être modifiés autrement, tels que des fichiers cachés ou en lecture seule ou des alias ou des variables en lecture seule. L’applet de commande ne peut pas modifier les alias ou variables constants.
L'implémentation est différente d'un fournisseur à l'autre. Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.

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

### -LiteralPath

Spécifie un chemin d’accès à un ou plusieurs emplacements. La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewName

Spécifie le nouveau nom de l’élément. Entrez uniquement un nom, et non un chemin d’accès et un nom. Si vous entrez un chemin d’accès différent du chemin d’accès spécifié dans le paramètre **path** , `Rename-Item` génère une erreur.
Pour renommer et déplacer un élément, utilisez `Move-Item` .

Vous ne pouvez pas utiliser de caractères génériques dans la valeur du paramètre **NewName** . Pour spécifier un nom pour plusieurs fichiers, utilisez l’opérateur **Replace** dans une expression régulière. Pour plus d’informations sur l’opérateur Replace, consultez [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).

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

### -PassThru

Retourne un objet qui représente l’élément dans le pipeline. Par défaut, cette applet de commande ne génère aucun résultat.

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

### -Path

Spécifie le chemin d’accès de l’élément à renommer.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.

## SORTIES

### Aucun ou un objet qui représente l’élément renommé.

Cette applet de commande génère un objet qui représente l’élément renommé, si vous spécifiez le paramètre **PassThru** . Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

`Rename-Item` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

