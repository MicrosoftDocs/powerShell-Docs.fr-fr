---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: 2e3d49700adb8115bf24ae505fbb00c14a774f15
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201978"
---
# <span data-ttu-id="d02b1-103">Test-Json</span><span class="sxs-lookup"><span data-stu-id="d02b1-103">Test-Json</span></span>

## <span data-ttu-id="d02b1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d02b1-104">SYNOPSIS</span></span>
<span data-ttu-id="d02b1-105">Teste si une chaîne est un document JSON valide</span><span class="sxs-lookup"><span data-stu-id="d02b1-105">Tests whether a string is a valid JSON document</span></span>

## <span data-ttu-id="d02b1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d02b1-106">SYNTAX</span></span>

```
Test-Json [-Json] <string> [[-Schema] <string>] [<CommonParameters>]
```

## <span data-ttu-id="d02b1-107">Description</span><span class="sxs-lookup"><span data-stu-id="d02b1-107">DESCRIPTION</span></span>

<span data-ttu-id="d02b1-108">L' `Test-Json` applet de commande teste si une chaîne est un document JavaScript Object Notation (JSON) valide et peut éventuellement vérifier ce document JSON par rapport à un schéma fourni.</span><span class="sxs-lookup"><span data-stu-id="d02b1-108">The `Test-Json` cmdlet tests whether a string is a valid JavaScript Object Notation (JSON) document and can optionally verify that JSON document against a provided schema.</span></span>

<span data-ttu-id="d02b1-109">La chaîne vérifiée peut ensuite être utilisée avec l’applet de commande `ConvertFrom-Json` pour convertir une chaîne au format JSON en objet JSON, qui est facilement gérée dans PowerShell ou envoyée à un autre programme ou service Web qui accède à l’entrée JSON.</span><span class="sxs-lookup"><span data-stu-id="d02b1-109">The verified string can then be used with the `ConvertFrom-Json` cmdlet convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell or sent to another program or web service that access JSON input.</span></span>

<span data-ttu-id="d02b1-110">De nombreux sites web utilisent JSON au lieu de XML pour sérialiser les données en vue de la communication entre les serveurs et les applications basées sur le web.</span><span class="sxs-lookup"><span data-stu-id="d02b1-110">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="d02b1-111">Cette applet de commande a été introduite dans PowerShell 6,1</span><span class="sxs-lookup"><span data-stu-id="d02b1-111">This cmdlet was introduced in PowerShell 6.1</span></span>

## <span data-ttu-id="d02b1-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d02b1-112">EXAMPLES</span></span>

### <span data-ttu-id="d02b1-113">Exemple 1 : tester si un objet est un objet JSON valide</span><span class="sxs-lookup"><span data-stu-id="d02b1-113">Example 1: Test if an object is valid JSON</span></span>

<span data-ttu-id="d02b1-114">Cet exemple vérifie si la chaîne d’entrée est un document JSON valide.</span><span class="sxs-lookup"><span data-stu-id="d02b1-114">This example tests whether the input string is a valid JSON document.</span></span>

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### <span data-ttu-id="d02b1-115">Exemple 2 : tester un objet sur un schéma fourni</span><span class="sxs-lookup"><span data-stu-id="d02b1-115">Example 2: Test an object against a provided schema</span></span>

<span data-ttu-id="d02b1-116">Cet exemple prend une chaîne contenant un schéma JSON et la compare à une chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d02b1-116">This example takes a string containing a JSON schema and compares it to an input string.</span></span>

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

<span data-ttu-id="d02b1-117">Dans cet exemple, nous obtenons une erreur, car le schéma attend un entier pour **Age** , mais l’entrée JSON que nous avons testée utilise une valeur de chaîne à la place.</span><span class="sxs-lookup"><span data-stu-id="d02b1-117">In this example, we get an error because the schema expects an integer for **age** but the JSON input we tested uses a string value instead.</span></span>

