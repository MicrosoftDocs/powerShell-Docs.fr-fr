---
title: Déclaration d’attribut ValidateSet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364278"
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

`ValidValues` ([System. String](/dotnet/api/System.String)) requis. Spécifie les valeurs d’élément de paramètre valides. L’exemple suivant montre comment spécifier un élément ou plusieurs éléments.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) paramètre nommé facultatif. La valeur par défaut de `true` indique que la casse est ignorée. La valeur `false` rend l’applet de commande sensible à la casse.

## <a name="remarks"></a>Remarks

- Cet attribut ne peut être utilisé qu’une seule fois par paramètre.

- Si la valeur de paramètre est un tableau, chaque élément du tableau doit correspondre à un élément de l’ensemble d’attributs.

- L’attribut ValidateSetAttribute est défini par la classe [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
