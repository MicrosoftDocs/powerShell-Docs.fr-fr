---
title: Déclaration d’attribut de ValidateCount | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859155"
---
# <a name="validatecount-attribute-declaration"></a>Déclaration de l’attribut ValidateCount

L’attribut ValidateCount Spécifie le nombre minimal et maximal d’arguments autorisés pour un paramètre d’applet de commande.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Paramètres

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) requis. Spécifie le nombre minimal d’arguments.

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) requis. Spécifie le nombre maximal d’arguments.

## <a name="remarks"></a>Remarques

- Pour plus d’informations sur la façon de déclarer cet attribut, consultez [comment déclarer des règles de Validation d’entrée](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Lorsque cet attribut n’est pas appelé, le paramètre d’applet de commande correspondant peut avoir n’importe quel nombre d’arguments.

- Le runtime Windows PowerShell génère une erreur dans les conditions suivantes :

    - Le `MinLength` et `MaxLength` des paramètres d’attribut ne sont pas de type [System.Int32](/dotnet/api/System.Int32).

    - La valeur de la `MaxLength` paramètre d’attribut est inférieure à la valeur de la `MinLength` paramètre d’attribut.

- L’attribut ValidateCount est défini par le [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) classe.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[Comment déclarer des règles de Validation d’entrée](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Comment déclarer des règles de Validation d’entrée](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
