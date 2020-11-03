---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: a0d0e31e9010c5ee119b4fbe5f6a877ebc4dc1d3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201918"
---
# New-Module

## SYNOPSIS
Crée un module dynamique qui existe uniquement en mémoire.

## SYNTAX

### ScriptBlock (valeur par défaut)

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### Nom

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## Description

L' `New-Module` applet de commande crée un module dynamique à partir d’un bloc de script. Les membres du module dynamique, tels des fonctions et des variables, sont immédiatement disponibles dans la session et restent disponibles jusqu'à la fermeture de la session.

Comme des modules statiques, les applets de commande et les fonctions figurant dans un module dynamique sont exportées par défaut, alors que les variables et les alias ne le sont pas. Toutefois, vous pouvez utiliser l’applet de commande Export-ModuleMember et les paramètres de `New-Module` pour remplacer les valeurs par défaut.

Vous pouvez également utiliser le paramètre **AsCustomObject** de `New-Module` pour retourner le module dynamique en tant qu’objet personnalisé. Les membres des modules, tels que les fonctions, sont implémentés en tant que méthodes de script de l'objet personnalisé au lieu d'être importés dans la session.

Les modules dynamiques existent uniquement en mémoire, pas sur le disque. Comme tous les modules, les membres des modules dynamiques s'exécutent dans une étendue de module privée qui est un enfant de l'étendue globale. Get-Module ne peut pas obtenir un module dynamique, mais Get-Command peut obtenir les membres exportés.

Pour mettre un module dynamique à la disposition de `Get-Module` , dirigez une `New-Module` commande vers Import-Module, ou dirigez l’objet de module qui `New-Module` retourne à `Import-Module` . Cette action ajoute le module dynamique à la `Get-Module` liste, mais il n’enregistre pas le module sur le disque ou le rend persistant.

## EXEMPLES

### Exemple 1 : créer un module dynamique

Cet exemple crée un nouveau module dynamique avec une fonction appelée `Hello` . La commande retourne un objet de module qui représente le nouveau module dynamique.

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### Exemple 2 : utilisation des modules dynamiques et des Get-Module et des Get-Command

Cet exemple montre que les modules dynamiques ne sont pas retournés par l’applet de commande `Get-Module` . Les membres qu’ils exportent sont retournés par l’applet de commande `Get-Command` .

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### Exemple 3 : exporter une variable dans la session active

Cet exemple utilise l' `Export-ModuleMember` applet de commande pour exporter une variable dans la session active.
Sans la `Export-ModuleMember` commande, seule la fonction est exportée.

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

La sortie indique que la variable et la fonction ont été exportées dans la session.

### Exemple 4 : mettre un module dynamique à la disposition d' Get-Module

Cet exemple montre que vous pouvez mettre un module dynamique à la disposition de `Get-Module` en canalisant le module dynamique vers `Import-Module` .

`New-Module` crée un objet de module qui est dirigé vers l’applet de commande `Import-Module` . Le paramètre **Name** de `New-Module` affecte un nom convivial au module. Étant donné que `Import-Module` ne retourne pas d’objets par défaut, il n’y a aucune sortie de cette commande. `Get-Module` que le **GreetingModule** a été importé dans la session active.

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

L' `Get-Command` applet de commande affiche la `Hello` fonction exportée par le module dynamique.

### Exemple 5 : générer un objet personnalisé qui a des fonctions exportées

Cet exemple montre comment utiliser le paramètre **AsCustomObject** de `New-Module` pour générer un objet personnalisé qui a des méthodes de script qui représentent les fonctions exportées.

L' `New-Module` applet de commande crée un module dynamique avec deux fonctions, `Hello` et `Goodbye` . Le paramètre **AsCustomObject** crée un objet personnalisé à la place de l’objet **PSModuleInfo** `New-Module` généré par défaut par. Cet objet personnalisé est enregistré dans la `$m` variable.
La `$m` variable semble n’avoir aucune valeur assignée.

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

Le canalisation `$m` vers l’applet de commande `Get-Member` affiche les propriétés et les méthodes de l’objet personnalisé. La sortie indique que l’objet possède des méthodes de script qui représentent les `Hello` `Goodbye` fonctions et.
Enfin, nous appelons ces méthodes de script et affichons les résultats.

### Exemple 6 : obtenir les résultats du bloc de script

Cet exemple utilise le paramètre **ReturnResult** pour demander les résultats de l’exécution du bloc de script au lieu de demander un objet de module. Le bloc de script dans le nouveau module définit la `SayHello` fonction, puis appelle la fonction.

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## PARAMETERS

### -ArgumentList

Spécifie un tableau d’arguments qui sont des valeurs de paramètre passées au bloc de script. Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

Indique que cette applet de commande retourne un objet personnalisé qui représente le module dynamique. Les membres de module sont implémentés en tant que méthodes de script de l'objet personnalisé, mais ils ne sont pas importés dans la session. Vous pouvez enregistrer l'objet personnalisé dans une variable et utiliser la notation par points pour appeler les membres.

Si le module possède plusieurs membres portant le même nom, tels qu’une fonction et une variable qui sont tous deux nommés A, un seul membre avec chaque nom est accessible à partir de l’objet personnalisé.

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

### -Applet de commande

Spécifie un tableau d’applets de commande que cette applet de commande exporte à partir du module dans la session active.
Entrez la liste des applets de commandes, séparées par des virgules. Les caractères génériques sont autorisés. Par défaut, toutes les applets de commande du module sont exportées.

Vous ne pouvez pas définir des applets de commande dans un bloc de script, mais un module dynamique peut inclure des applets de commande s'il importe les applets de commande à partir d'un module binaire.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fonction

Spécifie un tableau de fonctions que cette applet de commande exporte à partir du module dans la session active.
Entrez la liste des fonctions, séparées par des virgules. Les caractères génériques sont autorisés. Par défaut, toutes les fonctions définies dans un module sont exportées.

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

### -Name

Spécifie un nom pour le nouveau module. Vous pouvez également diriger un nom de module vers New-Module.

La valeur par défaut est un nom généré automatiquement qui commence par `__DynamicModule_` et est suivi d’un GUID qui spécifie le chemin d’accès du module dynamique.

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ReturnResult

Indique que cette applet de commande exécute le bloc de script et retourne les résultats du bloc de script au lieu de retourner un objet de module.

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

### -ScriptBlock

Spécifie le contenu du module dynamique. Placez le contenu entre accolades ( `{}` ) pour créer un bloc de script. Ce paramètre est obligatoire.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger un nom de module vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSModuleInfo, System. Management. Automation. PSCustomObject ou aucun

Par défaut, cette applet de commande génère un objet **PSModuleInfo** . Si vous utilisez le paramètre **AsCustomObject** , il génère un objet **PSCustomObject** . Si vous utilisez le paramètre **ReturnResult** , il retourne le résultat de l’évaluation du bloc de script dans le module dynamique.

## REMARQUES

Vous pouvez également faire référence à `New-Module` par son alias, `nmo` . Pour plus d’informations, consultez [about_Aliases](About/about_Aliases.md).

## LIENS CONNEXES

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[Module d’importation](Import-Module.md)

[Remove-Module](Remove-Module.md)
