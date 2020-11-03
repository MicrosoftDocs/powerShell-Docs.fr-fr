---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: f430dd1f9d9f820dda88ba5ad40023650204604d
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205985"
---
# Group-Object

## SYNOPSIS
Groupe les objets qui contiennent la même valeur pour les propriétés spécifiées.

## SYNTAX

### Hachage

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## Description

L' `Group-Object` applet de commande affiche les objets dans des groupes en fonction de la valeur d’une propriété spécifiée.
`Group-Object` retourne une table avec une ligne pour chaque valeur de propriété et une colonne qui affiche le nombre d’éléments avec cette valeur.

Si vous spécifiez plusieurs propriétés, vous `Group-Object` les regroupez d’abord selon les valeurs de la première propriété, puis, dans chaque groupe de propriétés, elle est regroupée selon la valeur de la propriété Next.

## EXEMPLES

### Exemple 1 : regrouper des fichiers par extension

Cet exemple obtient de manière récursive les fichiers sous `$PSHOME` et les regroupe par extension de nom de fichier. La sortie est envoyée à l' `Sort-Object` applet de commande, qui les trie par nombre de fichiers trouvés pour l’extension donnée. Le **nom** vide représente des répertoires.

Cet exemple utilise le paramètre **NoElement** pour omettre les membres du groupe.

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### Exemple 2 : regrouper des entiers par des chances et même

Cet exemple montre comment utiliser des blocs de script comme valeur du paramètre **Property** . Cette commande affiche les entiers de 1 à 20, regroupés par chances et même.

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### Exemple 3 : regrouper les événements du journal des événements par EntryType

Cet exemple affiche les 1 000 entrées les plus récentes dans le journal des événements système, regroupées par **entryType** .

Dans la sortie, la colonne **Count** représente le nombre d’entrées dans chaque groupe. La colonne **nom** représente les valeurs de **eventType** qui définissent un groupe. La colonne **groupe** représente les objets de chaque groupe.

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### Exemple 4 : regrouper des processus par classe de priorité

Cet exemple illustre l’effet du paramètre **NoElement** . Ces commandes regroupent les processus en cours d'exécution sur l'ordinateur par classe de priorité.

La première commande utilise l' `Get-Process` applet de commande pour récupérer les processus sur l’ordinateur et envoie les objets dans le pipeline. `Group-Object`regroupe les objets selon la valeur de la propriété **PriorityClass** du processus.

Le deuxième exemple utilise le paramètre **NoElement** pour éliminer les membres du groupe de la sortie. Le résultat est une table avec uniquement la valeur de la propriété **Count** et **Name** .

Les résultats sont présentés dans l'exemple de sortie suivant.

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### Exemple 5 : regrouper les processus par nom

L’exemple suivant utilise `Group-Object` pour regrouper plusieurs instances de processus en cours d’exécution sur l’ordinateur local. `Where-Object` affiche les processus avec plusieurs instances.

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### Exemple 6 : regrouper des objets dans une table de hachage

Cet exemple utilise les paramètres **AsHashTable** et **AsString** pour retourner les groupes dans une table de hachage, sous la forme d’une collection de paires clé-valeur.

Dans la table de hachage résultante, chaque valeur de propriété est une clé et les éléments de groupe sont les valeurs.
Comme chaque clé est une propriété de l'objet de table de hachage, vous pouvez utiliser la notation par points pour afficher les valeurs.

La première commande obtient les `Get` `Set` applets de commande et dans la session, les regroupe par verbe, retourne les groupes sous la forme d’une table de hachage et enregistre la table de hachage dans la `$A` variable.

La deuxième commande affiche la table de hachage dans `$A` . Il existe deux paires clé-valeur, une pour les `Get` applets de commande et une pour les `Set` applets de commande.

