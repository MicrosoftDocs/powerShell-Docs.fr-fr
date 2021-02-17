---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSReadLine
ms.date: 02/16/2021
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 22ad8a33f80ad5f4d75fe23c0c8f6c845a40d748
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563248"
---
# Set-PSReadLineKeyHandler

## SYNOPSIS
Lie des clés à des fonctions de gestionnaire de clés définies par l’utilisateur ou PSReadLine.

## SYNTAXE

### ScriptBlock

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### Fonction

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## Description

L' `Set-PSReadLineKeyHandler` applet de commande personnalise le résultat lorsqu’une touche ou une séquence de touches est enfoncée. Avec les combinaisons de touches définies par l’utilisateur, vous pouvez effectuer pratiquement tout ce qui est possible à partir d’un script PowerShell.

## EXEMPLES

### Exemple 1 : lier la touche de direction à une fonction

Cette commande lie la touche de direction haut à la fonction **HistorySearchBackward** . Cette fonction recherche les lignes de commande dans l’historique des commandes qui commencent par le contenu actuel de la ligne de commande.

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### Exemple 2 : lier une clé à un bloc de script

Cet exemple montre comment une clé unique peut être utilisée pour exécuter une commande. La commande lie la clé `Ctrl+B` à un bloc de script qui efface la ligne, insère le mot « Build », puis accepte la ligne.

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## PARAMETERS

### -BriefDescription

Brève description de la combinaison de touches. Cette description est affichée par l' `Get-PSReadLineKeyHandler` applet de commande.

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Corde

Clé ou séquence de clés à lier à une fonction ou à un bloc de script. Utilisez une chaîne unique pour spécifier une seule liaison. Si la liaison est une séquence de clés, séparez les clés par une virgule, comme dans l’exemple suivant :

`Ctrl+X,Ctrl+L`

> [!NOTE]
> À partir de PSReadLine 2.0.0, le paramètre **corde** respecte la **casse**. Cela signifie `Ctrl+X` qu' `Ctrl+x` elle créera des liaisons différentes.

Ce paramètre accepte un tableau de chaînes. Chaque chaîne est une liaison distincte, et non une séquence de clés pour une seule liaison.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### Description

Spécifie une description plus détaillée de la combinaison de touches qui est visible dans la sortie de l’applet de commande `Get-PSReadLineKeyHandler` .

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fonction

Spécifie le nom d’un gestionnaire de clés existant fourni par PSReadLine. Ce paramètre vous permet de relier des liaisons de clés existantes ou de lier un gestionnaire qui est actuellement indépendant.

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

Spécifie une valeur de bloc de script à exécuter lorsque le segment est entré. PSReadLine transmet un ou deux paramètres à ce bloc de script. Le premier paramètre est un objet **ConsoleKeyInfo** représentant la touche enfoncée. Le deuxième argument peut être n’importe quel objet en fonction du contexte.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

Spécifiez le mode VI auquel la liaison s’applique.

Les valeurs autorisées sont :

- Insérer
- Commande

```yaml
Type: Microsoft.PowerShell.ViMode
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

### None

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### None

Cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[PSReadLineOption](Get-PSReadLineOption.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)
