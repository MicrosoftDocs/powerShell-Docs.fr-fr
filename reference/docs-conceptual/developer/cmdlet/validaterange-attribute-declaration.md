---
title: Déclaration d’attribut ValidateRange | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369128"
---
# <a name="validaterange-attribute-declaration"></a>Déclaration de l’attribut ValidateRange

L’attribut ValidateRange spécifie les valeurs minimales et maximales (la plage) pour l’argument du paramètre de l’applet de commande. Cet attribut peut également être utilisé par les fonctions Windows PowerShell.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Paramètres

`MinRange` ([System. Object](/dotnet/api/system.object)) requis. Spécifie la valeur minimale autorisée.

`MaxRange` ([System. Object](/dotnet/api/system.object)) requis. Spécifie la valeur maximale autorisée.

## <a name="remarks"></a>Remarks

- Le runtime Windows PowerShell lève une erreur de construction quand la valeur du paramètre `MinRange` est supérieure à la valeur du paramètre `MaxRange`.

- Le runtime Windows PowerShell lève une erreur de validation dans les conditions suivantes :

    - Lorsque la valeur de l’argument est inférieure à la limite `MinRange` ou supérieure à la limite de `MaxRange`.

    - Lorsque l’argument n’est pas du même type que les paramètres `MinRange` et `MaxRange`.

- L’attribut ValidateRange est défini par la classe [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
