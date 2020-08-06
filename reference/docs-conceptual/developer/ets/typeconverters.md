---
title: Convertisseurs de type de système de type étendu
ms.date: 07/09/2020
ms.openlocfilehash: 0d04293fffde9901ed2e33a9bab21e6612ce9cd5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786184"
---
# <a name="ets-type-converters"></a>Convertisseurs de type ETS

ETS utilise deux types de convertisseurs de type de base lorsqu’un appel est effectué à la `LanguagePrimitives.ConvertTo(System.Object, System.Type)` méthode. Lorsque cette méthode est appelée, PowerShell tente d’effectuer la conversion de type à l’aide de ses convertisseurs de langage PowerShell standard ou d’un convertisseur personnalisé. Si PowerShell ne peut pas effectuer la conversion, il lève une exception **PSInvalidCastException** .

## <a name="standard-windows-powershell-language-converters"></a>Convertisseurs de langage Windows PowerShell standard

Ces conversions standard sont vérifiées avant les conversions personnalisées et ne peuvent pas être remplacées. Le tableau suivant répertorie les conversions de types effectuées par PowerShell lorsque la `ConvertTo(System.Object, System.Type)` méthode est appelée. N’oubliez pas que les références aux paramètres **valueToConvert** et **ResultType** font référence aux paramètres de la `ConvertTo(System.Object,System.Type)` méthode.

| De (valueToConvert) |  À (resultType)  |                                                                               Retours                                                                               |
| --------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Null                  | String            | ""                                                                                                                                                                  |
| Null                  | Char              | '\0'                                                                                                                                                                |
| Null                  | Numérique           | `0`du type spécifié dans le paramètre **ResultType** .                                                                                                          |
| Null                  | Boolean           | Résultats de l’appel à la `IsTrue(System.Object)(Null)` méthode.                                                                                                        |
| Null                  | PSObject          | Nouvel objet de type **PSObject**.                                                                                                                                    |
| Null                  | Type non-valeur    | Nul.                                                                                                                                                               |
| Null                  | Nullable &lt; T&gt; | Nul.                                                                                                                                                               |
| Classe dérivée         | Classe de base        | **valueToConvert**                                                                                                                                                  |
| Rien              | Void              | **AutomationNull. Value**                                                                                                                                            |
| Rien              | String            | Appelle le `ToString` mécanisme.                                                                                                                                         |
| Rien              | Boolean           | `IsTrue(System.Object) (valueToConvert)`                                                                                                                            |
| Rien              | PSObject          | Résultats de l’appel à la `AsPSObject(System.Object) (valueToConvert)` méthode.                                                                                         |
| Rien              | Document XML      | Convertit **valueToConvert** en String, puis appelle **XmlDocument** Constructor.                                                                                      |
| Array                 | Array             | Tente de convertir chaque élément du tableau.                                                                                                                      |
| Singleton             | Array             | `Array[0]`est égal à **valueToConvert** qui est converti en type d’élément du tableau.                                                                            |
| IDictionary           | Table de hachage        | Résultats de l’appel à Hashtable (valueToConvert).                                                                                                                       |
| String                | Char[]            | `valueToConvert.ToCharArray`                                                                                                                                        |
| String                | RegEx             | Résultats de l’appel à `Regx(valueToConvert)` .                                                                                                                          |
| String                | Type              | Retourne le type approprié à l’aide du paramètre **valueToConvert** pour rechercher des **RunspaceConfiguration. Assemblies**.                                                 |
| String                | Numérique           | Si **valueToConvert** est «», retourne `0` du **ResultType**. Sinon, la culture « culture invariant » est utilisée pour produire une valeur numérique.                       |
| Integer               | System.Enum       | Convertit l’entier en constante si l’entier est défini par l’énumération. Si l’entier n’est pas défini, une exception **PSInvalidCastException** est levée. |

## <a name="custom-conversions"></a>Conversions personnalisées

