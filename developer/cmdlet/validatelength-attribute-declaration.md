---
title: Déclaration d’attribut de ValidateLength | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855158"
---
# <a name="validatelength-attribute-declaration"></a>Déclaration de l’attribut ValidateLength

L’attribut ValidateLength Spécifie le nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande. Cet attribut peut également être utilisé par les fonctions de Windows PowerShell.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Paramètres

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) requis. Spécifie le nombre minimal de caractères autorisés.

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) requis. Spécifie le nombre maximal de caractères autorisés.

## <a name="remarks"></a>Remarks

- Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de Validation d’entrée](./how-to-validate-parameter-input.md).

- Lorsque cet attribut n’est pas utilisé, l’argument de paramètre correspondant peut être de n’importe quelle longueur.

- Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :

    - Lorsque la valeur de la `MaxLength` paramètre d’attribut est inférieure à la valeur de la `MinLength` paramètre d’attribut.

    - Lorsque le `MaxLength` paramètre d’attribut est défini sur 0.

    - Lorsque l’argument n’est pas une chaîne.

- L’attribut ValidateLength est défini par le [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
