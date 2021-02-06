---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: a29eab449e567f78d1e54a6716ca91d87aa08405
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597971"
---
# <span data-ttu-id="6e573-102">Test-Json</span><span class="sxs-lookup"><span data-stu-id="6e573-102">Test-Json</span></span>

## <span data-ttu-id="6e573-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6e573-103">SYNOPSIS</span></span>
<span data-ttu-id="6e573-104">Teste si une chaîne est un document JSON valide</span><span class="sxs-lookup"><span data-stu-id="6e573-104">Tests whether a string is a valid JSON document</span></span>

## <span data-ttu-id="6e573-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="6e573-105">SYNTAX</span></span>

### <span data-ttu-id="6e573-106">__AllParameterSets (par défaut)</span><span class="sxs-lookup"><span data-stu-id="6e573-106">__AllParameterSets (Default)</span></span>
```
Test-Json [-Json] <String> [<CommonParameters>]
```

### <span data-ttu-id="6e573-107">SchemaString</span><span class="sxs-lookup"><span data-stu-id="6e573-107">SchemaString</span></span>
```
Test-Json [-Json] <String> [[-Schema] <String>] [<CommonParameters>]
```

### <span data-ttu-id="6e573-108">Fichierschéma</span><span class="sxs-lookup"><span data-stu-id="6e573-108">SchemaFile</span></span>
```
Test-Json [-Json] <String> [-SchemaFile <String>] [<CommonParameters>]
```

## <span data-ttu-id="6e573-109">Description</span><span class="sxs-lookup"><span data-stu-id="6e573-109">DESCRIPTION</span></span>

<span data-ttu-id="6e573-110">L' `Test-Json` applet de commande teste si une chaîne est un document JavaScript Object Notation (JSON) valide et peut éventuellement vérifier ce document JSON par rapport à un schéma fourni.</span><span class="sxs-lookup"><span data-stu-id="6e573-110">The `Test-Json` cmdlet tests whether a string is a valid JavaScript Object Notation (JSON) document and can optionally verify that JSON document against a provided schema.</span></span>

<span data-ttu-id="6e573-111">La chaîne vérifiée peut ensuite être utilisée avec l’applet de commande `ConvertFrom-Json` pour convertir une chaîne au format JSON en objet JSON, qui est facilement gérée dans PowerShell ou envoyée à un autre programme ou service Web qui accède à l’entrée JSON.</span><span class="sxs-lookup"><span data-stu-id="6e573-111">The verified string can then be used with the `ConvertFrom-Json` cmdlet convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell or sent to another program or web service that access JSON input.</span></span>

<span data-ttu-id="6e573-112">De nombreux sites web utilisent JSON au lieu de XML pour sérialiser les données en vue de la communication entre les serveurs et les applications basées sur le web.</span><span class="sxs-lookup"><span data-stu-id="6e573-112">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="6e573-113">Cette applet de commande a été introduite dans PowerShell 6,1</span><span class="sxs-lookup"><span data-stu-id="6e573-113">This cmdlet was introduced in PowerShell 6.1</span></span>

## <span data-ttu-id="6e573-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6e573-114">EXAMPLES</span></span>

### <span data-ttu-id="6e573-115">Exemple 1 : tester si un objet est un objet JSON valide</span><span class="sxs-lookup"><span data-stu-id="6e573-115">Example 1: Test if an object is valid JSON</span></span>

<span data-ttu-id="6e573-116">Cet exemple vérifie si la chaîne d’entrée est un document JSON valide.</span><span class="sxs-lookup"><span data-stu-id="6e573-116">This example tests whether the input string is a valid JSON document.</span></span>

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### <span data-ttu-id="6e573-117">Exemple 2 : tester un objet sur un schéma fourni</span><span class="sxs-lookup"><span data-stu-id="6e573-117">Example 2: Test an object against a provided schema</span></span>

<span data-ttu-id="6e573-118">Cet exemple prend une chaîne contenant un schéma JSON et la compare à une chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="6e573-118">This example takes a string containing a JSON schema and compares it to an input string.</span></span>

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

<span data-ttu-id="6e573-119">Dans cet exemple, nous obtenons une erreur, car le schéma attend un entier pour **Age** , mais l’entrée JSON que nous avons testée utilise une valeur de chaîne à la place.</span><span class="sxs-lookup"><span data-stu-id="6e573-119">In this example, we get an error because the schema expects an integer for **age** but the JSON input we tested uses a string value instead.</span></span>