Si PowerShell ne peut pas convertir le type à l’aide d’un convertisseur de langage PowerShell standard, il recherche les convertisseurs personnalisés. PowerShell recherche plusieurs types de convertisseurs personnalisés dans l’ordre décrit dans cette section. N’oubliez pas que les références aux paramètres **valueToConvert** et **ResultType** font référence aux paramètres de la `ConvertTo(System.Object, System.Type)` méthode. Si un convertisseur personnalisé lève une exception, aucune autre tentative n’est faite pour convertir l’objet et cette exception est encapsulée dans une exception **PSInvalidCastException** qui est ensuite levée.

## <a name="powershell-type-converter"></a>Convertisseur de type PowerShell

Les convertisseurs de type PowerShell sont utilisés pour convertir un type unique ou une famille de types, tels que tous les types qui dérivent de la classe **System. Enum** . Pour créer un convertisseur de type PowerShell, vous devez implémenter une classe PSTypeConverter et associer cette implémentation à la classe cible. Il existe deux façons d’associer le convertisseur de type PowerShell à sa classe cible.

- Par le biais du fichier de configuration de type
- En appliquant l’attribut **TypeConverterAttribute** à la classe cible

Les convertisseurs de type PowerShell, dérivés de la classe abstraite [PSTypeConverter](/dotnet/api/system.management.automation.pstypeconverter) , fournissent des méthodes pour convertir un objet en un type spécifique ou à partir d’un type spécifique. Si le paramètre **valueToConvert** contient un objet associé à un convertisseur de type PowerShell, PowerShell appelle la`PSTypeConverter.ConvertTo(System.Object, System.Type,System.IFormatProvider, System.Boolean)`
méthode du convertisseur associé pour convertir l’objet en type spécifié par le paramètre **ResultType** . Si le paramètre **ResultType** fait référence à un type qui est associé à un convertisseur de type PowerShell, PowerShell appelle la`PSTypeConverter.ConvertFrom(System.Object,System.Type, System.IFormatProvider, System.Boolean)`
méthode du convertisseur associé pour convertir l’objet à partir du type spécifié par le paramètre **ResultType** .

## <a name="system-type-converter"></a>Convertisseur de type de système

Les convertisseurs de type système permettent de convertir une classe cible spécifique. Ce type de convertisseur ne peut pas être utilisé pour convertir une famille de classes. Pour créer un convertisseur de type système, vous devez implémenter une classe [TypeConverter](/dotnet/api/system.management.automation.runspaces.typedata.typeconverter#System_Management_Automation_Runspaces_TypeData_TypeConverter) et associer cette implémentation à la classe cible. Il existe deux façons d’associer le convertisseur de type système à sa classe cible.

- Par le biais du fichier de configuration de type
- En appliquant l’attribut TypeConverterAttribute à la classe cible

## <a name="parse-converter"></a>Convertisseur d’analyse

Si le paramètre **valueToConvert** est une chaîne et que le type d’objet du paramètre **ResultType** a une `Parse` méthode, la `Parse` méthode est appelée pour convertir la chaîne.

## <a name="constructor-converter"></a>Convertisseur de constructeur

Si le type d’objet du paramètre **ResultType** a un constructeur qui a un paramètre unique qui est du même type que l’objet du paramètre **valueToConvert** , ce constructeur est appelé.

## <a name="implicit-cast-operator-converter"></a>Convertisseur d’opérateur de cast implicite

Si le paramètre **valueToConvert** a un opérateur de cast implicite qui convertit en **ResultType**, son opérateur de conversion est appelé. Si le paramètre **ResultType** a un opérateur de cast implicite qui effectue une conversion à partir de **valueToConvert**, son opérateur de conversion est appelé.

## <a name="explicit-cast-operator-converter"></a>Convertisseur d’opérateur de cast explicite

Si le paramètre **valueToConvert** a un opérateur de cast explicite qui convertit en **ResultType**, son opérateur de conversion est appelé. Si le paramètre **ResultType** a un opérateur de cast explicite qui convertit à partir de **valueToConvert**, son opérateur de conversion est appelé.
