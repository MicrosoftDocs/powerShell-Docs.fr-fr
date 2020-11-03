---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: 79cf0d9a8107cbf843eba5c58e4b4e9ad30ad285
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202162"
---
# Test-Json

## SYNOPSIS
Teste si une chaîne est un document JSON valide

## SYNTAX

### __AllParameterSets (par défaut)
```
Test-Json [-Json] <String> [<CommonParameters>]
```

### SchemaString
```
Test-Json [-Json] <String> [[-Schema] <String>] [<CommonParameters>]
```

### Fichierschéma
```
Test-Json [-Json] <String> [-SchemaFile <String>] [<CommonParameters>]
```

## Description

L' `Test-Json` applet de commande teste si une chaîne est un document JavaScript Object Notation (JSON) valide et peut éventuellement vérifier ce document JSON par rapport à un schéma fourni.

La chaîne vérifiée peut ensuite être utilisée avec l’applet de commande `ConvertFrom-Json` pour convertir une chaîne au format JSON en objet JSON, qui est facilement gérée dans PowerShell ou envoyée à un autre programme ou service Web qui accède à l’entrée JSON.

De nombreux sites web utilisent JSON au lieu de XML pour sérialiser les données en vue de la communication entre les serveurs et les applications basées sur le web.

Cette applet de commande a été introduite dans PowerShell 6,1

## EXEMPLES

### Exemple 1 : tester si un objet est un objet JSON valide

Cet exemple vérifie si la chaîne d’entrée est un document JSON valide.

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### Exemple 2 : tester un objet sur un schéma fourni

Cet exemple prend une chaîne contenant un schéma JSON et la compare à une chaîne d’entrée.

```powershell
$schema = @'
{
  "definitions": {},
  "$schema": "http://json-schema.org/draft-07/schema#",
  "$id": "http://example.com/root.json",
  "type": "object",
  "title": "The Root Schema",
  "required": [
    "name",
    "age"
  ],
  "properties": {
    "name": {
      "$id": "#/properties/name",
      "type": "string",
      "title": "The Name Schema",
      "default": "",
      "examples": [
        "Ashley"
      ],
      "pattern": "^(.*)$"
    },
    "age": {
      "$id": "#/properties/age",
      "type": "integer",
      "title": "The Age Schema",
      "default": 0,
      "examples": [
        25
      ]
    }
  }
}
'@
"{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
```

```Output
Test-Json : IntegerExpected: #/age
At line:1 char:37
+ "{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
+                                     ~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (:) [Test-Json], Exception
+ FullyQualifiedErrorId : InvalidJsonAgainstSchema,Microsoft.PowerShell.Commands.TestJsonCommand
False
```

Dans cet exemple, nous obtenons une erreur, car le schéma attend un entier pour **Age** , mais l’entrée JSON que nous avons testée utilise une valeur de chaîne à la place.

Pour plus d’informations, consultez [schéma JSON](https://json-schema.org/).

### Exemple 3 : tester un objet sur un schéma à partir d’un fichier

Le schéma JSON peut référencer des définitions à l’aide d’un `$ref` mot clé. Le `$ref` peut être résolu en un URI qui fait référence à un autre fichier. Le `SchemaFile` paramètre accepte le chemin d’accès littéral au fichier de schéma JSON et permet la validation des fichiers JSON par rapport à ces schémas.

Dans cet exemple, nous avons un `schema.json` fichier qui fait référence à `definitions.json` .

```powershell
PS> Get-Content schema.json

{
  "description":"A person",
  "type":"object",
  "properties":{
    "name":{
      "$ref":"definitions.json#/definitions/name"
    },
    "hobbies":{
      "$ref":"definitions.json#/definitions/hobbies"
    }
  }
}

PS> Get-Content definitions.json

{
  "definitions":{
    "name":{
      "type":"string"
    },
    "hobbies":{
      "type":"array",
      "items":{
        "type":"string"
      }
    }
  }
}

'{"name": "James", "hobbies": [".NET", "Blogging"]}' | Test-Json -SchemaFile 'schema.json'
```

```Output
True
```

Pour plus d’informations, consultez [structure d’un schéma complexe](https://json-schema.org/understanding-json-schema/structuring.html).

## PARAMETERS

### -JSON

Spécifie la chaîne JSON dont la validité doit être testée. Entrez une variable contenant la chaîne, ou tapez une commande ou une expression qui obtient la chaîne. Vous pouvez également diriger une chaîne vers `Test-Json` .

Le paramètre **JSON** est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Schéma

Spécifie un schéma pour la validation de l’entrée JSON. Si la `Test-Json` valeur est passée, le confirme que l’entrée JSON est conforme à la spécification spécifiée par le paramètre de **schéma** et retourne `$True` uniquement si l’entrée est conforme au schéma fourni.

Pour plus d’informations, consultez [schéma JSON](https://json-schema.org/).

```yaml
Type: System.String
Parameter Sets: SchemaString
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fichierschéma

Spécifie un fichier de schéma utilisé pour valider l’entrée JSON. Lorsqu’il est utilisé, le `Test-Json` retourne `$True` uniquement si l’entrée JSON est conforme au schéma défini dans le fichier spécifié par le **paramètre fichierschéma** .

Pour plus d’informations, consultez [schéma JSON](https://json-schema.org/).

```yaml
Type: System.String
Parameter Sets: SchemaFile
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

Vous pouvez diriger une chaîne JSON vers `Test-Json` .

## SORTIES

### Boolean

## REMARQUES

L' `Test-Json` applet de commande est implémentée à l’aide de la [classe NJsonSchema](https://github.com/RSuter/NJsonSchema).

## LIENS CONNEXES

[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[Détails supplémentaires sur le schéma JSON](https://json-schema.org/)

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
