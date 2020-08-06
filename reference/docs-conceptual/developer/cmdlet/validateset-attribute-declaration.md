---
title: Déclaration d’attribut ValidateSet | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.openlocfilehash: 0b6833efb0ce8e9474e9d91049fd201fc845cbea
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787765"
---
# <a name="validateset-attribute-declaration"></a>Déclaration de l’attribut ValidateSet

L’attribut ValidateSetAttribute spécifie un ensemble de valeurs possibles pour un argument de paramètre d’applet de commande. Cet attribut peut également être utilisé par les fonctions Windows PowerShell.

Lorsque cet attribut est spécifié, le runtime Windows PowerShell détermine si l’argument fourni pour le paramètre d’applet de commande correspond à un élément dans l’ensemble d’éléments fourni. L’applet de commande est exécutée uniquement si l’argument de paramètre correspond à un élément du jeu. Si aucune correspondance n’est trouvée, une erreur est générée par le runtime Windows PowerShell.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Paramètres

`ValidValues`([System. String](/dotnet/api/System.String)) requis. Spécifie les valeurs d’élément de paramètre valides. L’exemple suivant montre comment spécifier un élément ou plusieurs éléments.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase`([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. La valeur par défaut `true` indique que la casse est ignorée. La valeur de `false` rend l’applet de commande sensible à la casse.

## <a name="remarks"></a>Notes

- Cet attribut ne peut être utilisé qu’une seule fois par paramètre.

- Si la valeur de paramètre est un tableau, chaque élément du tableau doit correspondre à un élément de l’ensemble d’attributs.

- L’attribut ValidateSetAttribute est défini par la classe [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
