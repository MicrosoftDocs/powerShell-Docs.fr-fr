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
ms.openlocfilehash: 560fa105ac3f93ae6334df0112f5290dfa20576c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692012"
---
# <a name="validaterange-attribute-declaration"></a>Déclaration de l’attribut ValidateRange

L’attribut ValidateRange spécifie les valeurs minimales et maximales (la plage) pour l’argument du paramètre de l’applet de commande. Cet attribut peut également être utilisé par les fonctions Windows PowerShell.

## <a name="syntax"></a>Syntaxe

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Paramètres

`MinRange`([System. Object](/dotnet/api/system.object)) requis. Spécifie la valeur minimale autorisée.

`MaxRange`([System. Object](/dotnet/api/system.object)) requis. Spécifie la valeur maximale autorisée.

## <a name="remarks"></a>Notes

- Le runtime Windows PowerShell lève une erreur de construction quand la valeur du `MinRange` paramètre est supérieure à la valeur du `MaxRange` paramètre.

- Le runtime Windows PowerShell lève une erreur de validation dans les conditions suivantes :

  - Lorsque la valeur de l’argument est inférieure à la `MinRange` limite ou supérieure à la `MaxRange` limite.

  - Lorsque l’argument n’est pas du même type que les `MinRange` paramètres et `MaxRange` .

- L’attribut ValidateRange est défini par la classe [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
