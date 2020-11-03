---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: eb7bafff1af34ef34a1b67c1fbe8f9e2db0ca7ad
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203097"
---
# Update-TypeData

## Synopsis
Met à jour les données de type étendu dans la session.

## Syntaxe

### (Par défaut)

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DynamicTypeSet

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### TypeDataSet

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Update-TypeData` applet de commande met à jour les données de type étendu dans la session en rechargeant les `Types.ps1xml` fichiers en mémoire et en ajoutant de nouvelles données de type étendu.

Par défaut, PowerShell charge les données de type étendu en fonction des besoins. Sans paramètres, `Update-TypeData` recharge tous les `Types.ps1xml` fichiers qu’il a chargés dans la session, y compris tous les fichiers de type que vous avez ajoutés. Vous pouvez utiliser les paramètres de `Update-TypeData` pour ajouter de nouveaux fichiers de type et ajouter et remplacer des données de type étendu.

L' `Update-TypeData` applet de commande peut être utilisée pour précharger toutes les données de type. Cette fonctionnalité est particulièrement utile quand vous développez des types et que vous souhaitez charger ces nouveaux types à des fins de test.

À compter de Windows PowerShell 3,0, vous pouvez utiliser `Update-TypeData` pour ajouter et remplacer des données de type étendu dans la session sans utiliser de `Types.ps1xml` fichier. Les données de type ajoutées de manière dynamique, c'est-à-dire sans fichier, sont ajoutées uniquement à la session active. Pour ajouter les données de type à toutes les sessions, ajoutez une `Update-TypeData` commande à votre profil PowerShell. Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

En outre, à compter de Windows PowerShell 3,0, vous pouvez utiliser l' `Get-TypeData` applet de commande pour récupérer les types étendus dans la session active et l' `Remove-TypeData` applet de commande pour supprimer les types étendus de la session active.

Les exceptions qui se produisent dans les propriétés, ou l’ajout de propriétés à une `Update-TypeData` commande, ne signalent pas d’erreurs. Cela permet de supprimer des exceptions qui se produisent dans de nombreux types courants durant la mise en forme et la sortie. Si vous obtenez des propriétés .NET, vous pouvez contourner la suppression des exceptions en utilisant la syntaxe de méthode à la place, comme indiqué dans l’exemple suivant :

`"hello".get_Length()`

Notez que la syntaxe de méthode peut uniquement être utilisée avec des propriétés .NET. Les propriétés ajoutées en exécutant l’applet de commande `Update-TypeData` ne peuvent pas utiliser la syntaxe de méthode.

Pour plus d’informations sur les `Types.ps1xml` fichiers dans PowerShell, consultez [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).

## Exemples

### Exemple 1 : mettre à jour les types étendus

```powershell
Update-TypeData
```

Cette commande met à jour la configuration de type étendu à partir des `Types.ps1xml` fichiers qui ont déjà été utilisés dans la session.

### Exemple 2 : mettre à jour les types plusieurs fois

Cet exemple montre comment mettre à jour les types dans un fichier de type plusieurs fois dans la même session.

La première commande met à jour la configuration de type étendu à partir des `Types.ps1xml` fichiers, en traitant les `TypesA.types.ps1xml` fichiers et en `TypesB.types.ps1xml` premier.

La deuxième commande montre comment mettre à jour le `TypesA.types.ps1xml` , comme vous pouvez le faire si vous avez ajouté ou modifié un type dans le fichier. Vous pouvez répéter la commande précédente pour le `TypesA.types.ps1xml` fichier ou exécuter une `Update-TypeData` commande sans paramètres, car `TypesA.types.ps1xml` figure déjà dans la liste des fichiers de type pour la session active.

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### Exemple 3 : ajouter une propriété de script aux objets DateTime

Cet exemple utilise `Update-TypeData` pour ajouter la propriété de script **Quarter** aux objets **System. DateTime** dans la session active, tels que ceux retournés par l’applet de commande `Get-Date` .

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

La `Update-TypeData` commande utilise le paramètre **TypeName** pour spécifier **le type System. DateTime** , le paramètre **MemberName** pour spécifier un nom pour la nouvelle propriété, la propriété **MemberType** pour spécifier le type **ScriptProperty** et le paramètre **value** pour spécifier le script qui détermine le trimestre annuel.

La valeur de la propriété **Value** est un script qui calcule le trimestre annuel actif. Le bloc de script utilise la `$this` variable automatique pour représenter l’instance actuelle de l’objet et l’opérateur in pour déterminer si la valeur de mois apparaît dans chaque tableau d’entiers. Pour plus d’informations sur l' `-in` opérateur, consultez [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).

La deuxième commande obtient la nouvelle propriété Quarter de la date actuelle.

### Exemple 4 : mettre à jour un type qui s’affiche dans des listes par défaut

Cet exemple montre comment définir les propriétés d’un type qui s’affiche dans des listes par défaut, autrement dit, quand aucune propriété n’est spécifiée. Étant donné que les données de type ne sont pas spécifiées dans un `Types.ps1xml` fichier, elles sont effectives uniquement dans la session active.

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

La première commande utilise l' `Update-TypeData` applet de commande pour définir les propriétés de liste par défaut pour le type **System. DateTime** . La commande utilise le paramètre **TypeName** pour spécifier le type et le paramètre **DefaultDisplayPropertySet** pour spécifier les propriétés par défaut d'une liste. Les propriétés sélectionnées incluent la nouvelle propriété de script **Quarter** qui a été ajoutée dans un exemple précédent.

La deuxième commande utilise l' `Get-Date` applet de commande pour obtenir un objet **System. DateTime** qui représente la date actuelle. La commande utilise un opérateur de pipeline ( `|` ) pour envoyer l’objet **DateTime** à l’applet de commande `Format-List` . Étant donné que la `Format-List` commande ne spécifie pas les propriétés à afficher dans la liste, PowerShell utilise les valeurs par défaut qui ont été établies par la `Update-TypeData` commande.

### Exemple 5 : mettre à jour les données de type pour un objet dirigé

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

Cet exemple montre que lorsque vous dirigez un objet vers `Update-TypeData` , `Update-TypeData` ajoute des données de type étendu pour le type d’objet.

Cette technique est plus rapide que l’utilisation de l' `Get-Member` applet `Get-Type` de commande ou de la méthode pour accéder au type d’objet. Toutefois, si vous dirigez une collection d’objets vers `Update-TypeData` , elle met à jour les données de type du premier type d’objet, puis retourne une erreur pour tous les autres objets de la collection, car le membre est déjà défini sur le type.

La première commande utilise l' `Get-Module` applet de commande pour récupérer le module PSScheduledJob. La commande dirige l’objet module vers l' `Update-TypeData` applet de commande, qui met à jour les données de type pour le type **System. Management. Automation. PSModuleInfo** et les types dérivés, tels que le type ModuleInfoGrouping qui `Get-Module` retourne quand vous utilisez le paramètre **listAvailable** dans la commande.

La `Update-TypeData` commande ajoute la propriété de script **SupportsUpdatableHelp** à tous les modules importés. La valeur du paramètre **value** est un script qui retourne `$True` si la propriété **HelpInfoUri** du module est remplie et dans le `$False` cas contraire.

La deuxième commande transmet les objets de module de `Get-Module` à l’applet de commande `Format-Table` , qui affiche les propriétés **Name** et **SupportsUpdatableHelp** de tous les modules d’une liste.

## Paramètres

### -AppendPath

Spécifie le chemin d’accès aux fichiers facultatifs `.ps1xml` . Les fichiers spécifiés sont chargés dans l'ordre dans lequel ils sont répertoriés après le chargement des fichiers intégrés. Vous pouvez également diriger une valeur **AppendPath** vers `Update-TypeData` .

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DefaultDisplayProperty

Spécifie la propriété du type qui est affiché par l' `Format-Wide` applet de commande quand aucune autre propriété n’est spécifiée.

Tapez le nom d'une propriété standard ou étendue du type. La valeur de ce paramètre peut correspondre au nom d'un type ajouté dans la même commande.

Cette valeur est effective uniquement lorsqu’il n’existe aucune vue étendue définie pour le type dans un `Format.ps1xml` fichier.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultDisplayPropertySet

Spécifie une ou plusieurs propriétés du type. Ces propriétés sont affichées par l' `Format-List` applet de commande quand aucune autre propriété n’est spécifiée.

Tapez les noms des propriétés standard ou étendues du type. La valeur de ce paramètre peut correspondre aux noms des types ajoutés dans la même commande.

Cette valeur est effective uniquement quand il n’existe aucun affichage de liste défini pour le type dans un `Format.ps1xml` fichier.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultKeyPropertySet

Spécifie une ou plusieurs propriétés du type. Ces propriétés sont utilisées par les `Group-Object` applets de commande et `Sort-Object` quand aucune autre propriété n’est spécifiée.

Tapez les noms des propriétés standard ou étendues du type. La valeur de ce paramètre peut correspondre aux noms des types ajoutés dans la même commande.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Indique que l’applet de commande utilise les données de type spécifiées, même si des données de type ont déjà été spécifiées pour ce type.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InheritPropertySerializationSet

Indique si le jeu des propriétés sérialisées est hérité. La valeur par défaut est `$Null`. Les valeurs valides pour ce paramètre sont :

- `$True`. Le jeu de propriétés est hérité.
- `$False`. Le jeu de propriétés n'est pas hérité.
- `$Null`. L'héritage n'est pas défini.

Ce paramètre est valide uniquement lorsque la valeur du paramètre **SerializationMethod** est `SpecificProperties` . Lorsque la valeur de ce paramètre est `$False` , le paramètre **PropertySerializationSet** est obligatoire.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberName

Spécifie le nom d'une propriété ou d'une méthode.

Utilisez ce paramètre avec les paramètres **TypeName** , **MemberType** , **Value** et **SecondValue** pour ajouter ou modifier une propriété ou méthode d'un type.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberType

Spécifie le type du membre à ajouter ou changer.

Utilisez ce paramètre avec les paramètres **TypeName** , **MemberType** , **Value** et **SecondValue** pour ajouter ou modifier une propriété ou méthode d'un type. Les valeurs valides pour ce paramètre sont :

- AliasProperty
- CodeMethod
- CodeProperty
- NoteProperty
- ScriptMethod
- ScriptProperty

Pour plus d’informations sur ces valeurs, consultez [énumération PSMemberTypes](/dotnet/api/system.management.automation.psmembertypes).

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrependPath

Spécifie le chemin d’accès aux fichiers facultatifs `.ps1xml` . Les fichiers spécifiés sont chargés dans l'ordre dans lequel ils sont répertoriés avant le chargement des fichiers intégrés.

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PropertySerializationSet

Spécifie les noms des propriétés qui sont sérialisées. Utilisez ce paramètre quand la valeur du paramètre **SerializationMethod** est **SpecificProperties** .

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondValue

Spécifie des valeurs supplémentaires pour les membres **AliasProperty** , **ScriptProperty** , **CodeProperty** ou **CodeMethod** .

Utilisez ce paramètre avec les paramètres **TypeName** , **MemberType** , **value** et **SecondValue** pour ajouter ou modifier une propriété ou une méthode d’un type.

Quand la valeur du paramètre **MemberType** est `AliasProperty` , la valeur du paramètre **SecondValue** doit être un type de données. PowerShell convertit (autrement dit, effectue un cast) la valeur de la propriété d’alias vers le type spécifié. Par exemple, si vous ajoutez une propriété d’alias qui fournit un autre nom pour une propriété de type chaîne, vous pouvez également spécifier un **SecondValue** de **System. Int32** pour convertir la valeur de chaîne avec alias en entier.

Quand la valeur du paramètre **MemberType** est `ScriptProperty` , vous pouvez utiliser le paramètre **SecondValue** pour spécifier un bloc de script supplémentaire. Le bloc de script dans la valeur du paramètre **Value** obtient la valeur d'une variable. Le bloc de script dans la valeur du paramètre **SecondValue** définit la valeur de la variable.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationDepth

Spécifie le nombre de niveaux d'objets de type sérialisés en tant que chaînes. La valeur par défaut `1` sérialise l’objet et ses propriétés. `0`La valeur sérialise l’objet, mais pas ses propriétés. `2`La valeur sérialise l’objet, ses propriétés et tous les objets des valeurs de propriété.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationMethod

Spécifie une méthode de sérialisation pour le type. Une méthode de sérialisation détermine quelles sont les propriétés du type qui sont sérialisées, ainsi que la technique de sérialisation utilisée. Les valeurs valides pour ce paramètre sont :

- `AllPublicProperties`. sérialisez toutes les propriétés publiques du type. Vous pouvez utiliser le paramètre **SerializationDepth** pour déterminer si les propriétés enfants sont sérialisées.
- `String`. sérialisez le type en tant que chaîne. Vous pouvez utiliser **StringSerializationSource** pour spécifier une propriété du type à utiliser comme résultat de la sérialisation. Sinon, le type est sérialisé à l'aide de la méthode **ToString** de l'objet.
- `SpecificProperties`. Sérialise uniquement les propriétés spécifiées de ce type. Utilisez le paramètre **PropertySerializationSet** pour spécifier les propriétés du type qui sont sérialisées.
  Vous pouvez également utiliser le paramètre **InheritPropertySerializationSet** pour déterminer si le jeu de propriétés est hérité, ainsi que le paramètre **SerializationDepth** pour déterminer si les propriétés enfants sont sérialisées.

Dans PowerShell, les méthodes de sérialisation sont stockées dans des objets internes **PSStandardMembers** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StringSerializationSource

Spécifie le nom d'une propriété du type. La valeur de la propriété spécifiée est utilisée comme résultat de la sérialisation. Ce paramètre est valide uniquement lorsque la valeur du paramètre **SerializationMethod** est String.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetTypeForDeserialization

Spécifie le type vers lequel les objets de ce type sont convertis quand ils sont désérialisés.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeAdapter

Spécifie le type d’un adaptateur de type, tel que **Microsoft. PowerShell. CIM. CimInstanceAdapter** . Un adaptateur de type permet à PowerShell d’obtenir les membres d’un type.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeConverter

Spécifie un convertisseur de type pour convertir des valeurs entre différents types. Si un convertisseur de type est défini pour un type, une instance du convertisseur de type est utilisée pour la conversion.

Entrez une valeur **System.Type** dérivée des classes **System.ComponentModel.TypeConverter** ou **System.Management.Automation.PSTypeConverter** .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

Spécifie un tableau de données de type que cette applet de commande ajoute à la session. Entrez une variable qui contient un objet **TypeData** ou une commande qui obtient un objet **TypeData** , tel qu’une `Get-TypeData` commande. Vous pouvez également diriger un objet **TypeData** vers `Update-TypeData` .

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TypeName

Spécifie le nom du type à étendre.

Pour les types de l'espace de noms **System** , entrez le nom court. Sinon, le nom de type complet est obligatoire. Les caractères génériques ne sont pas pris en charge.

Vous pouvez diriger les noms de types vers `Update-TypeData` . Quand vous dirigez un objet vers `Update-TypeData` , `Update-TypeData` obtient le nom de type de l’objet et les données de type vers le type d’objet.

Utilisez ce paramètre avec les paramètres **MemberName** , **MemberType** , **value** et **SecondValue** pour ajouter ou modifier une propriété ou une méthode d’un type.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Value

Spécifie la valeur de la propriété ou de la méthode.

Si vous ajoutez un `AliasProperty` `CodeProperty` membre,, `ScriptProperty` ou `CodeMethod` , vous pouvez utiliser le paramètre **SecondValue** pour ajouter des informations supplémentaires.

Utilisez ce paramètre avec les paramètres **MemberName** , **MemberType** , **value** et **SecondValue** pour ajouter ou modifier une propriété ou une méthode d’un type.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### System.String

Vous pouvez diriger une chaîne qui contient les valeurs des paramètres **AppendPath** , **TypeName** ou **TypeData** vers `Update-TypeData` .

## Sorties

### Aucun

Cette applet de commande ne retourne aucune sortie.

## Notes

## Liens connexes

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Get-TypeData](Get-TypeData.md)

[Remove-TypeData](Remove-TypeData.md)
