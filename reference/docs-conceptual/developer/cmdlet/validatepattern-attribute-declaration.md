---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut ValidatePattern
description: Déclaration de l’attribut ValidatePattern
ms.openlocfilehash: 364f63d2c52563eaefe64bcbb2bbae511bccb074
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646164"
---
# <a name="validatepattern-attribute-declaration"></a>Déclaration de l’attribut ValidatePattern

L’attribut ValidatePattern spécifie un modèle d’expression régulière qui valide l’argument d’un paramètre d’applet de commande. Cet attribut peut également être utilisé par les fonctions Windows PowerShell.

Quand ValidatePattern est appelé dans une applet de commande, le runtime Windows PowerShell convertit l’argument du paramètre d’applet de commande en une chaîne, puis compare cette chaîne au modèle fourni par l’attribut ValidatePattern. L’applet de commande est exécutée uniquement si la représentation sous forme de chaîne convertie de l’argument et du modèle fourni correspond à. Si elles ne correspondent pas, une erreur est générée par le runtime Windows PowerShell.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Paramètres

`RegexString` ([System. String](/dotnet/api/System.String)) requis. Spécifie une expression régulière qui valide l’argument du paramètre.

Options ([System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) paramètre nommé facultatif. Spécifie une combinaison d’opérations de bits d’indicateurs [System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) qui spécifient des options d’expression régulière.

## <a name="remarks"></a>Notes

- Cet attribut ne peut être utilisé qu’une seule fois par paramètre.

- Vous pouvez utiliser le `Option` paramètre de l’attribut pour définir plus précisément le modèle. Par exemple, vous pouvez rendre le modèle sensible à la casse.

- Si cet attribut est appliqué à une collection, chaque élément de la collection doit correspondre au modèle.

- L’attribut ValidatePattern est défini par la classe [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
