---
title: Déclaration d’attribut ValidateCount | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.openlocfilehash: c013a354ee339bd14508fe30549673bc79d5c616
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786320"
---
# <a name="validatecount-attribute-declaration"></a>Déclaration de l’attribut ValidateCount

L’attribut ValidateCount spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Paramètres

`MinLength`([System. Int32][]) requis. Spécifie le nombre minimal d’arguments.

`MaxLength`([System. Int32][]) requis. Spécifie le nombre maximal d’arguments.

## <a name="remarks"></a>Notes

- Pour plus d’informations sur la façon de déclarer cet attribut, consultez [Comment valider un nombre d’arguments][].

- Lorsque cet attribut n’est pas appelé, le paramètre d’applet de commande correspondant peut avoir n’importe quel nombre d’arguments.

- Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :

  - Les `MinLength` `MaxLength` paramètres d’attribut et ne sont pas de type [System. Int32][].

  - La valeur du `MaxLength` paramètre d’attribut est inférieure à la valeur du `MinLength` paramètre d’attribut.

- L’attribut ValidateCount est défini par la classe [System. Management. Automation. ValidateCountAttribute][] .

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. ValidateCountAttribute][]

[Guide pratique pour valider un nombre d’arguments][]

[Écriture d’une applet de commande Windows PowerShell][]

[Guide pratique pour valider un nombre d’arguments]: how-to-validate-an-argument-count.md
[Écriture d’une applet de commande Windows PowerShell]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
