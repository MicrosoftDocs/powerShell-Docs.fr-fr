---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: e2498c02d42123e207b49e622654d3cb881fc0fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595504"
---
# Split-Path

## SYNOPSIS
Retourne la partie spécifiée d'un chemin d'accès.

## SYNTAXE

### ParentSet (par défaut)

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LeafSet

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### LeafBaseSet

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### ExtensionSet

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### QualifierSet

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### NoQualifierSet

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### IsAbsoluteSet

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LiteralPathSet

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## Description

L' `Split-Path` applet de commande retourne uniquement la partie spécifiée d’un chemin d’accès, par exemple le dossier parent, un sous-dossier ou un nom de fichier. Elle peut également obtenir des éléments qui sont référencés par le chemin d’accès fractionné et indiquer si le chemin d’accès est relatif ou absolu.

Vous pouvez utiliser cette applet de commande pour obtenir ou envoyer uniquement une partie sélectionnée d’un chemin d’accès.

## EXEMPLES

### Exemple 1 : obtenir le qualificateur d’un chemin d’accès

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

Cette commande retourne uniquement le qualificateur du chemin d’accès. Le qualificateur est le lecteur.

### Exemple 2 : afficher les noms de fichiers

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

Cette commande affiche les fichiers qui sont référencés par le chemin d’accès fractionné. Étant donné que ce chemin d’accès est fractionné au dernier élément, également connu sous le nom de feuille, la commande affiche uniquement les noms de fichiers.

Le paramètre **Resolve** indique `Split-Path` à d’afficher les éléments référencés par le chemin d’accès de fractionnement, au lieu d’afficher le chemin d’accès de fractionnement.

Comme toutes les `Split-Path` commandes, cette commande retourne des chaînes. Elle ne retourne pas d’objets **FileInfo** représentant les fichiers.

### Exemple 3 : récupération du conteneur parent

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

Cette commande retourne uniquement les conteneurs parents du chemin d’accès. Comme il n’inclut pas de paramètres pour spécifier le fractionnement, `Split-Path` utilise la valeur par défaut de l’emplacement de fractionnement, qui est le **parent**.

### Exemple 4 : détermine si un chemin d’accès est absolu

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

Cette commande détermine si le chemin d’accès est relatif ou absolu. Dans ce cas, étant donné que le chemin d’accès est relatif au dossier actif, représenté par un point ( `.` ), il retourne `$False` .

### Exemple 5 : modifier l’emplacement d’un chemin d’accès spécifié

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

Cette commande remplace votre emplacement par le dossier qui contient le profil PowerShell.

La commande entre parenthèses utilise `Split-Path` pour retourner uniquement le parent du chemin d’accès stocké dans la `$Profile` variable intégrée. Le paramètre **parent** est le paramètre d’emplacement de fractionnement par défaut.
Par conséquent, vous pouvez l’omettre de la commande. Les parenthèses indiquent à PowerShell d’exécuter la commande en premier. Il s’agit d’une méthode utile pour vous déplacer vers un dossier qui a un nom de chemin d’accès long.

### Exemple 6 : fractionner un chemin d’accès à l’aide du pipeline

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

Cette commande utilise un opérateur de pipeline ( `|` ) pour envoyer un chemin d’accès à `Split-Path` . Le chemin d’accès figure entre guillemets pour indiquer qu’il s’agit d’un jeton unique.

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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Extension

Indique que cette applet de commande retourne uniquement l’extension de la feuille. Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement `.log` .

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IsAbsolute

Indique que cette applet de commande retourne $True si le chemin d’accès est absolu et $False s’il est relatif. Un chemin d’accès absolu a une longueur supérieure à zéro et n’utilise pas de point ( `.` ) pour indiquer le chemin d’accès actuel.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Feuille

Indique que cette applet de commande retourne uniquement le dernier élément ou conteneur dans le chemin d’accès. Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement PASS1. log.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LeafBase

Indique que cette applet de commande retourne uniquement le nom de base de la feuille. Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement `Pass1` .

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie les chemins d’accès à fractionner. Contrairement au paramètre **Path**, la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n'est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoQualifier

Indique que cette applet de commande retourne le chemin d’accès sans le qualificateur. Pour les fournisseurs de système de fichiers ou de Registre, le qualificateur est le lecteur du chemin d’accès du fournisseur, tel que `C:` ou `HKCU:` . Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement `\Test\Logs\Pass1.log` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Parent

Indique que cette applet de commande retourne uniquement les conteneurs parents de l’élément ou du conteneur spécifié par le chemin d’accès. Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne `C:\Test\Logs` .
Le paramètre **parent** est le paramètre d’emplacement de fractionnement par défaut.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie les chemins d’accès à fractionner. Les caractères génériques sont autorisés. Si le chemin d’accès inclut des espaces, mettez-le entre guillemets. Vous pouvez également diriger un chemin vers cette applet de commande.

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Qualificateur

Indique que cette applet de commande retourne uniquement le qualificateur du chemin d’accès spécifié. Pour les fournisseurs de système de fichiers ou de Registre, le qualificateur est le lecteur du chemin d’accès du fournisseur, tel que `C:` ou `HKCU:` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Résoudre

Indique que cette applet de commande affiche les éléments qui sont référencés par le chemin d’accès de fractionnement résultant au lieu d’afficher les éléments de chemin d’accès.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.

## SORTIES

### System. String, System. Boolean

`Split-Path` retourne des chaînes de texte. Lorsque vous spécifiez le paramètre **Resolve** , `Split-Path` retourne une chaîne qui décrit l’emplacement des éléments ; il ne retourne pas d’objets qui représentent les éléments, tels qu’un objet **FileInfo** ou **RegistryKey** .

Lorsque vous spécifiez le paramètre **IsAbsolute** , `Split-Path` retourne une valeur **booléenne** .

## REMARQUES

- Les paramètres d’emplacement de fractionnement (**qualifier**, **parent**, **extension**, **feuille**, **LeafBase** et **NoQualifier**) sont exclusifs. Autrement dit, vous ne pouvez utiliser qu’un seul de ces paramètres dans chaque commande.

- Les applets de commande qui contiennent le nom de **chemin** d’accès (les applets de commande **path** ) fonctionnent avec des noms de chemins d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter. Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier. Utilisez-les de la même façon que vous utilisez **dirname**, **Normpath**, **realpath**, **join** ou d’autres manipulateurs de chemin d’accès.

- Vous pouvez utiliser les applets de commande **path** avec plusieurs fournisseurs. Il s’agit notamment des fournisseurs de système de fichiers, de Registre et de certificats.

- `Split-Path` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez about_Providers.

## LIENS CONNEXES

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Test-Path](Test-Path.md)
