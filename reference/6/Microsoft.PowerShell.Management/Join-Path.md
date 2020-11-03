---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 7752688a04057861fffdbc7b30c293239acb132e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202882"
---
# Join-Path

## SYNOPSIS
Combine un chemin d’accès et un chemin d’accès d’enfant en un seul chemin d’accès.

## SYNTAX

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## Description

L’applet de commande combine un chemin d’accès et un chemin d’accès `Join-Path` enfant dans un chemin d’accès unique.
Le fournisseur fournit les séparateurs de chemin d’accès.

## EXEMPLES

### Exemple 1 : combiner un chemin d’accès avec un chemin d’accès enfant

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

Cette commande utilise `Join-Path` pour combiner un chemin d’accès à un childpath.

Étant donné que la commande est exécutée à partir du `FileSystem` fournisseur, elle fournit le `\` délimiteur pour joindre les chemins d’accès.

### Exemple 2 : combiner des chemins qui contiennent déjà des séparateurs de répertoire

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

Séparateurs de répertoire existants `\` et gérés pour qu’il n’y ait qu’un seul séparateur entre `Path` et `ChildPath`

### Exemple 3 : afficher des fichiers et des dossiers en joignant un chemin d’accès à un chemin d’accès enfant

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

Cette commande affiche les fichiers et les dossiers qui sont référencés en joignant le \* chemin d’accès C:\win et le \* chemin d’accès enfant système.
Elle affiche les mêmes fichiers et dossiers que `Get-ChildItem` , mais elle affiche le chemin d’accès complet à chaque élément.
Dans cette commande, les `Path` `ChildPath` noms de paramètres facultatifs et sont omis.

### Exemple 4 : utiliser Join-Path avec le fournisseur de Registre PowerShell

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

Cette commande affiche les clés de Registre dans la `HKLM\System` sous-clé de Registre qui inclut `ControlSet` .

Le `Resolve` paramètre tente de résoudre le chemin d’accès joint, y compris les caractères génériques du chemin d’accès du fournisseur actuel `HKLM:\`

### Exemple 5 : combiner plusieurs racines de chemin d’accès avec un chemin d’accès enfant

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

Cette commande utilise `Join-Path` pour combiner plusieurs racines de chemin d’accès avec un chemin d’accès enfant.

> [!NOTE]
> Les lecteurs spécifiés par `Path` doivent exister ou la jointure de cette entrée échouera.

### Exemple 6 : combiner les racines d’un lecteur du système de fichiers avec un chemin d’accès enfant

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

Cette commande combine les racines de chaque lecteur du système de fichiers PowerShell dans la console avec le chemin d’accès enfant subdir.

La commande utilise l' `Get-PSDrive` applet de commande pour récupérer les lecteurs PowerShell pris en charge par le fournisseur FileSystem.
L' `ForEach-Object` instruction sélectionne uniquement la propriété racine des `PSDriveInfo` objets et la combine avec le chemin d’accès enfant spécifié.

La sortie indique que les lecteurs PowerShell sur l’ordinateur incluaient un lecteur mappé au répertoire C:\Program Files.

### Exemple 7 : combiner un nombre indéfini de chemins d’accès

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

Le `AdditionalChildPath` paramètre permet de joindre un nombre illimité de chemins d’accès.

Dans cet exemple, aucun nom de paramètre n’est utilisé. par conséquent, « a » est lié à `Path` , « b » `ChildPath` et « c-g » à `AdditionalChildPath`

## PARAMETERS

### -AdditionalChildPath

Spécifie des éléments supplémentaires à ajouter à la valeur du paramètre *path* . Le `ChildPath` paramètre est toujours obligatoire et doit également être spécifié.

Ce paramètre est spécifié avec la `ValueFromRemainingArguments` propriété qui permet de joindre un nombre indéfini de chemins d’accès.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ChildPath

Spécifie les éléments à ajouter à la valeur du `Path` paramètre.
Les caractères génériques sont autorisés.
Le `ChildPath` paramètre est obligatoire, bien que le nom du paramètre (« ChildPath ») soit facultatif.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

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

### -Path

Spécifie les chemins d’accès principaux auxquels le chemin d’accès enfant est ajouté.
Les caractères génériques sont autorisés.

La valeur de `Path` détermine quel fournisseur joint les chemins d’accès et ajoute les séparateurs de chemin d’accès.
Le `Path` paramètre est obligatoire, bien que le nom du paramètre (« Path ») soit facultatif.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Résoudre

Indique que cette applet de commande doit tenter de résoudre le chemin d’accès joint à partir du fournisseur actuel.

- Si des caractères génériques sont utilisés, l’applet de commande retourne tous les chemins qui correspondent au chemin d’accès joint.
- Si **aucun** caractère générique n’est utilisé, l’applet de commande génère une erreur si le chemin d’accès n’existe pas.

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

### System.String

Cette applet de commande retourne une chaîne qui contient le chemin d’accès résultant.

## REMARQUES

Les applets de commande qui contiennent le nom du chemin d’accès (les applets de commande Path) manipulent les noms de chemin d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter. Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier. Utilisez-les comme Dirname, Normpath, Realpath, Join ou tout autre manipulateur de chemin d’accès.

Vous pouvez utiliser les applets de commande Path avec plusieurs fournisseurs, notamment les `FileSystem` `Registry` fournisseurs, et `Certificate` .

Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.
Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .
Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Convert-Path](Convert-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-PSDrive](Get-PSDrive.md)
