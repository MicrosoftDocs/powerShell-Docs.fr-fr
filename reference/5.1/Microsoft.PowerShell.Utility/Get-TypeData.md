---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: 431b768ba909ddbd3671f03fc52789ae56c01019
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203245"
---
# Get-TypeData

## Synopsis
Obtient les données de type étendu dans la session active.

## Syntaxe

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## Description

L' `Get-TypeData` applet de commande obtient les données de type étendu dans la session active. Cela comprend les données de type qui ont été ajoutées à la session par `Types.ps1xml` fichier et les données de type dynamique qui ont été ajoutées à l’aide du paramètre de l’applet de commande `Update-TypeData` .

Vous pouvez utiliser les données de type étendu qui sont `Get-TypeData` retournées pour examiner les données de type dans la session et les envoyer aux `Update-TypeData` applets de commande et `Remove-TypeData` .

Les données de type étendu ajoutent des propriétés et des méthodes aux objets dans PowerShell. Vous pouvez utiliser les propriétés et les méthodes ajoutées de la même manière que vous utiliseriez les propriétés et les méthodes qui sont définies dans le type d'objet. Toutefois, lors de l’écriture de scripts, sachez que les propriétés et les méthodes ajoutées peuvent ne pas être présentes dans chaque session PowerShell.

Pour plus d’informations sur les `Types.ps1xml` fichiers, consultez [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md). Pour plus d’informations sur les données de type dynamique ajoutées par l’applet de commande `Update-TypeData` , consultez `Update-TypeData` .

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## Exemples

### Exemple 1 : récupération de toutes les données de type étendu

Cet exemple obtient toutes les données de type étendu dans la session active.

 ```powershell
Get-TypeData
```

### Exemple 2 : récupération des types par nom

Cet exemple obtient tous les types dans la session active qui ont des noms qui contiennent des événements.

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### Exemple 3 : obtenir le bloc de script qui crée une valeur de propriété

Cet exemple obtient le bloc de script qui crée la valeur de la propriété **eventID** des objets **EventLogEntry** .

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### Exemple 4 : obtenir le bloc de script qui définit une propriété pour un objet spécifié

Cet exemple obtient le bloc de script qui définit la propriété **DateTime** des objets **System. DateTime** dans PowerShell.

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

La commande utilise l' `Get-TypeData` applet de commande pour obtenir les données de type étendu pour le type **System. DataTime** . La commande obtient la propriété **Members** de l'objet **TypeData** .

La propriété **members** contient une table de hachage des propriétés et des méthodes qui sont définies par les données de type étendu. Chaque clé dans la table de hachage Members est un nom de propriété ou de méthode et chaque valeur est la définition de la valeur de propriété ou de méthode.

La commande obtient la clé **DateTime** dans **members** et sa valeur de propriété **GetScriptBlock** .

La sortie affiche le bloc de script qui crée la valeur de la propriété **DateTime** de chaque objet **System. DateTime** dans PowerShell.

## Paramètres

### -TypeName

Spécifie les données de type sous forme de tableau uniquement pour les types avec les noms spécifiés. Par défaut, `Get-TypeData` obtient tous les types dans la session.

Entrez des noms de types ou des modèles de nom. Les noms complets ou les modèles de nom avec des caractères génériques sont requis, même pour les types de l’espace de noms System. Les caractères génériques sont pris en charge et le nom de paramètre **TypeName** est facultatif. Vous pouvez également diriger les noms de types vers `Get-TypeData` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Entrées

### System.String

Vous pouvez diriger les noms de types vers `Get-TypeData` .

## Sorties

### System. Management. Automation. instances d’exécution. TypeData

## Notes

`Get-TypeData` Obtient uniquement les données de type étendu dans la session active. Il n'obtient pas les données de type étendu sur l'ordinateur, mais n'a pas été ajouté à la session active, comme les types étendus qui sont définis dans les modules qui n'ont pas été importés dans la session active.

## Liens connexes

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Remove-TypeData](Remove-TypeData.md)

[Update-TypeData](Update-TypeData.md)