La troisième commande utilise la notation par points `$A.Get` pour afficher les valeurs de la clé d' **extraction** dans `$A` . Les valeurs sont des objets **CmdletInfo** . Le paramètre **AsString** ne convertit pas les objets des groupes en chaînes.

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Cmdlet          Get-Acl                            6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                          6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AuthenticodeSignature          6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-ChildItem                      6.1.0.0    Microsoft.PowerShell.Management
...
```

## PARAMETERS

### -AsHashTable

Indique que cette applet de commande retourne le groupe sous la forme d’une table de hachage. Les clés de la table de hachage sont les valeurs des propriétés selon lesquelles les objets sont regroupés. Les valeurs de la table de hachage sont les objets qui ont cette valeur de propriété.

En soi, le paramètre **AsHashTable** retourne chaque table de hachage dans laquelle chaque clé est une instance de l’objet groupé. En cas d’utilisation avec le paramètre **AsString** , les clés de la table de hachage sont des chaînes.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsString

Indique que cette applet de commande convertit les clés de table de hachage en chaînes. Par défaut, les clés d'une table de hachage sont des instances de l'objet regroupé. Ce paramètre n’est valide que lorsqu’il est utilisé avec le paramètre **AsHashTable** .

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

### -CaseSensitive

Indique que cette applet de commande rend le regroupement sensible à la casse. Sans ce paramètre, les valeurs des propriétés des objets dans un groupe peuvent avoir des casses différentes.

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

### -Culture

Spécifie la culture à utiliser lors de la comparaison de chaînes.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets à regrouper. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

Quand vous utilisez le paramètre **InputObject** pour envoyer une collection d’objets à `Group-Object` , `Group-Object` reçoit un objet qui représente la collection. Elle crée donc un seul groupe avec cet objet comme membre.

Pour regrouper les objets d’une collection, dirigez les objets vers `Group-Object` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoElement

Indique que cette applet de commande omet les membres d’un groupe des résultats.

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

### -Propriété

Spécifie les propriétés pour le regroupement. Les objets sont organisés en groupes en fonction de la valeur de la propriété spécifiée.

La valeur du paramètre **Property** peut être une nouvelle propriété calculée. La propriété calculée peut être un bloc de script ou une table de hachage. Les paires clé-valeur valides sont :

- Expression `<string>` ou `<script block>`

Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger n’importe quel objet vers `Group-Object` .

## SORTIES

### Microsoft. PowerShell. Commands. GroupInfo ou System. Collections. Hashtable

Quand vous utilisez le paramètre **AsHashTable** , `Group-Object` retourne un objet **Hashtable** .
Sinon, elle retourne un objet **GroupInfo** .

## REMARQUES

Vous pouvez utiliser le paramètre **GroupBy** des applets de commande de mise en forme, telles que `Format-Table` et `Format-List` , pour regrouper des objets. Contrairement à `Group-Object` , qui crée une seule table avec une ligne pour chaque valeur de propriété, les paramètres **GroupBy** créent une table pour chaque valeur de propriété avec une ligne pour chaque élément ayant la valeur de propriété.

`Group-Object` n’exige pas que les objets regroupés soient du même Microsoft .NET type de noyau. Lors du regroupement d’objets de différents types .NET Core, `Group-Object` utilise les règles suivantes :

- Mêmes noms et types de propriétés.

  Si les objets ont une propriété avec le nom spécifié et que les valeurs de propriété ont le même type .NET Core, les valeurs de propriété sont regroupées à l’aide des mêmes règles que celles utilisées pour les objets du même type.

- Mêmes noms de propriété, types différents.

  Si les objets ont une propriété avec le nom spécifié, mais que les valeurs de propriété ont un type .NET Core différent dans des objets différents, `Group-Object` utilise le type .net Core de la première occurrence de la propriété comme type .net Core pour ce groupe de propriétés. Quand un objet a une propriété avec un type différent, la valeur de la propriété est convertie vers le type de ce groupe. Si la conversion de type échoue, l’objet n’est pas inclus dans le groupe.

- Propriétés manquantes.

  Les objets qui n’ont pas de propriété spécifiée ne peuvent pas être regroupés. Les objets qui ne sont pas regroupés apparaissent dans la sortie finale de l’objet **GroupInfo** dans un groupe nommé `AutomationNull.Value` .

## LIENS CONNEXES

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
