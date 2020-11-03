---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: 2e7ebe3a528095873dc7ba5ba0deba2905f531ee
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204214"
---
# ConvertTo-Xml

## SYNOPSIS
Crée une représentation XML d'un objet.

## SYNTAX

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## Description

L' `ConvertTo-Xml` applet de commande crée une représentation [XML](/dotnet/api/system.xml.xmldocument) d’un ou de plusieurs objets .net. Pour utiliser cette applet de commande, dirigez un ou plusieurs objets vers l’applet de commande, ou utilisez le paramètre **InputObject** pour spécifier l’objet.

Lorsque vous dirigez plusieurs objets vers `ConvertTo-Xml` ou utilisez le paramètre **InputObject** pour envoyer plusieurs objets, `ConvertTo-Xml` retourne un document XML en mémoire unique qui comprend les représentations de tous les objets.

Cette applet de commande est similaire à [Export-Clixml](./Export-Clixml.md) , à ceci près que `Export-Clixml` stocke les données XML résultantes dans un fichier [XML Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm) qui peuvent être réimportées en tant qu’objets avec [Import-Clixml](./Import-Clixml.md). `ConvertTo-Xml` retourne une représentation en mémoire d’un document XML, ce qui vous permet de continuer à le traiter dans PowerShell. `ConvertTo-Xml` n’a pas d’option permettant de convertir des objets en langage XML CLI.

## EXEMPLES

### Exemple 1 : convertir une date en XML

```
PS C:\> Get-Date | ConvertTo-Xml
```

Cette commande convertit la date actuelle (un objet **DateTime** ) en XML.

### Exemple 2 : convertir des processus en XML

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

Cette commande convertit les objets processus qui représentent tous les processus sur l'ordinateur en document XML. Les objets sont étendus à une profondeur de trois niveaux.

## PARAMETERS

### -As

Détermine le format de sortie.
Les valeurs valides pour ce paramètre sont :

- Chaîne.
retourne une chaîne unique.
- Flux.
retourne un tableau de chaînes.
- Document.
Retourne un objet **XmlDocument** .

La valeur par défaut est document.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Profondeur

Spécifie le nombre de niveaux d'objets contenus inclus dans la représentation XML. La valeur par défaut est 1.

Par exemple, si les propriétés de l'objet contiennent également des objets, pour enregistrer une représentation XML des propriétés des objets contenus, vous devez spécifier une profondeur de 2.

La valeur par défaut peut être remplacée par le type d'objet des fichiers Types.ps1xml. Pour plus d'informations, consultez about_Types.ps1xml.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie l'objet à convertir. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets. Vous pouvez également diriger les objets vers **ConvertTo-XML** .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

Omet l'attribut Type des nœuds d'objet.

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

### System. Management. Automation. PSObject

Vous pouvez diriger n’importe quel objet vers **ConvertTo-XML** .

## SORTIES

### Document System. String ou System.Xml.Xml

La valeur du paramètre *As* détermine le type d’objet retourné par **ConvertTo-XML** .

## REMARQUES

## LIENS CONNEXES

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Html](ConvertTo-Html.md)

[Export-Clixml](Export-Clixml.md)

[Obtient la date](Get-Date.md)

[Import-Clixml](Import-Clixml.md)

