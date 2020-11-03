---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 926239c0bbdb17f53b7d869c0bb08c8ab125f1a4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203654"
---
# Remove-TypeData

## Synopsis
Supprime les types étendus de la session active.

## Syntaxe

### RemoveTypeDataSet (par défaut)

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveTypeSet

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveFileSet

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Remove-TypeData` applet de commande supprime les données de type étendu de la session active. Cette applet de commande affecte seulement la session active et les sessions qui sont créées dans la session active.

Vous pouvez ajouter des propriétés et des méthodes aux objets dans PowerShell en les définissant dans les `Update-TypeData` commandes et les `Types.ps1xml` fichiers. `Remove-TypeData` supprime ces propriétés et méthodes étendues de la session active. `Remove-TypeData` ne supprime pas les `Types.ps1xml` fichiers ou ne supprime pas les définitions de type étendu des `Types.ps1xml` fichiers. Pour plus d’informations sur les `Types.ps1xml` fichiers, consultez [about_Types.ps1XML](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## Exemples

### Exemple 1 : supprimer les données de type pour un type spécifié

Cet exemple supprime toutes les données de type pour le type **System. Array** de la session, y compris les données de type qui ont été ajoutées par un `Types.ps1xml` fichier et les données de type dynamique qui ont été ajoutées à la session à l’aide de l’applet de commande `Update-TypeData` .

```powershell
Remove-TypeData -TypeName System.Array
```

### Exemple 2 : supprimer un type de données étendu d’une session

Cet exemple montre l’effet de la suppression des données de type étendu d’une session. La première `Get-TypeData` obtient les données de type étendu pour le type **System. DateTime** . La sortie indique qu’une propriété **DateTime** a été ajoutée à tous les objets **System. DateTime** dans PowerShell. L' `Get-Date` applet de commande retourne un objet **System. DateTime** . La commande utilise la notation par points pour récupérer la valeur de la propriété **DateTime** de l’objet **System. DateTime** qui `Get-Date` retourne.

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

L' `Get-TypeData` applet de commande suivante pour obtenir toutes les données de type étendu pour le type **System. DateTime** et les canalise vers l' `Remove-TypeData` applet de commande pour supprimer les données de type étendu. La dernière `Get-Date` applet de commande montre l’effet de la suppression des données de type étendu pour le type **System. DateTime** . Étant donné que la propriété **System. DateTime** n’existe plus, une commande permettant d’obtenir sa valeur ne retourne rien.

### Exemple 3 : supprimer les types étendus pour les modules

Cet exemple supprime toutes les données de type étendu pour les objets de module. Quand vous dirigez un objet vers `Remove-TypeData` , `Remove-TypeData` obtient le nom du type d’objet et supprime toutes les données de type pour tous les objets de ce type.

```powershell
Get-Module | Remove-TypeData
```

### Exemple 4 : supprimer les types étendus des modules spécifiés

Cet exemple utilise le paramètre **path** de l' `Remove-TypeData` applet de commande pour supprimer les types étendus qui sont définis dans les `Types.ps1xml` fichiers ajoutés par les modules **PSScheduledJob** et **PSWorkflow** . Cette commande n’affecte pas les données de type dynamique ajoutées à l’aide de l’applet de commande `Update-TypeData` . Cette commande réussit seulement quand les modules ont été importés dans la session active.

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

Pour plus d’informations sur les modules, consultez [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).

### Exemple 5 : supprimer les types étendus d’une session distante

Cet exemple supprime les types étendus d’une session à distance. La commande utilise l' `Invoke-Command` applet de commande pour supprimer les données de type étendu pour tous les types CIM dans les sessions de la `$S` variable.

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## Paramètres

### -Path

Spécifie un tableau de fichiers que cette applet de commande supprime des données de type étendu de la session. Ce paramètre est obligatoire.

Entrez les chemins d’accès et les noms de fichiers d’un ou de plusieurs `Types.ps1xml` fichiers. Les caractères génériques ne sont pas pris en charge. Si vous omettez le chemin d'accès, l'emplacement par défaut est le répertoire actif.

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

Spécifie les données de type que cette applet de commande supprime de la session. Ce paramètre est obligatoire. Entrez une variable qui contient des objets **TypeData** ( **System. Management. Automation. instances d’exécution. TypeData** ) ou une commande qui obtient les objets **TypeData** , par exemple une `Get-TypeData` commande. Vous pouvez également diriger les objets **TypeData** vers `Remove-TypeData` .

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -TypeName

Spécifie les types pour lesquels cette applet de commande supprime toutes les données de type étendu. Pour les types de l'espace de noms système, entrez le nom court. Sinon, le nom de type complet est obligatoire. Les caractères génériques ne sont pas pris en charge.

Vous pouvez diriger les noms de types vers `Remove-TypeData` . Quand vous dirigez un objet vers `Remove-TypeData` , `Remove-TypeData` obtient le nom de type de l’objet et supprime toutes les données de type pour le type d’objet.

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Entrées

### System. Management. Automation. instances d’exécution. TypeData

Vous pouvez diriger un objet **TypeData** , tel que celui vers lequel l' `Get-TypeData` applet de commande retourne `Remove-TypeData` .

### System.String

Vous pouvez diriger les noms de types vers `Remove-TypeData` . Quand vous dirigez un objet vers `Remove-TypeData` , `Remove-TypeData` obtient le nom de type de l’objet et supprime toutes les données de type pour le type d’objet.

## Sorties

### Aucun

Cette applet de commande ne génère aucune sortie.

## Notes

`Remove-TypeData` peut supprimer uniquement les données de type étendu dans la session active. Il ne peut pas supprimer les données de type étendu qui se trouvent sur l'ordinateur, mais qui n'ont pas été ajoutées à la session active, comme des types étendus qui sont définis dans des modules qui n'ont pas été importés dans la session active.

## Liens connexes

[Get-TypeData](Get-TypeData.md)

[Update-TypeData](Update-TypeData.md)

