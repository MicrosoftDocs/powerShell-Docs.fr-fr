---
title: Déclaration d’attribut ValidateLength | Microsoft Docs
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
ms.openlocfilehash: a1a494534169b2da470286020dfacfa8e9084839
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692325"
---
# <a name="validatelength-attribute-declaration"></a>Déclaration de l’attribut ValidateLength

L’attribut ValidateLength spécifie le nombre minimal et maximal de caractères pour un argument de paramètre d’applet de commande. Cet attribut peut également être utilisé par les fonctions Windows PowerShell.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Paramètres

`MinLength`([System. Int32](/dotnet/api/System.Int32)) requis. Spécifie le nombre minimal de caractères autorisés.

`MaxLength`([System. Int32](/dotnet/api/System.Int32)) requis. Spécifie le nombre maximal de caractères autorisés.

## <a name="remarks"></a>Notes

- Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de validation d’entrée](./how-to-validate-parameter-input.md).

- Lorsque cet attribut n’est pas utilisé, l’argument du paramètre correspondant peut avoir n’importe quelle longueur.

- Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :

  - Lorsque la valeur du `MaxLength` paramètre d’attribut est inférieure à la valeur du `MinLength` paramètre d’attribut.

  - Lorsque le `MaxLength` paramètre d’attribut a la valeur 0.

  - Lorsque l’argument n’est pas une chaîne.

- L’attribut ValidateLength est défini par la classe [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
