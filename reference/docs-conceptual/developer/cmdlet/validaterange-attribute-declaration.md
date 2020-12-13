---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut ValidateRange
description: Déclaration de l’attribut ValidateRange
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660601"
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

## <a name="remarks"></a>Notes

- Le runtime Windows PowerShell lève une erreur de construction quand la valeur du `MinRange` paramètre est supérieure à la valeur du `MaxRange` paramètre.

- Le runtime Windows PowerShell lève une erreur de validation dans les conditions suivantes :

  - Lorsque la valeur de l’argument est inférieure à la `MinRange` limite ou supérieure à la `MaxRange` limite.

  - Lorsque l’argument n’est pas du même type que les `MinRange` paramètres et `MaxRange` .

- L’attribut ValidateRange est défini par la classe [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