<span data-ttu-id="d02b1-118">Pour plus d’informations, consultez [schéma JSON](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="d02b1-118">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

## <span data-ttu-id="d02b1-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d02b1-119">PARAMETERS</span></span>

### <span data-ttu-id="d02b1-120">-JSON</span><span class="sxs-lookup"><span data-stu-id="d02b1-120">-Json</span></span>

<span data-ttu-id="d02b1-121">Spécifie la chaîne JSON dont la validité doit être testée.</span><span class="sxs-lookup"><span data-stu-id="d02b1-121">Specifies the JSON string to test for validity.</span></span> <span data-ttu-id="d02b1-122">Entrez une variable contenant la chaîne, ou tapez une commande ou une expression qui obtient la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d02b1-122">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="d02b1-123">Vous pouvez également diriger une chaîne vers `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="d02b1-123">You can also pipe a string to `Test-Json`.</span></span>

<span data-ttu-id="d02b1-124">Le paramètre **JSON** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d02b1-124">The **Json** parameter is required.</span></span>

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

### <span data-ttu-id="d02b1-125">-Schéma</span><span class="sxs-lookup"><span data-stu-id="d02b1-125">-Schema</span></span>

<span data-ttu-id="d02b1-126">Spécifie un schéma pour la validation de l’entrée JSON.</span><span class="sxs-lookup"><span data-stu-id="d02b1-126">Specifies a Schema to validate the JSON input against.</span></span> <span data-ttu-id="d02b1-127">Si la `Test-Json` valeur est passée, le confirme que l’entrée JSON est conforme à la spécification spécifiée par le paramètre de **schéma** et retourne `$True` uniquement si l’entrée est conforme au schéma fourni.</span><span class="sxs-lookup"><span data-stu-id="d02b1-127">If passed `Test-Json` will validate that the Json input conforms to the spec specified by the **Schema** parameter and return `$True` only if the input conforms to the provided Schema.</span></span>

<span data-ttu-id="d02b1-128">Pour plus d’informations, consultez [schéma JSON](https://json-schema.org/).</span><span class="sxs-lookup"><span data-stu-id="d02b1-128">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d02b1-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d02b1-129">CommonParameters</span></span>

<span data-ttu-id="d02b1-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d02b1-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d02b1-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d02b1-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d02b1-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d02b1-132">INPUTS</span></span>

### <span data-ttu-id="d02b1-133">System.String</span><span class="sxs-lookup"><span data-stu-id="d02b1-133">System.String</span></span>

<span data-ttu-id="d02b1-134">Vous pouvez diriger une chaîne JSON vers `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="d02b1-134">You can pipe a JSON string to `Test-Json`.</span></span>

## <span data-ttu-id="d02b1-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d02b1-135">OUTPUTS</span></span>

### <span data-ttu-id="d02b1-136">Boolean</span><span class="sxs-lookup"><span data-stu-id="d02b1-136">Boolean</span></span>

## <span data-ttu-id="d02b1-137">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d02b1-137">NOTES</span></span>

<span data-ttu-id="d02b1-138">L' `Test-Json` applet de commande est implémentée à l’aide de la [classe NJsonSchema](https://github.com/RSuter/NJsonSchema).</span><span class="sxs-lookup"><span data-stu-id="d02b1-138">The `Test-Json` cmdlet is implemented by using the [NJsonSchema Class](https://github.com/RSuter/NJsonSchema).</span></span>

## <span data-ttu-id="d02b1-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d02b1-139">RELATED LINKS</span></span>

<span data-ttu-id="d02b1-140">[Introduction à JavaScript Object Notation (JSON) dans JavaScript et .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="d02b1-140">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="d02b1-141">Détails supplémentaires sur le schéma JSON</span><span class="sxs-lookup"><span data-stu-id="d02b1-141">Additional JSON Schema Details</span></span>](https://json-schema.org/)

[<span data-ttu-id="d02b1-142">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="d02b1-142">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="d02b1-143">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="d02b1-143">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="d02b1-144">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="d02b1-144">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
