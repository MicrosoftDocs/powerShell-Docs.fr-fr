---
description: Décrit un attribut qui indique le type d'objet retourné par la fonction.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 7cd7f04941077d823bb15d0fa393ca241f38ae3b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206521"
---
# <a name="about-functions-outputtypeattribute"></a>À propos des fonctions OutputTypeAttribute

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit un attribut qui indique le type d'objet retourné par la fonction.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

L’attribut OutputType répertorie les types .NET des objets retournées par la fonction. Vous pouvez utiliser son paramètre ParameterSetName facultatif pour répertorier différents types de sortie pour chaque jeu de paramètres.

L’attribut OutputType est pris en charge sur les fonctions simples et avancées. Il est indépendant de l’attribut CmdletBinding.

L’attribut OutputType fournit la valeur de la propriété OutputType de l’objet **System. Management. Automation. FunctionInfo** retourné par l’applet de commande `Get-Command` .

La valeur de l’attribut OutputType n’est qu’une note de documentation. Elle n’est pas dérivée du code de la fonction ou est comparée à la sortie de la fonction réelle. Par conséquent, la valeur peut être inexacte.

## <a name="syntax"></a>SYNTAX

L’attribut OutputType des fonctions a la syntaxe suivante :

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

Le paramètre **ParameterSetName** est facultatif.

Vous pouvez répertorier plusieurs types dans l’attribut OutputType.

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

Vous pouvez utiliser le paramètre **ParameterSetName** pour indiquer que des jeux de paramètres différents retournent des types différents.

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

Placez les instructions de l’attribut OutputType dans la liste des attributs qui précède l' `Param` instruction.

L’exemple suivant montre le placement de l’attribut OutputType dans une fonction simple.

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

L’exemple suivant montre le placement de l’attribut OutputType dans les fonctions avancées.

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a>EXEMPLES

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a>Exemple 1 : créer une fonction qui a le OutputType de String

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

Pour afficher la propriété type de sortie qui en résulte, utilisez l’applet de commande `Get-Command` .

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a>Exemple 2 : utilisation de l’attribut output pour indiquer les types de sortie dynamiques

La fonction avancée suivante utilise l’attribut OutputType pour indiquer que la fonction retourne des types différents en fonction du jeu de paramètres utilisé dans la commande de fonction.

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a>Exemple 3 : indique quand une sortie réelle diffère du OutputType

L’exemple suivant montre que la valeur de la propriété type de sortie affiche la valeur de l’attribut OutputType, même si elle est incorrecte.

La `Get-Time` fonction retourne une chaîne qui contient la forme abrégée de l’heure dans tout objet DateTime. Toutefois, l’attribut OutputType indique qu’il retourne un objet **System. DateTime** .

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

La `GetType()` méthode confirme que la fonction retourne une chaîne.

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

Toutefois, la propriété OutputType, qui obtient sa valeur de l’attribut OutputType, signale que la fonction retourne un objet **DateTime** .

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a>Exemple 4 : fonction qui ne doit pas avoir de sortie

L’exemple suivant montre une fonction personnalisée qui doit exécuter et agir, mais ne retourne rien.

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a>REMARQUES

La valeur de la propriété OutputType d’un objet **FunctionInfo** est un tableau d’objets **System. Management. Automation. PSTypeName** , dont chacun possède les propriétés Name et type.

Pour obtenir uniquement le nom de chaque type de sortie, utilisez une commande au format suivant.

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

La valeur de la propriété OutputType peut être null. Utilisez une valeur NULL lorsque la sortie n’est pas un type .NET, tel qu’un objet **WMI** ou une vue mise en forme d’un objet.

## <a name="see-also"></a>VOIR AUSSI

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

