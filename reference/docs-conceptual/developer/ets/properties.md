---
title: Propriétés du système de type étendu
ms.date: 07/09/2020
ms.openlocfilehash: c0a994e5b946117dcc1a2d647d07ae62af883861
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786201"
---
# <a name="ets-properties"></a>Propriétés de ETS

Les propriétés sont des membres qui peuvent être traités comme une propriété. Pour l’essentiel, ils peuvent apparaître sur le côté gauche d’une expression. Les propriétés disponibles incluent les propriétés alias, code, note et script.

## <a name="alias-property"></a>Propriété alias

Une propriété d’alias est une propriété qui fait référence à une autre propriété que l’objet **PSObject** contient. Il est principalement utilisé pour renommer la propriété référencée. Toutefois, il peut également être utilisé pour convertir la valeur de la propriété référencée en un autre type. En ce qui concerne ETS, ce type de propriété est toujours un membre étendu et est défini par la classe [PSAliasProperty](/dotnet/api/system.management.automation.psaliasproperty) . La classe comprend les propriétés suivantes.

- Propriété **ConversionType** : type CLR utilisé pour convertir la valeur du membre référencé.
- Propriété **IsGettable** : indique si la valeur de la propriété référencée peut être récupérée.
  Cette propriété est déterminée dynamiquement en examinant la propriété **IsGettable** de la propriété référencée.
- Propriété **IsSettable** : indique si la valeur de la propriété référencée peut être définie. Cette propriété est déterminée dynamiquement en examinant la propriété **IsSettable** de la propriété référencée.
- Propriété **MemberType** : constante d’énumération **AliasProperty** qui définit cette propriété en tant que propriété d’alias.
- Propriété **ReferencedMemberName** : nom de la propriété référencée à laquelle cet alias fait référence.
- Propriété **TypeNameOfValue** : nom complet du type CLR de la valeur de la propriété référencée.
- Propriété **value** : valeur de la propriété référencée.

## <a name="code-property"></a>Code, propriété

Une propriété de code est une propriété qui est un accesseur get et un accesseur Set définis dans un langage CLR. Pour qu’une propriété de code soit disponible, un développeur doit écrire la propriété dans un langage CLR, compiler et livrer l’assembly résultant. Cet assembly doit être disponible dans l’instance d’exécution où la propriété de code est souhaitée. En ce qui concerne ETS, ce type de propriété est toujours un membre étendu et est défini par la classe [PSCodeProperty](/dotnet/api/system.management.automation.pscodeproperty) . La classe comprend les propriétés suivantes.

- Propriété **GetterCodeReference** : méthode utilisée pour récupérer la valeur de la propriété de code.
- Propriété **IsGettable** : indique si la valeur de la propriété de code peut être récupérée, la propriété **SetterCodeReference** : la méthode utilisée pour définir la valeur de la propriété de code.
- Propriété **IsSettable** : indique si la valeur de la propriété de code peut être définie, que la propriété **SetterCodeReference** n’a pas la valeur null.
- Propriété **MemberType** : constante d’énumération **CodeProperty** qui définit cette propriété en tant que propriété de code.
- Propriété **SetterCodeReference** : méthode utilisée pour récupérer la valeur de la propriété de code.
- Propriété **TypeNameOfValue** : type CLR de la valeur de la propriété de code qui est retournée par l’opération de récupération des propriétés.
- Propriété **value** : valeur de la propriété de code. Quand cette propriété est récupérée, le code de l’accesseur Get dans la propriété GetterCodeReference est appelé, en passant l’objet **PSObject** en cours et en retournant la valeur retournée par l’appel. Quand cette propriété est définie, le code d’accesseur set dans la propriété **SetterCodeReference** est appelé, en passant l’objet **PSObject** actuel comme premier argument et l’objet utilisé pour définir la valeur comme deuxième argument.

## <a name="note-property"></a>Propriété de note

Une propriété de note est une propriété qui a un jumelage nom/valeur. En ce qui concerne ETS, ce type de propriété est toujours un membre étendu et est défini par la classe [PSNoteProperty](/dotnet/api/system.management.automation.psnoteproperty) . La classe comprend les propriétés suivantes.

- Propriété **IsGettable** : indique si la valeur de la propriété de note peut être récupérée.
- Propriété **IsSettable** : indique si la valeur de la propriété de note peut être définie.
- Propriété **MemberType** : constante d’énumération **NoteProperty** qui définit cette propriété en tant que propriété de note.
- Propriété **TypeNameOfValue** : nom de type qualifié complet de l’objet retourné par l’opération d’extraction de la propriété de la note.
- **Valeur**: valeur de la propriété de note.

## <a name="powershell-property"></a>Propriété PowerShell

Une propriété PowerShell est une propriété définie sur l’objet de base ou sur une propriété qui est mise à disposition via un adaptateur. Il peut faire référence aux champs CLR et aux propriétés CLR. En ce qui concerne ETS, ce type de propriété peut être un membre de base ou un élément d’adaptateur et est défini par la classe [PSProperty](/dotnet/api/system.management.automation.psproperty) . La classe comprend les propriétés suivantes.

- Propriété **IsGettable** : indique si la valeur de la propriété de base ou adaptée peut être récupérée.
- Propriété **IsSettable** : indique si la valeur de la propriété de base ou adaptée peut être définie.
- Propriété **MemberType** : constante d’énumération de propriété qui définit cette propriété en tant que propriété PowerShell.
- Propriété **TypeNameOfValue** : nom complet du type de valeur de propriété. Par exemple, pour une propriété dont la valeur est une chaîne, son type de valeur de propriété est **System. String**.
- Propriété **value** : valeur de la propriété. Si l’opération d’extraction ou de définition est appelée sur une propriété qui ne prend pas en charge cette opération, une exception **GetValueException** ou **SetValueException** est levée

## <a name="powershell-script-property"></a>Propriété de script PowerShell

Une propriété de script est une propriété qui contient des scripts getter et Setter. En ce qui concerne ETS, ce type de propriété est toujours un membre étendu et est défini par la classe [PSScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) . La classe comprend les propriétés suivantes.

- Propriété **GetterScript** : script utilisé pour récupérer la valeur de la propriété de script.
- Propriété **IsGettable** : indique si la propriété **GetterScript** expose un bloc de script.
- Propriété **IsSettable** : indique si la propriété **SetterScript** expose un bloc de script.
- Propriété **MemberType** : constante d’énumération ScriptProperty qui identifie cette propriété en tant que propriété de script.
- Propriété **SetterScript** : script utilisé pour définir la valeur de la propriété de script.
- Propriété **TypeNameOfValue** : nom de type complet de l’objet retourné par le script de l’accesseur Get. Dans ce cas, **System. Object** est toujours retourné.
- Propriété **value** : valeur de la propriété script. Une méthode get appelle le script de l’accesseur get et retourne la valeur fournie. Un ensemble appelle le script Setter.