<span data-ttu-id="6e573-120">Pour plus d’informations, consultez [schéma JSON](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="6e573-120">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

### <span data-ttu-id="6e573-121">Exemple 3 : tester un objet sur un schéma à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="6e573-121">Example 3: Test an object against a schema from file</span></span>

<span data-ttu-id="6e573-122">Le schéma JSON peut référencer des définitions à l’aide d’un `$ref` mot clé.</span><span class="sxs-lookup"><span data-stu-id="6e573-122">JSON schema can reference definitions using `$ref` keyword.</span></span> <span data-ttu-id="6e573-123">Le `$ref` peut être résolu en un URI qui fait référence à un autre fichier.</span><span class="sxs-lookup"><span data-stu-id="6e573-123">The `$ref` can resolve to a URI that references another file.</span></span> <span data-ttu-id="6e573-124">Le `SchemaFile` paramètre accepte le chemin d’accès littéral au fichier de schéma JSON et permet la validation des fichiers JSON par rapport à ces schémas.</span><span class="sxs-lookup"><span data-stu-id="6e573-124">The `SchemaFile` parameter accepts literal path to the JSON schema file and allows JSON files to be validated against such schemas.</span></span>

<span data-ttu-id="6e573-125">Dans cet exemple, nous avons un `schema.json` fichier qui fait référence à `definitions.json` .</span><span class="sxs-lookup"><span data-stu-id="6e573-125">In this example we have `schema.json` file which references `definitions.json`.</span></span>

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

<span data-ttu-id="6e573-126">Pour plus d’informations, consultez [structure d’un schéma complexe](https://json-schema.org/understanding-json-schema/structuring.html).</span><span class="sxs-lookup"><span data-stu-id="6e573-126">For more information, see [Structuring a complex schema](https://json-schema.org/understanding-json-schema/structuring.html).</span></span>

## <span data-ttu-id="6e573-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e573-127">PARAMETERS</span></span>

### <span data-ttu-id="6e573-128">-JSON</span><span class="sxs-lookup"><span data-stu-id="6e573-128">-Json</span></span>

<span data-ttu-id="6e573-129">Spécifie la chaîne JSON dont la validité doit être testée.</span><span class="sxs-lookup"><span data-stu-id="6e573-129">Specifies the JSON string to test for validity.</span></span> <span data-ttu-id="6e573-130">Entrez une variable contenant la chaîne, ou tapez une commande ou une expression qui obtient la chaîne.</span><span class="sxs-lookup"><span data-stu-id="6e573-130">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="6e573-131">Vous pouvez également diriger une chaîne vers `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="6e573-131">You can also pipe a string to `Test-Json`.</span></span>

<span data-ttu-id="6e573-132">Le paramètre **JSON** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6e573-132">The **Json** parameter is required.</span></span>

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

### <span data-ttu-id="6e573-133">-Schéma</span><span class="sxs-lookup"><span data-stu-id="6e573-133">-Schema</span></span>

<span data-ttu-id="6e573-134">Spécifie un schéma pour la validation de l’entrée JSON.</span><span class="sxs-lookup"><span data-stu-id="6e573-134">Specifies a Schema to validate the JSON input against.</span></span> <span data-ttu-id="6e573-135">Si la `Test-Json` valeur est passée, le confirme que l’entrée JSON est conforme à la spécification spécifiée par le paramètre de **schéma** et retourne `$True` uniquement si l’entrée est conforme au schéma fourni.</span><span class="sxs-lookup"><span data-stu-id="6e573-135">If passed `Test-Json` will validate that the Json input conforms to the spec specified by the **Schema** parameter and return `$True` only if the input conforms to the provided Schema.</span></span>

<span data-ttu-id="6e573-136">Pour plus d’informations, consultez [schéma JSON](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="6e573-136">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

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

### <span data-ttu-id="6e573-137">-Fichierschéma</span><span class="sxs-lookup"><span data-stu-id="6e573-137">-SchemaFile</span></span>

<span data-ttu-id="6e573-138">Spécifie un fichier de schéma utilisé pour valider l’entrée JSON.</span><span class="sxs-lookup"><span data-stu-id="6e573-138">Specifies a schema file used to validate the JSON input.</span></span> <span data-ttu-id="6e573-139">Lorsqu’il est utilisé, le `Test-Json` retourne `$True` uniquement si l’entrée JSON est conforme au schéma défini dans le fichier spécifié par le **paramètre fichierschéma** .</span><span class="sxs-lookup"><span data-stu-id="6e573-139">When used, the `Test-Json` returns `$True` only if the JSON input conforms to the Schema defined in the file specified by the **SchemaFile** parameter.</span></span>

<span data-ttu-id="6e573-140">Pour plus d’informations, consultez [schéma JSON](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="6e573-140">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

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

### <span data-ttu-id="6e573-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6e573-141">CommonParameters</span></span>

<span data-ttu-id="6e573-142">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6e573-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6e573-143">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6e573-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6e573-144">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="6e573-144">INPUTS</span></span>

### <span data-ttu-id="6e573-145">System.String</span><span class="sxs-lookup"><span data-stu-id="6e573-145">System.String</span></span>

<span data-ttu-id="6e573-146">Vous pouvez diriger une chaîne JSON vers `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="6e573-146">You can pipe a JSON string to `Test-Json`.</span></span>

## <span data-ttu-id="6e573-147">SORTIES</span><span class="sxs-lookup"><span data-stu-id="6e573-147">OUTPUTS</span></span>

### <span data-ttu-id="6e573-148">Boolean</span><span class="sxs-lookup"><span data-stu-id="6e573-148">Boolean</span></span>

## <span data-ttu-id="6e573-149">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="6e573-149">NOTES</span></span>

<span data-ttu-id="6e573-150">L' `Test-Json` applet de commande est implémentée à l’aide de la [classe NJsonSchema](https://github.com/RSuter/NJsonSchema).</span><span class="sxs-lookup"><span data-stu-id="6e573-150">The `Test-Json` cmdlet is implemented by using the [NJsonSchema Class](https://github.com/RSuter/NJsonSchema).</span></span>

## <span data-ttu-id="6e573-151">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="6e573-151">RELATED LINKS</span></span>

<span data-ttu-id="6e573-152">[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="6e573-152">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="6e573-153">Détails supplémentaires sur le schéma JSON</span><span class="sxs-lookup"><span data-stu-id="6e573-153">Additional JSON Schema Details</span></span>](https://json-schema.org/)

[<span data-ttu-id="6e573-154">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="6e573-154">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="6e573-155">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="6e573-155">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="6e573-156">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="6e573-156">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
